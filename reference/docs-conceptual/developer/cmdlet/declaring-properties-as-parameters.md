---
ms.date: 09/13/2016
ms.topic: reference
title: 將屬性宣告為參數
description: 將屬性宣告為參數
ms.openlocfilehash: ade7928e2ca277da8bbd1a5e04997bd1d05f1e5d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653162"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="d1c78-103">將屬性宣告為參數</span><span class="sxs-lookup"><span data-stu-id="d1c78-103">Declaring Properties as Parameters</span></span>

<span data-ttu-id="d1c78-104">本主題提供您在宣告 Cmdlet 參數之前必須瞭解的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="d1c78-104">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="d1c78-105">若要在您的 Cmdlet 類別內宣告 Cmdlet 的參數，請定義代表每個參數的公用屬性，然後將一或多個參數屬性新增至每個屬性。</span><span class="sxs-lookup"><span data-stu-id="d1c78-105">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="d1c78-106">Windows PowerShell 執行時間使用參數屬性將屬性識別為 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="d1c78-106">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="d1c78-107">宣告參數屬性的基本語法為 `[Parameter()]` 。</span><span class="sxs-lookup"><span data-stu-id="d1c78-107">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="d1c78-108">以下是定義為必要參數的屬性範例。</span><span class="sxs-lookup"><span data-stu-id="d1c78-108">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="d1c78-109">以下是一些要記住參數的事項。</span><span class="sxs-lookup"><span data-stu-id="d1c78-109">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="d1c78-110">參數必須明確標記為公用。</span><span class="sxs-lookup"><span data-stu-id="d1c78-110">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="d1c78-111">未標記為 public 的參數預設為內部，而且 Windows PowerShell 執行時間找不到。</span><span class="sxs-lookup"><span data-stu-id="d1c78-111">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="d1c78-112">參數應定義為 Microsoft .NET Framework 類型，以提供更好的參數驗證。</span><span class="sxs-lookup"><span data-stu-id="d1c78-112">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="d1c78-113">例如，限制為一組值的一個值的參數，應該定義為列舉型別。</span><span class="sxs-lookup"><span data-stu-id="d1c78-113">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="d1c78-114">採用統一資源識別項 (URI) 值的參數應為[system.string 類型。](/dotnet/api/System.Uri)</span><span class="sxs-lookup"><span data-stu-id="d1c78-114">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="d1c78-115">針對所有但自由格式的文字屬性，請避免基本的字串參數。</span><span class="sxs-lookup"><span data-stu-id="d1c78-115">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="d1c78-116">您可以將參數新增至任意數目的參數集合。</span><span class="sxs-lookup"><span data-stu-id="d1c78-116">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="d1c78-117">如需參數集的詳細資訊，請參閱 [Cmdlet 參數集](./cmdlet-parameter-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="d1c78-117">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="d1c78-118">Windows PowerShell 也會提供一組可自動提供給每個 Cmdlet 的通用參數。</span><span class="sxs-lookup"><span data-stu-id="d1c78-118">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="d1c78-119">如需這些參數及其別名的詳細資訊，請參閱 [Cmdlet 一般參數](./common-parameter-names.md)。</span><span class="sxs-lookup"><span data-stu-id="d1c78-119">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1c78-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1c78-120">See Also</span></span>

[<span data-ttu-id="d1c78-121">Cmdlet 一般參數</span><span class="sxs-lookup"><span data-stu-id="d1c78-121">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="d1c78-122">Cmdlet 參數的類型</span><span class="sxs-lookup"><span data-stu-id="d1c78-122">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="d1c78-123">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d1c78-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
