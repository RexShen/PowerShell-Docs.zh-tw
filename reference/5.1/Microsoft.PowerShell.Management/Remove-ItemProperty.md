---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 9ae9c0e7c17a6a63da5487cce138ddce129b975b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203560"
---
# <span data-ttu-id="bae5e-103">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae5e-103">Remove-ItemProperty</span></span>

## <span data-ttu-id="bae5e-104">概要</span><span class="sxs-lookup"><span data-stu-id="bae5e-104">SYNOPSIS</span></span>
<span data-ttu-id="bae5e-105">刪除項目的屬性及其值。</span><span class="sxs-lookup"><span data-stu-id="bae5e-105">Deletes the property and its value from an item.</span></span>

## <span data-ttu-id="bae5e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bae5e-106">SYNTAX</span></span>

### <span data-ttu-id="bae5e-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="bae5e-107">Path (Default)</span></span>

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="bae5e-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="bae5e-108">LiteralPath</span></span>

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="bae5e-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bae5e-109">DESCRIPTION</span></span>

<span data-ttu-id="bae5e-110">`Remove-ItemProperty`Cmdlet 會從專案中刪除屬性和其值。</span><span class="sxs-lookup"><span data-stu-id="bae5e-110">The `Remove-ItemProperty` cmdlet deletes a property and its value from an item.</span></span>
<span data-ttu-id="bae5e-111">您可以使用它來刪除登錄值和它們所儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="bae5e-111">You can use it to delete registry values and the data that they store.</span></span>

## <span data-ttu-id="bae5e-112">範例</span><span class="sxs-lookup"><span data-stu-id="bae5e-112">EXAMPLES</span></span>

### <span data-ttu-id="bae5e-113">範例 1：刪除登錄值</span><span class="sxs-lookup"><span data-stu-id="bae5e-113">Example 1: Delete a registry value</span></span>

<span data-ttu-id="bae5e-114">此命令會從 "HKEY_LOCAL_MACHINE\Software" 登錄機碼的 "SmpApplication" 子機碼中刪除 "SmpProperty" 登錄值及其資料。</span><span class="sxs-lookup"><span data-stu-id="bae5e-114">This command deletes the "SmpProperty" registry value, and its data, from the "SmpApplication" subkey of the "HKEY_LOCAL_MACHINE\Software" registry key.</span></span>

<span data-ttu-id="bae5e-115">因為命令是從檔案系統磁片磁碟機 () 發出 `PS C:\>` ，所以它會包含 "SmpApplication" 子機碼的完整路徑，包括磁片磁碟機、 `HKLM:` 和 "Software" 機碼。</span><span class="sxs-lookup"><span data-stu-id="bae5e-115">Because the command is issued from a file system drive (`PS C:\>`), it includes the fully qualified path of the "SmpApplication" subkey, including the drive, `HKLM:`, and the "Software" key.</span></span>

<span data-ttu-id="bae5e-116">它會使用 **Name** 參數來識別要刪除的登錄值。</span><span class="sxs-lookup"><span data-stu-id="bae5e-116">It uses the **Name** parameter to identify the registry value that is being deleted.</span></span>

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

### <span data-ttu-id="bae5e-117">範例 2︰從 HKCU 位置刪除登錄值</span><span class="sxs-lookup"><span data-stu-id="bae5e-117">Example 2: Delete a registry value from the HKCU location</span></span>

<span data-ttu-id="bae5e-118">這些命令會從 "HKEY_CURRENT_USER\Software\MyCompany" 的 "MyApp" 子機碼中刪除 "Options" 登錄值及其資料。</span><span class="sxs-lookup"><span data-stu-id="bae5e-118">These commands delete the "Options" registry value, and its data, from the "MyApp" subkey of "HKEY_CURRENT_USER\Software\MyCompany".</span></span>

<span data-ttu-id="bae5e-119">第一個命令會使用 `Set-Location` Cmdlet 將目前的位置變更為 **HKEY_CURRENT_USER** 磁片磁碟機 (`HKCU:`) 和 "Software\MyCompany\MyApp" 子機碼。</span><span class="sxs-lookup"><span data-stu-id="bae5e-119">The first command uses the `Set-Location` cmdlet to change the current location to the **HKEY_CURRENT_USER** drive (`HKCU:`) and the "Software\MyCompany\MyApp" subkey.</span></span>

<span data-ttu-id="bae5e-120">第二個命令會使用 `Remove-ItemProperty` 從 "MyApp" 子機碼移除 "Options" 登錄值及其資料。</span><span class="sxs-lookup"><span data-stu-id="bae5e-120">The second command uses `Remove-ItemProperty` to remove the "Options" registry value, and its data, from the "MyApp" subkey.</span></span>
<span data-ttu-id="bae5e-121">因為 **路徑** 是必要的，所以命令會使用點 ( '. ') ，表示目前的位置。</span><span class="sxs-lookup"><span data-stu-id="bae5e-121">Because **Path** is required, the command uses a dot ('.') to indicate the current location.</span></span>
<span data-ttu-id="bae5e-122">它會使用 **Name** 來指定要刪除的登錄值。</span><span class="sxs-lookup"><span data-stu-id="bae5e-122">It uses **Name** to specify which registry value to delete.</span></span>
<span data-ttu-id="bae5e-123">它會使用 **Confirm** 參數，在刪除值之前要求使用者提示。</span><span class="sxs-lookup"><span data-stu-id="bae5e-123">It uses the **Confirm** parameter to request a user prompt before deleting the value.</span></span>

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

### <span data-ttu-id="bae5e-124">範例 3︰使用管線移除登錄值</span><span class="sxs-lookup"><span data-stu-id="bae5e-124">Example 3: Remove a registry value by using the pipeline</span></span>

<span data-ttu-id="bae5e-125">此命令會從 "HKLM\Software\MyCompany" 登錄機碼中刪除 "NoOfEmployees" 登錄值及其資料。</span><span class="sxs-lookup"><span data-stu-id="bae5e-125">This command deletes the "NoOfEmployees" registry value, and its data, from the "HKLM\Software\MyCompany" registry key.</span></span>

<span data-ttu-id="bae5e-126">此命令會使用 `Get-Item` Cmdlet 來取得代表登錄機碼的專案。</span><span class="sxs-lookup"><span data-stu-id="bae5e-126">The command uses the `Get-Item` cmdlet to get an item that represents the registry key.</span></span>
<span data-ttu-id="bae5e-127">它使用管線運算子 (`|`) 傳送物件至 `Remove-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="bae5e-127">It uses a pipeline operator (`|`) to send the object to `Remove-ItemProperty`.</span></span>
<span data-ttu-id="bae5e-128">然後，它會使用的 **name** 參數 `Remove-ItemProperty` 來指定登錄值的名稱。</span><span class="sxs-lookup"><span data-stu-id="bae5e-128">Then, it uses the **Name** parameter of `Remove-ItemProperty` to specify the name of the registry value.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

## <span data-ttu-id="bae5e-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bae5e-129">PARAMETERS</span></span>

### <span data-ttu-id="bae5e-130">-Credential</span><span class="sxs-lookup"><span data-stu-id="bae5e-130">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="bae5e-131">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="bae5e-131">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="bae5e-132">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="bae5e-132">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="bae5e-133">-Exclude</span><span class="sxs-lookup"><span data-stu-id="bae5e-133">-Exclude</span></span>

<span data-ttu-id="bae5e-134">指定此 Cmdlet 省略的項目。</span><span class="sxs-lookup"><span data-stu-id="bae5e-134">Specifies items that this cmdlet omits.</span></span>
<span data-ttu-id="bae5e-135">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="bae5e-135">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="bae5e-136">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="bae5e-136">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="bae5e-137">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="bae5e-137">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="bae5e-138">-Filter</span><span class="sxs-lookup"><span data-stu-id="bae5e-138">-Filter</span></span>

<span data-ttu-id="bae5e-139">以提供者的格式或語言指定篩選。</span><span class="sxs-lookup"><span data-stu-id="bae5e-139">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="bae5e-140">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="bae5e-140">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="bae5e-141">篩選的語法 (包括是否使用萬用字元) 取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="bae5e-141">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="bae5e-142">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="bae5e-142">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="bae5e-143">-Force</span><span class="sxs-lookup"><span data-stu-id="bae5e-143">-Force</span></span>

<span data-ttu-id="bae5e-144">強制 Cmdlet 對使用者無法以其他方式存取的物件移除屬性。</span><span class="sxs-lookup"><span data-stu-id="bae5e-144">Forces the cmdlet to remove a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="bae5e-145">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="bae5e-145">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="bae5e-146">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="bae5e-146">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="bae5e-147">-Include</span><span class="sxs-lookup"><span data-stu-id="bae5e-147">-Include</span></span>

<span data-ttu-id="bae5e-148">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="bae5e-148">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="bae5e-149">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="bae5e-149">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="bae5e-150">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="bae5e-150">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="bae5e-151">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="bae5e-151">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="bae5e-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="bae5e-152">-LiteralPath</span></span>

<span data-ttu-id="bae5e-153">指定屬性之目前位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="bae5e-153">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="bae5e-154">與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="bae5e-154">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="bae5e-155">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="bae5e-155">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="bae5e-156">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="bae5e-156">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="bae5e-157">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="bae5e-157">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="bae5e-158">-Name</span><span class="sxs-lookup"><span data-stu-id="bae5e-158">-Name</span></span>

<span data-ttu-id="bae5e-159">指定要移除的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="bae5e-159">Specifies the names of the properties to remove.</span></span>
<span data-ttu-id="bae5e-160">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="bae5e-160">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="bae5e-161">-Path</span><span class="sxs-lookup"><span data-stu-id="bae5e-161">-Path</span></span>

<span data-ttu-id="bae5e-162">指定要移除其屬性的項目路徑。</span><span class="sxs-lookup"><span data-stu-id="bae5e-162">Specifies the path of the item whose properties are being removed.</span></span>
<span data-ttu-id="bae5e-163">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="bae5e-163">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="bae5e-164">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="bae5e-164">-UseTransaction</span></span>

<span data-ttu-id="bae5e-165">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="bae5e-165">Includes the command in the active transaction.</span></span>
<span data-ttu-id="bae5e-166">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="bae5e-166">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="bae5e-167">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="bae5e-167">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="bae5e-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bae5e-168">-Confirm</span></span>

<span data-ttu-id="bae5e-169">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="bae5e-169">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bae5e-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bae5e-170">-WhatIf</span></span>

<span data-ttu-id="bae5e-171">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="bae5e-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="bae5e-172">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="bae5e-172">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bae5e-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bae5e-173">CommonParameters</span></span>

<span data-ttu-id="bae5e-174">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="bae5e-174">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="bae5e-175">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="bae5e-175">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="bae5e-176">輸入</span><span class="sxs-lookup"><span data-stu-id="bae5e-176">INPUTS</span></span>

### <span data-ttu-id="bae5e-177">System.String</span><span class="sxs-lookup"><span data-stu-id="bae5e-177">System.String</span></span>

<span data-ttu-id="bae5e-178">您可以使用管線將包含路徑 (但不是常值路徑) 的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bae5e-178">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="bae5e-179">輸出</span><span class="sxs-lookup"><span data-stu-id="bae5e-179">OUTPUTS</span></span>

### <span data-ttu-id="bae5e-180">無</span><span class="sxs-lookup"><span data-stu-id="bae5e-180">None</span></span>

<span data-ttu-id="bae5e-181">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="bae5e-181">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="bae5e-182">注意</span><span class="sxs-lookup"><span data-stu-id="bae5e-182">NOTES</span></span>

<span data-ttu-id="bae5e-183">在 PowerShell 登錄提供者中，登錄值會被視為登錄機碼或子機碼的屬性。</span><span class="sxs-lookup"><span data-stu-id="bae5e-183">In the PowerShell Registry provider, registry values are considered to be properties of a registry key or subkey.</span></span> <span data-ttu-id="bae5e-184">您可以使用 **ItemProperty** Cmdlet 來管理這些值。</span><span class="sxs-lookup"><span data-stu-id="bae5e-184">You can use the **ItemProperty** cmdlets to manage these values.</span></span>

<span data-ttu-id="bae5e-185">`Remove-ItemProperty` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="bae5e-185">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="bae5e-186">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="bae5e-186">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="bae5e-187">如需詳細資訊，請參閱 about_Providers。</span><span class="sxs-lookup"><span data-stu-id="bae5e-187">For more information, see about_Providers.</span></span>

## <span data-ttu-id="bae5e-188">相關連結</span><span class="sxs-lookup"><span data-stu-id="bae5e-188">RELATED LINKS</span></span>

[<span data-ttu-id="bae5e-189">Get-Item</span><span class="sxs-lookup"><span data-stu-id="bae5e-189">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="bae5e-190">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae5e-190">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="bae5e-191">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae5e-191">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="bae5e-192">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae5e-192">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="bae5e-193">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae5e-193">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="bae5e-194">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae5e-194">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="bae5e-195">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="bae5e-195">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="bae5e-196">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae5e-196">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="bae5e-197">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="bae5e-197">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="bae5e-198">about_Providers</span><span class="sxs-lookup"><span data-stu-id="bae5e-198">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
