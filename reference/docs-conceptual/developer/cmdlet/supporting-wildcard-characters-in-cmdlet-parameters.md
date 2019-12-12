---
title: 在 Cmdlet 參數中支援萬用字元
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365307"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>在 Cmdlet 參數中支援萬用字元

通常，您必須設計 Cmdlet 來針對一組資源執行，而不是針對單一資源。 例如，Cmdlet 可能需要找出資料存放區中具有相同名稱或副檔名的所有檔案。 當您設計將針對一組資源執行的 Cmdlet 時，必須提供萬用字元支援。

> [!NOTE]
> 使用萬用字元有時稱為*通配*。

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>使用萬用字元的 Windows PowerShell Cmdlet

 許多 Windows PowerShell Cmdlet 都支援其參數值的萬用字元。 例如，幾乎每個具有 `Name` 或 `Path` 參數的 Cmdlet 都支援這些參數的萬用字元。 （雖然大部分具有 `Path` 參數的 Cmdlet 也具有不支援萬用字元的 `LiteralPath` 參數）。下列命令會顯示如何使用萬用字元來傳回目前會話中名稱包含 Get 動詞的所有 Cmdlet。

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a>支援的萬用字元

Windows PowerShell 支援下列萬用字元。

| 萬用字元 |                             描述                             |  範例   |     相符項目      | 不符合 |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | 符合零或多個字元，從指定的位置開始 | `a*`       | A、ag、Apple     |                |
| ?        | 符合指定位置的任何字元                     | `?n`       | 中的、       | 延續            |
| [ ]      | 符合字元範圍                                       | `[a-l]ook` | 著作、庫、尋找 | nook，花費了     |
| [ ]      | 符合指定的字元                                    | `[bn]ook`  | 書籍、nook       | 庫、外觀     |

當您設計支援萬用字元的 Cmdlet 時，允許組合萬用字元。 例如，下列命令會使用 `Get-ChildItem` Cmdlet 來取出 c:\Techdocs 資料夾中的所有 .txt 檔案，並以字母 "a" 到 "l."

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

先前的命令會使用範圍萬用字元 `[a-l]` 來指定檔案名的開頭應為 "a" 到 "l" 字元，並使用 `*` 萬用字元做為檔案名的第一個字母和 **.txt**副檔名之間任何字元的預留位置。

下列範例使用的範圍萬用字元模式會排除字母 "d"，但會包含 "a" 到 "f" 的所有其他字母。

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a>處理萬用字元模式中的常值字元

如果您指定的萬用字元模式包含不應該解釋為萬用字元的常值字元，請使用倒引號字元（`` ` ``）做為逸出字元。 當您指定常值字元 int PowerShell API 時，請使用單一倒引號。 當您在 PowerShell 命令提示字元中指定常值時，請使用兩個倒引號。

例如，下列模式包含兩個必須逐字採用的括弧。

當用於 PowerShell API 時，請使用：

- "John Smith \`[* ']"

從 PowerShell 命令提示字元使用時：

- "John Smith \`\`[*\`']"

此模式符合 "John Smith [Marketing]" 或 "John Smith [開發]"。 例如：

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a>Cmdlet 輸出和萬用字元

當 Cmdlet 參數支援萬用字元時，作業通常會產生陣列輸出。
有時候，支援陣列輸出並不合理，因為使用者可能只會使用單一專案。 例如，`Set-Location` Cmdlet 不支援陣列輸出，因為使用者只會設定一個位置。 在此情況下，Cmdlet 仍然支援萬用字元，但會強制解析成單一位置。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[WildcardPattern 類別](/dotnet/api/system.management.automation.wildcardpattern)
