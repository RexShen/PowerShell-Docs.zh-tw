---
ms.openlocfilehash: f46b14e44c32ce31b4da1a14580fe03564bf9946
ms.sourcegitcommit: 0e18be0a2869beaa711ba3eca7a8a15514e5e962
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91899263"
---
# <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 開放原始碼管理辦法

此專案採用了 [Microsoft 開放原始碼管理辦法](https://opensource.microsoft.com/codeofconduct/)。 如需詳細資訊，請參閱[管理辦法常見問題集 (英文)](https://opensource.microsoft.com/codeofconduct/faq/)。如果有任何其他疑問或意見，請連絡 [opencode@microsoft.com](mailto:opencode@microsoft.com)。

[即時徽章]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[預備徽章]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a>組建狀態

|          即時分支          |           預備分支            |
| :---------------------------- | :---------------------------------- |
| [![即時徽章][]][即時徽章] | [![預備徽章][]][預備徽章] |

## <a name="powershell-documentation"></a>PowerShell 文件

歡迎使用 PowerShell-Docs 存放庫，此處為正式 PowerShell 文件的首頁。

## <a name="repository-structure"></a>存放庫結構

下列清單描述此存放庫中的主要資料夾。

- `.github` - 包含 GitHub 在此存放庫所使用的組態
- `.vscode` - 包含 Visual Studio Code (VS Code) 的組態設定與建議延伸模組
- `assets` - 包含本文件中連結的可下載檔案
- `reference` - 包含發佈至 [docs.microsoft.com]([https://docs.microsoft.com/powershell/scripting/) 的文件。 包含參考與概念內容。
  - `5.1` - 包含 Cmdlet 參考與 PowerShell 5.1 的相關主題
  - `6` - 包含 Cmdlet 參考與 PowerShell 6 的相關主題
  - `7.0` - 包含 Cmdlet 參考與 PowerShell 7.0 的相關主題
  - `7.1` - 包含 Cmdlet 參考與 PowerShell 7.1 的相關主題
  - `bread` - 包含用於軌跡瀏覽的目錄
  - `docs-conceptual` - 包含發佈至 Docs 網站的概念文章。 一般而言，資料夾結構會建立鏡像目錄 (TOC)。
  - `mapping` - 包含建置系統所使用的版本對應組態
  - `media` - 包含文件中所使用的影像檔案。 `docs-conceptual` 內容中包含媒體資料夾。 如需在文件中使用影像的詳細資訊，請參閱參與者指南。
  - `module` - 包含 [模組瀏覽器] 頁面的 Markdown 來源
- `tests` - 包含建置系統所使用的 Pester 測試
- `tools` - 包含建置系統所使用的其他工具

> 注意：(在編號資料夾中的) 參考內容是用來在 Docs 網站上建立網頁，以及 PowerShell 所使用的可更新說明。
> `docs-conceptual` 資料夾中的文章只會發佈到 Docs 網站。

## <a name="contributing"></a>參與

我們歡迎透過[提取要求](https://help.github.com/articles/using-pull-requests/)，投稿至存放庫的「暫存」分支中。
請注意，您必須先同意[貢獻授權合約](https://cla.microsoft.com/)，我們才會接受您的提取要求。 這只需要執行一次。

如需如何參與的詳細資訊，請閱讀我們的[參與者指南](https://aka.ms/PSDocsContributor)。 參與者指南包含有關如何參與文件、建議工具與樣式和格式需求的詳細資訊。 請使用「問題」和「提取要求」範本，以協助維持文件在不同版本之間的一致性。

## <a name="licenses"></a>授權

此專案有兩個授權檔案。 MIT 授權適用於此存放庫中包含的程式碼。 而 Creative Commons 授權則適用於文件。
