---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,psgallery,資源庫
title: 手動下載套件
ms.openlocfilehash: e562f5b94b4d2caa7d31269a324e417d1a9e844a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278698"
---
# <a name="manual-package-download"></a>手動下載套件

Powershell 資源庫支援直接從網站下載套件，而不需要使用 PowerShellGet Cmdlet。 您可以將任何套件下載為 NuGet 套件 (`.nupkg`) 檔案，然後複製到內部存放庫。

> [!NOTE]
> 手動下載套件**不會**取代 `Install-Module` Cmdlet。
> 下載套件不會安裝模組或指令碼。 下載的 NuGet 套件中不會包含相依性。 下列指示僅供參考。

## <a name="using-manual-download-to-acquire-a-package"></a>使用手動下載來取得套件

每個頁面會有 [手動下載] 連結，如下所示：

![手動下載](media/manual-download/packagedisplaypagewithpseditions.png)

若要手動下載，請按一下 [Download the raw nupkg file] \(下載原始 nupkg 檔案\)  。 這會將套件複本複製到您瀏覽器中的下載資料夾 (名為 `<name>.<version>.nupkg`)。

NuGet 套件是 ZIP 封存以及含有套件內容相關資訊的額外檔案。 某些瀏覽器 (例如 Internet Explorer) 會自動以 `.zip` 取代 `.nupkg` 副檔名。 若要展開套件，請視需要將 `.nupkg` 檔案重新命名為 `.zip`，然後將內容解壓縮至本機資料夾。

NuGet 套件檔案包含不屬於原始封裝程式碼的下列 **NuGet 特定元素**：

- 名為 `_rels` 的資料夾 - 包含列出相依性的 `.rels` 檔案
- 名為 `package` 的資料夾 - 包含 NuGet 特定資料
- 名為 `[Content_Types].xml` 的檔案 - 描述 PowerShellGet 等延伸模組如何與 NuGet 搭配運作
- 名為 `<name>.nuspec` 的檔案 - 包含大量中繼資料

## <a name="installing-powershell-modules-from-a-nuget-package"></a>從 NuGet 套件安裝 PowerShell 模組

> [!NOTE]
> 這些指示**不會**提供與執行 `Install-Module` 相同的結果。 這些指示符合最低需求。 它們不會取代 `Install-Module`。
> `Install-Module` 執行的一些步驟並未包含在內。

最簡單的方法是從資料夾中移除 NuGet 特定項目。 移除那些元素會留下套件作者所建立的 PowerShell 程式碼。
針對 NuGet 特定元素清單，請參閱[使用手動下載來取得套件](#using-manual-download-to-acquire-a-package)。

步驟如下：

1. 將從網際網路下載的 NuGet 套件 (`.nupkg`) 檔案解除封鎖，例如使用 `Unblock-File -Path C:\Downloads\module.nupkg` Cmdlet。
2. 將 NuGet 套件內容解壓縮至本機資料夾。
2. 從資料夾中刪除 NuGet 特定項目。
3. 重新命名資料夾。 預設資料夾名稱通常是 `<name>.<version>`。 如果模組標記為發行前版本，則版本可以包含 `-prerelease`。 請將資料夾重新命名為只有模組名稱。 例如，`azurerm.storage.5.0.4-preview` 會成為 `azurerm.storage`。
4. 將資料夾複製到 `$env:PSModulePath value` 的其中一個資料夾。 `$env:PSModulePath` 是以分號分隔的路徑集合，PowerShell 會在此集合中尋找模組。

> [!IMPORTANT]
> 手動下載不會包含模組所需的任何相依性。 如果套件具有相依性，則必須在系統上加以安裝，此模組才能正常運作。 PowerShell 資源庫會顯示套件所需的所有相依性。

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>從 NuGet 套件安裝 PowerShell 指令碼

> [!NOTE]
> 這些指示**不會**提供與執行 `Install-Script` 相同的結果。 這些指示符合最低需求。 它們不會取代 `Install-Script`。

最簡單的方法是解壓縮 NuGet 套件，然後直接使用指令碼。

步驟如下：

1. 將從網際網路下載的 NuGet 套件 (`.nupkg`) 檔案解除封鎖，例如使用 `Unblock-File -Path C:\Downloads\package.nupkg` Cmdlet。
2. 解壓縮 NuGet 套件內容。
2. 資料夾中的 `.PS1` 檔案可直接從此位置使用。
3. 您可以刪除此資料夾中的 NuGet 特定項目。

針對 NuGet 特定元素清單，請參閱[使用手動下載來取得套件](#using-manual-download-to-acquire-a-package)。

> [!IMPORTANT]
> 手動下載不會包含模組所需的任何相依性。 如果套件具有相依性，則必須在系統上加以安裝，此模組才能正常運作。 PowerShell 資源庫會顯示套件所需的所有相依性。
