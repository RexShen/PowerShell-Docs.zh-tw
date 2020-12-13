---
ms.date: 09/13/2016
ms.topic: reference
title: 參數屬性宣告
description: 參數屬性宣告
ms.openlocfilehash: bab48a94cb4b1e8501fb79c2f3ef71393fa2ee68
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650354"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="17b3d-103">參數屬性宣告</span><span class="sxs-lookup"><span data-stu-id="17b3d-103">Parameter Attribute Declaration</span></span>

<span data-ttu-id="17b3d-104">Parameter 屬性會將 Cmdlet 類別的公用屬性識別為 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-104">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="17b3d-105">語法</span><span class="sxs-lookup"><span data-stu-id="17b3d-105">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="17b3d-106">參數</span><span class="sxs-lookup"><span data-stu-id="17b3d-106">Parameters</span></span>

<span data-ttu-id="17b3d-107">`Mandatory` ([system.string) 選擇性的命名](/dotnet/api/System.Boolean) 參數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-107">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="17b3d-108">`True` 指出需要 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-108">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="17b3d-109">如果叫用 Cmdlet 時未提供必要的參數，Windows PowerShell 會提示使用者提供參數值。</span><span class="sxs-lookup"><span data-stu-id="17b3d-109">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="17b3d-110">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="17b3d-110">The default is `false`.</span></span>

<span data-ttu-id="17b3d-111">`ParameterSetName` ([system.string](/dotnet/api/System.String)) 選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-111">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="17b3d-112">指定此 Cmdlet 參數所屬的參數集。</span><span class="sxs-lookup"><span data-stu-id="17b3d-112">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="17b3d-113">如果未指定任何參數集，則參數屬於所有參數集。</span><span class="sxs-lookup"><span data-stu-id="17b3d-113">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="17b3d-114">`Position` ([的 system.object](/dotnet/api/System.Int32)) 選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-114">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="17b3d-115">指定參數在 Windows PowerShell 命令中的位置。</span><span class="sxs-lookup"><span data-stu-id="17b3d-115">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="17b3d-116">`ValueFromPipeline` ([system.string) 選擇性的命名](/dotnet/api/System.Boolean) 參數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-116">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="17b3d-117">`True` 指出 Cmdlet 參數接受來自管線物件的值。</span><span class="sxs-lookup"><span data-stu-id="17b3d-117">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="17b3d-118">如果 Cmdlet 存取完整的物件，而不只是物件的屬性，請指定此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="17b3d-118">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="17b3d-119">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="17b3d-119">The default is `false`.</span></span>

<span data-ttu-id="17b3d-120">`ValueFromPipelineByPropertyName` ([system.string) 選擇性的命名](/dotnet/api/System.Boolean) 參數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-120">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="17b3d-121">`True` 指出 Cmdlet 參數會從具有相同名稱或與此參數相同別名的管線物件的屬性取得其值。</span><span class="sxs-lookup"><span data-stu-id="17b3d-121">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="17b3d-122">例如，如果 Cmdlet 有 `Name` 參數，且管線物件也有 `Name` 屬性，則會將屬性的值指派給 `Name` Cmdlet 的 `Name` 參數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-122">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="17b3d-123">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="17b3d-123">The default is `false`.</span></span>

<span data-ttu-id="17b3d-124">`ValueFromRemainingArguments` ([system.string) 選擇性的命名](/dotnet/api/System.Boolean) 參數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-124">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="17b3d-125">`True` 指出 Cmdlet 參數接受所有傳遞給 Cmdlet 的其餘引數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-125">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="17b3d-126">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="17b3d-126">The default is `false`.</span></span>

<span data-ttu-id="17b3d-127">`HelpMessage` 選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-127">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="17b3d-128">指定參數的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="17b3d-128">Specifies a short description of the parameter.</span></span> <span data-ttu-id="17b3d-129">Windows PowerShell 在執行 Cmdlet 且未指定必要參數時，會顯示此訊息。</span><span class="sxs-lookup"><span data-stu-id="17b3d-129">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="17b3d-130">`HelpMessageBaseName` 選擇性的具名引數。指定資源識別碼所在的位置。</span><span class="sxs-lookup"><span data-stu-id="17b3d-130">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="17b3d-131">例如，這個參數可以指定資源元件，其中包含您要當地語系化的說明訊息。</span><span class="sxs-lookup"><span data-stu-id="17b3d-131">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="17b3d-132">`HelpMessageResourceId` 選擇性的具名引數。指定說明訊息的資源識別碼。</span><span class="sxs-lookup"><span data-stu-id="17b3d-132">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="17b3d-133">備註</span><span class="sxs-lookup"><span data-stu-id="17b3d-133">Remarks</span></span>

- <span data-ttu-id="17b3d-134">如需如何宣告此屬性的詳細資訊，請參閱 [如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="17b3d-134">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="17b3d-135">Cmdlet 可以有任意數目的參數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-135">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="17b3d-136">不過，若要獲得更好的使用者體驗，請限制參數的數目。</span><span class="sxs-lookup"><span data-stu-id="17b3d-136">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="17b3d-137">您必須在公用非靜態欄位或屬性上宣告參數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-137">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="17b3d-138">必須在屬性上宣告參數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-138">Parameters should be declared on properties.</span></span> <span data-ttu-id="17b3d-139">屬性必須具有公用 set 存取子，而且如果指定了 `ValueFromPipeline` 或 `ValueFromPipelineByPropertyName` 關鍵字，屬性必須具有公用 get 存取子。</span><span class="sxs-lookup"><span data-stu-id="17b3d-139">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="17b3d-140">當您指定位置參數時，請將參數中的位置參數數目限制為小於5。</span><span class="sxs-lookup"><span data-stu-id="17b3d-140">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="17b3d-141">而且，位置參數不一定要是連續的。</span><span class="sxs-lookup"><span data-stu-id="17b3d-141">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="17b3d-142">位置5、100和250的運作方式與位置0、1和2相同。</span><span class="sxs-lookup"><span data-stu-id="17b3d-142">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="17b3d-143">如果 `Position` 未指定關鍵字，則 Cmdlet 參數必須由其名稱參考。</span><span class="sxs-lookup"><span data-stu-id="17b3d-143">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="17b3d-144">當您使用參數集時，請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="17b3d-144">When you use parameter sets, note the following:</span></span>

  - <span data-ttu-id="17b3d-145">每個參數集都必須至少有一個唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-145">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="17b3d-146">良好的 Cmdlet 設計指出，如果可能的話，這個唯一的參數也應該是必要的。</span><span class="sxs-lookup"><span data-stu-id="17b3d-146">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="17b3d-147">如果您的 Cmdlet 是設計為在沒有參數的情況下執行，則唯一的參數不能是強制性的。</span><span class="sxs-lookup"><span data-stu-id="17b3d-147">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

  - <span data-ttu-id="17b3d-148">沒有任何參數集應包含一個以上具有相同位置的位置參數。</span><span class="sxs-lookup"><span data-stu-id="17b3d-148">No parameter set should contain more than one positional parameter with the same position.</span></span>

  - <span data-ttu-id="17b3d-149">參數集中只能有一個參數 `ValueFromPipeline = true` 。</span><span class="sxs-lookup"><span data-stu-id="17b3d-149">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="17b3d-150">可以定義多個參數 `ValueFromPipelineByPropertyName = true` 。</span><span class="sxs-lookup"><span data-stu-id="17b3d-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

  - <span data-ttu-id="17b3d-151">可以定義多個參數 `ValueFromPipelineByPropertyName = true` 。</span><span class="sxs-lookup"><span data-stu-id="17b3d-151">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="17b3d-152">如需參數名稱指導方針的詳細資訊，請參閱 [Cmdlet 參數名稱](standard-cmdlet-parameter-names-and-types.md)。</span><span class="sxs-lookup"><span data-stu-id="17b3d-152">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="17b3d-153">Parameter 屬性是由 [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 類別所定義。</span><span class="sxs-lookup"><span data-stu-id="17b3d-153">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="17b3d-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17b3d-154">See Also</span></span>

[<span data-ttu-id="17b3d-155">Parameterattribute。</span><span class="sxs-lookup"><span data-stu-id="17b3d-155">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="17b3d-156">Cmdlet 參數名稱</span><span class="sxs-lookup"><span data-stu-id="17b3d-156">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="17b3d-157">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="17b3d-157">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
