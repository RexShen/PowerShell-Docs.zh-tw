---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-ItemProperty
ms.openlocfilehash: 4cf883964e1ff86487bf5abca8789af62b274c8a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203599"
---
# <span data-ttu-id="b1367-103">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b1367-103">Move-ItemProperty</span></span>

## <span data-ttu-id="b1367-104">概要</span><span class="sxs-lookup"><span data-stu-id="b1367-104">Synopsis</span></span>
<span data-ttu-id="b1367-105">將屬性從某個位置移動到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="b1367-105">Moves a property from one location to another.</span></span>

## <span data-ttu-id="b1367-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b1367-106">SYNTAX</span></span>

### <span data-ttu-id="b1367-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="b1367-107">Path (Default)</span></span>

```
Move-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="b1367-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b1367-108">LiteralPath</span></span>

```
Move-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="b1367-109">Description</span><span class="sxs-lookup"><span data-stu-id="b1367-109">Description</span></span>

<span data-ttu-id="b1367-110">`Move-ItemProperty`Cmdlet 會將專案的屬性從某個專案移到另一個專案。</span><span class="sxs-lookup"><span data-stu-id="b1367-110">The `Move-ItemProperty` cmdlet moves a property of an item from one item to another item.</span></span>
<span data-ttu-id="b1367-111">例如，它可以將登錄專案從一個登錄機碼移至另一個登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="b1367-111">For instance, it can move a registry entry from one registry key to another registry key.</span></span>
<span data-ttu-id="b1367-112">當您移動項目屬性後，就會將它加到新位置，並從其原始位置中刪除。</span><span class="sxs-lookup"><span data-stu-id="b1367-112">When you move an item property, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="b1367-113">範例</span><span class="sxs-lookup"><span data-stu-id="b1367-113">EXAMPLES</span></span>

### <span data-ttu-id="b1367-114">範例1：將登錄值和其資料移至另一個金鑰</span><span class="sxs-lookup"><span data-stu-id="b1367-114">Example 1: Move a registry value and its data to another key</span></span>

<span data-ttu-id="b1367-115">此命令會將 Version 登錄值和其資料從 "MyApp" 子機碼移至登錄機碼的 NewApp 子機 `HKLM\Software\MyCompany` 碼。</span><span class="sxs-lookup"><span data-stu-id="b1367-115">This command moves the Version registry value, and its data, from the "MyApp" subkey to the NewApp subkey of the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Move-ItemProperty "HKLM:\Software\MyCompany\MyApp" -Name "Version" -Destination "HKLM:\Software\MyCompany\NewApp"
```

## <span data-ttu-id="b1367-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b1367-116">PARAMETERS</span></span>

### <span data-ttu-id="b1367-117">-Credential</span><span class="sxs-lookup"><span data-stu-id="b1367-117">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="b1367-118">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="b1367-118">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="b1367-119">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="b1367-119">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="b1367-120">-Destination</span><span class="sxs-lookup"><span data-stu-id="b1367-120">-Destination</span></span>

<span data-ttu-id="b1367-121">指定目的地位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="b1367-121">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="b1367-122">-Exclude</span><span class="sxs-lookup"><span data-stu-id="b1367-122">-Exclude</span></span>

<span data-ttu-id="b1367-123">以字串陣列指定此 Cmdlet 從作業中排除的屬性或屬性。</span><span class="sxs-lookup"><span data-stu-id="b1367-123">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="b1367-124">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="b1367-124">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="b1367-125">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="b1367-125">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="b1367-126">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b1367-126">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="b1367-127">-Filter</span><span class="sxs-lookup"><span data-stu-id="b1367-127">-Filter</span></span>

<span data-ttu-id="b1367-128">以提供者的格式或語言指定篩選。</span><span class="sxs-lookup"><span data-stu-id="b1367-128">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="b1367-129">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="b1367-129">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="b1367-130">篩選的語法 (包括是否使用萬用字元) 取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="b1367-130">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="b1367-131">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="b1367-131">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="b1367-132">-Force</span><span class="sxs-lookup"><span data-stu-id="b1367-132">-Force</span></span>

<span data-ttu-id="b1367-133">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="b1367-133">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="b1367-134">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="b1367-134">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="b1367-135">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="b1367-135">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="b1367-136">-Include</span><span class="sxs-lookup"><span data-stu-id="b1367-136">-Include</span></span>

<span data-ttu-id="b1367-137">以字串陣列指定此 Cmdlet 在作業中包含的屬性或屬性。</span><span class="sxs-lookup"><span data-stu-id="b1367-137">Specifies, as a string array, a property or property that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="b1367-138">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="b1367-138">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="b1367-139">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="b1367-139">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="b1367-140">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b1367-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="b1367-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b1367-141">-LiteralPath</span></span>

<span data-ttu-id="b1367-142">指定屬性之目前位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="b1367-142">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="b1367-143">與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="b1367-143">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="b1367-144">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b1367-144">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="b1367-145">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="b1367-145">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="b1367-146">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="b1367-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="b1367-147">-Name</span><span class="sxs-lookup"><span data-stu-id="b1367-147">-Name</span></span>

<span data-ttu-id="b1367-148">指定要移動之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1367-148">Specifies the name of the property to be moved.</span></span>

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

### <span data-ttu-id="b1367-149">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b1367-149">-PassThru</span></span>

<span data-ttu-id="b1367-150">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="b1367-150">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="b1367-151">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="b1367-151">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="b1367-152">-Path</span><span class="sxs-lookup"><span data-stu-id="b1367-152">-Path</span></span>

<span data-ttu-id="b1367-153">指定屬性之目前位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="b1367-153">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="b1367-154">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b1367-154">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="b1367-155">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="b1367-155">-UseTransaction</span></span>

<span data-ttu-id="b1367-156">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="b1367-156">Includes the command in the active transaction.</span></span>
<span data-ttu-id="b1367-157">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="b1367-157">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="b1367-158">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="b1367-158">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="b1367-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b1367-159">-Confirm</span></span>

<span data-ttu-id="b1367-160">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="b1367-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b1367-161">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b1367-161">-WhatIf</span></span>

<span data-ttu-id="b1367-162">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="b1367-162">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b1367-163">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="b1367-163">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b1367-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b1367-164">CommonParameters</span></span>

<span data-ttu-id="b1367-165">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="b1367-165">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="b1367-166">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b1367-166">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b1367-167">輸入</span><span class="sxs-lookup"><span data-stu-id="b1367-167">INPUTS</span></span>

### <span data-ttu-id="b1367-168">System.String</span><span class="sxs-lookup"><span data-stu-id="b1367-168">System.String</span></span>

<span data-ttu-id="b1367-169">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b1367-169">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="b1367-170">輸出</span><span class="sxs-lookup"><span data-stu-id="b1367-170">OUTPUTS</span></span>

### <span data-ttu-id="b1367-171">無或 System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="b1367-171">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="b1367-172">當您使用 **PassThru** 參數時，此 Cmdlet 會產生代表已移動之專案屬性的 **PSCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="b1367-172">When you use the **PassThru** parameter, this cmdlet generates a **PSCustomObject** representing the moved item property.</span></span>
<span data-ttu-id="b1367-173">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="b1367-173">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b1367-174">注意</span><span class="sxs-lookup"><span data-stu-id="b1367-174">NOTES</span></span>

<span data-ttu-id="b1367-175">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="b1367-175">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="b1367-176">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="b1367-176">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="b1367-177">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="b1367-177">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="b1367-178">相關連結</span><span class="sxs-lookup"><span data-stu-id="b1367-178">RELATED LINKS</span></span>

[<span data-ttu-id="b1367-179">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b1367-179">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="b1367-180">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b1367-180">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="b1367-181">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b1367-181">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="b1367-182">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b1367-182">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="b1367-183">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b1367-183">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="b1367-184">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b1367-184">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="b1367-185">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b1367-185">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="b1367-186">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b1367-186">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
