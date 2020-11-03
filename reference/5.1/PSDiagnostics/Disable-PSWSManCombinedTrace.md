---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 4a98941de072b9b57b89a25bc180c0ee391d8b63
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203067"
---
# <span data-ttu-id="3742b-103">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="3742b-103">Disable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="3742b-104">概要</span><span class="sxs-lookup"><span data-stu-id="3742b-104">SYNOPSIS</span></span>
<span data-ttu-id="3742b-105">停止 PSWSManCombinedTrace 啟動的記錄會話。</span><span class="sxs-lookup"><span data-stu-id="3742b-105">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

## <span data-ttu-id="3742b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3742b-106">SYNTAX</span></span>

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## <span data-ttu-id="3742b-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3742b-107">DESCRIPTION</span></span>

<span data-ttu-id="3742b-108">此 Cmdlet 會停止啟動的記錄會話 `Enable-PSWSManCombinedTrace` 。</span><span class="sxs-lookup"><span data-stu-id="3742b-108">This cmdlet stops the logging session started by `Enable-PSWSManCombinedTrace`.</span></span>

<span data-ttu-id="3742b-109">此 Cmdlet 會使用 `Stop-Trace` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3742b-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="3742b-110">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3742b-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="3742b-111">範例</span><span class="sxs-lookup"><span data-stu-id="3742b-111">EXAMPLES</span></span>

### <span data-ttu-id="3742b-112">範例1：停用合併的記錄會話</span><span class="sxs-lookup"><span data-stu-id="3742b-112">Example 1: Disable the combined logging session</span></span>

```powershell
Disable-PSWSManCombinedTrace
```

## <span data-ttu-id="3742b-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3742b-113">PARAMETERS</span></span>

### <span data-ttu-id="3742b-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3742b-114">CommonParameters</span></span>

<span data-ttu-id="3742b-115">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3742b-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3742b-116">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3742b-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3742b-117">輸入</span><span class="sxs-lookup"><span data-stu-id="3742b-117">INPUTS</span></span>

### <span data-ttu-id="3742b-118">無</span><span class="sxs-lookup"><span data-stu-id="3742b-118">None</span></span>

## <span data-ttu-id="3742b-119">輸出</span><span class="sxs-lookup"><span data-stu-id="3742b-119">OUTPUTS</span></span>

### <span data-ttu-id="3742b-120">System.Object</span><span class="sxs-lookup"><span data-stu-id="3742b-120">System.Object</span></span>

## <span data-ttu-id="3742b-121">注意</span><span class="sxs-lookup"><span data-stu-id="3742b-121">NOTES</span></span>

## <span data-ttu-id="3742b-122">相關連結</span><span class="sxs-lookup"><span data-stu-id="3742b-122">RELATED LINKS</span></span>

[<span data-ttu-id="3742b-123">事件追蹤</span><span class="sxs-lookup"><span data-stu-id="3742b-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="3742b-124">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="3742b-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="3742b-125">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="3742b-125">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)
