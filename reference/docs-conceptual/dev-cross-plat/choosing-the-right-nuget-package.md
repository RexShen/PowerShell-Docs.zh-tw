---
title: 為 .NET 專案選擇正確的 PowerShell NuGet 套件
description: 除了與每個 PowerShell 版本一同發佈的可執行檔套件之外，PowerShell 小組也在 NuGet 上維護數個可用的套件。 這些套件允許在 .NET 中以 PowerShell 作為 API 平台。
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 39369ed872faa76ad2c41d813da5e0a98cf1c078
ms.sourcegitcommit: d0461273abb6db099c5e784ef00f57fd551be4a6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85795256"
---
# <a name="choosing-the-right-powershell-nuget-package-for-your-net-project"></a>為 .NET 專案選擇正確的 PowerShell NuGet 套件

除了與每個 PowerShell 版本一同發佈的 `pwsh` 可執行檔套件之外，PowerShell 小組也在 [NuGet][] 上維護數個可用的套件。 這些套件允許在 .NET 中以 PowerShell 作為 API 平台。

作為提供 API 並預期載入實作自身 (二進位模組) .NET 程式庫的 .NET 應用程式，以 NuGet 的形式提供 PowerShell 非常重要。

目前有數個 NuGet 套件呈現了一些 PowerShell API 的介面區。 要針對特定專案使用哪一個套件不見得總是明確。 本文揭示一些以 PowerShell 為目標的 .NET 專案常見案例，以及如何為以 PowerShell 為導向的 .NET 專案選擇正確 NuGet 套件作為目標。

## <a name="hosting-vs-referencing"></a>主機與參考

有些 .NET 專案會要求撰寫程式碼來將其載入已預先存在的 PowerShell 執行階段 (例如 `pwsh`、`powershell.exe`、PowerShell 整合式主控台或 ISE)，其他專案則可能會想要在其自身的應用程式內執行 PowerShell。

- **參考**指的是專案 (通常是模組) 旨在載入 PowerShell。
  為了與 PowerShell 進行互動，其必須針對 PowerShell 提供的 API 編譯，但 PowerShell 實作是由載入該專案的 PowerShell 處理序提供的。 針對參考，專案可使用[參考組件][]或實際的執行階段組件作為編譯目標，但必須確保其不會附帶任何編譯目標發佈其組建。
- **裝載**指的是專案需要其自身的 PowerShell 實作，通常是因為其為需要執行 PowerShell 的獨立應用程式。 在此情況下，即無法使用純參考組件。 在此情況下，必須改為倚賴具體的 PowerShell 實作。 由於必須使用具體的 PowerShell 實作，因此必須針對裝載選擇特定的 PowerShell 版本；單一主機應用程式無法以多個 PowerShell 版本作為目標。

### <a name="publishing-projects-that-target-powershell-as-a-reference"></a>將以 PowerShell 為目標的專案作為參考發佈

> [!NOTE]
> 我們會在本文中使用**發佈**這個術語來表示執行 `dotnet publish`，這個命令會將 .NET 程式庫與其所有的相依性放入目錄中，準備就緒以供部署至特定的執行階段。

為了避免發佈作為編譯參考目標使用的專案相依性，建議設定 [PrivateAssets 屬性][]：

```xml
<PackageReference Include="PowerShellStandard.Library" Version="5.1.0.0" PrivateAssets="all" />
```

若忘記執行這項操作，並使用參考組件作為目標，即可能會看到與使用參考組件預設實作相關的問題，而非實際的實作。 其形式可能會是 `NullReferenceException`，因為參考組件通常會透過直接傳回 `null` 來模擬實作 API。

## <a name="key-kinds-of-powershell-targeting-net-projects"></a>以 PowerShell 為目標 .NET 專案的主要類型

雖然任何 .NET 程式庫或應用程式都可內嵌 PowerShell，仍然有些使用 PowerShell API 的常見案例：

- **實作 PowerShell 二進位模組**

  PowerShell 二進位模組是由 PowerShell 載入的 .NET 程式庫，這些模組必須實作 [PSCmdlet][] 或 [CmdletProvider][] 類型等 PowerShell API，才能分別公開 Cmdlet 或提供者。 因為會載入這些模組，這些模組會針對 PowerShell 的參考進行編譯，但不會在其組建中發佈任何參考。 模組也經常會想要支援多個 PowerShell 版本和平台，且最好是將磁碟空間、複雜度或重複實作的額外負荷降至最低。 請參閱 [about_Modules][] 以取得模組的詳細資訊。

- **實作 PowerShell 主機**

  PowerShell 主機提供 PowerShell 執行階段的互動層。 這是一種「裝載」的特定形式，其中 [PSHost][] 會作為 PowerShell 的新使用者介面實作。 例如，PowerShell ConsoleHost 提供適用於 PowerShell 可執行檔的終端使用者介面，PowerShell 編輯器服務主機和 ISE 主機則提供與編輯器整合的 PowerShell 部分圖形化使用者介面。 雖然可將主機載入現有的 PowerShell 處理序，但將主機實作用作為轉散布 PowerShell 引擎的獨立 PowerShell 實作更為常見。

- **從另一個 .NET 應用程式呼叫 PowerShell**

  如同任何應用程式，可將 PowerShell 作為子流程呼叫來執行工作負載。 但是，作為 .NET 應用程式，也可以在處理序中叫用 PowerShell 來取回完整的 .NET 物件，以在呼叫的應用程式中使用。 這是更為一般的「裝載」形式，其中應用程式會保有其自身的 PowerShell 實作以供內部使用。 其範例可能是服務或是執行 PowerShell 來管理機器狀態的精靈，或根據要求執行 PowerShell 來執行如管理雲端部署等工作的 Web 應用程式。

- **從 .NET 針對 PowerShell 模組進行單元測試**

  雖然模組和其他旨在向 PowerShell 公開功能的程式庫主要應在 PowerShell 內進行測試 (建議使用 [Pester][])，有時候還是必須從 .NET 針對為 PowerShell 模組撰寫的 API 進行單元測試。 這種情況涉及模組程式碼嘗試以多個 PowerShell 版本為目標，同時測試應在特定、具體的實作上執行該模組程式碼。

## <a name="powershell-nuget-packages-at-a-glance"></a>PowerShell NuGet 套件一覽

在本文中，我們會涵蓋公開 PowerShell API 的下列 NuGet 套件：

- [PowerShellStandard.Library][]，這是一種參考組件，其可供建置可由多個 PowerShell 執行階段載入的單一組件。
- [Microsoft.PowerShell.SDK][]，瞄準及重新裝載整個 PowerShell SDK 的方式
- [System.Management.Automation][] 套件，這是核心 PowerShell 執行階段和引擎實作，在最少裝載實作以及以特定版本為目標的案例中相當實用。
- **Windows PowerShell 參考組件**，瞄準及有效重新裝載 Windows PowerShell (PowerShell 版本 5.1 及更早版本) 的方式。

> [!NOTE]
> [PowerShell NuGet][] 套件完全不是 .NET 程式庫套件，但可提供 PowerShell dotnet 全域工具實作。 此項目不應由任何專案使用，因為其只提供可執行檔。

## <a name="powershellstandardlibrary"></a>PowerShellStandard.Library

PowerShell Standard 程式庫是一種參考組件，其擷取 PowerShell 版本 7、6 及 5.1 API 的交集。 此提供編譯時間檢查 API 介面，以針對其編譯 .NET 程式碼，允許 .NET 專案以 PowerShell 版本 7、6 和 5.1 作為目標，而不會有呼叫不存在 API 的風險。

PowerShell Standard 旨在適用於撰寫 PowerShell 模組，或其他僅旨在載入 PowerShell 處理序後執行的程式碼。 由於其為參考組件，PowerShell Standard 本身不包含任何實作，因此不會提供任何標準應用程式的功能。

### <a name="using-powershell-standard-with-different-net-runtimes"></a>搭配不同的 .NET 執行階段使用 PowerShell Standard

PowerShell Standard 以 [.NET Standard 2.0][] 目標執行階段為目標，這是一種旨在提供 .NET Framework 和 .NET Core 通用介面區的外觀執行階段。 這會允許以單一執行階段作為目標，以產生可搭配多個 PowerShell 版本使用的單一組件，但會有下列結果：

- 載入模組或程式庫的 PowerShell 至少必須執行 .NET 4.6.1，.NET 4.6 和 .NET 4.5.2 不支援 .NET Standard。 請注意，更新的 Windows PowerShell 版本並不等同於更新的 .NET Framework 版本；Windows PowerShell 5.1 可能會在 .NET 4.5.2 上執行。
- 若要與執行 .NET Framework 4.7.1 或以下版本的 PowerShell 搭配使用，在較舊的 .NET Framework 版本中，需要 .NET 4.6.1 [NETStandard.Library][] 實作來提供 netstandard.dll 和其他填充碼組件。

PowerShell 6 以上版本會提供其自身的填充碼組件，以將類型從 .NET Framework 4.6.1 (及更新版本) 轉送至 .NET Core。 這表示只要模組僅使用 .NET Core 中存在的 API，PowerShell 6 以上版本即可在為 .NET Framework 4.6.1 (`net461` 執行階段目標) 建置的情況下載入及執行。

這表示使用 PowerShell Standard，透過單一發佈的 DLL 以多個 PowerShell 版本為目標的二進位模組會有兩個選項：

1. 發佈為 `net461` 目標執行階段建置的組件。 這包括：
   - 為 `net461` 執行階段發佈專案
   - 同時針對 `netstandard2.0` 執行階段進行編譯 (不使用其建置輸出)，以確保所有使用的 API 也都存在於 .NET Core 中。

1. 為 `netstandard2.0` 目標執行階段發佈組件的組建。 這需要：
   - 為 `netstandard2.0` 執行階段發佈專案
   - 取得 NETStandard.Library 的 `net461` 相依性，並將其複製到專案組件的發佈位置，以在 .NET Framework 中正確地針對組件進行類型轉送。

若要建置以較舊 .NET Framework 版本為目標的 PowerShell 模組或程式庫，則建議以多個 .NET 執行階段作為目標。 這將會為每個目標執行階段發佈組件，且將需要在載入模組時載入正確的組件 (例如以小型的 psm1 作為根模組)。

### <a name="testing-powershell-standard-projects-in-net"></a>在 .NET 中測試 PowerShell Standard 專案

當想要在 xUnit 等 .NET 測試執行器中測試模組時，請記住編譯時間檢查能帶來的效果有限。 您必須針對相關的 PowerShell 平台測試模組。

若要在 .NET 中測試針對 PowerShell Standard 建置的 API，建議新增 `Microsoft.Powershell.SDK` 作為 .NET Core 的測試相依性 (並將版本設為相符於所需 PowerShell 版本)，並針對 .NET Framework 新增適當的 Windows PowerShell 參考組件。

如需 PowerShell Standard 的詳細資訊，以及使用其來撰寫可在多個 PowerShell 版本中運作的二進位模組詳細資訊，請參閱[此部落格文章][]。 另請參閱 GitHub 上的 [PowerShell Standard 存放庫][]。

## <a name="microsoftpowershellsdk"></a>Microsoft.PowerShell.SDK

`Microsoft.PowerShell.SDK` 是一種中繼套件，這個套件將所有 PowerShell SDK 的元件組合成單一 NuGet 套件。 獨立的 .NET 應用程式可使用 Microsoft PowerShell.SDK 來執行任意 PowerShell 功能，而無須依賴任何外部 PowerShell 安裝或程式庫。

> [!NOTE]
> PowerShell SDK 會直接參考構成 PowerShell 的所有元件套件，以及可用於搭配 PowerShell 進行 .NET 開發的套件。

指定的 `Microsoft.Powershell.SDK` 版本包含相同版本 PowerShell 應用程式的具體實作；版本 7.0 包含 PowerShell 7.0 的實作，且使用其來執行命令或指令碼就如同在 PowerShell 7.0 中執行這些命令或指令碼。

從 SDK 執行 PowerShell 命令大部分 (但不全是) 都和在 `pwsh` 中執行命令相同。 例如，[Start-Job][] 目前依賴可用的 `pwsh` 可執行檔，因此根據預設無法和 `Microsoft.Powershell.SDK` 搭配運作。

從 .NET 應用程式以 `Microsoft.Powershell.SDK` 作為目標，可供和所有 PowerShell 的實作組件整合，例如 `System.Management.Automation`、`Microsoft.PowerShell.Management` 和其他模組組件。

發佈以 `Microsoft.Powershell.SDK` 作為目標的應用程式將會包含所有這些組件，以及任何 PowerShell 需要的相依性。 這也會包含其他 PowerShell 在其組建中需要的資產，例如 `Microsoft.PowerShell.*` 模組的模組資訊清單，以及 [Add-Type][] 需要的 `ref` 目錄。

基於 `Microsoft.Powershell.SDK` 的完整性，其最適合用於：

- PowerShell 主機的實作。
- 以 PowerShell 參考組件作為目標的程式庫 xUnit 測試。
- 從 .NET 應用程式的處理序中叫用 PowerShell。

`Microsoft.PowerShell.SDK` 也可以在 .NET 專案旨在用來作為模組，或會由 PowerShell 載入，但是依賴只存在於特定 PowerShell 版本中的 API 時，作為參考目標使用。 請注意，針對特定 `Microsoft.PowerShell.SDK` 版本所發佈組件只有在於該版本的 PowerShell 中載入及使用時才安全。 若要以具備特定 API 的多個 PowerShell 版本作為目標，則需要多個組建，且每個組建都會以其自身的 `Microsoft.Powershell.SDK` 版本作為目標。

> [!NOTE]
> PowerShell SDK 僅提供 PowerShell 6 以上版本使用。 若要透過 Windows PowerShell 提供相等的功能，請使用以下所述的 Windows PowerShell 參考組件。

## <a name="systemmanagementautomation"></a>System.Management.Automation

`System.Management.Automation` 套件是 PowerShell SDK 的核心。 其存在於 NuGet 上，主要作為 `Microsoft.Powershell.SDK` 提取的資產。 但是，其也可以直接用來作為較小裝載案例和瞄準版本模組的套件。

具體而言，`System.Management.Automation` 套件可能會是以下情況的偏好 PowerShell 功能提供者：

- 您只想要使用 PowerShell 語言功能 (位於 `System.Management.Automation.Language` 命名空間)，例如 PowerShell 剖析器、AST，以及 AST 訪客 API (例如 PowerShell 的靜態分析)。
- 您只想要執行 `Microsoft.PowerShell.Core` 模組中的特定命令，且可在使用 [CreateDefault2][] Factory 方法建立的工作階段狀態中執行。

此外，`System.Management.Automation` 也是以下情況的實用參考組件：

- 您想要以只在特定 PowerShell 版本中存在的 API 作為目標
- 您不會依賴在 `System.Management.Automation` 組件外部發生的類型 (例如由 `Microsoft.PowerShell.*` 模組中 Cmdlet 匯出的類型)。

## <a name="windows-powershell-reference-assemblies"></a>Windows PowerShell 參考組件

針對 PowerShell 版本 5.1 及更早版本 (Windows PowerShell)，沒有 SDK 提供 PowerShell 的實作，因為 Windows PowerShell 的實作是 Windows 的一部分。

相反地，Windows PowerShell 參考組件提供參考目標以及重新裝載 Windows PowerShell 的方式，其運作方式與 PowerShell SDK 為版本 6 及更新版本執行的工作相同。

Windows PowerShell 參考組件針對每個 Windows PowerShell 版本皆有不同的套件，而非以版本進行區別：

- [PowerShell 5.1](https://www.nuget.org/packages/Microsoft.PowerShell.5.ReferenceAssemblies/)
- [PowerShell 4](https://www.nuget.org/packages/Microsoft.PowerShell.4.ReferenceAssemblies/)
- [PowerShell 3](https://www.nuget.org/packages/Microsoft.PowerShell.3.ReferenceAssemblies/)

您可在 [Windows PowerShell SDK][] 中找到如何使用 Windows PowerShell 參考組件的資訊。

## <a name="real-world-examples-using-these-nuget-packages"></a>使用這些 NuGet 套件的真實世界範例

取決於其需求，不同的 PowerShell 工具專案會以不同 PowerShell NuGet 套件作為目標。 以下列出的是一些知名範例。

### <a name="psreadline"></a>PSReadLine

[PSReadLine][] 是一種 PowerShell 模組，其提供許多 PowerShell 的豐富主控台體驗，以 PowerShell Standard 而非特定 PowerShell 版本作為相依性，並在其 [csproj][] 中以 `net461` .NET 執行階段作為目標。

PowerShell 6 以上版本會提供其自身的填充碼組件，允許以 `net461` 執行階段作為目標的 DLL 在載入時「正常運作」(其方式為將 .NET Framework `mscorlib.dll` 的繫結重新導向到相關的 .NET Core 組件)。

這大幅簡化 PSReadLine 模組的配置和傳遞，因為 PowerShell Standard 會確保使用的 API 都存在於 Power 5.1 和 PowerShell 6.0，同時也允許僅透過單一組件來傳遞模組。

雖然 .NET 4.6.1 目標表示其不支援在 .NET 4.5.2 和 .NET 4.6 上執行的 Windows PowerShell。

### <a name="powershell-editor-services"></a>PowerShell 編輯器服務

[PowerShell 編輯器服務][] (PSES) 是 [Visual Studio Code][] [PowerShell 延伸模組][]的後端，其實際上是一種由 PowerShell 可執行檔載入，並接管該處理序來在其內部重新裝載 PowerShell，同時提供語言服務通訊協定及偵錯配接器功能的 PowerShell 模組形式。

PSES 提供 `netcoreapp2.1` 的具體實作目標來以 PowerShell 6 以上版本作為目標 (因為 PowerShell 7 的 `netcoreapp3.1` 執行階段具備回溯相容性)，並提供 `net461` 來以 Windows PowerShell 5.1 作為目標，但在第二個以 `netstandard2.0` 和 PowerShell Standard 作為目標的組件中包含大多數的邏輯。 這可讓其提取 .NET Core 和 .NET Framework 平台需要的相依性，同時透過統一的抽象化來簡化大多數程式碼基底。

由於其是針對 PowerShell Standard 所建置，因此 PSES 需要 PowerShell 的執行階段實作，才能正確地進行測試。 為了執行這項操作，[PSES 的 xUnit][] 測試會提取 `Microsoft.PowerShell.SDK` 和 `Microsoft.PowerShell.5.ReferenceAssemblies`，來在測試環境中提供 PowerShell 實作。

如同 PSReadLine，PSES 無法支援 .NET 4.6 及更早版本，但其會在呼叫任何可能會在較低 .NET Framework 執行階段中造成損毀的 API 之前，於執行階段[執行檢查][]。

### <a name="psscriptanalyzer"></a>PSScriptAnalyzer

[PSScriptAnalyzer][]是 PowerShell 的 Linter，其必須以在特定 PowerShell 版本中引進的語法項目作為目標。 由於識別這些語法項目的方式是透過實作 [AstVisitor2][]，因此其無法在使用 PowerShellStandard 的同時為 PowerShell 較新語法實作 AST 訪客方法。

相反地，PSScriptAnalyzer 的組建組態[會以每個 PowerShell 版本作為目標][]，並為每個版本產生個別的 DLL。 這會增加組建的大小和複雜度，但允許：

- 以特定版本的 API 作為目標
- 在基本上沒有任何執行階段成本的情況下實作版本特定功能
- 直到 Windows PowerShell 到 .NET Framework 4.5.2 的整體支援

## <a name="summary"></a>摘要

在本文中，我們已列出和討論了作為目標的 NuGet 套件 (在實作使用 PowerShell 的 .NET 專案時)，以及您可能會使用其中一個套件而非另一個套件的原因。

若您已跳到摘要，一些廣義的建議包括：

- PowerShell **模組**如果只需要不同 PowerShell 版本通用的 API，則應針對 PowerShell Standard 進行編譯。
- 需要在內部執行 PowerShell 的 PowerShell **主機和應用程式**，其應針對 PowerShell 6 以上版本以 PowerShell SDK 作為目標，或針對 Windows PowerShell 以相關 Windows PowerShell 參考組件作為目標。
- 需要**版本特定 API** 的 PowerShell 模組應針對 PowerShell 必要版本，以 PowerShell SDK 或 Windows PowerShell 參考組件作為目標 (將其作為參考組件使用，即不發佈 PowerShell 相依性)。

<!--link references -->

[.NET Standard 2.0]: /dotnet/standard/net-standard
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[Add-Type]: /powershell/module/microsoft.powershell.utility/add-type
[AstVisitor2]: /dotnet/api/system.management.automation.language.astvisitor2
[CmdletProvider]: /dotnet/api/system.management.automation.provider.cmdletprovider
[CreateDefault2]: /dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2
[csproj]: https://github.com/PowerShell/PSReadLine/blob/master/PSReadLine/PSReadLine.csproj
[Microsoft.PowerShell.SDK]: https://www.nuget.org/packages/Microsoft.PowerShell.SDK/
[NETStandard.Library]: https://www.nuget.org/packages/NETStandard.Library/
[NuGet]: https://www.nuget.org/
[執行檢查]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/src/PowerShellEditorServices.Hosting/EditorServicesLoader.cs#L231-L251
[Pester]: https://github.com/Pester/Pester
[PowerShell 編輯器服務]: https://github.com/PowerShell/PowerShellEditorServices/
[PowerShell 延伸模組]: https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[PowerShell NuGet]: https://www.nuget.org/packages/PowerShell/
[PowerShell Standard 存放庫]: https://github.com/PowerShell/PowerShellStandard
[PowerShellStandard.Library]: https://www.nuget.org/packages/PowerShellStandard.Library/
[PSCmdlet]: /dotnet/api/system.management.automation.pscmdlet
[PSES 的 xUnit]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/test/PowerShellEditorServices.Test/PowerShellEditorServices.Test.csproj#L15-L20
[PSHost]: /dotnet/api/system.management.automation.host.pshost
[PrivateAssets 屬性]: /dotnet/core/tools/csproj#packagereference
[PSReadLine]: https://github.com/PowerShell/PSReadLine
[PSScriptAnalyzer]: https://github.com/powershell/psscriptanalyzer
[參考組件]: https://github.com/dotnet/standard/blob/master/docs/history/evolution-of-design-time-assemblies.md#definitions
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[System.Management.Automation]: https://www.nuget.org/packages/System.Management.Automation/
[以每個 PowerShell 版本作為目標]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/Engine/Engine.csproj
[此部落格文章]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
[Visual Studio Code]: https://code.visualstudio.com/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell
