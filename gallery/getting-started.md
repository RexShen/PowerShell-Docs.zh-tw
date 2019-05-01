---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 開始使用 PowerShell Gallery
ms.openlocfilehash: c8beba3009e462ce52cdecd34fc0313d9234f289
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084754"
---
# <a name="getting-started-with-the-powershell-gallery"></a>開始使用 PowerShell 資源庫

PowerShell 資源庫是一個套件存放庫，其中包含您可以下載並利用的指令碼、模組和 DSC 資源。 您可以使用 [PowerShellGet](/powershell/module/powershellget) 模組中的 Cmdlet，從 PowerShell 資源庫安裝套件。 您不需要登入，就可以從 PowerShell Gallery 下載項目。

> [!NOTE]
> 您可以從 PowerShell 資源庫直接下載套件，但這不是建議的方法。
> 如需詳細資訊，請參閱[手動下載套件](/powershell/gallery/how-to/working-with-packages/manual-download)。

## <a name="discovering-packages-from-the-powershell-gallery"></a>從 PowerShell 資源庫探索套件

您可以使用 PowerShell 資源庫[首頁](https://www.powershellgallery.com) \(英文\) 上的**搜尋**控制項，或從[套件頁面](https://www.powershellgallery.com/packages) \(英文\) 完整瀏覽模組和指令碼，藉以在 PowerShell 資源庫中尋找套件。 您也可以搭配 `-Repository PSGallery` 執行 [Find-Module][]、[Find-DscResource] 及 [Find-Script][] Cmdlet (視套件類型而定)，來尋找 PowerShell 資源庫中的套件。

您可以使用下列參數，從資源庫中篩選結果：

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

## <a name="learning-about-packages-in-the-powershell-gallery"></a>在 PowerShell 資源庫中了解套件

在您找出自己感興趣的套件之後，可能會想要深入了解它。 您可以透過檢查該套件在資源庫上的特定頁面來這麼做。 在該頁面上，您將可以看到所有與該套件一起上傳的中繼資料。 此中繼資料是由套件的作者所提供，且未經 Microsoft 驗證。 套件的擁有者與用來發行該套件的資源庫帳戶具有緊密的關聯性，因此會比 [Author] \(作者\) 欄位中的資訊更為可靠。

如果您發現可能未以誠信心態發行的套件，請按一下該套件頁面上的 [Report Abuse] \(檢舉不當使用\)。

如果您是執行 [Find-Module][] 或 [Find-Script][]，則可以在所傳回的 PSGetModuleInfo 物件中檢視這個資料。 例如，執行 `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
會傳回資源庫中 PSReadLine 模組的相關資料。

## <a name="downloading-packages-from-the-powershell-gallery"></a>從 PowerShell 資源庫下載套件

從 PowerShell 資源庫下載套件時，建議使用下列程序︰

### <a name="inspect"></a>檢查

若要下載資源庫中的套件以進行檢查，請執行 [Save-Module][] 或 [Save-Script][] Cmdlet (視套件類型而定)。 這可讓您在不安裝該套件的情況下於本機儲存它，並檢查套件內容。 請記得手動刪除已儲存的套件。

這些套件有一部分是由 Microsoft 所撰寫，其他則是由 PowerShell 社群所撰寫。
Microsoft 建議您先檢閱此資源庫上的套件內容和程式碼，然後再進行安裝。

如果您發現可能未以誠信心態發行的套件，請按一下該套件頁面上的 [Report Abuse] \(檢舉不當使用\)。

### <a name="install"></a>安裝

若要安裝資源庫中的套件以來進行使用，請執行 [Install-Module][] 或 [Install-Script][] Cmdlet (視套件類型而定)。

[Install-Module][] 預設會將模組安裝至 `$env:ProgramFiles\WindowsPowerShell\Modules`。
這需要系統管理員帳戶。 如果您新增 `-Scope CurrentUser` 參數，模組就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。

[Install-Script][] 預設會將指令碼安裝至 `$env:ProgramFiles\WindowsPowerShell\Scripts`。
這需要系統管理員帳戶。 如果您新增 `-Scope CurrentUser` 參數，指令碼就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。

根據預設，[Install-Module][] 和 [Install-Script][] 會安裝套件的最新版本。
若要安裝較舊的套件版本，請新增 `-RequiredVersion` 參數。

### <a name="deploy"></a>在客體叢集部署

若要將套件從 PowerShell 資源庫部署至 Azure 自動化，按一下 [Azure 自動化]，然後按一下套件詳細資料頁面上的 [部署至 Azure 自動化]。 系統會將您重新導向至 Azure 管理入口網站，而您必須使用 Azure 帳戶認證來登入。 請注意，部署含相依性的套件會將所有相依性部署至 Azure 自動化。 若要停用 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕，請將 **AzureAutomationNotSupported** 標記新增至套件中繼資料。

若要深入了解 Azure 自動化，請參閱 [Azure 自動化](/azure/automation)文件。

## <a name="updating-packages-from-the-powershell-gallery"></a>從 PowerShell 資源庫更新套件

若要更新從 PowerShell 資源庫安裝的套件，請執行 [Update-Module][] 或 [Update-Script][] Cmdlet。 如果執行時未指定任何其他參數，[Update-Module][] 就會嘗試更新透過執行 [Install-Module][] 安裝的所有模組。 若要選擇性地更新模組，請新增 `-Name` 參數。 

同樣地，如果執行時未指定任何其他參數，[Update-Script][] 也會嘗試更新透過執行 [Install-Script][] 安裝的所有指令碼。 若要選擇性地更新指令碼，請新增 `-Name` 參數。

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>列出已從 PowerShell 資源庫安裝的套件

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
