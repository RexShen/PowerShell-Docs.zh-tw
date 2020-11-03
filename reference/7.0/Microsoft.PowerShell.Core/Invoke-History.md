---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: baedf2be8bb3fca2223c65c33beb21f01ed84969
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201923"
---
# <span data-ttu-id="232e2-103">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="232e2-103">Invoke-History</span></span>

## <span data-ttu-id="232e2-104">概要</span><span class="sxs-lookup"><span data-stu-id="232e2-104">SYNOPSIS</span></span>
<span data-ttu-id="232e2-105">從工作階段歷程記錄執行命令。</span><span class="sxs-lookup"><span data-stu-id="232e2-105">Runs commands from the session history.</span></span>

## <span data-ttu-id="232e2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="232e2-106">SYNTAX</span></span>

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="232e2-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="232e2-107">DESCRIPTION</span></span>

<span data-ttu-id="232e2-108">此 `Invoke-History` Cmdlet 會從會話歷程記錄執行命令。</span><span class="sxs-lookup"><span data-stu-id="232e2-108">The `Invoke-History` cmdlet runs commands from the session history.</span></span> <span data-ttu-id="232e2-109">您可以將代表命令的物件傳遞給 Get-History `Invoke-History` ，或者您可以使用 **識別碼** 號碼來識別目前歷程記錄中的命令。</span><span class="sxs-lookup"><span data-stu-id="232e2-109">You can pass objects representing the commands from Get-History to `Invoke-History`, or you can identify commands in the current history by using their **Id** number.</span></span> <span data-ttu-id="232e2-110">若要尋找命令的識別碼，請使用 `Get-History` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="232e2-110">To find the identification number of a command, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="232e2-111">會話歷程記錄是與 **PSReadLine** 模組所維護的歷程記錄分開管理。</span><span class="sxs-lookup"><span data-stu-id="232e2-111">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="232e2-112">這兩個歷程記錄都可以在載入 **PSReadLine** 的會話中使用。</span><span class="sxs-lookup"><span data-stu-id="232e2-112">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="232e2-113">此 Cmdlet 僅適用于會話歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="232e2-113">This cmdlet only works with the session history.</span></span> <span data-ttu-id="232e2-114">如需詳細資訊，請參閱 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="232e2-114">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="232e2-115">範例</span><span class="sxs-lookup"><span data-stu-id="232e2-115">EXAMPLES</span></span>

### <span data-ttu-id="232e2-116">範例1：在歷程記錄中執行最新的命令</span><span class="sxs-lookup"><span data-stu-id="232e2-116">Example 1: Run the most recent command in the history</span></span>

<span data-ttu-id="232e2-117">此範例會執行會話歷程記錄中的最後一個或最新的命令。</span><span class="sxs-lookup"><span data-stu-id="232e2-117">This example runs the last, or most recent, command in the session history.</span></span> <span data-ttu-id="232e2-118">您可以將此命令縮寫為 `r` 的別名 `Invoke-History` 。</span><span class="sxs-lookup"><span data-stu-id="232e2-118">You can abbreviate this command as `r`, the alias for `Invoke-History`.</span></span>

```powershell
Invoke-History
```

### <span data-ttu-id="232e2-119">範例2：執行具有指定識別碼的命令</span><span class="sxs-lookup"><span data-stu-id="232e2-119">Example 2: Run the command that has a specified ID</span></span>

<span data-ttu-id="232e2-120">此範例會在 **識別碼** 為132的會話歷程記錄中執行命令。</span><span class="sxs-lookup"><span data-stu-id="232e2-120">This example runs the command in the session history with **Id** 132.</span></span> <span data-ttu-id="232e2-121">因為 **Id** 參數的名稱是選擇性的，所以您可以將此命令縮寫為下列內容： `Invoke-History 132` 、 `ihy 132` 或 `r 132` 。</span><span class="sxs-lookup"><span data-stu-id="232e2-121">Because the name of the **Id** parameter is optional, you can abbreviate this command as the following: `Invoke-History 132`, `ihy 132`, or `r 132`.</span></span>

```powershell
Invoke-History -Id 132
```

### <span data-ttu-id="232e2-122">範例3：使用命令文字執行最新的命令</span><span class="sxs-lookup"><span data-stu-id="232e2-122">Example 3: Run the most recent command by using the command text</span></span>

<span data-ttu-id="232e2-123">此範例會在會話歷程記錄中執行最新的 `Get-Process` 命令。</span><span class="sxs-lookup"><span data-stu-id="232e2-123">This example runs the most recent `Get-Process` command in the session history.</span></span> <span data-ttu-id="232e2-124">當您輸入 **Id** 參數的字元時， `Invoke-History` 會執行它所找到的第一個符合模式的命令，從最新的命令開始。</span><span class="sxs-lookup"><span data-stu-id="232e2-124">When you type characters for the **Id** parameter, `Invoke-History` runs the first command that it finds that matches the pattern, starting with the most recent commands.</span></span>

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> <span data-ttu-id="232e2-125">模式比對不區分大小寫，但模式符合該行的開頭。</span><span class="sxs-lookup"><span data-stu-id="232e2-125">Pattern matching is case-insensitive, but the pattern matches the beginning of the line.</span></span>

### <span data-ttu-id="232e2-126">範例4：從歷程記錄執行一連串的命令</span><span class="sxs-lookup"><span data-stu-id="232e2-126">Example 4: Run a sequence of commands from the history</span></span>

<span data-ttu-id="232e2-127">此範例會執行命令16到24。</span><span class="sxs-lookup"><span data-stu-id="232e2-127">This example runs commands 16 through 24.</span></span> <span data-ttu-id="232e2-128">因為您只能列出一個 **識別碼** 值，所以命令會使用 `ForEach-Object` Cmdlet 來 `Invoke-History` 針對每個 **識別碼** 值執行一次命令。</span><span class="sxs-lookup"><span data-stu-id="232e2-128">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command one time for each **Id** value.</span></span>

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### <span data-ttu-id="232e2-129">範例 5</span><span class="sxs-lookup"><span data-stu-id="232e2-129">Example 5</span></span>

<span data-ttu-id="232e2-130">此範例會在記錄中執行以命令 255 (249 到 255) 結尾的七個命令。</span><span class="sxs-lookup"><span data-stu-id="232e2-130">This example runs the seven commands in the history that end with command 255 (249 through 255).</span></span> <span data-ttu-id="232e2-131">它會使用 `Get-History` Cmdlet 來取得命令。</span><span class="sxs-lookup"><span data-stu-id="232e2-131">It uses the `Get-History` cmdlet to retrieve the commands.</span></span> <span data-ttu-id="232e2-132">因為您只能列出一個 **識別碼** 值，所以命令會使用 `ForEach-Object` Cmdlet `Invoke-History` 針對每個 **識別碼** 值執行一次命令。</span><span class="sxs-lookup"><span data-stu-id="232e2-132">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command once for each **Id** value.</span></span>

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## <span data-ttu-id="232e2-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="232e2-133">PARAMETERS</span></span>

### <span data-ttu-id="232e2-134">-Id</span><span class="sxs-lookup"><span data-stu-id="232e2-134">-Id</span></span>

<span data-ttu-id="232e2-135">指定記錄中命令的 **識別碼** 。</span><span class="sxs-lookup"><span data-stu-id="232e2-135">Specifies the **Id** of a command in the history.</span></span> <span data-ttu-id="232e2-136">您可以輸入命令的 **識別碼** 或命令的前幾個字元。</span><span class="sxs-lookup"><span data-stu-id="232e2-136">You can type the **Id** number of the command or the first few characters of the command.</span></span>

<span data-ttu-id="232e2-137">如果您輸入字元，則會 `Invoke-History` 先符合最新的命令。</span><span class="sxs-lookup"><span data-stu-id="232e2-137">If you type characters, `Invoke-History` matches the most recent commands first.</span></span> <span data-ttu-id="232e2-138">如果您省略此參數，則會 `Invoke-History` 執行最後一個或最新的命令。</span><span class="sxs-lookup"><span data-stu-id="232e2-138">If you omit this parameter, `Invoke-History` runs the last, or most recent, command.</span></span> <span data-ttu-id="232e2-139">若要尋找命令的 **識別碼** ，請使用 `Get-History` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="232e2-139">To find the **Id** number of a command, use the `Get-History` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="232e2-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="232e2-140">-Confirm</span></span>

<span data-ttu-id="232e2-141">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="232e2-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="232e2-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="232e2-142">-WhatIf</span></span>

<span data-ttu-id="232e2-143">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="232e2-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="232e2-144">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="232e2-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="232e2-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="232e2-145">CommonParameters</span></span>

<span data-ttu-id="232e2-146">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="232e2-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="232e2-147">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="232e2-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="232e2-148">輸入</span><span class="sxs-lookup"><span data-stu-id="232e2-148">INPUTS</span></span>

### <span data-ttu-id="232e2-149">System.String</span><span class="sxs-lookup"><span data-stu-id="232e2-149">System.String</span></span>

<span data-ttu-id="232e2-150">您可以使用管線將歷程記錄 **識別碼** 傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="232e2-150">You can pipe a history **Id** to this cmdlet.</span></span>

## <span data-ttu-id="232e2-151">輸出</span><span class="sxs-lookup"><span data-stu-id="232e2-151">OUTPUTS</span></span>

### <span data-ttu-id="232e2-152">無</span><span class="sxs-lookup"><span data-stu-id="232e2-152">None</span></span>

<span data-ttu-id="232e2-153">此 Cmdlet 不會產生任何輸出，但輸出可能是由執行的命令所產生 `Invoke-History` 。</span><span class="sxs-lookup"><span data-stu-id="232e2-153">This cmdlet does not generate any output, but output might be generated by the commands that `Invoke-History` runs.</span></span>

## <span data-ttu-id="232e2-154">注意</span><span class="sxs-lookup"><span data-stu-id="232e2-154">NOTES</span></span>

<span data-ttu-id="232e2-155">工作階段歷程記錄是工作階段期間輸入的命令清單。</span><span class="sxs-lookup"><span data-stu-id="232e2-155">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="232e2-156">工作階段歷程記錄代表命令的執行順序、狀態及開始和結束時間。</span><span class="sxs-lookup"><span data-stu-id="232e2-156">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="232e2-157">當您輸入每個命令時，PowerShell 會將它新增至歷程記錄，以便您可以重複使用。</span><span class="sxs-lookup"><span data-stu-id="232e2-157">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="232e2-158">如需會話歷程記錄的詳細資訊，請參閱 [about_History](About/about_History.md)。</span><span class="sxs-lookup"><span data-stu-id="232e2-158">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="232e2-159">您也可以 `Invoke-History` 使用內建的別名和來參考 `r` `ihy` 。</span><span class="sxs-lookup"><span data-stu-id="232e2-159">You can also refer to `Invoke-History` by its built-in aliases, `r` and `ihy`.</span></span> <span data-ttu-id="232e2-160">如需詳細資訊，請參閱 [about_Aliases](About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="232e2-160">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="232e2-161">相關連結</span><span class="sxs-lookup"><span data-stu-id="232e2-161">RELATED LINKS</span></span>

[<span data-ttu-id="232e2-162">Add-History</span><span class="sxs-lookup"><span data-stu-id="232e2-162">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="232e2-163">Clear-History</span><span class="sxs-lookup"><span data-stu-id="232e2-163">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="232e2-164">Get-History</span><span class="sxs-lookup"><span data-stu-id="232e2-164">Get-History</span></span>](Get-History.md)
