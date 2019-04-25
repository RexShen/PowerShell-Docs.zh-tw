---
ms.date: 3/18/2019
title: 使用 FilterHashtable 建立 Get-WinEvent 查詢
ms.openlocfilehash: 28ba3c99a297944003a28eaba7de34b77d9df536
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058799"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>使用 FilterHashtable 建立 Get-WinEvent 查詢

若要閱讀原始的 2014 年 6 月 3 日 **Scripting Guy** 部落格文章，請參閱[使用 FilterHashTable 搭配 PowerShell 篩選事件記錄檔](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/) \(英文\)。

本文是原始部落格文章的摘錄，並說明如何使用 `Get-WinEvent` Cmdlet 的 **FilterHashtable** 參數來篩選事件記錄檔。 PowerShell 的 `Get-WinEvent` Cmdlet 是一種功能強大的方法，可篩選 Windows 事件和診斷記錄。 `Get-WinEvent` 查詢使用 **FilterHashtable** 參數時，效能會提高。

當您使用大型事件記錄檔時，將管線中的物件傳送到 `Where-Object` 命令不是有效率的方式。 在 PowerShell 6 之前，`Get-EventLog` Cmdlet 是取得記錄資料的另一個選項。 例如，下列命令篩選 **Microsoft-Windows-Defrag** 記錄檔的效率不佳：

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

下列命令會使用雜湊表，可改善效能：

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>關於列舉的部落格文章

本文介紹有關如何在雜湊表中使用列舉值的資訊。 如需有關列舉的詳細資訊，請參閱這些 **Scripting Guy** 部落格文章。 若要建立傳回列舉值的函式，請參閱[列舉和值](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values)。
如需詳細資訊，請參閱[有關列舉的 Scripting Guy 部落格系列文章](https://devblogs.microsoft.com/scripting/?s=about+enumeration)。

## <a name="hash-table-keyvalue-pairs"></a>雜湊資料表索引鍵/值組

若要建立有效率的查詢，請將 `Get-WinEvent` Cmdlet 與 **FilterHashtable** 參數一起使用。
**FilterHashtable** 接受雜湊表作為篩選條件，以從 Windows 事件記錄檔中取得特定資訊。 雜湊資料表使用**索引鍵/值**組。 如需雜湊表的相關詳細資訊，請參閱 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)。

如果**索引鍵/值**組位於同一行上，則必須以分號分隔。 如果每個**索引鍵/值**組位於不同行上，則不需要分號。 例如，本文將**索引鍵/值**組放在不同的行上，且不使用分號。

此範例會使用數個 **FilterHashtable** 參數的**索引鍵/值**組。 已完成的查詢中包括 **LogName**、**ProviderName**、**Keywords**、**ID** 與 **Level**。

接受的**索引鍵/值**組如下表所示，並包含在 [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** 參數的文件中。

下表顯示索引鍵名稱、資料類型，以及資料值是否接受萬用字元。

| 機碼名稱     | 數值資料類型    | 接受萬用字元？ |
|------------- | ------------------ | ---------------------------- |
| LogName      | `<String[]>`       | 是 |
| ProviderName | `<String[]>`       | 是 |
| 路徑         | `<String[]>`       | 否  |
| 關鍵字     | `<Long[]>`         | 否  |
| ID           | `<Int32[]>`        | 否  |
| 層級        | `<Int32[]>`        | 否  |
| StartTime    | `<DateTime>`       | 否  |
| EndTime      | `<DateTime>`       | 否  |
| UserID       | `<SID>`            | 否  |
| 資料         | `<String[]>`       | 否  |
| *            | `<String[]>`       | 否  |

## <a name="building-a-query-with-a-hash-table"></a>使用雜湊表建立查詢

若要驗證結果並針對問題進行疑難排解，最好一次一個**索引鍵/值**組來建置雜湊表。 該查詢會從**應用程式**記錄檔中取得資料。 雜湊表就相當於 `Get-WinEvent –LogName Application`。

首先，建立 `Get-WinEvent` 查詢。 使用 **FilterHashtable** 參數的**索引鍵/值**組，其中索引鍵為 **LogName** 而值為 **Application**。

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

繼續使用 **ProviderName** 索引鍵建置雜湊表。 **ProviderName** 是 **Windows 事件檢視器**中 [來源] 欄位中顯示的名稱。 例如，下列螢幕擷取畫面中的 **.NET Runtime**：

![Windows 事件檢視器來源的影像。](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

更新雜湊表，並包含**索引鍵/值**組，其中索引鍵為 **ProviderName，而值為 **.NET Runtime**。

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

如果您的查詢需要從封存事件記錄檔中取得資料，請使用 **Path** 索引鍵。 **Path** 值會指定記錄檔的完整路徑。 如需詳細資訊，請參閱 **Scripting Guy** 部落格文章[使用 PowerShell 剖析儲存的事件記錄檔以尋找錯誤](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors)。

## <a name="using-enumerated-values-in-a-hash-table"></a>使用雜湊表中的列舉值

**Keywords** 是雜湊表中的下一個索引鍵。 **Keywords** 資料類型是包含大量數字之 `[long]` 實值型別的陣列。 使用下列命令來尋找 `[long]` 的最大值：

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

針對 **Keywords** 索引鍵，PowerShell 會使用數字，而不是**安全性**等字串。 **Windows 事件檢視器**將 **Keywords** 顯示為字串，但它們是列舉值。 在雜湊表中，如果您使用帶有字串值的 **Keywords** 索引鍵，則會顯示錯誤訊息。

開啟 **Windows 事件檢視器**，然後從 [動作] 窗格中，按一下 [篩選目前的記錄]。
**Keywords** 下拉式功能表會顯示可用的關鍵字，如下列螢幕擷取畫面所示：

![Windows 事件檢視器關鍵字的影像。](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

使用下列命令來顯示 `StandardEventKeywords` 屬性名稱。

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

列舉值記錄在 **.NET Framework** 中。 如需詳細資訊，請參閱 [StandardEventKeywords 列舉](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2)。

**Keywords** 名稱和列舉值如下所示：

| 名稱             |  值            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| Sqm              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| ResponseTime     | 281474976710656   |
| 無             | 0                 |

更新雜湊表並包含**索引鍵/值**組，其中索引鍵為 **Keywords**，而 **EventLogClassic** 列舉值為 **36028797018963968**。

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>關鍵字靜態屬性值 (選擇性)

列舉 **Keywords** 索引鍵，但您可以在雜湊表查詢中使用靜態屬性名稱。
必須將屬性名稱轉換為具有 **Value__** 屬性的值，而不是使用傳回的字串。

例如，下列指令碼會使用 **Value__** 屬性。

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>依事件識別碼篩選

若要取得更特定的資料，查詢的結果將依**事件識別碼**進行篩選。雜湊表中將**事件識別碼**作為索引鍵 **ID** 參考，且值為特定**事件識別碼**。**Windows 事件檢視器**會顯示**事件識別碼**。這個範例會使用**事件識別碼 1023**。

更新雜湊表，並包含**索引鍵/值**組，其中索引鍵為 **ID**，而值為 **1023**。

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>依層級篩選

若要進一步精簡結果並僅包含錯誤的事件，請使用 **Level** 索引鍵。
**Windows 事件檢視器**將 **Level** 顯示為字串值，但它們是列舉值。 在雜湊表中，如果您使用帶有字串值的 **Level** 索引鍵，則會顯示錯誤訊息。

**Level** 的值包括 **Error**、**Warning** 或 **Informational**。 使用下列命令來顯示 `StandardEventLevel` 屬性名稱。

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

列舉值記錄在 **.NET Framework** 中。 如需詳細資訊，請參閱 [StandardEventLevel 列舉](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2)。

**Level** 索引鍵的名稱和列舉值如下所示：

| 名稱           | 值 |
| -------------- | ----- |
| Verbose        |   5   |
| 資訊  |   4   |
| Warning        |   3   |
| 錯誤          |   2   |
| 重大       |   1   |
| LogAlways      |   0   |

已完成查詢的雜湊表包含索引鍵 **Level** 和值 **2**。

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>列舉中的層級靜態屬性 (選用)

列舉 **Level** 索引鍵，但您可以在雜湊表查詢中使用靜態屬性名稱。
必須將屬性名稱轉換為具有 **Value__** 屬性的值，而不是使用傳回的字串。

例如，下列指令碼會使用 **Value__** 屬性。

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```