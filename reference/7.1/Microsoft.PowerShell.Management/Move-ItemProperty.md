---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-itemproperty?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-ItemProperty
ms.openlocfilehash: e3c1d1641c6f4b30b17c9f0f6703cd063663f25b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202087"
---
# <span data-ttu-id="b3238-103">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b3238-103">Move-ItemProperty</span></span>

## <span data-ttu-id="b3238-104">概要</span><span class="sxs-lookup"><span data-stu-id="b3238-104">Synopsis</span></span>
<span data-ttu-id="b3238-105">將屬性從某個位置移動到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="b3238-105">Moves a property from one location to another.</span></span>

## <span data-ttu-id="b3238-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b3238-106">SYNTAX</span></span>

### <span data-ttu-id="b3238-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="b3238-107">Path (Default)</span></span>

```
Move-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b3238-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b3238-108">LiteralPath</span></span>

```
Move-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b3238-109">Description</span><span class="sxs-lookup"><span data-stu-id="b3238-109">Description</span></span>

<span data-ttu-id="b3238-110">`Move-ItemProperty`Cmdlet 會將專案的屬性從某個專案移到另一個專案。</span><span class="sxs-lookup"><span data-stu-id="b3238-110">The `Move-ItemProperty` cmdlet moves a property of an item from one item to another item.</span></span>
<span data-ttu-id="b3238-111">例如，它可以將登錄專案從一個登錄機碼移至另一個登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="b3238-111">For instance, it can move a registry entry from one registry key to another registry key.</span></span>
<span data-ttu-id="b3238-112">當您移動項目屬性後，就會將它加到新位置，並從其原始位置中刪除。</span><span class="sxs-lookup"><span data-stu-id="b3238-112">When you move an item property, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="b3238-113">範例</span><span class="sxs-lookup"><span data-stu-id="b3238-113">EXAMPLES</span></span>

### <span data-ttu-id="b3238-114">範例1：將登錄值和其資料移至另一個金鑰</span><span class="sxs-lookup"><span data-stu-id="b3238-114">Example 1: Move a registry value and its data to another key</span></span>

<span data-ttu-id="b3238-115">此命令會將 Version 登錄值和其資料從 "MyApp" 子機碼移至登錄機碼的 NewApp 子機 `HKLM\Software\MyCompany` 碼。</span><span class="sxs-lookup"><span data-stu-id="b3238-115">This command moves the Version registry value, and its data, from the "MyApp" subkey to the NewApp subkey of the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Move-ItemProperty "HKLM:\Software\MyCompany\MyApp" -Name "Version" -Destination "HKLM:\Software\MyCompany\NewApp"
```

## <span data-ttu-id="b3238-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b3238-116">PARAMETERS</span></span>

### <span data-ttu-id="b3238-117">-Credential</span><span class="sxs-lookup"><span data-stu-id="b3238-117">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="b3238-118">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="b3238-118">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="b3238-119">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="b3238-119">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="b3238-120">-Destination</span><span class="sxs-lookup"><span data-stu-id="b3238-120">-Destination</span></span>

<span data-ttu-id="b3238-121">指定目的地位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="b3238-121">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="b3238-122">-Exclude</span><span class="sxs-lookup"><span data-stu-id="b3238-122">-Exclude</span></span>

<span data-ttu-id="b3238-123">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="b3238-123">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="b3238-124">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="b3238-124">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b3238-125">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="b3238-125">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="b3238-126">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b3238-126">Wildcard characters are permitted.</span></span> <span data-ttu-id="b3238-127">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="b3238-127">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="b3238-128">-Filter</span><span class="sxs-lookup"><span data-stu-id="b3238-128">-Filter</span></span>

<span data-ttu-id="b3238-129">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="b3238-129">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="b3238-130">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="b3238-130">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="b3238-131">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="b3238-131">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="b3238-132">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="b3238-132">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="b3238-133">-Force</span><span class="sxs-lookup"><span data-stu-id="b3238-133">-Force</span></span>

<span data-ttu-id="b3238-134">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="b3238-134">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="b3238-135">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="b3238-135">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="b3238-136">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="b3238-136">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="b3238-137">-Include</span><span class="sxs-lookup"><span data-stu-id="b3238-137">-Include</span></span>

<span data-ttu-id="b3238-138">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="b3238-138">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="b3238-139">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="b3238-139">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b3238-140">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="b3238-140">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="b3238-141">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b3238-141">Wildcard characters are permitted.</span></span> <span data-ttu-id="b3238-142">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="b3238-142">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="b3238-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b3238-143">-LiteralPath</span></span>

<span data-ttu-id="b3238-144">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="b3238-144">Specifies a path to one or more locations.</span></span> <span data-ttu-id="b3238-145">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="b3238-145">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="b3238-146">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b3238-146">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b3238-147">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="b3238-147">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b3238-148">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="b3238-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="b3238-149">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="b3238-149">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="b3238-150">-Name</span><span class="sxs-lookup"><span data-stu-id="b3238-150">-Name</span></span>

<span data-ttu-id="b3238-151">指定要移動之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="b3238-151">Specifies the name of the property to be moved.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b3238-152">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b3238-152">-PassThru</span></span>

<span data-ttu-id="b3238-153">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="b3238-153">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="b3238-154">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="b3238-154">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="b3238-155">-Path</span><span class="sxs-lookup"><span data-stu-id="b3238-155">-Path</span></span>

<span data-ttu-id="b3238-156">指定屬性之目前位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="b3238-156">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="b3238-157">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b3238-157">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="b3238-158">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b3238-158">-Confirm</span></span>

<span data-ttu-id="b3238-159">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="b3238-159">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b3238-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b3238-160">-WhatIf</span></span>

<span data-ttu-id="b3238-161">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="b3238-161">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b3238-162">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="b3238-162">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b3238-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b3238-163">CommonParameters</span></span>

<span data-ttu-id="b3238-164">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="b3238-164">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="b3238-165">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b3238-165">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b3238-166">輸入</span><span class="sxs-lookup"><span data-stu-id="b3238-166">INPUTS</span></span>

### <span data-ttu-id="b3238-167">System.String</span><span class="sxs-lookup"><span data-stu-id="b3238-167">System.String</span></span>

<span data-ttu-id="b3238-168">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b3238-168">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="b3238-169">輸出</span><span class="sxs-lookup"><span data-stu-id="b3238-169">OUTPUTS</span></span>

### <span data-ttu-id="b3238-170">無或 System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="b3238-170">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="b3238-171">當您使用 **PassThru** 參數時，此 Cmdlet 會產生代表已移動之專案屬性的 **PSCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="b3238-171">When you use the **PassThru** parameter, this cmdlet generates a **PSCustomObject** representing the moved item property.</span></span> <span data-ttu-id="b3238-172">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="b3238-172">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b3238-173">注意</span><span class="sxs-lookup"><span data-stu-id="b3238-173">NOTES</span></span>

<span data-ttu-id="b3238-174">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="b3238-174">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="b3238-175">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="b3238-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="b3238-176">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="b3238-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="b3238-177">相關連結</span><span class="sxs-lookup"><span data-stu-id="b3238-177">RELATED LINKS</span></span>

[<span data-ttu-id="b3238-178">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b3238-178">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="b3238-179">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b3238-179">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="b3238-180">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b3238-180">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="b3238-181">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b3238-181">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="b3238-182">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b3238-182">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="b3238-183">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b3238-183">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="b3238-184">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b3238-184">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="b3238-185">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b3238-185">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

