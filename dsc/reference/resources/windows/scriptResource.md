---
ms.date: 08/24/2018
keywords: dsc,powershell,設定,安裝
title: DSC Script 資源
ms.openlocfilehash: ef84239820a44aab2a028f7f0fe17653a851b72e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676688"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="3af48-103">DSC Script 資源</span><span class="sxs-lookup"><span data-stu-id="3af48-103">DSC Script Resource</span></span>

> <span data-ttu-id="3af48-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="3af48-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="3af48-105">Windows PowerShell 預期狀態設定 (DSC) 的 **Script** 資源提供了在目標節點執行 Windows PowerShell 指令碼區塊的機制。</span><span class="sxs-lookup"><span data-stu-id="3af48-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="3af48-106">**Script** 資源會使用 `GetScript`、`SetScript` 和 `TestScript` 屬性，其中包含您定義來執行對應 DSC 狀態作業的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="3af48-106">The **Script** resource uses `GetScript`, `SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="3af48-107">語法</span><span class="sxs-lookup"><span data-stu-id="3af48-107">Syntax</span></span>

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

> [!NOTE]
> <span data-ttu-id="3af48-108">`GetScript`、`TestScript` 與 `SetScript` 區塊會以字串形式儲存。</span><span class="sxs-lookup"><span data-stu-id="3af48-108">The `GetScript`, `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="3af48-109">Properties</span><span class="sxs-lookup"><span data-stu-id="3af48-109">Properties</span></span>

|<span data-ttu-id="3af48-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3af48-110">Property</span></span>|<span data-ttu-id="3af48-111">描述</span><span class="sxs-lookup"><span data-stu-id="3af48-111">Description</span></span>|
|--------|-----------|
|<span data-ttu-id="3af48-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="3af48-112">GetScript</span></span>|<span data-ttu-id="3af48-113">指令碼區塊，會傳回節點的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="3af48-113">A script block that returns the current state of the Node.</span></span>|
|<span data-ttu-id="3af48-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="3af48-114">SetScript</span></span>|<span data-ttu-id="3af48-115">指令碼區塊，DSC 會在節點未處於預期狀態時，用來強制執行合規性。</span><span class="sxs-lookup"><span data-stu-id="3af48-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span>|
|<span data-ttu-id="3af48-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="3af48-116">TestScript</span></span>|<span data-ttu-id="3af48-117">指令碼區塊，可判斷節點是否處於預期狀態。</span><span class="sxs-lookup"><span data-stu-id="3af48-117">A script block that determines if the Node is in the desired state.</span></span>|
|<span data-ttu-id="3af48-118">認證</span><span class="sxs-lookup"><span data-stu-id="3af48-118">Credential</span></span>| <span data-ttu-id="3af48-119">如果需要認證，表示執行這個指令碼所要使用的認證。</span><span class="sxs-lookup"><span data-stu-id="3af48-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
|<span data-ttu-id="3af48-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3af48-120">DependsOn</span></span>| <span data-ttu-id="3af48-121">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="3af48-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3af48-122">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="3af48-122">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

### <a name="getscript"></a><span data-ttu-id="3af48-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="3af48-123">GetScript</span></span>

<span data-ttu-id="3af48-124">DSC 不會使用 `GetScript` 的輸出。</span><span class="sxs-lookup"><span data-stu-id="3af48-124">DSC does not use the output from `GetScript`.</span></span> <span data-ttu-id="3af48-125">[Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) Cmdlet 會執行 `GetScript` 以擷取節點的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="3af48-125">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes the `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="3af48-126">`GetScript` 不需要傳回值。</span><span class="sxs-lookup"><span data-stu-id="3af48-126">A return value is not required from `GetScript`.</span></span> <span data-ttu-id="3af48-127">如果您指定傳回值，它必須是 `hashtable`，其中包含值為 `String` 的 **Result** 機碼。</span><span class="sxs-lookup"><span data-stu-id="3af48-127">If you specify a return value, it must be a `hashtable` containing a **Result** key whose value is a `String`.</span></span>

### <a name="testscript"></a><span data-ttu-id="3af48-128">TestScript</span><span class="sxs-lookup"><span data-stu-id="3af48-128">TestScript</span></span>

<span data-ttu-id="3af48-129">`TestScript` 會透過 DSC 執行，以判斷是否應該執行 `SetScript`。</span><span class="sxs-lookup"><span data-stu-id="3af48-129">The `TestScript` is executed by DSC to determine if the `SetScript` should be run.</span></span> <span data-ttu-id="3af48-130">如果 `TestScript` 傳回 `$false`，DSC 就會執行 `SetScript`，以讓節點回到預期狀態。</span><span class="sxs-lookup"><span data-stu-id="3af48-130">If the `TestScript` returns `$false`, DSC executes the `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="3af48-131">它必須傳回 `boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="3af48-131">It must return a `boolean` value.</span></span> <span data-ttu-id="3af48-132">`$true` 的結果指出節點符合規範，而且 `SetScript` 應該不會執行。</span><span class="sxs-lookup"><span data-stu-id="3af48-132">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="3af48-133">[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) Cmdlet 會執行 `TestScript`，利用 **Script** 資源來擷取節點合規性。</span><span class="sxs-lookup"><span data-stu-id="3af48-133">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes the `TestScript` to retrieve the nodes compliance with the  **Script** resources.</span></span> <span data-ttu-id="3af48-134">不過，在此情況下，無論 `TestScript` 區塊傳回什麼，`SetScript` 都不會執行。</span><span class="sxs-lookup"><span data-stu-id="3af48-134">However, in this case, the `SetScript` does not run, no matter what the `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="3af48-135">來自您 `TestScript` 的所有輸出都是其傳回值的一部分。</span><span class="sxs-lookup"><span data-stu-id="3af48-135">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="3af48-136">PowerShell 會將非隱藏的輸出解譯為非零值，這表示不論節點的狀態為何，您的 `TestScript` 都將傳回 `$true`。</span><span class="sxs-lookup"><span data-stu-id="3af48-136">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span>
> <span data-ttu-id="3af48-137">這會產生無法預期的結果、誤判，並導致疑難排解期間出現問題。</span><span class="sxs-lookup"><span data-stu-id="3af48-137">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

### <a name="setscript"></a><span data-ttu-id="3af48-138">SetScript</span><span class="sxs-lookup"><span data-stu-id="3af48-138">SetScript</span></span>

<span data-ttu-id="3af48-139">`SetScript` 會修改節點以強制進入預期狀態。</span><span class="sxs-lookup"><span data-stu-id="3af48-139">The `SetScript` modifies the node to enfore the desired state.</span></span> <span data-ttu-id="3af48-140">如果 `TestScript` 指令碼區塊傳回 `$false`，則會由 DSC 加以呼叫。</span><span class="sxs-lookup"><span data-stu-id="3af48-140">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="3af48-141">`SetScript` 應該不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="3af48-141">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="3af48-142">範例</span><span class="sxs-lookup"><span data-stu-id="3af48-142">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="3af48-143">範例 1：撰寫使用指令碼資源的範例文字</span><span class="sxs-lookup"><span data-stu-id="3af48-143">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="3af48-144">此範例會在每個節點上測試 `C:\TempFolder\TestFile.txt` 是否存在。</span><span class="sxs-lookup"><span data-stu-id="3af48-144">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="3af48-145">如果不存在，就會使用 `SetScript` 建立它。</span><span class="sxs-lookup"><span data-stu-id="3af48-145">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="3af48-146">`GetScript` 會傳回檔案的內容，而且不會使用它的傳回值。</span><span class="sxs-lookup"><span data-stu-id="3af48-146">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="3af48-147">範例 2：比較使用指令碼資源的版本資訊</span><span class="sxs-lookup"><span data-stu-id="3af48-147">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="3af48-148">此範例會從撰寫電腦上的文字檔擷取「符合規範」的版本資訊，並將它儲存在 `$version` 變數中。</span><span class="sxs-lookup"><span data-stu-id="3af48-148">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="3af48-149">產生節點的 MOF 檔案時，DSC 會使用 `$version` 變數的值，來取代每個指令碼區塊中的 `$using:version` 變數。</span><span class="sxs-lookup"><span data-stu-id="3af48-149">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span> <span data-ttu-id="3af48-150">執行期間，「符合規範」的版本會儲存在每個節點的文字檔中，並與後續執行進行比較及更新。</span><span class="sxs-lookup"><span data-stu-id="3af48-150">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
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
}
```