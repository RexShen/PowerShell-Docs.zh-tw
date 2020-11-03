---
description: 防止腳本在沒有必要元素的情況下執行。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: c6b10137ca58da93caff365a50b125929fd4d11a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208159"
---
# <a name="about-requires"></a><span data-ttu-id="887b6-104">關於需求</span><span class="sxs-lookup"><span data-stu-id="887b6-104">About Requires</span></span>

## <a name="short-description"></a><span data-ttu-id="887b6-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="887b6-105">Short description</span></span>
<span data-ttu-id="887b6-106">防止腳本在沒有必要元素的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="887b6-106">Prevents a script from running without the required elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="887b6-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="887b6-107">Long description</span></span>

<span data-ttu-id="887b6-108">此 `#Requires` 語句可防止腳本執行，除非 PowerShell 版本、模組 (和版本) 或嵌入式管理單元 (和版本) ，以及符合版本的必要條件。</span><span class="sxs-lookup"><span data-stu-id="887b6-108">The `#Requires` statement prevents a script from running unless the PowerShell version, modules (and version), or snap-ins (and version), and edition prerequisites are met.</span></span> <span data-ttu-id="887b6-109">如果不符合必要條件，則 PowerShell 不會執行腳本。</span><span class="sxs-lookup"><span data-stu-id="887b6-109">If the prerequisites aren't met, PowerShell doesn't run the script.</span></span>

### <a name="syntax"></a><span data-ttu-id="887b6-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="887b6-110">Syntax</span></span>

```
#Requires -Assembly { <Path to .dll> | <.NET assembly specification> }
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

<span data-ttu-id="887b6-111">如需語法的詳細資訊，請參閱 [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements)。</span><span class="sxs-lookup"><span data-stu-id="887b6-111">For more information about the syntax, see [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span></span>

### <a name="rules-for-use"></a><span data-ttu-id="887b6-112">使用的規則</span><span class="sxs-lookup"><span data-stu-id="887b6-112">Rules for use</span></span>

<span data-ttu-id="887b6-113">腳本可以包含一個以上的 `#Requires` 語句。</span><span class="sxs-lookup"><span data-stu-id="887b6-113">A script can include more than one `#Requires` statement.</span></span> <span data-ttu-id="887b6-114">這些 `#Requires` 語句可以出現在腳本中的任何一行。</span><span class="sxs-lookup"><span data-stu-id="887b6-114">The `#Requires` statements can appear on any line in a script.</span></span>

<span data-ttu-id="887b6-115">將語句放在函式 `#Requires` 內不會限制其範圍。</span><span class="sxs-lookup"><span data-stu-id="887b6-115">Placing a `#Requires` statement inside a function does NOT limit its scope.</span></span> <span data-ttu-id="887b6-116">所有 `#Requires` 語句一律會全域套用，而且必須符合，腳本才能執行。</span><span class="sxs-lookup"><span data-stu-id="887b6-116">All `#Requires` statements are always applied globally, and must be met, before the script can execute.</span></span>

> [!WARNING]
> <span data-ttu-id="887b6-117">雖然 `#Requires` 語句可以出現在腳本中的任何一行，但它在腳本中的位置並不會影響其應用程式的順序。</span><span class="sxs-lookup"><span data-stu-id="887b6-117">Even though a `#Requires` statement can appear on any line in a script, its position in a script does not affect the sequence of its application.</span></span> <span data-ttu-id="887b6-118">在 `#Requires` 腳本執行之前，必須符合語句所呈現的全域狀態。</span><span class="sxs-lookup"><span data-stu-id="887b6-118">The global state the `#Requires` statement presents must be met before script execution.</span></span>

<span data-ttu-id="887b6-119">範例：</span><span class="sxs-lookup"><span data-stu-id="887b6-119">Example:</span></span>

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

<span data-ttu-id="887b6-120">您可能會認為上述程式碼不應該執行，因為必要的模組會在 `#Requires` 語句之前移除。</span><span class="sxs-lookup"><span data-stu-id="887b6-120">You might think that the above code shouldn't run because the required module was removed before the `#Requires` statement.</span></span> <span data-ttu-id="887b6-121">不過，在 `#Requires` 腳本甚至可以執行之前，必須先符合狀態。</span><span class="sxs-lookup"><span data-stu-id="887b6-121">However, the `#Requires` state had to be met before the script could even execute.</span></span> <span data-ttu-id="887b6-122">然後，腳本的第一行會使所需的狀態失效。</span><span class="sxs-lookup"><span data-stu-id="887b6-122">Then the first line of the script invalidated the required state.</span></span>

### <a name="parameters"></a><span data-ttu-id="887b6-123">參數</span><span class="sxs-lookup"><span data-stu-id="887b6-123">Parameters</span></span>

#### <a name="-assembly-assembly-path--net-assembly-specification"></a><span data-ttu-id="887b6-124">-Assembly \<Assembly path> |\<.NET assembly specification></span><span class="sxs-lookup"><span data-stu-id="887b6-124">-Assembly \<Assembly path> | \<.NET assembly specification></span></span>

<span data-ttu-id="887b6-125">指定元件 DLL 檔案的路徑或 .NET 元件名稱。</span><span class="sxs-lookup"><span data-stu-id="887b6-125">Specifies the path to the assembly DLL file or a .NET assembly name.</span></span> <span data-ttu-id="887b6-126">**元件** 參數是在 PowerShell 5.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="887b6-126">The **Assembly** parameter was introduced in PowerShell 5.0.</span></span> <span data-ttu-id="887b6-127">如需 .NET 元件的詳細資訊，請參閱 [元件名稱](/dotnet/standard/assembly/names)。</span><span class="sxs-lookup"><span data-stu-id="887b6-127">For more information about .NET assemblies, see [Assembly names](/dotnet/standard/assembly/names).</span></span>

<span data-ttu-id="887b6-128">例如：</span><span class="sxs-lookup"><span data-stu-id="887b6-128">For example:</span></span>

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a><span data-ttu-id="887b6-129">-Version \<N\> [. \<n\> ]</span><span class="sxs-lookup"><span data-stu-id="887b6-129">-Version \<N\>[.\<n\>]</span></span>

<span data-ttu-id="887b6-130">指定腳本所需的 PowerShell 最低版本。</span><span class="sxs-lookup"><span data-stu-id="887b6-130">Specifies the minimum version of PowerShell that the script requires.</span></span> <span data-ttu-id="887b6-131">輸入主要版本號碼和選用的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="887b6-131">Enter a major version number and optional minor version number.</span></span>

<span data-ttu-id="887b6-132">例如：</span><span class="sxs-lookup"><span data-stu-id="887b6-132">For example:</span></span>

```powershell
#Requires -Version 6.0
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a><span data-ttu-id="887b6-133">-PSSnapin \<PSSnapin-Name\> [-Version \<N\> [. \<n\> ]]</span><span class="sxs-lookup"><span data-stu-id="887b6-133">-PSSnapin \<PSSnapin-Name\> [-Version \<N\>[.\<n\>]]</span></span>

<span data-ttu-id="887b6-134">指定腳本需要的 PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="887b6-134">Specifies a PowerShell snap-in that the script requires.</span></span> <span data-ttu-id="887b6-135">輸入嵌入式管理單元名稱和選用的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="887b6-135">Enter the snap-in name and an optional version number.</span></span>

<span data-ttu-id="887b6-136">例如：</span><span class="sxs-lookup"><span data-stu-id="887b6-136">For example:</span></span>

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a><span data-ttu-id="887b6-137">-模組 \<Module-Name\> |\<Hashtable\></span><span class="sxs-lookup"><span data-stu-id="887b6-137">-Modules \<Module-Name\> | \<Hashtable\></span></span>

<span data-ttu-id="887b6-138">指定腳本需要的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="887b6-138">Specifies PowerShell modules that the script requires.</span></span> <span data-ttu-id="887b6-139">輸入模組名稱和選用的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="887b6-139">Enter the module name and an optional version number.</span></span>

<span data-ttu-id="887b6-140">如果必要的模組不在目前的會話中，則 PowerShell 會將它們匯入。</span><span class="sxs-lookup"><span data-stu-id="887b6-140">If the required modules aren't in the current session, PowerShell imports them.</span></span>
<span data-ttu-id="887b6-141">如果無法匯入模組，則 PowerShell 會擲回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="887b6-141">If the modules can't be imported, PowerShell throws a terminating error.</span></span>

<span data-ttu-id="887b6-142">針對每個模組，輸入 (\<String\>) 或雜湊表的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="887b6-142">For each module, type the module name (\<String\>) or a hash table.</span></span> <span data-ttu-id="887b6-143">此值可以是字串和雜湊表的組合。</span><span class="sxs-lookup"><span data-stu-id="887b6-143">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="887b6-144">雜湊表具有下列索引鍵。</span><span class="sxs-lookup"><span data-stu-id="887b6-144">The hash table has the following keys.</span></span>

- <span data-ttu-id="887b6-145">`ModuleName` - **必要** 指定模組名稱。</span><span class="sxs-lookup"><span data-stu-id="887b6-145">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="887b6-146">`GUID` - **選擇性** 指定模組的 GUID。</span><span class="sxs-lookup"><span data-stu-id="887b6-146">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="887b6-147">您也 **必須** 指定下列三個索引鍵中的其中一個。</span><span class="sxs-lookup"><span data-stu-id="887b6-147">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="887b6-148">這些金鑰無法一起使用。</span><span class="sxs-lookup"><span data-stu-id="887b6-148">These keys can't be used together.</span></span>
  - <span data-ttu-id="887b6-149">`ModuleVersion` -指定模組可接受的最小版本。</span><span class="sxs-lookup"><span data-stu-id="887b6-149">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="887b6-150">`RequiredVersion` -指定完全必要的模組版本。</span><span class="sxs-lookup"><span data-stu-id="887b6-150">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="887b6-151">`MaximumVersion` -指定模組可接受的最大版本。</span><span class="sxs-lookup"><span data-stu-id="887b6-151">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="887b6-152">`RequiredVersion` 已在 Windows PowerShell 5.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="887b6-152">`RequiredVersion` was added in Windows PowerShell 5.0.</span></span>
> <span data-ttu-id="887b6-153">`MaximumVersion` 已在 Windows PowerShell 5.1 中新增。</span><span class="sxs-lookup"><span data-stu-id="887b6-153">`MaximumVersion` was added in Windows PowerShell 5.1.</span></span>

<span data-ttu-id="887b6-154">例如：</span><span class="sxs-lookup"><span data-stu-id="887b6-154">For example:</span></span>

<span data-ttu-id="887b6-155">需要 `AzureRM.Netcore` 安裝 (版 `0.12.0` 或更高的) 。</span><span class="sxs-lookup"><span data-stu-id="887b6-155">Require that `AzureRM.Netcore` (version `0.12.0` or greater) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; ModuleVersion="0.12.0" }
```

<span data-ttu-id="887b6-156">要求 `AzureRM.Netcore` **只** 安裝 (版本 `0.12.0`) 。</span><span class="sxs-lookup"><span data-stu-id="887b6-156">Require that `AzureRM.Netcore` ( **only** version `0.12.0`) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12.0" }
```

<span data-ttu-id="887b6-157">需要 `AzureRM.Netcore` 安裝 (版本 `0.12.0` 或較少的) 。</span><span class="sxs-lookup"><span data-stu-id="887b6-157">Requires that `AzureRM.Netcore` (version `0.12.0` or lesser) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; MaximumVersion="0.12.0" }
```

<span data-ttu-id="887b6-158">需要安裝任何版本的 `AzureRM.Netcore` 和 `PowerShellGet` 。</span><span class="sxs-lookup"><span data-stu-id="887b6-158">Require that any version of `AzureRM.Netcore` and `PowerShellGet` is installed.</span></span>

```powershell
#Requires -Modules AzureRM.Netcore, PowerShellGet
```

<span data-ttu-id="887b6-159">使用金鑰時 `RequiredVersion` ，請確定您的版本字串完全符合所需的版本字串。</span><span class="sxs-lookup"><span data-stu-id="887b6-159">When using the `RequiredVersion` key, ensure your version string exactly matches the version string you require.</span></span>

```powershell
Get-Module AzureRM.Netcore -ListAvailable
```

```Output
    Directory: /home/azureuser/.local/share/powershell/Modules

ModuleType Version Name            PSEdition ExportedCommands
---------- ------- ----            --------- ----------------
Script     0.12.0  AzureRM.Netcore Core
```

<span data-ttu-id="887b6-160">下列範例會失敗，因為 **0.12** 與 **v0.12.0** 完全相符。</span><span class="sxs-lookup"><span data-stu-id="887b6-160">The following example fails because **0.12** doesn't exactly match **0.12.0** .</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12" }
```

#### <a name="-psedition-psedition-name"></a><span data-ttu-id="887b6-161">-PSEdition \<PSEdition-Name\></span><span class="sxs-lookup"><span data-stu-id="887b6-161">-PSEdition \<PSEdition-Name\></span></span>

<span data-ttu-id="887b6-162">指定腳本需要的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="887b6-162">Specifies a PowerShell edition that the script requires.</span></span> <span data-ttu-id="887b6-163">有效的值為 PowerShell Core 的 **核心** 和 Windows PowerShell 的 **桌面** 。</span><span class="sxs-lookup"><span data-stu-id="887b6-163">Valid values are **Core** for PowerShell Core and **Desktop** for Windows PowerShell.</span></span>

<span data-ttu-id="887b6-164">例如：</span><span class="sxs-lookup"><span data-stu-id="887b6-164">For example:</span></span>

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a><span data-ttu-id="887b6-165">-ShellId</span><span class="sxs-lookup"><span data-stu-id="887b6-165">-ShellId</span></span>

<span data-ttu-id="887b6-166">指定腳本所需的 shell。</span><span class="sxs-lookup"><span data-stu-id="887b6-166">Specifies the shell that the script requires.</span></span> <span data-ttu-id="887b6-167">輸入 shell 識別碼。</span><span class="sxs-lookup"><span data-stu-id="887b6-167">Enter the shell ID.</span></span> <span data-ttu-id="887b6-168">如果您使用 **ShellId** 參數，則也必須包含 **PSSnapin** 參數。</span><span class="sxs-lookup"><span data-stu-id="887b6-168">If you use the **ShellId** parameter, you must also include the **PSSnapin** parameter.</span></span>
<span data-ttu-id="887b6-169">您可以藉由查詢自動變數來尋找目前的 **ShellId** `$ShellId` 。</span><span class="sxs-lookup"><span data-stu-id="887b6-169">You can find the current **ShellId** by querying the `$ShellId` automatic variable.</span></span>

<span data-ttu-id="887b6-170">例如：</span><span class="sxs-lookup"><span data-stu-id="887b6-170">For example:</span></span>

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> <span data-ttu-id="887b6-171">這個參數的目的是要在已被取代的迷你 shell 中使用。</span><span class="sxs-lookup"><span data-stu-id="887b6-171">This parameter is intended for use in mini-shells, which have been deprecated.</span></span>

#### <a name="-runasadministrator"></a><span data-ttu-id="887b6-172">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="887b6-172">-RunAsAdministrator</span></span>

<span data-ttu-id="887b6-173">當此切換參數加入至您的 `#Requires` 語句時，它會指定您要在其中執行腳本的 PowerShell 會話必須以提高的使用者權限來啟動。</span><span class="sxs-lookup"><span data-stu-id="887b6-173">When this switch parameter is added to your `#Requires` statement, it specifies that the PowerShell session in which you're running the script must be started with elevated user rights.</span></span> <span data-ttu-id="887b6-174">非 Windows 作業系統會忽略 **RunAsAdministrator** 參數。</span><span class="sxs-lookup"><span data-stu-id="887b6-174">The **RunAsAdministrator** parameter is ignored on a non-Windows operating system.</span></span> <span data-ttu-id="887b6-175">**RunAsAdministrator** 參數是在 PowerShell 4.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="887b6-175">The **RunAsAdministrator** parameter was introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="887b6-176">例如：</span><span class="sxs-lookup"><span data-stu-id="887b6-176">For example:</span></span>

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a><span data-ttu-id="887b6-177">範例</span><span class="sxs-lookup"><span data-stu-id="887b6-177">Examples</span></span>

<span data-ttu-id="887b6-178">下列腳本有兩個 `#Requires` 語句。</span><span class="sxs-lookup"><span data-stu-id="887b6-178">The following script has two `#Requires` statements.</span></span> <span data-ttu-id="887b6-179">如果不符合這兩個語句中指定的需求，腳本就不會執行。</span><span class="sxs-lookup"><span data-stu-id="887b6-179">If the requirements specified in both statements aren't met, the script doesn't run.</span></span> <span data-ttu-id="887b6-180">每個 `#Requires` 語句都必須是該行的第一個專案：</span><span class="sxs-lookup"><span data-stu-id="887b6-180">Each `#Requires` statement must be the first item on a line:</span></span>

```powershell
#Requires -Modules AzureRM.Netcore
#Requires -Version 6.0
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a><span data-ttu-id="887b6-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="887b6-181">See also</span></span>

[<span data-ttu-id="887b6-182">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="887b6-182">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="887b6-183">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="887b6-183">about_Language_Keywords</span></span>](about_Language_Keywords.md)
