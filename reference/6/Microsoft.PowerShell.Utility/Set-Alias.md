---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 2/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Alias
ms.openlocfilehash: 791b500660ed536eb1bd7ba4d6f37e8211078a0c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204427"
---
# <span data-ttu-id="68d60-103">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="68d60-103">Set-Alias</span></span>

## <span data-ttu-id="68d60-104">概要</span><span class="sxs-lookup"><span data-stu-id="68d60-104">SYNOPSIS</span></span>
<span data-ttu-id="68d60-105">在目前的 PowerShell 會話中，建立或變更 Cmdlet 或其他命令的別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-105">Creates or changes an alias for a cmdlet or other command in the current PowerShell session.</span></span>

## <span data-ttu-id="68d60-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="68d60-106">SYNTAX</span></span>

### <span data-ttu-id="68d60-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="68d60-107">Default (Default)</span></span>

```
Set-Alias [-Name] <string> [-Value] <string> [-Description <string>] [-Option <ScopedItemOptions>]
 [-PassThru] [-Scope <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="68d60-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="68d60-108">DESCRIPTION</span></span>

<span data-ttu-id="68d60-109">此 `Set-Alias` Cmdlet 會建立或變更 Cmdlet 或命令的別名，例如函式、腳本、檔案或其他可執行檔。</span><span class="sxs-lookup"><span data-stu-id="68d60-109">The `Set-Alias` cmdlet creates or changes an alias for a cmdlet or a command, such as a function, script, file, or other executable.</span></span> <span data-ttu-id="68d60-110">別名是參考 Cmdlet 或命令的替代名稱。</span><span class="sxs-lookup"><span data-stu-id="68d60-110">An alias is an alternate name that refers to a cmdlet or command.</span></span>
<span data-ttu-id="68d60-111">例如， `sal` 是 Cmdlet 的別名 `Set-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-111">For example, `sal` is the alias for the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="68d60-112">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="68d60-112">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="68d60-113">Cmdlet 可以有多個別名，但別名只能與一個 Cmdlet 相關聯。</span><span class="sxs-lookup"><span data-stu-id="68d60-113">A cmdlet can have multiple aliases, but an alias can only be associated with one cmdlet.</span></span> <span data-ttu-id="68d60-114">您可以使用 `Set-Alias` 將現有的別名重新指派給另一個 Cmdlet，或變更別名的屬性，例如描述。</span><span class="sxs-lookup"><span data-stu-id="68d60-114">You can use `Set-Alias` to reassign an existing alias to another cmdlet, or change an alias's properties, such as the description.</span></span>

<span data-ttu-id="68d60-115">所建立或變更的別名 `Set-Alias` 不是永久性的，而且只能在目前的 PowerShell 會話期間使用。</span><span class="sxs-lookup"><span data-stu-id="68d60-115">An alias that is created or changed by `Set-Alias` is not permanent and is only available during the current PowerShell session.</span></span> <span data-ttu-id="68d60-116">當 PowerShell 會話關閉時，就會移除別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-116">When the PowerShell session is closed, the alias is removed.</span></span>

## <span data-ttu-id="68d60-117">範例</span><span class="sxs-lookup"><span data-stu-id="68d60-117">EXAMPLES</span></span>

### <span data-ttu-id="68d60-118">範例 1︰建立 Cmdlet 的別名</span><span class="sxs-lookup"><span data-stu-id="68d60-118">Example 1: Create an alias for a cmdlet</span></span>

<span data-ttu-id="68d60-119">此命令會在目前的 PowerShell 會話中建立 Cmdlet 的別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-119">This command creates an alias to a cmdlet in the current PowerShell session.</span></span>

```
PS> Set-Alias -Name list -Value Get-ChildItem

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem
```

<span data-ttu-id="68d60-120">`Set-Alias`Cmdlet 會在目前的 PowerShell 會話中建立別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-120">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="68d60-121">**Name** 參數會指定別名的名稱 `list` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-121">The **Name** parameter specifies the alias's name, `list`.</span></span> <span data-ttu-id="68d60-122">**Value** 參數會指定別名執行的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68d60-122">The **Value** parameter specifies the cmdlet that the alias runs.</span></span>

<span data-ttu-id="68d60-123">若要執行別名，請 `list` 在 PowerShell 命令列上輸入。</span><span class="sxs-lookup"><span data-stu-id="68d60-123">To run the alias, type `list` on the PowerShell command line.</span></span>

### <span data-ttu-id="68d60-124">範例2：將現有的別名重新指派給不同的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="68d60-124">Example 2: Reassign an existing alias to a different cmdlet</span></span>

<span data-ttu-id="68d60-125">此命令會重新指派現有的別名，以執行不同的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68d60-125">This command reassigns an existing alias to run a different cmdlet.</span></span>

```
PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem

PS> Set-Alias -Name list -Value Get-Location

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-Location
```

<span data-ttu-id="68d60-126">此 `Get-Alias` Cmdlet 會使用 **Name** 參數來顯示 `list` 別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-126">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="68d60-127">`list`別名與 Cmdlet 相關聯 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-127">The `list` alias is associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="68d60-128">當 `list` 別名執行時，會顯示目前目錄中的專案。</span><span class="sxs-lookup"><span data-stu-id="68d60-128">When the `list` alias is run, the items in the current directory are displayed.</span></span>

<span data-ttu-id="68d60-129">此 `Set-Alias` Cmdlet 會使用 **Name** 參數來指定 `list` 別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-129">The `Set-Alias` cmdlet uses the **Name** parameter to specify the `list` alias.</span></span> <span data-ttu-id="68d60-130">**Value** 參數會將別名與 Cmdlet 產生關聯 `Get-Location` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-130">The **Value** parameter associates the alias to the `Get-Location` cmdlet.</span></span>

<span data-ttu-id="68d60-131">此 `Get-Alias` Cmdlet 會使用 **Name** 參數來顯示 `list` 別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-131">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="68d60-132">`list`別名與 Cmdlet 相關聯 `Get-Location` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-132">The `list` alias is associated with the `Get-Location` cmdlet.</span></span> <span data-ttu-id="68d60-133">當 `list` 別名執行時，會顯示目前的目錄的位置。</span><span class="sxs-lookup"><span data-stu-id="68d60-133">When the `list` alias is run, the current directory's location is displayed.</span></span>

### <span data-ttu-id="68d60-134">範例3：建立和變更唯讀別名</span><span class="sxs-lookup"><span data-stu-id="68d60-134">Example 3: Create and change a read-only alias</span></span>

<span data-ttu-id="68d60-135">此命令會建立唯讀別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-135">This command creates a read-only alias.</span></span> <span data-ttu-id="68d60-136">唯讀選項可防止非預期的別名變更。</span><span class="sxs-lookup"><span data-stu-id="68d60-136">The read-only option prevents unintended changes to an alias.</span></span> <span data-ttu-id="68d60-137">若要變更或刪除唯讀別名，請使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="68d60-137">To change or delete a read-only alias, use the **Force** parameter.</span></span>

```
PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         :
Name                : loc
CommandType         : Alias

PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -Description 'Displays the current directory' -Force -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         : Displays the current directory
Name                : loc
CommandType         : Alias
```

<span data-ttu-id="68d60-138">`Set-Alias`Cmdlet 會在目前的 PowerShell 會話中建立別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-138">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="68d60-139">**Name** 參數會指定別名的名稱 `loc` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-139">The **Name** parameter specifies the alias's name, `loc`.</span></span> <span data-ttu-id="68d60-140">**Value** 參數 `Get-Location` 會指定別名執行的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68d60-140">The **Value** parameter specifies the `Get-Location` cmdlet that the alias runs.</span></span> <span data-ttu-id="68d60-141">**Option** 參數會指定 **ReadOnly** 值。</span><span class="sxs-lookup"><span data-stu-id="68d60-141">The **Option** parameter specifies the **ReadOnly** value.</span></span> <span data-ttu-id="68d60-142">**PassThru** 參數代表別名物件，並將物件沿著管線向下傳送至 `Format-List` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68d60-142">The **PassThru** parameter represents the alias object and sends the object down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="68d60-143">`Format-List` 使用 **Property** 參數搭配星號 (`*`) ，以便顯示所有屬性。</span><span class="sxs-lookup"><span data-stu-id="68d60-143">`Format-List` uses the **Property** parameter with an asterisk (`*`) so that all of the properties are displayed.</span></span> <span data-ttu-id="68d60-144">範例輸出會顯示這些屬性的部分清單。</span><span class="sxs-lookup"><span data-stu-id="68d60-144">The example output shows a partial list of those properties.</span></span>

<span data-ttu-id="68d60-145">`loc`別名的變更會加上兩個參數。</span><span class="sxs-lookup"><span data-stu-id="68d60-145">The `loc` alias is changed with the addition of two parameters.</span></span> <span data-ttu-id="68d60-146">**描述** 會新增文字來說明別名的用途。</span><span class="sxs-lookup"><span data-stu-id="68d60-146">**Description** adds text to explain the alias's purpose.</span></span> <span data-ttu-id="68d60-147">需要 **Force** 參數，因為 `loc` 別名為唯讀。</span><span class="sxs-lookup"><span data-stu-id="68d60-147">The **Force** parameter is needed because the `loc` alias is read-only.</span></span> <span data-ttu-id="68d60-148">如果未使用 **Force** 參數，變更就會失敗。</span><span class="sxs-lookup"><span data-stu-id="68d60-148">If the **Force** parameter is not used, the change fails.</span></span>

### <span data-ttu-id="68d60-149">範例4：建立可執行檔的別名</span><span class="sxs-lookup"><span data-stu-id="68d60-149">Example 4: Create an alias to an executable file</span></span>

<span data-ttu-id="68d60-150">這個範例會建立本機電腦上可執行檔的別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-150">This example creates an alias to an executable file on the local computer.</span></span>

```
PS> Set-Alias -Name np -Value C:\Windows\notepad.exe

PS> Get-Alias -Name np

CommandType     Name
-----------     ----
Alias           np -> notepad.exe
```

<span data-ttu-id="68d60-151">`Set-Alias`Cmdlet 會在目前的 PowerShell 會話中建立別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-151">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="68d60-152">**Name** 參數會指定別名的名稱 `np` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-152">The **Name** parameter specifies the alias's name, `np`.</span></span> <span data-ttu-id="68d60-153">**Value** 參數會指定 **C:\Windows\notepad.exe** 的路徑和應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="68d60-153">The **Value** parameter specifies the path and application name **C:\Windows\notepad.exe** .</span></span> <span data-ttu-id="68d60-154">此 `Get-Alias` Cmdlet 會使用 **Name** 參數來顯示 `np` 別名與 **notepad.exe** 相關聯。</span><span class="sxs-lookup"><span data-stu-id="68d60-154">The `Get-Alias` cmdlet uses the **Name** parameter to show that the `np` alias is associated with **notepad.exe** .</span></span>

<span data-ttu-id="68d60-155">若要執行別名，請 `np` 在 PowerShell 命令列上輸入，以開啟 **notepad.exe** 。</span><span class="sxs-lookup"><span data-stu-id="68d60-155">To run the alias, type `np` on the PowerShell command line to open **notepad.exe** .</span></span>

### <span data-ttu-id="68d60-156">範例5：使用參數建立命令的別名</span><span class="sxs-lookup"><span data-stu-id="68d60-156">Example 5: Create an alias for a command with parameters</span></span>

<span data-ttu-id="68d60-157">此範例示範如何使用參數將別名指派給命令。</span><span class="sxs-lookup"><span data-stu-id="68d60-157">This example shows how to assign an alias to a command with parameters.</span></span>

<span data-ttu-id="68d60-158">您可以為 Cmdlet 建立別名，例如 `Set-Location` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-158">You can create an alias for a cmdlet, such as `Set-Location`.</span></span> <span data-ttu-id="68d60-159">您無法為具有參數和值的命令建立別名，例如 `Set-Location -Path C:\Windows\System32` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-159">You cannot create an alias for a command with parameters and values, such as `Set-Location -Path C:\Windows\System32`.</span></span> <span data-ttu-id="68d60-160">若要為命令建立別名，請建立一個包含該命令的函式，然後建立該函式的別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-160">To create an alias for a command, create a function that includes the command, and then create an alias to the function.</span></span> <span data-ttu-id="68d60-161">如需詳細資訊，請參閱 [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)。</span><span class="sxs-lookup"><span data-stu-id="68d60-161">For more information, see [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md).</span></span>

```
PS> Function CD32 {Set-Location -Path C:\Windows\System32}

PS> Set-Alias -Name Go -Value CD32
```

<span data-ttu-id="68d60-162">即會建立名為的函式 `CD32` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-162">A function named `CD32` is created.</span></span> <span data-ttu-id="68d60-163">此函式會使用 `Set-Location` Cmdlet 搭配 **Path** 參數來指定目錄 **C:\Windows\System32** 。</span><span class="sxs-lookup"><span data-stu-id="68d60-163">The function uses the `Set-Location` cmdlet with the **Path** parameter to specify the directory, **C:\Windows\System32** .</span></span>

<span data-ttu-id="68d60-164">`Set-Alias`Cmdlet 會在目前的 PowerShell 會話中建立函式的別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-164">The `Set-Alias` cmdlet creates an alias to the function in the current PowerShell session.</span></span> <span data-ttu-id="68d60-165">**Name** 參數會指定別名的名稱 `Go` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-165">The **Name** parameter specifies the alias's name, `Go`.</span></span> <span data-ttu-id="68d60-166">**Value** 參數會指定函數的名稱 `CD32` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-166">The **Value** parameter specifies the function's name, `CD32`.</span></span>

<span data-ttu-id="68d60-167">若要執行別名，請 `Go` 在 PowerShell 命令列上輸入。</span><span class="sxs-lookup"><span data-stu-id="68d60-167">To run the alias, type `Go` on the PowerShell command line.</span></span> <span data-ttu-id="68d60-168">`CD32`函數會執行並變更目錄 **C:\Windows\System32** 。</span><span class="sxs-lookup"><span data-stu-id="68d60-168">The `CD32` function runs and changes to the directory **C:\Windows\System32** .</span></span>

## <span data-ttu-id="68d60-169">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="68d60-169">PARAMETERS</span></span>

### <span data-ttu-id="68d60-170">-Description</span><span class="sxs-lookup"><span data-stu-id="68d60-170">-Description</span></span>

<span data-ttu-id="68d60-171">指定別名的描述。</span><span class="sxs-lookup"><span data-stu-id="68d60-171">Specifies a description of the alias.</span></span> <span data-ttu-id="68d60-172">您可以輸入任何字串。</span><span class="sxs-lookup"><span data-stu-id="68d60-172">You can type any string.</span></span> <span data-ttu-id="68d60-173">如果描述包含空格，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="68d60-173">If the description includes spaces, enclose it single quotation marks.</span></span>

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

### <span data-ttu-id="68d60-174">-Force</span><span class="sxs-lookup"><span data-stu-id="68d60-174">-Force</span></span>

<span data-ttu-id="68d60-175">使用 **Force** 參數來變更或刪除將 **Option** 參數設定為 **ReadOnly** 的別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-175">Use the **Force** parameter to change or delete an alias that has the **Option** parameter set to **ReadOnly** .</span></span>

<span data-ttu-id="68d60-176">**Force** 參數無法變更或刪除將 **Option** 參數設為 **常數** 的別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-176">The **Force** parameter cannot change or delete an alias with the **Option** parameter set to **Constant** .</span></span>

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

### <span data-ttu-id="68d60-177">-Name</span><span class="sxs-lookup"><span data-stu-id="68d60-177">-Name</span></span>

<span data-ttu-id="68d60-178">指定新別名的名稱。</span><span class="sxs-lookup"><span data-stu-id="68d60-178">Specifies the name of a new alias.</span></span> <span data-ttu-id="68d60-179">別名名稱可包含英數位元和連字號。</span><span class="sxs-lookup"><span data-stu-id="68d60-179">An alias name can contain alphanumeric characters and hyphens.</span></span> <span data-ttu-id="68d60-180">別名名稱不可以是數值，例如123。</span><span class="sxs-lookup"><span data-stu-id="68d60-180">Alias names cannot be numeric, such as 123.</span></span>

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

### <span data-ttu-id="68d60-181">-Option</span><span class="sxs-lookup"><span data-stu-id="68d60-181">-Option</span></span>

<span data-ttu-id="68d60-182">設定別名的 **Option** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="68d60-182">Sets the **Option** property value of the alias.</span></span> <span data-ttu-id="68d60-183">**ReadOnly** 和 **常數** 等值會保護別名免于非預期的變更。</span><span class="sxs-lookup"><span data-stu-id="68d60-183">Values such as **ReadOnly** and **Constant** protect an alias from unintended changes.</span></span> <span data-ttu-id="68d60-184">若要查看會話中所有別名的 **Option** 屬性，請輸入 `Get-Alias | Format-Table -Property Name, Options -Autosize` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-184">To see the **Option** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -Autosize`.</span></span>

<span data-ttu-id="68d60-185">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="68d60-185">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="68d60-186">**AllScope** 別名會複製到所建立的任何新範圍。</span><span class="sxs-lookup"><span data-stu-id="68d60-186">**AllScope** The alias is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="68d60-187">**常數** 無法變更或刪除。</span><span class="sxs-lookup"><span data-stu-id="68d60-187">**Constant** Cannot be changed or deleted.</span></span>
- <span data-ttu-id="68d60-188">**無** 不設定任何選項，而且是預設值。</span><span class="sxs-lookup"><span data-stu-id="68d60-188">**None** Sets no options and is the default.</span></span>
- <span data-ttu-id="68d60-189">**私** 用別名只能在目前的範圍中使用。</span><span class="sxs-lookup"><span data-stu-id="68d60-189">**Private** The alias is available only in the current scope.</span></span>
- <span data-ttu-id="68d60-190">**ReadOnly** 除非使用 **Force** 參數，否則無法變更或刪除。</span><span class="sxs-lookup"><span data-stu-id="68d60-190">**ReadOnly** Cannot be changed or deleted unless the **Force** parameter is used.</span></span>
- <span data-ttu-id="68d60-191">**未指定**</span><span class="sxs-lookup"><span data-stu-id="68d60-191">**Unspecified**</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: AllScope, Constant, None, Private, ReadOnly, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="68d60-192">-PassThru</span><span class="sxs-lookup"><span data-stu-id="68d60-192">-PassThru</span></span>

<span data-ttu-id="68d60-193">傳回代表別名的物件。</span><span class="sxs-lookup"><span data-stu-id="68d60-193">Returns an object that represents the alias.</span></span> <span data-ttu-id="68d60-194">使用格式 Cmdlet （例如） `Format-List` 來顯示物件。</span><span class="sxs-lookup"><span data-stu-id="68d60-194">Use a format cmdlet such as `Format-List` to display the object.</span></span> <span data-ttu-id="68d60-195">依預設，不 `Set-Alias` 會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="68d60-195">By default, `Set-Alias` does not generate any output.</span></span>

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

### <span data-ttu-id="68d60-196">-Scope</span><span class="sxs-lookup"><span data-stu-id="68d60-196">-Scope</span></span>

<span data-ttu-id="68d60-197">指定別名的有效範圍。</span><span class="sxs-lookup"><span data-stu-id="68d60-197">Specifies the scope in which this alias is valid.</span></span> <span data-ttu-id="68d60-198">預設值為 [ **本機** ]。</span><span class="sxs-lookup"><span data-stu-id="68d60-198">The default value is **Local** .</span></span> <span data-ttu-id="68d60-199">如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="68d60-199">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

<span data-ttu-id="68d60-200">可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="68d60-200">The acceptable values are as follows:</span></span>

- <span data-ttu-id="68d60-201">全球</span><span class="sxs-lookup"><span data-stu-id="68d60-201">Global</span></span>
- <span data-ttu-id="68d60-202">本機</span><span class="sxs-lookup"><span data-stu-id="68d60-202">Local</span></span>
- <span data-ttu-id="68d60-203">私人</span><span class="sxs-lookup"><span data-stu-id="68d60-203">Private</span></span>
- <span data-ttu-id="68d60-204">編號的範圍</span><span class="sxs-lookup"><span data-stu-id="68d60-204">Numbered scopes</span></span>
- <span data-ttu-id="68d60-205">指令碼</span><span class="sxs-lookup"><span data-stu-id="68d60-205">Script</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Global, Local, Private, Numbered scopes, Script

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="68d60-206">-Value</span><span class="sxs-lookup"><span data-stu-id="68d60-206">-Value</span></span>

<span data-ttu-id="68d60-207">指定別名所執行 Cmdlet 或命令的名稱。</span><span class="sxs-lookup"><span data-stu-id="68d60-207">Specifies the name of the cmdlet or command that the alias runs.</span></span> <span data-ttu-id="68d60-208">**值** 參數是別名的 **定義** 屬性。</span><span class="sxs-lookup"><span data-stu-id="68d60-208">The **Value** parameter is the alias's **Definition** property.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68d60-209">-Confirm</span><span class="sxs-lookup"><span data-stu-id="68d60-209">-Confirm</span></span>

<span data-ttu-id="68d60-210">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="68d60-210">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="68d60-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="68d60-211">-WhatIf</span></span>

<span data-ttu-id="68d60-212">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="68d60-212">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="68d60-213">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="68d60-213">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="68d60-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="68d60-214">CommonParameters</span></span>

<span data-ttu-id="68d60-215">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="68d60-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="68d60-216">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="68d60-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="68d60-217">輸入</span><span class="sxs-lookup"><span data-stu-id="68d60-217">INPUTS</span></span>

### <span data-ttu-id="68d60-218">無</span><span class="sxs-lookup"><span data-stu-id="68d60-218">None</span></span>

<span data-ttu-id="68d60-219">`Set-Alias` 不接受來自管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="68d60-219">`Set-Alias` does not accept input from the pipeline.</span></span>

## <span data-ttu-id="68d60-220">輸出</span><span class="sxs-lookup"><span data-stu-id="68d60-220">OUTPUTS</span></span>

### <span data-ttu-id="68d60-221">無或 System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="68d60-221">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="68d60-222">當您使用 **PassThru** 參數時，會 `Set-Alias` 產生代表別名的 **system.management.automation.aliasinfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="68d60-222">When you use the **PassThru** parameter, `Set-Alias` generates a **System.Management.Automation.AliasInfo** object representing the alias.</span></span> <span data-ttu-id="68d60-223">否則，不 `Set-Alias` 會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="68d60-223">Otherwise, `Set-Alias` does not generate any output.</span></span>

## <span data-ttu-id="68d60-224">注意</span><span class="sxs-lookup"><span data-stu-id="68d60-224">NOTES</span></span>

<span data-ttu-id="68d60-225">PowerShell 包含可在每個 PowerShell 會話中使用的內建別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-225">PowerShell includes built-in aliases that are available in each PowerShell session.</span></span> <span data-ttu-id="68d60-226">此 `Get-Alias` Cmdlet 會顯示 PowerShell 會話中可用的別名。</span><span class="sxs-lookup"><span data-stu-id="68d60-226">The `Get-Alias` cmdlet displays the aliases available in a PowerShell session.</span></span>

<span data-ttu-id="68d60-227">若要建立別名，請使用 Cmdlet `Set-Alias` 或 `New-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-227">To create an alias, use the cmdlets `Set-Alias` or `New-Alias`.</span></span> <span data-ttu-id="68d60-228">在 PowerShell 6 中，若要刪除別名，請使用 `Remove-Alias` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68d60-228">In PowerShell 6, to delete an alias, use the `Remove-Alias` cmdlet.</span></span> <span data-ttu-id="68d60-229">`Remove-Item` 是針對回溯相容性所接受，例如，針對使用舊版 PowerShell 所建立的腳本。</span><span class="sxs-lookup"><span data-stu-id="68d60-229">`Remove-Item` is accepted for backwards compatibility such as for scripts created with prior versions of PowerShell.</span></span> <span data-ttu-id="68d60-230">使用像這樣的命令 `Remove-Item -Path Alias:aliasname` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-230">Use a command such as `Remove-Item -Path Alias:aliasname`.</span></span>

<span data-ttu-id="68d60-231">若要建立可在每個 PowerShell 會話中使用的別名，請將它新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="68d60-231">To create an alias that is available in each PowerShell session, add it to your PowerShell profile.</span></span>
<span data-ttu-id="68d60-232">如需詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="68d60-232">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="68d60-233">您可以執行匯出和匯入，將別名儲存並重複使用於另一個 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="68d60-233">An alias can be saved and reused in another PowerShell session by doing an export and import.</span></span> <span data-ttu-id="68d60-234">若要將別名儲存至檔案，請使用 `Export-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-234">To save an alias to a file, use `Export-Alias`.</span></span> <span data-ttu-id="68d60-235">若要將儲存的別名新增至新的 PowerShell 會話，請使用 `Import-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="68d60-235">To add a saved alias to a new PowerShell session, use `Import-Alias`.</span></span>

## <span data-ttu-id="68d60-236">相關連結</span><span class="sxs-lookup"><span data-stu-id="68d60-236">RELATED LINKS</span></span>

[<span data-ttu-id="68d60-237">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="68d60-237">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="68d60-238">about_Functions</span><span class="sxs-lookup"><span data-stu-id="68d60-238">about_Functions</span></span>](../Microsoft.PowerShell.Core/about/about_Functions.md)

[<span data-ttu-id="68d60-239">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="68d60-239">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_Profiles.md)

[<span data-ttu-id="68d60-240">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="68d60-240">about_Scopes</span></span>](../Microsoft.PowerShell.Core/About/about_Scopes.md)

[<span data-ttu-id="68d60-241">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="68d60-241">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="68d60-242">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="68d60-242">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="68d60-243">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="68d60-243">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="68d60-244">New-Alias</span><span class="sxs-lookup"><span data-stu-id="68d60-244">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="68d60-245">Remove-Alias</span><span class="sxs-lookup"><span data-stu-id="68d60-245">Remove-Alias</span></span>](Remove-Alias.md)

[<span data-ttu-id="68d60-246">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="68d60-246">Remove-Item</span></span>](../Microsoft.PowerShell.Management/Remove-Item.md)
