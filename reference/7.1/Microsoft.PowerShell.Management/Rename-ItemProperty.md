---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-itemproperty?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-ItemProperty
ms.openlocfilehash: 4ce6bce60a3f1e87a8512b32166fb3e22f7d737e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202052"
---
# <span data-ttu-id="9c6c0-103">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c6c0-103">Rename-ItemProperty</span></span>

## <span data-ttu-id="9c6c0-104">概要</span><span class="sxs-lookup"><span data-stu-id="9c6c0-104">SYNOPSIS</span></span>
<span data-ttu-id="9c6c0-105">重新命名項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-105">Renames a property of an item.</span></span>

## <span data-ttu-id="9c6c0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9c6c0-106">SYNTAX</span></span>

### <span data-ttu-id="9c6c0-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="9c6c0-107">Path (Default)</span></span>

```
Rename-ItemProperty [-Path] <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9c6c0-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9c6c0-108">LiteralPath</span></span>

```
Rename-ItemProperty -LiteralPath <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9c6c0-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9c6c0-109">DESCRIPTION</span></span>

<span data-ttu-id="9c6c0-110">`Rename-ItemProperty`Cmdlet 會變更指定之專案屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-110">The `Rename-ItemProperty` cmdlet changes the name of a specified item property.</span></span>
<span data-ttu-id="9c6c0-111">屬性的值不會變更。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-111">The value of the property is not changed.</span></span>
<span data-ttu-id="9c6c0-112">例如，您可以使用 `Rename-ItemProperty` 來變更登錄專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-112">For example, you can use `Rename-ItemProperty` to change the name of a registry entry.</span></span>

## <span data-ttu-id="9c6c0-113">範例</span><span class="sxs-lookup"><span data-stu-id="9c6c0-113">EXAMPLES</span></span>

### <span data-ttu-id="9c6c0-114">範例 1︰重新命名登錄項目</span><span class="sxs-lookup"><span data-stu-id="9c6c0-114">Example 1: Rename a registry entry</span></span>

<span data-ttu-id="9c6c0-115">此命令會將金鑰中包含的 config 登錄專案重新命名 `HKEY_LOCAL_MACHINE\Software\SmpApplication` 為 "oldconfig"。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-115">This command renames the config registry entry that is contained in the `HKEY_LOCAL_MACHINE\Software\SmpApplication` key to "oldconfig".</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\Software\SmpApplication -Name config -NewName oldconfig
```

## <span data-ttu-id="9c6c0-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9c6c0-116">PARAMETERS</span></span>

### <span data-ttu-id="9c6c0-117">-Credential</span><span class="sxs-lookup"><span data-stu-id="9c6c0-117">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="9c6c0-118">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-118">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="9c6c0-119">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-119">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="9c6c0-120">-Exclude</span><span class="sxs-lookup"><span data-stu-id="9c6c0-120">-Exclude</span></span>

<span data-ttu-id="9c6c0-121">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-121">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="9c6c0-122">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-122">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9c6c0-123">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-123">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="9c6c0-124">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-124">Wildcard characters are permitted.</span></span> <span data-ttu-id="9c6c0-125">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-125">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="9c6c0-126">-Filter</span><span class="sxs-lookup"><span data-stu-id="9c6c0-126">-Filter</span></span>

<span data-ttu-id="9c6c0-127">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-127">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="9c6c0-128">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-128">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="9c6c0-129">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-129">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="9c6c0-130">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-130">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="9c6c0-131">-Force</span><span class="sxs-lookup"><span data-stu-id="9c6c0-131">-Force</span></span>

<span data-ttu-id="9c6c0-132">強制 Cmdlet 在使用者無法以其他方式存取的物件上重新命名屬性。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-132">Forces the cmdlet to rename a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="9c6c0-133">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-133">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="9c6c0-134">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-134">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="9c6c0-135">-Include</span><span class="sxs-lookup"><span data-stu-id="9c6c0-135">-Include</span></span>

<span data-ttu-id="9c6c0-136">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-136">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="9c6c0-137">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9c6c0-138">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-138">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="9c6c0-139">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="9c6c0-140">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-140">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="9c6c0-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9c6c0-141">-LiteralPath</span></span>

<span data-ttu-id="9c6c0-142">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-142">Specifies a path to one or more locations.</span></span> <span data-ttu-id="9c6c0-143">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-143">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="9c6c0-144">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="9c6c0-145">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="9c6c0-146">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="9c6c0-147">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-147">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9c6c0-148">-Name</span><span class="sxs-lookup"><span data-stu-id="9c6c0-148">-Name</span></span>

<span data-ttu-id="9c6c0-149">指定要重新命名之屬性的目前名稱。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-149">Specifies the current name of the property to rename.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9c6c0-150">-NewName</span><span class="sxs-lookup"><span data-stu-id="9c6c0-150">-NewName</span></span>

<span data-ttu-id="9c6c0-151">指定屬性的新名稱。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-151">Specifies the new name for the property.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9c6c0-152">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9c6c0-152">-PassThru</span></span>

<span data-ttu-id="9c6c0-153">傳回代表項目屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-153">Returns an object that represents the item property.</span></span>
<span data-ttu-id="9c6c0-154">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-154">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="9c6c0-155">-Path</span><span class="sxs-lookup"><span data-stu-id="9c6c0-155">-Path</span></span>

<span data-ttu-id="9c6c0-156">指定要重新命名之項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-156">Specifies the path of the item to rename.</span></span>
<span data-ttu-id="9c6c0-157">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-157">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="9c6c0-158">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9c6c0-158">-Confirm</span></span>

<span data-ttu-id="9c6c0-159">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-159">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9c6c0-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9c6c0-160">-WhatIf</span></span>

<span data-ttu-id="9c6c0-161">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-161">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9c6c0-162">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-162">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9c6c0-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9c6c0-163">CommonParameters</span></span>

<span data-ttu-id="9c6c0-164">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-164">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="9c6c0-165">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-165">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9c6c0-166">輸入</span><span class="sxs-lookup"><span data-stu-id="9c6c0-166">INPUTS</span></span>

### <span data-ttu-id="9c6c0-167">System.String</span><span class="sxs-lookup"><span data-stu-id="9c6c0-167">System.String</span></span>

<span data-ttu-id="9c6c0-168">您可以使用管線將包含路徑 (但不是常值路徑) 的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-168">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="9c6c0-169">輸出</span><span class="sxs-lookup"><span data-stu-id="9c6c0-169">OUTPUTS</span></span>

### <span data-ttu-id="9c6c0-170">None，System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="9c6c0-170">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="9c6c0-171">如果您指定 **PassThru** 參數，這個 Cmdlet 會產生代表重新命名之項目屬性的 **PSCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-171">This cmdlet generates a **PSCustomObject** that represents the renamed item property, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="9c6c0-172">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-172">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9c6c0-173">注意</span><span class="sxs-lookup"><span data-stu-id="9c6c0-173">NOTES</span></span>

<span data-ttu-id="9c6c0-174">`Remove-ItemProperty` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-174">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="9c6c0-175">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="9c6c0-176">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="9c6c0-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="9c6c0-177">相關連結</span><span class="sxs-lookup"><span data-stu-id="9c6c0-177">RELATED LINKS</span></span>

[<span data-ttu-id="9c6c0-178">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c6c0-178">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="9c6c0-179">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c6c0-179">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="9c6c0-180">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c6c0-180">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="9c6c0-181">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c6c0-181">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="9c6c0-182">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c6c0-182">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="9c6c0-183">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c6c0-183">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="9c6c0-184">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="9c6c0-184">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="9c6c0-185">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c6c0-185">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="9c6c0-186">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9c6c0-186">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

