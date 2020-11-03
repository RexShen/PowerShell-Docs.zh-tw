---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: abf6a5ef365a606b6ca501e9cb924528763a8754
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204452"
---
# <span data-ttu-id="5a6cd-103">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5a6cd-103">Get-ItemProperty</span></span>

## <span data-ttu-id="5a6cd-104">概要</span><span class="sxs-lookup"><span data-stu-id="5a6cd-104">SYNOPSIS</span></span>
<span data-ttu-id="5a6cd-105">取得指定項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-105">Gets the properties of a specified item.</span></span>

## <span data-ttu-id="5a6cd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5a6cd-106">SYNTAX</span></span>

### <span data-ttu-id="5a6cd-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="5a6cd-107">Path (Default)</span></span>

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="5a6cd-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5a6cd-108">LiteralPath</span></span>

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="5a6cd-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5a6cd-109">DESCRIPTION</span></span>

<span data-ttu-id="5a6cd-110">`Get-ItemProperty`Cmdlet 會取得指定專案的屬性。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-110">The `Get-ItemProperty` cmdlet gets the properties of the specified items.</span></span>
<span data-ttu-id="5a6cd-111">例如，您可以使用這個 Cmdlet 取得檔案物件的 LastAccessTime 屬性值。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-111">For example, you can use this cmdlet to get the value of the LastAccessTime property of a file object.</span></span> <span data-ttu-id="5a6cd-112">您也可以使用這個 Cmdlet 來查看登錄專案和其值。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-112">You can also use this cmdlet to view registry entries and their values.</span></span>

## <span data-ttu-id="5a6cd-113">範例</span><span class="sxs-lookup"><span data-stu-id="5a6cd-113">EXAMPLES</span></span>

### <span data-ttu-id="5a6cd-114">範例1：取得特定目錄的相關資訊</span><span class="sxs-lookup"><span data-stu-id="5a6cd-114">Example 1: Get information about a specific directory</span></span>

<span data-ttu-id="5a6cd-115">此命令會取得目錄的相關資訊 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-115">This command gets information about the `C:\Windows` directory.</span></span>

```powershell
Get-ItemProperty C:\Windows
```

### <span data-ttu-id="5a6cd-116">範例2：取得特定檔案的屬性</span><span class="sxs-lookup"><span data-stu-id="5a6cd-116">Example 2: Get the properties of a specific file</span></span>

<span data-ttu-id="5a6cd-117">此命令會取得檔案的屬性 `C:\Test\Weather.xls` 。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-117">This command gets the properties of the `C:\Test\Weather.xls` file.</span></span>
<span data-ttu-id="5a6cd-118">結果會透過管道傳送至 `Format-List` Cmdlet，以將輸出顯示為清單。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-118">The result is piped to the `Format-List` cmdlet to display the output as a list.</span></span>

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### <span data-ttu-id="5a6cd-119">範例3：顯示登錄子機碼中登錄專案的值名稱和資料</span><span class="sxs-lookup"><span data-stu-id="5a6cd-119">Example 3: Display the value name and data of registry entries in a registry subkey</span></span>

<span data-ttu-id="5a6cd-120">此命令顯示 "CurrentVersion" 登錄子機碼中包含之每個登錄專案的值名稱和資料。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-120">This command displays the value name and data of each of the registry entries contained in the "CurrentVersion" registry subkey.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

> [!NOTE]
> <span data-ttu-id="5a6cd-121">此命令會要求將名為的 PowerShell 磁片磁碟機 `HKLM:` 對應至登錄的 "HKEY_LOCAL_MACHINE" hive。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-121">This command requires that there is a PowerShell drive named `HKLM:` that is mapped to the "HKEY_LOCAL_MACHINE" hive of the registry.</span></span>
>
> <span data-ttu-id="5a6cd-122">具有該名稱和對應的磁片磁碟機預設可在 PowerShell 中使用。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-122">A drive with that name and mapping is available in PowerShell by default.</span></span>
> <span data-ttu-id="5a6cd-123">或者，您可以使用下列替代路徑 (開頭為提供者名稱，後面是兩個冒號) 來指定此登錄子機碼的路徑：</span><span class="sxs-lookup"><span data-stu-id="5a6cd-123">Alternatively, the path to this registry subkey can be specified by using the following alternative path that begins with the provider name followed by two colons:</span></span>
>
> <span data-ttu-id="5a6cd-124">`Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="5a6cd-124">`Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

### <span data-ttu-id="5a6cd-125">範例4：取得登錄子機碼中登錄專案的值名稱和資料</span><span class="sxs-lookup"><span data-stu-id="5a6cd-125">Example 4: Get the value name and data of a registry entry in a registry subkey</span></span>

<span data-ttu-id="5a6cd-126">此命令會取得 "CurrentVersion" 登錄子機碼中 "ProgramFilesDir" 登錄專案的值名稱和資料。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-126">This command gets the value name and data of the "ProgramFilesDir" registry entry in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="5a6cd-127">**路徑** 會指定子機碼，而 **Name** 參數會指定專案的值名稱。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-127">The **Path** specifies the subkey and the **Name** parameter specifies the value name of the entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### <span data-ttu-id="5a6cd-128">範例5：取得登錄機碼中登錄專案的值名稱和資料</span><span class="sxs-lookup"><span data-stu-id="5a6cd-128">Example 5: Get the value names and data of registry entries in a registry key</span></span>

<span data-ttu-id="5a6cd-129">此命令會取得 "PowerShellEngine" 登錄機碼中登錄專案的值名稱和資料。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-129">This command gets the value names and data of the registry entries in the "PowerShellEngine" registry key.</span></span> <span data-ttu-id="5a6cd-130">結果顯示在下列範例輸出中。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-130">The results are shown in the following sample output.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
```

## <span data-ttu-id="5a6cd-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5a6cd-131">PARAMETERS</span></span>

### <span data-ttu-id="5a6cd-132">-Credential</span><span class="sxs-lookup"><span data-stu-id="5a6cd-132">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="5a6cd-133">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-133">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="5a6cd-134">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-134">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="5a6cd-135">-Exclude</span><span class="sxs-lookup"><span data-stu-id="5a6cd-135">-Exclude</span></span>

<span data-ttu-id="5a6cd-136">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-136">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="5a6cd-137">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="5a6cd-138">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-138">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="5a6cd-139">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="5a6cd-140">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-140">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="5a6cd-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="5a6cd-141">-Filter</span></span>

<span data-ttu-id="5a6cd-142">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-142">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="5a6cd-143">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-143">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="5a6cd-144">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-144">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="5a6cd-145">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-145">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="5a6cd-146">-Include</span><span class="sxs-lookup"><span data-stu-id="5a6cd-146">-Include</span></span>

<span data-ttu-id="5a6cd-147">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-147">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="5a6cd-148">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-148">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="5a6cd-149">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-149">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="5a6cd-150">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-150">Wildcard characters are permitted.</span></span> <span data-ttu-id="5a6cd-151">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-151">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="5a6cd-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5a6cd-152">-LiteralPath</span></span>

<span data-ttu-id="5a6cd-153">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-153">Specifies a path to one or more locations.</span></span> <span data-ttu-id="5a6cd-154">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-154">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="5a6cd-155">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-155">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="5a6cd-156">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-156">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="5a6cd-157">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-157">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="5a6cd-158">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-158">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="5a6cd-159">-Name</span><span class="sxs-lookup"><span data-stu-id="5a6cd-159">-Name</span></span>

<span data-ttu-id="5a6cd-160">指定要抓取之一或多個屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-160">Specifies the name of the property or properties to retrieve.</span></span>
<span data-ttu-id="5a6cd-161">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-161">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="5a6cd-162">-Path</span><span class="sxs-lookup"><span data-stu-id="5a6cd-162">-Path</span></span>

<span data-ttu-id="5a6cd-163">指定一或多個項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-163">Specifies the path to the item or items.</span></span>
<span data-ttu-id="5a6cd-164">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-164">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="5a6cd-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5a6cd-165">CommonParameters</span></span>

<span data-ttu-id="5a6cd-166">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-166">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="5a6cd-167">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-167">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5a6cd-168">輸入</span><span class="sxs-lookup"><span data-stu-id="5a6cd-168">INPUTS</span></span>

### <span data-ttu-id="5a6cd-169">System.String</span><span class="sxs-lookup"><span data-stu-id="5a6cd-169">System.String</span></span>

<span data-ttu-id="5a6cd-170">您可以使用管線將包含路徑的字串傳送至 `Get-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-170">You can pipe a string that contains a path to `Get-ItemProperty`.</span></span>

## <span data-ttu-id="5a6cd-171">輸出</span><span class="sxs-lookup"><span data-stu-id="5a6cd-171">OUTPUTS</span></span>

### <span data-ttu-id="5a6cd-172">System.Boolean、System.String、System.DateTime</span><span class="sxs-lookup"><span data-stu-id="5a6cd-172">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="5a6cd-173">`Get-ItemProperty` 針對它取得的每個專案屬性，各傳回一個物件。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-173">`Get-ItemProperty` returns an object for each item property that it gets.</span></span> <span data-ttu-id="5a6cd-174">物件類型取決於所抓取的物件。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-174">The object type depends on the object that is retrieved.</span></span> <span data-ttu-id="5a6cd-175">例如，在檔案系統磁碟機中，它可能會傳回檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-175">For example, in a file system drive, it might return a file or folder.</span></span>

## <span data-ttu-id="5a6cd-176">注意</span><span class="sxs-lookup"><span data-stu-id="5a6cd-176">NOTES</span></span>

<span data-ttu-id="5a6cd-177">此 `Get-ItemProperty` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-177">The `Get-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="5a6cd-178">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-178">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="5a6cd-179">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="5a6cd-179">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="5a6cd-180">相關連結</span><span class="sxs-lookup"><span data-stu-id="5a6cd-180">RELATED LINKS</span></span>

[<span data-ttu-id="5a6cd-181">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5a6cd-181">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="5a6cd-182">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5a6cd-182">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="5a6cd-183">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5a6cd-183">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="5a6cd-184">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5a6cd-184">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="5a6cd-185">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5a6cd-185">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="5a6cd-186">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5a6cd-186">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="5a6cd-187">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5a6cd-187">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="5a6cd-188">about_Providers</span><span class="sxs-lookup"><span data-stu-id="5a6cd-188">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
