---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 建立及發行項目
ms.openlocfilehash: 70696535a3bf540ff75a2dc43bca80cb1adf8f45
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012529"
---
# <a name="creating-and-publishing-an-item"></a>建立及發行項目

「PowerShell 資源庫」是可供您發行及與更廣大的 PowerShell 使用者社群共用穩定的 PowerShell 模組、指令碼及 DSC 資源的地方。

本文涵蓋準備指令碼或模組並將其發行至「PowerShell 資源庫」的機制和重要步驟。 強烈建議您檢閱[發行指導分針](../../concepts/publishing-guidelines.md) \(英文\)，以了解如何確保您發行的項目將更廣泛地獲得「PowerShell 資源庫」使用者接受。

將項目發行至「PowerShell 資源庫」的最低需求包括：

- 擁有「PowerShell 資源庫」帳戶及與該帳戶關聯的 API 金鑰
- 確定您的項目中有「必要的中繼資料」
- 使用預先驗證工具來確保您的項目已可發行
- 使用 Publish-Module 和 Publish-Script 命令將項目發行至「PowerShell 資源庫」
- 回應問題或疑慮，您的項目相關

「PowerShell 資源庫」接受 PowerShell 模組和 PowerShell 指令碼。 當我們提到指令碼時，是指本身是單一檔案而不屬於較大模組之一部分的 PowerShell 指令碼。

## <a name="powershell-gallery-account-and-api-key"></a>PowerShell 資源庫帳戶和 API 金鑰

如需了解如何設定您的「PowerShell 資源庫」帳戶，請參閱[建立 PowerShell 資源庫帳戶](/powershell/gallery/how-to/publishing-packages/creating-an-account) \(英文\)。

建立帳戶之後，您可以取得發行項目所需的 API 金鑰。 使用帳戶進行登入之後，您的使用者名稱將會顯示在「PowerShell 資源庫」頁面的頂端，而不會顯示 [註冊]。 按一下您的帳戶名稱就會前往 [我的帳戶] 頁面，您將可以在該頁面找到 API 金鑰。

注意：API 金鑰必須為您的登入和密碼安全地處理。
您或任何其他使用者只要有了這個金鑰，便可更新「PowerShell 資源庫」中您擁有的所有項目。
建議您定期更新此金鑰，只要使用 [我的帳戶] 頁面上的 [重設金鑰]，即可完成此操作。

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>發行至 PowerShell 資源庫之項目的必要中繼資料

「PowerShell 資源庫」會將從指令碼或模組資訊清單所包含之中繼資料欄位取得的資訊，提供給資源庫使用者。 建立或修改要發行至「PowerShell 資源庫」的項目時，針對在項目資訊清單中提供的資訊有一些要求。
強烈建議您檢閱[發行指導方針](../../concepts/publishing-guidelines.md) \(英文\) 的 ＜項目中繼資料＞ (Item Metadata) 一節，以了解如何為您項目的使用者提供最佳資訊。

[New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest) 和 [New-ScriptFileInfo](/powershell/module/PowerShellGet/New-ScriptFileInfo) Cmdlet 將會為您建立資訊清單範本，其中會包含所有資訊清單元素的預留位置。

這兩個資訊清單都有重要的發行，PrivateData 的主索引鍵資料和 PSData 區域的兩個區段。 PowerShell 模組資訊清單中主索引鍵的資料是指 PrivateData 區段外的所有項目。 主索引鍵組會繫結至使用中的 PowerShell 版本，且不支援設為未定義。 PrivateData 支援新增金鑰，因此「PowerShell 資源庫」特定的元素會在 PSData 中。


對您要發行至「PowerShell 資源庫」的項目來說，要填入的最重要資訊清單元素包括：

- 指令碼或模組名稱 - 這些名稱會取自 .PS1 (適用於指令碼) 或 .PSD1 (適用於模組)。
- 版本-這是必要的主索引鍵，格式應該依循 SemVer 指導方針。 如需詳細資訊，請參閱最佳作法。
- 作者-這是必要的主索引鍵，並包含與項目相關聯的名稱。
請參閱作者和下方的擁有者。
- 描述 - 這是必要的主索引鍵，用來簡要說明此項目的功能及使用它時的任何需求
- ProjectURI - 這是強烈建議使用的 PSData 中 URI 欄位，可提供 Github 儲存機制或可供您進行項目相關開發之類似位置的連結
- 標記-它是強式的建議，來標記您根據其具有 PSEditions 與平台的相容性的套件。 如需詳細資訊，請參閱 <<c0> [ 發行指導方針](../../concepts/publishing-guidelines.md#tag-your-package-with-the-compatible-pseditions-and-platforms)。

「PowerShell 資源庫」項目的「作者」和「擁有者」是相關的概念，但未必一定相符。 項目「擁有者」是「PowerShell 資源庫」帳戶具有項目維護權限的使用者。 可能會有許多個能夠更新任何項目的「擁有者」。 「擁有者」只有從「PowerShell 資源庫」中才有提供，且如果將項目從一個系統複製到另一個系統，就會遺失擁有者。 「作者」是建置在資訊清單資料中的字串，因此它一律是項目的一部分。 針對來自 Microsoft 產品的項目，建議事項包括：

- 設定多個擁有者，其中至少有一個是產生項目的小組名稱
- 將「作者」設為已知的小組名稱 (例如 Azure SDK Team) 或 Microsoft Corporation


## <a name="pre-validate-your-item"></a>預先驗證您的項目

將項目發行至「PowerShell 資源庫」之前，有一些您必須針對程式碼執行的工具：

- [PowerShell 指令碼分析程式](https://www.powershellgallery.com/packages/PSScriptAnalyzer/)：此工具位於「PowerShell 資源庫」中
- 針對模組，請執行 Test-ModuleManifest，這包含在 PowerShell 中
- 針對指令碼，請執行 Test-ScriptFileInfo，這隨附於 PowerShell Get

[PowerShell 指令碼分析程式](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) 是一個靜態的程式碼分析工具，會掃描您的程式碼以確保它符合基本的 PowerShell 程式碼編寫指導方針。 此工具會識別您程式碼中的一般和重大問題，在開發期間應該定期執行，以協助您備妥項目以供發行。 「PowerShell 指令碼分析工具」會提供識別為「錯誤」、「警告」及「資訊」的問題清單。 您必須解決所有錯誤，才能將項目發行至「PowerShell 資源庫」。 警告需要經過檢閱，且大多數都應該加以解決。 每次在「PowerShell 資源庫」中發行或更新項目時，都會執行「PowerShell 指令碼分析工具」。 「資源庫作業」小組將會連絡項目擁有者來解決所發現的問題。

如果「PowerShell 資源庫」基礎結構無法讀取您項目中的資訊清單資訊，您將無法發行該項目。
[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest) 會捕捉將造成模組在安裝後無法使用的常見問題。 您必須先針對每個模組執行此 Cmdlet，才能將模組發行至「PowerShell 資源庫」。

同樣地，[Test-ScriptFileInfo](/powershell/module/PowerShellGet/test-scriptfileinfo) 會驗證指令碼中的資訊清單，且必須先在每個指令碼 (與模組個別發行) 上執行，才能將指令碼發行至「PowerShell 資源庫」。


## <a name="publishing-items"></a>發行項目

您必須使用 [Publish-Script](/powershell/module/PowerShellGet/publish-script) 或 [Publish-Module](/powershell/module/PowerShellGet/publish-module) 將項目發行至「PowerShell 資源庫」。 這些命令都需要：

- 您將發行之項目的路徑。 針對模組，請使用針對您模組命名的資料夾。 如果您指定的資料夾包含同一個模組的多個版本，您就必須指定 RequiredVersion。
- Nuget API 金鑰。 這是在「PowerShell 資源庫」上 [我的帳戶] 頁面中找到的 API 金鑰。

命令列中大多數其他選項應該都在您要發行之項目的資訊清單資料中，因此您應該不需要在命令中指定它們。

為了避免錯誤，強烈建議您在發行之前，先使用 -Whatif -Verbose 來嘗試執行命令。 這將可大幅節省時間，因為每次您發行至「PowerShell 資源庫」時，都必須更新項目資訊清單區段中的版本號碼。

範例可能是：

* `Publish-Module -Path ".\MyModule" -NugetAPIKey "GUID" -Whatif -Verbose`
* `Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -Whatif -Verbose`

請小心檢閱輸出，如果沒看見任何錯誤或警告，請在不使用 -Whatif 的情況下重複執行該命令。

系統會對所有發行至「PowerShell 資源庫」的項目進行病毒掃描，並使用「PowerShell 指令碼分析工具」進行分析。 在該時間出現的所有問題都會傳回給發行者來進行解析。

將項目發行至「PowerShell 資源庫」之後，您將必須監看有關項目的意見反應。

- 請務必監看與用來發行之帳戶相關的電子郵件地址。 使用者及「PowerShell 資源庫作業」小組將會透過提供該帳戶提供意見反應，包括來自 PSSA 或防毒軟體掃描的問題。 如果該電子郵件帳戶無效，或將嚴重問題回報給該帳戶而長時間未獲得解決，系統就可能將項目視為已遭捨棄，而將會如[使用規定](https://www.powershellgallery.com/policies/Terms)所述，從「PowerShell 資源庫」中移除。
- 建議您訂閱您所發行之每個「PowerShell 資源庫」項目的「評論」。 如此一來，當任何使用者對您在「PowerShell 資源庫」中的項目提出評論時，您便會收到通知。 這是選擇性選項，因為這需要使用 LiveFyre 來建立帳戶。
