---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC Script 資源
ms.openlocfilehash: 9b89981c17e87b3681c6416c7dee44a75c432ea1
ms.sourcegitcommit: eb6a7c01e6385809656ac828b9211683e0b1a6fe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "89041124"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="1feac-103">DSC Script 資源</span><span class="sxs-lookup"><span data-stu-id="1feac-103">DSC Script Resource</span></span>

> <span data-ttu-id="1feac-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="1feac-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="1feac-105">Windows PowerShell 預期狀態設定 (DSC) 的 `Script` 資源提供了在目標節點執行 Windows PowerShell 指令碼區塊的機制。</span><span class="sxs-lookup"><span data-stu-id="1feac-105">The `Script` resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="1feac-106">`Script` 資源會使用 `GetScript`
`SetScript` 和 `TestScript` 屬性，其包含定義來執行對應 DSC 狀態作業的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="1feac-106">The `Script` resource uses `GetScript`
`SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="1feac-107">語法</span><span class="sxs-lookup"><span data-stu-id="1feac-107">Syntax</span></span>

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="1feac-108">`GetScript`、`TestScript` 和 `SetScript` 區塊會儲存為字串。</span><span class="sxs-lookup"><span data-stu-id="1feac-108">`GetScript` `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="1feac-109">屬性</span><span class="sxs-lookup"><span data-stu-id="1feac-109">Properties</span></span>

|  <span data-ttu-id="1feac-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1feac-110">Property</span></span>  |                                          <span data-ttu-id="1feac-111">描述</span><span class="sxs-lookup"><span data-stu-id="1feac-111">Description</span></span>                                          |
| ---------- | --------------------------------------------------------------------------------------------- |
| <span data-ttu-id="1feac-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="1feac-112">GetScript</span></span>  | <span data-ttu-id="1feac-113">指令碼區塊，會傳回節點的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="1feac-113">A script block that returns the current state of the Node.</span></span>                                    |
| <span data-ttu-id="1feac-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="1feac-114">SetScript</span></span>  | <span data-ttu-id="1feac-115">指令碼區塊，DSC 會在節點未處於預期狀態時，用來強制執行合規性。</span><span class="sxs-lookup"><span data-stu-id="1feac-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span> |
| <span data-ttu-id="1feac-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="1feac-116">TestScript</span></span> | <span data-ttu-id="1feac-117">指令碼區塊，可判斷節點是否處於預期狀態。</span><span class="sxs-lookup"><span data-stu-id="1feac-117">A script block that determines if the Node is in the desired state.</span></span>                           |
| <span data-ttu-id="1feac-118">認證</span><span class="sxs-lookup"><span data-stu-id="1feac-118">Credential</span></span> | <span data-ttu-id="1feac-119">如果需要認證，表示執行這個指令碼所要使用的認證。</span><span class="sxs-lookup"><span data-stu-id="1feac-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>        |

## <a name="common-properties"></a><span data-ttu-id="1feac-120">通用屬性</span><span class="sxs-lookup"><span data-stu-id="1feac-120">Common properties</span></span>

|       <span data-ttu-id="1feac-121">屬性</span><span class="sxs-lookup"><span data-stu-id="1feac-121">Property</span></span>       |                                            <span data-ttu-id="1feac-122">描述</span><span class="sxs-lookup"><span data-stu-id="1feac-122">Description</span></span>                                            |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="1feac-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1feac-123">DependsOn</span></span>            | <span data-ttu-id="1feac-124">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="1feac-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> |
| <span data-ttu-id="1feac-125">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1feac-125">PsDscRunAsCredential</span></span> | <span data-ttu-id="1feac-126">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="1feac-126">Sets the credential for running the entire resource as.</span></span>                                           |

> [!NOTE]
> <span data-ttu-id="1feac-127">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="1feac-127">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="1feac-128">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="1feac-128">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="1feac-129">其他資訊</span><span class="sxs-lookup"><span data-stu-id="1feac-129">Additional information</span></span>

#### <a name="getscript"></a><span data-ttu-id="1feac-130">GetScript</span><span class="sxs-lookup"><span data-stu-id="1feac-130">GetScript</span></span>

<span data-ttu-id="1feac-131">DSC 不會使用 `GetScript` 的輸出。[Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) Cmdlet 會執行 `GetScript` 以擷取節點目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="1feac-131">DSC does not use the output from `GetScript` The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="1feac-132">不需要來自 `GetScript` 的傳回值。如果指定傳回值，則必須是 **Result** 機碼的雜湊表，其中所包含的值為字串。</span><span class="sxs-lookup"><span data-stu-id="1feac-132">A return value is not required from `GetScript` If you specify a return value, it must be a hashtable containing a **Result** key whose value is a String.</span></span>

#### <a name="testscript"></a><span data-ttu-id="1feac-133">TestScript</span><span class="sxs-lookup"><span data-stu-id="1feac-133">TestScript</span></span>

<span data-ttu-id="1feac-134">`TestScript` 會透過 DSC 執行，以判斷是否應該執行 `SetScript`。</span><span class="sxs-lookup"><span data-stu-id="1feac-134">`TestScript` is executed by DSC to determine if `SetScript` should be run.</span></span> <span data-ttu-id="1feac-135">如果 `TestScript` 傳回 `$false`，DSC 就會執行 `SetScript`，以讓節點回到預期狀態。</span><span class="sxs-lookup"><span data-stu-id="1feac-135">If `TestScript` returns `$false`, DSC executes `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="1feac-136">它必須傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="1feac-136">It must return a boolean value.</span></span> <span data-ttu-id="1feac-137">`$true` 的結果指出節點符合規範，而且 `SetScript` 應該不會執行。</span><span class="sxs-lookup"><span data-stu-id="1feac-137">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="1feac-138">[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) Cmdlet 會執行 `TestScript` 以利用 `Script` 資源來擷取節點合規性。</span><span class="sxs-lookup"><span data-stu-id="1feac-138">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes `TestScript` to retrieve the nodes compliance with the `Script` resources.</span></span> <span data-ttu-id="1feac-139">不過，在此情況下，無論 `TestScript` 區塊傳回什麼，`SetScript` 都不會執行。</span><span class="sxs-lookup"><span data-stu-id="1feac-139">However, in this case, `SetScript` does not run, no matter what `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="1feac-140">來自您 `TestScript` 的所有輸出都是其傳回值的一部分。</span><span class="sxs-lookup"><span data-stu-id="1feac-140">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="1feac-141">PowerShell 會將非隱藏的輸出解譯為非零值，這表示不論節點的狀態為何，您的 `TestScript` 都將傳回 `$true`。</span><span class="sxs-lookup"><span data-stu-id="1feac-141">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span> <span data-ttu-id="1feac-142">這會產生無法預期的結果、誤判，並導致疑難排解期間出現問題。</span><span class="sxs-lookup"><span data-stu-id="1feac-142">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

#### <a name="setscript"></a><span data-ttu-id="1feac-143">SetScript</span><span class="sxs-lookup"><span data-stu-id="1feac-143">SetScript</span></span>

<span data-ttu-id="1feac-144">`SetScript` 會修改節點以強制進入預期狀態。</span><span class="sxs-lookup"><span data-stu-id="1feac-144">`SetScript` modifies the node to enforce the desired state.</span></span> <span data-ttu-id="1feac-145">如果 `TestScript` 指令碼區塊傳回 `$false`，則會由 DSC 加以呼叫。</span><span class="sxs-lookup"><span data-stu-id="1feac-145">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="1feac-146">`SetScript` 應該不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="1feac-146">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="1feac-147">範例</span><span class="sxs-lookup"><span data-stu-id="1feac-147">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="1feac-148">範例 1：使用指令碼資源撰寫範例文字</span><span class="sxs-lookup"><span data-stu-id="1feac-148">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="1feac-149">此範例會在每個節點上測試 `C:\TempFolder\TestFile.txt` 是否存在。</span><span class="sxs-lookup"><span data-stu-id="1feac-149">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="1feac-150">如果不存在，就會使用 `SetScript` 建立它。</span><span class="sxs-lookup"><span data-stu-id="1feac-150">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="1feac-151">`GetScript` 會傳回檔案的內容，而且不會使用它的傳回值。</span><span class="sxs-lookup"><span data-stu-id="1feac-151">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="1feac-152">範例 2：使用指令碼資源比較版本資訊</span><span class="sxs-lookup"><span data-stu-id="1feac-152">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="1feac-153">此範例會從撰寫電腦上的文字檔擷取「符合規範」的版本資訊，並將它儲存在 `$version` 變數中。</span><span class="sxs-lookup"><span data-stu-id="1feac-153">This example retrieves the _compliant_ version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="1feac-154">產生節點的 MOF 檔案時，DSC 會使用 `$version` 變數的值，來取代每個指令碼區塊中的 `$using:version` 變數。</span><span class="sxs-lookup"><span data-stu-id="1feac-154">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>
<span data-ttu-id="1feac-155">執行期間，「符合規範」的版本會儲存在每個節點的文字檔中，並與後續執行進行比較及更新。</span><span class="sxs-lookup"><span data-stu-id="1feac-155">During execution, the _compliant_ version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

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

                if( $state.Result -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state.Result,$using:version)
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

### <a name="example-3-utilizing-parameters-in-a-script-resource"></a><span data-ttu-id="1feac-156">範例 3：利用指令碼資源中的參數</span><span class="sxs-lookup"><span data-stu-id="1feac-156">Example 3: Utilizing parameters in a Script resource</span></span>

<span data-ttu-id="1feac-157">此範例使用 `using` 範圍，存取指令碼資源中的參數。</span><span class="sxs-lookup"><span data-stu-id="1feac-157">This example accesses parameters from within the Script resource by making use of the `using` scope.</span></span>
<span data-ttu-id="1feac-158">請注意，您可以使用類似方式存取 **ConfigurationData**。</span><span class="sxs-lookup"><span data-stu-id="1feac-158">Please note that **ConfigurationData** can be accessed in a similar way.</span></span> <span data-ttu-id="1feac-159">一如範例 2，版本會儲存在目標節點的本機檔案中。</span><span class="sxs-lookup"><span data-stu-id="1feac-159">Like example 2, a version is expected to be stored inside a local file on the target node.</span></span> <span data-ttu-id="1feac-160">然而，因為本機檔案路徑與版本均可設定，所以會將程式碼與設定資料分離。</span><span class="sxs-lookup"><span data-stu-id="1feac-160">Both the local file path as well as the version are configurable however, decoupling code from configuration data.</span></span>

```powershell
Configuration ScriptTest
{
    param
    (
        [Version]
        $Version,

        [string]
        $FilePath
    )

    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content -Path $using:FilePath
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:Version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }

                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                Set-Content -Path $using:FilePath -Value $using:Version
            }
        }
    }
}
```

<span data-ttu-id="1feac-161">產生的 MOF 檔案包含透過 `using` 範圍存取的變數及其值。</span><span class="sxs-lookup"><span data-stu-id="1feac-161">The resulting MOF file includes the variables and their values accessed through the `using` scope.</span></span>
<span data-ttu-id="1feac-162">這些檔案會插入每個使用變數的 ScriptBlock。</span><span class="sxs-lookup"><span data-stu-id="1feac-162">They are injected into each scriptblock which uses the variables.</span></span> <span data-ttu-id="1feac-163">因簡要考量，已移除 Test 與 Set 指令碼：</span><span class="sxs-lookup"><span data-stu-id="1feac-163">Test and Set scripts have been removed for brevity:</span></span>

```Output
instance of MSFT_ScriptResource as $MSFT_ScriptResource1ref
{
 GetScript = "$FilePath ='C:\\Config.ini'\n\n $currentVersion = Get-Content -Path $FilePath\n return @{ 'Result' = \"$currentVersion\" }\n";
 TestScript = ...;
 SetScript = ...;
};
```

### <a name="known-limitations"></a><span data-ttu-id="1feac-164">已知限制</span><span class="sxs-lookup"><span data-stu-id="1feac-164">Known Limitations</span></span>

- <span data-ttu-id="1feac-165">使用提取或推送伺服器模型時，在指令碼資源內傳遞的認證不一定可靠。</span><span class="sxs-lookup"><span data-stu-id="1feac-165">Credentials being passed within a script resource are not always reliable when using a pull or push server model.</span></span> <span data-ttu-id="1feac-166">這種情況下，建議使用完整資源，不要使用指令碼資源。</span><span class="sxs-lookup"><span data-stu-id="1feac-166">It is recommended to use a full resource rather than use a script resource in this case.</span></span>
