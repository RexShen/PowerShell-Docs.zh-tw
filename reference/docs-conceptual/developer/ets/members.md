---
title: 擴充類型系統類別成員
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: c066bd69c0ab20cceff96aa789654e80443758e5
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217947"
---
# <a name="extended-type-system-class-members"></a><span data-ttu-id="ce9fd-102">擴充類型系統類別成員</span><span class="sxs-lookup"><span data-stu-id="ce9fd-102">Extended Type System class members</span></span>

<span data-ttu-id="ce9fd-103">ETS 是指\*\* psmembertypes\*\*列舉所定義的各種不同類型的成員。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-103">ETS refers to a number of different kinds of members whose types are defined by the **PSMemberTypes** enumeration.</span></span> <span data-ttu-id="ce9fd-104">這些成員類型包括屬性、方法、成員和成員集，這些都是由自己的 CLR 類型所定義。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-104">These member types include properties, methods, members, and member sets that are each defined by their own CLR type.</span></span> <span data-ttu-id="ce9fd-105">例如， **NoteProperty**是由自己的**PSNoteProperty**類型所定義。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-105">For example, a **NoteProperty** is defined by its own **PSNoteProperty** type.</span></span> <span data-ttu-id="ce9fd-106">這些個別的 CLR 型別都有自己唯一的屬性，以及繼承自[PSMemberInfo 類別](/dotnet/api/system.management.automation.psmemberinfo)的通用屬性。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-106">These individual CLR types have both their own unique properties and common properties that are inherited from the [PSMemberInfo class](/dotnet/api/system.management.automation.psmemberinfo).</span></span>

## <a name="the-psmemberinfo-class"></a><span data-ttu-id="ce9fd-107">PSMemberInfo 類別</span><span class="sxs-lookup"><span data-stu-id="ce9fd-107">The PSMemberInfo class</span></span>

<span data-ttu-id="ce9fd-108">**PSMemberInfo**類別可做為所有 ETS 成員類型的基類。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-108">The **PSMemberInfo** class serves as a base class for all ETS member types.</span></span> <span data-ttu-id="ce9fd-109">這個類別會將下列基底屬性提供給所有成員 CLR 類型。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-109">This class provides the following base properties to all member CLR types.</span></span>

- <span data-ttu-id="ce9fd-110">**Name**屬性：成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-110">**Name** property: The name of the member.</span></span> <span data-ttu-id="ce9fd-111">此名稱可由基底物件定義，或在公開調整成員或擴充成員時由 PowerShell 定義。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-111">This name can be defined by the base-object or defined by PowerShell when adapted members or extended members are exposed.</span></span>
- <span data-ttu-id="ce9fd-112">**Value**屬性：從特定成員傳回的值。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-112">**Value** property: The value returned from the particular member.</span></span> <span data-ttu-id="ce9fd-113">每個成員類型都會定義它如何處理其成員值。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-113">Each member type defines how it handles its member value.</span></span>
- <span data-ttu-id="ce9fd-114">**TypeNameOfValue**屬性：這是 value 屬性所傳回之值的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-114">**TypeNameOfValue** property: This is the name of the CLR type of the value that is returned by the Value property.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="ce9fd-115">存取成員</span><span class="sxs-lookup"><span data-stu-id="ce9fd-115">Accessing members</span></span>

<span data-ttu-id="ce9fd-116">成員集合可以透過**PSObject**物件的**members**、**方法**和**properties**屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-116">Collections of members can be accessed through the **Members**, **Methods**, and **Properties** properties of the **PSObject** object.</span></span>

## <a name="ets-properties"></a><span data-ttu-id="ce9fd-117">ETS 屬性</span><span class="sxs-lookup"><span data-stu-id="ce9fd-117">ETS properties</span></span>

<span data-ttu-id="ce9fd-118">ETS 屬性是可視為屬性的成員。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-118">ETS properties are members that can be treated as a property.</span></span> <span data-ttu-id="ce9fd-119">基本上，它們可以出現在運算式的左側。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-119">Essentially, they can appear on the left-hand side of an expression.</span></span> <span data-ttu-id="ce9fd-120">其中包括別名屬性、程式碼屬性、PowerShell 屬性、附注屬性和腳本屬性。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-120">They include alias properties, code properties, PowerShell properties, note properties, and script properties.</span></span> <span data-ttu-id="ce9fd-121">如需這些屬性類型的詳細資訊，請參閱[ETS 屬性](properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-121">For more information about these types of properties, see [ETS properties](properties.md).</span></span>

## <a name="ets-methods"></a><span data-ttu-id="ce9fd-122">ETS 方法</span><span class="sxs-lookup"><span data-stu-id="ce9fd-122">ETS methods</span></span>

<span data-ttu-id="ce9fd-123">ETS 方法是可以接受引數、可能會傳回結果，而且不能出現在運算式左側的成員。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-123">ETS methods are members that can take arguments, may return results, and cannot appear on the left-hand side of an expression.</span></span> <span data-ttu-id="ce9fd-124">其中包括程式碼方法、PowerShell 方法和腳本方法。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-124">They include code methods, PowerShell methods, and script methods.</span></span>
<span data-ttu-id="ce9fd-125">如需這些類型之方法的詳細資訊，請參閱[ETS 方法](methods.md)。</span><span class="sxs-lookup"><span data-stu-id="ce9fd-125">For more information about these types of methods, see [ETS methods](methods.md).</span></span>
