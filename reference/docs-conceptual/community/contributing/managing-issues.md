---
title: 我們管理問題的方式
description: 此文章說明 PowerShell-Docs 小組管理提取要求的方式。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 018200f1a9384f1ea956c9b27a7605db21f2da9e
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692525"
---
# <a name="how-we-manage-issues"></a>我們管理問題的方式

此文章記錄我們管理 PowerShell-Docs 存放庫中問題的方式。 此文章是設計來輔助 PowerShell-Docs 小組成員的工作之用。 在此發佈的原因，是為了向我們的公共參與者提供流程上的透明度。

## <a name="sources-of-issues"></a>問題的來源

- 社群參與者
- 內部參與者
- 來自社交媒體通道的留言文字記錄
- 透過 Docs 意見反應表單提供的意見反應

## <a name="response-time-targets"></a>回應時間目標

- 分級：5 個工作天
- 修正或變更：無特定目標，盡最大努力

### <a name="labeling--milestones"></a>標記與里程碑

#### <a name="label-types"></a>標籤類型

|前置詞  | 描述                                                         |
|------- | --------------------------------------------------------------------|
|區域    | 用來指出問題正在討論 PowerShell 或文件的哪一個部分。<br>適合讓功能擁有者找出其功能的問題。|
|Pri     | 用來指出問題的優先順序。 值範圍為 0-4。        |
|問題   | 用來分類問題的意見反應類型                     |
|檢閱  | 用於需要由小組進一步審查的問題              |
|狀態  | 用來指出工作項目的狀態                        |
|等候 | 用來指出我們正在等候某個項目                   |

#### <a name="milestones"></a>里程碑

問題與 PR 應該要以適當的里程碑進行標記。 如果問題的目標不是特定版本，則不會使用任何里程碑。 針對尚未合併到 PowerShell 程式碼基底之變更的 Docs PR 問題，應該要指派給 [Future] \(未來\) 里程碑。 在合併程式碼變更之後，請將里程碑變更為適當的版本。

|    里程碑     |                    描述                     |
| ---------------- | -------------------------------------------------- |
| 6.x              | 與 PowerShell 6.0 至 6.2.x 相關的工作項目 |
| 7.0.0            | 與 PowerShell 7.0 相關的工作項目               |
| 7.1.0            | 與 PowerShell 7.1 相關的工作項目               |
| 未來           | 與未來的 PowerShell 版本相關的工作項目          |
| PSReadline-vNext | 與未來的 PSReadline 版本相關的工作項目          |

## <a name="triage-process"></a>分級程序

PowerShell Docs 小組每週會開會一次，以討論在上次會議之後新增的任何問題。 當已指派標籤，或是已指派擁有者時，便會將問題視為已分級。 我們鼓勵 PowerShell Docs 小組成員每日審查問題，並在新問題抵達時便對其進行分級。 如此一來，便可以視需要將每週的分級會議用來深入討論新問題。

### <a name="misplaced-product-feedback"></a>錯置的產品意見反應

- 為客戶輸入留言以指出其為產品意見反應，並提供適當意見反應管道的連結。
- 選擇性：將問題複製到適當的產品意見反應位置、新增已複製項目的連結，然後關閉該問題。 請勿將問題複製到 UserVoice。

  | DocSet    | 產品意見反應 URL                                           |
  | --------- | -------------------------------------------------------------- |
  | developer | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | dsc       | `https://windowsserver.uservoice.com/forums/301869-powershell` |
  | gallery   | `https://github.com/powershell/powershellgallery/issues/new`   |
  | jea       | `https://github.com/powershell/jea/issues/new`                 |
  | reference | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | wmf       | `https://windowsserver.uservoice.com/forums/301869-powershell` |

### <a name="support-requests"></a>支援要求

- 如果支援問題很簡單，請有禮貌地加以回答，然後關閉該問題。
- 如果問題比較複雜，或是提交者回覆更多問題，請將其重新導向到論壇和支援管道。 重新導向到論壇的建議文字：

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a>管理辦法違規

- 若有需要，請編輯問題以移除任何冒犯的內容。
- 輸入留言以指出該問題為垃圾訊息、關閉該問題，然後加以鎖定以防止進一步的留言。
- 發生此情況的每一個案例都應該在每週的分級會議中討論，以判斷是否需要執行進一步動作 (向 GitHub 或 Microsoft 法務部門回報)。
