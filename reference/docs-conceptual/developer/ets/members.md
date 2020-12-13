---
ms.date: 07/09/2020
ms.topic: reference
title: 擴充類型系統類別成員
description: 擴充類型系統類別成員
ms.openlocfilehash: 06488ce423f363a285ab53b21ab45989654346dc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666836"
---
# <a name="extended-type-system-class-members"></a><span data-ttu-id="6f4ed-103">擴充類型系統類別成員</span><span class="sxs-lookup"><span data-stu-id="6f4ed-103">Extended Type System class members</span></span>

<span data-ttu-id="6f4ed-104">ETS 指的是許多不同類型的成員，而其類型是由 **psmembertypes** 列舉所定義。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-104">ETS refers to a number of different kinds of members whose types are defined by the **PSMemberTypes** enumeration.</span></span> <span data-ttu-id="6f4ed-105">這些成員類型包括屬性、方法、成員和成員集，這些都是由自己的 CLR 類型所定義。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-105">These member types include properties, methods, members, and member sets that are each defined by their own CLR type.</span></span> <span data-ttu-id="6f4ed-106">例如， **NoteProperty** 是由它自己的 **PSNoteProperty** 型別所定義。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-106">For example, a **NoteProperty** is defined by its own **PSNoteProperty** type.</span></span> <span data-ttu-id="6f4ed-107">這些個別的 CLR 類型都有自己的唯一屬性，以及繼承自 [PSMemberInfo 類別](/dotnet/api/system.management.automation.psmemberinfo)的通用屬性。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-107">These individual CLR types have both their own unique properties and common properties that are inherited from the [PSMemberInfo class](/dotnet/api/system.management.automation.psmemberinfo).</span></span>

## <a name="the-psmemberinfo-class"></a><span data-ttu-id="6f4ed-108">PSMemberInfo 類別</span><span class="sxs-lookup"><span data-stu-id="6f4ed-108">The PSMemberInfo class</span></span>

<span data-ttu-id="6f4ed-109">**PSMemberInfo** 類別會作為所有 ETS 成員類型的基類。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-109">The **PSMemberInfo** class serves as a base class for all ETS member types.</span></span> <span data-ttu-id="6f4ed-110">這個類別會將下列基底屬性提供給所有成員 CLR 類型。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-110">This class provides the following base properties to all member CLR types.</span></span>

- <span data-ttu-id="6f4ed-111">**Name** 屬性：成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-111">**Name** property: The name of the member.</span></span> <span data-ttu-id="6f4ed-112">此名稱可由基底物件定義，或在公開調整成員或擴充成員時由 PowerShell 定義。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-112">This name can be defined by the base-object or defined by PowerShell when adapted members or extended members are exposed.</span></span>
- <span data-ttu-id="6f4ed-113">**Value** 屬性：從特定成員傳回的值。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-113">**Value** property: The value returned from the particular member.</span></span> <span data-ttu-id="6f4ed-114">每個成員類型都會定義其成員值的處理方式。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-114">Each member type defines how it handles its member value.</span></span>
- <span data-ttu-id="6f4ed-115">**TypeNameOfValue** 屬性：這是 value 屬性所傳回之值的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-115">**TypeNameOfValue** property: This is the name of the CLR type of the value that is returned by the Value property.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="6f4ed-116">存取成員</span><span class="sxs-lookup"><span data-stu-id="6f4ed-116">Accessing members</span></span>

<span data-ttu-id="6f4ed-117">您可以透過 **PSObject** 物件的 **成員**、**方法** 和 **屬性** 屬性來存取成員集合。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-117">Collections of members can be accessed through the **Members**, **Methods**, and **Properties** properties of the **PSObject** object.</span></span>

## <a name="ets-properties"></a><span data-ttu-id="6f4ed-118">ETS 屬性</span><span class="sxs-lookup"><span data-stu-id="6f4ed-118">ETS properties</span></span>

<span data-ttu-id="6f4ed-119">ETS 屬性是可視為屬性的成員。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-119">ETS properties are members that can be treated as a property.</span></span> <span data-ttu-id="6f4ed-120">基本上，它們可以出現在運算式的左側。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-120">Essentially, they can appear on the left-hand side of an expression.</span></span> <span data-ttu-id="6f4ed-121">它們包括別名屬性、程式碼屬性、PowerShell 屬性、附注屬性，以及腳本屬性。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-121">They include alias properties, code properties, PowerShell properties, note properties, and script properties.</span></span> <span data-ttu-id="6f4ed-122">如需這些屬性類型的詳細資訊，請參閱 [ETS 屬性](properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-122">For more information about these types of properties, see [ETS properties](properties.md).</span></span>

## <a name="ets-methods"></a><span data-ttu-id="6f4ed-123">ETS 方法</span><span class="sxs-lookup"><span data-stu-id="6f4ed-123">ETS methods</span></span>

<span data-ttu-id="6f4ed-124">ETS 方法是可採用引數、可能會傳回結果，且不能出現在運算式左側的成員。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-124">ETS methods are members that can take arguments, may return results, and cannot appear on the left-hand side of an expression.</span></span> <span data-ttu-id="6f4ed-125">它們包含程式碼方法、PowerShell 方法和腳本方法。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-125">They include code methods, PowerShell methods, and script methods.</span></span>
<span data-ttu-id="6f4ed-126">如需這些類型之方法的詳細資訊，請參閱 [ETS 方法](methods.md)。</span><span class="sxs-lookup"><span data-stu-id="6f4ed-126">For more information about these types of methods, see [ETS methods](methods.md).</span></span>
