---
ms.date: 08/26/2019
ms.topic: reference
title: 在 Cmdlet 參數中支援萬用字元
description: 在 Cmdlet 參數中支援萬用字元
ms.openlocfilehash: 06693c62cd2613050bdeb9d6b12ad6e9597a9894
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646395"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>在 Cmdlet 參數中支援萬用字元

通常，您必須設計 Cmdlet 來針對一組資源執行，而不是針對單一資源。 例如，Cmdlet 可能需要找出資料存放區中具有相同名稱或副檔名的所有檔案。 當您設計會針對一組資源執行的 Cmdlet 時，您必須提供萬用字元的支援。

> [!NOTE]
> 使用萬用字元有時也稱為 *通配*。

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Windows PowerShell 使用萬用字元的 Cmdlet

 許多 Windows PowerShell Cmdlet 都支援其參數值的萬用字元。 例如，幾乎每個具有或參數的 Cmdlet 都 `Name` `Path` 支援這些參數的萬用字元。  (雖然大部分具有參數的 Cmdlet `Path` 也都有不 `LiteralPath` 支援萬用字元的參數。 ) 下列命令顯示如何使用萬用字元來傳回目前會話中名稱包含 Get 動詞的所有 Cmdlet。

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a>支援的萬用字元

Windows PowerShell 支援下列萬用字元。

| 萬用字元 |                             說明                             |  範例   |     相符項      | 不符合 |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | 符合零或多個字元（從指定位置開始） | `a*`       | A、ag、Apple     |                |
| ?        | 符合指定位置的任何字元                     | `?n`       | A、in、on       | 跑            |
| [ ]      | 符合字元範圍                                       | `[a-l]ook` | 著作、庫、尋找 | nook，花費了     |
| [ ]      | 符合指定的字元                                    | `[bn]ook`  | 書籍，nook       | 庫、外觀     |

當您設計支援萬用字元的 Cmdlet 時，允許萬用字元的組合。 例如，下列命令 `Get-ChildItem` 會使用 Cmdlet 取出 c:\Techdocs 資料夾中的所有 .txt 檔案，且開頭為字母 "a" 至 "l"。

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

上述命令會使用範圍萬用字元 `[a-l]` 來指定檔案名的開頭應為 "a" 到 "l" 字元，並使用 `*` 萬用字元作為檔案名的第一個字母和 **.txt** 副檔名之間的任何字元的預留位置。

下列範例使用的範圍萬用字元模式排除字母 "d"，但包含從 "a" 到 "f" 的所有其他字母。

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a>處理萬用字元模式中的常值字元

如果您指定的萬用字元模式包含不應解釋為萬用字元的常值字元，請使用倒引號字元 (`` ` ``) 作為 escape 字元。 當您指定 PowerShell API 的常值字元時，請使用單一倒引號。 當您在 PowerShell 命令提示字元中指定常值字元時，請使用兩個倒引號。

例如，下列模式包含兩個必須真正採用的括弧。

使用於 PowerShell API 時，請使用：

- "John Smith \` [* ']"

從 PowerShell 命令提示字元使用時：

- "John Smith \` \` [* \` ']"

此模式符合「John Smith [Marketing]」或「John Smith [開發]」。 例如：

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a>Cmdlet 輸出和萬用字元

當 Cmdlet 參數支援萬用字元時，此作業通常會產生陣列輸出。
有時候，因為使用者可能只會使用單一專案，所以不會支援陣列輸出。 例如，Cmdlet 不 `Set-Location` 支援陣列輸出，因為使用者只會設定單一位置。 在此情況下，Cmdlet 仍然支援萬用字元，但它會強制解析成單一位置。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[WildcardPattern 類別](/dotnet/api/system.management.automation.wildcardpattern)
