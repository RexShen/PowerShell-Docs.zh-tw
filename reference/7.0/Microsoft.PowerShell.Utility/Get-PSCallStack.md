---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: 315965d3103fc7064f522ca84c8aae77e90ceeb0
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200927"
---
# <span data-ttu-id="c9ff3-103">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="c9ff3-103">Get-PSCallStack</span></span>

## <span data-ttu-id="c9ff3-104">概要</span><span class="sxs-lookup"><span data-stu-id="c9ff3-104">SYNOPSIS</span></span>
<span data-ttu-id="c9ff3-105">顯示目前的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-105">Displays the current call stack.</span></span>

## <span data-ttu-id="c9ff3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c9ff3-106">SYNTAX</span></span>

```
Get-PSCallStack [<CommonParameters>]
```

## <span data-ttu-id="c9ff3-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c9ff3-107">DESCRIPTION</span></span>

<span data-ttu-id="c9ff3-108">**Get-pscallstack** 指令 Cmdlet 會顯示目前的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-108">The **Get-PSCallStack** cmdlet displays the current call stack.</span></span>

<span data-ttu-id="c9ff3-109">雖然它是設計來搭配 PowerShell 偵錯工具使用，但您可以使用這個 Cmdlet，在偵錯工具之外的腳本或函式中顯示呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-109">Although it is designed to be used with the PowerShell debugger, you can use this cmdlet to display the call stack in a script or function outside of the debugger.</span></span>

<span data-ttu-id="c9ff3-110">若要在偵錯工具中執行 **get-pscallstack** 命令，請輸入 `k` 或 `Get-PSCallStack` 。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-110">To run a **Get-PSCallStack** command while in the debugger, type `k` or `Get-PSCallStack`.</span></span>

## <span data-ttu-id="c9ff3-111">範例</span><span class="sxs-lookup"><span data-stu-id="c9ff3-111">EXAMPLES</span></span>

### <span data-ttu-id="c9ff3-112">範例1：取得函式的呼叫堆疊</span><span class="sxs-lookup"><span data-stu-id="c9ff3-112">Example 1: Get the call stack for a function</span></span>

```
PS C:\> function my-alias {
$p = $args[0]
Get-Alias | where {$_.definition -like "*$p"} | format-table definition, name -auto
}
PS C:\ps-test> Set-PSBreakpoint -Command my-alias
Command    : my-alias
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : prompt PS C:\> my-alias Get-Content

Entering debug mode. Use h or ? for help.
Hit Command breakpoint on 'prompt:my-alias'
my-alias get-content
[DBG]: PS C:\ps-test> s
$p = $args[0]
DEBUG: Stepped to ':    $p = $args[0]    '
[DBG]: PS C:\ps-test> s
get-alias | Where {$_.Definition -like "*$p*"} | format-table Definition,
[DBG]: PS C:\ps-test>get-pscallstack

Name        CommandLineParameters         UnboundArguments              Location
----        ---------------------         ----------------              --------
prompt      {}                            {}                            prompt
my-alias    {}                            {get-content}                 prompt
prompt      {}                            {}                            prompt PS C:\> [DBG]: PS C:\ps-test> o
Definition  Name
----------  ----
Get-Content gc
Get-Content cat
Get-Content type
```

<span data-ttu-id="c9ff3-113">此命令會使用 **get-pscallstack** 指令程式來顯示我別名的呼叫堆疊，這個簡單的函式會取得 Cmdlet 名稱的別名。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-113">This command uses the **Get-PSCallStack** cmdlet to display the call stack for My-Alias, a simple function that gets the aliases for a cmdlet name.</span></span>

<span data-ttu-id="c9ff3-114">第一個命令會在 PowerShell 提示字元中輸入函式。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-114">The first command enters the function at the PowerShell prompt.</span></span>
<span data-ttu-id="c9ff3-115">第二個命令使用 Set-PSBreakpoint Cmdlet 在 My-Alias 函式上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-115">The second command uses the Set-PSBreakpoint cmdlet to set a breakpoint on the My-Alias function.</span></span>
<span data-ttu-id="c9ff3-116">第三個命令使用 My-Alias 函式取得目前工作階段中 Get-Content Cmdlet 的所有別名。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-116">The third command uses the My-Alias function to get all of the aliases in the current session for the Get-Content cmdlet.</span></span>

<span data-ttu-id="c9ff3-117">偵錯工具會在函式呼叫時中斷。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-117">The debugger breaks in at the function call.</span></span>
<span data-ttu-id="c9ff3-118">兩個連續「逐步執行」命令 (s) 開始逐行執行函式。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-118">Two consecutive step-into (s) commands begin executing the function line by line.</span></span>
<span data-ttu-id="c9ff3-119">然後，會使用 **get-pscallstack** 命令來取得呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-119">Then, a **Get-PSCallStack** command is used to retrieve the call stack.</span></span>

<span data-ttu-id="c9ff3-120">最後一個命令是「跳離」命令 (o)，它會結束偵錯工具，並繼續執行指令碼直到完成。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-120">The final command is a Step-Out command (o) that exits the debugger and continues executing the script to completion.</span></span>

## <span data-ttu-id="c9ff3-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c9ff3-121">PARAMETERS</span></span>

### <span data-ttu-id="c9ff3-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c9ff3-122">CommonParameters</span></span>

<span data-ttu-id="c9ff3-123">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c9ff3-124">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-124">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c9ff3-125">輸入</span><span class="sxs-lookup"><span data-stu-id="c9ff3-125">INPUTS</span></span>

### <span data-ttu-id="c9ff3-126">無</span><span class="sxs-lookup"><span data-stu-id="c9ff3-126">None</span></span>

<span data-ttu-id="c9ff3-127">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-127">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="c9ff3-128">輸出</span><span class="sxs-lookup"><span data-stu-id="c9ff3-128">OUTPUTS</span></span>

### <span data-ttu-id="c9ff3-129">CallStackFrame。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-129">System.Management.Automation.CallStackFrame</span></span>

<span data-ttu-id="c9ff3-130">**Get-pscallstack** 會傳回代表呼叫堆疊中專案的物件。</span><span class="sxs-lookup"><span data-stu-id="c9ff3-130">**Get-PSCallStack** returns an object that represents the items in the call stack.</span></span>

## <span data-ttu-id="c9ff3-131">注意</span><span class="sxs-lookup"><span data-stu-id="c9ff3-131">NOTES</span></span>

## <span data-ttu-id="c9ff3-132">相關連結</span><span class="sxs-lookup"><span data-stu-id="c9ff3-132">RELATED LINKS</span></span>

[<span data-ttu-id="c9ff3-133">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c9ff3-133">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="c9ff3-134">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c9ff3-134">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="c9ff3-135">Format-Table</span><span class="sxs-lookup"><span data-stu-id="c9ff3-135">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="c9ff3-136">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c9ff3-136">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="c9ff3-137">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c9ff3-137">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="c9ff3-138">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c9ff3-138">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
