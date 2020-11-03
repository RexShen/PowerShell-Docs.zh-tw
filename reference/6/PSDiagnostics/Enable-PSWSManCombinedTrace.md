---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: cfe73dea98cdf858f1364e1daf434334b57a62cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204828"
---
# <span data-ttu-id="469c3-103">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="469c3-103">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="469c3-104">概要</span><span class="sxs-lookup"><span data-stu-id="469c3-104">SYNOPSIS</span></span>
<span data-ttu-id="469c3-105">啟動已啟用 WSMan 和 PowerShell 提供者的記錄會話。</span><span class="sxs-lookup"><span data-stu-id="469c3-105">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="469c3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="469c3-106">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="469c3-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="469c3-107">DESCRIPTION</span></span>

<span data-ttu-id="469c3-108">此 Cmdlet 會啟動已啟用下列 PowerShell 提供者的記錄會話：</span><span class="sxs-lookup"><span data-stu-id="469c3-108">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="469c3-109">Microsoft-Windows-PowerShell</span><span class="sxs-lookup"><span data-stu-id="469c3-109">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="469c3-110">Microsoft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="469c3-110">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="469c3-111">會話的名稱為 ' PSTrace '。</span><span class="sxs-lookup"><span data-stu-id="469c3-111">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="469c3-112">此 Cmdlet 會使用 `Start-Trace` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="469c3-112">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="469c3-113">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="469c3-113">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="469c3-114">範例</span><span class="sxs-lookup"><span data-stu-id="469c3-114">EXAMPLES</span></span>

### <span data-ttu-id="469c3-115">範例1：啟動合併的記錄會話</span><span class="sxs-lookup"><span data-stu-id="469c3-115">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="469c3-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="469c3-116">PARAMETERS</span></span>

### <span data-ttu-id="469c3-117">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="469c3-117">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="469c3-118">根據預設，事件會寫入 "$pshome \Traces\PSTrace.etl"。</span><span class="sxs-lookup"><span data-stu-id="469c3-118">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="469c3-119">使用此參數時，Cmdlet 會建立唯一的檔案名： "$pshome \Traces\ PSTrace_ {guid}. etl"</span><span class="sxs-lookup"><span data-stu-id="469c3-119">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

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

### <span data-ttu-id="469c3-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="469c3-120">CommonParameters</span></span>

<span data-ttu-id="469c3-121">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="469c3-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="469c3-122">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="469c3-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="469c3-123">輸入</span><span class="sxs-lookup"><span data-stu-id="469c3-123">INPUTS</span></span>

### <span data-ttu-id="469c3-124">無</span><span class="sxs-lookup"><span data-stu-id="469c3-124">None</span></span>

## <span data-ttu-id="469c3-125">輸出</span><span class="sxs-lookup"><span data-stu-id="469c3-125">OUTPUTS</span></span>

### <span data-ttu-id="469c3-126">無</span><span class="sxs-lookup"><span data-stu-id="469c3-126">None</span></span>

## <span data-ttu-id="469c3-127">注意</span><span class="sxs-lookup"><span data-stu-id="469c3-127">NOTES</span></span>

## <span data-ttu-id="469c3-128">相關連結</span><span class="sxs-lookup"><span data-stu-id="469c3-128">RELATED LINKS</span></span>

[<span data-ttu-id="469c3-129">事件追蹤</span><span class="sxs-lookup"><span data-stu-id="469c3-129">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="469c3-130">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="469c3-130">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="469c3-131">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="469c3-131">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)
