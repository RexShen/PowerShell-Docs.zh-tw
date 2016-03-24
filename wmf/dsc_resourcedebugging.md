# DSC 資源指令碼偵錯
WMF 5.0 Production Preview 支援在目標節點上執行時，偵錯 DSC 資源指令碼。 在較舊的 WMF 5.0 版本中，我們加入了進階指令碼偵錯功能，能夠連線至本機處理序 (Get-PSHostProcessInfo、Enter-PSHostProcessInfo、Exit-PSHostProcessInfo)、列舉處理序中的所有 runspace，以及在處理序中為隨意自定 runspace 進行偵錯 (Get-Runspace, Debug-Runspace)。

DSC 資源指令碼偵錯是藉由加上兩個新的 Cmdlet 來組建這項工作。

##語法
**啟用-DscDebug**
Enable-DscDebug \[-BreakAll\] \[-CimSession <CIM 工作階段\[\]>\] \[-ThrottleLimit <int>\] \[-AsJob\] \[-WhatIf\] \[-Confirm\] \[<一般參數>\]

**Disable-DscDebug**
Disable-DscDebug \[-CimSession <CIM 工作階段\[\]>\] \[-ThrottleLimit <int>\] \[-AsJob\] \[-WhatIf\] \[-Confirm\] \[<一般參數>\]

##一般工作流程


```PowerShell
PS C:\Test> Enable-DscDebug –BreakAll

PS C:\Test> Start-DscConfiguration -path .\TestConfig2 -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration,'className' = MSFT\_DSCLocalConfigurationManager,'methodName' = SendConfigurationApply'.
VERBOSE: An LCM method call arrived from computer MGMT-10001-827 with user sid S-1-5-21-397955417-626881126-188441444-3860663.
VERBOSE: [MGMT-10001-827]: LCM: [ Start Set ]
WARNING: [MGMT-10001-827]: [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode. Resource script processing will be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [MGMT-10001-827]: [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_EnvironmentResource\MSFT_EnvironmentResource.psm1 in force mode.
VERBOSE: [MGMT-10001-827]: LCM: [ Start Resource ] [[Environment]e1]
VERBOSE: [MGMT-10001-827]: LCM: [ Start Test ] [[Environment]e1]
VERBOSE: [MGMT-10001-827]: [[Environment]e1] Importing the module MSFT_EnvironmentResource in force mode.
WARNING: [MGMT-10001-827]: [[Environment]e1] Resource is waiting for PowerShell script debugger to attach. Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName MGMT-10001-827 -Credential <credentials>
Enter-PSHostProcess -Id 2640 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 3

PS C:\Test> Disable-DscDebug
```
現在讓我們看看這些命令，以及它們的功能︰

**啟用-DscDebug –BreakAll**
搭配 BreakAll 的 Enable-DscDebug Cmdlet 將 DSC LCM 設定為在 Break All 模式下執行 Get-TargetResource、Set-TargetResource 及 Test-TargetResource 指令碼。 這代表此指令碼會在第一個指令碼陳述式上停止，並等候附加偵錯工具。 您可以使用 Windows PowerShell 遠端連線到目標電腦，並將 Windows PowerShell 偵錯工具附加至 LCM 處理序和 Runspace 以偵錯指令碼。 執行這項操作之後，您可以用一般的 Windows PowerShell 方式設定中斷點及偵錯指令碼。

**Start-DscConfiguration -path .\TestConfig2 -Wait -Verbose**

這樣就能啟動 DSC，但如先前所述，因為目標節點啟用了偵錯模式，它會在 LCM 執行第一個 DSC 資源時停止。

為了啟動偵錯工作階段，先執行 Start-DscConfiguration，之後再執行警告訊息中所示的命令，接著將用戶端 Windows PowerShell 指令碼偵錯工具附加至適當的電腦、處理、應用程式定義域和 Runspace。

* 執行此命令可選擇性地使用 Windows PowerShell 遠端以連線到目標電腦。 如果您已經有遠端桌面連線的話，請略過此步驟。
```PowerShell
Enter-PSSession -ComputerName MGMT-10001-827
```
* 此命令將附加到 DSC LCM 主機處理序和正在執行資源指令碼的應用程式網域。
```PowerShell
Enter-PSHostProcess -Id 2640 -AppDomainName DscPsPluginWkr\_AppDomain
```
*  最後一項命令可讓您為執行指令碼的 DSC Runspace 偵錯。
```PowerShell
Debug-Runspace -Id 3
```
![](images/DscResourceDebugging.jpg)

附加偵錯工具後，將行中斷點設定到您要調查指令碼執行的地方，接著執行 **continue** 偵錯工具命令，讓指令碼在偵錯工具中執行。 當您完成偵錯，您可以藉由鍵入 **quit** 偵錯工具命令停止正在執行的指令碼，或者執行 **detach** 偵錯工具命令讓指令碼在沒有偵錯工具的情形下繼續執行。

請注意 ***all*** 資源指令碼在偵錯工具中停止了。 這代表 Test-TargetResoruce、Set-TargetResource 和 Get-TargetResource 指令碼會依序在偵錯工具中停止。 如果您不想偵錯資源指令碼，您可以執行此命令來結束 Runspace 中的偵錯模式。

Disable-RunspaceDebug -RunspaceId 3

您也可以藉由執行 Debug-Runspace，然後立即執行 **detach** 命令以附加偵錯工具。

完成偵錯資源指令碼後，您應該藉由執行下列命令停止 DSC 設定。

Stop-DscConfiguration –Force

最後，您必須重新設定目標電腦 LCM 以停用偵錯模式，方法為使用 Disable-DscDebug Cmdlet。<!--HONumber=Mar16_HO2-->
