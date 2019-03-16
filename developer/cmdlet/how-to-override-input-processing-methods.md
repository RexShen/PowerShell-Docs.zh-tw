---
title: 如何覆寫輸入處理方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056391"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="8a046-102">如何覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="8a046-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="8a046-103">這些範例示範如何覆寫的輸入處理方法中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8a046-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="8a046-104">這些方法用來執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="8a046-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="8a046-105">[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法用來執行一次啟動作業適用於 cmdlet 所處理的所有物件。</span><span class="sxs-lookup"><span data-stu-id="8a046-105">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="8a046-106">Windows PowerShell 執行階段會呼叫這個方法一次。</span><span class="sxs-lookup"><span data-stu-id="8a046-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="8a046-107">[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法用來處理物件傳遞至 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8a046-107">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="8a046-108">Windows PowerShell 執行階段會呼叫這個方法，每個物件傳遞至 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8a046-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="8a046-109">[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法用來執行單次 post 的處理作業。</span><span class="sxs-lookup"><span data-stu-id="8a046-109">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="8a046-110">Windows PowerShell 執行階段會呼叫這個方法一次。</span><span class="sxs-lookup"><span data-stu-id="8a046-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="8a046-111">若要覆寫 BeginProcessing 方法</span><span class="sxs-lookup"><span data-stu-id="8a046-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="8a046-112">宣告的受保護的覆寫[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="8a046-112">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="8a046-113">下列類別會列印範例訊息。</span><span class="sxs-lookup"><span data-stu-id="8a046-113">The following class prints a sample message.</span></span> <span data-ttu-id="8a046-114">若要使用這個類別，變更的指令動詞和名詞 Cmdlet 屬性中的，變更以反映新的動詞和名詞，類別名稱，然後新增所需的功能來覆寫[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="8a046-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="8a046-115">若要覆寫 ProcessRecord 方法</span><span class="sxs-lookup"><span data-stu-id="8a046-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="8a046-116">宣告的受保護的覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="8a046-116">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="8a046-117">下列類別會列印範例訊息。</span><span class="sxs-lookup"><span data-stu-id="8a046-117">The following class prints a sample message.</span></span> <span data-ttu-id="8a046-118">若要使用這個類別，變更的指令動詞和名詞 Cmdlet 屬性中的，變更以反映新的動詞和名詞，類別名稱，然後新增所需的功能來覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="8a046-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="8a046-119">若要覆寫 EndProcessing 方法</span><span class="sxs-lookup"><span data-stu-id="8a046-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="8a046-120">宣告的受保護的覆寫[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="8a046-120">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="8a046-121">下列類別會列印範例。</span><span class="sxs-lookup"><span data-stu-id="8a046-121">The following class prints a sample.</span></span> <span data-ttu-id="8a046-122">若要使用這個類別，變更的指令動詞和名詞 Cmdlet 屬性中的，變更以反映新的動詞和名詞，類別名稱，然後新增所需的功能來覆寫[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="8a046-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a><span data-ttu-id="8a046-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a046-123">See Also</span></span>

[<span data-ttu-id="8a046-124">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="8a046-124">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="8a046-125">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="8a046-125">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="8a046-126">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="8a046-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="8a046-127">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8a046-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
