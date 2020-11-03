---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Item
ms.openlocfilehash: c49cc60ec6ebf3f62a94f5511b55d578337be804
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203516"
---
# <span data-ttu-id="a515b-103">Set-Item</span><span class="sxs-lookup"><span data-stu-id="a515b-103">Set-Item</span></span>

## <span data-ttu-id="a515b-104">概要</span><span class="sxs-lookup"><span data-stu-id="a515b-104">SYNOPSIS</span></span>
<span data-ttu-id="a515b-105">將項目的值變更為命令中指定的值。</span><span class="sxs-lookup"><span data-stu-id="a515b-105">Changes the value of an item to the value specified in the command.</span></span>

## <span data-ttu-id="a515b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a515b-106">SYNTAX</span></span>

### <span data-ttu-id="a515b-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="a515b-107">Path (Default)</span></span>

```
Set-Item [-Path] <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="a515b-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a515b-108">LiteralPath</span></span>

```
Set-Item -LiteralPath <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="a515b-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a515b-109">DESCRIPTION</span></span>

<span data-ttu-id="a515b-110">Cmdlet 會將 `Set-Item` 專案（例如變數或登錄機碼）的值變更為命令中指定的值。</span><span class="sxs-lookup"><span data-stu-id="a515b-110">The `Set-Item` cmdlet changes the value of an item, such as a variable or registry key, to the value specified in the command.</span></span>

## <span data-ttu-id="a515b-111">範例</span><span class="sxs-lookup"><span data-stu-id="a515b-111">EXAMPLES</span></span>

### <span data-ttu-id="a515b-112">範例1：建立別名</span><span class="sxs-lookup"><span data-stu-id="a515b-112">Example 1: Create an alias</span></span>

<span data-ttu-id="a515b-113">此命令會為「記事本」建立 np 的別名。</span><span class="sxs-lookup"><span data-stu-id="a515b-113">This command creates an alias of np for Notepad.</span></span>

```powershell
Set-Item -Path alias:np -Value "c:\windows\notepad.exe"
```

### <span data-ttu-id="a515b-114">範例2：變更環境變數的值</span><span class="sxs-lookup"><span data-stu-id="a515b-114">Example 2: Change the value of an environment variable</span></span>

<span data-ttu-id="a515b-115">此命令會將 UserRole 環境變數的值變更為 Administrator。</span><span class="sxs-lookup"><span data-stu-id="a515b-115">This command changes the value of the UserRole environment variable to Administrator.</span></span>

```powershell
Set-Item -Path env:UserRole -Value "Administrator"
```

### <span data-ttu-id="a515b-116">範例3：修改提示字元函式</span><span class="sxs-lookup"><span data-stu-id="a515b-116">Example 3: Modify your prompt function</span></span>

<span data-ttu-id="a515b-117">此命令會變更提示字元函式，讓它顯示路徑之前的時間。</span><span class="sxs-lookup"><span data-stu-id="a515b-117">This command changes the prompt function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path function:prompt -Value {'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '}
```

### <span data-ttu-id="a515b-118">範例4：設定 prompt 函數的選項</span><span class="sxs-lookup"><span data-stu-id="a515b-118">Example 4: Set options for your prompt function</span></span>

<span data-ttu-id="a515b-119">此命令會設定 prompt 函式的 **AllScope** 和 **ReadOnly** 選項。</span><span class="sxs-lookup"><span data-stu-id="a515b-119">This command sets the **AllScope** and **ReadOnly** options for the prompt function.</span></span>
<span data-ttu-id="a515b-120">此命令會使用 **Options** 的動態參數選項 `Set-Item` 。</span><span class="sxs-lookup"><span data-stu-id="a515b-120">This command uses the **Options** dynamic parameter of `Set-Item`.</span></span>
<span data-ttu-id="a515b-121">**Options** `Set-Item` 只有當您將 Options 參數與 **Alias** 或 **Function** 提供者搭配使用時，才能使用這些選項。</span><span class="sxs-lookup"><span data-stu-id="a515b-121">The **Options** parameter is available in `Set-Item` only when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path function:prompt -Options "AllScope,ReadOnly"
```

## <span data-ttu-id="a515b-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a515b-122">PARAMETERS</span></span>

### <span data-ttu-id="a515b-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="a515b-123">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a515b-124">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="a515b-124">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="a515b-125">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="a515b-125">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a515b-126">-Exclude</span><span class="sxs-lookup"><span data-stu-id="a515b-126">-Exclude</span></span>

<span data-ttu-id="a515b-127">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="a515b-127">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="a515b-128">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="a515b-128">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a515b-129">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="a515b-129">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a515b-130">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="a515b-130">Wildcard characters are permitted.</span></span> <span data-ttu-id="a515b-131">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="a515b-131">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a515b-132">-Filter</span><span class="sxs-lookup"><span data-stu-id="a515b-132">-Filter</span></span>

<span data-ttu-id="a515b-133">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="a515b-133">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="a515b-134">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="a515b-134">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="a515b-135">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="a515b-135">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="a515b-136">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="a515b-136">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a515b-137">-Force</span><span class="sxs-lookup"><span data-stu-id="a515b-137">-Force</span></span>

<span data-ttu-id="a515b-138">強制 Cmdlet 設定無法以其他方式變更的專案，例如唯讀別名或變數。</span><span class="sxs-lookup"><span data-stu-id="a515b-138">Forces the cmdlet to set items that cannot otherwise be changed, such as read-only alias or variables.</span></span> <span data-ttu-id="a515b-139">此 Cmdlet 無法變更常數別名或變數。</span><span class="sxs-lookup"><span data-stu-id="a515b-139">The cmdlet cannot change constant aliases or variables.</span></span>
<span data-ttu-id="a515b-140">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="a515b-140">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="a515b-141">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="a515b-141">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="a515b-142">即使使用 *Force* 參數，Cmdlet 也無法覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="a515b-142">Even using the *Force* parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="a515b-143">-Include</span><span class="sxs-lookup"><span data-stu-id="a515b-143">-Include</span></span>

<span data-ttu-id="a515b-144">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="a515b-144">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="a515b-145">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="a515b-145">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a515b-146">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="a515b-146">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="a515b-147">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="a515b-147">Wildcard characters are permitted.</span></span> <span data-ttu-id="a515b-148">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="a515b-148">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a515b-149">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a515b-149">-LiteralPath</span></span>

<span data-ttu-id="a515b-150">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="a515b-150">Specifies a path to one or more locations.</span></span> <span data-ttu-id="a515b-151">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="a515b-151">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="a515b-152">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="a515b-152">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a515b-153">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="a515b-153">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a515b-154">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="a515b-154">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a515b-155">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="a515b-155">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a515b-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a515b-156">-PassThru</span></span>

<span data-ttu-id="a515b-157">將代表專案的物件傳遞至管線。</span><span class="sxs-lookup"><span data-stu-id="a515b-157">Passes an object that represents the item to the pipeline.</span></span>
<span data-ttu-id="a515b-158">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="a515b-158">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a515b-159">-Path</span><span class="sxs-lookup"><span data-stu-id="a515b-159">-Path</span></span>

<span data-ttu-id="a515b-160">指定專案位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="a515b-160">Specifies a path of the location of the items.</span></span>
<span data-ttu-id="a515b-161">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="a515b-161">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a515b-162">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="a515b-162">-UseTransaction</span></span>

<span data-ttu-id="a515b-163">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="a515b-163">Includes the command in the active transaction.</span></span>
<span data-ttu-id="a515b-164">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="a515b-164">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="a515b-165">如需詳細資訊，請參閱 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="a515b-165">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="a515b-166">-Value</span><span class="sxs-lookup"><span data-stu-id="a515b-166">-Value</span></span>

<span data-ttu-id="a515b-167">指定項目的新值。</span><span class="sxs-lookup"><span data-stu-id="a515b-167">Specifies a new value for the item.</span></span>

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

### <span data-ttu-id="a515b-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a515b-168">-Confirm</span></span>

<span data-ttu-id="a515b-169">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="a515b-169">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a515b-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a515b-170">-WhatIf</span></span>

<span data-ttu-id="a515b-171">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="a515b-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a515b-172">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="a515b-172">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a515b-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a515b-173">CommonParameters</span></span>

<span data-ttu-id="a515b-174">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="a515b-174">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a515b-175">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="a515b-175">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a515b-176">輸入</span><span class="sxs-lookup"><span data-stu-id="a515b-176">INPUTS</span></span>

### <span data-ttu-id="a515b-177">System.Object</span><span class="sxs-lookup"><span data-stu-id="a515b-177">System.Object</span></span>

<span data-ttu-id="a515b-178">您可以使用管線將代表專案新值的物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a515b-178">You can pipe an object that represents the new value of the item to this cmdlet.</span></span>

## <span data-ttu-id="a515b-179">輸出</span><span class="sxs-lookup"><span data-stu-id="a515b-179">OUTPUTS</span></span>

### <span data-ttu-id="a515b-180">無或是表示新項目或變更項目的物件。</span><span class="sxs-lookup"><span data-stu-id="a515b-180">None or an object representing the new or changed item.</span></span>

<span data-ttu-id="a515b-181">如果您指定 *PassThru* 參數，此 Cmdlet 會產生代表專案的物件。</span><span class="sxs-lookup"><span data-stu-id="a515b-181">This cmdlet generates an object that represent the item, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="a515b-182">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="a515b-182">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a515b-183">注意</span><span class="sxs-lookup"><span data-stu-id="a515b-183">NOTES</span></span>

- <span data-ttu-id="a515b-184">`Set-Item` PowerShell FileSystem 提供者不支援。</span><span class="sxs-lookup"><span data-stu-id="a515b-184">`Set-Item` is not supported by the PowerShell FileSystem provider.</span></span> <span data-ttu-id="a515b-185">若要變更檔案系統中專案的值，請使用 `Set-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a515b-185">To change the values of items in the file system, use the `Set-Content` cmdlet.</span></span>
- <span data-ttu-id="a515b-186">在登錄磁片磁碟機 `HKLM:` 和中 `HKCU:` ，會 `Set-Item` 變更登錄機碼 (預設) 值中的資料。</span><span class="sxs-lookup"><span data-stu-id="a515b-186">In the Registry drives, `HKLM:` and `HKCU:`, `Set-Item` changes the data in the (Default) value of a registry key.</span></span>
  - <span data-ttu-id="a515b-187">若要建立和變更登錄機碼的名稱，請使用 `New-Item` 和 `Rename-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a515b-187">To create and change the names of registry keys, use the `New-Item` and `Rename-Item` cmdlet.</span></span>
  - <span data-ttu-id="a515b-188">若要變更登錄值中的名稱和資料，請使用 `New-ItemProperty` 、 `Set-ItemProperty` 和 `Rename-ItemProperty` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a515b-188">To change the names and data in registry values, use the `New-ItemProperty`, `Set-ItemProperty`, and `Rename-ItemProperty` cmdlets.</span></span>
- <span data-ttu-id="a515b-189">`Set-Item` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="a515b-189">`Set-Item` is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="a515b-190">若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="a515b-190">To list the providers available in your session, type `Get-PsProvider`.</span></span>
  <span data-ttu-id="a515b-191">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="a515b-191">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a515b-192">相關連結</span><span class="sxs-lookup"><span data-stu-id="a515b-192">RELATED LINKS</span></span>

[<span data-ttu-id="a515b-193">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="a515b-193">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="a515b-194">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="a515b-194">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="a515b-195">Get-Item</span><span class="sxs-lookup"><span data-stu-id="a515b-195">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="a515b-196">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="a515b-196">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="a515b-197">Move-Item</span><span class="sxs-lookup"><span data-stu-id="a515b-197">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="a515b-198">New-Item</span><span class="sxs-lookup"><span data-stu-id="a515b-198">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="a515b-199">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="a515b-199">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="a515b-200">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="a515b-200">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="a515b-201">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a515b-201">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
