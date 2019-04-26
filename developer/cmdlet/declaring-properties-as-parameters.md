---
title: 宣告做為參數的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068261"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="0d045-102">將屬性宣告為參數</span><span class="sxs-lookup"><span data-stu-id="0d045-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="0d045-103">本主題提供宣告之參數的 cmdlet 之前，必須了解的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="0d045-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="0d045-104">若要宣告 cmdlet 類別內的 cmdlet 的參數，定義公用屬性，代表每個參數，然後再新增一或多個參數屬性對每個屬性。</span><span class="sxs-lookup"><span data-stu-id="0d045-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="0d045-105">Windows PowerShell 執行階段會使用參數屬性來識別做為指令程式參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="0d045-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="0d045-106">宣告參數屬性的基本語法是`[Parameter()]`。</span><span class="sxs-lookup"><span data-stu-id="0d045-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="0d045-107">以下是定義為必要的參數屬性的範例。</span><span class="sxs-lookup"><span data-stu-id="0d045-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="0d045-108">以下是參數時，必須注意的事項。</span><span class="sxs-lookup"><span data-stu-id="0d045-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="0d045-109">參數必須明確標示為公用。</span><span class="sxs-lookup"><span data-stu-id="0d045-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="0d045-110">未標示為公用的預設值為 internal，並將找不到 Windows PowerShell 執行階段的參數。</span><span class="sxs-lookup"><span data-stu-id="0d045-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="0d045-111">參數應定義為 Microsoft.NET Framework 型別，以提供更好的參數驗證。</span><span class="sxs-lookup"><span data-stu-id="0d045-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="0d045-112">比方說，會限制為一個值，超出一組值的參數應該定義為列舉型別。</span><span class="sxs-lookup"><span data-stu-id="0d045-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="0d045-113">使用統一資源識別元 (URI) 值的參數必須是類型[System.Uri](/dotnet/api/System.Uri)。</span><span class="sxs-lookup"><span data-stu-id="0d045-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="0d045-114">避免以外的所有自由格式文字屬性的基本字串參數。</span><span class="sxs-lookup"><span data-stu-id="0d045-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="0d045-115">您可以將參數新增至任何數目的參數集合。</span><span class="sxs-lookup"><span data-stu-id="0d045-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="0d045-116">如需參數集的詳細資訊，請參閱[指令程式參數設定](./cmdlet-parameter-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="0d045-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="0d045-117">Windows PowerShell 也提供一組通用參數，會自動提供給每個 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0d045-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="0d045-118">如需有關這些參數和其別名的詳細資訊，請參閱 <<c0> [ 一般參數的 Cmdlet](./common-parameter-names.md)。</span><span class="sxs-lookup"><span data-stu-id="0d045-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d045-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d045-119">See Also</span></span>

[<span data-ttu-id="0d045-120">指令程式的一般參數</span><span class="sxs-lookup"><span data-stu-id="0d045-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="0d045-121">Cmdlet 參數的類型</span><span class="sxs-lookup"><span data-stu-id="0d045-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="0d045-122">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0d045-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
