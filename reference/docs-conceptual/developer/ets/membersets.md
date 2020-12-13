---
ms.date: 07/09/2020
ms.topic: reference
title: 擴充類型系統成員集合
description: 擴充類型系統成員集合
ms.openlocfilehash: b04d2618dc4bcf302d2e683d50c351ad3aa076ac
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650086"
---
# <a name="ets-member-sets"></a><span data-ttu-id="94390-103">ETS 成員集</span><span class="sxs-lookup"><span data-stu-id="94390-103">ETS member sets</span></span>

<span data-ttu-id="94390-104">成員集可讓您將 **PSObject** 物件的成員分割成兩個子集，讓子集的成員可以透過其子集名稱加以參考。</span><span class="sxs-lookup"><span data-stu-id="94390-104">Member sets allow you to partition the members of the **PSObject** object into two subsets so that the members of the subsets can be referenced together by their subset name.</span></span> <span data-ttu-id="94390-105">這兩種類型的子集包括屬性集和成員集。</span><span class="sxs-lookup"><span data-stu-id="94390-105">The two types of subsets include property sets and member sets.</span></span> <span data-ttu-id="94390-106">例如，PowerShell 如何使用成員集，會有一個名為 **DefaultDisplayPropertySet** 的特定屬性集，用來決定在執行時間，要針對指定的 **PSObject** 物件顯示哪些屬性。</span><span class="sxs-lookup"><span data-stu-id="94390-106">For example of how PowerShell uses member sets, there is a specific property set named **DefaultDisplayPropertySet** that is used to determine, at runtime, which properties to display for a given **PSObject** object.</span></span>

## <a name="property-sets"></a><span data-ttu-id="94390-107">屬性集</span><span class="sxs-lookup"><span data-stu-id="94390-107">Property Sets</span></span>

<span data-ttu-id="94390-108">屬性集可以包含 **PSObject** 型別的任意數目屬性。</span><span class="sxs-lookup"><span data-stu-id="94390-108">Property sets can include any number of properties of an **PSObject** type.</span></span> <span data-ttu-id="94390-109">一般情況下，每當需要相同) 類型 (的屬性集合時，就可以使用屬性集。</span><span class="sxs-lookup"><span data-stu-id="94390-109">In general, a property set can be used whenever a collection of properties (of the same type) is needed.</span></span> <span data-ttu-id="94390-110">您可以 `PSPropertySet(System.String,System.Collections.Generic.IEnumerable{System.String})` 使用屬性集的名稱和參考屬性的名稱來呼叫該函式，以建立屬性集。</span><span class="sxs-lookup"><span data-stu-id="94390-110">The property set is created by calling the `PSPropertySet(System.String,System.Collections.Generic.IEnumerable{System.String})` constructor with the name of the property set and the names of the referenced properties.</span></span> <span data-ttu-id="94390-111">然後，您可以使用建立的 **PSPropertySet** 物件做為指向集合中屬性的別名。</span><span class="sxs-lookup"><span data-stu-id="94390-111">The created **PSPropertySet** object can then be used as an alias that points to the properties in the set.</span></span> <span data-ttu-id="94390-112">[PSPropertySet](/dotnet/api/system.management.automation.pspropertyset)類別具有下列屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="94390-112">The [PSPropertySet](/dotnet/api/system.management.automation.pspropertyset) class has the following properties and methods.</span></span>

- <span data-ttu-id="94390-113">**IsInstance** 屬性：取得 **布林** 值，這個值表示屬性的來源。</span><span class="sxs-lookup"><span data-stu-id="94390-113">**IsInstance** property: Gets a **Boolean** value that indicates the source of the property.</span></span>
- <span data-ttu-id="94390-114">**MemberType** 屬性：取得屬性集內的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="94390-114">**MemberType** property: Gets the type of properties in the property set.</span></span>
- <span data-ttu-id="94390-115">**Name** 屬性：取得屬性集的名稱。</span><span class="sxs-lookup"><span data-stu-id="94390-115">**Name** property: Gets the name of the property set.</span></span>
- <span data-ttu-id="94390-116">**ReferencedPropertyNames** 屬性：取得屬性集內屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="94390-116">**ReferencedPropertyNames** property: Gets the names of the properties in the property set.</span></span>
- <span data-ttu-id="94390-117">**TypeNameOfValue** 屬性：取得將此集合定義為屬性集的 **PropertySet** 列舉常數。</span><span class="sxs-lookup"><span data-stu-id="94390-117">**TypeNameOfValue** property: Gets a **PropertySet** enumeration constant that defines this set as a property set.</span></span>
- <span data-ttu-id="94390-118">**Value** 屬性：取得或設定 **PSPropertySet** 物件。</span><span class="sxs-lookup"><span data-stu-id="94390-118">**Value** property: Gets or sets the **PSPropertySet** object.</span></span>
- <span data-ttu-id="94390-119">`PSPropertySet.Copy` 方法：建立 **PSPropertySet** 物件的完整複本。</span><span class="sxs-lookup"><span data-stu-id="94390-119">`PSPropertySet.Copy` method: Makes an exact copy of the **PSPropertySet** object.</span></span>
- <span data-ttu-id="94390-120">`PSMemberSet.ToString` 方法：將 **PSPropertySet** 物件轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="94390-120">`PSMemberSet.ToString` method: Converts the **PSPropertySet** object to a string.</span></span>

## <a name="member-sets"></a><span data-ttu-id="94390-121">成員集</span><span class="sxs-lookup"><span data-stu-id="94390-121">Member Sets</span></span>

<span data-ttu-id="94390-122">成員集可包含任何類型的任意數目的擴充成員。</span><span class="sxs-lookup"><span data-stu-id="94390-122">Member sets can include any number of extended members of any type.</span></span> <span data-ttu-id="94390-123">成員集的建立方式是呼叫 `PSMemberSet(System.String,System.Collections.Generic.IEnumerable{System.Management.Automation.PSMemberInfo})`</span><span class="sxs-lookup"><span data-stu-id="94390-123">The member set is created by calling the `PSMemberSet(System.String,System.Collections.Generic.IEnumerable{System.Management.Automation.PSMemberInfo})`</span></span>
<span data-ttu-id="94390-124">具有成員集名稱的函式和參考成員名稱的函式。</span><span class="sxs-lookup"><span data-stu-id="94390-124">constructor with the name of the member set and the names of the referenced members.</span></span> <span data-ttu-id="94390-125">然後，您可以使用建立的 **PSPropertySet** 物件做為指向集合中成員的別名。</span><span class="sxs-lookup"><span data-stu-id="94390-125">The created **PSPropertySet** object can then be used as an alias that points to the members in the set.</span></span> <span data-ttu-id="94390-126">[PSMemberSet](/dotnet/api/system.management.automation.psmemberset)類別具有下列屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="94390-126">The [PSMemberSet](/dotnet/api/system.management.automation.psmemberset) class has the following properties and methods.</span></span>

- <span data-ttu-id="94390-127">**IsInstance** 屬性：取得指出成員來源的 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="94390-127">**IsInstance** property: Gets a **Boolean** value that indicates the source of the member.</span></span>
- <span data-ttu-id="94390-128">**Members** 屬性：取得成員集合的所有成員。</span><span class="sxs-lookup"><span data-stu-id="94390-128">**Members** property: Gets all the members of the member set.</span></span>
- <span data-ttu-id="94390-129">**MemberType** 屬性：取得將此集合定義為成員集的成員 **集列舉常數** 。</span><span class="sxs-lookup"><span data-stu-id="94390-129">**MemberType** property: Gets a **MemberSet** enumeration constant that defines this set as a member set.</span></span>
- <span data-ttu-id="94390-130">**方法** 屬性：取得成員集合中包含的方法。</span><span class="sxs-lookup"><span data-stu-id="94390-130">**Methods** property: Gets the methods included in the member set.</span></span>
- <span data-ttu-id="94390-131">**Properties** 屬性：取得成員集合中包含的屬性。</span><span class="sxs-lookup"><span data-stu-id="94390-131">**Properties** property: Gets the properties included in the member set.</span></span>
- <span data-ttu-id="94390-132">**TypeNameOfValue** 屬性：取得將此集合定義為成員集的成員 **集列舉常數** 。</span><span class="sxs-lookup"><span data-stu-id="94390-132">**TypeNameOfValue** property: Gets a **MemberSet** enumeration constant that defines this set as a member set.</span></span>
- <span data-ttu-id="94390-133">**Value** 屬性：取得 **PSMemberSet** 物件。</span><span class="sxs-lookup"><span data-stu-id="94390-133">**Value** property: Gets the **PSMemberSet** object.</span></span>
- <span data-ttu-id="94390-134">`PSMemberSet.Copy` 方法：建立 **PSMemberSet** 物件的完整複本。</span><span class="sxs-lookup"><span data-stu-id="94390-134">`PSMemberSet.Copy` method: Makes an exact copy of the **PSMemberSet** object.</span></span>
- <span data-ttu-id="94390-135">`PSMemberSet.ToString` 方法：將 **PSMemberSet** 物件轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="94390-135">`PSMemberSet.ToString` method: Converts the **PSMemberSet** object to a string.</span></span>
