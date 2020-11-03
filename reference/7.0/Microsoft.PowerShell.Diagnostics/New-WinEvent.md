---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 8e64c3e3a782fadf1669f1310d1615f3a014ccee
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201288"
---
# <span data-ttu-id="6cc2a-103">New-WinEvent</span><span class="sxs-lookup"><span data-stu-id="6cc2a-103">New-WinEvent</span></span>

## <span data-ttu-id="6cc2a-104">概要</span><span class="sxs-lookup"><span data-stu-id="6cc2a-104">SYNOPSIS</span></span>
<span data-ttu-id="6cc2a-105">為指定的事件提供者建立新的 Windows 事件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-105">Creates a new Windows event for the specified event provider.</span></span>

## <span data-ttu-id="6cc2a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6cc2a-106">SYNTAX</span></span>

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="6cc2a-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6cc2a-107">DESCRIPTION</span></span>

<span data-ttu-id="6cc2a-108">**New-WinEvent** Cmdlet 會為事件提供者建立 Windows 事件追蹤 (ETW) 事件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-108">The **New-WinEvent** cmdlet creates an Event Tracing for Windows (ETW) event for an event provider.</span></span>
<span data-ttu-id="6cc2a-109">您可以使用這個 Cmdlet，從 PowerShell 將事件新增到 ETW 通道。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-109">You can use this cmdlet to add events to ETW channels from PowerShell.</span></span>

## <span data-ttu-id="6cc2a-110">範例</span><span class="sxs-lookup"><span data-stu-id="6cc2a-110">EXAMPLES</span></span>

### <span data-ttu-id="6cc2a-111">範例 1</span><span class="sxs-lookup"><span data-stu-id="6cc2a-111">Example 1</span></span>

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

<span data-ttu-id="6cc2a-112">這個命令會使用 **New-WinEvent** Cmdlet，針對 Microsoft-Windows-PowerShell 提供者建立事件 45090。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-112">This command uses the **New-WinEvent** cmdlet to create event 45090 for the Microsoft-Windows-PowerShell provider.</span></span>

## <span data-ttu-id="6cc2a-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6cc2a-113">PARAMETERS</span></span>

### <span data-ttu-id="6cc2a-114">-Id</span><span class="sxs-lookup"><span data-stu-id="6cc2a-114">-Id</span></span>

<span data-ttu-id="6cc2a-115">指定透過工具資訊清單登錄的事件識別碼。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-115">Specifies an event id that was registered through an instrumentation manifest.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6cc2a-116">-Payload</span><span class="sxs-lookup"><span data-stu-id="6cc2a-116">-Payload</span></span>

<span data-ttu-id="6cc2a-117">指定事件的訊息。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-117">Specifies the message for the event.</span></span> <span data-ttu-id="6cc2a-118">將事件寫入事件記錄檔時，承載會儲存於事件物件的 **Message** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-118">When the event is written to an event log, the payload is stored in the **Message** property of the event object.</span></span>

<span data-ttu-id="6cc2a-119">當指定的承載不符合事件定義中的承載時，PowerShell 會產生警告，但命令仍會成功。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-119">When the specified payload does not match the payload in the event definition, PowerShell generates a warning, but the command still succeeds.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6cc2a-120">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="6cc2a-120">-ProviderName</span></span>

<span data-ttu-id="6cc2a-121">指定將事件寫入事件記錄檔的事件提供者，例如 "Microsoft-Windows-PowerShell"。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-121">Specifies the event provider that writes the event to an event log, such as "Microsoft-Windows-PowerShell".</span></span> <span data-ttu-id="6cc2a-122">ETW 事件提供者是將事件寫入 ETW 工作階段的邏輯實體。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-122">An ETW event provider is a logical entity that writes events to ETW sessions.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6cc2a-123">-Version</span><span class="sxs-lookup"><span data-stu-id="6cc2a-123">-Version</span></span>

<span data-ttu-id="6cc2a-124">指定事件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-124">Specifies the version number of the event.</span></span> <span data-ttu-id="6cc2a-125">輸入事件編號。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-125">Type the event number.</span></span> <span data-ttu-id="6cc2a-126">PowerShell 會將此數位轉換成所需的位元組類型。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-126">PowerShell converts the number to the required Byte type.</span></span>

<span data-ttu-id="6cc2a-127">這個參數可讓您在定義相同事件的不同版本時指定事件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-127">This parameter lets you specify an event when different versions of the same event are defined.</span></span>

```yaml
Type: System.Byte
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6cc2a-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6cc2a-128">CommonParameters</span></span>

<span data-ttu-id="6cc2a-129">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6cc2a-130">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6cc2a-131">輸入</span><span class="sxs-lookup"><span data-stu-id="6cc2a-131">INPUTS</span></span>

### <span data-ttu-id="6cc2a-132">無</span><span class="sxs-lookup"><span data-stu-id="6cc2a-132">None</span></span>

<span data-ttu-id="6cc2a-133">此 Cmdlet 不接受來自管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-133">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="6cc2a-134">輸出</span><span class="sxs-lookup"><span data-stu-id="6cc2a-134">OUTPUTS</span></span>

### <span data-ttu-id="6cc2a-135">無</span><span class="sxs-lookup"><span data-stu-id="6cc2a-135">None</span></span>

<span data-ttu-id="6cc2a-136">此 Cmdlet 會產生輸出。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-136">This cmdlet does to generate any output.</span></span>

## <span data-ttu-id="6cc2a-137">注意</span><span class="sxs-lookup"><span data-stu-id="6cc2a-137">NOTES</span></span>

* <span data-ttu-id="6cc2a-138">當提供者將事件寫入事件記錄檔之後，您可以使用 Get-WinEvent Cmdlet 從事件記錄檔取得事件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-138">After the provider writes the even to an eventlog, you can use the Get-WinEvent cmdlet to get the event from the event log.</span></span>

## <span data-ttu-id="6cc2a-139">相關連結</span><span class="sxs-lookup"><span data-stu-id="6cc2a-139">RELATED LINKS</span></span>

[<span data-ttu-id="6cc2a-140">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="6cc2a-140">Get-WinEvent</span></span>](Get-WinEvent.md)
