---
description: 描述 Windows PowerShell 5.1 中包含的新功能。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/17/2018
online version: https://docs.microsoft.com/powershell/module/?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_5 1
ms.openlocfilehash: 567af048dd137c0287c6eba4ccc42a77055c0c92
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208740"
---
# <a name="about_windows_powershell_51"></a>about_Windows_PowerShell_5 1

## <a name="short-description"></a>簡短描述

描述 Windows PowerShell 5.1 中包含的新功能。

## <a name="long-description"></a>詳細描述

Windows PowerShell 5.1 包含大量的新功能，可延伸其用途、改善其可用性，並可讓您更輕鬆且全面地控制及管理 Windows 環境。

Windows PowerShell 5.1 與舊版相容。 針對 Windows PowerShell 4.0、Windows PowerShell 3.0 和 Windows PowerShell 2.0 所設計的 Cmdlet、提供者、模組、嵌入式管理單元、腳本、函式及設定檔，通常會在 Windows PowerShell 5.1 的情況下運作，而不會有任何變更。

- 新的 Cmdlet︰本機使用者和群組；Get-ComputerInfo
- PowerShellGet 改善功能包括強制執行已簽署的模組，以及安裝 JEA 模組
- PackageManagement 新增對容器、CBS 安裝、以執行檔為基礎的安裝、封包封裝的支援
- DSC 和 PowerShell 類別的偵錯改善
- 安全性增強功能包括強制執行來自提取伺服器的目錄簽署模組，以及在使用 PowerShellGet Cmdlet 時加以強制執行
- 回應數個使用者要求和問題

預設會在 Windows Server 2016 和 Windows 10 上安裝 Windows PowerShell 5.1。 若要在 Windows Server 2012 R2、Windows 8.1 企業版或 Windows 8.1 Pro 上安裝 Windows PowerShell 5.1，請參閱 [安裝和設定 WMF 5.1](/powershell/scripting/wmf/setup/install-configure)。
安裝 Windows Management Framework 5.1 之前，請務必先閱讀下載詳細資料，並符合所有系統需求。

您也可以在 [Windows PowerShell 的新功能](/powershell/scripting/windows-powershell/whats-new/what-s-new-in-windows-powershell-50)中，閱讀 Windows PowerShell 5.1 的變更。

## <a name="new-scenarios-and-features-in-wmf-51"></a>WMF 5.1 的新案例和功能

> 注意：本資訊尚屬初始版本，後續有可能變更。

### <a name="powershell-editions"></a>PowerShell 版本
從 5.1 版開始，PowerShell 提供代表各種功能集和平台相容性的不同版本。

- **Desktop Edition：** 建置在 .NET Framework 上，並與目標為完整版 Windows (Server Core 和 Windows Desktop 等) 上執行之 PowerShell 版本的指令碼和模組相容。
- **Core Edition：** 建置在 .NET Core 上，並與目標為縮減版 Windows (Nano Server 和 Windows IoT 等) 上執行之 PowerShell 版本的指令碼和模組相容。

**深入了解使用 PowerShell 版本**

- [使用 PSVersionTable 來判斷執行的 PowerShell 版本](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [使用 PSEdition 參數並依據 CompatiblePSEditions 篩選 Get-Module 結果](/powershell/module/microsoft.powershell.core/get-module)
- [只有在相容的 PowerShell 版本上執行才會執行指令碼](/powershell/scripting/gallery/concepts/script-psedition-support)
- [宣告特定 PowerShell 版本的模組相容性](/powershell/scripting/gallery/concepts/module-psedition-support)

### <a name="catalog-cmdlets"></a>類別目錄 Cmdlet

[Microsoft.PowerShell.Security](/previous-versions/windows/powershell-scripting/hh847877(v=wps.640)) 模組中新增了兩個新的 Cmdlet，它們會產生和驗證 Windows 類別目錄檔案。

#### <a name="new-filecatalog"></a>New-FileCatalog

New-FileCatalog 會建立 Windows 類別目錄檔案，供資料夾和檔案集合使用。
此類別目錄檔案包含指定路徑中的所有檔案雜湊。 使用者可以散發資料夾集合以及代表這些資料夾的對應類別目錄檔案。 這項資訊對驗證資料夾在類別目錄建立後是否有任何變更，非常有用。

```
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>]
 [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

支援類別目錄第 1 版和第 2 版。 第 1 版使用 SHA1 雜湊演算法建立檔案雜湊，第 2 版使用 SHA256。 *Windows Server 2008 R2* 或 *Windows 7* 不支援第 2 版的類別目錄。 *Windows 8* 、 *Windows Server 2012* 和更新版本的作業系統，應該使用類別目錄第 2 版。

若要驗證類別目錄檔案 (上例中為 Pester.cat) 的完整性，請使用 [Set-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/set-authenticodesignature) Cmdlet 來加以簽署。

#### <a name="test-filecatalog"></a>Test-FileCatalog

Test-FileCatalog 會驗證代表資料夾集合的類別目錄。

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>]
 [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

此 Cmdlet 會比較所有的檔案雜湊及在 *catalog* 和 *disk* 中找到的相對路徑。 如果檔案雜湊和路徑中偵測到任何不相符的項目，就會傳回 *ValidationFailed* 狀態。 使用者可以使用 *-Detailed* 參數來擷取此資訊的完整內容。 它也會在 *Signature* 屬性中顯示類別目錄的簽署狀態，和呼叫 [Get-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/get-authenticodesignature) Cmdlet 一模一樣。 使用者也可以使用 *-FilesToSkip* 參數，在驗證期間略過任何檔案。

### <a name="module-analysis-cache"></a>模組分析快取

從 WMF 5.1 開始，PowerShell 可以控制快取模組資料所用的檔案，例如匯出的命令。

此快取預設儲存在 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 檔案中。 快取一般在啟動同時搜尋命令時讀取，並在模組匯入一段時間後寫入背景執行緒。

若要變更快取的預設位置，請先設定環境變數 `$env:PSModuleAnalysisCachePath` 再啟動 PowerShell。 此環境變數的變更只會影響子處理程序。 該值應該命名 PowerShell 有權建立和寫入檔案的完整路徑 (包括檔名)。 若要停用檔案快取，請將此值設定於無效的位置，例如︰

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

這會將路徑設定到無效的裝置。 如果 PowerShell 無法寫入該路徑，就不會傳回任何錯誤，但您可以藉由使用追蹤查看錯誤報告︰

```powershell
Trace-Command -PSHost -Name Modules -Expression {
  Import-Module Microsoft.PowerShell.Management -Force
}
```

寫出快取時，PowerShell 會檢查確認模組已不存在，避免不必要的大型快取。 有時候不需要這些檢查，在此情況下，您可以透過設定下列項目關閉這些檢查：

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

此環境變數設定會立即在目前的程序中生效。

### <a name="specifying-module-version"></a>指定模組版本

在 WMF 5.1 中，`using module` 與 PowerShell 中其他模組相關的語法結構表現一致。 以往，您無法指定特定的模組版本；如果有多個版本存在，這會導致錯誤。

在 WMF 5.1 中：

* 您可以使用 [ModuleSpecification 建構函式 (雜湊表)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor)。
  此雜湊表與 `Get-Module -FullyQualifiedName` 的格式相同。

  **範例：** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* 如果模組有多個版本，PowerShell 會使用與 `Import-Module`**相同的解析邏輯** ，不傳回錯誤，和 `Import-Module` 及 `Import-DscResource` 的行為一樣。

### <a name="improvements-to-pester"></a>Pester 的改善

在 WMF 5.1 中，隨附于 PowerShell 的 Pester 版本已從3.3.5 更新為3.4.0，並新增了 GitHub [PR # 484](https://github.com/pester/Pester/pull/484)，可針對 Nano Server 上的 Pester 提供更佳的行為。

您可以調查 ChangeLog.md 檔案來檢視 3.3.5 版到 3.4.0 版之間的變更，位置在：https://github.com/pester/Pester/blob/master/CHANGELOG.md

## <a name="keywords"></a>關鍵 字

Windows PowerShell 5.1 的新功能
