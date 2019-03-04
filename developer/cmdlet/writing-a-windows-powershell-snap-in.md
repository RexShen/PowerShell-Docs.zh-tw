---
title: Windows PowerShell 嵌入式管理單元撰寫 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: ee8a6538fa6ad4d0f480f2dac46fe0f823a38be8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853764"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="a3f87-102">撰寫 Windows PowerShell 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="a3f87-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="a3f87-103">此範例示範如何撰寫 Windows PowerShell 嵌入式管理單元，可用來註冊組件中的所有 cmdlet 和 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="a3f87-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="a3f87-104">使用此類型的嵌入式管理單元，您沒有選取的 cmdlet 與您想要註冊的提供者。</span><span class="sxs-lookup"><span data-stu-id="a3f87-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="a3f87-105">若要撰寫一個嵌入式管理單元，可讓您選取 註冊的項目，請參閱[撰寫自訂 Windows PowerShell 嵌入式管理單元](./writing-a-custom-windows-powershell-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="a3f87-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="a3f87-106">撰寫 Windows PowerShell 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="a3f87-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="a3f87-107">新增 RunInstallerAttribute 屬性。</span><span class="sxs-lookup"><span data-stu-id="a3f87-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="a3f87-108">建立公用類別衍生自[System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn)類別。</span><span class="sxs-lookup"><span data-stu-id="a3f87-108">Create a public class that derives from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="a3f87-109">在此範例中，類別名稱會是"GetProcPSSnapIn01 」。</span><span class="sxs-lookup"><span data-stu-id="a3f87-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="a3f87-110">新增公用屬性 （必要） 嵌入式管理單元的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3f87-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="a3f87-111">在命名嵌入式管理單元時，請勿使用任何下列字元: #。</span><span class="sxs-lookup"><span data-stu-id="a3f87-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="a3f87-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span><span class="sxs-lookup"><span data-stu-id="a3f87-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="a3f87-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="a3f87-113">@ \` \*</span></span>

    <span data-ttu-id="a3f87-114">在此範例中，嵌入式管理單元的名稱會是"GetProcPSSnapIn01 」。</span><span class="sxs-lookup"><span data-stu-id="a3f87-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="a3f87-115">新增嵌入式管理單元 （必要） 廠商的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="a3f87-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="a3f87-116">在此範例中，廠商會是 「 Microsoft 」。</span><span class="sxs-lookup"><span data-stu-id="a3f87-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="a3f87-117">新增嵌入式管理單元 （選擇性） 廠商資源的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="a3f87-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="a3f87-118">在此範例中，廠商資源為 「 GetProcPSSnapIn01，Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="a3f87-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="a3f87-119">新增公用屬性 （必要） 嵌入式管理單元的描述。</span><span class="sxs-lookup"><span data-stu-id="a3f87-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="a3f87-120">在此範例中，描述會是 「 這是一個 Windows PowerShell 嵌入式管理單元，註冊 get-proc cmdlet 」。</span><span class="sxs-lookup"><span data-stu-id="a3f87-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="a3f87-121">新增嵌入式管理單元 （選擇性） 說明資源的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="a3f87-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="a3f87-122">在此範例中，廠商資源是 「 GetProcPSSnapIn01，這是一個 Windows PowerShell 嵌入式管理單元，註冊 get-proc cmdlet 」。</span><span class="sxs-lookup"><span data-stu-id="a3f87-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="a3f87-123">範例</span><span class="sxs-lookup"><span data-stu-id="a3f87-123">Example</span></span>

<span data-ttu-id="a3f87-124">此範例示範如何撰寫 Windows PowerShell 嵌入式管理單元，可用來註冊 Get-proc cmdlet 在 Windows PowerShell 介面中。</span><span class="sxs-lookup"><span data-stu-id="a3f87-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="a3f87-125">請注意，在此範例中，完整的組件會包含只有 GetProcPSSnapIn01 嵌入式管理單元類別和 Get-proc cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="a3f87-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="a3f87-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3f87-126">See Also</span></span>

[<span data-ttu-id="a3f87-127">如何註冊 Cmdlet、 提供者，以及裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="a3f87-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="a3f87-128">如何註冊 Cmdlet、 提供者，以及裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="a3f87-128">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="a3f87-129">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="a3f87-129">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
