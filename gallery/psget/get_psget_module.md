---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: 資源庫,powershell,cmdlet,psget
title: 取得 PowerShellGet 模組
ms.openlocfilehash: a392f795d8c065ff881bc6cc113e63a1f18bcb44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
<a name="get-powershellget-module"></a>取得 PowerShellGet 模組
========================

### <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet 是下列版本中的內建模組
- [Windows 10](https://www.microsoft.com/windows/get-windows-10) 或更新版本
- [Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) 或更新版本
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 或更新版本
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

### <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>取得適用於 PowerShell 3.0 和 4.0 版的 PowerShellGet 模組
- [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

### <a name="get-the-latest-version-from-powershell-gallery"></a>從 PowerShell 資源庫取的最新版本

- 更新 PowerShellGet 之前，您應該一律先安裝最新的 Nuget 提供者。 若要這樣做，請在已提升權限的 PowerShell 工作階段中執行下列命令。
```powershell
Install-PackageProvider Nuget –Force
Exit
```

#### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>針對具有 PowerShell 5.0 (或更新版本) 的系統，您可以安裝最新的 PowerShellGet
- 若要在 Windows 10、Windows Server 2016、任何已安裝 WMF 5.0 或 5.1 的系統或任何具有 PowerShell 6 的系統上執行此操作，請從已提升權限的 PowerShell 工作階段執行下列命令。
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- 使用 Update-Module 來取得較新的版本。
```powershell
Update-Module -Name PowerShellGet
Exit
```

#### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a>針對執行 PowerShell 3 或 PowerShell 4 且已安裝 [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 的系統

- 從已提升權限的 PowerShell 工作階段中使用下列 PowerShellGet Cmdlet 將模組儲存至本機目錄

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- 確定在任何其他處理序中未載入 PowerShellGet 和 PackageManagment 模組。
- 刪除 `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 和 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` 資料夾的內容。
- 使用已提升的權限來重新開啟「PS 主控台」，然後執行下列命令。

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
```