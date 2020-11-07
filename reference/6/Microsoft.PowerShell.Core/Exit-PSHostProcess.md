---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 1734758d34e89020f579fffa217cef58eb222736
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344043"
---
# <span data-ttu-id="529c2-103">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="529c2-103">Exit-PSHostProcess</span></span>

## <span data-ttu-id="529c2-104">概要</span><span class="sxs-lookup"><span data-stu-id="529c2-104">SYNOPSIS</span></span>
<span data-ttu-id="529c2-105">關閉具有本機進程的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="529c2-105">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="529c2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="529c2-106">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="529c2-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="529c2-107">DESCRIPTION</span></span>

<span data-ttu-id="529c2-108">此 `Exit-PSHostProcess` Cmdlet 會關閉具有本機進程的互動式會話，您可以執行此 Cmdlet 來開啟 `Enter-PSHostProcess` 。</span><span class="sxs-lookup"><span data-stu-id="529c2-108">The `Exit-PSHostProcess` cmdlet closes an interactive session with a local process that you have opened by running the `Enter-PSHostProcess` cmdlet.</span></span> <span data-ttu-id="529c2-109">`Exit-PSHostProcess`當您完成對在進程中執行的腳本進行偵錯工具或針對其進行疑難排解時，您可以從進程內執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="529c2-109">You run the `Exit-PSHostProcess` cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span> <span data-ttu-id="529c2-110">從 PowerShell 6.2 開始，非 Windows 平臺支援此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="529c2-110">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="529c2-111">範例</span><span class="sxs-lookup"><span data-stu-id="529c2-111">EXAMPLES</span></span>

### <span data-ttu-id="529c2-112">範例1：結束處理常式</span><span class="sxs-lookup"><span data-stu-id="529c2-112">Example 1: Exit a process</span></span>

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

<span data-ttu-id="529c2-113">在此範例中，您已在使用中的進程中處理，以依照中的說明，在進程的運行空間中對執行的腳本進行 debug 錯 `Enter-PSHostProcess` 。</span><span class="sxs-lookup"><span data-stu-id="529c2-113">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in `Enter-PSHostProcess`.</span></span> <span data-ttu-id="529c2-114">鍵入 `exit` 命令以結束偵錯工具之後，請執行 Cmdlet， `Exit-PSHostProcess` 以關閉進程的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="529c2-114">After you type the `exit` command to exit the debugger, run the `Exit-PSHostProcess` cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="529c2-115">此 Cmdlet 會關閉進程中的會話，並將您返回 `PS C:\>` 提示字元。</span><span class="sxs-lookup"><span data-stu-id="529c2-115">The cmdlet closes your session in the process, and returns you to the `PS C:\>` prompt.</span></span>

## <span data-ttu-id="529c2-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="529c2-116">PARAMETERS</span></span>

### <span data-ttu-id="529c2-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="529c2-117">CommonParameters</span></span>

<span data-ttu-id="529c2-118">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="529c2-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="529c2-119">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="529c2-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="529c2-120">輸入</span><span class="sxs-lookup"><span data-stu-id="529c2-120">INPUTS</span></span>

## <span data-ttu-id="529c2-121">輸出</span><span class="sxs-lookup"><span data-stu-id="529c2-121">OUTPUTS</span></span>

## <span data-ttu-id="529c2-122">注意</span><span class="sxs-lookup"><span data-stu-id="529c2-122">NOTES</span></span>

## <span data-ttu-id="529c2-123">相關連結</span><span class="sxs-lookup"><span data-stu-id="529c2-123">RELATED LINKS</span></span>

[<span data-ttu-id="529c2-124">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="529c2-124">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)
