---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: 5d92acbe080b0d232047f1184c9a369b8837845c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203487"
---
# <span data-ttu-id="3e583-103">Split-Path</span><span class="sxs-lookup"><span data-stu-id="3e583-103">Split-Path</span></span>

## <span data-ttu-id="3e583-104">概要</span><span class="sxs-lookup"><span data-stu-id="3e583-104">SYNOPSIS</span></span>
<span data-ttu-id="3e583-105">傳回路徑的指定部分。</span><span class="sxs-lookup"><span data-stu-id="3e583-105">Returns the specified part of a path.</span></span>

## <span data-ttu-id="3e583-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3e583-106">SYNTAX</span></span>

### <span data-ttu-id="3e583-107">ParentSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="3e583-107">ParentSet (Default)</span></span>

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="3e583-108">NoQualifierSet</span><span class="sxs-lookup"><span data-stu-id="3e583-108">NoQualifierSet</span></span>

```
Split-Path [-Path] <String[]> [-NoQualifier] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="3e583-109">LeafSet</span><span class="sxs-lookup"><span data-stu-id="3e583-109">LeafSet</span></span>

```
Split-Path [-Path] <String[]> [-Leaf] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="3e583-110">QualifierSet</span><span class="sxs-lookup"><span data-stu-id="3e583-110">QualifierSet</span></span>

```
Split-Path [-Path] <String[]> [-Qualifier] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="3e583-111">IsAbsoluteSet</span><span class="sxs-lookup"><span data-stu-id="3e583-111">IsAbsoluteSet</span></span>

```
Split-Path [-Path] <String[]> [-Resolve] [-IsAbsolute] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="3e583-112">LiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="3e583-112">LiteralPathSet</span></span>

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="3e583-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3e583-113">DESCRIPTION</span></span>

<span data-ttu-id="3e583-114">**分割路徑** Cmdlet 只會傳回路徑的指定部分，例如上層資料夾、子資料夾或檔案名。</span><span class="sxs-lookup"><span data-stu-id="3e583-114">The **Split-Path** cmdlet returns only the specified part of a path, such as the parent folder, a subfolder, or a file name.</span></span>
<span data-ttu-id="3e583-115">它也可以取得分割路徑所參照的項目，並分辨路徑是相對路徑或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="3e583-115">It can also get items that are referenced by the split path and tell whether the path is relative or absolute.</span></span>

<span data-ttu-id="3e583-116">您可以使用這個 Cmdlet 來只取得或只送出路徑的選取部分。</span><span class="sxs-lookup"><span data-stu-id="3e583-116">You can use this cmdlet to get or submit only a selected part of a path.</span></span>

## <span data-ttu-id="3e583-117">範例</span><span class="sxs-lookup"><span data-stu-id="3e583-117">EXAMPLES</span></span>

### <span data-ttu-id="3e583-118">範例1：取得路徑的辨識符號</span><span class="sxs-lookup"><span data-stu-id="3e583-118">Example 1: Get the qualifier of a path</span></span>

```
PS C:\> Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
HKCU:
```

<span data-ttu-id="3e583-119">此命令只會傳回路徑的辨識符號。</span><span class="sxs-lookup"><span data-stu-id="3e583-119">This command returns only the qualifier of the path.</span></span>
<span data-ttu-id="3e583-120">辨識符號是磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="3e583-120">The qualifier is the drive.</span></span>

### <span data-ttu-id="3e583-121">範例2：顯示檔案名</span><span class="sxs-lookup"><span data-stu-id="3e583-121">Example 2: Display file names</span></span>

```
PS C:\> Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
Pass1.log
Pass2.log
...
```

<span data-ttu-id="3e583-122">這個命令會顯示分割路徑所參照的檔案。</span><span class="sxs-lookup"><span data-stu-id="3e583-122">This command displays the files that are referenced by the split path.</span></span>
<span data-ttu-id="3e583-123">因為此路徑會分割至最後一個專案（也稱為分葉），所以命令只會顯示檔案名。</span><span class="sxs-lookup"><span data-stu-id="3e583-123">Because this path is split to the last item, also known as the leaf, the command displays only the file names.</span></span>

<span data-ttu-id="3e583-124">*Resolve* 參數會告訴 **分割路徑** 顯示分割路徑所參考的專案，而不是顯示分割路徑。</span><span class="sxs-lookup"><span data-stu-id="3e583-124">The *Resolve* parameter tells **Split-Path** to display the items that the split path references, instead of displaying the split path.</span></span>

<span data-ttu-id="3e583-125">如同所有 **分割路徑** 命令，此命令會傳回字串。</span><span class="sxs-lookup"><span data-stu-id="3e583-125">Like all **Split-Path** commands, this command returns strings.</span></span>
<span data-ttu-id="3e583-126">它不會傳回代表檔案的 **FileInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="3e583-126">It does not return **FileInfo** objects that represent the files.</span></span>

### <span data-ttu-id="3e583-127">範例3：取得父容器</span><span class="sxs-lookup"><span data-stu-id="3e583-127">Example 3: Get the parent container</span></span>

```
PS C:\> Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

<span data-ttu-id="3e583-128">這個命令只會傳回路徑的父容器。</span><span class="sxs-lookup"><span data-stu-id="3e583-128">This command returns only the parent containers of the path.</span></span>
<span data-ttu-id="3e583-129">因為它不包含任何用來指定分割的參數，所以 **分割路徑** 會使用預設的分割位置，也就是 *父系* 。</span><span class="sxs-lookup"><span data-stu-id="3e583-129">Because it does not include any parameters to specify the split, **Split-Path** uses the split location default, which is *Parent* .</span></span>

### <span data-ttu-id="3e583-130">範例4：判斷路徑是否為絕對路徑</span><span class="sxs-lookup"><span data-stu-id="3e583-130">Example 4: Determines whether a path is absolute</span></span>

```
PS C:\> Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
False
```

<span data-ttu-id="3e583-131">這個命令會判斷路徑是相對路徑或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="3e583-131">This command determines whether the path is relative or absolute.</span></span>
<span data-ttu-id="3e583-132">在此情況下，因為路徑相對於目前的資料夾，而該資料夾是以點 ( ) ，所以會傳回 $False。</span><span class="sxs-lookup"><span data-stu-id="3e583-132">In this case, because the path is relative to the current folder, which is represented by a dot (.), it returns $False.</span></span>

### <span data-ttu-id="3e583-133">範例5：將位置變更為指定的路徑</span><span class="sxs-lookup"><span data-stu-id="3e583-133">Example 5: Change location to a specified path</span></span>

```
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

<span data-ttu-id="3e583-134">此命令會將您的位置變更為包含 PowerShell 設定檔的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3e583-134">This command changes your location to the folder that contains the PowerShell profile.</span></span>

<span data-ttu-id="3e583-135">括弧中的命令會使用 **分割路徑** ，只傳回內建 $Profile 變數中所儲存之路徑的父系。</span><span class="sxs-lookup"><span data-stu-id="3e583-135">The command in parentheses uses **Split-Path** to return only the parent of the path stored in the built-in $Profile variable.</span></span>
<span data-ttu-id="3e583-136">*Parent* 參數是預設的分割位置參數。</span><span class="sxs-lookup"><span data-stu-id="3e583-136">The *Parent* parameter is the default split location parameter.</span></span>
<span data-ttu-id="3e583-137">因此，您可以在命令中省略它。</span><span class="sxs-lookup"><span data-stu-id="3e583-137">Therefore, you can omit it from the command.</span></span>
<span data-ttu-id="3e583-138">括弧直接 PowerShell 以執行命令。</span><span class="sxs-lookup"><span data-stu-id="3e583-138">The parentheses direct PowerShell to run the command first.</span></span>
<span data-ttu-id="3e583-139">這是移至具有完整路徑名稱之資料夾的實用方式。</span><span class="sxs-lookup"><span data-stu-id="3e583-139">This is a useful way to move to a folder that has a long path name.</span></span>

### <span data-ttu-id="3e583-140">範例6：使用管線分割路徑</span><span class="sxs-lookup"><span data-stu-id="3e583-140">Example 6: Split a path by using the pipeline</span></span>

```
PS C:\> 'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
C:\Documents and Settings\User01\My Documents
```

<span data-ttu-id="3e583-141">此命令會使用管線運算子 (|) 傳送 **分割路徑** 的路徑。</span><span class="sxs-lookup"><span data-stu-id="3e583-141">This command uses a pipeline operator (|) to send a path to **Split-Path** .</span></span>
<span data-ttu-id="3e583-142">此路徑是括在引號中來表示它是單一語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3e583-142">The path is enclosed in quotation marks to indicate that it is a single token.</span></span>

## <span data-ttu-id="3e583-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3e583-143">PARAMETERS</span></span>

### <span data-ttu-id="3e583-144">-Credential</span><span class="sxs-lookup"><span data-stu-id="3e583-144">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="3e583-145">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="3e583-145">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="3e583-146">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="3e583-146">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="3e583-147">-IsAbsolute</span><span class="sxs-lookup"><span data-stu-id="3e583-147">-IsAbsolute</span></span>

<span data-ttu-id="3e583-148">指出如果路徑是絕對路徑，此 Cmdlet 會傳回 $True，如果是相對路徑，則會傳回 $False。</span><span class="sxs-lookup"><span data-stu-id="3e583-148">Indicates that this cmdlet returns $True if the path is absolute and $False if it is relative.</span></span>
<span data-ttu-id="3e583-149">絕對路徑的長度大於零，且不會使用點 (。 ) 表示目前的路徑。</span><span class="sxs-lookup"><span data-stu-id="3e583-149">An absolute path has a length greater than zero and does not use a dot (.) to indicate the current path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e583-150">-Leaf</span><span class="sxs-lookup"><span data-stu-id="3e583-150">-Leaf</span></span>

<span data-ttu-id="3e583-151">指出此 Cmdlet 只會傳回路徑中的最後一個專案或容器。</span><span class="sxs-lookup"><span data-stu-id="3e583-151">Indicates that this cmdlet returns only the last item or container in the path.</span></span>
<span data-ttu-id="3e583-152">例如，在路徑中 `C:\Test\Logs\Pass1.log` ，它只會傳回 pass1.log .log。</span><span class="sxs-lookup"><span data-stu-id="3e583-152">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e583-153">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3e583-153">-LiteralPath</span></span>

<span data-ttu-id="3e583-154">指定要分割的路徑。</span><span class="sxs-lookup"><span data-stu-id="3e583-154">Specifies the paths to be split.</span></span>
<span data-ttu-id="3e583-155">與 *Path* 不同， *LiteralPath* 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="3e583-155">Unlike *Path* , the value of *LiteralPath* is used exactly as it is typed.</span></span>
<span data-ttu-id="3e583-156">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="3e583-156">No characters are interpreted as wildcard characters.</span></span>
<span data-ttu-id="3e583-157">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="3e583-157">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="3e583-158">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="3e583-158">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e583-159">-NoQualifier</span><span class="sxs-lookup"><span data-stu-id="3e583-159">-NoQualifier</span></span>

<span data-ttu-id="3e583-160">指出此 Cmdlet 會傳回不含限定詞的路徑。</span><span class="sxs-lookup"><span data-stu-id="3e583-160">Indicates that this cmdlet returns the path without the qualifier.</span></span>
<span data-ttu-id="3e583-161">對 FileSystem 或登錄提供者來說，限定詞是提供者路徑的磁碟機，例如 C: 或 HKCU:。</span><span class="sxs-lookup"><span data-stu-id="3e583-161">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as C: or HKCU:.</span></span>
<span data-ttu-id="3e583-162">例如，在路徑中 `C:\Test\Logs\Pass1.log` ，它只會傳回 \Test\Logs\Pass1.log。</span><span class="sxs-lookup"><span data-stu-id="3e583-162">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only \Test\Logs\Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e583-163">-Parent</span><span class="sxs-lookup"><span data-stu-id="3e583-163">-Parent</span></span>

<span data-ttu-id="3e583-164">指出此 Cmdlet 只會傳回該路徑所指定之專案或容器的父容器。</span><span class="sxs-lookup"><span data-stu-id="3e583-164">Indicates that this cmdlet returns only the parent containers of the item or of the container specified by the path.</span></span>
<span data-ttu-id="3e583-165">例如，在路徑中 `C:\Test\Logs\Pass1.log` ，它會傳回 C:\Test\Logs。</span><span class="sxs-lookup"><span data-stu-id="3e583-165">For example, in the path `C:\Test\Logs\Pass1.log`, it returns C:\Test\Logs.</span></span>
<span data-ttu-id="3e583-166">*Parent* 參數是預設的分割位置參數。</span><span class="sxs-lookup"><span data-stu-id="3e583-166">The *Parent* parameter is the default split location parameter.</span></span>

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

### <span data-ttu-id="3e583-167">-Path</span><span class="sxs-lookup"><span data-stu-id="3e583-167">-Path</span></span>

<span data-ttu-id="3e583-168">指定要分割的路徑。</span><span class="sxs-lookup"><span data-stu-id="3e583-168">Specifies the paths to be split.</span></span>
<span data-ttu-id="3e583-169">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="3e583-169">Wildcard characters are permitted.</span></span>
<span data-ttu-id="3e583-170">如果路徑包含空格，請將它括在引號中。</span><span class="sxs-lookup"><span data-stu-id="3e583-170">If the path includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="3e583-171">您也可以使用管線將路徑傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3e583-171">You can also pipe a path to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ParentSet, NoQualifierSet, LeafSet, QualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="3e583-172">-Qualifier</span><span class="sxs-lookup"><span data-stu-id="3e583-172">-Qualifier</span></span>

<span data-ttu-id="3e583-173">指出此 Cmdlet 只會傳回指定路徑的辨識符號。</span><span class="sxs-lookup"><span data-stu-id="3e583-173">Indicates that this cmdlet returns only the qualifier of the specified path.</span></span>
<span data-ttu-id="3e583-174">對 FileSystem 或登錄提供者來說，限定詞是提供者路徑的磁碟機，例如 C: 或 HKCU:。</span><span class="sxs-lookup"><span data-stu-id="3e583-174">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as C: or HKCU:.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e583-175">-Resolve</span><span class="sxs-lookup"><span data-stu-id="3e583-175">-Resolve</span></span>

<span data-ttu-id="3e583-176">指出此 Cmdlet 會顯示產生之分割路徑所參考的專案，而不是顯示路徑元素。</span><span class="sxs-lookup"><span data-stu-id="3e583-176">Indicates that this cmdlet displays the items that are referenced by the resulting split path instead of displaying the path elements.</span></span>

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

### <span data-ttu-id="3e583-177">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="3e583-177">-UseTransaction</span></span>

<span data-ttu-id="3e583-178">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="3e583-178">Includes the command in the active transaction.</span></span>
<span data-ttu-id="3e583-179">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="3e583-179">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="3e583-180">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="3e583-180">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="3e583-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e583-181">CommonParameters</span></span>

<span data-ttu-id="3e583-182">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3e583-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e583-183">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3e583-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3e583-184">輸入</span><span class="sxs-lookup"><span data-stu-id="3e583-184">INPUTS</span></span>

### <span data-ttu-id="3e583-185">System.String</span><span class="sxs-lookup"><span data-stu-id="3e583-185">System.String</span></span>

<span data-ttu-id="3e583-186">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3e583-186">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="3e583-187">輸出</span><span class="sxs-lookup"><span data-stu-id="3e583-187">OUTPUTS</span></span>

### <span data-ttu-id="3e583-188">System.String、System.Boolean</span><span class="sxs-lookup"><span data-stu-id="3e583-188">System.String, System.Boolean</span></span>

<span data-ttu-id="3e583-189">**分割路徑** 會傳回文字字串。</span><span class="sxs-lookup"><span data-stu-id="3e583-189">**Split-Path** returns text strings.</span></span>
<span data-ttu-id="3e583-190">當您指定 *Resolve* 參數時， **分割路徑** 會傳回描述專案位置的字串。它不會傳回代表專案的物件，例如 **FileInfo** 或 **RegistryKey** 物件。</span><span class="sxs-lookup"><span data-stu-id="3e583-190">When you specify the *Resolve* parameter, **Split-Path** returns a string that describes the location of the items; it does not return objects that represent the items, such as a **FileInfo** or **RegistryKey** object.</span></span>

<span data-ttu-id="3e583-191">當您指定 *IsAbsolute* 參數時， **分割路徑** 會傳回 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="3e583-191">When you specify the *IsAbsolute* parameter, **Split-Path** returns a **Boolean** value.</span></span>

## <span data-ttu-id="3e583-192">注意</span><span class="sxs-lookup"><span data-stu-id="3e583-192">NOTES</span></span>

* <span data-ttu-id="3e583-193"> (辨識 *符號* 、 *父系* 、分 *葉* 和 *NoQualifier* ) 的分割位置參數是獨佔的。</span><span class="sxs-lookup"><span data-stu-id="3e583-193">The split location parameters ( *Qualifier* , *Parent* , *Leaf* , and *NoQualifier* ) are exclusive.</span></span> <span data-ttu-id="3e583-194">在每個命令中只能使用一個。</span><span class="sxs-lookup"><span data-stu-id="3e583-194">You can use only one in each command.</span></span>

  <span data-ttu-id="3e583-195">包含路徑名詞 (Path **Cmdlet 的 Cmdlet** 會 **Path** ) 使用路徑名稱，並傳回所有 PowerShell 提供者都可解讀的精簡格式名稱。</span><span class="sxs-lookup"><span data-stu-id="3e583-195">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span>
<span data-ttu-id="3e583-196">它們是設計用於程式與指令碼，您可以在其中以特定格式顯示所有或部分路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="3e583-196">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span>
<span data-ttu-id="3e583-197">使用 **Dirname** 、 **Normpath** 、 **Realpath** 、 **Join** 或其他路徑操作工具的方式來使用它們。</span><span class="sxs-lookup"><span data-stu-id="3e583-197">Use them in the way that you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

  <span data-ttu-id="3e583-198">您可以搭配多個提供者使用 **Path** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3e583-198">You can use the **Path** cmdlets together with several providers.</span></span>
<span data-ttu-id="3e583-199">其中包括 FileSystem、Registry 和 Certificate provider。</span><span class="sxs-lookup"><span data-stu-id="3e583-199">These include the FileSystem, Registry, and Certificate providers.</span></span>

  <span data-ttu-id="3e583-200">**分割路徑** 是設計來與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="3e583-200">**Split-Path** is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="3e583-201">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="3e583-201">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="3e583-202">如需詳細資訊，請參閱 about_Providers。</span><span class="sxs-lookup"><span data-stu-id="3e583-202">For more information, see about_Providers.</span></span>

## <span data-ttu-id="3e583-203">相關連結</span><span class="sxs-lookup"><span data-stu-id="3e583-203">RELATED LINKS</span></span>

[<span data-ttu-id="3e583-204">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="3e583-204">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="3e583-205">Join-Path</span><span class="sxs-lookup"><span data-stu-id="3e583-205">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="3e583-206">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="3e583-206">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="3e583-207">Test-Path</span><span class="sxs-lookup"><span data-stu-id="3e583-207">Test-Path</span></span>](Test-Path.md)
