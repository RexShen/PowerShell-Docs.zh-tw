---
ms.date: 07/09/2020
ms.topic: reference
title: 擴充類型系統類別方法
description: 擴充類型系統類別方法
ms.openlocfilehash: b53604a36e0a0c3587f345262e8f274e3a2c4859
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660375"
---
# <a name="ets-class-methods"></a><span data-ttu-id="bed27-103">ETS 類別方法</span><span class="sxs-lookup"><span data-stu-id="bed27-103">ETS class methods</span></span>

<span data-ttu-id="bed27-104">ETS 方法是可採用引數、可能會傳回結果，且不能出現在運算式左側的成員。</span><span class="sxs-lookup"><span data-stu-id="bed27-104">ETS methods are members that can take arguments, may return results, and cannot appear on the left-hand side of an expression.</span></span> <span data-ttu-id="bed27-105">ETS 中可用的方法包括程式碼、Windows PowerShell 和腳本方法。</span><span class="sxs-lookup"><span data-stu-id="bed27-105">The methods that are available within ETS include code, Windows PowerShell, and script methods.</span></span>

> [!NOTE]
> <span data-ttu-id="bed27-106">在腳本中，方法是使用與其他成員相同的語法來存取，而在方法名稱的結尾加上括弧。</span><span class="sxs-lookup"><span data-stu-id="bed27-106">From scripts, methods are accessed using the same syntax as other members with the addition of parenthesis at the end of the method name.</span></span>

## <a name="code-methods"></a><span data-ttu-id="bed27-107">程式碼方法</span><span class="sxs-lookup"><span data-stu-id="bed27-107">Code Methods</span></span>

<span data-ttu-id="bed27-108">程式碼方法是以 CLR 語言定義的擴充成員。</span><span class="sxs-lookup"><span data-stu-id="bed27-108">A code method is an extended member that is defined in a CLR language.</span></span> <span data-ttu-id="bed27-109">它會針對基底物件上定義的方法提供類似的功能。不過，程式碼方法可能會動態新增到 **PSObject** 物件。</span><span class="sxs-lookup"><span data-stu-id="bed27-109">It provides similar functionality to a method defined on a base object; however, a code method may be added dynamically to an **PSObject** object.</span></span> <span data-ttu-id="bed27-110">為了讓程式碼方法可供使用，開發人員必須以某些 CLR 語言撰寫屬性、編譯和傳送結果元件。</span><span class="sxs-lookup"><span data-stu-id="bed27-110">In order for a code method to become available, a developer must write the property in some CLR language, compile, and ship the resultant assembly.</span></span> <span data-ttu-id="bed27-111">此元件必須可在需要程式碼方法的運行空間中使用。</span><span class="sxs-lookup"><span data-stu-id="bed27-111">This assembly must be available in the runspace where the code method is desired.</span></span> <span data-ttu-id="bed27-112">請注意，程式碼方法的執行必須具備執行緒安全。</span><span class="sxs-lookup"><span data-stu-id="bed27-112">Be aware that a code method implementation must be thread safe.</span></span> <span data-ttu-id="bed27-113">這些方法的存取是透過提供下列公用方法和屬性的 [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) 物件來完成。</span><span class="sxs-lookup"><span data-stu-id="bed27-113">Access to these methods is done through [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) objects that provides the following public methods and properties.</span></span>

- <span data-ttu-id="bed27-114">`PSCodeMethod.Copy` 方法：建立 **PSCodeMethod** 物件的完整複本。</span><span class="sxs-lookup"><span data-stu-id="bed27-114">`PSCodeMethod.Copy` method: Makes an exact copy of the **PSCodeMethod** object.</span></span>
- <span data-ttu-id="bed27-115">`PSCodeMethod.Invoke(System.Object[])` 方法：叫用基礎程式碼方法。</span><span class="sxs-lookup"><span data-stu-id="bed27-115">`PSCodeMethod.Invoke(System.Object[])` method: Invokes the underlying code method.</span></span>
- <span data-ttu-id="bed27-116">`PSCodeMethod.ToString` 方法：將 **PSCodeMethod** 物件轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="bed27-116">`PSCodeMethod.ToString` method: Converts the **PSCodeMethod** object to a string.</span></span>
- <span data-ttu-id="bed27-117">`PSCodeMethod.CodeReference` 屬性：取得程式碼方法所依據的基礎方法。</span><span class="sxs-lookup"><span data-stu-id="bed27-117">`PSCodeMethod.CodeReference` property: Gets the underlying method that the code method is based on.</span></span>
- <span data-ttu-id="bed27-118">**PSMemberInfo. IsInstance** 屬性：取得指出成員來源的 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="bed27-118">**PSMemberInfo.IsInstance** property: Gets a **Boolean** value that indicates the source of the member.</span></span>
- <span data-ttu-id="bed27-119">**PSCodeMethod. MemberType** 屬性：取得將此方法識別為程式碼方法的 **psmembertypes. CodeMethod** 列舉常數。</span><span class="sxs-lookup"><span data-stu-id="bed27-119">**PSCodeMethod.MemberType** property: Gets an **PSMemberTypes.CodeMethod** enumeration constant that identifies this method as a code method.</span></span>
- <span data-ttu-id="bed27-120">**PSMemberInfo.Name** 屬性：取得基礎程式碼方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="bed27-120">**PSMemberInfo.Name** property: Gets the name of the underlying code method.</span></span>
- <span data-ttu-id="bed27-121">**PSCodeMethod. OverloadDefinitions** 屬性：取得基礎程式碼方法的所有多載的定義。</span><span class="sxs-lookup"><span data-stu-id="bed27-121">**PSCodeMethod.OverloadDefinitions** property: Gets a definition of all the overloads of the underlying code method.</span></span>
- <span data-ttu-id="bed27-122">**PSCodeMethod. TypeNameOfValue** 屬性：取得程式碼方法的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="bed27-122">**PSCodeMethod.TypeNameOfValue** property: Gets the full name of the code method.</span></span>
- <span data-ttu-id="bed27-123">**PSMemberInfo。 Value** 屬性：取得 **PSCodeMethod** 物件。</span><span class="sxs-lookup"><span data-stu-id="bed27-123">**PSMemberInfo.Value** property: Gets the **PSCodeMethod** object.</span></span>

## <a name="windows-powershell-methods"></a><span data-ttu-id="bed27-124">Windows PowerShell 方法</span><span class="sxs-lookup"><span data-stu-id="bed27-124">Windows PowerShell Methods</span></span>

<span data-ttu-id="bed27-125">PowerShell 方法是在基底物件上定義或可透過介面卡存取的 CLR 方法。</span><span class="sxs-lookup"><span data-stu-id="bed27-125">A PowerShell method is a CLR method defined on the base object or is made accessible through an adapter.</span></span> <span data-ttu-id="bed27-126">這些方法的存取是透過提供下列公用方法和屬性的 **PSMethod** 物件來完成。</span><span class="sxs-lookup"><span data-stu-id="bed27-126">Access to these methods is done through **PSMethod** objects that provides the following public methods and properties.</span></span>

- <span data-ttu-id="bed27-127">`PSMethod.Copy` 方法：建立 **PSMethod** 物件的完整複本。</span><span class="sxs-lookup"><span data-stu-id="bed27-127">`PSMethod.Copy` method: Makes an exact copy of the **PSMethod** object.</span></span>
- <span data-ttu-id="bed27-128">`PSMethod.Invoke(System.Object[])` 方法：叫用基礎方法。</span><span class="sxs-lookup"><span data-stu-id="bed27-128">`PSMethod.Invoke(System.Object[])` method: Invokes the underlying method.</span></span>
- <span data-ttu-id="bed27-129">`PSMethod.ToString` 方法：將 **PSMethod** 物件轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="bed27-129">`PSMethod.ToString` method: Converts the **PSMethod** object to a string.</span></span>
- <span data-ttu-id="bed27-130">**PSMemberInfo. IsInstance** 屬性：取得指出成員來源的 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="bed27-130">**PSMemberInfo.IsInstance** property: Gets a **Boolean** value that indicates the source of the member.</span></span>
- <span data-ttu-id="bed27-131">**PSMethod. MemberType** 屬性：取得將此方法識別為 PowerShell 方法的 **psmembertypes. 方法** 列舉常數。</span><span class="sxs-lookup"><span data-stu-id="bed27-131">**PSMethod.MemberType** property: Gets an **PSMemberTypes.Method** enumeration constant that identifies this method as a PowerShell method.</span></span>
- <span data-ttu-id="bed27-132">**PSMemberInfo.Name** 屬性：取得基礎方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="bed27-132">**PSMemberInfo.Name** property: Gets the name of the underlying method.</span></span>
- <span data-ttu-id="bed27-133">**PSMethod. OverloadDefinitions** 屬性：取得基礎方法的所有多載的定義。</span><span class="sxs-lookup"><span data-stu-id="bed27-133">**PSMethod.OverloadDefinitions** property: Gets the definitions of all the overloads of the underlying method.</span></span>
- <span data-ttu-id="bed27-134">**PSMethod. TypeNameOfValue** 屬性：取得這個方法的 ETS 型別。</span><span class="sxs-lookup"><span data-stu-id="bed27-134">**PSMethod.TypeNameOfValue** property: Gets the ETS type of this method.</span></span>
- <span data-ttu-id="bed27-135">**PSMemberInfo。 Value** 屬性：取得 **PSMethod** 物件。</span><span class="sxs-lookup"><span data-stu-id="bed27-135">**PSMemberInfo.Value** property: Gets the **PSMethod** object.</span></span>

## <a name="script-methods"></a><span data-ttu-id="bed27-136">腳本方法</span><span class="sxs-lookup"><span data-stu-id="bed27-136">Script Methods</span></span>

<span data-ttu-id="bed27-137">腳本方法是以 PowerShell 語言定義的擴充成員。</span><span class="sxs-lookup"><span data-stu-id="bed27-137">A script method is an extended member that is defined in the PowerShell language.</span></span> <span data-ttu-id="bed27-138">它會針對基底物件上定義的方法提供類似的功能。不過，您可以將腳本方法動態新增到 **PSObject** 物件。</span><span class="sxs-lookup"><span data-stu-id="bed27-138">It provides similar functionality to a method defined on a base object; however, a script method may be added dynamically to an **PSObject** object.</span></span> <span data-ttu-id="bed27-139">這些方法的存取是透過提供下列公用方法和屬性的 [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) 物件來完成。</span><span class="sxs-lookup"><span data-stu-id="bed27-139">Access to these methods is done through [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) objects that provides the following public methods and properties.</span></span>

- <span data-ttu-id="bed27-140">`PSScriptMethod.Copy` 方法：建立 **PSScriptMethod** 物件的完整複本。</span><span class="sxs-lookup"><span data-stu-id="bed27-140">`PSScriptMethod.Copy` method: Makes an exact copy of the **PSScriptMethod** object.</span></span>
- <span data-ttu-id="bed27-141">`PSScriptMethod.Invoke(System.Object[])` 方法：叫用基礎腳本方法。</span><span class="sxs-lookup"><span data-stu-id="bed27-141">`PSScriptMethod.Invoke(System.Object[])` method: Invokes the underlying script method.</span></span>
- <span data-ttu-id="bed27-142">`PSScriptMethod.ToString` 方法：將 **PSScriptMethod** 物件轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="bed27-142">`PSScriptMethod.ToString` method: Converts the **PSScriptMethod** object to a string.</span></span>
- <span data-ttu-id="bed27-143">**PSMemberInfo. IsInstance** 屬性：取得指出成員來源的 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="bed27-143">**PSMemberInfo.IsInstance** property: Gets a **Boolean** value that indicates the source of the member.</span></span>
- <span data-ttu-id="bed27-144">**PSScriptMethod. MemberType** 屬性：取得將這個方法識別為腳本方法的 **psmembertypes. ScriptMethod** 列舉常數。</span><span class="sxs-lookup"><span data-stu-id="bed27-144">**PSScriptMethod.MemberType** property: Gets a **PSMemberTypes.ScriptMethod** enumeration constant that identifies this method as a script method.</span></span>
- <span data-ttu-id="bed27-145">**PSMemberInfo.Name** 屬性：取得基礎程式碼方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="bed27-145">**PSMemberInfo.Name** property: Gets the name of the underlying code method.</span></span>
- <span data-ttu-id="bed27-146">**PSScriptMethod. OverloadDefinitions** 屬性：取得基礎腳本方法的所有多載的定義。</span><span class="sxs-lookup"><span data-stu-id="bed27-146">**PSScriptMethod.OverloadDefinitions** property: Gets the definitions of all the overloads of the underlying script method.</span></span>
- <span data-ttu-id="bed27-147">**PSScriptMethod. TypeNameOfValue** 屬性：取得這個方法的 ETS 型別。</span><span class="sxs-lookup"><span data-stu-id="bed27-147">**PSScriptMethod.TypeNameOfValue** property: Gets the ETS type of this method.</span></span>
- <span data-ttu-id="bed27-148">**PSScriptMethod** 屬性：取得用來叫用方法的腳本。</span><span class="sxs-lookup"><span data-stu-id="bed27-148">**PSScriptMethod.Script** property: Gets the script used to invoke the method.</span></span>
- <span data-ttu-id="bed27-149">**PSMemberInfo。 Value** 屬性：取得 **PSScriptMethod** 物件。</span><span class="sxs-lookup"><span data-stu-id="bed27-149">**PSMemberInfo.Value** property: Gets the **PSScriptMethod** object.</span></span>
