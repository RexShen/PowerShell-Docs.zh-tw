---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 854769bea9c1b3c104f87d99909f6201a39cac42
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200891"
---
# <span data-ttu-id="a9f21-103">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="a9f21-103">Disable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="a9f21-104">概要</span><span class="sxs-lookup"><span data-stu-id="a9f21-104">SYNOPSIS</span></span>
<span data-ttu-id="a9f21-105">停止 PSWSManCombinedTrace 啟動的記錄會話。</span><span class="sxs-lookup"><span data-stu-id="a9f21-105">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

## <span data-ttu-id="a9f21-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a9f21-106">SYNTAX</span></span>

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## <span data-ttu-id="a9f21-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a9f21-107">DESCRIPTION</span></span>

<span data-ttu-id="a9f21-108">此 Cmdlet 會停止啟動的記錄會話 `Enable-PSWSManCombinedTrace` 。</span><span class="sxs-lookup"><span data-stu-id="a9f21-108">This cmdlet stops the logging session started by `Enable-PSWSManCombinedTrace`.</span></span>

<span data-ttu-id="a9f21-109">此 Cmdlet 會使用 `Stop-Trace` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a9f21-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="a9f21-110">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a9f21-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="a9f21-111">範例</span><span class="sxs-lookup"><span data-stu-id="a9f21-111">EXAMPLES</span></span>

### <span data-ttu-id="a9f21-112">範例1：停用合併的記錄會話</span><span class="sxs-lookup"><span data-stu-id="a9f21-112">Example 1: Disable the combined logging session</span></span>

```powershell
Disable-PSWSManCombinedTrace
```

## <span data-ttu-id="a9f21-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a9f21-113">PARAMETERS</span></span>

### <span data-ttu-id="a9f21-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a9f21-114">CommonParameters</span></span>

<span data-ttu-id="a9f21-115">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a9f21-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a9f21-116">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a9f21-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a9f21-117">輸入</span><span class="sxs-lookup"><span data-stu-id="a9f21-117">INPUTS</span></span>

### <span data-ttu-id="a9f21-118">無</span><span class="sxs-lookup"><span data-stu-id="a9f21-118">None</span></span>

## <span data-ttu-id="a9f21-119">輸出</span><span class="sxs-lookup"><span data-stu-id="a9f21-119">OUTPUTS</span></span>

### <span data-ttu-id="a9f21-120">無</span><span class="sxs-lookup"><span data-stu-id="a9f21-120">None</span></span>

## <span data-ttu-id="a9f21-121">注意</span><span class="sxs-lookup"><span data-stu-id="a9f21-121">NOTES</span></span>

## <span data-ttu-id="a9f21-122">相關連結</span><span class="sxs-lookup"><span data-stu-id="a9f21-122">RELATED LINKS</span></span>

[<span data-ttu-id="a9f21-123">事件追蹤</span><span class="sxs-lookup"><span data-stu-id="a9f21-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="a9f21-124">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="a9f21-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="a9f21-125">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="a9f21-125">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

