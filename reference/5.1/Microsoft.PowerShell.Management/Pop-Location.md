---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: 6843a598b5d20ebd9819b2ed0b180cd21f0416f4
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "93205880"
---
# <span data-ttu-id="43e48-103">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="43e48-103">Pop-Location</span></span>

## <span data-ttu-id="43e48-104">概要</span><span class="sxs-lookup"><span data-stu-id="43e48-104">SYNOPSIS</span></span>
<span data-ttu-id="43e48-105">將目前的位置變更至最近推送到堆疊上的位置。</span><span class="sxs-lookup"><span data-stu-id="43e48-105">Changes the current location to the location most recently pushed onto the stack.</span></span>

## <span data-ttu-id="43e48-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="43e48-106">SYNTAX</span></span>

```
Pop-Location [-PassThru] [-StackName <String>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="43e48-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="43e48-107">DESCRIPTION</span></span>

<span data-ttu-id="43e48-108">此 `Pop-Location` Cmdlet 會使用 Cmdlet 將目前的位置變更為最近推送至堆疊的位置 `Push-Location` 。</span><span class="sxs-lookup"><span data-stu-id="43e48-108">The `Pop-Location` cmdlet changes the current location to the location most recently pushed onto the stack by using the `Push-Location` cmdlet.</span></span> <span data-ttu-id="43e48-109">您可以從預設堆疊或從您使用命令建立的堆疊中取出位置 `Push-Location` 。</span><span class="sxs-lookup"><span data-stu-id="43e48-109">You can pop a location from the default stack or from a stack that you create by using a `Push-Location` command.</span></span>

## <span data-ttu-id="43e48-110">範例</span><span class="sxs-lookup"><span data-stu-id="43e48-110">EXAMPLES</span></span>

### <span data-ttu-id="43e48-111">範例 1︰變更為最新的位置</span><span class="sxs-lookup"><span data-stu-id="43e48-111">Example 1: Change to most recent location</span></span>

```
PS C:\> Pop-Location
```

<span data-ttu-id="43e48-112">此命令將您的位置變更至最近新增到目前堆疊的位置。</span><span class="sxs-lookup"><span data-stu-id="43e48-112">This command changes your location to the location most recently added to the current stack.</span></span>

### <span data-ttu-id="43e48-113">範例 2︰變更為具名堆疊中的最新位置</span><span class="sxs-lookup"><span data-stu-id="43e48-113">Example 2: Change to most recent location in a named stack</span></span>

```
PS C:\> Pop-Location -StackName "Stack2"
```

<span data-ttu-id="43e48-114">此命令將您的位置變更至最近新增到 Stack2 位置堆疊的位置。</span><span class="sxs-lookup"><span data-stu-id="43e48-114">This command changes your location to the location most recently added to the Stack2 location stack.</span></span>

<span data-ttu-id="43e48-115">如需位置堆疊的詳細資訊，請參閱 [附注](#notes)。</span><span class="sxs-lookup"><span data-stu-id="43e48-115">For more information about location stacks, see the [Notes](#notes).</span></span>

### <span data-ttu-id="43e48-116">範例 3︰在不同提供者的位置之間移動</span><span class="sxs-lookup"><span data-stu-id="43e48-116">Example 3: Move between locations for different providers</span></span>

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

<span data-ttu-id="43e48-117">這些命令會使用 `Push-Location` 和 `Pop-Location` Cmdlet 來移動不同 PowerShell 提供者所支援的位置。</span><span class="sxs-lookup"><span data-stu-id="43e48-117">These commands use the `Push-Location` and `Pop-Location` cmdlets to move between locations supported by different PowerShell providers.</span></span> <span data-ttu-id="43e48-118">這些命令會使用的 `pushd` 別名 `Push-Location` ，以及的 `popd` 別名 `Pop-Location` 。</span><span class="sxs-lookup"><span data-stu-id="43e48-118">The commands use the `pushd` alias for `Push-Location` and the `popd` alias for `Pop-Location`.</span></span>

<span data-ttu-id="43e48-119">第一個命令會將目前的檔案系統位置推送到堆疊上，並移至 PowerShell 登錄提供者所支援的 HKLM 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="43e48-119">The first command pushes the current file system location onto the stack and moves to the HKLM drive supported by the PowerShell Registry provider.</span></span>

<span data-ttu-id="43e48-120">第二個命令將登錄位置推送到堆疊上，並移至 PowerShell 憑證提供者所支援的位置。</span><span class="sxs-lookup"><span data-stu-id="43e48-120">The second command pushes the registry location onto the stack and moves to a location supported by the PowerShell certificate provider.</span></span>

<span data-ttu-id="43e48-121">最後兩個命令將這些位置從堆疊中取出。</span><span class="sxs-lookup"><span data-stu-id="43e48-121">The last two commands pop those locations off the stack.</span></span> <span data-ttu-id="43e48-122">第一個 `popd` 命令會返回登錄磁片磁碟機，第二個命令則會返回檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="43e48-122">The first `popd` command returns to the Registry drive, and the second command returns to the file system drive.</span></span>

## <span data-ttu-id="43e48-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="43e48-123">PARAMETERS</span></span>

### <span data-ttu-id="43e48-124">-PassThru</span><span class="sxs-lookup"><span data-stu-id="43e48-124">-PassThru</span></span>

<span data-ttu-id="43e48-125">將代表位置的物件傳遞至管線。</span><span class="sxs-lookup"><span data-stu-id="43e48-125">Passes an object that represents the location to the pipeline.</span></span> <span data-ttu-id="43e48-126">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="43e48-126">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="43e48-127">-StackName</span><span class="sxs-lookup"><span data-stu-id="43e48-127">-StackName</span></span>

<span data-ttu-id="43e48-128">指定要從中取出位置的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="43e48-128">Specifies the location stack from which the location is popped.</span></span> <span data-ttu-id="43e48-129">請輸入位置堆疊名稱。</span><span class="sxs-lookup"><span data-stu-id="43e48-129">Enter a location stack name.</span></span>

<span data-ttu-id="43e48-130">如果沒有這個參數，會 `Pop-Location` 從目前的位置堆疊取出位置。</span><span class="sxs-lookup"><span data-stu-id="43e48-130">Without this parameter, `Pop-Location` pops a location from the current location stack.</span></span> <span data-ttu-id="43e48-131">根據預設，目前的位置堆疊是 PowerShell 所建立的未命名預設位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="43e48-131">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span> <span data-ttu-id="43e48-132">若要將位置堆疊設為目前的位置堆疊，請使用 Cmdlet 的 **StackName** 參數 `Set-Location` 。</span><span class="sxs-lookup"><span data-stu-id="43e48-132">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="43e48-133">如需位置堆疊的詳細資訊，請參閱 [附注](#notes)。</span><span class="sxs-lookup"><span data-stu-id="43e48-133">For more information about location stacks, see the [Notes](#notes).</span></span>

<span data-ttu-id="43e48-134">`Pop-Location` 無法從未命名的預設堆疊中 pop 位置，除非它是目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="43e48-134">`Pop-Location` cannot pop a location from the unnamed default stack unless it is the current location stack.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="43e48-135">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="43e48-135">-UseTransaction</span></span>

<span data-ttu-id="43e48-136">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="43e48-136">Includes the command in the active transaction.</span></span> <span data-ttu-id="43e48-137">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="43e48-137">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="43e48-138">如需詳細資訊，請參閱 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="43e48-138">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="43e48-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="43e48-139">CommonParameters</span></span>

<span data-ttu-id="43e48-140">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="43e48-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="43e48-141">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="43e48-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="43e48-142">輸入</span><span class="sxs-lookup"><span data-stu-id="43e48-142">INPUTS</span></span>

### <span data-ttu-id="43e48-143">無</span><span class="sxs-lookup"><span data-stu-id="43e48-143">None</span></span>

<span data-ttu-id="43e48-144">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43e48-144">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="43e48-145">輸出</span><span class="sxs-lookup"><span data-stu-id="43e48-145">OUTPUTS</span></span>

### <span data-ttu-id="43e48-146">無、System.Management.Automation.PathInfo</span><span class="sxs-lookup"><span data-stu-id="43e48-146">None, System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="43e48-147">如果您指定 **PassThru** 參數，此 Cmdlet 會產生代表位置的 **System.Management.Automation.PathInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="43e48-147">This cmdlet generates a **System.Management.Automation.PathInfo** object that represents the location, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="43e48-148">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="43e48-148">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="43e48-149">注意</span><span class="sxs-lookup"><span data-stu-id="43e48-149">NOTES</span></span>

<span data-ttu-id="43e48-150">PowerShell 支援每個進程有多個空間。</span><span class="sxs-lookup"><span data-stu-id="43e48-150">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="43e48-151">每個運行空間都有自己的 _目前的目錄_ 。</span><span class="sxs-lookup"><span data-stu-id="43e48-151">Each runspace has its own _current directory_ .</span></span>
<span data-ttu-id="43e48-152">這與不同 `[System.Environment]::CurrentDirectory` 。</span><span class="sxs-lookup"><span data-stu-id="43e48-152">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="43e48-153">呼叫 .NET Api 或執行原生應用程式而不提供明確的目錄路徑時，此行為可能會產生問題。</span><span class="sxs-lookup"><span data-stu-id="43e48-153">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="43e48-154">即使位置 Cmdlet 已設定整個進程的目錄，您也無法依賴它，因為另一個執行時間可能會隨時變更。</span><span class="sxs-lookup"><span data-stu-id="43e48-154">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="43e48-155">您應該使用 location Cmdlet 來執行以路徑為基礎的作業，並使用目前的運行時特定的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="43e48-155">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="43e48-156">堆疊是一份後進先出的清單，其中只能存取最近新增的項目。</span><span class="sxs-lookup"><span data-stu-id="43e48-156">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="43e48-157">將項目新增到堆疊中時，順序與您使用它們的順序相同，然後抓取它們來使用時的順序則相反。</span><span class="sxs-lookup"><span data-stu-id="43e48-157">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="43e48-158">PowerShell 可讓您將提供者位置儲存在位置堆疊中。</span><span class="sxs-lookup"><span data-stu-id="43e48-158">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="43e48-159">PowerShell 會建立未命名的預設位置堆疊，而且您可以建立多個命名位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="43e48-159">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="43e48-160">如果您未指定堆疊名稱，PowerShell 會使用目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="43e48-160">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="43e48-161">根據預設，未命名的預設位置為目前的位置堆疊，但您可以使用 `Set-Location` Cmdlet 來變更目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="43e48-161">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="43e48-162">若要管理位置堆疊，請使用 PowerShell Cmdlet，如下所示 `*-Location` ：</span><span class="sxs-lookup"><span data-stu-id="43e48-162">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="43e48-163">若要將位置新增至位置堆疊，請使用 `Push-Location` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43e48-163">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="43e48-164">若要從位置堆疊取得位置，請使用 `Pop-Location` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43e48-164">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="43e48-165">若要顯示目前位置堆疊中的位置，請使用 Cmdlet 的 **stack** 參數 `Get-Location` 。</span><span class="sxs-lookup"><span data-stu-id="43e48-165">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="43e48-166">若要顯示命名位置堆疊中的位置，請使用 Cmdlet 的 **StackName** 參數 `Get-Location` 。</span><span class="sxs-lookup"><span data-stu-id="43e48-166">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="43e48-167">若要建立新的位置堆疊，請使用 Cmdlet 的 **StackName** 參數 `Push-Location` 。</span><span class="sxs-lookup"><span data-stu-id="43e48-167">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="43e48-168">如果您指定的堆疊不存在，就會 `Push-Location` 建立堆疊。</span><span class="sxs-lookup"><span data-stu-id="43e48-168">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="43e48-169">若要將位置堆疊設為目前的位置堆疊，請使用 Cmdlet 的 **StackName** 參數 `Set-Location` 。</span><span class="sxs-lookup"><span data-stu-id="43e48-169">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="43e48-170">未命名的預設位置堆疊只有在做為目前的位置堆疊時，才能供完整存取。</span><span class="sxs-lookup"><span data-stu-id="43e48-170">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="43e48-171">如果您將指定的位置堆疊設為目前的位置堆疊，您便無法再使用 `Push-Location` 或 `Pop-Location` Cmdlet 來加入或取得預設堆疊中的專案，或使用 `Get-Location` Cmdlet 來顯示未命名堆疊中的位置。</span><span class="sxs-lookup"><span data-stu-id="43e48-171">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="43e48-172">若要將未命名的堆疊設為目前的堆疊，請使用 Cmdlet 的 **StackName** 參數搭配的 `Set-Location` 值 `$Null` 或 () 的空字串 `""` 。</span><span class="sxs-lookup"><span data-stu-id="43e48-172">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$Null` or an empty string (`""`).</span></span>

<span data-ttu-id="43e48-173">您也可以 `Pop-Location` 使用內建的別名來參考 `popd` 。</span><span class="sxs-lookup"><span data-stu-id="43e48-173">You can also refer to `Pop-Location` by its built-in alias, `popd`.</span></span> <span data-ttu-id="43e48-174">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="43e48-174">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="43e48-175">`Pop-Location` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="43e48-175">`Pop-Location` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="43e48-176">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="43e48-176">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="43e48-177">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="43e48-177">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="43e48-178">相關連結</span><span class="sxs-lookup"><span data-stu-id="43e48-178">RELATED LINKS</span></span>

[<span data-ttu-id="43e48-179">Get-Location</span><span class="sxs-lookup"><span data-stu-id="43e48-179">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="43e48-180">Push-Location</span><span class="sxs-lookup"><span data-stu-id="43e48-180">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="43e48-181">Set-Location</span><span class="sxs-lookup"><span data-stu-id="43e48-181">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="43e48-182">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="43e48-182">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="43e48-183">about_Providers</span><span class="sxs-lookup"><span data-stu-id="43e48-183">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)