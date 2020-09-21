---
title: 如何建立標準程式庫的二進位模組
description: PowerShell 標準程式庫可讓我們建立跨平台模組，以便在 PowerShell Core 和 Windows PowerShell 5.1 中使用。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: ff6a49f70a3fb77f5a30cc909d53bb77b3cd7d43
ms.sourcegitcommit: 8c01e56f0c10ff2637955dc892ea78432d563a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2020
ms.locfileid: "88702740"
---
# <a name="how-to-create-a-standard-library-binary-module"></a>如何建立標準程式庫的二進位模組

我最近已瞭解要實作為二進位模組的模組。 我還得使用 [PowerShell 標準程式庫][]來建立一個模組，因此這會是一個很好的機會。 我使用[建立跨平台二進位模組][]指南來建立此模組，不會有任何障礙。
我們將逐步介紹相同的流程，並在過程中新增一些額外的評論。

> [!NOTE]
> 本文的[原始版本][]出自 [@KevinMarquette][] 所撰寫的部落格。 PowerShell 小組感謝 Kevin 分享的內容。 請前往 [PowerShellExplained.com][] 瀏覽他的部落格。

## <a name="what-is-the-powershell-standard-library"></a>什麼是 PowerShell 標準程式庫？

PowerShell 標準程式庫可讓我們建立跨平台模組，以便在 PowerShell Core 和 Windows PowerShell 5.1 (或 3.0) 中使用。

## <a name="planning-our-module"></a>規劃我們的模組

此模組的規劃是針對 C# 程式碼建立 `src` 資料夾 ，並針對指令碼模組建立其餘部分的架構，如同我即將執行的作業。 這包括使用組建指令碼將所有內容編譯在 `output` 資料夾中。 資料夾結構如下所示：

```
MyModule
├───src
├───Output
│   └───MyModule
├───MyModule
│   ├───Data
│   ├───Private
│   └───Public
└───Tests
```

## <a name="getting-started"></a>開始使用

我通常會使用 Plaster 範本，但目前的範本尚未提供任何二進位模組支援。 不過，這沒什麼大不了的。 我現在就能馬上手動建立一個。

首先我需要建立資料夾，並建立 git 存放庫。 我使用 `$module` 做為模組名稱的預留位置。 若有需要，這應該可讓您更輕鬆地重複使用這些範例。

```powershell
$module = 'MyModule'
New-Item -Path $module -Type Directory
Set-Location $module
git init
```

然後建立根層級資料夾。

```powershell
New-Item -Path 'src' -Type Directory
New-Item -Path 'Output' -Type Directory
New-Item -Path 'Tests' -Type Directory
New-Item -Path $module -Type Directory
```

### <a name="binary-module-setup"></a>二進位模組設定

本文內容著重在二進位模組，因此我們將從這裡開始。 本節會從[建立跨平台二進位模組][]指南中舉例說明。 如果您需要更多詳細資料或有任何問題，請參閱該指南。

我們首先要做的，就是檢查我們所安裝的 [dotnet core SDK][] 版本。 我使用的是 2.1.4，但您應該先擁有 2.0.0 或更新版本，才能繼續進行。

```powershell
PS> dotnet --version
2.1.4
```

我正在處理本節所述的 `src` 資料夾。

```powershell
Set-Location 'src'
```

使用 dotnet 命令建立新的類別庫。

```powershell
dotnet new classlib --name $module
```

這會在子資料夾中建立程式庫專案，但我不想要這個額外的嵌套層級。 我要將這些檔案往上移一層。

```powershell
Move-Item -Path .\$module\* -Destination .\
Remove-Item $module -Recurse
```

設定專案的 .NET core SDK 版本。 我有 2.1 SDK，所以我要指定 2.1.0。
如果您使用的是 2.0 SDK，請使用 2.0.0。

```powershell
dotnet new globaljson --sdk-version 2.1.0
```

將 PowerShell Standard 程式庫 [ NuGet 套件][] 新增至專案。 請確定您使用的是最新版本，以取得您所需的相容性層級。 我會預設為最新版本，但我不認為此模組會利用比 PowerShell 3.0 還新的任何功能。

```powershell
dotnet add package PowerShellStandard.Library --version 7.0.0-preview.1
```

我們應該會有一個 src 資料夾，如下所示：

```powershell
PS> Get-ChildItem
    Directory: \MyModule\src

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        7/14/2018   9:51 PM                obj
-a----        7/14/2018   9:51 PM             86 Class1.cs
-a----        7/14/2018  10:03 PM            259 MyModule.csproj
-a----        7/14/2018  10:05 PM             45 global.json
```

現在我們已經準備好將自己的程式碼加入專案中。

### <a name="building-a-binary-cmdlet"></a>建立二進位 Cmdlet

我們需要更新 `src\Class1.cs` 以包含此入門 Cmdlet：

```csharp
using System;
using System.Management.Automation;

namespace MyModule
{
    [Cmdlet( VerbsDiagnostic.Resolve , "MyCmdlet")]
    public class ResolveMyCmdletCommand : PSCmdlet
    {
        [Parameter(Position=0)]
        public Object InputObject { get; set; }

        protected override void EndProcessing()
        {
            this.WriteObject(this.InputObject);
            base.EndProcessing();
        }
    }
}
```

將檔案重新命名以符合類別名稱。

```powershell
Rename-Item .\Class1.cs .\ResolveMyCmdletCommand.cs
```

然後我們可以建立自己的模組。

```powershell
PS> dotnet build

Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

Restore completed in 18.19 ms for C:\workspace\MyModule\src\MyModule.csproj.
MyModule -> C:\workspace\MyModule\src\bin\Debug\netstandard2.0\MyModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.19
```

我們可以在新的 dll 上呼叫 `Import-Module`，載入新的 CMDlet。

```powershell
PS> Import-Module .\bin\Debug\netstandard2.0\$module.dll
PS> Get-Command -Module $module

CommandType Name                    Version Source
----------- ----                    ------- ------
Cmdlet      Resolve-MyCmdlet        1.0.0.0 MyModule
```

如果您的系統匯入失敗，請嘗試將 .NET 更新為 4.7.1 或更新版本。 [建立跨平台二進位模組][]指南會進一步探討 .NET 支援和舊版 .NET 的相容性。

### <a name="module-manifest"></a>模組資訊清單

很棒的是，我們可以匯入 dll 並擁有一個有效的模組。 我想要繼續使用它，並建立模組資訊清單。 如果想要稍後發行至 PSGallery，我們需要資訊清單。

從專案的根目錄，我們可以執行此命令以建立所需的模組資訊清單。

```powershell
$manifestSplat = @{
    Path              = ".\$module\$module.psd1"
    Author            = 'Kevin Marquette'
    NestedModules     = @('bin\MyModule.dll')
    RootModule        = "$module.psm1"
    FunctionsToExport = @('Resolve-MyCmdlet')
}
New-ModuleManifest @manifestSplat
```

我也會建立一個空的根模組，供未來的 PowerShell 函式使用。

```powershell
Set-Content -Value '' -Path ".\$module\$module.psm1"
```

這可讓我在同一個專案中混合使用一般的 PowerShell 函式與二進位 Cmdlet。

### <a name="building-the-full-module"></a>建置完整的模組

我將所有專案編譯成輸出資料夾。 我們需要建立組建指令碼以執行此動作。 我通常會將此程式碼新增至 `Invoke-Build` 指令碼，但在此範例中，我們可以將它簡化。 將此加入至專案根目錄的 `build.ps1`。

```powershell
$module = 'MyModule'
Push-Location $PSScriptRoot

dotnet build $PSScriptRoot\src -o $PSScriptRoot\output\$module\bin
Copy-Item "$PSScriptRoot\$module\*" "$PSScriptRoot\output\$module" -Recurse -Force

Import-Module "$PSScriptRoot\Output\$module\$module.psd1"
Invoke-Pester "$PSScriptRoot\Tests"
```

這些命令會建立 DLL，並將其放入我們的 `output\$module\bin` 資料夾中。 然後，它會將其他模組檔案複製到定位。

```
Output
└───MyModule
    │   MyModule.psd1
    │   MyModule.psm1
    │
    └───bin
            MyModule.deps.json
            MyModule.dll
            MyModule.pdb
```

此時，我們可以使用 psd1 檔案匯入模組。

```powershell
Import-Module ".\Output\$module\$module.psd1"
```

在這裡，我們可以將 `.\Output\$module` 資料夾放入我們的 `$env:PSModulePath` 目錄中，並在需要時該資料夾會自動載入我們的命令。

### <a name="update-dotnet-new-psmodule"></a>更新： dotnet 新的 PSModule

我瞭解 `dotnet` 工具具有 `PSModule` 範本。

上面所述的所有步驟仍然有效，但此範本減少了許多步驟。它仍然是一個非常新的範本，仍然有待進一步完善。 期待它此後會日益完善。

這是您使用 install 和使用 PSModule 範本的方式。

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
dotnet new psmodule
dotnet build
Import-Module "bin\Debug\netstandard2.0\$module.dll"
Get-Module $module
```

這個最低可行的範本會負責新增 .NET SDK、PowerShell 標準程式庫，並在專案中建立範例類別。 您可以建立範本並立即加以執行。

## <a name="important-details"></a>重要詳細資料

在本文結束之前，這裡有一些值得一提的其他詳細資料。

### <a name="unloading-dlls"></a>卸載 DLL

載入二進位模組之後，您就無法真正將其卸載。 系統會鎖定 DLL 檔案，直到其卸載為止。 這可能會在開發時造成困擾，因為每當您進行變更並想要加以建置時，檔案常常會遭到鎖定。 解決此問題的唯一可靠方式，就是關閉載入 DLL 的 PowerShell 工作階段。

### <a name="vs-code-reload-window-action"></a>VS Code 重載視窗動作

我大部分的 PowerShell 開發工作都是在 [VS 程式碼][] 中執行。 當我使用二進位模組 (或具有類別的模組) 時，我已經養成在每次建立時都重載 VS Code 的習慣。
<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 會使命令視窗隨即開啟，而 `Reload Window` 則一律位於清單頂端。

### <a name="nested-powershell-sessions"></a>嵌套的 PowerShell 工作階段

另一個選項是使用良好的 Pester 測試涵蓋範圍。 接著，您可以調整 build.ps1 指令碼來啟動新的 PowerShell 工作階段、執行組建、執行測試，然後關閉工作階段。

### <a name="updating-installed-modules"></a>更新已安裝的模組

嘗試更新您在本機安裝的模組時，這種鎖定可能會造成困擾。 如果有任何工作階段將其載入，您就必須將向下搜尋它並加以關閉。 從 PSGallery 安裝時，這種問題比較少出現，因為模組版本設定會將新的設定放在不同的資料夾中。

您可以設定本機 PSGallery，並將其發佈以做為組建的一部分。 然後從該 PSGallery 進行本機安裝。 這聽起來似乎頗為繁瑣，不過這就像啟動 docker 容器一樣簡單。 我在 [使用適用於 PSRepository 的 NuGet 伺服器][] (英文) 文章中，介紹了執行這項操作的方法。

## <a name="why-binary-modules"></a>為何要選擇二進位模組？

我直接跳到如何製作二進位模組，卻沒有提及您為什麼要製作。 實際上，您正在撰寫 C# 並且讓您輕鬆地存取 PowerShell Cmdlet 和函式。 這是我未搶先移至二進位模組的主要原因。

不過，如果您要建立的模組並不依賴許多其他 PowerShell 命令，便可以在效能方面產生巨大優勢。 藉由將放入 C# ，您就可以擺脫 PowerShell 新增的負荷。 PowerShell 已針對系統管理員 (而不是電腦) 進行最佳化，因而增加了一些負荷。

在工作時，我們有一個非常重要的流程，其中會使用 JSON 和雜湊表執行許多工作。 儘管我們已經盡可能將 PowerShell 最佳化，但此流程仍需要執行 12 分鐘。 模組已包含許多 C# 樣式的 PowerShell。 這使得轉換成二進位模組變得簡單俐落，而且容易執行。 我們的轉換會將流程從12分鐘縮短至 4 分鐘以內。

### <a name="hybrid-modules"></a>混合式模組

您可以混合使用二進位 Cmdlet 與 PowerShell 進階函式。 這正是我在本指南中執行的動作。 關於指令碼模組，您所知的一切，也全都以相同的方式適用。
我今天所建立的空白 `psm1` 檔案，就是您稍後可以放入其他 PowerShell 函式的位置。

幾乎我們所建立的所有經過編譯的 Cmdlet，都是先以 PowerShell 函式的方式開始的。 我們所有的二進位模組都是混合式模組。

### <a name="build-scripts"></a>組建指令碼

我在此將簡化組建指令碼。 我通常會使用大型的 `Invoke-Build` 指令碼做為 CI/CD 管道的一部分。 執行 Pester 測試、執行 PSScriptAnalyzer、管理版本控制，以及發行至 PSGallery 等，都能發揮更大的神奇效用。 當我開始針對模組使用組建指令碼之後，我就可以找到要新增至模組的許多內容。

## <a name="final-thoughts"></a>最後的想法

二進位模組很容易建立。 建立 Cmdlet，我並未採用 C# 語法，不過 [Windows PowerShell SDK][] 中有許多相關文件。 這種作法絕對值得一試，可做為更嚴謹的 C# 的跳板。

<!-- link references -->
[原始版本]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[PowerShell 標準程式庫]: https://github.com/PowerShell/PowerShellStandard
[建立跨平台二進位模組]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[dotnet core SDK]: https://www.microsoft.com/net/download/core
[使用適用於 PSRepository 的 NuGet 伺服器]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell-reference
[VS 程式碼]: https://code.visualstudio.com
[ NuGet 套件]: https://www.nuget.org/packages/PowerShellStandard.Library/
