---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: 4189201cd373d29e8ea8e88441376e0df902742e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202091"
---
# <span data-ttu-id="8ab14-103">Join-Path</span><span class="sxs-lookup"><span data-stu-id="8ab14-103">Join-Path</span></span>

## <span data-ttu-id="8ab14-104">概要</span><span class="sxs-lookup"><span data-stu-id="8ab14-104">SYNOPSIS</span></span>
<span data-ttu-id="8ab14-105">將路徑和子路徑結合成單一路徑。</span><span class="sxs-lookup"><span data-stu-id="8ab14-105">Combines a path and a child path into a single path.</span></span>

## <span data-ttu-id="8ab14-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8ab14-106">SYNTAX</span></span>

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [[-AdditionalChildPath] <String[]>] [-Resolve]
 [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="8ab14-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8ab14-107">DESCRIPTION</span></span>

<span data-ttu-id="8ab14-108">此 `Join-Path` Cmdlet 會將路徑和子路徑結合成單一路徑。</span><span class="sxs-lookup"><span data-stu-id="8ab14-108">The `Join-Path` cmdlet combines a path and child-path into a single path.</span></span>
<span data-ttu-id="8ab14-109">提供者會提供路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8ab14-109">The provider supplies the path delimiters.</span></span>

## <span data-ttu-id="8ab14-110">範例</span><span class="sxs-lookup"><span data-stu-id="8ab14-110">EXAMPLES</span></span>

### <span data-ttu-id="8ab14-111">範例1：將路徑與子路徑結合</span><span class="sxs-lookup"><span data-stu-id="8ab14-111">Example 1: Combine a path with a child path</span></span>

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

<span data-ttu-id="8ab14-112">此命令會使用 `Join-Path` 將路徑與 childpath 結合。</span><span class="sxs-lookup"><span data-stu-id="8ab14-112">This command uses `Join-Path` to combine a path with a childpath.</span></span>

<span data-ttu-id="8ab14-113">因為命令是從 `FileSystem` 提供者執行，所以它會提供 `\` 分隔符號來加入路徑。</span><span class="sxs-lookup"><span data-stu-id="8ab14-113">Since the command is executed from the `FileSystem` provider, it provides the `\` delimiter to join the paths.</span></span>

### <span data-ttu-id="8ab14-114">範例2：合併已包含目錄分隔符號的路徑</span><span class="sxs-lookup"><span data-stu-id="8ab14-114">Example 2: Combine paths that already contain directory separators</span></span>

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

<span data-ttu-id="8ab14-115">現有的目錄分隔符號 `\` 和處理，因此和之間只有一個分隔符號 `Path``ChildPath`</span><span class="sxs-lookup"><span data-stu-id="8ab14-115">Existing directory separators `\` and handled so there is only one separator between `Path` and `ChildPath`</span></span>

### <span data-ttu-id="8ab14-116">範例3：聯結路徑與子路徑以顯示檔案和資料夾</span><span class="sxs-lookup"><span data-stu-id="8ab14-116">Example 3: Display files and folders by joining a path with a child path</span></span>

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

<span data-ttu-id="8ab14-117">此命令會顯示藉由聯結 C:\Win \* 路徑和系統子路徑所參考的檔案和資料夾 \* 。</span><span class="sxs-lookup"><span data-stu-id="8ab14-117">This command displays the files and folders that are referenced by joining the C:\Win\* path and the System\* child path.</span></span>
<span data-ttu-id="8ab14-118">它會顯示與相同的檔案和資料夾 `Get-ChildItem` ，但它會顯示每個專案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="8ab14-118">It displays the same files and folders as `Get-ChildItem`, but it displays the fully qualified path to each item.</span></span>
<span data-ttu-id="8ab14-119">在這個命令中， `Path` `ChildPath` 會省略和選擇性參數名稱。</span><span class="sxs-lookup"><span data-stu-id="8ab14-119">In this command, the `Path` and `ChildPath` optional parameter names are omitted.</span></span>

### <span data-ttu-id="8ab14-120">範例4：搭配 PowerShell 登錄提供者使用 Join-Path</span><span class="sxs-lookup"><span data-stu-id="8ab14-120">Example 4: Use Join-Path with the PowerShell registry provider</span></span>

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

<span data-ttu-id="8ab14-121">此命令會顯示登錄子機碼中包含的登錄機碼 `HKLM\System` `ControlSet` 。</span><span class="sxs-lookup"><span data-stu-id="8ab14-121">This command displays the registry keys in the `HKLM\System` registry subkey that include `ControlSet`.</span></span>

<span data-ttu-id="8ab14-122">`Resolve`參數，會嘗試解析聯結的路徑，包括來自目前提供者路徑的萬用字元`HKLM:\`</span><span class="sxs-lookup"><span data-stu-id="8ab14-122">The `Resolve` parameter, attempts to resolve the joined path, including wildcards from the current provider path `HKLM:\`</span></span>

### <span data-ttu-id="8ab14-123">範例5：結合多個路徑根目錄與子路徑</span><span class="sxs-lookup"><span data-stu-id="8ab14-123">Example 5: Combine multiple path roots with a child path</span></span>

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

<span data-ttu-id="8ab14-124">此命令會使用 `Join-Path` 將多個路徑根目錄與子路徑結合。</span><span class="sxs-lookup"><span data-stu-id="8ab14-124">This command uses `Join-Path` to combine multiple path roots with a child path.</span></span>

> [!NOTE]
> <span data-ttu-id="8ab14-125">指定的磁片磁碟機 `Path` 必須存在，否則該專案的聯結將會失敗。</span><span class="sxs-lookup"><span data-stu-id="8ab14-125">The Drives specified by `Path` must exist or the join of that entry will fail.</span></span>

### <span data-ttu-id="8ab14-126">範例6：將檔案系統磁片磁碟機的根目錄與子路徑結合</span><span class="sxs-lookup"><span data-stu-id="8ab14-126">Example 6: Combine the roots of a file system drive with a child path</span></span>

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

<span data-ttu-id="8ab14-127">此命令會將主控台中每個 PowerShell 檔案系統磁片磁碟機的根目錄與 Subdir 子路徑結合。</span><span class="sxs-lookup"><span data-stu-id="8ab14-127">This command combines the roots of each PowerShell file system drive in the console with the Subdir child path.</span></span>

<span data-ttu-id="8ab14-128">此命令會使用 `Get-PSDrive` Cmdlet 來取得 FileSystem 提供者所支援的 PowerShell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="8ab14-128">The command uses the `Get-PSDrive` cmdlet to get the PowerShell drives supported by the FileSystem provider.</span></span>
<span data-ttu-id="8ab14-129">`ForEach-Object`語句只會選取物件的根屬性 `PSDriveInfo` ，並將它與指定的子路徑結合。</span><span class="sxs-lookup"><span data-stu-id="8ab14-129">The `ForEach-Object` statement selects only the Root property of the `PSDriveInfo` objects and combines it with the specified child path.</span></span>

<span data-ttu-id="8ab14-130">輸出顯示電腦上的 PowerShell 磁片磁碟機包含對應至 C:\Program Files 目錄的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="8ab14-130">The output shows that the PowerShell drives on the computer included a drive mapped to the C:\Program Files directory.</span></span>

### <span data-ttu-id="8ab14-131">範例7：結合不定數目的路徑</span><span class="sxs-lookup"><span data-stu-id="8ab14-131">Example 7: Combine an indefinite number of paths</span></span>

```powershell
Join-Path a b c d e f g
```

```Output
a\b\c\d\e\f\g
```

<span data-ttu-id="8ab14-132">`AdditionalChildPath`參數允許聯結不限數目的路徑。</span><span class="sxs-lookup"><span data-stu-id="8ab14-132">The `AdditionalChildPath` parameter allows the joining of an unlimited number of paths.</span></span>

<span data-ttu-id="8ab14-133">在此範例中，不會使用任何參數名稱，因此 "a" 會系結至 `Path` ，"b" 至 " `ChildPath` c-g" 至 `AdditionalChildPath`</span><span class="sxs-lookup"><span data-stu-id="8ab14-133">In this example, no parameter names are used, thus "a" binds to `Path`, "b" to `ChildPath` and "c-g" to `AdditionalChildPath`</span></span>

## <span data-ttu-id="8ab14-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8ab14-134">PARAMETERS</span></span>

### <span data-ttu-id="8ab14-135">-AdditionalChildPath</span><span class="sxs-lookup"><span data-stu-id="8ab14-135">-AdditionalChildPath</span></span>

<span data-ttu-id="8ab14-136">指定要附加至 *Path* 參數值的其他元素。</span><span class="sxs-lookup"><span data-stu-id="8ab14-136">Specifies additional elements to append to the value of the *Path* parameter.</span></span> <span data-ttu-id="8ab14-137">`ChildPath`參數仍然是強制性的，也必須指定。</span><span class="sxs-lookup"><span data-stu-id="8ab14-137">The `ChildPath` parameter is still mandatory and must be specified as well.</span></span>

<span data-ttu-id="8ab14-138">這個參數是以屬性（property）指定，該 `ValueFromRemainingArguments` 屬性可讓您聯結不定數目的路徑。</span><span class="sxs-lookup"><span data-stu-id="8ab14-138">This parameter is specified with the `ValueFromRemainingArguments` property which enables joining an indefinite number of paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8ab14-139">-ChildPath</span><span class="sxs-lookup"><span data-stu-id="8ab14-139">-ChildPath</span></span>

<span data-ttu-id="8ab14-140">指定要附加至參數值的元素 `Path` 。</span><span class="sxs-lookup"><span data-stu-id="8ab14-140">Specifies the elements to append to the value of the `Path` parameter.</span></span>
<span data-ttu-id="8ab14-141">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8ab14-141">Wildcards are permitted.</span></span>
<span data-ttu-id="8ab14-142">`ChildPath`參數是必要參數，雖然參數名稱 ( "ChildPath" ) 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="8ab14-142">The `ChildPath` parameter is required, although the parameter name ("ChildPath") is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="8ab14-143">-Credential</span><span class="sxs-lookup"><span data-stu-id="8ab14-143">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="8ab14-144">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="8ab14-144">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="8ab14-145">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="8ab14-145">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="8ab14-146">-Path</span><span class="sxs-lookup"><span data-stu-id="8ab14-146">-Path</span></span>

<span data-ttu-id="8ab14-147">指定附加子路徑的主要路徑。</span><span class="sxs-lookup"><span data-stu-id="8ab14-147">Specifies the main path (or paths) to which the child-path is appended.</span></span>
<span data-ttu-id="8ab14-148">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8ab14-148">Wildcards are permitted.</span></span>

<span data-ttu-id="8ab14-149">的值會 `Path` 決定要加入路徑的提供者，並新增路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8ab14-149">The value of `Path` determines which provider joins the paths and adds the path delimiters.</span></span>
<span data-ttu-id="8ab14-150">`Path`參數是必要參數，雖然參數名稱 ( "Path" ) 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="8ab14-150">The `Path` parameter is required, although the parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="8ab14-151">-Resolve</span><span class="sxs-lookup"><span data-stu-id="8ab14-151">-Resolve</span></span>

<span data-ttu-id="8ab14-152">指出此 Cmdlet 應該嘗試解析來自目前提供者的聯結路徑。</span><span class="sxs-lookup"><span data-stu-id="8ab14-152">Indicates that this cmdlet should attempt to resolve the joined path from the current provider.</span></span>

- <span data-ttu-id="8ab14-153">如果使用萬用字元，則 Cmdlet 會傳回所有符合聯結路徑的路徑。</span><span class="sxs-lookup"><span data-stu-id="8ab14-153">If wildcards are used, the cmdlet returns all paths that match the joined path.</span></span>
- <span data-ttu-id="8ab14-154">如果 **未** 使用萬用字元，則如果路徑不存在，Cmdlet 將會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8ab14-154">If **no** wildcards are used, the cmdlet will error if the path does not exist.</span></span>

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

### <span data-ttu-id="8ab14-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8ab14-155">CommonParameters</span></span>

<span data-ttu-id="8ab14-156">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8ab14-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8ab14-157">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8ab14-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8ab14-158">輸入</span><span class="sxs-lookup"><span data-stu-id="8ab14-158">INPUTS</span></span>

### <span data-ttu-id="8ab14-159">System.String</span><span class="sxs-lookup"><span data-stu-id="8ab14-159">System.String</span></span>

<span data-ttu-id="8ab14-160">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8ab14-160">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="8ab14-161">輸出</span><span class="sxs-lookup"><span data-stu-id="8ab14-161">OUTPUTS</span></span>

### <span data-ttu-id="8ab14-162">System.String</span><span class="sxs-lookup"><span data-stu-id="8ab14-162">System.String</span></span>

<span data-ttu-id="8ab14-163">這個 Cmdlet 會傳回包含產生之路徑的字串。</span><span class="sxs-lookup"><span data-stu-id="8ab14-163">This cmdlet returns a string that contains the resulting path.</span></span>

## <span data-ttu-id="8ab14-164">注意</span><span class="sxs-lookup"><span data-stu-id="8ab14-164">NOTES</span></span>

<span data-ttu-id="8ab14-165">包含路徑名詞 (Path Cmdlet 的 Cmdlet 會) 操作路徑名稱，並傳回所有 PowerShell 提供者都能解讀的精簡格式名稱。</span><span class="sxs-lookup"><span data-stu-id="8ab14-165">The cmdlets that contain the Path noun (the Path cmdlets) manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="8ab14-166">它們是設計用於程式與指令碼，您可以在其中以特定格式顯示所有或部分路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="8ab14-166">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="8ab14-167">使用方式與使用 Dirname、Normpath、Realpath、Join 或其他路徑操作工具的方式相同。</span><span class="sxs-lookup"><span data-stu-id="8ab14-167">Use them like you would use Dirname, Normpath, Realpath, Join, or other path manipulators.</span></span>

<span data-ttu-id="8ab14-168">您可以搭配多個提供者使用 path Cmdlet，包括 `FileSystem` 、 `Registry` 和 `Certificate` 提供者。</span><span class="sxs-lookup"><span data-stu-id="8ab14-168">You can use the path cmdlets with several providers, including the `FileSystem`, `Registry`, and `Certificate` providers.</span></span>

<span data-ttu-id="8ab14-169">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="8ab14-169">This cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="8ab14-170">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="8ab14-170">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="8ab14-171">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="8ab14-171">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="8ab14-172">相關連結</span><span class="sxs-lookup"><span data-stu-id="8ab14-172">RELATED LINKS</span></span>

[<span data-ttu-id="8ab14-173">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="8ab14-173">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="8ab14-174">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="8ab14-174">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="8ab14-175">Split-Path</span><span class="sxs-lookup"><span data-stu-id="8ab14-175">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="8ab14-176">Test-Path</span><span class="sxs-lookup"><span data-stu-id="8ab14-176">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="8ab14-177">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="8ab14-177">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="8ab14-178">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="8ab14-178">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="8ab14-179">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="8ab14-179">Get-PSDrive</span></span>](Get-PSDrive.md)

