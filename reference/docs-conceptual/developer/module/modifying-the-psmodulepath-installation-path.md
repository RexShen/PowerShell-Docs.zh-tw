---
ms.date: 09/13/2016
ms.topic: reference
title: 修改 PSModulePath 安裝路徑
description: 修改 PSModulePath 安裝路徑
ms.openlocfilehash: b802492bf9b49e8165e296817e3f80b9ae8265a6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92661942"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>修改 PSModulePath 安裝路徑

`PSModulePath`環境變數會儲存安裝在磁片上的模組位置路徑。 當使用者未指定模組的完整路徑時，PowerShell 會使用此變數來尋找模組。 此變數中的路徑會依照其出現的順序來搜尋。

當 PowerShell 啟動時， `PSModulePath` 會建立為具有下列預設值的系統內容變數： `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` 在 Windows、 `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` Linux 或 Mac 上，以及 `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` 用於 Windows PowerShell。

> [!NOTE]
> 使用者專屬的 **CurrentUser** 位置是 `WindowsPowerShell\Modules` 位於您使用者設定檔中檔位置的資料夾。 該位置的特定路徑會因 Windows 版本而異，以及您是否正在使用資料夾重新導向。 根據預設，在 Windows 10 上，該位置為 `$HOME\Documents\WindowsPowerShell\Modules` 。

## <a name="to-view-the-psmodulepath-variable"></a>若要查看 PSModulePath 變數

若要查看變數中指定的路徑 `PSModulePath` ，請輸入下列命令：

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>若要將位置新增至 PSModulePath 變數

若要將路徑新增至此變數，請使用下列其中一種方法：

- 若要新增僅適用于目前會話的暫時值，請在命令列執行下列命令：

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- 若要新增會話開啟時可用的持續值，請將上述命令新增至 PowerShell 設定檔檔 (`$PROFILE`) # A0

  如需設定檔的詳細資訊，請參閱 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)。

- 若要將持續性變數新增至登錄，請 `PSModulePath` 使用 [ **系統屬性** ] 對話方塊中的環境變數編輯器，建立名為的新使用者環境變數。

- 若要使用腳本新增持續性變數，請在[system.object](/dotnet/api/system.environment)類別上使用 .Net 方法[SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) 。 例如，下列腳本會將路徑新增 `C:\Program Files\Fabrikam\Module` 至 `PSModulePath` 電腦的環境變數值。 若要將路徑新增至使用者 `PSModulePath` 環境變數，請將目標設定為 "user"。

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>從 PSModulePath 中移除位置

您可以使用類似的方法，從變數移除路徑：例如， `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` 將會從目前的會話移除 **c:\ModulePath** 路徑。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)

[about_Modules](/powershell/module/microsoft.powershell.core/about/about_modules)
