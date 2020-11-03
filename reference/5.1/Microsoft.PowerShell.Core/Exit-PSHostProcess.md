---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 29a72bac55dd4aabca52673a192b13f75b88f308
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93196688"
---
# <span data-ttu-id="947a7-103">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="947a7-103">Exit-PSHostProcess</span></span>

## <span data-ttu-id="947a7-104">概要</span><span class="sxs-lookup"><span data-stu-id="947a7-104">SYNOPSIS</span></span>
<span data-ttu-id="947a7-105">關閉具有本機進程的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="947a7-105">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="947a7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="947a7-106">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="947a7-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="947a7-107">DESCRIPTION</span></span>
<span data-ttu-id="947a7-108">**>enter-pshostprocess** 指令程式會透過執行 Enter-PSHostProcess Cmdlet，關閉您已開啟的本機進程的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="947a7-108">The **Exit-PSHostProcess** cmdlet closes an interactive session with a local process that you have opened by running the Enter-PSHostProcess cmdlet.</span></span>
<span data-ttu-id="947a7-109">當您完成對在進程中執行的腳本進行錯錯或疑難排解時，您可以從進程內執行 **>enter-pshostprocess 指令程式** 。</span><span class="sxs-lookup"><span data-stu-id="947a7-109">You run the **Exit-PSHostProcess** cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span>

## <span data-ttu-id="947a7-110">範例</span><span class="sxs-lookup"><span data-stu-id="947a7-110">EXAMPLES</span></span>

### <span data-ttu-id="947a7-111">範例1：結束處理常式</span><span class="sxs-lookup"><span data-stu-id="947a7-111">Example 1: Exit a process</span></span>

```
PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

<span data-ttu-id="947a7-112">在此範例中，您已在使用中的進程中處理，以在進程的運行空間中對執行的腳本進行 debug 錯，如 >enter-pshostprocess 中所述。</span><span class="sxs-lookup"><span data-stu-id="947a7-112">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in Enter-PSHostProcess.</span></span>
<span data-ttu-id="947a7-113">輸入 **exit** 命令以結束偵錯工具之後，請執行 **>enter-pshostprocess** 指令程式，以關閉進程的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="947a7-113">After you type the **exit** command to exit the debugger, run the **Exit-PSHostProcess** cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="947a7-114">此 Cmdlet 會關閉進程中的會話，並讓您回到 PS C： \\ \> 提示字元。</span><span class="sxs-lookup"><span data-stu-id="947a7-114">The cmdlet closes your session in the process, and returns you to the PS C:\\\> prompt.</span></span>

## <span data-ttu-id="947a7-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="947a7-115">PARAMETERS</span></span>

### <span data-ttu-id="947a7-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="947a7-116">CommonParameters</span></span>
<span data-ttu-id="947a7-117">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="947a7-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="947a7-118">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="947a7-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="947a7-119">輸入</span><span class="sxs-lookup"><span data-stu-id="947a7-119">INPUTS</span></span>

## <span data-ttu-id="947a7-120">輸出</span><span class="sxs-lookup"><span data-stu-id="947a7-120">OUTPUTS</span></span>

## <span data-ttu-id="947a7-121">注意</span><span class="sxs-lookup"><span data-stu-id="947a7-121">NOTES</span></span>

## <span data-ttu-id="947a7-122">相關連結</span><span class="sxs-lookup"><span data-stu-id="947a7-122">RELATED LINKS</span></span>

[<span data-ttu-id="947a7-123">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="947a7-123">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)
