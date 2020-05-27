---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
title: 預期狀態設定 (DSC) 的已知問題和限制
ms.openlocfilehash: a76c5bb336804c5b384e6b6ba6a705c6049ef7fb
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808694"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>預期狀態設定 (DSC) 的已知問題和限制

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>重大變更：用來加密/解密 DSC 設定密碼的憑證，在安裝 WMF 5.0 RTM 之後可能無法運作

在 WMF 4.0 和 WMF 5.0 Preview 版本中，DSC 不允許組態中的密碼長度超過 121 個字元。 DSC 已強制使用短密碼，即使需要冗長的強式密碼亦同。 這項重大變更允許 DSC 組態中的密碼為任意長度。

**解決方案：** 以 [資料編密] 或 [金鑰編密] 的金鑰使用方式，與 [文件加密增強] 金鑰使用方式 (1.3.6.1.4.1.311.80.1) 重新建立憑證。 如需詳細資訊，請參閱 [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)。

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>DSC Cmdlet 在安裝 WMF 5.0 RTM 之後可能會失敗

`Start-DscConfiguration` 和其他 DSC Cmdlet 可能會在安裝 WMF 5.0 RTM 之後失敗，並傳回下列錯誤：

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

**解決方案：** 在提高權限的 PowerShell 工作階段 (以系統管理員身分執行) 中執行下列命令來刪除 DSCEngineCache.mof︰

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>如果 WMF 5.0 RTM 安裝在 WMF 5.0 Production Preview 之上，DSC Cmdlet 就有可能無法運作

**解決方案：** 在提高權限的 PowerShell 工作階段 (以系統管理員身分執行) 中執行下列命令︰

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>在 DebugMode 中使用 Get-DscConfiguration 時，LCM 可能會陷入不穩定的狀態

如果 LCM 處於 DebugMode，按下 CTRL + C 以停止處理 `Get-DscConfiguration`，可能造成 LCM 進入不穩定狀態，而使得大部分的 DSC Cmdlet 都將無法運作。

**解決方案：** 偵錯 `Get-DscConfiguration` Cmdlet 時，請勿按下 CTRL+C。

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a>Stop-DscConfiguration 在 DebugMode 中可能不會回應

如果 LCM 處於 DebugMode，則嘗試停止 `Get-DscConfiguration` 所啟動的作業時，`Stop-DscConfiguration` 可能不會回應

**解決方案：** 完成對 `Get-DscConfiguration` 所啟動的作業進行偵錯，如[偵錯 DSC 資源](/powershell/scripting/dsc/troubleshooting/debugResource)中所述。

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a>在 DebugMode 中不顯示詳細的錯誤訊息

如果 LCM 處於 **DebugMode**，則 DSC 資源不會顯示詳細的錯誤訊息。

**解決方案：** 停用 **DebugMode** 以查看資源中的詳細訊息

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>DscConfigurationStatus Cmdlet 無法擷取 Invoke-DscResource 作業

使用 `Invoke-DscResource` Cmdlet 直接叫用任何資源的方法之後，就無法透過 `Get-DscConfigurationStatus` 擷取這類作業的記錄。

**解決方案：** 無。

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Get-DscConfigurationStatus 傳回提取循環作業，作為類型**一致性**

將節點設定為 PULL 重新整理模式時，對於每個執行的提取作業，`Get-DscConfigurationStatus` Cmdlet 會將作業類型報告為**一致性**，而非「初始」  。

**解決方案：** 無。

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>Invoke-DscResource Cmdlet 不會以這些作業所產生的順序傳回訊息

`Invoke-DscResource` Cmdlet 不會以 LCM 或 DSC 資源產生它們的順序來傳回詳細資訊、警告和錯誤訊息。

**解決方案：** 無。

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>以 Invoke-DscResource 使用 DSC 資源時，無法輕易偵錯 DSC 資源

當 LCM 在偵錯模式中執行時，`Invoke-DscResource` Cmdlet 不會提供要連線以進行偵錯的 Runspace 相關資訊。 如需詳細資訊，請參閱[偵錯 DSC 資源](/powershell/scripting/dsc/troubleshooting/debugResource)。

**解決方案：** 使用 `Get-PSHostProcessInfo`、`Enter-PSHostProcess`、`Get-Runspace` 及 `Debug-Runspace` Cmdlet 來探索並附加至 Runspace，以對 DSC 資源進行偵錯。

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>相同節點的各種部分組態文件不能有相同的資源名稱

對於部署到單一節點上的多個部分組態，相同的資源名稱會造成執行階段錯誤。

**解決方案：** 在不同的部分設定中使用不同資源名稱 (即使是相同的資源)。

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Start-DscConfiguration –UseExisting 無法使用 -Credential

搭配 **UseExisting** 參數使用 `Start-DscConfiguration` 時，會忽略 **Credential** 參數。 DSC 會使用預設處理序身分識別，繼續作業； 而如果在遠端節點上繼續作業時需要不同的認證，這樣做會導致錯誤。

**解決方案：** 使用遠端 DSC 作業的 CIM 工作階段︰

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>以 IPv6 位址作為 DSC 組態中的節點名稱

在此版本中，不支援以 IPv6 位址作為 DSC 組態指令碼中的節點名稱。

**解決方案：** 無。

## <a name="debugging-of-class-based-dsc-resources"></a>對 `Class-Based` DSC 資源進行偵錯

在此版本中，不支援以類別為基礎的 DSC 資源偵錯。

**解決方案：** 無。

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>在 DSC 以類別為基礎之資源的 $script 範圍中定義的變數和函式，不會在對 DSC 資源的多個呼叫之間保留

如果設定使用任何以類別為基礎的資源，且該資源具有 `$script` 範圍中定義的變數或函式時，對 `Start-DSCConfiguration` 的多個連續呼叫將會失敗。

**解決方案：** 在 DSC 資源類別本身中定義所有變數和函式。 沒有 `$script` 範圍變數/函式。

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>當資源正在使用 PSDscRunAsCredential 時偵錯 DSC 資源

在此版本中，當資源正在使用設定中的 **PSDscRunAsCredential** 屬性時，不支援 DSC 資源偵錯。

**解決方案：** 無。

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>對於 DSC 複合資源不支援 PsDscRunAsCredential

**解決方案：** 使用 Credential 屬性 (如果有的話)。 範例 ServiceSet 和 WindowsFeatureSet

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>Get-DscResource-Syntax 並未正確反映 PsDscRunAsCredential

當資源將 **PsDscRunAsCredential** 標記為強制或不支援它時，**Syntax** 參數就不會正確反映它。

**解決方案：** 無。 不過，使用 IntelliSense 時，在 ISE 中撰寫設定會反映有關 **PsDscRunAsCredential** 屬性的正確中繼資料。

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature 不適用於 Windows 7

**WindowsOptionalFeature** DSC 資源不適用於 Windows 7。 此資源需要 DISM 模組，以及在 Windows 8 起和較新版本 Windows 作業系統中可用的 DISM Cmdlet。

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>針對以類別為基礎的 DSC 資源，Import-DscResource -ModuleVersion 可能無法如預期般運作

如果編譯節點有多個以類別為基礎的 DSC 資源模組版本，`Import-DscResource -ModuleVersion` 就不會挑選指定的版本，並產生下列編譯錯誤。

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**解決方案：** 藉由將 **ModuleSpecification** 物件定義為 **ModuleName** 參數，並指定 **RequiredVersion** 索引鍵來匯入所需的版本，如下所示：

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>某些像登錄資源這樣的 DSC 資源可能會啟動，花費較長的時間來處理要求。

**解決方法 1：** 建立排程工作，定期清除下列資料夾。

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**解決方法 2：** 變更 DSC 設定，清除設定結尾的 *CommandAnalysis* 資料夾。

```powershell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
