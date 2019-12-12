---
title: 屬性類型 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364577"
---
# <a name="attribute-types"></a><span data-ttu-id="698c6-102">屬性類型</span><span class="sxs-lookup"><span data-stu-id="698c6-102">Attribute Types</span></span>

<span data-ttu-id="698c6-103">Cmdlet 屬性可以依功能分組。</span><span class="sxs-lookup"><span data-stu-id="698c6-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="698c6-104">下列各節描述可用的屬性，並描述叫用屬性時執行時間的功能。</span><span class="sxs-lookup"><span data-stu-id="698c6-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="698c6-105">Cmdlet 屬性</span><span class="sxs-lookup"><span data-stu-id="698c6-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="698c6-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="698c6-106">Cmdlet</span></span>

<span data-ttu-id="698c6-107">將 .NET Framework 類別識別為 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="698c6-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="698c6-108">這是必要的基底屬性。</span><span class="sxs-lookup"><span data-stu-id="698c6-108">This is the required base attribute.</span></span>
<span data-ttu-id="698c6-109">如需詳細資訊，請參閱[Cmdlet 屬性](./cmdlet-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="698c6-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="698c6-110">參數屬性</span><span class="sxs-lookup"><span data-stu-id="698c6-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="698c6-111">參數</span><span class="sxs-lookup"><span data-stu-id="698c6-111">Parameter</span></span>

<span data-ttu-id="698c6-112">將 Cmdlet 類別中的公用屬性識別為 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="698c6-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="698c6-113">如需詳細資訊，請參閱[參數屬性](./parameter-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="698c6-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="698c6-114">別名</span><span class="sxs-lookup"><span data-stu-id="698c6-114">Alias</span></span>

<span data-ttu-id="698c6-115">為參數指定一或多個別名。</span><span class="sxs-lookup"><span data-stu-id="698c6-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="698c6-116">如需詳細資訊，請參閱[Alias 屬性](./alias-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="698c6-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="698c6-117">引數驗證屬性</span><span class="sxs-lookup"><span data-stu-id="698c6-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="698c6-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="698c6-118">ValidateCount</span></span>

<span data-ttu-id="698c6-119">指定 Cmdlet 參數所允許之引數的最小和最大數目。</span><span class="sxs-lookup"><span data-stu-id="698c6-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="698c6-120">如需詳細資訊，請參閱[ValidateCount 屬性](./validatecount-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="698c6-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="698c6-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="698c6-121">ValidateLength</span></span>

<span data-ttu-id="698c6-122">指定 Cmdlet 參數引數的最小和最大字元數。</span><span class="sxs-lookup"><span data-stu-id="698c6-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="698c6-123">如需詳細資訊，請參閱[ValidateLength 屬性](./validatelength-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="698c6-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="698c6-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="698c6-124">ValidatePattern</span></span>

<span data-ttu-id="698c6-125">指定 Cmdlet 參數引數必須符合的正則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="698c6-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="698c6-126">如需詳細資訊，請參閱[ValidatePattern 屬性](./validatepattern-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="698c6-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="698c6-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="698c6-127">ValidateRange</span></span>

<span data-ttu-id="698c6-128">指定 Cmdlet 參數引數的最小和最大值。</span><span class="sxs-lookup"><span data-stu-id="698c6-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="698c6-129">如需詳細資訊，請參閱[ValidateRange 屬性](./validaterange-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="698c6-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="698c6-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="698c6-130">ValidateSet</span></span>

<span data-ttu-id="698c6-131">為 Cmdlet 參數引數指定一組有效的值。</span><span class="sxs-lookup"><span data-stu-id="698c6-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="698c6-132">如需詳細資訊，請參閱[ValidateSet 屬性](./validateset-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="698c6-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="698c6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="698c6-133">See Also</span></span>

[<span data-ttu-id="698c6-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="698c6-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
