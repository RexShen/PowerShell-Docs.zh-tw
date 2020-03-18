---
title: 開始對 PowerShell 文件做出貢獻
description: 此文章是如何以 PowerShell 文件參與者身分開始貢獻的概觀。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 95eb2c3157a99fcb6560914da8464022e1b64fad
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060303"
---
# <a name="get-started-contributing-to-powershell-documentation"></a>開始對 PowerShell 文件做出貢獻

此文章是如何以 PowerShell 文件參與者身分開始貢獻的概觀。

## <a name="powershell-docs-structure"></a>PowerShell-Docs 結構

[PowerShell-Docs 存放庫][psdocs]分為兩個內容群組。 Git 分支是用來管理文件的發佈方式與時間。

### <a name="reference-content"></a>參考內容

參考內容是 PowerShell 所隨附 Cmdlet 的 PowerShell Cmdlet 參考。
[參考][ref]是收集在版本資料夾中 (5.1、6、7.0 與 7.1)。 此內容只包含 PowerShell 所隨附模組的 Cmdlet 參考。 此內容也用來建立 `Get-Help` Cmdlet 所顯示的說明資訊。

> [!NOTE]
> 參考內容的目錄 (TOC) 是由發行系統自動產生的。 您不需要更新 TOC。

### <a name="conceptual-content"></a>概念性內容

概念性文件包含下列內容：

- 版本資訊
- 安裝指示
- 範例指令碼與操作說明文章
- DSC 文件
- SDK 文件

[概念性文件][conceptual]不是依版本組織的。 所有文章都為每個 PowerShell 版本顯示。 我們正致力於建立版本特定文章。 當我們的文件中有該功能時，此指南將會以適當的資訊更新。

> [!NOTE]
> 每當加入、移除或重新命名概念性文章時，都必須更新目錄並包含在提取要求中。

## <a name="using-git-branches"></a>使用 Git 分支

PowerShell-Docs 的預設分支是 `staging` 分支。 在工作分支中所做的變更，會在發佈之前合併到 `staging` 分支中。 `staging` 分支大約每週會合併到 `live` 分支中一次。 `live` 分支包含發佈至 docs.microsoft.com 的內容。 一律不應該在 `live` 分支中直接進行變更。

如果您提交的文件變更僅適用於未發行版本的 PowerShell，請檢查是否有該版本的發行分支。 所有適用於特定、未來版本的變更都應該以發行分支為目標。 發行分支具有下列名稱模式：`release-<version>`。

開始進行任何變更之前，請先在您的 PowerShell-Docs 存放庫本機複本中建立工作分支。 這應該是[您派生的複製][fork]。 請務必先同步處理本機存放庫，再建立您的工作分支。 您應該從已更新為最新版的 `staging` 或 `release` 分支複本建立工作分支。

請遵循中心《參與者指南》中[進行變更][making-changes]小節的程序，來進行您想要的變更。

### <a name="creating-new-articles"></a>建立新文章

您必須針對想要貢獻的任何新文件建立 GitHub 問題。 檢查問題是否已經存在，以確保不會重複。 已指派給某人的問題會視為「進行中」。 如果您想要對問題進行共同作業，請連絡獲指派該問題的人員。

與 PowerShell [RFC 程序][rfc]類似，在撰寫內容之前先建立問題，可確保您不會花了很多時間與心力，結果內容被 PowerShell-Docs 小組拒絕。 這也允許我們向您詢問內容的範圍，以及其在 PowerShell 文件中適合的位置。

### <a name="updating-existing-articles"></a>更新現有文章

在適用的情況下，Cmdlet 參考文章會在所有 PowerShell 版本之間重複。 當回報有關 Cmdlet 參考或 `About_` 文章的問題時，您必須指定哪些版本受該問題影響。 GitHub 中的問題範本包含版本的檢查清單。 使用核取方塊來指定內容的哪些版本受影響。 當您針對影響內容多個版本的問題提交文章變更時，您必須將適用的變更套用至檔案的每個版本。

## <a name="next-steps"></a>後續步驟

請參閱[提交提取要求](pull-requests.md)

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md