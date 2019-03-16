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
ms.openlocfilehash: 065214647dfa6d376b727930fe75140911095faf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059366"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="5ca1c-102">Cmdlet 輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="5ca1c-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="5ca1c-103">一或多個的輸入處理方法來執行其工作本主題中所述，必須覆寫 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span> <span data-ttu-id="5ca1c-104">這些方法可讓 cmdlet 來執行前置處理作業、 輸入處理作業和後置處理作業。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-104">These methods allow the cmdlet to perform pre-processing operations, input processing operations, and post-processing operations.</span></span> <span data-ttu-id="5ca1c-105">這些方法也可讓您停止指令程式處理。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-105">These methods also allow you to stop cmdlet processing.</span></span>

## <a name="pre-processing-tasks"></a><span data-ttu-id="5ca1c-106">前置處理工作</span><span class="sxs-lookup"><span data-stu-id="5ca1c-106">Pre-Processing Tasks</span></span>

<span data-ttu-id="5ca1c-107">指令程式應該覆寫[System.Management.Automation.Cmdlet.Beginprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法來加入有效的指令程式會稍後處理的所有記錄的任何前置處理作業。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-107">Cmdlets should override the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span> <span data-ttu-id="5ca1c-108">當 Windows PowerShell 處理命令管線時，Windows PowerShell 呼叫這個方法一次的管線中的指令程式的每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-108">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="5ca1c-109">如需有關 Windows PowerShell 如何叫用命令管道的詳細資訊，請參閱 < [Cmdlet 處理生命週期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-109">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="5ca1c-110">下列程式碼示範如何實作[System.Management.Automation.Cmdlet.Beginprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-110">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

<span data-ttu-id="5ca1c-111">如需更詳細的如何使用範例[System.Management.Automation.Cmdlet.Beginprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法，請參閱 < [SelectStr 教學課程](./selectstr-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-111">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span> <span data-ttu-id="5ca1c-112">在本教學課程中，**選取 Str** cmdlet 會使用[System.Management.Automation.Cmdlet.Beginprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法產生的規則運算式，用來搜尋的輸入處理的記錄。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-112">In this tutorial, the **Select-Str** cmdlet uses the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to generate the regular expression that is used to search the input processing records.</span></span>

## <a name="input-processing-tasks"></a><span data-ttu-id="5ca1c-113">輸入處理工作</span><span class="sxs-lookup"><span data-stu-id="5ca1c-113">Input Processing Tasks</span></span>

<span data-ttu-id="5ca1c-114">Cmdlet 可以覆寫[System.Management.Automation.Cmdlet.Processrecord%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法來處理傳送至 cmdlet 的輸入。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-114">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="5ca1c-115">當 Windows PowerShell 處理命令管線時，Windows PowerShell 就會呼叫這個方法的 cmdlet 所處理的每個輸入記錄。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-115">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="5ca1c-116">如需有關 Windows PowerShell 如何叫用命令管道的詳細資訊，請參閱 < [Cmdlet 處理生命週期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-116">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="5ca1c-117">下列程式碼示範如何實作[System.Management.Automation.Cmdlet.Processrecord%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-117">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

<span data-ttu-id="5ca1c-118">如需更詳細的如何使用範例[System.Management.Automation.Cmdlet.Processrecord%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法，請參閱 < [SelectStr 教學課程](./selectstr-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-118">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="post-processing-tasks"></a><span data-ttu-id="5ca1c-119">後置處理工作</span><span class="sxs-lookup"><span data-stu-id="5ca1c-119">Post-Processing Tasks</span></span>

<span data-ttu-id="5ca1c-120">指令程式應該覆寫[System.Management.Automation.Cmdlet.Endprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)方法來加入有效的 cmdlet 所處理的所有記錄的任何後置處理作業。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-120">Cmdlets should override the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span> <span data-ttu-id="5ca1c-121">例如，您的 cmdlet 可能要清除物件變數，在它完成之後處理。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-121">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="5ca1c-122">當 Windows PowerShell 處理命令管線時，Windows PowerShell 呼叫這個方法一次的管線中的指令程式的每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-122">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="5ca1c-123">不過，請務必記住，Windows PowerShell 執行階段不會呼叫[System.Management.Automation.Cmdlet.Endprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)如果 cmdlet 可透過其輸入的處理程序中途取消或終止錯誤發生在 cmdlet 的任何部分的方法。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-123">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="5ca1c-124">基於這個理由，需要物件清除 cmdlet 應該實作完整[System.IDisposable](/dotnet/api/System.IDisposable)模式，包括完成項，可讓執行階段呼叫兩者[System.Management.Automation.Cmdlet.Endprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)並[System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose)結尾的處理方法。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-124">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="5ca1c-125">如需有關 Windows PowerShell 如何叫用命令管道的詳細資訊，請參閱 < [Cmdlet 處理生命週期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-125">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="5ca1c-126">下列程式碼示範如何實作[System.Management.Automation.Cmdlet.Processrecord%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-126">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

<span data-ttu-id="5ca1c-127">如需更詳細的如何使用範例[System.Management.Automation.Cmdlet.Processrecord%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法，請參閱 < [SelectStr 教學課程](./selectstr-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="5ca1c-127">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ca1c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ca1c-128">See Also</span></span>

[<span data-ttu-id="5ca1c-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="5ca1c-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="5ca1c-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="5ca1c-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[<span data-ttu-id="5ca1c-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="5ca1c-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="5ca1c-132">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="5ca1c-132">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="5ca1c-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="5ca1c-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
