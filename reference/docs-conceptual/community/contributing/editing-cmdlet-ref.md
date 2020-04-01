---
title: 編輯參考文章
description: 此文章說明編輯 PowerShell 文件中的 Cmdlet 參考與「關於」主題的特定需求。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3aed1c14429310c57681397d4877a3a6f48400fd
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500967"
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

`About_*` 檔案現已由 [Pandoc][] 處理，而非 PlatyPS。 `About_*` 檔案的格式設定方式，會使其能在 PowerShell 的所有版本與發行工具上取得最佳相容性。

基本格式設定指導方針：

- 將行限制為 80 個字元
- 程式碼區塊與表格會限制為 76 個字元，因為 Pandoc 會在轉換為純文字時，對其進行四個空格的縮排
- 表格必須能容納在 76 個字元之內
  - 手動將資料格的內容跨多行進行換行
  - 在每一行的開頭和結尾使用 `|` 字元
  - 在 [about_Comparison_Operators][about-example] 中查看實用範例
- 使用 Pandoc 特殊字元 `\`、`$` 與 `<`
  - 在標頭內，這些字元必須透過使用前置 `\` 字元，或是以倒引號 (`` ` ``) 括住來逸出
  - 在段落內，這些字元應該要置於程式碼範圍中。 例如：

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

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
