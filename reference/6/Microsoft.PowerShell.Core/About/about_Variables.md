---
description: 描述變數如何儲存可在 PowerShell 中使用的值。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: e301d323fff8f8519c60f8916a019acea324a589
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206812"
---
# <a name="about-variables"></a>關於變數

## <a name="short-description"></a>簡短描述

描述變數如何儲存可在 PowerShell 中使用的值。

## <a name="long-description"></a>完整描述

您可以將所有類型的值儲存在 PowerShell 變數中。 例如，儲存命令的結果，並儲存命令和運算式中使用的元素，例如名稱、路徑、設定和值。

變數是儲存值的記憶體單位。 在 PowerShell 中，變數會以文字字串表示（以貨幣符號 (`$`) ，例如 `$a` 、或） `$process` `$my_var` 。

變數名稱不區分大小寫，而且可以包含空格和特殊字元。 但是，包含特殊字元和空格的變數名稱不容易使用，而且應該避免使用。 如需詳細資訊，請參閱 [包含特殊字元的變數名稱](#variable-names-that-include-special-characters)。

PowerShell 中有數種不同類型的變數。

- 使用者建立的變數：使用者建立的變數由使用者建立和維護。 根據預設，您在 PowerShell 命令列建立的變數只會在 PowerShell 視窗開啟時存在。 當 PowerShell 視窗關閉時，會刪除變數。 若要儲存變數，請將它新增至您的 PowerShell 設定檔。 您也可以在具有全域、腳本或區域範圍的腳本中建立變數。

- 自動變數：自動變數會儲存 PowerShell 的狀態。 這些變數是由 PowerShell 所建立，而 PowerShell 則會視需要變更其值，以維持其精確度。 使用者無法變更這些變數的值。 例如，變數會 `$PSHOME` 儲存 PowerShell 安裝目錄的路徑。

  如需詳細資訊、清單和自動變數的描述，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)。

- 喜好設定變數：喜好設定變數會儲存 PowerShell 的使用者喜好設定。 這些變數是由 PowerShell 所建立，並以預設值填入。 使用者可以變更這些變數的值。 例如，變數會 `$MaximumHistoryCount` 決定會話歷程記錄中的最大專案數。

  如需詳細資訊、清單和喜好設定變數的描述，請參閱 [about_Preference_Variables](about_Preference_Variables.md)。

## <a name="working-with-variables"></a>使用變數

若要建立新的變數，請使用指派語句將值指派給變數。 在使用變數之前，您不需要宣告該變數。 所有變數的預設值為 `$null` 。

若要取得 PowerShell 會話中所有變數的清單，請輸入 `Get-Variable` 。 變數名稱顯示時，不會有之前的貨幣 (`$` 用來參考變數) 號。

例如：

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

變數很適合用來儲存命令的結果。

例如：

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

若要顯示變數的值，請輸入變數名稱，前面加上貨幣符號 (`$`) 。

例如：

```powershell
$MyVariable
```

```Output
1
2
3
```

```powershell
$Today
```

```Output
Tuesday, September 3, 2019 09:46:46
```

若要變更變數的值，請將新值指派給變數。

下列範例會顯示變數的值 `$MyVariable` 、變更變數的值，然後顯示新的值。

```powershell
$MyVariable = 1, 2, 3
$MyVariable
```

```Output
1
2
3
```

```powershell
$MyVariable = "The green cat."
$MyVariable
```

```Output
The green cat.
```

若要刪除變數的值，請使用 `Clear-Variable` Cmdlet 或將值變更為 `$null` 。

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

若要刪除變數，請使用 [移除變數](xref:Microsoft.PowerShell.Utility.Remove-Variable) 或 [移除專案](xref:Microsoft.PowerShell.Management.Remove-Item)。

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

## <a name="types-of-variables"></a>變數類型

您可以將任何類型的物件儲存在變數中，包括整數、字串、陣列和雜湊表。 以及代表進程、服務、事件記錄和電腦的物件。

PowerShell 變數是鬆散類型，這表示它們不受限於特定類型的物件。 單一變數甚至可以同時包含不同類型之物件的集合或陣列。

變數的資料類型是由變數值的 .NET 類型所決定。 若要查看變數的物件類型，請使用 [ [取得成員](xref:Microsoft.PowerShell.Utility.Get-Member)]。

例如：

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

您可以使用類型屬性和轉換標記法，以確定變數只能包含可轉換成該類型的特定物件類型或物件。 如果您嘗試指派另一種類型的值，則 PowerShell 會嘗試將值轉換為其類型。 如果無法轉換類型，指派語句將會失敗。

若要使用轉型標記法，請在指派語句的左邊輸入名稱（以括弧括住），然後再 (變數名稱) 。 下列範例會建立只能包含 `$number` 整數的變數、只能包含字串的 `$words` 變數，以及只能 `$dates` 包含 **DateTime** 物件的變數。

```powershell
[int]$number = 8
$number = "12345"  # The string is converted to an integer.
$number = "Hello"
```

```Output
Cannot convert value "Hello" to type "System.Int32". Error: "Input string was
 not in a correct format."
At line:1 char:1
+ $number = "Hello"
+ ~~~~~~~~~~~~~~~~~
+ CategoryInfo          : MetadataError: (:) [],
    ArgumentTransformationMetadataException
+ FullyQualifiedErrorId : RuntimeException
```

```powershell
[string]$words = "Hello"
$words = 2       # The integer is converted to a string.
$words += 10     # The plus (+) sign concatenates the strings.
$words
```

```Output
210
```

```powershell
[datetime] $dates = "09/12/91"  # The string is converted to a DateTime object.
$dates
```

```Output
Thursday, September 12, 1991 00:00:00
```

```powershell
$dates = 10    # The integer is converted to a DateTime object.
$dates
```

```Output
Monday, January 1, 0001 00:00:00
```

## <a name="using-variables-in-commands-and-expressions"></a>在命令和運算式中使用變數

若要在命令或運算式中使用變數，請輸入變數名稱，前面加上貨幣 (`$`) 號。

如果變數名稱和貨幣符號未以引號括住，或以雙引號括住 (`"`) 標記，則會在命令或運算式中使用變數的值。

如果變數名稱和貨幣符號以單引號括住 (`'`) 標記，就會在運算式中使用變數名稱。

如需在 PowerShell 中使用引號的詳細資訊，請參閱 [about_Quoting_Rules](about_Quoting_Rules.md)。

此範例會取得變數的值 `$PROFILE` ，這是 powershell 主控台中 powershell 使用者設定檔的路徑。

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

在此範例中，會顯示兩個命令，可在 **notepad.exe** 中開啟 PowerShell 設定檔。 使用雙引號 () 標記的範例會 `"` 使用變數的值。

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

下列範例會使用單引號 (`'`) 標記，將變數視為常值文字。

```powershell
'$PROFILE'
```

```Output
$PROFILE
```

```powershell
'Use the $PROFILE variable.'
```

```Output
Use the $PROFILE variable.
```

## <a name="variable-names-that-include-special-characters"></a>包含特殊字元的變數名稱

變數名稱的開頭為貨幣 (`$`) 符號，而且可以包含英數位元和特殊字元。 變數名稱長度只受限於可用的記憶體。

最佳做法是變數名稱只包含英數位元和底線 (`_`) 字元。 包含空格和其他特殊字元的變數名稱不容易使用，而且應該避免使用。

英數位元變數名稱可以包含下列字元：

- 這些類別的 Unicode 字元： **Lu** 、 **Ll** 、 **Lt** 、 **Lm** 、 **Lo** 或 **Nd** 。
- 底線 (`_`) 字元。
- 問號 (`?`) 字元。

下列清單包含 Unicode 分類描述。 如需詳細資訊，請參閱 [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory)。

- **Lu** -UppercaseLetter
- **Ll** -LowercaseLetter
- **Lt** -TitlecaseLetter
- **Lm** -ModifierLetter
- **Lo** -OtherLetter
- **Nd** -DecimalDigitNumber

若要建立或顯示包含空格或特殊字元的變數名稱，請用大括弧括住變數名稱， (`{}`) 個字元。
大括弧會直接將變數名稱的字元解讀為常值。

特殊字元變數名稱可以包含下列字元：

- 任何 Unicode 字元，但有下列例外狀況：
  - 右大括弧 (`}`) 字元 (U + 007D) 。
  - 倒引號 (`` ` ``) 字元 (U + 0060) 。 倒引號是用來將 Unicode 字元換成常值，因此會被視為常值。

PowerShell 有包含英數位元 `$$` `$?` `$^` `$_` 和特殊字元的保留變數，例如、、和。 如需詳細資訊，請參閱 [about_Automatic_Variables](about_automatic_variables.md)。

例如，下列命令會建立名為的變數 `save-items` 。 需要大括弧 (`{}`) ，因為變數名稱包含連字號 (`-`) 特殊字元。

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

下列命令會取得環境變數所表示之目錄中的子專案 `ProgramFiles(x86)` 。

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

若要參考包含大括弧的變數名稱，請以大括弧括住變數名稱，並使用倒引號字元來將大括弧換用。 例如，若要建立名為 type 的變數 `this{value}is` ：

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a>變數和範圍

根據預設，變數僅適用于其建立所在的範圍。

例如，您在函式中建立的變數只能在函式內使用。 您在腳本中建立的變數只能在腳本中使用。 如果您是以點為來源的腳本，則會將變數加入至目前的範圍。 如需詳細資訊，請參閱 [about_Scopes](about_Scopes.md)。

您可以使用範圍修飾符來變更變數的預設範圍。 下列運算式會建立名為的變數 `Computers` 。 變數有全域範圍，即使是在腳本或函式中建立也一樣。

```powershell
$Global:Computers = "Server01"
```

針對任何執行的腳本或命令，您必須 `Using` 要有範圍修飾詞，才能從呼叫會話範圍內嵌變數值，讓會話外的程式碼可以存取它們。

如需詳細資訊，請參閱 [about_Remote_Variables](about_Remote_Variables.md)。

## <a name="saving-variables"></a>儲存變數

您建立的變數只能在您建立變數的會話中使用。 當您關閉會話時，它們就會遺失。

若要在每個您啟動的 PowerShell 會話中建立變數，請將變數新增至您的 PowerShell 設定檔。

例如，若要變更 `$VerbosePreference` 每個 powershell 會話中的變數值，請將下列命令新增至您的 powershell 設定檔。

```powershell
$VerbosePreference = "Continue"
```

您可以 `$PROFILE` 在文字編輯器中開啟檔案（例如 **notepad.exe** ），將此命令新增至您的 PowerShell 設定檔。 如需 PowerShell 設定檔的詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。

## <a name="the-variable-drive"></a>Variable：磁片磁碟機

PowerShell 變數提供者所建立的 `Variable:` 磁片磁碟機會像檔案系統磁片磁碟機一樣，但會包含會話中的變數及其值。

若要變更為 `Variable:` 磁片磁碟機，請使用下列命令：

```powershell
Set-Location Variable:
```

若要列出磁片磁碟機中的專案和變數 `Variable:` ，請使用 `Get-Item` 或 `Get-ChildItem` Cmdlet。

```powershell
Get-ChildItem Variable:
```

若要取得特定變數的值，請使用檔案系統標記法來指定磁片磁碟機的名稱和變數的名稱。 例如，若要取得 `$PSCulture` 自動變數，請使用下列命令。

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

若要顯示 `Variable:` 磁片磁碟機和 PowerShell 變數提供者的詳細資訊，請輸入：

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a>具有提供者路徑的變數語法

您可以在提供者路徑前面加上貨幣 (`$`) 號，並存取任何實 [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) 介面的提供者的內容。

下列內建 PowerShell 提供者支援此標記法：

- [about_Environment_Provider](about_Environment_Provider.md)
- [about_Variable_Provider](about_Variable_Provider.md)
- [about_Function_Provider](about_Function_Provider.md)
- [about_Alias_Provider](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a>變數 Cmdlet

PowerShell 包含一組設計來管理變數的 Cmdlet。

若要列出 Cmdlet，請輸入：

```powershell
Get-Command -Noun Variable
```

若要取得特定 Cmdlet 的說明，請輸入：

```powershell
Get-Help <cmdlet-name>
```

| 指令程式名稱       | 描述                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | 刪除變數的值。           |
| `Get-Variable`    | 取得目前主控台中的變數。 |
| `New-Variable`    | 建立新變數。                    |
| `Remove-Variable` | 刪除變數和它的值。          |
| `Set-Variable`    | 變更變數的值。           |

## <a name="see-also"></a>另請參閱

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Scopes](about_Scopes.md)

[about_Remote_Variables](about_Remote_Variables.md)
