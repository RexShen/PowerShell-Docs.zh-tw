---
description: 說明語言模式及其對 PowerShell 會話的影響。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: 0b94125574bc65359b264225bb6c64231c1052d7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206507"
---
# <a name="about-language-modes"></a><span data-ttu-id="432e3-104">關於語言模式</span><span class="sxs-lookup"><span data-stu-id="432e3-104">About Language Modes</span></span>

## <a name="short-description"></a><span data-ttu-id="432e3-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="432e3-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="432e3-106">說明語言模式及其對 PowerShell 會話的影響。</span><span class="sxs-lookup"><span data-stu-id="432e3-106">Explains language modes and their effect on PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="432e3-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="432e3-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="432e3-108">PowerShell 會話的語言模式會決定可以在會話中使用 PowerShell 語言的哪些元素。</span><span class="sxs-lookup"><span data-stu-id="432e3-108">The language mode of a PowerShell session determines, in part, which elements of the PowerShell language can be used in the session.</span></span>

<span data-ttu-id="432e3-109">PowerShell 支援下列語言模式：</span><span class="sxs-lookup"><span data-stu-id="432e3-109">PowerShell supports the following language modes:</span></span>

- <span data-ttu-id="432e3-110">FullLanguage</span><span class="sxs-lookup"><span data-stu-id="432e3-110">FullLanguage</span></span>
- <span data-ttu-id="432e3-111">PowerShell 3.0 中引進的 ConstrainedLanguage () </span><span class="sxs-lookup"><span data-stu-id="432e3-111">ConstrainedLanguage (introduced in PowerShell 3.0)</span></span>
- <span data-ttu-id="432e3-112">RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="432e3-112">RestrictedLanguage</span></span>
- <span data-ttu-id="432e3-113">NoLanguage</span><span class="sxs-lookup"><span data-stu-id="432e3-113">NoLanguage</span></span>

### <a name="what-is-a-language-mode"></a><span data-ttu-id="432e3-114">什麼是語言模式？</span><span class="sxs-lookup"><span data-stu-id="432e3-114">WHAT IS A LANGUAGE MODE?</span></span>

<span data-ttu-id="432e3-115">語言模式會決定會話中允許的語言元素。</span><span class="sxs-lookup"><span data-stu-id="432e3-115">The language mode determines the language elements that are permitted in the session.</span></span>

<span data-ttu-id="432e3-116">語言模式實際上是會話設定的屬性 (或用來建立會話的「端點」 ) 。</span><span class="sxs-lookup"><span data-stu-id="432e3-116">The language mode is actually a property of the session configuration (or "endpoint") that is used to create the session.</span></span> <span data-ttu-id="432e3-117">使用特定會話設定的所有會話都具有會話設定的語言模式。</span><span class="sxs-lookup"><span data-stu-id="432e3-117">All sessions that use a particular session configuration have the language mode of the session configuration.</span></span>

<span data-ttu-id="432e3-118">所有的 PowerShell 會話都有語言模式，包括您使用 Cmdlet 建立的 Pssession `New-PSSession` 、使用 ComputerName 參數的暫時會話，以及啟動 PowerShell 時出現的預設會話。</span><span class="sxs-lookup"><span data-stu-id="432e3-118">All PowerShell sessions have a language mode, including PSSessions that you create by using the `New-PSSession` cmdlet, temporary sessions that use the ComputerName parameter, and the default sessions that appear when you start PowerShell.</span></span>

<span data-ttu-id="432e3-119">遠端會話是使用遠端電腦上的會話設定所建立。</span><span class="sxs-lookup"><span data-stu-id="432e3-119">Remote sessions are created by using the session configurations on the remote computer.</span></span> <span data-ttu-id="432e3-120">會話設定中設定的語言模式會決定會話的語言模式。</span><span class="sxs-lookup"><span data-stu-id="432e3-120">The language mode set in the session configuration determines the language mode of the session.</span></span> <span data-ttu-id="432e3-121">若要指定 PSSession 的會話設定，請使用建立會話之 Cmdlet 的 ConfigurationName 參數。</span><span class="sxs-lookup"><span data-stu-id="432e3-121">To specify the session configuration of a PSSession, use the ConfigurationName parameter of cmdlets that create a session.</span></span>

### <a name="language-modes"></a><span data-ttu-id="432e3-122">語言模式</span><span class="sxs-lookup"><span data-stu-id="432e3-122">LANGUAGE MODES</span></span>

<span data-ttu-id="432e3-123">本節說明 PowerShell 會話中的語言模式。</span><span class="sxs-lookup"><span data-stu-id="432e3-123">This section describes the language modes in PowerShell sessions.</span></span>

#### <a name="full-language-fulllanguage"></a><span data-ttu-id="432e3-124">完整語言 (>fulllanguage) </span><span class="sxs-lookup"><span data-stu-id="432e3-124">FULL LANGUAGE (FullLanguage)</span></span>

<span data-ttu-id="432e3-125">>fulllanguage 模式允許會話中的所有語言元素。</span><span class="sxs-lookup"><span data-stu-id="432e3-125">The FullLanguage mode permits all language elements in the session.</span></span>
<span data-ttu-id="432e3-126">>fulllanguage 是所有 Windows 版本上預設會話的預設語言模式，但 Windows RT 除外。</span><span class="sxs-lookup"><span data-stu-id="432e3-126">FullLanguage is the default language mode for default sessions on all versions of Windows except for Windows RT.</span></span>

#### <a name="restricted-language-restrictedlanguage"></a><span data-ttu-id="432e3-127">受限制的語言 (RestrictedLanguage) </span><span class="sxs-lookup"><span data-stu-id="432e3-127">RESTRICTED LANGUAGE (RestrictedLanguage)</span></span>

<span data-ttu-id="432e3-128">在 RestrictedLanguage 模式中，使用者可 (Cmdlet、函式、CIM 命令和工作流程執行命令) 但不允許使用腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="432e3-128">In RestrictedLanguage mode, users may run commands (cmdlets, functions, CIM commands, and workflows) but are not permitted to use script blocks.</span></span>

<span data-ttu-id="432e3-129">根據預設，RestrictedLanguage 模式中只允許下列變數：</span><span class="sxs-lookup"><span data-stu-id="432e3-129">By default, only the following variables are permitted in RestrictedLanguage mode:</span></span>

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

<span data-ttu-id="432e3-130">使用 RestrictedLanguage 模式的模組資訊清單也會允許下列其他變數：</span><span class="sxs-lookup"><span data-stu-id="432e3-130">Module manifests, which use RestrictedLanguage mode, permit the following additional variables as well:</span></span>

- `$PSScriptRoot`
- <span data-ttu-id="432e3-131">`$PSEdition` PowerShell Core) 中的 (</span><span class="sxs-lookup"><span data-stu-id="432e3-131">`$PSEdition` (in PowerShell Core)</span></span>
- <span data-ttu-id="432e3-132">`$EnabledExperimentalFeatures` PowerShell Core) 中的 (</span><span class="sxs-lookup"><span data-stu-id="432e3-132">`$EnabledExperimentalFeatures` (in PowerShell Core)</span></span>

<span data-ttu-id="432e3-133">只允許下列比較運算子：</span><span class="sxs-lookup"><span data-stu-id="432e3-133">Only the following comparison operators are permitted:</span></span>

- <span data-ttu-id="432e3-134">`-eq` (等於) </span><span class="sxs-lookup"><span data-stu-id="432e3-134">`-eq` (equal)</span></span>
- <span data-ttu-id="432e3-135">`-gt` (大於) </span><span class="sxs-lookup"><span data-stu-id="432e3-135">`-gt` (greater-than)</span></span>
- <span data-ttu-id="432e3-136">`-lt` (小於) </span><span class="sxs-lookup"><span data-stu-id="432e3-136">`-lt` (less-than)</span></span>

<span data-ttu-id="432e3-137">不允許指派陳述式、屬性參照及方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="432e3-137">Assignment statements, property references, and method calls are not permitted.</span></span>

#### <a name="no-language-nolanguage"></a><span data-ttu-id="432e3-138">沒有語言 (NoLanguage) </span><span class="sxs-lookup"><span data-stu-id="432e3-138">NO LANGUAGE (NoLanguage)</span></span>

<span data-ttu-id="432e3-139">NoLanguage 模式只能透過 API 使用。</span><span class="sxs-lookup"><span data-stu-id="432e3-139">NoLanguage mode can only be used through the API.</span></span> <span data-ttu-id="432e3-140">NoLanguage 模式表示不允許任何表單的腳本文字。</span><span class="sxs-lookup"><span data-stu-id="432e3-140">NoLanguage mode means no script text of any form is permitted.</span></span> <span data-ttu-id="432e3-141">這樣就不會使用 **AddScript ( # B1** 方法來傳送要剖析和執行的 PowerShell 腳本片段。</span><span class="sxs-lookup"><span data-stu-id="432e3-141">This precludes the use of the **AddScript()** method which sends fragments of PowerShell script to be parsed and executed.</span></span> <span data-ttu-id="432e3-142">您只能使用 **AddCommand ( # B1** 和 **AddParameter ( # B3** ，而不會經過剖析器。</span><span class="sxs-lookup"><span data-stu-id="432e3-142">You can only use **AddCommand()** and **AddParameter()** which don't go through the parser.</span></span>

#### <a name="constrained-language-constrained-language"></a><span data-ttu-id="432e3-143">受限語言 (受限語言) </span><span class="sxs-lookup"><span data-stu-id="432e3-143">CONSTRAINED LANGUAGE (Constrained Language)</span></span>

<span data-ttu-id="432e3-144">ConstrainedLanguage 模式允許所有 Cmdlet 和所有 PowerShell 語言元素，但它會限制允許的類型。</span><span class="sxs-lookup"><span data-stu-id="432e3-144">The ConstrainedLanguage mode permits all cmdlets and all PowerShell language elements, but it limits permitted types.</span></span>

<span data-ttu-id="432e3-145">ConstrainedLanguage 模式是設計用來支援 Windows RT 上的使用者模式程式碼完整性 (UMCI) 。</span><span class="sxs-lookup"><span data-stu-id="432e3-145">ConstrainedLanguage mode is designed to support User Mode Code Integrity (UMCI) on Windows RT.</span></span> <span data-ttu-id="432e3-146">它是 Windows RT 上唯一支援的語言模式，但可在所有支援的系統上使用。</span><span class="sxs-lookup"><span data-stu-id="432e3-146">It is the only supported language mode on Windows RT, but it is available on all supported systems.</span></span>

<span data-ttu-id="432e3-147">UMCI 藉由只允許在 Windows RT 型裝置上安裝 Microsoft 簽署和經 Microsoft 認證的應用程式，來保護 ARM 裝置。</span><span class="sxs-lookup"><span data-stu-id="432e3-147">UMCI protects ARM devices by allowing only Microsoft-signed and Microsoft-certified apps to be installed on Windows RT-based devices.</span></span>
<span data-ttu-id="432e3-148">ConstrainedLanguage 模式會防止使用者使用 PowerShell 規避或違反 UMCI。</span><span class="sxs-lookup"><span data-stu-id="432e3-148">ConstrainedLanguage mode prevents users from using PowerShell to circumvent or violate UMCI.</span></span>

<span data-ttu-id="432e3-149">ConstrainedLanguage 模式的功能如下所示：</span><span class="sxs-lookup"><span data-stu-id="432e3-149">The features of ConstrainedLanguage mode are as follows:</span></span>

- <span data-ttu-id="432e3-150">Windows 模組中的所有 Cmdlet，以及其他 UMCI 核准的 Cmdlet 皆可完全正常運作，並可完整存取系統資源（如所述除外）。</span><span class="sxs-lookup"><span data-stu-id="432e3-150">All cmdlets in Windows modules, and other UMCI-approved cmdlets, are fully functional and have complete access to system resources, except as noted.</span></span>

- <span data-ttu-id="432e3-151">允許 PowerShell 指令碼語言的所有元素。</span><span class="sxs-lookup"><span data-stu-id="432e3-151">All elements of the PowerShell scripting language are permitted.</span></span>

- <span data-ttu-id="432e3-152">您可以匯入 Windows 中包含的所有模組，以及模組匯出在會話中執行的所有命令。</span><span class="sxs-lookup"><span data-stu-id="432e3-152">All modules included in Windows can be imported and all commands that the modules export run in the session.</span></span>

- <span data-ttu-id="432e3-153">在 PowerShell 工作流程中，您可以撰寫和執行以 PowerShell 語言) 撰寫 (工作流程的腳本工作流程。</span><span class="sxs-lookup"><span data-stu-id="432e3-153">In PowerShell Workflow, you can write and run script workflows (workflows written in the PowerShell language).</span></span> <span data-ttu-id="432e3-154">不支援以 XAML 為基礎的工作流程，而且您無法在腳本工作流程（例如使用）中執行 XAML `Invoke-Expression -Language XAML` 。</span><span class="sxs-lookup"><span data-stu-id="432e3-154">XAML-based workflows are not supported and you cannot run XAML in a script workflow, such as by using `Invoke-Expression -Language XAML`.</span></span> <span data-ttu-id="432e3-155">此外，工作流程無法呼叫其他工作流程，雖然允許嵌套工作流程。</span><span class="sxs-lookup"><span data-stu-id="432e3-155">Also, workflows cannot call other workflows, although nested workflows are permitted.</span></span>

- <span data-ttu-id="432e3-156">`Add-Type`Cmdlet 可以載入已簽署的元件，但無法載入任意的 c # 程式碼或 Win32 api。</span><span class="sxs-lookup"><span data-stu-id="432e3-156">The `Add-Type` cmdlet can load signed assemblies, but it cannot load arbitrary C# code or Win32 APIs.</span></span>

- <span data-ttu-id="432e3-157">此 `New-Object` Cmdlet 只能用在以下) 所列的允許類型 (：</span><span class="sxs-lookup"><span data-stu-id="432e3-157">The `New-Object` cmdlet can be used only on allowed types (listed below).</span></span>

- <span data-ttu-id="432e3-158">只有下面所列的允許類型 (可在 PowerShell 中使用) 。</span><span class="sxs-lookup"><span data-stu-id="432e3-158">Only allowed types (listed below) can be used in PowerShell.</span></span> <span data-ttu-id="432e3-159">不允許其他類型。</span><span class="sxs-lookup"><span data-stu-id="432e3-159">Other types are not permitted.</span></span>

- <span data-ttu-id="432e3-160">允許類型轉換，但只有在結果是允許的類型時。</span><span class="sxs-lookup"><span data-stu-id="432e3-160">Type conversion is permitted, but only when the result is an allowed type.</span></span>

- <span data-ttu-id="432e3-161">只有當產生的型別是允許的型別時，才會將字串輸入轉換成類型的 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="432e3-161">Cmdlet parameters that convert string input to types work only when the resulting type is an allowed type.</span></span>

- <span data-ttu-id="432e3-162">您可以叫用 **ToString ( # B1** 方法和允許類型 (的 .net 方法，如下所示) 。</span><span class="sxs-lookup"><span data-stu-id="432e3-162">The **ToString()** method and the .NET methods of allowed types (listed below) can be invoked.</span></span> <span data-ttu-id="432e3-163">無法叫用其他方法。</span><span class="sxs-lookup"><span data-stu-id="432e3-163">Other methods cannot be invoked.</span></span>

- <span data-ttu-id="432e3-164">使用者可以取得允許類型的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="432e3-164">Users can get all properties of allowed types.</span></span> <span data-ttu-id="432e3-165">使用者只能在核心類型上設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="432e3-165">Users can set the values of properties only on Core types.</span></span> <span data-ttu-id="432e3-166">只允許下列 COM 物件：</span><span class="sxs-lookup"><span data-stu-id="432e3-166">Only the following COM objects are permitted:</span></span>

  - <span data-ttu-id="432e3-167">**腳本字典**</span><span class="sxs-lookup"><span data-stu-id="432e3-167">**Scripting.Dictionary**</span></span>
  - <span data-ttu-id="432e3-168">**Scripting.FileSystemObject**</span><span class="sxs-lookup"><span data-stu-id="432e3-168">**Scripting.FileSystemObject**</span></span>
  - <span data-ttu-id="432e3-169">**VBScript. RegExp**</span><span class="sxs-lookup"><span data-stu-id="432e3-169">**VBScript.RegExp**</span></span>

<span data-ttu-id="432e3-170">以下是在 ConstrainedLanguage 模式中允許的類型。</span><span class="sxs-lookup"><span data-stu-id="432e3-170">The following types are permitted in ConstrainedLanguage mode.</span></span> <span data-ttu-id="432e3-171">使用者可以取得屬性、叫用方法，以及將物件轉換為這些類型。</span><span class="sxs-lookup"><span data-stu-id="432e3-171">Users can get properties, invoke methods, and convert objects to these types.</span></span>

<span data-ttu-id="432e3-172">允許的類型：</span><span class="sxs-lookup"><span data-stu-id="432e3-172">Allowed Types:</span></span>

- <span data-ttu-id="432e3-173">AliasAttribute</span><span class="sxs-lookup"><span data-stu-id="432e3-173">AliasAttribute</span></span>
- <span data-ttu-id="432e3-174">AllowEmptyCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="432e3-174">AllowEmptyCollectionAttribute</span></span>
- <span data-ttu-id="432e3-175">AllowEmptyStringAttribute</span><span class="sxs-lookup"><span data-stu-id="432e3-175">AllowEmptyStringAttribute</span></span>
- <span data-ttu-id="432e3-176">AllowNullAttribute</span><span class="sxs-lookup"><span data-stu-id="432e3-176">AllowNullAttribute</span></span>
- <span data-ttu-id="432e3-177">Array</span><span class="sxs-lookup"><span data-stu-id="432e3-177">Array</span></span>
- <span data-ttu-id="432e3-178">Bool</span><span class="sxs-lookup"><span data-stu-id="432e3-178">Bool</span></span>
- <span data-ttu-id="432e3-179">byte</span><span class="sxs-lookup"><span data-stu-id="432e3-179">byte</span></span>
- <span data-ttu-id="432e3-180">char</span><span class="sxs-lookup"><span data-stu-id="432e3-180">char</span></span>
- <span data-ttu-id="432e3-181">CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="432e3-181">CmdletBindingAttribute</span></span>
- <span data-ttu-id="432e3-182">Datetime</span><span class="sxs-lookup"><span data-stu-id="432e3-182">DateTime</span></span>
- <span data-ttu-id="432e3-183">decimal</span><span class="sxs-lookup"><span data-stu-id="432e3-183">decimal</span></span>
- <span data-ttu-id="432e3-184">DirectoryEntry</span><span class="sxs-lookup"><span data-stu-id="432e3-184">DirectoryEntry</span></span>
- <span data-ttu-id="432e3-185">DirectorySearcher</span><span class="sxs-lookup"><span data-stu-id="432e3-185">DirectorySearcher</span></span>
- <span data-ttu-id="432e3-186">double</span><span class="sxs-lookup"><span data-stu-id="432e3-186">double</span></span>
- <span data-ttu-id="432e3-187">FLOAT</span><span class="sxs-lookup"><span data-stu-id="432e3-187">float</span></span>
- <span data-ttu-id="432e3-188">Guid</span><span class="sxs-lookup"><span data-stu-id="432e3-188">Guid</span></span>
- <span data-ttu-id="432e3-189">雜湊表</span><span class="sxs-lookup"><span data-stu-id="432e3-189">Hashtable</span></span>
- <span data-ttu-id="432e3-190">int</span><span class="sxs-lookup"><span data-stu-id="432e3-190">int</span></span>
- <span data-ttu-id="432e3-191">Int16</span><span class="sxs-lookup"><span data-stu-id="432e3-191">Int16</span></span>
- <span data-ttu-id="432e3-192">long</span><span class="sxs-lookup"><span data-stu-id="432e3-192">long</span></span>
- <span data-ttu-id="432e3-193">ManagementClass</span><span class="sxs-lookup"><span data-stu-id="432e3-193">ManagementClass</span></span>
- <span data-ttu-id="432e3-194">System.management.managementobject</span><span class="sxs-lookup"><span data-stu-id="432e3-194">ManagementObject</span></span>
- <span data-ttu-id="432e3-195">ManagementObjectSearcher</span><span class="sxs-lookup"><span data-stu-id="432e3-195">ManagementObjectSearcher</span></span>
- <span data-ttu-id="432e3-196">NullString</span><span class="sxs-lookup"><span data-stu-id="432e3-196">NullString</span></span>
- <span data-ttu-id="432e3-197">OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="432e3-197">OutputTypeAttribute</span></span>
- <span data-ttu-id="432e3-198">ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="432e3-198">ParameterAttribute</span></span>
- <span data-ttu-id="432e3-199">PSCredential</span><span class="sxs-lookup"><span data-stu-id="432e3-199">PSCredential</span></span>
- <span data-ttu-id="432e3-200">PSDefaultValueAttribute</span><span class="sxs-lookup"><span data-stu-id="432e3-200">PSDefaultValueAttribute</span></span>
- <span data-ttu-id="432e3-201">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="432e3-201">PSListModifier</span></span>
- <span data-ttu-id="432e3-202">PSObject</span><span class="sxs-lookup"><span data-stu-id="432e3-202">PSObject</span></span>
- <span data-ttu-id="432e3-203">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="432e3-203">PSPrimitiveDictionary</span></span>
- <span data-ttu-id="432e3-204">PSReference</span><span class="sxs-lookup"><span data-stu-id="432e3-204">PSReference</span></span>
- <span data-ttu-id="432e3-205">PSTypeNameAttribute</span><span class="sxs-lookup"><span data-stu-id="432e3-205">PSTypeNameAttribute</span></span>
- <span data-ttu-id="432e3-206">Regex</span><span class="sxs-lookup"><span data-stu-id="432e3-206">Regex</span></span>
- <span data-ttu-id="432e3-207">SByte</span><span class="sxs-lookup"><span data-stu-id="432e3-207">SByte</span></span>
- <span data-ttu-id="432e3-208">字串</span><span class="sxs-lookup"><span data-stu-id="432e3-208">string</span></span>
- <span data-ttu-id="432e3-209">SupportsWildcardsAttribute</span><span class="sxs-lookup"><span data-stu-id="432e3-209">SupportsWildcardsAttribute</span></span>
- <span data-ttu-id="432e3-210">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="432e3-210">SwitchParameter</span></span>
- <span data-ttu-id="432e3-211">System.Globalization.CultureInfo</span><span class="sxs-lookup"><span data-stu-id="432e3-211">System.Globalization.CultureInfo</span></span>
- <span data-ttu-id="432e3-212">系統 .Net IPAddress</span><span class="sxs-lookup"><span data-stu-id="432e3-212">System.Net.IPAddress</span></span>
- <span data-ttu-id="432e3-213">系統 .Net MailAddress</span><span class="sxs-lookup"><span data-stu-id="432e3-213">System.Net.Mail.MailAddress</span></span>
- <span data-ttu-id="432e3-214">BigInteger</span><span class="sxs-lookup"><span data-stu-id="432e3-214">System.Numerics.BigInteger</span></span>
- <span data-ttu-id="432e3-215">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="432e3-215">System.Security.SecureString</span></span>
- <span data-ttu-id="432e3-216">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="432e3-216">TimeSpan</span></span>
- <span data-ttu-id="432e3-217">UInt16</span><span class="sxs-lookup"><span data-stu-id="432e3-217">UInt16</span></span>
- <span data-ttu-id="432e3-218">UInt32</span><span class="sxs-lookup"><span data-stu-id="432e3-218">UInt32</span></span>
- <span data-ttu-id="432e3-219">UInt64</span><span class="sxs-lookup"><span data-stu-id="432e3-219">UInt64</span></span>

### <a name="finding-the-language-mode-of-a-session-configuration"></a><span data-ttu-id="432e3-220">尋找會話設定的語言模式</span><span class="sxs-lookup"><span data-stu-id="432e3-220">FINDING THE LANGUAGE MODE OF A SESSION CONFIGURATION</span></span>

<span data-ttu-id="432e3-221">使用會話設定檔建立會話設定時，會話設定具有 LanguageMode 屬性。</span><span class="sxs-lookup"><span data-stu-id="432e3-221">When a session configuration is created by using a session configuration file, the session configuration has a LanguageMode property.</span></span> <span data-ttu-id="432e3-222">您可以藉由取得 LanguageMode 屬性的值來尋找語言模式。</span><span class="sxs-lookup"><span data-stu-id="432e3-222">You can find the language mode by getting the value of the LanguageMode property.</span></span>

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

<span data-ttu-id="432e3-223">在其他會話設定中，您可以藉由尋找使用會話設定建立之會話的語言模式，來間接找到語言模式。</span><span class="sxs-lookup"><span data-stu-id="432e3-223">On other session configurations, you can find the language mode indirectly by finding the language mode of a session that is created by using the session configuration.</span></span>

### <a name="finding-the-language-mode-of-a-session"></a><span data-ttu-id="432e3-224">尋找會話的語言模式</span><span class="sxs-lookup"><span data-stu-id="432e3-224">FINDING THE LANGUAGE MODE OF A SESSION</span></span>

<span data-ttu-id="432e3-225">您可以取得會話狀態的 LanguageMode 屬性值，以尋找 >fulllanguage 或 ConstrainedLanguage 會話的語言模式。</span><span class="sxs-lookup"><span data-stu-id="432e3-225">You can find the language mode of a FullLanguage or ConstrainedLanguage session by getting the value of the LanguageMode property of the session state.</span></span>

<span data-ttu-id="432e3-226">例如：</span><span class="sxs-lookup"><span data-stu-id="432e3-226">For example:</span></span>

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

<span data-ttu-id="432e3-227">不過，在具有 RestrictedLanguage 和 NoLanguage 模式的會話中，您無法使用點方法來取得屬性值。</span><span class="sxs-lookup"><span data-stu-id="432e3-227">However, in sessions with RestrictedLanguage and NoLanguage modes, you cannot use the dot method to get property values.</span></span> <span data-ttu-id="432e3-228">相反地，錯誤訊息會顯示語言模式。</span><span class="sxs-lookup"><span data-stu-id="432e3-228">Instead, the error message reveals the language mode.</span></span>

<span data-ttu-id="432e3-229">當您 `$ExecutionContext.SessionState.LanguageMode` 在 RestrictedLanguage 會話中執行命令時，PowerShell 會傳回 PropertyReferenceNotSupportedInDataSection 和 VariableReferenceNotSupportedInDataSection 錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="432e3-229">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a RestrictedLanguage session, PowerShell returns the PropertyReferenceNotSupportedInDataSection and VariableReferenceNotSupportedInDataSection error messages.</span></span>

- <span data-ttu-id="432e3-230">PropertyReferenceNotSupportedInDataSection：不允許在受限制的語言模式或資料區段中使用屬性參考。</span><span class="sxs-lookup"><span data-stu-id="432e3-230">PropertyReferenceNotSupportedInDataSection: Property references are not allowed in restricted language mode or a Data section.</span></span>
- <span data-ttu-id="432e3-231">VariableReferenceNotSupportedInDataSection 無法在受限制的語言模式下參考的變數，或參考的資料區段。</span><span class="sxs-lookup"><span data-stu-id="432e3-231">VariableReferenceNotSupportedInDataSection A variable that cannot be referenced in restricted language mode or a Data section is being referenced.</span></span>

<span data-ttu-id="432e3-232">當您 `$ExecutionContext.SessionState.LanguageMode` 在 NoLanguage 會話中執行命令時，PowerShell 會傳回 ScriptsNotAllowed 錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="432e3-232">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a NoLanguage session, PowerShell returns the ScriptsNotAllowed error message.</span></span>

- <span data-ttu-id="432e3-233">ScriptsNotAllowed：此執行空間不支援語法。</span><span class="sxs-lookup"><span data-stu-id="432e3-233">ScriptsNotAllowed: The syntax is not supported by this runspace.</span></span> <span data-ttu-id="432e3-234">這可能是因為它在無語言模式中。</span><span class="sxs-lookup"><span data-stu-id="432e3-234">This might be because it is in no-language mode.</span></span>

## <a name="keywords"></a><span data-ttu-id="432e3-235">關鍵 字</span><span class="sxs-lookup"><span data-stu-id="432e3-235">KEYWORDS</span></span>

- <span data-ttu-id="432e3-236">about_ConstrainedLanguage</span><span class="sxs-lookup"><span data-stu-id="432e3-236">about_ConstrainedLanguage</span></span>
- <span data-ttu-id="432e3-237">about_FullLanguage</span><span class="sxs-lookup"><span data-stu-id="432e3-237">about_FullLanguage</span></span>
- <span data-ttu-id="432e3-238">about_NoLanguage</span><span class="sxs-lookup"><span data-stu-id="432e3-238">about_NoLanguage</span></span>
- <span data-ttu-id="432e3-239">about_RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="432e3-239">about_RestrictedLanguage</span></span>

## <a name="see-also"></a><span data-ttu-id="432e3-240">另請參閱</span><span class="sxs-lookup"><span data-stu-id="432e3-240">SEE ALSO</span></span>

- [<span data-ttu-id="432e3-241">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="432e3-241">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)
- [<span data-ttu-id="432e3-242">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="432e3-242">about_Session_Configurations</span></span>](about_Session_Configurations.md)

