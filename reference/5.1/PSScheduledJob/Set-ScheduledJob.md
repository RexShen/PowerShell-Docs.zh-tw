---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJob
ms.openlocfilehash: 6144d9f19b86727bc09d07e94f4bcf158e3b7071
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387901"
---
# Set-ScheduledJob

## 概要
變更排程工作。

## SYNTAX

### ScriptBlock (預設值)

```
Set-ScheduledJob [-Name <String>] [-ScriptBlock <ScriptBlock>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### FilePath

```
Set-ScheduledJob [-Name <String>] [-FilePath <String>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### 執行

```
Set-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-ClearExecutionHistory] [-PassThru]
 [<CommonParameters>]
```

## DESCRIPTION
**Set-ScheduledJob** Cmdlet 會變更排程工作的屬性，例如工作執行的命令或執行工作所需的認證。
您也可以使用它來清除排程工作的執行記錄。

若要使用此 Cmdlet，請先使用 Get-ScheduledJob Cmdlet 來取得排程工作。
然後，使用管線將排程工作傳送至 **register-scheduledjob** ，或將工作儲存在變數中，然後使用 *InputObject* 參數來識別工作。
使用 **Set-ScheduledJob** 的其他參數來變更工作屬性或清除執行記錄。

雖然您可以使用 **Set-ScheduledJob** 變更排程工作的觸發程序和選項，但是 Add-JobTrigger、Set-JobTrigger 和 Set-ScheduledJobOption Cmdlet 提供更簡單的方式讓您完成那些工作。
若要建立新的排程工作，請使用 Register-ScheduledJob Cmdlet。

**Register-scheduledjob** 的 *Trigger* 參數會加入一個或多個工作觸發程式來啟動工作。
*觸發* 程式參數是選擇性的，因此您可以在建立排程工作時新增觸發程式、稍後新增工作觸發程式、新增 *RunNow* 參數以立即啟動工作、使用 Start-Job Cmdlet 來立即啟動作業，或將 untriggered 排程工作儲存為其他作業的範本。

**Set-ScheduledJob** 為 Windows PowerShell 內含之 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：變更工作執行的指令碼

```
PS C:\> Get-ScheduledJob -Name "Inventory"
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-Inventory.ps1             True

The second command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job. A pipeline operator (|) sends the scheduled job to the **Set-ScheduledJob** cmdlet. The **Set-ScheduledJob** cmdlet uses the *Script* parameter to specify a new script, Get-FullInventory.ps1. The command uses the *Passthru* parameter to return the scheduled job after the change.
PS C:\> Get-ScheduledJob -Name "Inventory" | Set-ScheduledJob -FilePath "C:\Scripts\Get-FullInventory.ps1" -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-FullInventory.ps1         True
```

此範例顯示如何變更排程工作中執行的指令碼。

第一個命令會使用 Get-ScheduledJob Cmdlet 來取得清查排程工作。
輸出會顯示該工作執行 Get-Inventory.ps1 指令碼。

此命令並非必要；包含此命令僅為顯示指令碼變更的效果。

### 範例 2：刪除排程工作的執行記錄

```
PS C:\> Get-ScheduledJob BackupArchive | Set-ScheduledJob -ClearExecutionHistory
```

此命令會刪除 BackupArchive 排程工作的目前執行記錄與儲存的工作結果。

此命令會使用 Get-ScheduledJob Cmdlet 來取得 BackupArchive 排程工作。
管線運算子 (|) 會將工作傳送至 **Set-ScheduledJob** Cmdlet 以變更它。
**Register-scheduledjob** 指令 Cmdlet 會使用 *ClearExecutionHistory* 參數來刪除執行歷程記錄和儲存的結果。

如需排程工作之執行記錄與儲存的工作結果的詳細資訊，請參閱 about_Scheduled_Jobs。

### 範例 3：變更遠端電腦上的排程工作

```
PS C:\> Invoke-Command -Computer "Server01, Server02" -ScriptBlock {Get-ScheduledJob | Set-ScheduledJob -InitializationScript \\SrvA\Scripts\SetForRun.ps1}
```

此命令會變更 Server01 與 Server02 電腦上所有排程工作的初始化指令碼。

此命令會使用 Invoke-Command Cmdlet，在 Server01 和 Server02 電腦上執行命令。

遠端命令的開頭是可取得電腦上所有排程工作的 Get-ScheduledJob 命令。
排程的工作會以管道傳送至 **register-scheduledjob** Cmdlet，這會將初始化腳本變更為 SetForRun.ps1。

## PARAMETERS

### -ArgumentList
指定由 *FilePath* 參數所指定之指令碼的參數值，或指定由 *ScriptBlock* 參數所指定之命令的參數值。

```yaml
Type: System.Object[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentication
指定用來驗證使用者認證的機制。
此參數可接受的值為：

- 預設
- 基本
- Credssp
- Digest
- Kerberos
- 交涉
- NegotiateWithImplicitCredential

預設值為 Default。 如需此參數值的詳細資訊，請參閱 PowerShell SDK 中的 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism) 。

注意：使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。
此機制會使得遠端作業的安全性風險變高。
若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ScriptBlock, FilePath
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClearExecutionHistory
刪除排程工作的目前執行記錄與儲存的結果。

工作執行記錄與工作結果會隨著排程工作儲存在工作建立所在電腦的 $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs 目錄。
若要查看執行記錄，請使用 Get-Job Cmdlet。
若要取得工作結果，請使用 Receive-Job Cmdlet。

此參數不會影響 [工作排程器] 寫入到 Windows 事件記錄檔的事件，而且它不會使得 Windows PowerShell 停止儲存工作結果。
若要管理儲存的工作結果數目，請使用 *MaxResultCount* 參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Execution
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
指定具有執行排程工作之權限的使用者帳戶。
預設為目前使用者。

輸入使用者名稱（例如 User01 或 Domain01\User01），或輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 中的物件。
若您只輸入使用者名稱，將會提示您輸入密碼。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath
指定排程工作所執行的指令碼。
輸入本機電腦上之 .ps1 檔案的路徑。
若要指定指令碼參數的預設值，請使用 *ArgumentList* 參數。
每個排程工作都必須有 *ScriptBlock* 或 *FilePath* 值。

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript
指定 Windows PowerShell 指令碼 (.ps1) 的完整路徑。
初始化指令碼會在執行 *ScriptBlock* 參數所指定的命令或 *FilePath* 參數所指定的指令碼之前，在針對背景工作所建立的工作階段中執行。
您可以使用初始化指令碼來設定工作階段，例如新增檔案/函式/別名、建立目錄，或檢查先決條件。

若要指定會執行主要工作命令的指令碼，請使用 *FilePath* 參數。

如果初始化腳本產生錯誤（包括非終止錯誤），則排程工作的目前實例不會執行，且其狀態會是 [失敗]。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
指定要變更的排程工作。
輸入包含 **>scheduledjobdefinition** 物件的變數，或輸入可取得 **>scheduledjobdefinition** 物件的命令或運算式，例如 Get-ScheduledJob 命令。
您也可以使用管線將 **ScheduledJobDefinition** 物件傳送至 **Set-ScheduledJob** 。

若指定多個排程工作， **Set-ScheduledJob** 會對所有工作進行相同的變更。

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MaxResultCount
指定要為排程工作保留幾個工作結果項目。
預設值為 32。

Windows PowerShell 會將每個觸發之排程工作執行個體的執行記錄與結果儲存在磁碟上。
此參數的值決定針對此排程工作儲存的工作執行個體結果數目。
當工作執行個體數目超過此值時，Windows PowerShell 會刪除最舊的工作執行個體結果，以便挪出空間儲存最新工作執行個體結果。

作業執行歷程記錄和工作結果會儲存在工作建立所在電腦的 $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs \\ \<JobName\> \Output \\ \<Timestamp\> 目錄中。
若要查看執行記錄，請使用 Get-Job Cmdlet。
若要取得工作結果，請使用 Receive-Job Cmdlet。

*MaxResultCount* 參數會設定排程工作之 ExecutionHistoryLength 屬性的值。

若要刪除目前的執行記錄與工作結果，請使用 *ClearExecutionHistory* 參數。

```yaml
Type: System.Int32
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
指定排程工作的新名稱與排程工作的執行個體。
此名稱在本機電腦上必須是唯一的。

若要識別要變更的排程工作，請使用 *InputObject* 參數或使用管線將排程工作從 Get-ScheduledJob 傳送至 **Set-ScheduledJob** 。

此參數不會變更磁碟上的工作執行個體名稱。
它只會影響此命令完成後啟動的工作執行個體。

```yaml
Type: System.String
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru
傳回代表您正在使用之項目的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAs32
在 32 位元處理程序中執行排程工作。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunEvery

用來指定執行作業的頻率。 例如，使用此選項可每隔15分鐘執行一次作業。

```yaml
Type: System.TimeSpan
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunNow
在 **register-scheduledjob** 指令程式執行之後，立即啟動作業。
此參數可減少在登錄後觸發 [工作排程器] 以立即執行 Windows PowerShell 指令碼的需求，而且不需要使用者建立指定開始日期和時間的觸發程序。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScheduledJobOption
設定排程工作的選項。
輸入 **ScheduledJobOptions** 物件，例如您使用 New-ScheduledJobOption Cmdlet 或雜湊表值建立的物件。

您可以在登錄排程工作時設定排程工作的選項，或使用 Set-ScheduledJobOption 或 **Set-ScheduledJob** Cmdlet 來設定或變更選項。

許多選項與其預設值會決定排程工作是否會執行以及執行時間。
排定工作之前，請務必檢閱這些選項。
如需排程工作選項的描述 (包括預設值)，請參閱 New-ScheduledJobOption。

若要提交雜湊表，請使用下列索引鍵。
在下列雜湊表中，索引鍵隨著其預設值顯示。

`@{# Power SettingsStartIfOnBattery=$False;StopIfGoingOnBattery=$True; WakeToRun=$False; # Idle SettingsStartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False;# Security settingsShowInTaskScheduler=$TrueRunElevated=$False;# MiscRunWithoutNetwork=$False;DoNotAllowDemandStart=$False;MultipleInstancePolicy=IgnoreNew# Can be IgnoreNew, Parallel, Queue, StopExisting}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock
指定排程工作執行的命令。
使用大括弧 ( { } ) 括住命令以建立指令碼區塊。
若要指定命令參數的預設值，請使用 *ArgumentList* 參數。

每個 Register-ScheduledJob 命令都必須使用 *ScriptBlock* 或 *FilePath* 參數。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Trigger
指定排程工作的觸發程序。
輸入一或多個 **ScheduledJobTrigger** 物件，例如 New-JobTrigger Cmdlet 傳回的物件，或輸入由工作觸發程序索引鍵與值組成的雜湊表。

工作觸發程式會在一次性或週期性排程或事件發生時自動啟動排程工作。

工作觸發程序是選擇性的。
您可以在建立排程工作時新增觸發程式、使用 Add-JobTrigger 或 Register-scheduledjob 指令 **程式** 稍後新增觸發程式，或使用 Start-Job Cmdlet 來立即啟動排程工作。
您也可以建立及維護沒有工作觸發程序的排程工作。

若要提交雜湊表，請使用下列索引鍵。

`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (或任何有效的時間字串) ; `DaysOfWeek="Monday", "Wednesday"` (或日期名稱的任何組合) ; `Interval=2` (或任何有效的頻率間隔) ; `RandomDelay="30minutes"` (或任何有效的 timespan 字串) ; `User="Domain1\User01"` (或任何有效的使用者;只能搭配 AtLogon 頻率值使用) 

}

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
您可以使用管線傳送排程工作至 **Set-ScheduledJob** 。

## 輸出

### 無或 Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
若使用 *Passthru* 參數， **Set-ScheduledJob** 會傳回已變更的排程工作。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[Add-JobTrigger](Add-JobTrigger.md)

[Disable-JobTrigger](Disable-JobTrigger.md)

[Disable-ScheduledJob](Disable-ScheduledJob.md)

[Enable-JobTrigger](Enable-JobTrigger.md)

[Enable-ScheduledJob](Enable-ScheduledJob.md)

[Get-JobTrigger](Get-JobTrigger.md)

[Get-ScheduledJob](Get-ScheduledJob.md)

[Get-ScheduledJobOption](Get-ScheduledJobOption.md)

[New-JobTrigger](New-JobTrigger.md)

[New-ScheduledJobOption](New-ScheduledJobOption.md)

[Register-ScheduledJob](Register-ScheduledJob.md)

[Remove-JobTrigger](Remove-JobTrigger.md)

[Set-JobTrigger](Set-JobTrigger.md)

[Set-ScheduledJob](Set-ScheduledJob.md)

[Set-ScheduledJobOption](Set-ScheduledJobOption.md)

[Unregister-ScheduledJob](Unregister-ScheduledJob.md)
