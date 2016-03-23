# 偵錯 DSC 資源

> 適用於：Windows PowerShell 5.0

在 PowerShell 5.0 中，預期狀態設定 (DSC) 引進了新功能，可讓您將 DSC 資源當做已套用的設定偵錯。

## 啟用 DSC 偵錯
偵錯資源之前，您必須先呼叫 [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx) Cmdlet 啟用偵錯。 這個 Cmdlet 使用強制參數 **BreakAll**。 您可以查看呼叫 [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) 的結果，確認是否啟用偵錯。 下列 PowerShell 輸出會顯示啟用偵錯的結果：


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## 啟動啟用偵錯的設定
若要偵錯 DSC 資源，您要啟動設定呼叫該資源。 本例中，我們會探討呼叫 [WindowsFeature](windowsfeatureResource.md) 資源的簡單設定，確定已安裝 "WindowsPowerShellWebAccess" 功能：

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
編譯設定之後，再呼叫 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) 來啟動它。 設定停止的時機為
本機設定管理員 (LCM) 叫入設定的第一個資源。 如果使用 `-Verbose` 和 `-Wait` 參數，輸出會顯示您需要輸入的程式行
以開始偵錯。

```powershell
PS C:\DebugTest> Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will 
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.  Use the follow
ing commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
此時，LCM 已呼叫資源且來到第一個中斷點。 輸出中的最後三行會示範如何附加至處理程序，並開始偵錯資源指令碼。

## 偵錯資源指令碼

啟動 PowerShell ISE 的新執行個體。 在主控台窗格中，輸入 `Start-DscConifiguration` 輸出的最後三行輸出作為命令，將 `<credentials>` 替換成
有效的使用者認證。 以下為得到的輸出。



<!--HONumber=Feb16_HO4-->
