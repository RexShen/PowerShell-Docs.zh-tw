---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/push-location?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Push-Location
ms.openlocfilehash: 91ee85507d8ad0f128025af3d549d461310a415d
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "93205863"
---
# <span data-ttu-id="8747c-103">Push-Location</span><span class="sxs-lookup"><span data-stu-id="8747c-103">Push-Location</span></span>

## <span data-ttu-id="8747c-104">概要</span><span class="sxs-lookup"><span data-stu-id="8747c-104">SYNOPSIS</span></span>
<span data-ttu-id="8747c-105">在位置堆疊頂端新增目前的位置。</span><span class="sxs-lookup"><span data-stu-id="8747c-105">Adds the current location to the top of a location stack.</span></span>

## <span data-ttu-id="8747c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8747c-106">SYNTAX</span></span>

### <span data-ttu-id="8747c-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="8747c-107">Path (Default)</span></span>

```
Push-Location [[-Path] <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

### <span data-ttu-id="8747c-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8747c-108">LiteralPath</span></span>

```
Push-Location [-LiteralPath <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="8747c-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8747c-109">DESCRIPTION</span></span>

<span data-ttu-id="8747c-110">`Push-Location`Cmdlet 會將目前位置 )  ( 「推送」新增至位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="8747c-110">The `Push-Location` cmdlet adds ("pushes") the current location onto a location stack.</span></span> <span data-ttu-id="8747c-111">如果您指定路徑，則會 `Push-Location` 將目前的位置推入至位置堆疊，然後將目前的位置變更為路徑所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="8747c-111">If you specify a path, `Push-Location` pushes the current location onto a location stack and then changes the current location to the location specified by the path.</span></span> <span data-ttu-id="8747c-112">您可以使用 `Pop-Location` Cmdlet 從位置堆疊取得位置。</span><span class="sxs-lookup"><span data-stu-id="8747c-112">You can use the `Pop-Location` cmdlet to get locations from the location stack.</span></span>

<span data-ttu-id="8747c-113">根據預設，此 `Push-Location` Cmdlet 會將目前的位置推送到目前的位置堆疊，但您可以使用 **StackName** 參數來指定替代的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="8747c-113">By default, the `Push-Location` cmdlet pushes the current location onto the current location stack, but you can use the **StackName** parameter to specify an alternate location stack.</span></span> <span data-ttu-id="8747c-114">如果堆疊不存在，則會 `Push-Location` 加以建立。</span><span class="sxs-lookup"><span data-stu-id="8747c-114">If the stack does not exist, `Push-Location` creates it.</span></span>

<span data-ttu-id="8747c-115">如需位置堆疊的詳細資訊，請參閱 [附注](#notes)。</span><span class="sxs-lookup"><span data-stu-id="8747c-115">For more information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="8747c-116">範例</span><span class="sxs-lookup"><span data-stu-id="8747c-116">EXAMPLES</span></span>

### <span data-ttu-id="8747c-117">範例 1</span><span class="sxs-lookup"><span data-stu-id="8747c-117">Example 1</span></span>

<span data-ttu-id="8747c-118">這個範例會將目前的位置推入至預設位置堆疊，然後將位置變更為 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="8747c-118">This example pushes the current location onto the default location stack and then changes the location to `C:\Windows`.</span></span>

```
PS C:\> Push-Location C:\Windows
```

### <span data-ttu-id="8747c-119">範例 2</span><span class="sxs-lookup"><span data-stu-id="8747c-119">Example 2</span></span>

<span data-ttu-id="8747c-120">此範例會將目前的位置推送至 Regfunction 上方堆疊，並將目前的位置變更為 `HKLM:\Software\Policies` 位置。</span><span class="sxs-lookup"><span data-stu-id="8747c-120">This example pushes the current location onto the RegFunction stack and changes the current location to the `HKLM:\Software\Policies` location.</span></span>

```
PS C:\> Push-Location HKLM:\Software\Policies -StackName RegFunction
```

<span data-ttu-id="8747c-121">您可以使用任何 PowerShell 磁片磁碟機中的 Location Cmdlet (New-psdrive) 。</span><span class="sxs-lookup"><span data-stu-id="8747c-121">You can use the Location cmdlets in any PowerShell drive (PSDrive).</span></span>

### <span data-ttu-id="8747c-122">範例 3</span><span class="sxs-lookup"><span data-stu-id="8747c-122">Example 3</span></span>

<span data-ttu-id="8747c-123">此命令將目前位置推入至預設堆疊上方。</span><span class="sxs-lookup"><span data-stu-id="8747c-123">This command pushes the current location onto the default stack.</span></span> <span data-ttu-id="8747c-124">它不會變更位置。</span><span class="sxs-lookup"><span data-stu-id="8747c-124">It does not change the location.</span></span>

```
PS C:\> Push-Location
```

### <span data-ttu-id="8747c-125">範例 4-建立和使用命名堆疊</span><span class="sxs-lookup"><span data-stu-id="8747c-125">Example 4 - Create and use a named stack</span></span>

<span data-ttu-id="8747c-126">這些命令顯示如何建立和使用命名位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="8747c-126">These commands show how to create and use a named location stack.</span></span>

```
PS C:\> Push-Location ~ -StackName Stack2
PS C:\Users\User01> Pop-Location -StackName Stack2
PS C:\>
```

<span data-ttu-id="8747c-127">第一個命令會將目前的位置推送至名為 Stack2 的新堆疊，然後將目前的位置變更為 home 目錄，在命令中以波狀符號符號 (`~`) （在檔案系統提供者磁片磁碟機上使用時相當於 `$HOME` 和） `$env:USERPROFILE` 。</span><span class="sxs-lookup"><span data-stu-id="8747c-127">The first command pushes the current location onto a new stack named Stack2, and then changes the current location to the home directory, represented in the command by the tilde symbol (`~`), which when used on a FileSystem provider drives is equivalent to `$HOME` and `$env:USERPROFILE`.</span></span>

<span data-ttu-id="8747c-128">如果 Stack2 不存在於會話中，則會 `Push-Location` 加以建立。</span><span class="sxs-lookup"><span data-stu-id="8747c-128">If Stack2 does not already exist in the session, `Push-Location` creates it.</span></span> <span data-ttu-id="8747c-129">第二個命令會使用 `Pop-Location` Cmdlet 來 (`C:\` 從 Stack2 堆疊) 的原始位置。</span><span class="sxs-lookup"><span data-stu-id="8747c-129">The second command uses the `Pop-Location` cmdlet to pop the original location (`C:\`) from the Stack2 stack.</span></span> <span data-ttu-id="8747c-130">如果沒有 **StackName** 參數， `Pop-Location` 會從未命名的預設堆疊中取出位置。</span><span class="sxs-lookup"><span data-stu-id="8747c-130">Without the **StackName** parameter, `Pop-Location` would pop the location from the unnamed default stack.</span></span>

<span data-ttu-id="8747c-131">如需位置堆疊的詳細資訊，請參閱 [附注](#notes)。</span><span class="sxs-lookup"><span data-stu-id="8747c-131">For more information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="8747c-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8747c-132">PARAMETERS</span></span>

### <span data-ttu-id="8747c-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8747c-133">-LiteralPath</span></span>

<span data-ttu-id="8747c-134">指定新位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="8747c-134">Specifies the path to the new location.</span></span> <span data-ttu-id="8747c-135">與 **Path** 參數不同， **LiteralPath** 參數的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="8747c-135">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="8747c-136">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8747c-136">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="8747c-137">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="8747c-137">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="8747c-138">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="8747c-138">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8747c-139">-PassThru</span><span class="sxs-lookup"><span data-stu-id="8747c-139">-PassThru</span></span>

<span data-ttu-id="8747c-140">將代表位置的物件傳遞至管線。</span><span class="sxs-lookup"><span data-stu-id="8747c-140">Passes an object representing the location to the pipeline.</span></span> <span data-ttu-id="8747c-141">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="8747c-141">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="8747c-142">-Path</span><span class="sxs-lookup"><span data-stu-id="8747c-142">-Path</span></span>

<span data-ttu-id="8747c-143">變更您的位置為此路徑所指定的位置 (在將目前位置新增 (推入) 至堆疊頂端之後)。</span><span class="sxs-lookup"><span data-stu-id="8747c-143">Changes your location to the location specified by this path after it adds (pushes) the current location onto the top of the stack.</span></span> <span data-ttu-id="8747c-144">輸入其提供者支援此 Cmdlet 的任何位置路徑。</span><span class="sxs-lookup"><span data-stu-id="8747c-144">Enter a path to any location whose provider supports this cmdlet.</span></span> <span data-ttu-id="8747c-145">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8747c-145">Wildcards are permitted.</span></span> <span data-ttu-id="8747c-146">參數名稱為選擇性。</span><span class="sxs-lookup"><span data-stu-id="8747c-146">The parameter name is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="8747c-147">-StackName</span><span class="sxs-lookup"><span data-stu-id="8747c-147">-StackName</span></span>

<span data-ttu-id="8747c-148">指定要新增目前位置的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="8747c-148">Specifies the location stack to which the current location is added.</span></span> <span data-ttu-id="8747c-149">請輸入位置堆疊名稱。</span><span class="sxs-lookup"><span data-stu-id="8747c-149">Enter a location stack name.</span></span>
<span data-ttu-id="8747c-150">如果堆疊不存在，則會 `Push-Location` 加以建立。</span><span class="sxs-lookup"><span data-stu-id="8747c-150">If the stack does not exist, `Push-Location` creates it.</span></span>

<span data-ttu-id="8747c-151">如果沒有這個參數，則會 `Push-Location` 將位置新增至目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="8747c-151">Without this parameter, `Push-Location` adds the location to the current location stack.</span></span> <span data-ttu-id="8747c-152">根據預設，目前的位置堆疊是 PowerShell 所建立的未命名預設位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="8747c-152">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span>
<span data-ttu-id="8747c-153">若要將位置堆疊設為目前的位置堆疊，請使用 Cmdlet 的 **StackName** 參數 `Set-Location` 。</span><span class="sxs-lookup"><span data-stu-id="8747c-153">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="8747c-154">如需位置堆疊的詳細資訊，請參閱 [附注](#notes)。</span><span class="sxs-lookup"><span data-stu-id="8747c-154">For more information about location stacks, see the [Notes](#notes).</span></span>

> [!NOTE]
> <span data-ttu-id="8747c-155">`Push-Location` 無法將位置新增至未命名的預設堆疊，除非它是目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="8747c-155">`Push-Location` cannot add a location to the unnamed default stack unless it is the current location stack.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default stack
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8747c-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8747c-156">CommonParameters</span></span>

<span data-ttu-id="8747c-157">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8747c-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8747c-158">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8747c-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8747c-159">輸入</span><span class="sxs-lookup"><span data-stu-id="8747c-159">INPUTS</span></span>

### <span data-ttu-id="8747c-160">System.String</span><span class="sxs-lookup"><span data-stu-id="8747c-160">System.String</span></span>

<span data-ttu-id="8747c-161">您可以使用管線將包含路徑 (但不是常值路徑) 的字串傳送至 `Push-Location` 。</span><span class="sxs-lookup"><span data-stu-id="8747c-161">You can pipe a string that contains a path (but not a literal path) to `Push-Location`.</span></span>

## <span data-ttu-id="8747c-162">輸出</span><span class="sxs-lookup"><span data-stu-id="8747c-162">OUTPUTS</span></span>

### <span data-ttu-id="8747c-163">無或 System.Management.Automation.PathInfo</span><span class="sxs-lookup"><span data-stu-id="8747c-163">None or System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="8747c-164">當您使用 **PassThru** 參數時，會 `Push-Location` 產生代表位置的 **system.management.automation.pathinfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="8747c-164">When you use the **PassThru** parameter, `Push-Location` generates a **System.Management.Automation.PathInfo** object that represents the location.</span></span> <span data-ttu-id="8747c-165">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="8747c-165">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8747c-166">注意</span><span class="sxs-lookup"><span data-stu-id="8747c-166">NOTES</span></span>

<span data-ttu-id="8747c-167">PowerShell 支援每個進程有多個空間。</span><span class="sxs-lookup"><span data-stu-id="8747c-167">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="8747c-168">每個運行空間都有自己的 _目前的目錄_ 。</span><span class="sxs-lookup"><span data-stu-id="8747c-168">Each runspace has its own _current directory_ .</span></span>
<span data-ttu-id="8747c-169">這與不同 `[System.Environment]::CurrentDirectory` 。</span><span class="sxs-lookup"><span data-stu-id="8747c-169">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="8747c-170">呼叫 .NET Api 或執行原生應用程式而不提供明確的目錄路徑時，此行為可能會產生問題。</span><span class="sxs-lookup"><span data-stu-id="8747c-170">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="8747c-171">即使位置 Cmdlet 已設定整個進程的目錄，您也無法依賴它，因為另一個執行時間可能會隨時變更。</span><span class="sxs-lookup"><span data-stu-id="8747c-171">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="8747c-172">您應該使用 location Cmdlet 來執行以路徑為基礎的作業，並使用目前的運行時特定的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="8747c-172">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="8747c-173">堆疊是一個後進先出的清單，其中只有最近新增的專案可供存取。</span><span class="sxs-lookup"><span data-stu-id="8747c-173">A stack is a last-in, first-out list in which only the most recently added item is accessible.</span></span>
<span data-ttu-id="8747c-174">將項目新增到堆疊中時，順序與您使用它們的順序相同，然後抓取它們來使用時的順序則相反。</span><span class="sxs-lookup"><span data-stu-id="8747c-174">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="8747c-175">PowerShell 可讓您將提供者位置儲存在位置堆疊中。</span><span class="sxs-lookup"><span data-stu-id="8747c-175">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="8747c-176">PowerShell 會建立未命名的預設位置堆疊，而且您可以建立多個命名位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="8747c-176">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="8747c-177">如果您未指定堆疊名稱，PowerShell 會使用目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="8747c-177">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="8747c-178">根據預設，未命名的預設位置為目前的位置堆疊，但您可以使用 `Set-Location` Cmdlet 來變更目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="8747c-178">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="8747c-179">若要管理位置堆疊，請使用 PowerShell Location Cmdlet，如下所示。</span><span class="sxs-lookup"><span data-stu-id="8747c-179">To manage location stacks, use the PowerShell Location cmdlets, as follows.</span></span>

- <span data-ttu-id="8747c-180">若要將位置新增至位置堆疊，請使用 `Push-Location` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8747c-180">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="8747c-181">若要從位置堆疊取得位置，請使用 `Pop-Location` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8747c-181">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="8747c-182">若要顯示目前位置堆疊中的位置，請使用 Cmdlet 的 **stack** 參數 `Get-Location` 。</span><span class="sxs-lookup"><span data-stu-id="8747c-182">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="8747c-183">若要顯示命名位置堆疊中的位置，請使用 Cmdlet 的 **StackName** 參數 `Get-Location` 。</span><span class="sxs-lookup"><span data-stu-id="8747c-183">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="8747c-184">若要建立新的位置堆疊，請使用 Cmdlet 的 StackName 參數 `Push-Location` 。</span><span class="sxs-lookup"><span data-stu-id="8747c-184">To create a new location stack, use the StackName parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="8747c-185">如果您指定的堆疊不存在，就會 `Push-Location` 建立堆疊。</span><span class="sxs-lookup"><span data-stu-id="8747c-185">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="8747c-186">若要將位置堆疊設為目前的位置堆疊，請使用 Cmdlet 的 StackName 參數 `Set-Location` 。</span><span class="sxs-lookup"><span data-stu-id="8747c-186">To make a location stack the current location stack, use the StackName parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="8747c-187">未命名的預設位置堆疊只有在做為目前的位置堆疊時，才能供完整存取。</span><span class="sxs-lookup"><span data-stu-id="8747c-187">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="8747c-188">如果您將指定的位置堆疊設為目前的位置堆疊，您便無法再使用 `Push-Location` 或 `Pop-Location` Cmdlet 來加入或取得預設堆疊中的專案，或使用 `Get-Location` Cmdlet 來顯示未命名堆疊中的位置。</span><span class="sxs-lookup"><span data-stu-id="8747c-188">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="8747c-189">若要將未命名的堆疊設為目前的堆疊，請使用 Cmdlet 的 **StackName** 參數搭配的 `Set-Location` 值 `$null` 或 () 的空字串 `""` 。</span><span class="sxs-lookup"><span data-stu-id="8747c-189">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="8747c-190">您也可以 `Push-Location` 使用內建的別名來參考 `pushd` 。</span><span class="sxs-lookup"><span data-stu-id="8747c-190">You can also refer to `Push-Location` by its built-in alias, `pushd`.</span></span> <span data-ttu-id="8747c-191">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="8747c-191">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="8747c-192">此 `Push-Location` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="8747c-192">The `Push-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="8747c-193">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="8747c-193">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="8747c-194">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="8747c-194">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="8747c-195">相關連結</span><span class="sxs-lookup"><span data-stu-id="8747c-195">RELATED LINKS</span></span>

[<span data-ttu-id="8747c-196">Get-Location</span><span class="sxs-lookup"><span data-stu-id="8747c-196">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="8747c-197">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="8747c-197">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="8747c-198">Set-Location</span><span class="sxs-lookup"><span data-stu-id="8747c-198">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="8747c-199">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="8747c-199">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="8747c-200">about_Providers</span><span class="sxs-lookup"><span data-stu-id="8747c-200">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
