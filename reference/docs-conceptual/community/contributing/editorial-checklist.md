---
title: 編輯檢查清單
description: 這是編輯 PowerShell 文件之規則的摘要清單。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 511e0c323e1a3256039e819d06f32f6e1ac42767
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060333"
---
# <a name="editors-checklist"></a>編輯的檢查清單

這是在撰寫新文章或更新現有文章時應套用之規則的摘要。 請參閱《參與者指南》中的其他文章，以取得這些規則的詳細說明與範例。

## <a name="metadata"></a>中繼資料

- `ms.date`：格式必須為 **MM/DD/YYYY**
  - 在做出重大或事實更新時，請變更日期
    - 重新組織文章
    - 修正事實錯誤
    - 加入新資訊
  - 如果更新內容無足輕重，請勿變更日期
    - 修正錯字與格式
- `title`：43-59 個字元的唯一字串 (包括空格)
  - 請勿包含網站識別碼 (會自動產生)
  - 使用句首大寫，也就是指將第一個文字及任何專有名詞以大寫字母輸入
- `description`:115-145 個字元 (包括空格)，此摘要會顯示於搜尋結果中

## <a name="formatting"></a>格式化

- 以內嵌方式顯示在段落內的倒引號語法元素
  - Cmdlet 名稱 `Verb-Noun`
  - 變數 `$counter`
  - 語法範例 `Verb-Noun -Parameter`
  - 檔案路徑 `C:\Program Files\PowerShell`、`/usr/bin/pwsh`
  - 文件中不應該可點選的 URL
- 針對屬性名稱、參數值、參數名稱、類別名稱、模組名稱、實體名稱、物件或類型名稱使用粗體
  - 粗體是用於語意標記，不是用來強調
  - 粗體：使用星號 `**`
- 斜體：使用底線 `_`
  - 僅用來強調，不是用於語意標記
- 於第 100 欄使用分行符號 (針對 **about_Topics** 則為第 80 欄)
- 勿使用硬式 Tab，僅使用空格
- 在行上勿使用尾端空格

### <a name="headers"></a>headers

- H1 為第一；每篇文章僅能有一個 H1
- 僅使用 [ATX 標頭](https://github.github.com/gfm/#atx-headings) \(英文\)
- 針對所有標頭使用句首大寫
- 勿略過層級 (在沒有 H2 的情況下便不能有 H3)
- 最大深度為 H3 或 H4
- 在前後都使用空白行
- PlatyPS 會在其結構描述中強制使用特定標頭，請不要加入或移除標頭

### <a name="code-blocks"></a>程式碼區塊

- 在前後都使用空白行
- 使用已標記的程式碼柵欄：**powershell**、**Output** 或其他適當的語言識別碼
- 未標記的柵欄：語法區塊或其他殼層
- 除了您不想讓讀者使用 [Copy]  \(複製\) 按鈕的簡單範例以外，請將 [Output]  \(輸出\) 置於個別的程式碼區塊
- 請參閱[支援的語言](/contribute/code-in-docs#supported-languages)清單

### <a name="lists"></a>清單

- 已適當縮排
- 在第一個項目之前與最後一個項目之後使用空白行
- 項目符號：請使用連字號 (`-`) 而非星號 (`*`)，因為星號太容易與強調混淆
- 針對編號清單，所有數字都是 "1."

## <a name="terminology"></a>詞彙

- PowerShell 與Windows PowerShell 與PowerShell Core
- 請參閱[產品術語](powershell-style-guide.md#product-terminology)

## <a name="cmdlet-reference-examples"></a>Cmdlet 參考範例

- 至少必須有一個 Cmdlet 參考的範例
- 範例應該包含剛好足以示範使用方式的程式碼
- PowerShell 語法
  - 使用 Cmdlet 與參數的全名，請勿使用別名
  - 當命令列太長時，請針對參數使用展開
  - 避免使用行接續符號倒引號，僅在必要時使用
- 移除或簡化 PowerShell 提示字元 (`PS>`)，除非是範例所需
- Cmdlet 參考範例必須遵循下列 PlatyPS 結構描述

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- 勿將段落置於程式碼區塊之間。 所有描述性內容都必須位於程式碼區塊之前或之後。

## <a name="linking-to-other-documents"></a>連結到其他文件

- 連結到 DocSet 之外，或是在 Cmdlet 參考與概念之間連結
  - 在連結到 docs.microsoft.com 時，請使用相對 URL (移除 `https://docs.microsoft.com/en-us`)
  - 勿在 Microsoft 內容的 URL 中包含地區設定 (例如， 從 URL 中移除 `/en-us`)
  - 針對外部網站的所有 URL 都應該使用 HTTPS，除非目標網站不適用
- 在 DocSet 之內
  - 連結到檔案路徑 (例如 `../folder/file.md`)
  - 所有檔案路徑都使用正斜線 (`/`) 字元
- 影像連結應該要有不重複的替代文字
