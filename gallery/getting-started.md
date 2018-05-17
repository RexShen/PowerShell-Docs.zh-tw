---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: c3aafe9e76eda9acdd4787f63dc0f8c71a20d02a
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="get-started-with-the-powershell-gallery"></a>開始使用 PowerShell Gallery

將項目從 PowerShell Gallery 下載至系統時，需要 [PowerShellGet](/powershell/module/powershellget) 模組。 您可以在下列任何一項中尋找 PowerShellGet 模組。 您不需要登入，就可以從 PowerShell Gallery 下載項目。

## <a name="discovering-items-from-the-powershell-gallery"></a>探索 PowerShell Gallery 中的項目

在這個網站上使用 **Search** 控制項，或瀏覽 [模組] 和 [指令碼] 頁面，即可尋找 PowerShell Gallery 中的項目。 您也可以執行 [Find-Module][] 與 [Find-Script][] Cmdlet (視項目類型而定) 並搭配 `-Repository PSGallery`，以尋找 PowerShell 資源庫中的項目。

若要從資源庫篩選結果，可以使用下列參數：

- 名稱
- AllVersions
- MinimumVersion
- RequiredVersion
- 標籤
- Includes
- DscResource
- RoleCapability
- 命令
- 篩選器

如果您只想要探索資源庫中的特定 DSC 資源，則可以執行 [Find-DscResource] Cmdlet。 Find-DscResource 會傳回資源庫中所含 DSC 資源的資料。
因為 DSC 資源一律傳遞為模組的一部分，所以您仍然需要執行 [Install-Module][] 來安裝這些 DSC 資源。

## <a name="learning-about-items-in-the-powershell-gallery"></a>了解 PowerShell Gallery 中的項目

在您識別到感興趣的項目之後，可能會想要深入了解。 做法是檢查 Galler 上項目的特定頁面。 在該頁面上，您可以看到所有與項目一起上傳的中繼資料。 項目的這個中繼資料是由項目作者所提供，未經 Microsoft 驗證。 項目的 [擁有者] 與用來發行項目的 Gallery 帳戶緊密連結，而且比 [作者] 欄位更為可靠。

如果您發現可能未以誠信方式發行的項目，請按一下該項目之頁面上的 [檢舉不當使用]。

如果您是執行 [Find-Module][] 或 [Find-Script][]，則可以在所傳回的 PSGetModuleInfo 物件中檢視這個資料。 例如，執行 `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` 可傳回資源庫中 PSReadLine 模組的資料。

## <a name="downloading-items-from-the-powershell-gallery"></a>從 PowerShell Gallery 下載項目

從 PowerShell Gallery 下載項目時，建議使用下列程序︰

### <a name="inspect"></a>檢查

若要下載資源庫中的項目來進行檢查，請執行 [Save-Module][] 或 [Save-Script][] Cmdlet (視項目類型而定)。 這可讓您在本機儲存項目，而不需要安裝它，並且檢查項目內容。 請記得手動刪除儲存的項目。

這些項目有一部分是由 Microsoft 所撰寫，其他則是由 PowerShell 社群所撰寫。
Microsoft 建議您檢閱這個組件庫上項目的內容和程式碼，再進行安裝。

如果您發現可能未以誠信方式發行的項目，請按一下該項目之頁面上的 [檢舉不當使用]。

### <a name="install"></a>安裝

若要安裝資源庫中的項目來進行使用，請執行 [Install-Module][] 或 [Install-Script][] Cmdlet (視項目類型而定)。

[Install-Module][] 預設會將模組安裝至 `$env:ProgramFiles\WindowsPowerShell\Modules`。
這需要系統管理員帳戶。 如果您新增 `-Scope CurrentUser` 參數，模組就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。

[Install-Script][] 預設會將指令碼安裝至 `$env:ProgramFiles\WindowsPowerShell\Scripts`。
這需要系統管理員帳戶。 如果您新增 `-Scope CurrentUser` 參數，指令碼就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。

[Install-Module][] 和 [Install-Script][] 預設會安裝項目的最新版本。
若要安裝項目的舊版本，請新增 `-RequiredVersion` 參數。

### <a name="deploy"></a>在客體叢集部署

若要將項目從 PowerShell Gallery 部署至 Azure 自動化，請按一下項目詳細資料頁面上的 [Deploy to Azure Automation] \(部署至 Azure 自動化)。 會將您重新導向至使用 Azure 帳戶認證所登入的 Azure 管理入口網站。 請注意，部署包含相依性的項目時會將所有相依性部署至 Azure 自動化。 將 **AzureAutomationNotSupported** 標記新增至項目中繼資料，即可停用 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕。

若要深入了解 Azure 自動化，請參閱 [Azure 自動化](/azure/automation)文件。

## <a name="updating-items-from-the-powershell-gallery"></a>更新 PowerShell Gallery 中的項目

若要更新從「PowerShell 資源庫」安裝的項目，請執行 [Update-Module][] 或 [Update-Script][] Cmdlet。 如果執行時未指定任何其他參數，[Update-Module][] 就會嘗試更新透過執行 [Install-Module][] 所安裝的每個模組。 若要選擇性地更新模組，請新增 `-Name` 參數。

同樣地，如果執行時未指定任何其他參數，[Update-Script][] 也會嘗試更新透過執行 [Install-Script][] 所安裝的每個指令碼。 若要選擇性地更新指令碼，請新增 `-Name` 參數。

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>列出您已從 PowerShell Gallery 安裝的項目

若要找出您已從 PowerShell 資源庫安裝的模組，請執行 [Get-InstalledModule][] Cmdlet。 這個命令會列出系統上直接從 PowerShell Gallery 安裝的所有模組。

同樣地，若要找出您已從 PowerShell 資源庫安裝的指令碼，請執行 [Get-InstalledScript][] Cmdlet。 這個命令會列出系統上直接從 PowerShell Gallery 安裝的所有指令碼。

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script