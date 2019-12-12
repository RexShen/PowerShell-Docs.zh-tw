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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365927"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="b7378-102">Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="b7378-102">Cmdlet Parameters</span></span>

<span data-ttu-id="b7378-103">Cmdlet 參數提供允許 Cmdlet 接受輸入的機制。</span><span class="sxs-lookup"><span data-stu-id="b7378-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="b7378-104">參數可以直接從命令列或透過管線傳遞給 Cmdlet 的物件接受輸入，這些參數的引數（也稱為*值*）可以指定 Cmdlet 接受的輸入、Cmdlet 應如何執行其動作，以及 Cmdlet 傳回給管線的資料。</span><span class="sxs-lookup"><span data-stu-id="b7378-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b7378-105">在本節中</span><span class="sxs-lookup"><span data-stu-id="b7378-105">In This Section</span></span>

<span data-ttu-id="b7378-106">將[屬性宣告為參數](./declaring-properties-as-parameters.md)提供在宣告 Cmdlet 的參數之前，您必須瞭解的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="b7378-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="b7378-107">[Cmdlet 參數的類型](./types-of-cmdlet-parameters.md)說明您可以在 Cmdlet 中宣告的不同參數類型。</span><span class="sxs-lookup"><span data-stu-id="b7378-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="b7378-108">[Cmdlet 參數名稱和功能方針](./standard-cmdlet-parameter-names-and-types.md)Discuses 標準參數的名稱、建議的資料類型和功能。</span><span class="sxs-lookup"><span data-stu-id="b7378-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="b7378-109">[參數別名](./parameter-aliases.md)討論您可以為參數定義的別名。</span><span class="sxs-lookup"><span data-stu-id="b7378-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="b7378-110">[一般參數名稱](./common-parameter-names.md)本主題說明 Windows PowerShell 新增至 Cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="b7378-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="b7378-111">[Cmdlet 參數集](./cmdlet-parameter-sets.md)討論參數集如何讓您撰寫可針對不同案例執行不同動作的單一 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b7378-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="b7378-112">[Cmdlet 動態參數](./cmdlet-dynamic-parameters.md)討論使用者在特殊條件下可使用的參數。</span><span class="sxs-lookup"><span data-stu-id="b7378-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="b7378-113">[支援 Cmdlet 參數中的萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)說明當您設計將針對一組資源執行的 Cmdlet 時，如何提供萬用字元支援。</span><span class="sxs-lookup"><span data-stu-id="b7378-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="b7378-114">[驗證參數輸入](./validating-parameter-input.md)說明 Windows PowerShell 如何驗證傳遞給 Cmdlet 參數的引數。</span><span class="sxs-lookup"><span data-stu-id="b7378-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="b7378-115">[輸入篩選參數](./input-filter-parameters.md)討論 `Filter`、`Include`和 `Exclude` 參數，以篩選 Cmdlet 所影響的輸入物件集合。</span><span class="sxs-lookup"><span data-stu-id="b7378-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b7378-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="b7378-116">Related Sections</span></span>

[<span data-ttu-id="b7378-117">如何驗證參數輸入</span><span class="sxs-lookup"><span data-stu-id="b7378-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="b7378-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7378-118">See Also</span></span>

[<span data-ttu-id="b7378-119">參數屬性宣告</span><span class="sxs-lookup"><span data-stu-id="b7378-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="b7378-120">Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b7378-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
