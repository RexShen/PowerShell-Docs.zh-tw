---
title: 屬性型別 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068652"
---
# <a name="attribute-types"></a><span data-ttu-id="d6cab-102">屬性類型</span><span class="sxs-lookup"><span data-stu-id="d6cab-102">Attribute Types</span></span>

<span data-ttu-id="d6cab-103">Cmdlet 屬性可以依功能分組。</span><span class="sxs-lookup"><span data-stu-id="d6cab-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="d6cab-104">下列各節說明可用的屬性，並描述項目執行階段會叫用的屬性時。</span><span class="sxs-lookup"><span data-stu-id="d6cab-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="d6cab-105">Cmdlet 屬性</span><span class="sxs-lookup"><span data-stu-id="d6cab-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="d6cab-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d6cab-106">Cmdlet</span></span>

<span data-ttu-id="d6cab-107">指令程式會識別.NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="d6cab-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="d6cab-108">這是必要的基底屬性。</span><span class="sxs-lookup"><span data-stu-id="d6cab-108">This is the required base attribute.</span></span>
<span data-ttu-id="d6cab-109">如需詳細資訊，請參閱 < [Cmdlet 屬性宣告](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="d6cab-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="d6cab-110">參數屬性</span><span class="sxs-lookup"><span data-stu-id="d6cab-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="d6cab-111">參數</span><span class="sxs-lookup"><span data-stu-id="d6cab-111">Parameter</span></span>

<span data-ttu-id="d6cab-112">Cmdlet 參數的形式會識別在 cmdlet 類別中的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="d6cab-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="d6cab-113">如需詳細資訊，請參閱 <<c0> [ 參數的屬性宣告](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="d6cab-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="d6cab-114">別名</span><span class="sxs-lookup"><span data-stu-id="d6cab-114">Alias</span></span>

<span data-ttu-id="d6cab-115">指定一或多個參數的別名。</span><span class="sxs-lookup"><span data-stu-id="d6cab-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="d6cab-116">如需詳細資訊，請參閱 <<c0> [ 別名屬性宣告](./alias-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="d6cab-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="d6cab-117">引數驗證屬性</span><span class="sxs-lookup"><span data-stu-id="d6cab-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="d6cab-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="d6cab-118">ValidateCount</span></span>

<span data-ttu-id="d6cab-119">指定允許針對 cmdlet 參數的引數的最小和最大數目。</span><span class="sxs-lookup"><span data-stu-id="d6cab-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="d6cab-120">如需詳細資訊，請參閱 < [ValidateCount 屬性宣告](./validatecount-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="d6cab-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="d6cab-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="d6cab-121">ValidateLength</span></span>

<span data-ttu-id="d6cab-122">指定最小和最大的字元數的 cmdlet 參數引數。</span><span class="sxs-lookup"><span data-stu-id="d6cab-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="d6cab-123">如需詳細資訊，請參閱 < [ValidateLength 屬性宣告](./validatelength-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="d6cab-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="d6cab-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="d6cab-124">ValidatePattern</span></span>

<span data-ttu-id="d6cab-125">指定 cmdlet 參數引數必須符合規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="d6cab-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="d6cab-126">如需詳細資訊，請參閱 < [ValidatePattern 屬性宣告](./validatepattern-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="d6cab-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="d6cab-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="d6cab-127">ValidateRange</span></span>

<span data-ttu-id="d6cab-128">指定 cmdlet 參數引數的最小和最大值。</span><span class="sxs-lookup"><span data-stu-id="d6cab-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="d6cab-129">如需詳細資訊，請參閱 < [ValidateRange 屬性宣告](./validaterange-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="d6cab-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="d6cab-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="d6cab-130">ValidateSet</span></span>

<span data-ttu-id="d6cab-131">指定一組 cmdlet 參數引數的有效值。</span><span class="sxs-lookup"><span data-stu-id="d6cab-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="d6cab-132">如需詳細資訊，請參閱 < [ValidateSet 屬性宣告](./validateset-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="d6cab-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d6cab-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6cab-133">See Also</span></span>

[<span data-ttu-id="d6cab-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d6cab-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
