---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
title: WMF 5.x 版本資訊
ms.openlocfilehash: 3fc712dbcbe184c60ae248b260c8f6800f111fdd
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416497"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Windows Management Framework (WMF) 5.x 版本資訊

## <a name="wmf-50-changes"></a>WMF 5.0 變更

- PowerShell 5.0 會新增新的結構化**資訊**串流
- 對 DSC 的改進包括四個新 DSC 資源：
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- 已新增 Just Enough Administration，可透過 PowerShell 遠端來啟用以角色為基礎的系統管理
- PowerShell 5.0 會擴充語言以包含使用者定義的類別和列舉
- 已改進 PowerShell ISE 中的偵錯功能，並新增了遠端偵錯
- 已新增 PowerShellGet 和 PackageManagement 模組
- 已增強 PowerShell 指令碼記錄和文字記錄
- 新增密碼編譯訊息語法 Cmdlet
- WMF 5.0 包含適用於 Windows 的 NetworkSwitchManager 模組
- 已新增 Microsoft.PowerShell.ODataUtils 模組
- 已新增支援軟體清查記錄 (SIL)
- 提供新的或更新的 Cmdlet 來回應使用者要求和問題

## <a name="wmf-51-changes"></a>WMF 5.1 變更

WMF 5.1 包含已搭配 Windows Server 2016 發行的 PowerShell、WMI、WinRM，以及軟體清查記錄 (SIL) 元件。 WMF 5.1 可以安裝於 Windows 7、Windows 8.1、Windows Server 2008 R2、2012 及 2012 R2 上，並提供數個對 WMF 5.0 的改進，包括：

- 新的 Cmdlet
- PowerShellGet 改善功能包括強制執行已簽署的模組，以及安裝 JEA 模組
- PackageManagement 新增對容器、CBS 安裝、以執行檔為基礎的安裝、封包封裝的支援
- DSC 和 PowerShell 類別的偵錯改善
- 安全性增強功能包括強制執行來自提取伺服器的目錄簽署模組，以及在使用 PowerShellGet Cmdlet 時加以強制執行
- 回應數個使用者要求和問題

> [!IMPORTANT]
> 在 Windows Server 2008 或 Windows 7 上安裝 WMF 5.1 之前，請先確認未安裝 WMF 3.0。 如需詳細資訊，請參閱 [Windows Server 2008 R2 SP1 和 Windows 7 SP1 的 WMF 5.1 必要條件](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1)。

## <a name="powershell-editions"></a>PowerShell 版本

從 5.1 版開始，PowerShell 適用於代表各種功能集及平台相容性的不同版本。

- **Desktop Edition：** 建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行的 PowerShell 指令碼和模組目標版本相容相容。
- **Core Edition：** 建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行的 PowerShell 指令碼和模組目標版本相容。

### <a name="learn-more-about-using-powershell-editions"></a>深入了解使用 PowerShell 版本

- [使用 PSVersionTable 來判斷執行的 PowerShell 版本](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [使用 PSEdition 參數並依據 CompatiblePSEditions 篩選 Get-Module 結果](/powershell/module/microsoft.powershell.core/get-module)
- [只有在相容的 PowerShell 版本上執行才會執行指令碼](/powershell/scripting/gallery/concepts/script-psedition-support)
- [宣告特定 PowerShell 版本的模組相容性](/powershell/scripting/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>模組分析快取

從 WMF 5.1 開始，PowerShell 可以控制快取模組資料所用的檔案，例如匯出的命令。

此快取預設儲存在 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 檔案中。 快取一般在啟動同時搜尋命令時讀取，並在模組匯入一段時間後寫入背景執行緒。

若要變更快取的預設位置，請先設定環境變數 `$env:PSModuleAnalysisCachePath` 再啟動 PowerShell。 此環境變數的變更只會影響子處理程序。 該值應該命名 PowerShell 有權建立和寫入檔案的完整路徑 (包括檔名)。 若要停用檔案快取，請將此值設定於無效的位置，例如︰

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

這會將路徑設定到無效的裝置。 如果 PowerShell 無法寫入該路徑，就不會傳回任何錯誤，但您可以藉由使用追蹤查看錯誤報告︰

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

寫出快取時，PowerShell 會檢查確認模組已不存在，避免不必要的大型快取。 有時候不需要這些檢查，在此情況下，您可以透過設定下列項目關閉這些檢查：

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

此環境變數設定會立即在目前的程序中生效。

## <a name="specifying-module-version"></a>指定模組版本

在 WMF 5.1 中，`using module` 與 PowerShell 中其他模組相關的語法結構表現一致。
以往，您無法指定特定的模組版本；如果有多個版本存在，這會導致錯誤。

在 WMF 5.1 中：

- 您可以使用 [ModuleSpecification 建構函式 (雜湊表)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)。

  此雜湊表與 `Get-Module -FullyQualifiedName` 的格式相同。

  **範例：** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- 如果模組有多個版本，PowerShell 會使用與 `Import-Module` **相同的解析邏輯**，不傳回錯誤，和 `Import-Module` 及 `Import-DscResource` 的行為一樣。

## <a name="improvements-to-pester"></a>Pester 的改善

在 WMF 5.1 中，PowerShell 隨附的 Pester 版本已從 3.3.5 更新為 3.4.0。
此更新讓 Pester 在 Nano 伺服器上有更好的表現。

您可以藉由檢查 GitHub 存放庫中的 [ChangeLog.md](https://github.com/pester/Pester/blob/master/CHANGELOG.md) 檔案，來檢閱 Pester 中的變更。
