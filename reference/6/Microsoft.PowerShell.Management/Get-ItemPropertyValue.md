---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: fe49b968c859060b6f1c82c27bac87b33dabe079
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204451"
---
# <span data-ttu-id="64c29-103">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="64c29-103">Get-ItemPropertyValue</span></span>

## <span data-ttu-id="64c29-104">概要</span><span class="sxs-lookup"><span data-stu-id="64c29-104">SYNOPSIS</span></span>
<span data-ttu-id="64c29-105">取得指定項目的一或多個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="64c29-105">Gets the value for one or more properties of a specified item.</span></span>

## <span data-ttu-id="64c29-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="64c29-106">SYNTAX</span></span>

### <span data-ttu-id="64c29-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="64c29-107">Path (Default)</span></span>

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="64c29-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="64c29-108">LiteralPath</span></span>

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="64c29-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="64c29-109">DESCRIPTION</span></span>

<span data-ttu-id="64c29-110">`Get-ItemPropertyValue`當您使用 *Name* 參數時，會取得您所指定之屬性的目前值（位於您以 *path* 或 *LiteralPath* 參數指定的路徑中）。</span><span class="sxs-lookup"><span data-stu-id="64c29-110">The `Get-ItemPropertyValue` gets the current value for a property that you specify when you use the *Name* parameter, located in a path that you specify with either the *Path* or *LiteralPath* parameters.</span></span>

## <span data-ttu-id="64c29-111">範例</span><span class="sxs-lookup"><span data-stu-id="64c29-111">EXAMPLES</span></span>

### <span data-ttu-id="64c29-112">範例 1︰取得 ProductID 屬性的值</span><span class="sxs-lookup"><span data-stu-id="64c29-112">Example 1: Get the value of the ProductID property</span></span>

<span data-ttu-id="64c29-113">此命令會取得 Windows 登錄提供者中 "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" 物件的 **ProductID** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="64c29-113">This command gets the value of the **ProductID** property of the "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" object in the Windows Registry provider.</span></span>

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### <span data-ttu-id="64c29-114">範例 2︰取得檔案或資料夾的上次寫入時間</span><span class="sxs-lookup"><span data-stu-id="64c29-114">Example 2: Get the last write time of a file or folder</span></span>

<span data-ttu-id="64c29-115">此命令會取得 **LastWriteTime** 屬性的值，或上次變更檔案或資料夾的時間，從 "C:\Users\Test\Documents\ModuleToAssembly" 資料夾，在 FileSystem 提供者中工作。</span><span class="sxs-lookup"><span data-stu-id="64c29-115">This command gets the value of the **LastWriteTime** property, or the last time a file or folder was changed, from the "C:\Users\Test\Documents\ModuleToAssembly" folder, working in the FileSystem provider.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### <span data-ttu-id="64c29-116">範例 3︰取得檔案或資料夾的多個屬性值</span><span class="sxs-lookup"><span data-stu-id="64c29-116">Example 3: Get multiple property values of a file or folder</span></span>

<span data-ttu-id="64c29-117">此命令會取得資料夾的 **LastWriteTime** 、 **CreationTime** 和 **Root** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="64c29-117">This command gets the values of the **LastWriteTime** , **CreationTime** , and **Root** properties of a folder.</span></span> <span data-ttu-id="64c29-118">屬性值會以您指定屬性名稱的順序傳回。</span><span class="sxs-lookup"><span data-stu-id="64c29-118">The property values are returned in the order in which you specified the property names.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime,CreationTime,Root
```

```output
Wednesday, September 3, 2014 2:53:22 PM
Wednesday, September 3, 2014 2:53:10 PM

Name              : C:\
Parent            :
Exists            : True
Root              : C:\
FullName          : C:\
Extension         :
CreationTime      : 9/1/2014 4:59:45 AM
CreationTimeUtc   : 9/1/2014 11:59:45 AM
LastAccessTime    : 9/27/2014 5:22:02 PM
LastAccessTimeUtc : 9/28/2014 12:22:02 AM
LastWriteTime     : 9/27/2014 5:22:02 PM
LastWriteTimeUtc  : 9/28/2014 12:22:02 AM
Attributes        : Hidden, System, Directory
BaseName          : C:\
Target            :
LinkType          :
Mode              : d--hs-
```

## <span data-ttu-id="64c29-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="64c29-119">PARAMETERS</span></span>

### <span data-ttu-id="64c29-120">-Credential</span><span class="sxs-lookup"><span data-stu-id="64c29-120">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="64c29-121">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="64c29-121">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="64c29-122">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="64c29-122">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="64c29-123">-Exclude</span><span class="sxs-lookup"><span data-stu-id="64c29-123">-Exclude</span></span>

<span data-ttu-id="64c29-124">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="64c29-124">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="64c29-125">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="64c29-125">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="64c29-126">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="64c29-126">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="64c29-127">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="64c29-127">Wildcard characters are permitted.</span></span> <span data-ttu-id="64c29-128">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="64c29-128">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="64c29-129">-Filter</span><span class="sxs-lookup"><span data-stu-id="64c29-129">-Filter</span></span>

<span data-ttu-id="64c29-130">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="64c29-130">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="64c29-131">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="64c29-131">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="64c29-132">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="64c29-132">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="64c29-133">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="64c29-133">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="64c29-134">-Include</span><span class="sxs-lookup"><span data-stu-id="64c29-134">-Include</span></span>

<span data-ttu-id="64c29-135">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="64c29-135">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="64c29-136">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="64c29-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="64c29-137">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="64c29-137">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="64c29-138">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="64c29-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="64c29-139">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="64c29-139">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="64c29-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="64c29-140">-LiteralPath</span></span>

<span data-ttu-id="64c29-141">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="64c29-141">Specifies a path to one or more locations.</span></span> <span data-ttu-id="64c29-142">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="64c29-142">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="64c29-143">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="64c29-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="64c29-144">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="64c29-144">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="64c29-145">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="64c29-145">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="64c29-146">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="64c29-146">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="64c29-147">-Name</span><span class="sxs-lookup"><span data-stu-id="64c29-147">-Name</span></span>

<span data-ttu-id="64c29-148">指定要抓取之一或多個屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="64c29-148">Specifies the name of the property or properties to retrieve.</span></span>
<span data-ttu-id="64c29-149">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="64c29-149">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="64c29-150">-Path</span><span class="sxs-lookup"><span data-stu-id="64c29-150">-Path</span></span>

<span data-ttu-id="64c29-151">指定一或多個項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="64c29-151">Specifies the path to the item or items.</span></span>
<span data-ttu-id="64c29-152">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="64c29-152">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="64c29-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="64c29-153">CommonParameters</span></span>

<span data-ttu-id="64c29-154">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="64c29-154">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="64c29-155">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="64c29-155">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="64c29-156">輸入</span><span class="sxs-lookup"><span data-stu-id="64c29-156">INPUTS</span></span>

### <span data-ttu-id="64c29-157">System.String</span><span class="sxs-lookup"><span data-stu-id="64c29-157">System.String</span></span>

<span data-ttu-id="64c29-158">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64c29-158">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="64c29-159">輸出</span><span class="sxs-lookup"><span data-stu-id="64c29-159">OUTPUTS</span></span>

### <span data-ttu-id="64c29-160">System.Boolean、System.String、System.DateTime</span><span class="sxs-lookup"><span data-stu-id="64c29-160">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="64c29-161">此 Cmdlet 對於取得的每個項目屬性值會傳回一個物件。</span><span class="sxs-lookup"><span data-stu-id="64c29-161">This cmdlet returns an object for each item property value that it gets.</span></span>
<span data-ttu-id="64c29-162">物件類型取決於所抓取的屬性值。</span><span class="sxs-lookup"><span data-stu-id="64c29-162">The object type depends on the property value that is retrieved.</span></span>
<span data-ttu-id="64c29-163">例如，在檔案系統磁碟機中，此 Cmdlet 可能會傳回檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="64c29-163">For example, in a file system drive, the cmdlet might return a file or folder.</span></span>

## <span data-ttu-id="64c29-164">注意</span><span class="sxs-lookup"><span data-stu-id="64c29-164">NOTES</span></span>

<span data-ttu-id="64c29-165">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="64c29-165">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="64c29-166">若要列出您的會話中可用的提供者，請執行 `Get-PSProvider` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64c29-166">To list the providers available in your session, run the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="64c29-167">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="64c29-167">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="64c29-168">相關連結</span><span class="sxs-lookup"><span data-stu-id="64c29-168">RELATED LINKS</span></span>

[<span data-ttu-id="64c29-169">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64c29-169">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="64c29-170">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64c29-170">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="64c29-171">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64c29-171">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="64c29-172">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="64c29-172">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="64c29-173">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64c29-173">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="64c29-174">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64c29-174">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="64c29-175">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64c29-175">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="64c29-176">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64c29-176">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="64c29-177">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64c29-177">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="64c29-178">about_Providers</span><span class="sxs-lookup"><span data-stu-id="64c29-178">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
