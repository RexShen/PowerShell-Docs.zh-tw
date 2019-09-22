---
ms.date: 06/12/2017
contributor: manikb
keywords: 資源庫,powershell,cmdlet,psget
title: 安裝 PowerShellGet
ms.openlocfilehash: a0ef46a9ee4bbf668a58067256d098967bde48c5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143601"
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

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a>針對執行 PowerShell 3 或 PowerShell 4 且已安裝 PackageManagement 的系統

1. 從已提升權限的 PowerShell 工作階段 `Save-Module` 將模組儲存至本機目錄

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. 確定任何其他處理序都未載入 **PowerShellGet** 和 **PackageManagment** 模組。
1. 刪除資料夾的內容：`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 與 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`。
1. 使用已提升的權限重新開啟 PowerShell 主控台，然後執行下列命令。

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
