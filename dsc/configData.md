---
title: "分離設定和環境資料"
ms.date: 2016-05-16
keywords: "PowerShell，DSC"
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 72555a36819c9717fafdd3daede8fa2f02c692b2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="separating-configuration-and-environment-data"></a>分離設定和環境資料

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

您可以使用內建的 DSC **ConfigurationData** 參數，定義可用於設定中的資料。 這可讓您建立可用於多個節點或不同環境的單一設定。 例如，如果您要開發應用程式，您可以針對開發和生產環境使用一個設定，並使用設定資料來指定每個環境的資料。

讓我們看看一個非常簡單的範例，以了解其運作方式。 我們將建立單一設定，確保 **IIS** 位於一些節點上，而 **HYPER-V** 位於另一些節點上： 

```powershell
Configuration MyDscConfiguration {
    
    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
        
    }
    Node $AllNodes.Where($_.Role -eq "VMHost").NodeName
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
        }

        @{
            NodeName    = 'VM-2'
            FeatureName = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

此指令碼中的最後一行會將設定編譯為 MOF 文件，並傳遞 `$MyData` 作為 **ConfigurationData** 參數值。 `$MyData` 指定兩個不同的節點，各有其專屬的 `NodeName` 和 `Role`。 此設定會從 `$MyData` 取得節點集合 (亦即 `$AllNodes`)，然後針對 `Role` 屬性篩選該集合，藉此以動態方式建立 **Node** 區塊。

現在讓我們更詳細地看看其運作方式。

## <a name="the-configurationdata-parameter"></a>ConfigurationData 參數

DSC 設定使用名為 **ConfigurationData** 的參數，這是編譯設定時所指定的參數。 如需編譯設定的資訊，請參閱 [DSC 設定](configurations.md)。

**ConfigurationData** 參數是至少必須有一個名為 **AllNodes** 之索引鍵的雜湊表。 它也可以包含其他索引鍵：

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

**AllNodes** 索引鍵的值是陣列。 此陣列的每個元素也是至少必須有一個名為 **NodeName** 之索引鍵的雜湊表：

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
        },

 
        @{
            NodeName = "VM-2"
        },

 
        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""   
}
```

您也可以將其他索引鍵新增至每個雜湊表：

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

若要將屬性套用至所有節點，您可以建立 **AllNodes** 陣列的成員，其 **NodeName** 為 `*`。 例如，您可以如下為每個節點提供 `LogPath` 屬性：

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },

 
        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },

 
        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },

 
        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

這相當於將名稱為 `LogPath` 且值為 `"C:\Logs"` 的屬性新增至每個其他區塊 (`VM-1`、`VM-2` 和 `VM-3`)。

## <a name="defining-the-configurationdata-hashtable"></a>定義 ConfigurationData 雜湊表

您可以將 **ConfigurationData** 定義為與設定位於相同指令碼檔案中的變數 (如上述範例)，或個別 .psd1 檔案中的變數。 若要在 .psd1 檔案中定義 **ConfigurationData**，請建立只包含代表設定資料之雜湊表的檔案。

例如，您可以建立具有下列內容的檔案，並命名為 `MyData.psd1`：

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        }

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

若要使用在 .psd1 檔案中定義的設定資料，您可以在編譯設定時，傳遞該檔案的路徑和名稱作為 **ConfigurationData** 參數值：

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>在設定中使用 ConfigurationData 變數

DSC 提供三種特殊變數，可用於設定指令碼中︰**$AllNodes**、**$Node** 和 **$ConfigurationData**。

- **$AllNodes** 代表 **ConfigurationData** 中所定義的整個節點集合。 您可以使用 **.Where()** 和 **.ForEach()** 篩選 **AllNodes** 集合。
- **Node** 代表 **AllNodes** 集合使用 **.Where()** 或 **.ForEach()** 篩選後所包含的特定項目。
- **ConfigurationData** 代表編譯設定時，當做參數傳遞的整個雜湊表。

## <a name="devops-example"></a>DevOps 範例

讓我們看看一個完整的範例，該範例使用單一設定來設定網站的開發和生產環境。 在開發環境中，IIS 和 SQL Server 會安裝在單一節點上。 在生產環境中，IIS 和 SQL Server 會安裝在不同的節點上。 我們將使用設定資料檔案 .psd1，來指定這兩個不同環境的資料。

### <a name="configuration-data-file"></a>設定資料檔案

我們將在名為 `DevProdEnvData.psd1` 的檔案中定義開發和生產環境資料，如下所示：

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
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
        }

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"

        }

    )

}

    )

}
```

### <a name="configuration-file"></a>設定檔案

現在，在設定中，我們將依節點的角色 (`MSSQL`、`Dev` 或兩者)，來篩選 `DevProdEnvData.psd1` 中所定義的節點，並據此進行設定。 開發環境會將 SQL Server 和 IIS 放在一個節點上，而生產環境則會將這兩者放在兩個不同的節點上。 網站內容也會依照 `SiteContents` 屬性的指定而有所不同。

在設定指令碼結尾處，我們會呼叫設定 (將其編譯為 MOF 文件)，並傳遞 `DevProdEnvData.psd1` 作為 `$ConfigurationData` 參數。

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.Nodename
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

   Node $AllNodes.Where($_.Role -contains "Web")
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
            Name            = $WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

## <a name="see-also"></a>另請參閱
- [設定資料的認證選項](configDataCredentials.md)
- [DSC 設定](configurations.md)