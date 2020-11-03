---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-JobTrigger
ms.openlocfilehash: 8d1b12b67ccf695e1c4b948e6eeecf292c588af4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202987"
---
# Set-JobTrigger

## 概要
變更排程工作的工作觸發程序。

## SYNTAX

```
Set-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-DaysInterval <Int32>] [-WeeksInterval <Int32>]
 [-RandomDelay <TimeSpan>] [-At <DateTime>] [-User <String>] [-DaysOfWeek <DayOfWeek[]>] [-AtStartup]
 [-AtLogOn] [-Once] [-RepetitionInterval <TimeSpan>] [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely]
 [-Daily] [-Weekly] [-PassThru] [<CommonParameters>]
```

## DESCRIPTION
**Set-JobTrigger** Cmdlet 會變更排程工作的工作觸發程序屬性。
您可以使用它來變更工作啟動時間或頻率，或將以時間為基礎的排程變更為依登入或啟動而觸發的排程。

工作觸發程式會定義用於啟動排程工作的週期性排程或條件。
雖然工作觸發程序不會儲存到磁碟，您可以變更排程工作 (會儲存到磁碟) 的工作觸發程序。

若要變更排程工作的工作觸發程序，請先使用 Get-JobTrigger Cmdlet 取得排程工作的工作觸發程序。
接著，使用管線傳送觸發程序至 **Set-JobTrigger** ，或將觸發程序儲存在變數中並使用 *Set-JobTrigger* Cmdlet 的 **InputObject** 參數來識別該觸發程序。
使用 **Set-JobTrigger** 的其他參數來變更工作觸發程序。

當您變更工作觸發程式的類型時（例如將工作觸發程式從每日或每週觸發程式變更為 *AtLogon* 觸發程式），系統會刪除原始觸發程式屬性。
不過，若變更觸發程序的值但未變更其類型 (例如變更每週觸發程序中的星期幾)，則只會變更您指定的屬性。
原始工作觸發程序的所有其他屬性會維持不變。

**Set-JobTrigger** 為 Windows PowerShell 所包含 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：變更工作觸發程序中的星期幾

```
PS C:\> Get-JobTrigger -Name "DeployPackage"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Saturday}   True

The second command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job. A pipeline operator (|) sends the trigger to the **Set-JobTrigger** cmdlet, which changes the job trigger so that it starts the DeployPackage job on Wednesdays and Sundays. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "DeployPackage" | Set-JobTrigger -DaysOfWeek "Wednesday", "Sunday" -Passthru
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Sunday}     True
```

此範例顯示如何變更每週工作觸發程序中的星期幾。

第一個命令會使用 Get-JobTrigger Cmdlet 來取得 DeployPackage 排程工作的工作觸發程式。
輸出會顯示觸發程序在星期三與星期六午夜啟動工作。

此命令並非必要；包含此命令僅為顯示觸發程序變更的效果。

### 範例 2：變更工作觸發程序類型

```
PS C:\> Get-JobTrigger -Name "Inventory"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          AtStartup                                                      True

The second command uses the **Get-JobTrigger** cmdlet to get the *AtStartup* job trigger of the Inventory job. The command uses the *TriggerID* parameter to identify the job trigger. A pipeline operator (|) sends the job trigger to the **Set-JobTrigger** cmdlet, which changes it to a weekly job trigger that runs every four weeks on Monday at midnight. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "Inventory" -TriggerID 2 | Set-JobTrigger -Weekly -WeeksInterval 4 -DaysOfWeek Monday -At "12:00 AM"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          Weekly          10/31/2011 12:00:00 AM {Monday}                True
```

此範例顯示如何變更啟動工作之工作觸發程序的類型。
此範例中的命令會將 AtStartup 工作觸發程序取代為每週觸發程序。

第一個命令會使用 Get-JobTrigger Cmdlet 來取得清查排程工作的工作觸發程式。
輸出顯示作業的每日觸發程式和 *AtStartup* 觸發程式都有兩個觸發程式。

此命令並非必要；包含此命令僅為顯示觸發程序變更的效果。

### 範例 3：變更遠端工作觸發程序的使用者

```
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.User} | Set-JobTrigger -User "Domain01/Admin02"}
```

此命令會變更 Server01 電腦上排程工作之所有 *AtLogon* 工作觸發程式中的使用者。

此命令會使用 Invoke-Command Cmdlet，在 Server01 電腦上執行命令。

遠端命令的開頭是可取得電腦上所有排程工作的 Get-ScheduledJob 命令。
排程的工作會以管線傳送至 Get-JobTrigger Cmdlet，此 Cmdlet 會取得排程工作的工作觸發程序。
輸入包含 JobDefinition 屬性 (其中包含排程工作) 的工作觸發程序，這樣觸發程序就會維持與排程工作的關聯 (即使它已被變更)。

工作觸發程式會以管線傳送至 Where-Object Cmdlet，此 Cmdlet 會取得具有 User 屬性的工作觸發程式。
系統會使用管線將選取的工作觸發程序傳送至 **Set-JobTrigger** Cmdlet，此 Cmdlet 會將使用者變更為 Domain01\Admin02。

### 範例 4：變更多個工作觸發程序的其中一個

```
PS C:\> Get-JobTrigger -Name "SecurityCheck"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           4/24/2013 3:00:00 AM                           True
2          Weekly          4/24/2013 4:00:00 PM   {Sunday}                True
3          Once            4/24/2013 4:00:00 PM                           True

The second command uses the **TriggerID** parameter of the **Get-JobTrigger** cmdlet to get the *Once* trigger of the SecurityCheck scheduled job. The command pipes the trigger to the Format-List cmdlet, which displays all of the properties of the *Once* job trigger.The output shows that the trigger starts the job once every hour (RepetitionInterval = 1 hour) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:00:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The third command changes the repetition interval of the job trigger from one hour to 90 minutes. The command does not return any output.
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerId 3 | Set-JobTrigger -RepetitionInterval (New-TimeSpan -Minutes 90)

The fourth command displays the effect of the change.The output shows that the trigger starts the job once every 90 minutes (RepetitionInterval = 1 hour, 30 minutes) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:30:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

此範例中的命令會將 SecurityCheck 排程工作之 *Once* 工作觸發程序的重複間隔從 60 分鐘變更為 90 分鐘。
SecurityCheck 排程的工作有三個工作觸發程序，因此命令會使用 Get-JobTrigger Cmdlet 的 *TriggerId* 參數來識別正在變更的工作觸發程序。

第一個命令使用 **Get-JobTrigger** Cmdlet 來取得 SecurityCheck 排程工作的所有工作觸發程序。
輸出 (顯示工作觸發程序的識別碼) 會顯示 *Once* 工作觸發程序具有 3 的識別碼。

## PARAMETERS

### -At
在指定的日期和時間啟動工作。
輸入 **DateTime** 物件 (例如 Get-Date Cmdlet 傳回的物件) 或可轉換為時間的字串 (例如 "April 19, 2012 15:00"、"12/31/2013 9:00 PM" 或 "3am")。

如果您未指定 **DateTime** 物件的元素（例如秒），則工作觸發程式的該元素不會變更。
如果原始工作觸發程式未包含 **DateTime** 物件且您省略某個元素，則會使用目前日期和時間的對應元素來建立工作觸發程式。

使用 *Once* 參數時，將 *At* 參數的值設定為特定日期和時間。
因為 **DateTime** 物件中的預設日期是目前日期，若設定目前時間之前的時間且未指定明確的日期，則系統會建立時間為過去時間的工作觸發程序。

**DateTime** 物件與轉換為 **DateTime** 物件的字串會自動調整為與為本機電腦所選取的日期和時間格式 (在 [控制台] 中的[地區及語言]) 相容。

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
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
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AtStartup
在 Windows 啟動時啟動排程工作。

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

### -Daily
指定每日週期性工作排程。
使用 *每日* 參數集中的其他參數來指定排程詳細資料。

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

### -DaysInterval
在每日排程上指定執行週期間隔天數。
例如，3 的值會在第 1、4、7 天啟動排程工作，依此類推。
預設值為 1。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DaysOfWeek
指定每週排程工作要在星期幾執行。
輸入日名稱，例如星期一、星期四、整數0-6、0代表星期日，或星號 (\*) 代表每一天。
在 Weekly 參數集中，此為必要參數。

在工作觸發程序中，星期幾名稱會轉換為其整數值。
當您在命令中將星期幾名稱放在引號中時，請將每個星期幾名稱放在各自的引號中，例如 "Monday"、"Tuesday"。
若將多個星期幾名稱放在一組引號中，則會加總對應的整數值。
例如，"Monday, Tuesday" (1, 2) 會產生 "Wednesday" (3) 的值。

```yaml
Type: System.DayOfWeek[]
Parameter Sets: (All)
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
指定工作觸發程序。
輸入包含 **>scheduledjobtrigger** 物件的變數，或輸入可取得 **>scheduledjobtrigger** 物件的命令或運算式，例如 Get-JobTrigger 命令。
您也可以使用管線將 **ScheduledJobTrigger** 物件傳遞給 **Set-JobTrigger** 。

若指定多個工作觸發程序， **Set-JobTrigger** 會對所有工作觸發程序進行相同的變更。

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Once
指定非週期性 (一次性) 排程。

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

### -PassThru
傳回已變更的工作觸發程序。
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

### -RandomDelay
啟用排定的開始時間前的隨機延遲，並設定最大延遲值。
延遲長度是在每次開始前隨機設定，其值介於無延遲到此參數值所指定的時間之間。
預設值零 (00:00:00) 會停用隨機延遲。

輸入 timespan 物件（例如 New-TimeSpan Cmdlet 所傳回的物件），或輸入 \<hours\> ： \<minutes\> ： format 格式的值 \<seconds\> ，此物件會自動轉換為 timespan 物件。

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
Parameter Sets: (All)
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
例如，若 **RepetitionInterval** 的值是 5 分鐘且 *RepetitionDuration* 的值是 2 小時，則在兩小時內，每隔五分鐘會觸發該工作。

輸入 timespan 物件 (例如 New-TimeSpan Cmdlet 傳回的物件) 或可轉換為 timespan 物件的字串 (例如 "1:05:30")。

若要以無終止時間方式執行工作，請改為新增 *RepeatIndefinitely* 參數。

若要在工作觸發程序重複期間過期之前停止工作，請將 **RepetitionDuration** 值設定為零 (0)。

若要變更 *Once* 工作觸發程序的重複期間或重複間隔，命令必須包含 **RepetitionInterval** 與 **RepetitionDuration** 參數。
若要變更其他類型之工作觸發程序的重複期間或重複間隔，命令必須包含 *Once* 、 *At* 、 *RepetitionInterval* 與 *RepetitionDuration* 參數。

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

### -RepetitionInterval
以指定的時間間隔重複執行工作。
例如，若此參數的值是設定為 2 小時，則每隔兩小時會觸發一次工作。
預設值 0 不會重複執行工作。

輸入 timespan 物件 (例如 New-TimeSpan Cmdlet 傳回的物件) 或可轉換為 timespan 物件的字串 (例如 "1:05:30")。

若要變更 **Once** 工作觸發程序的重複期間或重複間隔，命令必須包含 **RepetitionInterval** 與 **RepetitionDuration** 參數。
若要變更其他類型之工作觸發程序的重複期間或重複間隔，命令必須包含 **Once** 、 **At** 、 **RepetitionInterval** 與 **RepetitionDuration** 參數。

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

### -User
指定觸發 *AtLogon* 排程工作啟動的使用者。
以或格式輸入使用者的名稱 \<UserName\> ， \<Domain\Username\> 或輸入星號 (\*) 代表所有使用者。
預設值是所有使用者。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Weekly
指定週期性每週工作排程。
使用 *每週* 參數集中的其他參數來指定排程詳細資料。

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

### -WeeksInterval
指定每週工作排程的週次。
例如，3 的值會在第 1、4、7 週啟動排程工作，依此類推。
預設值為 1。

```yaml
Type: System.Int32
Parameter Sets: (All)
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

### Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger
您可以透過管線將多個工作觸發程式傳送至 **enable-jobtrigger** 。

## 輸出

### 無或 Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger
當您使用 *Passthru* 參數時， **Set-JobTrigger** 會傳回已變更的工作觸發程序。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

* 工作觸發程序具有 JobDefintion 屬性，此屬性會將它們與排程工作關聯。 當您變更排程工作的工作觸發程序時，工作也會被變更。 您不需要使用 Set-ScheduledJob 命令將已變更的觸發程序套用到排程工作。

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
