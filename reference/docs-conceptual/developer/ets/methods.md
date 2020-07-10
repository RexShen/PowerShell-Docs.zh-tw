---
title: 擴充類型系統類別方法
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 97c11093d2faeb2a73b349c479d6de34ae2ea788
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217919"
---
# <a name="ets-class-methods"></a><span data-ttu-id="7224a-102">ETS 類別方法</span><span class="sxs-lookup"><span data-stu-id="7224a-102">ETS class methods</span></span>

<span data-ttu-id="7224a-103">ETS 方法是可以接受引數、可能會傳回結果，而且不能出現在運算式左側的成員。</span><span class="sxs-lookup"><span data-stu-id="7224a-103">ETS methods are members that can take arguments, may return results, and cannot appear on the left-hand side of an expression.</span></span> <span data-ttu-id="7224a-104">ETS 內可用的方法包括程式碼、Windows PowerShell 和腳本方法。</span><span class="sxs-lookup"><span data-stu-id="7224a-104">The methods that are available within ETS include code, Windows PowerShell, and script methods.</span></span>

> [!NOTE]
> <span data-ttu-id="7224a-105">在腳本中，方法是使用與其他成員相同的語法來存取，並在方法名稱的結尾加上括弧。</span><span class="sxs-lookup"><span data-stu-id="7224a-105">From scripts, methods are accessed using the same syntax as other members with the addition of parenthesis at the end of the method name.</span></span>

## <a name="code-methods"></a><span data-ttu-id="7224a-106">程式碼方法</span><span class="sxs-lookup"><span data-stu-id="7224a-106">Code Methods</span></span>

<span data-ttu-id="7224a-107">程式碼方法是以 CLR 語言定義的擴充成員。</span><span class="sxs-lookup"><span data-stu-id="7224a-107">A code method is an extended member that is defined in a CLR language.</span></span> <span data-ttu-id="7224a-108">它會針對基底物件上定義的方法提供類似的功能;不過，程式碼方法可能會動態新增至**PSObject**物件。</span><span class="sxs-lookup"><span data-stu-id="7224a-108">It provides similar functionality to a method defined on a base object; however, a code method may be added dynamically to an **PSObject** object.</span></span> <span data-ttu-id="7224a-109">為了讓程式碼方法可供使用，開發人員必須以某種 CLR 語言撰寫屬性、編譯和傳送結果元件。</span><span class="sxs-lookup"><span data-stu-id="7224a-109">In order for a code method to become available, a developer must write the property in some CLR language, compile, and ship the resultant assembly.</span></span> <span data-ttu-id="7224a-110">這個元件必須可在需要程式碼方法的運行時使用。</span><span class="sxs-lookup"><span data-stu-id="7224a-110">This assembly must be available in the runspace where the code method is desired.</span></span> <span data-ttu-id="7224a-111">請注意，程式碼方法的執行必須是安全線程。</span><span class="sxs-lookup"><span data-stu-id="7224a-111">Be aware that a code method implementation must be thread safe.</span></span> <span data-ttu-id="7224a-112">這些方法的存取是透過提供下列公用方法和屬性的[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)物件來完成。</span><span class="sxs-lookup"><span data-stu-id="7224a-112">Access to these methods is done through [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) objects that provides the following public methods and properties.</span></span>

- <span data-ttu-id="7224a-113">`PSCodeMethod.Copy`method：建立**PSCodeMethod**物件的完全相同複本。</span><span class="sxs-lookup"><span data-stu-id="7224a-113">`PSCodeMethod.Copy` method: Makes an exact copy of the **PSCodeMethod** object.</span></span>
- <span data-ttu-id="7224a-114">`PSCodeMethod.Invoke(System.Object[])`method：叫用基礎程式碼方法。</span><span class="sxs-lookup"><span data-stu-id="7224a-114">`PSCodeMethod.Invoke(System.Object[])` method: Invokes the underlying code method.</span></span>
- <span data-ttu-id="7224a-115">`PSCodeMethod.ToString`method：將**PSCodeMethod**物件轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="7224a-115">`PSCodeMethod.ToString` method: Converts the **PSCodeMethod** object to a string.</span></span>
- <span data-ttu-id="7224a-116">`PSCodeMethod.CodeReference`property：取得程式碼方法所依據的基礎方法。</span><span class="sxs-lookup"><span data-stu-id="7224a-116">`PSCodeMethod.CodeReference` property: Gets the underlying method that the code method is based on.</span></span>
- <span data-ttu-id="7224a-117">**PSMemberInfo. IsInstance**屬性：取得指出成員來源的**布林**值。</span><span class="sxs-lookup"><span data-stu-id="7224a-117">**PSMemberInfo.IsInstance** property: Gets a **Boolean** value that indicates the source of the member.</span></span>
- <span data-ttu-id="7224a-118">**PSCodeMethod. MemberType**屬性：取得將此方法識別為程式碼方法的\*\* psmembertypes. CodeMethod\*\*列舉常數。</span><span class="sxs-lookup"><span data-stu-id="7224a-118">**PSCodeMethod.MemberType** property: Gets an **PSMemberTypes.CodeMethod** enumeration constant that identifies this method as a code method.</span></span>
- <span data-ttu-id="7224a-119">**PSMemberInfo.Name**屬性：取得基礎程式碼方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="7224a-119">**PSMemberInfo.Name** property: Gets the name of the underlying code method.</span></span>
- <span data-ttu-id="7224a-120">**PSCodeMethod. OverloadDefinitions**屬性：取得基礎程式碼方法的所有多載的定義。</span><span class="sxs-lookup"><span data-stu-id="7224a-120">**PSCodeMethod.OverloadDefinitions** property: Gets a definition of all the overloads of the underlying code method.</span></span>
- <span data-ttu-id="7224a-121">**PSCodeMethod. TypeNameOfValue**屬性：取得程式碼方法的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="7224a-121">**PSCodeMethod.TypeNameOfValue** property: Gets the full name of the code method.</span></span>
- <span data-ttu-id="7224a-122">**PSMemberInfo**屬性：取得**PSCodeMethod**物件。</span><span class="sxs-lookup"><span data-stu-id="7224a-122">**PSMemberInfo.Value** property: Gets the **PSCodeMethod** object.</span></span>

## <a name="windows-powershell-methods"></a><span data-ttu-id="7224a-123">Windows PowerShell 方法</span><span class="sxs-lookup"><span data-stu-id="7224a-123">Windows PowerShell Methods</span></span>

<span data-ttu-id="7224a-124">PowerShell 方法是在基底物件上定義的 CLR 方法，或透過介面卡來存取。</span><span class="sxs-lookup"><span data-stu-id="7224a-124">A PowerShell method is a CLR method defined on the base object or is made accessible through an adapter.</span></span> <span data-ttu-id="7224a-125">這些方法的存取是透過提供下列公用方法和屬性的**PSMethod**物件來完成。</span><span class="sxs-lookup"><span data-stu-id="7224a-125">Access to these methods is done through **PSMethod** objects that provides the following public methods and properties.</span></span>

- <span data-ttu-id="7224a-126">`PSMethod.Copy`method：建立**PSMethod**物件的完全相同複本。</span><span class="sxs-lookup"><span data-stu-id="7224a-126">`PSMethod.Copy` method: Makes an exact copy of the **PSMethod** object.</span></span>
- <span data-ttu-id="7224a-127">`PSMethod.Invoke(System.Object[])`method：叫用基礎方法。</span><span class="sxs-lookup"><span data-stu-id="7224a-127">`PSMethod.Invoke(System.Object[])` method: Invokes the underlying method.</span></span>
- <span data-ttu-id="7224a-128">`PSMethod.ToString`method：將**PSMethod**物件轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="7224a-128">`PSMethod.ToString` method: Converts the **PSMethod** object to a string.</span></span>
- <span data-ttu-id="7224a-129">**PSMemberInfo. IsInstance**屬性：取得指出成員來源的**布林**值。</span><span class="sxs-lookup"><span data-stu-id="7224a-129">**PSMemberInfo.IsInstance** property: Gets a **Boolean** value that indicates the source of the member.</span></span>
- <span data-ttu-id="7224a-130">**PSMethod. MemberType**屬性：取得將此方法識別為 PowerShell 方法的\*\* psmembertypes\*\*方法列舉常數。</span><span class="sxs-lookup"><span data-stu-id="7224a-130">**PSMethod.MemberType** property: Gets an **PSMemberTypes.Method** enumeration constant that identifies this method as a PowerShell method.</span></span>
- <span data-ttu-id="7224a-131">**PSMemberInfo.Name**屬性：取得基礎方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="7224a-131">**PSMemberInfo.Name** property: Gets the name of the underlying method.</span></span>
- <span data-ttu-id="7224a-132">**PSMethod. OverloadDefinitions**屬性：取得基礎方法之所有多載的定義。</span><span class="sxs-lookup"><span data-stu-id="7224a-132">**PSMethod.OverloadDefinitions** property: Gets the definitions of all the overloads of the underlying method.</span></span>
- <span data-ttu-id="7224a-133">**PSMethod. TypeNameOfValue**屬性：取得這個方法的 ETS 類型。</span><span class="sxs-lookup"><span data-stu-id="7224a-133">**PSMethod.TypeNameOfValue** property: Gets the ETS type of this method.</span></span>
- <span data-ttu-id="7224a-134">**PSMemberInfo**屬性：取得**PSMethod**物件。</span><span class="sxs-lookup"><span data-stu-id="7224a-134">**PSMemberInfo.Value** property: Gets the **PSMethod** object.</span></span>

## <a name="script-methods"></a><span data-ttu-id="7224a-135">腳本方法</span><span class="sxs-lookup"><span data-stu-id="7224a-135">Script Methods</span></span>

<span data-ttu-id="7224a-136">腳本方法是以 PowerShell 語言定義的擴充成員。</span><span class="sxs-lookup"><span data-stu-id="7224a-136">A script method is an extended member that is defined in the PowerShell language.</span></span> <span data-ttu-id="7224a-137">它會針對基底物件上定義的方法提供類似的功能;不過，腳本方法可能會動態新增至**PSObject**物件。</span><span class="sxs-lookup"><span data-stu-id="7224a-137">It provides similar functionality to a method defined on a base object; however, a script method may be added dynamically to an **PSObject** object.</span></span> <span data-ttu-id="7224a-138">這些方法的存取是透過提供下列公用方法和屬性的[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod)物件來完成。</span><span class="sxs-lookup"><span data-stu-id="7224a-138">Access to these methods is done through [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) objects that provides the following public methods and properties.</span></span>

- <span data-ttu-id="7224a-139">`PSScriptMethod.Copy`method：建立**PSScriptMethod**物件的完全相同複本。</span><span class="sxs-lookup"><span data-stu-id="7224a-139">`PSScriptMethod.Copy` method: Makes an exact copy of the **PSScriptMethod** object.</span></span>
- <span data-ttu-id="7224a-140">`PSScriptMethod.Invoke(System.Object[])`method：叫用基礎腳本方法。</span><span class="sxs-lookup"><span data-stu-id="7224a-140">`PSScriptMethod.Invoke(System.Object[])` method: Invokes the underlying script method.</span></span>
- <span data-ttu-id="7224a-141">`PSScriptMethod.ToString`method：將**PSScriptMethod**物件轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="7224a-141">`PSScriptMethod.ToString` method: Converts the **PSScriptMethod** object to a string.</span></span>
- <span data-ttu-id="7224a-142">**PSMemberInfo. IsInstance**屬性：取得指出成員來源的**布林**值。</span><span class="sxs-lookup"><span data-stu-id="7224a-142">**PSMemberInfo.IsInstance** property: Gets a **Boolean** value that indicates the source of the member.</span></span>
- <span data-ttu-id="7224a-143">**PSScriptMethod. MemberType**屬性：取得將此方法識別為腳本方法的\*\* psmembertypes. ScriptMethod\*\*列舉常數。</span><span class="sxs-lookup"><span data-stu-id="7224a-143">**PSScriptMethod.MemberType** property: Gets a **PSMemberTypes.ScriptMethod** enumeration constant that identifies this method as a script method.</span></span>
- <span data-ttu-id="7224a-144">**PSMemberInfo.Name**屬性：取得基礎程式碼方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="7224a-144">**PSMemberInfo.Name** property: Gets the name of the underlying code method.</span></span>
- <span data-ttu-id="7224a-145">**PSScriptMethod. OverloadDefinitions**屬性：取得基礎腳本方法之所有多載的定義。</span><span class="sxs-lookup"><span data-stu-id="7224a-145">**PSScriptMethod.OverloadDefinitions** property: Gets the definitions of all the overloads of the underlying script method.</span></span>
- <span data-ttu-id="7224a-146">**PSScriptMethod. TypeNameOfValue**屬性：取得這個方法的 ETS 類型。</span><span class="sxs-lookup"><span data-stu-id="7224a-146">**PSScriptMethod.TypeNameOfValue** property: Gets the ETS type of this method.</span></span>
- <span data-ttu-id="7224a-147">**PSScriptMethod**屬性：取得用來叫用方法的腳本。</span><span class="sxs-lookup"><span data-stu-id="7224a-147">**PSScriptMethod.Script** property: Gets the script used to invoke the method.</span></span>
- <span data-ttu-id="7224a-148">**PSMemberInfo**屬性：取得**PSScriptMethod**物件。</span><span class="sxs-lookup"><span data-stu-id="7224a-148">**PSMemberInfo.Value** property: Gets the **PSScriptMethod** object.</span></span>
