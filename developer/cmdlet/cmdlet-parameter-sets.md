---
title: Cmdlet 參數集 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857264"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="0c38d-102">Cmdlet 參數集</span><span class="sxs-lookup"><span data-stu-id="0c38d-102">Cmdlet Parameter Sets</span></span>

<span data-ttu-id="0c38d-103">Windows PowerShell 會使用參數集，讓您撰寫單一的 cmdlet，可以針對不同的案例中執行不同的動作。</span><span class="sxs-lookup"><span data-stu-id="0c38d-103">Windows PowerShell uses parameter sets to enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span> <span data-ttu-id="0c38d-104">參數集可讓您公開給使用者的不同參數，並傳回不同的資訊，根據使用者所指定的參數。</span><span class="sxs-lookup"><span data-stu-id="0c38d-104">Parameter sets enable you to expose different parameters to the user and to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="0c38d-105">參數集範例</span><span class="sxs-lookup"><span data-stu-id="0c38d-105">Examples of Parameter Sets</span></span>

<span data-ttu-id="0c38d-106">例如， `Get-EventLog` （Windows PowerShell 所提供） 的 cmdlet 會傳回不同的資訊，根據使用者指定了是否`List`或`LogName`參數。</span><span class="sxs-lookup"><span data-stu-id="0c38d-106">For example, the `Get-EventLog` cmdlet (provided by Windows PowerShell) returns different information depending on whether the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="0c38d-107">如果`List`參數指定，則此 cmdlet 會傳回資訊的記錄檔本身，但不是包含事件的資訊。</span><span class="sxs-lookup"><span data-stu-id="0c38d-107">If the `List` parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="0c38d-108">如果`LogName`參數指定，則指令程式可傳回特定的事件記錄檔事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0c38d-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="0c38d-109">`List`和`LogName`參數會識別兩個不同的參數集。</span><span class="sxs-lookup"><span data-stu-id="0c38d-109">The `List` and `LogName` parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="0c38d-110">唯一的參數</span><span class="sxs-lookup"><span data-stu-id="0c38d-110">Unique Parameter</span></span>

<span data-ttu-id="0c38d-111">每個參數集必須具有唯一的參數，Windows PowerShell 執行階段可供公開適當的參數組。</span><span class="sxs-lookup"><span data-stu-id="0c38d-111">Each parameter set must have a unique parameter that the Windows PowerShell runtime can use to expose the appropriate parameter set.</span></span> <span data-ttu-id="0c38d-112">可能的話，唯一的參數應該是必要的參數。</span><span class="sxs-lookup"><span data-stu-id="0c38d-112">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="0c38d-113">時為必要參數，來指定參數，會強制使用者和 Windows PowerShell 執行階段可以使用該參數，來識別設定為使用的參數。</span><span class="sxs-lookup"><span data-stu-id="0c38d-113">When a parameter is mandatory, the user is forced to specify the parameter, and the Windows PowerShell runtime can use that parameter to identify the parameter set to use.</span></span> <span data-ttu-id="0c38d-114">唯一的參數不得為必要項目，如果您的指令程式可執行，而不指定任何參數。</span><span class="sxs-lookup"><span data-stu-id="0c38d-114">The unique parameter cannot be mandatory if your cmdlet is designed to be run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="0c38d-115">多個參數集</span><span class="sxs-lookup"><span data-stu-id="0c38d-115">Multiple Parameter Sets</span></span>

<span data-ttu-id="0c38d-116">下圖中，在左方的欄會顯示三個有效的參數集。</span><span class="sxs-lookup"><span data-stu-id="0c38d-116">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="0c38d-117">參數的而言是唯一的第一個參數集、 參數 B 是唯一的第二個參數集，而且參數 C 是專用的第三個參數集。</span><span class="sxs-lookup"><span data-stu-id="0c38d-117">Parameter A is unique to the first parameter set, parameter B is unique to the second parameter set, and parameter C is unique to the third parameter set.</span></span> <span data-ttu-id="0c38d-118">不過，在右欄中，參數集不需要唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="0c38d-118">However, in the right column, the parameter sets do not have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="0c38d-120">參數集需求</span><span class="sxs-lookup"><span data-stu-id="0c38d-120">Parameter Set Requirements</span></span>

<span data-ttu-id="0c38d-121">下列需求適用於所有參數集。</span><span class="sxs-lookup"><span data-stu-id="0c38d-121">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="0c38d-122">每個參數集必須至少一個唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="0c38d-122">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="0c38d-123">如果可能，請此參數為必要參數。</span><span class="sxs-lookup"><span data-stu-id="0c38d-123">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="0c38d-124">參數集，其中包含多個位置的參數必須定義每個參數的唯一位置。</span><span class="sxs-lookup"><span data-stu-id="0c38d-124">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="0c38d-125">沒有兩個位置參數可以指定相同的位置。</span><span class="sxs-lookup"><span data-stu-id="0c38d-125">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="0c38d-126">集合中的只有一個參數可以宣告`ValueFromPipeline`關鍵字的值與`true`。</span><span class="sxs-lookup"><span data-stu-id="0c38d-126">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="0c38d-127">可以定義多個參數`ValueFromPipelineByPropertyName`關鍵字的值與`true`。</span><span class="sxs-lookup"><span data-stu-id="0c38d-127">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="0c38d-128">如果未設定任何參數不指定為參數，參數是屬於所有參數集。</span><span class="sxs-lookup"><span data-stu-id="0c38d-128">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="0c38d-129">預設參數集</span><span class="sxs-lookup"><span data-stu-id="0c38d-129">Default Parameter Sets</span></span>

<span data-ttu-id="0c38d-130">定義了多個參數集，您可以使用`DefaultParameterSetName`Cmdlet 屬性，以指定預設參數集的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0c38d-130">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the Cmdlet attribute to specify the default parameter set.</span></span> <span data-ttu-id="0c38d-131">Windows PowerShell 會使用的預設參數集，如果它無法判斷將參數設定為使用根據命令所提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="0c38d-131">Windows PowerShell uses the default parameter set if it cannot determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="0c38d-132">如需有關 Cmdlet 屬性的詳細資訊，請參閱[Cmdlet 屬性宣告](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="0c38d-132">For more information about the Cmdlet attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="0c38d-133">宣告參數集</span><span class="sxs-lookup"><span data-stu-id="0c38d-133">Declaring Parameter Sets</span></span>

<span data-ttu-id="0c38d-134">若要建立參數集，您必須指定`ParameterSetName`關鍵字宣告的參數集的每個參數的參數屬性。</span><span class="sxs-lookup"><span data-stu-id="0c38d-134">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the Parameter attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="0c38d-135">對於屬於多個參數集的參數，新增每個參數集的參數屬性。</span><span class="sxs-lookup"><span data-stu-id="0c38d-135">For parameters that belong to multiple parameter sets, add a Parameter attribute for each parameter set.</span></span> <span data-ttu-id="0c38d-136">這可讓您定義每個參數集不同的參數。</span><span class="sxs-lookup"><span data-stu-id="0c38d-136">This enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="0c38d-137">比方說，您可以將參數定義為在一組必要和選用在另一個。</span><span class="sxs-lookup"><span data-stu-id="0c38d-137">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="0c38d-138">不過，每個參數集必須包含一個唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="0c38d-138">However, each parameter set must contain one unique parameter.</span></span>

<span data-ttu-id="0c38d-139">在下列範例中，`UserName`參數是 Test01 參數集的唯一的參數和`ComputerName`參數是 Test02 參數集的唯一參數。</span><span class="sxs-lookup"><span data-stu-id="0c38d-139">In the following example, the `UserName` parameter is the unique parameter of the Test01 parameter set, and the `ComputerName` parameter is the unique parameter of the Test02 parameter set.</span></span> <span data-ttu-id="0c38d-140">`SharedParam`參數屬於這兩個集合，且為 Test01 參數，但 Test02 參數集的選擇性設定的必要項目。</span><span class="sxs-lookup"><span data-stu-id="0c38d-140">The `SharedParam` parameter belongs to both sets and is mandatory for the Test01 parameter set but optional for the Test02 parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```