---
description: 說明語言模式及其對 PowerShell 會話的影響。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: 91e3021c854945d86822c5d8219542eff7118aa7
ms.sourcegitcommit: fb1a4bc4b249afd3513663de2e1ba3025d63467e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2020
ms.locfileid: "94625647"
---
# <a name="about-language-modes"></a><span data-ttu-id="213a6-104">關於語言模式</span><span class="sxs-lookup"><span data-stu-id="213a6-104">About Language Modes</span></span>

## <a name="short-description"></a><span data-ttu-id="213a6-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="213a6-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="213a6-106">說明語言模式及其對 PowerShell 會話的影響。</span><span class="sxs-lookup"><span data-stu-id="213a6-106">Explains language modes and their effect on PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="213a6-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="213a6-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="213a6-108">PowerShell 會話的語言模式會決定可以在會話中使用 PowerShell 語言的哪些元素。</span><span class="sxs-lookup"><span data-stu-id="213a6-108">The language mode of a PowerShell session determines, in part, which elements of the PowerShell language can be used in the session.</span></span>

<span data-ttu-id="213a6-109">PowerShell 支援下列語言模式：</span><span class="sxs-lookup"><span data-stu-id="213a6-109">PowerShell supports the following language modes:</span></span>

- <span data-ttu-id="213a6-110">FullLanguage</span><span class="sxs-lookup"><span data-stu-id="213a6-110">FullLanguage</span></span>
- <span data-ttu-id="213a6-111">PowerShell 3.0 中引進的 ConstrainedLanguage () </span><span class="sxs-lookup"><span data-stu-id="213a6-111">ConstrainedLanguage (introduced in PowerShell 3.0)</span></span>
- <span data-ttu-id="213a6-112">RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="213a6-112">RestrictedLanguage</span></span>
- <span data-ttu-id="213a6-113">NoLanguage</span><span class="sxs-lookup"><span data-stu-id="213a6-113">NoLanguage</span></span>

### <a name="what-is-a-language-mode"></a><span data-ttu-id="213a6-114">什麼是語言模式？</span><span class="sxs-lookup"><span data-stu-id="213a6-114">WHAT IS A LANGUAGE MODE?</span></span>

<span data-ttu-id="213a6-115">語言模式會決定會話中允許的語言元素。</span><span class="sxs-lookup"><span data-stu-id="213a6-115">The language mode determines the language elements that are permitted in the session.</span></span>

<span data-ttu-id="213a6-116">語言模式實際上是會話設定的屬性 (或用來建立會話的「端點」 ) 。</span><span class="sxs-lookup"><span data-stu-id="213a6-116">The language mode is actually a property of the session configuration (or "endpoint") that is used to create the session.</span></span> <span data-ttu-id="213a6-117">使用特定會話設定的所有會話都具有會話設定的語言模式。</span><span class="sxs-lookup"><span data-stu-id="213a6-117">All sessions that use a particular session configuration have the language mode of the session configuration.</span></span>

<span data-ttu-id="213a6-118">所有的 PowerShell 會話都有語言模式，包括您使用 Cmdlet 建立的 Pssession `New-PSSession` 、使用 ComputerName 參數的暫時會話，以及啟動 PowerShell 時出現的預設會話。</span><span class="sxs-lookup"><span data-stu-id="213a6-118">All PowerShell sessions have a language mode, including PSSessions that you create by using the `New-PSSession` cmdlet, temporary sessions that use the ComputerName parameter, and the default sessions that appear when you start PowerShell.</span></span>

<span data-ttu-id="213a6-119">遠端會話是使用遠端電腦上的會話設定所建立。</span><span class="sxs-lookup"><span data-stu-id="213a6-119">Remote sessions are created by using the session configurations on the remote computer.</span></span> <span data-ttu-id="213a6-120">會話設定中設定的語言模式會決定會話的語言模式。</span><span class="sxs-lookup"><span data-stu-id="213a6-120">The language mode set in the session configuration determines the language mode of the session.</span></span> <span data-ttu-id="213a6-121">若要指定 PSSession 的會話設定，請使用建立會話之 Cmdlet 的 ConfigurationName 參數。</span><span class="sxs-lookup"><span data-stu-id="213a6-121">To specify the session configuration of a PSSession, use the ConfigurationName parameter of cmdlets that create a session.</span></span>

### <a name="language-modes"></a><span data-ttu-id="213a6-122">語言模式</span><span class="sxs-lookup"><span data-stu-id="213a6-122">LANGUAGE MODES</span></span>

<span data-ttu-id="213a6-123">本節說明 PowerShell 會話中的語言模式。</span><span class="sxs-lookup"><span data-stu-id="213a6-123">This section describes the language modes in PowerShell sessions.</span></span>

#### <a name="full-language-fulllanguage"></a><span data-ttu-id="213a6-124">完整語言 (>fulllanguage) </span><span class="sxs-lookup"><span data-stu-id="213a6-124">FULL LANGUAGE (FullLanguage)</span></span>

<span data-ttu-id="213a6-125">>fulllanguage 模式允許會話中的所有語言元素。</span><span class="sxs-lookup"><span data-stu-id="213a6-125">The FullLanguage mode permits all language elements in the session.</span></span>
<span data-ttu-id="213a6-126">>fulllanguage 是所有 Windows 版本上預設會話的預設語言模式，但 Windows RT 除外。</span><span class="sxs-lookup"><span data-stu-id="213a6-126">FullLanguage is the default language mode for default sessions on all versions of Windows except for Windows RT.</span></span>

#### <a name="restricted-language-restrictedlanguage"></a><span data-ttu-id="213a6-127">受限制的語言 (RestrictedLanguage) </span><span class="sxs-lookup"><span data-stu-id="213a6-127">RESTRICTED LANGUAGE (RestrictedLanguage)</span></span>

<span data-ttu-id="213a6-128">在 RestrictedLanguage 模式中，使用者可 (Cmdlet、函式、CIM 命令和工作流程執行命令) 但不允許使用腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="213a6-128">In RestrictedLanguage mode, users may run commands (cmdlets, functions, CIM commands, and workflows) but are not permitted to use script blocks.</span></span>

<span data-ttu-id="213a6-129">根據預設，RestrictedLanguage 模式中只允許下列變數：</span><span class="sxs-lookup"><span data-stu-id="213a6-129">By default, only the following variables are permitted in RestrictedLanguage mode:</span></span>

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

<span data-ttu-id="213a6-130">只允許下列比較運算子：</span><span class="sxs-lookup"><span data-stu-id="213a6-130">Only the following comparison operators are permitted:</span></span>

- <span data-ttu-id="213a6-131">`-eq` (等於) </span><span class="sxs-lookup"><span data-stu-id="213a6-131">`-eq` (equal)</span></span>
- <span data-ttu-id="213a6-132">`-gt` (大於) </span><span class="sxs-lookup"><span data-stu-id="213a6-132">`-gt` (greater-than)</span></span>
- <span data-ttu-id="213a6-133">`-lt` (小於) </span><span class="sxs-lookup"><span data-stu-id="213a6-133">`-lt` (less-than)</span></span>

<span data-ttu-id="213a6-134">不允許指派陳述式、屬性參照及方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="213a6-134">Assignment statements, property references, and method calls are not permitted.</span></span>

#### <a name="no-language-nolanguage"></a><span data-ttu-id="213a6-135">沒有語言 (NoLanguage) </span><span class="sxs-lookup"><span data-stu-id="213a6-135">NO LANGUAGE (NoLanguage)</span></span>

<span data-ttu-id="213a6-136">NoLanguage 模式只能透過 API 使用。</span><span class="sxs-lookup"><span data-stu-id="213a6-136">NoLanguage mode can only be used through the API.</span></span> <span data-ttu-id="213a6-137">NoLanguage 模式表示不允許任何表單的腳本文字。</span><span class="sxs-lookup"><span data-stu-id="213a6-137">NoLanguage mode means no script text of any form is permitted.</span></span> <span data-ttu-id="213a6-138">這樣就不會使用 **AddScript ( # B1** 方法來傳送要剖析和執行的 PowerShell 腳本片段。</span><span class="sxs-lookup"><span data-stu-id="213a6-138">This precludes the use of the **AddScript()** method which sends fragments of PowerShell script to be parsed and executed.</span></span> <span data-ttu-id="213a6-139">您只能使用 **AddCommand ( # B1** 和 **AddParameter ( # B3** ，而不會經過剖析器。</span><span class="sxs-lookup"><span data-stu-id="213a6-139">You can only use **AddCommand()** and **AddParameter()** which don't go through the parser.</span></span>

#### <a name="constrained-language-constrained-language"></a><span data-ttu-id="213a6-140">受限語言 (受限語言) </span><span class="sxs-lookup"><span data-stu-id="213a6-140">CONSTRAINED LANGUAGE (Constrained Language)</span></span>

<span data-ttu-id="213a6-141">ConstrainedLanguage 模式允許所有 Cmdlet 和所有 PowerShell 語言元素，但它會限制允許的類型。</span><span class="sxs-lookup"><span data-stu-id="213a6-141">The ConstrainedLanguage mode permits all cmdlets and all PowerShell language elements, but it limits permitted types.</span></span>

<span data-ttu-id="213a6-142">ConstrainedLanguage 模式是設計用來支援 Windows RT 上的使用者模式程式碼完整性 (UMCI) 。</span><span class="sxs-lookup"><span data-stu-id="213a6-142">ConstrainedLanguage mode is designed to support User Mode Code Integrity (UMCI) on Windows RT.</span></span> <span data-ttu-id="213a6-143">它是 Windows RT 上唯一支援的語言模式，但可在所有支援的系統上使用。</span><span class="sxs-lookup"><span data-stu-id="213a6-143">It is the only supported language mode on Windows RT, but it is available on all supported systems.</span></span>

<span data-ttu-id="213a6-144">UMCI 藉由只允許在 Windows RT 型裝置上安裝 Microsoft 簽署和經 Microsoft 認證的應用程式，來保護 ARM 裝置。</span><span class="sxs-lookup"><span data-stu-id="213a6-144">UMCI protects ARM devices by allowing only Microsoft-signed and Microsoft-certified apps to be installed on Windows RT-based devices.</span></span>
<span data-ttu-id="213a6-145">ConstrainedLanguage 模式會防止使用者使用 PowerShell 規避或違反 UMCI。</span><span class="sxs-lookup"><span data-stu-id="213a6-145">ConstrainedLanguage mode prevents users from using PowerShell to circumvent or violate UMCI.</span></span>

<span data-ttu-id="213a6-146">ConstrainedLanguage 模式的功能如下所示：</span><span class="sxs-lookup"><span data-stu-id="213a6-146">The features of ConstrainedLanguage mode are as follows:</span></span>

- <span data-ttu-id="213a6-147">Windows 模組中的所有 Cmdlet，以及其他 UMCI 核准的 Cmdlet 皆可完全正常運作，並可完整存取系統資源（如所述除外）。</span><span class="sxs-lookup"><span data-stu-id="213a6-147">All cmdlets in Windows modules, and other UMCI-approved cmdlets, are fully functional and have complete access to system resources, except as noted.</span></span>

- <span data-ttu-id="213a6-148">允許 PowerShell 指令碼語言的所有元素。</span><span class="sxs-lookup"><span data-stu-id="213a6-148">All elements of the PowerShell scripting language are permitted.</span></span>

- <span data-ttu-id="213a6-149">您可以匯入 Windows 中包含的所有模組，以及模組匯出在會話中執行的所有命令。</span><span class="sxs-lookup"><span data-stu-id="213a6-149">All modules included in Windows can be imported and all commands that the modules export run in the session.</span></span>

- <span data-ttu-id="213a6-150">在 PowerShell 工作流程中，您可以撰寫和執行以 PowerShell 語言) 撰寫 (工作流程的腳本工作流程。</span><span class="sxs-lookup"><span data-stu-id="213a6-150">In PowerShell Workflow, you can write and run script workflows (workflows written in the PowerShell language).</span></span> <span data-ttu-id="213a6-151">不支援以 XAML 為基礎的工作流程，而且您無法在腳本工作流程（例如使用）中執行 XAML `Invoke-Expression -Language XAML` 。</span><span class="sxs-lookup"><span data-stu-id="213a6-151">XAML-based workflows are not supported and you cannot run XAML in a script workflow, such as by using `Invoke-Expression -Language XAML`.</span></span> <span data-ttu-id="213a6-152">此外，工作流程無法呼叫其他工作流程，雖然允許嵌套工作流程。</span><span class="sxs-lookup"><span data-stu-id="213a6-152">Also, workflows cannot call other workflows, although nested workflows are permitted.</span></span>

- <span data-ttu-id="213a6-153">`Add-Type`Cmdlet 可以載入已簽署的元件，但無法載入任意的 c # 程式碼或 Win32 api。</span><span class="sxs-lookup"><span data-stu-id="213a6-153">The `Add-Type` cmdlet can load signed assemblies, but it cannot load arbitrary C# code or Win32 APIs.</span></span>

- <span data-ttu-id="213a6-154">此 `New-Object` Cmdlet 只能用在以下) 所列的允許類型 (：</span><span class="sxs-lookup"><span data-stu-id="213a6-154">The `New-Object` cmdlet can be used only on allowed types (listed below).</span></span>

- <span data-ttu-id="213a6-155">只有下面所列的允許類型 (可在 PowerShell 中使用) 。</span><span class="sxs-lookup"><span data-stu-id="213a6-155">Only allowed types (listed below) can be used in PowerShell.</span></span> <span data-ttu-id="213a6-156">不允許其他類型。</span><span class="sxs-lookup"><span data-stu-id="213a6-156">Other types are not permitted.</span></span>

- <span data-ttu-id="213a6-157">允許類型轉換，但只有在結果是允許的類型時。</span><span class="sxs-lookup"><span data-stu-id="213a6-157">Type conversion is permitted, but only when the result is an allowed type.</span></span>

- <span data-ttu-id="213a6-158">只有當產生的型別是允許的型別時，才會將字串輸入轉換成類型的 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="213a6-158">Cmdlet parameters that convert string input to types work only when the resulting type is an allowed type.</span></span>

- <span data-ttu-id="213a6-159">您可以叫用 **ToString ( # B1** 方法和允許類型 (的 .net 方法，如下所示) 。</span><span class="sxs-lookup"><span data-stu-id="213a6-159">The **ToString()** method and the .NET methods of allowed types (listed below) can be invoked.</span></span> <span data-ttu-id="213a6-160">無法叫用其他方法。</span><span class="sxs-lookup"><span data-stu-id="213a6-160">Other methods cannot be invoked.</span></span>

- <span data-ttu-id="213a6-161">使用者可以取得允許類型的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="213a6-161">Users can get all properties of allowed types.</span></span> <span data-ttu-id="213a6-162">使用者只能在核心類型上設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="213a6-162">Users can set the values of properties only on Core types.</span></span> <span data-ttu-id="213a6-163">只允許下列 COM 物件：</span><span class="sxs-lookup"><span data-stu-id="213a6-163">Only the following COM objects are permitted:</span></span>

  - <span data-ttu-id="213a6-164">**腳本字典**</span><span class="sxs-lookup"><span data-stu-id="213a6-164">**Scripting.Dictionary**</span></span>
  - <span data-ttu-id="213a6-165">**Scripting.FileSystemObject**</span><span class="sxs-lookup"><span data-stu-id="213a6-165">**Scripting.FileSystemObject**</span></span>
  - <span data-ttu-id="213a6-166">**VBScript. RegExp**</span><span class="sxs-lookup"><span data-stu-id="213a6-166">**VBScript.RegExp**</span></span>

<span data-ttu-id="213a6-167">以下是在 ConstrainedLanguage 模式中允許的類型。</span><span class="sxs-lookup"><span data-stu-id="213a6-167">The following types are permitted in ConstrainedLanguage mode.</span></span> <span data-ttu-id="213a6-168">使用者可以取得屬性、叫用方法，以及將物件轉換為這些類型。</span><span class="sxs-lookup"><span data-stu-id="213a6-168">Users can get properties, invoke methods, and convert objects to these types.</span></span>

<span data-ttu-id="213a6-169">允許的類型：</span><span class="sxs-lookup"><span data-stu-id="213a6-169">Allowed Types:</span></span>

- <span data-ttu-id="213a6-170">AliasAttribute</span><span class="sxs-lookup"><span data-stu-id="213a6-170">AliasAttribute</span></span>
- <span data-ttu-id="213a6-171">AllowEmptyCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="213a6-171">AllowEmptyCollectionAttribute</span></span>
- <span data-ttu-id="213a6-172">AllowEmptyStringAttribute</span><span class="sxs-lookup"><span data-stu-id="213a6-172">AllowEmptyStringAttribute</span></span>
- <span data-ttu-id="213a6-173">AllowNullAttribute</span><span class="sxs-lookup"><span data-stu-id="213a6-173">AllowNullAttribute</span></span>
- <span data-ttu-id="213a6-174">Array</span><span class="sxs-lookup"><span data-stu-id="213a6-174">Array</span></span>
- <span data-ttu-id="213a6-175">Bool</span><span class="sxs-lookup"><span data-stu-id="213a6-175">Bool</span></span>
- <span data-ttu-id="213a6-176">byte</span><span class="sxs-lookup"><span data-stu-id="213a6-176">byte</span></span>
- <span data-ttu-id="213a6-177">char</span><span class="sxs-lookup"><span data-stu-id="213a6-177">char</span></span>
- <span data-ttu-id="213a6-178">CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="213a6-178">CmdletBindingAttribute</span></span>
- <span data-ttu-id="213a6-179">Datetime</span><span class="sxs-lookup"><span data-stu-id="213a6-179">DateTime</span></span>
- <span data-ttu-id="213a6-180">decimal</span><span class="sxs-lookup"><span data-stu-id="213a6-180">decimal</span></span>
- <span data-ttu-id="213a6-181">DirectoryEntry</span><span class="sxs-lookup"><span data-stu-id="213a6-181">DirectoryEntry</span></span>
- <span data-ttu-id="213a6-182">DirectorySearcher</span><span class="sxs-lookup"><span data-stu-id="213a6-182">DirectorySearcher</span></span>
- <span data-ttu-id="213a6-183">double</span><span class="sxs-lookup"><span data-stu-id="213a6-183">double</span></span>
- <span data-ttu-id="213a6-184">FLOAT</span><span class="sxs-lookup"><span data-stu-id="213a6-184">float</span></span>
- <span data-ttu-id="213a6-185">Guid</span><span class="sxs-lookup"><span data-stu-id="213a6-185">Guid</span></span>
- <span data-ttu-id="213a6-186">雜湊表</span><span class="sxs-lookup"><span data-stu-id="213a6-186">Hashtable</span></span>
- <span data-ttu-id="213a6-187">int</span><span class="sxs-lookup"><span data-stu-id="213a6-187">int</span></span>
- <span data-ttu-id="213a6-188">Int16</span><span class="sxs-lookup"><span data-stu-id="213a6-188">Int16</span></span>
- <span data-ttu-id="213a6-189">long</span><span class="sxs-lookup"><span data-stu-id="213a6-189">long</span></span>
- <span data-ttu-id="213a6-190">ManagementClass</span><span class="sxs-lookup"><span data-stu-id="213a6-190">ManagementClass</span></span>
- <span data-ttu-id="213a6-191">System.management.managementobject</span><span class="sxs-lookup"><span data-stu-id="213a6-191">ManagementObject</span></span>
- <span data-ttu-id="213a6-192">ManagementObjectSearcher</span><span class="sxs-lookup"><span data-stu-id="213a6-192">ManagementObjectSearcher</span></span>
- <span data-ttu-id="213a6-193">NullString</span><span class="sxs-lookup"><span data-stu-id="213a6-193">NullString</span></span>
- <span data-ttu-id="213a6-194">OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="213a6-194">OutputTypeAttribute</span></span>
- <span data-ttu-id="213a6-195">ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="213a6-195">ParameterAttribute</span></span>
- <span data-ttu-id="213a6-196">PSCredential</span><span class="sxs-lookup"><span data-stu-id="213a6-196">PSCredential</span></span>
- <span data-ttu-id="213a6-197">PSDefaultValueAttribute</span><span class="sxs-lookup"><span data-stu-id="213a6-197">PSDefaultValueAttribute</span></span>
- <span data-ttu-id="213a6-198">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="213a6-198">PSListModifier</span></span>
- <span data-ttu-id="213a6-199">PSObject</span><span class="sxs-lookup"><span data-stu-id="213a6-199">PSObject</span></span>
- <span data-ttu-id="213a6-200">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="213a6-200">PSPrimitiveDictionary</span></span>
- <span data-ttu-id="213a6-201">PSReference</span><span class="sxs-lookup"><span data-stu-id="213a6-201">PSReference</span></span>
- <span data-ttu-id="213a6-202">PSTypeNameAttribute</span><span class="sxs-lookup"><span data-stu-id="213a6-202">PSTypeNameAttribute</span></span>
- <span data-ttu-id="213a6-203">Regex</span><span class="sxs-lookup"><span data-stu-id="213a6-203">Regex</span></span>
- <span data-ttu-id="213a6-204">SByte</span><span class="sxs-lookup"><span data-stu-id="213a6-204">SByte</span></span>
- <span data-ttu-id="213a6-205">字串</span><span class="sxs-lookup"><span data-stu-id="213a6-205">string</span></span>
- <span data-ttu-id="213a6-206">SupportsWildcardsAttribute</span><span class="sxs-lookup"><span data-stu-id="213a6-206">SupportsWildcardsAttribute</span></span>
- <span data-ttu-id="213a6-207">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="213a6-207">SwitchParameter</span></span>
- <span data-ttu-id="213a6-208">System.Globalization.CultureInfo</span><span class="sxs-lookup"><span data-stu-id="213a6-208">System.Globalization.CultureInfo</span></span>
- <span data-ttu-id="213a6-209">系統 .Net IPAddress</span><span class="sxs-lookup"><span data-stu-id="213a6-209">System.Net.IPAddress</span></span>
- <span data-ttu-id="213a6-210">系統 .Net MailAddress</span><span class="sxs-lookup"><span data-stu-id="213a6-210">System.Net.Mail.MailAddress</span></span>
- <span data-ttu-id="213a6-211">BigInteger</span><span class="sxs-lookup"><span data-stu-id="213a6-211">System.Numerics.BigInteger</span></span>
- <span data-ttu-id="213a6-212">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="213a6-212">System.Security.SecureString</span></span>
- <span data-ttu-id="213a6-213">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="213a6-213">TimeSpan</span></span>
- <span data-ttu-id="213a6-214">UInt16</span><span class="sxs-lookup"><span data-stu-id="213a6-214">UInt16</span></span>
- <span data-ttu-id="213a6-215">UInt32</span><span class="sxs-lookup"><span data-stu-id="213a6-215">UInt32</span></span>
- <span data-ttu-id="213a6-216">UInt64</span><span class="sxs-lookup"><span data-stu-id="213a6-216">UInt64</span></span>

### <a name="finding-the-language-mode-of-a-session-configuration"></a><span data-ttu-id="213a6-217">尋找會話設定的語言模式</span><span class="sxs-lookup"><span data-stu-id="213a6-217">FINDING THE LANGUAGE MODE OF A SESSION CONFIGURATION</span></span>

<span data-ttu-id="213a6-218">使用會話設定檔建立會話設定時，會話設定具有 LanguageMode 屬性。</span><span class="sxs-lookup"><span data-stu-id="213a6-218">When a session configuration is created by using a session configuration file, the session configuration has a LanguageMode property.</span></span> <span data-ttu-id="213a6-219">您可以藉由取得 LanguageMode 屬性的值來尋找語言模式。</span><span class="sxs-lookup"><span data-stu-id="213a6-219">You can find the language mode by getting the value of the LanguageMode property.</span></span>

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

<span data-ttu-id="213a6-220">在其他會話設定中，您可以藉由尋找使用會話設定建立之會話的語言模式，來間接找到語言模式。</span><span class="sxs-lookup"><span data-stu-id="213a6-220">On other session configurations, you can find the language mode indirectly by finding the language mode of a session that is created by using the session configuration.</span></span>

### <a name="finding-the-language-mode-of-a-session"></a><span data-ttu-id="213a6-221">尋找會話的語言模式</span><span class="sxs-lookup"><span data-stu-id="213a6-221">FINDING THE LANGUAGE MODE OF A SESSION</span></span>

<span data-ttu-id="213a6-222">您可以取得會話狀態的 LanguageMode 屬性值，以尋找 >fulllanguage 或 ConstrainedLanguage 會話的語言模式。</span><span class="sxs-lookup"><span data-stu-id="213a6-222">You can find the language mode of a FullLanguage or ConstrainedLanguage session by getting the value of the LanguageMode property of the session state.</span></span>

<span data-ttu-id="213a6-223">例如：</span><span class="sxs-lookup"><span data-stu-id="213a6-223">For example:</span></span>

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

<span data-ttu-id="213a6-224">不過，在具有 RestrictedLanguage 和 NoLanguage 模式的會話中，您無法使用點方法來取得屬性值。</span><span class="sxs-lookup"><span data-stu-id="213a6-224">However, in sessions with RestrictedLanguage and NoLanguage modes, you cannot use the dot method to get property values.</span></span> <span data-ttu-id="213a6-225">相反地，錯誤訊息會顯示語言模式。</span><span class="sxs-lookup"><span data-stu-id="213a6-225">Instead, the error message reveals the language mode.</span></span>

<span data-ttu-id="213a6-226">當您 `$ExecutionContext.SessionState.LanguageMode` 在 RestrictedLanguage 會話中執行命令時，PowerShell 會傳回 PropertyReferenceNotSupportedInDataSection 和 VariableReferenceNotSupportedInDataSection 錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="213a6-226">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a RestrictedLanguage session, PowerShell returns the PropertyReferenceNotSupportedInDataSection and VariableReferenceNotSupportedInDataSection error messages.</span></span>

- <span data-ttu-id="213a6-227">PropertyReferenceNotSupportedInDataSection：不允許在受限制的語言模式或資料區段中使用屬性參考。</span><span class="sxs-lookup"><span data-stu-id="213a6-227">PropertyReferenceNotSupportedInDataSection: Property references are not allowed in restricted language mode or a Data section.</span></span>
- <span data-ttu-id="213a6-228">VariableReferenceNotSupportedInDataSection 無法在受限制的語言模式下參考的變數，或參考的資料區段。</span><span class="sxs-lookup"><span data-stu-id="213a6-228">VariableReferenceNotSupportedInDataSection A variable that cannot be referenced in restricted language mode or a Data section is being referenced.</span></span>

<span data-ttu-id="213a6-229">當您 `$ExecutionContext.SessionState.LanguageMode` 在 NoLanguage 會話中執行命令時，PowerShell 會傳回 ScriptsNotAllowed 錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="213a6-229">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a NoLanguage session, PowerShell returns the ScriptsNotAllowed error message.</span></span>

- <span data-ttu-id="213a6-230">ScriptsNotAllowed：此執行空間不支援語法。</span><span class="sxs-lookup"><span data-stu-id="213a6-230">ScriptsNotAllowed: The syntax is not supported by this runspace.</span></span> <span data-ttu-id="213a6-231">這可能是因為它在無語言模式中。</span><span class="sxs-lookup"><span data-stu-id="213a6-231">This might be because it is in no-language mode.</span></span>

## <a name="see-also"></a><span data-ttu-id="213a6-232">另請參閱</span><span class="sxs-lookup"><span data-stu-id="213a6-232">SEE ALSO</span></span>

- [<span data-ttu-id="213a6-233">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="213a6-233">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)
- [<span data-ttu-id="213a6-234">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="213a6-234">about_Session_Configurations</span></span>](about_Session_Configurations.md)
