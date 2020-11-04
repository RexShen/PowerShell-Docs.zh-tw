---
description: 介紹可使用腳本建立 Cmdlet 的 advanced 函數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced
ms.openlocfilehash: 36b354e813c60208960f4cfb826ef0db81435c77
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206623"
---
# <a name="about-functions-advanced"></a><span data-ttu-id="b5959-104">關於函式 Advanced</span><span class="sxs-lookup"><span data-stu-id="b5959-104">About Functions Advanced</span></span>

## <a name="short-description"></a><span data-ttu-id="b5959-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="b5959-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="b5959-106">介紹可使用腳本建立 Cmdlet 的 advanced 函數。</span><span class="sxs-lookup"><span data-stu-id="b5959-106">Introduces advanced functions that are a way to create cmdlets using scripts.</span></span>

## <a name="long-description"></a><span data-ttu-id="b5959-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="b5959-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="b5959-108">Cmdlet 是參與 PowerShell 管線語義的單一命令。</span><span class="sxs-lookup"><span data-stu-id="b5959-108">A cmdlet is a single command that participates in the pipeline semantics of PowerShell.</span></span> <span data-ttu-id="b5959-109">這包括二元 Cmdlet、advanced script 函數、CDXML 和工作流程。</span><span class="sxs-lookup"><span data-stu-id="b5959-109">This includes binary cmdlets, advanced script functions, CDXML, and Workflows.</span></span>

<span data-ttu-id="b5959-110">Advanced 函數可讓您建立以 PowerShell 函數撰寫的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b5959-110">Advanced functions allow you create cmdlets that are written as a PowerShell function.</span></span> <span data-ttu-id="b5959-111">Advanced 函數可讓您更輕鬆地建立 Cmdlet，而不需要撰寫和編譯二進位 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b5959-111">Advanced functions make it easier to create cmdlets without having to write and compile a binary cmdlet.</span></span> <span data-ttu-id="b5959-112">二元 Cmdlet 是以 .NET 語言（如 c #）撰寫的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="b5959-112">Binary cmdlets are .NET classes that are written in a .NET language such as C#.</span></span>

<span data-ttu-id="b5959-113">Advanced 函數會使用 `CmdletBinding` 屬性，將其識別為函式，如同 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b5959-113">Advanced functions use the `CmdletBinding` attribute to identify them as functions that act like cmdlets.</span></span> <span data-ttu-id="b5959-114">`CmdletBinding`屬性類似于編譯的 Cmdlet 類別中用來將類別識別為 Cmdlet 的 Cmdlet 屬性。</span><span class="sxs-lookup"><span data-stu-id="b5959-114">The `CmdletBinding` attribute is similar to the Cmdlet attribute that is used in compiled cmdlet classes to identify the class as a cmdlet.</span></span> <span data-ttu-id="b5959-115">如需此屬性的詳細資訊，請參閱 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)。</span><span class="sxs-lookup"><span data-stu-id="b5959-115">For more information about this attribute, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="b5959-116">下列範例顯示接受名稱的函式，然後使用所提供的名稱來列印問候語。</span><span class="sxs-lookup"><span data-stu-id="b5959-116">The following example shows a function that accepts a name and then prints a greeting using the supplied name.</span></span> <span data-ttu-id="b5959-117">另請注意，此函式會定義包含動詞的名稱 (傳送) 和名詞 (問候) 組，例如已編譯 Cmdlet 的動詞-名詞配對。</span><span class="sxs-lookup"><span data-stu-id="b5959-117">Also notice that this function defines a name that includes a verb (Send) and noun (Greeting) pair like the verb-noun pair of a compiled cmdlet.</span></span> <span data-ttu-id="b5959-118">不過，函式不需要具有動詞-名詞名稱。</span><span class="sxs-lookup"><span data-stu-id="b5959-118">However, functions are not required to have a verb-noun name.</span></span>

```powershell
function Send-Greeting
{
    [CmdletBinding()]
    Param(
        [Parameter(Mandatory=$true)]
        [string] $Name
    )

    Process
    {
        Write-Host ("Hello " + $Name + "!")
    }
}
```

<span data-ttu-id="b5959-119">函數的參數是使用參數屬性來宣告。</span><span class="sxs-lookup"><span data-stu-id="b5959-119">The parameters of the function are declared by using the Parameter attribute.</span></span>
<span data-ttu-id="b5959-120">這個屬性可以單獨使用，也可以與 Alias 屬性或其他數個參數驗證屬性結合使用。</span><span class="sxs-lookup"><span data-stu-id="b5959-120">This attribute can be used alone, or it can be combined with the Alias attribute or with several other parameter validation attributes.</span></span> <span data-ttu-id="b5959-121">如需如何宣告參數的詳細資訊 (包括在執行時間) 加入的動態參數，請參閱 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b5959-121">For more information about how to declare parameters (including dynamic parameters that are added at runtime), see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

<span data-ttu-id="b5959-122">先前函式的實際工作是在進程區塊中執行，這相當於編譯的 Cmdlet 用來處理傳遞給 Cmdlet 之資料的 ProcessingRecord 方法。</span><span class="sxs-lookup"><span data-stu-id="b5959-122">The actual work of the previous function is performed in the Process block, which is equivalent to the ProcessingRecord method that is used by compiled cmdlets to process the data that is passed to the cmdlet.</span></span> <span data-ttu-id="b5959-123">此區塊以及開始和結束區塊將在 [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) 主題中說明。</span><span class="sxs-lookup"><span data-stu-id="b5959-123">This block, along with the Begin and End blocks, is described in the [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) topic.</span></span>

<span data-ttu-id="b5959-124">Advanced 函式與編譯的 Cmdlet 有下列不同之處：</span><span class="sxs-lookup"><span data-stu-id="b5959-124">Advanced functions differ from compiled cmdlets in the following ways:</span></span>

- <span data-ttu-id="b5959-125">當字串陣列系結至布林值參數時，Advanced 函數參數系結不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b5959-125">Advanced function parameter binding does not throw an exception when an array of strings is bound to a Boolean parameter.</span></span>
- <span data-ttu-id="b5959-126">ValidateSet 屬性和 ValidatePattern 屬性無法傳遞具名引數。</span><span class="sxs-lookup"><span data-stu-id="b5959-126">The ValidateSet attribute and the ValidatePattern attribute cannot pass named parameters.</span></span>
- <span data-ttu-id="b5959-127">Advanced 函數不能用在交易中。</span><span class="sxs-lookup"><span data-stu-id="b5959-127">Advanced functions cannot be used in transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5959-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5959-128">SEE ALSO</span></span>

[<span data-ttu-id="b5959-129">about_Functions</span><span class="sxs-lookup"><span data-stu-id="b5959-129">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="b5959-130">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="b5959-130">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="b5959-131">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="b5959-131">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="b5959-132">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="b5959-132">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="b5959-133">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="b5959-133">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)