---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 分離設定和環境資料
ms.openlocfilehash: b16243fc9096f786a25ed20868e94a3aa85e403e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954435"
---
# <a name="separating-configuration-and-environment-data"></a>分離設定和環境資料

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

使用設定資料來分離 DSC 設定中所用資料與設定本身，是非常實用的。
藉由執行此動作，您就能針對多個環境使用單一設定。

例如，如果您要開發應用程式，您可以針對開發和生產環境使用一個設定，並使用設定資料來指定每個環境的資料。

## <a name="what-is-configuration-data"></a>何謂設定資料？

設定資料是當您編譯 DSC 設定時，定義於雜湊表中並傳遞至該設定的資料。

如需 **ConfigurationData** 雜湊表的詳細描述，請參閱[使用設定資料](configData.md)。

## <a name="a-simple-example"></a>一個簡單的範例

讓我們看看一個非常簡單的範例，以了解其運作方式。
我們將建立單一設定，確保 **IIS** 位於一些節點上，而 **HYPER-V** 位於另一些節點上：

```powershell
Configuration MyDscConfiguration {

    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }

    }
    Node $AllNodes.Where{$_.Role -eq "VMHost"}.NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        },

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

此指令碼的最後一行會編譯設定，並傳遞 `$MyData` 作為 **ConfigurationData** 參數值。

結果會建立兩個 MOF 檔案：

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData` 指定兩個不同的節點，各有其專屬的 `NodeName` 和 `Role`。 此設定會從 `$MyData` 取得節點集合 (亦即 `$AllNodes`)，然後針對 `Role` 屬性篩選該集合，藉此以動態方式建立 **Node** 區塊。

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>使用設定資料定義開發和生產環境

讓我們看看一個完整的範例，該範例使用單一設定來設定網站的開發和生產環境。 在開發環境中，IIS 和 SQL Server 會安裝在單一節點上。 在生產環境中，IIS 和 SQL Server 會安裝在不同的節點上。 我們將使用設定資料檔案 .psd1，來指定這兩個不同環境的資料。

### <a name="configuration-data-file"></a>設定資料檔案

我們將在名為 `DevProdEnvData.psd1` 的檔案中定義開發與生產環境資料，如下所示：

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        WebSiteName     = "New website"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        },

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"
        }
    )
}
```

### <a name="configuration-script-file"></a>設定指令檔

現在，在定義於 `.ps1` 檔案的設定中，我們會依其角色 (`MSSQL`、`Dev` 或兩者) 來篩選 `DevProdEnvData.psd1` 中所定義的節點，並據此加以設定。
開發環境會將 SQL Server 和 IIS 放在一個節點上，而生產環境則會將這兩者放在兩個不同的節點上。
網站內容也會依照 `SiteContents` 屬性的指定而有所不同。

在設定指令碼結尾處，我們會呼叫設定 (將其編譯為 MOF 文件)，並傳遞 `DevProdEnvData.psd1` 作為 `$ConfigurationData` 參數。

>**注意︰** 這項設定要求在目標節點上安裝模組 `xSqlPs` 和 `xWebAdministration`。

讓我們在名為 `MyWebApp.ps1` 的檔案中定義設定：

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.NodeName
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where{$_.Role -contains "Web"}.NodeName
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $Node.WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

當您執行此設定時，會建立三個 MOF 檔案 (在 **AllNodes** 陣列中針對每個具名項目各建立一個)：

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>使用非節點資料

您可以將額外的索引鍵加入 **ConfigurationData** 雜湊表，以供非節點專屬的資料使用。
下列設定確保會存在兩個網站。
每個網站的資料均定義於 **AllNodes** 陣列中。
檔案 `Config.xml` 要供這兩個網站使用，因此，我們將它定義於名為 `NonNodeData` 的額外索引鍵中。
請注意，您可以視需要定義任意多個額外的索引鍵，且可隨意命名。
`NonNodeData` 不是保留字，它只是我們決定來為額外索引鍵命名的名稱。

您可以使用特殊變數 **$ConfigurationData** 來存取額外的索引鍵。
在此範例中，會使用下列程式碼行來存取 `ConfigFileContents`：
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 在 `File` 資源區塊中。


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

        @{
            NodeName = "VM-1"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },


        @{
            NodeName = "VM-2"
            SiteContents = "C:\Site2"
            SiteName = "Website2"
        }
    );

    NonNodeData =
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }
}

configuration WebsiteConfig
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a>另請參閱
- [使用設定資料](configData.md)
- [設定資料的認證選項](configDataCredentials.md)
- [DSC 設定](configurations.md)
