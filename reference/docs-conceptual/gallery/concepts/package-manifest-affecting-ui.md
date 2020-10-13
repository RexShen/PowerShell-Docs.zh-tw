---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: 影響 PowerShell 資源庫 UI 的套件資訊清單值
ms.openlocfilehash: d5e0b85a635c4090f8ccb814277a1a6dd6a951e2
ms.sourcegitcommit: 1695df0d241c0390cac71a7401e61198fc6ff756
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "91772298"
---
# <a name="package-manifest-values-that-impact-the-powershell-gallery-ui"></a>影響 PowerShell 資源庫 UI 的套件資訊清單值

本主題為發行者提供如何修改其 PowerShell 資源庫出版物資訊清單的摘要資訊，以影響 PowerShellGet Cmdlet 的功能和 PowerShell 資源庫 UI。 本內容是根據出現變更的位置來組織，首先從中間的區段開始，然後是左側的瀏覽區域。 其中有詳述標籤的小節，列出重要的標籤和一些較常用的標籤。 有兩個主題提供資訊清單範例：

- 針對模組，請參閱[更新模組資訊清單](/powershell/module/powershellget/Update-ModuleManifest)
- 針對指令碼，請參閱[建立含有中繼資料的指令碼檔](/powershell/module/powershellget/New-ScriptFileInfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>由資訊清單控制的 PowerShell 資源庫功能元素

下表顯示由發行者控制的 PowerShell 資源庫套件頁面 UI 元素。 每個項目都指出它是由模組或指令碼資訊清單所控制。

| UI 元素 | 描述 | 模組 | 指令碼 |
| --- | --- | --- | --- |
| **Title** (標題) | 這是發行到資源庫之套件的名稱  | 否 | 否 |
| **版本** | 顯示的版本是中繼資料中的版本字串，若指定則會顯示為發行前版本。 模組資訊清單中版本的主要部分是 ModuleVersion。 針對指令碼，會以 .VERSION 識別。 若指定發行前版本字串，系統會將它附加到模組的 ModuleVersion，或是指定為指令碼之 .VERSION 的一部分。 如需詳細資訊，請參閱有關在[模組](module-prerelease-support.md)中和在[指令碼](script-prerelease-support.md)中指定發行前版本字串的文件 | 是 | 是 |
| **說明** | 這是模組資訊清單中的 Description，而在指令碼檔案資訊清單中是 .DESCRIPTION | 是 | 是 |
| **Require license acceptance** (必須接受授權) | 模組可以要求使用者接受授權，方法是以 RequireLicenseAcceptance = $true 修改模組資訊清單、提供 LicenseURI，並在模組資料夾的根資料夾提供 license.txt 檔案。 其他資訊可在[必須接受授權](../how-to/working-with-packages/packages-that-require-license-acceptance.md)主題取得。 | 是 | 否 |
| **版本資訊** | 針對模組，此資訊是取自 PSData\PrivateData 下的 [ReleaseNotes] 區段。 在指令碼資訊清單中，它是 .RELEASENOTES 元素。 | 是 | 是 |
| **Owners** (擁有者) | 擁有者是可以更新套件的 PowerShell 資源庫使用者清單。 擁有者清單未包含在套件資訊清單中。 描述如何[管理項目擁有者](../how-to/publishing-packages/managing-package-owners.md)的其他文件。 | 否 | 否 |
| **Author** (作者) | 此項目以 Author 包含在模組資訊清單中，而在指令碼清單中是 .AUTHOR。 [建立者] 欄位通常是用於指定與某個套件相關聯的公司或組織。 | 是 | 是 |
| **Copyright** (著作權) | 這是模組資訊清單中的 [Copyright] 欄位，而在指令碼資訊清單中是 .COPYRIGHT。 | 是 | 是 |
| **FileList** (檔案清單) | 當套件發佈到 PowerShell 資源庫時，會從套件取得檔案清單。 它不是由資訊清單資訊控制。 注意：每個套件在 PowerShell 資源庫中都列出一個額外的 .nuspec 檔案，但是在系統上安裝套件之後不會顯示該檔案。 這是該套件的 Nuget 套件資訊清單，可以忽略它。 | 否 | 否 |
| **Tags** (標籤) | 針對模組，Tags 包含在 PSData\PrivateData 之下。 針對指令碼，該區段標記為 .TAGS。 請注意，標籤不能包含空格，即使當它們在引號中亦然。 標籤具有其他需求和意義，稍後會在本主題的＜標籤詳細資訊＞一節中說明。 | 是 | 是 |
| **Cmdlet** | 此項目在模組資訊清單中使用 CmdletsToExport 來提供。 請注意，最佳做法是明確地列出項目，這樣可改善使用者的載入模組效能，而不是使用萬用字元 "*"。 | 是 | 否 |
| **函數** | 此項目在模組資訊清單中使用 FunctionsToExport 來提供。 請注意，最佳做法是明確地列出項目，這樣可改善使用者的載入模組效能，而不是使用萬用字元 "*"。 | 是 | 否 |
| **DSC 資源** | 針對將會用於 PowerShell 5.0 版和以上版本的模組，此項目在資訊清單中是使用 DscResourcesToExport 來提供。 如果模組是在 PowerShell 4 中使用，則不應使用 DSCResourcesToExport，因為它不是受支援的資訊清單金鑰 (PowerShell 4 之前的版本不支援 DSC)。 | 是 | 否 |
| **工作流程** | 工作流程會以指令碼的形式發佈到 PowerShell 資源庫，並在程式碼中識別為工作流程 (如需範例，請參閱 [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1))。 此項目不是由資訊清單控制。 | 否 | 否 |
| **Role capabilities** (角色功能) | 當模組發佈到 PowerShell 資源庫且包含一或多個角色功能 (.psrc) 檔案 (由 JEA 使用) 時，系統會列出此清單。 如需[角色功能](/powershell/scripting/learn/remoting/jea/role-capabilities)的詳細資訊，請參閱 JEA 文件。 | 是 | 否 |
| **PowerShell Editions** (PowerShell 版本) | 此項目是在指令碼或模組資訊清單中指定。 針對專門為 PowerShell 5.0 和以下版本設計的模組，此項目使用 Tags 控制。 針對 Desktop，請使用 PSEdition_Desktop 標籤；針對 Core，請使用 PSEdition_Core。 針對只會在 PowerShell 5.1 和以上版本使用的模組，在主要資訊清單中有 CompatiblePSEditions 金鑰。 如需其他詳細資料，請檢閱 [PowerShell Get 文件](module-psedition-support.md)中的 PS Edition 功能。 | 是 | 是 |
| **Dependencies** (相依性) | 相依性是 PowerShell 資源庫中的模組以 RequiredModules 宣告的模組，或是指令碼資訊清單中以 #Requires –Module (名稱) 宣告的模組。 | 是 | 是 |
| **最低 PowerShell 版本** | 此項目可在模組資訊清單中以 PowerShellVersion 指定 | 是 | 否 |
| **Version History** (版本歷程記錄) | 版本歷程記錄反映對 PowerShell 資源庫中的模組進行的更新。 如果使用 Delete 功能隱藏套件的版本，則除了對套件擁有者之外，系統將不會在版本歷程記錄中顯示版本。 | 否 | 否 |
| **Project Site** (專案網站) | 模組的專案網站是在模組資訊清單中的 Privatedata\PSData 區段以 ProjectURI 提供。 在指令碼資訊清單中，是透過指定 .PROJECTURI 來控制。 | 是 | 是 |
| **授權** | 模組的授權連結是在模組資訊清單中的 Privatedata\PSData 區段以 LicenseURI 提供。 在指令碼資訊清單中，是透過指定 .LICENSEURI 來控制。 請務必注意，如果授權不是透過 LicenseURI 提供，或在模組中提供，則該套件的使用規定是由 PowerShell 資源庫使用規定來指定。 如需詳細資訊，請參閱使用規定。 | 是 | 是 |
| **圖示** | 您可以在指令碼資訊清單或模組資訊清單的 Privatedata-PSData 區段中提供 IconURI 旗標，為 PowerShell 資源庫中的任何套件指定圖示。 IconURI 應該指向具有透明背景的 85x85 影像。 URI **必須**是直接影像 URL，**不得**連至包含該影像的網頁，或 PowerShell 資源庫套件中的檔案。 | 是 | 是 |

## <a name="editing-package-details"></a>編輯套件詳細資料

PowerShell 資源庫 [編輯套件] 頁面可讓發行者變更針對套件顯示的數個欄位，特別是：

- Title
- 描述
- 摘要
- Icon URL (圖示 URL)
- Project home page URL (專案首頁 URL)
- Authors
- 著作權
- Tags
- 版本資訊
- Require license (需要授權)

通常不建議使用此方法，除非在需要修正舊版模組顯示的資訊時才使用。 取得模組的使用者將會看到中繼資料與 PowerShell 資源庫中顯示的內容不符合，這會讓使用者對套件產生疑慮。 此情況通常會造成使用者向套件擁有者詢問以確認變更。 強烈建議每次使用此方法時，也應該發佈具有相同變更的新版套件。

## <a name="tag-details"></a>標籤詳細資料

標籤是取用者用來尋找套件的簡單字串。 將標籤一致地用於與某個主題相關的多個套件時，可發揮其最大價值。 使用同一個單字的多個形式 (例如 database 和 databases，或 test 和 testing) 通常能提供一點助益。 標籤是區分大小寫的單一字詞字串，且不能包含空格。 如果您認為使用者會搜尋某個片語，將該片語新增到套件描述，它就會出現在搜尋結果中。 如果您想要改善可讀性，可以使用 Pascal 大小寫慣例、連字號、底線或句號。
建立長而複雜且不尋常的標籤時請特別留意，因為它們常被拼錯。

請特別注意某些標籤，因為 PowerShell 資源庫和 PowerShellGet Cmdlet 會將它們視為不同。 已在上面說明過的 PSEdition_Desktop 和 PSEdition_Core 即為範例。

如上面提及，當標籤是明確的且一致地用於許多套件時，可發揮其最大價值。 當發行者嘗試找出最合適的標籤時，最簡單的方法是在 PowerShell 資源庫搜尋您所考慮的標籤。 在理想的情況下，系統會傳回許多套件，且套件描述會與您使用的關鍵字相符合。

如需參考，以下是截至 2017/12/14 為止最常被使用的標籤。 在某些案例中，標籤旁邊列有相似但可能較不理想的選項。 最佳做法是使用「偏好的標籤」，因為這樣會造成的干擾較少，且取用者有較佳的搜尋結果。

| 偏好的標籤 | 替代選項和注意事項 |
| --- | --- |
| Azure |  |
| DSC | DesiredStateConfiguration 太長，因此不建議使用 |
| ResourceManager | ARM 是用於描述處理器群組，不應該用於 Azure Resource Manager |
| DSCResourceKit |  |
| SQL |  |
| AWS |  |
| DSCResource |  |
| 自動化 |  |
| REST |  |
| ActiveDirectory | 目前它本身未使用 AD  |
| SQLServer |  |
| DBA |  |
| 安全性 | Defense 較不精確 |
| 資料庫 | 不建議使用 Databases (複數) |
| DevOps |  |
| Windows |  |
| Build |  |
| 部署 | 相較之下較少使用 Deploy |
| Cloud |  |
| GIT |  |
| 測試 | 不建議使用 Testing |
| VersionControl | Version 較不精確，但使用的頻率較高  |
| 記錄 | 建議用於將「記錄」當成一個動作 |
| Log | 建議用於將「記錄」當成一個東西 |
| Backup |  |
| IaaS |  |
| Linux |  |
| IIS |  |
| AzureAutomation |  |
| 儲存體 |  |
| GitHub |  |
| Json |  |
| Exchange |  |
| 網路 | Networking 為相似的字，但較少使用 |
| SharePoint |  |
| 報告 | Reporting 是一個動作，Report 是一個東西 |
| Report | Report 是一個東西 |
| WinRM |  |
| 監視 |  |
| VSTS |  |
| Excel |  |
| Google |  |
| Color |  |
| DNS |  |
| Office365 | 建議拼為 Office。 雖然 O365 較簡短，但較少使用 |
| Gitlab |  |
| Pester |  |
| AzureAD |  |
| HTML |  |
| Hyper-V | 通常不以 HyperV 作為標籤 |
| 組態 |  |
| ChatOps |  |
| PackageManagement |  |
| WMI |  |
| 防火牆 |  |
| Docker |  |
| Appveyor |  |
| AzureRm | 主要用於 AzureRM 模組 |
| Zip |  |
| MSI |  |
| MacOS |  |
| PoshBot |  |
