---
title: "功能或案例寫上的範例範本"
contributor: KeithB
translationtype: Human Translation
ms.sourcegitcommit: 8c55ca4b972c8d708a09b922f27eec585ddc33d0
ms.openlocfilehash: 025565404b60cebefac27e51c70d70edb5e47bc9

---

>注意︰請提供建議的描述性標題和簡短描述

## PowerShellGet 增強功能 ##
在 WMF 5.1 中，已大幅更新 PowerShellGet 模組中的 Cmdlet。 下列是現在支援的新案例：

- **Proxy 支援：**現在支援搭配使用 PowerShellGet Cmdlet 與內部 Proxy，並將 Proxy 和 ProxyCredential 參數新增至 PowerShellGet 模組 (例如：Find-Module、Install-Module、Save-Module、Publish-Module) 中的所有 Find-、Install-、Save- 和 Publish- Cmdlet。 
- **強制簽署類別目錄：**所有 PowerShellGet Cmdlet 現在都會檢查和強制更新已簽署的模組。 PowerShellGet Cmdlet 將會檢查使用新 Catalog Cmdlet 所簽署的模組，確定未在傳輸時修改模組，而且模組的更新可能只會來自原始發行者。 這會影響 Install-Module 和 Update-Module Cmdlet。 
- **共用和取得角色功能︰**角色功能是用來設定 Just Enough Administration 所限制的端點定義，而且會透過 PowerShell 模組中的 PowerShell Gallery 共用。 Cmdlet 包含 Find-RoleCapability 和 New-PSRoleCapabilityFile。 
- **尋找命令︰**Find-Command 可讓使用者尋找 PowerShell Gallery 中包含所尋找命令的模組。 
- **已驗證存放庫：**Visual Studio 套件管理摘要需要現在透過 PowerShellGet Cmdlet 支援的驗證。

使用者意見反應識別已在 5.1 中解決之改善的其他區域，包括：

- **Install-Script 變更︰**Install-Script 所使用的位置不會自動新增至 5.1 中的使用者路徑。 這項變更是在獨立版的 PowerShellGet 中進行，但現在處於 WMF 5.1。
- **將中繼資料欄位新增至現有指令碼：**Update-ScriptFileInfo 可以用於現有指令碼，以新增發行至 PowerShellGallery 所需的預設中繼資料欄位。 以前，使用者需要手動將此合併至現有指令碼。
- **將低版本的模組發行至 Gallery：**現在可以使用 Publish-Module 將版本號碼低於目前最高舊版本的模型發行至 Gallery。 如果發行者已發行 2.0.0 版且具有 1.x 版重大變更的模型，則無法輕鬆地發行 1.5.0 版的修正程式。 現在，它們可以發行 1.5.1，以改善維護 PowerShell Gallery 中模組的支援。 
- **安裝指令碼和模組時檢查命令覆寫︰**Install-Module 和 Install-Script 現在會確認它們是否包含已存在於系統上的命令，而且錯誤預設會在發生這種情況時消失。 
- **在 Publish- Cmdlet 中啟動載入 Nuget：**以前，使用很難完成特定自動化工作的 Publish-Module 或 Publish-Script 時，沒有方法可以自動安裝 Nuget 提供者。 使用者現在可以將 -Force 新增至 Publish- 命令，以略過提示。 

>注意︰涵蓋新概念、實作、範例等的其他詳細資料，應該連結到標準技術文件。

**深入了解使用 PowerShellGet**
- [About-CatalogSigning]()
- []()
- [依據 CompatiblePSEditions 篩選 Get-Module 結果]()
- [只有在相容的 PowerShell 版本上執行才會執行指令碼]()






<!--HONumber=Aug16_HO3-->


