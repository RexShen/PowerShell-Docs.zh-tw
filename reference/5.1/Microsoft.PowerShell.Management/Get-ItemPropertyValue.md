---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: 2dbbbfeac3810f79b976b6a68ab3089e91707fb3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203995"
---
# <span data-ttu-id="ad026-103">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="ad026-103">Get-ItemPropertyValue</span></span>

## <span data-ttu-id="ad026-104">概要</span><span class="sxs-lookup"><span data-stu-id="ad026-104">SYNOPSIS</span></span>
<span data-ttu-id="ad026-105">取得指定項目的一或多個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ad026-105">Gets the value for one or more properties of a specified item.</span></span>

## <span data-ttu-id="ad026-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ad026-106">SYNTAX</span></span>

### <span data-ttu-id="ad026-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="ad026-107">Path (Default)</span></span>

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="ad026-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ad026-108">LiteralPath</span></span>

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="ad026-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ad026-109">DESCRIPTION</span></span>

<span data-ttu-id="ad026-110">`Get-ItemPropertyValue`當您使用 *Name* 參數時，會取得您所指定之屬性的目前值（位於您以 *path* 或 *LiteralPath* 參數指定的路徑中）。</span><span class="sxs-lookup"><span data-stu-id="ad026-110">The `Get-ItemPropertyValue` gets the current value for a property that you specify when you use the *Name* parameter, located in a path that you specify with either the *Path* or *LiteralPath* parameters.</span></span>

## <span data-ttu-id="ad026-111">範例</span><span class="sxs-lookup"><span data-stu-id="ad026-111">EXAMPLES</span></span>

### <span data-ttu-id="ad026-112">範例 1︰取得 ProductID 屬性的值</span><span class="sxs-lookup"><span data-stu-id="ad026-112">Example 1: Get the value of the ProductID property</span></span>

<span data-ttu-id="ad026-113">此命令會取得 Windows 登錄提供者中 "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" 物件的 **ProductID** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="ad026-113">This command gets the value of the **ProductID** property of the "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" object in the Windows Registry provider.</span></span>

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### <span data-ttu-id="ad026-114">範例 2︰取得檔案或資料夾的上次寫入時間</span><span class="sxs-lookup"><span data-stu-id="ad026-114">Example 2: Get the last write time of a file or folder</span></span>

<span data-ttu-id="ad026-115">此命令會取得 **LastWriteTime** 屬性的值，或上次變更檔案或資料夾的時間，從 "C:\Users\Test\Documents\ModuleToAssembly" 資料夾，在 FileSystem 提供者中工作。</span><span class="sxs-lookup"><span data-stu-id="ad026-115">This command gets the value of the **LastWriteTime** property, or the last time a file or folder was changed, from the "C:\Users\Test\Documents\ModuleToAssembly" folder, working in the FileSystem provider.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### <span data-ttu-id="ad026-116">範例 3︰取得檔案或資料夾的多個屬性值</span><span class="sxs-lookup"><span data-stu-id="ad026-116">Example 3: Get multiple property values of a file or folder</span></span>

<span data-ttu-id="ad026-117">此命令會取得資料夾的 **LastWriteTime** 、 **CreationTime** 和 **Root** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ad026-117">This command gets the values of the **LastWriteTime** , **CreationTime** , and **Root** properties of a folder.</span></span>
<span data-ttu-id="ad026-118">屬性值會以您指定屬性名稱的順序傳回。</span><span class="sxs-lookup"><span data-stu-id="ad026-118">The property values are returned in the order in which you specified the property names.</span></span>

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

## <span data-ttu-id="ad026-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ad026-119">PARAMETERS</span></span>

### <span data-ttu-id="ad026-120">-Credential</span><span class="sxs-lookup"><span data-stu-id="ad026-120">-Credential</span></span>

<span data-ttu-id="ad026-121">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad026-121">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="ad026-122">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="ad026-122">The default is the current user.</span></span>

<span data-ttu-id="ad026-123">輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="ad026-123">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="ad026-124">若您輸入使用者名稱時，會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="ad026-124">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="ad026-125">與 Windows PowerShell 一起安裝的任何提供者皆不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="ad026-125">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

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

### <span data-ttu-id="ad026-126">-Exclude</span><span class="sxs-lookup"><span data-stu-id="ad026-126">-Exclude</span></span>

<span data-ttu-id="ad026-127">以字串陣列指定此 Cmdlet 在作業中排除的項目。</span><span class="sxs-lookup"><span data-stu-id="ad026-127">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="ad026-128">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="ad026-128">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="ad026-129">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="ad026-129">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="ad026-130">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ad026-130">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="ad026-131">-Filter</span><span class="sxs-lookup"><span data-stu-id="ad026-131">-Filter</span></span>

<span data-ttu-id="ad026-132">以提供者的格式或語言指定篩選。</span><span class="sxs-lookup"><span data-stu-id="ad026-132">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="ad026-133">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="ad026-133">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="ad026-134">篩選的語法 (包括是否使用萬用字元) 取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="ad026-134">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="ad026-135">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="ad026-135">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="ad026-136">-Include</span><span class="sxs-lookup"><span data-stu-id="ad026-136">-Include</span></span>

<span data-ttu-id="ad026-137">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="ad026-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="ad026-138">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="ad026-138">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="ad026-139">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="ad026-139">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="ad026-140">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ad026-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="ad026-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ad026-141">-LiteralPath</span></span>

<span data-ttu-id="ad026-142">指定屬性之目前位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="ad026-142">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="ad026-143">與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="ad026-143">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="ad026-144">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ad026-144">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="ad026-145">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="ad026-145">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="ad026-146">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="ad026-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="ad026-147">-Name</span><span class="sxs-lookup"><span data-stu-id="ad026-147">-Name</span></span>

<span data-ttu-id="ad026-148">指定要抓取之一或多個屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="ad026-148">Specifies the name of the property or properties to retrieve.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad026-149">-Path</span><span class="sxs-lookup"><span data-stu-id="ad026-149">-Path</span></span>

<span data-ttu-id="ad026-150">指定一或多個項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="ad026-150">Specifies the path to the item or items.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ad026-151">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="ad026-151">-UseTransaction</span></span>

<span data-ttu-id="ad026-152">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="ad026-152">Includes the command in the active transaction.</span></span>
<span data-ttu-id="ad026-153">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="ad026-153">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="ad026-154">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="ad026-154">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="ad026-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ad026-155">CommonParameters</span></span>

<span data-ttu-id="ad026-156">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="ad026-156">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="ad026-157">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="ad026-157">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ad026-158">輸入</span><span class="sxs-lookup"><span data-stu-id="ad026-158">INPUTS</span></span>

### <span data-ttu-id="ad026-159">System.String</span><span class="sxs-lookup"><span data-stu-id="ad026-159">System.String</span></span>

<span data-ttu-id="ad026-160">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad026-160">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="ad026-161">輸出</span><span class="sxs-lookup"><span data-stu-id="ad026-161">OUTPUTS</span></span>

### <span data-ttu-id="ad026-162">System.Boolean、System.String、System.DateTime</span><span class="sxs-lookup"><span data-stu-id="ad026-162">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="ad026-163">此 Cmdlet 對於取得的每個項目屬性值會傳回一個物件。</span><span class="sxs-lookup"><span data-stu-id="ad026-163">This cmdlet returns an object for each item property value that it gets.</span></span>
<span data-ttu-id="ad026-164">物件類型取決於所抓取的屬性值。</span><span class="sxs-lookup"><span data-stu-id="ad026-164">The object type depends on the property value that is retrieved.</span></span>
<span data-ttu-id="ad026-165">例如，在檔案系統磁碟機中，此 Cmdlet 可能會傳回檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="ad026-165">For example, in a file system drive, the cmdlet might return a file or folder.</span></span>

## <span data-ttu-id="ad026-166">注意</span><span class="sxs-lookup"><span data-stu-id="ad026-166">NOTES</span></span>

<span data-ttu-id="ad026-167">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="ad026-167">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="ad026-168">若要列出您的會話中可用的提供者，請執行 `Get-PSProvider` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad026-168">To list the providers available in your session, run the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="ad026-169">如需詳細資訊，請參閱 about_Providers。</span><span class="sxs-lookup"><span data-stu-id="ad026-169">For more information, see about_Providers.</span></span>

## <span data-ttu-id="ad026-170">相關連結</span><span class="sxs-lookup"><span data-stu-id="ad026-170">RELATED LINKS</span></span>

[<span data-ttu-id="ad026-171">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ad026-171">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="ad026-172">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ad026-172">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="ad026-173">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ad026-173">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="ad026-174">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ad026-174">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="ad026-175">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ad026-175">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="ad026-176">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ad026-176">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="ad026-177">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ad026-177">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="ad026-178">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ad026-178">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="ad026-179">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="ad026-179">Get-PSProvider</span></span>](Get-PSProvider.md)
