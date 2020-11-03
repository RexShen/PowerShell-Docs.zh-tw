---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: 06b1596366c9c9e20857b55aa9a17342bab07028
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "93206063"
---
# <span data-ttu-id="625da-103">Set-Location</span><span class="sxs-lookup"><span data-stu-id="625da-103">Set-Location</span></span>

## <span data-ttu-id="625da-104">概要</span><span class="sxs-lookup"><span data-stu-id="625da-104">SYNOPSIS</span></span>
<span data-ttu-id="625da-105">將目前的工作位置設定為指定的位置。</span><span class="sxs-lookup"><span data-stu-id="625da-105">Sets the current working location to a specified location.</span></span>

## <span data-ttu-id="625da-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="625da-106">SYNTAX</span></span>

### <span data-ttu-id="625da-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="625da-107">Path (Default)</span></span>

```
Set-Location [[-Path] <String>] [-PassThru] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="625da-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="625da-108">LiteralPath</span></span>

```
Set-Location -LiteralPath <String> [-PassThru] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="625da-109">Stack</span><span class="sxs-lookup"><span data-stu-id="625da-109">Stack</span></span>

```
Set-Location [-PassThru] [-StackName <String>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="625da-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="625da-110">DESCRIPTION</span></span>

<span data-ttu-id="625da-111">`Set-Location`Cmdlet 會將工作位置設定為指定的位置。</span><span class="sxs-lookup"><span data-stu-id="625da-111">The `Set-Location` cmdlet sets the working location to a specified location.</span></span> <span data-ttu-id="625da-112">該位置可以是目錄、子目錄、登錄位置或任何提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="625da-112">That location could be a directory, a subdirectory, a registry location, or any provider path.</span></span>

<span data-ttu-id="625da-113">您也可以使用 **StackName** 參數，將命名位置堆疊設為目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="625da-113">You can also use the **StackName** parameter to make a named location stack the current location stack.</span></span> <span data-ttu-id="625da-114">如需位置堆疊的詳細資訊，請參閱附註。</span><span class="sxs-lookup"><span data-stu-id="625da-114">For more information about location stacks, see the Notes.</span></span>

## <span data-ttu-id="625da-115">範例</span><span class="sxs-lookup"><span data-stu-id="625da-115">EXAMPLES</span></span>

### <span data-ttu-id="625da-116">範例1：設定目前的位置</span><span class="sxs-lookup"><span data-stu-id="625da-116">Example 1: Set the current location</span></span>

```powershell
PS C:\> Set-Location -Path "HKLM:\"
```

```output
PS HKLM:\>
```

<span data-ttu-id="625da-117">此命令會將目前的位置設定為 `HKLM:` 磁片磁碟機的根目錄。</span><span class="sxs-lookup"><span data-stu-id="625da-117">This command sets the current location to the root of the `HKLM:` drive.</span></span>

### <span data-ttu-id="625da-118">範例2：設定目前的位置，並顯示該位置</span><span class="sxs-lookup"><span data-stu-id="625da-118">Example 2: Set the current location and display that location</span></span>

```powershell
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```output
Path
----
Env:\

PS Env:\>
```

<span data-ttu-id="625da-119">此命令會將目前的位置設定為 `Env:` 磁片磁碟機的根目錄。</span><span class="sxs-lookup"><span data-stu-id="625da-119">This command sets the current location to the root of the `Env:` drive.</span></span> <span data-ttu-id="625da-120">它使用 **PassThru** 參數指示 PowerShell 傳回代表位置的 **system.management.automation.pathinfo** 物件 `Env:\` 。</span><span class="sxs-lookup"><span data-stu-id="625da-120">It uses the **PassThru** parameter to direct PowerShell to return a **PathInfo** object that represents the `Env:\` location.</span></span>

### <span data-ttu-id="625da-121">範例3：將位置設定為 C：磁片磁碟機中的目前位置</span><span class="sxs-lookup"><span data-stu-id="625da-121">Example 3: Set location to the current location in the C: drive</span></span>

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

<span data-ttu-id="625da-122">第一個命令會將位置設定為 `HKLM:` 登錄提供者中磁片磁碟機的根目錄。</span><span class="sxs-lookup"><span data-stu-id="625da-122">The first command sets the location to the root of the `HKLM:` drive in the Registry provider.</span></span>
<span data-ttu-id="625da-123">第二個命令會將位置設定為 `C:` FileSystem 提供者中磁片磁碟機的目前位置。</span><span class="sxs-lookup"><span data-stu-id="625da-123">The second command sets the location to the current location of the `C:` drive in the FileSystem provider.</span></span>
<span data-ttu-id="625da-124">當磁片磁碟機名稱是以格式 `<DriveName>:` (沒有反斜線) 指定時，此 Cmdlet 會將位置設定為 new-psdrive 中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="625da-124">When the drive name is specified in the form `<DriveName>:` (without backslash), the cmdlet sets the location to the current location in the PSDrive.</span></span>
<span data-ttu-id="625da-125">以取得 New-psdrive use 命令中的目前位置 `Get-Location -PSDrive <DriveName>` 。</span><span class="sxs-lookup"><span data-stu-id="625da-125">To get the current location in the PSDrive use `Get-Location -PSDrive <DriveName>` command.</span></span>

### <span data-ttu-id="625da-126">範例4：將目前位置設定為命名堆疊</span><span class="sxs-lookup"><span data-stu-id="625da-126">Example 4: Set the current location to a named stack</span></span>

```powershell
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

<span data-ttu-id="625da-127">第一個命令會將目前的位置新增至路徑堆疊。</span><span class="sxs-lookup"><span data-stu-id="625da-127">The first command adds the current location to the Paths stack.</span></span>
<span data-ttu-id="625da-128">第二個命令會讓路徑位置堆疊成為目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="625da-128">The second command makes the Paths location stack the current location stack.</span></span>
<span data-ttu-id="625da-129">第三個命令會顯示目前位置堆疊中的位置。</span><span class="sxs-lookup"><span data-stu-id="625da-129">The third command displays the locations in the current location stack.</span></span>

<span data-ttu-id="625da-130">`*-Location`除非在命令中指定不同的位置堆疊，否則 Cmdlet 會使用目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="625da-130">The `*-Location` cmdlets use the current location stack unless a different location stack is specified in the command.</span></span> <span data-ttu-id="625da-131">如需位置堆疊的相關資訊，請參閱 [附注](#notes)。</span><span class="sxs-lookup"><span data-stu-id="625da-131">For information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="625da-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="625da-132">PARAMETERS</span></span>

### <span data-ttu-id="625da-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="625da-133">-LiteralPath</span></span>

<span data-ttu-id="625da-134">指定位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="625da-134">Specifies a path of the location.</span></span> <span data-ttu-id="625da-135">**LiteralPath** 參數的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="625da-135">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="625da-136">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="625da-136">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="625da-137">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="625da-137">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="625da-138">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="625da-138">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="625da-139">單引號告知 Windows PowerShell 不要將任何字元視為逸出序列。</span><span class="sxs-lookup"><span data-stu-id="625da-139">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="625da-140">-PassThru</span><span class="sxs-lookup"><span data-stu-id="625da-140">-PassThru</span></span>

<span data-ttu-id="625da-141">傳回代表位置的 **system.management.automation.pathinfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="625da-141">Returns a **PathInfo** object that represents the location.</span></span> <span data-ttu-id="625da-142">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="625da-142">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="625da-143">-Path</span><span class="sxs-lookup"><span data-stu-id="625da-143">-Path</span></span>

<span data-ttu-id="625da-144">指定新工作位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="625da-144">Specify the path of a new working location.</span></span> <span data-ttu-id="625da-145">如果未提供路徑，則 `Set-Location` 預設為目前使用者的主目錄。</span><span class="sxs-lookup"><span data-stu-id="625da-145">If no path is provided, `Set-Location` defaults to the current user's home directory.</span></span> <span data-ttu-id="625da-146">使用萬用字元時，此 Cmdlet 會選擇符合萬用字元模式的第一個路徑。</span><span class="sxs-lookup"><span data-stu-id="625da-146">When wildcards are used, the cmdlet chooses the first path that matches the wildcard pattern.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="625da-147">-StackName</span><span class="sxs-lookup"><span data-stu-id="625da-147">-StackName</span></span>

<span data-ttu-id="625da-148">指定此 Cmdlet 用來建立目前位置堆疊的現有位置堆疊名稱。</span><span class="sxs-lookup"><span data-stu-id="625da-148">Specifies the existing location stack name that this cmdlet makes the current location stack.</span></span> <span data-ttu-id="625da-149">請輸入位置堆疊名稱。</span><span class="sxs-lookup"><span data-stu-id="625da-149">Enter a location stack name.</span></span> <span data-ttu-id="625da-150">若要指出未命名的預設位置堆疊，請輸入 `$null` 或 () 的空字串 `""` 。</span><span class="sxs-lookup"><span data-stu-id="625da-150">To indicate the unnamed default location stack, type `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="625da-151">`*-Location`Cmdlet 會在目前的堆疊上作用，除非您使用 **StackName** 參數來指定不同的堆疊。</span><span class="sxs-lookup"><span data-stu-id="625da-151">The `*-Location` cmdlets act on the current stack unless you use the **StackName** parameter to specify a different stack.</span></span>

```yaml
Type: System.String
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="625da-152">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="625da-152">-UseTransaction</span></span>

<span data-ttu-id="625da-153">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="625da-153">Includes the command in the active transaction.</span></span>
<span data-ttu-id="625da-154">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="625da-154">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="625da-155">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="625da-155">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="625da-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="625da-156">CommonParameters</span></span>

<span data-ttu-id="625da-157">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="625da-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="625da-158">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="625da-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="625da-159">輸入</span><span class="sxs-lookup"><span data-stu-id="625da-159">INPUTS</span></span>

### <span data-ttu-id="625da-160">System.String</span><span class="sxs-lookup"><span data-stu-id="625da-160">System.String</span></span>

<span data-ttu-id="625da-161">您可以使用管線將包含路徑 (但不是常值路徑) 的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="625da-161">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="625da-162">輸出</span><span class="sxs-lookup"><span data-stu-id="625da-162">OUTPUTS</span></span>

### <span data-ttu-id="625da-163">無、System.Management.Automation.PathInfo、System.Management.Automation.PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="625da-163">None, System.Management.Automation.PathInfo, System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="625da-164">除非您指定 **PassThru** 參數，否則這個 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="625da-164">This cmdlet does not generate any output unless you specify the **PassThru** parameter.</span></span> <span data-ttu-id="625da-165">使用 **PassThru** 搭配 **Path** 或 **LiteralPath** 會產生代表新位置的 **system.management.automation.pathinfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="625da-165">Using **PassThru** with **Path** or **LiteralPath** generates a **PathInfo** object that represents the new location.</span></span> <span data-ttu-id="625da-166">使用 **PassThru** with **StackName** 會產生代表新堆疊內容的 **PathInfoStack** 物件。</span><span class="sxs-lookup"><span data-stu-id="625da-166">Using **PassThru** with **StackName** generates a **PathInfoStack** object representing the new stack context.</span></span>

## <span data-ttu-id="625da-167">注意</span><span class="sxs-lookup"><span data-stu-id="625da-167">NOTES</span></span>

<span data-ttu-id="625da-168">PowerShell 支援每個進程有多個空間。</span><span class="sxs-lookup"><span data-stu-id="625da-168">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="625da-169">每個運行空間都有自己的 _目前的目錄_ 。</span><span class="sxs-lookup"><span data-stu-id="625da-169">Each runspace has its own _current directory_ .</span></span>
<span data-ttu-id="625da-170">這與不同 `[System.Environment]::CurrentDirectory` 。</span><span class="sxs-lookup"><span data-stu-id="625da-170">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="625da-171">呼叫 .NET Api 或執行原生應用程式而不提供明確的目錄路徑時，此行為可能會產生問題。</span><span class="sxs-lookup"><span data-stu-id="625da-171">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="625da-172">即使位置 Cmdlet 已設定整個進程的目錄，您也無法依賴它，因為另一個執行時間可能會隨時變更。</span><span class="sxs-lookup"><span data-stu-id="625da-172">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="625da-173">您應該使用 location Cmdlet 來執行以路徑為基礎的作業，並使用目前的運行時特定的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="625da-173">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="625da-174">此 `Set-Location` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="625da-174">The `Set-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="625da-175">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="625da-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="625da-176">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="625da-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span></span>

<span data-ttu-id="625da-177">堆疊是一份後進先出的清單，其中只能存取最近新增的項目。</span><span class="sxs-lookup"><span data-stu-id="625da-177">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="625da-178">將項目新增到堆疊中時，順序與您使用它們的順序相同，然後抓取它們來使用時的順序則相反。</span><span class="sxs-lookup"><span data-stu-id="625da-178">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="625da-179">PowerShell 可讓您將提供者位置儲存在位置堆疊中。</span><span class="sxs-lookup"><span data-stu-id="625da-179">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="625da-180">PowerShell 會建立未命名的預設位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="625da-180">PowerShell creates an unnamed default location stack.</span></span> <span data-ttu-id="625da-181">您可以建立多個命名位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="625da-181">You can create multiple named location stacks.</span></span> <span data-ttu-id="625da-182">如果您未指定堆疊名稱，PowerShell 會使用目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="625da-182">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="625da-183">根據預設，未命名的預設位置為目前的位置堆疊，但您可以使用 `Set-Location` Cmdlet 來變更目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="625da-183">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="625da-184">若要管理位置堆疊，請使用 Cmdlet，如下所示 `*-Location` ：</span><span class="sxs-lookup"><span data-stu-id="625da-184">To manage location stacks, use the `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="625da-185">若要將位置新增至位置堆疊，請使用 `Push-Location` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="625da-185">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="625da-186">若要從位置堆疊取得位置，請使用 `Pop-Location` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="625da-186">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="625da-187">若要顯示目前位置堆疊中的位置，請使用 Cmdlet 的 **stack** 參數 `Get-Location` 。</span><span class="sxs-lookup"><span data-stu-id="625da-187">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="625da-188">若要顯示命名位置堆疊中的位置，請使用的 **StackName** 參數 `Get-Location` 。</span><span class="sxs-lookup"><span data-stu-id="625da-188">To display the locations in a named location stack, use the **StackName** parameter of `Get-Location`.</span></span>

- <span data-ttu-id="625da-189">若要建立新的位置堆疊，請使用的 **StackName** 參數 `Push-Location` 。</span><span class="sxs-lookup"><span data-stu-id="625da-189">To create a new location stack, use the **StackName** parameter of `Push-Location`.</span></span> <span data-ttu-id="625da-190">如果您指定的堆疊不存在，就會 `Push-Location` 建立堆疊。</span><span class="sxs-lookup"><span data-stu-id="625da-190">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="625da-191">若要將位置堆疊設為目前的位置堆疊，請使用的 **StackName** 參數 `Set-Location` 。</span><span class="sxs-lookup"><span data-stu-id="625da-191">To make a location stack the current location stack, use the **StackName** parameter of `Set-Location`.</span></span>

<span data-ttu-id="625da-192">未命名的預設位置堆疊只有在做為目前的位置堆疊時，才能供完整存取。</span><span class="sxs-lookup"><span data-stu-id="625da-192">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="625da-193">如果您將指定的位置堆疊設為目前的位置堆疊，您便無法再使用 `Push-Location` 或 `Pop-Location` Cmdlet 來加入或取得預設堆疊中的專案，或使用 `Get-Location` Cmdlet 來顯示未命名堆疊中的位置。</span><span class="sxs-lookup"><span data-stu-id="625da-193">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="625da-194">若要將未命名的堆疊設為目前的堆疊，請使用 Cmdlet 的 **StackName** 參數搭配的 `Set-Location` 值 `$null` 或 () 的空字串 `""` 。</span><span class="sxs-lookup"><span data-stu-id="625da-194">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="625da-195">相關連結</span><span class="sxs-lookup"><span data-stu-id="625da-195">RELATED LINKS</span></span>

[<span data-ttu-id="625da-196">Get-Location</span><span class="sxs-lookup"><span data-stu-id="625da-196">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="625da-197">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="625da-197">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="625da-198">Push-Location</span><span class="sxs-lookup"><span data-stu-id="625da-198">Push-Location</span></span>](Push-Location.md)
