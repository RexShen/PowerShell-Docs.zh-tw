---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: 2288b3a7f7db33dbf22cc47fe2bb16106ea9bb90
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201692"
---
# <span data-ttu-id="2e1f5-103">Clear-History</span><span class="sxs-lookup"><span data-stu-id="2e1f5-103">Clear-History</span></span>

## <span data-ttu-id="2e1f5-104">概要</span><span class="sxs-lookup"><span data-stu-id="2e1f5-104">SYNOPSIS</span></span>
<span data-ttu-id="2e1f5-105">從 PowerShell 會話命令歷程記錄中刪除專案。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-105">Deletes entries from the PowerShell session command history.</span></span>

## <span data-ttu-id="2e1f5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2e1f5-106">SYNTAX</span></span>

### <span data-ttu-id="2e1f5-107">IDParameter (預設值)</span><span class="sxs-lookup"><span data-stu-id="2e1f5-107">IDParameter (Default)</span></span>

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2e1f5-108">CommandLineParameter</span><span class="sxs-lookup"><span data-stu-id="2e1f5-108">CommandLineParameter</span></span>

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## <span data-ttu-id="2e1f5-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2e1f5-109">DESCRIPTION</span></span>

<span data-ttu-id="2e1f5-110">`Clear-History` 從 PowerShell 會話刪除命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-110">`Clear-History` deletes the command history from a PowerShell session.</span></span> <span data-ttu-id="2e1f5-111">每個 PowerShell 會話都有自己的命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-111">Each PowerShell session has its own command history.</span></span> <span data-ttu-id="2e1f5-112">若要顯示命令歷程記錄，請使用 `Get-History` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-112">To display the command history, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="2e1f5-113">根據預設，會 `Clear-History` 從 PowerShell 會話刪除整個命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-113">By default, `Clear-History` deletes the entire command history from a PowerShell session.</span></span> <span data-ttu-id="2e1f5-114">您可以使用參數搭配 `Clear-History` 來刪除選取的命令。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-114">You can use parameters with `Clear-History` to delete selected commands.</span></span>

<span data-ttu-id="2e1f5-115">`Clear-History` 不會清除 `PSReadLine` 命令歷程記錄檔。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-115">`Clear-History` does not clear the `PSReadLine` command history file.</span></span> <span data-ttu-id="2e1f5-116">`PSReadLine`模組會儲存歷程記錄檔案，其中包含每個 powershell 會話的每個 powershell 命令。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-116">The `PSReadLine` module stores a history file that contains every PowerShell command from every PowerShell session.</span></span> <span data-ttu-id="2e1f5-117">從 PowerShell 提示字元中，使用鍵盤上的向上和向下箭號來流覽命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-117">From a PowerShell prompt, use the up and down arrows on your keyboard to scroll through the command history.</span></span> <span data-ttu-id="2e1f5-118">若要顯示 `PSReadLine` 命令歷程記錄的設定，請使用 `Get-PSReadLineOption` 。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-118">To display the `PSReadLine` configuration for command history, use `Get-PSReadLineOption`.</span></span>
<span data-ttu-id="2e1f5-119">`PSReadLine` 隨附于 PowerShell 5.0 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-119">`PSReadLine` shipped with PowerShell 5.0 and above.</span></span> <span data-ttu-id="2e1f5-120">如需詳細資訊，請參閱 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-120">For more information, see [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="2e1f5-121">範例</span><span class="sxs-lookup"><span data-stu-id="2e1f5-121">EXAMPLES</span></span>

### <span data-ttu-id="2e1f5-122">範例1：從 PowerShell 會話刪除命令歷程記錄</span><span class="sxs-lookup"><span data-stu-id="2e1f5-122">Example 1: Delete the command history from a PowerShell session</span></span>

<span data-ttu-id="2e1f5-123">此命令會從 PowerShell 會話的歷程記錄中刪除所有命令。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-123">This command deletes all of the commands from a PowerShell session's history.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location .\Test
   2 Update-Help
   3 Set-Location C:\Test\Logs
   4 Get-Location
```

```powershell
Clear-History
Get-History
```

```Output
  Id CommandLine
  -- -----------
   5 Clear-History
```

<span data-ttu-id="2e1f5-124">此 `Get-History` Cmdlet 會顯示 PowerShell 會話的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-124">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="2e1f5-125">`Clear-History` 刪除整個命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-125">`Clear-History` deletes the entire command history.</span></span> <span data-ttu-id="2e1f5-126">`Get-History` 顯示已更新的命令歷程記錄，並確認已刪除先前的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-126">`Get-History` displays the updated command history and confirms the prior history was deleted.</span></span>

### <span data-ttu-id="2e1f5-127">範例2：刪除最新的命令</span><span class="sxs-lookup"><span data-stu-id="2e1f5-127">Example 2: Delete the newest commands</span></span>

<span data-ttu-id="2e1f5-128">此命令會使用 **Count** 和 **最新** 的參數，從 PowerShell 會話的歷程記錄中刪除最新的命令。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-128">This command uses the **Count** and **Newest** parameters to delete the newest commands from a PowerShell session's history.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Count 5 -Newest
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
  11 Clear-History -Count 5 -Newest
```

<span data-ttu-id="2e1f5-129">此 `Get-History` Cmdlet 會顯示 PowerShell 會話的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-129">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="2e1f5-130">`Clear-History` 用來刪除命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-130">`Clear-History` is used to delete the command history.</span></span> <span data-ttu-id="2e1f5-131">**Count** 參數指定要刪除的命令數目（包含指定的 **識別碼** ）。 **最新** 的參數指定從歷程記錄中清除最新的命令。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-131">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id** . The **Newest** parameter specifies that the newest commands are cleared from the history.</span></span> <span data-ttu-id="2e1f5-132">`Get-History`顯示已更新的命令歷程記錄，並確認已刪除五個最新的命令， **識別碼 6**  -  **識別碼 10** 。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-132">`Get-History` displays the updated command history and confirms that the five newest commands were deleted, **Id 6** - **Id 10** .</span></span>

### <span data-ttu-id="2e1f5-133">範例3：刪除符合特定準則的命令</span><span class="sxs-lookup"><span data-stu-id="2e1f5-133">Example 3: Delete commands that match specific criteria</span></span>

<span data-ttu-id="2e1f5-134">此命令會刪除符合命令 **行** 參數所定義之特定準則的命令。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-134">This command deletes commands that match specific criteria defined by the **CommandLine** parameter.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
```

```powershell
Clear-History -CommandLine *Help*, *Syntax
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   4 Get-Command Clear-History -ShowCommandInfo
   8 Clear-History -CommandLine *Help*, *Syntax
```

<span data-ttu-id="2e1f5-135">此 `Get-History` Cmdlet 會顯示 PowerShell 會話的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-135">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="2e1f5-136">`Clear-History` 刪除命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-136">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="2e1f5-137">命令 **行** 參數 **指定包含說明** 或結尾 **語法** 的命令。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-137">The **CommandLine** parameter specifies commands that contain **Help** or end with **Syntax** .</span></span> <span data-ttu-id="2e1f5-138">`Get-History` 顯示已更新的命令歷程記錄，並確認已刪除命令 **識別碼 3** 、 **id 5** 、 **id 6** 和 **id 7** 。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-138">`Get-History` displays the updated command history and confirms that commands **Id 3** , **Id 5** , **Id 6** , and **Id 7** were deleted.</span></span>

### <span data-ttu-id="2e1f5-139">範例4：依識別碼刪除命令</span><span class="sxs-lookup"><span data-stu-id="2e1f5-139">Example 4: Delete commands by Id number</span></span>

<span data-ttu-id="2e1f5-140">此命令會使用 **識別碼** 刪除特定的記錄專案。若要刪除多個命令，請提交以逗號分隔的 **識別碼** 清單。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-140">This command deletes specific history items using the **Id** . To delete multiple commands, submit a comma-separated list of **Id** numbers.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   3 Get-Help Get-Alias
   4 Get-Command Clear-History
   5 Get-Command Clear-History -Syntax
   6 Get-Command Clear-History -ShowCommandInfo
```

```powershell
Clear-History -Id 3, 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   4 Get-Command Clear-History
   6 Get-Command Clear-History -ShowCommandInfo
   7 Get-History
   8 Clear-History -Id 3, 5
```

<span data-ttu-id="2e1f5-141">此 `Get-History` Cmdlet 會顯示 PowerShell 會話的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-141">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="2e1f5-142">`Clear-History` 刪除命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-142">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="2e1f5-143">**Id** 參數指定要刪除的命令。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-143">The **Id** parameter specifies which commands to delete.</span></span> <span data-ttu-id="2e1f5-144">`Get-History` 顯示已更新的命令歷程記錄，並確認已刪除 **識別碼 3** 和 **識別碼 5** 。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-144">`Get-History` displays the updated command history and confirms that **Id 3** and **Id 5** were deleted.</span></span>

### <span data-ttu-id="2e1f5-145">範例5：依識別碼和計數刪除命令</span><span class="sxs-lookup"><span data-stu-id="2e1f5-145">Example 5: Delete commands by Id number and count</span></span>

<span data-ttu-id="2e1f5-146">此命令會使用 **Id** 和 **Count** 參數來刪除命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-146">This command uses the **Id** and **Count** parameters to delete command history.</span></span> <span data-ttu-id="2e1f5-147">命令會以反向順序從指定的 **識別碼** 中刪除，最新到最舊。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-147">Commands are deleted from the specified **Id** in reverse order, newest to oldest.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Id 7 -Count 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
  11 Clear-History -Id 7 -Count 5
```

<span data-ttu-id="2e1f5-148">此 `Get-History` Cmdlet 會顯示 PowerShell 會話的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-148">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="2e1f5-149">`Clear-History` 刪除命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-149">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="2e1f5-150">**Id** 參數指定開頭為 **id 7** 。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-150">The **Id** parameter specifies to begin with **Id 7** .</span></span> <span data-ttu-id="2e1f5-151">**Count** 參數指定要刪除五個命令，內含指定的 **識別碼** 。`Get-History`顯示已更新的命令歷程記錄，並確認已刪除五個命令， **識別碼 3**  -  **識別碼 7** 。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-151">The **Count** parameter specifies to delete five commands, inclusive of the specified **Id** . `Get-History` displays the updated command history and confirms that five commands were deleted, **Id 3** - **Id 7** .</span></span>

## <span data-ttu-id="2e1f5-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2e1f5-152">PARAMETERS</span></span>

### <span data-ttu-id="2e1f5-153">-CommandLine</span><span class="sxs-lookup"><span data-stu-id="2e1f5-153">-CommandLine</span></span>

<span data-ttu-id="2e1f5-154">從 PowerShell 會話刪除命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-154">Deletes command history from a PowerShell session.</span></span> <span data-ttu-id="2e1f5-155">字串必須完全相符，或使用萬用字元來比對顯示之 PowerShell 會話歷程記錄中的命令 `Get-History` 。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-155">The string must be an exact match or use wildcards to match commands in the PowerShell session history displayed by `Get-History`.</span></span> <span data-ttu-id="2e1f5-156">如果您輸入一個以上的字串，則會 `Clear-History` 刪除符合任何字串的命令。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-156">If you enter more than one string, `Clear-History` deletes commands that match any of the strings.</span></span> <span data-ttu-id="2e1f5-157">**命令列** 參數可以搭配 **Count** 使用。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-157">The **CommandLine** parameter can be used with **Count** .</span></span>

<span data-ttu-id="2e1f5-158">針對具有空格的字串，請使用單一引號。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-158">For strings with a space, use single quotations.</span></span> <span data-ttu-id="2e1f5-159">如需詳細資訊，請參閱 [about_Quoting_Rules](About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-159">For more information, see [about_Quoting_Rules](About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandLineParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2e1f5-160">-Count</span><span class="sxs-lookup"><span data-stu-id="2e1f5-160">-Count</span></span>

<span data-ttu-id="2e1f5-161">指定要刪除之記錄專案的數目 `Clear-History` 。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-161">Specifies the number of history entries that `Clear-History` deletes.</span></span> <span data-ttu-id="2e1f5-162">從歷程記錄中最舊的專案開始，依序刪除命令。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-162">Commands are deleted in order, beginning with the oldest entry in the history.</span></span>

<span data-ttu-id="2e1f5-163">**Count** 和 **Id** 參數可以一起使用。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-163">The **Count** and **Id** parameters can be used together.</span></span> <span data-ttu-id="2e1f5-164">**Count** 參數指定要刪除的命令數目（包含指定的 **識別碼** ）。從指定的 **識別碼** 開始，會以反向順序刪除命令。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-164">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id** . Beginning at the specified **Id** , commands are deleted in reverse sequential order.</span></span> <span data-ttu-id="2e1f5-165">例如，如果 **識別碼** 為30且 **計數** 為10，則會 `Clear-History` 刪除專案21到30。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-165">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 21 through 30.</span></span>

<span data-ttu-id="2e1f5-166">**Count** 和 **命令列** 參數可以一起使用。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-166">The **Count** and **CommandLine** parameters can be used together.</span></span> <span data-ttu-id="2e1f5-167">**Count** 指定要刪除符合 **命令列** 參數值的命令數目。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-167">**Count** specifies the number of commands to delete that match **CommandLine** parameter value.</span></span> <span data-ttu-id="2e1f5-168">這些命令會依順序刪除。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-168">The commands are deleted in sequential order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e1f5-169">-Id</span><span class="sxs-lookup"><span data-stu-id="2e1f5-169">-Id</span></span>

<span data-ttu-id="2e1f5-170">指定刪除的命令歷程記錄 **識別碼** `Clear-History` 。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-170">Specifies the command history **Id** that `Clear-History` deletes.</span></span> <span data-ttu-id="2e1f5-171">若要顯示 **識別碼** ，請使用 `Get-History` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-171">To display **Id** numbers, use the `Get-History` cmdlet.</span></span> <span data-ttu-id="2e1f5-172">**識別碼** 是連續的，而且命令會在 PowerShell 會話中保留其 **識別碼** 號碼。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-172">The **Id** numbers are sequential and commands keep their **Id** number throughout a PowerShell session.</span></span> <span data-ttu-id="2e1f5-173">**Id** 參數可以搭配 **Count** 和 **最新** 使用。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-173">The **Id** parameter can be used with **Count** and **Newest** .</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IDParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e1f5-174">-Newest</span><span class="sxs-lookup"><span data-stu-id="2e1f5-174">-Newest</span></span>

<span data-ttu-id="2e1f5-175">使用 **最新** 的參數時，會 `Clear-History` 刪除歷程記錄中的最新專案。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-175">When the **Newest** parameter is used, `Clear-History` deletes the newest entries in the history.</span></span> <span data-ttu-id="2e1f5-176">依預設，會 `Clear-History` 刪除歷程記錄中最舊的專案。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-176">By default, `Clear-History` deletes the oldest entries in the history.</span></span>

<span data-ttu-id="2e1f5-177">**最新** 的參數可以搭配 **Id** 和 **Count** 使用。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-177">The **Newest** parameter can be used with **Id** and **Count** .</span></span> <span data-ttu-id="2e1f5-178">**Count** 參數指定要刪除的命令數目（包含指定的 **識別碼** ）。從指定的 **識別碼** 開始，會依順序刪除命令。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-178">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id** . Beginning at the specified **Id** , commands are deleted in sequential order.</span></span> <span data-ttu-id="2e1f5-179">例如，如果 **識別碼** 為30且 **計數** 為10，則會 `Clear-History` 刪除30到39的專案。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-179">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 30 through 39.</span></span>

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

### <span data-ttu-id="2e1f5-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2e1f5-180">-Confirm</span></span>

<span data-ttu-id="2e1f5-181">在執行 Cmdlet 前提示您確認 `Clear-History` 。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-181">Prompts you for confirmation before running the `Clear-History` cmdlet.</span></span>

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

### <span data-ttu-id="2e1f5-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2e1f5-182">-WhatIf</span></span>

<span data-ttu-id="2e1f5-183">顯示當 Cmdlet 執行時，會發生什麼事 `Clear-History` 。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-183">Shows what would happen if the `Clear-History` cmdlet runs.</span></span> <span data-ttu-id="2e1f5-184">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-184">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2e1f5-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2e1f5-185">CommonParameters</span></span>

<span data-ttu-id="2e1f5-186">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2e1f5-187">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-187">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2e1f5-188">輸入</span><span class="sxs-lookup"><span data-stu-id="2e1f5-188">INPUTS</span></span>

### <span data-ttu-id="2e1f5-189">無</span><span class="sxs-lookup"><span data-stu-id="2e1f5-189">None</span></span>

<span data-ttu-id="2e1f5-190">您無法透過管道傳送物件至 `Clear-History` 。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-190">You cannot pipe objects to `Clear-History`.</span></span>

## <span data-ttu-id="2e1f5-191">輸出</span><span class="sxs-lookup"><span data-stu-id="2e1f5-191">OUTPUTS</span></span>

### <span data-ttu-id="2e1f5-192">無</span><span class="sxs-lookup"><span data-stu-id="2e1f5-192">None</span></span>

<span data-ttu-id="2e1f5-193">`Clear-History` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-193">`Clear-History` does not generate any output.</span></span>

## <span data-ttu-id="2e1f5-194">注意</span><span class="sxs-lookup"><span data-stu-id="2e1f5-194">NOTES</span></span>

<span data-ttu-id="2e1f5-195">PowerShell 會話歷程記錄是在 PowerShell 會話期間輸入的命令清單。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-195">The PowerShell session history is a list of the commands entered during a PowerShell session.</span></span> <span data-ttu-id="2e1f5-196">您可以檢視歷程記錄、新增和刪除命令，以及從歷程記錄執行命令。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-196">You can view the history, add and delete commands, and run commands from the history.</span></span> <span data-ttu-id="2e1f5-197">如需詳細資訊，請參閱 [about_History](About/about_History.md)。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-197">For more information, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="2e1f5-198">會話歷程記錄是與 **PSReadLine** 模組所維護的歷程記錄分開管理。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-198">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="2e1f5-199">這兩個歷程記錄都可以在載入 **PSReadLine** 的會話中使用。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-199">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="2e1f5-200">此 Cmdlet 僅適用于會話歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-200">This cmdlet only works with the session history.</span></span> <span data-ttu-id="2e1f5-201">如需詳細資訊，請參閱 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="2e1f5-201">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="2e1f5-202">相關連結</span><span class="sxs-lookup"><span data-stu-id="2e1f5-202">RELATED LINKS</span></span>

[<span data-ttu-id="2e1f5-203">about_History</span><span class="sxs-lookup"><span data-stu-id="2e1f5-203">about_History</span></span>](About/about_History.md)

[<span data-ttu-id="2e1f5-204">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="2e1f5-204">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="2e1f5-205">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="2e1f5-205">about_Quoting_Rules</span></span>](About/about_Quoting_Rules.md)

[<span data-ttu-id="2e1f5-206">Add-History</span><span class="sxs-lookup"><span data-stu-id="2e1f5-206">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="2e1f5-207">Get-History</span><span class="sxs-lookup"><span data-stu-id="2e1f5-207">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="2e1f5-208">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="2e1f5-208">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="2e1f5-209">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="2e1f5-209">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="2e1f5-210">設定-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="2e1f5-210">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)
