---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: eac42af069b5d1276105c16dd6e280c7c72cf558
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204579"
---
# <span data-ttu-id="6a853-103">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="6a853-103">Get-Variable</span></span>

## <span data-ttu-id="6a853-104">概要</span><span class="sxs-lookup"><span data-stu-id="6a853-104">SYNOPSIS</span></span>
<span data-ttu-id="6a853-105">取得目前主控台中的變數。</span><span class="sxs-lookup"><span data-stu-id="6a853-105">Gets the variables in the current console.</span></span>

## <span data-ttu-id="6a853-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6a853-106">SYNTAX</span></span>

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="6a853-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6a853-107">DESCRIPTION</span></span>

<span data-ttu-id="6a853-108">`Get-Variable`Cmdlet 會取得目前主控台中的 PowerShell 變數。</span><span class="sxs-lookup"><span data-stu-id="6a853-108">The `Get-Variable` cmdlet gets the PowerShell variables in the current console.</span></span>
<span data-ttu-id="6a853-109">您可以透過指定 **ValueOnly** 參數來只抓取變數的值，而且您可以依名稱篩選傳回的變數。</span><span class="sxs-lookup"><span data-stu-id="6a853-109">You can retrieve just the values of the variables by specifying the **ValueOnly** parameter, and you can filter the variables returned by name.</span></span>

## <span data-ttu-id="6a853-110">範例</span><span class="sxs-lookup"><span data-stu-id="6a853-110">EXAMPLES</span></span>

### <span data-ttu-id="6a853-111">範例 1︰依字母取得變數</span><span class="sxs-lookup"><span data-stu-id="6a853-111">Example 1: Get variables by letter</span></span>

<span data-ttu-id="6a853-112">此命令會取得名稱以字母 m 為開頭的變數。</span><span class="sxs-lookup"><span data-stu-id="6a853-112">This command gets variables with names that begin with the letter m.</span></span>
<span data-ttu-id="6a853-113">命令也會取得變數的值。</span><span class="sxs-lookup"><span data-stu-id="6a853-113">The command also gets the value of the variables.</span></span>

```powershell
Get-Variable m*
```

### <span data-ttu-id="6a853-114">範例 2︰依字母取得變數值</span><span class="sxs-lookup"><span data-stu-id="6a853-114">Example 2: Get variable values by letter</span></span>

<span data-ttu-id="6a853-115">此命令只會取得名稱以 m 為開頭之變數的值。</span><span class="sxs-lookup"><span data-stu-id="6a853-115">This command gets only the values of the variables that have names that begin with m.</span></span>

```powershell
Get-Variable m* -ValueOnly
```

### <span data-ttu-id="6a853-116">範例 3︰依兩個字母取得變數</span><span class="sxs-lookup"><span data-stu-id="6a853-116">Example 3: Get variables by two letters</span></span>

<span data-ttu-id="6a853-117">此命令會取得以字母 M 或字母 P 為開頭之變數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6a853-117">This command gets information about the variables that begin with either the letter M or the letter P.</span></span>

```powershell
Get-Variable -Include M*,P*
```

### <span data-ttu-id="6a853-118">範例 4︰依範圍取得變數</span><span class="sxs-lookup"><span data-stu-id="6a853-118">Example 4: Get variables by scope</span></span>

<span data-ttu-id="6a853-119">第一個命令只會取得本機範圍中定義的變數。</span><span class="sxs-lookup"><span data-stu-id="6a853-119">The first command gets only the variables that are defined in the local scope.</span></span>
<span data-ttu-id="6a853-120">它相當於 `Get-Variable -Scope Local`，並可縮寫成 `gv -s 0`。</span><span class="sxs-lookup"><span data-stu-id="6a853-120">It is equivalent to `Get-Variable -Scope Local` and can be abbreviated as `gv -s 0`.</span></span>

<span data-ttu-id="6a853-121">第二個命令 `Compare-Object` 會使用 Cmdlet 來尋找 (範圍 1) 的父範圍中定義的變數，但只在區域 (範圍 0) 可見。</span><span class="sxs-lookup"><span data-stu-id="6a853-121">The second command uses the `Compare-Object` cmdlet to find the variables that are defined in the parent scope (Scope 1) but are visible only in the local scope (Scope 0).</span></span>

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## <span data-ttu-id="6a853-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6a853-122">PARAMETERS</span></span>

### <span data-ttu-id="6a853-123">-Exclude</span><span class="sxs-lookup"><span data-stu-id="6a853-123">-Exclude</span></span>

<span data-ttu-id="6a853-124">指定此 Cmdlet 從作業排除之項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="6a853-124">Specifies an array of items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="6a853-125">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6a853-125">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6a853-126">-Include</span><span class="sxs-lookup"><span data-stu-id="6a853-126">-Include</span></span>

<span data-ttu-id="6a853-127">指定 Cmdlet 會在其中作用的項目陣列，不包含其他所有項目。</span><span class="sxs-lookup"><span data-stu-id="6a853-127">Specifies an array of items upon which the cmdlet will act, excluding all others.</span></span>
<span data-ttu-id="6a853-128">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6a853-128">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6a853-129">-Name</span><span class="sxs-lookup"><span data-stu-id="6a853-129">-Name</span></span>

<span data-ttu-id="6a853-130">指定變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="6a853-130">Specifies the name of the variable.</span></span>
<span data-ttu-id="6a853-131">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6a853-131">Wildcards are permitted.</span></span>
<span data-ttu-id="6a853-132">您也可以使用管線將變數名稱傳送至 `Get-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="6a853-132">You can also pipe a variable name to `Get-Variable`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="6a853-133">-Scope</span><span class="sxs-lookup"><span data-stu-id="6a853-133">-Scope</span></span>

<span data-ttu-id="6a853-134">指定範圍中的變數。此參數可接受的值包括：</span><span class="sxs-lookup"><span data-stu-id="6a853-134">Specifies the variables in the scope.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6a853-135">**全球**</span><span class="sxs-lookup"><span data-stu-id="6a853-135">**Global**</span></span>
- <span data-ttu-id="6a853-136">**本機**</span><span class="sxs-lookup"><span data-stu-id="6a853-136">**Local**</span></span>
- <span data-ttu-id="6a853-137">**指令碼**</span><span class="sxs-lookup"><span data-stu-id="6a853-137">**Script**</span></span>
- <span data-ttu-id="6a853-138">相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。</span><span class="sxs-lookup"><span data-stu-id="6a853-138">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="6a853-139">預設值為 [ **本機** ]。</span><span class="sxs-lookup"><span data-stu-id="6a853-139">**Local** is the default.</span></span>
<span data-ttu-id="6a853-140">如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="6a853-140">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a853-141">-ValueOnly</span><span class="sxs-lookup"><span data-stu-id="6a853-141">-ValueOnly</span></span>

<span data-ttu-id="6a853-142">指示此 Cmdlet 只取得變數的值。</span><span class="sxs-lookup"><span data-stu-id="6a853-142">Indicates that this cmdlet gets only the value of the variable.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a853-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6a853-143">CommonParameters</span></span>

<span data-ttu-id="6a853-144">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6a853-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6a853-145">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="6a853-145">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6a853-146">輸入</span><span class="sxs-lookup"><span data-stu-id="6a853-146">INPUTS</span></span>

### <span data-ttu-id="6a853-147">System.String</span><span class="sxs-lookup"><span data-stu-id="6a853-147">System.String</span></span>

<span data-ttu-id="6a853-148">您可以使用管線將包含變數名稱的字串傳送至 `Get-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="6a853-148">You can pipe a string that contains the variable name to `Get-Variable`.</span></span>

## <span data-ttu-id="6a853-149">輸出</span><span class="sxs-lookup"><span data-stu-id="6a853-149">OUTPUTS</span></span>

### <span data-ttu-id="6a853-150">System.Management.Automation.PSVariable</span><span class="sxs-lookup"><span data-stu-id="6a853-150">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="6a853-151">此 Cmdlet 會傳回它所取得之每個變數的 **System.Management.AutomationPSVariable** 物件。</span><span class="sxs-lookup"><span data-stu-id="6a853-151">This cmdlet returns a **System.Management.AutomationPSVariable** object for each variable that it gets.</span></span> <span data-ttu-id="6a853-152">物件類型會視變數而定。</span><span class="sxs-lookup"><span data-stu-id="6a853-152">The object type depends on the variable.</span></span>

### <span data-ttu-id="6a853-153">System.object []</span><span class="sxs-lookup"><span data-stu-id="6a853-153">System.Object[]</span></span>

<span data-ttu-id="6a853-154">當您指定 **ValueOnly** 參數時，如果指定的變數值為集合，則會傳回 `Get-Variable` `[System.Object[]]` 。</span><span class="sxs-lookup"><span data-stu-id="6a853-154">When you specify the **ValueOnly** parameter, if the specified variable's value is a collection, `Get-Variable` returns a `[System.Object[]]`.</span></span> <span data-ttu-id="6a853-155">此行為可防止正常管線操作一次處理一個變數的值。</span><span class="sxs-lookup"><span data-stu-id="6a853-155">This behavior prevents normal pipeline operation from processing the variable's values one at a time.</span></span> <span data-ttu-id="6a853-156">強制集合列舉的因應措施是將命令以括弧括住 `Get-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="6a853-156">A workaround to force collection enumeration is to enclose the `Get-Variable` command in parenthesis.</span></span>

## <span data-ttu-id="6a853-157">注意</span><span class="sxs-lookup"><span data-stu-id="6a853-157">NOTES</span></span>

- <span data-ttu-id="6a853-158">此 Cmdlet 並不會管理環境變數。</span><span class="sxs-lookup"><span data-stu-id="6a853-158">This cmdlet does not manage environment variables.</span></span> <span data-ttu-id="6a853-159">若要管理環境變數，您可以使用環境變數提供者。</span><span class="sxs-lookup"><span data-stu-id="6a853-159">To manage environment variables, you can use the environment variable provider.</span></span>

## <span data-ttu-id="6a853-160">相關連結</span><span class="sxs-lookup"><span data-stu-id="6a853-160">RELATED LINKS</span></span>

[<span data-ttu-id="6a853-161">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="6a853-161">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="6a853-162">New-Variable</span><span class="sxs-lookup"><span data-stu-id="6a853-162">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="6a853-163">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="6a853-163">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="6a853-164">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="6a853-164">Set-Variable</span></span>](Set-Variable.md)
