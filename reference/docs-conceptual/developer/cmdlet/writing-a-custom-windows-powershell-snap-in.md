---
title: 撰寫自訂的 Windows PowerShell 嵌入式管理單元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364247"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="67653-102">撰寫自訂 Windows PowerShell 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="67653-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="67653-103">這個範例示範如何撰寫 Windows PowerShell 嵌入式管理單元，以註冊特定 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="67653-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="67653-104">使用這種類型的嵌入式管理單元，您可以指定要註冊的 Cmdlet、提供者、類型或格式。</span><span class="sxs-lookup"><span data-stu-id="67653-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="67653-105">如需有關如何撰寫嵌入式管理單元，以在元件中註冊所有 Cmdlet 和提供者的詳細資訊，請參閱[撰寫 Windows PowerShell 嵌入式管理單元](./writing-a-windows-powershell-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="67653-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="67653-106">撰寫可註冊特定 Cmdlet 的 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="67653-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="67653-107">加入 RunInstallerAttribute 屬性。</span><span class="sxs-lookup"><span data-stu-id="67653-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="67653-108">建立衍生自[Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)類別的公用類別。</span><span class="sxs-lookup"><span data-stu-id="67653-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="67653-109">在此範例中，類別名稱為 "CustomPSSnapinTest"。</span><span class="sxs-lookup"><span data-stu-id="67653-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="67653-110">新增嵌入式管理單元名稱的公用屬性（必要）。</span><span class="sxs-lookup"><span data-stu-id="67653-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="67653-111">命名嵌入式管理單元時，請勿使用下列任何字元： #。</span><span class="sxs-lookup"><span data-stu-id="67653-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="67653-112">、（） {} [] &-/\ $;： "' \< > &#124; ？</span><span class="sxs-lookup"><span data-stu-id="67653-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span></span> <span data-ttu-id="67653-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="67653-113">@ \` \*</span></span>

   <span data-ttu-id="67653-114">在此範例中，嵌入式管理單元的名稱是 "CustomPSSnapInTest"。</span><span class="sxs-lookup"><span data-stu-id="67653-114">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="67653-115">新增嵌入式管理單元之廠商的公用屬性（必要）。</span><span class="sxs-lookup"><span data-stu-id="67653-115">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="67653-116">在此範例中，廠商是 "Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="67653-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="67653-117">新增嵌入式管理單元之廠商資源的公用屬性（選擇性）。</span><span class="sxs-lookup"><span data-stu-id="67653-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="67653-118">在此範例中，廠商資源為 "CustomPSSnapInTest，Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="67653-118">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="67653-119">新增嵌入式管理單元描述的公用屬性（必要）。</span><span class="sxs-lookup"><span data-stu-id="67653-119">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="67653-120">在此範例中，描述為：「這是自訂的 Windows PowerShell 嵌入式管理單元，其中包含 HelloWorld 和 CustomSnapinTest Cmdlet」。</span><span class="sxs-lookup"><span data-stu-id="67653-120">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

7. <span data-ttu-id="67653-121">新增嵌入式管理單元的 [描述] 資源的公用屬性（選擇性）。</span><span class="sxs-lookup"><span data-stu-id="67653-121">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="67653-122">在此範例中，廠商資源是 "CustomPSSnapInTest，這是一個自訂的 Windows PowerShell 嵌入式管理單元，其中包含 HelloWorld 和 CustomSnapinTest Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="67653-122">In this example, the vendor resource is "CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="67653-123">使用[Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry)類別，指定屬於自訂嵌入式管理單元（選擇性）的指令程式。</span><span class="sxs-lookup"><span data-stu-id="67653-123">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="67653-124">此處新增的資訊包括 Cmdlet 的名稱、其 .NET 類型和 Cmdlet 說明檔名稱（Cmdlet 說明文件名的格式應為 dll-help .xml）。</span><span class="sxs-lookup"><span data-stu-id="67653-124">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be name.dll-help.xml).</span></span>

   <span data-ttu-id="67653-125">這個範例會新增 HelloWorld 和 TestCustomSnapinTest Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="67653-125">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="67653-126">指定屬於自訂嵌入式管理單元的提供者（選擇性）。</span><span class="sxs-lookup"><span data-stu-id="67653-126">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="67653-127">這個範例不會指定任何提供者。</span><span class="sxs-lookup"><span data-stu-id="67653-127">This example does not specify any providers.</span></span>

10. <span data-ttu-id="67653-128">指定屬於自訂嵌入式管理單元的類型（選擇性）。</span><span class="sxs-lookup"><span data-stu-id="67653-128">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="67653-129">這個範例不會指定任何類型。</span><span class="sxs-lookup"><span data-stu-id="67653-129">This example does not specify any types.</span></span>

11. <span data-ttu-id="67653-130">指定屬於自訂嵌入式管理單元的格式（選擇性）。</span><span class="sxs-lookup"><span data-stu-id="67653-130">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="67653-131">這個範例不會指定任何格式。</span><span class="sxs-lookup"><span data-stu-id="67653-131">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="67653-132">範例</span><span class="sxs-lookup"><span data-stu-id="67653-132">Example</span></span>

<span data-ttu-id="67653-133">這個範例示範如何撰寫自訂的 Windows PowerShell 嵌入式管理單元，可用來註冊 HelloWorld 和 CustomSnapinTest Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="67653-133">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the Test-HelloWorld and Test-CustomSnapinTest cmdlets.</span></span> <span data-ttu-id="67653-134">請注意，在此範例中，完整的元件可能包含不會由這個嵌入式管理單元註冊的其他 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="67653-134">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
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
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
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
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

<span data-ttu-id="67653-135">如需註冊嵌入式管理單元的詳細資訊，請參閱《 [Windows PowerShell 程式設計人員指南》](../prog-guide/windows-powershell-programmer-s-guide.md)中的[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="67653-135">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="67653-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67653-136">See Also</span></span>

[<span data-ttu-id="67653-137">如何註冊 Cmdlet、提供者和主機應用程式</span><span class="sxs-lookup"><span data-stu-id="67653-137">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="67653-138">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="67653-138">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)