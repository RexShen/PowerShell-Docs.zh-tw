---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "分離設定和環境資料"
ms.openlocfilehash: df3cfea08419c37716b408fdbd6b43e78be2331c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="8292a-103">分離設定和環境資料</span><span class="sxs-lookup"><span data-stu-id="8292a-103">Separating configuration and environment data</span></span>

><span data-ttu-id="8292a-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8292a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="8292a-105">使用設定資料來分離 DSC 設定中所用資料與設定本身，是非常實用的。</span><span class="sxs-lookup"><span data-stu-id="8292a-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="8292a-106">藉由執行此動作，您就能針對多個環境使用單一設定。</span><span class="sxs-lookup"><span data-stu-id="8292a-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="8292a-107">例如，如果您要開發應用程式，您可以針對開發和生產環境使用一個設定，並使用設定資料來指定每個環境的資料。</span><span class="sxs-lookup"><span data-stu-id="8292a-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="8292a-108">何謂設定資料？</span><span class="sxs-lookup"><span data-stu-id="8292a-108">What is configuration data?</span></span>

<span data-ttu-id="8292a-109">設定資料是當您編譯 DSC 設定時，定義於雜湊表中並傳遞至該設定的資料。</span><span class="sxs-lookup"><span data-stu-id="8292a-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="8292a-110">如需 **ConfigurationData** 雜湊表的詳細描述，請參閱[使用設定資料](configData.md)。</span><span class="sxs-lookup"><span data-stu-id="8292a-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="8292a-111">一個簡單的範例</span><span class="sxs-lookup"><span data-stu-id="8292a-111">A simple example</span></span>

<span data-ttu-id="8292a-112">讓我們看看一個非常簡單的範例，以了解其運作方式。</span><span class="sxs-lookup"><span data-stu-id="8292a-112">Let's look at a very simple example to see how this works.</span></span> <span data-ttu-id="8292a-113">我們將建立單一設定，確保 **IIS** 位於一些節點上，而 **HYPER-V** 位於另一些節點上：</span><span class="sxs-lookup"><span data-stu-id="8292a-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span> 

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

<span data-ttu-id="8292a-114">此指令碼的最後一行會編譯設定，並傳遞 `$MyData` 作為 **ConfigurationData** 參數值。</span><span class="sxs-lookup"><span data-stu-id="8292a-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="8292a-115">結果會建立兩個 MOF 檔案：</span><span class="sxs-lookup"><span data-stu-id="8292a-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:09 PM           1968 VM-1.mof                                                                                                                
-a----        3/31/2017   5:09 PM           1970 VM-2.mof  
```
 
<span data-ttu-id="8292a-116">`$MyData` 指定兩個不同的節點，各有其專屬的 `NodeName` 和 `Role`。</span><span class="sxs-lookup"><span data-stu-id="8292a-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="8292a-117">此設定會從 `$MyData` 取得節點集合 (亦即 `$AllNodes`)，然後針對 `Role` 屬性篩選該集合，藉此以動態方式建立 **Node** 區塊。</span><span class="sxs-lookup"><span data-stu-id="8292a-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="8292a-118">使用設定資料定義開發和生產環境</span><span class="sxs-lookup"><span data-stu-id="8292a-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="8292a-119">讓我們看看一個完整的範例，該範例使用單一設定來設定網站的開發和生產環境。</span><span class="sxs-lookup"><span data-stu-id="8292a-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="8292a-120">在開發環境中，IIS 和 SQL Server 會安裝在單一節點上。</span><span class="sxs-lookup"><span data-stu-id="8292a-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="8292a-121">在生產環境中，IIS 和 SQL Server 會安裝在不同的節點上。</span><span class="sxs-lookup"><span data-stu-id="8292a-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="8292a-122">我們將使用設定資料檔案 .psd1，來指定這兩個不同環境的資料。</span><span class="sxs-lookup"><span data-stu-id="8292a-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

 ### <a name="configuration-data-file"></a><span data-ttu-id="8292a-123">設定資料檔案</span><span class="sxs-lookup"><span data-stu-id="8292a-123">Configuration data file</span></span>

<span data-ttu-id="8292a-124">我們將在名為 `DevProdEnvData.psd1` 的檔案中定義開發和生產環境資料，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8292a-124">We'll define the development and production environment data in a file namd `DevProdEnvData.psd1` as follows:</span></span>

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

### <a name="configuration-script-file"></a><span data-ttu-id="8292a-125">設定指令檔</span><span class="sxs-lookup"><span data-stu-id="8292a-125">Configuration script file</span></span>

<span data-ttu-id="8292a-126">現在，在定義於 `.ps1` 檔案的設定中，我們會依其角色 (`MSSQL`、`Dev` 或兩者) 來篩選 `DevProdEnvData.psd1` 中所定義的節點，並據此加以設定。</span><span class="sxs-lookup"><span data-stu-id="8292a-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span> <span data-ttu-id="8292a-127">開發環境會將 SQL Server 和 IIS 放在一個節點上，而生產環境則會將這兩者放在兩個不同的節點上。</span><span class="sxs-lookup"><span data-stu-id="8292a-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span> <span data-ttu-id="8292a-128">網站內容也會依照 `SiteContents` 屬性的指定而有所不同。</span><span class="sxs-lookup"><span data-stu-id="8292a-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="8292a-129">在設定指令碼結尾處，我們會呼叫設定 (將其編譯為 MOF 文件)，並傳遞 `DevProdEnvData.psd1` 作為 `$ConfigurationData` 參數。</span><span class="sxs-lookup"><span data-stu-id="8292a-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="8292a-130">**注意︰**這項設定要求在目標節點上安裝模組 `xSqlPs` 和 `xWebAdministration`。</span><span class="sxs-lookup"><span data-stu-id="8292a-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="8292a-131">讓我們在名為 `MyWebApp.ps1` 的檔案中定義設定：</span><span class="sxs-lookup"><span data-stu-id="8292a-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

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
            Name            = $WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

<span data-ttu-id="8292a-132">當您執行此設定時，會建立三個 MOF 檔案 (在 **AllNodes** 陣列中針對每個具名項目各建立一個)：</span><span class="sxs-lookup"><span data-stu-id="8292a-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof                                                                                                            
-a----        3/31/2017   5:47 PM           6994 Dev.mof                                                                                                                 
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="8292a-133">使用非節點資料</span><span class="sxs-lookup"><span data-stu-id="8292a-133">Using non-node data</span></span>

<span data-ttu-id="8292a-134">您可以將額外的索引鍵加入 **ConfigurationData** 雜湊表，以供非節點專屬的資料使用。</span><span class="sxs-lookup"><span data-stu-id="8292a-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="8292a-135">下列設定確保會存在兩個網站。</span><span class="sxs-lookup"><span data-stu-id="8292a-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="8292a-136">每個網站的資料均定義於 **AllNodes** 陣列中。</span><span class="sxs-lookup"><span data-stu-id="8292a-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="8292a-137">檔案 `Config.xml` 要供這兩個網站使用，因此，我們將它定義於名為 `NonNodeData` 的額外索引鍵中。</span><span class="sxs-lookup"><span data-stu-id="8292a-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="8292a-138">請注意，您可以視需要定義任意多個額外的索引鍵，且可隨意命名。</span><span class="sxs-lookup"><span data-stu-id="8292a-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="8292a-139">`NonNodeData` 不是保留字，它只是我們決定來為額外索引鍵命名的名稱。</span><span class="sxs-lookup"><span data-stu-id="8292a-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="8292a-140">您可以使用特殊變數 **$ConfigurationData** 來存取額外的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8292a-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="8292a-141">在此範例中，會使用下列程式碼行來存取 `ConfigFileContents`：</span><span class="sxs-lookup"><span data-stu-id="8292a-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="8292a-142">在 `File` 資源區塊中。</span><span class="sxs-lookup"><span data-stu-id="8292a-142">in the `File` resource block.</span></span>


```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
        },
 
        @{
            NodeName = “VM-1”
            SiteContents = “C:\Site1”
            SiteName = “Website1”
        },
 
        
        @{
            NodeName = “VM-2”;
            SiteContents = “C:\Site2”
            SiteName = “Website2”
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
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
        }
 
        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + “\\config.xml”
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
} 
```


## <a name="see-also"></a><span data-ttu-id="8292a-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8292a-143">See Also</span></span>
- [<span data-ttu-id="8292a-144">使用設定資料</span><span class="sxs-lookup"><span data-stu-id="8292a-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="8292a-145">設定資料的認證選項</span><span class="sxs-lookup"><span data-stu-id="8292a-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="8292a-146">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="8292a-146">DSC Configurations</span></span>](configurations.md)
