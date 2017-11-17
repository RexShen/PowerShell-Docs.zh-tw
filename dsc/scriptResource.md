---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC Script 資源"
ms.openlocfilehash: 81718de0b0c8463189e33e565dc9ff39692dbe8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-script-resource"></a><span data-ttu-id="1cffc-103">DSC Script 資源</span><span class="sxs-lookup"><span data-stu-id="1cffc-103">DSC Script Resource</span></span>

 
> <span data-ttu-id="1cffc-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1cffc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1cffc-105">Windows PowerShell 預期狀態設定 (DSC) 的 **Script** 資源提供了在目標節點執行 Windows PowerShell 指令碼區塊的機制。</span><span class="sxs-lookup"><span data-stu-id="1cffc-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="1cffc-106">`Script`資源有`GetScript`、`SetScript` 和`TestScript` 屬性。</span><span class="sxs-lookup"><span data-stu-id="1cffc-106">The `Script` resource has `GetScript`, `SetScript`, and `TestScript` properties.</span></span> <span data-ttu-id="1cffc-107">應該要對將會在每個目標節點上執行的指令碼區塊，設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="1cffc-107">These properties should be set to script blocks that will run on each target node.</span></span> 

<span data-ttu-id="1cffc-108">`GetScript` 指令碼區塊應該會傳回代表目前節點狀態的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="1cffc-108">The `GetScript` script block should return a hashtable representing the state of the current node.</span></span> <span data-ttu-id="1cffc-109">雜湊表必須只包含一個機碼 `Result`，且值必須是 `String` 類型。</span><span class="sxs-lookup"><span data-stu-id="1cffc-109">The hashtable must only contain one key `Result` and the value must be of type `String`.</span></span> <span data-ttu-id="1cffc-110">不需要傳回任何內容。</span><span class="sxs-lookup"><span data-stu-id="1cffc-110">It is not required to return anything.</span></span> <span data-ttu-id="1cffc-111">DSC 不會對此指令碼區塊的輸出進行任何動作。</span><span class="sxs-lookup"><span data-stu-id="1cffc-111">DSC doesn't do anything with the output of this script block.</span></span>

<span data-ttu-id="1cffc-112">`TestScript` 指令碼區塊必須判斷目前的節點是否需要修改。</span><span class="sxs-lookup"><span data-stu-id="1cffc-112">The `TestScript` script block should determine if the current node needs to be modified.</span></span> <span data-ttu-id="1cffc-113">若該節點處於最新的狀態，應傳回 `$true`。</span><span class="sxs-lookup"><span data-stu-id="1cffc-113">It should return `$true` if the node is up-to-date.</span></span> <span data-ttu-id="1cffc-114">若節點的設定已過期，應傳回 `$false`，並使用 `SetScript` 指令碼區塊進行更新。</span><span class="sxs-lookup"><span data-stu-id="1cffc-114">It should return `$false` if the node's configuration is out-of-date and should be updated by the `SetScript` script block.</span></span> <span data-ttu-id="1cffc-115">`TestScript` 指令碼區塊由 DSC 呼叫。</span><span class="sxs-lookup"><span data-stu-id="1cffc-115">The `TestScript` script block is called by DSC.</span></span>

<span data-ttu-id="1cffc-116">`SetScript` 指令碼區塊應修改該節點。</span><span class="sxs-lookup"><span data-stu-id="1cffc-116">The `SetScript` script block should modify the node.</span></span> <span data-ttu-id="1cffc-117">若 `TestScript` 區塊傳回 `$false`，會由 DSC 加以呼叫。</span><span class="sxs-lookup"><span data-stu-id="1cffc-117">It is called by DSC if the `TestScript` block return `$false`.</span></span>

<span data-ttu-id="1cffc-118">若您需要使用 `GetScript`、`TestScript` 或 `SetScript` 指令碼區塊中設定指令碼的變數，請使用 `$using:` 範圍 (請參閱下方範例)</span><span class="sxs-lookup"><span data-stu-id="1cffc-118">If you need to use variables from your configuration script in the `GetScript`, `TestScript`, or `SetScript` script blocks, use the `$using:` scope (see below for an example).</span></span>


## <a name="syntax"></a><span data-ttu-id="1cffc-119">語法</span><span class="sxs-lookup"><span data-stu-id="1cffc-119">Syntax</span></span>

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="1cffc-120">[內容]</span><span class="sxs-lookup"><span data-stu-id="1cffc-120">Properties</span></span>

|  <span data-ttu-id="1cffc-121">屬性</span><span class="sxs-lookup"><span data-stu-id="1cffc-121">Property</span></span>  |  <span data-ttu-id="1cffc-122">描述</span><span class="sxs-lookup"><span data-stu-id="1cffc-122">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="1cffc-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="1cffc-123">GetScript</span></span>| <span data-ttu-id="1cffc-124">提供叫用 [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) Cmdlet 時所執行的 Windows PowerShell 指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="1cffc-124">Provides a block of Windows PowerShell script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet.</span></span> <span data-ttu-id="1cffc-125">這個區塊必須傳回雜湊表。</span><span class="sxs-lookup"><span data-stu-id="1cffc-125">This block must return a hashtable.</span></span> <span data-ttu-id="1cffc-126">雜湊表必須只包含一個機碼 **Result**，且值必須是 **String** 類型。</span><span class="sxs-lookup"><span data-stu-id="1cffc-126">The hashtable must only contain one key **Result** and the value must be of type **String**.</span></span>| 
| <span data-ttu-id="1cffc-127">SetScript</span><span class="sxs-lookup"><span data-stu-id="1cffc-127">SetScript</span></span>| <span data-ttu-id="1cffc-128">提供 Windows PowerShell 指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="1cffc-128">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="1cffc-129">當您叫用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 時，**TestScript** 區塊會先執行。</span><span class="sxs-lookup"><span data-stu-id="1cffc-129">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** block runs first.</span></span> <span data-ttu-id="1cffc-130">如果 **TestScript** 區塊傳回 **$false**，則 **SetScript** 區塊就會執行。</span><span class="sxs-lookup"><span data-stu-id="1cffc-130">If the **TestScript** block returns **$false**, the **SetScript** block will run.</span></span> <span data-ttu-id="1cffc-131">如果 **TestScript** 區塊傳回 **$true**，則 **SetScript** 區塊就會執行。</span><span class="sxs-lookup"><span data-stu-id="1cffc-131">If the **TestScript** block returns **$true**, the **SetScript** block will not run.</span></span>| 
| <span data-ttu-id="1cffc-132">TestScript</span><span class="sxs-lookup"><span data-stu-id="1cffc-132">TestScript</span></span>| <span data-ttu-id="1cffc-133">提供 Windows PowerShell 指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="1cffc-133">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="1cffc-134">當您叫用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 時，這個區塊就會執行。</span><span class="sxs-lookup"><span data-stu-id="1cffc-134">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this block runs.</span></span> <span data-ttu-id="1cffc-135">如果傳回 **$false**，SetScript 區塊就會執行。</span><span class="sxs-lookup"><span data-stu-id="1cffc-135">If it returns **$false**, the SetScript block will run.</span></span> <span data-ttu-id="1cffc-136">如果傳回 **$true**，SetScript 區塊就不會執行。</span><span class="sxs-lookup"><span data-stu-id="1cffc-136">If it returns **$true**, the SetScript block will not run.</span></span> <span data-ttu-id="1cffc-137">**TestScript** 區塊也會在叫用 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) Cmdlet 時執行。</span><span class="sxs-lookup"><span data-stu-id="1cffc-137">The **TestScript** block also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="1cffc-138">不過，在此情況下，無論 TestScript 區塊傳回何值，**SetScript** 區塊都不會執行。</span><span class="sxs-lookup"><span data-stu-id="1cffc-138">However, in this case, the **SetScript** block will not run, no matter what value the TestScript block returns.</span></span> <span data-ttu-id="1cffc-139">如果實際的設定符合目前的預期狀態設定，則 **TestScript** 區塊必須傳回 True；如果不符合，則為 False。</span><span class="sxs-lookup"><span data-stu-id="1cffc-139">The **TestScript** block must return True if the actual configuration matches the current desired state configuration, and False if it does not match.</span></span> <span data-ttu-id="1cffc-140">(目前的預期狀態設定是上次使用 DSC 的節點上施行的設定)。</span><span class="sxs-lookup"><span data-stu-id="1cffc-140">(The current desired state configuration is the last configuration enacted on the node that is using DSC.)</span></span>| 
| <span data-ttu-id="1cffc-141">認證</span><span class="sxs-lookup"><span data-stu-id="1cffc-141">Credential</span></span>| <span data-ttu-id="1cffc-142">如果需要認證，表示執行這個指令碼所要使用的認證。</span><span class="sxs-lookup"><span data-stu-id="1cffc-142">Indicates the credentials to use for running this script, if credentials are required.</span></span>| 
| <span data-ttu-id="1cffc-143">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1cffc-143">DependsOn</span></span>| <span data-ttu-id="1cffc-144">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="1cffc-144">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1cffc-145">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="1cffc-145">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

## <a name="example-1"></a><span data-ttu-id="1cffc-146">範例 1</span><span class="sxs-lookup"><span data-stu-id="1cffc-146">Example 1</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript = 
        { 
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
    }
}
```

## <a name="example-2"></a><span data-ttu-id="1cffc-147">範例 2</span><span class="sxs-lookup"><span data-stu-id="1cffc-147">Example 2</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Version' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
            if( $state['Version'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Version'],$using:version)
                return $true
            }
            Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
            return $false
        }
        SetScript = { 
            $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        }
    }
}
```

<span data-ttu-id="1cffc-148">此資源正在將設定的版本寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="1cffc-148">This resource is writing the configuration's version to a text file.</span></span> <span data-ttu-id="1cffc-149">用戶端電腦上可以使用此版本，但在其餘節點則無法使用，所以必須以 PowerShell 的 `using` 範圍，將其傳遞至各個 `Script` 資源的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="1cffc-149">This version is available on the client computer, but isn't on any of the nodes, so it has to be passed to each of the `Script` resource's script blocks with PowerShell's `using` scope.</span></span> <span data-ttu-id="1cffc-150">產生節點的 MOF 檔案時，會從用戶端電腦的文字檔讀取 `$version` 變數的值。</span><span class="sxs-lookup"><span data-stu-id="1cffc-150">When generating the node's MOF file, the value of the `$version` variable is read from a text file on the client computer.</span></span> <span data-ttu-id="1cffc-151">DSC 會以 `$version` 變數的值，取代各個指令碼區塊中的 `$using:version` 變數。</span><span class="sxs-lookup"><span data-stu-id="1cffc-151">DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>

