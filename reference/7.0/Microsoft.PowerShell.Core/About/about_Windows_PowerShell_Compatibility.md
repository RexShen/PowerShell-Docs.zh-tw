---
description: 描述 PowerShell 7 的 Windows PowerShell 相容性功能。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_Compatibility
ms.openlocfilehash: 777dab1cce4329958337a7c0857b0d712b4387a9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207476"
---
# <a name="about-windows-powershell-compatibility"></a>關於 Windows PowerShell 相容性

## <a name="short-description"></a>簡短描述

描述 PowerShell 7 的 Windows PowerShell 相容性功能。

## <a name="long-description"></a>詳細描述

除非模組資訊清單指出模組與 PowerShell Core 相容，否則 `%windir%\system32\WindowsPowerShell\v1.0\Modules` 會 Windows PowerShell 相容性功能，在背景 Windows PowerShell 5.1 進程中載入資料夾中的模組。

### <a name="using-the-compatibility-feature"></a>使用相容性功能

使用 Windows PowerShell 相容性功能匯入第一個模組時，PowerShell 會建立名為的遠端會話， `WinPSCompatSession` 該會話會在背景 Windows PowerShell 5.1 進程中執行。 當相容性功能匯入第一個模組時，就會建立此進程。 移除最後一個此類別模組時， (使用 `Remove-Module`) 或 PowerShell 進程結束時，會關閉此進程。

會話中載入的模組 `WinPSCompatSession` 會透過隱含遠端處理來使用，並反映到目前的 PowerShell 會話。 這與用於 PowerShell 作業的傳輸方法相同。

將模組匯入 `WinPSCompatSession` 會話時，隱含的遠端會在使用者的目錄中產生 proxy 模組， `$env:Temp` 並將此 proxy 模組匯入到目前的 PowerShell 會話。 這可讓 PowerShell 偵測模組是使用 Windows PowerShell 相容性功能載入的。

一旦建立會話之後，就可以將它用於無法在已還原序列化的物件上正常運作的作業。 整個管線會在 Windows PowerShell 中執行，而且只會傳回最終結果。 例如：

```powershell
$s = Get-PSSession -Name WinPSCompatSession
Invoke-Command -Session $s -ScriptBlock {
  "Running in Windows PowerShell version $($PSVersionTable.PSVersion)"
}
```

您可以透過兩種方式叫用相容性功能：

- 使用 **UseWindowsPowerShell** 參數匯入模組以明確地進行

   ```powershell
   Import-Module -Name ScheduledTasks -UseWindowsPowerShell
   ```

- 依模組名稱、路徑或自動載入功能透過命令探索，以隱含方式匯入 Windows PowerShell 模組。

   ```powershell
   Import-Module -Name ServerManager
   Get-AppLockerPolicy -Local
   ```

   如果尚未載入，則會在您執行時自動載入 AppLocker 模組  `Get-AppLockerPolicy` 。

Windows PowerShell 相容性會封鎖載入 `WindowsPowerShellCompatibilityModuleDenyList` PowerShell 設定檔中設定所列出的模組。

此設定的預設值為：

```json
"WindowsPowerShellCompatibilityModuleDenyList":  [
   "PSScheduledJob","BestPractices","UpdateServices"
]
```

### <a name="managing-implicit-module-loading"></a>管理隱含模組載入

若要停用 Windows PowerShell 相容性功能的隱含匯入行為，請使用 `DisableImplicitWinCompat` PowerShell 設定檔中的設定。 此設定可新增至檔案 `powershell.config.json` 。 如需詳細資訊，請參閱 [about_powershell_config](about_powershell_config.md)。

這個範例示範如何建立設定檔，以停用 Windows PowerShell 相容性的隱含模組載入功能。

```powershell
$ConfigPath = "$PSHOME\DisableWinCompat.powershell.config.json"
$ConfigJSON = ConvertTo-Json -InputObject @{
  "DisableImplicitWinCompat" = $true
  "Microsoft.PowerShell:ExecutionPolicy" = "RemoteSigned"
}
$ConfigJSON | Out-File -Force $ConfigPath
pwsh -settingsFile $ConfigPath
```

如需有關模組相容性的最新資訊，請參閱 [PowerShell 7 模組相容性](https://aka.ms/PSModuleCompat) 清單。

### <a name="managing-cmdlet-clobbering"></a>管理 Cmdlet 阻礙

Windows PowerShell 相容性功能會使用隱含的遠端處理功能，在相容性模式中載入模組。 結果是模組所匯出的命令優先于目前 PowerShell 7 會話中相同名稱的命令。 在 PowerShell 7.0.0 版中，這包含了 PowerShell 隨附的核心模組。

在 PowerShell 7.1 中，行為已變更，因此不會事情下列核心 PowerShell 模組：

- ConsoleHost
- Microsoft.PowerShell.Diagnostics
- Microsoft.PowerShell.Host
- Microsoft.PowerShell.Management
- Microsoft.PowerShell.Security
- Microsoft.PowerShell.Utility
- Microsoft.WSMan.Management

PowerShell 7.1 也加入了列出其他模組的功能，這些模組不應由相容性模式事情。

您可以將 `WindowsPowerShellCompatibilityNoClobberModuleList` 設定新增至 PowerShell 設定檔。 這項設定的值是以逗號分隔的模組名稱清單。 此設定的預設值為：

```json
"WindowsPowerShellCompatibilityNoClobberModuleList": [ ]
```

## <a name="limitations"></a>限制

Windows PowerShell 相容性功能：

1. 只能在 Windows 電腦本機上運作
1. 需要 Windows PowerShell 5。1
1. 在序列化的 Cmdlet 參數和傳回值上運作，而不是在即時物件上操作
1. 匯入 Windows PowerShell 遠端會話的所有模組都會共用相同的運行時。

## <a name="keywords"></a>關鍵字

about_Windows_PowerShell_Compatibility

## <a name="see-also"></a>另請參閱

[about_Modules](about_Modules.md)

[Import-Module](xref:Microsoft.PowerShell.Core.Import-Module)
