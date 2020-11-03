---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 335f1f5b3e40eaf39cee7213b7bb02dbfa69ee3c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202055"
---
# <span data-ttu-id="2dd26-103">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2dd26-103">Remove-ItemProperty</span></span>

## <span data-ttu-id="2dd26-104">概要</span><span class="sxs-lookup"><span data-stu-id="2dd26-104">SYNOPSIS</span></span>
<span data-ttu-id="2dd26-105">刪除項目的屬性及其值。</span><span class="sxs-lookup"><span data-stu-id="2dd26-105">Deletes the property and its value from an item.</span></span>

## <span data-ttu-id="2dd26-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2dd26-106">SYNTAX</span></span>

### <span data-ttu-id="2dd26-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="2dd26-107">Path (Default)</span></span>

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2dd26-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2dd26-108">LiteralPath</span></span>

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2dd26-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2dd26-109">DESCRIPTION</span></span>

<span data-ttu-id="2dd26-110">`Remove-ItemProperty`Cmdlet 會從專案中刪除屬性和其值。</span><span class="sxs-lookup"><span data-stu-id="2dd26-110">The `Remove-ItemProperty` cmdlet deletes a property and its value from an item.</span></span>
<span data-ttu-id="2dd26-111">您可以使用它來刪除登錄值和它們所儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="2dd26-111">You can use it to delete registry values and the data that they store.</span></span>

## <span data-ttu-id="2dd26-112">範例</span><span class="sxs-lookup"><span data-stu-id="2dd26-112">EXAMPLES</span></span>

### <span data-ttu-id="2dd26-113">範例 1：刪除登錄值</span><span class="sxs-lookup"><span data-stu-id="2dd26-113">Example 1: Delete a registry value</span></span>

<span data-ttu-id="2dd26-114">此命令會從登錄機碼的 "SmpApplication" 子機碼中刪除 "SmpProperty" 登錄值及其資料 `HKEY_LOCAL_MACHINE\Software` 。</span><span class="sxs-lookup"><span data-stu-id="2dd26-114">This command deletes the "SmpProperty" registry value, and its data, from the "SmpApplication" subkey of the `HKEY_LOCAL_MACHINE\Software` registry key.</span></span>

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

<span data-ttu-id="2dd26-115">因為命令是從檔案系統磁片磁碟機 () 發出 `PS C:\>` ，所以它會包含 "SmpApplication" 子機碼的完整路徑，包括磁片磁碟機、 `HKLM:` 和 "Software" 機碼。</span><span class="sxs-lookup"><span data-stu-id="2dd26-115">Because the command is issued from a file system drive (`PS C:\>`), it includes the fully qualified path of the "SmpApplication" subkey, including the drive, `HKLM:`, and the "Software" key.</span></span>

### <span data-ttu-id="2dd26-116">範例 2︰從 HKCU 位置刪除登錄值</span><span class="sxs-lookup"><span data-stu-id="2dd26-116">Example 2: Delete a registry value from the HKCU location</span></span>

<span data-ttu-id="2dd26-117">這些命令會從 "HKEY_CURRENT_USER\Software\MyCompany" 的 "MyApp" 子機碼中刪除 "Options" 登錄值及其資料。</span><span class="sxs-lookup"><span data-stu-id="2dd26-117">These commands delete the "Options" registry value, and its data, from the "MyApp" subkey of "HKEY_CURRENT_USER\Software\MyCompany".</span></span>

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

<span data-ttu-id="2dd26-118">第一個命令會使用 `Set-Location` Cmdlet 將目前的位置變更為 **HKEY_CURRENT_USER** 磁片磁碟機 (`HKCU:`) 和子機碼 `Software\MyCompany\MyApp` 。</span><span class="sxs-lookup"><span data-stu-id="2dd26-118">The first command uses the `Set-Location` cmdlet to change the current location to the **HKEY_CURRENT_USER** drive (`HKCU:`) and the `Software\MyCompany\MyApp` subkey.</span></span>

<span data-ttu-id="2dd26-119">第二個命令會使用 `Remove-ItemProperty` 從 "MyApp" 子機碼移除 "Options" 登錄值及其資料。</span><span class="sxs-lookup"><span data-stu-id="2dd26-119">The second command uses `Remove-ItemProperty` to remove the "Options" registry value, and its data, from the "MyApp" subkey.</span></span> <span data-ttu-id="2dd26-120">因為 **Path** 是必要的，所以命令會使用點 (`.`) 來指出目前的位置。</span><span class="sxs-lookup"><span data-stu-id="2dd26-120">Because **Path** is required, the command uses a dot (`.`) to indicate the current location.</span></span> <span data-ttu-id="2dd26-121">**Confirm** 參數會在刪除值之前要求使用者提示。</span><span class="sxs-lookup"><span data-stu-id="2dd26-121">The **Confirm** parameter requests a user prompt before deleting the value.</span></span>

### <span data-ttu-id="2dd26-122">範例 3︰使用管線移除登錄值</span><span class="sxs-lookup"><span data-stu-id="2dd26-122">Example 3: Remove a registry value by using the pipeline</span></span>

<span data-ttu-id="2dd26-123">此命令會從登錄機碼中刪除 "NoOfEmployees" 登錄值及其資料 `HKLM\Software\MyCompany` 。</span><span class="sxs-lookup"><span data-stu-id="2dd26-123">This command deletes the "NoOfEmployees" registry value, and its data, from the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

<span data-ttu-id="2dd26-124">此命令會使用 `Get-Item` Cmdlet 來取得代表登錄機碼的專案。</span><span class="sxs-lookup"><span data-stu-id="2dd26-124">The command uses the `Get-Item` cmdlet to get an item that represents the registry key.</span></span>
<span data-ttu-id="2dd26-125">它使用管線運算子 (`|`) 傳送物件至 `Remove-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="2dd26-125">It uses a pipeline operator (`|`) to send the object to `Remove-ItemProperty`.</span></span>
<span data-ttu-id="2dd26-126">然後，它會使用的 **name** 參數 `Remove-ItemProperty` 來指定登錄值的名稱。</span><span class="sxs-lookup"><span data-stu-id="2dd26-126">Then, it uses the **Name** parameter of `Remove-ItemProperty` to specify the name of the registry value.</span></span>

## <span data-ttu-id="2dd26-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2dd26-127">PARAMETERS</span></span>

### <span data-ttu-id="2dd26-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="2dd26-128">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="2dd26-129">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="2dd26-129">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="2dd26-130">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="2dd26-130">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="2dd26-131">-Exclude</span><span class="sxs-lookup"><span data-stu-id="2dd26-131">-Exclude</span></span>

<span data-ttu-id="2dd26-132">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="2dd26-132">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="2dd26-133">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="2dd26-133">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2dd26-134">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="2dd26-134">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="2dd26-135">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2dd26-135">Wildcard characters are permitted.</span></span> <span data-ttu-id="2dd26-136">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="2dd26-136">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2dd26-137">-Filter</span><span class="sxs-lookup"><span data-stu-id="2dd26-137">-Filter</span></span>

<span data-ttu-id="2dd26-138">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="2dd26-138">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="2dd26-139">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="2dd26-139">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="2dd26-140">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="2dd26-140">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="2dd26-141">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="2dd26-141">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="2dd26-142">-Force</span><span class="sxs-lookup"><span data-stu-id="2dd26-142">-Force</span></span>

<span data-ttu-id="2dd26-143">強制 Cmdlet 對使用者無法以其他方式存取的物件移除屬性。</span><span class="sxs-lookup"><span data-stu-id="2dd26-143">Forces the cmdlet to remove a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="2dd26-144">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="2dd26-144">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="2dd26-145">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="2dd26-145">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="2dd26-146">-Include</span><span class="sxs-lookup"><span data-stu-id="2dd26-146">-Include</span></span>

<span data-ttu-id="2dd26-147">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="2dd26-147">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="2dd26-148">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="2dd26-148">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2dd26-149">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="2dd26-149">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="2dd26-150">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2dd26-150">Wildcard characters are permitted.</span></span> <span data-ttu-id="2dd26-151">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="2dd26-151">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2dd26-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2dd26-152">-LiteralPath</span></span>

<span data-ttu-id="2dd26-153">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="2dd26-153">Specifies a path to one or more locations.</span></span> <span data-ttu-id="2dd26-154">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="2dd26-154">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="2dd26-155">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2dd26-155">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="2dd26-156">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="2dd26-156">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2dd26-157">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="2dd26-157">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="2dd26-158">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="2dd26-158">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="2dd26-159">-Name</span><span class="sxs-lookup"><span data-stu-id="2dd26-159">-Name</span></span>

<span data-ttu-id="2dd26-160">指定要移除的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="2dd26-160">Specifies the names of the properties to remove.</span></span>
<span data-ttu-id="2dd26-161">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2dd26-161">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="2dd26-162">-Path</span><span class="sxs-lookup"><span data-stu-id="2dd26-162">-Path</span></span>

<span data-ttu-id="2dd26-163">指定要移除其屬性的項目路徑。</span><span class="sxs-lookup"><span data-stu-id="2dd26-163">Specifies the path of the item whose properties are being removed.</span></span>
<span data-ttu-id="2dd26-164">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2dd26-164">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="2dd26-165">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2dd26-165">-Confirm</span></span>

<span data-ttu-id="2dd26-166">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="2dd26-166">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2dd26-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2dd26-167">-WhatIf</span></span>

<span data-ttu-id="2dd26-168">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="2dd26-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2dd26-169">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="2dd26-169">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2dd26-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2dd26-170">CommonParameters</span></span>

<span data-ttu-id="2dd26-171">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="2dd26-171">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="2dd26-172">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="2dd26-172">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2dd26-173">輸入</span><span class="sxs-lookup"><span data-stu-id="2dd26-173">INPUTS</span></span>

### <span data-ttu-id="2dd26-174">System.String</span><span class="sxs-lookup"><span data-stu-id="2dd26-174">System.String</span></span>

<span data-ttu-id="2dd26-175">您可以使用管線將包含路徑 (但不是常值路徑) 的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2dd26-175">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="2dd26-176">輸出</span><span class="sxs-lookup"><span data-stu-id="2dd26-176">OUTPUTS</span></span>

### <span data-ttu-id="2dd26-177">無</span><span class="sxs-lookup"><span data-stu-id="2dd26-177">None</span></span>

<span data-ttu-id="2dd26-178">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="2dd26-178">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="2dd26-179">注意</span><span class="sxs-lookup"><span data-stu-id="2dd26-179">NOTES</span></span>

- <span data-ttu-id="2dd26-180">在 PowerShell 登錄提供者中，登錄值會被視為登錄機碼或子機碼的屬性。</span><span class="sxs-lookup"><span data-stu-id="2dd26-180">In the PowerShell Registry provider, registry values are considered to be properties of a registry key or subkey.</span></span> <span data-ttu-id="2dd26-181">您可以使用 **ItemProperty** Cmdlet 來管理這些值。</span><span class="sxs-lookup"><span data-stu-id="2dd26-181">You can use the **ItemProperty** cmdlets to manage these values.</span></span>
- <span data-ttu-id="2dd26-182">`Remove-ItemProperty` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="2dd26-182">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="2dd26-183">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="2dd26-183">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="2dd26-184">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="2dd26-184">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="2dd26-185">相關連結</span><span class="sxs-lookup"><span data-stu-id="2dd26-185">RELATED LINKS</span></span>

[<span data-ttu-id="2dd26-186">Get-Item</span><span class="sxs-lookup"><span data-stu-id="2dd26-186">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="2dd26-187">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2dd26-187">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="2dd26-188">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2dd26-188">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="2dd26-189">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2dd26-189">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="2dd26-190">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2dd26-190">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="2dd26-191">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2dd26-191">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="2dd26-192">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="2dd26-192">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="2dd26-193">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2dd26-193">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="2dd26-194">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2dd26-194">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="2dd26-195">Set-Location</span><span class="sxs-lookup"><span data-stu-id="2dd26-195">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="2dd26-196">about_Providers</span><span class="sxs-lookup"><span data-stu-id="2dd26-196">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

