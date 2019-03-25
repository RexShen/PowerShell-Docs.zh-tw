---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,服務,安裝
title: 撰寫、編譯及套用設定
ms.openlocfilehash: c884af9d92ac375457d6eb75d815ae9a9159e273
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795414"
---
> <span data-ttu-id="b3ef1-103">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b3ef1-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="b3ef1-104">撰寫、編譯及套用設定</span><span class="sxs-lookup"><span data-stu-id="b3ef1-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="b3ef1-105">這個練習會從頭開始完整地逐步建立並套用預期狀態設定 (DSC)。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="b3ef1-106">在下列範例中，您會了解如何撰寫及套用非常簡單的設定。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="b3ef1-107">此設定會確保本機電腦上有 "HelloWorld.txt" 檔案。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="b3ef1-108">如果您刪除此檔案，DSC 會在下次更新時重新建立它。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="b3ef1-109">如需了解 DSC 及其運作方式的概觀，請參閱[開發人員適用的預期狀態設定概觀](../overview/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b3ef1-110">需求</span><span class="sxs-lookup"><span data-stu-id="b3ef1-110">Requirements</span></span>

<span data-ttu-id="b3ef1-111">若要執行此範例，您需要執行 PowerShell 4.0 或更新版本的電腦。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="b3ef1-112">撰寫設定</span><span class="sxs-lookup"><span data-stu-id="b3ef1-112">Write the configuration</span></span>

<span data-ttu-id="b3ef1-113">DSC [設定](configurations.md)是特殊的 PowerShell 函式，可定義您想設定一或多個目標電腦 (節點) 的方式。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="b3ef1-114">在 PowerShell ISE 或其他 PowerShell 編輯器中，鍵入下列命令：</span><span class="sxs-lookup"><span data-stu-id="b3ef1-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

<span data-ttu-id="b3ef1-115">將檔案另存為 "HelloWorld.ps1"。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="b3ef1-116">定義設定如同定義函式。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="b3ef1-117">**Node** 區塊會指定要設定的目標節點，在本範例中為 `localhost`。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="b3ef1-118">此設定會呼叫一項[資源](../resources/resources.md)，即 `File` 資源。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="b3ef1-119">資源會確保目標節點處於設定所定義的狀態。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="b3ef1-120">編譯設定</span><span class="sxs-lookup"><span data-stu-id="b3ef1-120">Compile the configuration</span></span>

<span data-ttu-id="b3ef1-121">DSC 設定若要套用至節點，便必須先編譯成 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="b3ef1-122">執行設定 (例如函式)，會針對 `Node` 區塊定義的每個節點編譯一個 ".mof" 檔案。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="b3ef1-123">為執行此設定，您需要「點溯源」"HelloWorld.ps1" 指令碼到目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="b3ef1-124">如需詳細資訊，請參閱 [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing)。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<span data-ttu-id="b3ef1-125"><!-- markdownlint-disable MD038 -->
在 `. ` (點、空格) 後鍵入儲存路徑，即可「點溯源」"HelloWorld.ps1" 指令碼。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-125"><!-- markdownlint-disable MD038 -->
*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="b3ef1-126">然後，您就可以像呼叫函式一樣呼叫它來執行您的設定。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-126">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

<span data-ttu-id="b3ef1-127">這會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b3ef1-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="b3ef1-128">套用設定</span><span class="sxs-lookup"><span data-stu-id="b3ef1-128">Apply the configuration</span></span>

<span data-ttu-id="b3ef1-129">現在您已經有已編譯的 MOF，您接著可呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 來將設定套用至目標節點 (在本範例中為本機電腦)。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="b3ef1-130">`Start-DscConfiguration` Cmdlet 會要求[本機設定管理員 (LCM)](../managing-nodes/metaConfig.md) (即 DSC 的引擎) 套用設定。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="b3ef1-131">LCM 會呼叫 DSC 資源以套用設定。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="b3ef1-132">使用下列程式碼執行 `Start-DSCConfiguration` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="b3ef1-133">將您儲存 "localhost.mof" 的目錄路徑指定給 `-Path` 參數。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="b3ef1-134">`Start-DSCConfiguration` Cmdlet 會查看是否有針對任何 "\<電腦名稱\>.mof" 檔案指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="b3ef1-135">`Start-DSCConfiguration` Cmdlet 會嘗試將它所找到每個 ".mof" 檔案套用到檔案名稱 ("localhost"、"server01"、"dc-02" 等等) 指定的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="b3ef1-136">如未指定 `-Wait` 參數，`Start-DSCConfiguration` 就會建立背景作業來執行作業。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="b3ef1-137">指定 `-Verbose` 參數可讓您監看作業的**詳細資訊**輸出。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="b3ef1-138">`-Wait` 和 `-Verbose` 都是選用參數。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="b3ef1-139">測試組態</span><span class="sxs-lookup"><span data-stu-id="b3ef1-139">Test the configuration</span></span>

<span data-ttu-id="b3ef1-140">`Start-DSCConfiguration` Cmdlet 完成後，您應該會在指定的位置看到 "HelloWorld.txt" 檔案。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="b3ef1-141">您可以使用 [Get-Content](/powershell/module/microsoft.powershell.management/get-content) Cmdlet 驗證內容。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="b3ef1-142">您也可以使用 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)「測試」目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="b3ef1-143">如果節點目前與套用的設定相容，則輸出應為 "True"。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="b3ef1-144">重新套用設定</span><span class="sxs-lookup"><span data-stu-id="b3ef1-144">Re-applying the configuration</span></span>

<span data-ttu-id="b3ef1-145">若要查看再次套用設定，您可以移除由設定建立的文字檔。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="b3ef1-146">使用 `Start-DSCConfiguration` Cmdlet 搭配 `-UseExisting` 參數。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="b3ef1-147">`-UseExisting` 參數會指示 `Start-DSCConfiguration` 重新套用 "current.mof" 檔案，它代表最近成功套用的設定。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="b3ef1-148">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="b3ef1-148">Next steps</span></span>

- <span data-ttu-id="b3ef1-149">在 [DSC 設定](configurations.md)中深入了解 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="b3ef1-150">在 [DSC 資源](../resources/resources.md)中查看可用的 DSC 資源，以及如何建立自訂 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="b3ef1-151">在 [PowerShell 資源庫 (英文)](https://www.powershellgallery.com/) 中尋找 DSC 設定和資源。</span><span class="sxs-lookup"><span data-stu-id="b3ef1-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
