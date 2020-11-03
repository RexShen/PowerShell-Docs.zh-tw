---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/new-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-IseSnippet
ms.openlocfilehash: 0ed1c2913fc7531574bfbdd435a002d60931d24a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202476"
---
# <span data-ttu-id="bd6c2-103">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="bd6c2-103">New-IseSnippet</span></span>

## <span data-ttu-id="bd6c2-104">概要</span><span class="sxs-lookup"><span data-stu-id="bd6c2-104">SYNOPSIS</span></span>
<span data-ttu-id="bd6c2-105">建立 Windows PowerShell ISE 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-105">Creates a Windows PowerShell ISE code snippet.</span></span>

## <span data-ttu-id="bd6c2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bd6c2-106">SYNTAX</span></span>

```
New-IseSnippet [-Title] <String> [-Description] <String> [-Text] <String> [-Author <String>]
 [-CaretOffset <Int32>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="bd6c2-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bd6c2-107">DESCRIPTION</span></span>

<span data-ttu-id="bd6c2-108">`New-ISESnippet`Cmdlet 會為 Windows PowerShell ISE 建立可重複使用的文字「程式碼片段」。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-108">The `New-ISESnippet` cmdlet creates a reusable text "snippet" for Windows PowerShell ISE.</span></span> <span data-ttu-id="bd6c2-109">您可以使用程式碼片段來將文字新增到 Windows PowerShell ISE 的 [程式碼片段] 窗格或 [命令] 窗格。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-109">You can use snippets to add text to the Script pane or Command pane in Windows PowerShell ISE.</span></span> <span data-ttu-id="bd6c2-110">這個 Cmdlet 只在 Windows PowerShell ISE 中提供。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-110">This cmdlet is available only in Windows PowerShell ISE.</span></span>

<span data-ttu-id="bd6c2-111">自 Windows PowerShell 3.0 開始，Windows PowerShell ISE 包含了內建程式碼片段的集合。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-111">Beginning in Windows PowerShell 3.0, Windows PowerShell ISE includes a collection of built-in snippets.</span></span> <span data-ttu-id="bd6c2-112">此 `New-ISESnippet` Cmdlet 可讓您建立自己的程式碼片段，以加入至內建集合。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-112">The `New-ISESnippet` cmdlet lets you create your own snippets to add to the built-in collection.</span></span> <span data-ttu-id="bd6c2-113">您可以檢視、變更、新增、刪除和共用程式碼片段檔案，並將它們包含在 Windows PowerShell 模組中。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-113">You can view, change, add, delete, and share snippet files and include them in Windows PowerShell modules.</span></span> <span data-ttu-id="bd6c2-114">若要查看 Windows PowerShell ISE 中的程式碼片段，請從 [ **編輯** ] 功能表選取 [ **啟動程式碼片段** ]，或按 <kbd>CTRL</kbd> + <kbd>J</kbd>。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-114">To see snippets in Windows PowerShell ISE, from the **Edit** menu, select **Start Snippets** or press <kbd>CTRL</kbd>+<kbd>J</kbd>.</span></span>

<span data-ttu-id="bd6c2-115">`New-ISESnippet`Cmdlet `<Title>.Snippets.ps1xml` 會以 `$home\Documents\WindowsPowerShell\Snippets` 您指定的標題，在目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-115">The `New-ISESnippet` cmdlet creates a `<Title>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory with the title that you specify.</span></span> <span data-ttu-id="bd6c2-116">如果要在您撰寫的模組中包含程式碼片段檔案，請將程式碼片段檔案加到模組目錄的 Snippets 子目錄。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-116">To include a snippet file in a module that you are authoring, add the snippet file to a Snippets subdirectory of your module directory.</span></span>

<span data-ttu-id="bd6c2-117">您無法在執行原則 **受限** 或 **AllSigned** 的會話中使用使用者建立的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-117">You cannot use user-created snippets in a session in which the execution policy is **Restricted** or **AllSigned** .</span></span>

<span data-ttu-id="bd6c2-118">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-118">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="bd6c2-119">範例</span><span class="sxs-lookup"><span data-stu-id="bd6c2-119">EXAMPLES</span></span>

### <span data-ttu-id="bd6c2-120">範例1：建立 Comment-Based 的說明程式碼片段</span><span class="sxs-lookup"><span data-stu-id="bd6c2-120">Example 1: Create a Comment-Based help snippet</span></span>

```
New-IseSnippet -Title Comment-BasedHelp -Description "A template for comment-based help." -Text "<#
    .SYNOPSIS

    .DESCRIPTION
    .PARAMETER  <Parameter-Name>
    .INPUTS
    .OUTPUTS
    .EXAMPLE
    .LINK
#>"
```

<span data-ttu-id="bd6c2-121">此命令會為 Windows PowerShell ISE 建立 Comment-BasedHelp 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-121">This command creates a Comment-BasedHelp snippet for Windows PowerShell ISE.</span></span> <span data-ttu-id="bd6c2-122">它會 `Comment-BasedHelp.snippets.ps1xml` 在使用者的程式碼片段目錄中建立名為的檔案 `$home\Documents\WindowsPowerShell\Snippets` 。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-122">It creates a file named `Comment-BasedHelp.snippets.ps1xml` in the user's Snippets directory `$home\Documents\WindowsPowerShell\Snippets`.</span></span>

### <span data-ttu-id="bd6c2-123">範例2：建立必要的程式碼片段</span><span class="sxs-lookup"><span data-stu-id="bd6c2-123">Example 2: Create a mandatory snippet</span></span>

```
$M = @'
Param
(
  [parameter(Mandatory=$true)]
  [String[]]
  $<ParameterName>
)
'@

New-ISESnippet -Text $M -Title Mandatory -Description "Adds a mandatory function parameter." -Author "Patti Fuller, Fabrikam Corp." -Force
```

<span data-ttu-id="bd6c2-124">此範例會針對 Windows PowerShell ISE 建立名為「 **強制** 」的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-124">This example creates a snippet named **Mandatory** for Windows PowerShell ISE.</span></span> <span data-ttu-id="bd6c2-125">第一個命令會將程式碼片段文字儲存在 `$M` 變數中。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-125">The first command saves the snippet text in the `$M` variable.</span></span> <span data-ttu-id="bd6c2-126">第二個命令會使用 `New-ISESnippet` Cmdlet 建立程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-126">The second command uses the `New-ISESnippet` cmdlet to create the snippet.</span></span> <span data-ttu-id="bd6c2-127">此命令會使用 **Force** 參數覆寫先前同名的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-127">The command uses the **Force** parameter to overwrite a previous snippet with the same name.</span></span>

### <span data-ttu-id="bd6c2-128">範例3：將必要的程式碼片段從資料夾複製到目的資料夾</span><span class="sxs-lookup"><span data-stu-id="bd6c2-128">Example 3: Copy a mandatory snippet from a folder to a destination folder</span></span>

```
Copy-Item "$Home\Documents\WindowsPowerShell\Snippets\Mandatory.Snippets.ps1xml" -Destination "\\Server\Share"
```

<span data-ttu-id="bd6c2-129">此命令會使用 `Copy-Item` Cmdlet 將 **必要** 的程式碼片段從放置於 Server\Share 檔案共用的資料夾中複製 `New-ISESnippet` 。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-129">This command uses the `Copy-Item` cmdlet to copy the **Mandatory** snippet from the folder where `New-ISESnippet` places it to the Server\Share file share.</span></span>

## <span data-ttu-id="bd6c2-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bd6c2-130">PARAMETERS</span></span>

### <span data-ttu-id="bd6c2-131">-作者</span><span class="sxs-lookup"><span data-stu-id="bd6c2-131">-Author</span></span>

<span data-ttu-id="bd6c2-132">指定程式碼片段的作者。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-132">Specifies the author of the snippet.</span></span> <span data-ttu-id="bd6c2-133">作者欄位會顯示在程式碼片段檔案中，但是當您在 Windows PowerShell ISE 中按一下程式碼片段名稱時則不會顯示。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-133">The author field appears in the snippet file, but it does not appear when you click the snippet name in Windows PowerShell ISE.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd6c2-134">-CaretOffset</span><span class="sxs-lookup"><span data-stu-id="bd6c2-134">-CaretOffset</span></span>

<span data-ttu-id="bd6c2-135">指定此 Cmdlet 放置游標所在的程式碼片段文字字元。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-135">Specifies the character of the snippet text that this cmdlet places the cursor on.</span></span> <span data-ttu-id="bd6c2-136">輸入一個代表游標位置的整數，"1" 代表文字的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-136">Enter an integer that represents the cursor position, with "1" representing the first character of text.</span></span> <span data-ttu-id="bd6c2-137">預設值 0 (零) 會將游標放在文字第一個字元的正前方。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-137">The default value, 0 (zero), places the cursor immediately before the first character of text.</span></span> <span data-ttu-id="bd6c2-138">這個參數不會縮排程式碼片段文字。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-138">This parameter does not indent the snippet text.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd6c2-139">-Description</span><span class="sxs-lookup"><span data-stu-id="bd6c2-139">-Description</span></span>

<span data-ttu-id="bd6c2-140">指定程式碼片段的描述。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-140">Specifies a description of the snippet.</span></span> <span data-ttu-id="bd6c2-141">當您在 Windows PowerShell ISE 中按一下程式碼片段名稱時，即會顯示描述值。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-141">The description value appears when you click the snippet name in Windows PowerShell ISE.</span></span> <span data-ttu-id="bd6c2-142">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-142">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd6c2-143">-Force</span><span class="sxs-lookup"><span data-stu-id="bd6c2-143">-Force</span></span>

<span data-ttu-id="bd6c2-144">指出此 Cmdlet 會覆寫相同位置中名稱相同的程式碼片段檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-144">Indicates that this cmdlet overwrites snippet files with the same name in the same location.</span></span> <span data-ttu-id="bd6c2-145">依預設，不 `New-ISESnippet` 會覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-145">By default, `New-ISESnippet` does not overwrite files.</span></span>

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

### <span data-ttu-id="bd6c2-146">-文字</span><span class="sxs-lookup"><span data-stu-id="bd6c2-146">-Text</span></span>

<span data-ttu-id="bd6c2-147">指定當您選取程式碼片段時新增的文字值。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-147">Specifies the text value that is added when you select the snippet.</span></span> <span data-ttu-id="bd6c2-148">當您在 Windows PowerShell ISE 中按一下程式碼片段名稱時，即會顯示程式碼片段文字。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-148">The snippet text appears when you click the snippet name in Windows PowerShell ISE.</span></span> <span data-ttu-id="bd6c2-149">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-149">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd6c2-150">-Title</span><span class="sxs-lookup"><span data-stu-id="bd6c2-150">-Title</span></span>

<span data-ttu-id="bd6c2-151">指定程式碼片段的標題或名稱。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-151">Specifies a title or name for the snippet.</span></span> <span data-ttu-id="bd6c2-152">標題也會用來命名程式碼片段檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-152">The title also names the snippet file.</span></span> <span data-ttu-id="bd6c2-153">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-153">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd6c2-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd6c2-154">CommonParameters</span></span>

<span data-ttu-id="bd6c2-155">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd6c2-156">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bd6c2-157">輸入</span><span class="sxs-lookup"><span data-stu-id="bd6c2-157">INPUTS</span></span>

### <span data-ttu-id="bd6c2-158">無</span><span class="sxs-lookup"><span data-stu-id="bd6c2-158">None</span></span>

<span data-ttu-id="bd6c2-159">此 Cmdlet 不接受來自管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-159">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="bd6c2-160">輸出</span><span class="sxs-lookup"><span data-stu-id="bd6c2-160">OUTPUTS</span></span>

### <span data-ttu-id="bd6c2-161">無</span><span class="sxs-lookup"><span data-stu-id="bd6c2-161">None</span></span>

<span data-ttu-id="bd6c2-162">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-162">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="bd6c2-163">注意</span><span class="sxs-lookup"><span data-stu-id="bd6c2-163">NOTES</span></span>

<span data-ttu-id="bd6c2-164">`New-IseSnippet` 將新使用者建立的程式碼片段儲存在未簽署的 .ps1xml 檔案中。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-164">`New-IseSnippet` stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="bd6c2-165">因此，Windows PowerShell 無法將它們新增到執行原則為 **AllSigned** 或 **Restricted** 的工作階段中。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-165">As such, Windows PowerShell cannot add them to a session in which the execution policy is **AllSigned** or **Restricted** .</span></span> <span data-ttu-id="bd6c2-166">在 **Restricted** 或 **AllSigned** 工作階段中，您可以建立、取得和匯入使用者建立的未簽署程式碼片段，卻無法在工作階段中使用它們。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-166">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

<span data-ttu-id="bd6c2-167">如果您 `New-IseSnippet` 在 **受限** 或 **AllSigned** 會話中使用此 Cmdlet，則會建立程式碼片段，但是當 Windows PowerShell 嘗試將新建立的程式碼片段新增至會話時，會出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-167">If you use the `New-IseSnippet` cmdlet in a **Restricted** or **AllSigned** session, the snippet is created, but an error message appears when Windows PowerShell tries to add the newly created snippet to the session.</span></span> <span data-ttu-id="bd6c2-168">如果要使用新的程式碼片段 (和其他使用者建立的未簽署程式碼片段)，請變更執行原則，然後重新啟動 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-168">To use the new snippet (and other unsigned user-created snippets), change the execution policy, and then restart Windows PowerShell ISE.</span></span>

<span data-ttu-id="bd6c2-169">如需 Windows PowerShell 執行原則的詳細資訊，請參閱 about_Execution_Policies。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-169">For more information about Windows PowerShell execution policies, see about_Execution_Policies.</span></span>

- <span data-ttu-id="bd6c2-170">若要變更程式碼片段，請編輯程式碼片段檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-170">To change a snippet, edit the snippet file.</span></span> <span data-ttu-id="bd6c2-171">您可以在 Windows PowerShell ISE 的腳本窗格中編輯程式碼片段檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-171">You can edit snippet files in the Script pane of Windows PowerShell ISE.</span></span>
- <span data-ttu-id="bd6c2-172">若要刪除您新增的程式碼片段，請刪除程式碼片段檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-172">To delete a snippet that you added, delete the snippet file.</span></span>
- <span data-ttu-id="bd6c2-173">您無法刪除內建的程式碼片段，但您可以使用 "$psise 來隱藏所有內建程式碼片段。ShowDefaultSnippets = $false "命令。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-173">You cannot delete a built-in snippet, but you can hide all built-in snippets by using the "$psise.Options.ShowDefaultSnippets=$false" command.</span></span>
- <span data-ttu-id="bd6c2-174">您可以建立與內建程式碼片段同名的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-174">You can create a snippet that has the same name as a built-in snippet.</span></span> <span data-ttu-id="bd6c2-175">這兩種程式碼片段都會顯示在 Windows PowerShell ISE 的程式碼片段功能表中。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-175">Both snippets appear in the snippet menu in Windows PowerShell ISE.</span></span>

## <span data-ttu-id="bd6c2-176">相關連結</span><span class="sxs-lookup"><span data-stu-id="bd6c2-176">RELATED LINKS</span></span>

[<span data-ttu-id="bd6c2-177">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="bd6c2-177">Get-IseSnippet</span></span>](Get-IseSnippet.md)

[<span data-ttu-id="bd6c2-178">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="bd6c2-178">Import-IseSnippet</span></span>](Import-IseSnippet.md)
