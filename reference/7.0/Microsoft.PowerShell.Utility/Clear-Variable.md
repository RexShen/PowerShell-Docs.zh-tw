---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/clear-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Variable
ms.openlocfilehash: 6208e9c1b7124c8faec1e3e87a6e815540d2b962
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201995"
---
# <span data-ttu-id="49422-103">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="49422-103">Clear-Variable</span></span>

## <span data-ttu-id="49422-104">概要</span><span class="sxs-lookup"><span data-stu-id="49422-104">SYNOPSIS</span></span>
<span data-ttu-id="49422-105">刪除變數的值。</span><span class="sxs-lookup"><span data-stu-id="49422-105">Deletes the value of a variable.</span></span>

## <span data-ttu-id="49422-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="49422-106">SYNTAX</span></span>

```
Clear-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-PassThru]
 [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="49422-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="49422-107">DESCRIPTION</span></span>

<span data-ttu-id="49422-108">**清除變數** Cmdlet 會刪除儲存在變數中的資料，但不會刪除變數。</span><span class="sxs-lookup"><span data-stu-id="49422-108">The **Clear-Variable** cmdlet deletes the data stored in a variable, but it does not delete the variable.</span></span>
<span data-ttu-id="49422-109">因此，變數的值是 NULL (空白)。</span><span class="sxs-lookup"><span data-stu-id="49422-109">As a result, the value of the variable is NULL (empty).</span></span>
<span data-ttu-id="49422-110">如果變數具有指定的資料或物件類型，這個 Cmdlet 會保留變數中所儲存之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="49422-110">If the variable has a specified data or object type, this cmdlet preserves the type of the object stored in the variable.</span></span>

## <span data-ttu-id="49422-111">範例</span><span class="sxs-lookup"><span data-stu-id="49422-111">EXAMPLES</span></span>

### <span data-ttu-id="49422-112">範例1：移除以搜尋字串開頭之全域變數的值</span><span class="sxs-lookup"><span data-stu-id="49422-112">Example 1: Remove the value of global variables that begin with a search string</span></span>

```
PS C:\> Clear-Variable my* -Scope Global
```

<span data-ttu-id="49422-113">此命令會移除名稱開頭為 my 的全域變數值。</span><span class="sxs-lookup"><span data-stu-id="49422-113">This command removes the value of global variables that have names that begin with my.</span></span>

### <span data-ttu-id="49422-114">範例2：清除子範圍中的變數，但不清除父範圍中的變數</span><span class="sxs-lookup"><span data-stu-id="49422-114">Example 2: Clear a variable in a child scope but not the parent scope</span></span>

```
PS C:\> $a=3
PS C:\> &{ Clear-Variable a }
PS C:\> $a
3
```

<span data-ttu-id="49422-115">這些命令示範清除子系範圍中的變數不會清除父系範圍中的值。</span><span class="sxs-lookup"><span data-stu-id="49422-115">These commands demonstrate that clearing a variable in a child scope does not clear the value in the parent scope.</span></span>
<span data-ttu-id="49422-116">第一個命令將變數 $A 值設定為3。</span><span class="sxs-lookup"><span data-stu-id="49422-116">The first command sets the value of the variable $A to 3.</span></span>
<span data-ttu-id="49422-117">第二個命令使用叫用運算子 ( # A0) 在新的範圍中執行 **清除變數** 命令。</span><span class="sxs-lookup"><span data-stu-id="49422-117">The second command uses the invoke operator (&) to run the **Clear-Variable** command in a new scope.</span></span>
<span data-ttu-id="49422-118">子系範圍內的變數會被清除 (雖然它不存在)，但本機範圍內的變數不會被清除。</span><span class="sxs-lookup"><span data-stu-id="49422-118">The variable is cleared in the child scope (although it did not exist), but it is not cleared in the local scope.</span></span>
<span data-ttu-id="49422-119">第三個命令會取得 $A 的值，顯示值3不受影響。</span><span class="sxs-lookup"><span data-stu-id="49422-119">The third command, which gets the value of $A, shows that the value 3 is unaffected.</span></span>

### <span data-ttu-id="49422-120">範例3：刪除指定之變數的值</span><span class="sxs-lookup"><span data-stu-id="49422-120">Example 3: Delete the value of the specified variable</span></span>

```
PS C:\> Clear-Variable -Name "Processes"
```

<span data-ttu-id="49422-121">此命令會刪除名為「進程」的變數值。</span><span class="sxs-lookup"><span data-stu-id="49422-121">This command deletes the value of the variable named Processes.</span></span>
<span data-ttu-id="49422-122">當 Cmdlet 完成作業之後，名為進程的變數仍然存在，但值為 null。</span><span class="sxs-lookup"><span data-stu-id="49422-122">After the cmdlet completes the operation, the variable named Processes still exists, but the value is null.</span></span>

## <span data-ttu-id="49422-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="49422-123">PARAMETERS</span></span>

### <span data-ttu-id="49422-124">-Exclude</span><span class="sxs-lookup"><span data-stu-id="49422-124">-Exclude</span></span>

<span data-ttu-id="49422-125">指定此 Cmdlet 在作業中省略的專案陣列。</span><span class="sxs-lookup"><span data-stu-id="49422-125">Specifies an array of items that this cmdlet omits in the operation.</span></span>
<span data-ttu-id="49422-126">此參數的值會限定 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="49422-126">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="49422-127">輸入名稱元素或模式，例如 "s\*"。</span><span class="sxs-lookup"><span data-stu-id="49422-127">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="49422-128">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="49422-128">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="49422-129">-Force</span><span class="sxs-lookup"><span data-stu-id="49422-129">-Force</span></span>

<span data-ttu-id="49422-130">允許 Cmdlet 清除變數，即使它是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="49422-130">Allows the cmdlet to clear a variable even if it is read-only.</span></span>
<span data-ttu-id="49422-131">即使使用 Force 參數，Cmdlet 仍然無法清除常數。</span><span class="sxs-lookup"><span data-stu-id="49422-131">Even using the Force parameter, the cmdlet cannot clear constants.</span></span>

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

### <span data-ttu-id="49422-132">-Include</span><span class="sxs-lookup"><span data-stu-id="49422-132">-Include</span></span>

<span data-ttu-id="49422-133">指定此 Cmdlet 在作業中納入之項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="49422-133">Specifies an array of items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="49422-134">此參數的值會限定 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="49422-134">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="49422-135">輸入名稱元素或模式，例如 "s\*"。</span><span class="sxs-lookup"><span data-stu-id="49422-135">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="49422-136">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="49422-136">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="49422-137">-Name</span><span class="sxs-lookup"><span data-stu-id="49422-137">-Name</span></span>

<span data-ttu-id="49422-138">指定要清除之變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="49422-138">Specifies the name of the variable to be cleared.</span></span>
<span data-ttu-id="49422-139">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="49422-139">Wildcards are permitted.</span></span>
<span data-ttu-id="49422-140">此為必要參數，但是參數名稱 ("Name") 為選擇性。</span><span class="sxs-lookup"><span data-stu-id="49422-140">This parameter is required, but the parameter name ("Name") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="49422-141">-PassThru</span><span class="sxs-lookup"><span data-stu-id="49422-141">-PassThru</span></span>

<span data-ttu-id="49422-142">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="49422-142">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="49422-143">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="49422-143">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="49422-144">-Scope</span><span class="sxs-lookup"><span data-stu-id="49422-144">-Scope</span></span>

<span data-ttu-id="49422-145">指定別名的有效範圍。</span><span class="sxs-lookup"><span data-stu-id="49422-145">Specifies the scope in which this alias is valid.</span></span>

<span data-ttu-id="49422-146">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="49422-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="49422-147">全球</span><span class="sxs-lookup"><span data-stu-id="49422-147">Global</span></span>
- <span data-ttu-id="49422-148">本機</span><span class="sxs-lookup"><span data-stu-id="49422-148">Local</span></span>
- <span data-ttu-id="49422-149">指令碼</span><span class="sxs-lookup"><span data-stu-id="49422-149">Script</span></span>

<span data-ttu-id="49422-150">您也可以使用相對於目前範圍的數位 (0 至範圍數目，0為目前範圍，1為其父) 。</span><span class="sxs-lookup"><span data-stu-id="49422-150">You can also use a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>
<span data-ttu-id="49422-151">Local 為預設值。</span><span class="sxs-lookup"><span data-stu-id="49422-151">Local is the default.</span></span>
<span data-ttu-id="49422-152">如需詳細資訊，請參閱 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="49422-152">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="49422-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="49422-153">-Confirm</span></span>

<span data-ttu-id="49422-154">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="49422-154">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49422-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="49422-155">-WhatIf</span></span>

<span data-ttu-id="49422-156">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="49422-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="49422-157">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="49422-157">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49422-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="49422-158">CommonParameters</span></span>

<span data-ttu-id="49422-159">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="49422-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="49422-160">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="49422-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="49422-161">輸入</span><span class="sxs-lookup"><span data-stu-id="49422-161">INPUTS</span></span>

### <span data-ttu-id="49422-162">無</span><span class="sxs-lookup"><span data-stu-id="49422-162">None</span></span>

<span data-ttu-id="49422-163">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="49422-163">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="49422-164">輸出</span><span class="sxs-lookup"><span data-stu-id="49422-164">OUTPUTS</span></span>

### <span data-ttu-id="49422-165">無或 System.Management.Automation.PSVariable</span><span class="sxs-lookup"><span data-stu-id="49422-165">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="49422-166">當您使用 *PassThru* 參數時，此 Cmdlet 會產生代表已清除變數的 **system.management.automation.psvariable** 物件。</span><span class="sxs-lookup"><span data-stu-id="49422-166">When you use the *PassThru* parameter, this cmdlet generates a **System.Management.Automation.PSVariable** object representing the cleared variable.</span></span>
<span data-ttu-id="49422-167">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="49422-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="49422-168">注意</span><span class="sxs-lookup"><span data-stu-id="49422-168">NOTES</span></span>

* <span data-ttu-id="49422-169">若要刪除變數與其值，請使用 Remove-Variable 或 Remove-Item。</span><span class="sxs-lookup"><span data-stu-id="49422-169">To delete a variable, along with its value, use Remove-Variable or Remove-Item.</span></span>

  <span data-ttu-id="49422-170">此 Cmdlet 不會刪除設定為常數或系統所擁有的變數值，即使您使用 *Force* 參數也是如此。</span><span class="sxs-lookup"><span data-stu-id="49422-170">This cmdlet does not delete the values of variables that are set as constants or owned by the system, even if you use the *Force* parameter.</span></span>

  <span data-ttu-id="49422-171">如果您清除的變數不存在，Cmdlet 不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="49422-171">If the variable that you are clearing does not exist, the cmdlet has no effect.</span></span>
<span data-ttu-id="49422-172">它不會建立具有 null 值的變數。</span><span class="sxs-lookup"><span data-stu-id="49422-172">It does not create a variable with a null value.</span></span>

  <span data-ttu-id="49422-173">您也可以使用內建的別名 clv 來參考 **清除變數** 。</span><span class="sxs-lookup"><span data-stu-id="49422-173">You can also refer to **Clear-Variable** by its built-in alias, clv.</span></span>
<span data-ttu-id="49422-174">如需詳細資訊，請參閱 about_Aliases。</span><span class="sxs-lookup"><span data-stu-id="49422-174">For more information, see about_Aliases.</span></span>

*

## <span data-ttu-id="49422-175">相關連結</span><span class="sxs-lookup"><span data-stu-id="49422-175">RELATED LINKS</span></span>

[<span data-ttu-id="49422-176">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="49422-176">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="49422-177">New-Variable</span><span class="sxs-lookup"><span data-stu-id="49422-177">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="49422-178">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="49422-178">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="49422-179">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="49422-179">Set-Variable</span></span>](Set-Variable.md)
