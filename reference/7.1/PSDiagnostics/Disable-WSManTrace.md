---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 5566fb2e11311990cea76e6802c84985795c3553
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200888"
---
# <span data-ttu-id="f9092-103">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="f9092-103">Disable-WSManTrace</span></span>

## <span data-ttu-id="f9092-104">概要</span><span class="sxs-lookup"><span data-stu-id="f9092-104">SYNOPSIS</span></span>
<span data-ttu-id="f9092-105">停止啟用-WSManTrace 所啟動的 WSMan 記錄會話。</span><span class="sxs-lookup"><span data-stu-id="f9092-105">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="f9092-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f9092-106">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="f9092-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f9092-107">DESCRIPTION</span></span>
<span data-ttu-id="f9092-108">此 Cmdlet 會停止 WSManTrace 啟動的 WSMan 記錄會話。</span><span class="sxs-lookup"><span data-stu-id="f9092-108">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="f9092-109">此 Cmdlet 會使用 `Stop-Trace` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f9092-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="f9092-110">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f9092-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="f9092-111">範例</span><span class="sxs-lookup"><span data-stu-id="f9092-111">EXAMPLES</span></span>

### <span data-ttu-id="f9092-112">範例1：停止 WSMan 追蹤</span><span class="sxs-lookup"><span data-stu-id="f9092-112">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="f9092-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f9092-113">PARAMETERS</span></span>

### <span data-ttu-id="f9092-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f9092-114">CommonParameters</span></span>

<span data-ttu-id="f9092-115">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f9092-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f9092-116">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f9092-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f9092-117">輸入</span><span class="sxs-lookup"><span data-stu-id="f9092-117">INPUTS</span></span>

### <span data-ttu-id="f9092-118">無</span><span class="sxs-lookup"><span data-stu-id="f9092-118">None</span></span>

## <span data-ttu-id="f9092-119">輸出</span><span class="sxs-lookup"><span data-stu-id="f9092-119">OUTPUTS</span></span>

### <span data-ttu-id="f9092-120">無</span><span class="sxs-lookup"><span data-stu-id="f9092-120">None</span></span>

## <span data-ttu-id="f9092-121">注意</span><span class="sxs-lookup"><span data-stu-id="f9092-121">NOTES</span></span>

## <span data-ttu-id="f9092-122">相關連結</span><span class="sxs-lookup"><span data-stu-id="f9092-122">RELATED LINKS</span></span>

[<span data-ttu-id="f9092-123">事件追蹤</span><span class="sxs-lookup"><span data-stu-id="f9092-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="f9092-124">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="f9092-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="f9092-125">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="f9092-125">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

