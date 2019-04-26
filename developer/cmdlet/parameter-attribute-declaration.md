---
title: 參數屬性的宣告 |Microsoft Docs
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
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067547"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="dee13-102">參數屬性宣告</span><span class="sxs-lookup"><span data-stu-id="dee13-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="dee13-103">參數屬性會識別在 cmdlet 類別的公用屬性當做 cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="dee13-104">語法</span><span class="sxs-lookup"><span data-stu-id="dee13-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="dee13-105">參數</span><span class="sxs-lookup"><span data-stu-id="dee13-105">Parameters</span></span>

<span data-ttu-id="dee13-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="dee13-107">`True` 表示需要 cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="dee13-108">如果未提供必要的參數，叫用 cmdlet 時，Windows PowerShell 會提示使用者輸入的參數值。</span><span class="sxs-lookup"><span data-stu-id="dee13-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="dee13-109">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="dee13-109">The default is `false`.</span></span>

<span data-ttu-id="dee13-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) 選擇性具名參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="dee13-111">指定此 cmdlet 的參數所屬的參數集合。</span><span class="sxs-lookup"><span data-stu-id="dee13-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="dee13-112">如果未不指定任何參數集，則參數所屬的所有參數集。</span><span class="sxs-lookup"><span data-stu-id="dee13-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="dee13-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) 選擇性具名參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) Optional named parameter.</span></span> <span data-ttu-id="dee13-114">指定在 Windows PowerShell 命令中參數的位置。</span><span class="sxs-lookup"><span data-stu-id="dee13-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="dee13-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="dee13-116">`True` 指出 cmdlet 參數接受從管線物件，其值。</span><span class="sxs-lookup"><span data-stu-id="dee13-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="dee13-117">指定此關鍵字，如果 cmdlet 會在存取完整的物件，不只是物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="dee13-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="dee13-118">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="dee13-118">The default is `false`.</span></span>

<span data-ttu-id="dee13-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="dee13-120">`True` 指出 cmdlet 參數接受從管線物件具有相同名稱或相同的別名作為此參數的屬性及其值。</span><span class="sxs-lookup"><span data-stu-id="dee13-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="dee13-121">例如，如果 cmdlet 不會有`Name`參數和管線的物件也有`Name`屬性、 值`Name`屬性會指派給`Name`指令程式參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="dee13-122">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="dee13-122">The default is `false`.</span></span>

<span data-ttu-id="dee13-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="dee13-124">`True` 指出 cmdlet 參數接受所有剩餘的引數傳遞至 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dee13-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="dee13-125">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="dee13-125">The default is `false`.</span></span>

<span data-ttu-id="dee13-126">`HelpMessage` 選擇性具名參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="dee13-127">指定參數的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="dee13-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="dee13-128">指令程式會執行，且未指定必要的參數時，Windows PowerShell 就會顯示此訊息。</span><span class="sxs-lookup"><span data-stu-id="dee13-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="dee13-129">`HelpMessageBaseName` 選擇性具名參數。指定資源識別項的所在的位置。</span><span class="sxs-lookup"><span data-stu-id="dee13-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="dee13-130">比方說，這個參數可以指定資源組件，其中包含您想要當地語系化的說明訊息。</span><span class="sxs-lookup"><span data-stu-id="dee13-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="dee13-131">`HelpMessageResourceId` 選擇性具名參數。指定說明訊息的資源識別項。</span><span class="sxs-lookup"><span data-stu-id="dee13-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="dee13-132">備註</span><span class="sxs-lookup"><span data-stu-id="dee13-132">Remarks</span></span>

- <span data-ttu-id="dee13-133">如需如何宣告這個屬性的詳細資訊，請參閱[如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="dee13-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="dee13-134">Cmdlet 可以有任意數目的參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="dee13-135">不過，為了更好的使用者體驗，限制參數的數目。</span><span class="sxs-lookup"><span data-stu-id="dee13-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="dee13-136">參數必須宣告為公用非靜態欄位或屬性。</span><span class="sxs-lookup"><span data-stu-id="dee13-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="dee13-137">參數應該宣告為屬性。</span><span class="sxs-lookup"><span data-stu-id="dee13-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="dee13-138">此屬性必須具有公用 set 存取子，而如果`ValueFromPipeline`或`ValueFromPipelineByPropertyName`關鍵字指定，則此屬性必須具有公用 get 存取子。</span><span class="sxs-lookup"><span data-stu-id="dee13-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="dee13-139">當您指定位置參數時，限制參數設定為小於 5 中的位置參數的數目。</span><span class="sxs-lookup"><span data-stu-id="dee13-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="dee13-140">而且，不需要是連續的位置參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="dee13-141">位置 5、 100 到 250 運作相同位置 0、 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="dee13-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="dee13-142">當`Position`關鍵字未指定，必須依名稱參考的 cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="dee13-143">當您使用參數集時，請注意下列各項：</span><span class="sxs-lookup"><span data-stu-id="dee13-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="dee13-144">每個參數集必須至少一個唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="dee13-145">良好的 cmdlet 的設計會指出這個唯一參數應該也是必要的話。</span><span class="sxs-lookup"><span data-stu-id="dee13-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="dee13-146">如果您的 cmdlet 設計來執行未包含參數，則無法強制唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="dee13-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="dee13-147">未設定任何參數應不包含多個位置的參數具有相同的位置。</span><span class="sxs-lookup"><span data-stu-id="dee13-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="dee13-148">參數集合中的只有一個參數應該宣告`ValueFromPipeline = true`。</span><span class="sxs-lookup"><span data-stu-id="dee13-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="dee13-149">可以定義多個參數`ValueFromPipelineByPropertyName = true`。</span><span class="sxs-lookup"><span data-stu-id="dee13-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="dee13-150">可以定義多個參數`ValueFromPipelineByPropertyName = true`。</span><span class="sxs-lookup"><span data-stu-id="dee13-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="dee13-151">如需參數名稱的指導方針的詳細資訊，請參閱[Cmdlet 的參數名稱](standard-cmdlet-parameter-names-and-types.md)。</span><span class="sxs-lookup"><span data-stu-id="dee13-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="dee13-152">所定義的參數屬性[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)類別。</span><span class="sxs-lookup"><span data-stu-id="dee13-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="dee13-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dee13-153">See Also</span></span>

[<span data-ttu-id="dee13-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="dee13-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="dee13-155">Cmdlet 參數名稱</span><span class="sxs-lookup"><span data-stu-id="dee13-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="dee13-156">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="dee13-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
