---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-JobTrigger
ms.openlocfilehash: de49ab937c6f3a8187f5aecd6aafc81425b8cd00
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202999"
---
# New-JobTrigger

## 概要
建立排程工作的工作觸發程序。

## SYNTAX

###  (預設值之後) 

```
New-JobTrigger [-RandomDelay <TimeSpan>] -At <DateTime> [-Once] [-RepetitionInterval <TimeSpan>]
 [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely] [<CommonParameters>]
```

### 每日

```
New-JobTrigger [-DaysInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> [-Daily] [<CommonParameters>]
```

### 每週

```
New-JobTrigger [-WeeksInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> -DaysOfWeek <DayOfWeek[]>
 [-Weekly] [<CommonParameters>]
```

### AtStartup

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-AtStartup] [<CommonParameters>]
```

### AtLogon

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-User <String>] [-AtLogOn] [<CommonParameters>]
```

## DESCRIPTION
**Enable-jobtrigger 指令程式** 會建立工作觸發程式，以一次性或週期性排程來啟動排程工作，或在事件發生時啟動排程工作。

您可以使用由 **New-JobTrigger** 所傳回的 **ScheduledJobTrigger** 物件為新的排程工作或現有的排程工作設定工作觸發程序。
您也可以使用 Get-JobTrigger Cmdlet 來建立工作觸發程式，以取得現有排程工作的工作觸發程式，或使用雜湊表值來代表工作觸發程式。

建立工作觸發程式時，請檢查 New-ScheduledJobOption Cmdlet 所指定之選項的預設值。
這些選項的有效值/預設值與 **Task Scheduler** 中之對應選項的有效值/預設值相同，而且會影響排程工作的排程與執行時間。

**Enable-jobtrigger** 是包含在 Windows PowerShell 之 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：排程

```
PS C:\> New-JobTrigger -Once -At "1/20/2012 3:00 AM"
```

此命令會使用 **New-JobTrigger** Cmdlet 來建立工作觸發程序，此工作觸發程序會以一次性方式啟動排程工作。
*At* 參數的值是 Windows PowerShell 轉換為 **DateTime** 物件的字串。
*At* 參數值包含明確的日期，不只是時間。
若省略日期，則會以目前日期與上午 3:00 的時間建立觸發程序，這可能代表過去的時間。

### 範例2：每日排程

```
PS C:\> New-JobTrigger -Daily -At "4:15 AM" -DaysInterval 3
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/21/2012 4:15:00 AM                           True
```

此命令會建立每隔 3 天在上午 4:15 啟動排程工作的工作觸發程序。

因為 *At* 參數的值不包含日期，會使用目前日期做為 **DateTime** 物件中的日期值。
若日期和時間為過去時間，則排程工作會在排定的下次執行時間啟動，亦即自 *At* 參數值起的三天後。

### 範例3：每週排程

```
PS C:\> New-JobTrigger -Weekly -DaysOfWeek Monday, Wednesday, Friday -At "23:00" -WeeksInterval 4
Id Frequency Time                  DaysOfWeek                  Enabled
-- --------- ----                  ----------                  -------
0  Weekly    9/21/2012 11:00:00 PM {Monday, Wednesday, Friday} True
```

此命令會建立每隔四週在星期一、星期三與星期五 23:00 (下午 11:00) 啟動排程工作的工作觸發程序。

您也可以在整數中輸入 *DaysOfWeek* 參數值，例如 `-DaysOfWeek 1, 5` 。

### 範例4：登入排程

```
PS C:\> New-JobTrigger -AtLogOn -User Domain01\Admin01
```

此命令會建立在網域系統管理員登入電腦時執行排程工作的工作觸發程序。

### 範例5：使用隨機延遲

```
PS C:\> New-JobTrigger -Daily -At 1:00 -RandomDelay 00:20:00
```

此命令會建立在每天凌晨 1:00 啟動排程工作的工作觸發程序。
此命令會使用 *RandomDelay* 參數將最大延遲設定為 20 分鐘。
因此，該工作會在每天凌晨 1:00 到凌晨 1:20 之間執行，且間隔為隨機指定。

您可以將隨機延遲用於取樣、負載平衡與其他系統管理工作。
設定延遲值時，請檢查 New-ScheduledJobOption Cmdlet 的有效和預設值，並協調延遲與選項設定。

### 範例6：建立新排程工作的工作觸發程式

```
The first command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The command saves the job trigger in the $T variable.
PS C:\> $T = New-JobTrigger -Weekly -DaysOfWeek 1,3,5 -At 12:01AM


The second command uses the Register-ScheduledJob cmdlet to create a scheduled job that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The value of the *Trigger* parameter is the trigger that is stored in the $T variable.
PS C:\> Register-ScheduledJob -Name Test-HelpFiles -FilePath C:\Scripts\Test-HelpFiles.ps1 -Trigger $T
```

這些命令使用工作觸發程序來建立新的排程工作。

### 範例7：將工作觸發程式新增至排程工作

```
PS C:\> Add-JobTrigger -Name SynchronizeApps -Trigger (New-JobTrigger -Daily -At 3:10AM)
```

此範例顯示如何將工作觸發程序新增到現有的排程工作。
您可以將多個工作觸發程序新增到任何排程工作。

此命令會使用 Add-JobTrigger Cmdlet，將工作觸發程式新增至 SynchronizeApps 排程工作。
*Trigger* 參數的值是 **New-JobTrigger** 命令，此命令會在每天上午 3:10 執行工作。

當命令完成時，SynchronizeApps 是在由工作觸發程序所指定之時間執行的排程工作。

### 範例8：建立重複的工作觸發程式

```
PS C:\> New-JobTrigger -Once -At "09/12/2013 1:00:00" -RepetitionInterval (New-TimeSpan -Hours 1) -RepetitionDuration (New-Timespan -Hours 48)
```

此命令會建立每隔 60 48 分鐘執行一次工作的工作觸發程式2013，從年9月12日（上午1:00）開始。

### 範例9：停止重複的工作觸發程式

```
PS C:\> Get-JobTrigger -Name SecurityCheck | Set-JobTrigger -RepetitionInterval 0:00 -RepetitionDuration 0:00
```

此命令會強制停止 SecurityCheck 工作，此工作是觸發為每隔 60 分鐘執行一次，直到其工作觸發程序過期。

為了避免重複作業，此命令會使用 Get-JobTrigger 取得 SecurityCheck 作業的工作觸發程式，並使用 Set-JobTrigger Cmdlet 將工作觸發程式的重複間隔和重複期間變更為零 (0) 。

### 範例10：建立每小時工作觸發程式

```
PS C:\> New-JobTrigger -Once -At "9/21/2012 0am" -RepetitionInterval (New-TimeSpan -Hour 12) -RepetitionDuration ([TimeSpan]::MaxValue)
```

下列命令會建立工作觸發程序，此工作觸發程序會以無終止時間的方式每隔 12 小時執行排程工作。
該排程是從明天 (9/21/2012) 午夜 (上午 0:00) 開始。

## PARAMETERS

### -At
在指定的日期和時間啟動工作。
輸入 **DateTime** 物件（例如 Get-Date Cmdlet 傳回的物件），或是可轉換成日期和時間的字串，例如 "4 月19日、2012 15:00"、"12/31" 或 "3am"。
若未指定日期的元素 (例如年)，觸發程序中的日期會具有與目前日期對應的元素。

使用 *Once* 參數時，將 *At* 參數的值設定為未來的日期和時間。
因為 **DateTime** 物件中的預設日期是目前日期，若指定目前時間以前的時間且未指定明確的日期，則系統會建立時間為過去時間的工作觸發程序。

**DateTime** 物件與轉換為 **DateTime** 物件的字串會自動調整為與為本機電腦所選取的日期和時間格式 (在 [控制台] 中的[地區及語言]) 相容。

```yaml
Type: System.DateTime
Parameter Sets: Once, Daily, Weekly
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AtLogOn
在指定的使用者登入電腦時啟動排程工作。
若要指定使用者，請使用 *User* 參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtLogon
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AtStartup
在 Windows 啟動時啟動排程工作。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtStartup
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Daily
指定每日週期性工作排程。
使用 *每日* 參數集中的其他參數來指定排程詳細資料。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Daily
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DaysInterval
在每日排程上指定執行週期間隔天數。
例如，3 的值會在第 1、4、7 天啟動排程工作，依此類推。
預設值為 1。

```yaml
Type: System.Int32
Parameter Sets: Daily
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DaysOfWeek
指定每週排程工作要在星期幾執行。
輸入星期幾名稱，例如 "Monday" 或 0-6 之間的整數，其中 0 代表 Sunday。
在 Weekly 參數集中，此為必要參數。

在工作觸發程序中，星期幾名稱會轉換為其整數值。
當您在命令中將星期幾名稱放在引號中時，請將每個星期幾名稱放在各自的引號中，例如 "Monday"、"Tuesday"。
若將多個星期幾名稱放在一組引號中，則會加總對應的整數值。
例如，"Monday, Tuesday" (1, 2) 會產生 "Wednesday" (3) 的值。

```yaml
Type: System.DayOfWeek[]
Parameter Sets: Weekly
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Once
指定非週期性 (一次性) 或自訂重複性排程。
若要建立重複性排程，請使用 *Once* 參數搭配 *RepetitionDuration* 與 *RepetitionInterval* 參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RandomDelay
啟用排定的開始時間前的隨機延遲，並設定最大延遲值。
延遲長度是在每次開始前隨機設定，其值介於無延遲到此參數值所指定的時間之間。
預設值零 (00:00:00) 會停用隨機延遲。

輸入 timespan 物件（例如 New-TimeSpan Cmdlet 所傳回的物件），或輸入 \<hours\> ： \<minutes\> ： format 格式的值 \<seconds\> ，此物件會自動轉換為 **timespan** 物件。

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

### -RepeatIndefinitely
若要重複執行無終止時間之排程工作，使用此參數 (從 Windows PowerShell 4.0 開始提供) 可取代為 **RepetitionDuration** 參數指定 *TimeSpan.MaxValue* 值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RepetitionDuration
重複執行工作，直到經過指定的時間。
重複頻率是由 *RepetitionInterval* 參數的值指定。
例如，若 **RepetitionInterval** 的值是 5 分鐘且 **RepetitionDuration** 的值是 2 小時，則在兩小時內，每隔五分鐘會觸發該工作。

輸入 timespan 物件 (例如 New-TimeSpan Cmdlet 傳回的物件) 或可轉換為 timespan 物件的字串 (例如 "1:05:30")。

若要以無終止時間方式執行工作，請改為新增 *RepeatIndefinitely* 參數。

若要在工作觸發程式重複期間過期之前停止工作，請使用 Set-JobTrigger Cmdlet 將 *RepetitionDuration* 值設定為零 (0) 。

只有當已在命令中使用 *Once* 、 *At* 與 *RepetitionInterval* 參數時，此參數才有效。

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RepetitionInterval
以指定的時間間隔重複執行工作。
例如，若此參數的值是設定為 2 小時，則每隔兩小時會觸發一次工作。
預設值 0 不會重複執行工作。

輸入 timespan 物件 (例如 New-TimeSpan Cmdlet 傳回的物件) 或可轉換為 timespan 物件的字串 (例如 "1:05:30")。

只有當已在命令中使用 *Once* 、 *At* 與 *RepetitionDuration* 參數時，此參數才有效。

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -User
指定觸發 *AtLogon* 排程工作啟動的使用者。
以或格式輸入使用者的名稱 \<UserName\> ， \<Domain\Username\> 或輸入星號 (\*) 代表所有使用者。
預設值是所有使用者。

```yaml
Type: System.String
Parameter Sets: AtLogon
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Weekly
指定週期性每週工作排程。
使用 Weekly 參數中的其他參數來指定排程詳細資料。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Weekly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WeeksInterval
指定每週工作排程的週次。
例如，3 的值會在第 1、4、7 週啟動排程工作，依此類推。
預設值為 1。

```yaml
Type: System.Int32
Parameter Sets: Weekly
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

### 無
您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger

## 注意

* 工作觸發程序不會儲存到磁碟。 不過，排程的工作會儲存至磁片，而您可以使用 Get-JobTrigger 取得任何排程工作的工作觸發程式。
* **Enable-jobtrigger** 不會防止您建立將不會執行排程工作的工作觸發程式，例如過去日期的一次性觸發程式。
* Register-ScheduledJob Cmdlet 會接受 >scheduledjobtrigger 物件，例如 **enable-jobtrigger** 或 Get-JobTrigger Cmdlet 所傳回的物件，或具有觸發程式值的雜湊表。

  若要提交雜湊表，請使用下列索引鍵。

  `@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (或任何有效的時間字串) ; `DaysOfWeek="Monday", "Wednesday"` (或日期名稱的任何組合) ; `Interval=2` (或任何有效的頻率間隔) ; `RandomDelay="30minutes"` (或任何有效的 timespan 字串) ; `User="Domain1\User01` (或任何有效的使用者;只能與 *AtLogon* 頻率值搭配使用) }

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
