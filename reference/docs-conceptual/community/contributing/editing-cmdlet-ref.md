---
title: 編輯參考文章
description: 此文章說明編輯 PowerShell 文件中的 Cmdlet 參考與「關於」主題的特定需求。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: e135f6cc81ba7537a535a08421e1ca9b2b2af573
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624766"
---
# <a name="editing-reference-articles"></a>編輯參考文章

Cmdlet 參考文章具有特定的結構。 此結構是由 [PlatyPS][] 所定義。
PlatyPS 會以 Markdown 產生 PowerShell 模組的 Cmdlet 說明。 在編輯 Markdown 檔案之後，會使用 PlatyPS 來建立 `Get-Help` Cmdlet 所使用的 MAML 說明檔案。

PlatyPS 為會寫入程式碼中，適用於 Cmdlet 參考的硬式編碼結構描述。 [platyPS.schema.md][] 文件會嘗試描述此結構。 結構描述違規會導致建置錯誤；您必須先將其修正，我們才能接受您的貢獻。

## <a name="general-guidelines"></a>一般方針

- 勿移除任何標頭結構。 PlatyPS 會預期特定的標頭集合。
- [Input type]  \(輸入類型\) 與 [Output type]  \(輸出類型\) 標頭必須具有類型。 如果 Cmdlet 不接受輸入或是傳回值，請使用 `None` 值。
- 僅於 [Examples](#structuring-examples) 小節允許使用具柵欄的程式碼區塊。
- 內嵌程式碼範圍可用於任何段落。

## <a name="formatting-about_-files"></a>設定 About_ 檔案格式

`About_*` 檔案是以 Markdown 撰寫，但以純文字檔案格式送交。 我們使用 [Pandoc][] 將 Markdown 轉換為純文字。 `About_*` 檔案的格式設定方式，會使其能在 PowerShell 的所有版本與發行工具上取得最佳相容性。

基本格式設定指導方針：

- 將行限制為 80 個字元。 Pandoc 會縮排某些 Markdown 區塊，因此必須調整那些區塊。
  - 程式碼區塊限制為 76 個字元
  - 表格限制為 76 個字元
  - 區塊引述 (與警示) 限制為 78 個字元

- 使用 Pandoc 的特殊中繼字元 `\`、`$` 與 `<`
  - 在標題內，這些字元必須透過使用前置 `\` 字元，或是使用倒引號 (`` ` ``) 來以程式碼範圍括住
  - 在段落內，這些字元應該要置於程式碼範圍中。 例如：

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- 表格必須能容納在 76 個字元之內
  - 手動將資料格的內容跨多行進行換行
  - 在每一行的開頭和結尾使用 `|` 字元
  - 下列範例說明如何正確地建立一個表格，其中包含包裝在資料格內多行的資訊。

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > 76 欄限制僅適用於 `About_*` 主題。 您可以在概念或 Cmdlet 參考文章中使用寬欄。

## <a name="structuring-examples"></a>結構範例

在 PlatyPS 結構描述中，**EXAMPLES** 標頭為 H2 標頭，且每個範例都是 H3 標頭。

在範例內，結構描述不允許使用段落來區分程式碼區塊。 支援的結構描述為：

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

為每個範例加上編號，然後加入簡短的標題。

例如：

### <a name="example-1-get-cmdlets-functions-and-aliases"></a>範例 1：取得 Cmdlet、函式與別名

此命令會取得電腦上安裝的 PowerShell Cmdlet、函式與別名。

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a>範例 2：取得目前工作階段中的命令

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a>後續步驟

[編輯檢查清單](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
