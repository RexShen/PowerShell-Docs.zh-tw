---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transcript
ms.openlocfilehash: 2e4380163c7dc34c84460a1cfef3ef2f4b33507b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202884"
---
# <span data-ttu-id="b9eb9-103">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="b9eb9-103">Start-Transcript</span></span>

## <span data-ttu-id="b9eb9-104">概要</span><span class="sxs-lookup"><span data-stu-id="b9eb9-104">SYNOPSIS</span></span>
<span data-ttu-id="b9eb9-105">在文字檔中建立所有或部分 PowerShell 會話的記錄。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-105">Creates a record of all or part of a PowerShell session to a text file.</span></span>

## <span data-ttu-id="b9eb9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b9eb9-106">SYNTAX</span></span>

### <span data-ttu-id="b9eb9-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="b9eb9-107">ByPath (Default)</span></span>

```
Start-Transcript [[-Path] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader]
 [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="b9eb9-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="b9eb9-108">ByLiteralPath</span></span>

```
Start-Transcript [[-LiteralPath] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="b9eb9-109">ByOutputDirectory</span><span class="sxs-lookup"><span data-stu-id="b9eb9-109">ByOutputDirectory</span></span>

```
Start-Transcript [[-OutputDirectory] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="b9eb9-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b9eb9-110">DESCRIPTION</span></span>

<span data-ttu-id="b9eb9-111">`Start-Transcript`Cmdlet 會建立所有或部分 PowerShell 會話的記錄至文字檔。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-111">The `Start-Transcript` cmdlet creates a record of all or part of a PowerShell session to a text file.</span></span> <span data-ttu-id="b9eb9-112">文字記錄包含使用者輸入的所有命令，以及顯示在主控台上的所有輸出。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-112">The transcript includes all command that the user types and all output that appears on the console.</span></span>

<span data-ttu-id="b9eb9-113">從 Windows PowerShell 5.0 開始，會 `Start-Transcript` 在為所有文字記錄產生的檔案名中包含主機名稱。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-113">Starting in Windows PowerShell 5.0, `Start-Transcript` includes the hostname in the generated file name of all transcripts.</span></span> <span data-ttu-id="b9eb9-114">當您的企業記錄會集中管理時，這特別有用。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-114">This is especially useful when your enterprise's logging is centralized.</span></span>
<span data-ttu-id="b9eb9-115">Cmdlet 所建立的檔案會 `Start-Transcript` 在名稱中包含隨機字元，以防止在同時啟動兩個或多個文字記錄時，可能會覆寫或重複。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-115">Files that are created by the `Start-Transcript` cmdlet include random characters in names to prevent potential overwrites or duplication when two or more transcripts are started simultaneously.</span></span>
<span data-ttu-id="b9eb9-116">這也可以防止未經授權探索儲存於集中式檔案共用中的文字記錄。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-116">This also prevents unauthorized discovery of transcripts that are stored in a centralized file share.</span></span>

## <span data-ttu-id="b9eb9-117">範例</span><span class="sxs-lookup"><span data-stu-id="b9eb9-117">EXAMPLES</span></span>

### <span data-ttu-id="b9eb9-118">範例 1︰使用預設設定啟動文字記錄檔</span><span class="sxs-lookup"><span data-stu-id="b9eb9-118">Example 1: Start a transcript file with default settings</span></span>

```powershell
Start-Transcript
```

<span data-ttu-id="b9eb9-119">此命令會在預設檔案位置中啟動文字記錄。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-119">This command starts a transcript in the default file location.</span></span>

### <span data-ttu-id="b9eb9-120">範例 2︰啟動特定位置上的文字記錄檔</span><span class="sxs-lookup"><span data-stu-id="b9eb9-120">Example 2: Start a transcript file at a specific location</span></span>

```powershell
Start-Transcript -Path "C:\transcripts\transcript0.txt" -NoClobber
```

<span data-ttu-id="b9eb9-121">此命令會在中的檔案中啟動文字記錄 `Transcript0.txt` `C:\transcripts` 。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-121">This command starts a transcript in the `Transcript0.txt` file in `C:\transcripts`.</span></span> <span data-ttu-id="b9eb9-122">由於使用了 **NoClobber** 參數，此命令會防止任何現有的檔案遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-122">Since the **NoClobber** parameter is used, the command prevents any existing files from being overwritten.</span></span> <span data-ttu-id="b9eb9-123">如果檔案 `Transcript0.txt` 已存在，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-123">If the `Transcript0.txt` file already exists, the command fails.</span></span>

## <span data-ttu-id="b9eb9-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b9eb9-124">PARAMETERS</span></span>

### <span data-ttu-id="b9eb9-125">-Append</span><span class="sxs-lookup"><span data-stu-id="b9eb9-125">-Append</span></span>

<span data-ttu-id="b9eb9-126">指出此 Cmdlet 會將新的文字記錄新增到現有檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-126">Indicates that this cmdlet adds the new transcript to the end of an existing file.</span></span> <span data-ttu-id="b9eb9-127">使用 **Path** 參數指定檔案。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-127">Use the **Path** parameter to specify the file.</span></span>

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

### <span data-ttu-id="b9eb9-128">-Force</span><span class="sxs-lookup"><span data-stu-id="b9eb9-128">-Force</span></span>

<span data-ttu-id="b9eb9-129">可讓 Cmdlet 將文字記錄附加到現有的唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-129">Allows the cmdlet to append the transcript to an existing read-only file.</span></span> <span data-ttu-id="b9eb9-130">針對唯讀檔案使用時，此 Cmdlet 會將檔案權限變更為讀寫。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-130">When used on a read-only file, the cmdlet changes the file permission to read-write.</span></span> <span data-ttu-id="b9eb9-131">若使用了此參數，此 Cmdlet 便無法覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-131">The cmdlet cannot override security restrictions when this parameter is used.</span></span>

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

### <span data-ttu-id="b9eb9-132">-IncludeInvocationHeader</span><span class="sxs-lookup"><span data-stu-id="b9eb9-132">-IncludeInvocationHeader</span></span>

<span data-ttu-id="b9eb9-133">指出此 Cmdlet 會在執行命令時記錄時間戳記。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-133">Indicates that this cmdlet logs the time stamp when commands are run.</span></span>

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

### <span data-ttu-id="b9eb9-134">-UseMinimalHeader</span><span class="sxs-lookup"><span data-stu-id="b9eb9-134">-UseMinimalHeader</span></span>

<span data-ttu-id="b9eb9-135">在文字記錄前面加上簡短的標頭，而不是預設包含的詳細標頭。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-135">Prepend a short header to the transcript, instead of the detailed header included by default.</span></span> <span data-ttu-id="b9eb9-136">此參數已新增至 PowerShell 6.2。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-136">This parameter was added in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="b9eb9-137">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b9eb9-137">-LiteralPath</span></span>

<span data-ttu-id="b9eb9-138">指定文字記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-138">Specifies a location to the transcript file.</span></span> <span data-ttu-id="b9eb9-139">與 **Path** 參數不同， **LiteralPath** 參數的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-139">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="b9eb9-140">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-140">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b9eb9-141">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-141">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b9eb9-142">單引號會通知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-142">Single quotation marks inform PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9eb9-143">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="b9eb9-143">-NoClobber</span></span>

<span data-ttu-id="b9eb9-144">指出此 Cmdlet 將不會覆寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-144">Indicates that this cmdlet will not overwrite of an existing file.</span></span> <span data-ttu-id="b9eb9-145">根據預設，如果文字記錄檔存在於指定的路徑中， `Start-Transcript` 會覆寫檔案而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-145">By default, if a transcript file exists in the specified path, `Start-Transcript` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9eb9-146">-OutputDirectory</span><span class="sxs-lookup"><span data-stu-id="b9eb9-146">-OutputDirectory</span></span>

<span data-ttu-id="b9eb9-147">指定要用來儲存文字記錄的特定路徑和資料夾。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-147">Specifies a specific path and folder in which to save a transcript.</span></span> <span data-ttu-id="b9eb9-148">PowerShell 會自動指派文字記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-148">PowerShell automatically assigns the transcript name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByOutputDirectory
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9eb9-149">-Path</span><span class="sxs-lookup"><span data-stu-id="b9eb9-149">-Path</span></span>

<span data-ttu-id="b9eb9-150">指定文字記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-150">Specifies a location to the transcript file.</span></span> <span data-ttu-id="b9eb9-151">輸入檔案的路徑 `.txt` 。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-151">Enter a path to a `.txt` file.</span></span> <span data-ttu-id="b9eb9-152">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-152">Wildcards are not permitted.</span></span>

<span data-ttu-id="b9eb9-153">如果您未指定路徑，則會 `Start-Transcript` 使用全域變數值中的路徑 `$Transcript` 。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-153">If you do not specify a path, `Start-Transcript` uses the path in the value of the `$Transcript` global variable.</span></span> <span data-ttu-id="b9eb9-154">如果您尚未建立此變數，請將文字記錄 `Start-Transcript` 儲存在檔案中 `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` 。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-154">If you have not created this variable, `Start-Transcript` stores the transcripts in the `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` files.</span></span>

<span data-ttu-id="b9eb9-155">如果路徑中不存在任何目錄，命令就會失敗。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-155">If any of the directories in the path do not exist, the command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9eb9-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b9eb9-156">-Confirm</span></span>

<span data-ttu-id="b9eb9-157">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b9eb9-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b9eb9-158">-WhatIf</span></span>

<span data-ttu-id="b9eb9-159">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-159">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b9eb9-160">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b9eb9-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b9eb9-161">CommonParameters</span></span>

<span data-ttu-id="b9eb9-162">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b9eb9-163">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b9eb9-164">輸入</span><span class="sxs-lookup"><span data-stu-id="b9eb9-164">INPUTS</span></span>

### <span data-ttu-id="b9eb9-165">無</span><span class="sxs-lookup"><span data-stu-id="b9eb9-165">None</span></span>

<span data-ttu-id="b9eb9-166">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-166">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="b9eb9-167">輸出</span><span class="sxs-lookup"><span data-stu-id="b9eb9-167">OUTPUTS</span></span>

### <span data-ttu-id="b9eb9-168">System.String</span><span class="sxs-lookup"><span data-stu-id="b9eb9-168">System.String</span></span>

<span data-ttu-id="b9eb9-169">此 Cmdlet 會傳回包含確認訊息和輸出檔路徑的字串。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-169">This cmdlet returns a string that contains a confirmation message and the path to the output file.</span></span>

## <span data-ttu-id="b9eb9-170">注意</span><span class="sxs-lookup"><span data-stu-id="b9eb9-170">NOTES</span></span>

<span data-ttu-id="b9eb9-171">若要停止文字記錄，請使用 `Stop-Transcript` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-171">To stop a transcript, use the `Stop-Transcript` cmdlet.</span></span>

<span data-ttu-id="b9eb9-172">若要記錄整個會話，請將 `Start-Transcript` 命令新增至您的設定檔。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-172">To record an entire session, add the `Start-Transcript` command to your profile.</span></span> <span data-ttu-id="b9eb9-173">如需詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="b9eb9-173">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

## <span data-ttu-id="b9eb9-174">相關連結</span><span class="sxs-lookup"><span data-stu-id="b9eb9-174">RELATED LINKS</span></span>

[<span data-ttu-id="b9eb9-175">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="b9eb9-175">Stop-Transcript</span></span>](Stop-Transcript.md)
