---
title: 擴充類型系統中的錯誤和例外狀況
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 0e0b158e51d15db266415fb1ea6bb16fba319e62
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217959"
---
# <a name="errors-and-exceptions-in-the-extended-type-system"></a><span data-ttu-id="d4c3f-102">擴充類型系統中的錯誤和例外狀況</span><span class="sxs-lookup"><span data-stu-id="d4c3f-102">Errors and exceptions in the Extended Type System</span></span>

<span data-ttu-id="d4c3f-103">在初始化類型資料時，以及存取**PSObject**物件的成員或使用其中一個公用程式類別（例如**languageprimitives.physicalequality**）時，ETS 可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-103">Errors can occur in ETS during the initialization of type data and when accessing a member of an **PSObject** object or using one of the utility classes such as **LanguagePrimitives**.</span></span>

## <a name="runtime-errors"></a><span data-ttu-id="d4c3f-104">執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="d4c3f-104">Runtime errors</span></span>

<span data-ttu-id="d4c3f-105">有一個例外狀況，在轉換時，在執行時間期間從 ETS 擲回的所有例外狀況都是**ExtendedTypeSystemException**例外狀況或衍生自**ExtendedTypeSystemException**類別的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-105">With one exception, when casting, all exceptions thrown from ETS during runtime are either an **ExtendedTypeSystemException** exception or an exception derived from the **ExtendedTypeSystemException** class.</span></span> <span data-ttu-id="d4c3f-106">這可讓腳本開發人員使用其腳本中的語句來攔截這些例外狀況 `Trap` 。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-106">This allows script developers to trap these exceptions using the `Trap` statement in their script.</span></span>

## <a name="errors-getting-member-values"></a><span data-ttu-id="d4c3f-107">取得成員值時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="d4c3f-107">Errors getting member values</span></span>

<span data-ttu-id="d4c3f-108">取得 ETS 成員的值 (屬性、方法或參數化屬性時，所發生的所有錯誤) 會擲回**GetValueException**或**GetValueInvocationException**例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-108">All errors that occur when getting the value of an ETS member (property, method, or parameterized property) cause a **GetValueException** or **GetValueInvocationException** exception to be thrown.</span></span>
<span data-ttu-id="d4c3f-109">當 ETS 辨識出錯誤發生時，就會擲回**GetValueException**例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-109">When ETS recognizes that an error occurred a **GetValueException** exception is thrown.</span></span> <span data-ttu-id="d4c3f-110">當參考成員的基礎 getter 辨識出錯誤時，會擲回**GetValueInvocationException**例外狀況，而不一定會包含造成 get 調用錯誤的內部例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-110">When the underlying getter of a referenced member recognizes that an error occurred, a **GetValueInvocationException** exception is thrown that may or may not include the inner exception that caused the get invocation error.</span></span>

## <a name="errors-setting-member-values"></a><span data-ttu-id="d4c3f-111">設定成員值時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="d4c3f-111">Errors setting member values</span></span>

<span data-ttu-id="d4c3f-112">設定 ETS 屬性的值時所發生的所有錯誤都會導致擲回**SetValueException**或**SetValueInvocationException**例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-112">All errors that occur when setting the value of an ETS property cause a **SetValueException** or **SetValueInvocationException** exception to be thrown.</span></span> <span data-ttu-id="d4c3f-113">當 ETS 辨識出錯誤發生時，就會擲回**SetValueException**例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-113">When ETS recognizes that an error occurred a **SetValueException** exception is thrown.</span></span> <span data-ttu-id="d4c3f-114">當所參考屬性的基礎 setter 發現發生錯誤時，會擲回**SetValueInvocationException**例外狀況，而不一定會包含造成設定調用錯誤的內部例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-114">When the underlying setter of a referenced property recognizes that an error occurred, a **SetValueInvocationException** exception is thrown that may or may not include the inner exception that caused the set invocation error.</span></span>

## <a name="errors-invoking-a-method"></a><span data-ttu-id="d4c3f-115">叫用方法時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="d4c3f-115">Errors invoking a method</span></span>

<span data-ttu-id="d4c3f-116">叫用 ETS 方法時所發生的所有錯誤都會導致擲回**MethodException**或**MethodInvocationException**例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-116">All errors that occur when invoking an ETS method cause a **MethodException** or **MethodInvocationException** exception to be thrown.</span></span> <span data-ttu-id="d4c3f-117">當 ETS 辨識出錯誤發生時，就會擲回**MethodException**例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-117">When ETS recognizes that an error occurred a **MethodException** exception is thrown.</span></span> <span data-ttu-id="d4c3f-118">當參考的方法辨識出錯誤時，會擲回**MethodInvocationException**例外狀況，而不一定會包含造成調用錯誤的內部例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-118">When the referenced method recognizes that an error occurred, a **MethodInvocationException** exception is thrown that may or may not include the inner exception that caused the invocation error.</span></span>

## <a name="casting-errors"></a><span data-ttu-id="d4c3f-119">轉換錯誤</span><span class="sxs-lookup"><span data-stu-id="d4c3f-119">Casting errors</span></span>

<span data-ttu-id="d4c3f-120">當嘗試不正確轉換時，就會擲回**PSInvalidCastException** 。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-120">When an invalid cast is attempted, an **PSInvalidCastException** is thrown.</span></span> <span data-ttu-id="d4c3f-121">因為此例外狀況衍生自**InvalidCastException**，所以無法直接從腳本中攔截。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-121">Because this exception derives from **System.InvalidCastException**, it is not able to be directly trapped from script.</span></span> <span data-ttu-id="d4c3f-122">請注意，嘗試轉換的實體必須將**PSInvalidCastException**包裝在**PSRuntimeException**中，才能由腳本加以捕獲。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-122">Be aware that the entity attempting the cast would need to wrap **PSInvalidCastException** in an **PSRuntimeException** for this to be trappable by scripts.</span></span> <span data-ttu-id="d4c3f-123">如果嘗試設定**PSPropertySet**、 **PSMemberSet**、 **PSMethodInfo**或**ReadOnlyPSMemberInfoCollection ' 1**成員的值，則會擲回**NotSupportedException** 。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-123">If an attempt is made to set the value of an **PSPropertySet**, **PSMemberSet**, **PSMethodInfo**, or a member of the **ReadOnlyPSMemberInfoCollection\`1**, a **NotSupportedException** is thrown.</span></span>

## <a name="common-runtime-errors"></a><span data-ttu-id="d4c3f-124">常見的執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="d4c3f-124">Common runtime errors</span></span>

<span data-ttu-id="d4c3f-125">發生的任何其他常見執行階段錯誤都屬於類型**ExtendedTypeSystemException**例外狀況，且沒有其他特定的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-125">Any other common runtime errors that occur are of type **ExtendedTypeSystemException** exception with no additional specific exception types.</span></span>

## <a name="initialization-errors"></a><span data-ttu-id="d4c3f-126">初始化錯誤</span><span class="sxs-lookup"><span data-stu-id="d4c3f-126">Initialization errors</span></span>

<span data-ttu-id="d4c3f-127">初始化時，可能會發生錯誤 `types.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-127">Errors may occur when initializing `types.ps1xml`.</span></span> <span data-ttu-id="d4c3f-128">這些錯誤通常會在 PowerShell 執行時間啟動時顯示。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-128">Typically, these errors are displayed when the PowerShell runtime starts.</span></span> <span data-ttu-id="d4c3f-129">不過，也可以在載入模組時顯示。</span><span class="sxs-lookup"><span data-stu-id="d4c3f-129">However, they can also be displayed when a module is loaded.</span></span>
