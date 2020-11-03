---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: c0ee5552e33792f208faba63dc05ddb93473bc49
ms.sourcegitcommit: 9a53e53e7a3ef9ac0a212c61005efff9e9902452
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "93206095"
---
# <span data-ttu-id="05441-103">Split-Path</span><span class="sxs-lookup"><span data-stu-id="05441-103">Split-Path</span></span>

## <span data-ttu-id="05441-104">概要</span><span class="sxs-lookup"><span data-stu-id="05441-104">SYNOPSIS</span></span>
<span data-ttu-id="05441-105">傳回路徑的指定部分。</span><span class="sxs-lookup"><span data-stu-id="05441-105">Returns the specified part of a path.</span></span>

## <span data-ttu-id="05441-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="05441-106">SYNTAX</span></span>

### <span data-ttu-id="05441-107">ParentSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="05441-107">ParentSet (Default)</span></span>

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="05441-108">LeafSet</span><span class="sxs-lookup"><span data-stu-id="05441-108">LeafSet</span></span>

```
Split-Path [-Path] <String[]> -Leaf [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="05441-109">LeafBaseSet</span><span class="sxs-lookup"><span data-stu-id="05441-109">LeafBaseSet</span></span>

```
Split-Path [-Path] <String[]> -LeafBase [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="05441-110">ExtensionSet</span><span class="sxs-lookup"><span data-stu-id="05441-110">ExtensionSet</span></span>

```
Split-Path [-Path] <String[]> -Extension [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="05441-111">QualifierSet</span><span class="sxs-lookup"><span data-stu-id="05441-111">QualifierSet</span></span>

```
Split-Path [-Path] <String[]> -Qualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="05441-112">NoQualifierSet</span><span class="sxs-lookup"><span data-stu-id="05441-112">NoQualifierSet</span></span>

```
Split-Path [-Path] <String[]> -NoQualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="05441-113">IsAbsoluteSet</span><span class="sxs-lookup"><span data-stu-id="05441-113">IsAbsoluteSet</span></span>

```
Split-Path [-Path] <String[]> [-Resolve] -IsAbsolute [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="05441-114">LiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="05441-114">LiteralPathSet</span></span>

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="05441-115">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="05441-115">DESCRIPTION</span></span>

<span data-ttu-id="05441-116">此 `Split-Path` Cmdlet 只會傳回路徑的指定部分，例如上層資料夾、子資料夾或檔案名。</span><span class="sxs-lookup"><span data-stu-id="05441-116">The `Split-Path` cmdlet returns only the specified part of a path, such as the parent folder, a subfolder, or a file name.</span></span> <span data-ttu-id="05441-117">它也可以取得分割路徑所參照的項目，並分辨路徑是相對路徑或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="05441-117">It can also get items that are referenced by the split path and tell whether the path is relative or absolute.</span></span>

<span data-ttu-id="05441-118">您可以使用這個 Cmdlet 來只取得或只送出路徑的選取部分。</span><span class="sxs-lookup"><span data-stu-id="05441-118">You can use this cmdlet to get or submit only a selected part of a path.</span></span>

## <span data-ttu-id="05441-119">範例</span><span class="sxs-lookup"><span data-stu-id="05441-119">EXAMPLES</span></span>

### <span data-ttu-id="05441-120">範例1：取得路徑的辨識符號</span><span class="sxs-lookup"><span data-stu-id="05441-120">Example 1: Get the qualifier of a path</span></span>

```powershell
Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
```

```Output
HKCU:
```

<span data-ttu-id="05441-121">此命令只會傳回路徑的辨識符號。</span><span class="sxs-lookup"><span data-stu-id="05441-121">This command returns only the qualifier of the path.</span></span> <span data-ttu-id="05441-122">辨識符號是磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="05441-122">The qualifier is the drive.</span></span>

### <span data-ttu-id="05441-123">範例2：顯示檔案名</span><span class="sxs-lookup"><span data-stu-id="05441-123">Example 2: Display file names</span></span>

```powershell
Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
```

```Output
Pass1.log
Pass2.log
...
```

<span data-ttu-id="05441-124">這個命令會顯示分割路徑所參照的檔案。</span><span class="sxs-lookup"><span data-stu-id="05441-124">This command displays the files that are referenced by the split path.</span></span> <span data-ttu-id="05441-125">因為此路徑會分割至最後一個專案（也稱為分葉），所以命令只會顯示檔案名。</span><span class="sxs-lookup"><span data-stu-id="05441-125">Because this path is split to the last item, also known as the leaf, the command displays only the file names.</span></span>

<span data-ttu-id="05441-126">**Resolve** 參數會告訴您 `Split-Path` 顯示分割路徑所參考的專案，而不是顯示分割路徑。</span><span class="sxs-lookup"><span data-stu-id="05441-126">The **Resolve** parameter tells `Split-Path` to display the items that the split path references, instead of displaying the split path.</span></span>

<span data-ttu-id="05441-127">如同所有 `Split-Path` 命令，此命令會傳回字串。</span><span class="sxs-lookup"><span data-stu-id="05441-127">Like all `Split-Path` commands, this command returns strings.</span></span> <span data-ttu-id="05441-128">它不會傳回代表檔案的 **FileInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="05441-128">It does not return **FileInfo** objects that represent the files.</span></span>

### <span data-ttu-id="05441-129">範例3：取得父容器</span><span class="sxs-lookup"><span data-stu-id="05441-129">Example 3: Get the parent container</span></span>

```powershell
Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
```

```Output
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

<span data-ttu-id="05441-130">這個命令只會傳回路徑的父容器。</span><span class="sxs-lookup"><span data-stu-id="05441-130">This command returns only the parent containers of the path.</span></span> <span data-ttu-id="05441-131">因為它不包含任何用來指定分割的參數，所以會 `Split-Path` 使用預設的分割位置，也就是 **父系** 。</span><span class="sxs-lookup"><span data-stu-id="05441-131">Because it does not include any parameters to specify the split, `Split-Path` uses the split location default, which is **Parent** .</span></span>

### <span data-ttu-id="05441-132">範例4：判斷路徑是否為絕對路徑</span><span class="sxs-lookup"><span data-stu-id="05441-132">Example 4: Determines whether a path is absolute</span></span>

```powershell
Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
```

```Output
False
```

<span data-ttu-id="05441-133">這個命令會判斷路徑是相對路徑或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="05441-133">This command determines whether the path is relative or absolute.</span></span> <span data-ttu-id="05441-134">在此情況下，因為路徑相對於目前的資料夾，而該資料夾是以點 (`.`) 表示，所以會傳回 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="05441-134">In this case, because the path is relative to the current folder, which is represented by a dot (`.`), it returns `$False`.</span></span>

### <span data-ttu-id="05441-135">範例5：將位置變更為指定的路徑</span><span class="sxs-lookup"><span data-stu-id="05441-135">Example 5: Change location to a specified path</span></span>

```powershell
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

<span data-ttu-id="05441-136">此命令會將您的位置變更為包含 PowerShell 設定檔的資料夾。</span><span class="sxs-lookup"><span data-stu-id="05441-136">This command changes your location to the folder that contains the PowerShell profile.</span></span>

<span data-ttu-id="05441-137">括弧中的命令會使用 `Split-Path` ，只傳回內建變數中所儲存之路徑的父系 `$Profile` 。</span><span class="sxs-lookup"><span data-stu-id="05441-137">The command in parentheses uses `Split-Path` to return only the parent of the path stored in the built-in `$Profile` variable.</span></span> <span data-ttu-id="05441-138">**Parent** 參數是預設的分割位置參數。</span><span class="sxs-lookup"><span data-stu-id="05441-138">The **Parent** parameter is the default split location parameter.</span></span>
<span data-ttu-id="05441-139">因此，您可以在命令中省略它。</span><span class="sxs-lookup"><span data-stu-id="05441-139">Therefore, you can omit it from the command.</span></span> <span data-ttu-id="05441-140">括弧直接 PowerShell 以執行命令。</span><span class="sxs-lookup"><span data-stu-id="05441-140">The parentheses direct PowerShell to run the command first.</span></span> <span data-ttu-id="05441-141">這是移至具有完整路徑名稱之資料夾的實用方式。</span><span class="sxs-lookup"><span data-stu-id="05441-141">This is a useful way to move to a folder that has a long path name.</span></span>

### <span data-ttu-id="05441-142">範例6：使用管線分割路徑</span><span class="sxs-lookup"><span data-stu-id="05441-142">Example 6: Split a path by using the pipeline</span></span>

```powershell
'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
```

```Output
C:\Documents and Settings\User01\My Documents
```

<span data-ttu-id="05441-143">此命令會使用管線運算子 (`|`) 傳送的路徑 `Split-Path` 。</span><span class="sxs-lookup"><span data-stu-id="05441-143">This command uses a pipeline operator (`|`) to send a path to `Split-Path`.</span></span> <span data-ttu-id="05441-144">此路徑是括在引號中來表示它是單一語彙基元。</span><span class="sxs-lookup"><span data-stu-id="05441-144">The path is enclosed in quotation marks to indicate that it is a single token.</span></span>

## <span data-ttu-id="05441-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="05441-145">PARAMETERS</span></span>

### <span data-ttu-id="05441-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="05441-146">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="05441-147">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="05441-147">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="05441-148">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="05441-148">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="05441-149">-擴充</span><span class="sxs-lookup"><span data-stu-id="05441-149">-Extension</span></span>

<span data-ttu-id="05441-150">指出這個 Cmdlet 只會傳回分葉的延伸。</span><span class="sxs-lookup"><span data-stu-id="05441-150">Indicates that this cmdlet returns only the extension of the leaf.</span></span> <span data-ttu-id="05441-151">例如，在路徑中 `C:\Test\Logs\Pass1.log` ，它只會傳回 `.log` 。</span><span class="sxs-lookup"><span data-stu-id="05441-151">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `.log`.</span></span>

<span data-ttu-id="05441-152">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="05441-152">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ExtensionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="05441-153">-IsAbsolute</span><span class="sxs-lookup"><span data-stu-id="05441-153">-IsAbsolute</span></span>

<span data-ttu-id="05441-154">指出如果路徑是絕對路徑，此 Cmdlet 會傳回 $True，如果是相對路徑，則會傳回 $False。</span><span class="sxs-lookup"><span data-stu-id="05441-154">Indicates that this cmdlet returns $True if the path is absolute and $False if it is relative.</span></span> <span data-ttu-id="05441-155">絕對路徑的長度大於零，且不會使用點 (`.`) 來指出目前的路徑。</span><span class="sxs-lookup"><span data-stu-id="05441-155">An absolute path has a length greater than zero and does not use a dot (`.`) to indicate the current path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="05441-156">-Leaf</span><span class="sxs-lookup"><span data-stu-id="05441-156">-Leaf</span></span>

<span data-ttu-id="05441-157">指出此 Cmdlet 只會傳回路徑中的最後一個專案或容器。</span><span class="sxs-lookup"><span data-stu-id="05441-157">Indicates that this cmdlet returns only the last item or container in the path.</span></span> <span data-ttu-id="05441-158">例如，在路徑中 `C:\Test\Logs\Pass1.log` ，它只會傳回 pass1.log .log。</span><span class="sxs-lookup"><span data-stu-id="05441-158">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="05441-159">-LeafBase</span><span class="sxs-lookup"><span data-stu-id="05441-159">-LeafBase</span></span>

<span data-ttu-id="05441-160">指出此 Cmdlet 只會傳回分葉的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="05441-160">Indicates that this cmdlet returns only base name of the leaf.</span></span> <span data-ttu-id="05441-161">例如，在路徑中 `C:\Test\Logs\Pass1.log` ，它只會傳回 `Pass1` 。</span><span class="sxs-lookup"><span data-stu-id="05441-161">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `Pass1`.</span></span>

<span data-ttu-id="05441-162">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="05441-162">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafBaseSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="05441-163">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="05441-163">-LiteralPath</span></span>

<span data-ttu-id="05441-164">指定要分割的路徑。</span><span class="sxs-lookup"><span data-stu-id="05441-164">Specifies the paths to be split.</span></span> <span data-ttu-id="05441-165">與 **Path** 不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="05441-165">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="05441-166">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="05441-166">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="05441-167">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="05441-167">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="05441-168">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="05441-168">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="05441-169">-NoQualifier</span><span class="sxs-lookup"><span data-stu-id="05441-169">-NoQualifier</span></span>

<span data-ttu-id="05441-170">指出此 Cmdlet 會傳回不含限定詞的路徑。</span><span class="sxs-lookup"><span data-stu-id="05441-170">Indicates that this cmdlet returns the path without the qualifier.</span></span> <span data-ttu-id="05441-171">針對 FileSystem 或登錄提供者，限定詞是提供者路徑的磁片磁碟機，例如 `C:` 或 `HKCU:` 。</span><span class="sxs-lookup"><span data-stu-id="05441-171">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span> <span data-ttu-id="05441-172">例如，在路徑中 `C:\Test\Logs\Pass1.log` ，它只會傳回 `\Test\Logs\Pass1.log` 。</span><span class="sxs-lookup"><span data-stu-id="05441-172">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `\Test\Logs\Pass1.log`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="05441-173">-Parent</span><span class="sxs-lookup"><span data-stu-id="05441-173">-Parent</span></span>

<span data-ttu-id="05441-174">指出此 Cmdlet 只會傳回該路徑所指定之專案或容器的父容器。</span><span class="sxs-lookup"><span data-stu-id="05441-174">Indicates that this cmdlet returns only the parent containers of the item or of the container specified by the path.</span></span> <span data-ttu-id="05441-175">例如，在路徑中 `C:\Test\Logs\Pass1.log` ，它會傳回 `C:\Test\Logs` 。</span><span class="sxs-lookup"><span data-stu-id="05441-175">For example, in the path `C:\Test\Logs\Pass1.log`, it returns `C:\Test\Logs`.</span></span>
<span data-ttu-id="05441-176">**Parent** 參數是預設的分割位置參數。</span><span class="sxs-lookup"><span data-stu-id="05441-176">The **Parent** parameter is the default split location parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParentSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="05441-177">-Path</span><span class="sxs-lookup"><span data-stu-id="05441-177">-Path</span></span>

<span data-ttu-id="05441-178">指定要分割的路徑。</span><span class="sxs-lookup"><span data-stu-id="05441-178">Specifies the paths to be split.</span></span> <span data-ttu-id="05441-179">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="05441-179">Wildcard characters are permitted.</span></span> <span data-ttu-id="05441-180">如果路徑包含空格，請將它括在引號中。</span><span class="sxs-lookup"><span data-stu-id="05441-180">If the path includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="05441-181">您也可以使用管線將路徑傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="05441-181">You can also pipe a path to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ParentSet, LeafSet, LeafBaseSet, ExtensionSet, QualifierSet, NoQualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="05441-182">-Qualifier</span><span class="sxs-lookup"><span data-stu-id="05441-182">-Qualifier</span></span>

<span data-ttu-id="05441-183">指出此 Cmdlet 只會傳回指定路徑的辨識符號。</span><span class="sxs-lookup"><span data-stu-id="05441-183">Indicates that this cmdlet returns only the qualifier of the specified path.</span></span> <span data-ttu-id="05441-184">針對 FileSystem 或登錄提供者，限定詞是提供者路徑的磁片磁碟機，例如 `C:` 或 `HKCU:` 。</span><span class="sxs-lookup"><span data-stu-id="05441-184">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="05441-185">-Resolve</span><span class="sxs-lookup"><span data-stu-id="05441-185">-Resolve</span></span>

<span data-ttu-id="05441-186">指出此 Cmdlet 會顯示產生之分割路徑所參考的專案，而不是顯示路徑元素。</span><span class="sxs-lookup"><span data-stu-id="05441-186">Indicates that this cmdlet displays the items that are referenced by the resulting split path instead of displaying the path elements.</span></span>

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

### <span data-ttu-id="05441-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="05441-187">CommonParameters</span></span>

<span data-ttu-id="05441-188">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="05441-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="05441-189">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="05441-189">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="05441-190">輸入</span><span class="sxs-lookup"><span data-stu-id="05441-190">INPUTS</span></span>

### <span data-ttu-id="05441-191">System.String</span><span class="sxs-lookup"><span data-stu-id="05441-191">System.String</span></span>

<span data-ttu-id="05441-192">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="05441-192">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="05441-193">輸出</span><span class="sxs-lookup"><span data-stu-id="05441-193">OUTPUTS</span></span>

### <span data-ttu-id="05441-194">System.String、System.Boolean</span><span class="sxs-lookup"><span data-stu-id="05441-194">System.String, System.Boolean</span></span>

<span data-ttu-id="05441-195">`Split-Path` 傳回文字字串。</span><span class="sxs-lookup"><span data-stu-id="05441-195">`Split-Path` returns text strings.</span></span> <span data-ttu-id="05441-196">當您指定 **Resolve** 參數時， `Split-Path` 會傳回描述專案位置的字串，而不會傳回代表專案的物件，例如 **FileInfo** 或 **RegistryKey** 物件。</span><span class="sxs-lookup"><span data-stu-id="05441-196">When you specify the **Resolve** parameter, `Split-Path` returns a string that describes the location of the items; it does not return objects that represent the items, such as a **FileInfo** or **RegistryKey** object.</span></span>

<span data-ttu-id="05441-197">當您指定 **IsAbsolute** 參數時，會傳回 `Split-Path` **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="05441-197">When you specify the **IsAbsolute** parameter, `Split-Path` returns a **Boolean** value.</span></span>

## <span data-ttu-id="05441-198">注意</span><span class="sxs-lookup"><span data-stu-id="05441-198">NOTES</span></span>

- <span data-ttu-id="05441-199">分割位置參數 (辨識 **符號** 、 **父系** 、 **延伸** 模組、分 **葉** 、 **LeafBase** 和 **NoQualifier** ) 是專屬的。</span><span class="sxs-lookup"><span data-stu-id="05441-199">The split location parameters ( **Qualifier** , **Parent** , **Extension** , **Leaf** , **LeafBase** , and **NoQualifier** ) are exclusive.</span></span> <span data-ttu-id="05441-200">在每個命令中只能使用一個。</span><span class="sxs-lookup"><span data-stu-id="05441-200">You can use only one in each command.</span></span>

- <span data-ttu-id="05441-201">包含路徑名詞 (Path **Cmdlet 的 Cmdlet** 會 **Path** ) 使用路徑名稱，並傳回所有 PowerShell 提供者都可解讀的精簡格式名稱。</span><span class="sxs-lookup"><span data-stu-id="05441-201">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="05441-202">它們是設計用於程式與指令碼，您可以在其中以特定格式顯示所有或部分路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="05441-202">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="05441-203">使用 **Dirname** 、 **Normpath** 、 **Realpath** 、 **Join** 或其他路徑操作工具的方式來使用它們。</span><span class="sxs-lookup"><span data-stu-id="05441-203">Use them in the way that you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

- <span data-ttu-id="05441-204">您可以搭配多個提供者使用 **Path** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="05441-204">You can use the **Path** cmdlets together with several providers.</span></span> <span data-ttu-id="05441-205">其中包括 FileSystem、Registry 和 Certificate provider。</span><span class="sxs-lookup"><span data-stu-id="05441-205">These include the FileSystem, Registry, and Certificate providers.</span></span>

- <span data-ttu-id="05441-206">`Split-Path` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="05441-206">`Split-Path` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="05441-207">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="05441-207">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="05441-208">如需詳細資訊，請參閱 about_Providers。</span><span class="sxs-lookup"><span data-stu-id="05441-208">For more information, see about_Providers.</span></span>

## <span data-ttu-id="05441-209">相關連結</span><span class="sxs-lookup"><span data-stu-id="05441-209">RELATED LINKS</span></span>

[<span data-ttu-id="05441-210">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="05441-210">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="05441-211">Join-Path</span><span class="sxs-lookup"><span data-stu-id="05441-211">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="05441-212">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="05441-212">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="05441-213">Test-Path</span><span class="sxs-lookup"><span data-stu-id="05441-213">Test-Path</span></span>](Test-Path.md)
