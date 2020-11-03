---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-debugger?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Debugger
ms.openlocfilehash: 7c850b94e2c64d8beb72a83fe8ae503594d20864
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200861"
---
# <span data-ttu-id="9db1e-103">Wait-Debugger</span><span class="sxs-lookup"><span data-stu-id="9db1e-103">Wait-Debugger</span></span>

## <span data-ttu-id="9db1e-104">概要</span><span class="sxs-lookup"><span data-stu-id="9db1e-104">SYNOPSIS</span></span>
<span data-ttu-id="9db1e-105">先停止偵錯工具中的腳本，再執行腳本中的下一個語句。</span><span class="sxs-lookup"><span data-stu-id="9db1e-105">Stops a script in the debugger before running the next statement in the script.</span></span>

## <span data-ttu-id="9db1e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9db1e-106">SYNTAX</span></span>

```
Wait-Debugger [<CommonParameters>]
```

## <span data-ttu-id="9db1e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9db1e-107">DESCRIPTION</span></span>

<span data-ttu-id="9db1e-108">在指令程式之後的時間點停止 PowerShell 腳本執行引擎 `Wait-Debugger` ，並等候附加偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="9db1e-108">Stops the PowerShell script execution engine at the point immediately after the `Wait-Debugger` cmdlet and waits for a debugger to be attached.</span></span> <span data-ttu-id="9db1e-109">這類似于 `Enable-RunspaceDebug -BreakAll` 在 DSC 資源中使用，但會在腳本中的特定點中斷。</span><span class="sxs-lookup"><span data-stu-id="9db1e-109">This is similar to using `Enable-RunspaceDebug -BreakAll` in a DSC resource but breaks at a specific point in the script.</span></span>

> [!CAUTION]
> <span data-ttu-id="9db1e-110">完成之後，請務必移除這些 `Wait-Debugger` 行。</span><span class="sxs-lookup"><span data-stu-id="9db1e-110">Make sure you remove the `Wait-Debugger` lines after you are done.</span></span> <span data-ttu-id="9db1e-111">當執行中的腳本在停止時，就會出現無反應 `Wait-Debugger` 。</span><span class="sxs-lookup"><span data-stu-id="9db1e-111">A running script appears to be hung when it is stopped at a `Wait-Debugger`.</span></span>

## <span data-ttu-id="9db1e-112">範例</span><span class="sxs-lookup"><span data-stu-id="9db1e-112">EXAMPLES</span></span>

### <span data-ttu-id="9db1e-113">範例1：用於偵錯工具的插入中斷點</span><span class="sxs-lookup"><span data-stu-id="9db1e-113">Example 1: Insert breakpoint for debugging</span></span>

```
[DscResource()]
class FileResource
{
    [DscProperty(Key)]
    [string] $Path

    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    [DscProperty(Mandatory)]
    [string] $SourcePath

    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime


    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (! $fileExists)
            {
               $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    [bool] Test()
    {
        $present = Test-Path -LiteralPath $this.Path

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return (! $present)
        }
    }

    [FileResource] Get()
    {
        $present = Test-Path -Path $this.Path

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    [void] CopyFile()
    {
        # Testing only - Remove before deployment!
        Wait-Debugger

        if (! (Test-Path -LiteralPath $this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose "Copying $($this.SourcePath) to $($this.Path)"

        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <span data-ttu-id="9db1e-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9db1e-114">PARAMETERS</span></span>

### <span data-ttu-id="9db1e-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9db1e-115">CommonParameters</span></span>

<span data-ttu-id="9db1e-116">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9db1e-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9db1e-117">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="9db1e-117">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9db1e-118">輸入</span><span class="sxs-lookup"><span data-stu-id="9db1e-118">INPUTS</span></span>

### <span data-ttu-id="9db1e-119">無</span><span class="sxs-lookup"><span data-stu-id="9db1e-119">None</span></span>

## <span data-ttu-id="9db1e-120">輸出</span><span class="sxs-lookup"><span data-stu-id="9db1e-120">OUTPUTS</span></span>

### <span data-ttu-id="9db1e-121">無</span><span class="sxs-lookup"><span data-stu-id="9db1e-121">None</span></span>

## <span data-ttu-id="9db1e-122">注意</span><span class="sxs-lookup"><span data-stu-id="9db1e-122">NOTES</span></span>

## <span data-ttu-id="9db1e-123">相關連結</span><span class="sxs-lookup"><span data-stu-id="9db1e-123">RELATED LINKS</span></span>

[<span data-ttu-id="9db1e-124">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="9db1e-124">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
