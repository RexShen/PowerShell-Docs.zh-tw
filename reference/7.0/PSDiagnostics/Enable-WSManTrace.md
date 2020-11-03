---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: c872b57186a854a67908bb07daac7f1a31bbb995
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200964"
---
# <span data-ttu-id="0ee73-103">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="0ee73-103">Enable-WSManTrace</span></span>

## <span data-ttu-id="0ee73-104">概要</span><span class="sxs-lookup"><span data-stu-id="0ee73-104">SYNOPSIS</span></span>
<span data-ttu-id="0ee73-105">啟動已啟用 WSMan 提供者的記錄會話。</span><span class="sxs-lookup"><span data-stu-id="0ee73-105">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="0ee73-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0ee73-106">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="0ee73-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0ee73-107">DESCRIPTION</span></span>
<span data-ttu-id="0ee73-108">此 Cmdlet 會啟動已啟用 WSMan 提供者的記錄會話。</span><span class="sxs-lookup"><span data-stu-id="0ee73-108">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="0ee73-109">下列事件提供者已啟用：</span><span class="sxs-lookup"><span data-stu-id="0ee73-109">The following event providers are enabled:</span></span>

- <span data-ttu-id="0ee73-110">事件轉送</span><span class="sxs-lookup"><span data-stu-id="0ee73-110">Event Forwarding</span></span>
- <span data-ttu-id="0ee73-111">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="0ee73-111">IpmiDrv</span></span>
- <span data-ttu-id="0ee73-112">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="0ee73-112">IPMIPrv</span></span>
- <span data-ttu-id="0ee73-113">WinRM</span><span class="sxs-lookup"><span data-stu-id="0ee73-113">WinRM</span></span>
- <span data-ttu-id="0ee73-114">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="0ee73-114">WinrsCmd</span></span>
- <span data-ttu-id="0ee73-115">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="0ee73-115">WinrsExe</span></span>
- <span data-ttu-id="0ee73-116">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="0ee73-116">WinrsMgr</span></span>
- <span data-ttu-id="0ee73-117">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="0ee73-117">WSManProvHost</span></span>

<span data-ttu-id="0ee73-118">會話的名稱為 ' wsmlog '。</span><span class="sxs-lookup"><span data-stu-id="0ee73-118">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="0ee73-119">此 Cmdlet 會使用 `Start-Trace` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0ee73-119">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="0ee73-120">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0ee73-120">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="0ee73-121">範例</span><span class="sxs-lookup"><span data-stu-id="0ee73-121">EXAMPLES</span></span>

### <span data-ttu-id="0ee73-122">範例1：啟動 WSMan 記錄會話。</span><span class="sxs-lookup"><span data-stu-id="0ee73-122">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="0ee73-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0ee73-123">PARAMETERS</span></span>

### <span data-ttu-id="0ee73-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0ee73-124">CommonParameters</span></span>

<span data-ttu-id="0ee73-125">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0ee73-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0ee73-126">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0ee73-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0ee73-127">輸入</span><span class="sxs-lookup"><span data-stu-id="0ee73-127">INPUTS</span></span>

### <span data-ttu-id="0ee73-128">無</span><span class="sxs-lookup"><span data-stu-id="0ee73-128">None</span></span>

## <span data-ttu-id="0ee73-129">輸出</span><span class="sxs-lookup"><span data-stu-id="0ee73-129">OUTPUTS</span></span>

### <span data-ttu-id="0ee73-130">無</span><span class="sxs-lookup"><span data-stu-id="0ee73-130">None</span></span>

## <span data-ttu-id="0ee73-131">注意</span><span class="sxs-lookup"><span data-stu-id="0ee73-131">NOTES</span></span>

## <span data-ttu-id="0ee73-132">相關連結</span><span class="sxs-lookup"><span data-stu-id="0ee73-132">RELATED LINKS</span></span>

[<span data-ttu-id="0ee73-133">事件追蹤</span><span class="sxs-lookup"><span data-stu-id="0ee73-133">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="0ee73-134">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="0ee73-134">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="0ee73-135">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="0ee73-135">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)
