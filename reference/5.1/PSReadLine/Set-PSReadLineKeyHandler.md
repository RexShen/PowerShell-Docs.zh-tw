---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadline
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 8eefd819b59cf8d0050484c6aad3058bc6e7753a
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208736"
---
# <span data-ttu-id="5f0ad-103">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="5f0ad-103">Set-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="5f0ad-104">概要</span><span class="sxs-lookup"><span data-stu-id="5f0ad-104">SYNOPSIS</span></span>
<span data-ttu-id="5f0ad-105">將索引鍵系結至使用者定義或 PSReadLine 的索引鍵處理函式。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-105">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

## <span data-ttu-id="5f0ad-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5f0ad-106">SYNTAX</span></span>

### <span data-ttu-id="5f0ad-107">ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="5f0ad-107">ScriptBlock</span></span>

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### <span data-ttu-id="5f0ad-108">函式</span><span class="sxs-lookup"><span data-stu-id="5f0ad-108">Function</span></span>

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## <span data-ttu-id="5f0ad-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5f0ad-109">DESCRIPTION</span></span>

<span data-ttu-id="5f0ad-110">`Set-PSReadLineKeyHandler`Cmdlet 會在按下按鍵或按鍵序列時自訂結果。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-110">The `Set-PSReadLineKeyHandler` cmdlet customizes the result when a key or sequence of keys is pressed.</span></span> <span data-ttu-id="5f0ad-111">透過使用者定義的金鑰系結，您幾乎可以從 PowerShell 腳本內進行任何可能的作業。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-111">With user-defined key bindings, you can do almost anything that is possible from within a PowerShell script.</span></span>

## <span data-ttu-id="5f0ad-112">範例</span><span class="sxs-lookup"><span data-stu-id="5f0ad-112">EXAMPLES</span></span>

### <span data-ttu-id="5f0ad-113">範例1：將箭號系結至函式</span><span class="sxs-lookup"><span data-stu-id="5f0ad-113">Example 1: Bind the arrow key to a function</span></span>

<span data-ttu-id="5f0ad-114">此命令會將向上箭號系結至 **HistorySearchBackward** 函式。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-114">This command binds the up arrow key to the **HistorySearchBackward** function.</span></span> <span data-ttu-id="5f0ad-115">此函式會搜尋命令列的命令歷程記錄，其開頭為命令列的目前內容。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-115">This function searches command history for command lines that start with the current contents of the command line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### <span data-ttu-id="5f0ad-116">範例2：將索引鍵系結至腳本區塊</span><span class="sxs-lookup"><span data-stu-id="5f0ad-116">Example 2: Bind a key to a script block</span></span>

<span data-ttu-id="5f0ad-117">這個範例會示範如何使用單一索引鍵來執行命令。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-117">This example shows how a single key can be used to run a command.</span></span> <span data-ttu-id="5f0ad-118">此命令會將金鑰系結 `Ctrl+B` 至清除該行的腳本區塊、插入 "build" 一字，然後接受該行。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-118">The command binds the key `Ctrl+B` to a script block that clears the line, inserts the word "build", and then accepts the line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## <span data-ttu-id="5f0ad-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5f0ad-119">PARAMETERS</span></span>

### <span data-ttu-id="5f0ad-120">-BriefDescription</span><span class="sxs-lookup"><span data-stu-id="5f0ad-120">-BriefDescription</span></span>

<span data-ttu-id="5f0ad-121">按鍵系結的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-121">A brief description of the key binding.</span></span> <span data-ttu-id="5f0ad-122">Cmdlet 會顯示此描述 `Get-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-122">This description is displayed by the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f0ad-123">-弦</span><span class="sxs-lookup"><span data-stu-id="5f0ad-123">-Chord</span></span>

<span data-ttu-id="5f0ad-124">要系結至函數或腳本區塊的索引鍵或索引鍵序列。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-124">The key or sequence of keys to be bound to a function or script block.</span></span> <span data-ttu-id="5f0ad-125">使用單一字串來指定單一系結。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-125">Use a single string to specify a single binding.</span></span> <span data-ttu-id="5f0ad-126">如果系結是索引鍵的序列，請以逗號分隔索引鍵，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5f0ad-126">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+X,Ctrl+L`

<span data-ttu-id="5f0ad-127">此參數接受字串陣列。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-127">This parameter accepts an array of strings.</span></span> <span data-ttu-id="5f0ad-128">每個字串都是個別的系結，而不是單一系結的索引鍵序列。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-128">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f0ad-129">-Description</span><span class="sxs-lookup"><span data-stu-id="5f0ad-129">-Description</span></span>

<span data-ttu-id="5f0ad-130">指定 Cmdlet 輸出中可見的按鍵系結更詳細描述 `Get-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-130">Specifies a more detailed description of the key binding that is visible in the output of the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases: LongDescription

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f0ad-131">-Function</span><span class="sxs-lookup"><span data-stu-id="5f0ad-131">-Function</span></span>

<span data-ttu-id="5f0ad-132">指定 PSReadLine 所提供之現有金鑰處理常式的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-132">Specifies the name of an existing key handler provided by PSReadLine.</span></span> <span data-ttu-id="5f0ad-133">此參數可讓您重新系結現有的金鑰系結，或系結目前未系結的處理常式。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-133">This parameter lets you rebind existing key bindings, or bind a handler that is currently unbound.</span></span>

```yaml
Type: System.String
Parameter Sets: Function
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f0ad-134">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="5f0ad-134">-ScriptBlock</span></span>

<span data-ttu-id="5f0ad-135">指定輸入弦時要執行的腳本區塊值。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-135">Specifies a script block value to run when the chord is entered.</span></span> <span data-ttu-id="5f0ad-136">PSReadLine 會將一或兩個參數傳遞至這個腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-136">PSReadLine passes one or two parameters to this script block.</span></span> <span data-ttu-id="5f0ad-137">第一個參數是 **ConsoleKeyInfo** 物件，代表按下的按鍵。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-137">The first parameter is a **ConsoleKeyInfo** object representing the key pressed.</span></span> <span data-ttu-id="5f0ad-138">第二個引數可以是任何物件（視內容而定）。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-138">The second argument can be any object depending on the context.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f0ad-139">-ViMode</span><span class="sxs-lookup"><span data-stu-id="5f0ad-139">-ViMode</span></span>

<span data-ttu-id="5f0ad-140">指定要套用系結的 vi 模式。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-140">Specify which vi mode the binding applies to.</span></span>

<span data-ttu-id="5f0ad-141">有效值為：</span><span class="sxs-lookup"><span data-stu-id="5f0ad-141">Valid values are:</span></span>

- <span data-ttu-id="5f0ad-142">插入</span><span class="sxs-lookup"><span data-stu-id="5f0ad-142">Insert</span></span>
- <span data-ttu-id="5f0ad-143">Command</span><span class="sxs-lookup"><span data-stu-id="5f0ad-143">Command</span></span>

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f0ad-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5f0ad-144">CommonParameters</span></span>

<span data-ttu-id="5f0ad-145">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5f0ad-146">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5f0ad-147">輸入</span><span class="sxs-lookup"><span data-stu-id="5f0ad-147">INPUTS</span></span>

### <span data-ttu-id="5f0ad-148">無</span><span class="sxs-lookup"><span data-stu-id="5f0ad-148">None</span></span>

<span data-ttu-id="5f0ad-149">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-149">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="5f0ad-150">輸出</span><span class="sxs-lookup"><span data-stu-id="5f0ad-150">OUTPUTS</span></span>

### <span data-ttu-id="5f0ad-151">無</span><span class="sxs-lookup"><span data-stu-id="5f0ad-151">None</span></span>

<span data-ttu-id="5f0ad-152">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="5f0ad-152">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5f0ad-153">注意</span><span class="sxs-lookup"><span data-stu-id="5f0ad-153">NOTES</span></span>

## <span data-ttu-id="5f0ad-154">相關連結</span><span class="sxs-lookup"><span data-stu-id="5f0ad-154">RELATED LINKS</span></span>

[<span data-ttu-id="5f0ad-155">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="5f0ad-155">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="5f0ad-156">移除-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="5f0ad-156">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="5f0ad-157">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="5f0ad-157">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="5f0ad-158">設定-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="5f0ad-158">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)