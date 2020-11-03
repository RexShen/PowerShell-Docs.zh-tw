---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: 8d45f8b6b0272394fe855be07243412bd3a15d71
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201456"
---
# <span data-ttu-id="5ba3a-103">New-Variable</span><span class="sxs-lookup"><span data-stu-id="5ba3a-103">New-Variable</span></span>

## <span data-ttu-id="5ba3a-104">概要</span><span class="sxs-lookup"><span data-stu-id="5ba3a-104">SYNOPSIS</span></span>
<span data-ttu-id="5ba3a-105">建立新變數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-105">Creates a new variable.</span></span>

## <span data-ttu-id="5ba3a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5ba3a-106">SYNTAX</span></span>

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="5ba3a-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5ba3a-107">DESCRIPTION</span></span>
<span data-ttu-id="5ba3a-108">**新的-Variable** Cmdlet 會在 PowerShell 中建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-108">The **New-Variable** cmdlet creates a new variable in PowerShell.</span></span>
<span data-ttu-id="5ba3a-109">您可以在建立變數時指派值給變數，或者在建立後指派或變更變數的值。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-109">You can assign a value to the variable while creating it or assign or change the value after it is created.</span></span>

<span data-ttu-id="5ba3a-110">您可以使用 **New-Variable** 的參數來設定變數的屬性、設定變數的範圍，以及決定變數是公開或私用變數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-110">You can use the parameters of **New-Variable** to set the properties of the variable, set the scope of a variable, and determine whether variables are public or private.</span></span>

<span data-ttu-id="5ba3a-111">您通常會透過輸入變數名稱及其值來建立新的變數 (例如 `$Var = 3`)，但您可以使用 **New-Variable** Cmdlet 來使用其參數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-111">Typically, you create a new variable by typing the variable name and its value, such as `$Var = 3`, but you can use the **New-Variable** cmdlet to use its parameters.</span></span>

## <span data-ttu-id="5ba3a-112">範例</span><span class="sxs-lookup"><span data-stu-id="5ba3a-112">EXAMPLES</span></span>

### <span data-ttu-id="5ba3a-113">範例 1︰建立變數</span><span class="sxs-lookup"><span data-stu-id="5ba3a-113">Example 1: Create a variable</span></span>

```
PS C:\> New-Variable days
```

<span data-ttu-id="5ba3a-114">此命令會建立名為 days 的新參數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-114">This command creates a new variable named days.</span></span>
<span data-ttu-id="5ba3a-115">您不需要輸入 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-115">You are not required to type the *Name* parameter.</span></span>

### <span data-ttu-id="5ba3a-116">範例 2︰建立變數並指派其值</span><span class="sxs-lookup"><span data-stu-id="5ba3a-116">Example 2: Create a variable and assign it a value</span></span>

```
PS C:\> New-Variable -Name "zipcode" -Value 98033
```

<span data-ttu-id="5ba3a-117">此命令會建立名為 zipcode 的變數，並指派 98033 做為其值。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-117">This command creates a variable named zipcode and assigns it the value 98033.</span></span>

### <span data-ttu-id="5ba3a-118">範例 3︰使用 ReadOnly 選項建立變數</span><span class="sxs-lookup"><span data-stu-id="5ba3a-118">Example 3: Create a variable with the ReadOnly option</span></span>

```
PS C:\> New-Variable -Name Max -Value 256 -Option ReadOnly
PS C:\> New-Variable -Name max -Value 1024

New-Variable : A variable with name 'max' already exists.
At line:1 char:1
+ New-Variable -Name max -Value 1024
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ResourceExists: (max:String) [New-Variable], SessionStateException
    + FullyQualifiedErrorId : VariableAlreadyExists,Microsoft.PowerShell.Commands.NewVariableCommand

PS C:\> New-Variable -Name max -Value 1024 -Force
```

<span data-ttu-id="5ba3a-119">此範例示範如何使用 **New-Variable** 的 ReadOnly 選項來保護變數不會遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-119">This example shows how to use the ReadOnly option of **New-Variable** to protect a variable from being overwritten.</span></span>

<span data-ttu-id="5ba3a-120">第一個命令會建立名為 Max 的新變數，並將它的值設為 256。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-120">The first command creates a new variable named Max and sets its value to 256.</span></span>
<span data-ttu-id="5ba3a-121">它會使用值為 ReadOnly 的 *Option* 參數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-121">It uses the *Option* parameter with a value of ReadOnly.</span></span>

<span data-ttu-id="5ba3a-122">第二個命令會嘗試建立名稱相同的第二個變數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-122">The second command tries to create a second variable with the same name.</span></span>
<span data-ttu-id="5ba3a-123">此命令會傳回錯誤，因為變數上已設定唯讀選項。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-123">This command returns an error, because the read-only option is set on the variable.</span></span>

<span data-ttu-id="5ba3a-124">第三個命令會使用 *Force* 參數來覆寫變數上的唯讀保護。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-124">The third command uses the *Force* parameter to override the read-only protection on the variable.</span></span>
<span data-ttu-id="5ba3a-125">在此情況下，使用相同名稱建立新變數的命令可以成功執行。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-125">In this case, the command to create a new variable with the same name succeeds.</span></span>

### <span data-ttu-id="5ba3a-126">範例 4︰建立私用變數</span><span class="sxs-lookup"><span data-stu-id="5ba3a-126">Example 4: Create a private variable</span></span>

```
PS C:\> New-Variable -Name counter -Visibility Private

#Effect of private variable in a module.

PS C:\> Get-Variable c*

Name                           Value
----                           -----
Culture                        en-US
ConsoleFileName
ConfirmPreference              High
CommandLineParameters          {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"
At line:1 char:1
+ $counter
+ ~~~~~~~~
    + CategoryInfo          : PermissionDenied: (counter:String) [], SessionStateException
    + FullyQualifiedErrorId : VariableIsPrivate

PS C:\> Get-Counter
Name         Value
----         -----
Counter1     3.1415
...
```

<span data-ttu-id="5ba3a-127">此命令示範模組中私用變數的行為。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-127">This command demonstrates the behavior of a private variable in a module.</span></span>
<span data-ttu-id="5ba3a-128">此模組包含 Get-Counter Cmdlet，它具有名為 Counter 的私用變數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-128">The module contains the Get-Counter cmdlet, which has a private variable named Counter.</span></span>
<span data-ttu-id="5ba3a-129">此命令會使用值為 Private 的 *Visibility* 參數來建立變數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-129">The command uses the *Visibility* parameter with a value of Private to create the variable.</span></span>

<span data-ttu-id="5ba3a-130">範例輸出會顯示私用變數的行為。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-130">The sample output shows the behavior of a private variable.</span></span>
<span data-ttu-id="5ba3a-131">載入模組的使用者無法檢視或變更 Counter 變數的值，但模組中的命令可以讀取及變更 Counter 變數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-131">The user who has loaded the module cannot view or change the value of the Counter variable, but the Counter variable can be read and changed by the commands in the module.</span></span>

### <span data-ttu-id="5ba3a-132">範例5：建立具有空格的變數</span><span class="sxs-lookup"><span data-stu-id="5ba3a-132">Example 5: Create a variable with a space</span></span>

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

<span data-ttu-id="5ba3a-133">此命令示範可以建立具有空格的變數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-133">This command demonstrates that variables with spaces can be created.</span></span>
<span data-ttu-id="5ba3a-134">您可以使用「 **取得變數** 」 Cmdlet 或直接以大括弧分隔變數來存取這些變數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-134">The variables can be accessed using the **Get-Variable** cmdlet or directly by delimiting a variable with braces.</span></span>

## <span data-ttu-id="5ba3a-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5ba3a-135">PARAMETERS</span></span>

### <span data-ttu-id="5ba3a-136">-Description</span><span class="sxs-lookup"><span data-stu-id="5ba3a-136">-Description</span></span>
<span data-ttu-id="5ba3a-137">指定變數的描述。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-137">Specifies a description of the variable.</span></span>

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

### <span data-ttu-id="5ba3a-138">-Force</span><span class="sxs-lookup"><span data-stu-id="5ba3a-138">-Force</span></span>
<span data-ttu-id="5ba3a-139">指出 Cmdlet 會使用和現有唯讀變數相同的名稱建立新變數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-139">Indicates that the cmdlet creates a variable with the same name as an existing read-only variable.</span></span>

<span data-ttu-id="5ba3a-140">根據預設，您可以覆寫變數，除非該變數具有 ReadOnly 或 Constant 的選項值。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-140">By default, you can overwrite a variable unless the variable has an option value of ReadOnly or Constant.</span></span>
<span data-ttu-id="5ba3a-141">如需詳細資訊，請參閱 *Option* 參數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-141">For more information, see the *Option* parameter.</span></span>

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

### <span data-ttu-id="5ba3a-142">-Name</span><span class="sxs-lookup"><span data-stu-id="5ba3a-142">-Name</span></span>
<span data-ttu-id="5ba3a-143">指定新變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-143">Specifies a name for the new variable.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5ba3a-144">-Option</span><span class="sxs-lookup"><span data-stu-id="5ba3a-144">-Option</span></span>
<span data-ttu-id="5ba3a-145">指定變數的 **Options** 屬性值。此參數可接受的值包括：</span><span class="sxs-lookup"><span data-stu-id="5ba3a-145">Specifies the value of the **Options** property of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5ba3a-146">無。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-146">None.</span></span>
<span data-ttu-id="5ba3a-147">不設定任何選項。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-147">Sets no options.</span></span>
<span data-ttu-id="5ba3a-148">(None 為預設值。)</span><span class="sxs-lookup"><span data-stu-id="5ba3a-148">(None is the default.)</span></span>
- <span data-ttu-id="5ba3a-149">ReadOnly。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-149">ReadOnly.</span></span>
<span data-ttu-id="5ba3a-150">可以刪除。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-150">Can be deleted.</span></span>
<span data-ttu-id="5ba3a-151">除非使用 *Force* 參數，否則無法變更。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-151">Cannot be changed, except by using the *Force* parameter.</span></span>
- <span data-ttu-id="5ba3a-152">私人。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-152">Private.</span></span>
<span data-ttu-id="5ba3a-153">變數只能在目前的範圍中使用。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-153">The variable is available only in the current scope.</span></span>
- <span data-ttu-id="5ba3a-154">AllScope。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-154">AllScope.</span></span>
<span data-ttu-id="5ba3a-155">將複製變數到任何新建立的範圍。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-155">The variable is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="5ba3a-156">Constant。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-156">Constant.</span></span>
<span data-ttu-id="5ba3a-157">不能刪除或變更。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-157">Cannot be deleted or changed.</span></span>
<span data-ttu-id="5ba3a-158">Constant 只在您建立變數時有效。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-158">Constant is valid only when you are creating a variable.</span></span>
<span data-ttu-id="5ba3a-159">您不能將現有變數的選項變更為 Constant。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-159">You cannot change the options of an existing variable to Constant.</span></span>

<span data-ttu-id="5ba3a-160">若要查看工作階段中所有變數的 **Options** 屬性，請輸入 `Get-Variable | Format-Table -Property name, options -autosize`。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-160">To see the **Options** property of all variables in the session, type `Get-Variable | Format-Table -Property name, options -autosize`.</span></span>

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

### <span data-ttu-id="5ba3a-161">-PassThru</span><span class="sxs-lookup"><span data-stu-id="5ba3a-161">-PassThru</span></span>
<span data-ttu-id="5ba3a-162">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-162">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="5ba3a-163">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-163">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="5ba3a-164">-Scope</span><span class="sxs-lookup"><span data-stu-id="5ba3a-164">-Scope</span></span>
<span data-ttu-id="5ba3a-165">指定新變數的範圍。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-165">Specifies the scope of the new variable.</span></span>
<span data-ttu-id="5ba3a-166">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="5ba3a-166">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5ba3a-167">全域。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-167">Global.</span></span>
<span data-ttu-id="5ba3a-168">在全域範圍中建立的變數可在 PowerShell 處理常式中隨處存取。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-168">Variables created in the global scope are accessible everywhere in a PowerShell process.</span></span>
- <span data-ttu-id="5ba3a-169">本機。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-169">Local.</span></span>
<span data-ttu-id="5ba3a-170">區域範圍是指目前的範圍，這可以是任何範圍（視內容而定）。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-170">The local scope refers to the current scope, this can be any scope depending on the context.</span></span>
- <span data-ttu-id="5ba3a-171">指令碼：</span><span class="sxs-lookup"><span data-stu-id="5ba3a-171">Script.</span></span>
<span data-ttu-id="5ba3a-172">在腳本範圍中建立的變數只能在其建立所在的腳本檔案或模組中進行存取。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-172">Variables created in the script scope are accessible only within the script file or module they are created in.</span></span>
- <span data-ttu-id="5ba3a-173">私人。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-173">Private.</span></span>
<span data-ttu-id="5ba3a-174">在私用範圍中建立的變數無法在其存在的範圍之外存取。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-174">Variables created in the private scope cannot be accessed outside the scope they exist in.</span></span>
<span data-ttu-id="5ba3a-175">您可以使用私用範圍，在其他範圍中建立具有相同名稱的專案私用版本。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-175">You can use private scope to create a private version of an item with the same name in another scope.</span></span>
- <span data-ttu-id="5ba3a-176">相對於目前範圍的數位 (0 至範圍數目，0為目前範圍，1為其父系，2是父範圍的父系，依此類推) 。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-176">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope, 1 is its parent, 2 the parent of the parent scope, and so on).</span></span>
<span data-ttu-id="5ba3a-177">無法使用負數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-177">Negative numbers cannot be used.</span></span>

<span data-ttu-id="5ba3a-178">當未指定 scope 參數時，Local 是預設範圍。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-178">Local is the default scope when the scope parameter is not specified.</span></span>

<span data-ttu-id="5ba3a-179">如需詳細資訊，請參閱 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-179">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="5ba3a-180">-Value</span><span class="sxs-lookup"><span data-stu-id="5ba3a-180">-Value</span></span>
<span data-ttu-id="5ba3a-181">指定變數的初始值。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-181">Specifies the initial value of the variable.</span></span>

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

### <span data-ttu-id="5ba3a-182">-Visibility</span><span class="sxs-lookup"><span data-stu-id="5ba3a-182">-Visibility</span></span>
<span data-ttu-id="5ba3a-183">決定是否可在變數建立所在的工作階段之外看見變數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-183">Determines whether the variable is visible outside of the session in which it was created.</span></span>
<span data-ttu-id="5ba3a-184">此參數是針對將傳遞給其他使用者的指令碼和命令中使用所設計。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-184">This parameter is designed for  use in scripts and commands that will be delivered to other users.</span></span>
<span data-ttu-id="5ba3a-185">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="5ba3a-185">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5ba3a-186">公用。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-186">Public.</span></span>
<span data-ttu-id="5ba3a-187">可看見變數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-187">The variable is visible.</span></span>
<span data-ttu-id="5ba3a-188">(Public 為預設值)。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-188">(Public is the default.)</span></span>
- <span data-ttu-id="5ba3a-189">私人。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-189">Private.</span></span>
<span data-ttu-id="5ba3a-190">看不到變數。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-190">The variable is not visible.</span></span>

<span data-ttu-id="5ba3a-191">當變數為私用變數時，它不會顯示在變數清單中 (例如由 Get-Variable 傳回的清單) 或顯示在 Variable: 磁碟機的顯示畫面中。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-191">When a variable is private, it does not appear in lists of variables, such as those returned by Get-Variable, or in displays of the Variable: drive.</span></span>
<span data-ttu-id="5ba3a-192">讀取或變更私用變數值的命令會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-192">Commands to read or change the value of a private variable return an error.</span></span>
<span data-ttu-id="5ba3a-193">但是，如果命令是寫入在定義變數的工作階段中，使用者就可以執行使用私用變數的命令。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-193">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5ba3a-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5ba3a-194">-Confirm</span></span>
<span data-ttu-id="5ba3a-195">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-195">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5ba3a-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5ba3a-196">-WhatIf</span></span>
<span data-ttu-id="5ba3a-197">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-197">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5ba3a-198">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-198">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5ba3a-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5ba3a-199">CommonParameters</span></span>
<span data-ttu-id="5ba3a-200">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5ba3a-201">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5ba3a-202">輸入</span><span class="sxs-lookup"><span data-stu-id="5ba3a-202">INPUTS</span></span>

### <span data-ttu-id="5ba3a-203">System.Object</span><span class="sxs-lookup"><span data-stu-id="5ba3a-203">System.Object</span></span>
<span data-ttu-id="5ba3a-204">您可以使用管線將值傳送至 **New-Variable** 。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-204">You can pipe a value to **New-Variable** .</span></span>

## <span data-ttu-id="5ba3a-205">輸出</span><span class="sxs-lookup"><span data-stu-id="5ba3a-205">OUTPUTS</span></span>

### <span data-ttu-id="5ba3a-206">無或 System.Management.Automation.PSVariable</span><span class="sxs-lookup"><span data-stu-id="5ba3a-206">None or System.Management.Automation.PSVariable</span></span>
<span data-ttu-id="5ba3a-207">使用 *PassThru* 參數時， **New-Variable** 會產生代表新變數的 **System.Management.Automation.PSVariable** 物件。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-207">When you use the *PassThru* parameter, **New-Variable** generates a **System.Management.Automation.PSVariable** object representing the new variable.</span></span>
<span data-ttu-id="5ba3a-208">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="5ba3a-208">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5ba3a-209">注意</span><span class="sxs-lookup"><span data-stu-id="5ba3a-209">NOTES</span></span>

## <span data-ttu-id="5ba3a-210">相關連結</span><span class="sxs-lookup"><span data-stu-id="5ba3a-210">RELATED LINKS</span></span>

[<span data-ttu-id="5ba3a-211">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="5ba3a-211">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="5ba3a-212">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="5ba3a-212">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="5ba3a-213">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="5ba3a-213">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="5ba3a-214">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="5ba3a-214">Set-Variable</span></span>](Set-Variable.md)
