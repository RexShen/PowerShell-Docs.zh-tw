---
title: Cmdlet 輸入處理方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369867"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="89758-102">Cmdlet 輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="89758-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="89758-103">Cmdlet 必須覆寫本主題中所述的一或多個輸入處理方法，才能執行其工作。</span><span class="sxs-lookup"><span data-stu-id="89758-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="89758-104">這些方法可讓 Cmdlet 執行前置處理、輸入處理和後置處理的作業。</span><span class="sxs-lookup"><span data-stu-id="89758-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="89758-105">這些方法也可讓您停止 Cmdlet 處理。</span><span class="sxs-lookup"><span data-stu-id="89758-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="89758-106">如需如何使用這些方法的更詳細範例，請參閱[SelectStr 教學](selectstr-tutorial.md)課程。</span><span class="sxs-lookup"><span data-stu-id="89758-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="89758-107">前置處理作業</span><span class="sxs-lookup"><span data-stu-id="89758-107">Pre-Processing Operations</span></span>

<span data-ttu-id="89758-108">Cmdlet 應該覆寫[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法，以新增任何對稍後將由 Cmdlet 處理的所有記錄有效的前置處理作業。</span><span class="sxs-lookup"><span data-stu-id="89758-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="89758-109">當 PowerShell 處理命令管線時，PowerShell 會針對管線中的每個 Cmdlet 實例呼叫這個方法一次。</span><span class="sxs-lookup"><span data-stu-id="89758-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="89758-110">如需 PowerShell 如何叫用命令管線的詳細資訊，請參閱[Cmdlet 處理生命週期](/previous-versions/ms714429(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="89758-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="89758-111">下列程式碼顯示 BeginProcessing 方法的執行。</span><span class="sxs-lookup"><span data-stu-id="89758-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="89758-112">輸入處理作業</span><span class="sxs-lookup"><span data-stu-id="89758-112">Input Processing Operations</span></span>

<span data-ttu-id="89758-113">Cmdlet 可以覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，以處理傳送至指令程式的輸入。</span><span class="sxs-lookup"><span data-stu-id="89758-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="89758-114">當 PowerShell 處理命令管線時，PowerShell 會針對 Cmdlet 所處理的每個輸入記錄呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="89758-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="89758-115">如需 PowerShell 如何叫用命令管線的詳細資訊，請參閱[Cmdlet 處理生命週期](/previous-versions/ms714429(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="89758-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="89758-116">下列程式碼顯示 ProcessRecord 方法的執行。</span><span class="sxs-lookup"><span data-stu-id="89758-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="89758-117">後置處理作業</span><span class="sxs-lookup"><span data-stu-id="89758-117">Post-Processing Operations</span></span>

<span data-ttu-id="89758-118">Cmdlet 應該覆寫[system.servicemodel 方法，](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)以新增對 Cmdlet 所處理之所有記錄有效的任何後置處理作業。</span><span class="sxs-lookup"><span data-stu-id="89758-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="89758-119">例如，您的 Cmdlet 可能必須在處理完成後清除物件變數。</span><span class="sxs-lookup"><span data-stu-id="89758-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="89758-120">當 PowerShell 處理命令管線時，PowerShell 會針對管線中的每個 Cmdlet 實例呼叫這個方法一次。</span><span class="sxs-lookup"><span data-stu-id="89758-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="89758-121">不過，請務必記住，如果 Cmdlet 在其輸入處理過程中取消，或 Cmdlet 的任何部分發生終止錯誤，則 PowerShell 執行時間不會呼叫 EndProcessing 方法。</span><span class="sxs-lookup"><span data-stu-id="89758-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="89758-122">基於這個理由，需要物件清理的 Cmdlet 應該會執行完整的[IDisposable](/dotnet/api/System.IDisposable)模式，包括完成項，讓執行時間可以在結尾處呼叫 EndProcessing 和 IDisposable 方法[。](/dotnet/api/System.IDisposable.Dispose)流程.</span><span class="sxs-lookup"><span data-stu-id="89758-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="89758-123">如需 PowerShell 如何叫用命令管線的詳細資訊，請參閱[Cmdlet 處理生命週期](/previous-versions/ms714429(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="89758-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="89758-124">下列程式碼顯示 EndProcessing 方法的執行。</span><span class="sxs-lookup"><span data-stu-id="89758-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="89758-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89758-125">See Also</span></span>

[<span data-ttu-id="89758-126">BeginProcessing 的管理元件</span><span class="sxs-lookup"><span data-stu-id="89758-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="89758-127">ProcessRecord 的管理元件</span><span class="sxs-lookup"><span data-stu-id="89758-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="89758-128">System.servicemodel. Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="89758-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="89758-129">SelectStr 教學課程</span><span class="sxs-lookup"><span data-stu-id="89758-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="89758-130">IDisposable</span><span class="sxs-lookup"><span data-stu-id="89758-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="89758-131">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="89758-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)