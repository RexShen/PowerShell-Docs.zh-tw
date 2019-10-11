---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 在 PowerShell 4.0 中設定 LCM
ms.openlocfilehash: 747b15c483c79a7ecbb62214ef5a59f8dc137bd4
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953825"
---
# <a name="configuring-the-lcm-in-powershell-40"></a><span data-ttu-id="d280a-103">在 PowerShell 4.0 中設定 LCM</span><span class="sxs-lookup"><span data-stu-id="d280a-103">Configuring the LCM in PowerShell 4.0</span></span>

><span data-ttu-id="d280a-104">適用於：Windows PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="d280a-104">Applies To: Windows PowerShell 4.0</span></span>

<span data-ttu-id="d280a-105">**如需 Windows PowerShell 5.0 及更新版本的相關資訊，請參閱[設定本機設定管理員](metaConfig.md)。**</span><span class="sxs-lookup"><span data-stu-id="d280a-105">**For information related to Windows PowerShell 5.0 and later, see [Configuring the Local Configuration Manager](metaConfig.md).**</span></span>

<span data-ttu-id="d280a-106">本機設定管理員是 Windows PowerShell 預期狀態設定 (DSC) 引擎，</span><span class="sxs-lookup"><span data-stu-id="d280a-106">Local Configuration Manager is the Windows PowerShell Desired State Configuration (DSC) engine.</span></span>
<span data-ttu-id="d280a-107">會在所有目標節點上執行，負責呼叫包含在 DSC 設定指令碼中的設定資源。</span><span class="sxs-lookup"><span data-stu-id="d280a-107">It runs on all target nodes, and it is responsible for calling the configuration resources that are included in a DSC configuration script.</span></span>
<span data-ttu-id="d280a-108">本主題列出本機設定管理員屬性，並說明如何修改目標節點上的本機設定管理員設定。</span><span class="sxs-lookup"><span data-stu-id="d280a-108">This topic lists the properties of Local Configuration Manager and describes how you can modify the Local Configuration Manager settings on a target node.</span></span>

## <a name="local-configuration-manager-properties"></a><span data-ttu-id="d280a-109">本機設定管理員屬性</span><span class="sxs-lookup"><span data-stu-id="d280a-109">Local Configuration Manager properties</span></span>

<span data-ttu-id="d280a-110">以下列出您可以設定或擷取的本機設定管理員屬性。</span><span class="sxs-lookup"><span data-stu-id="d280a-110">The following lists the Local Configuration Manager properties that you can set or retrieve.</span></span>

- <span data-ttu-id="d280a-111">**AllowModuleOverwrite**：控制是否允許以從設定服務下載的新設定來覆寫目標節點上的舊設定。</span><span class="sxs-lookup"><span data-stu-id="d280a-111">**AllowModuleOverwrite**: Controls whether new configurations downloaded from the configuration service are allowed to overwrite the old ones on the target node.</span></span> <span data-ttu-id="d280a-112">可能的值為 True 和 False。</span><span class="sxs-lookup"><span data-stu-id="d280a-112">Possible values are True and False.</span></span>
- <span data-ttu-id="d280a-113">**CertificateID**：憑證指紋，用來保護在設定中傳遞的憑證。</span><span class="sxs-lookup"><span data-stu-id="d280a-113">**CertificateID**: The thumbprint of a certificate used to secure credentials passed in a configuration.</span></span> <span data-ttu-id="d280a-114">如需詳細資訊，請參閱 [Want to secure credentials in Windows PowerShell Desired State Configuration (需要保護 Windows PowerShell 預期狀態設定的憑證嗎？)](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/)。</span><span class="sxs-lookup"><span data-stu-id="d280a-114">For more information see [Want to secure credentials in Windows PowerShell Desired State Configuration?](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).</span></span>
- <span data-ttu-id="d280a-115">**ConfigurationID**：表示用來從提取服務取得特定設定檔的 GUID。</span><span class="sxs-lookup"><span data-stu-id="d280a-115">**ConfigurationID**: Indicates a GUID which is used to get a particular configuration file from a pull service.</span></span> <span data-ttu-id="d280a-116">此 GUID 可確保存取正確的設定檔。</span><span class="sxs-lookup"><span data-stu-id="d280a-116">The GUID ensures that the correct configuration file is accessed.</span></span>
- <span data-ttu-id="d280a-117">**ConfigurationMode**：指定本機設定管理員實際上如何將設定套用至目標節點。</span><span class="sxs-lookup"><span data-stu-id="d280a-117">**ConfigurationMode**: Specifies how the Local Configuration Manager actually applies the configuration to the target nodes.</span></span> <span data-ttu-id="d280a-118">它可以接受下列值：</span><span class="sxs-lookup"><span data-stu-id="d280a-118">It can take the following values:</span></span>
  - <span data-ttu-id="d280a-119">**ApplyOnly**：若設定此選項，DSC 會套用設定，並且不會執行任何進一步的動作，除非它透過下列兩種方式偵測到新的設定：您直接將新設定傳送至目標節點，或是您連線至提取服務且 DSC 於檢查提取服務時發現新設定。</span><span class="sxs-lookup"><span data-stu-id="d280a-119">**ApplyOnly**: With this option, DSC applies the configuration and does nothing further unless a new configuration is detected, either by you sending a new configuration directly to the target node or if you are connecting to a pull service and DSC discovers a new configuration when it checks with the pull service.</span></span> <span data-ttu-id="d280a-120">如果目標節點的設定偏離，就不採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="d280a-120">If the target node's configuration drifts, no action is taken.</span></span>
  - <span data-ttu-id="d280a-121">**ApplyAndMonitor**：若設定此選項 (此為預設值)，DSC 會套用任何新設定，無論新設定是由您直接傳送至目標節點，或是在提取服務上發現。</span><span class="sxs-lookup"><span data-stu-id="d280a-121">**ApplyAndMonitor**: With this option (which is the default), DSC applies any new configurations, whether sent by you directly to the target node or discovered on a pull service.</span></span> <span data-ttu-id="d280a-122">之後，如果目標節點的設定偏離設定檔，DSC 就會報告記錄檔中的差異。</span><span class="sxs-lookup"><span data-stu-id="d280a-122">Thereafter, if the configuration of the target node drifts from the configuration file, DSC reports the discrepancy in logs.</span></span> <span data-ttu-id="d280a-123">如需 DSC 記錄的資訊，請參閱 [Using Event Logs to Diagnose Errors in Desired State Configuration (在預期狀態設定中使用事件記錄檔診斷錯誤)](https://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d280a-123">For more about DSC logging, see [Using Event Logs to Diagnose Errors in Desired State Configuration](https://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).</span></span>
  - <span data-ttu-id="d280a-124">**ApplyAndAutoCorrect**：若設定此選項，DSC 會套用任何新設定，無論新設定是由您直接傳送至目標節點，或是在提取服務上發現。</span><span class="sxs-lookup"><span data-stu-id="d280a-124">**ApplyAndAutoCorrect**: With this option, DSC applies any new configurations, whether sent by you directly to the target node or discovered on a pull service.</span></span> <span data-ttu-id="d280a-125">之後，如果目標節點的設定偏離設定檔，DSC 就會報告記錄檔中的差異，然後嘗試調整目標節點設定，以符合設定檔。</span><span class="sxs-lookup"><span data-stu-id="d280a-125">Thereafter, if the configuration of the target node drifts from the configuration file, DSC reports the discrepancy in logs, and then attempts to adjust the target node configuration to bring in compliance with the configuration file.</span></span>
- <span data-ttu-id="d280a-126">**ConfigurationModeFrequencyMins**：代表 DSC 背景應用程式嘗試在目標節點上實作目前設定的頻率 (以分鐘為單位)。</span><span class="sxs-lookup"><span data-stu-id="d280a-126">**ConfigurationModeFrequencyMins**: Represents the frequency (in minutes) at which the background application of DSC attempts to implement the current configuration on the target node.</span></span> <span data-ttu-id="d280a-127">預設值為 15。</span><span class="sxs-lookup"><span data-stu-id="d280a-127">The default value is 15.</span></span> <span data-ttu-id="d280a-128">這個值可以搭配 RefreshMode 設定。</span><span class="sxs-lookup"><span data-stu-id="d280a-128">This value can be set in conjunction with RefreshMode.</span></span> <span data-ttu-id="d280a-129">當 RefreshMode 設定為 PULL 時，目標節點會以由 RefreshFrequencyMins 所設定的間隔連絡設定服務，並下載目前的設定。</span><span class="sxs-lookup"><span data-stu-id="d280a-129">When RefreshMode is set to PULL, the target node contacts the configuration service at an interval set by RefreshFrequencyMins and downloads the current configuration.</span></span> <span data-ttu-id="d280a-130">不論 RefreshMode 值為何，在 ConfigurationModeFrequencyMins 所設定的間隔中，一致性引擎會套用已下載至目標節點的最新設定。</span><span class="sxs-lookup"><span data-stu-id="d280a-130">Regardless of the RefreshMode value, at the interval set by ConfigurationModeFrequencyMins, the consistency engine applies the latest configuration that was downloaded to the target node.</span></span> <span data-ttu-id="d280a-131">RefreshFrequencyMins 應為 ConfigurationModeFrequencyMins 的整數倍數。</span><span class="sxs-lookup"><span data-stu-id="d280a-131">RefreshFrequencyMins should be set to an integer multiple of ConfigurationModeFrequencyMins.</span></span>
- <span data-ttu-id="d280a-132">**Credential**：表示存取遠端資源所需的認證 (如同 Get-Credential)，例如連絡設定服務。</span><span class="sxs-lookup"><span data-stu-id="d280a-132">**Credential**: Indicates credentials (as with Get-Credential) required to access remote resources, such as to contact the configuration service.</span></span>
- <span data-ttu-id="d280a-133">**DownloadManagerCustomData**：代表陣列，其中包含下載管理員特定的自訂資料。</span><span class="sxs-lookup"><span data-stu-id="d280a-133">**DownloadManagerCustomData**: Represents an array that contains custom data specific to the download manager.</span></span>
- <span data-ttu-id="d280a-134">**DownloadManagerName**：指出設定和模組下載管理員的名稱。</span><span class="sxs-lookup"><span data-stu-id="d280a-134">**DownloadManagerName**: Indicates the name of the configuration and module download manager.</span></span>
- <span data-ttu-id="d280a-135">**RebootNodeIfNeeded**：將此設為 `$true`，以允許資源使用 `$global:DSCMachineStatus` 旗標來重新啟動節點。</span><span class="sxs-lookup"><span data-stu-id="d280a-135">**RebootNodeIfNeeded**: Set this to `$true` to allow resources to reboot the Node using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="d280a-136">否則，您將必須手動重新啟動任何設定所需的節點。</span><span class="sxs-lookup"><span data-stu-id="d280a-136">Otherwise, you will have to manually reboot the node for any configuration that requires it.</span></span> <span data-ttu-id="d280a-137">預設值為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="d280a-137">The default value is `$false`.</span></span> <span data-ttu-id="d280a-138">若要在重新啟動條件是由 DSC 以外的項目 (例如 Windows Installer) 所制定的情況下使用此設定，請將此設定與 [xPendingReboot](https://github.com/powershell/xpendingreboot) \(英文\) 模組結合。</span><span class="sxs-lookup"><span data-stu-id="d280a-138">To use this setting when a reboot condition is enacted by something other than DSC (such as Windows Installer), combine this setting with the [xPendingReboot](https://github.com/powershell/xpendingreboot) module.</span></span>
- <span data-ttu-id="d280a-139">**RefreshFrequencyMins**：於您設定提取服務時使用。</span><span class="sxs-lookup"><span data-stu-id="d280a-139">**RefreshFrequencyMins**: Used when you have set up a pull service.</span></span> <span data-ttu-id="d280a-140">代表的本機設定管理員連絡提取服務來下載目前設定的頻率 (以分鐘為單位)。</span><span class="sxs-lookup"><span data-stu-id="d280a-140">Represents the frequency (in minutes) at which the Local Configuration Manager contacts a pull service to download the current configuration.</span></span> <span data-ttu-id="d280a-141">這個值可以搭配 ConfigurationModeFrequencyMins 設定。</span><span class="sxs-lookup"><span data-stu-id="d280a-141">This value can be set in conjunction with ConfigurationModeFrequencyMins.</span></span> <span data-ttu-id="d280a-142">當 RefreshMode 設定為 PULL 時，目標節點會以由 RefreshFrequencyMins 所設定的間隔連絡提取服務，並下載目前的設定。</span><span class="sxs-lookup"><span data-stu-id="d280a-142">When RefreshMode is set to PULL, the target node contacts the pull service at an interval set by RefreshFrequencyMins and downloads the current configuration.</span></span> <span data-ttu-id="d280a-143">在 ConfigurationModeFrequencyMins 所設定的間隔中，一致性引擎接著會套用已下載至目標節點的最新設定。</span><span class="sxs-lookup"><span data-stu-id="d280a-143">At the interval set by ConfigurationModeFrequencyMins, the consistency engine then applies the latest configuration that was downloaded to the target node.</span></span> <span data-ttu-id="d280a-144">如果 RefreshFrequencyMins 未設定為 ConfigurationModeFrequencyMins 的整數倍數，則系統會無條件進位。</span><span class="sxs-lookup"><span data-stu-id="d280a-144">If RefreshFrequencyMins is not set to an integer multiple of ConfigurationModeFrequencyMins, the system will round it up.</span></span> <span data-ttu-id="d280a-145">預設值為 30。</span><span class="sxs-lookup"><span data-stu-id="d280a-145">The default value is 30.</span></span>
- <span data-ttu-id="d280a-146">**RefreshMode**：可能的值為 **Push** (預設值) 和 **Pull**。</span><span class="sxs-lookup"><span data-stu-id="d280a-146">**RefreshMode**: Possible values are **Push** (the default) and **Pull**.</span></span> <span data-ttu-id="d280a-147">在 [推送] 設定中，您必須使用任何用戶端電腦，在每個目標節點上放置設定檔。</span><span class="sxs-lookup"><span data-stu-id="d280a-147">In the "push" configuration, you must place a configuration file on each target node, using any client computer.</span></span> <span data-ttu-id="d280a-148">在 [提取] 模式中，您必須設定提取服務，本機設定管理員才能連絡及存取設定檔。</span><span class="sxs-lookup"><span data-stu-id="d280a-148">In the "pull" mode, you must set up a pull service for Local Configuration Manager to contact and access the configuration files.</span></span>

> [!NOTE]
> <span data-ttu-id="d280a-149">LCM 會根據以下項目，啟動 **ConfigurationModeFrequencyMins**：</span><span class="sxs-lookup"><span data-stu-id="d280a-149">The LCM starts the **ConfigurationModeFrequencyMins** cycle based on:</span></span>
>
> - <span data-ttu-id="d280a-150">新的中繼設定會使用 `Set-DscLocalConfigurationManager` 來套用</span><span class="sxs-lookup"><span data-stu-id="d280a-150">A new metaconfig is applied using `Set-DscLocalConfigurationManager`</span></span>
> - <span data-ttu-id="d280a-151">電腦重新啟動</span><span class="sxs-lookup"><span data-stu-id="d280a-151">A machine restart</span></span>
>
> <span data-ttu-id="d280a-152">針對任何計時器處理序發生當機的狀況，會在 30 秒內偵測該狀況，並重新啟動循環。</span><span class="sxs-lookup"><span data-stu-id="d280a-152">For any condition where the timer process experiences a crash, that will be detected within 30 seconds and the cycle will be restarted.</span></span>
> <span data-ttu-id="d280a-153">若此作業的期間超過所設定循環頻率，則下一個計時器便不會啟動，並可能使同時作業延遲啟動循環。</span><span class="sxs-lookup"><span data-stu-id="d280a-153">A concurrent operation could delay the cycle from being started, if the duration of this operation exceeds the configured cycle frequency, the next timer will not start.</span></span>
>
> <span data-ttu-id="d280a-154">例如，中繼設定已設定為 15 分鐘的提取頻率，而提取動作則在 T1 發生。</span><span class="sxs-lookup"><span data-stu-id="d280a-154">Example, the metaconfig is configured at a 15 minute pull frequency and a pull occurs at T1.</span></span>  <span data-ttu-id="d280a-155">節點沒有在 16 分鐘內完成工作。</span><span class="sxs-lookup"><span data-stu-id="d280a-155">The Node does not finish work for 16 minutes.</span></span>  <span data-ttu-id="d280a-156">這樣便會忽略第一個 15 分鐘循環，而下一個提取則會在 T1+15+15 時發生。</span><span class="sxs-lookup"><span data-stu-id="d280a-156">The first 15 minute cycle is ignored, and next pull will happen at T1+15+15.</span></span>

### <a name="example-of-updating-local-configuration-manager-settings"></a><span data-ttu-id="d280a-157">更新本機設定管理員設定的範例</span><span class="sxs-lookup"><span data-stu-id="d280a-157">Example of updating Local Configuration Manager settings</span></span>

<span data-ttu-id="d280a-158">您可以更新目標節點的本機設定管理員設定，方法是在設定指令碼中節點區塊內加入 **LocalConfigurationManager** 區塊，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d280a-158">You can update the Local Configuration Manager settings of a target node by including a **LocalConfigurationManager** block inside the node block in a configuration script, as shown in the following example.</span></span>

```powershell
Configuration ExampleConfig
{
    Node "Server001"
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

<span data-ttu-id="d280a-159">執行上述範例中的指令碼會產生 MOF 檔案，該檔案指定並儲存所需的設定。</span><span class="sxs-lookup"><span data-stu-id="d280a-159">Running the script in the previous example generates a MOF file that specifies and stores the desired settings.</span></span>
<span data-ttu-id="d280a-160">若要套用設定，您可以使用 **Set-DscLocalConfigurationManager** Cmdlet，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d280a-160">To apply the settings, you can use the **Set-DscLocalConfigurationManager** cmdlet, as shown in the following example.</span></span>

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> [!NOTE]
> <span data-ttu-id="d280a-161">針對 **Path** 參數，當您叫用前一個範例中的設定時，您指定的路徑必須與您為 **OutputPath** 參數所指定的路徑相同。</span><span class="sxs-lookup"><span data-stu-id="d280a-161">For the **Path** parameter, you must specify the same path that you specified for the **OutputPath** parameter when you invoked the configuration in the previous example.</span></span>

<span data-ttu-id="d280a-162">若要查看目前本機設定管理員設定，您可以使用 **Get-DscLocalConfigurationManager** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d280a-162">To see the current Local Configuration Manager settings, you can use the **Get-DscLocalConfigurationManager** cmdlet.</span></span>
<span data-ttu-id="d280a-163">如果您叫用的這個 Cmdlet 不含任何參數，依預設會取得您用來執行此 Cmdlet 之節點的本機設定管理員設定。</span><span class="sxs-lookup"><span data-stu-id="d280a-163">If you invoke this cmdlet with no parameters, by default it will get the Local Configuration Manager settings for the node on which you run it.</span></span>
<span data-ttu-id="d280a-164">若要指定另一個節點，請使用這項 Cmdlet 的 **CimSession** 參數。</span><span class="sxs-lookup"><span data-stu-id="d280a-164">To specify another node, use the **CimSession** parameter with this cmdlet.</span></span>
