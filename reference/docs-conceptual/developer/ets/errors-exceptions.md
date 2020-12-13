---
ms.date: 07/09/2020
ms.topic: reference
title: 擴充類型系統中的錯誤和例外狀況
description: 擴充類型系統中的錯誤和例外狀況
ms.openlocfilehash: 295c16ad9abb67b0c4967bf32125bfc7ee0a35da
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652478"
---
# <a name="errors-and-exceptions-in-the-extended-type-system"></a><span data-ttu-id="42046-103">擴充類型系統中的錯誤和例外狀況</span><span class="sxs-lookup"><span data-stu-id="42046-103">Errors and exceptions in the Extended Type System</span></span>

<span data-ttu-id="42046-104">在初始化類型資料時，以及存取 **PSObject** 物件的成員或使用其中一個公用程式類別（例如 **languageprimitives.physicalequality**）時，ETS 中可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="42046-104">Errors can occur in ETS during the initialization of type data and when accessing a member of an **PSObject** object or using one of the utility classes such as **LanguagePrimitives**.</span></span>

## <a name="runtime-errors"></a><span data-ttu-id="42046-105">執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="42046-105">Runtime errors</span></span>

<span data-ttu-id="42046-106">除了一個例外狀況，轉換時，在執行時間期間從 ETS 擲回的所有例外狀況都是 **ExtendedTypeSystemException** 例外狀況或衍生自 **ExtendedTypeSystemException** 類別的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42046-106">With one exception, when casting, all exceptions thrown from ETS during runtime are either an **ExtendedTypeSystemException** exception or an exception derived from the **ExtendedTypeSystemException** class.</span></span> <span data-ttu-id="42046-107">這可讓腳本開發人員使用其腳本中的語句來攔截這些例外狀況 `Trap` 。</span><span class="sxs-lookup"><span data-stu-id="42046-107">This allows script developers to trap these exceptions using the `Trap` statement in their script.</span></span>

## <a name="errors-getting-member-values"></a><span data-ttu-id="42046-108">取得成員值時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="42046-108">Errors getting member values</span></span>

<span data-ttu-id="42046-109">取得 ETS 成員的值時所發生的所有錯誤 (屬性、方法或參數化屬性) 會導致擲回 **GetValueException** 或 **GetValueInvocationException** 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42046-109">All errors that occur when getting the value of an ETS member (property, method, or parameterized property) cause a **GetValueException** or **GetValueInvocationException** exception to be thrown.</span></span>
<span data-ttu-id="42046-110">當 ETS 辨識出發生錯誤時，就會擲回 **GetValueException** 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42046-110">When ETS recognizes that an error occurred a **GetValueException** exception is thrown.</span></span> <span data-ttu-id="42046-111">當參考成員的基礎 getter 辨識出發生錯誤時，會擲回 **GetValueInvocationException** 例外狀況，而不一定會包含造成 get 調用錯誤的內部例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42046-111">When the underlying getter of a referenced member recognizes that an error occurred, a **GetValueInvocationException** exception is thrown that may or may not include the inner exception that caused the get invocation error.</span></span>

## <a name="errors-setting-member-values"></a><span data-ttu-id="42046-112">設定成員值時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="42046-112">Errors setting member values</span></span>

<span data-ttu-id="42046-113">當設定 ETS 屬性的值時，所發生的所有錯誤都會擲回 **SetValueException** 或 **SetValueInvocationException** 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42046-113">All errors that occur when setting the value of an ETS property cause a **SetValueException** or **SetValueInvocationException** exception to be thrown.</span></span> <span data-ttu-id="42046-114">當 ETS 辨識出發生錯誤時，就會擲回 **SetValueException** 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42046-114">When ETS recognizes that an error occurred a **SetValueException** exception is thrown.</span></span> <span data-ttu-id="42046-115">當參考屬性的基礎 setter 辨識出發生錯誤時，就會擲回 **SetValueInvocationException** 例外狀況，而不一定會包含造成集合調用錯誤的內部例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42046-115">When the underlying setter of a referenced property recognizes that an error occurred, a **SetValueInvocationException** exception is thrown that may or may not include the inner exception that caused the set invocation error.</span></span>

## <a name="errors-invoking-a-method"></a><span data-ttu-id="42046-116">叫用方法時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="42046-116">Errors invoking a method</span></span>

<span data-ttu-id="42046-117">叫用 ETS 方法時所發生的所有錯誤都會擲回 **MethodException** 或 **MethodInvocationException** 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42046-117">All errors that occur when invoking an ETS method cause a **MethodException** or **MethodInvocationException** exception to be thrown.</span></span> <span data-ttu-id="42046-118">當 ETS 辨識出發生錯誤時，就會擲回 **MethodException** 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42046-118">When ETS recognizes that an error occurred a **MethodException** exception is thrown.</span></span> <span data-ttu-id="42046-119">當參考的方法辨識出發生錯誤時，就會擲回 **MethodInvocationException** 例外狀況，而不一定會包含導致叫用錯誤的內部例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42046-119">When the referenced method recognizes that an error occurred, a **MethodInvocationException** exception is thrown that may or may not include the inner exception that caused the invocation error.</span></span>

## <a name="casting-errors"></a><span data-ttu-id="42046-120">轉換錯誤</span><span class="sxs-lookup"><span data-stu-id="42046-120">Casting errors</span></span>

<span data-ttu-id="42046-121">嘗試不正確轉換時，會擲回 **PSInvalidCastException** 。</span><span class="sxs-lookup"><span data-stu-id="42046-121">When an invalid cast is attempted, an **PSInvalidCastException** is thrown.</span></span> <span data-ttu-id="42046-122">因為這個例外狀況是衍生自 **InvalidCastException**，所以無法從腳本中直接將它捕捉。</span><span class="sxs-lookup"><span data-stu-id="42046-122">Because this exception derives from **System.InvalidCastException**, it is not able to be directly trapped from script.</span></span> <span data-ttu-id="42046-123">請注意，嘗試轉換的實體需要將 **PSInvalidCastException** 包裝在 **PSRuntimeException** 中，如此腳本才能將其進行可捕獲。</span><span class="sxs-lookup"><span data-stu-id="42046-123">Be aware that the entity attempting the cast would need to wrap **PSInvalidCastException** in an **PSRuntimeException** for this to be trappable by scripts.</span></span> <span data-ttu-id="42046-124">如果嘗試設定 **PSPropertySet**、 **PSMemberSet**、 **PSMethodInfo** 或 **ReadOnlyPSMemberInfoCollection ' 1** 的成員值，則會擲回 **NotSupportedException** 。</span><span class="sxs-lookup"><span data-stu-id="42046-124">If an attempt is made to set the value of an **PSPropertySet**, **PSMemberSet**, **PSMethodInfo**, or a member of the **ReadOnlyPSMemberInfoCollection\`1**, a **NotSupportedException** is thrown.</span></span>

## <a name="common-runtime-errors"></a><span data-ttu-id="42046-125">常見的執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="42046-125">Common runtime errors</span></span>

<span data-ttu-id="42046-126">任何其他發生的常見執行階段錯誤都屬於類型 **ExtendedTypeSystemException** 例外狀況，而且沒有其他特定的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="42046-126">Any other common runtime errors that occur are of type **ExtendedTypeSystemException** exception with no additional specific exception types.</span></span>

## <a name="initialization-errors"></a><span data-ttu-id="42046-127">初始化錯誤</span><span class="sxs-lookup"><span data-stu-id="42046-127">Initialization errors</span></span>

<span data-ttu-id="42046-128">初始化時可能會發生錯誤 `types.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="42046-128">Errors may occur when initializing `types.ps1xml`.</span></span> <span data-ttu-id="42046-129">一般而言，這些錯誤會在 PowerShell 執行時間啟動時顯示。</span><span class="sxs-lookup"><span data-stu-id="42046-129">Typically, these errors are displayed when the PowerShell runtime starts.</span></span> <span data-ttu-id="42046-130">不過，它們也可以在載入模組時顯示。</span><span class="sxs-lookup"><span data-stu-id="42046-130">However, they can also be displayed when a module is loaded.</span></span>
