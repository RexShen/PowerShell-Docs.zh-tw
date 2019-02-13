---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 快速入門-使用 DSC 建立網站
ms.openlocfilehash: c62e2d8af46bf74c4dd13069ddff6cc39763a209
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676604"
---
> <span data-ttu-id="08979-103">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="08979-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart---create-a-website-with-dsc"></a><span data-ttu-id="08979-104">快速入門-使用 DSC 建立網站</span><span class="sxs-lookup"><span data-stu-id="08979-104">Quickstart - Create a website with DSC</span></span>

<span data-ttu-id="08979-105">這個練習會從頭開始完整地逐步建立並套用預期狀態設定 (DSC)。</span><span class="sxs-lookup"><span data-stu-id="08979-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="08979-106">我們將使用的範例會確保伺服器已啟用 `Web-Server` (IIS) 功能，且在該伺服器的 `intepub\wwwroot` 目錄中有簡單 "Hello World" 網站的內容。</span><span class="sxs-lookup"><span data-stu-id="08979-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `intepub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="08979-107">如需 DSC 及其運作方式的概觀，請參閱[適合決策者的預期狀態設定概觀](../overview/decisionMaker.md)。</span><span class="sxs-lookup"><span data-stu-id="08979-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="08979-108">需求</span><span class="sxs-lookup"><span data-stu-id="08979-108">Requirements</span></span>

<span data-ttu-id="08979-109">若要執行此範例，您將需要執行 Windows Server 2012 或更新版本的電腦，以及 PowerShell 4.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="08979-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="08979-110">撰寫並放置 index.htm 檔案</span><span class="sxs-lookup"><span data-stu-id="08979-110">Write and place the index.htm file</span></span>

<span data-ttu-id="08979-111">首先，我們會建立 HTML 檔案，將它用來做為網站內容。</span><span class="sxs-lookup"><span data-stu-id="08979-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="08979-112">在您的根資料夾中，建立名為 `test` 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="08979-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="08979-113">在文字編輯器中，輸入下列文字：</span><span class="sxs-lookup"><span data-stu-id="08979-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="08979-114">將此內容在您稍早建立的 `test` 資料夾中另存為 `index.htm`。</span><span class="sxs-lookup"><span data-stu-id="08979-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="08979-115">撰寫設定</span><span class="sxs-lookup"><span data-stu-id="08979-115">Write the configuration</span></span>

<span data-ttu-id="08979-116">[DSC 設定](../configurations/configurations.md)是特殊的 PowerShell 函式，可定義您想要設定一或多部目標電腦 (節點) 的方式。</span><span class="sxs-lookup"><span data-stu-id="08979-116">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="08979-117">在 PowerShell ISE 中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="08979-117">In the PowerShell ISE, type the following:</span></span>

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

<span data-ttu-id="08979-118">將檔案儲存為 `WebsiteTest.ps1`。</span><span class="sxs-lookup"><span data-stu-id="08979-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="08979-119">您可以看到它看起來像是 PowerShell 函式，並在函式名稱前使用額外的關鍵字 **Configuration**。</span><span class="sxs-lookup"><span data-stu-id="08979-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="08979-120">**Node** 區塊會指定要設定的目標節點，在本範例中為 `localhost`。</span><span class="sxs-lookup"><span data-stu-id="08979-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="08979-121">設定會呼叫兩個[資源](../resources/resources.md)，**WindowsFeature** 和 **File**。</span><span class="sxs-lookup"><span data-stu-id="08979-121">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File**.</span></span>
<span data-ttu-id="08979-122">資源會確保目標節點處於設定所定義的狀態。</span><span class="sxs-lookup"><span data-stu-id="08979-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="08979-123">編譯設定</span><span class="sxs-lookup"><span data-stu-id="08979-123">Compile the configuration</span></span>

<span data-ttu-id="08979-124">DSC 設定若要套用至節點，便必須先編譯成 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="08979-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="08979-125">若要這麼做，您要如函式一般執行設定。</span><span class="sxs-lookup"><span data-stu-id="08979-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="08979-126">在 PowerShell 主控台中，瀏覽至您儲存設定的同一個資料夾，並執行下列命令以將設定編譯成 MOF 檔案：</span><span class="sxs-lookup"><span data-stu-id="08979-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="08979-127">這會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="08979-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="08979-128">第一行會使設定函式可在主控台中使用。</span><span class="sxs-lookup"><span data-stu-id="08979-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="08979-129">第二行會執行設定。</span><span class="sxs-lookup"><span data-stu-id="08979-129">The second line runs the configuration.</span></span>
<span data-ttu-id="08979-130">結果會在目前資料夾中，建立名為 `WebsiteTest` 的新子資料夾。</span><span class="sxs-lookup"><span data-stu-id="08979-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="08979-131">`WebsiteTest` 資料夾包含名稱為 `localhost.mof` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="08979-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="08979-132">此檔案即為可套用至目標節點的檔案。</span><span class="sxs-lookup"><span data-stu-id="08979-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="08979-133">套用設定</span><span class="sxs-lookup"><span data-stu-id="08979-133">Apply the configuration</span></span>

<span data-ttu-id="08979-134">現在您已經有已編譯的 MOF，您接著可呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 來將設定套用至目標節點 (在本範例中為本機電腦)。</span><span class="sxs-lookup"><span data-stu-id="08979-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="08979-135">`Start-DscConfiguration` Cmdlet 會要求[本機設定管理員 (LCM)](../managing-nodes/metaConfig.md) (也就是 DSC 的引擎) 套用設定。</span><span class="sxs-lookup"><span data-stu-id="08979-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="08979-136">LCM 會呼叫 DSC 資源以套用設定。</span><span class="sxs-lookup"><span data-stu-id="08979-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="08979-137">在 PowerShell 主控台中，瀏覽至您儲存設定的同一個資料夾，並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="08979-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="08979-138">測試組態</span><span class="sxs-lookup"><span data-stu-id="08979-138">Test the configuration</span></span>

<span data-ttu-id="08979-139">您可以呼叫 [Get DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) Cmdlet 來查看設定是否成功。</span><span class="sxs-lookup"><span data-stu-id="08979-139">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="08979-140">您也可以直接測試結果，在本範例中是透過網頁瀏覽器瀏覽至 `http://localhost/`。</span><span class="sxs-lookup"><span data-stu-id="08979-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="08979-141">您應該會看到您做為本範例的第一個步驟所建立的 "Hello World" HTML 頁面。</span><span class="sxs-lookup"><span data-stu-id="08979-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="08979-142">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="08979-142">Next steps</span></span>

- <span data-ttu-id="08979-143">在 [DSC 設定](../configurations/configurations.md)中深入了解 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="08979-143">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="08979-144">在 [DSC 資源](../resources/resources.md)中查看可用的 DSC 資源，以及如何建立自訂 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="08979-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="08979-145">在 [PowerShell 資源庫 (英文)](https://www.powershellgallery.com/) 中尋找 DSC 設定和資源。</span><span class="sxs-lookup"><span data-stu-id="08979-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
