---
title: 參數屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365357"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="719d5-102">參數屬性宣告</span><span class="sxs-lookup"><span data-stu-id="719d5-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="719d5-103">Parameter 屬性會將 Cmdlet 類別的公用屬性識別為 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="719d5-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="719d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="719d5-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="719d5-105">參數</span><span class="sxs-lookup"><span data-stu-id="719d5-105">Parameters</span></span>

<span data-ttu-id="719d5-106">`Mandatory` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="719d5-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="719d5-107">`True` 表示 Cmdlet 參數是必要的。</span><span class="sxs-lookup"><span data-stu-id="719d5-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="719d5-108">如果叫用 Cmdlet 時未提供必要的參數，Windows PowerShell 會提示使用者輸入參數值。</span><span class="sxs-lookup"><span data-stu-id="719d5-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="719d5-109">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="719d5-109">The default is `false`.</span></span>

<span data-ttu-id="719d5-110">`ParameterSetName` （[system.string](/dotnet/api/System.String)）選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="719d5-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="719d5-111">指定此 Cmdlet 參數所屬的參數集。</span><span class="sxs-lookup"><span data-stu-id="719d5-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="719d5-112">如果未指定參數集，參數會屬於所有參數集。</span><span class="sxs-lookup"><span data-stu-id="719d5-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="719d5-113">`Position` （[Int32](/dotnet/api/System.Int32)）選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="719d5-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="719d5-114">指定參數在 Windows PowerShell 命令中的位置。</span><span class="sxs-lookup"><span data-stu-id="719d5-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="719d5-115">`ValueFromPipeline` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="719d5-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="719d5-116">`True` 表示 Cmdlet 參數接受管線物件的值。</span><span class="sxs-lookup"><span data-stu-id="719d5-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="719d5-117">如果 Cmdlet 存取完整的物件，而不只是物件的屬性，請指定此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="719d5-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="719d5-118">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="719d5-118">The default is `false`.</span></span>

<span data-ttu-id="719d5-119">`ValueFromPipelineByPropertyName` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="719d5-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="719d5-120">`True` 表示 Cmdlet 參數從管線物件的屬性取得其值，其名稱或別名與此參數相同。</span><span class="sxs-lookup"><span data-stu-id="719d5-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="719d5-121">例如，如果 Cmdlet 具有 `Name` 參數，而且管線物件也有 `Name` 屬性，則 `Name` 屬性的值會指派給 Cmdlet 的 `Name` 參數。</span><span class="sxs-lookup"><span data-stu-id="719d5-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="719d5-122">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="719d5-122">The default is `false`.</span></span>

<span data-ttu-id="719d5-123">`ValueFromRemainingArguments` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="719d5-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="719d5-124">`True` 表示 Cmdlet 參數接受傳遞給 Cmdlet 的所有其餘引數。</span><span class="sxs-lookup"><span data-stu-id="719d5-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="719d5-125">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="719d5-125">The default is `false`.</span></span>

<span data-ttu-id="719d5-126">`HelpMessage` 選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="719d5-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="719d5-127">指定參數的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="719d5-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="719d5-128">當 Cmdlet 執行時，Windows PowerShell 會顯示此訊息，且未指定強制參數。</span><span class="sxs-lookup"><span data-stu-id="719d5-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="719d5-129">`HelpMessageBaseName` 選擇性的具名引數。指定資源識別碼所在的位置。</span><span class="sxs-lookup"><span data-stu-id="719d5-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="719d5-130">例如，此參數可以指定資源元件，其中包含您想要當地語系化的說明訊息。</span><span class="sxs-lookup"><span data-stu-id="719d5-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="719d5-131">`HelpMessageResourceId` 選擇性的具名引數。指定說明訊息的資源識別碼。</span><span class="sxs-lookup"><span data-stu-id="719d5-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="719d5-132">備註</span><span class="sxs-lookup"><span data-stu-id="719d5-132">Remarks</span></span>

- <span data-ttu-id="719d5-133">如需如何宣告此屬性的詳細資訊，請參閱 how [To Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="719d5-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="719d5-134">Cmdlet 可以有任意數目的參數。</span><span class="sxs-lookup"><span data-stu-id="719d5-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="719d5-135">不過，若要獲得更佳的使用者體驗，請限制參數的數目。</span><span class="sxs-lookup"><span data-stu-id="719d5-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="719d5-136">參數必須在公用非靜態欄位或屬性上宣告。</span><span class="sxs-lookup"><span data-stu-id="719d5-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="719d5-137">參數應該在屬性上宣告。</span><span class="sxs-lookup"><span data-stu-id="719d5-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="719d5-138">屬性必須具有公用 set 存取子，如果指定了 `ValueFromPipeline` 或 `ValueFromPipelineByPropertyName` 關鍵字，則屬性必須具有公用 get 存取子。</span><span class="sxs-lookup"><span data-stu-id="719d5-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="719d5-139">當您指定位置參數時，請將參數集中的位置參數數目限制為小於五個。</span><span class="sxs-lookup"><span data-stu-id="719d5-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="719d5-140">和，位置參數不一定要是連續的。</span><span class="sxs-lookup"><span data-stu-id="719d5-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="719d5-141">位置5、100和250的工作方式與位置0、1和2相同。</span><span class="sxs-lookup"><span data-stu-id="719d5-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="719d5-142">未指定 `Position` 關鍵字時，Cmdlet 參數必須由其名稱參考。</span><span class="sxs-lookup"><span data-stu-id="719d5-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="719d5-143">當您使用參數集時，請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="719d5-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="719d5-144">每個參數集必須至少有一個唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="719d5-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="719d5-145">良好的 Cmdlet 設計表示如果可能，此唯一參數也應該是強制的。</span><span class="sxs-lookup"><span data-stu-id="719d5-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="719d5-146">如果您的 Cmdlet 設計為不搭配參數執行，則 unique 參數不可以是強制的。</span><span class="sxs-lookup"><span data-stu-id="719d5-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="719d5-147">沒有參數集應包含一個以上具有相同位置的位置參數。</span><span class="sxs-lookup"><span data-stu-id="719d5-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="719d5-148">參數集中只有一個參數應宣告 `ValueFromPipeline = true`。</span><span class="sxs-lookup"><span data-stu-id="719d5-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="719d5-149">多個參數可以定義 `ValueFromPipelineByPropertyName = true`。</span><span class="sxs-lookup"><span data-stu-id="719d5-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="719d5-150">多個參數可以定義 `ValueFromPipelineByPropertyName = true`。</span><span class="sxs-lookup"><span data-stu-id="719d5-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="719d5-151">如需參數名稱指導方針的詳細資訊，請參閱[Cmdlet 參數名稱](standard-cmdlet-parameter-names-and-types.md)。</span><span class="sxs-lookup"><span data-stu-id="719d5-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="719d5-152">Parameter 屬性是由[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)類別所定義。</span><span class="sxs-lookup"><span data-stu-id="719d5-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="719d5-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="719d5-153">See Also</span></span>

[<span data-ttu-id="719d5-154">Parameterattribute。</span><span class="sxs-lookup"><span data-stu-id="719d5-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="719d5-155">Cmdlet 參數名稱</span><span class="sxs-lookup"><span data-stu-id="719d5-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="719d5-156">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="719d5-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)