---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-ItemProperty
ms.openlocfilehash: b23db6af5d34b8a6413a21fafd34fc5e19f5690a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204067"
---
# <span data-ttu-id="21253-103">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="21253-103">Clear-ItemProperty</span></span>

## <span data-ttu-id="21253-104">概要</span><span class="sxs-lookup"><span data-stu-id="21253-104">SYNOPSIS</span></span>
<span data-ttu-id="21253-105">清除屬性的值，但不刪除屬性。</span><span class="sxs-lookup"><span data-stu-id="21253-105">Clears the value of a property but does not delete the property.</span></span>

## <span data-ttu-id="21253-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="21253-106">SYNTAX</span></span>

### <span data-ttu-id="21253-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="21253-107">Path (Default)</span></span>

```
Clear-ItemProperty [-Path] <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="21253-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="21253-108">LiteralPath</span></span>

```
Clear-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="21253-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="21253-109">DESCRIPTION</span></span>

<span data-ttu-id="21253-110">`Clear-ItemProperty`Cmdlet 會清除屬性的值，但不會刪除屬性。</span><span class="sxs-lookup"><span data-stu-id="21253-110">The `Clear-ItemProperty` cmdlet clears the value of a property, but it does not delete the property.</span></span>
<span data-ttu-id="21253-111">您可以使用此 Cmdlet 刪除登錄值中的資料。</span><span class="sxs-lookup"><span data-stu-id="21253-111">You can use this cmdlet to delete the data from a registry value.</span></span>

## <span data-ttu-id="21253-112">範例</span><span class="sxs-lookup"><span data-stu-id="21253-112">EXAMPLES</span></span>

### <span data-ttu-id="21253-113">範例1：清除登錄機碼的值</span><span class="sxs-lookup"><span data-stu-id="21253-113">Example 1: Clear the value of registry key</span></span>

<span data-ttu-id="21253-114">此命令會清除的 "MyApp" 子機碼中 "Options" 登錄值的資料 `HKEY_LOCAL_MACHINE\Software\MyCompany` 。</span><span class="sxs-lookup"><span data-stu-id="21253-114">This command clears the data in the "Options" registry value in the "MyApp" subkey of `HKEY_LOCAL_MACHINE\Software\MyCompany`.</span></span>

```powershell
Clear-ItemProperty -Path "HKLM:\Software\MyCompany\MyApp" -Name "Options"
```

## <span data-ttu-id="21253-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="21253-115">PARAMETERS</span></span>

### <span data-ttu-id="21253-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="21253-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="21253-117">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="21253-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="21253-118">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="21253-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="21253-119">-Exclude</span><span class="sxs-lookup"><span data-stu-id="21253-119">-Exclude</span></span>

<span data-ttu-id="21253-120">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="21253-120">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="21253-121">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="21253-121">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="21253-122">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="21253-122">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="21253-123">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="21253-123">Wildcard characters are permitted.</span></span> <span data-ttu-id="21253-124">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="21253-124">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="21253-125">-Filter</span><span class="sxs-lookup"><span data-stu-id="21253-125">-Filter</span></span>

<span data-ttu-id="21253-126">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="21253-126">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="21253-127">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="21253-127">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="21253-128">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="21253-128">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="21253-129">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="21253-129">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="21253-130">-Force</span><span class="sxs-lookup"><span data-stu-id="21253-130">-Force</span></span>

<span data-ttu-id="21253-131">指出此 Cmdlet 會從使用者無法以其他方式存取的專案刪除屬性。</span><span class="sxs-lookup"><span data-stu-id="21253-131">Indicates that this cmdlet deletes properties from items that cannot otherwise be accessed by the user.</span></span> <span data-ttu-id="21253-132">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="21253-132">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="21253-133">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="21253-133">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="21253-134">-Include</span><span class="sxs-lookup"><span data-stu-id="21253-134">-Include</span></span>

<span data-ttu-id="21253-135">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="21253-135">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="21253-136">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="21253-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="21253-137">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="21253-137">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="21253-138">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="21253-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="21253-139">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="21253-139">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="21253-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="21253-140">-LiteralPath</span></span>

<span data-ttu-id="21253-141">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="21253-141">Specifies a path to one or more locations.</span></span> <span data-ttu-id="21253-142">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="21253-142">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="21253-143">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="21253-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="21253-144">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="21253-144">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="21253-145">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="21253-145">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="21253-146">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="21253-146">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="21253-147">-Name</span><span class="sxs-lookup"><span data-stu-id="21253-147">-Name</span></span>

<span data-ttu-id="21253-148">指定要清除的屬性名稱，例如登錄值的名稱。</span><span class="sxs-lookup"><span data-stu-id="21253-148">Specifies the name of the property to be cleared, such as the name of a registry value.</span></span>
<span data-ttu-id="21253-149">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="21253-149">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="21253-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="21253-150">-PassThru</span></span>

<span data-ttu-id="21253-151">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="21253-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="21253-152">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="21253-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="21253-153">-Path</span><span class="sxs-lookup"><span data-stu-id="21253-153">-Path</span></span>

<span data-ttu-id="21253-154">指定要清除屬性的路徑。</span><span class="sxs-lookup"><span data-stu-id="21253-154">Specifies the path to the property being cleared.</span></span>
<span data-ttu-id="21253-155">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="21253-155">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="21253-156">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="21253-156">-UseTransaction</span></span>

<span data-ttu-id="21253-157">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="21253-157">Includes the command in the active transaction.</span></span>
<span data-ttu-id="21253-158">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="21253-158">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="21253-159">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="21253-159">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="21253-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="21253-160">-Confirm</span></span>

<span data-ttu-id="21253-161">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="21253-161">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="21253-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="21253-162">-WhatIf</span></span>

<span data-ttu-id="21253-163">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="21253-163">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="21253-164">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="21253-164">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="21253-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="21253-165">CommonParameters</span></span>

<span data-ttu-id="21253-166">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="21253-166">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="21253-167">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="21253-167">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="21253-168">輸入</span><span class="sxs-lookup"><span data-stu-id="21253-168">INPUTS</span></span>

### <span data-ttu-id="21253-169">System.String</span><span class="sxs-lookup"><span data-stu-id="21253-169">System.String</span></span>

<span data-ttu-id="21253-170">您可以使用管線將路徑字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="21253-170">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="21253-171">輸出</span><span class="sxs-lookup"><span data-stu-id="21253-171">OUTPUTS</span></span>

### <span data-ttu-id="21253-172">無或 System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="21253-172">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="21253-173">當您使用 *PassThru* 參數時，會 `Clear-ItemProperty` 產生代表已清除專案屬性的 **PSCustomObject** 物件。</span><span class="sxs-lookup"><span data-stu-id="21253-173">When you use the *PassThru* parameter, `Clear-ItemProperty` generates a **PSCustomObject** object that represents the cleared item property.</span></span>
<span data-ttu-id="21253-174">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="21253-174">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="21253-175">注意</span><span class="sxs-lookup"><span data-stu-id="21253-175">NOTES</span></span>

<span data-ttu-id="21253-176">您可以使用 `Clear-ItemProperty` 刪除登錄值中的資料而不刪除值。</span><span class="sxs-lookup"><span data-stu-id="21253-176">You can use `Clear-ItemProperty` to delete the data in registry values without deleting the value.</span></span> <span data-ttu-id="21253-177">如果值的資料類型是二進位或 DWORD，清除資料會將值設定為零。</span><span class="sxs-lookup"><span data-stu-id="21253-177">If the data type of the value is Binary or DWORD, clearing the data sets the value to zero.</span></span> <span data-ttu-id="21253-178">否則，值會是空的。</span><span class="sxs-lookup"><span data-stu-id="21253-178">Otherwise, the value is empty.</span></span>

<span data-ttu-id="21253-179">此 `Clear-ItemProperty` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="21253-179">The `Clear-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="21253-180">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="21253-180">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="21253-181">如需詳細資訊，請參閱 about_Providers。</span><span class="sxs-lookup"><span data-stu-id="21253-181">For more information, see about_Providers.</span></span>

## <span data-ttu-id="21253-182">相關連結</span><span class="sxs-lookup"><span data-stu-id="21253-182">RELATED LINKS</span></span>

[<span data-ttu-id="21253-183">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="21253-183">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="21253-184">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="21253-184">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="21253-185">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="21253-185">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="21253-186">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="21253-186">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="21253-187">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="21253-187">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="21253-188">about_Providers</span><span class="sxs-lookup"><span data-stu-id="21253-188">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)