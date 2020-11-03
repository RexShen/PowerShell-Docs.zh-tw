---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-localizeddata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-LocalizedData
ms.openlocfilehash: 552e37f8bef096ec7d072d41186f8919bc58f630
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203775"
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

**Import-LocalizedData** Cmdlet 會從名稱與為作業系統目前使用者設定之 UI 語言相符的子目錄動態抓取字串。
它是專為讓指令碼以目前使用者選取的 UI 語言顯示使用者訊息而設計。

**Import-LocalizedData** 會從指令碼目錄之語言特定子目錄中的 .psd1 檔案匯入資料，並將其儲存在命令中指定的區域變數中。
這個 Cmdlet 會根據 $PSUICulture 自動變數的值來選取子目錄和檔案。
在指令碼中使用區域變數來顯示使用者訊息時，訊息會以使用者的 UI 語言顯示。

您可以使用 **Import-LocalizedData** 的參數來指定替代的 UI 文化特性、路徑及檔案名稱、新增支援的命令，以及抑制找不到 .psd1 檔案時所顯示的錯誤訊息。

**Import-LocalizedData** Cmdlet 支援 Windows PowerShell 2.0 中所導入的指令碼國際化計畫。
這個計畫的目標是要藉由讓指令碼能輕鬆以目前使用者的 UI 語言顯示使用者訊息，為世界各地的使用者提供更好的服務。
如需有關此計畫及 .psd1 檔案格式的詳細資訊，請參閱 about_Script_Internationalization。

## 範例

### 範例 1︰匯入文字字串

```
PS C:\> Import-LocalizedData -BindingVariable "Messages"
```

這個命令會將文字字串匯入到 $Messages 變數中。
它會使用所有其他 Cmdlet 參數的預設值。

如果此命令包含在 C:\Test 目錄下的 Archives.ps1 指令碼中，並且 $PsUICulture 自動變數的值是 zh-CN， **Import-LocalizedData** 就會將 C:\test\zh-CN 目錄下的 Archives.psd1 檔案匯入到 $Messages 變數中。

### 範例 2︰匯入當地語系化資料字串

```
PS C:\> Import-LocalizedData -FileName "Test.psd1" -UICulture "en-US"

Name                           Value
----                           -----
Msg3                           "Use $_ to represent the object that is being processed."
Msg2                           "This command requires the credentials of a member of the Administrators group on the...
Msg1                           "The Name parameter is missing from the command."
```

這個命令是在命令列中執行；不是在指令碼中執行。
它會從 Test.psd1 檔案取得當地語系化資料字串，並在命令列中顯示這些字串。
由於此命令不是用於指令碼中，因此必須使用 *FileName* 參數。
此命令使用 *UICulture* 參數來指定 en-US 文化特性。

**Import-LocalizedData** 會傳回一個包含當地語系化資料字串的雜湊表。

### 範例 3︰匯入 UI 文化特性字串

```
PS C:\> Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

此命令會將文字字串匯入指令碼的 $MsgTbl 變數中。

它使用 *UICulture* 參數來指示 Cmdlet 從 C:\Data\Localized 之 ar-SA 子目錄中的 Simple.psd1 檔案匯入資料。

### 範例 4︰將當地語系化資料匯入指令碼

```
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

# In PowerShell

PS C:\> .\Test.ps1

This command requires the credentials of a member of the Administrators group on the computer.
```

這個範例示範如何在簡單的指令碼中使用當地語系化資料。

此範例的第一個部分示範 Test.psd1 檔案的內容。
它包含一個 ConvertFrom-StringData 命令，此命令會將一系列具名的文字字串轉換成雜湊表。
Test.psd1 檔案位於包含指令碼之 C:\Test 目錄的 en-US 子目錄中。

此範例的第二個部分示範 Test.ps1 指令碼的內容。
它包含一個 **Import-LocalizedData** 命令，此命令會將 matching .psd1 檔案中的資料匯入 $Messages 變數中，以及包含一個 Write-Host 命令，此命令會將 $Messages 變數中的其中一個訊息寫入主機程式中。

此範例的最後一個部分會執行指令碼。
此輸出顯示它使用了為作業系統目前使用者設定的 UI 語言顯示正確的使用者訊息。

### 範例 5︰取代指令碼中的預設文字字串

```
PS C:\> # In TestScript.ps1
$UserMessages = DATA

{    ConvertFrom-StringData @'

    # English strings

        Msg1 = "Enter a name."
        Msg2 = "Enter your employee ID."
        Msg3 = "Enter your building number."
'@ }
Import-LocalizedData -BindingVariable "UserMessages"
$UserMessages.Msg1...
```

這個範例示範如何使用 **Import-LocalizedData** 來取代指令碼的 DATA 區段中定義的預設文字字串。

在這個範例中，TestScript.ps1 指令碼的 DATA 區段包含 ConvertFrom-StringData 命令，此命令會將 DATA 區段的內容轉換成雜湊表，並儲存在 $UserMessages 變數的值中。

此指令碼也包含 **Import-LocalizedData** 命令，此命令會從 $PsUICulture 變數的值所指定之子目錄中的 TestScript.psd1 檔案匯入已翻譯之文字字串的雜湊表。
如果此命令找到 .psd1 檔案，它就會將來自檔案的已翻譯字串儲存在相同 $UserMessages 變數的值中，覆寫 DATA 區段邏輯所儲存的雜湊表。

第三個命令會顯示 $UserMessages 變數中的第一個訊息。

如果 **Import-LocalizedData** 命令找到 $PsUICulture 語言的 .psd1 檔案，$UserMessages 變數的值便會包含已翻譯的文字字串。
如果命令因任何原因而失敗，此命令便會顯示指令碼之 DATA 區段中定義的預設文字字串。

### 範例 6︰如果找不到 UI 文化特性就抑制錯誤訊息

```
PS C:\> # In Day1.ps1

Import-LocalizedData -BindingVariable "Day"

# In Day2.ps1

Import-LocalizedData -BindingVariable "Day" -ErrorAction:SilentlyContinue

PS C:\> .\Day1.ps1
Import-LocalizedData : Cannot find PowerShell data file 'Day1.psd1' in directory 'C:\ps-test\fr-BE\' or any parent culture directories.
At C:\ps-test\Day1.ps1:17 char:21+ Import-LocalizedData <<<<  Day
Today is Tuesday PS C:\> .\Day2.ps1
Today is Tuesday
```

這個範例示範如何抑制當 **Import-LocalizedData** 找不到與使用者之 UI 文化特性相符的目錄時所顯示的錯誤訊息，或在這些目錄中找不到指令碼的 .psd1 檔案時所顯示的錯誤訊息。

您可以使用 *ErrorAction* 一般參數搭配 SilentlyContinue 值來抑制錯誤訊息。
當您已用預設語言或遞補語言提供使用者訊息，而不需要任何錯誤訊息時，這會特別有用。

這個範例會比較兩個包含 **Import-LocalizedData** 命令的指令碼：Day1.ps1 和 Day2.ps1。
除了 Day2 使用了 *ErrorAction* 一般參數搭配 SilentlyContinue 值之外，這些指令碼完全相同。

此範例輸出顯示當 UI 文化特性設定為 fr-BE 而沒有與此 UI 文化特性相符的檔案或目錄時，這兩個指令碼的執行結果。
Day1.ps1 會顯示錯誤訊息和英文輸出。
Day2.ps1 只會顯示英文輸出。

## PARAMETERS

### -BaseDirectory

指定 .psd1 檔案所在位置的基礎目錄。
預設值是指令碼所在的目錄。
**Import-LocalizedData** 會在基礎目錄之語言特定子目錄中搜尋指令碼的 .psd1 檔案。

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

指定做為文字字串匯入位置的變數。
請輸入沒有貨幣符號 ($) 的變數名稱。

在 Windows PowerShell 2.0 中，這是必要參數。
在 Windows PowerShell 3.0 中，這是選擇性參數。
如果省略這個參數， **Import-LocalizedData** 就會傳回文字字串的雜湊表。
雜湊表會沿著管線向下傳遞或在命令列中顯示。

使用 **Import-LocalizedData** 來取代指令碼的 DATA 區段中指定的預設文字字串時，請將 DATA 區段指派給變數，並在 *BindingVariable* 參數的值中輸入 DATA 區段變數的名稱。
然後，當 **Import-LocalizedData** 將匯入的內容儲存在 *BindingVariable* 中時，匯入的資料就會取代預設文字字串。
如果您未指定預設的文字字串，則可選取任何變數名稱。

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

指定要匯入之資料檔 (.psd1) 的名稱。
請輸入檔案名稱。
您可以指定不包含 .psd1 副檔名的檔案名稱，也可以指定包含 .psd1 副檔名的檔案名稱。

指令碼中未使用 *Import-LocalizedData* 時，必須使用 **FileName** 參數。
否則，這個參數為選用參數，而預設值為指令碼的主檔名。
您可以使用這個參數來指示 **Import-LocalizedData** 搜尋不同的 .psd1 檔案。

例如，如果省略 *FileName* ，而指令碼名稱為 FindFiles.ps1， **Import-LocalizedData** 便會搜尋 FindFiles.psd1 資料檔。

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

請使用這個參數來包含您已經撰寫或測試的 Cmdlet 和函式。
如需詳細資訊，請參閱 about_Script_Internationalization。

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
預設為 $PsUICulture 自動變數的值。
輸入格式的 UI 文化特性 \<language\> - \<region\> ，例如 en-us、de 或 ar-SA。

*UICulture* 參數的值會決定供 **Import-LocalizedData** 取得指令碼之 .psd1 檔案的語言特定子目錄 (在基底目錄內)。

這個 Cmdlet 會搜尋名稱與 *UICulture* 參數或 $PsUICulture 自動變數的值 (例如 de-DE 或 ar-SA) 相同的子目錄。
如果找不到目錄，或目錄未包含指令碼的 .psd1 檔案，它就會搜尋具有語言代碼之名稱 (例如 de 或 ar) 的子目錄。
如果找不到子目錄或 .psd1 檔案，則命令會失敗，資料會以指令碼中指定的預設語言顯示。

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

**Import-LocalizedData** 會將雜湊表儲存在 **BindingVariable** 參數的值所指定的變數中。

## 注意

* 使用 **Import-LocalizedData** 之前，請先將您的使用者訊息翻譯成當地語言。 在機碼/值組的雜湊表中，將每個地區設定 (UI 文化特性) 的訊息格式化，並將此雜湊表儲存在與指令碼同名且副檔名為 .psd1 的檔案中。 在指令碼目錄下為每個支援的 UI 文化特性建立一個目錄，然後將每個 UI 文化特性的.psd1 檔案以 UI 文化特性名稱儲存在目錄中。

  例如，將您的使用者訊息針對 de-DE 地區設定翻譯成當地語言，然後在雜湊表中格式化。
將雜湊表儲存在 \<ScriptName\>.psd1 檔案中。
接著，在指令碼目錄下建立 de-DE 子目錄，然後將 de-DE \<ScriptName\>.psd1 檔案儲存在 de-DE 子目錄中。
針對您支援的每個地區設定重複使用這個方法。

* **Import-LocalizedData** 會執行指令碼之當地語系化使用者訊息的結構化搜尋。

  **Import-LocalizedData** 會在指令檔所在的目錄 (或 *BaseDirectory* 參數的值) 中開始搜尋。
然後，它會在基礎目錄內搜尋名稱與 $PsUICulture 變數的值 (或 *UICulture* 參數的值) (例如 de-DE 或 ar-SA) 相同的子目錄。
接著，它會在該子目錄中搜尋名稱與指令碼 (或 *FileName* 參數的值) 相同的 .psd1 檔案。

  如果 **Import-LocalizedData** 找不到具有 UI 文化特性名稱的子目錄，或子目錄未包含指令碼的 .psd1 檔案，它就會在具有語言代碼名稱 (例如 de 或 ar) 的子目錄中搜尋指令碼的 .psd1 檔案。
如果找不到子目錄或 .psd1 檔案，則命令會失敗，資料會以指令碼中的預設語言顯示，並且會顯示一則錯誤訊息，說明無法匯入資料。
若要抑制訊息並執行正常失敗程序，請使用 *ErrorAction* 一般參數搭配 SilentlyContinue 值。

  如果 **Import-LocalizedData** 找到子目錄和 .psd1 檔案，它就會將使用者訊息的雜湊表匯入到命令中 *BindingVariable* 參數的值中。
然後，當您從變數中的雜湊表顯示訊息時，就會顯示已翻譯成當地語言的訊息。

  如需詳細資訊，請參閱 [about_Script_Internationalization](../Microsoft.PowerShell.Core/about/about_Script_Internationalization.md)。

## 相關連結

[Write-Host](Write-Host.md)

[Import-PowerShellDataFile](Import-PowerShellDataFile.md)
