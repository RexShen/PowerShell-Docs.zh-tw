---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/stop-trace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Trace
ms.openlocfilehash: 48027fe707660f7844c28bf5f8916b0f51e0d4d1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203743"
---
# <span data-ttu-id="90f98-103">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="90f98-103">Stop-Trace</span></span>

## <span data-ttu-id="90f98-104">概要</span><span class="sxs-lookup"><span data-stu-id="90f98-104">SYNOPSIS</span></span>
<span data-ttu-id="90f98-105">停止事件追蹤記錄會話。</span><span class="sxs-lookup"><span data-stu-id="90f98-105">Stop an Event Trace logging session.</span></span>

## <span data-ttu-id="90f98-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="90f98-106">SYNTAX</span></span>

```
Stop-Trace [-SessionName] <Object> [-ETS] [<CommonParameters>]
```

## <span data-ttu-id="90f98-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="90f98-107">DESCRIPTION</span></span>

<span data-ttu-id="90f98-108">此 Cmdlet 會停止 Windows 事件追蹤記錄會話。</span><span class="sxs-lookup"><span data-stu-id="90f98-108">This cmdlet stops a Windows Event Trace logging session.</span></span>

<span data-ttu-id="90f98-109">下列 Cmdlet 會使用此 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="90f98-109">This cmdlet is used by the following cmdlets:</span></span>

- `Disable-PSWSManCombinedTrace`
- `Disable-WSManTrace`

<span data-ttu-id="90f98-110">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90f98-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="90f98-111">範例</span><span class="sxs-lookup"><span data-stu-id="90f98-111">EXAMPLES</span></span>

### <span data-ttu-id="90f98-112">範例1：停止 WSMan 追蹤記錄會話</span><span class="sxs-lookup"><span data-stu-id="90f98-112">Example 1: Stop a WSMan Trace logging session</span></span>

```powershell
Stop-Trace -SessionName 'wsmlog'
```

## <span data-ttu-id="90f98-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="90f98-113">PARAMETERS</span></span>

### <span data-ttu-id="90f98-114">-ETS</span><span class="sxs-lookup"><span data-stu-id="90f98-114">-ETS</span></span>
<span data-ttu-id="90f98-115">直接將命令傳送至事件追蹤會話，而不儲存或排程。</span><span class="sxs-lookup"><span data-stu-id="90f98-115">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="90f98-116">-SessionName</span><span class="sxs-lookup"><span data-stu-id="90f98-116">-SessionName</span></span>
<span data-ttu-id="90f98-117">要停止之事件追蹤會話的名稱。</span><span class="sxs-lookup"><span data-stu-id="90f98-117">The name of the Event Trace session to be stopped.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="90f98-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="90f98-118">CommonParameters</span></span>
<span data-ttu-id="90f98-119">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="90f98-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="90f98-120">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="90f98-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="90f98-121">輸入</span><span class="sxs-lookup"><span data-stu-id="90f98-121">INPUTS</span></span>

### <span data-ttu-id="90f98-122">無</span><span class="sxs-lookup"><span data-stu-id="90f98-122">None</span></span>

## <span data-ttu-id="90f98-123">輸出</span><span class="sxs-lookup"><span data-stu-id="90f98-123">OUTPUTS</span></span>

### <span data-ttu-id="90f98-124">無</span><span class="sxs-lookup"><span data-stu-id="90f98-124">None</span></span>

## <span data-ttu-id="90f98-125">注意</span><span class="sxs-lookup"><span data-stu-id="90f98-125">NOTES</span></span>

## <span data-ttu-id="90f98-126">相關連結</span><span class="sxs-lookup"><span data-stu-id="90f98-126">RELATED LINKS</span></span>

[<span data-ttu-id="90f98-127">事件追蹤</span><span class="sxs-lookup"><span data-stu-id="90f98-127">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="90f98-128">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="90f98-128">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="90f98-129">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="90f98-129">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="90f98-130">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="90f98-130">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="90f98-131">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="90f98-131">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="90f98-132">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="90f98-132">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
