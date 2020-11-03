---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-localizeddata?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-LocalizedData
ms.openlocfilehash: f43c8f56900782994602df07288ec8c1465c1ffc
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239919"
---
# Import-LocalizedData

## 概要
根據為作業系統選取的 UI 文化特性，將語言特定資料匯入指令碼和函式。

## SYNTAX

```
Import-LocalizedData [[-BindingVariable] <String>] [[-UICulture] <String>] [-BaseDirectory <String>]
 [-FileName <String>] [-SupportedCommand <String[]>] [<CommonParameters>]
```

## DESCRIPTION

此 `Import-LocalizedData` Cmdlet 會從名稱符合為作業系統目前使用者設定之 UI 語言的子目錄，動態抓取字串。 它是專為讓指令碼以目前使用者選取的 UI 語言顯示使用者訊息而設計。

`Import-LocalizedData` 從 `.psd1` 腳本目錄之語言特定子目錄中的檔案匯入資料，並將其儲存在命令中指定的本機變數中。 此 Cmdlet 會根據自動變數的值來選取子目錄和檔案 `$PSUICulture` 。 在指令碼中使用區域變數來顯示使用者訊息時，訊息會以使用者的 UI 語言顯示。

您可以使用的參數 `Import-LocalizedData` 來指定替代的 UI 文化特性、路徑及檔案名、新增支援的命令，以及抑制找不到檔案時所出現的錯誤訊息 `.psd1` 。

此 `Import-LocalizedData` Cmdlet 支援 Windows PowerShell 2.0 中引進的腳本國際化計畫。 這個計畫的目標是要藉由讓指令碼能輕鬆以目前使用者的 UI 語言顯示使用者訊息，為世界各地的使用者提供更好的服務。 如需有關這項資訊以及檔案格式的詳細資訊 `.psd1` ，請參閱 [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)。

## 範例

### 範例 1︰匯入文字字串

此範例會將文字字串匯入到 `$Messages` 變數中。 它會使用所有其他 Cmdlet 參數的預設值。

```powershell
Import-LocalizedData -BindingVariable "Messages"
```

如果命令包含在目錄中的 Archives.ps1 腳本中 `C:\Test` ，且 `$PsUICulture` 自動變數的值為 ZH-CN，則會將目錄中的檔案匯 `Import-LocalizedData` 入 `Archives.psd1` `C:\test\zh-CN` 到變數中 `$Messages` 。

### 範例 2︰匯入當地語系化資料字串

此範例會在命令列中執行，而不是在腳本中執行。 它會從 Test.psd1 檔案取得當地語系化資料字串，並在命令列中顯示這些字串。 由於此命令不是用於指令碼中，因此必須使用 **FileName** 參數。 此命令使用 **UICulture** 參數來指定 en-US 文化特性。

```powershell
Import-LocalizedData -FileName "Test.psd1" -UICulture "en-US"
```

```Output
Name                           Value
----                           -----
Msg3                           "Use $_ to represent the object that is being processed."
Msg2                           "This command requires the credentials of a member of the Administrators group on the...
Msg1                           "The Name parameter is missing from the command."
```

`Import-LocalizedData` 傳回包含當地語系化資料字串的雜湊表。

### 範例 3︰匯入 UI 文化特性字串

```powershell
Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

此命令會將文字字串匯入到 `$MsgTbl` 腳本的變數中。

它會使用 **UICulture** 參數指示 Cmdlet 從的子目錄中的檔案匯入資料 `Simple.psd1` `ar-SA` `C:\Data\Localized` 。

### 範例 4︰將當地語系化資料匯入指令碼

這個範例示範如何在簡單的指令碼中使用當地語系化資料。

```powershell
PS C:\> # In C:\Test\en-US\Test.psd1:

ConvertFrom-StringData @'

# English strings

Msg1 = "The Name parameter is missing from the command."
Msg2 = "This command requires the credentials of a member of the Administrators group on the computer."
Msg3 = "Use $_ to represent the object that is being processed."
'@

# In C:\Test\Test.ps1

Import-LocalizedData -BindingVariable "Messages"
Write-Host $Messages.Msg2

# In Windows PowerShell

PS C:\> .\Test.ps1

This command requires the credentials of a member of the Administrators group on the computer.
```

此範例的第一個部分會顯示檔案的內容 `Test.psd1` 。 它包含的 `ConvertFrom-StringData` 命令會將一系列的已命名文字字串轉換成雜湊表。 檔案 `Test.psd1` 位於包含腳本之目錄的 en-us 子目錄中 `C:\Test` 。

此範例的第二個部分會顯示腳本的內容 `Test.ps1` 。 它包含 `Import-LocalizedData` 的命令會將相符檔案中的資料匯入 `.psd1` `$Messages` 變數，以及將 `Write-Host` 變數中的其中一個訊息寫入 `$Messages` 至主機程式的命令。

此範例的最後一個部分會執行指令碼。 此輸出顯示它使用了為作業系統目前使用者設定的 UI 語言顯示正確的使用者訊息。

### 範例 5︰取代指令碼中的預設文字字串

這個範例示範如何使用 `Import-LocalizedData` 取代腳本的 DATA 區段中定義的預設文字字串。

```powershell
PS C:\> # In TestScript.ps1
$UserMessages = DATA

{    ConvertFrom-StringData @'

    # English strings

        Msg1 = "Enter a name."
        Msg2 = "Enter your employee ID."
        Msg3 = "Enter your building number."
'@
}

Import-LocalizedData -BindingVariable "UserMessages"
$UserMessages.Msg1...
```

在此範例中，TestScript.ps1 腳本的 DATA 區段包含一個 `ConvertFrom-StringData` 命令，此命令會將 DATA 區段的內容轉換成雜湊表，並儲存在變數的值中 `$UserMessages` 。

此腳本也包含一個 `Import-LocalizedData` 命令，此命令會從變數值所指定之子目錄中的 TestScript.psd1 檔案匯入已翻譯文字字串的雜湊表 `$PsUICulture` 。 如果命令找到檔案 `.psd1` ，則會將檔案中的已翻譯字串儲存在相同變數的值中 `$UserMessages` ，並覆寫資料區段邏輯所儲存的雜湊表。

第三個命令會顯示變數中的第一則訊息 `$UserMessages` 。

如果 `Import-LocalizedData` 命令找到語言的檔案 `.psd1` ，則 `$PsUICulture` 變數的值會包含已 `$UserMessages` 翻譯的文字字串。 如果命令因任何原因而失敗，此命令便會顯示指令碼之 DATA 區段中定義的預設文字字串。

### 範例 6︰如果找不到 UI 文化特性就抑制錯誤訊息

這個範例示範如何抑制當找 `Import-LocalizedData` 不到符合使用者 UI 文化特性的目錄，或 `.psd1` 在這些目錄中找不到腳本的檔案時，所出現的錯誤訊息。

```powershell
PS C:\> # In Day1.ps1

Import-LocalizedData -BindingVariable "Day"

# In Day2.ps1

Import-LocalizedData -BindingVariable "Day" -ErrorAction:SilentlyContinue

PS C:\> .\Day1.ps1
Import-LocalizedData : Cannot find PowerShell data file 'Day1.psd1' in directory 'C:\ps-test\fr-BE\' or any parent culture directories.
At C:\ps-test\Day1.ps1:17 char:21+ Import-LocalizedData <<<<  Day
Today is Tuesday

PS C:\> .\Day2.ps1
Today is Tuesday
```

您可以使用 **ErrorAction** 一般參數搭配 SilentlyContinue 值來抑制錯誤訊息。 當您已用預設語言或遞補語言提供使用者訊息，而不需要任何錯誤訊息時，這會特別有用。

此範例會比較兩個腳本， `Day1.ps1` 以及包含命令的 Day2.ps1 `Import-LocalizedData` 。 腳本完全相同，不同之處在于 Day2.ps1 會使用 **ErrorAction** 一般參數與值 `SilentlyContinue` 。

範例輸出會顯示當 UI 文化特性設定為 `fr-BE` ，且該 ui 文化特性沒有相符檔案或目錄時，執行這兩個腳本的結果。 `Day1.ps1` 顯示錯誤訊息和英文輸出。 `Day2.ps1` 只會顯示英文輸出。

## PARAMETERS

### -BaseDirectory

指定檔案所在的基底目錄 `.psd1` 。 預設值是指令碼所在的目錄。 `Import-LocalizedData``.psd1`在基底目錄的特定語言子目錄中搜尋腳本的檔案。

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

### -BindingVariable

指定做為文字字串匯入位置的變數。 輸入不含貨幣正負號 () 的變數名稱 `$` 。

在 Windows PowerShell 2.0 中，這是必要參數。 在 Windows PowerShell 3.0 中，這是選擇性參數。 如果您省略此參數，則會傳回 `Import-LocalizedData` 文字字串的雜湊表。 雜湊表會沿著管線向下傳遞或在命令列中顯示。

當使用 `Import-LocalizedData` 取代腳本的 data 區段中指定的預設文字字串時，請將 data 區段指派給變數，並在 **BindingVariable** 參數的值中輸入 data 區段變數的名稱。 然後，當將匯 `Import-LocalizedData` 入的內容儲存在 **BindingVariable** 中時，匯入的資料就會取代預設文字字串。 如果您未指定預設的文字字串，則可選取任何變數名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Variable

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FileName

指定要匯入 (資料檔案的名稱 `.psd1)` 。 請輸入檔案名稱。 您可以指定不含副檔名的檔案名 `.psd1` ，也可以指定檔案名（包括 `.psd1` 副檔名）。 資料檔案應該儲存為 Unicode 或 UTF-8。

當 **FileName** 未 `Import-LocalizedData` 在腳本中使用時，需要 FileName 參數。
否則，這個參數為選用參數，而預設值為指令碼的主檔名。 您可以使用這個參數來指示 `Import-LocalizedData` 搜尋不同的檔案 `.psd1` 。

例如，如果省略 **檔案名** 且腳本名稱為 FindFiles.ps1，則會 `Import-LocalizedData` 搜尋 FindFiles.psd1 資料檔案。

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

### -SupportedCommand

指定只產生資料的 Cmdlet 和函式。

請使用這個參數來包含您已經撰寫或測試的 Cmdlet 和函式。 如需詳細資訊，請參閱 [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UICulture

指定替代的 UI 文化特性。
預設值是自動變數的值 `$PsUICulture` 。
以格式輸入 UI 文化特性 `<language>-<region>` ，例如 `en-US` 、 `de-DE` 或 `ar-SA` 。

**UICulture** 參數的值會決定基底目錄中 (特定語言的子目錄，) 從中 `Import-LocalizedData` 取得腳本的檔案 `.psd1` 。

此 Cmdlet 會搜尋與 **UICulture** 參數的值或 `$PsUICulture` 自動變數（例如或）相同名稱的子目錄 `de-DE` `ar-SA` 。 如果找不到目錄，或目錄未包含腳本的檔案， `.psd1` 則會使用語言代碼名稱（例如 de 或 ar）來搜尋子目錄。 如果找不到子目錄或檔案 `.psd1` ，則命令會失敗，而且資料會以腳本中指定的預設語言顯示。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
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

### System.Collections.Hashtable

`Import-LocalizedData` 將雜湊表儲存在 **BindingVariable** 參數值所指定的變數中。

## 注意

- 在使用之前 `Import-LocalizedData` ，請將您的使用者訊息當地語系化。 在索引鍵/值組的雜湊表中，將每個地區設定 (UI 文化特性) 的訊息格式化，並將雜湊表儲存在與腳本同名的檔案中，並將其命名為 `.psd1` 副檔名。 在腳本目錄下為每個支援的 UI 文化特性建立一個目錄，然後將 `.psd1` 每個 ui 文化特性的檔案儲存在具有 ui 文化特性名稱的目錄中。

  例如，將您的使用者訊息針對 de-DE 地區設定翻譯成當地語言，然後在雜湊表中格式化。
  將雜湊表儲存在檔案中 `<ScriptName>.psd1` 。 然後在 `de-DE` 腳本目錄下建立子目錄，然後將德文檔案儲存 `<ScriptName\>.psd1` 在子目錄中 `de-DE` 。
  針對您支援的每個地區設定重複使用這個方法。

- `Import-LocalizedData` 針對腳本執行當地語系化使用者訊息的結構化搜尋。

  `Import-LocalizedData` 在腳本檔案所在的目錄中開始搜尋 (或 **BaseDirectory** 參數的值) 。 然後，它會在基底目錄中搜尋名稱與 `$PsUICulture` 變數值 (或 **UICulture** 參數值) 的子目錄，例如 `de-DE` 或 `ar-SA` 。 然後，它會在該子目錄中搜尋 `.psd1` 與腳本 (相同名稱的檔案，或) **FileName** 參數的值。

  如果找 `Import-LocalizedData` 不到具有 UI 文化特性名稱的子目錄，或子目錄未包含腳本的檔案 `.psd1` ，則會 `.psd1` 在具有語言代碼名稱（例如 de 或 ar）的子目錄中搜尋腳本的檔案。 如果找不到子目錄或檔案 `.psd1` ，則命令會失敗，資料會以腳本中的預設語言顯示，並且會顯示錯誤訊息，說明無法匯入資料。 若要抑制訊息並執行正常失敗程序，請使用 **ErrorAction** 一般參數搭配 SilentlyContinue 值。

  如果 `Import-LocalizedData` 找到子目錄和檔案 `.psd1` ，它就會將使用者訊息的雜湊表匯入到命令中 **BindingVariable** 參數的值。 然後，當您從變數中的雜湊表顯示訊息時，就會顯示已翻譯成當地語言的訊息。

  如需詳細資訊，請參閱 [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md)。

## 相關連結

[Write-Host](Write-Host.md)

[Import-PowerShellDataFile](Import-PowerShellDataFile.md)
