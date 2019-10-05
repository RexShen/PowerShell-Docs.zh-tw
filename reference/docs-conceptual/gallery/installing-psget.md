---
ms.date: 09/19/2019
contributor: manikb
keywords: 資源庫,powershell,cmdlet,psget
title: 安裝 PowerShellGet
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328199"
---
# <a name="installing-powershellget"></a>安裝 PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet 是下列版本中的內建模組

- [Windows 10](https://www.microsoft.com/windows) 或更新版本
- [Windows Server 2016](/windows-server/windows-server) 或更新版本
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 或更新版本
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a>從 PowerShell 資源庫取的最新版本

更新 **PowerShellGet** 之前，一律必須先安裝最新的 **NuGet** 提供者。 從已提高權限的 PowerShell 工作階段執行下列命令。

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>針對具有 PowerShell 5.0 (或更新版本) 的系統，您可以安裝最新的 PowerShellGet

若要在 Windows 10、Windows Server 2016、任何已安裝 WMF 5.0 或 5.1 的系統或任何具有 PowerShell 6 的系統上安裝 PowerShellGet，請從已提升權限的 PowerShell 工作階段執行下列命令。

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

使用 `Update-Module` 來取得較新版本。

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a>適用於執行 PowerShell 3.0 或 PowerShell 4.0 的電腦

這些指示適用於已安裝 **PackageManagement Preview** 的電腦，或未安裝任何版本 **PowerShellGet** 的電腦。

`Save-Module` Cmdlet 用於這兩組指令。 `Save-Module` 從已註冊的存放庫下載並儲存模組和任何相依性。 最新版本模組會儲存至本機電腦上的指定路徑，但不會安裝。 如需詳細資訊，請參閱 [Save-Module](/powershell/module/PowershellGet/Save-Module)。

#### <a name="computers-with-the-packagemanagement-preview-installed"></a>已安裝 PackageManagement Preview 的電腦

1. 從 PowerShell 工作階段使用 `Save-Module` 將模組儲存至本機目錄。

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. 確定任何其他處理序都未載入 **PowerShellGet** 和 **PackageManagment** 模組。
1. 刪除資料夾的內容：`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 與 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`。
1. 使用已提升的權限重新開啟 PowerShell 主控台，然後執行下列命令。

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a>不具有 PowerShellGet 的電腦

如果電腦沒有安裝任何版本的 **PowerShellGet**，則需要安裝具有 **PowerShellGet** 的電腦，才能下載模組。

1. 從已安裝 **PowerShellGet** 的電腦上，使用 `Save-Module` 下載目前版本的 **PowerShellGet**。 會下載兩個資料夾：**PowerShellGet** 和 **PackageManagement**。 每個資料夾都包含具有版本號碼的子資料夾。

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. 將 **PowerShellGet** 和 **PackageManagement** 資料夾複製到未安裝 **PowerShellGet** 的電腦。

   目的地目錄為：`$env:ProgramFiles\WindowsPowerShell\Modules`
