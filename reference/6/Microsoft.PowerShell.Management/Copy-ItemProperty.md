---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-ItemProperty
ms.openlocfilehash: debfe25e8ab977e1f994a94430988254ce5da5d0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202564"
---
# <span data-ttu-id="f97ca-103">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f97ca-103">Copy-ItemProperty</span></span>

## <span data-ttu-id="f97ca-104">概要</span><span class="sxs-lookup"><span data-stu-id="f97ca-104">SYNOPSIS</span></span>
<span data-ttu-id="f97ca-105">從指定的位置將屬性和值複製到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="f97ca-105">Copies a property and value from a specified location to another location.</span></span>

## <span data-ttu-id="f97ca-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f97ca-106">SYNTAX</span></span>

### <span data-ttu-id="f97ca-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="f97ca-107">Path (Default)</span></span>

```
Copy-ItemProperty [-Path] <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f97ca-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f97ca-108">LiteralPath</span></span>

```
Copy-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f97ca-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f97ca-109">DESCRIPTION</span></span>

<span data-ttu-id="f97ca-110">`Copy-ItemProperty`Cmdlet 會從指定的位置將屬性和值複製到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="f97ca-110">The `Copy-ItemProperty` cmdlet copies a property and value from a specified location to another location.</span></span>
<span data-ttu-id="f97ca-111">例如，您可以使用這個指令程式，將一個或多個登錄專案從某個登錄機碼複製到另一個登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="f97ca-111">For instance, you can use this cmdlet to copy one or more registry entries from one registry key to another registry key.</span></span>

## <span data-ttu-id="f97ca-112">範例</span><span class="sxs-lookup"><span data-stu-id="f97ca-112">EXAMPLES</span></span>

### <span data-ttu-id="f97ca-113">範例1：將屬性從登錄機碼複製到另一個登錄機碼</span><span class="sxs-lookup"><span data-stu-id="f97ca-113">Example 1: Copy a property from a registry key to another registry key</span></span>

<span data-ttu-id="f97ca-114">此命令會將名為 "MyProperty" 的屬性從 "MyApplication" 登錄機碼複製到 "MyApplicationRev2" 登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="f97ca-114">This command copies the property named "MyProperty" from the "MyApplication" registry key to the "MyApplicationRev2" registry key.</span></span>

```powershell
Copy-ItemProperty -Path "MyApplication" -Destination "HKLM:\Software\MyApplicationRev2" -Name "MyProperty"
```

## <span data-ttu-id="f97ca-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f97ca-115">PARAMETERS</span></span>

### <span data-ttu-id="f97ca-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="f97ca-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="f97ca-117">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="f97ca-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="f97ca-118">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="f97ca-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="f97ca-119">-Destination</span><span class="sxs-lookup"><span data-stu-id="f97ca-119">-Destination</span></span>

<span data-ttu-id="f97ca-120">指定目的地位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="f97ca-120">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="f97ca-121">-Exclude</span><span class="sxs-lookup"><span data-stu-id="f97ca-121">-Exclude</span></span>

<span data-ttu-id="f97ca-122">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="f97ca-122">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="f97ca-123">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="f97ca-123">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f97ca-124">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="f97ca-124">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="f97ca-125">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f97ca-125">Wildcard characters are permitted.</span></span> <span data-ttu-id="f97ca-126">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="f97ca-126">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="f97ca-127">-Filter</span><span class="sxs-lookup"><span data-stu-id="f97ca-127">-Filter</span></span>

<span data-ttu-id="f97ca-128">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="f97ca-128">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="f97ca-129">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="f97ca-129">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="f97ca-130">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="f97ca-130">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="f97ca-131">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="f97ca-131">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="f97ca-132">-Force</span><span class="sxs-lookup"><span data-stu-id="f97ca-132">-Force</span></span>

<span data-ttu-id="f97ca-133">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="f97ca-133">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="f97ca-134">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="f97ca-134">Implementation varies from provider to provider.</span></span>

<span data-ttu-id="f97ca-135">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="f97ca-135">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="f97ca-136">-Include</span><span class="sxs-lookup"><span data-stu-id="f97ca-136">-Include</span></span>

<span data-ttu-id="f97ca-137">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="f97ca-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="f97ca-138">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="f97ca-138">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f97ca-139">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="f97ca-139">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="f97ca-140">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f97ca-140">Wildcard characters are permitted.</span></span> <span data-ttu-id="f97ca-141">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="f97ca-141">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="f97ca-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f97ca-142">-LiteralPath</span></span>

<span data-ttu-id="f97ca-143">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="f97ca-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="f97ca-144">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="f97ca-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="f97ca-145">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f97ca-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="f97ca-146">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="f97ca-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="f97ca-147">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="f97ca-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="f97ca-148">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="f97ca-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f97ca-149">-Name</span><span class="sxs-lookup"><span data-stu-id="f97ca-149">-Name</span></span>

<span data-ttu-id="f97ca-150">指定要複製之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="f97ca-150">Specifies the name of the property to be copied.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f97ca-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f97ca-151">-PassThru</span></span>

<span data-ttu-id="f97ca-152">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="f97ca-152">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="f97ca-153">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f97ca-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f97ca-154">-Path</span><span class="sxs-lookup"><span data-stu-id="f97ca-154">-Path</span></span>

<span data-ttu-id="f97ca-155">以字串陣列指定要複製之屬性的路徑。</span><span class="sxs-lookup"><span data-stu-id="f97ca-155">Specifies, as a string array, the path to the property to be copied.</span></span>
<span data-ttu-id="f97ca-156">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f97ca-156">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="f97ca-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f97ca-157">-Confirm</span></span>

<span data-ttu-id="f97ca-158">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f97ca-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f97ca-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f97ca-159">-WhatIf</span></span>

<span data-ttu-id="f97ca-160">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f97ca-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f97ca-161">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="f97ca-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f97ca-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f97ca-162">CommonParameters</span></span>

<span data-ttu-id="f97ca-163">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="f97ca-163">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="f97ca-164">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="f97ca-164">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f97ca-165">輸入</span><span class="sxs-lookup"><span data-stu-id="f97ca-165">INPUTS</span></span>

### <span data-ttu-id="f97ca-166">System.String</span><span class="sxs-lookup"><span data-stu-id="f97ca-166">System.String</span></span>

<span data-ttu-id="f97ca-167">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f97ca-167">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="f97ca-168">輸出</span><span class="sxs-lookup"><span data-stu-id="f97ca-168">OUTPUTS</span></span>

### <span data-ttu-id="f97ca-169">無或 System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="f97ca-169">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="f97ca-170">當您使用 **Passthru** 參數時，此 Cmdlet 會產生代表所複製之專案屬性的 **PsCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="f97ca-170">When you use the **Passthru** parameter, this cmdlet generates a **PsCustomObject** representing the copied item property.</span></span> <span data-ttu-id="f97ca-171">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f97ca-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f97ca-172">注意</span><span class="sxs-lookup"><span data-stu-id="f97ca-172">NOTES</span></span>

<span data-ttu-id="f97ca-173">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="f97ca-173">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="f97ca-174">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="f97ca-174">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="f97ca-175">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="f97ca-175">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="f97ca-176">相關連結</span><span class="sxs-lookup"><span data-stu-id="f97ca-176">RELATED LINKS</span></span>

[<span data-ttu-id="f97ca-177">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f97ca-177">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="f97ca-178">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f97ca-178">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="f97ca-179">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f97ca-179">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="f97ca-180">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f97ca-180">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="f97ca-181">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f97ca-181">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="f97ca-182">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f97ca-182">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="f97ca-183">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="f97ca-183">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="f97ca-184">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f97ca-184">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
