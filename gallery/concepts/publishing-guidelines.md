---
ms.date: 06/12/2017
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
description: 發行者的指導方針
title: PowerShell 資源庫發行指導方針與最佳做法
ms.openlocfilehash: aa7ac4eeb96e8234bbac820fea6cab2b37f688d0
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215374"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShell 資源庫發行指導方針與最佳做法

此文章說明一些建議的步驟，Microsoft 小組會使用這些步驟，根據「PowerShell 資源庫」處理資訊清單資料的方式，以大量「PowerShell 資源庫」使用者的意見反應，確保發行至「PowerShell 資源庫」的套件會受到廣泛採用，並為使用者提供相當高的價值。 凡是依循這些指導方針發行的套件，將較可能獲得安裝、信任及吸引更多使用者。

以下是一些指導方針，說明哪些是良好「PowerShell 資源庫」套件的構成要素、哪些選擇性「資訊清單」設定最重要、如何利用初始檢閱者和 [Powershell 指令碼分析程式](https://aka.ms/psscriptanalyzer)的意見反應來改善您的程式碼，以及如何為模組、文件、測試和範例設定版本來指定如何使用您已共用的項目。 此文件大部分皆依循發行[高品質 DSC 資源模組](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md) \(英文\) 的指導方針。

如需了解將套件發行至「PowerShell 資源」的技巧，請參閱[建立和發行套件](/powershell/gallery/how-to/publishing-packages/publishing-a-package)。

歡迎您提供有關這些指導方針的意見反應。
如果您確實有意見反應，請在我們的 [GitHub 文件存放庫](https://github.com/powershell/powershell-docs/issues) \(英文\) 中提出問題。

## <a name="best-practices-for-publishing-packages"></a>發行套件的最佳做法

下列最佳做法是「PowerShell 資源庫」項目使用者表示重要的最佳做法，列出順序是依照提名優先順序。 遵循這些準則的套件更有可能被其他人下載和採用。

- 使用 PSScriptAnalyzer
- 包含文件和範例
- 針對意見反應做出回應
- 提供模組而不是指令碼
- 提供專案網站的連結
- 使用相容的 PSEdition 和平台標記您的套件
- 在模組中隨附測試
- 包含和/或連結至授權條款
- 簽署您的程式碼
- 依循 [SemVer](https://semver.org/) 指導方針來進行版本設定
- 使用「常用的 PowerShell 資源庫」標記中記載的常用標記
- 使用本機存放庫來測試發行
- 使用 PowerShellGet 發佈

下面各節將簡要說明這上述每一個做法。

## <a name="use-psscriptanalyzer"></a>使用 PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) 是一個可在 PowerShell 程式碼上運作的免費靜態程式碼分析工具。 **PSScriptAnalyzer** 會識別出 PowerShell 程式碼中最常見的問題，且通常會提供如何修正該問題的建議。 此工具相當容易使用，並且會將問題分類為「錯誤」(代表嚴重，必須加以解決)、「警告」(代表需要檢閱且應該加以解決)，以及「資訊」(代表值得查看以了解最佳做法)。 所有發行至「PowerShell 資源庫」的套件都會由 **PSScriptAnalyzer** 掃描，如有任何錯誤，就會回報給擁有者且必須加以解決。

最佳做法是搭配 `-Recurse` 和 `-Severity` 警告執行 `Invoke-ScriptAnalyzer`。

請檢閱結果並確保：

- 所有「錯誤」在您的文件中都已獲得更正或處理。
- 所有「警告」都已獲得檢閱和適當的處理。

強烈建議從「PowerShell 資源庫」取得套件的使用者執行 **PSScriptAnalyzer** 並評估所有「錯誤」和「警告」。 使用者如果看到 **PSScriptAnalyzer** 回報某個錯誤，非常可能會連絡套件擁有者。 如果您的套件有充分的理由必須保留標示為錯誤的程式碼，請將該資訊新增到您的文件中，以避免需要多次回答相同的問題。

## <a name="include-documentation-and-examples"></a>包含文件和範例

文件和範例是確保使用者能夠利用任何共用程式碼的最佳方式。

文件是可包含在發行至「PowerShell 資源庫」之套件中的最有用說明資料。
使用者通常會略過沒有文件的套件，因為可以選擇閱讀程式碼來了解該套件是什麼及如何使用它。 MSDN 中提供數篇有關如何隨 PowerShell 套件提供文件的文章，包括：

- 如需提供說明的指導方針，請參閱[如何撰寫 Cmdlet 說明](https://go.microsoft.com/fwlink/?LinkID=123415) \(英文\)。
- 建立 Cmdlet 說明，這是適用於所有 PowerShell 指令碼、函式或 Cmdlet 的最佳做法。
  如需如何建立 Cmdlet 說明的資訊，請從[如何撰寫 Cmdlet 說明](https://go.microsoft.com/fwlink/?LinkID=123415) \(英文\) 開始著手。
  若要在指令碼中新增說明，請參閱[關於註解型說明](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) \(英文\)。
- 許多模組也包含文字格式的文件，例如 MarkDown 檔案。 當 GitHub 中有大量使用 Markdown 格式的專案網站時，這會特別有用。 最佳做法是使用[具備 GitHub 特色的 Markdown](https://help.github.com/categories/writing-on-github/) \(英文\)。

範例會向使用者說明應該如何使用套件。 許多開發人員會說他們在看文件之前會先看範例來了解如何使用某些項目。 最佳類型的範例會說明基本用法，再加上模擬的實際使用案例，而且程式碼會有詳細的註解。 發行至「PowerShell 資源庫」之模組的範例應該位於模組根目錄底下的 [Examples] 資料夾中。

您可以在 `Examples\RegistryResource` 資料夾底下的 [PSDscResource 模組](https://www.powershellgallery.com/packages/PSDscResources)中找到理想的範例模式。 一共有四個範例使用案例，其中每個檔案最上方都有一段簡短的描述，記載了所要示範的內容。

## <a name="manage-dependencies"></a>管理相依性

請務必在模組資訊清單中指定您模組相依的模組。 如此一來，使用者就不需要擔心安裝您相依之模組的適當版本。 若要指定相依模組，您應該使用模組資訊清單中的必要模組欄位。 這會在匯入您的模組之前，先將任何列出的模組都載入至全域環境，除非它們已經載入。 例如，有些模組可能已經由其他模組載入。 您也可以使用 **RequiredVersion** 欄位 (而非 **ModuleVersion** 欄位) 來指定要載入的特定版本。 使用 **ModuleVersion** 時，系統會載入所指定最小版本的最新可用版本。 當不使用 **RequiredVersion** 欄位指定特定版本時，請務必監視所需模組的版本更新。 特別重要的是，請留意可能影響您模組使用者體驗的任何中斷性變更。

```powershell
Example: RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})

Example: RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})
```

## <a name="respond-to-feedback"></a>針對意見反應做出回應

正確地對意見反應做出回應的套件擁有者在社群中會享有高評價。 提供具建設性意見反應的使用者是重要的回應對象，因為他們對套件的興趣大到足以嘗試協助改進該套件。

「PowerShell 資源庫」中提供兩種意見反應方法：

- 連絡擁有者：這可讓使用者傳送電子郵件給套件擁有者。 如果您是套件擁有者，請務必隨時注意與「PowerShell 資源庫」套件搭配使用的電子郵件地址，並針對提出的問題進行回應。 此方法有一個缺點，就是只有使用者和擁有者可以看到溝通內容，因此擁有者可能必須回答相同的問題許多次。
- 註解：套件頁面底部有一個 [註解]  欄位。 此系統的優點是其他使用者可以看到評論和回應，減少了必須回答任何單一問題的次數。 如果您是套件擁有者，強烈建議您「關注」針對每個套件提出的評論。 如需相關做法的詳細資料，請參閱[透過社群媒體或評論來提供意見反應](../how-to/working-with-packages/social-media-feedback.md) \(英文\)。

以具建設性的方式回應意見反應的擁有者會受到社群激賞。 使用報表中的商機來要求詳細資訊。 如有需要，請提供因應措施，或識別更新是否能修正問題。

如果從這些溝通管道中的任何一個管道觀察到不當的行為，請使用「PowerShell 資源庫」的 [檢舉不當使用] 功能來連絡「資源庫系統管理員」。

## <a name="modules-versus-scripts"></a>模組與指令碼之比較

與其他使用者共用指令碼是相當好的做法，並可為其他使用者提供如何解決他們問題的範例。 問題在於「PowerShell 資源庫」中的指令碼是單一檔案，並無個別的文件、範例及測試。

「PowerShell 模組」具有資料夾結構，可允許將多個資料夾和檔案包含在套件中。 模組結構可將我們列為最佳做法的下列其他套件都納入其中：Cmdlet 說明、文件、範例與測試。 最大的缺點在於模組內的指令碼必須公開並當作函式使用。 如需有關如何建立模組的資訊，請參閱[撰寫 Windows PowerShell 模組](/powershell/developer/module/writing-a-windows-powershell-module) \(英文\)。

在一些情況下，指令碼可為使用者提供較佳的體驗，特別是搭配 DSC 設定時。 DSC 設定的最佳做法是以指令碼的形式發行設定，此指令碼會隨附一個包含文件、範例及測試的模組。 此指令碼會使用 `RequiredModules = @(Name of the Module)` 列出隨附的模組。 此方法可以與任何指令碼搭配使用。

依循其他最佳做法的獨立指令碼可以為其他使用者提供實際的價值。 將指令碼發行至「PowerShell 資源庫」時，強烈建議您提供註解型文件和「專案網站」的連結。

## <a name="provide-a-link-to-a-project-site"></a>提供專案網站的連結

「專案網站」是發行者可以與其「PowerShell 資源庫」套件使用者直接互動的地方。 使用者會偏好使用提供此連結的套件，因為這可讓他們更輕鬆取得套件的相關資訊。 「PowerShell 資源庫」中的許多套件都是在 GitHub 中開發的，其他套件則是由具有專用網站空間的組織提供的。 上述每一個都可以視為專案網站。

若要新增連結，請依下列方式將 ProjectURI 包含在資訊清單的 PSData 區段中：

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

當已提供 ProjectURI 時，「PowerShell 資源庫」就會在套件頁面的左邊包含「專案網站」的連結。

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>使用相容的 PSEdition 和平台標記您的套件

使用下列標籤向使用者示範能與其環境搭配並運作良好的套件：

- PSEdition_Desktop：與 Windows PowerShell 相容的套件
- PSEdition_Core：與 PowerShell Core 相容的套件
- Windows：與 Windows 作業系統相容的套件
- Linux：與 Linux 作業系統相容的套件
- MacOS：與 Mac 作業系統相容的套件

透過在相容平台標記您的套件，該套件就會包含在搜尋結果左側窗格的資源庫搜尋篩選中。 如果將套件裝載在 GitHub 上，標記套件時也可以利用我們的 [PowerShell 資源庫相容性防護](https://img.shields.io/powershellgallery/p/:packageName.svg)
![相容性防護](https://img.shields.io/powershellgallery/p/CosmosDB.svg)。

## <a name="include-tests"></a>包含測試

包含具有開放原始碼的測試對使用者而言相當重要，因為這可以向使用者提供您所驗證項目的相關保證，並提供與您程式碼運作情況相關的資訊。 這也可以讓使用者確保當修改您的程式碼以配合其環境時，不致於破壞您的原始功能。

強烈建議您撰寫測試來利用 Pester 測試架構，這是專為 PowerShell 設計的測試架構。 除了可以從 [GitHub](https://github.com/Pester/Pester)、[PowerShell 資源庫](https://www.powershellgallery.com/packages/Pester/)取得 Pester 之外，Windows 10、Windows Server 2016、WMF 5.0 及 WMF 5.1 中也隨附 Pester。

[GitHub 中的 Pester 專案網站](https://github.com/Pester/Pester)包含有關撰寫 Pester 測試的詳細文件，從入門到最佳做法一應俱全。

[高品質資源模組文件](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md) \(英文\) 中指出了測試目標涵蓋範圍，建議涵蓋 70% 的單元測試程式碼。

## <a name="include-andor-link-to-license-terms"></a>包含和/或連結至授權條款

所有發行至「PowerShell 資源庫」的套件都必須指定授權條款，或是受到[使用規定](https://www.powershellgallery.com/policies/Terms) \(英文\) 底下「附錄 A」  中所包含的授權約束。指定不同授權的最佳方法是在 **PSData** 中使用 **LicenseURI** 來提供授權的連結。 如需詳細資訊，請參閱[套件資訊清單與資源庫 UI](package-manifest-affecting-ui.md)。

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>簽署您的程式碼

程式碼簽署可以向使用者提供最高層級的保證，不僅可確保套件發行者安全可靠，也可確保他們取得的程式碼複本與發行者發行的完全相同。 若要廣泛深入了解程式碼簽署，請參閱[程式碼簽署簡介](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85)) \(英文\)。
PowerShell 透過兩種主要的方法來支援程式碼簽署驗證：

- 簽署指令碼檔
- 類別目錄簽署模組

簽署 PowerShell 檔案是一個廣為接受的方法，可確保所要執行的程式碼是由可靠的來源產生的，並且尚未經過修改。 如需有關如何簽署 PowerShell 指令碼檔的詳細資料，請參閱[關於簽署](/powershell/module/microsoft.powershell.core/about/about_signing) \(英文\) 文章。 大致而言，您可以將簽章新增至 PowerShell 在載入指令碼時驗證的任何 `.PS1` 檔案中。 您可以使用[執行原則](/powershell/module/microsoft.powershell.core/about/about_execution_policies) Cmdlet 來限制 PowerShell，以確保所使用的是已簽署的指令碼。

類別目錄簽署模組是 PowerShell 5.1 版中新增的功能。 如需了解如何簽署模組，請參閱[類別目錄 Cmdlet](/powershell/wmf/5.1/catalog-cmdlets) 文章。 大致而言，簽署類別目錄的方式是建立類別目錄檔案 (包含模組中每個檔案的雜湊值)，然後簽署該檔案。

**PowerShellGet** `Publish-Module`、`Install-Module` 與 `Update-Module` Cmdlet 將會檢查簽章以確保檔案有效，然後確認每個套件的雜湊值與類別目錄中的內容相符。 `Save-Module` 不會驗證簽章。 如果系統上已安裝舊版的模組，`Install-Module` 將會確認新版本的簽署授權單位與先前安裝的相符。 若套件未經類別目錄簽署，`Install-Module` 與 `Update-Module` 將會使用 `.PSD1` 檔案上的簽章。 類別目錄簽署可以與簽署指令碼檔案搭配運作，但不會取代其功能。 PowerShell 不會在載入模組時驗證類別目錄簽章。

## <a name="follow-semver-guidelines-for-versioning"></a>遵循 SemVer 方針來進行版本設定

[SemVer](https://semver.org/) 是一種公用慣例，其描述如何架構及變更版本，以輕鬆解譯變更。 您套件的版本必須包含在資訊清單資料中。

- 該版本的結構應該是 3 個以句號分隔的數值區塊，例如 `0.1.1` 或 `4.11.192`。
- 開頭為 `0` 的版本表示該套件還不適用於生產環境，並且如果 `0` 是唯一使用的數字，則第一個數字應該只能以 "0" 為開頭。
- 第一個數字的變更 (從 `1.9.9999` 變更為 `2.0.0`) 代表版本之間的主要與中斷性變更。
- 第二個數字 (`1.1` 到 `1.2`) 的變更代表功能層級變更，例如加入新的 Cmdlet 到某個模組中。
- 第三個數字的變更代表非中斷性變更，例如新參數、更新的範例或新測試。
- 列出版本時，PowerShell 會將版本當作字串來排序，因此會將 `1.01.0` 視為比 `1.001.0` 還要新。

PowerShell 的建立時間是在 SemVer 發行前，因此它支援 SemVer 的大多數但非全部元素，具體而言：

- 它不支援版本號碼中的發行前版本字串。 當發行者想要在提供 `1.0.0` 版之後提供某個新主要版本的預覽版本時，該字串會相當有用。 在未來的「PowerShell 資源庫」和 **PowerShellGet** Cmdlet 版本中將會支援此功能。
- PowerShell 和「PowerShell 資源庫」允許使用含有 1、2 及 4 個區段的版本字串。 許多早期的模組並未依循這些指導方針，而來自 Microsoft 的產品版本會包含組建資訊作為第 4 個數字區塊 (例如 `5.1.14393.1066`)。 從版本設定的觀點來看，會將這些差異都予以忽略。

## <a name="test-using-a-local-repository"></a>使用本機存放庫來測試

PowerShell 資源庫並不適合作為測試發行程序的目標。 若要測試發行至 PowerShell 資源庫的端點對端點程序，最佳方式為設定並使用您自己的本機存放庫。 這可以由以下方法達成：

- 在 GitHub 中使用 [PS 私人資源庫專案](https://github.com/PowerShell/PSPrivateGallery)來設定本機 PowerShell 資源庫執行個體。 此預覽專案會協助您設定 PowerShell 資源庫執行個體，讓您可以控制及用於測試。
- 設定[內部 NuGet 存放庫](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/)。
  這個方法的設定較為複雜，但是能夠驗證更多需求。值得注意的是，不論您發行時目標是否有相依性，都能使用 API 金鑰進行驗證。
- 將檔案共用設定為測試「存放庫」  。 這很容易設定，但因為其為檔案共用，所以無法執行上述的驗證。 在此案例中，因為檔案共用不會檢查 (必要的) API 金鑰，所以您可以使用發行到 PowerShell 資源庫的相同金鑰，這可以說是潛在優點。

有了上述任何解決方案，請使用 `Register-PSRepository` 來定義新**存放庫**，您可以在 `Publish-Module` 的 `-Repository` 參數中使用它。

另外為測試發行補充一點：您發行到 PowerShell 資源庫的任何套件都必須在營運團隊的協助下才能刪除，因此他們會確認沒有任何內容相依於您要發行的套件。 基於此原因，我們不支援將 PowerShell 資源庫用作測試目標，且會與任何這樣做的發行者連絡。

## <a name="use-powershellget-to-publish"></a>使用 PowerShellGet 發佈

強烈建議發行者搭配 PowerShell 資源庫使用 `Publish-Module` 和 `Publish-Script` Cmdlet。 已建立 **PowerShellGet**，因此您不需要記住透過發佈至 PowerShell 資源庫進行安裝的重要詳細資料。 有時候，發行者會選擇略過 **PowerShellGet** 並使用 **NuGet** 用戶端或 **PackageManagement** Cmdlet，而不是使用 `Publish-Module`。 有幾個容易忽略的詳細資料會導致各種不同的支援要求。

如果您有無法使用 `Publish-Module` 或 `Publish-Script` 的原因，請讓我們知道。
請在 **PowerShellGet** GitHub 存放庫中提出問題，並提供導致您選擇 **NuGet** 或 **PackageManagement** 的詳細原因。

## <a name="recommended-workflow"></a>建議的工作流程

針對發行至「PowerShell 資源庫」的套件，我們找到的最成功方法是：

- 在開放原始碼的專案網站中進行初始開發。 PowerShell 小組使用的是 GitHub。
- 利用檢閱者和 [Powershell 指令碼分析程式](https://aka.ms/psscriptanalyzer)的意見反應來讓程式碼變得穩定。
- 包含文件，讓其他使用者了解如何使用您的作品。
- 使用本機存放庫測試發行動作。
- 將穩定版或 Alpha 版發行至「PowerShell 資源庫」，其中務必包含文件和您專案網站的連結。
- 收集意見反應並在您的專案網站中逐一查看程式碼，然後將穩定的更新發行至「PowerShell 資源庫」。
- 在您的專案和模組中新增範例和 Pester 測試。
- 決定是否要以程式碼簽署您的套件。
- 當您覺得專案已經準備好在生產環境中使用時，將 `1.0.0` 版本發行至「PowerShell 資源庫」。
- 繼續收集意見反應並根據使用者提供的意見逐一查看您的程式碼。
