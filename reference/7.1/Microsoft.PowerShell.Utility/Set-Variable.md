---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: ba17b526de91e470149e90913814ecfac0f75392
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202176"
---
# <span data-ttu-id="ed411-103">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="ed411-103">Set-Variable</span></span>

## <span data-ttu-id="ed411-104">概要</span><span class="sxs-lookup"><span data-stu-id="ed411-104">SYNOPSIS</span></span>
<span data-ttu-id="ed411-105">設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="ed411-105">Sets the value of a variable.</span></span>
<span data-ttu-id="ed411-106">如果要求的名稱的變數不存在，便會建立變數。</span><span class="sxs-lookup"><span data-stu-id="ed411-106">Creates the variable if one with the requested name does not exist.</span></span>

## <span data-ttu-id="ed411-107">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ed411-107">SYNTAX</span></span>

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ed411-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ed411-108">DESCRIPTION</span></span>

<span data-ttu-id="ed411-109">**Set-Variable** Cmdlet 會將值指派給指定的變數，或變更目前的值。</span><span class="sxs-lookup"><span data-stu-id="ed411-109">The **Set-Variable** cmdlet assigns a value to a specified variable or changes the current value.</span></span>
<span data-ttu-id="ed411-110">如果變數不存在，Cmdlet 就會建立變數。</span><span class="sxs-lookup"><span data-stu-id="ed411-110">If the variable does not exist, the cmdlet creates it.</span></span>

## <span data-ttu-id="ed411-111">範例</span><span class="sxs-lookup"><span data-stu-id="ed411-111">EXAMPLES</span></span>

### <span data-ttu-id="ed411-112">範例 1︰設定變數，並取得其值</span><span class="sxs-lookup"><span data-stu-id="ed411-112">Example 1: Set a variable and get its value</span></span>

```
PS C:\> Set-Variable -Name "desc" -Value "A description"
PS C:\> Get-Variable -Name "desc"
```

<span data-ttu-id="ed411-113">這些命令會將 desc 變數的值設定為 A description，然後取得變數的值。</span><span class="sxs-lookup"><span data-stu-id="ed411-113">These commands set the value of the desc variable to A description, and then gets the value of the variable.</span></span>

### <span data-ttu-id="ed411-114">範例 2︰設定全域、唯讀變數</span><span class="sxs-lookup"><span data-stu-id="ed411-114">Example 2: Set a global, read-only variable</span></span>

```
PS C:\> Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru | Format-List -Property *
```

<span data-ttu-id="ed411-115">此命令建立包含系統上所有處理程序的全域、唯讀變數，然後顯示該變數的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="ed411-115">This command creates a global, read-only variable that contains all processes on the system, and then it displays all properties of the variable.</span></span>

<span data-ttu-id="ed411-116">命令使用 **Set-Variable** Cmdlet 建立變數。</span><span class="sxs-lookup"><span data-stu-id="ed411-116">The command uses the **Set-Variable** cmdlet to create the variable.</span></span>
<span data-ttu-id="ed411-117">它使用 *PassThru* 參數建立代表新變數的物件，並使用管線運算子 (|) 將物件傳遞至 Format-list Cmdlet 。</span><span class="sxs-lookup"><span data-stu-id="ed411-117">It uses the *PassThru* parameter to create an object representing the new variable, and it uses the pipeline operator (|) to pass the object to the Format-List cmdlet.</span></span>
<span data-ttu-id="ed411-118">它使用 Format-List 的 *Property* 參數與全部 (\*) 的值，顯示新建立之變數的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="ed411-118">It uses the *Property* parameter of Format-List with a value of all (\*) to display all properties of the newly created variable.</span></span>

<span data-ttu-id="ed411-119">"(Get-Process)" 值是括在括號內，以確保它在執行之後才儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="ed411-119">The value, "(Get-Process)", is enclosed in parentheses to ensure that it is executed before being stored in the variable.</span></span>
<span data-ttu-id="ed411-120">否則變數包含會 "Get-Process" 字詞。</span><span class="sxs-lookup"><span data-stu-id="ed411-120">Otherwise, the variable contains the words "Get-Process".</span></span>

### <span data-ttu-id="ed411-121">範例 3︰了解公用與私用變數</span><span class="sxs-lookup"><span data-stu-id="ed411-121">Example 3: Understand public vs. private variables</span></span>

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

<span data-ttu-id="ed411-122">此命令會顯示如何將變數的可見性變更為「私用」。</span><span class="sxs-lookup"><span data-stu-id="ed411-122">This command shows how to change the visibility of a variable to Private.</span></span>
<span data-ttu-id="ed411-123">此變數可以由有必要權限的指令碼讀取和變更，但使用者看不到此變數。</span><span class="sxs-lookup"><span data-stu-id="ed411-123">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

<span data-ttu-id="ed411-124">範例輸出顯示公用和私用變數的行為差異。</span><span class="sxs-lookup"><span data-stu-id="ed411-124">The sample output shows the difference in the behavior of public and private variables.</span></span>

## <span data-ttu-id="ed411-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ed411-125">PARAMETERS</span></span>

### <span data-ttu-id="ed411-126">-Description</span><span class="sxs-lookup"><span data-stu-id="ed411-126">-Description</span></span>

<span data-ttu-id="ed411-127">指定變數的描述。</span><span class="sxs-lookup"><span data-stu-id="ed411-127">Specifies the description of the variable.</span></span>

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

### <span data-ttu-id="ed411-128">-Exclude</span><span class="sxs-lookup"><span data-stu-id="ed411-128">-Exclude</span></span>

<span data-ttu-id="ed411-129">指定此 Cmdlet 從作業排除之項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="ed411-129">Specifies an array of items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="ed411-130">此參數的值會限定 *Path* 參數。</span><span class="sxs-lookup"><span data-stu-id="ed411-130">The value of this parameter qualifies the *Path* parameter.</span></span>
<span data-ttu-id="ed411-131">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="ed411-131">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="ed411-132">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ed411-132">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="ed411-133">-Force</span><span class="sxs-lookup"><span data-stu-id="ed411-133">-Force</span></span>

<span data-ttu-id="ed411-134">允許您建立與現有唯讀變數同名的變數，或變更唯讀變數的值。</span><span class="sxs-lookup"><span data-stu-id="ed411-134">Allows you to create a variable with the same name as an existing read-only variable, or to change the value of a read-only variable.</span></span>

<span data-ttu-id="ed411-135">根據預設，您可以覆寫變數，除非該變數具有 ReadOnly 或 Constant 的選項值。</span><span class="sxs-lookup"><span data-stu-id="ed411-135">By default, you can overwrite a variable, unless the variable has an option value of ReadOnly or Constant.</span></span>
<span data-ttu-id="ed411-136">如需詳細資訊，請參閱 *Option* 參數。</span><span class="sxs-lookup"><span data-stu-id="ed411-136">For more information, see the *Option* parameter.</span></span>

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

### <span data-ttu-id="ed411-137">-Include</span><span class="sxs-lookup"><span data-stu-id="ed411-137">-Include</span></span>

<span data-ttu-id="ed411-138">指定此 Cmdlet 在作業中納入之項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="ed411-138">Specifies an array of items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="ed411-139">此參數的值會限定 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="ed411-139">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="ed411-140">輸入名稱或名稱模式，例如 `c*`。</span><span class="sxs-lookup"><span data-stu-id="ed411-140">Enter a name or name pattern, such as `c*`.</span></span>
<span data-ttu-id="ed411-141">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ed411-141">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="ed411-142">-Name</span><span class="sxs-lookup"><span data-stu-id="ed411-142">-Name</span></span>

<span data-ttu-id="ed411-143">指定變數名稱。</span><span class="sxs-lookup"><span data-stu-id="ed411-143">Specifies the variable name.</span></span>

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

### <span data-ttu-id="ed411-144">-Option</span><span class="sxs-lookup"><span data-stu-id="ed411-144">-Option</span></span>

<span data-ttu-id="ed411-145">指定變數的 **Options** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="ed411-145">Specifies the value of the **Options** property of the variable.</span></span>

<span data-ttu-id="ed411-146">有效值為：</span><span class="sxs-lookup"><span data-stu-id="ed411-146">Valid values are:</span></span>

- <span data-ttu-id="ed411-147">None：不設定任何選項。</span><span class="sxs-lookup"><span data-stu-id="ed411-147">None: Sets no options.</span></span> <span data-ttu-id="ed411-148">("None" 為預設值。)</span><span class="sxs-lookup"><span data-stu-id="ed411-148">("None" is the default.)</span></span>
- <span data-ttu-id="ed411-149">ReadOnly：可以刪除。</span><span class="sxs-lookup"><span data-stu-id="ed411-149">ReadOnly: Can be deleted.</span></span> <span data-ttu-id="ed411-150">除非使用 Force 參數，否則無法變更。</span><span class="sxs-lookup"><span data-stu-id="ed411-150">Cannot be changed, except by using the Force parameter.</span></span>
- <span data-ttu-id="ed411-151">Constant：不能刪除或變更。</span><span class="sxs-lookup"><span data-stu-id="ed411-151">Constant: Cannot be deleted or changed.</span></span> <span data-ttu-id="ed411-152">"Constant" 只在您建立變數時有效。</span><span class="sxs-lookup"><span data-stu-id="ed411-152">"Constant" is valid only when you are creating a variable.</span></span> <span data-ttu-id="ed411-153">您不能將現有變數的選項變更為 "Constant"。</span><span class="sxs-lookup"><span data-stu-id="ed411-153">You cannot change the options of an existing variable to "Constant".</span></span>
- <span data-ttu-id="ed411-154">Private：變數只能在目前的範圍中使用。</span><span class="sxs-lookup"><span data-stu-id="ed411-154">Private: The variable is available only in the current scope.</span></span>
- <span data-ttu-id="ed411-155">AllScope：將變數複製到任何新建立的範圍。</span><span class="sxs-lookup"><span data-stu-id="ed411-155">AllScope: The variable is copied to any new scopes that are created.</span></span>

<span data-ttu-id="ed411-156">若要查看工作階段中所有變數的 **Options** 屬性，請輸入 `Get-Variable | Format-Table -Property name, options -Autosize`。</span><span class="sxs-lookup"><span data-stu-id="ed411-156">To see the **Options** property of all variables in the session, type `Get-Variable | Format-Table -Property name, options -Autosize`.</span></span>

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

### <span data-ttu-id="ed411-157">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ed411-157">-PassThru</span></span>
<span data-ttu-id="ed411-158">傳回代表新變數的物件。</span><span class="sxs-lookup"><span data-stu-id="ed411-158">Returns an object representing the new variable.</span></span>
<span data-ttu-id="ed411-159">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="ed411-159">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="ed411-160">-Scope</span><span class="sxs-lookup"><span data-stu-id="ed411-160">-Scope</span></span>

<span data-ttu-id="ed411-161">指定變數的範圍。此參數可接受的值包括：</span><span class="sxs-lookup"><span data-stu-id="ed411-161">Specifies the scope of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ed411-162">全球</span><span class="sxs-lookup"><span data-stu-id="ed411-162">Global</span></span>
- <span data-ttu-id="ed411-163">本機</span><span class="sxs-lookup"><span data-stu-id="ed411-163">Local</span></span>
- <span data-ttu-id="ed411-164">指令碼</span><span class="sxs-lookup"><span data-stu-id="ed411-164">Script</span></span>
- <span data-ttu-id="ed411-165">私人</span><span class="sxs-lookup"><span data-stu-id="ed411-165">Private</span></span>
- <span data-ttu-id="ed411-166">相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。</span><span class="sxs-lookup"><span data-stu-id="ed411-166">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="ed411-167">Local 為預設值。</span><span class="sxs-lookup"><span data-stu-id="ed411-167">Local is the default.</span></span>

<span data-ttu-id="ed411-168">如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="ed411-168">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span></span>

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

### <span data-ttu-id="ed411-169">-Value</span><span class="sxs-lookup"><span data-stu-id="ed411-169">-Value</span></span>

<span data-ttu-id="ed411-170">指定變數的值。</span><span class="sxs-lookup"><span data-stu-id="ed411-170">Specifies the value of the variable.</span></span>

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

### <span data-ttu-id="ed411-171">-Visibility</span><span class="sxs-lookup"><span data-stu-id="ed411-171">-Visibility</span></span>

<span data-ttu-id="ed411-172">決定是否可在變數建立所在的工作階段之外看見變數。</span><span class="sxs-lookup"><span data-stu-id="ed411-172">Determines whether the variable is visible outside of the session in which it was created.</span></span>
<span data-ttu-id="ed411-173">此參數是針對將傳遞給其他使用者的指令碼和命令中使用所設計。</span><span class="sxs-lookup"><span data-stu-id="ed411-173">This parameter is designed for  use in scripts and commands that will be delivered to other users.</span></span>

<span data-ttu-id="ed411-174">有效值為：</span><span class="sxs-lookup"><span data-stu-id="ed411-174">Valid values are:</span></span>

- <span data-ttu-id="ed411-175">Public：可看見變數。</span><span class="sxs-lookup"><span data-stu-id="ed411-175">Public:  The variable is visible.</span></span> <span data-ttu-id="ed411-176">("Public" 為預設值。)</span><span class="sxs-lookup"><span data-stu-id="ed411-176">("Public" is the default.)</span></span>
- <span data-ttu-id="ed411-177">Private：看不到變數。</span><span class="sxs-lookup"><span data-stu-id="ed411-177">Private: The variable is not visible.</span></span>

<span data-ttu-id="ed411-178">當變數為私用變數時，它不會顯示在變數清單中 (例如由 Get-Variable 傳回的清單) 或顯示在 Variable: 磁碟機的顯示畫面中。</span><span class="sxs-lookup"><span data-stu-id="ed411-178">When a variable is private, it does not appear in lists of variables, such as those returned by Get-Variable, or in displays of the Variable: drive.</span></span>
<span data-ttu-id="ed411-179">讀取或變更私用變數值的命令會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="ed411-179">Commands to read or change the value of a private variable return an error.</span></span>
<span data-ttu-id="ed411-180">但是，如果命令是寫入在定義變數的工作階段中，使用者就可以執行使用私用變數的命令。</span><span class="sxs-lookup"><span data-stu-id="ed411-180">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

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

### <span data-ttu-id="ed411-181">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ed411-181">-Confirm</span></span>
<span data-ttu-id="ed411-182">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="ed411-182">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ed411-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ed411-183">-WhatIf</span></span>

<span data-ttu-id="ed411-184">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="ed411-184">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ed411-185">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="ed411-185">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ed411-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ed411-186">CommonParameters</span></span>

<span data-ttu-id="ed411-187">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ed411-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ed411-188">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ed411-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ed411-189">輸入</span><span class="sxs-lookup"><span data-stu-id="ed411-189">INPUTS</span></span>

### <span data-ttu-id="ed411-190">System.Object</span><span class="sxs-lookup"><span data-stu-id="ed411-190">System.Object</span></span>

<span data-ttu-id="ed411-191">您可以使用管線將代表變數值的物件傳送至 **Set-Variable** 。</span><span class="sxs-lookup"><span data-stu-id="ed411-191">You can pipe an object that represents the value of the variable to **Set-Variable** .</span></span>

## <span data-ttu-id="ed411-192">輸出</span><span class="sxs-lookup"><span data-stu-id="ed411-192">OUTPUTS</span></span>

### <span data-ttu-id="ed411-193">無或 System.Management.Automation.PSVariable</span><span class="sxs-lookup"><span data-stu-id="ed411-193">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="ed411-194">使用 *PassThru* 參數時， **Set-Variable** 會產生代表新變數或已變更變數的 **System.Management.Automation.PSVariable** 物件。</span><span class="sxs-lookup"><span data-stu-id="ed411-194">When you use the *PassThru* parameter, **Set-Variable** generates a **System.Management.Automation.PSVariable** object representing the new or changed variable.</span></span>
<span data-ttu-id="ed411-195">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="ed411-195">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ed411-196">注意</span><span class="sxs-lookup"><span data-stu-id="ed411-196">NOTES</span></span>

## <span data-ttu-id="ed411-197">相關連結</span><span class="sxs-lookup"><span data-stu-id="ed411-197">RELATED LINKS</span></span>

[<span data-ttu-id="ed411-198">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="ed411-198">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="ed411-199">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="ed411-199">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="ed411-200">New-Variable</span><span class="sxs-lookup"><span data-stu-id="ed411-200">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="ed411-201">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="ed411-201">Remove-Variable</span></span>](Remove-Variable.md)

