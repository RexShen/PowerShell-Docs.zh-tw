---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 在節點上套用、取得並測試設定
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079705"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="01eb0-103">在節點上套用、取得並測試設定</span><span class="sxs-lookup"><span data-stu-id="01eb0-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="01eb0-104">本指南將示範如何在目標節點上使用設定。</span><span class="sxs-lookup"><span data-stu-id="01eb0-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="01eb0-105">本指南會分成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="01eb0-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="01eb0-106">套用設定</span><span class="sxs-lookup"><span data-stu-id="01eb0-106">Apply a Configuration</span></span>

<span data-ttu-id="01eb0-107">為了套用和管理設定，我們需要產生一個 ".mof" 檔案。</span><span class="sxs-lookup"><span data-stu-id="01eb0-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="01eb0-108">下列程式碼表示將在這整份指南中使用的簡單設定。</span><span class="sxs-lookup"><span data-stu-id="01eb0-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

<span data-ttu-id="01eb0-109">編譯此設定將產生兩個 ".mof" 檔案。</span><span class="sxs-lookup"><span data-stu-id="01eb0-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="01eb0-110">若要套用設定，請使用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="01eb0-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="01eb0-111">`-Path` 參數會指定 ".mof" 檔案所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="01eb0-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="01eb0-112">若未指定 `-Computername`，`Start-DSCConfiguration` 會嘗試將每個設定套用至 '.mof' 檔案名稱 (\<computername\>.mof) 所指定的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="01eb0-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="01eb0-113">為 `Start-DSCConfiguration` 指定 `-Verbose` 以查看更詳盡的輸出。</span><span class="sxs-lookup"><span data-stu-id="01eb0-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="01eb0-114">若未指定 `-Wait`，您就會看到建立了一個作業。</span><span class="sxs-lookup"><span data-stu-id="01eb0-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="01eb0-115">針對 `Start-DSCConfiguration` 所處理的每個 ".mof" 檔案，所建立的作業將會有一個 **ChildJob**。</span><span class="sxs-lookup"><span data-stu-id="01eb0-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="01eb0-116">如果設定花費了很長的時間，而您想要停止它，您可以使用 [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) 來停止本機節點上的應用程式。</span><span class="sxs-lookup"><span data-stu-id="01eb0-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="01eb0-117">完成之後，您就能透過 [Get-Job](/powershell/module/microsoft.powershell.core/get-job) 所傳回的作業物件來檢視作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="01eb0-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

<span data-ttu-id="01eb0-118">若要查看 **Verbose** 輸出，使用下列命令來檢視每個 **ChildJob** 的 **Verbose** 資料流。</span><span class="sxs-lookup"><span data-stu-id="01eb0-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="01eb0-119">如需 PowerShell 作業的詳細資訊，請參閱 [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)。</span><span class="sxs-lookup"><span data-stu-id="01eb0-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="01eb0-120">從 PowerShell 5.0 開始，已在 `Start-DSCConfiguration` 中新增 `-UseExisting` 參數。</span><span class="sxs-lookup"><span data-stu-id="01eb0-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="01eb0-121">藉由指定 `-UseExisting`，您可以指示 Cmdlet 使用目前套用的設定，而不是 `-Path` 參數所指定的設定。</span><span class="sxs-lookup"><span data-stu-id="01eb0-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="01eb0-122">測試設定</span><span class="sxs-lookup"><span data-stu-id="01eb0-122">Test a Configuration</span></span>

<span data-ttu-id="01eb0-123">您可以使用 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) 來測試目前套用的設定。</span><span class="sxs-lookup"><span data-stu-id="01eb0-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="01eb0-124">如果節點符合規範，`Test-DSCConfiguration` 將傳回 `True`，如果不符合，則會傳回 `False`。</span><span class="sxs-lookup"><span data-stu-id="01eb0-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="01eb0-125">從 PowerShell 5.0 開始，已新增 `-Detailed` 參數，它會傳回一個物件，其中含有適用於 **ResourcesInDesiredState** 和 **ResourcesNotInDesiredState** 的集合</span><span class="sxs-lookup"><span data-stu-id="01eb0-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="01eb0-126">從 PowerShell 5.0 開始，您可以在不套用設定的情況下測試設定。</span><span class="sxs-lookup"><span data-stu-id="01eb0-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="01eb0-127">`-ReferenceConfiguration` 參數會接受 ".mof" 檔案的路徑，據以測試節點。</span><span class="sxs-lookup"><span data-stu-id="01eb0-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="01eb0-128">不需針對節點採取任何**設定**動作。</span><span class="sxs-lookup"><span data-stu-id="01eb0-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="01eb0-129">PowerShell 4.0 中提供可在不套用設定的情況下測試設定的因應措施，但不會在此討論它們。</span><span class="sxs-lookup"><span data-stu-id="01eb0-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="01eb0-130">取得設定值</span><span class="sxs-lookup"><span data-stu-id="01eb0-130">Get Configuration Values</span></span>

<span data-ttu-id="01eb0-131">[Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) Cmdlet 會傳回目前套用的設定中任何已設定資源的目前值。</span><span class="sxs-lookup"><span data-stu-id="01eb0-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="01eb0-132">如果成功套用，則我們範例設定的輸出看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="01eb0-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a><span data-ttu-id="01eb0-133">取得設定狀態</span><span class="sxs-lookup"><span data-stu-id="01eb0-133">Get Configuration Status</span></span>

<span data-ttu-id="01eb0-134">從 PowerShell 5.0 開始，[Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) Cmdlet 可讓您查看將設定套用至節點的記錄。</span><span class="sxs-lookup"><span data-stu-id="01eb0-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="01eb0-135">PowerShell DSC 會持續追蹤在**推送**或**提取**模式中最後套用的 {{N}} 個設定。</span><span class="sxs-lookup"><span data-stu-id="01eb0-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="01eb0-136">這包括 LCM 所執行的任何「一致性」檢查。</span><span class="sxs-lookup"><span data-stu-id="01eb0-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="01eb0-137">根據預設，`Get-DSCConfigurationStatus` 只會顯示最後一個記錄項目。</span><span class="sxs-lookup"><span data-stu-id="01eb0-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="01eb0-138">使用 `-All` 參數來查看所有設定狀態記錄。</span><span class="sxs-lookup"><span data-stu-id="01eb0-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="01eb0-139">為求簡單明瞭，會截斷輸出。</span><span class="sxs-lookup"><span data-stu-id="01eb0-139">Output is truncated for brevity.</span></span>

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a><span data-ttu-id="01eb0-140">管理設定文件</span><span class="sxs-lookup"><span data-stu-id="01eb0-140">Manage Configuration Documents</span></span>

<span data-ttu-id="01eb0-141">LCM 會使用**設定文件**來管理節點的設定。</span><span class="sxs-lookup"><span data-stu-id="01eb0-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="01eb0-142">這些 ".mof" 檔案均位於 "C:\Windows\System32\Configuration" 目錄。</span><span class="sxs-lookup"><span data-stu-id="01eb0-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="01eb0-143">從 PowerShell 5.0 開始，[Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) 可讓您移除 ".mof" 檔案，以停止未來的一致性檢查，或移除套用時發生錯誤的設定。</span><span class="sxs-lookup"><span data-stu-id="01eb0-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="01eb0-144">`-Stage` 參數可讓您指定要移除哪一個 ".mof" 檔案。</span><span class="sxs-lookup"><span data-stu-id="01eb0-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="01eb0-145">在 PowerShell 4.0 中，您仍然可以直接使用 [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) 來移除這些 ".mof" 檔案。</span><span class="sxs-lookup"><span data-stu-id="01eb0-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="01eb0-146">發佈設定</span><span class="sxs-lookup"><span data-stu-id="01eb0-146">Publish Configurations</span></span>

<span data-ttu-id="01eb0-147">從 PowerShell 5.0 開始，已新增 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="01eb0-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="01eb0-148">此 Cmdlet 可讓您將 ".mof" 檔案發佈至遠端電腦，而不需套用它。</span><span class="sxs-lookup"><span data-stu-id="01eb0-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="01eb0-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01eb0-149">See also</span></span>

- [<span data-ttu-id="01eb0-150">取得、測試及設定</span><span class="sxs-lookup"><span data-stu-id="01eb0-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
