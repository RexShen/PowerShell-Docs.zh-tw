---
description: PowerShell 中的「實驗性功能」支援能提供一個機制，使實驗性功能可以與 PowerShell 或 PowerShell 模組中的現有穩定功能並存。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 關於實驗性功能
ms.openlocfilehash: e53af155c2a8691e2e4d4cc6f47bfd5932801db9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208219"
---
# <a name="experimental-features"></a><span data-ttu-id="984e6-104">實驗性功能</span><span class="sxs-lookup"><span data-stu-id="984e6-104">Experimental Features</span></span>

<span data-ttu-id="984e6-105">PowerShell 中的「實驗性功能」支援能提供一個機制，使實驗性功能可以與 PowerShell 或 PowerShell 模組中的現有穩定功能並存。</span><span class="sxs-lookup"><span data-stu-id="984e6-105">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="984e6-106">實驗性功能是設計尚未完成的功能。</span><span class="sxs-lookup"><span data-stu-id="984e6-106">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="984e6-107">該功能可供使用者測試並提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="984e6-107">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="984e6-108">在實驗性功能完成之後，設計變更便會成為中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="984e6-108">Once an experimental feature is finalized, the design changes become breaking changes.</span></span> <span data-ttu-id="984e6-109">實驗性功能並不適用於生產環境，因為允許對其進行中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="984e6-109">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span>

<span data-ttu-id="984e6-110">實驗性功能預設為停用，且必須由系統的使用者或系統管理員明確地啟用。</span><span class="sxs-lookup"><span data-stu-id="984e6-110">Experimental features are disabled by default and need to be explicitly enabled by the user or administrator of the system.</span></span>

<span data-ttu-id="984e6-111">啟用的實驗性功能會列在的檔案中，以 `powershell.config.json` `$PSHOME` 供特定使用者或使用者特定的設定檔使用。</span><span class="sxs-lookup"><span data-stu-id="984e6-111">Enabled experimental features are listed in the `powershell.config.json` file in `$PSHOME` for all users or the user-specific configuration file for a specific user.</span></span>

> [!NOTE]
> <span data-ttu-id="984e6-112">在使用者設定檔中啟用的實驗性功能優先于系統設定檔中所列的實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="984e6-112">Experimental features enabled in the user configuration file take precedence over experimental features listed in the system configuration file.</span></span>

## <a name="the-experimental-attribute"></a><span data-ttu-id="984e6-113">實驗性屬性</span><span class="sxs-lookup"><span data-stu-id="984e6-113">The Experimental Attribute</span></span>

<span data-ttu-id="984e6-114">您 `Experimental` 可以使用屬性將某些程式碼宣告為實驗。</span><span class="sxs-lookup"><span data-stu-id="984e6-114">Use the `Experimental` attribute to declare some code as experimental.</span></span>

<span data-ttu-id="984e6-115">使用下列語法來宣告 `Experimental` 屬性（attribute），以提供實驗性功能的名稱，以及啟用實驗性功能時要採取的動作：</span><span class="sxs-lookup"><span data-stu-id="984e6-115">Use the following syntax to declare the `Experimental` attribute providing the name of the experimental feature and the action to take if the experimental feature is enabled:</span></span>

```csharp
[Experimental(NameOfExperimentalFeature, ExperimentAction)]
```

<span data-ttu-id="984e6-116">針對模組， `NameOfExperimentalFeature` 必須遵循的形式 `<modulename>.<experimentname>` 。</span><span class="sxs-lookup"><span data-stu-id="984e6-116">For modules, the `NameOfExperimentalFeature` must follow the form of `<modulename>.<experimentname>`.</span></span> <span data-ttu-id="984e6-117">`ExperimentAction`必須指定參數，且唯一有效的值為：</span><span class="sxs-lookup"><span data-stu-id="984e6-117">The `ExperimentAction` parameter must be specified and the only valid values are:</span></span>

- <span data-ttu-id="984e6-118">`Show` 表示在功能啟用時顯示此實驗性功能</span><span class="sxs-lookup"><span data-stu-id="984e6-118">`Show` means to show this experimental feature if the feature is enabled</span></span>
- <span data-ttu-id="984e6-119">`Hide` 表示在啟用功能時隱藏此實驗性功能</span><span class="sxs-lookup"><span data-stu-id="984e6-119">`Hide` means to hide this experimental feature if the feature is enabled</span></span>

### <a name="declaring-experimental-features-in-modules-written-in-c"></a><span data-ttu-id="984e6-120">宣告以 C 撰寫的模組中的實驗性功能\#</span><span class="sxs-lookup"><span data-stu-id="984e6-120">Declaring Experimental Features in Modules Written in C\#</span></span>

<span data-ttu-id="984e6-121">想要使用實驗性功能旗標的模組作者，可以使用屬性將 Cmdlet 宣告為實驗性 `Experimental` 。</span><span class="sxs-lookup"><span data-stu-id="984e6-121">Module authors who want to use the Experimental Feature flags can declare a cmdlet as experimental by using the `Experimental` attribute.</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }
```

### <a name="declaring-experimental-features-in-modules-written-in-powershell"></a><span data-ttu-id="984e6-122">宣告以 PowerShell 撰寫的模組中的實驗性功能</span><span class="sxs-lookup"><span data-stu-id="984e6-122">Declaring Experimental Features in Modules written in PowerShell</span></span>

<span data-ttu-id="984e6-123">以 PowerShell 撰寫的模組也可以使用 `Experimental` 屬性來宣告實驗性 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="984e6-123">Module written in PowerShell can also use the `Experimental` attribute to declare experimental cmdlets:</span></span>

```powershell
function Enable-SSHRemoting {
    [Experimental("MyRemoting.PSSSHRemoting", "Show")]
    [CmdletBinding()]
    param()
    ...
}
```

### <a name="mutually-exclusive-experimental-features"></a><span data-ttu-id="984e6-124">相互專屬的實驗性功能</span><span class="sxs-lookup"><span data-stu-id="984e6-124">Mutually Exclusive Experimental Features</span></span>

<span data-ttu-id="984e6-125">在某些情況下，實驗性功能無法與現有的功能並存並存，或另一個實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="984e6-125">There are cases where an experimental feature cannot co-exist side-by-side with an existing feature or another experimental feature.</span></span>

<span data-ttu-id="984e6-126">例如，您可以擁有可覆寫現有 Cmdlet 的實驗性 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="984e6-126">For example, you can have an experimental cmdlet that overrides an existing cmdlet.</span></span> <span data-ttu-id="984e6-127">這兩個版本無法並存並存。</span><span class="sxs-lookup"><span data-stu-id="984e6-127">The two versions can't coexist side by side.</span></span> <span data-ttu-id="984e6-128">此 `ExperimentAction.Hide` 設定只允許一次啟用兩個 Cmdlet 的其中一個。</span><span class="sxs-lookup"><span data-stu-id="984e6-128">The `ExperimentAction.Hide` setting allows only one of the two cmdlets to be enabled at one time.</span></span>

<span data-ttu-id="984e6-129">在此範例中，我們會建立新的實驗 `Invoke-WebRequest` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="984e6-129">In this example, we create a new experimental `Invoke-WebRequest` cmdlet.</span></span>
<span data-ttu-id="984e6-130">`InvokeWebRequestCommand` 包含非實驗性的執行。</span><span class="sxs-lookup"><span data-stu-id="984e6-130">`InvokeWebRequestCommand` contains the non-experimental implementation.</span></span>
<span data-ttu-id="984e6-131">`InvokeWebRequestCommandV2` 包含 Cmdlet 的實驗版本。</span><span class="sxs-lookup"><span data-stu-id="984e6-131">`InvokeWebRequestCommandV2` contains the experimental version of the cmdlet.</span></span>

<span data-ttu-id="984e6-132">使用時， `ExperimentAction.Hide` 只會允許一次啟用兩項功能的其中一個：</span><span class="sxs-lookup"><span data-stu-id="984e6-132">The use of `ExperimentAction.Hide` will allow only one of the two features to be enabled at one time:</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }

[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Hide)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommand : WebCmdletBase { ... }
```

<span data-ttu-id="984e6-133">`MyWebCmdlets.PSWebCmdletV2`啟用實驗性功能時，將 `InvokeWebRequestCommand` 會隱藏現有的執行，並 `InvokeWebRequestCommandV2` 提供的實作為 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="984e6-133">When the `MyWebCmdlets.PSWebCmdletV2` experimental feature is enabled, the existing `InvokeWebRequestCommand` implementation is hidden and the `InvokeWebRequestCommandV2` provides the implementation of `Invoke-WebRequest`.</span></span>

<span data-ttu-id="984e6-134">這可讓使用者試用新的 Cmdlet 並提供意見反應，然後在需要時還原為非實驗版本。</span><span class="sxs-lookup"><span data-stu-id="984e6-134">This allows users to try out the new cmdlet and provide feedback then revert to the non-experimental version when needed.</span></span>

### <a name="experimental-parameters-in-cmdlets"></a><span data-ttu-id="984e6-135">Cmdlet 中的實驗性參數</span><span class="sxs-lookup"><span data-stu-id="984e6-135">Experimental Parameters in Cmdlets</span></span>

<span data-ttu-id="984e6-136">`Experimental`屬性也可以套用至個別參數。</span><span class="sxs-lookup"><span data-stu-id="984e6-136">The `Experimental` attribute can also be applied to individual parameters.</span></span> <span data-ttu-id="984e6-137">這可讓您針對現有的 Cmdlet （而不是全新的 Cmdlet）建立一組實驗性的參數。</span><span class="sxs-lookup"><span data-stu-id="984e6-137">This allows you to create an experimental set of parameters for an existing cmdlet rather than an entirely new cmdlet.</span></span>

<span data-ttu-id="984e6-138">以下是 c # 中的範例：</span><span class="sxs-lookup"><span data-stu-id="984e6-138">Here is an example in C#:</span></span>

```csharp
[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Show)]
[Parameter(ParameterSet = "NewCompilation")]
public CompilationParameters CompileParameters { ... }

[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Hide)]
[Parameter()]
public CodeDom CodeDom { ... }
```

<span data-ttu-id="984e6-139">以下是 PowerShell 腳本中的不同範例：</span><span class="sxs-lookup"><span data-stu-id="984e6-139">Here is a different example in PowerShell script:</span></span>

```powershell
param(
    [Experimental("MyModule.PSNewFeature", "Show")]
    [string] $NewName,

    [Experimental("MyModule.PSNewFeature", "Hide")]
    [string] $OldName
)
```

## <a name="checking-if-an-experimental-feature-is-enabled"></a><span data-ttu-id="984e6-140">檢查是否已啟用實驗性功能</span><span class="sxs-lookup"><span data-stu-id="984e6-140">Checking if an Experimental Feature is Enabled</span></span>

<span data-ttu-id="984e6-141">在您的程式碼中，您必須先檢查實驗性功能是否已啟用，然後再採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="984e6-141">In your code, you will need to check if your experimental feature is enabled before taking appropriate action.</span></span> <span data-ttu-id="984e6-142">您可以使用類別上的靜態方法，判斷是否已啟用實驗性功能 `IsEnabled()` `System.Management.Automation.ExperimentalFeature` 。</span><span class="sxs-lookup"><span data-stu-id="984e6-142">You can determine if an experimental feature is enabled using the static `IsEnabled()` method on the `System.Management.Automation.ExperimentalFeature` class.</span></span>

<span data-ttu-id="984e6-143">以下是 c # 中的範例：</span><span class="sxs-lookup"><span data-stu-id="984e6-143">Here is an example in C#:</span></span>

```csharp
if (ExperimentalFeature.IsEnabled("MyModule.MyExperimentalFeature"))
{
   // code specific to the experimental feature
}
```

<span data-ttu-id="984e6-144">以下是 PowerShell 腳本中的範例：</span><span class="sxs-lookup"><span data-stu-id="984e6-144">Here is an example in PowerShell script:</span></span>

```powershell
if ([ExperimentalFeature]::IsEnabled("MyModule.MyExperimentalFeature"))
{
  # code specific to the experimental feature
}
```

## <a name="see-also"></a><span data-ttu-id="984e6-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="984e6-145">See also</span></span>

[<span data-ttu-id="984e6-146">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="984e6-146">Enable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Enable-ExperimentalFeature)

[<span data-ttu-id="984e6-147">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="984e6-147">Disable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Disable-ExperimentalFeature)

[<span data-ttu-id="984e6-148">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="984e6-148">Get-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Get-ExperimentalFeature)
