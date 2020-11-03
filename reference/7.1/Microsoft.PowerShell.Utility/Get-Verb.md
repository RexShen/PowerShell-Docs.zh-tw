---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/07/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-verb?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 27434dfbc76d26724b34fe19fd143a7c52a14e90
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "93206047"
---
# <span data-ttu-id="24db8-103">Get-Verb</span><span class="sxs-lookup"><span data-stu-id="24db8-103">Get-Verb</span></span>

## <span data-ttu-id="24db8-104">概要</span><span class="sxs-lookup"><span data-stu-id="24db8-104">SYNOPSIS</span></span>
<span data-ttu-id="24db8-105">取得核准的 PowerShell 動詞。</span><span class="sxs-lookup"><span data-stu-id="24db8-105">Gets approved PowerShell verbs.</span></span>

## <span data-ttu-id="24db8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="24db8-106">SYNTAX</span></span>

```
Get-Verb [[-Verb] <String[]>] [[-Group] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="24db8-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="24db8-107">DESCRIPTION</span></span>

<span data-ttu-id="24db8-108">函式 `Get-Verb` 會取得已核准在 PowerShell 命令中使用的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="24db8-108">The `Get-Verb` function gets verbs that are approved for use in PowerShell commands.</span></span>

<span data-ttu-id="24db8-109">建議使用 PowerShell Cmdlet 和函式名稱的 `Verb-Noun` 格式，並包含已核准的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="24db8-109">It is recommended that PowerShell cmdlet and function names have the `Verb-Noun` format and include an approved verb.</span></span> <span data-ttu-id="24db8-110">這種做法可讓命令名稱更一致、可預測且更容易使用。</span><span class="sxs-lookup"><span data-stu-id="24db8-110">This practice makes command names more consistent, predictable, and easier to use.</span></span>

<span data-ttu-id="24db8-111">使用未核准動詞的命令仍會在 PowerShell 中執行。</span><span class="sxs-lookup"><span data-stu-id="24db8-111">Commands that use unapproved verbs, still run in PowerShell.</span></span> <span data-ttu-id="24db8-112">不過，當您匯入包含命令的模組（其名稱中包含未核准的動詞命令）時，此 `Import-Module` 命令會顯示一則警告訊息。</span><span class="sxs-lookup"><span data-stu-id="24db8-112">However, when you import a module that includes a command with an unapproved verb in its name, the `Import-Module` command displays a warning message.</span></span>

> [!NOTE]
> <span data-ttu-id="24db8-113">傳回的動詞清單 `Get-Verb` 可能不完整。</span><span class="sxs-lookup"><span data-stu-id="24db8-113">The verb list that `Get-Verb` returns might not be complete.</span></span> <span data-ttu-id="24db8-114">如需已核准的 PowerShell 動詞指令動詞清單和描述，請參閱 Microsoft Docs 中的 [已核准動詞](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) 。</span><span class="sxs-lookup"><span data-stu-id="24db8-114">For an updated list of approved PowerShell verbs with descriptions, see [Approved Verbs](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in the Microsoft Docs.</span></span>

## <span data-ttu-id="24db8-115">範例</span><span class="sxs-lookup"><span data-stu-id="24db8-115">Examples</span></span>

### <span data-ttu-id="24db8-116">範例 1-取得所有動詞的清單</span><span class="sxs-lookup"><span data-stu-id="24db8-116">Example 1 - Get a list of all verbs</span></span>

```powershell
Get-Verb
```

### <span data-ttu-id="24db8-117">範例 2-取得以 "un" 開頭的已核准動詞清單</span><span class="sxs-lookup"><span data-stu-id="24db8-117">Example 2 - Get a list of approved verbs that begin with "un"</span></span>

```powershell
Get-Verb un*
```

```Output
Verb       AliasPrefix Group     Description
----       ----------- -----     -----------
Undo       un          Common    Sets a resource to its previous state
Unlock     uk          Common    Releases a resource that was locked
Unpublish  ub          Data      Makes a resource unavailable to others
Uninstall  us          Lifecycle Removes a resource from an indicated location
Unregister ur          Lifecycle Removes the entry for a resource from a repository
Unblock    ul          Security  Removes restrictions to a resource
Unprotect  up          Security  Removes safeguards from a resource that were added to prevent it from attack or loss
```

### <span data-ttu-id="24db8-118">範例 3-取得安全性群組中所有已核准的動詞</span><span class="sxs-lookup"><span data-stu-id="24db8-118">Example 3 - Get all approved verbs in the Security group</span></span>

```powershell
Get-Verb -Group Security
```

```Output
Verb      AliasPrefix Group    Description
----      ----------- -----    -----------
Block     bl          Security Restricts access to a resource
Grant     gr          Security Allows access to a resource
Protect   pt          Security Safeguards a resource from attack or loss
Revoke    rk          Security Specifies an action that does not allow access to a resource
Unblock   ul          Security Removes restrictions to a resource
Unprotect up          Security Removes safeguards from a resource that were added to prevent it from attack or loss
```

### <span data-ttu-id="24db8-119">範例 4-在具有未核准動詞的模組中尋找所有命令</span><span class="sxs-lookup"><span data-stu-id="24db8-119">Example 4 - Finds all commands in a module that have unapproved verbs</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## <span data-ttu-id="24db8-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="24db8-120">PARAMETERS</span></span>

### <span data-ttu-id="24db8-121">-Verb</span><span class="sxs-lookup"><span data-stu-id="24db8-121">-Verb</span></span>

<span data-ttu-id="24db8-122">只取得指定的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="24db8-122">Gets only the specified verbs.</span></span> <span data-ttu-id="24db8-123">輸入動詞命令的名稱或名稱模式。</span><span class="sxs-lookup"><span data-stu-id="24db8-123">Enter the name of a verb or a name pattern.</span></span> <span data-ttu-id="24db8-124">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="24db8-124">Wildcards are allowed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Common, Communications, Data, Diagnostic, Lifecycle, Other, Security

Required: False
Position: 1
Default value: All groups
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="24db8-125">-Group</span><span class="sxs-lookup"><span data-stu-id="24db8-125">-Group</span></span>

<span data-ttu-id="24db8-126">只取得指定的群組。</span><span class="sxs-lookup"><span data-stu-id="24db8-126">Gets only the specified groups.</span></span> <span data-ttu-id="24db8-127">輸入群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="24db8-127">Enter the name of a group.</span></span> <span data-ttu-id="24db8-128">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="24db8-128">Wildcards are not allowed.</span></span>

<span data-ttu-id="24db8-129">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="24db8-129">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All verbs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="24db8-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="24db8-130">CommonParameters</span></span>

<span data-ttu-id="24db8-131">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="24db8-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="24db8-132">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="24db8-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="24db8-133">輸入</span><span class="sxs-lookup"><span data-stu-id="24db8-133">INPUTS</span></span>

### <span data-ttu-id="24db8-134">無</span><span class="sxs-lookup"><span data-stu-id="24db8-134">None</span></span>

## <span data-ttu-id="24db8-135">輸出</span><span class="sxs-lookup"><span data-stu-id="24db8-135">OUTPUTS</span></span>

### <span data-ttu-id="24db8-136">VerbInfo。</span><span class="sxs-lookup"><span data-stu-id="24db8-136">System.Management.Automation.VerbInfo</span></span>

## <span data-ttu-id="24db8-137">注意</span><span class="sxs-lookup"><span data-stu-id="24db8-137">NOTES</span></span>

<span data-ttu-id="24db8-138">PowerShell 動詞命令會根據其最常見的用途，指派給群組。</span><span class="sxs-lookup"><span data-stu-id="24db8-138">PowerShell verbs are assigned to a group based on their most common use.</span></span> <span data-ttu-id="24db8-139">這些群組的設計可讓您輕鬆地尋找並比較動詞命令，而不限制其用途。</span><span class="sxs-lookup"><span data-stu-id="24db8-139">The groups are designed to make the verbs easy to find and compare, not to restrict their use.</span></span> <span data-ttu-id="24db8-140">您可以為任何類型的命令使用任何已核准的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="24db8-140">You can use any approved verb for any type of command.</span></span>

<span data-ttu-id="24db8-141">每個 PowerShell 動詞命令都會指派給下列其中一個群組。</span><span class="sxs-lookup"><span data-stu-id="24db8-141">Each PowerShell verb is assigned to one of the following groups.</span></span>

- <span data-ttu-id="24db8-142">Common：定義可以套用到幾乎任何 Cmdlet 的一般動作，例如 Add。</span><span class="sxs-lookup"><span data-stu-id="24db8-142">Common: Define generic actions that can apply to almost any cmdlet, such as Add.</span></span>
- <span data-ttu-id="24db8-143">通訊：定義適用于通訊的動作，例如 Connect。</span><span class="sxs-lookup"><span data-stu-id="24db8-143">Communications: Define actions that apply to communications, such as Connect.</span></span>
- <span data-ttu-id="24db8-144">資料：定義適用于資料處理的動作，例如備份。</span><span class="sxs-lookup"><span data-stu-id="24db8-144">Data: Define actions that apply to data handling, such as Backup.</span></span>
- <span data-ttu-id="24db8-145">診斷：定義適用于診斷的動作，例如 Debug。</span><span class="sxs-lookup"><span data-stu-id="24db8-145">Diagnostic: Define actions that apply to diagnostics, such as Debug.</span></span>
- <span data-ttu-id="24db8-146">生命週期：定義適用于 Cmdlet 生命週期的動作，例如 [完成]。</span><span class="sxs-lookup"><span data-stu-id="24db8-146">Lifecycle: Define actions that apply to the lifecycle of a cmdlet, such as Complete.</span></span>
- <span data-ttu-id="24db8-147">安全性：定義適用于安全性的動作，例如 Revoke。</span><span class="sxs-lookup"><span data-stu-id="24db8-147">Security: Define actions that apply to security, such as Revoke.</span></span>
- <span data-ttu-id="24db8-148">其他：定義其他類型的動作。</span><span class="sxs-lookup"><span data-stu-id="24db8-148">Other: Define other types of actions.</span></span>

<span data-ttu-id="24db8-149">與 PowerShell 一起安裝的某些 Cmdlet （例如 `Tee-Object` 和 `Where-Object` ）會使用未核准的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="24db8-149">Some of the cmdlets that are installed with PowerShell, such as `Tee-Object` and `Where-Object`, use unapproved verbs.</span></span> <span data-ttu-id="24db8-150">這些 Cmdlet 是記錄例外狀況，而其動詞命令會分類為 **保留** 。</span><span class="sxs-lookup"><span data-stu-id="24db8-150">These cmdlets are historic exceptions and their verbs are classified as **reserved** .</span></span>

## <span data-ttu-id="24db8-151">相關連結</span><span class="sxs-lookup"><span data-stu-id="24db8-151">RELATED LINKS</span></span>

[<span data-ttu-id="24db8-152">Import-Module</span><span class="sxs-lookup"><span data-stu-id="24db8-152">Import-Module</span></span>](../microsoft.powershell.core/import-module.md)

