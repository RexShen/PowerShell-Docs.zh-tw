---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: f7ec371e0d9826dc095fbf71c4785cae2856875b
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93196708"
---
# <span data-ttu-id="fca15-103">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="fca15-103">Disable-WSManTrace</span></span>

## <span data-ttu-id="fca15-104">概要</span><span class="sxs-lookup"><span data-stu-id="fca15-104">SYNOPSIS</span></span>
<span data-ttu-id="fca15-105">停止啟用-WSManTrace 所啟動的 WSMan 記錄會話。</span><span class="sxs-lookup"><span data-stu-id="fca15-105">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="fca15-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fca15-106">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="fca15-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fca15-107">DESCRIPTION</span></span>
<span data-ttu-id="fca15-108">此 Cmdlet 會停止 WSManTrace 啟動的 WSMan 記錄會話。</span><span class="sxs-lookup"><span data-stu-id="fca15-108">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="fca15-109">此 Cmdlet 會使用 `Stop-Trace` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fca15-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="fca15-110">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fca15-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="fca15-111">範例</span><span class="sxs-lookup"><span data-stu-id="fca15-111">EXAMPLES</span></span>

### <span data-ttu-id="fca15-112">範例1：停止 WSMan 追蹤</span><span class="sxs-lookup"><span data-stu-id="fca15-112">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="fca15-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fca15-113">PARAMETERS</span></span>

### <span data-ttu-id="fca15-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fca15-114">CommonParameters</span></span>

<span data-ttu-id="fca15-115">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="fca15-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fca15-116">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="fca15-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fca15-117">輸入</span><span class="sxs-lookup"><span data-stu-id="fca15-117">INPUTS</span></span>

### <span data-ttu-id="fca15-118">無</span><span class="sxs-lookup"><span data-stu-id="fca15-118">None</span></span>

## <span data-ttu-id="fca15-119">輸出</span><span class="sxs-lookup"><span data-stu-id="fca15-119">OUTPUTS</span></span>

### <span data-ttu-id="fca15-120">無</span><span class="sxs-lookup"><span data-stu-id="fca15-120">None</span></span>

## <span data-ttu-id="fca15-121">注意</span><span class="sxs-lookup"><span data-stu-id="fca15-121">NOTES</span></span>

## <span data-ttu-id="fca15-122">相關連結</span><span class="sxs-lookup"><span data-stu-id="fca15-122">RELATED LINKS</span></span>

[<span data-ttu-id="fca15-123">事件追蹤</span><span class="sxs-lookup"><span data-stu-id="fca15-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="fca15-124">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="fca15-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="fca15-125">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="fca15-125">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
