---
description: 不同的 PowerShell 版本會在不同的基礎執行時間上執行。
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_editions?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Editions
ms.openlocfilehash: 63ee3fffb4d7594920fa7052aecee99aa01ddc7d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207284"
---
# <a name="about-powershell-editions"></a>關於 PowerShell 版本

## <a name="short-description"></a>簡短描述
不同的 PowerShell 版本會在不同的基礎執行時間上執行。

## <a name="long-description"></a>完整描述

從 PowerShell 5.1 開始，有多個 PowerShell *版本* 可在不同的 .net 執行時間上執行。 從 PowerShell 6.2 版來的 PowerShell 有兩種版本：

- 在 .NET Framework 上執行的 **桌面** 。 PowerShell 4 和以下版本，以及 Windows 桌面、Windows Server、Windows Server Core 和大部分其他 Windows 作業系統等完整功能的 Windows 版本上的 PowerShell 5.1 都是 Desktop edition。
  這是原始的 PowerShell 版本。
- **Core** ，可在 .net Core 上執行。 PowerShell 6.0 （含）以上版本，以及 PowerShell 5.1，在某些降低使用量的 Windows 版本（例如 Windows Nano Server 和 Windows IoT）上無法使用 .NET Framework。

因為 PowerShell 的版本對應至其 .NET 執行時間，所以它是 .NET API 和 PowerShell 模組相容性的主要指標。某些 .NET Api、類型或方法在 .NET 執行時間中無法使用，而這會影響依賴它們的 PowerShell 腳本和模組。

## <a name="the-psedition-automatic-variable"></a>`$PSEdition`自動變數

在 PowerShell 5.1 和更新版本中，您可以使用自動變數找出您正在 `$PSEdition` 執行的版本：

```powershell
$PSEdition
```

```Output
Core
```

在 PowerShell 4 和以下的中，此變數不存在。 `$PSEdition` null 應該視為具有值的相同值 `Desktop` 。

### <a name="edition-in-psversiontable"></a>版 `$PSVersionTable`

`$PSVersionTable`自動變數在 PowerShell 5.1 和更新版本中也有版本資訊：

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      6.2.0-rc.1
PSEdition                      Core           # <-- Edition information
GitCommitId                    6.2.0-rc.1
OS                             Microsoft Windows 10.0.18865
Platform                       Win32NT
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
WSManStackVersion              3.0
```

`PSEdition`欄位將具有與自動變數相同的值 `$PSEdition` 。

## <a name="the-compatiblepseditions-module-manifest-field"></a>`CompatiblePSEditions`模組資訊清單欄位

PowerShell 模組可以使用模組資訊清單的欄位，宣告與它們相容的 PowerShell 版本 `CompatiblePSEditions` 。

例如，宣告與 `Desktop` 和 PowerShell 版本相容的模組資訊清單 `Core` ：

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop', 'Core')
}
```

只有相容性的模組資訊清單範例 `Desktop` ：

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop')
}
```

略 `CompatiblePSEditions` 過模組資訊清單中的欄位將會有與將它設定為相同的效果 `Desktop` ，因為引進這個欄位之前建立的模組是針對此版本隱含撰寫的。

針對未隨附于 Windows 的模組 (例如您從資源庫) 撰寫或安裝的模組，此欄位僅供參考。PowerShell 不會根據欄位變更行為 `CompatiblePSEditions` ，但會對 `PSModuleInfo` 您自己的邏輯) 所傳回的物件 (公開它 `Get-Module` ：

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion '5.1'
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

> [!NOTE]
> `CompatiblePSEditions`模組欄位只與 PowerShell 5.1 和更新版本相容。
> 包含此欄位將會導致模組與 PowerShell 4 和以下模組不相容。
> 因為欄位純粹是資訊，所以可以在稍後的 PowerShell 版本中安全地省略。

在 PowerShell 6.1 中， `Get-Module -ListAvailable` 已更新其格式器以顯示每個模組的版本相容性：

```PowerShell
Get-Module -ListAvailable
```

```Output

    Directory: C:\Users\me\Documents\PowerShell\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Script     1.4.0      Az                                  Core,Desk
Script     1.3.1      Az.Accounts                         Core,Desk {Disable-AzDataCollection, Disable-AzContextAutosave, E...
Script     1.0.1      Az.Aks                              Core,Desk {Get-AzAks, New-AzAks, Remove-AzAks, Import-AzAksCreden...

...

Script     4.4.0      Pester                              Desk      {Describe, Context, It, Should...}
Script     1.18.0     PSScriptAnalyzer                    Desk      {Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer, Invoke-...
Script     1.0.0      WindowsCompatibility                Core      {Initialize-WinSession, Add-WinFunction, Invoke-WinComm...

```

## <a name="edition-compatibility-for-modules-that-ship-as-part-of-windows"></a>版本相容于 Windows 隨附的模組

如果模組是 Windows (的一部分，或安裝為角色或功能) 的一部分，則 PowerShell 6.1 和更新版本會 `CompatiblePSEditions` 以不同方式來處理欄位。 這類別模組可在 Windows PowerShell 系統模組目錄 () 中找到 `%windir%\System\WindowsPowerShell\v1.0\Modules` 。

針對從這個目錄載入或找到的模組，PowerShell 6.1 和 `CompatiblePSEditions` 更新版本會使用欄位來判斷模組是否與目前的會話相容，並據以運作。

`Import-Module`使用時，不會匯入不含 in 的模組， `Core` `CompatiblePSEditions` 而且會顯示錯誤：

```powershell
Import-Module BitsTransfer
```

```Output
Import-Module : Module 'C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1' does not support current PowerShell edition 'Core'. Its supported editions are 'Desktop'. Use 'Import-Module -SkipEditionCheck' to ignore the compatibility of this module.
At line:1 char:1
+ Import-Module BitsTransfer
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : ResourceUnavailable: (C:\WINDOWS\system32\u2026r\BitsTransfer.psd1:String) [Import-Module], InvalidOperationException
+ FullyQualifiedErrorId : Modules_PSEditionNotSupported,Microsoft.PowerShell.Commands.ImportModuleCommand
```

`Get-Module -ListAvailable`使用時，不會顯示不含 `Core` in 的模組 `CompatiblePSEditions` ：

```powershell
Get-Module -ListAvailable BitsTransfer
```

```Output
# No output
```

在這兩種情況下， `-SkipEditionCheck` switch 參數都可以用來覆寫此行為：

```powershell
Get-Module -ListAvailable -SkipEditionCheck BitsTransfer
```

```Output

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.0.0    BitsTransfer                        Desk      {Add-BitsFile, Complete-BitsTransfer, Get-BitsTransfer,...

```

> [!WARNING]
> `Import-Module -SkipEditionCheck` 模組的外觀可能會成功，但使用該模組會在稍後遇到不相容的風險。載入模組一開始會成功，稍後命令可能會呼叫不相容的 API，並自發地失敗。

## <a name="authoring-powershell-modules-for-edition-cross-compatibility"></a>撰寫適用于版本的 PowerShell 模組跨相容性

撰寫 PowerShell 模組以將 PowerShell 模組設為目標時 `Desktop` `Core` ，您可以進行一些動作，以確保跨版本的相容性。

唯一確認並持續驗證相容性的唯一方法，就是為您的腳本或模組撰寫測試，並在您需要相容性的所有 PowerShell 版本和版本上執行測試。 建議的測試架構為 [Pester][]。

### <a name="powershell-script"></a>PowerShell 指令碼

PowerShell 是一種語言，在各版本之間的運作方式相同;它是您所使用且受版本相容性影響的 Cmdlet、模組和 .NET Api。

一般而言，在 PowerShell 6.1 和更新版本中運作的腳本將會與 Windows PowerShell 5.1 搭配運作，但有一些例外狀況。

Version 1.18.0 [PSScriptAnalyzer][] 模組具有類似的規則， [`PSUseCompatibleCommands`][] 而且可以 [`PSUseCompatibleTypes`][] 在 PowerShell 腳本中偵測到可能不相容的命令和 .net api 的使用方式。

### <a name="net-assemblies"></a>.NET 組件

如果您要撰寫的二進位模組或模組包含 .NET 元件 (Dll) 從原始程式碼產生，您應該針對 .NET 和 PowerShell API 相容性的編譯時間相容性驗證，以 [.NET Standard][] 和 [powershell 標準][] 進行編譯。

雖然這些程式庫可以在編譯時期檢查某些相容性，但是它們無法攔截版本之間可能的行為差異。 針對這一點，您仍然必須撰寫測試。

## <a name="see-also"></a>另請參閱

- [about_Automatic_Variables](about_Automatic_Variables.md)
- [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module)
- [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module)
- [具有相容 PowerShell 版本的模組](/powershell/scripting/gallery/concepts/module-psedition-support)

[Pester]: https://github.com/pester/Pester/wiki/Pester
[PSScriptAnalyzer]: https://github.com/PowerShell/PSScriptAnalyzer
['PSUseCompatibleCommands']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
['PSUseCompatibleTypes']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
