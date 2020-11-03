---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: 4e0b79cae4af290c64f579217a3731aaac401d6d
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93196724"
---
# <span data-ttu-id="f99f9-103">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="f99f9-103">Exit-PSSession</span></span>

## <span data-ttu-id="f99f9-104">概要</span><span class="sxs-lookup"><span data-stu-id="f99f9-104">SYNOPSIS</span></span>
<span data-ttu-id="f99f9-105">結束遠端電腦的互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="f99f9-105">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="f99f9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f99f9-106">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="f99f9-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f99f9-107">DESCRIPTION</span></span>

<span data-ttu-id="f99f9-108">**Exit-PSSession** Cmdlet 結束您使用 Enter-PSSession Cmdlet 啟動的互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="f99f9-108">The **Exit-PSSession** cmdlet ends interactive sessions that you started by using the Enter-PSSession cmdlet.</span></span>

<span data-ttu-id="f99f9-109">您也可以使用 **Exit** 關鍵字結束互動式會話。</span><span class="sxs-lookup"><span data-stu-id="f99f9-109">You can also use the **Exit** keyword to end an interactive session.</span></span>
<span data-ttu-id="f99f9-110">效果與使用 **Exit-PSSession** 相同。</span><span class="sxs-lookup"><span data-stu-id="f99f9-110">The effect is the same as using **Exit-PSSession** .</span></span>

## <span data-ttu-id="f99f9-111">範例</span><span class="sxs-lookup"><span data-stu-id="f99f9-111">EXAMPLES</span></span>

### <span data-ttu-id="f99f9-112">範例 1︰啟動和停止互動式工作階段</span><span class="sxs-lookup"><span data-stu-id="f99f9-112">Example 1: Start and stop an interactive session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS>
```

<span data-ttu-id="f99f9-113">這些命令會啟動，然後再停止與 Server01 遠端電腦的互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="f99f9-113">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="f99f9-114">範例 2︰使用 PSSession 物件啟動和停止互動式工作階段</span><span class="sxs-lookup"><span data-stu-id="f99f9-114">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="f99f9-115">這些命令會啟動和停止 Server01 電腦的互動式會話，而該電腦使用 ( **PSSession** ) 的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="f99f9-115">These commands start and stop an interactive session with the Server01 computer that uses a PowerShell session ( **PSSession** ).</span></span>

<span data-ttu-id="f99f9-116">因為互動式會話是使用 PowerShell 會話來啟動，所以當互動式會話結束時， **PSSession** 仍然可以使用。</span><span class="sxs-lookup"><span data-stu-id="f99f9-116">Because the interactive session was started by using a PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span>
<span data-ttu-id="f99f9-117">如果您使用 *ComputerName* 參數，則 **輸入-PSSession** 會建立在互動式會話結束時關閉的暫時會話。</span><span class="sxs-lookup"><span data-stu-id="f99f9-117">If you use the *ComputerName* parameter, **Enter-PSSession** creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="f99f9-118">第一個命令使用 New-PSSession Cmdlet 在 Server01 電腦上建立 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="f99f9-118">The first command uses the New-PSSession cmdlet to create a **PSSession** on the Server01 computer.</span></span>
<span data-ttu-id="f99f9-119">命令會將 **PSSession** 儲存在 $s 變數中。</span><span class="sxs-lookup"><span data-stu-id="f99f9-119">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="f99f9-120">第二個命令使用 **Enter-PSSession** 使用 $s 中的 **PSSession** 啟動互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="f99f9-120">The second command uses **Enter-PSSession** to start an interactive session using the **PSSession** in $s.</span></span>

<span data-ttu-id="f99f9-121">第三個命令使用 **Exit-PSSession** 停止互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="f99f9-121">The third command uses **Exit-PSSession** to stop the interactive session.</span></span>

<span data-ttu-id="f99f9-122">最後一個命令會在 $s 變數中顯示 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="f99f9-122">The final command displays the **PSSession** in the $s variable.</span></span>
<span data-ttu-id="f99f9-123">**State** 屬性顯示 **PSSession** 仍然開啟且可供使用。</span><span class="sxs-lookup"><span data-stu-id="f99f9-123">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="f99f9-124">範例 3︰使用 Exit 關鍵字停止工作階段</span><span class="sxs-lookup"><span data-stu-id="f99f9-124">Example 3: Use the Exit keyword to stop a session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> exit
PS>
```

<span data-ttu-id="f99f9-125">此範例使用 **Exit** 關鍵字停止使用 **Enter-PSSession** 啟動的互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="f99f9-125">This example uses the **Exit** keyword to stop an interactive session started by using **Enter-PSSession** .</span></span>
<span data-ttu-id="f99f9-126">**Exit** 關鍵字與使用 **exit-PSSession** 具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="f99f9-126">The **Exit** keyword has the same effect as using **Exit-PSSession** .</span></span>

## <span data-ttu-id="f99f9-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f99f9-127">PARAMETERS</span></span>

### <span data-ttu-id="f99f9-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f99f9-128">CommonParameters</span></span>

<span data-ttu-id="f99f9-129">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f99f9-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f99f9-130">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f99f9-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f99f9-131">輸入</span><span class="sxs-lookup"><span data-stu-id="f99f9-131">INPUTS</span></span>

### <span data-ttu-id="f99f9-132">無</span><span class="sxs-lookup"><span data-stu-id="f99f9-132">None</span></span>

<span data-ttu-id="f99f9-133">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f99f9-133">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="f99f9-134">輸出</span><span class="sxs-lookup"><span data-stu-id="f99f9-134">OUTPUTS</span></span>

### <span data-ttu-id="f99f9-135">無</span><span class="sxs-lookup"><span data-stu-id="f99f9-135">None</span></span>

<span data-ttu-id="f99f9-136">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f99f9-136">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="f99f9-137">注意</span><span class="sxs-lookup"><span data-stu-id="f99f9-137">NOTES</span></span>

* <span data-ttu-id="f99f9-138">此 Cmdlet 只採用一般的參數。</span><span class="sxs-lookup"><span data-stu-id="f99f9-138">This cmdlet takes only the common parameters.</span></span>

*

## <span data-ttu-id="f99f9-139">相關連結</span><span class="sxs-lookup"><span data-stu-id="f99f9-139">RELATED LINKS</span></span>

[<span data-ttu-id="f99f9-140">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="f99f9-140">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="f99f9-141">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="f99f9-141">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="f99f9-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="f99f9-142">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="f99f9-143">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="f99f9-143">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="f99f9-144">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="f99f9-144">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="f99f9-145">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="f99f9-145">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="f99f9-146">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="f99f9-146">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="f99f9-147">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="f99f9-147">Remove-PSSession</span></span>](Remove-PSSession.md)
