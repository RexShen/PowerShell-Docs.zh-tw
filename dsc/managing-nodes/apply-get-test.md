---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 在節點上套用、取得並測試設定
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400855"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="5425a-103">在節點上套用、取得並測試設定</span><span class="sxs-lookup"><span data-stu-id="5425a-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="5425a-104">本指南將示範如何使用組態在目標節點上。</span><span class="sxs-lookup"><span data-stu-id="5425a-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="5425a-105">本指南會分成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="5425a-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="5425a-106">套用組態</span><span class="sxs-lookup"><span data-stu-id="5425a-106">Apply a Configuration</span></span>

<span data-ttu-id="5425a-107">若要套用管理設定，我們要產生 「.mof 」 檔案。</span><span class="sxs-lookup"><span data-stu-id="5425a-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="5425a-108">下列程式碼將代表簡單的設定將用於本指南。</span><span class="sxs-lookup"><span data-stu-id="5425a-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

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

<span data-ttu-id="5425a-109">編譯此組態會產生兩個 「.mof 」 檔案。</span><span class="sxs-lookup"><span data-stu-id="5425a-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="5425a-110">若要套用設定，請使用[Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5425a-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="5425a-111">`-Path`參數指定".mof 」 檔案所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="5425a-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="5425a-112">如果沒有`-Computername`指定，則`Start-DSCConfiguration`會嘗試將每個組態套用至 '.mof' 檔案的名稱所指定電腦名稱 (\<computername\>.mof)。</span><span class="sxs-lookup"><span data-stu-id="5425a-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="5425a-113">指定`-Verbose`至`Start-DSCConfiguration`以查看更詳細的輸出。</span><span class="sxs-lookup"><span data-stu-id="5425a-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="5425a-114">如果`-Wait`未指定，您會看到建立的一項作業。</span><span class="sxs-lookup"><span data-stu-id="5425a-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="5425a-115">建立的作業會有一個**ChildJob**每個 「.mof"檔案處理`Start-DSCConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="5425a-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="5425a-116">如果設定花費很長的時間，而且您想要將它停止，您可以使用[Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)本機節點上停止應用程式。</span><span class="sxs-lookup"><span data-stu-id="5425a-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="5425a-117">完成後，您可以檢視所傳回的工作物件透過作業的狀態[Get-job](/powershell/module/microsoft.powershell.core/get-job)。</span><span class="sxs-lookup"><span data-stu-id="5425a-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

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

<span data-ttu-id="5425a-118">若要查看**Verbose**輸出，使用下列命令來檢視**Verbose**每個資料流**ChildJob**。</span><span class="sxs-lookup"><span data-stu-id="5425a-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="5425a-119">如需有關 PowerShell 工作的詳細資訊，請參閱[about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)。</span><span class="sxs-lookup"><span data-stu-id="5425a-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

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

<span data-ttu-id="5425a-120">從 PowerShell 5.0`-UseExisting`參數已加入至`Start-DSCConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="5425a-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="5425a-121">藉由指定`-UseExisting`，您可以指示 cmdlet 來使用現有套用的設定，而不是一個由`-Path`參數。</span><span class="sxs-lookup"><span data-stu-id="5425a-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="5425a-122">測試組態</span><span class="sxs-lookup"><span data-stu-id="5425a-122">Test a Configuration</span></span>

<span data-ttu-id="5425a-123">您可以測試目前套用的設定使用[Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)。</span><span class="sxs-lookup"><span data-stu-id="5425a-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="5425a-124">`Test-DSCConfiguration` 會傳回`True`如果節點是符合規範，與`False`如果不是。</span><span class="sxs-lookup"><span data-stu-id="5425a-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="5425a-125">從 PowerShell 5.0`-Detailed`已新增參數，它會傳回集合的物件**ResourcesInDesiredState**和**ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="5425a-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="5425a-126">在 PowerShell 5.0 開始，可以測試組態而不套用它。</span><span class="sxs-lookup"><span data-stu-id="5425a-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="5425a-127">`-ReferenceConfiguration`參數可接受的 「.mof"檔案來測試依據的節點路徑。</span><span class="sxs-lookup"><span data-stu-id="5425a-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="5425a-128">否**設定**動作都會針對該節點。</span><span class="sxs-lookup"><span data-stu-id="5425a-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="5425a-129">在 PowerShell 4.0 中，有因應措施若要測試組態，而不套用它，但不是會在此討論。</span><span class="sxs-lookup"><span data-stu-id="5425a-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="5425a-130">取得組態值</span><span class="sxs-lookup"><span data-stu-id="5425a-130">Get Configuration Values</span></span>

<span data-ttu-id="5425a-131">[Get-dscconfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet 會傳回在目前套用的設定中設定的任何資源的目前值。</span><span class="sxs-lookup"><span data-stu-id="5425a-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="5425a-132">如果已成功套用，從我們的範例組態的輸出會看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="5425a-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

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

## <a name="get-configuration-status"></a><span data-ttu-id="5425a-133">取得設定狀態</span><span class="sxs-lookup"><span data-stu-id="5425a-133">Get Configuration Status</span></span>

<span data-ttu-id="5425a-134">從 PowerShell 5.0 [Get-dscconfigurationstatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet 可讓您查看的節點套用組態的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="5425a-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="5425a-135">PowerShell DSC 記錄的最後的 {{N}} 設定中套用**推播**或是**提取**模式。</span><span class="sxs-lookup"><span data-stu-id="5425a-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="5425a-136">這包括任何*一致性*LCM 所執行的檢查。</span><span class="sxs-lookup"><span data-stu-id="5425a-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="5425a-137">根據預設，`Get-DSCConfigurationStatus`之最後一個記錄項目只會顯示您。</span><span class="sxs-lookup"><span data-stu-id="5425a-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="5425a-138">使用`-All`參數，以查看所有的組態狀態歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="5425a-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="5425a-139">為求簡單明瞭，便會截斷輸出。</span><span class="sxs-lookup"><span data-stu-id="5425a-139">Output is truncated for brevity.</span></span>

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

## <a name="manage-configuration-documents"></a><span data-ttu-id="5425a-140">管理設定文件</span><span class="sxs-lookup"><span data-stu-id="5425a-140">Manage Configuration Documents</span></span>

<span data-ttu-id="5425a-141">LCM 使用來管理節點的組態**設定文件**。</span><span class="sxs-lookup"><span data-stu-id="5425a-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="5425a-142">這些 「.mof"檔案位於 「 C:\Windows\System32\Configuration"的目錄中。</span><span class="sxs-lookup"><span data-stu-id="5425a-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="5425a-143">從 PowerShell 5.0 [Remove-dscconfigurationdocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)可讓您移除 「.mof"檔案來停止未來的一致性檢查，或移除發生錯誤時套用的設定。</span><span class="sxs-lookup"><span data-stu-id="5425a-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="5425a-144">`-Stage`參數可讓您指定您想要移除哪一個 「.mof 」 檔案。</span><span class="sxs-lookup"><span data-stu-id="5425a-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="5425a-145">在 PowerShell 4.0 中，您仍然可以移除直接使用這些 「.mof"檔案[Remove-item](/powershell/module/microsoft.powershell.management/remove-item)。</span><span class="sxs-lookup"><span data-stu-id="5425a-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="5425a-146">發行設定</span><span class="sxs-lookup"><span data-stu-id="5425a-146">Publish Configurations</span></span>

<span data-ttu-id="5425a-147">從 PowerShell 5.0 [Publish-dscconfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet 已新增。</span><span class="sxs-lookup"><span data-stu-id="5425a-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="5425a-148">此 cmdlet 可讓您發佈至遠端電腦的".mof 」 檔案，而不套用它。</span><span class="sxs-lookup"><span data-stu-id="5425a-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="5425a-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5425a-149">See also</span></span>

- [<span data-ttu-id="5425a-150">取得、測試及設定</span><span class="sxs-lookup"><span data-stu-id="5425a-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
