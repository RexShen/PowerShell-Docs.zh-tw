---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 快速入門 - 使用 DSC 建立網站
description: 此快速入門說明如何使用 DSC 設定建立新網站。
ms.openlocfilehash: ece1ae964bce00a4102de4b13d99d6ee1259117a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650902"
---
# <a name="quickstart---create-a-website-with-desired-state-configuration-dsc"></a><span data-ttu-id="f4db6-104">快速入門 - 使用 Desired State Configuration (DSC) 來建立網站</span><span class="sxs-lookup"><span data-stu-id="f4db6-104">Quickstart - Create a website with Desired State Configuration (DSC)</span></span>

> <span data-ttu-id="f4db6-105">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f4db6-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f4db6-106">這個練習會從頭開始完整地逐步建立並套用預期狀態設定 (DSC)。</span><span class="sxs-lookup"><span data-stu-id="f4db6-106">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span> <span data-ttu-id="f4db6-107">我們將使用的範例會確保伺服器已啟用 `Web-Server` (IIS) 功能，且在該伺服器的 `inetpub\wwwroot` 目錄中有簡單 "Hello World" 網站的內容。</span><span class="sxs-lookup"><span data-stu-id="f4db6-107">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `inetpub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="f4db6-108">如需 DSC 及其運作方式的概觀，請參閱[適合決策者的預期狀態設定概觀](../overview/decisionMaker.md)。</span><span class="sxs-lookup"><span data-stu-id="f4db6-108">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="f4db6-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="f4db6-109">Requirements</span></span>

<span data-ttu-id="f4db6-110">若要執行此範例，您將需要執行 Windows Server 2012 或更新版本的電腦，以及 PowerShell 4.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="f4db6-110">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="f4db6-111">撰寫並放置 index.htm 檔案</span><span class="sxs-lookup"><span data-stu-id="f4db6-111">Write and place the index.htm file</span></span>

<span data-ttu-id="f4db6-112">首先，我們會建立 HTML 檔案，將它用來做為網站內容。</span><span class="sxs-lookup"><span data-stu-id="f4db6-112">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="f4db6-113">在您的根資料夾中，建立名為 `test` 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f4db6-113">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="f4db6-114">在文字編輯器中，輸入下列文字：</span><span class="sxs-lookup"><span data-stu-id="f4db6-114">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="f4db6-115">將此內容在您稍早建立的 `test` 資料夾中另存為 `index.htm`。</span><span class="sxs-lookup"><span data-stu-id="f4db6-115">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="f4db6-116">撰寫設定</span><span class="sxs-lookup"><span data-stu-id="f4db6-116">Write the configuration</span></span>

<span data-ttu-id="f4db6-117">[DSC 設定](../configurations/configurations.md)是特殊的 PowerShell 函式，可定義您想要設定一或多部目標電腦 (節點) 的方式。</span><span class="sxs-lookup"><span data-stu-id="f4db6-117">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="f4db6-118">在 PowerShell ISE 中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="f4db6-118">In the PowerShell ISE, type the following:</span></span>

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

<span data-ttu-id="f4db6-119">將檔案儲存為 `WebsiteTest.ps1`。</span><span class="sxs-lookup"><span data-stu-id="f4db6-119">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="f4db6-120">您可以看到它看起來像是 PowerShell 函式，並在函式名稱前使用額外的關鍵字 **Configuration** 。</span><span class="sxs-lookup"><span data-stu-id="f4db6-120">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="f4db6-121">**Node** 區塊會指定要設定的目標節點。</span><span class="sxs-lookup"><span data-stu-id="f4db6-121">The **Node** block specifies the target node to be configured.</span></span> <span data-ttu-id="f4db6-122">在此案例中為 `localhost`。</span><span class="sxs-lookup"><span data-stu-id="f4db6-122">In this case, `localhost`.</span></span>

<span data-ttu-id="f4db6-123">設定會呼叫兩個 [資源](../resources/resources.md)， **WindowsFeature** 和 **File** 。</span><span class="sxs-lookup"><span data-stu-id="f4db6-123">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File**.</span></span>
<span data-ttu-id="f4db6-124">資源會確保目標節點處於設定所定義的狀態。</span><span class="sxs-lookup"><span data-stu-id="f4db6-124">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="f4db6-125">編譯設定</span><span class="sxs-lookup"><span data-stu-id="f4db6-125">Compile the configuration</span></span>

<span data-ttu-id="f4db6-126">DSC 設定若要套用至節點，便必須先編譯成 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="f4db6-126">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span> <span data-ttu-id="f4db6-127">若要這麼做，您要如函式一般執行設定。</span><span class="sxs-lookup"><span data-stu-id="f4db6-127">To do this, you run the configuration like a function.</span></span> <span data-ttu-id="f4db6-128">在 PowerShell 主控台中，瀏覽至您儲存設定的同一個資料夾，並執行下列命令以將設定編譯成 MOF 檔案：</span><span class="sxs-lookup"><span data-stu-id="f4db6-128">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="f4db6-129">這會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f4db6-129">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="f4db6-130">第一行會使設定函式可在主控台中使用。</span><span class="sxs-lookup"><span data-stu-id="f4db6-130">The first line makes the configuration function available in the console.</span></span> <span data-ttu-id="f4db6-131">第二行會執行設定。</span><span class="sxs-lookup"><span data-stu-id="f4db6-131">The second line runs the configuration.</span></span> <span data-ttu-id="f4db6-132">結果會在目前資料夾中，建立名為 `WebsiteTest` 的新子資料夾。</span><span class="sxs-lookup"><span data-stu-id="f4db6-132">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span> <span data-ttu-id="f4db6-133">`WebsiteTest` 資料夾包含名稱為 `localhost.mof` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="f4db6-133">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span> <span data-ttu-id="f4db6-134">這是可接著套用至目標節點的檔案。</span><span class="sxs-lookup"><span data-stu-id="f4db6-134">This is the file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="f4db6-135">套用設定</span><span class="sxs-lookup"><span data-stu-id="f4db6-135">Apply the configuration</span></span>

<span data-ttu-id="f4db6-136">現在您已經有已編譯的 MOF，您接著可呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 來將設定套用至目標節點 (在本範例中為本機電腦)。</span><span class="sxs-lookup"><span data-stu-id="f4db6-136">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="f4db6-137">`Start-DscConfiguration` Cmdlet 會要求[本機設定管理員 (LCM)](../managing-nodes/metaConfig.md) (也就是 DSC 的引擎) 套用設定。</span><span class="sxs-lookup"><span data-stu-id="f4db6-137">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span> <span data-ttu-id="f4db6-138">LCM 會呼叫 DSC 資源以套用設定。</span><span class="sxs-lookup"><span data-stu-id="f4db6-138">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="f4db6-139">若要允許 DSC 執行，就必須將 Windows 設定成即使在您執行 `localhost` 設定時，也接收 PowerShell 遠端命令。</span><span class="sxs-lookup"><span data-stu-id="f4db6-139">To allow DSC to run, Windows needs to be configured to receive PowerShell remote commands, even when you're running a `localhost` configuration.</span></span> <span data-ttu-id="f4db6-140">若要輕鬆正確地設定您的環境，只要在已提高權限的 PowerShell 終端機中執行 `Set-WsManQuickConfig -Force` 即可。</span><span class="sxs-lookup"><span data-stu-id="f4db6-140">To easily configure your environment correctly, just run `Set-WsManQuickConfig -Force` in an elevated PowerShell Terminal.</span></span>

<span data-ttu-id="f4db6-141">在 PowerShell 主控台中，瀏覽至您儲存設定的同一個資料夾，並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="f4db6-141">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="f4db6-142">測試組態</span><span class="sxs-lookup"><span data-stu-id="f4db6-142">Test the configuration</span></span>

<span data-ttu-id="f4db6-143">您可以呼叫 [Get DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) Cmdlet 來查看設定是否成功。</span><span class="sxs-lookup"><span data-stu-id="f4db6-143">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="f4db6-144">您也可以直接測試結果，在本範例中是透過網頁瀏覽器瀏覽至 `http://localhost/`。</span><span class="sxs-lookup"><span data-stu-id="f4db6-144">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span> <span data-ttu-id="f4db6-145">您應該會看到您做為本範例的第一個步驟所建立的 "Hello World" HTML 頁面。</span><span class="sxs-lookup"><span data-stu-id="f4db6-145">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f4db6-146">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f4db6-146">Next steps</span></span>

- <span data-ttu-id="f4db6-147">在 [DSC 設定](../configurations/configurations.md)中深入了解 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="f4db6-147">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="f4db6-148">在 [DSC 資源](../resources/resources.md)中查看可用的 DSC 資源，以及如何建立自訂 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="f4db6-148">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="f4db6-149">在 [PowerShell 資源庫 (英文)](https://www.powershellgallery.com/) 中尋找 DSC 設定和資源。</span><span class="sxs-lookup"><span data-stu-id="f4db6-149">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
