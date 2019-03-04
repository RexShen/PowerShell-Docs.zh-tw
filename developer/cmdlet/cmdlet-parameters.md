---
title: Cmdlet 參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853844"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="c1322-102">Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="c1322-102">Cmdlet Parameters</span></span>

<span data-ttu-id="c1322-103">Cmdlet 參數提供的機制，可讓 cmdlet 接受輸入。</span><span class="sxs-lookup"><span data-stu-id="c1322-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="c1322-104">參數可以接受輸入，直接從命令列中，或透過管線中，引數傳遞至 cmdlet 的物件 (也稱為*值*) 這些參數可以指定此 cmdlet 會接受的輸入方式指令程式應該執行其動作和指令程式可傳回至管線的資料。</span><span class="sxs-lookup"><span data-stu-id="c1322-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c1322-105">在本節中</span><span class="sxs-lookup"><span data-stu-id="c1322-105">In This Section</span></span>

<span data-ttu-id="c1322-106">[宣告屬性做為參數](./declaring-properties-as-parameters.md)提供宣告之參數的 cmdlet 之前，必須了解的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="c1322-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="c1322-107">[Cmdlet 參數的型別](./types-of-cmdlet-parameters.md)說明不同類型的 cmdlet 中，您可以宣告的參數。</span><span class="sxs-lookup"><span data-stu-id="c1322-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="c1322-108">[Cmdlet 參數名稱和功能的指導方針](./standard-cmdlet-parameter-names-and-types.md)Discuses 名稱，建議的資料類型和功能的標準參數。</span><span class="sxs-lookup"><span data-stu-id="c1322-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="c1322-109">[參數別名](./parameter-aliases.md)討論您可以定義參數的別名。</span><span class="sxs-lookup"><span data-stu-id="c1322-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="c1322-110">[常見的參數名稱](./common-parameter-names.md)本主題描述 Windows PowerShell 將新增到 cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="c1322-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="c1322-111">[Cmdlet 參數會設定](./cmdlet-parameter-sets.md)討論如何參數集可讓您撰寫單一的 cmdlet，可以針對不同的案例中執行不同的動作。</span><span class="sxs-lookup"><span data-stu-id="c1322-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="c1322-112">[Cmdlet 的動態參數](./cmdlet-dynamic-parameters.md)討論在特殊情況下，使用者可以使用的參數。</span><span class="sxs-lookup"><span data-stu-id="c1322-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="c1322-113">[在 Cmdlet 參數支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)說明如何提供支援的萬用字元，當您設計的 cmdlet，將會針對資源群組中的執行。</span><span class="sxs-lookup"><span data-stu-id="c1322-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="c1322-114">[驗證參數輸入](./validating-parameter-input.md)說明 Windows PowerShell 如何驗證傳遞給 cmdlet 參數的引數。</span><span class="sxs-lookup"><span data-stu-id="c1322-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="c1322-115">[輸入篩選參數](./input-filter-parameters.md)討論`Filter`， `Include`，和`Exclude`篩選一組指令程式會影響的輸入物件的參數。</span><span class="sxs-lookup"><span data-stu-id="c1322-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c1322-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="c1322-116">Related Sections</span></span>

[<span data-ttu-id="c1322-117">如何驗證參數的輸入</span><span class="sxs-lookup"><span data-stu-id="c1322-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="c1322-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1322-118">See Also</span></span>

[<span data-ttu-id="c1322-119">參數屬性宣告</span><span class="sxs-lookup"><span data-stu-id="c1322-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="c1322-120">Windows PowerShell Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c1322-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
