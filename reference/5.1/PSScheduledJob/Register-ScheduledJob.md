---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/register-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ScheduledJob
ms.openlocfilehash: 89887474142490a71d372577576fb0059b4ff12e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202995"
---
# Register-ScheduledJob

## 概要
建立排程工作。

## SYNTAX

### ScriptBlock (預設值)

```
Register-ScheduledJob [-ScriptBlock] <ScriptBlock> [-Name] <String>
 [-Trigger <ScheduledJobTrigger[]>] [-InitializationScript <ScriptBlock>] [-RunAs32]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-ScheduledJobOption <ScheduledJobOptions>] [-ArgumentList <Object[]>] [-MaxResultCount <Int32>]
 [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilePath

```
Register-ScheduledJob [-FilePath] <String> [-Name] <String> [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-ArgumentList <Object[]>] [-MaxResultCount <Int32>] [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Register-ScheduledJob`Cmdlet 會在本機電腦上建立排程工作。

排程工作是一種 Windows PowerShell 背景工作，可以在單次或週期性排程上自動啟動。 排程的工作會儲存在磁片上，並在工作排程器中註冊。
您可以在工作排程器中管理工作，也可以使用 Windows PowerShell 中的排程工作 Cmdlet 來管理作業。

當排程工作啟動時，它會建立排程工作的實例。 排程工作執行個體類似 Windows PowerShell 背景工作，但排程工作的結果會儲存在磁碟上。 使用工作 Cmdlet （例如 `Start-Job` 、和） `Get-Job` `Receive-Job` 來啟動、查看和取得工作實例的結果。

用 `Register-ScheduledJob` 來建立新的排程工作。 若要指定排程工作執行的命令，請使用 **ScriptBlock** 參數。 若要指定工作執行的腳本，請使用 **FilePath** 參數。

Windows PowerShell 排程工作會使用工作排程器用於排程工作的相同工作觸發程式和工作選項。

的 **觸發** 程式參數 `Register-ScheduledJob` 會加入一個或多個工作觸發程式，以啟動作業。 **觸發** 程式參數是選擇性的，因此您可以在建立排程工作時新增觸發程式、稍後新增工作觸發程式、新增 **RunNow** 參數以立即啟動工作、使用 `Start-Job` Cmdlet 隨時啟動作業，或將 untriggered 排程工作儲存為其他作業的範本。

**Options** 參數可讓您自訂排程工作的選項設定。 **Options** 參數是選擇性的，因此您可以在建立排程工作時設定工作選項，或隨時變更工作選項。 因為工作選項設定可能會使得排程工作無法如預期般執行，因此請務必謹慎檢閱及設定工作選項。

`Register-ScheduledJob` 是 **PSScheduledJob** 模組中包含在 Windows PowerShell 中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 **PSScheduledJob** 課程模組中的相關文章。
匯入 **PSScheduledJob** 模組，然後輸入： `Get-Help about_Scheduled*` 或查看 [about_Scheduled_Jobs](./about/about_scheduled_jobs.md)。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：建立排程工作

此範例會在本機電腦上建立排程工作。

```powershell
Register-ScheduledJob -Name "Archive-Scripts" -ScriptBlock {
  Get-ChildItem $home\*.ps1 -Recurse |
    Copy-Item -Destination "\\Server\Share\PSScriptArchive"
}
```

`Register-ScheduledJob` 使用 **Name** 參數來建立封存 **-腳本** 排程工作。
**ScriptBlock** 參數會執行 `Get-ChildItem` ，以 `$home` 遞迴方式搜尋目錄中的檔案 `.ps1` 。 `Copy-Item`Cmdlet 會將檔案複製到 **目的地** 參數所指定的目錄。

因為排程工作不包含觸發程式，所以它不會自動啟動。 您可以使用新增工作觸發 `Add-JobTrigger` 程式、使用指令 `Start-Job` 程式依需求啟動作業，或使用排程工作做為其他排程工作的範本。

### 範例2：建立具有觸發程式和自訂選項的排程工作

此範例顯示如何建立具有工作觸發程序與自訂工作選項的排程工作。

```powershell
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
$path = "\\Srv01\Scripts\UpdateVersion.ps1"
Register-ScheduledJob -Name "UpdateVersion" -FilePath $path -ScheduledJobOption $O -Trigger $T
```

`$O`變數會儲存 Cmdlet 所建立的工作選項物件 `New-ScheduledJobOption` 。 選項會啟動排程工作，即使電腦未閒置，也會喚醒電腦以執行工作（如有必要），並允許工作的多個實例在數列中執行。

`$T`變數會儲存 Cmdlet 的結果 `New-JobTrigger` 來建立工作觸發程式，以在下午9:00 點啟動作業。

`$path`變數會儲存腳本檔案的路徑 `UpdateVersion.ps1` 。

`Register-ScheduledJob` 使用 **Name** 參數來建立 **UpdateVersion** 排程工作。
**FilePath** 參數會使用 `$path` 來指定工作執行的腳本。 **ScheduledJobOption** 參數會使用中儲存的工作選項 `$O` 。 **觸發** 程式參數會使用儲存在中的工作觸發程式 `$T` 。

### 範例3：使用雜湊表來指定觸發程式和排程工作選項

此範例的效果與範例2中的命令相同。 它會使用雜湊表來指定 **觸發** 程式和 **ScheduledJobOption** 參數的值，以建立排程工作。 `$O` `$T` 範例2中定義的和變數會以雜湊表取代。

```powershell
$T = @{
  Frequency="Weekly"
  At="9:00PM"
  DaysOfWeek="Monday"
  Interval=2
}
$O = @{
  WakeToRun=$true
  StartIfNotIdle=$false
  MultipleInstancePolicy="Queue"
}
Register-ScheduledJob -Trigger $T -ScheduledJobOption $O -Name UpdateVersion -FilePath "\\Srv01\Scripts\Update-Version.ps1"
```

### 範例4：在遠端電腦上建立排程工作

在此範例中，會在多部遠端電腦上建立 **EnergyData** 排程工作。 排程工作會執行腳本來收集原始資料，並將它儲存在遠端電腦上執行中的記錄檔。

```powershell
$Cred = Get-Credential
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Invoke-Command -ComputerName (Get-Content Servers.txt) -Credential $Cred -ScriptBlock {
  $params = @{
      Name = "Get-EnergyData"
      FilePath = "\\Srv01\Scripts\Get-EnergyData.ps1"
      ScheduledJobOption = $using:O
      Trigger = $using:T
  }
  Register-ScheduledJob @params
}
```

此 `$Cred` 變數會在具有建立排程工作之許可權的使用者的 **PSCredential** 物件中儲存認證。 `$O`變數會儲存以建立的工作選項 `New-ScheduledJobOption` 。 `$T`變數會儲存以建立的工作觸發程式 `New-JobTrigger` 。

此 `Invoke-Command` Cmdlet 會使用 **ComputerName** 參數來取得檔案中的伺服器名稱清單 `Servers.txt` 。 **Credential** 參數會取得儲存在中的認證物件 `$Cred` 。
**ScriptBlock** 參數會在檔案 `Register-ScheduledJob` 中的電腦上執行命令 `Servers.txt` 。

的參數 `Register-ScheduledJob` 是由定義 `$params` 。 **Name** 參數會指定在每部遠端電腦上將作業命名為 **EnergyData** 。 **FilePath** 提供腳本的位置 `EnergyData.ps1` 。 腳本位於可供所有參與電腦使用的檔案伺服器上。作業會依照中的工作觸發程式所指定的排程執行 `$T` ，以及中的工作選項 `$O` 。

此 `Register-ScheduledJob @params` 命令會使用腳本區塊中的參數建立排程工作。

### 範例5：建立在遠端電腦上執行腳本的排程工作

此範例會在本機電腦上建立 **CollectEnergyData** 排程工作。 作業會在多部遠端電腦上執行。

```powershell
$Admin = Get-Credential
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Register-ScheduledJob -Name "CollectEnergyData" -Trigger $T -MaxResultCount 99 -ScriptBlock {
  $params = @{
    AsJob = $true
    ComputerName = (Get-Content Servers.txt)
    FilePath = '\\Srv01\Scripts\Get-EnergyData.ps1'
    Credential = $using:Admin
    Authentication = 'CredSSP'
  }
  Invoke-Command @params
}
```

`$Admin`變數會儲存具有在 **PSCredential** 物件中執行命令之許可權的使用者認證。 `$T`變數會儲存以建立的工作觸發程式 `New-JobTrigger` 。

此 `Register-ScheduledJob` Cmdlet 會使用 **Name** 參數在本機電腦上建立 **CollectEnergyData** 排程工作。 **Trigger** 參數會指定中的工作觸發程式 `$T` ，而 **MaxResultCount** 參數會將儲存的結果數目增加到99。

**ScriptBlock** 參數會定義的 `Invoke-Command` 參數 `$params` 。 **AsJob** 參數會在本機電腦上建立背景工作物件，即使腳本是在 `Energydata.ps1` 遠端電腦上執行也一樣。 **ComputerName** 參數會從檔案取得伺服器名稱的清單 `Servers.txt` 。 **Credential** 參數指定有權在遠端電腦上執行腳本的使用者帳戶。 而且， **驗證** 參數會指定 **CredSSP** 的值來允許委派的認證。

會 `Invoke-Command @params` 以腳本區塊中的參數執行命令。

## PARAMETERS

### -ArgumentList

指定由 **FilePath** 參數所指定之指令碼的參數值，或指定由 **ScriptBlock** 參數所指定之命令的參數值。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentication

指定用來驗證使用者認證的機制。 預設值為 Default。

此參數可接受的值為：

- 預設
- 基本
- Credssp
- Digest
- Kerberos
- 交涉
- NegotiateWithImplicitCredential

如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

> [!CAUTION]
> 使用者認證會傳遞至要驗證之遠端電腦的「認證安全性服務提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。 此機制會使得遠端作業的安全性風險變高。 若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定具有執行排程工作之權限的使用者帳戶。 預設為目前使用者。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 **PSCredential** 物件，例如 Cmdlet 中的物件 `Get-Credential` 。 如果您只輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定排程工作所執行的指令碼。 輸入 `.ps1` 本機電腦上的檔案路徑。 若要指定指令碼參數的預設值，請使用 **ArgumentList** 參數。
每個 `Register-ScheduledJob` 命令都必須使用 **ScriptBlock** 或 **FilePath** 參數。

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

指定 () 之 Windows PowerShell 腳本的完整路徑 `.ps1` 。 初始化指令碼會在執行 **ScriptBlock** 參數所指定的命令或 **FilePath** 參數所指定的指令碼之前，在針對背景工作所建立的工作階段中執行。 您可以使用初始化指令碼來設定工作階段，例如新增檔案/函式/別名、建立目錄，或檢查先決條件。

若要指定會執行主要工作命令的指令碼，請使用 **FilePath** 參數。

如果初始化腳本產生錯誤（即使是非終止錯誤），則排程工作的目前實例不會執行，且其狀態會是 [ **失敗** ]。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxResultCount

指定要為排程工作保留幾個工作結果項目。 預設值為 32。

Windows PowerShell 會將每個觸發之排程工作執行個體的執行記錄與結果儲存在磁碟上。 此參數的值決定針對此排程工作儲存的工作執行個體結果數目。 當工作執行個體數目超過此值時，Windows PowerShell 會刪除最舊的工作執行個體結果，以便挪出空間儲存最新工作執行個體結果。

作業執行歷程記錄和工作結果會儲存在 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`
在其上建立作業的電腦上的目錄。 若要查看執行歷程記錄，請使用 `Get-Job` Cmdlet。 若要取得工作結果，請使用 `Receive-Job` Cmdlet。

**MaxResultCount** 參數會設定排程工作之 ExecutionHistoryLength 屬性的值。

若要刪除目前的執行歷程記錄和工作結果，請使用 Cmdlet 的 **ClearExecutionHistory** 參數 `Set-ScheduledJob` 。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定排程工作的名稱。 此名稱也會用於所有已啟動的排程工作執行個體。 此名稱在電腦上必須是唯一的。 這是必要參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAs32

在 32 位元處理程序中執行排程工作。

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

### -RunEvery

用來指定執行作業的頻率。 例如，使用此選項可每隔15分鐘執行一次作業。

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunNow

在執行 Cmdlet 之後立即啟動作業 `Register-ScheduledJob` 。 此參數可讓您不需要觸發工作排程器在註冊後立即執行 Windows PowerShell 腳本，也不需要使用者建立指定開始日期和時間的觸發程式。

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

### -ScheduledJobOption

設定排程工作的選項。 輸入 **ScheduledJobOptions** 物件，例如使用 Cmdlet 建立的物件 `New-ScheduledJobOption` ，或雜湊表值。

您可以在註冊排程工作時設定排程工作的選項，或使用 `Set-ScheduledJobOption` 或 `Set-ScheduledJob` Cmdlet 來變更選項。

許多選項與其預設值會決定排程工作是否會執行以及執行時間。 排定工作之前，請務必檢閱這些選項。 如需排程工作選項的描述（包括預設值），請參閱 `New-ScheduledJobOption` 。

若要提交雜湊表，請使用下列索引鍵。 在下列雜湊表中，索引鍵隨著其預設值顯示。

`@{StartIfOnBattery=$False; StopIfGoingOnBattery=$True; WakeToRun=$False; StartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False; ShowInTaskScheduler=$True; RunElevated=$False; RunWithoutNetwork=$False; DoNotAllowDemandStart=$False; MultipleInstancePolicy="IgnoreNew"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

指定排程工作執行的命令。 以大括弧括住命令 (`{}`) 來建立腳本區塊。 若要指定命令參數的預設值，請使用 **ArgumentList** 參數。

每個 `Register-ScheduledJob` 命令都必須使用 **ScriptBlock** 或 **FilePath** 參數。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Trigger

指定排程工作的觸發程序。 輸入一或多個 **>scheduledjobtrigger** 物件，例如 Cmdlet 傳回的物件 `New-JobTrigger` ，或工作觸發程式索引鍵和值的雜湊表。

工作觸發程式會啟動排程工作。 觸發程序可以指定一次性或週期性排程工作或事件 (例如當使用者登入時或 Windows 啟動時)。

**Trigger** 是選擇性參數。 您可以在建立排程工作時新增觸發程式、使用 `Add-JobTrigger` 、 `Set-JobTrigger` 或 `Set-ScheduledJob` Cmdlet 稍後新增或變更工作觸發程式，或使用 `Start-Job` Cmdlet 來立即啟動排程工作。 您也可以建立及維護沒有觸發程序且做為範本的排程工作。

若要提交雜湊表，請使用下列索引鍵：

- **頻率** ：每日、每週、AtStartup、AtLogon
- **At** ：任何有效的時間字串
- **DaysOfWeek** -日期名稱的任何組合
- **間隔** -任何有效的頻率間隔
- **RandomDelay** ：任何有效的 timespan 字串
- **使用者** ：任何有效的使用者。 只能搭配 AtLogon 頻率值使用

例如：

`@{Frequency="Once"; At="3am"; DaysOfWeek="Monday", "Wednesday"; Interval=2; RandomDelay="30minutes"; User="Domain1\User01"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 不會執行此 Cmdlet。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法將輸入向下傳送到此 Cmdlet。

## 輸出

### Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

## 注意

每個排程工作都是儲存在 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` 本機電腦上目錄的子目錄中。
子目錄是針對排程工作命名，而且包含排程工作的 XML 檔案，以及其執行歷程記錄的記錄。 如需有關磁片上之排程工作的詳細資訊，請參閱 [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md)。

您在 Windows PowerShell 中建立的排程工作會顯示在工作排程器的工作排程器 `Library\Microsoft\Windows\PowerShell\ScheduledJobs` 資料夾中。 您可以使用 [工作排程器] 來檢視及編輯排程工作。

您可以使用工作排程器、 **schtasks.exe** 命令列工具和工作排程器 Cmdlet 來管理您使用排程工作 Cmdlet 建立的排程工作。 不過，您無法使用「排程工作」 Cmdlet 來管理您在工作排程器中建立的工作。

若排程工作命令失敗，Windows PowerShell 會傳回錯誤訊息。 但是，如果工作排程器嘗試執行作業失敗，則無法 Windows PowerShell 錯誤。

如果排程工作未執行，請使用下列方法找出原因：

- 確認工作觸發程式已正確設定。
  - 確認已滿足工作選項中設定的條件。
- 確認執行作業的使用者帳戶具有執行作業中命令或腳本的許可權。
- 檢查工作排程器歷程記錄是否有錯誤。
- 檢查工作排程器事件記錄檔中是否有錯誤。

如需詳細資訊，請參閱 [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md)。

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
