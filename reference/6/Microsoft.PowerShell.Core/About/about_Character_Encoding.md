---
title: about_Character_Encoding
description: 描述 PowerShell 如何針對字串資料的輸入和輸出使用字元編碼。
ms.date: 10/21/2020
Locale: en-US
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_character_encoding?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
ms.openlocfilehash: cdefff5c29e880a2f8047aa2254b6b471906757e
ms.sourcegitcommit: df80c558e9a4b89c9798f084bd04012ece15155c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "93208851"
---
# <a name="about_character_encoding"></a>about_Character_Encoding

## <a name="short-description"></a>簡短描述
描述 PowerShell 如何針對字串資料的輸入和輸出使用字元編碼。

## <a name="long-description"></a>完整描述

Unicode 是全球字元編碼標準。 系統會專門針對字元和字串操作使用 Unicode。 如需 Unicode 所有方面的詳細說明，請參閱 [Unicode 標準](https://www.unicode.org/standard/standard.html)。

Windows 支援 Unicode 和傳統字元集。 傳統字元集（例如 Windows 字碼頁）使用8位值或8位值的組合來代表特定語言或地理區域設定中使用的字元。

PowerShell 預設會使用 Unicode 字元集。 不過，有數個 Cmdlet 具有可指定不同字元集編碼的 **編碼** 參數。 此參數可讓您選擇所需的字元編碼方式，以與其他系統和應用程式交互操作。

下列 Cmdlet 具有 **Encoding** 參數：

- Microsoft.PowerShell.Management
  - Add-Content
  - Get-Content
  - Set-Content
- Microsoft.PowerShell.Utility
  - Export-Clixml
  - Export-Csv
  - Export-PSSession
  - Format-Hex
  - Import-Csv
  - Out-File
  - Select-String
  - Send-MailMessage

## <a name="the-byte-order-mark"></a>位元組順序標記

位元組順序標記 (BOM) 是在檔案或文字資料流程的前幾個位元組中的 _unicode_ 簽章，指出用於資料的 unicode 編碼方式。 如需詳細資訊，請參閱維琪百科中的 [位元組順序標記](https://wikipedia.org/wiki/Byte_order_mark) 文章。

在 Windows PowerShell 中，除了以外的任何 Unicode 編碼 `UTF7` 一律會建立 BOM。 `utf8NoBOM`所有文字輸出的 PowerShell Core 預設為。

為了獲得最佳的整體相容性，請避免在 UTF-8 檔案中使用 Bom。 適用于 Windows 平臺的 unix 平臺和 Unix 遺產公用程式也不支援 Bom。

同樣地， `UTF7` 應該避免編碼。 UTF-7 不是標準的 Unicode 編碼方式，而且在所有版本的 PowerShell 中都不會使用 BOM 來撰寫。

在類似 Unix 的平臺上建立 PowerShell 腳本，或在 Windows 上使用跨平臺編輯器（例如 Visual Studio Code），會產生使用編碼的檔案 `UTF8NoBOM` 。 這些檔案在 PowerShell Core 上可正常運作，但如果檔案包含非 Ascii 字元，則可能會在 Windows PowerShell 中中斷。

如果您需要在腳本中使用非 Ascii 字元，請將它們儲存為 UTF-8 與 BOM。 如果沒有 BOM，Windows PowerShell 會將腳本誤譯為舊版 "ANSI" 字碼頁中的編碼方式。 相反地，具有 UTF-8 BOM 的檔案在類似 Unix 的平臺上可能會有問題。 許多 Unix 工具，例如 `cat` 、 `sed` 、 `awk` 和某些編輯器，例如 `gedit` 不知道如何處理 BOM。

## <a name="character-encoding-in-windows-powershell"></a>Windows PowerShell 中的字元編碼

在 PowerShell 5.1 中， **編碼** 參數支援下列值：

- `Ascii` 使用 Ascii (7 位) 字元集。
- `BigEndianUnicode` 以位元組由大到小的順序使用 UTF-16。
- `BigEndianUTF32` 使用具有位元組由大到小的 32 UTF-8 順序。
- `Byte` 將一組字元編碼成位元組序列。
- `Default` 使用與系統的作用中字碼頁對應的編碼， (通常是 ANSI) 。
- `Oem` 使用對應至系統目前 OEM 字碼頁的編碼方式。
- `String`：與 `Unicode` 相同。
- `Unicode` 使用 UTF-16 和位元組由小到小的位元組順序。
- `Unknown`：與 `Unicode` 相同。
- `UTF32` 以位元組由小到大的位元組順序使用 UTF-32。
- `UTF7` 使用 UTF-7。
- `UTF8` 使用 UTF-8 (搭配 BOM) 。

一般而言，Windows PowerShell 預設會使用 Unicode [utf-16le](https://wikipedia.org/wiki/UTF-16) 編碼。 不過，Windows PowerShell 中的 Cmdlet 所使用的預設編碼方式不一致。

> [!NOTE]
> 除了以外，使用任何 Unicode 編碼 `UTF7` 一律會建立 BOM。

針對將輸出寫入檔案的 Cmdlet：

- `Out-File` 以及重新導向運算子 `>` 和 `>>` 建立 utf-16le，這一點與 `Set-Content` 和不同 `Add-Content` 。

- `New-ModuleManifest``Export-CliXml`此外也會建立 utf-16le 檔案。

- 當目標檔案為空白或不存在時， `Set-Content` 請 `Add-Content` 使用 `Default` 編碼。 `Default` 這是使用中系統地區設定的 ANSI 舊版字碼頁所指定的編碼方式。

- `Export-Csv` 建立檔案 `Ascii` ，但使用 **附加** 參數時使用不同的編碼 (請參閱下面的) 。

- `Export-PSSession` 預設會建立具有 BOM 的 UTF-8 檔案。

- `New-Item -Type File -Value` 建立不使用 BOM 的 UTF-8 檔案。

- `Send-MailMessage` 預設會使用 `Default` 編碼。

- `Start-Transcript``Utf8`使用 BOM 建立檔案。 使用 **Append** 參數時，編碼可能會不同 (請參閱下面的) 。

針對附加至現有檔案的命令：

- `Out-File -Append` 而重新導向 `>>` 運算子不會嘗試比對現有目標檔案內容的編碼。 相反地，除非使用 **encoding** 參數，否則會使用預設的編碼方式。 附加內容時，您必須使用原始檔編碼。

- 如果沒有明確的 **編碼** 參數，則 `Add-Content` 會偵測現有的編碼，並自動將它套用至新的內容。 如果現有的內容沒有 BOM， `Default` 則會使用 ANSI 編碼。 `Add-Content`在 PowerShell Core (v6 和更新) 版本中的行為相同，除非預設編碼為 `Utf8` 。

- `Export-Csv -Append` 當目標檔案包含 BOM 時，符合現有的編碼。 如果 BOM 不存在，就會使用 `Utf8` 編碼。

- `Start-Transcript -Append` 符合包含 BOM 之檔案的現有編碼。 當 BOM 不存在時，它會預設為 `Ascii` 編碼。 當文字記錄中的資料包含多位元組字元時，此編碼可能會導致資料遺失或字元損毀。

針對在缺少 BOM 時讀取字串資料的 Cmdlet：

- `Get-Content` 和 `Import-PowerShellDataFile` 使用 `Default` ANSI 編碼。 當 PowerShell 引擎從檔案讀取原始程式碼時，也會使用 ANSI。

- `Import-Csv`、 `Import-CliXml` 和 `Select-String` 假設 `Utf8` 沒有 BOM。

## <a name="character-encoding-in-powershell-core"></a>PowerShell Core 中的字元編碼

在 PowerShell Core (v6 和更新版本的) 中， **Encoding** 參數支援下列值：

- `ascii`：使用 ASCII (7 位) 字元集的編碼方式。
- `bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。
- `oem`：針對 MS-DOS 和主控台程式使用預設編碼。
- `unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。
- `utf7`：以 UTF-7 格式編碼。
- `utf8`：以 UTF-8 格式編碼 (沒有 BOM) 。
- `utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式
- `utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) 
- `utf32`：以 UTF-32 格式編碼。

`utf8NoBOM`針對所有輸出 PowerShell Core 預設為。

從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。 如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage)。

## <a name="changing-the-default-encoding"></a>變更預設編碼

PowerShell 有兩個可以用來變更預設編碼行為的預設變數。

- `$PSDefaultParameterValues`
- `$OutputEncoding`

如需詳細資訊，請參閱 [about_Preference_Variables](about_Preference_Variables.md)。

從 PowerShell 5.1 開始，重新導向操作員 (`>` ， `>>`) 呼叫 `Out-File` Cmdlet。 因此，您可以使用喜好設定變數來設定預設的編碼方式， `$PSDefaultParameterValues` 如下列範例所示：

```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
```

使用下列語句來變更所有具有 **encoding** 參數之 Cmdlet 的預設編碼方式。

```powershell
$PSDefaultParameterValues['*:Encoding'] = 'utf8'
```

> [!IMPORTANT]
> 將此命令放入 PowerShell 設定檔中，會讓喜好設定成為會話全域設定，此設定會影響未明確指定編碼的所有命令和腳本。
>
> 同樣地，您應該將這類命令包含在您想要以相同方式行為的腳本或模組中。 使用這些命令可確保 Cmdlet 的行為方式，甚至是在其他使用者執行時、在不同的電腦上，或在不同版本的 PowerShell 中執行。

自動變數 `$OutputEncoding` 會影響 PowerShell 用來與外部程式通訊的編碼方式。 它不會影響輸出重新導向運算子和 PowerShell Cmdlet 用來儲存至檔案的編碼方式。

## <a name="see-also"></a>另請參閱

- [.NET 中的字元編碼簡介](/dotnet/standard/base-types/character-encoding-introduction)
- [字碼頁-Win32 應用程式](/windows/win32/intl/code-pages)
- [Unicode 標準](https://www.unicode.org/standard/standard.html)
- [編碼。字碼頁](/dotnet/api/system.text.encoding.codepage)
- [UTF-16LE](https://wikipedia.org/wiki/UTF-16)
- [位元組順序標記](https://wikipedia.org/wiki/Byte_order_mark)
- [about_Preference_Variables](about_Preference_Variables.md)
