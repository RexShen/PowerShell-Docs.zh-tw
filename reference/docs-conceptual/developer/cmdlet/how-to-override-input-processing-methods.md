---
title: 如何覆寫輸入處理方法 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b245dc56b78ce9b7f1dea80b5d4988057c2f125f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784107"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="823fd-102">如何覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="823fd-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="823fd-103">這些範例示範如何覆寫 Cmdlet 內的輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="823fd-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="823fd-104">這些方法是用來執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="823fd-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="823fd-105">[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法是用來執行一次性啟動作業，這是對 Cmdlet 所處理的所有物件有效的。</span><span class="sxs-lookup"><span data-stu-id="823fd-105">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="823fd-106">Windows PowerShell 執行時間只會呼叫這個方法一次。</span><span class="sxs-lookup"><span data-stu-id="823fd-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="823fd-107">[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法是用來處理傳遞至指令程式的物件。</span><span class="sxs-lookup"><span data-stu-id="823fd-107">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="823fd-108">Windows PowerShell 執行時間會針對傳遞給 Cmdlet 的每個物件，呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="823fd-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="823fd-109">System.servicemodel[方法是](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)用來執行一次性的後置處理作業。</span><span class="sxs-lookup"><span data-stu-id="823fd-109">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="823fd-110">Windows PowerShell 執行時間只會呼叫這個方法一次。</span><span class="sxs-lookup"><span data-stu-id="823fd-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="823fd-111">覆寫 BeginProcessing 方法</span><span class="sxs-lookup"><span data-stu-id="823fd-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="823fd-112">宣告[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法的受保護覆寫。</span><span class="sxs-lookup"><span data-stu-id="823fd-112">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="823fd-113">下列類別會列印範例訊息。</span><span class="sxs-lookup"><span data-stu-id="823fd-113">The following class prints a sample message.</span></span> <span data-ttu-id="823fd-114">若要使用這個類別，請變更 Cmdlet 屬性中的動詞和名詞、變更類別的名稱以反映新的動詞和名詞，然後將您需要的功能新增至[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法的覆寫。</span><span class="sxs-lookup"><span data-stu-id="823fd-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

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

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="823fd-115">覆寫 ProcessRecord 方法</span><span class="sxs-lookup"><span data-stu-id="823fd-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="823fd-116">宣告[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的受保護覆寫。</span><span class="sxs-lookup"><span data-stu-id="823fd-116">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="823fd-117">下列類別會列印範例訊息。</span><span class="sxs-lookup"><span data-stu-id="823fd-117">The following class prints a sample message.</span></span> <span data-ttu-id="823fd-118">若要使用這個類別，請變更 Cmdlet 屬性中的動詞和名詞、變更類別的名稱以反映新的動詞和名詞，然後將您需要的功能新增至[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫。</span><span class="sxs-lookup"><span data-stu-id="823fd-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

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

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="823fd-119">若要覆寫 EndProcessing 方法</span><span class="sxs-lookup"><span data-stu-id="823fd-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="823fd-120">宣告[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法的受保護覆寫。</span><span class="sxs-lookup"><span data-stu-id="823fd-120">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="823fd-121">下列類別會列印範例。</span><span class="sxs-lookup"><span data-stu-id="823fd-121">The following class prints a sample.</span></span> <span data-ttu-id="823fd-122">若要使用這個類別，請變更 Cmdlet 屬性中的動詞和名詞、變更類別的名稱以反映新的動詞和名詞，然後將您需要的功能加入至[system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)的覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="823fd-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="823fd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="823fd-123">See Also</span></span>

[<span data-ttu-id="823fd-124">BeginProcessing 的管理元件</span><span class="sxs-lookup"><span data-stu-id="823fd-124">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="823fd-125">System.servicemodel. Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="823fd-125">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="823fd-126">ProcessRecord 的管理元件</span><span class="sxs-lookup"><span data-stu-id="823fd-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="823fd-127">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="823fd-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
