---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC Script 資源
ms.openlocfilehash: e09e86011fa7dbb2a4d7f28b5032b4328b6f6ec2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953065"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="0f04b-103">DSC Script 資源</span><span class="sxs-lookup"><span data-stu-id="0f04b-103">DSC Script Resource</span></span>

> <span data-ttu-id="0f04b-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="0f04b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="0f04b-105">Windows PowerShell 預期狀態設定 (DSC) 的 **Script** 資源提供了在目標節點執行 Windows PowerShell 指令碼區塊的機制。</span><span class="sxs-lookup"><span data-stu-id="0f04b-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="0f04b-106">**Script** 資源會使用 **GetScript**、**SetScript** 和 **TestScript** 屬性，其中包含您定義來執行對應 DSC 狀態作業的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="0f04b-106">The **Script** resource uses **GetScript**, **SetScript**, and **TestScript** properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f04b-107">語法</span><span class="sxs-lookup"><span data-stu-id="0f04b-107">Syntax</span></span>

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
> <span data-ttu-id="0f04b-108">**GetScript**、**TestScript** 和 **SetScript** 區塊會儲存為字串。</span><span class="sxs-lookup"><span data-stu-id="0f04b-108">**GetScript**, **TestScript**, and **SetScript** blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="0f04b-109">Properties</span><span class="sxs-lookup"><span data-stu-id="0f04b-109">Properties</span></span>

|<span data-ttu-id="0f04b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0f04b-110">Property</span></span> |<span data-ttu-id="0f04b-111">描述</span><span class="sxs-lookup"><span data-stu-id="0f04b-111">Description</span></span> |
|---|---|
|<span data-ttu-id="0f04b-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="0f04b-112">GetScript</span></span> |<span data-ttu-id="0f04b-113">指令碼區塊，會傳回節點的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="0f04b-113">A script block that returns the current state of the Node.</span></span> |
|<span data-ttu-id="0f04b-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="0f04b-114">SetScript</span></span> |<span data-ttu-id="0f04b-115">指令碼區塊，DSC 會在節點未處於預期狀態時，用來強制執行合規性。</span><span class="sxs-lookup"><span data-stu-id="0f04b-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span> |
|<span data-ttu-id="0f04b-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="0f04b-116">TestScript</span></span> |<span data-ttu-id="0f04b-117">指令碼區塊，可判斷節點是否處於預期狀態。</span><span class="sxs-lookup"><span data-stu-id="0f04b-117">A script block that determines if the Node is in the desired state.</span></span> |
|<span data-ttu-id="0f04b-118">認證</span><span class="sxs-lookup"><span data-stu-id="0f04b-118">Credential</span></span> |<span data-ttu-id="0f04b-119">如果需要認證，表示執行這個指令碼所要使用的認證。</span><span class="sxs-lookup"><span data-stu-id="0f04b-119">Indicates the credentials to use for running this script, if credentials are required.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="0f04b-120">通用屬性</span><span class="sxs-lookup"><span data-stu-id="0f04b-120">Common properties</span></span>

|<span data-ttu-id="0f04b-121">屬性</span><span class="sxs-lookup"><span data-stu-id="0f04b-121">Property</span></span> |<span data-ttu-id="0f04b-122">描述</span><span class="sxs-lookup"><span data-stu-id="0f04b-122">Description</span></span> |
|---|---|
|<span data-ttu-id="0f04b-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0f04b-123">DependsOn</span></span> |<span data-ttu-id="0f04b-124">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="0f04b-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0f04b-125">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="0f04b-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="0f04b-126">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="0f04b-126">PsDscRunAsCredential</span></span> |<span data-ttu-id="0f04b-127">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="0f04b-127">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="0f04b-128">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="0f04b-128">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="0f04b-129">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="0f04b-129">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="0f04b-130">其他資訊</span><span class="sxs-lookup"><span data-stu-id="0f04b-130">Additional information</span></span>

#### <a name="getscript"></a><span data-ttu-id="0f04b-131">GetScript</span><span class="sxs-lookup"><span data-stu-id="0f04b-131">GetScript</span></span>

<span data-ttu-id="0f04b-132">DSC 不會使用 **GetScript** 的輸出。</span><span class="sxs-lookup"><span data-stu-id="0f04b-132">DSC does not use the output from **GetScript**.</span></span> <span data-ttu-id="0f04b-133">[Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) Cmdlet 會執行 **GetScript** 以擷取節點的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="0f04b-133">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes **GetScript** to retrieve a node's current state.</span></span> <span data-ttu-id="0f04b-134">**GetScript** 不需要傳回值。</span><span class="sxs-lookup"><span data-stu-id="0f04b-134">A return value is not required from **GetScript**.</span></span> <span data-ttu-id="0f04b-135">如果您指定傳回值，則它必須是雜湊碼，其中包含值為字串的 **Result** 機碼。</span><span class="sxs-lookup"><span data-stu-id="0f04b-135">If you specify a return value, it must be a hashtable containing a **Result** key whose value is a String.</span></span>

#### <a name="testscript"></a><span data-ttu-id="0f04b-136">TestScript</span><span class="sxs-lookup"><span data-stu-id="0f04b-136">TestScript</span></span>

<span data-ttu-id="0f04b-137">**TestScript** 會透過 DSC 執行，以判斷是否應該執行 **SetScript**。</span><span class="sxs-lookup"><span data-stu-id="0f04b-137">**TestScript** is executed by DSC to determine if **SetScript** should be run.</span></span> <span data-ttu-id="0f04b-138">如果 **TestScript** 傳回 `$false`，DSC 就會執行 **SetScript**，以讓節點回到預期狀態。</span><span class="sxs-lookup"><span data-stu-id="0f04b-138">If **TestScript** returns `$false`, DSC executes **SetScript** to bring the node back to the desired state.</span></span> <span data-ttu-id="0f04b-139">它必須傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="0f04b-139">It must return a boolean value.</span></span> <span data-ttu-id="0f04b-140">`$true` 的結果指出節點符合規範，且 **SetScript** 應該不會執行。</span><span class="sxs-lookup"><span data-stu-id="0f04b-140">A result of `$true` indicates that the node is compliant and **SetScript** should not executed.</span></span>

<span data-ttu-id="0f04b-141">[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) Cmdlet 會執行 **TestScript** 以利用 **Script** 資源來擷取節點合規性。</span><span class="sxs-lookup"><span data-stu-id="0f04b-141">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes **TestScript** to retrieve the nodes compliance with the **Script** resources.</span></span>
<span data-ttu-id="0f04b-142">不過，在此情況下，無論 **TestScript** 區塊傳回什麼，**SetScript** 都不會執行。</span><span class="sxs-lookup"><span data-stu-id="0f04b-142">However, in this case, **SetScript** does not run, no matter what **TestScript** block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="0f04b-143">來自您 **TestScript** 的所有輸出，都是其傳回值的一部分。</span><span class="sxs-lookup"><span data-stu-id="0f04b-143">All output from your **TestScript** is part of its return value.</span></span> <span data-ttu-id="0f04b-144">PowerShell 會將非隱藏的輸出解譯為非零值，這表示不論節點的狀態為何，您的 **TestScript** 都將傳回 `$true`。</span><span class="sxs-lookup"><span data-stu-id="0f04b-144">PowerShell interprets unsuppressed output as non-zero, which means that your **TestScript** will return `$true` regardless of your node's state.</span></span> <span data-ttu-id="0f04b-145">這會產生無法預期的結果、誤判，並導致疑難排解期間出現問題。</span><span class="sxs-lookup"><span data-stu-id="0f04b-145">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

#### <a name="setscript"></a><span data-ttu-id="0f04b-146">SetScript</span><span class="sxs-lookup"><span data-stu-id="0f04b-146">SetScript</span></span>

<span data-ttu-id="0f04b-147">**SetScript** 會修改節點以強制進入預期狀態。</span><span class="sxs-lookup"><span data-stu-id="0f04b-147">**SetScript** modifies the node to enforce the desired state.</span></span> <span data-ttu-id="0f04b-148">如果 **TestScript** 指令碼區塊傳回 `$false`，則會由 DSC 加以呼叫。</span><span class="sxs-lookup"><span data-stu-id="0f04b-148">It is called by DSC if the **TestScript** script block returns `$false`.</span></span> <span data-ttu-id="0f04b-149">**SetScript** 應該不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="0f04b-149">The **SetScript** should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="0f04b-150">範例</span><span class="sxs-lookup"><span data-stu-id="0f04b-150">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="0f04b-151">範例 1：使用指令碼資源撰寫範例文字</span><span class="sxs-lookup"><span data-stu-id="0f04b-151">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="0f04b-152">此範例會在每個節點上測試 `C:\TempFolder\TestFile.txt` 是否存在。</span><span class="sxs-lookup"><span data-stu-id="0f04b-152">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="0f04b-153">如果不存在，就會使用 `SetScript` 建立它。</span><span class="sxs-lookup"><span data-stu-id="0f04b-153">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="0f04b-154">`GetScript` 會傳回檔案的內容，而且不會使用它的傳回值。</span><span class="sxs-lookup"><span data-stu-id="0f04b-154">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="0f04b-155">範例 2：使用指令碼資源比較版本資訊</span><span class="sxs-lookup"><span data-stu-id="0f04b-155">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="0f04b-156">此範例會從撰寫電腦上的文字檔擷取「符合規範」  的版本資訊，並將它儲存在 `$version` 變數中。</span><span class="sxs-lookup"><span data-stu-id="0f04b-156">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="0f04b-157">產生節點的 MOF 檔案時，DSC 會使用 `$version` 變數的值，來取代每個指令碼區塊中的 `$using:version` 變數。</span><span class="sxs-lookup"><span data-stu-id="0f04b-157">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>
<span data-ttu-id="0f04b-158">執行期間，「符合規範」  的版本會儲存在每個節點的文字檔中，並與後續執行進行比較及更新。</span><span class="sxs-lookup"><span data-stu-id="0f04b-158">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

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