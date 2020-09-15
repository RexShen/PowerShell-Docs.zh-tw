---
title: 對 PowerShell 文件做出貢獻
description: 此文章是如何以 PowerShell 文件參與者身分開始貢獻的概觀。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3ea08c3acf4a31cbb7262aac57bf28b75388275d
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86158151"
---
# <a name="contributing-to-powershell-documentation"></a>對 PowerShell 文件做出貢獻

感謝您支援 PowerShell！

《參與者指南》是一系列文章，說明我們在 Microsoft 建立文件時所用的工具與程式。 某些指南涵蓋了所有發行至 [docs.microsoft.com][docs] 之文件集的通用資訊。 某些指南是關於我們如何撰寫 PowerShell 文件的專屬內容。

您可以在我們的集中式[參與者指南][contribute]中找到一般文章。 這裡提供 PowerShell 專屬指南。

## <a name="ways-to-contribute"></a>參與方法

做出貢獻的方式有兩種： 這兩個貢獻對我們而言很重要。

- [提出問題][file-an-issue]，以協助我們找出文件中的問題與缺口。 有時候問題不好解決，需要進行更多調查及研究。 問題程序可讓我們對問題進行交談，並開發出滿意的解決方式。

- 提交新內容或現有文章的變更是更複雜的程序。 下列資訊概述用於將內容提交至文件的工具、程序與標準。

## <a name="prepare-to-make-a-contribution"></a>準備做出貢獻

參與文件內容需要 GitHub 帳戶。 使用下列檢查清單來取得工具，並了解我們用來做出貢獻的程序。

1. [註冊 GitHub](/contribute/get-started-setup-github)
1. [安裝 Git 與 Markdown 工具](/contribute/get-started-setup-tools)
1. [安裝文件編寫套件](/contribute/how-to-write-docs-auth-pack)
1. [安裝 Posh-Git][posh-git] - 非必要，僅為建議
1. [設定本機 Git 存放庫](/contribute/get-started-setup-local)
1. [檢閱 Git 與 GitHub 基本概念](/contribute/git-github-fundamentals)

## <a name="get-started-writing-docs"></a>開始撰寫文件

有兩種方式可以參與文件的變更：

1. [對現有文件進行快速編輯](/contribute/#quick-edits-to-existing-documents)
   - 微幅修正、修正錯字或微幅新增
1. [文件的完整 GitHub 工作流程](/contribute/how-to-write-workflows-major)
   - 大幅變更、多個版本、新增或變更影像，或參與新文章編寫

此外，請參閱集中式《參與者指南》中的[編寫基本知識](/contribute/style-quick-start)一節。 另一個絕佳的資源是 [Microsoft 寫作風格指南][style-guide]。 《Microsoft 寫作風格指南》的目標是協助編輯者、技術作者、開發人員、行銷人員以及 IT 中的其他人撰寫更好的內容。

您對此公用存放庫中之文件與程式碼範例所做的微幅修正或釐清，將受到 docs.microsoft.com [ 使用規定][terms-of-use]的約束。

當您要進行大幅變更時，請使用完整的 GitHub 工作流程。 如果您不是 Microsoft 的員工，大幅變更會在提取要求中產生註解，要求您提交線上[貢獻授權合約 (CLA)][cla]。 您必須先完成線上表單，我們才會審核或接受您的提取要求。

## <a name="code-of-conduct"></a>管理辦法

所有發佈到 docs.microsoft.com 的存放庫都採用 [Microsoft 開放原始碼管理辦法](https://opensource.microsoft.com/codeofconduct/) \(英文\) 或 [.NET Foundation 管理辦法](https://dotnetfoundation.org/code-of-conduct) \(英文\)。 如需詳細資訊，請參閱[管理辦法常見問題集](https://opensource.microsoft.com/codeofconduct/faq/) \(英文\)。

## <a name="next-steps"></a>後續步驟

下列文章涵蓋 PowerShell 文件的專屬資訊。 當與集中式《參與者指南》中的指導方針重疊時，我們會說明那些規則與 PowerShell 內容有何差異。

請檢閱下列文件：

- [如何提出問題](file-an-issue.md)
- [開始編寫文件](get-started-writing.md)
- [提交提取要求](pull-requests.md)
- [PowerShell-Docs 樣式指南](powershell-style-guide.md)
- [編輯 Cmdlet 參考](editing-cmdlet-ref.md)

其他資源

- [編輯檢查清單](editorial-checklist.md)
- [我們管理問題的方式](managing-issues.md)
- [我們管理提取要求的方式](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: /powershell
[style-guide]: /style-guide/welcome/
[terms-of-use]: /legal/termsofuse
