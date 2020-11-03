---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 392f7d4be1e174e9ce270f4351adefbca4fe38e5
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239959"
---
# <span data-ttu-id="e74b3-103">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="e74b3-103">Set-Variable</span></span>

## <span data-ttu-id="e74b3-104">概要</span><span class="sxs-lookup"><span data-stu-id="e74b3-104">SYNOPSIS</span></span>
<span data-ttu-id="e74b3-105">設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="e74b3-105">Sets the value of a variable.</span></span> <span data-ttu-id="e74b3-106">如果要求的名稱的變數不存在，便會建立變數。</span><span class="sxs-lookup"><span data-stu-id="e74b3-106">Creates the variable if one with the requested name does not exist.</span></span>

## <span data-ttu-id="e74b3-107">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e74b3-107">SYNTAX</span></span>

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e74b3-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e74b3-108">DESCRIPTION</span></span>

<span data-ttu-id="e74b3-109">Cmdlet 會將 `Set-Variable` 值指派給指定的變數，或變更目前的值。</span><span class="sxs-lookup"><span data-stu-id="e74b3-109">The `Set-Variable` cmdlet assigns a value to a specified variable or changes the current value.</span></span> <span data-ttu-id="e74b3-110">如果變數不存在，Cmdlet 就會建立變數。</span><span class="sxs-lookup"><span data-stu-id="e74b3-110">If the variable does not exist, the cmdlet creates it.</span></span>

## <span data-ttu-id="e74b3-111">範例</span><span class="sxs-lookup"><span data-stu-id="e74b3-111">EXAMPLES</span></span>

### <span data-ttu-id="e74b3-112">範例 1︰設定變數，並取得其值</span><span class="sxs-lookup"><span data-stu-id="e74b3-112">Example 1: Set a variable and get its value</span></span>

<span data-ttu-id="e74b3-113">這些命令會將變數的值設定 `$desc` 為 `A description` ，然後取得變數的值。</span><span class="sxs-lookup"><span data-stu-id="e74b3-113">These commands set the value of the `$desc` variable to `A description`, and then gets the value of the variable.</span></span>

```powershell
Set-Variable -Name "desc" -Value "A description"
Get-Variable -Name "desc"
```

```Output
Name                           Value
----                           -----
desc                           A description
```

### <span data-ttu-id="e74b3-114">範例 2︰設定全域、唯讀變數</span><span class="sxs-lookup"><span data-stu-id="e74b3-114">Example 2: Set a global, read-only variable</span></span>

<span data-ttu-id="e74b3-115">這個範例會建立全域的唯讀變數，其中包含系統上的所有處理常式，然後顯示該變數的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="e74b3-115">This example creates a global, read-only variable that contains all processes on the system, and then it displays all properties of the variable.</span></span>

```powershell
Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru |
    Format-List -Property *
```

<span data-ttu-id="e74b3-116">此命令會使用 `Set-Variable` Cmdlet 來建立變數。</span><span class="sxs-lookup"><span data-stu-id="e74b3-116">The command uses the `Set-Variable` cmdlet to create the variable.</span></span> <span data-ttu-id="e74b3-117">它使用 **PassThru** 參數建立代表新變數的物件，並使用管線運算子 (`|`) 將物件傳遞給 `Format-List` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e74b3-117">It uses the **PassThru** parameter to create an object representing the new variable, and it uses the pipeline operator (`|`) to pass the object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="e74b3-118">它會使用的 **屬性** 參數搭配 `Format-List` 所有 () 的值 `*` ，以顯示新建立之變數的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="e74b3-118">It uses the **Property** parameter of `Format-List` with a value of all (`*`) to display all properties of the newly created variable.</span></span>

<span data-ttu-id="e74b3-119">值是以 `(Get-Process)` 括弧括住，以確保它會在儲存于變數之前執行。</span><span class="sxs-lookup"><span data-stu-id="e74b3-119">The value, `(Get-Process)`, is enclosed in parentheses to ensure that it is executed before being stored in the variable.</span></span> <span data-ttu-id="e74b3-120">否則，變數會包含 " **Get-Process** " 單字。</span><span class="sxs-lookup"><span data-stu-id="e74b3-120">Otherwise, the variable contains the words " **Get-Process** ".</span></span>

### <span data-ttu-id="e74b3-121">範例 3︰了解公用與私用變數</span><span class="sxs-lookup"><span data-stu-id="e74b3-121">Example 3: Understand public vs. private variables</span></span>

<span data-ttu-id="e74b3-122">此範例示範如何將變數的可見度變更為 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="e74b3-122">This example shows how to change the visibility of a variable to `Private`.</span></span> <span data-ttu-id="e74b3-123">此變數可以由有必要權限的指令碼讀取和變更，但使用者看不到此變數。</span><span class="sxs-lookup"><span data-stu-id="e74b3-123">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

```
PS C:\> New-Variable -Name "counter" -Visibility Public -Value 26
PS C:\> $Counter
26

PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}
Counter               26

PS C:\> Set-Variable -Name "counter" -Visibility Private
PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"

PS C:\> .\use-counter.ps1
#Commands completed successfully.
```

<span data-ttu-id="e74b3-124">此命令會顯示如何將變數的可見性變更為「私用」。</span><span class="sxs-lookup"><span data-stu-id="e74b3-124">This command shows how to change the visibility of a variable to Private.</span></span> <span data-ttu-id="e74b3-125">此變數可以由有必要權限的指令碼讀取和變更，但使用者看不到此變數。</span><span class="sxs-lookup"><span data-stu-id="e74b3-125">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

## <span data-ttu-id="e74b3-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e74b3-126">PARAMETERS</span></span>

### <span data-ttu-id="e74b3-127">-Description</span><span class="sxs-lookup"><span data-stu-id="e74b3-127">-Description</span></span>

<span data-ttu-id="e74b3-128">指定變數的描述。</span><span class="sxs-lookup"><span data-stu-id="e74b3-128">Specifies the description of the variable.</span></span>

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

### <span data-ttu-id="e74b3-129">-Exclude</span><span class="sxs-lookup"><span data-stu-id="e74b3-129">-Exclude</span></span>

<span data-ttu-id="e74b3-130">指定此 Cmdlet 從作業排除之項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="e74b3-130">Specifies an array of items that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="e74b3-131">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="e74b3-131">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e74b3-132">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="e74b3-132">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="e74b3-133">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="e74b3-133">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="e74b3-134">-Force</span><span class="sxs-lookup"><span data-stu-id="e74b3-134">-Force</span></span>

<span data-ttu-id="e74b3-135">允許您建立與現有唯讀變數同名的變數，或變更唯讀變數的值。</span><span class="sxs-lookup"><span data-stu-id="e74b3-135">Allows you to create a variable with the same name as an existing read-only variable, or to change the value of a read-only variable.</span></span>

<span data-ttu-id="e74b3-136">根據預設，您可以覆寫變數，除非變數有或的選項值 `ReadOnly` `Constant` 。</span><span class="sxs-lookup"><span data-stu-id="e74b3-136">By default, you can overwrite a variable, unless the variable has an option value of `ReadOnly` or `Constant`.</span></span> <span data-ttu-id="e74b3-137">如需詳細資訊，請參閱 **Option** 參數。</span><span class="sxs-lookup"><span data-stu-id="e74b3-137">For more information, see the **Option** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e74b3-138">-Include</span><span class="sxs-lookup"><span data-stu-id="e74b3-138">-Include</span></span>

<span data-ttu-id="e74b3-139">指定此 Cmdlet 在作業中納入之項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="e74b3-139">Specifies an array of items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="e74b3-140">此參數的值會限定 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="e74b3-140">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="e74b3-141">輸入名稱或名稱模式，例如 `c*`。</span><span class="sxs-lookup"><span data-stu-id="e74b3-141">Enter a name or name pattern, such as `c*`.</span></span> <span data-ttu-id="e74b3-142">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="e74b3-142">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="e74b3-143">-Name</span><span class="sxs-lookup"><span data-stu-id="e74b3-143">-Name</span></span>

<span data-ttu-id="e74b3-144">指定變數名稱。</span><span class="sxs-lookup"><span data-stu-id="e74b3-144">Specifies the variable name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e74b3-145">-Option</span><span class="sxs-lookup"><span data-stu-id="e74b3-145">-Option</span></span>

<span data-ttu-id="e74b3-146">指定變數的 **Options** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="e74b3-146">Specifies the value of the **Options** property of the variable.</span></span>

<span data-ttu-id="e74b3-147">有效值為：</span><span class="sxs-lookup"><span data-stu-id="e74b3-147">Valid values are:</span></span>

- <span data-ttu-id="e74b3-148">`None`：不設定任何選項。</span><span class="sxs-lookup"><span data-stu-id="e74b3-148">`None`: Sets no options.</span></span> <span data-ttu-id="e74b3-149">("None" 為預設值。)</span><span class="sxs-lookup"><span data-stu-id="e74b3-149">("None" is the default.)</span></span>
- <span data-ttu-id="e74b3-150">`ReadOnly`：可以刪除。</span><span class="sxs-lookup"><span data-stu-id="e74b3-150">`ReadOnly`: Can be deleted.</span></span> <span data-ttu-id="e74b3-151">除非使用 Force 參數，否則無法變更。</span><span class="sxs-lookup"><span data-stu-id="e74b3-151">Cannot be changed, except by using the Force parameter.</span></span>
- <span data-ttu-id="e74b3-152">`Constant`：無法刪除或變更。</span><span class="sxs-lookup"><span data-stu-id="e74b3-152">`Constant`: Cannot be deleted or changed.</span></span> <span data-ttu-id="e74b3-153">`Constant` 只有在您建立變數時才有效。</span><span class="sxs-lookup"><span data-stu-id="e74b3-153">`Constant` is valid only when you are creating a variable.</span></span> <span data-ttu-id="e74b3-154">您無法將現有變數的選項變更為 `Constant` 。</span><span class="sxs-lookup"><span data-stu-id="e74b3-154">You cannot change the options of an existing variable to `Constant`.</span></span>
- <span data-ttu-id="e74b3-155">`Private`：變數僅適用于目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="e74b3-155">`Private`: The variable is available only in the current scope.</span></span>
- <span data-ttu-id="e74b3-156">`AllScope`：變數會複製到所建立的任何新範圍。</span><span class="sxs-lookup"><span data-stu-id="e74b3-156">`AllScope`: The variable is copied to any new scopes that are created.</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e74b3-157">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e74b3-157">-PassThru</span></span>

<span data-ttu-id="e74b3-158">傳回代表新變數的物件。</span><span class="sxs-lookup"><span data-stu-id="e74b3-158">Returns an object representing the new variable.</span></span> <span data-ttu-id="e74b3-159">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="e74b3-159">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e74b3-160">-Scope</span><span class="sxs-lookup"><span data-stu-id="e74b3-160">-Scope</span></span>

<span data-ttu-id="e74b3-161">指定變數的範圍。此參數可接受的值包括：</span><span class="sxs-lookup"><span data-stu-id="e74b3-161">Specifies the scope of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e74b3-162">全球</span><span class="sxs-lookup"><span data-stu-id="e74b3-162">Global</span></span>
- <span data-ttu-id="e74b3-163">本機</span><span class="sxs-lookup"><span data-stu-id="e74b3-163">Local</span></span>
- <span data-ttu-id="e74b3-164">指令碼</span><span class="sxs-lookup"><span data-stu-id="e74b3-164">Script</span></span>
- <span data-ttu-id="e74b3-165">私人</span><span class="sxs-lookup"><span data-stu-id="e74b3-165">Private</span></span>
- <span data-ttu-id="e74b3-166">相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。</span><span class="sxs-lookup"><span data-stu-id="e74b3-166">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="e74b3-167">Local 為預設值。</span><span class="sxs-lookup"><span data-stu-id="e74b3-167">Local is the default.</span></span>

<span data-ttu-id="e74b3-168">如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="e74b3-168">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e74b3-169">-Value</span><span class="sxs-lookup"><span data-stu-id="e74b3-169">-Value</span></span>

<span data-ttu-id="e74b3-170">指定變數的值。</span><span class="sxs-lookup"><span data-stu-id="e74b3-170">Specifies the value of the variable.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e74b3-171">-Visibility</span><span class="sxs-lookup"><span data-stu-id="e74b3-171">-Visibility</span></span>

<span data-ttu-id="e74b3-172">決定是否可在變數建立所在的工作階段之外看見變數。</span><span class="sxs-lookup"><span data-stu-id="e74b3-172">Determines whether the variable is visible outside of the session in which it was created.</span></span> <span data-ttu-id="e74b3-173">此參數是針對將傳遞給其他使用者的指令碼和命令中使用所設計。</span><span class="sxs-lookup"><span data-stu-id="e74b3-173">This parameter is designed for use in scripts and commands that will be delivered to other users.</span></span>

<span data-ttu-id="e74b3-174">有效值為：</span><span class="sxs-lookup"><span data-stu-id="e74b3-174">Valid values are:</span></span>

- <span data-ttu-id="e74b3-175">Public：可看見變數。</span><span class="sxs-lookup"><span data-stu-id="e74b3-175">Public:  The variable is visible.</span></span> <span data-ttu-id="e74b3-176">("Public" 為預設值。)</span><span class="sxs-lookup"><span data-stu-id="e74b3-176">("Public" is the default.)</span></span>
- <span data-ttu-id="e74b3-177">Private：看不到變數。</span><span class="sxs-lookup"><span data-stu-id="e74b3-177">Private: The variable is not visible.</span></span>

<span data-ttu-id="e74b3-178">當變數為私用時，它不會出現在變數的清單中，例如傳回的變數， `Get-Variable` 或變數 **：** 磁片磁碟機的顯示中。</span><span class="sxs-lookup"><span data-stu-id="e74b3-178">When a variable is private, it does not appear in lists of variables, such as those returned by `Get-Variable`, or in displays of the **Variable:** drive.</span></span> <span data-ttu-id="e74b3-179">讀取或變更私用變數值的命令會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="e74b3-179">Commands to read or change the value of a private variable return an error.</span></span> <span data-ttu-id="e74b3-180">但是，如果命令是寫入在定義變數的工作階段中，使用者就可以執行使用私用變數的命令。</span><span class="sxs-lookup"><span data-stu-id="e74b3-180">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: Public
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e74b3-181">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e74b3-181">-Confirm</span></span>

<span data-ttu-id="e74b3-182">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="e74b3-182">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e74b3-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e74b3-183">-WhatIf</span></span>

<span data-ttu-id="e74b3-184">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="e74b3-184">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e74b3-185">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="e74b3-185">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e74b3-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e74b3-186">CommonParameters</span></span>

<span data-ttu-id="e74b3-187">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e74b3-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e74b3-188">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e74b3-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e74b3-189">輸入</span><span class="sxs-lookup"><span data-stu-id="e74b3-189">INPUTS</span></span>

### <span data-ttu-id="e74b3-190">System.Object</span><span class="sxs-lookup"><span data-stu-id="e74b3-190">System.Object</span></span>

<span data-ttu-id="e74b3-191">您可以使用管線將代表變數值的物件傳送至 `Set-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="e74b3-191">You can pipe an object that represents the value of the variable to `Set-Variable`.</span></span>

## <span data-ttu-id="e74b3-192">輸出</span><span class="sxs-lookup"><span data-stu-id="e74b3-192">OUTPUTS</span></span>

### <span data-ttu-id="e74b3-193">無或 System.Management.Automation.PSVariable</span><span class="sxs-lookup"><span data-stu-id="e74b3-193">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="e74b3-194">當您使用 **PassThru** 參數時，會 `Set-Variable` 產生代表新變數或已變更變數的 **system.management.automation.psvariable** 物件。</span><span class="sxs-lookup"><span data-stu-id="e74b3-194">When you use the **PassThru** parameter, `Set-Variable` generates a **System.Management.Automation.PSVariable** object representing the new or changed variable.</span></span>
<span data-ttu-id="e74b3-195">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="e74b3-195">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e74b3-196">注意</span><span class="sxs-lookup"><span data-stu-id="e74b3-196">NOTES</span></span>

## <span data-ttu-id="e74b3-197">相關連結</span><span class="sxs-lookup"><span data-stu-id="e74b3-197">RELATED LINKS</span></span>

[<span data-ttu-id="e74b3-198">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="e74b3-198">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="e74b3-199">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="e74b3-199">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="e74b3-200">New-Variable</span><span class="sxs-lookup"><span data-stu-id="e74b3-200">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="e74b3-201">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="e74b3-201">Remove-Variable</span></span>](Remove-Variable.md)
