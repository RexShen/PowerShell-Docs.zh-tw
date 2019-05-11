---
title: Cmdlet 的輸入處理方法 |Microsoft Docs
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
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670315"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="5337c-102">Cmdlet 輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="5337c-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="5337c-103">一或多個的輸入處理方法來執行其工作本主題中所述，必須覆寫 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5337c-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="5337c-104">這些方法可讓 cmdlet 來執行前置處理、 輸入的處理和後處理作業。</span><span class="sxs-lookup"><span data-stu-id="5337c-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="5337c-105">這些方法也可讓您停止指令程式處理。</span><span class="sxs-lookup"><span data-stu-id="5337c-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="5337c-106">如何使用這些方法的詳細範例，請參閱[SelectStr 教學課程](selectstr-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="5337c-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="5337c-107">前置處理的作業</span><span class="sxs-lookup"><span data-stu-id="5337c-107">Pre-Processing Operations</span></span>

<span data-ttu-id="5337c-108">指令程式應該覆寫[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法來加入有效的指令程式會稍後處理的所有記錄的任何前置處理作業。</span><span class="sxs-lookup"><span data-stu-id="5337c-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="5337c-109">當 PowerShell 處理命令管線時，PowerShell 呼叫這個方法一次的管線中的指令程式的每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="5337c-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="5337c-110">如需有關如何 PowerShell 叫用命令管道的詳細資訊，請參閱[Cmdlet 處理生命週期](/previous-versions/ms714429(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="5337c-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="5337c-111">下列程式碼顯示 BeginProcessing 方法的實作。</span><span class="sxs-lookup"><span data-stu-id="5337c-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="5337c-112">處理作業的輸入</span><span class="sxs-lookup"><span data-stu-id="5337c-112">Input Processing Operations</span></span>

<span data-ttu-id="5337c-113">Cmdlet 可以覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法來處理傳送至 cmdlet 的輸入。</span><span class="sxs-lookup"><span data-stu-id="5337c-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="5337c-114">當 PowerShell 處理命令管線時，PowerShell 會呼叫這個方法的 cmdlet 所處理的每個輸入記錄。</span><span class="sxs-lookup"><span data-stu-id="5337c-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="5337c-115">如需有關如何 PowerShell 叫用命令管道的詳細資訊，請參閱[Cmdlet 處理生命週期](/previous-versions/ms714429(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="5337c-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="5337c-116">下列程式碼顯示 ProcessRecord 方法的實作。</span><span class="sxs-lookup"><span data-stu-id="5337c-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="5337c-117">後置處理作業</span><span class="sxs-lookup"><span data-stu-id="5337c-117">Post-Processing Operations</span></span>

<span data-ttu-id="5337c-118">指令程式應該覆寫[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法來加入有效的 cmdlet 所處理的所有記錄的任何後置處理作業。</span><span class="sxs-lookup"><span data-stu-id="5337c-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="5337c-119">例如，您的 cmdlet 可能要清除物件變數，在它完成之後處理。</span><span class="sxs-lookup"><span data-stu-id="5337c-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="5337c-120">當 PowerShell 處理命令管線時，PowerShell 呼叫這個方法一次的管線中的指令程式的每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="5337c-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="5337c-121">不過，務必記得 PowerShell 執行階段將無法呼叫 EndProcessing 方法如果 cmdlet 可透過其輸入的處理程序中途取消或終止錯誤，就會發生此指令程式的任何部分。</span><span class="sxs-lookup"><span data-stu-id="5337c-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="5337c-122">基於這個理由，需要物件清除 cmdlet 應該實作完整[System.IDisposable](/dotnet/api/System.IDisposable)模式，包括完成項，可讓執行階段呼叫這兩個 EndProcessing 和[System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose)結尾的處理方法。</span><span class="sxs-lookup"><span data-stu-id="5337c-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="5337c-123">如需有關如何 PowerShell 叫用命令管道的詳細資訊，請參閱[Cmdlet 處理生命週期](/previous-versions/ms714429(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="5337c-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="5337c-124">下列程式碼顯示 EndProcessing 方法的實作。</span><span class="sxs-lookup"><span data-stu-id="5337c-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="5337c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5337c-125">See Also</span></span>

[<span data-ttu-id="5337c-126">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="5337c-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="5337c-127">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="5337c-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="5337c-128">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="5337c-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="5337c-129">SelectStr 教學課程</span><span class="sxs-lookup"><span data-stu-id="5337c-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="5337c-130">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="5337c-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="5337c-131">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="5337c-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
