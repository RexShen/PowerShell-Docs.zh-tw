---
ms.date: 09/19/2019
title: 安裝 PowerShellGet
description: 此文章說明如何在各種 PowerShell 版本中安裝 PowerShellGet 模組。
ms.openlocfilehash: 06ec331446849784bb8464912fbce0e5a940823f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662142"
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
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>針對具有 PowerShell 5.0 (或更新版本) 的系統，您可以安裝最新的 PowerShellGet

若要在 Windows 10、Windows Server 2016、任何已安裝 WMF 5.0 或 5.1 的系統或任何具有 PowerShell 6 的系統上安裝 PowerShellGet，請從已提升權限的 PowerShell 工作階段執行下列命令。

```powershell
Install-Module -Name PowerShellGet -Force
```

使用 `Update-Module` 來取得較新版本。

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a>適用於執行 PowerShell 3.0 或 PowerShell 4.0 的電腦

這些指示適用於已安裝 **PackageManagement Preview** 的電腦，或未安裝任何版本 **PowerShellGet** 的電腦。

`Save-Module` Cmdlet 用於這兩組指令。 `Save-Module` 從已註冊的存放庫下載並儲存模組和任何相依性。 最新版本模組會儲存至本機電腦上的指定路徑，但不會安裝。 若要將模組安裝在 PowerShell 3.0 或 4.0 中，請將該模組的預存資料夾複製到 `$env:ProgramFiles\WindowsPowerShell\Modules`。

如需詳細資訊，請參閱 [Save-Module](/powershell/module/PowershellGet/Save-Module)。

> [!NOTE]
> PowerShell 3.0 與 PowerShell 4.0 僅支援一個模組版本。 自 PowerShell 5.0 起，模組會安裝在 `<modulename>\<version>` 中。 這會允許並存安裝多個版本。 在使用 `Save-Module` 下載模組後，您必須從 `<modulename>\<version>` 將檔案複製到目標電腦上的 `<modulename>` 資料夾，如下列說明所示。

#### <a name="preparatory-step-on-computers-running-powershell-30"></a>執行 PowerShell 3.0 的電腦上準備步驟

下列各節中的說明會在 `$env:ProgramFiles\WindowsPowerShell\Modules` 目錄中安裝模組。
在 PowerShell 3.0 中，根據預設此目錄不會列在 `$env:PSModulePath` 中，因此需要新增此目錄，才能自動載入模組。

開啟提升權限的 PowerShell 工作階段，並執行下列命令 (這會在未來的工作階段中生效)：

```powershell
[Environment]::SetEnvironmentVariable(
  'PSModulePath',
  ((([Environment]::GetEnvironmentVariable('PSModulePath', 'Machine') -split ';') + "$env:ProgramFiles\WindowsPowerShell\Modules") -join ';'),
  'Machine'
)
```

#### <a name="computers-with-the-packagemanagement-preview-installed"></a>已安裝 PackageManagement Preview 的電腦

> [!NOTE]
> PackageManagement Preview 是一個可下載的元件，其可供在 PowerShell 版本 3 和 4 中使用 PowerShellGet，但其已不再提供使用。
> 若要測試是否已在指定電腦上安裝該項目，請執行 `Get-Module -ListAvailable PowerShellGet`。

1. 在 PowerShell 工作階段中，使用 `Save-Module` 來下載 **PowerShellGet** 的目前版本。 會下載兩個資料夾： **PowerShellGet** 和 **PackageManagement** 。 每個資料夾都包含具有版本號碼的子資料夾。

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. 確定任何其他處理序都未載入 **PowerShellGet** 和 **PackageManagment** 模組。

1. 使用已提升的權限重新開啟 PowerShell 主控台，並執行下列命令。

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     Remove-Item $targetDir\* -Recurse -Force
     Copy-Item C:\LocalFolder\$_\*\* $targetDir\ -Recurse -Force
   }
   ```

#### <a name="computers-without-powershellget"></a>不具有 PowerShellGet 的電腦

針對沒有安裝任何 **PowerShellGet** 版本的電腦 (使用 `Get-Module -ListAvailable PowerShellGet` 測試)，將需要已安裝 **PowerShellGet** 的電腦來下載模組。

1. 從已安裝 **PowerShellGet** 的電腦上，使用 `Save-Module` 下載目前版本的 **PowerShellGet** 。 會下載兩個資料夾： **PowerShellGet** 和 **PackageManagement** 。 每個資料夾都包含具有版本號碼的子資料夾。

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. 將 **PowerShellGet** 和 **PackageManagement** 資料夾中的個別 `<version>` 子資料夾分別複製到沒有安裝 **PowerShellGet** 電腦中的 `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 和 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` 資料夾，這項操作需要提升權限的工作階段。

1. 例如，若可存取其他電腦 (例如 `ws1`) 上的下載資料夾，請透過 UNC 路徑 (例如 `\\ws1\C$\LocalFolder`) 在目標電腦上開啟提升權限的 PowerShell 主控台，並執行下列命令：

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     $null = New-Item -Type Directory -Force $targetDir
     $fromComputer = 'ws1'  # Specify the name of the other computer here.
     Copy-Item \\$fromComputer\C$\LocalFolder\$_\*\* $targetDir -Recurse -Force
     if (-not (Get-ChildItem $targetDir)) { Throw "Copying failed." }
   }
   ```
