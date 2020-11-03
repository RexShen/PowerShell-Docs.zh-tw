---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 3/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventLog
ms.openlocfilehash: ab1a97dc3c78bbfdcc239fd573ef3b1f839e2b21
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204020"
---
# Get-EventLog

## 概要
取得本機電腦或遠端電腦上事件記錄檔中的事件，或事件記錄檔的清單。

## SYNTAX

### LogName (預設值)

```
Get-EventLog [-LogName] <String> [-ComputerName <String[]>] [-Newest <Int32>] [-After <DateTime>]
 [-Before <DateTime>] [-UserName <String[]>] [[-InstanceId] <Int64[]>] [-Index <Int32[]>]
 [-EntryType <String[]>] [-Source <String[]>] [-Message <String>] [-AsBaseObject]
 [<CommonParameters>]
```

### 清單

```
Get-EventLog [-ComputerName <String[]>] [-List] [-AsString] [<CommonParameters>]
```

## DESCRIPTION

`Get-EventLog`Cmdlet 會從本機和遠端電腦取得事件和事件記錄檔。 根據預設，會 `Get-EventLog` 從本機電腦取得記錄。 若要從遠端電腦取得記錄，請使用 **ComputerName** 參數。

您可以使用 `Get-EventLog` 參數和屬性值來搜尋事件。 Cmdlet 會取得符合指定屬性值的事件。

包含名詞的 PowerShell Cmdlet `EventLog` 僅適用于 Windows 傳統事件記錄檔，例如應用程式、系統或安全性。 若要在 Windows Vista 和更新版本的 Windows 中取得使用 Windows 事件記錄檔技術的記錄，請使用 `Get-WinEvent` 。

> [!NOTE]
> `Get-EventLog` 使用已被取代的 WIN32 API。 結果可能不正確。 請改用 `Get-WinEvent` Cmdlet。

## 範例

### 範例1：取得本機電腦上的事件記錄檔

此範例會顯示本機電腦上可用的事件記錄檔清單。 Log 資料行中的名稱會與 **LogName** 參數搭配使用，以指定要搜尋事件的記錄檔。

```powershell
Get-EventLog -List
```

```Output
Max(K)   Retain   OverflowAction      Entries  Log
------   ------   --------------      -------  ---
15,168        0   OverwriteAsNeeded   20,792   Application
15,168        0   OverwriteAsNeeded   12,559   System
15,360        0   OverwriteAsNeeded   11,173   Windows PowerShell
```

此 `Get-EventLog` Cmdlet 會使用 **List** 參數來顯示可用的記錄。

### 範例2：從本機電腦上的事件記錄檔取得最近的專案

此範例會從系統事件記錄檔取得最近的專案。

```powershell
Get-EventLog -LogName System -Newest 5
```

```Output
Index   Time          EntryType    Source              InstanceID   Message
-----   ----          ---------    ------              ----------   -------
13820   Jan 17 19:16  Error        DCOM                     10016   The description for Event...
13819   Jan 17 19:08  Error        DCOM                     10016   The description for Event...
13818   Jan 17 19:06  Information  Service Control...  1073748864   The start type of the Back...
13817   Jan 17 19:05  Error        DCOM                     10016   The description for Event...
13815   Jan 17 19:03  Information  Microsoft-Windows...        35   The time service is now sync...
```

此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統事件記錄檔。 **最新** 的參數會傳回五個最新的事件。

### 範例3：在事件記錄檔中尋找特定專案數的所有來源

此範例示範如何尋找 System 事件記錄檔中1000最新專案所包含的所有來源。

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$Events | Group-Object -Property Source -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count   Name
-----   ----
  110   DCOM
   65   Service Control Manager
   51   Microsoft-Windows-Kern...
   14   EventLog
   14   BTHUSB
   13   Win32k
```

此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統記錄檔。 **最新** 的參數會選取1000的最新事件。 事件物件會儲存在變數中 `$Events` 。 這些 `$Events` 物件會向下傳送至 `Group-Object` Cmdlet。
`Group-Object` 使用 **Property** 參數依來源將物件分組，並計算每個來源的物件數目。 **NoElement** 參數會從輸出中移除群組成員。
此 `Sort-Object` Cmdlet 會使用 **Property** 參數，依每個來源名稱的計數排序。
**遞減** 的參數會依計數排序清單（從最高到最低）。

### 範例4：取得特定事件記錄檔中的錯誤事件

此範例會從系統事件記錄檔中取得錯誤事件。

```powershell
Get-EventLog -LogName System -EntryType Error
```

```Output
Index Time          EntryType   Source  InstanceID Message
----- ----          ---------   ------  ---------- -------
13296 Jan 16 13:53  Error       DCOM    10016 The description for Event ID '10016' in Source...
13291 Jan 16 13:51  Error       DCOM    10016 The description for Event ID '10016' in Source...
13245 Jan 16 11:45  Error       DCOM    10016 The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error       DCOM    10016 The description for Event ID '10016' in Source...
```

此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統記錄檔。 **>entrytype** 參數會篩選事件，只顯示錯誤事件。

### 範例5：從含有 InstanceId 和來源值的事件記錄檔取得事件

此範例會從系統記錄檔取得特定 InstanceId 和來源的事件。

```powershell
Get-EventLog -LogName System -InstanceId 10016 -Source DCOM
```

```Output
Index Time          EntryType  Source  InstanceID  Message
----- ----          ---------  ------  ----------  -------
13245 Jan 16 11:45  Error      DCOM         10016  The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error      DCOM         10016  The description for Event ID '10016' in Source...
13219 Jan 16 10:00  Error      DCOM         10016  The description for Event ID '10016' in Source...
```

此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統記錄檔。 **InstanceID** 參數會選取具有指定實例識別碼的事件。 **Source** 參數指定事件屬性。

### 範例6：從多部電腦取得事件

此命令會從三部電腦上的系統事件記錄檔取得事件： Server01、Server02 和 Server03。

```powershell
Get-EventLog -LogName System -ComputerName Server01, Server02, Server03
```

此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統記錄檔。 **ComputerName** 參數使用逗點分隔字串來列出您要從中取得事件記錄檔的電腦。

### 範例7：取得訊息中包含特定單字的所有事件

此命令會取得系統事件記錄檔中的所有事件，該事件記錄檔中包含事件訊息中的特定字組。 您指定的 **訊息** 參數值可能會包含在訊息的內容中，但不會顯示在 PowerShell 主控台上。

```powershell
Get-EventLog -LogName System -Message *description*
```

```Output
Index Time          EntryType   Source       InstanceID   Message
----- ----          ---------   ------       ----------   -------
13821 Jan 17 19:17  Error       DCOM              10016   The description for Event ID '10016'...
13820 Jan 17 19:16  Error       DCOM              10016   The description for Event ID '10016'...
13819 Jan 17 19:08  Error       DCOM              10016   The description for Event ID '10016'...
```

此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統事件記錄檔。 **Message** 參數會在每個事件的 message 欄位中指定要搜尋的文字。

### 範例8：顯示事件的屬性值

此範例示範如何顯示所有事件的屬性和值。

```powershell
$A = Get-EventLog -LogName System -Newest 1
$A | Select-Object -Property *
```

```Output
EventID            : 10016
MachineName        : localhost
Data               : {}
Index              : 13821
Category           : (0)
CategoryNumber     : 0
EntryType          : Error
Message            : The description for Event ID '10016' in Source 'DCOM'...
Source             : DCOM
ReplacementStrings : {Local,...}
InstanceId         : 10016
TimeGenerated      : 1/17/2019 19:17:23
TimeWritten        : 1/17/2019 19:17:23
UserName           : username
Site               :
Container          :
```

此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統事件記錄檔。 **最新** 的參數會選取最新的事件物件。 物件會儲存在變數中 `$A` 。 變數中的物件 `$A` 會向下傳送至 `Select-Object` Cmdlet。
`Select-Object` 使用 **Property** 參數搭配星號 (`*`) 來選取物件的所有屬性。

### 範例9：使用來源和事件識別碼從事件記錄檔取得事件

這個範例會取得指定之來源和事件識別碼的事件。

```powershell
Get-EventLog -LogName Application -Source Outlook | Where-Object {$_.EventID -eq 63} |
              Select-Object -Property Source, EventID, InstanceId, Message
```

```Output
Source   EventID   InstanceId   Message
------   -------   ----------   -------
Outlook       63   1073741887   The Exchange web service request succeeded.
Outlook       63   1073741887   Outlook detected a change notification.
Outlook       63   1073741887   The Exchange web service request succeeded.
```

此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定應用程式事件記錄檔。 **Source** 參數指定應用程式名稱，Outlook。 這些物件會向下傳送至 `Where-Object` Cmdlet。 針對管線中的每個物件，此 `Where-Object` Cmdlet 會使用變數 `$_.EventID` 來比較事件識別碼屬性與指定的值。 這些物件會向下傳送至 `Select-Object` Cmdlet。 `Select-Object` 使用 **Property** 參數來選取要在 PowerShell 主控台中顯示的屬性。

### 範例10：依屬性取得事件和群組

```powershell
Get-EventLog -LogName System -UserName NT* | Group-Object -Property UserName -NoElement |
              Select-Object -Property Count, Name
```

```Output
Count  Name
-----  ----
6031   NT AUTHORITY\SYSTEM
  42   NT AUTHORITY\LOCAL SERVICE
   4   NT AUTHORITY\NETWORK SERVICE
```

此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統記錄檔。 **UserName** 參數包含星號 (`*`) 萬用字元來指定使用者名稱的一部分。 事件物件會以管線傳送至 `Group-Object` Cmdlet。 `Group-Object` 使用 **Property** 參數來指定 **UserName** 屬性是用來將物件分組，並計算每個使用者名稱的物件數目。 **NoElement** 參數會從輸出中移除群組成員。 這些物件會向下傳送至 `Select-Object` Cmdlet。
`Select-Object` 使用 **Property** 參數來選取要在 PowerShell 主控台中顯示的屬性。

### 範例11：取得特定日期和時間範圍內發生的事件

此範例會取得系統事件記錄檔中指定日期和時間範圍的錯誤事件。 **Before** 和 **After** 參數會設定日期和時間範圍，但會從輸出中排除。

```powershell
$Begin = Get-Date -Date '1/17/2019 08:00:00'
$End = Get-Date -Date '1/17/2019 17:00:00'
Get-EventLog -LogName System -EntryType Error -After $Begin -Before $End
```

```Output
Index Time          EntryType   Source   InstanceID  Message
----- ----          ---------   ------   ----------  -------
13821 Jan 17 13:40  Error       DCOM          10016  The description for Event ID...
13820 Jan 17 13:11  Error       DCOM          10016  The description for Event ID...
...
12372 Jan 17 10:08  Error       DCOM          10016  The description for Event ID...
12371 Jan 17 09:04  Error       DCOM          10016  The description for Event ID...
```

此 `Get-Date` Cmdlet 會使用 **date** 參數來指定日期和時間。 **DateTime** 物件會儲存在 `$Begin` 和變數中 `$End` 。 此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統記錄檔。 **>entrytype** 參數會指定錯誤事件種類。 日期和時間範圍是由 **After** 參數和 `$Begin` 變數以及 **Before** 參數和變數所設定 `$End` 。

## PARAMETERS

### -After

取得在指定的日期和時間之後發生的事件。 **After** 參數日期和時間會從輸出中排除。 輸入 **DateTime** 物件，例如 Cmdlet 所傳回的值 `Get-Date` 。

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsBaseObject

指出此 Cmdlet 會傳回每個事件的標準 **EventLogEntry** 物件。 如果沒有這個參數，則會傳回 `Get-EventLog` 具有其他 **EventLogName** 、 **Source** 和 **InstanceId** 屬性的擴充 **PSObject** 物件。

若要查看這個參數的效果，請透過管線將事件傳送至 `Get-Member` Cmdlet，然後檢查結果中的 **TypeName** 值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsString

指出此 Cmdlet 會以字串形式傳回輸出，而不是以物件的形式傳回。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Before

取得在指定的日期和時間之前發生的事件。 從輸出中排除 **之前** 的參數日期和時間。 輸入 **DateTime** 物件，例如 Cmdlet 所傳回的值 `Get-Date` 。

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

此參數會指定遠端電腦的 NetBIOS 名稱、網際網路通訊協定 (IP) 位址，或 (FQDN) 的完整功能變數名稱。

如果未指定 **ComputerName** 參數，則 `Get-EventLog` 預設為本機電腦。 參數也接受點 (`.`) 來指定本機電腦。

**ComputerName** 參數不依賴 Windows PowerShell 遠端處理。 `Get-EventLog`即使您的電腦未設定為執行遠端命令，您也可以使用 With **ComputerName** 參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EntryType

以字串陣列指定此 Cmdlet 所取得事件的專案類型。

此參數可接受的值為：

- 錯誤
- 資訊
- FailureAudit
- SuccessAudit
- 警告

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Index

指定要從事件記錄檔中取得的索引值。 參數接受以逗號分隔的值字串。

```yaml
Type: System.Int32[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

指定要從事件記錄檔取得的實例識別碼。 參數接受以逗號分隔的值字串。

```yaml
Type: System.Int64[]
Parameter Sets: LogName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -List

顯示電腦上的事件記錄檔清單。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName

指定一個事件記錄檔的名稱。 以尋找記錄檔名稱的使用 `Get-EventLog -List` 。 允許使用萬用字元。 這是必要參數。

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Message

指定事件訊息中的字串。 您可以使用這個參數來搜尋包含特定單字或片語的訊息。 允許使用萬用字元。

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: MSG

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Newest

開頭為最新的事件，並取得指定的事件數目。 例如，需要事件的數目 `-Newest 100` 。 指定傳回的最大事件數目。

```yaml
Type: System.Int32
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

以字串陣列的形式指定寫入至這個 Cmdlet 取得之記錄檔的來源。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ABO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -UserName

將與事件相關聯的使用者名稱指定為字串陣列。 輸入名稱或名稱模式，例如 `User01` 、 `User*` 或 `Domain01\User*` 。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法透過管道傳送輸入 `Get-EventLog` 。

## 輸出

### System.Diagnostics.EventLogEntry。 System.Diagnostics.EventLog。 System.String

如果指定了 **LogName** 參數，輸出就會是 **EventLogEntry** 物件的集合。

如果只指定 **List** 參數，則輸出會是 **系統** 記錄檔物件的集合。

如果同時指定 **List** 和 **AsString** 參數，則輸出會是 **system.string** 物件的集合。

## 注意

`Get-EventLog` `Get-WinEvent` Windows 預先安裝環境 (Windows PE) 不支援 Cmdlet 和。

## 相關連結

[Clear-EventLog](Clear-EventLog.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
