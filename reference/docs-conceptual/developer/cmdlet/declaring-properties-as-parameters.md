---
title: 將屬性宣告為參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365747"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="83fb5-102">將屬性宣告為參數</span><span class="sxs-lookup"><span data-stu-id="83fb5-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="83fb5-103">本主題提供您在宣告 Cmdlet 的參數之前必須瞭解的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="83fb5-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="83fb5-104">若要在您的 Cmdlet 類別中宣告 Cmdlet 的參數，請定義代表每個參數的公用屬性，然後將一個或多個參數屬性加入至每個屬性。</span><span class="sxs-lookup"><span data-stu-id="83fb5-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="83fb5-105">Windows PowerShell 執行時間會使用參數屬性，將屬性識別為 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="83fb5-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="83fb5-106">宣告參數屬性的基本語法為 `[Parameter()]`。</span><span class="sxs-lookup"><span data-stu-id="83fb5-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="83fb5-107">以下是定義為必要參數之屬性的範例。</span><span class="sxs-lookup"><span data-stu-id="83fb5-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="83fb5-108">以下是有關參數的一些注意事項。</span><span class="sxs-lookup"><span data-stu-id="83fb5-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="83fb5-109">參數必須明確標示為公用。</span><span class="sxs-lookup"><span data-stu-id="83fb5-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="83fb5-110">未標示為公用的參數預設為內部，Windows PowerShell 執行時間將找不到。</span><span class="sxs-lookup"><span data-stu-id="83fb5-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="83fb5-111">參數應該定義為 Microsoft .NET Framework 類型，以提供更佳的參數驗證。</span><span class="sxs-lookup"><span data-stu-id="83fb5-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="83fb5-112">例如，限制為一組值以外一個值的參數，應定義為列舉類型。</span><span class="sxs-lookup"><span data-stu-id="83fb5-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="83fb5-113">採用統一資源識別元（URI）值的參數應該是[system.string 類型。](/dotnet/api/System.Uri)</span><span class="sxs-lookup"><span data-stu-id="83fb5-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="83fb5-114">針對所有但自由格式的文字屬性，請避免基本的字串參數。</span><span class="sxs-lookup"><span data-stu-id="83fb5-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="83fb5-115">您可以將參數新增至任意數目的參數集合。</span><span class="sxs-lookup"><span data-stu-id="83fb5-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="83fb5-116">如需參數集的詳細資訊，請參閱[Cmdlet 參數集](./cmdlet-parameter-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="83fb5-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="83fb5-117">Windows PowerShell 也會提供一組可自動提供給每個 Cmdlet 的通用參數。</span><span class="sxs-lookup"><span data-stu-id="83fb5-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="83fb5-118">如需這些參數和其別名的詳細資訊，請參閱[Cmdlet 一般參數](./common-parameter-names.md)。</span><span class="sxs-lookup"><span data-stu-id="83fb5-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="83fb5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83fb5-119">See Also</span></span>

[<span data-ttu-id="83fb5-120">Cmdlet 一般參數</span><span class="sxs-lookup"><span data-stu-id="83fb5-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="83fb5-121">Cmdlet 參數的類型</span><span class="sxs-lookup"><span data-stu-id="83fb5-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="83fb5-122">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="83fb5-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)