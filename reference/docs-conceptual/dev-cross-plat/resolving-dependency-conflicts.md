---
title: 解析 PowerShell 模組組件的相依性衝突
description: 使用 C# 撰寫二進位 PowerShell 模組時，為提供功能而相依於其他套件或程式庫是很自然的事。
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 93bb39bdd440c7f97c27aa81e68f68331569b69e
ms.sourcegitcommit: 2fc6ee49a70bda4c59135136bd5cc7782836a124
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94810397"
---
# <a name="resolving-powershell-module-assembly-dependency-conflicts"></a>解析 PowerShell 模組組件的相依性衝突

使用 C# 撰寫二進位 PowerShell 模組時，為提供功能而相依於其他套件或程式庫是很自然的事。 為重複使用程式碼需要相依於其他程式庫。 PowerShell 一律會將組件載入相同的內容中。 當模組的相依性與已載入 DLL 發生衝突，且會阻礙同一 PowerShell 工作階段使用其他兩個不相關的模組時，就會發生問題。

如果遇到這個問題，即會看到類似下面的錯誤訊息：

![組件載入衝突錯誤訊息](./media/resolving-dependency-conflicts/moduleconflict.png)

本文會探討 PowerShell 發生相依性衝突的一些方式，以及減輕相依性衝突問題的方式。 即使您不是模組作者，文中還是有一些訣竅可有助解析所用模組的相依性衝突。

## <a name="why-do-dependency-conflicts-occur"></a>為何會發生相依性衝突？

在 .NET 中，當兩個版本的相同組件載入至同一「組件載入內容」時，就會發生相依性衝突。 這個字詞表示不同 .NET 平台上略微不同的東西，[後文](#powershell-and-net)會加以討論。 這是所有使用版本相依性的軟體其常見衝突。 因為沒有簡單的解決方案，而許多相依性解析架構都會使用不同的方式來嘗試解決問題，所以這種情況通常稱為「相依性地獄」。

衝突問題之所以複雜，是因為專案幾乎不會刻意或直接相依於兩個版本的同一相依性， 而是專案有兩個或以上的相依性，各自又都需要不同版本的相同相依性。

例如，假設 .NET 應用程式 `DuckBuilder` 引進兩個相依性來執行部分的功能，且看起來如下：

![DuckBuilder 其兩個相依性依賴不同版本的 Newtonsoft.Json](./media/resolving-dependency-conflicts/dep-conflict.jpg)

因為 `Contoso.ZipTools` 和 `Fabrikam.FileHelpers` 都相依於不同版本的 `Newtonsoft.Json`，所以可能會有相依性衝突，視每個相依性的載入方式而定。

### <a name="conflicting-with-powershells-dependencies"></a>與 PowerShell 的相依性發生衝突

在 PowerShell 中，相依性衝突問題會因為 PowerShell 模組和 PowerShell 本身的相依性載入至同一共用內容而放大。 這表示 PowerShell 引擎和所載入 PowerShell 全部模組絕不能有衝突的相依性。 `Newtonsoft.Json` 即為典型的範例：

![FictionalTools 模組相依於較新版的 Newtonsoft.Json，而不是 PowerShell](./media/resolving-dependency-conflicts/engine-conflict.jpg)

在此範例中，模組 `FictionalTools` 相依於 `12.0.3` 版的 `Newtonsoft.Json`，這個 `Newtonsoft.Json` 版本比範例 PowerShell 所附的 `11.0.2` 版本更新。

> [!NOTE]
> 此為範例，PowerShell 7 目前所附的版本為 `Newtonsoft.Json 12.0.3`。

因為模組相依於較新版本的組件，所以不接受 PowerShell 已載入的版本。 但因 PowerShell 已載入組件的某個版本，所以模組無法使用傳統載入機制來載入自己的版本。

### <a name="conflicting-with-another-modules-dependencies"></a>與另一個模組的相依性發生衝突

PowerShell 中另一個常見案例就是所載入模組相依於組件的某個版本，但稍後另一個載入模組相依於該組件的不同版本。

通常看起來如下：

![兩個 PowerShell 模組需要不同版本的 Microsoft.Extensions.Logging 相依性](./media/resolving-dependency-conflicts/mod-conflict.jpg)

在本例中，`FictionalTools` 模組需要比 `FilesystemManager` 模組更新版本的 `Microsoft.Extensions.Logging`。

假設這些模組都將相依性組件和根模組組件放在相同的目錄中，以載入其相依性。 這會讓 .NET 毫無疑慮地依名稱載入這些組件。 如果正在 .NET Core 3.1 上執行 PowerShell 7，則可載入並執行 `FictionalTools`，然後成功載入並執行 `FilesystemManager`。 但在新的工作階段中，如果我們載入並執行 `FilesystemManager`，然後載入 `FictionalTools`，就會從 `FictionalTools` 命令得到 `FileLoadException`，因為需要比所載入版本更新的 `Microsoft.Extensions.Logging`。
`FictionalTools` 無法載入所需的版本，因為已經載入具有相同名稱的組件。

## <a name="powershell-and-net"></a>PowerShell 和 .Net

PowerShell 會在 .NET 平台上執行。 因為最後是 NET 負責解析和載入組件相依性，所以我們必須了解 .NET 在這裡的運作方式，才能了解相依性衝突。

我們也必須面對在不同 .NET 實作中執行不同版本 PowerShell 的事實。 PowerShell 5.1 和較低版本一般會在 .NET Framework 上執行，而 PowerShell 6 和更新版本則是在 .NET Core 上執行。 這兩種 .NET 載入和處理組件的實作方式不同。
這表示解析相依性衝突會隨基礎 .NET 平台而有所不同。

### <a name="assembly-load-contexts"></a>組件載入內容

在 .NET 中，「組件載入內容」(ALC) 是組件載入所在的執行階段命名空間。 組件名稱必須是唯一的。 這個概念可在每個 ALC 中，依名稱來唯一解析組件。

### <a name="assembly-reference-loading-in-net"></a>.NET 中的組件參考載入

組件載入其語義取決於 .NET 實作 (.NET Core 與 .NET Framework) 和載入特定組件所用的 .NET API。 [進階閱讀](#further-reading)一節中提供的連結，可供深入了解 .NET 組件載入在每個 .NET 實作中的運作方式，這裡不詳細說明。

本文會討論下列機制：

- 隱含組件載入 (有效率地 `Assembly.Load(AssemblyName)`)，當 .NET 嘗試從 .NET 程式碼的靜態組件參考中隱含地依名稱載入組件時。
- `Assembly.LoadFrom()` 是外掛程式導向的載入 API，其會新增處理常式以解析所載入 DLL 的相依性。 這個方法可能無法以所要的方式來解析相依性。
- `Assembly.LoadFile()` 是基本的載入 API，僅用來載入所要求的組件，且不處理任何相依性。

### <a name="differences-in-net-framework-vs-net-core"></a>.NET Framework 與 .NET Core 的差異

這些 API 的運作方式在 .NET Core 與 .NET Framework 之間有些許變化，因此值得您詳閱隨附的[連結](#further-reading)。 重要的是，組件載入內容及其他組件解析機制在 .NET Framework 和 .NET Core 之間已經變更。

特別是 .NET Framework 具有下列功能：

- 全域組件快取，適用於整部電腦的組件解析
- 應用程式定義域，適用於隔離組件的半成品沙箱，但也會顯示要處理的序列化層
- 有限的組件載入內容模型 ([這裡](/dotnet/framework/deployment/best-practices-for-assembly-loading)會詳加說明)，具有一組固定的組件載入內容，各有各的行為：
  - 預設的載入內容，其包含預設載入的組件
  - 載入來源內容，以在執行階段手動載入組件
  - 僅限反映的內容，用於安全載入組件以讀取其中繼資料但不予以執行
  - 組件以 `Assembly.LoadFile(string path)` 載入和 `Assembly.Load(byte[] asmBytes)` 所在位置的神秘 void

.NET Core (和 .NET 5+) 已使用更簡單的模型取代此複雜情況：

- 無全域組件快取。 應用程式會攜帶自己所有的相依性。 這可排除應用程式相依性解析的外部因素，以更有機會重現相依性解析。
  對模組而言，以 PowerShell 作為外掛程式主機，情況會稍微複雜一點。 其在 `$PSHOME` 中的相依性會與所有模組共用。
- 只有一個應用程式定義域，且無法建立新的。 應用程式定義域概念是在 .NET Core 中維護，純為 .NET 程序的全域狀態。
- 新的可延伸組件載入內容模型。 將組件解析放入新的 ALC，可將其定義為命名空間。 .NET Core 程序從單一預設 ALC 開始，直到載入所有組件。 (以 `Assembly.LoadFile(string)` 和 `Assembly.Load(byte[])` 載入的除外) 但此程式可使用專屬載入邏輯來建立及定義自己的自訂 ALC。 載入組件時，其載入的第一個 ALC 會負責解析其相依性。 這提供機會來實作功能強大的 .NET 外掛程式載入機制。

這兩種實作都會延遲載入組件。 這表示載入時，有方法要求其第一次執行時的類型。

例如，下列兩個版本的相同程式碼在不同時間載入相依性。

呼叫 `Program.GetRange()` 時，第一個版本一律載入自己的相依性，因為相依性參考是以語彙方式呈現在方法中：

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetRange(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library will be loaded when GetRange is run
                // because the dependency call occurs directly within the method
                DependencyApi.Use();
            }

            list.Add(i);
        }
        return list;
    }
}
```

而第二個版本只有在 `limit` 參數為 20 或以上時才會載入自己的相依性，因為是透過方法的內部間接取值：

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetNumbers(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library is only referenced within
                // the UseDependencyApi() method,
                // so will only be loaded when limit >= 20
                UseDependencyApi();
            }

            list.Add(i);
        }
        return list;
    }

    private static void UseDependencyApi()
    {
        // Once UseDependencyApi() is called, Dependency.Library is loaded
        DependencyApi.Use();
    }
}
```

這是很好的做法，因為既可將記憶體和檔案系統 I/O 降到最低，又能更有效率地使用資源。 但其副作用是，不到嘗試載入組件的程式碼路徑，不會知道組件無法載入。

這也會建立組件載入衝突的計時條件。 如果同一個程式有兩個部分嘗試載入同一組件的不同版本，則第一次執行的程式碼路徑會決定所載入版本。

對 PowerShell 而言，這表示下列因素會影響組件載入衝突：

- 首先載入哪一個模組？
- 執行了使用相依性程式庫的程式碼路徑嗎？
- PowerShell 是在啟動時載入衝突的相依性，或只在特定程式碼路徑下才會載入衝突的相依性？

## <a name="quick-fixes-and-their-limitations"></a>快速修正及其限制

在某些情況下，您可微幅調整模組，並以最不費力的方式來修正問題。 但這些解決方案通常會附帶一些注意事項。 其也許可能適用於模組，卻不適用於所有模組。

### <a name="change-your-dependency-version"></a>變更相依性版本

避免發生相依性衝突的最簡單方式就是同意相依性。 可能的狀況如下：

- 衝突來自於模組的直接相依性，且您控制了版本。
- 衝突來自於間接相依性，但您可設定直接相依性，令其使用可行的間接相依性版本。
- 您知道發生衝突的版本，且依賴其的不變更。

`Newtonsoft.Json` 套件是最後一種情況的絕佳範例。 這是 PowerShell 6 及更新版本的相依性，不會用在 Windows PowerShell 中。 這表示解析版本控制衝突的簡單方法，就是在您希望作為目標的所有 PowerShell 版本中，以最低版本的 `Newtonsoft.Json` 為目標。

例如，PowerShell 6.2.6 和 PowerShell 7.0.2 目前都使用 12.0.3 版的 `Newtonsoft.Json`。 因此，若要建立以 Windows PowerShell、PowerShell 6 和 PowerShell 7 為目標的模組，則要使用 `Newtonsoft.Json 12.0.3` 作為相依性目標，並包含在建置模組中。 在 PowerShell 6 或 7 中載入模組時，即已載入 PowerShell 自己的 `Newtonsoft.Json` 組件。 而且，至少是模組所需版本，所以解析成功。 在 Windows PowerShell 中，組件尚未出現在 PowerShell 中。 所以會改從模組資料夾載入。

一般以具體的 PowerShell 套件 (例如 `Microsoft.PowerShell.Sdk` 或 `System.Management.Automation`) 為目標時，NuGet 應該能夠解析所需的正確相依性版本。 以 Windows PowerShell 和 PowerShell 6+ 為目標會更加困難，因為必須選擇以多個架構或以 `PowerShellStandard.Library` 為目標。

無法釘選到通用相依性版本的情況包括：

- 衝突來自間接相依性，且所有相依性皆無法設定為使用通用版本。
- 其他相依性版本可能經常變更，因此設定通用版本只能短期修正問題。

### <a name="add-an-assemblyresolve-event-handler-to-create-a-dynamic-binding-redirect"></a>新增 AssemblyResolve 事件處理常式以建立動態繫結重新導向

變更自己的相依性版本，有時不太可能或太難。 另一個選項是註冊 `AssemblyResolve` 事件的事件處理常式，以設定動態繫結重新導向。

和靜態繫結重新導向一樣，重點在於強制某個相依性的所有取用者都使用相同的實際組件。 您要攔截載入相依性的呼叫，並將其一律重新導向至所要的版本。

看起來如下：

```csharp
// Register the event handler as early as you can in your code.
// A good option is to use the IModuleAssemblyInitializer interface
// that PowerShell provides to run code early on when your module is loaded.

// This class will be instantiated on module import and the OnImport() method run.
// Make sure that:
//  - the class is public
//  - the class has a public, parameterless constructor
//  - the class implements IModuleAssemblyInitializer
public class MyModuleInitializer : IModuleAssemblyInitializer
{
    public void OnImport()
    {
        AppDomain.CurrentDomain.AssemblyResolve += DependencyResolution.ResolveNewtonsoftJson;
    }
}

// Clean up the event handler when the the module is removed
// to prevent memory leaks.
//
// Like IModuleAssemblyInitializer, IModuleAssemblyCleanup allows
// you to register code to run when a module is removed (with Remove-Module).
// Make sure it is also public with a public parameterless contructor
// and implements IModuleAssemblyCleanup.
public class MyModuleCleanup : IModuleAssemblyCleanup
{
    public void OnRemove()
    {
        AppDomain.CurrentDomain.AssemblyResolve -= DependencyResolution.ResolveNewtonsoftJson;
    }
}

internal static class DependencyResolution
{
    private static readonly string s_modulePath = Path.GetDirectoryName(
        Assembly.GetExecutingAssembly().Location);

    public static Assembly ResolveNewtonsoftJson(object sender, ResolveEventArgs args)
    {
        // Parse the assembly name
        var assemblyName = new AssemblyName(args.Name);

        // We only want to handle the dependency we care about.
        // In this example it's Newtonsoft.Json.
        if (!assemblyName.Name.Equals("Newtonsoft.Json"))
        {
            return null;
        }

        // Generally the version of the dependency you want to load is the higher one,
        // since it's the most likely to be compatible with all dependent assemblies.
        // The logic here assumes our module always has the version we want to load.
        // Also note the use of Assembly.LoadFrom() here rather than Assembly.LoadFile().
        return Assembly.LoadFrom(Path.Combine(s_modulePath, "Newtonsoft.Json.dll"));
    }
}
```

技術上，您可在 PowerShell 中註冊 ScriptBlock 以處理 `AssemblyResolve` 事件，但：

- 任何執行緒上都可能觸發 `AssemblyResolve` 事件，PowerShell 有時都無法處理。
- 即使在正確的執行緒上處理了事件，PowerShell 的範圍概念也表示必須謹慎寫入事件處理常式 ScriptBlock，而不要相依於在其外部定義的變數。

有時候，重新導向至通用版本無效：

- 當多個版本間的相依性出現重大變更時，或相依的程式碼若不依賴某個功能，即無法在所重新導向的版本中使用。
- 先載入發生衝突的相依性，後載入模組時。 如果在載入相依性之後才註冊 `AssemblyResolve` 事件處理常式，則永遠不會引發。 如果嘗試避免與另一個模組發生相依性衝突，這可能會造成問題，因為其他模組可能已先行載入。

### <a name="use-the-dependency-out-of-process"></a>在程序外使用相依性

此解決方案更適合模組使用者，較不偏向模組作者。 當模組因現有相依性衝突而無法作用時，可使用此解決方案。

相依性衝突發生的原因，是在相同 .NET 程序中載入了兩個版本的相同組件。 簡單的解決方法是將組件載入至不同程序，只要仍然可同時使用兩者的功能即可。

PowerShell 中有數種方法可達到此目標：

- 將 PowerShell 叫用為子程序

  在目前程序外執行 PowerShell 命令的簡單方法，就是直接使用命令呼叫來啟動新的 PowerShell 程序：

  ```powershell
  pwsh -c 'Invoke-ConflictingCommand'
  ```

  此方法的主要限制是重組結果可能更棘手，或比其他選項更容易發生錯誤。

- PowerShell 工作系統

  PowerShell 工作系統也會將命令傳送至新的 PowerShell 程序並傳回結果，以在程序外執行命令：

  ```powershell
  $result = Start-Job { Invoke-ConflictingCommand } | Receive-Job -Wait
  ```

  如此一來，您只需要確定所有變數和狀態皆已正確傳遞即可。

  工作系統在執行小型命令時，也略為繁瑣。

- PowerShell 遠端

  當可用時，PowerShell 遠端是在程序外執行命令的實用方式。 您可透過遠端在新的程序中建立全新 **PSSession**、透過 PowerShell 遠端呼叫其命令，然後在本機使用結果及包含衝突相依性的其他模組。

  範例可能會如下：

  ```powershell
  # Create a local PowerShell session
  # where the module with conflicting assemblies will be loaded
  $s = New-PSSession

  # Import the module with the conflicting dependency via remoting,
  # exposing the commands locally
  Import-Module -PSSession $s -Name ConflictingModule

  # Run a command from the module with the conflicting dependencies
  Invoke-ConflictingCommand
  ```

- Windows PowerShell 隱含的遠端功能

  PowerShell 7 還有另一個選項，是在 `Import-Module` 上使用 `-UseWindowsPowerShell` 旗標。 這會透過本機遠端工作階段將模組匯入 Windows PowerShell：

  ```powershell
  Import-Module -Name ConflictingModule -UseWindowsPowerShell
  ```

  請注意，模組可能無法配合 Windows PowerShell，或運作方式不同。

#### <a name="when-out-of-process-invocation-should-not-be-used"></a>不應使用程序外叫用的情況

身為模組作者，程序外命令調用很難併入模組中，且可能會有造成問題的邊緣案例。 特別是在模組需要運作的所有環境中，可能無法使用遠端功能和工作。 不過，將實作移出程序，允許 PowerShell 模組成為更精簡用戶端的一般原則，仍然適用。

身為模組使用者，有時候程序外叫用無法正常執行：

- 因為您無權使用 PowerShell 遠端或其未啟用，以致無法使用時。
- 當需要輸出中特定 .NET 類型作為方法或其他命令的輸入時。
  透過 PowerShell 遠端所執行命令會發出還原序列化的物件，而不是強型別的 .NET 物件。 這表示方法呼叫和強型別 API 都不適用透過遠端匯入的命令輸出。

## <a name="more-robust-solutions"></a>更強大的解決方案

前述解決方案都有不適用的案例和模組。 但其也都相當簡單，可正確實作。 下列解決方案較強大，但需要花費更多精力才能正確執行，且若撰寫不慎，可能會造成微小的錯誤。

### <a name="loading-through-net-core-assembly-load-contexts"></a>透過 .NET Core 組件載入內容載入

[組件載入內容](/dotnet/api/system.runtime.loader.assemblyloadcontext) (ALC) 是可實作的 API，早在 .NET Core 1.0 中即已引入，專門用來處理將多個版本其相同組件載入同一執行階段的需求。

.NET Core 和 .NET 5 為載入組件衝突版本的問題提供了強大解決方案。 不過，.NET Framework 中無法使用自訂的 ALC。 這表示此解決方案僅適用於 PowerShell 6 和更新版本。

目前，在 PowerShell 中使用 ALC 隔離相依性的最佳範例，是 PowerShell 編輯器服務中，適用於 Visual Studio Code 的 PowerShell 延伸模組的語言伺服器。 [ALC](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs) 旨在防止 PowerShell 編輯器服務的自有相依性與 PowerShell 模組中相依性發生衝突。

使用 ALC 實作模組相依性隔離，在概念上很困難，但我們會利用最基本的範例來逐步解說。 假設我們有一個簡單模組，其僅適用於 PowerShell 7。
原始程式碼的組織方式如下：

```
+ AlcModule.psd1
+ src/
    + TestAlcModuleCommand.cs
    + AlcModule.csproj
```

Cmdlet 的實作看起來如下：

```csharp
using Shared.Dependency;

namespace AlcModule
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            // Here's where our dependency gets used
            Dependency.Use();
            // Something trivial to make our cmdlet do *something*
            WriteObject("done!");
        }
    }
}
```

(已大幅簡化的) 資訊清單看起來如下：

```powershell
@{
    Author = 'Me'
    ModuleVersion = '0.0.1'
    RootModule = 'AlcModule.dll'
    CmdletsToExport = @('Test-AlcModule')
    PowerShellVersion = '7.0'
}
```

`csproj` 看起來如下：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

當建置此模組時，所產生的輸出會有下列配置：

```
AlcModule/
  + AlcModule.psd1
  + AlcModule.dll
  + Shared.Dependency.dll
```

在此範例中，問題出在 `Shared.Dependency.dll` 組件，這是假想的衝突相依性。 這個相依性需要放在 ALC 後面，以便使用模組特定版本。

我們需要重新設計模組，以便：

- 模組相依性只會載入至自訂的 ALC，不會載入到 PowerShell 的 ALC，所以不會發生衝突。 此外，當在專案中新增更多相依性時，我們不希望為了讓載入保持運作而持續新增更多程式碼。 而是想要可重複使用的一般相依性解析邏輯。
- 載入模組仍可在 PowerShell 中如常運作。 PowerShell 模組系統所需 Cmdlet 和其他類型是在 PowerShell 專屬的 ALC 中定義。

為協調這兩種需求，則必須將模組分成兩個組件：

- Cmdlet 組件 `AlcModule.Cmdlets.dll`，包含 PowerShell 模組系統正確載入模組所需的所有類型定義。 亦即，`Cmdlet` 基底類別及實作 `IModuleAssemblyInitializer` 的類別其所有實作，會透過自訂的 ALC，將 `AssemblyLoadContext.Default.Resolving` 的事件處理常式設定為可正確載入 `AlcModule.Engine.dll`。 因為 PowerShell 7 刻意隱藏在其他 ALC 載入組件中所定義的類型，所以您也必須在這裡定義要向 PowerShell 公開的所有類型。 最後，我們必須在這個組件中定義自訂的 ALC 定義。 此外，這個組件中應盡可能不要留存程式碼。
- 引擎組件 `AlcModule.Engine.dll`，負責處理模組的實際實作。
  PowerShell ALC 中可使用來自此組件的類型，但其一開始要透過自訂的 ALC 載入。 其相依性只會載入自訂的 ALC。 實際上，這會成為兩個 ALC 之間的「橋樑」。

使用此橋接概念，新組件的情況會如下：

![AlcModule.Engine.dll 橋接兩個 ALC 的示意圖](./media/resolving-dependency-conflicts/alc-diagram.jpg)

為確保預設 ALC 其相依性探查邏輯不會解析要載入到自訂 ALC 的相依性，我們必須將此模組的兩個部分放在不同目錄中。 新模組配置具有下列結構：

```
AlcModule/
  AlcModule.Cmdlets.dll
  AlcModule.psd1
  Dependencies/
  | + AlcModule.Engine.dll
  | + Shared.Dependency.dll
```

為查看實作變更的方式，我們將從 `AlcModule.Engine.dll` 的實作開始：

```csharp
using Shared.Dependency;

namespace AlcModule.Engine
{
    public class AlcEngine
    {
        public static void Use()
        {
            Dependency.Use();
        }
    }
}
```

`Shared.Dependency.dll` 是簡單的相依性容器，但應視為 PowerShell 其他組件換行 Cmdlet 功能的 .NET API。

`AlcModule.Cmdlets.dll` 中的 Cmdlet 看起來如下：

```csharp
// Reference our module's Engine implementation here
using AlcModule.Engine;

namespace AlcModule.Cmdlets
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            AlcEngine.Use();
            WriteObject("done!");
        }
    }
}
```

此時，如果要載入 **AlcModule** 並執行 `Test-AlcModule`，則當預設 ALC 嘗試載入 `Alc.Engine.dll` 以執行 `EndProcessing()` 時，就會得到 `FileNotFoundException`。 這很好，因為這表示預設 ALC 找不到我們想要隱藏的相依性。

現在，我們需要將程式碼新增至 `AlcModule.Cmdlets.dll`，以便其知道如何解析 `AlcModule.Engine.dll`。 首先，我們必須定義會從模組其 `Dependencies` 目錄解析組件的自訂 ALC：

```csharp
namespace AlcModule.Cmdlets
{
    internal class AlcModuleAssemblyLoadContext : AssemblyLoadContext
    {
        private readonly string _dependencyDirPath;

        public AlcModuleAssemblyLoadContext(string dependencyDirPath)
        {
            _dependencyDirPath = dependencyDirPath;
        }

        protected override Assembly Load(AssemblyName assemblyName)
        {
            // We do the simple logic here of
            // looking for an assembly of the given name
            // in the configured dependency directory
            string assemblyPath = Path.Combine(
                _dependencyDirPath,
                $"{assemblyName.Name}.dll");

            // The ALC must use inherited methods to load assemblies
            // Assembly.Load*() won't work here
            return LoadFromAssemblyPath(assemblyPath);
        }
    }
}
```

然後，我們需要將自訂 ALC 連接至預設 ALC 的 `Resolving` 事件，這是應用程式定義域中 `AssemblyResolve` 事件的 ALC 版本。 當呼叫 `EndProcessing()` 時，就會引發此事件以尋找 `AlcModule.Engine.dll`。

```csharp
namespace AlcModule.Cmdlets
{
    public class AlcModuleResolveEventHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // Get the path of the dependency directory.
        // In this case we find it relative to the AlcModule.Cmdlets.dll location
        private static readonly string s_dependencyDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        private static readonly AlcModuleAssemblyLoadContext s_dependencyAlc = new AlcModuleAssemblyLoadContext(s_dependencyDirPath);

        public void OnImport()
        {
            // Add the Resolving event handler here
            AssemblyLoadContext.Default.Resolving += ResolveAlcEngine;
        }

        public void OnRemove()
        {
          // Remove the Resolving event handler here
          AssemblyLoadContext.Default.Resolving -= ResolveAlcEngine;
        }

        private static Assembly ResolveAlcEngine(
            AssemblyLoadContext defaultAlc,
            AssemblyName assemblyToResolve)
        {
            // We only want to resolve the Alc.Engine.dll assembly here.
            // Because this will be loaded into the custom ALC,
            // all of *its* dependencies will be resolved
            // by the logic we defined for that ALC's implementation.
            //
            // Note that we are safe in our assumption that the name is enough
            // to distinguish our assembly here,
            // since it's unique to our module.
            // There should be no other AlcModule.Engine.dll on the system.
            if (!assemblyToResolve.Name.Equals("AlcModule.Engine"))
            {
                return null;
            }

            // Allow our ALC to handle the directory discovery concept
            //
            // This is where Alc.Engine.dll is loaded into our custom ALC
            // and then passed through into PowerShell's ALC,
            // becoming the bridge between both
            return s_dependencyAlc.LoadFromAssemblyName(assemblyToResolve);
        }
    }
}
```

請藉由新的實作來查看載入模組並執行 `Test-AlcModule` 時所發生的呼叫順序：

![使用自訂 ALC 載入相依性的呼叫順序圖](./media/resolving-dependency-conflicts/alc-sequence.png)

要點如下：

- 當模組載入並設定 `Resolving` 事件時，會先執行 `IModuleAssemblyInitializer`。
- 執行 `Test-AlcModule` 且呼叫其 `EndProcessing()` 方法後才會載入相依性。
- 呼叫 `EndProcessing()` 時，預設 ALC 會找不到 `AlcModule.Engine.dll`，並引發 `Resolving` 事件。
- 事件處理常式會將自訂 ALC 連接至預設 ALC，並只載入 `AlcModule.Engine.dll`。
- 在 `AlcModule.Engine.dll` 中呼叫 `AlcEngine.Use()` 時，自訂 ALC 會再次開始解決 `Shared.Dependency.dll`。 具體而言，一律會載入`Shared.Dependency.dll`，因為其絕對不會與預設 ALC 中的任何內容發生衝突，且只會在 `Dependencies` 目錄中尋找。

組合實作時，新的原始程式碼配置看起來會如下：

```
+ AlcModule.psd1
+ src/
  + AlcModule.Cmdlets/
  | + AlcModule.Cmdlets.csproj
  | + TestAlcModuleCommand.cs
  | + AlcModuleAssemblyLoadContext.cs
  | + AlcModuleInitializer.cs
  |
  + AlcModule.Engine/
  | + AlcModule.Engine.csproj
  | + AlcEngine.cs
```

AlcModule.Cmdlets.csproj 看起來如下：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <ProjectReference Include="..\AlcModule.Engine\AlcModule.Engine.csproj" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

AlcModule.Engine.csproj 看起來如下：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
  </ItemGroup>
</Project>
```

因此，建置模組時，我們的策略是：

- 建置 `AlcModule.Engine`
- 建置 `AlcModule.Cmdlets`
- 將 `AlcModule.Engine` 所有的內容複製到 `Dependencies` 目錄，並記住所複製的內容
- 將 `AlcModule.Engine` 中沒有的全部 `AlcModule.Cmdlets` 內容複製到基底模組目錄

因為這裡的模組配置對分隔相依性很重要，所以要從來源根目錄使用建置指令碼：

```powershell
param(
    # The .NET build configuration
    [ValidateSet('Debug', 'Release')]
    [string]
    $Configuration = 'Debug'
)

# Convenient reusable constants
$mod = "AlcModule"
$netcore = "netcoreapp3.1"
$copyExtensions = @('.dll', '.pdb')

# Source code locations
$src = "$PSScriptRoot/src"
$engineSrc = "$src/$mod.Engine"
$cmdletsSrc = "$src/$mod.Cmdlets"

# Generated output locations
$outDir = "$PSScriptRoot/out/$mod"
$outDeps = "$outDir/Dependencies"

# Build AlcModule.Engine
Push-Location $engineSrc
dotnet publish -c $Configuration
Pop-Location

# Build AlcModule.Cmdlets
Push-Location $cmdletsSrc
dotnet publish -c $Configuration
Pop-Location

# Ensure out directory exists and is clean
Remove-Item -Path $outDir -Recurse -ErrorAction Ignore
New-Item -Path $outDir -ItemType Directory
New-Item -Path $outDeps -ItemType Directory

# Copy manifest
Copy-Item -Path "$PSScriptRoot/$mod.psd1"

# Copy each Engine asset and remember it
$deps = [System.Collections.Generic.Hashtable[string]]::new()
Get-ChildItem -Path "$engineSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { $_.Extension -in $copyExtensions } |
    ForEach-Object { [void]$deps.Add($_.Name); Copy-Item -Path $_.FullName -Destination $outDeps }

# Now copy each Cmdlets asset, not taking any found in Engine
Get-ChildItem -Path "$cmdletsSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { -not $deps.Contains($_.Name) -and $_.Extension -in $copyExtensions } |
    ForEach-Object { Copy-Item -Path $_.FullName -Destination $outDir }
```

最後，我們有個可使用組件載入內容隔離模組其相依性的一般方法，其會隨著與時俱增的相依性保持穩定。

如需更詳細的範例，請參閱此 [GitHub 存放庫](https://github.com/rjmholt/ModuleDependencyIsolationExample)。 此範例會示範如何移轉模組以使用 ALC，同時讓該模組能在 .NET Framework 中繼續運作。 其也會示範如何使用 .NET Standard 和 PowerShell Standard 來簡化核心實作。

### <a name="assembly-resolve-handler-for-side-by-side-loading-with-assemblyloadfile"></a>搭配 `Assembly.LoadFile()` 用於並存載入的組件解析處理常式

另一個可能較容易達到載入並存組件的方法，是將 `AssemblyResolve` 事件連接到 `Assembly.LoadFile()`。 使用 `Assembly.LoadFile()` 的優點是，這是實作及使用 .NET Core 和 .NET Framework 的最簡單解決方案。

讓我們以一個快速的實作範例示範，其結合了動態繫結重新導向範例的想法，以及前文的組件載入內容範例。

此模組稱為 **LoadFileModule**，其擁有一般的命令 `Test-LoadFile [-Path] <path>`。 此模組相依於 `CsvHelper` 組件 (15.0.5 版)。

和 ALC 模組一樣，我們必須先將模組分為兩部分。

第一個部分負責實際的實作，即 `LoadFileModule.Engine`：

```csharp
using CsvHelper;

namespace LoadFileModule.Engine
{
    public class Runner
    {
        public void Use(string path)
        {
            // Here's where we use the CsvHelper dependency
            using (var reader = new StreamReader(path))
            using (var csvReader = new CsvReader(reader, CultureInfo.InvariantCulture))
            {
                // Imagine we do something useful here...
            }
        }
    }
}
```

第二個部分是 PowerShell 直接載入的內容，即 `LoadFileModule.Cmdlets`。 我們使用的策略與 ALC 模組雷同，將相依性隔離在不同的目錄中。 但是這一次，我們會載入所有包含解析事件的組件，而不僅是 `LoadFileModule.Engine.dll`。

```csharp
using LoadFileModule.Engine;

namespace LoadFileModule.Cmdlets
{
    // Actual cmdlet definition
    [Cmdlet(VerbsDiagnostic.Test, "LoadFile")]
    public class TestLoadFileCommand : Cmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        protected override void EndProcessing()
        {
            // Here's where we use LoadFileModule.Engine
            new Runner().Use(Path);
        }
    }

    // This class controls our dependency resolution
    public class ModuleContextHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // We catalog our dependencies here to ensure we don't load anything else
        private static IReadOnlyDictionary<string, int> s_dependencies = new Dictionary<string, int>
        {
            { "CsvHelper", 15 },
        };

        // Set up the path to our dependency directory within the module
        private static string s_dependenciesDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        // This makes sure we only try to resolve dependencies when the module is loaded
        private static bool s_engineLoaded = false;

        public void OnImport()
          {
            // Set up our event when the module is loaded
            AppDomain.CurrentDomain.AssemblyResolve += HandleResolveEvent;
        }

        public void OnRemove(PSModuleInfo psModuleInfo)
        {
            // Unset the event when the module is unloaded
            AppDomain.CurrentDomain.AssemblyResolve -= HandleResolveEvent;
        }

        private static Assembly HandleResolveEvent(object sender, ResolveEventArgs args)
        {
            var asmName = new AssemblyName(args.Name);

            // First we want to know if this is the top-level assembly
            if (asmName.Name.Equals("LoadFileModule.Engine"))
            {
                s_engineLoaded = true;
                return Assembly.LoadFile(Path.Combine(s_dependenciesDirPath, "Unrelated.Engine.dll"));
            }

            // Otherwise, if that assembly has been loaded, we must try to resolve its dependencies too
            if (s_engineLoaded
                && s_dependencies.TryGetValue(asmName.Name, out int requiredMajorVersion)
                && asmName.Version.Major == requiredMajorVersion)
            {
                string asmPath = Path.Combine(s_dependenciesDirPath, $"{asmName.Name}.dll");
                return Assembly.LoadFile(asmPath);
            }

            return null;
        }
    }
}
```

最後，模組的配置也與 ALC 模組雷同：

```
LoadFileModule/
  + LoadFileModule.Cmdlets.dll
  + LoadFileModule.psd1
  + Dependencies/
  |  + LoadFileModule.Engine.dll
  |  + CsvHelper.dll
```

在此結構就緒後，**LoadFileModule** 現可支援與其他模組一起載入，且有 **CsvHelper** 相依性。

因為處理常式適用於整個應用程式定義域的 **所有** `AssemblyResolve` 事件，所以我們必須在此設計一些特定選項：

- 為縮小事件可能會干擾其他載入的時間範圍，我們只會在載入 `LoadFileModule.Engine.dll` 之後，再開始處理一般相依性載入。
- 我們會將 `LoadFileModule.Engine.dll` 推送至相依性目錄，使其由 `LoadFile()` 呼叫載入，而不是由 PowerShell 載入。 這表示它自己的相依性載入一律會引發 `AssemblyResolve` 事件，即使 PowerShell 中已載入另一個 (例如) `CsvHelper.dll`。
  這讓我們有機會找出正確的相依性。
- 因為我們必須只解析模組的特定相依性，所以我們不得不將相依性名稱和版本的字典編碼成處理常式。 在特定情況下，可使用 `ResolveEventArgs.RequestingAssembly` 屬性來得知模組是否正在要求 `CsvHelper`。 但這對相依性的相依性無效；例如，如果 `CsvHelper` 本身引發了 `AssemblyResolve` 事件。 還有其他更困難的方法可執行這項操作，例如比較要求的組件與 `Dependencies` 目錄中的組件中繼資料。 但是在此範例中，我們既醒目提示了問題又簡化了範例，讓這項檢查變得更明確。

這是 `LoadFile()` 策略與 ALC 策略之間的主要差異：`AssemblyResolve` 事件必須為應用程式定義域中的所有載入提供服務，讓相依性解析變得更困難，以免與其他模組糾纏不休。 不過，.NET Framework 中缺少 ALC 讓此選項更值得了解。

### <a name="custom-application-domains"></a>自訂的應用程式定義域

組件隔離的最後一個，也是最極端的選項，是使用自訂的應用程式定義域。
應用程式定義域 (複數名詞) 只能在 .NET Framework 中使用。 其可用來半隔離 .NET 應用程式的各組件。 其中一個用途是隔離同一程序中的組件載入。

不過，應用程式定義域是序列化界限。 一個應用程式定義域中物件無法直接參考及使用另一個應用程式定義域中的物件。 您可實作 `MarshalByRefObject` 以暫時解決這個問題。 但是若不控制類型，因為相依性常有這種情況，就無法在此強制實作。 大型架構化變更是唯一的解決之道。 序列化界限也會對效能造成嚴重影響。

因為應用程式定義域具有這項重大限制，實作很複雜，且只在 .NET Framework 中有效，所以本文不舉例示範使用方法。 雖然值得一提，但不建議這麼做。

如果想要嘗試使用自訂的應用程式定義域，下列連結可能會有所幫助：

- [有關應用程式定義域概念的文件](/dotnet/framework/app-domains/application-domains)
- [使用應用程式定義域的範例](/dotnet/framework/app-domains/use)

## <a name="solutions-for-dependency-conflicts-that-dont-work-for-powershell"></a>不適用於 PowerShell 的相依性衝突解決方案

最後，我們會討論在研究 .NET 的 .NET 相依性衝突時看起來很有希望的可能方案，但這些通常不適用於 PowerShell。

這些解決方案的共同主題是，會變更您控制應用程式，甚至可能是整部電腦的環境部署組態。 這些解決方案所適用案例為網頁伺服器和其他部署至伺服器環境的應用程式，此環境旨在裝載應用程式，且可供部署使用者自由設定。 其也非常適合 .NET Framework，這表示其不適用於 PowerShell 6 或更新版本。

如果確定模組僅用在您擁有完全控制權的 Windows PowerShell 5.1 環境中，則可嘗試其中一些方案。 不過，總而言之，**模組不應以此方式修改全域電腦狀態**。 這會中斷組態，導致 `powershell.exe`、其他模組，或造成模組以非預期方式失敗的其他相依應用程式發生問題。

### <a name="static-binding-redirect-with-appconfig-to-force-using-the-same-dependency-version"></a>使用 app.config 重新導向靜態繫結，以強制使用相同的相依性版本

.NET Framework 應用程式可利用 `app.config` 檔案，以宣告方式設定應用程式的部分行為。 您可撰寫 `app.config` 項目，將組件繫結設定為將組件載入重新導向至特定版本。

PowerShell 有關這方面的兩個問題如下：

- .NET Core 不支援 `app.config`，所以此方案僅適用於 `powershell.exe`。
- `powershell.exe` 是存在於 `System32` 目錄中的共用應用程式。 在許多系統上，模組很可能無法修改其內容。 即使可以，修改 `app.config` 可能會中斷現有組態，或影響其他模組載入。

### <a name="setting-codebase-with-appconfig"></a>使用 app.config 設定 `codebase`

基於相同的原因，嘗試在 `app.config` 中進行 `codebase` 設定在 PowerShell 模組中無效。

### <a name="installing-dependencies-to-the-global-assembly-cache-gac"></a>將相依性安裝到全域組件快取 (GAC)

解析 .NET Framework 相依性版本衝突的另一個方法是將相依性安裝到 GAC，以從 GAC 並存載入不同的版本。

再次說明，PowerShell 模組的主要問題是：

- GAC 僅適用於 .NET Framework，所以這對 PowerShell 6 和更新版本沒有幫助。
- 將組件安裝到 GAC 會修改全域電腦狀態，且可能對其他應用程式或其他模組產生副作用。 即使模組具有必要的存取權限，也不容易正確執行。 如果發生錯誤，可能會造成其他 .NET 應用程式嚴重的全電腦問題。

## <a name="further-reading"></a>進一步閱讀

.NET 組件版本相依性衝突還有許多內容值得了解。 以下是一些不錯的起點：

- [.NET：.NET 中的組件](/dotnet/standard/assembly/)
- [.NET Core：受控組件載入演算法](/dotnet/core/dependency-loading/loading-managed)
- [.NET Core：了解 System.Runtime.Loader.AssemblyLoadContext](/dotnet/core/dependency-loading/understanding-assemblyloadcontext)
- [.NET Core：討論有關並存組件載入的解決方案](https://github.com/dotnet/runtime/issues/13471)
- [.NET Framework：重新導向組件版本](/dotnet/framework/configure-apps/redirect-assembly-versions)
- [.NET Framework：組件載入的最佳做法](/dotnet/framework/deployment/best-practices-for-assembly-loading)
- [.NET Framework：執行階段如何找出組件](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [.NET Framework：解析組件載入](/dotnet/standard/assembly/resolve-loads)
- [StackOverflow：Assembly binding redirect, how and why?](https://stackoverflow.com/questions/43365736/assembly-binding-redirect-how-and-why) (組件繫結重新導向：方法及原因？)
- [PowerShell：討論如何實作 AssemblyLoadCoNtexts](https://github.com/PowerShell/PowerShell/issues/11571)
- [PowerShell：`Assembly.LoadFile()` 不會載入至預設的 AssemblyLoadCoNtext](https://github.com/PowerShell/PowerShell/issues/12052)
- [Rick Strahl：When does a .NET assembly dependency get loaded?](https://weblog.west-wind.com/posts/2012/Nov/03/Back-to-Basics-When-does-a-NET-Assembly-Dependency-get-loaded) (何時會載入 .NET 組件相依性？)
- [Jon Skeet：.NET 的版本控制摘要](https://codeblog.jonskeet.uk/2019/06/30/versioning-limitations-in-net/)
- [Nate McMaster：Deep dive into .NET Core primitives](https://natemcmaster.com/blog/2017/12/21/netcore-primitives/) (深入探討 .NET Core 的基本類型)
