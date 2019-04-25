---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 偵錯 DSC 資源
ms.openlocfilehash: c088e13a25ba31ceebaf52b2d24b5d32b96ae2fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076798"
---
# <a name="debugging-dsc-resources"></a>偵錯 DSC 資源

> 適用於：Windows PowerShell 5.0

在 PowerShell 5.0 中，預期狀態設定 (DSC) 引進了新功能，可讓您將 DSC 資源當作已套用的設定偵錯。

## <a name="enabling-dsc-debugging"></a>啟用 DSC 偵錯
偵錯資源之前，您必須先呼叫 [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) Cmdlet 啟用偵錯。
這個 Cmdlet 使用強制參數 **BreakAll**。

您可以查看呼叫 [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) 的結果，確認是否已啟用偵錯。

下列 PowerShell 輸出會顯示啟用偵錯的結果：


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


## <a name="starting-a-configuration-with-debug-enabled"></a>啟動啟用偵錯的設定
若要偵錯 DSC 資源，您要啟動設定呼叫該資源。
本例中，我們會探討呼叫 **WindowsFeature** 資源的簡單設定，確定已安裝 "WindowsPowerShellWebAccess" 功能：

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
編譯設定之後，再呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) 加以啟動。
設定停止的時機為本機設定管理員 (LCM) 叫入設定的第一個資源。
如果使用 `-Verbose` 和 `-Wait` 參數，輸出會顯示您需要輸入的程式行以開始偵錯。

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
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
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
此時，LCM 已呼叫資源且來到第一個中斷點。
輸出中的最後三行會示範如何附加至處理程序，並開始偵錯資源指令碼。

## <a name="debugging-the-resource-script"></a>偵錯資源指令碼

啟動 PowerShell ISE 的新執行個體。
在主控台窗格中，輸入 `Start-DscConfiguration` 輸出的最後三行輸出作為命令，將 `<credentials>` 替換成有效的使用者認證。
您現在應該會看到類似這樣的提示︰

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

此資源指令碼會在指令碼窗格中開啟，且偵錯工具會停在 **Test-TargetResource** 函式的第一行 (以類別為基礎之資源的 **Test()** 方法)。
現在您可以在 ISE 中使用偵錯命令逐步執行資源指令碼、查看變數值、檢視呼叫堆疊，並執行其他工作。 請記住，資源指令碼 (或類別) 中的每一行均已設為中斷點。

## <a name="disabling-dsc-debugging"></a>停用 DSC 偵錯

呼叫 [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) 後，所有對 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) 的呼叫將會導致設定中斷並進入偵錯工具。 若要使設定正常執行，您必須透過呼叫 [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) Cmdlet 來停用偵錯。

>**注意：** 重新開機不會變更 LCM 的偵錯狀態。 若啟用偵錯，則重新開機後啟動設定時仍然會中斷並進入偵錯工具。

## <a name="see-also"></a>另請參閱

- [撰寫自訂的 DSC 資源與 MOF](../resources/authoringResourceMOF.md)
- [使用 PowerShell 類別撰寫自訂的 DSC 資源](../resources/authoringResourceClass.md)
