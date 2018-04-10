---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: 599b148e141ba4205a7c774581e737a5d54bfae1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-the-powershell-gallery"></a>開始使用 PowerShell Gallery

## <a name="what-is-the-powershell-gallery"></a>什麼是 PowerShell Gallery？

PowerShell 資源庫是 PowerShell 內容的集中存放庫。
您可以在其中找到包含 PowerShell 命令或預期狀態設定 (DSC) 資源的有用 PowerShell 模組。 您也可以尋找 PowerShell 指令碼，其中有些可能會包含 PowerShell 工作流程，有些則概述一組工作並提供這些工作的序列。
這些項目有一部分是由 Microsoft 所撰寫，其他則是由 PowerShell 社群所撰寫。

## <a name="requirements"></a>需求

將項目從 PowerShell Gallery 下載至系統時，需要 [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 模組。 您可以在下列任何一項中尋找 PowerShellGet 模組。 您不需要登入，就可以從 PowerShell Gallery 下載項目。

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [MSI Installer (適用於 PowerShell 3 和 4)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

PowerShellGet 也需要 [NuGet 提供者](http://go.microsoft.com/fwlink/?LinkId=722208)，才能處理 PowerShell Gallery。 如果 NuGet 提供者不在下列其中一個位置中，則系統會在第一次使用 PowerShellGet 時提示您安裝 NuGet 提供者：

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

或者，您可以執行 `Install-PackageProvider -Name NuGet -Force` 來自動下載和安裝 NuGet 提供者。


如果您的版本比 NuGet 2.8.5.201 還要舊，則需要呼叫下列 PowerShell Cmdlet 來安裝並切換至最新版本的 NuGet。

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  從上述安裝的位置中，刪除舊版本的 NuGet。

如需詳細資訊，請參閱 <http://oneget.org/>。


注意︰因為封裝格式變更，所以建議您更新至最新版本的 PowerShellGet 和 PackageManagement，以安裝最近更新過的項目。 PowerShellGet 包含可在[這裡](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)進一步了解的 Windows 10 中。
PowerShellGet 也是可在[這裡](http://go.microsoft.com/fwlink/?LinkId=398175)下載之 Windows Management Framework (WMF) 5.0 的一部分。

## <a name="discovering-items-from-the-powershell-gallery"></a>探索 PowerShell Gallery 中的項目

在這個網站上使用 **Search** 控制項，或瀏覽 [模組] 和 [指令碼] 頁面，即可尋找 PowerShell Gallery 中的項目。 您也可以執行 [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 與 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) Cmdlet (視項目類型而定) 並搭配 `-Repository PSGallery`，以尋找 PowerShell 資源庫中的項目。

使用下列 [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 和 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) 參數，即可篩選 Gallery 中的結果。

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

如果您只想要探索資源庫中的特定 DSC 資源，則可以執行 [Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) Cmdlet。
[Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) 會傳回資源庫中所含 DSC 資源的資料。 因為 DSC 資源一律傳遞為模組的一部分，所以您仍然需要執行 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 來安裝這些 DSC 資源。

## <a name="learning-about-items-in-the-powershell-gallery"></a>了解 PowerShell Gallery 中的項目

在您識別到感興趣的項目之後，可能會想要深入了解。 做法是檢查 Galler 上項目的特定頁面。 在該頁面上，您可以看到所有與項目一起上傳的中繼資料。 項目的這個中繼資料是由項目作者所提供，未經 Microsoft 驗證。 項目的 [擁有者] 與用來發行項目的 Gallery 帳戶緊密連結，而且比 [作者] 欄位更為可靠。

如果您發現可能未以誠信方式發行的項目，請按一下該項目之頁面上的 [檢舉不當使用]。

如果您是執行 [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 或 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)，則可以在所傳回的 PSGetModuleInfo 物件中檢視這個資料。
例如，執行 `Find-Module -Name PSReadLine -Repository PSGallery | Get-Member` 可傳回資源庫中 PSReadLine 模組的資料。

## <a name="downloading-items-from-the-powershell-gallery"></a>從 PowerShell Gallery 下載項目

從 PowerShell Gallery 下載項目時，建議使用下列程序︰

### <a name="inspect"></a>檢查

若要下載資源庫中的項目來進行檢查，請執行 [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) 或 [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334) Cmdlet (視項目類型而定)。 這可讓您在本機儲存項目，而不需要安裝它，並且檢查項目內容。 請記得手動刪除儲存的項目。

這些項目有一部分是由 Microsoft 所撰寫，其他則是由 PowerShell 社群所撰寫。 Microsoft 建議您檢閱這個組件庫上項目的內容和程式碼，再進行安裝。

如果您發現可能未以誠信方式發行的項目，請按一下該項目之頁面上的 [檢舉不當使用]。

### <a name="install"></a>安裝

若要安裝資源庫中的項目來進行使用，請執行 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 或 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) Cmdlet (視項目類型而定)。

[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 預設會將模組安裝至 `$env:ProgramFiles\WindowsPowerShell\Modules`。 這需要系統管理員帳戶。 如果您新增 `-Scope
CurrentUser` 參數，模組就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。

[Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) 預設會將指令碼安裝至 `$env:ProgramFiles\WindowsPowerShell\Scripts`。 這需要系統管理員帳戶。 如果您新增 `-Scope
CurrentUser` 參數，指令碼就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。

[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 和 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) 預設會安裝項目的最新版本。 若要安裝項目的舊版本，請新增 `-RequiredVersion` 參數。

### <a name="deploy"></a>在客體叢集部署

若要將項目從 PowerShell Gallery 部署至 Azure 自動化，請按一下項目詳細資料頁面上的 [Deploy to Azure Automation] \(部署至 Azure 自動化)。 會將您重新導向至使用 Azure 帳戶認證所登入的 Azure 管理入口網站。 請注意，部署包含相依性的項目時會將所有相依性部署至 Azure 自動化。 將 **AzureAutomationNotSupported** 標記新增至項目中繼資料，即可停用 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕。

若要深入了解 Azure 自動化，請參閱 [Azure 自動化網站](http://azure.microsoft.com/services/automation/)。

## <a name="updating-items-from-the-powershell-gallery"></a>更新 PowerShell Gallery 中的項目

若要更新從 PowerShell Gallery 安裝的項目，請執行 [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) 或 [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787) Cmdlet。 如果執行時未包含任何其他參數，則 [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) 會嘗試更新透過執行 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 所安裝的每個模組。
若要選擇性地更新模組，請新增 `-Name` 參數。

同樣地，如果執行時未包含任何其他參數，則 [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787) 也會嘗試更新透過執行 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) 所安裝的每個指令碼。
若要選擇性地更新指令碼，請新增 `-Name` 參數。

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>列出您已從 PowerShell Gallery 安裝的項目

若要找出您已從 PowerShell 資源庫安裝的模組，請執行 [Get-InstalledModule](https://go.microsoft.com/fwlink/?LinkId=526863) Cmdlet。 這個命令會列出系統上直接從 PowerShell Gallery 安裝的所有模組。

同樣地，若要找出您已從 PowerShell 資源庫安裝的指令碼，請執行 [Get-InstalledScript](https://go.microsoft.com/fwlink/?LinkId=619790) Cmdlet。 這個命令會列出系統上直接從 PowerShell Gallery 安裝的所有指令碼。