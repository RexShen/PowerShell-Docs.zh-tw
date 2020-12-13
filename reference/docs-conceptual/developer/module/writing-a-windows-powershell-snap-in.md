---
ms.date: 09/13/2016
ms.topic: reference
title: 撰寫 Windows PowerShell 嵌入式管理單元
description: 撰寫 Windows PowerShell 嵌入式管理單元
ms.openlocfilehash: f658c2fa1211bfb77d2e8edd3999ce7f92df13bb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659451"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="d25eb-103">撰寫 Windows PowerShell 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="d25eb-103">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="d25eb-104">此範例示範如何撰寫 Windows PowerShell 的嵌入式管理單元，可用來註冊元件中的所有 Cmdlet 和 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="d25eb-104">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="d25eb-105">使用這種類型的嵌入式管理單元時，不會選取您要註冊的 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="d25eb-105">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="d25eb-106">若要撰寫可讓您選取已註冊內容的嵌入式管理單元，請參閱 [撰寫自訂 Windows PowerShell 嵌入式管理單元](./writing-a-custom-windows-powershell-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="d25eb-106">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="d25eb-107">撰寫 Windows PowerShell 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="d25eb-107">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="d25eb-108">加入 RunInstallerAttribute 屬性。</span><span class="sxs-lookup"><span data-stu-id="d25eb-108">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="d25eb-109">建立衍生自 [PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) 類別的公用類別。</span><span class="sxs-lookup"><span data-stu-id="d25eb-109">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="d25eb-110">在此範例中，類別名稱為 "GetProcPSSnapIn01"。</span><span class="sxs-lookup"><span data-stu-id="d25eb-110">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="d25eb-111">新增嵌入式管理單元名稱的公用屬性 (所需的) 。</span><span class="sxs-lookup"><span data-stu-id="d25eb-111">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="d25eb-112">命名嵌入式管理單元時，請勿使用下列任何字元： `#` 、 `.` 、 `,` 、 `(` 、 `)` 、 `{` 、 `}` `[` `]` `&` `-` `/` `\` `$` `;` `:` `"` `'` `<` `>` `|` `?` `@` `` ` `` 、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `*`</span><span class="sxs-lookup"><span data-stu-id="d25eb-112">When naming snap-ins, do not use any of the following characters: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span></span>

    <span data-ttu-id="d25eb-113">在此範例中，嵌入式管理單元的名稱為 "GetProcPSSnapIn01"。</span><span class="sxs-lookup"><span data-stu-id="d25eb-113">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="d25eb-114">為嵌入式管理單元的廠商新增公用屬性 (必要的) 。</span><span class="sxs-lookup"><span data-stu-id="d25eb-114">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="d25eb-115">在此範例中，廠商為 "Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="d25eb-115">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="d25eb-116">為嵌入式管理單元的廠商資源新增公用屬性 (選擇性) 。</span><span class="sxs-lookup"><span data-stu-id="d25eb-116">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="d25eb-117">在此範例中，廠商資源是「GetProcPSSnapIn01，Microsoft」。</span><span class="sxs-lookup"><span data-stu-id="d25eb-117">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="d25eb-118">新增嵌入式管理單元描述 (所需) 的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="d25eb-118">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="d25eb-119">在此範例中，描述為「這是註冊 proc Cmdlet 的 Windows PowerShell 嵌入式管理單元」。</span><span class="sxs-lookup"><span data-stu-id="d25eb-119">In this example, the description is "This is a Windows PowerShell snap-in that registers the  get-proc cmdlet".</span></span>

7. <span data-ttu-id="d25eb-120">為嵌入式管理單元的描述資源新增公用屬性 (選擇性) 。</span><span class="sxs-lookup"><span data-stu-id="d25eb-120">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="d25eb-121">在此範例中，廠商資源是「GetProcPSSnapIn01，這是註冊 proc Cmdlet 的 Windows PowerShell 嵌入式管理單元」。</span><span class="sxs-lookup"><span data-stu-id="d25eb-121">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in  that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="d25eb-122">範例</span><span class="sxs-lookup"><span data-stu-id="d25eb-122">Example</span></span>

<span data-ttu-id="d25eb-123">此範例示範如何撰寫 Windows PowerShell 的嵌入式管理單元，可用來在 Windows PowerShell shell 中註冊 Get-Proc Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d25eb-123">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="d25eb-124">請注意，在此範例中，完整的元件只會包含 GetProcPSSnapIn01 嵌入式管理單元類別和 `Get-Proc` Cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="d25eb-124">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the `Get-Proc` cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d25eb-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d25eb-125">See Also</span></span>

<span data-ttu-id="d25eb-126">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d25eb-126">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="d25eb-127">Windows PowerShell 殼層 SDK</span><span class="sxs-lookup"><span data-stu-id="d25eb-127">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
