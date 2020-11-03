---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/07/2018
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/functions/get-verb?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 4474bb50c2bf3be10e72d2554190208e956f9040
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "93206035"
---
# <span data-ttu-id="c3daa-103">Get-Verb</span><span class="sxs-lookup"><span data-stu-id="c3daa-103">Get-Verb</span></span>

## <span data-ttu-id="c3daa-104">概要</span><span class="sxs-lookup"><span data-stu-id="c3daa-104">SYNOPSIS</span></span>
<span data-ttu-id="c3daa-105">取得核准的 PowerShell 動詞。</span><span class="sxs-lookup"><span data-stu-id="c3daa-105">Gets approved PowerShell verbs.</span></span>

## <span data-ttu-id="c3daa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c3daa-106">SYNTAX</span></span>

```
Get-Verb [[-verb] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="c3daa-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c3daa-107">DESCRIPTION</span></span>

<span data-ttu-id="c3daa-108">函式 `Get-Verb` 會取得已核准在 PowerShell 命令中使用的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="c3daa-108">The `Get-Verb` function gets verbs that are approved for use in PowerShell commands.</span></span>

<span data-ttu-id="c3daa-109">PowerShell 建議 Cmdlet 和函式名稱具有 Verb-Noun 格式，並包含已核准的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="c3daa-109">PowerShell recommends cmdlet and function names have the Verb-Noun format and include an approved verb.</span></span> <span data-ttu-id="c3daa-110">這種做法可讓命令名稱更一致、可預測且更容易使用。</span><span class="sxs-lookup"><span data-stu-id="c3daa-110">This practice makes command names more consistent, predictable, and easier to use.</span></span>

<span data-ttu-id="c3daa-111">使用未核准的動詞命令在 PowerShell 中執行的命令。</span><span class="sxs-lookup"><span data-stu-id="c3daa-111">Commands that use unapproved verbs run in PowerShell.</span></span> <span data-ttu-id="c3daa-112">不過，當您匯入包含命令的模組（其名稱中包含未核准的動詞命令）時，此 `Import-Module` 命令會顯示一則警告訊息。</span><span class="sxs-lookup"><span data-stu-id="c3daa-112">However, when you import a module that includes a command with an unapproved verb in its name, the `Import-Module` command displays a warning message.</span></span>

> [!NOTE]
> <span data-ttu-id="c3daa-113">傳回的動詞清單 `Get-Verb` 可能不完整。</span><span class="sxs-lookup"><span data-stu-id="c3daa-113">The verb list that `Get-Verb` returns might not be complete.</span></span> <span data-ttu-id="c3daa-114">如需已核准的 PowerShell 動詞指令動詞清單和描述，請參閱 Microsoft Docs 中的 [已核准動詞](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) 。</span><span class="sxs-lookup"><span data-stu-id="c3daa-114">For an updated list of approved PowerShell verbs with descriptions, see [Approved Verbs](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in the Microsoft Docs.</span></span>

## <span data-ttu-id="c3daa-115">範例</span><span class="sxs-lookup"><span data-stu-id="c3daa-115">EXAMPLES</span></span>

### <span data-ttu-id="c3daa-116">範例 1-取得所有動詞的清單</span><span class="sxs-lookup"><span data-stu-id="c3daa-116">Example 1 - Get a list of all verbs</span></span>

```powershell
Get-Verb
```

### <span data-ttu-id="c3daa-117">範例 2-取得以 "un" 開頭的已核准動詞清單</span><span class="sxs-lookup"><span data-stu-id="c3daa-117">Example 2 - Get a list of approved verbs that begin with "un"</span></span>

```powershell
Get-Verb un*
```

```Output
Verb                 Group
----                 -----
Undo                 Common
Unlock               Common
Unpublish            Data
Uninstall            Lifecycle
Unregister           Lifecycle
Unblock              Security
Unprotect            Security
```

### <span data-ttu-id="c3daa-118">範例 3-取得安全性群組中所有已核准的動詞</span><span class="sxs-lookup"><span data-stu-id="c3daa-118">Example 3 - Get all approved verbs in the Security group</span></span>

```powershell
Get-Verb | Where-Object Group -EQ Security
```

```Output
Verb      Group
----      -----
Block     Security
Grant     Security
Protect   Security
Revoke    Security
Unblock   Security
Unprotect Security
```

### <span data-ttu-id="c3daa-119">範例 4-在具有未核准動詞的模組中尋找所有命令</span><span class="sxs-lookup"><span data-stu-id="c3daa-119">Example 4 - Finds all commands in a module that have unapproved verbs</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## <span data-ttu-id="c3daa-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c3daa-120">PARAMETERS</span></span>

### <span data-ttu-id="c3daa-121">-動詞</span><span class="sxs-lookup"><span data-stu-id="c3daa-121">-verb</span></span>

<span data-ttu-id="c3daa-122">只取得指定的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="c3daa-122">Gets only the specified verbs.</span></span>
<span data-ttu-id="c3daa-123">輸入動詞命令的名稱或名稱模式。</span><span class="sxs-lookup"><span data-stu-id="c3daa-123">Enter the name of a verb or a name pattern.</span></span>
<span data-ttu-id="c3daa-124">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c3daa-124">Wildcards are allowed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: All verbs
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

## <span data-ttu-id="c3daa-125">輸入</span><span class="sxs-lookup"><span data-stu-id="c3daa-125">INPUTS</span></span>

### <span data-ttu-id="c3daa-126">無</span><span class="sxs-lookup"><span data-stu-id="c3daa-126">None</span></span>

## <span data-ttu-id="c3daa-127">輸出</span><span class="sxs-lookup"><span data-stu-id="c3daa-127">OUTPUTS</span></span>

### <span data-ttu-id="c3daa-128">Selected.Microsoft.PowerShell.Commands.MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="c3daa-128">Selected.Microsoft.PowerShell.Commands.MemberDefinition</span></span>

## <span data-ttu-id="c3daa-129">注意</span><span class="sxs-lookup"><span data-stu-id="c3daa-129">NOTES</span></span>

<span data-ttu-id="c3daa-130">`Get-Verb` 傳回 MemberDefinition 物件的已修改版本。</span><span class="sxs-lookup"><span data-stu-id="c3daa-130">`Get-Verb` returns a modified version of a Microsoft.PowerShell.Commands.MemberDefinition object.</span></span>
<span data-ttu-id="c3daa-131">此物件沒有 MemberDefinition 物件的標準屬性，</span><span class="sxs-lookup"><span data-stu-id="c3daa-131">The object does not have the standard properties of a MemberDefinition object.</span></span> <span data-ttu-id="c3daa-132">而是擁有 Verb 和 Group 屬性。</span><span class="sxs-lookup"><span data-stu-id="c3daa-132">Instead it has Verb and Group properties.</span></span> <span data-ttu-id="c3daa-133">Verb 屬性包含具有動詞命令名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="c3daa-133">The Verb property contains a string with the verb name.</span></span> <span data-ttu-id="c3daa-134">Group 屬性包含具有動詞命令群組的字串。</span><span class="sxs-lookup"><span data-stu-id="c3daa-134">The Group property contains a string with the verb group.</span></span>

<span data-ttu-id="c3daa-135">PowerShell 動詞命令會根據其最常見的用途，指派給群組。</span><span class="sxs-lookup"><span data-stu-id="c3daa-135">PowerShell verbs are assigned to a group based on their most common use.</span></span> <span data-ttu-id="c3daa-136">這些群組的設計可讓您輕鬆地尋找並比較動詞命令，而不限制其用途。</span><span class="sxs-lookup"><span data-stu-id="c3daa-136">The groups are designed to make the verbs easy to find and compare, not to restrict their use.</span></span> <span data-ttu-id="c3daa-137">您可以為任何類型的命令使用任何已核准的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="c3daa-137">You can use any approved verb for any type of command.</span></span>

<span data-ttu-id="c3daa-138">每個 PowerShell 動詞命令都會指派給下列其中一個群組。</span><span class="sxs-lookup"><span data-stu-id="c3daa-138">Each PowerShell verb is assigned to one of the following groups.</span></span>

- <span data-ttu-id="c3daa-139">Common：定義可以套用到幾乎任何 Cmdlet 的一般動作，例如 Add。</span><span class="sxs-lookup"><span data-stu-id="c3daa-139">Common: Define generic actions that can apply to almost any cmdlet, such as Add.</span></span>
- <span data-ttu-id="c3daa-140">通訊：定義適用于通訊的動作，例如 Connect。</span><span class="sxs-lookup"><span data-stu-id="c3daa-140">Communications:  Define actions that apply to communications, such as Connect.</span></span>
- <span data-ttu-id="c3daa-141">資料：定義適用于資料處理的動作，例如備份。</span><span class="sxs-lookup"><span data-stu-id="c3daa-141">Data:  Define actions that apply to data handling, such as Backup.</span></span>
- <span data-ttu-id="c3daa-142">診斷：定義適用于診斷的動作，例如 Debug。</span><span class="sxs-lookup"><span data-stu-id="c3daa-142">Diagnostic: Define actions that apply to diagnostics, such as Debug.</span></span>
- <span data-ttu-id="c3daa-143">生命週期：定義適用于 Cmdlet 生命週期的動作，例如 [完成]。</span><span class="sxs-lookup"><span data-stu-id="c3daa-143">Lifecycle: Define actions that apply to the lifecycle of a cmdlet, such as Complete.</span></span>
- <span data-ttu-id="c3daa-144">安全性：定義適用于安全性的動作，例如 Revoke。</span><span class="sxs-lookup"><span data-stu-id="c3daa-144">Security: Define actions that apply to security, such as Revoke.</span></span>
- <span data-ttu-id="c3daa-145">其他：定義其他類型的動作。</span><span class="sxs-lookup"><span data-stu-id="c3daa-145">Other: Define other types of actions.</span></span>

<span data-ttu-id="c3daa-146">與 PowerShell 一起安裝的某些 Cmdlet （例如 `Tee-Object` 和 `Where-Object` ）會使用未核准的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="c3daa-146">Some of the cmdlets that are installed with PowerShell, such as `Tee-Object` and `Where-Object`, use unapproved verbs.</span></span> <span data-ttu-id="c3daa-147">這些 Cmdlet 是記錄例外狀況，而其動詞命令會分類為 **保留** 。</span><span class="sxs-lookup"><span data-stu-id="c3daa-147">These cmdlets are historic exceptions and their verbs are classified as **reserved** .</span></span>

## <span data-ttu-id="c3daa-148">相關連結</span><span class="sxs-lookup"><span data-stu-id="c3daa-148">RELATED LINKS</span></span>

[<span data-ttu-id="c3daa-149">Import-Module</span><span class="sxs-lookup"><span data-stu-id="c3daa-149">Import-Module</span></span>](import-module.md)
