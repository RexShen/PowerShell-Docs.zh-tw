---
title: 擴充類型系統成員集
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 11e1e7819efecc1f1d8164ef32fb97cda978e748
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217944"
---
# <a name="ets-member-sets"></a><span data-ttu-id="0e74e-102">ETS 成員集</span><span class="sxs-lookup"><span data-stu-id="0e74e-102">ETS member sets</span></span>

<span data-ttu-id="0e74e-103">成員集可讓您將**PSObject**物件的成員分割成兩個子集，讓子集的成員可以透過其子集名稱加以參考。</span><span class="sxs-lookup"><span data-stu-id="0e74e-103">Member sets allow you to partition the members of the **PSObject** object into two subsets so that the members of the subsets can be referenced together by their subset name.</span></span> <span data-ttu-id="0e74e-104">這兩個子集類型包含屬性集和成員集。</span><span class="sxs-lookup"><span data-stu-id="0e74e-104">The two types of subsets include property sets and member sets.</span></span> <span data-ttu-id="0e74e-105">例如，PowerShell 如何使用成員集，會有一個名為**DefaultDisplayPropertySet**的特定屬性集，可在執行時間用來判斷要針對指定的**PSObject**物件顯示哪些屬性。</span><span class="sxs-lookup"><span data-stu-id="0e74e-105">For example of how PowerShell uses member sets, there is a specific property set named **DefaultDisplayPropertySet** that is used to determine, at runtime, which properties to display for a given **PSObject** object.</span></span>

## <a name="property-sets"></a><span data-ttu-id="0e74e-106">屬性集</span><span class="sxs-lookup"><span data-stu-id="0e74e-106">Property Sets</span></span>

<span data-ttu-id="0e74e-107">屬性集可以包含**PSObject**類型的任意數目屬性。</span><span class="sxs-lookup"><span data-stu-id="0e74e-107">Property sets can include any number of properties of an **PSObject** type.</span></span> <span data-ttu-id="0e74e-108">一般來說，每當需要) 相同類型 (屬性集合時，就可以使用屬性集。</span><span class="sxs-lookup"><span data-stu-id="0e74e-108">In general, a property set can be used whenever a collection of properties (of the same type) is needed.</span></span> <span data-ttu-id="0e74e-109">藉由呼叫 `PSPropertySet(System.String,System.Collections.Generic.IEnumerable{System.String})` 具有屬性集名稱和參考屬性名稱的函式，即可建立屬性集。</span><span class="sxs-lookup"><span data-stu-id="0e74e-109">The property set is created by calling the `PSPropertySet(System.String,System.Collections.Generic.IEnumerable{System.String})` constructor with the name of the property set and the names of the referenced properties.</span></span> <span data-ttu-id="0e74e-110">然後，建立的**PSPropertySet**物件可以用來當做指向集合中屬性的別名。</span><span class="sxs-lookup"><span data-stu-id="0e74e-110">The created **PSPropertySet** object can then be used as an alias that points to the properties in the set.</span></span> <span data-ttu-id="0e74e-111">[PSPropertySet](/dotnet/api/system.management.automation.pspropertyset)類別具有下列屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="0e74e-111">The [PSPropertySet](/dotnet/api/system.management.automation.pspropertyset) class has the following properties and methods.</span></span>

- <span data-ttu-id="0e74e-112">**IsInstance**屬性：取得**布林**值，指出屬性的來源。</span><span class="sxs-lookup"><span data-stu-id="0e74e-112">**IsInstance** property: Gets a **Boolean** value that indicates the source of the property.</span></span>
- <span data-ttu-id="0e74e-113">**MemberType**屬性：取得屬性集內的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="0e74e-113">**MemberType** property: Gets the type of properties in the property set.</span></span>
- <span data-ttu-id="0e74e-114">**Name**屬性：取得屬性集的名稱。</span><span class="sxs-lookup"><span data-stu-id="0e74e-114">**Name** property: Gets the name of the property set.</span></span>
- <span data-ttu-id="0e74e-115">**ReferencedPropertyNames**屬性：取得屬性集內的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="0e74e-115">**ReferencedPropertyNames** property: Gets the names of the properties in the property set.</span></span>
- <span data-ttu-id="0e74e-116">**TypeNameOfValue**屬性：取得將此集合定義為屬性集的**PropertySet**列舉常數。</span><span class="sxs-lookup"><span data-stu-id="0e74e-116">**TypeNameOfValue** property: Gets a **PropertySet** enumeration constant that defines this set as a property set.</span></span>
- <span data-ttu-id="0e74e-117">**Value**屬性：取得或設定**PSPropertySet**物件。</span><span class="sxs-lookup"><span data-stu-id="0e74e-117">**Value** property: Gets or sets the **PSPropertySet** object.</span></span>
- <span data-ttu-id="0e74e-118">`PSPropertySet.Copy`method：建立**PSPropertySet**物件的完全相同複本。</span><span class="sxs-lookup"><span data-stu-id="0e74e-118">`PSPropertySet.Copy` method: Makes an exact copy of the **PSPropertySet** object.</span></span>
- <span data-ttu-id="0e74e-119">`PSMemberSet.ToString`method：將**PSPropertySet**物件轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="0e74e-119">`PSMemberSet.ToString` method: Converts the **PSPropertySet** object to a string.</span></span>

## <a name="member-sets"></a><span data-ttu-id="0e74e-120">成員集</span><span class="sxs-lookup"><span data-stu-id="0e74e-120">Member Sets</span></span>

<span data-ttu-id="0e74e-121">成員集可以包含任何類型的任意數目的擴充成員。</span><span class="sxs-lookup"><span data-stu-id="0e74e-121">Member sets can include any number of extended members of any type.</span></span> <span data-ttu-id="0e74e-122">成員集的建立方式是呼叫`PSMemberSet(System.String,System.Collections.Generic.IEnumerable{System.Management.Automation.PSMemberInfo})`</span><span class="sxs-lookup"><span data-stu-id="0e74e-122">The member set is created by calling the `PSMemberSet(System.String,System.Collections.Generic.IEnumerable{System.Management.Automation.PSMemberInfo})`</span></span>
<span data-ttu-id="0e74e-123">具有成員集名稱和參考成員名稱的函式。</span><span class="sxs-lookup"><span data-stu-id="0e74e-123">constructor with the name of the member set and the names of the referenced members.</span></span> <span data-ttu-id="0e74e-124">然後，建立的**PSPropertySet**物件可以用來當做指向集合中成員的別名。</span><span class="sxs-lookup"><span data-stu-id="0e74e-124">The created **PSPropertySet** object can then be used as an alias that points to the members in the set.</span></span> <span data-ttu-id="0e74e-125">[PSMemberSet](/dotnet/api/system.management.automation.psmemberset)類別具有下列屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="0e74e-125">The [PSMemberSet](/dotnet/api/system.management.automation.psmemberset) class has the following properties and methods.</span></span>

- <span data-ttu-id="0e74e-126">**IsInstance**屬性：取得指出成員來源的**布林**值。</span><span class="sxs-lookup"><span data-stu-id="0e74e-126">**IsInstance** property: Gets a **Boolean** value that indicates the source of the member.</span></span>
- <span data-ttu-id="0e74e-127">**Members**屬性：取得成員集的所有成員。</span><span class="sxs-lookup"><span data-stu-id="0e74e-127">**Members** property: Gets all the members of the member set.</span></span>
- <span data-ttu-id="0e74e-128">**MemberType**屬性：取得將此集合定義為成員集的**成員**集列舉常數。</span><span class="sxs-lookup"><span data-stu-id="0e74e-128">**MemberType** property: Gets a **MemberSet** enumeration constant that defines this set as a member set.</span></span>
- <span data-ttu-id="0e74e-129">**方法**屬性：取得成員集合中包含的方法。</span><span class="sxs-lookup"><span data-stu-id="0e74e-129">**Methods** property: Gets the methods included in the member set.</span></span>
- <span data-ttu-id="0e74e-130">**Properties**屬性：取得成員集合中包含的屬性。</span><span class="sxs-lookup"><span data-stu-id="0e74e-130">**Properties** property: Gets the properties included in the member set.</span></span>
- <span data-ttu-id="0e74e-131">**TypeNameOfValue**屬性：取得將此集合定義為成員集的**成員**集列舉常數。</span><span class="sxs-lookup"><span data-stu-id="0e74e-131">**TypeNameOfValue** property: Gets a **MemberSet** enumeration constant that defines this set as a member set.</span></span>
- <span data-ttu-id="0e74e-132">**Value**屬性：取得**PSMemberSet**物件。</span><span class="sxs-lookup"><span data-stu-id="0e74e-132">**Value** property: Gets the **PSMemberSet** object.</span></span>
- <span data-ttu-id="0e74e-133">`PSMemberSet.Copy`method：建立**PSMemberSet**物件的完全相同複本。</span><span class="sxs-lookup"><span data-stu-id="0e74e-133">`PSMemberSet.Copy` method: Makes an exact copy of the **PSMemberSet** object.</span></span>
- <span data-ttu-id="0e74e-134">`PSMemberSet.ToString`method：將**PSMemberSet**物件轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="0e74e-134">`PSMemberSet.ToString` method: Converts the **PSMemberSet** object to a string.</span></span>
