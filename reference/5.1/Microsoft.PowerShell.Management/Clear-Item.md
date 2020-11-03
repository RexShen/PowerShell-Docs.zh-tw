---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Item
ms.openlocfilehash: a0854fbff06ea51c322bdaf46c81f47f76af978b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204060"
---
# <span data-ttu-id="5fe2e-103">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="5fe2e-103">Clear-Item</span></span>

## <span data-ttu-id="5fe2e-104">概要</span><span class="sxs-lookup"><span data-stu-id="5fe2e-104">SYNOPSIS</span></span>
<span data-ttu-id="5fe2e-105">清除專案的內容，但不會刪除專案。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-105">Clears the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="5fe2e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5fe2e-106">SYNTAX</span></span>

### <span data-ttu-id="5fe2e-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="5fe2e-107">Path (Default)</span></span>

```
Clear-Item [-Path] <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="5fe2e-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5fe2e-108">LiteralPath</span></span>

```
Clear-Item -LiteralPath <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="5fe2e-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5fe2e-109">DESCRIPTION</span></span>

<span data-ttu-id="5fe2e-110">`Clear-Item`Cmdlet 會清除專案的內容，但不會刪除專案。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-110">The `Clear-Item` cmdlet clears the content of an item, but it does not delete the item.</span></span>
<span data-ttu-id="5fe2e-111">例如， `Clear-Item` Cmdlet 可以刪除變數的值，但不會刪除變數。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-111">For example, the `Clear-Item` cmdlet can delete the value of a variable, but it does not delete the variable.</span></span> <span data-ttu-id="5fe2e-112">用來代表已清除專案的值，是由每個 PowerShell 提供者所定義。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-112">The value that used to represent a cleared item is defined by each PowerShell provider.</span></span>
<span data-ttu-id="5fe2e-113">這個 Cmdlet 類似于 `Clear-Content` ，但它可用於別名和變數，而不是檔案。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-113">This cmdlet is similar to `Clear-Content`, but it works on aliases and variables, instead of files.</span></span>

## <span data-ttu-id="5fe2e-114">範例</span><span class="sxs-lookup"><span data-stu-id="5fe2e-114">EXAMPLES</span></span>

### <span data-ttu-id="5fe2e-115">範例1：清除變數的值</span><span class="sxs-lookup"><span data-stu-id="5fe2e-115">Example 1: Clear the value of a variable</span></span>

<span data-ttu-id="5fe2e-116">此命令會清除名為之變數的值 `TestVar1` 。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-116">This command clears the value of the variable named `TestVar1`.</span></span>
<span data-ttu-id="5fe2e-117">變數維持有效，但其值設定為 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-117">The variable remains and is valid, but its value is set to `$null`.</span></span>
<span data-ttu-id="5fe2e-118">變數名稱前面會加上 `Variable:` ，以表示 PowerShell 變數提供者。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-118">The variable name is prefixed with `Variable:` to indicate the PowerShell Variable provider.</span></span>

<span data-ttu-id="5fe2e-119">替代命令顯示，若要取得相同的結果，您可以切換到 PowerShell `Variable:` 磁片磁碟機，然後執行 `Clear-Item` 命令。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-119">The alternate commands show that, to get the same result, you can switch to the PowerShell `Variable:` drive and then run the `Clear-Item` command.</span></span>

```powershell
Clear-Item Variable:TestVar1
```

```
Set-Location Variable:
PS Variable:\> Clear-Item TestVar1
```

### <span data-ttu-id="5fe2e-120">範例2：清除所有登錄專案</span><span class="sxs-lookup"><span data-stu-id="5fe2e-120">Example 2: Clear all registry entries</span></span>

<span data-ttu-id="5fe2e-121">此命令會清除 "MyKey" 子機碼中的所有登錄專案，但是只有在提示您確認意圖之後才會這麼做。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-121">This command clears all registry entries in the "MyKey" subkey, but only after prompting you to confirm your intent.</span></span>
<span data-ttu-id="5fe2e-122">它不會刪除 "MyKey" 子機碼或影響任何其他的登錄機碼或專案。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-122">It does not delete the "MyKey" subkey or affect any other registry keys or entries.</span></span>
<span data-ttu-id="5fe2e-123">您可以使用 **Include** 與 **Exclude** 參數識別特定的登錄機碼，但無法使用它們來識別登錄項目。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-123">You can use the **Include** and **Exclude** parameters to identify particular registry keys, but you cannot use them to identify registry entries.</span></span>

- <span data-ttu-id="5fe2e-124">若要刪除特定的登錄專案，請使用 `Remove-ItemProperty` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-124">To delete particular registry entries, use the `Remove-ItemProperty` cmdlet.</span></span>
- <span data-ttu-id="5fe2e-125">若要刪除登錄專案的值，請使用 `Clear-ItemProperty` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-125">To delete the value of a registry entry, use the `Clear-ItemProperty` cmdlet.</span></span>

```powershell
Clear-Item HKLM:\Software\MyCompany\MyKey -Confirm
```

## <span data-ttu-id="5fe2e-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5fe2e-126">PARAMETERS</span></span>

### <span data-ttu-id="5fe2e-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="5fe2e-127">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="5fe2e-128">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-128">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="5fe2e-129">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-129">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="5fe2e-130">-Exclude</span><span class="sxs-lookup"><span data-stu-id="5fe2e-130">-Exclude</span></span>

<span data-ttu-id="5fe2e-131">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-131">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="5fe2e-132">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-132">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="5fe2e-133">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-133">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="5fe2e-134">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-134">Wildcard characters are permitted.</span></span> <span data-ttu-id="5fe2e-135">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-135">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="5fe2e-136">-Filter</span><span class="sxs-lookup"><span data-stu-id="5fe2e-136">-Filter</span></span>

<span data-ttu-id="5fe2e-137">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-137">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="5fe2e-138">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-138">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="5fe2e-139">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-139">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="5fe2e-140">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-140">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="5fe2e-141">-Force</span><span class="sxs-lookup"><span data-stu-id="5fe2e-141">-Force</span></span>

<span data-ttu-id="5fe2e-142">指出此 Cmdlet 會清除無法以其他方式變更的專案，例如唯讀別名。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-142">Indicates that the cmdlet clears items that cannot otherwise be changed, such as read- only aliases.</span></span>
<span data-ttu-id="5fe2e-143">Cmdlet 無法清除常數。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-143">The cmdlet cannot clear constants.</span></span>
<span data-ttu-id="5fe2e-144">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-144">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="5fe2e-145">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-145">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="5fe2e-146">即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-146">The cmdlet cannot override security restrictions, even when the **Force** parameter is used.</span></span>

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

### <span data-ttu-id="5fe2e-147">-Include</span><span class="sxs-lookup"><span data-stu-id="5fe2e-147">-Include</span></span>

<span data-ttu-id="5fe2e-148">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-148">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="5fe2e-149">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-149">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="5fe2e-150">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-150">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="5fe2e-151">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-151">Wildcard characters are permitted.</span></span> <span data-ttu-id="5fe2e-152">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-152">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="5fe2e-153">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5fe2e-153">-LiteralPath</span></span>

<span data-ttu-id="5fe2e-154">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-154">Specifies a path to one or more locations.</span></span> <span data-ttu-id="5fe2e-155">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-155">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="5fe2e-156">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-156">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="5fe2e-157">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-157">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="5fe2e-158">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-158">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="5fe2e-159">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-159">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="5fe2e-160">-Path</span><span class="sxs-lookup"><span data-stu-id="5fe2e-160">-Path</span></span>

<span data-ttu-id="5fe2e-161">指定要清除之項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-161">Specifies the path to the items being cleared.</span></span>
<span data-ttu-id="5fe2e-162">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-162">Wildcard characters are permitted.</span></span>
<span data-ttu-id="5fe2e-163">這個參數是必要參數，但參數名稱 **路徑** 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-163">This parameter is required, but the parameter name **Path** is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="5fe2e-164">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="5fe2e-164">-UseTransaction</span></span>

<span data-ttu-id="5fe2e-165">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-165">Includes the command in the active transaction.</span></span>
<span data-ttu-id="5fe2e-166">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-166">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="5fe2e-167">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-167">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="5fe2e-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5fe2e-168">-Confirm</span></span>

<span data-ttu-id="5fe2e-169">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-169">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5fe2e-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5fe2e-170">-WhatIf</span></span>

<span data-ttu-id="5fe2e-171">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5fe2e-172">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-172">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5fe2e-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5fe2e-173">CommonParameters</span></span>

<span data-ttu-id="5fe2e-174">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-174">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="5fe2e-175">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-175">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5fe2e-176">輸入</span><span class="sxs-lookup"><span data-stu-id="5fe2e-176">INPUTS</span></span>

### <span data-ttu-id="5fe2e-177">System.String</span><span class="sxs-lookup"><span data-stu-id="5fe2e-177">System.String</span></span>

<span data-ttu-id="5fe2e-178">您可以使用管線將路徑字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-178">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="5fe2e-179">輸出</span><span class="sxs-lookup"><span data-stu-id="5fe2e-179">OUTPUTS</span></span>

### <span data-ttu-id="5fe2e-180">無</span><span class="sxs-lookup"><span data-stu-id="5fe2e-180">None</span></span>

<span data-ttu-id="5fe2e-181">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-181">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5fe2e-182">注意</span><span class="sxs-lookup"><span data-stu-id="5fe2e-182">NOTES</span></span>

- <span data-ttu-id="5fe2e-183">`Clear-Item`只有數個 PowerShell 提供者支援此 Cmdlet，包括 **別名** 、 **環境** 、函 **Function** 式、 **Registry** 登錄和 **變數** 提供者。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-183">The `Clear-Item` cmdlet is supported only by several PowerShell providers, including the **Alias** , **Environment** , **Function** , **Registry** , and **Variable** providers.</span></span> <span data-ttu-id="5fe2e-184">因此，您可以使用 `Clear-Item` 刪除提供者命名空間中的專案內容。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-184">As such, you can use `Clear-Item` to delete the content of items in the provider namespaces.</span></span> <span data-ttu-id="5fe2e-185">若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-185">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="5fe2e-186">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-186">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
- <span data-ttu-id="5fe2e-187">您無法使用 `Clear-Item` 刪除檔案的內容，因為 PowerShell FileSystem 提供者不支援此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-187">You cannot use `Clear-Item` to delete the contents of a file, because the PowerShell FileSystem provider does not support this cmdlet.</span></span> <span data-ttu-id="5fe2e-188">若要清除檔案，請使用 `Clear-Content` 。</span><span class="sxs-lookup"><span data-stu-id="5fe2e-188">To clear files, use the `Clear-Content`.</span></span>

## <span data-ttu-id="5fe2e-189">相關連結</span><span class="sxs-lookup"><span data-stu-id="5fe2e-189">RELATED LINKS</span></span>

[<span data-ttu-id="5fe2e-190">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="5fe2e-190">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="5fe2e-191">Get-Item</span><span class="sxs-lookup"><span data-stu-id="5fe2e-191">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="5fe2e-192">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="5fe2e-192">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="5fe2e-193">Move-Item</span><span class="sxs-lookup"><span data-stu-id="5fe2e-193">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="5fe2e-194">New-Item</span><span class="sxs-lookup"><span data-stu-id="5fe2e-194">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="5fe2e-195">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="5fe2e-195">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="5fe2e-196">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="5fe2e-196">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="5fe2e-197">Set-Item</span><span class="sxs-lookup"><span data-stu-id="5fe2e-197">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="5fe2e-198">about_Providers</span><span class="sxs-lookup"><span data-stu-id="5fe2e-198">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
