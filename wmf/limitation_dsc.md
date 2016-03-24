# 預期狀態設定 (DSC) 的已知問題和限制

重大變更︰用來加密/解密 DSC 組態中密碼的憑證可能無法在安裝 WMF 5.0 RTM 之後執行
--------------------------------------------------------------------------------------------------------------------------------

在 WMF 4.0 和 WMF 5.0 Preview 版本中，DSC 不允許組態中的密碼長度超過 121 個字元。 DSC 已強制使用短密碼，即使需要冗長的強式密碼亦同。 這項重大變更允許 DSC 組態中的密碼為任意長度。

**解決方式︰**以 [資料編密] 或 [金鑰編密] 的金鑰使用方式，與 [文件加密增強] 金鑰使用方式 (1.3.6.1.4.1.311.80.1) 重新建立憑證。 Technet 文章 <https://technet.microsoft.com/en-us/library/dn807171.aspx> 有詳細資訊。


DSC Cmdlet 在安裝 WMF 5.0 RTM 之後可能會失敗
------------------------------------------------------------------------------------
Start-DscConfiguration 和其他 DSC Cmdlet 可能會在安裝 WMF 5.0 RTM 之後失敗，並傳回下列錯誤︰
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**解決方式︰**在提高權限的 PowerShell 工作階段 (以系統管理員身分執行) 中執行下列命令，以刪除 DSCEngineCache.mof︰
    
```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


如果 WMF 5.0 RTM 安裝在 WMF 5.0 Production Preview 之上，DSC Cmdlet 就有可能無法運作
------------------------------------------------------
**解決方式︰**在提高權限的 PowerShell 工作階段 (以系統管理員身分執行) 中執行下列命令︰
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


在 DebugMode 中使用 Get-DscConfiguration 時，LCM 可能會陷入不穩定的狀態
-------------------------------------------------------------------------------

如果 LCM 處於 DebugMode 中，若按下 CTRL + C 來停止 Get-DscConfiguration 執行，可能會造成 LCM 陷入不穩定的狀態，使得大部分的 DSC Cmdlet 將無法運作。

**解決方式︰**在偵錯 Get-DscConfiguration Cmdlet 時，請勿按 CTRL + C。


Stop-DscConfiguration 可能會在 DebugMode 中停止回應
------------------------------------------------------------------------------------------------------------------------
如果 LCM 處於 DebugMode 中，則嘗試停止 Get-DscConfiguration 所啟動的作業時，Stop-DscConfiguration 可能會停止回應

**解決方式︰**完成 Get-DscConfiguration 所啟動作業的偵錯，如〈[DSC 資源指令碼偵錯](#dsc-resource-script-debugging)〉一節中所述。


在 DebugMode 中不顯示詳細的錯誤訊息
-----------------------------------------------------------------------------------
如果 LCM 處於 DebugMode 中，DSC 資源中就不會顯示詳細的錯誤訊息。

**解決方式︰**停用 *DebugMode* 以查看資源中的詳細訊息


DscConfigurationStatus Cmdlet 無法擷取 Invoke-DscResource 作業
--------------------------------------------------------------------------------------
使用 Invoke-DscResource Cmdlet 來直接叫用任何資源方法之後，這類作業的記錄無法透過 Get-DscConfigurationStatus 在稍後擷取。

**解決方式︰**無。


Get-DscConfigurationStatus 傳回提取循環作業，作為類型*一致性*
---------------------------------------------------------------------------------
當節點設定為 PULL 重新整理模式時，對於每個執行的提取作業，Get-DscConfigurationStatus Cmdlet 會報告作業類型，作為*一致性*，而不是*初始*

**解決方式︰**無。

Invoke-DscResource Cmdlet 不會以這些作業所產生的順序傳回訊息
---------------------------------------------------------------------------------
Invoke-DscResource Cmdlet 不會以 LCM 或 DSC 資源產生這些作業的順序傳回詳細、警告和錯誤訊息

**解決方式︰**無。


以 Invoke-DscResource 使用 DSC 資源時，無法輕易偵錯 DSC 資源
-----------------------------------------------------------------------
LCM 在偵錯模式執行時 (如需詳細資訊，請參閱〈[DSC 資源指令碼偵錯](#dsc-resource-script-debugging)〉)，Invoke-DscResource Cmdlet 並不提供連接到 Runspace 以偵錯的資訊。
**解決方式︰**使用 Cmdlets **Get-PSHostProcessInfo**、**Enter-PSHostProcess**、**Get-Runspace** 和 **Debug-Runspace** 探索並附加至 Runspace，以偵錯 DSC 資源。

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```


相同節點的各種部分組態文件不能有相同的資源名稱
------------------------------------------------------------------------------------------

對於部署到單一節點上的多個部分組態，相同的資源名稱會造成執行階段錯誤。

**解決方式︰**在不同的部分組態使用不同的資源名稱 (即使是相同的資源)。


Start-DscConfiguration –UseExisting 無法使用 -Credential
------------------------------------------------------------------

以 – UseExisting 參數使用 Start-DscConfiguration 時，會忽略 –Credential 參數。 DSC 會使用預設處理序身分識別，繼續作業； 而如果在遠端節點上繼續作業時需要不同的認證，這樣做會導致錯誤。

**解決方式︰**使用遠端 DSC 作業的 CIM 工作階段︰
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


以 IPv6 位址作為 DSC 組態中的節點名稱
--------------------------------------------------
在此版本中，不支援以 IPv6 位址作為 DSC 組態指令碼中的節點名稱。

**解決方式︰**無。


以類別為基礎的 DSC 資源偵錯
--------------------------------------
在此版本中，不支援以類別為基礎的 DSC 資源偵錯。

**解決方式︰**無。


在 DSC 以類別為基礎的資源之 $script 範圍中定義的變數和函數，不會在對 DSC 資源的多個呼叫之間保留 
-------------------------------------------------------------------------------------------------------------------------------------

如果組態使用任何以類別為基礎的資源，且該資源具有 $script 範圍中定義的變數或函數時，對 Start-DSCConfiguration 的多個連續呼叫將失敗。

**解決方式︰**在 DSC 資源類別本身中定義所有變數和函數。 不使用 $script 範圍變數/函數。


當資源正在使用 PSDscRunAsCredential 時偵錯 DSC 資源
----------------------------------------------------------------------
在此版本中，當資源正在使用組態中的 *PSDscRunAsCredential* 屬性時，不支援 DSC 資源偵錯。

**解決方式︰**無。


對於 DSC 複合資源不支援 PsDscRunAsCredential
----------------------------------------------------------------

**解決方式︰**使用 Credential 屬性 (如果有的話)。 範例 ServiceSet 和 WindowsFeatureSet


*Get-DscResource-Syntax* 不會正確反映 PsDscRunAsCredential
-------------------------------------------------------------------------
當資源將 PsDscRunAsCredential 標記為強制，或資源對其不支援時，Get-DscResource -Syntax 不會正確反映 PsDscRunAsCredential。

**解決方式︰**無。 不過在使用 IntelliSense 時，撰寫 ISE 中的組態會反映正確的 PsDscRunAsCredential 屬性中繼資料。


WindowsOptionalFeature 不適用於 Windows 7
-----------------------------------------------------

WindowsOptionalFeature 資源不適用於 Windows 7。 此資源需要 DISM 模組，以及在 Windows 8 起和較新版本 Windows 作業系統中可用的 DISM Cmdlet。


將無法執行 Set-DscLocalConfigurationManager，以針對 WMF 4.0 或 WMF 5.0 Production Preview 組建設定中繼組態
---------------------------------------------------------------------------------------------------------------------------------------

對舊版 WMF 執行 Set-DscLocalConfiguration 時，會產生回溯相容性問題。 您會看到新增的 -Force 參數無法在目標電腦上使用的錯誤。
```powershell
Set-DscLocalConfigurationManager -Path . -Verbose -ComputerName WIN-3B576EM3669
VERBOSE: Performing the operation "Start-DscConfiguration: SendMetaConfigurationApply" on target "MSFT_DSCLocalConfigurationManager".
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendMetaConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
The WinRM client cannot process the request. The object contains an unrecognized argument: "Force". Verify that the spelling of the argument name is correct.
+ CategoryInfo : MetadataError: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : HRESULT 0x803381e1
+ PSComputerName : WIN-3B576EM3669
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Set-DscLocalConfigurationManager finished in 0.121 seconds.
```
**解決方式︰**遵循下列步驟使用 Invoke-CimMethod 直接呼叫基礎 CIM 方法，以設定中繼組態。
```powershell
$computerName = "WIN-3B576EM3669"
$mofPath = "C:\$computerName.meta.mof"
$configurationData = [Byte[]][System.IO.File]::ReadAllBytes($mofPath)
$totalSize = [System.BitConverter]::GetBytes($configurationData.Length + 4 )
$configurationData = $totalSize + $configurationData
Invoke-CimMethod -Namespace root/microsoft/windows/desiredstateconfiguration -Class MSFT_DSCLocalConfigurationManager -Name SendMetaConfigurationApply -Arguments @{ConfigurationData = [Byte[]]$configurationData} -Verbose -ComputerName $computerName
VERBOSE: Performing the operation "Invoke-CimMethod: SendMetaConfigurationApply" on target "MSFT_DSCLocalConfigurationManager".
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendMetaConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/microsoft/windows/desiredstateconfiguration'.
VERBOSE: An LCM method call arrived from computer WIN-3B576EM3669 with user sid S-1-5-21-2127521184-1604012920-1887927527-5557045.
VERBOSE: [WIN-3B576EM3669]: LCM: [ Start Set ]
VERBOSE: [WIN-3B576EM3669]: LCM: [ Start Resource ] [MSFT_DSCMetaConfiguration]
VERBOSE: [WIN-3B576EM3669]: LCM: [ Start Set ] [MSFT_DSCMetaConfiguration]
VERBOSE: [WIN-3B576EM3669]: LCM: [ End Set ] [MSFT_DSCMetaConfiguration] in 0.4060 seconds.
VERBOSE: [WIN-3B576EM3669]: LCM: [ End Resource ] [MSFT_DSCMetaConfiguration]
VERBOSE: [WIN-3B576EM3669]: LCM: [ End Set ] in 0.4807 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<!--HONumber=Mar16_HO2-->
