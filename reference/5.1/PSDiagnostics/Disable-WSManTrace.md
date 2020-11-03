---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 90cb571f93243e6fbc59970e5602911e17e25ec7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203060"
---
# <span data-ttu-id="ebab0-103">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="ebab0-103">Disable-WSManTrace</span></span>

## <span data-ttu-id="ebab0-104">概要</span><span class="sxs-lookup"><span data-stu-id="ebab0-104">SYNOPSIS</span></span>
<span data-ttu-id="ebab0-105">停止啟用-WSManTrace 所啟動的 WSMan 記錄會話。</span><span class="sxs-lookup"><span data-stu-id="ebab0-105">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="ebab0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ebab0-106">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="ebab0-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ebab0-107">DESCRIPTION</span></span>
<span data-ttu-id="ebab0-108">此 Cmdlet 會停止 WSManTrace 啟動的 WSMan 記錄會話。</span><span class="sxs-lookup"><span data-stu-id="ebab0-108">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="ebab0-109">此 Cmdlet 會使用 `Stop-Trace` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ebab0-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="ebab0-110">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ebab0-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="ebab0-111">範例</span><span class="sxs-lookup"><span data-stu-id="ebab0-111">EXAMPLES</span></span>

### <span data-ttu-id="ebab0-112">範例1：停止 WSMan 追蹤</span><span class="sxs-lookup"><span data-stu-id="ebab0-112">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="ebab0-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ebab0-113">PARAMETERS</span></span>

### <span data-ttu-id="ebab0-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ebab0-114">CommonParameters</span></span>

<span data-ttu-id="ebab0-115">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ebab0-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ebab0-116">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ebab0-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ebab0-117">輸入</span><span class="sxs-lookup"><span data-stu-id="ebab0-117">INPUTS</span></span>

### <span data-ttu-id="ebab0-118">無</span><span class="sxs-lookup"><span data-stu-id="ebab0-118">None</span></span>

## <span data-ttu-id="ebab0-119">輸出</span><span class="sxs-lookup"><span data-stu-id="ebab0-119">OUTPUTS</span></span>

### <span data-ttu-id="ebab0-120">System.Object</span><span class="sxs-lookup"><span data-stu-id="ebab0-120">System.Object</span></span>

## <span data-ttu-id="ebab0-121">注意</span><span class="sxs-lookup"><span data-stu-id="ebab0-121">NOTES</span></span>

## <span data-ttu-id="ebab0-122">相關連結</span><span class="sxs-lookup"><span data-stu-id="ebab0-122">RELATED LINKS</span></span>

[<span data-ttu-id="ebab0-123">事件追蹤</span><span class="sxs-lookup"><span data-stu-id="ebab0-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="ebab0-124">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="ebab0-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="ebab0-125">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="ebab0-125">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
