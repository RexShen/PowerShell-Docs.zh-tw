---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-ItemProperty
ms.openlocfilehash: 5cbd228f78da3bf7fa70a001391bc98f63085a73
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203552"
---
# <span data-ttu-id="58a84-103">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="58a84-103">Rename-ItemProperty</span></span>

## <span data-ttu-id="58a84-104">概要</span><span class="sxs-lookup"><span data-stu-id="58a84-104">SYNOPSIS</span></span>
<span data-ttu-id="58a84-105">重新命名項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="58a84-105">Renames a property of an item.</span></span>

## <span data-ttu-id="58a84-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="58a84-106">SYNTAX</span></span>

### <span data-ttu-id="58a84-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="58a84-107">Path (Default)</span></span>

```
Rename-ItemProperty [-Path] <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="58a84-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="58a84-108">LiteralPath</span></span>

```
Rename-ItemProperty -LiteralPath <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="58a84-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="58a84-109">DESCRIPTION</span></span>

<span data-ttu-id="58a84-110">`Rename-ItemProperty`Cmdlet 會變更指定之專案屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="58a84-110">The `Rename-ItemProperty` cmdlet changes the name of a specified item property.</span></span>
<span data-ttu-id="58a84-111">屬性的值不會變更。</span><span class="sxs-lookup"><span data-stu-id="58a84-111">The value of the property is not changed.</span></span>
<span data-ttu-id="58a84-112">例如，您可以使用 `Rename-ItemProperty` 來變更登錄專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="58a84-112">For example, you can use `Rename-ItemProperty` to change the name of a registry entry.</span></span>

## <span data-ttu-id="58a84-113">範例</span><span class="sxs-lookup"><span data-stu-id="58a84-113">EXAMPLES</span></span>

### <span data-ttu-id="58a84-114">範例 1︰重新命名登錄項目</span><span class="sxs-lookup"><span data-stu-id="58a84-114">Example 1: Rename a registry entry</span></span>

<span data-ttu-id="58a84-115">此命令會將 "HKEY_LOCAL_MACHINE\Software\SmpApplication" 機碼中包含的 config 登錄專案重新命名為 "oldconfig"。</span><span class="sxs-lookup"><span data-stu-id="58a84-115">This command renames the config registry entry that is contained in the "HKEY_LOCAL_MACHINE\Software\SmpApplication" key to "oldconfig".</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\Software\SmpApplication -Name config -NewName oldconfig
```

## <span data-ttu-id="58a84-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="58a84-116">PARAMETERS</span></span>

### <span data-ttu-id="58a84-117">-Credential</span><span class="sxs-lookup"><span data-stu-id="58a84-117">-Credential</span></span>

<span data-ttu-id="58a84-118">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="58a84-118">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="58a84-119">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="58a84-119">The default is the current user.</span></span>

<span data-ttu-id="58a84-120">輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="58a84-120">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="58a84-121">若您輸入使用者名稱時，會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="58a84-121">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="58a84-122">與 Windows PowerShell 一起安裝的任何提供者皆不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="58a84-122">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

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

### <span data-ttu-id="58a84-123">-Exclude</span><span class="sxs-lookup"><span data-stu-id="58a84-123">-Exclude</span></span>

<span data-ttu-id="58a84-124">指定此 Cmdlet 省略的項目。</span><span class="sxs-lookup"><span data-stu-id="58a84-124">Specifies items that this cmdlet omits.</span></span>
<span data-ttu-id="58a84-125">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="58a84-125">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="58a84-126">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="58a84-126">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="58a84-127">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="58a84-127">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="58a84-128">-Filter</span><span class="sxs-lookup"><span data-stu-id="58a84-128">-Filter</span></span>

<span data-ttu-id="58a84-129">以提供者的格式或語言指定篩選。</span><span class="sxs-lookup"><span data-stu-id="58a84-129">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="58a84-130">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="58a84-130">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="58a84-131">篩選的語法 (包括是否使用萬用字元) 取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="58a84-131">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="58a84-132">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="58a84-132">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="58a84-133">-Force</span><span class="sxs-lookup"><span data-stu-id="58a84-133">-Force</span></span>

<span data-ttu-id="58a84-134">強制 Cmdlet 在使用者無法以其他方式存取的物件上重新命名屬性。</span><span class="sxs-lookup"><span data-stu-id="58a84-134">Forces the cmdlet to rename a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="58a84-135">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="58a84-135">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="58a84-136">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="58a84-136">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="58a84-137">-Include</span><span class="sxs-lookup"><span data-stu-id="58a84-137">-Include</span></span>

<span data-ttu-id="58a84-138">僅指定 Cmdlet 會在其中作用的項目，不包含其他所有項目。</span><span class="sxs-lookup"><span data-stu-id="58a84-138">Specifies only those items upon which the cmdlet acts, excluding all others.</span></span>
<span data-ttu-id="58a84-139">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="58a84-139">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="58a84-140">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="58a84-140">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="58a84-141">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="58a84-141">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="58a84-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="58a84-142">-LiteralPath</span></span>

<span data-ttu-id="58a84-143">指定項目屬性的路徑。</span><span class="sxs-lookup"><span data-stu-id="58a84-143">Specifies a path of the item property.</span></span>
<span data-ttu-id="58a84-144">與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="58a84-144">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="58a84-145">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="58a84-145">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="58a84-146">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="58a84-146">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="58a84-147">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="58a84-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="58a84-148">-Name</span><span class="sxs-lookup"><span data-stu-id="58a84-148">-Name</span></span>

<span data-ttu-id="58a84-149">指定要重新命名之屬性的目前名稱。</span><span class="sxs-lookup"><span data-stu-id="58a84-149">Specifies the current name of the property to rename.</span></span>

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

### <span data-ttu-id="58a84-150">-NewName</span><span class="sxs-lookup"><span data-stu-id="58a84-150">-NewName</span></span>

<span data-ttu-id="58a84-151">指定屬性的新名稱。</span><span class="sxs-lookup"><span data-stu-id="58a84-151">Specifies the new name for the property.</span></span>

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

### <span data-ttu-id="58a84-152">-PassThru</span><span class="sxs-lookup"><span data-stu-id="58a84-152">-PassThru</span></span>

<span data-ttu-id="58a84-153">傳回代表項目屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="58a84-153">Returns an object that represents the item property.</span></span>
<span data-ttu-id="58a84-154">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="58a84-154">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="58a84-155">-Path</span><span class="sxs-lookup"><span data-stu-id="58a84-155">-Path</span></span>

<span data-ttu-id="58a84-156">指定要重新命名之項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="58a84-156">Specifies the path of the item to rename.</span></span>

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

### <span data-ttu-id="58a84-157">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="58a84-157">-UseTransaction</span></span>

<span data-ttu-id="58a84-158">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="58a84-158">Includes the command in the active transaction.</span></span>
<span data-ttu-id="58a84-159">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="58a84-159">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="58a84-160">如需詳細資訊，請參閱 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="58a84-160">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="58a84-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="58a84-161">-Confirm</span></span>

<span data-ttu-id="58a84-162">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="58a84-162">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="58a84-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="58a84-163">-WhatIf</span></span>

<span data-ttu-id="58a84-164">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="58a84-164">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="58a84-165">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="58a84-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="58a84-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="58a84-166">CommonParameters</span></span>

<span data-ttu-id="58a84-167">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="58a84-167">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="58a84-168">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="58a84-168">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="58a84-169">輸入</span><span class="sxs-lookup"><span data-stu-id="58a84-169">INPUTS</span></span>

### <span data-ttu-id="58a84-170">System.String</span><span class="sxs-lookup"><span data-stu-id="58a84-170">System.String</span></span>

<span data-ttu-id="58a84-171">您可以使用管線將包含路徑 (但不是常值路徑) 的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="58a84-171">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="58a84-172">輸出</span><span class="sxs-lookup"><span data-stu-id="58a84-172">OUTPUTS</span></span>

### <span data-ttu-id="58a84-173">None，System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="58a84-173">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="58a84-174">如果您指定 *PassThru* 參數，這個 Cmdlet 會產生代表重新命名之項目屬性的 **PSCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="58a84-174">This cmdlet generates a **PSCustomObject** that represents the renamed item property, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="58a84-175">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="58a84-175">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="58a84-176">注意</span><span class="sxs-lookup"><span data-stu-id="58a84-176">NOTES</span></span>

<span data-ttu-id="58a84-177">`Remove-ItemProperty` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="58a84-177">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="58a84-178">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="58a84-178">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="58a84-179">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="58a84-179">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="58a84-180">相關連結</span><span class="sxs-lookup"><span data-stu-id="58a84-180">RELATED LINKS</span></span>

[<span data-ttu-id="58a84-181">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="58a84-181">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="58a84-182">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="58a84-182">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="58a84-183">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="58a84-183">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="58a84-184">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="58a84-184">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="58a84-185">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="58a84-185">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="58a84-186">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="58a84-186">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="58a84-187">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="58a84-187">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="58a84-188">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="58a84-188">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="58a84-189">about_Providers</span><span class="sxs-lookup"><span data-stu-id="58a84-189">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)