---
ms.date: 12/12/2018
keywords: dsc，powershell，設定、 服務、 安裝程式
title: 撰寫、編譯及套用設定
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400663"
---
> <span data-ttu-id="e8a7b-103">適用於：Windows PowerShell 4.0 中，Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e8a7b-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="e8a7b-104">撰寫、編譯及套用設定</span><span class="sxs-lookup"><span data-stu-id="e8a7b-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="e8a7b-105">這個練習會從頭開始完整地逐步建立並套用預期狀態設定 (DSC)。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="e8a7b-106">在下列範例中，您將學習如何撰寫及套用非常簡單的組態。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="e8a7b-107">組態可確保 「 HelloWorld.txt"檔案存在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="e8a7b-108">如果您刪除檔案時，DSC 會重新建立它便會更新下一次。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="e8a7b-109">如需 DSC 的功能及其運作方式的概觀，請參閱 <<c0> [ 適用於開發人員 Desired State Configuration 概觀](../overview/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="e8a7b-110">需求</span><span class="sxs-lookup"><span data-stu-id="e8a7b-110">Requirements</span></span>

<span data-ttu-id="e8a7b-111">若要執行此範例中，您必須執行 PowerShell 4.0 或更新版本的電腦。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="e8a7b-112">撰寫設定</span><span class="sxs-lookup"><span data-stu-id="e8a7b-112">Write the configuration</span></span>

<span data-ttu-id="e8a7b-113">DSC [設定](configurations.md)是特殊的 PowerShell 函式，可定義您想設定一或多個目標電腦 (節點) 的方式。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="e8a7b-114">在 PowerShell ISE 中或其他 PowerShell 編輯器中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="e8a7b-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

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

<span data-ttu-id="e8a7b-115">將檔案儲存為"HelloWorld.ps1 」 中。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="e8a7b-116">定義組態，就像定義的函式。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="e8a7b-117">**Node** 區塊會指定要設定的目標節點，在本範例中為 `localhost`。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="e8a7b-118">此設定會呼叫其中一個[資源](../resources/resources.md)，則`File`資源。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="e8a7b-119">資源會確保目標節點處於設定所定義的狀態。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="e8a7b-120">編譯設定</span><span class="sxs-lookup"><span data-stu-id="e8a7b-120">Compile the configuration</span></span>

<span data-ttu-id="e8a7b-121">DSC 設定若要套用至節點，便必須先編譯成 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="e8a7b-122">執行設定，例如函式，將會編譯一個 「.mof"檔案所定義的每個節點的`Node`區塊。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="e8a7b-123">若要執行設定時，您必須*點溯源*"HelloWorld.ps1 」 指令碼到目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="e8a7b-124">如需詳細資訊，請參閱 < [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing)。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<span data-ttu-id="e8a7b-125">*點溯源*"HelloWorld.ps1 」 指令碼中您儲存的路徑之後, 輸入`. `（點、 空格）。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="e8a7b-126">然後，您可能會藉由呼叫例如函式中執行您的設定。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-126">You may then, run your configuration by calling it like a Function.</span></span>

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

<span data-ttu-id="e8a7b-127">這會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e8a7b-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="e8a7b-128">套用設定</span><span class="sxs-lookup"><span data-stu-id="e8a7b-128">Apply the configuration</span></span>

<span data-ttu-id="e8a7b-129">現在您已經有已編譯的 MOF，您接著可呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 來將設定套用至目標節點 (在本範例中為本機電腦)。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="e8a7b-130">`Start-DscConfiguration` Cmdlet 會告知[本機設定管理員 (LCM)](../managing-nodes/metaConfig.md)，DSC，以套用組態的引擎。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="e8a7b-131">LCM 會呼叫 DSC 資源以套用設定。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="e8a7b-132">使用下列程式碼來執行`Start-DSCConfiguration`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="e8a7b-133">指定的目錄路徑來儲存您 「 localhost.mof"`-Path`參數。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="e8a7b-134">`Start-DSCConfiguration`指令程式會透過任何指定的目錄"\<computername\>.mof 」 檔案。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="e8a7b-135">`Start-DSCConfiguration`指令程式會嘗試將每個找到的".mof"檔案套用到檔案名稱 （"localhost"、"server01"、"dc-02"等等） 所指定電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="e8a7b-136">如果`-Wait`未指定參數，`Start-DSCConfiguration`建立背景工作來執行作業。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="e8a7b-137">指定`-Verbose`參數可讓您監看**Verbose**作業的輸出。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="e8a7b-138">`-Wait`與`-Verbose`是這兩個選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="e8a7b-139">測試組態</span><span class="sxs-lookup"><span data-stu-id="e8a7b-139">Test the configuration</span></span>

<span data-ttu-id="e8a7b-140">一次`Start-DSCConfiguration`cmdlet 完成時，您應該會看到您所指定的位置中的 「 HelloWorld.txt"檔案。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="e8a7b-141">您可以確認與內容[Get-content](/powershell/module/microsoft.powershell.management/get-content) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="e8a7b-142">您也可以*測試*目前的狀態使用[Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="e8a7b-143">如果節點是目前符合套用的設定，輸出應該是"True"。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

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

## <a name="re-applying-the-configuration"></a><span data-ttu-id="e8a7b-144">重新套用組態</span><span class="sxs-lookup"><span data-stu-id="e8a7b-144">Re-applying the configuration</span></span>

<span data-ttu-id="e8a7b-145">若要查看您一次套用的設定，您可以移除您組態所建立的文字檔。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="e8a7b-146">使用`Start-DSCConfiguration`cmdlet 搭配`-UseExisting`參數。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="e8a7b-147">`-UseExisting`參數會指示`Start-DSCConfiguration`來重新套用 「 current.mof"檔案，表示最近成功套用設定。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="e8a7b-148">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="e8a7b-148">Next steps</span></span>

- <span data-ttu-id="e8a7b-149">在 [DSC 設定](configurations.md)中深入了解 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="e8a7b-150">在 [DSC 資源](../resources/resources.md)中查看可用的 DSC 資源，以及如何建立自訂 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="e8a7b-151">在 [PowerShell 資源庫 (英文)](https://www.powershellgallery.com/) 中尋找 DSC 設定和資源。</span><span class="sxs-lookup"><span data-stu-id="e8a7b-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
