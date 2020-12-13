---
ms.date: 09/13/2016
ms.topic: reference
title: 屬性類型
description: 屬性類型
ms.openlocfilehash: 65640f2f8449887dedb9fae137eb16b6252f1d57
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667108"
---
# <a name="attribute-types"></a><span data-ttu-id="e104e-103">屬性類型</span><span class="sxs-lookup"><span data-stu-id="e104e-103">Attribute Types</span></span>

<span data-ttu-id="e104e-104">Cmdlet 屬性可以依功能分組。</span><span class="sxs-lookup"><span data-stu-id="e104e-104">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="e104e-105">下列各節描述可用的屬性，並描述叫用屬性時執行時間的功能。</span><span class="sxs-lookup"><span data-stu-id="e104e-105">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="e104e-106">Cmdlet 屬性</span><span class="sxs-lookup"><span data-stu-id="e104e-106">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="e104e-107">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e104e-107">Cmdlet</span></span>

<span data-ttu-id="e104e-108">將 .NET Framework 類別識別為 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e104e-108">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="e104e-109">這是必要的基底屬性。</span><span class="sxs-lookup"><span data-stu-id="e104e-109">This is the required base attribute.</span></span>
<span data-ttu-id="e104e-110">如需詳細資訊，請參閱 [Cmdlet 屬性聲明](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="e104e-110">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="e104e-111">參數屬性</span><span class="sxs-lookup"><span data-stu-id="e104e-111">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="e104e-112">參數</span><span class="sxs-lookup"><span data-stu-id="e104e-112">Parameter</span></span>

<span data-ttu-id="e104e-113">將 Cmdlet 類別中的公用屬性識別為 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="e104e-113">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="e104e-114">如需詳細資訊，請參閱 [參數屬性聲明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="e104e-114">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="e104e-115">Alias</span><span class="sxs-lookup"><span data-stu-id="e104e-115">Alias</span></span>

<span data-ttu-id="e104e-116">為參數指定一或多個別名。</span><span class="sxs-lookup"><span data-stu-id="e104e-116">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="e104e-117">如需詳細資訊，請參閱 [別名屬性聲明](./alias-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="e104e-117">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="e104e-118">引數驗證屬性</span><span class="sxs-lookup"><span data-stu-id="e104e-118">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="e104e-119">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="e104e-119">ValidateCount</span></span>

<span data-ttu-id="e104e-120">指定 Cmdlet 參數允許的最小和最大引數數目。</span><span class="sxs-lookup"><span data-stu-id="e104e-120">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="e104e-121">如需詳細資訊，請參閱 [ValidateCount 屬性聲明](./validatecount-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="e104e-121">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="e104e-122">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="e104e-122">ValidateLength</span></span>

<span data-ttu-id="e104e-123">指定 Cmdlet 參數引數的最小和最大字元數。</span><span class="sxs-lookup"><span data-stu-id="e104e-123">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="e104e-124">如需詳細資訊，請參閱 [ValidateLength 屬性聲明](./validatelength-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="e104e-124">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="e104e-125">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="e104e-125">ValidatePattern</span></span>

<span data-ttu-id="e104e-126">指定 Cmdlet 參數引數必須符合的正則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="e104e-126">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="e104e-127">如需詳細資訊，請參閱 [ValidatePattern 屬性聲明](./validatepattern-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="e104e-127">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="e104e-128">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="e104e-128">ValidateRange</span></span>

<span data-ttu-id="e104e-129">指定 Cmdlet 參數引數的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="e104e-129">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="e104e-130">如需詳細資訊，請參閱 [ValidateRange 屬性聲明](./validaterange-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="e104e-130">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="e104e-131">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="e104e-131">ValidateSet</span></span>

<span data-ttu-id="e104e-132">為 Cmdlet 參數引數指定一組有效的值。</span><span class="sxs-lookup"><span data-stu-id="e104e-132">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="e104e-133">如需詳細資訊，請參閱 [ValidateSet 屬性聲明](./validateset-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="e104e-133">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e104e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e104e-134">See Also</span></span>

[<span data-ttu-id="e104e-135">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e104e-135">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
