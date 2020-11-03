---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: 08c9d61f210761e2ed7a3a5014812b2bd362201b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203055"
---
# <span data-ttu-id="b917d-103">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="b917d-103">Enable-WSManTrace</span></span>

## <span data-ttu-id="b917d-104">概要</span><span class="sxs-lookup"><span data-stu-id="b917d-104">SYNOPSIS</span></span>
<span data-ttu-id="b917d-105">啟動已啟用 WSMan 提供者的記錄會話。</span><span class="sxs-lookup"><span data-stu-id="b917d-105">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="b917d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b917d-106">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="b917d-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b917d-107">DESCRIPTION</span></span>
<span data-ttu-id="b917d-108">此 Cmdlet 會啟動已啟用 WSMan 提供者的記錄會話。</span><span class="sxs-lookup"><span data-stu-id="b917d-108">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="b917d-109">下列事件提供者已啟用：</span><span class="sxs-lookup"><span data-stu-id="b917d-109">The following event providers are enabled:</span></span>

- <span data-ttu-id="b917d-110">事件轉送</span><span class="sxs-lookup"><span data-stu-id="b917d-110">Event Forwarding</span></span>
- <span data-ttu-id="b917d-111">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="b917d-111">IpmiDrv</span></span>
- <span data-ttu-id="b917d-112">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="b917d-112">IPMIPrv</span></span>
- <span data-ttu-id="b917d-113">WinRM</span><span class="sxs-lookup"><span data-stu-id="b917d-113">WinRM</span></span>
- <span data-ttu-id="b917d-114">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="b917d-114">WinrsCmd</span></span>
- <span data-ttu-id="b917d-115">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="b917d-115">WinrsExe</span></span>
- <span data-ttu-id="b917d-116">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="b917d-116">WinrsMgr</span></span>
- <span data-ttu-id="b917d-117">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="b917d-117">WSManProvHost</span></span>

<span data-ttu-id="b917d-118">會話的名稱為 ' wsmlog '。</span><span class="sxs-lookup"><span data-stu-id="b917d-118">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="b917d-119">此 Cmdlet 會使用 `Start-Trace` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b917d-119">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="b917d-120">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b917d-120">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="b917d-121">範例</span><span class="sxs-lookup"><span data-stu-id="b917d-121">EXAMPLES</span></span>

### <span data-ttu-id="b917d-122">範例1：啟動 WSMan 記錄會話。</span><span class="sxs-lookup"><span data-stu-id="b917d-122">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="b917d-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b917d-123">PARAMETERS</span></span>

### <span data-ttu-id="b917d-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b917d-124">CommonParameters</span></span>

<span data-ttu-id="b917d-125">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b917d-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b917d-126">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b917d-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b917d-127">輸入</span><span class="sxs-lookup"><span data-stu-id="b917d-127">INPUTS</span></span>

### <span data-ttu-id="b917d-128">無</span><span class="sxs-lookup"><span data-stu-id="b917d-128">None</span></span>

## <span data-ttu-id="b917d-129">輸出</span><span class="sxs-lookup"><span data-stu-id="b917d-129">OUTPUTS</span></span>

### <span data-ttu-id="b917d-130">System.Object</span><span class="sxs-lookup"><span data-stu-id="b917d-130">System.Object</span></span>

## <span data-ttu-id="b917d-131">注意</span><span class="sxs-lookup"><span data-stu-id="b917d-131">NOTES</span></span>

## <span data-ttu-id="b917d-132">相關連結</span><span class="sxs-lookup"><span data-stu-id="b917d-132">RELATED LINKS</span></span>

[<span data-ttu-id="b917d-133">事件追蹤</span><span class="sxs-lookup"><span data-stu-id="b917d-133">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="b917d-134">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="b917d-134">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="b917d-135">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="b917d-135">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)
