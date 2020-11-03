---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: 7d57e7cff0dc3ca0eff36dbe38e240efdd324060
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203252"
---
# <span data-ttu-id="a3a4c-103">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="a3a4c-103">Get-TraceSource</span></span>

## <span data-ttu-id="a3a4c-104">概要</span><span class="sxs-lookup"><span data-stu-id="a3a4c-104">SYNOPSIS</span></span>
<span data-ttu-id="a3a4c-105">取得已檢測進行追蹤的 PowerShell 元件。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-105">Gets PowerShell components that are instrumented for tracing.</span></span>

## <span data-ttu-id="a3a4c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a3a4c-106">SYNTAX</span></span>

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="a3a4c-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a3a4c-107">DESCRIPTION</span></span>

<span data-ttu-id="a3a4c-108">**TraceSource** 指令程式會取得目前使用中之 PowerShell 元件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-108">The **Get-TraceSource** cmdlet gets the trace sources for PowerShell components that are currently in use.</span></span>
<span data-ttu-id="a3a4c-109">您可以使用資料來判斷您可以追蹤的 PowerShell 元件。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-109">You can use the data to determine which PowerShell components you can trace.</span></span>
<span data-ttu-id="a3a4c-110">當進行追蹤時，元件會產生有關內部處理中每個步驟的詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-110">When tracing, the component generates detailed messages about each step in its internal processing.</span></span>
<span data-ttu-id="a3a4c-111">開發人員使用追蹤資料來監視資料流量、程式執行和錯誤。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-111">Developers use the trace data to monitor data flow, program execution, and errors.</span></span>

<span data-ttu-id="a3a4c-112">追蹤 Cmdlet 是專為 PowerShell 開發人員所設計，但它們可供所有使用者使用。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-112">The tracing cmdlets were designed for PowerShell developers, but they are available to all users.</span></span>

## <span data-ttu-id="a3a4c-113">範例</span><span class="sxs-lookup"><span data-stu-id="a3a4c-113">EXAMPLES</span></span>

### <span data-ttu-id="a3a4c-114">範例 1︰依名稱取得追蹤來源</span><span class="sxs-lookup"><span data-stu-id="a3a4c-114">Example 1: Get trace sources by name</span></span>

```
PS C:\> Get-TraceSource -Name "*provider*"
```

<span data-ttu-id="a3a4c-115">此命令會取得所有名稱包含 provider 的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-115">This command gets all of the trace sources that have names that include provider.</span></span>

### <span data-ttu-id="a3a4c-116">範例 2︰取得所有的追蹤來源</span><span class="sxs-lookup"><span data-stu-id="a3a4c-116">Example 2: Get all trace sources</span></span>

```
PS C:\> Get-TraceSource
```

<span data-ttu-id="a3a4c-117">此命令會取得所有可追蹤的 PowerShell 元件。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-117">This command gets all of the PowerShell components that can be traced.</span></span>

## <span data-ttu-id="a3a4c-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a3a4c-118">PARAMETERS</span></span>

### <span data-ttu-id="a3a4c-119">-Name</span><span class="sxs-lookup"><span data-stu-id="a3a4c-119">-Name</span></span>

<span data-ttu-id="a3a4c-120">指定要取得的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-120">Specifies the trace sources to get.</span></span>
<span data-ttu-id="a3a4c-121">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-121">Wildcards are permitted.</span></span>
<span data-ttu-id="a3a4c-122">參數名稱 *名稱* 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-122">The parameter name *Name* is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="a3a4c-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a3a4c-123">CommonParameters</span></span>

<span data-ttu-id="a3a4c-124">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a3a4c-125">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a3a4c-126">輸入</span><span class="sxs-lookup"><span data-stu-id="a3a4c-126">INPUTS</span></span>

### <span data-ttu-id="a3a4c-127">System.String</span><span class="sxs-lookup"><span data-stu-id="a3a4c-127">System.String</span></span>

<span data-ttu-id="a3a4c-128">您可以使用管線將包含追蹤來源名稱的字串傳送至 **TraceSource** 。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-128">You can pipe a string that contains the name of a trace source to **Get-TraceSource** .</span></span>

## <span data-ttu-id="a3a4c-129">輸出</span><span class="sxs-lookup"><span data-stu-id="a3a4c-129">OUTPUTS</span></span>

### <span data-ttu-id="a3a4c-130">System.Management.Automation.PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="a3a4c-130">System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="a3a4c-131">**TraceSource** 會傳回代表追蹤來源的物件。</span><span class="sxs-lookup"><span data-stu-id="a3a4c-131">**Get-TraceSource** returns objects that represent the trace sources.</span></span>

## <span data-ttu-id="a3a4c-132">注意</span><span class="sxs-lookup"><span data-stu-id="a3a4c-132">NOTES</span></span>

## <span data-ttu-id="a3a4c-133">相關連結</span><span class="sxs-lookup"><span data-stu-id="a3a4c-133">RELATED LINKS</span></span>

[<span data-ttu-id="a3a4c-134">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="a3a4c-134">Set-TraceSource</span></span>](Set-TraceSource.md)

[<span data-ttu-id="a3a4c-135">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="a3a4c-135">Trace-Command</span></span>](Trace-Command.md)
