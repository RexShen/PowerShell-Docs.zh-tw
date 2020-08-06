---
title: 撰寫 Windows PowerShell 嵌入式管理單元 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.openlocfilehash: 02603c54fb9852a8b78ecf68e3ee387d1fd418fc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779098"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="5bffe-102">撰寫 Windows PowerShell 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="5bffe-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="5bffe-103">這個範例示範如何撰寫 Windows PowerShell 嵌入式管理單元，可用來在元件中註冊所有的 Cmdlet 和 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="5bffe-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="5bffe-104">使用這種類型的嵌入式管理單元時，您不會選取要註冊的 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="5bffe-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="5bffe-105">若要撰寫可讓您選取已註冊內容的嵌入式管理單元，請參閱[撰寫自訂的 Windows PowerShell 嵌入式管理單元](./writing-a-custom-windows-powershell-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="5bffe-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="5bffe-106">撰寫 Windows PowerShell 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="5bffe-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="5bffe-107">加入 RunInstallerAttribute 屬性。</span><span class="sxs-lookup"><span data-stu-id="5bffe-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="5bffe-108">建立衍生自[PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)類別的公用類別。</span><span class="sxs-lookup"><span data-stu-id="5bffe-108">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="5bffe-109">在此範例中，類別名稱為 "GetProcPSSnapIn01"。</span><span class="sxs-lookup"><span data-stu-id="5bffe-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="5bffe-110">新增 (所需的嵌入式管理單元名稱) 的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="5bffe-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="5bffe-111">命名嵌入式管理單元時，請勿使用下列任何字元： `#` 、 `.` 、 `,` 、、 `(` `)` `{` `}` `[` `]` `&` `-` `/` `\` `$` `;` `:` `"` `'` `<` `>` `|` `?` `@` 、、、、 `` ` `` 、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、`*`</span><span class="sxs-lookup"><span data-stu-id="5bffe-111">When naming snap-ins, do not use any of the following characters: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span></span>

    <span data-ttu-id="5bffe-112">在此範例中，嵌入式管理單元的名稱是 "GetProcPSSnapIn01"。</span><span class="sxs-lookup"><span data-stu-id="5bffe-112">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="5bffe-113">新增嵌入式管理單元廠商的公用屬性， (所需的) 。</span><span class="sxs-lookup"><span data-stu-id="5bffe-113">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="5bffe-114">在此範例中，廠商是 "Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="5bffe-114">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="5bffe-115">新增嵌入式管理單元之廠商資源的公用屬性 (選擇性) 。</span><span class="sxs-lookup"><span data-stu-id="5bffe-115">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="5bffe-116">在此範例中，廠商資源為 "GetProcPSSnapIn01，Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="5bffe-116">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="5bffe-117">針對所需的嵌入式管理單元 (，新增 [公用] 屬性) 。</span><span class="sxs-lookup"><span data-stu-id="5bffe-117">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="5bffe-118">在此範例中，描述是「這是註冊了 get proc Cmdlet 的 Windows PowerShell 嵌入式管理單元」。</span><span class="sxs-lookup"><span data-stu-id="5bffe-118">In this example, the description is "This is a Windows PowerShell snap-in that registers the  get-proc cmdlet".</span></span>

7. <span data-ttu-id="5bffe-119">新增嵌入式管理單元之 [描述] 資源的 [公用] 屬性 (選擇性) 。</span><span class="sxs-lookup"><span data-stu-id="5bffe-119">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="5bffe-120">在此範例中，廠商資源是 "GetProcPSSnapIn01，這是一個 Windows PowerShell 嵌入式管理單元，它會註冊「get-proc」 Cmdlet」。</span><span class="sxs-lookup"><span data-stu-id="5bffe-120">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in  that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="5bffe-121">範例</span><span class="sxs-lookup"><span data-stu-id="5bffe-121">Example</span></span>

<span data-ttu-id="5bffe-122">這個範例示範如何撰寫 Windows PowerShell 嵌入式管理單元，以在 Windows PowerShell shell 中用來註冊該程式。</span><span class="sxs-lookup"><span data-stu-id="5bffe-122">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="5bffe-123">請注意，在此範例中，完整的元件只會包含 GetProcPSSnapIn01 嵌入式管理單元類別和 `Get-Proc` Cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="5bffe-123">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the `Get-Proc` cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5bffe-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bffe-124">See Also</span></span>

<span data-ttu-id="5bffe-125">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5bffe-125">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="5bffe-126">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="5bffe-126">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
