---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: 024fa690ff9ddd4eae2d7fd6203e83f56fef6cd7
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201660"
---
# <span data-ttu-id="1aaed-103">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="1aaed-103">Get-TraceSource</span></span>

## <span data-ttu-id="1aaed-104">概要</span><span class="sxs-lookup"><span data-stu-id="1aaed-104">SYNOPSIS</span></span>
<span data-ttu-id="1aaed-105">取得已檢測進行追蹤的 PowerShell 元件。</span><span class="sxs-lookup"><span data-stu-id="1aaed-105">Gets PowerShell components that are instrumented for tracing.</span></span>

## <span data-ttu-id="1aaed-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1aaed-106">SYNTAX</span></span>

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="1aaed-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1aaed-107">DESCRIPTION</span></span>

<span data-ttu-id="1aaed-108">**TraceSource** 指令程式會取得目前使用中之 PowerShell 元件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="1aaed-108">The **Get-TraceSource** cmdlet gets the trace sources for PowerShell components that are currently in use.</span></span>
<span data-ttu-id="1aaed-109">您可以使用資料來判斷您可以追蹤的 PowerShell 元件。</span><span class="sxs-lookup"><span data-stu-id="1aaed-109">You can use the data to determine which PowerShell components you can trace.</span></span>
<span data-ttu-id="1aaed-110">當進行追蹤時，元件會產生有關內部處理中每個步驟的詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="1aaed-110">When tracing, the component generates detailed messages about each step in its internal processing.</span></span>
<span data-ttu-id="1aaed-111">開發人員使用追蹤資料來監視資料流量、程式執行和錯誤。</span><span class="sxs-lookup"><span data-stu-id="1aaed-111">Developers use the trace data to monitor data flow, program execution, and errors.</span></span>

<span data-ttu-id="1aaed-112">追蹤 Cmdlet 是專為 PowerShell 開發人員所設計，但它們可供所有使用者使用。</span><span class="sxs-lookup"><span data-stu-id="1aaed-112">The tracing cmdlets were designed for PowerShell developers, but they are available to all users.</span></span>

## <span data-ttu-id="1aaed-113">範例</span><span class="sxs-lookup"><span data-stu-id="1aaed-113">EXAMPLES</span></span>

### <span data-ttu-id="1aaed-114">範例 1︰依名稱取得追蹤來源</span><span class="sxs-lookup"><span data-stu-id="1aaed-114">Example 1: Get trace sources by name</span></span>

```
PS C:\> Get-TraceSource -Name "*provider*"
```

<span data-ttu-id="1aaed-115">此命令會取得所有名稱包含 provider 的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="1aaed-115">This command gets all of the trace sources that have names that include provider.</span></span>

### <span data-ttu-id="1aaed-116">範例 2︰取得所有的追蹤來源</span><span class="sxs-lookup"><span data-stu-id="1aaed-116">Example 2: Get all trace sources</span></span>

```
PS C:\> Get-TraceSource
```

<span data-ttu-id="1aaed-117">此命令會取得所有可追蹤的 PowerShell 元件。</span><span class="sxs-lookup"><span data-stu-id="1aaed-117">This command gets all of the PowerShell components that can be traced.</span></span>

## <span data-ttu-id="1aaed-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1aaed-118">PARAMETERS</span></span>

### <span data-ttu-id="1aaed-119">-Name</span><span class="sxs-lookup"><span data-stu-id="1aaed-119">-Name</span></span>

<span data-ttu-id="1aaed-120">指定要取得的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="1aaed-120">Specifies the trace sources to get.</span></span>
<span data-ttu-id="1aaed-121">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="1aaed-121">Wildcards are permitted.</span></span>
<span data-ttu-id="1aaed-122">參數名稱 *名稱* 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="1aaed-122">The parameter name *Name* is optional.</span></span>

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

### <span data-ttu-id="1aaed-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1aaed-123">CommonParameters</span></span>

<span data-ttu-id="1aaed-124">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1aaed-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1aaed-125">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1aaed-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1aaed-126">輸入</span><span class="sxs-lookup"><span data-stu-id="1aaed-126">INPUTS</span></span>

### <span data-ttu-id="1aaed-127">System.String</span><span class="sxs-lookup"><span data-stu-id="1aaed-127">System.String</span></span>

<span data-ttu-id="1aaed-128">您可以使用管線將包含追蹤來源名稱的字串傳送至 **TraceSource** 。</span><span class="sxs-lookup"><span data-stu-id="1aaed-128">You can pipe a string that contains the name of a trace source to **Get-TraceSource** .</span></span>

## <span data-ttu-id="1aaed-129">輸出</span><span class="sxs-lookup"><span data-stu-id="1aaed-129">OUTPUTS</span></span>

### <span data-ttu-id="1aaed-130">System.Management.Automation.PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="1aaed-130">System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="1aaed-131">**TraceSource** 會傳回代表追蹤來源的物件。</span><span class="sxs-lookup"><span data-stu-id="1aaed-131">**Get-TraceSource** returns objects that represent the trace sources.</span></span>

## <span data-ttu-id="1aaed-132">注意</span><span class="sxs-lookup"><span data-stu-id="1aaed-132">NOTES</span></span>

## <span data-ttu-id="1aaed-133">相關連結</span><span class="sxs-lookup"><span data-stu-id="1aaed-133">RELATED LINKS</span></span>

[<span data-ttu-id="1aaed-134">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="1aaed-134">Set-TraceSource</span></span>](Set-TraceSource.md)

[<span data-ttu-id="1aaed-135">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="1aaed-135">Trace-Command</span></span>](Trace-Command.md)
