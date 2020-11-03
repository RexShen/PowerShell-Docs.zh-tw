---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-winevent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WinEvent
ms.openlocfilehash: ba68ded5afe19a98555e7224692ab8dbe09e3486
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202624"
---
# Get-WinEvent

## 概要
從本機電腦和遠端電腦上的事件記錄檔和事件追蹤記錄檔取得事件。

## SYNTAX

### GetLogSet (預設) 

```
Get-WinEvent [[-LogName] <String[]>] [-MaxEvents <Int64>] [-ComputerName <String>]
 [-Credential <PSCredential>] [-FilterXPath <String>] [-Force] [-Oldest] [<CommonParameters>]
```

### ListLogSet

```
Get-WinEvent [-ListLog] <String[]> [-ComputerName <String>] [-Credential <PSCredential>] [-Force]
 [<CommonParameters>]
```

### ListProviderSet

```
Get-WinEvent [-ListProvider] <String[]> [-ComputerName <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### GetProviderSet

```
Get-WinEvent [-ProviderName] <String[]> [-MaxEvents <Int64>] [-ComputerName <String>]
 [-Credential <PSCredential>] [-FilterXPath <String>] [-Force] [-Oldest] [<CommonParameters>]
```

### FileSet

```
Get-WinEvent [-Path] <String[]> [-MaxEvents <Int64>] [-Credential <PSCredential>]
 [-FilterXPath <String>] [-Oldest] [<CommonParameters>]
```

### HashQuerySet

```
Get-WinEvent [-MaxEvents <Int64>] [-ComputerName <String>] [-Credential <PSCredential>]
 [-FilterHashtable] <Hashtable[]> [-Force] [-Oldest] [<CommonParameters>]
```

### XmlQuerySet

```
Get-WinEvent [-MaxEvents <Int64>] [-ComputerName <String>] [-Credential <PSCredential>]
 [-FilterXml] <XmlDocument> [-Oldest] [<CommonParameters>]
```

## DESCRIPTION

此 `Get-WinEvent` Cmdlet 會從事件記錄檔中取得事件，包括傳統記錄檔，例如 **系統** 和 **應用程式** 記錄檔。 Cmdlet 會從 windows Vista 引進的 Windows 事件記錄技術所產生的事件記錄檔中取得資料。 此外，Windows 事件追蹤所產生的記錄檔中的事件 **(ETW)** 。 依預設，會 `Get-WinEvent` 以最新到最舊的順序傳回事件資訊。

`Get-WinEvent` 列出事件記錄檔和事件記錄檔提供者。 若要中斷命令，請按下<kbd>CTRL</kbd> + <kbd>C</kbd>。 您可以從選取的記錄檔或從選取的事件提供者所產生的記錄檔取得事件。 而且您可以在單一命令中結合來自多個來源的事件。
`Get-WinEvent` 可讓您使用 XPath 查詢、結構化 XML 查詢，以及雜湊表查詢來篩選事件。

如果您不是以系統管理員身分執行 PowerShell，您可能會看到錯誤訊息，指出您無法抓取記錄檔的相關資訊。

## 範例

### 範例1：從本機電腦取得所有記錄

此命令會取得本機電腦上的所有事件記錄檔。 記錄會以取得它們的順序列出 `Get-WinEvent` 。 傳統記錄檔會先抓取，接著是新的 Windows 事件記錄檔。
記錄檔的 **RecordCount** 可能是 null （空白或零）。

```powershell
Get-WinEvent -ListLog *
```

```Output
LogMode   MaximumSizeInBytes RecordCount LogName
-------   ------------------ ----------- -------
Circular            15532032       14500 Application
Circular             1052672         117 Azure Information Protection
Circular             1052672        3015 CxAudioSvcLog
Circular            20971520             ForwardedEvents
Circular            20971520           0 HardwareEvents
```

`Get-WinEvent`Cmdlet 會從電腦取得記錄資訊。 **ListLog** 參數會使用星號 (`*`) 萬用字元來顯示每個記錄檔的相關資訊。

### 範例2：取得傳統安裝程式記錄檔

此命令會取得代表傳統 **安裝程式** 記錄檔的 **system.diagnostics.eventing.reader.eventlogconfiguration** 物件。 物件包含記錄檔的相關資訊，例如檔案大小、提供者、檔案路徑，以及是否啟用記錄檔。

```powershell
Get-WinEvent -ListLog Setup | Format-List -Property *
```

```Output
FileSize                       : 69632
IsLogFull                      : False
LastAccessTime                 : 3/13/2019 09:41:46
LastWriteTime                  : 3/13/2019 09:41:46
OldestRecordNumber             : 1
RecordCount                    : 23
LogName                        : Setup
LogType                        : Operational
LogIsolation                   : Application
IsEnabled                      : True
IsClassicLog                   : False
SecurityDescriptor             : O:BAG:SYD: ...
LogFilePath                    : %SystemRoot%\System32\Winevt\Logs\Setup.evtx
MaximumSizeInBytes             : 1052672
LogMode                        : Circular
OwningProviderName             : Microsoft-Windows-Eventlog
ProviderNames                  : {Microsoft-Windows-WUSA, Microsoft-Windows-ActionQueue...
ProviderLevel                  :
ProviderKeywords               :
ProviderBufferSize             : 64
ProviderMinimumNumberOfBuffers : 0
ProviderMaximumNumberOfBuffers : 64
ProviderLatency                : 1000
ProviderControlGuid            :
```

此 `Get-WinEvent` Cmdlet 會使用 **ListLog** 參數來指定 **安裝程式** 記錄檔。 物件會向下傳送至 `Format-List` Cmdlet。 `Format-List` 使用 **Property** 參數搭配星號 (`*`) 萬用字元來顯示每個屬性。

### 範例3：取得伺服器的事件記錄檔

此命令只會取得本機電腦上包含事件的事件記錄檔。 記錄檔的 **RecordCount** 可能是 null 或零。 此範例會使用 `$_` 變數。 如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/about/about_automatic_variables.md)。

```powershell
Get-WinEvent -ListLog * -ComputerName localhost | Where-Object { $_.RecordCount }
```

```Output
LogMode   MaximumSizeInBytes RecordCount LogName
-------   ------------------ ----------- -------
Circular            15532032       14546 Application
Circular             1052672         117 Azure Information Protection
Circular             1052672        2990 CxAudioSvcLog
Circular             1052672           9 MSFTVPN Setup
Circular             1052672         282 OAlerts
```

`Get-WinEvent`Cmdlet 會從電腦取得記錄資訊。 **ListLog** 參數會使用星號 (`*`) 萬用字元來顯示每個記錄檔的相關資訊。 **ComputerName** 參數指定要從本機電腦（ **localhost** ）取得記錄。 這些物件會向下傳送至 `Where-Object` Cmdlet。 `Where-Object` 用 `$_.RecordCount` 來只傳回包含資料的記錄。 `$_` 這是一個變數，代表管線中的目前物件。 **RecordCount** 是具有非 null 值之物件的屬性。

### 範例4：取得多部伺服器的事件記錄檔

這個範例會取得物件，代表三部電腦上的 **應用程式** 事件記錄檔： Server01、Server02 和 Server03。 使用 **ForEach** 關鍵字的原因是 **ComputerName** 參數只接受一個值。 如需詳細資訊，請參閱 [about_Foreach](../Microsoft.PowerShell.Core/about/about_Foreach.md)。

```powershell
$S = 'Server01', 'Server02', 'Server03'
ForEach ($Server in $S) {
  Get-WinEvent -ListLog Application -ComputerName $Server |
    Select-Object LogMode, MaximumSizeInBytes, RecordCount, LogName,
      @{name='ComputerName'; expression={$Server}} |
    Format-Table -AutoSize
}
```

```Output
 LogMode MaximumSizeInBytes RecordCount LogName     ComputerName
 ------- ------------------ ----------- -------     ------------
Circular           15532032       14577 Application Server01
Circular           15532032        9689 Application Server02
Circular           15532032        5309 Application Server03
```

變數會 `$S` 將名稱儲存為三部伺服器： **Server01** 、 **Server02** 和 **Server03** 。 **ForEach** 語句會使用迴圈來處理每一部伺服器 `($Server in $S)` 。 大括弧 (中的腳本區塊會 `{ }`) 執行此 `Get-WinEvent` 命令。 **ListLog** 參數會指定 **應用程式** 記錄檔。 **ComputerName** 參數會使用變數 `$Server` 來取得每部伺服器的記錄資訊。

這些物件會向下傳送至 `Select-Object` Cmdlet。 `Select-Object` 取得屬性 **LogMode** 、 **MaximumSizeInBytes** 、 **RecordCount** 、 **LogName** ，並使用匯出運算式來顯示使用變數的 **ComputerName** `$Server` 。 這些物件會向下傳送至 Cmdlet， `Format-Table` 以在 PowerShell 主控台中顯示輸出。 **AutoSize** 參數會將輸出格式化為符合畫面。

### 範例5：取得事件記錄檔提供者和記錄檔名稱

此命令會取得事件記錄檔提供者以及它們所寫入的記錄檔。

```powershell
Get-WinEvent -ListProvider *
```

```Output
Name     : .NET Runtime
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : .NET Runtime Optimization Service
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}
```

`Get-WinEvent`Cmdlet 會從電腦取得記錄資訊。 **ListProvider** 參數會使用星號 (`*`) 萬用字元來顯示每個提供者的相關資訊。 在輸出中， **名稱** 是提供者，而 **LogLinks** 是提供者寫入的記錄檔。

### 範例6：取得寫入特定記錄檔的所有事件記錄提供者

此命令會取得寫入 **應用程式** 記錄檔的所有提供者。

```powershell
(Get-WinEvent -ListLog Application).ProviderNames
```

```Output
.NET Runtime
.NET Runtime Optimization Service
Application
Application Error
Application Hang
Application Management
```

`Get-WinEvent`Cmdlet 會從電腦取得記錄資訊。 **ListLog** 參數會使用 **應用程式** 取得該記錄檔的物件。 **ProviderNames** 是物件的屬性，會顯示寫入 **應用程式** 記錄檔的提供者。

### 範例7：取得包含特定字串的事件記錄檔提供者名稱

此命令會取得名稱中包含特定字串的事件記錄檔提供者名稱。

```powershell
Get-WinEvent -ListProvider *Policy*
```

```Output
Name     : Group Policy Applications
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : Group Policy Client
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : Group Policy Data Sources
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}
```

`Get-WinEvent`Cmdlet 會從電腦取得記錄資訊。 **ListProvider** 參數會使用星號 (`*`) 萬用字元來尋找提供者名稱內任何位置的 **原則** 。

### 範例8：取得事件提供者所產生的事件識別碼

此命令會列出 **Microsoft Windows GroupPolicy** 事件提供者所產生的事件識別碼以及事件描述。

```powershell
(Get-WinEvent -ListProvider Microsoft-Windows-GroupPolicy).Events | Format-Table Id, Description
```

```Output
  Id  Description
  --  -----------
1500  The Group Policy settings for the computer were processed successfully...
1501  The Group Policy settings for the user were processed successfully...
4115  Group Policy Service started.
4116  Started the Group Policy service initialization phase.
4117  Group Policy Session started.
```

`Get-WinEvent`Cmdlet 會從電腦取得記錄資訊。 **ListProvider** 參數會指定提供者 **GroupPolicy** 。 運算式會以括弧括住，並使用 **Events** 屬性來取得物件。 這些物件會向下傳送至 `Format-Table` Cmdlet。 `Format-Table` 顯示事件物件的 **識別碼** 和 **描述** 。

### 範例9：從事件物件屬性取得記錄資訊

這個範例示範如何使用事件物件屬性取得記錄檔內容的相關資訊。
事件物件會儲存在變數中，然後依 **事件識別碼** 和 **層級** 進行分組和計算。

```powershell
$Event = Get-WinEvent -LogName 'Windows PowerShell'
$Event.Count
$Event | Group-Object -Property Id -NoElement | Sort-Object -Property Count -Descending
$Event | Group-Object -Property LevelDisplayName -NoElement
```

```Output
195

Count  Name
-----  ----
  147  600
   22  400
   21  601
    3  403
    2  103

Count  Name
-----  ----
    2  Warning
  193  Information
```

此 `Get-WinEvent` Cmdlet 會使用 **LogName** 參數來指定 **Windows PowerShell** 事件記錄檔。 事件物件會儲存在變數中 `$Event` 。 的 [ **計數** ] 屬性會 `$Event` 顯示已記錄的事件總數。

此 `$Event` 變數會向下傳送至 `Group-Object` Cmdlet。 `Group-Object` 使用 **Property** 參數指定 **Id** 屬性，並依事件識別碼值來計算物件數目。 **NoElement** 參數會從物件輸出中移除其他屬性。 分組的物件會向下傳送至 `Sort-Object` Cmdlet。 `Sort-Object` 使用 **Property** 參數依 **計數** 排序物件。 **遞減** 參數會依計數顯示輸出，從最高到最低。 在輸出中，[ **計數** ] 資料行包含每個事件的總計數。 [ **名稱** ] 資料行包含已分組的事件識別碼。

此 `$Event` 變數會向下傳送至 `Group-Object` Cmdlet。 `Group-Object` 使用 **Property** 參數指定 **LevelDisplayName** 屬性，並依 **LevelDisplayName** 計算物件數目。 物件是依 **警告** 和 **資訊** 等層級進行分組。
**NoElement** 參數會從輸出中移除其他屬性。 在輸出中，[ **計數** ] 資料行包含每個事件的總計數。 [ **名稱** ] 資料行包含群組的 **LevelDisplayName** 。

### 範例10：取得名稱中有指定字串的錯誤事件

這個範例會使用以逗號分隔的記錄檔名稱字串。 輸出會依層級分組，例如錯誤或警告，以及記錄檔名稱。

```powershell
Get-WinEvent -LogName *PowerShell*, Microsoft-Windows-Kernel-WHEA* |
  Group-Object -Property LevelDisplayName, LogName -NoElement |
    Format-Table -AutoSize
```

```Output
Count  Name
-----  ----
    1  Error, PowerShellCore/Operational
   26  Information, Microsoft-Windows-Kernel-WHEA/Operational
  488  Information, Microsoft-Windows-PowerShell/Operational
   77  Information, PowerShellCore/Operational
 9835  Information, Windows PowerShell
   19  Verbose, PowerShellCore/Operational
  444  Warning, Microsoft-Windows-PowerShell/Operational
  512  Warning, PowerShellCore/Operational
```

`Get-WinEvent`Cmdlet 會從電腦取得記錄資訊。 **LogName** 參數會使用以逗號分隔的字串，並以星號 (`*`) 萬用字元來指定記錄檔名稱。 這些物件會向下傳送至 `Group-Object` Cmdlet。 `Group-Object` 使用 **Property** 參數，依 **LevelDisplayName** 和 **LogName** 將物件分組。 **NoElement** 參數會從輸出中移除其他屬性。 分組的物件會向下傳送至 `Format-Table` Cmdlet。 `Format-Table` 使用 **AutoSize** 參數來格式化資料行。 [ **計數** ] 資料行包含每個事件的總計數。 [ **名稱** ] 資料行包含已分組的 **LevelDisplayName** 和 **LogName** 。

### 範例11：從封存的事件記錄檔取得事件

`Get-WinEvent` 可以從已儲存的記錄檔取得事件資訊。 此範例會使用儲存在本機電腦上的封存 PowerShell 記錄檔。

```powershell
Get-WinEvent -Path 'C:\Test\Windows PowerShell.evtx'
```

```Output
   ProviderName: PowerShell

TimeCreated              Id LevelDisplayName  Message
-----------              -- ----------------  -------
3/15/2019 13:54:13      403 Information       Engine state is changed from Available to Stopped...
3/15/2019 13:54:13      400 Information       Engine state is changed from None to Available...
3/15/2019 13:54:13      600 Information       Provider "Variable" is Started...
3/15/2019 13:54:13      600 Information       Provider "Function" is Started...
3/15/2019 13:54:13      600 Information       Provider "FileSystem" is Started...
```

`Get-WinEvent`Cmdlet 會從電腦取得記錄資訊。 **Path** 參數會指定目錄和檔案名。

### 範例12：從封存的事件記錄檔中取得特定數目的事件

這些命令會從封存的事件記錄檔取得特定數目的事件。 `Get-WinEvent` 具有可取得事件數目上限或最舊事件的參數。 此範例會使用儲存在 **C:\Test\PowerShellCore 操作** 的封存 PowerShell 記錄檔。

```powershell
Get-WinEvent -Path 'C:\Test\PowerShellCore Operational.evtx' -MaxEvents 100
```

```Output
   ProviderName: PowerShellCore

TimeCreated                 Id   LevelDisplayName  Message
-----------                 --   ----------------  -------
3/15/2019 09:54:54        4104   Warning           Creating Scriptblock text (1 of 1):...
3/15/2019 09:37:13       40962   Information       PowerShell console is ready for user input
3/15/2019 07:56:24        4104   Warning           Creating Scriptblock text (1 of 1):...
...
3/7/2019 10:53:22        40961   Information       PowerShell console is starting up
3/7/2019 10:53:22         8197   Verbose           Runspace state changed to Opening
3/7/2019 10:53:22         8195   Verbose           Opening RunspacePool
```

`Get-WinEvent`Cmdlet 會從電腦取得記錄資訊。 **Path** 參數指定目錄和檔案名。 **MaxEvents** 參數會指定顯示100筆記錄，從最新到最舊。

### 範例13： Windows 的事件追蹤

Windows 事件追蹤 (ETW) 在事件發生時將事件寫入記錄檔。 這些事件會以最舊到最新的順序儲存。 封存的 ETW 檔案會儲存為 `.etl` **tracelog.exe。**
事件會依照寫入記錄檔的順序列出，因此需要 *最舊* 的參數。

```powershell
Get-WinEvent -Path 'C:\Tracing\TraceLog.etl' -Oldest |
  Sort-Object -Property TimeCreated -Descending |
    Select-Object -First 100
```

`Get-WinEvent`Cmdlet 會從封存的檔案取得記錄資訊。 **Path** 參數會指定目錄和檔案名。 **最舊** 的參數可用來依照寫入順序（最舊到最新）來輸出事件。 物件會向下傳送至 Cmdlet，以 `Sort-Object` `Sort-Object` 依 **TimeCreated** 屬性的值以遞減順序排序物件。 這些物件會向下傳送至 `Select-Object` Cmdlet，以顯示100最新的事件。

### 範例14：從事件追蹤記錄檔取得事件

這個範例示範如何從事件追蹤記錄檔取得事件 (`.etl`) ，以及 () 的封存 Windows PowerShell 記錄檔 `.evtx` 。 您可以在單一命令中結合多個檔案類型。
由於檔案包含相同類型的 **.NET Framework** 物件 **EventLogRecord** ，因此您可以使用相同的屬性來篩選它們。 此命令需要 **最舊** 的參數，因為它是從檔案讀取 `.etl` ，但是 **最舊** 的參數會套用至每個檔案。

```powershell
Get-WinEvent -Path 'C:\Tracing\TraceLog.etl', 'C:\Test\Windows PowerShell.evtx' -Oldest |
  Where-Object { $_.Id -eq '403' }
```

`Get-WinEvent`Cmdlet 會從封存的檔案取得記錄資訊。 **Path** 參數會使用以逗號分隔的清單來指定每個檔案目錄和檔案名。 **最舊** 的參數可用來依照寫入順序（最舊到最新）來輸出事件。 這些物件會向下傳送至 `Where-Object` Cmdlet。 `Where-Object` 使用腳本區塊來尋找 **識別碼** 為 **403** 的事件。 `$_`變數代表管線中目前的物件，而 **識別碼** 是事件識別碼屬性。

### 範例15：篩選事件記錄檔結果

此範例顯示各種不同的方法，可篩選並從事件記錄檔中選取事件。 所有這些命令都會從 **Windows PowerShell** 事件記錄檔取得過去24小時內發生的事件。
篩選方法比使用 Cmdlet 更有效率 `Where-Object` 。 篩選準則會在抓取物件時套用。 `Where-Object` 抓取所有物件，然後將篩選套用至所有物件。

```powershell
# Using the Where-Object cmdlet:
$Yesterday = (Get-Date) - (New-TimeSpan -Day 1)
Get-WinEvent -LogName 'Windows PowerShell' | Where-Object { $_.TimeCreated -ge $Yesterday }

# Using the FilterHashtable parameter:
$Yesterday = (Get-Date) - (New-TimeSpan -Day 1)
Get-WinEvent -FilterHashtable @{ LogName='Windows PowerShell'; Level=3; StartTime=$Yesterday }

# Using the FilterXML parameter:
$xmlQuery = @'
<QueryList>
  <Query Id="0" Path="Windows PowerShell">
    <Select Path="System">*[System[(Level=3) and
        TimeCreated[timediff(@SystemTime) &lt;= 86400000]]]</Select>
  </Query>
</QueryList>
'@
Get-WinEvent -FilterXML $xmlQuery

# Using the FilterXPath parameter:
$XPath = '*[System[Level=3 and TimeCreated[timediff(@SystemTime) &lt;= 86400000]]]'
Get-WinEvent -LogName 'Windows PowerShell' -FilterXPath $XPath
```

### 範例16：使用 FilterHashtable 從應用程式記錄檔取得事件

此範例使用 **FilterHashtable** 參數從 **應用程式** 記錄檔取得事件。 雜湊表使用索引 **鍵/值** 組。 如需 **FilterHashtable** 參數的詳細資訊，請參閱 [使用 FilterHashtable 建立 Get-WinEvent 查詢](/powershell/scripting/samples/Creating-Get-WinEvent-queries-with-FilterHashtable)。
如需雜湊表的相關詳細資訊，請參閱 [about_Hash_Tables](../Microsoft.PowerShell.Core/about/about_hash_tables.md)。

```powershell
$Date = (Get-Date).AddDays(-2)
Get-WinEvent -FilterHashtable @{ LogName='Application'; StartTime=$Date; Id='1003' }
```

此 `Get-Date` Cmdlet 會使用 **AddDays** 方法來取得目前日期前兩天的日期。 Date 物件儲存在 `$Date` 變數中。

`Get-WinEvent`Cmdlet 會取得記錄資訊。 **FilterHashtable** 參數是用來篩選輸出。 **LogName** 索引鍵會將值指定為 **應用程式** 記錄檔。 **StartTime** 索引鍵會使用儲存在變數中的值 `$Date` 。 **識別碼** 索引鍵會使用事件識別碼值 **1003** 。

### 範例17：使用 FilterHashtable 取得應用程式錯誤

此範例會使用 **FilterHashtable** 參數，找出在上周發生 Internet Explorer 應用程式錯誤。

```powershell
$StartTime = (Get-Date).AddDays(-7)
Get-WinEvent -FilterHashtable @{
  Logname='Application'
  ProviderName='Application Error'
  Data='iexplore.exe'
  StartTime=$StartTime
}
```

此 `Get-Date` Cmdlet 會使用 **AddDays** 方法來取得目前日期前七天的日期。 Date 物件儲存在 `$StartTime` 變數中。

`Get-WinEvent`Cmdlet 會取得記錄資訊。 **FilterHashtable** 參數是用來篩選輸出。 **LogName** 索引鍵會將值指定為 **應用程式** 記錄檔。 **ProviderName** 索引鍵會使用值，也就是 **應用程式錯誤** ，也就是事件的 **來源** 。 **資料** 索引鍵會使用值 **iexplore.exe** **StartTime** 索引鍵使用儲存在變數中的值 `$StartTime` 。

## PARAMETERS

### -ComputerName

指定此 Cmdlet 從事件記錄檔取得事件的電腦名稱稱。 輸入電腦的 NetBIOS 名稱、IP 位址或完整功能變數名稱 (FQDN) 。 預設值為本機電腦 **localhost** 。 此參數一次只能接受一個電腦名稱。

若要從遠端電腦取得事件記錄檔，請將事件記錄檔服務的防火牆埠設定為允許遠端存取。

此 Cmdlet 不依賴 PowerShell 遠端功能。 即使您的電腦未設定為執行遠端命令，您仍然可以使用 **ComputerName** 參數。

```yaml
Type: System.String
Parameter Sets: GetLogSet, ListLogSet, ListProviderSet, GetProviderSet, HashQuerySet, XmlQuerySet
Aliases: Cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作權限的使用者帳戶。 預設值為目前使用者。

輸入使用者名稱，例如 **User01** 或 **Domain01\User01** 。 或者，輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。 若您輸入使用者名稱時，會提示您輸入密碼。 如果您只輸入參數名稱，系統會提示您輸入使用者名稱和密碼。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterHashtable

指定雜湊資料表格式的查詢，以從一或多個事件記錄檔選取事件。 查詢包含具有一或多個索引 **鍵/值** 組的雜湊表。

雜湊資料表查詢有下列規則：

- 索引鍵和值不區分大小寫。
- 萬用字元只有在與 **LogName** 和 **ProviderName** 索引鍵相關聯的值中才有效。
- 每個索引鍵只能在每個雜湊表中列出一次。
- **路徑** 值會取得 `.etl` 、 `.evt` 和記錄檔的路徑 `.evtx` 。
- **LogName** 、 **Path** 和 **ProviderName** 索引鍵可以在相同的查詢中使用。
- **UserID** 金鑰可以取得有效的安全識別碼 (SID) 或可用來建立有效 **NTAccount 物件** 的網域帳戶名稱。
- **資料** 值會接受未命名欄位中的事件資料。 例如，傳統事件記錄檔中的事件。

當 `Get-WinEvent` 無法解讀索引 **鍵/值** 組時，它會針對事件中的事件資料，將索引鍵解釋為區分大小寫的名稱。

有效的索引 `Get-WinEvent` **鍵/值** 組如下所示：

- **LogName**=`<String[]>`
- **ProviderName**=`<String[]>`
- **路徑**=`<String[]>`
- **關鍵 字**=`<Long[]>`
- **Id**=`<Int32[]>`
- **水準**=`<Int32[]>`
- **StartTime**=`<DateTime>`
- **EndTime**=`<DateTime>`
- **UserID**=`<SID>`
- **資料**=`<String[]>`

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: HashQuerySet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterXPath

指定此 Cmdlet 從一個或多個記錄檔中選取事件的 XPath 查詢。

如需有關 XPath 語言的詳細資訊，請參閱[事件選取專案](/previous-versions/aa385231(v=vs.85))的 [ [xpath 參考](/previous-versions/dotnet/netframework-4.0/ms256115(v=vs.100))] 和 [選取篩選] 區段。

```yaml
Type: System.String
Parameter Sets: GetLogSet, GetProviderSet, FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterXml

指定結構化 XML 查詢，此 Cmdlet 會從一或多個事件記錄檔中選取事件。

若要產生有效的 XML 查詢，請使用 Windows 事件檢視器中的 [ **建立自訂視圖** ] 和 [ **篩選目前的記錄** ] 功能。 使用對話方塊中的項目建立查詢，然後按一下 XML 索引標籤來使用 XML 格式檢視查詢。 您也可以從 XML 索引標籤將 XML 複製到 **FilterXml** 參數的值。 如需事件檢視器功能的詳細資訊，請參閱事件檢視器說明。

您可以使用 XML 查詢來建立包含數個 XPath 語句的複雜查詢。 XML 格式也可讓您使用 **抑制 XML** 專案，該專案會從查詢中排除事件。 如需事件記錄檔查詢之 XML 架構的詳細資訊，請參閱[事件選取範圍](/previous-versions/aa385231(v=vs.85))的[查詢架構](/windows/win32/wes/queryschema-schema)和 xml 事件查詢一節。

```yaml
Type: System.Xml.XmlDocument
Parameter Sets: XmlQuerySet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

除了其他事件記錄檔之外，也會取得偵錯和分析記錄檔。 當名稱參數的值包括萬用字元時， **Force** 參數為取得偵錯或分析記錄檔的必要參數。

依預設，此 `Get-WinEvent` Cmdlet 會排除這些記錄檔，除非您指定 debug 或 analytics 記錄檔的完整名稱。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetLogSet, ListLogSet, GetProviderSet, HashQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ListLog

指定事件記錄檔。 以逗號分隔的清單方式輸入事件記錄檔名稱。 允許使用萬用字元。 若要取得所有記錄檔，請使用星號 (`*`) 萬用字元。

```yaml
Type: System.String[]
Parameter Sets: ListLogSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ListProvider

指定此 Cmdlet 取得的事件記錄檔提供者。 事件記錄檔提供者是將事件寫入事件記錄檔的程式或服務。

以逗號分隔的清單方式輸入提供者名稱。 允許使用萬用字元。 若要取得電腦上所有事件記錄檔的提供者，請使用星號 (`*`) 萬用字元。

```yaml
Type: System.String[]
Parameter Sets: ListProviderSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LogName

指定此 Cmdlet 從中取得事件的事件記錄檔。 以逗號分隔的清單方式輸入事件記錄檔名稱。 允許使用萬用字元。 您也可以透過管線將記錄檔名稱傳送至 `Get-WinEvent` Cmdlet。

> [!NOTE]
> PowerShell 不會限制您可以要求的記錄數量。 不過，此 `Get-WinEvent` Cmdlet 會查詢 WINDOWS API，其限制為256。 這可能會讓您難以一次篩選所有記錄。 若要解決此問題，您可以使用 `foreach` 迴圈逐一查看每個記錄檔，如下所示： `Get-WinEvent -ListLog * | ForEach-Object{ Get-WinEvent -LogName $_.Logname }`

```yaml
Type: System.String[]
Parameter Sets: GetLogSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -MaxEvents

指定傳回的最大事件數目。 輸入整數，例如100。 預設值為傳回記錄檔或檔案中的所有事件。

```yaml
Type: System.Int64
Parameter Sets: GetLogSet, GetProviderSet, FileSet, HashQuerySet, XmlQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -最舊

指出此 Cmdlet 會以最舊的第一個順序取得事件。 根據預設，事件是最新者先傳回的順序傳回。

此參數是從 `.etl` 和檔案 `.evt` ，以及從偵測和分析記錄檔取得事件時所需的參數。 在這些檔案中，事件是以最舊者先記錄的順序記錄，並且只能以最舊者先傳回的順序傳回事件。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetLogSet, GetProviderSet, FileSet, HashQuerySet, XmlQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定此 Cmdlet 從中取得事件之事件記錄檔的路徑。 在使用逗號分隔的清單中輸入記錄檔路徑，或使用萬用字元來建立檔案路徑模式。

`Get-WinEvent` 支援具有、和副檔名的檔案 `.evt` `.evtx` `.etl` 。 您可以在同一個命令中包含來自不同檔案和檔案類型的事件。

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ProviderName

以字串陣列指定此 Cmdlet 從中取得事件的事件記錄檔提供者。 在使用逗號區隔的清單中輸入提供者名稱，或使用萬用字元來建立提供者名稱模式。

事件記錄檔提供者是將事件寫入事件記錄檔的程式或服務。 它不是 PowerShell 提供者。

```yaml
Type: System.String[]
Parameter Sets: GetProviderSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.string、System.Xml.Xml檔、System.object

您可以使用管線將 **LogName** (字串) 、 **FilterXML** 查詢或 **FilterHashtable** 查詢管線至 `Get-WinEvent` 。

## 輸出

### System.diagnostics.eventing.reader.eventlogconfiguration，EventLogRecord，，ProviderMetadata 的，中的程式，系統中的

使用 **ListLog** 參數，會 `Get-WinEvent` 傳回 **system.diagnostics.eventing.reader.eventlogconfiguration** 物件。

使用 **ListProvider** 參數，會 `Get-WinEvent` 傳回 **ProviderMetadata** 物件。

使用所有其他參數時，會傳回 `Get-WinEvent` **EventLogRecord** 物件。

## 注意

`Get-WinEvent` 的設計目的是要取代執行 `Get-EventLog` Windows Vista 和更新版本之 windows 電腦上的 Cmdlet。 `Get-EventLog` 只取得傳統事件記錄檔中的事件。 `Get-EventLog` 保留以提供回溯相容性。

`Get-WinEvent` `Get-EventLog` Windows 預先安裝環境 (Windows PE) 不支援和 Cmdlet。

## 相關連結

[about_Automatic_Variables](../Microsoft.PowerShell.Core/about/about_automatic_variables.md)

[about_Foreach](../Microsoft.PowerShell.Core/about/about_Foreach.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/about/about_hash_tables.md)

[使用 FilterHashtable 建立 Get-WinEvent 查詢](/powershell/scripting/samples/Creating-Get-WinEvent-queries-with-FilterHashtable)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Sort-Object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
