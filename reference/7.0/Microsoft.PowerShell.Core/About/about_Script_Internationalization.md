---
description: 描述腳本國際化功能，可讓腳本輕鬆地在使用者介面中顯示使用者介面的訊息和指示 (UI) 語言。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_internationalization?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Internationalization
ms.openlocfilehash: dddf090ba18ca9eb703b307db9fddcdb88e4a5ac
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206591"
---
# <a name="about-script-internationalization"></a>關於腳本國際化

## <a name="short-description"></a>簡短描述
描述腳本國際化功能，可讓腳本輕鬆地在使用者介面中顯示使用者介面的訊息和指示 (UI) 語言。

## <a name="long-description"></a>完整描述

PowerShell script 國際化功能可讓您以使用者的語言顯示說明和使用者訊息，更有效地提供全球各地的使用者。

腳本國際化功能可在執行期間查詢作業系統的 UI 文化特性，匯入適當的已翻譯文字字串，並將其顯示給使用者。 Data 區段可讓您將文字字串與程式碼分開儲存，以便輕鬆地識別和解壓縮文字字串。 新的 Cmdlet 會 `ConvertFrom-StringData` 將文字字串轉換成類似字典的雜湊表，以加速轉譯。

為了支援國際化的解說文字，PowerShell 包含下列功能：

- 分隔文字字串與程式碼指令的資料區段。 如需有關 [資料] 區段的詳細資訊，請參閱 [about_Data_Sections](about_Data_Sections.md)。

- 新的自動變數 `$PSCulture` 和 `$PSUICulture` 。 `$PSCulture` 儲存用於系統上的 UI 語言名稱，以用於專案，例如日期、時間和貨幣。 `$PSUICulture`變數會儲存系統上用於使用者介面元素（例如功能表和文字字串）之 UI 語言的名稱。

- Cmdlet， `ConvertFrom-StringData` 它會將文字字串轉換成類似字典的雜湊表，以促進轉譯。 如需詳細資訊，請參閱 [convertfrom-string-至 convertfrom-stringdata](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)。

- 新的檔案類型， `.psd1` 儲存已翻譯的文字字串。 這些檔案 `.psd1` 會儲存在腳本目錄的特定語言子目錄中。

- Cmdlet， `Import-LocalizedData` 它會在執行時間將指定語言的已翻譯文字字串匯入腳本中。 此 Cmdlet 會以任何支援 Windows 的語言辨識和匯入字串。 如需詳細資訊，請參閱 [>import-localizeddata](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)。

### <a name="the-data-section-storing-default-strings"></a>Data 區段：儲存預設字串

使用腳本中的資料區段，以預設語言儲存文字字串。 將字串中的索引鍵/值組中的字串排列。 每個索引鍵/值組都必須位於不同的行。 如果您包含批註，批註必須位於不同的行。

此 `ConvertFrom-StringData` Cmdlet 會將此字串中的索引鍵/值組轉換成類似字典的雜湊表，並儲存在 Data 區段變數的值中。

在下列範例中，腳本的 Data 區段 `World.ps1` 包含 English-United 狀態 (en-us) 腳本的提示訊息集。 `ConvertFrom-StringData`Cmdlet 會將字串轉換成雜湊表，並將它們儲存在 `$msgtable` 變數中。

```powershell
$msgTable = Data {
    #culture="en-US"
    ConvertFrom-StringData @'
    helloWorld = Hello, World.
    errorMsg1 = You cannot leave the user name field blank.
    promptMsg = Please enter your user name.
'@
}
```

如需有關此字串的詳細資訊，請參閱 [about_Quoting_Rules](about_Quoting_Rules.md)。

### <a name="psd1-files-storing-translated-strings"></a>.PSD1 檔案：儲存轉譯的字串

將每個 UI 語言的腳本訊息儲存在與腳本同名的不同文字檔中，並將其命名為 `.psd1` 副檔名。 以下列格式，將檔案儲存在腳本目錄中具有文化特性名稱的子目錄：

`<language>-<region>`

範例： de/DE、ar-SA 和 zh-Hans

例如，如果 `World.ps1` 腳本儲存在 `C:\Scripts` 目錄中，您會建立如下的檔案目錄結構：

```
C:\Scripts
C:\Scripts\World.ps1
C:\Scripts\de-DE\World.psd1
C:\Scripts\ar-SA\World.psd1
C:\Scripts\zh-CN\World.psd1
...
```

`World.psd1`腳本目錄的解除刪除子目錄中的檔案可能包含下列語句：

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = Hallo, Welt.
errorMsg1 = Das Feld Benutzername darf nicht leer sein.
promptMsg = Geben Sie Ihren Benutzernamen ein.
'@
```

同樣地， `World.psd1` 腳本目錄的 ar-SA 子目錄中的檔案可能包含下列語句：

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = مرحبًا أيها العالَم
errorMsg1 = لا يمكنك ترك حقل اسم المستخدم فارغًا
promptMsg = يرجى إدخال اسم المستخدم الخاص بك
'@
```

### <a name="import-localizeddata-dynamic-retrieval-of-translated-strings"></a>>import-localizeddata：動態抓取翻譯的字串

若要以目前使用者的 UI 語言取出字串，請使用 `Import-LocalizedData` Cmdlet。

`Import-LocalizedData` 尋找自動變數的值 `$PSUICulture` ，並匯入 `<script-name>.psd1` 符合值之子目錄中的檔案內容 `$PSUICulture` 。 然後，它會將匯入的內容儲存在 **BindingVariable** 參數值所指定的變數中。

```powershell
Import-LocalizedData -BindingVariable msgTable
```

例如，如果 `Import-LocalizedData` 命令出現在腳本中， `C:\Scripts\World.ps1` 且值 `$PSUICulture` 為 "ar-SA"，則會 `Import-LocalizedData` 尋找下列檔案：

`C:\Scripts\ar-SA\World.psd1`

然後，它會將檔案中的阿拉伯文文字字串匯入到 `$msgTable` 變數中，取代任何可能在腳本的 Data 區段中定義的預設字串 `World.ps1` 。

因此，當腳本使用 `$msgTable` 變數來顯示使用者訊息時，訊息會以阿拉伯文顯示。

例如，下列腳本會以阿拉伯文顯示「請輸入您的使用者名稱」訊息：

```powershell
if (!($username)) { $msgTable.promptMsg }
```

如果找 `Import-LocalizedData` 不到 `.psd1` 符合值的檔案，則 `$PSUIculture` `$msgTable` 不會取代的值，而且會呼叫來顯示回復 `$msgTable.promptMsg` 的 en-us 字串。

## <a name="examples"></a>範例

這個範例示範如何在腳本中使用腳本國際化功能，以電腦上所設定的語言顯示一周的某一天。

以下是 Sample1.ps1 腳本檔案的完整清單。

腳本一開始會有一個名為 Day ($Day) 包含命令的資料區段 `ConvertFrom-StringData` 。 提交至的運算式 `ConvertFrom-StringData` 是在此字串中，其中包含預設 UI 文化特性中的日名稱（en-us），其成對的索引鍵/值組。 `ConvertFrom-StringData`Cmdlet 會將此字串中的索引鍵/值組轉換成雜湊表，然後將它儲存在變數的值中 `$Day` 。

此命令會將檔案的 `Import-LocalizedData` 內容匯入 `.psd1` 到符合自動變數值的目錄中， `$PSUICulture` 然後將它儲存在變數中 `$Day` ，以取代 `$Day` Data 區段中所定義的值。

其餘的命令會將字串載入至陣列，並加以顯示。

```powershell
$Day = Data {
#culture="en-US"
ConvertFrom-StringData -StringData @'
    messageDate = Today is
    d0 = Sunday
    d1 = Monday
    d2 = Tuesday
    d3 = Wednesday
    d4 = Thursday
    d5 = Friday
    d6 = Saturday
'@
}

Import-LocalizedData -BindingVariable Day

#Build an array of weekdays.
$a = $Day.d0, $Day.d1, $Day.d2, $Day.d3, $Day.d4, $Day.d5, $Day.d6

# Get the day of the week as a number (Monday = 1).
# Index into $a to get the name of the day.
# Use string formatting to build a sentence.

"{0} {1}" -f $Day.messageDate, $a[(Get-Date -UFormat %u)] | Out-Host
```

`.psd1`支援腳本的檔案會儲存在腳本目錄的子目錄中，且名稱與 `$PSUICulture` 值相符。

以下是完整的清單 `.\de-DE\sample1.psd1` ：

```powershell
# culture="de-DE"
ConvertFrom-StringData @'
    messageDate = Heute ist
    d0 = Sonntag
    d1 = Montag
    d2 = Dienstag
    d3 = Mittwoch
    d4 = Donnerstag
    d5 = Freitag
    d6 = Samstag
'@
```

如此一來，當您在的系統上執行 Sample.ps1 取消刪除時 `$PSUICulture` ，腳本的輸出為：

```Output
Heute ist Freitag
```

## <a name="see-also"></a>另請參閱

- [about_Data_Sections](about_Data_Sections.md)
- [about_Automatic_Variables](about_Automatic_Variables.md)
- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Quoting_Rules](about_Quoting_Rules.md)
- [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
- [Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)
