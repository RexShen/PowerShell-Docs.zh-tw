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
ms.openlocfilehash: 41cb32735091f065a0835378428de190d08f3160
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278973"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="af7a2-102">Cmdlet 參數集</span><span class="sxs-lookup"><span data-stu-id="af7a2-102">Cmdlet parameter sets</span></span>

<span data-ttu-id="af7a2-103">PowerShell 會使用參數集，讓您撰寫可針對不同案例執行不同動作的單一 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="af7a2-103">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="af7a2-104">參數集可讓您向使用者公開不同的參數。</span><span class="sxs-lookup"><span data-stu-id="af7a2-104">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="af7a2-105">和，根據使用者指定的參數傳回不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="af7a2-105">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="af7a2-106">參數集的範例</span><span class="sxs-lookup"><span data-stu-id="af7a2-106">Examples of parameter sets</span></span>

<span data-ttu-id="af7a2-107">例如，PowerShell `Get-EventLog` Cmdlet 會根據使用者是否指定**List**或**LogName**參數，傳回不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="af7a2-107">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="af7a2-108">如果指定了**List**參數，Cmdlet 會傳回記錄檔本身的相關資訊，但不會傳回其包含的事件資訊。</span><span class="sxs-lookup"><span data-stu-id="af7a2-108">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="af7a2-109">如果指定**LogName**參數，此 Cmdlet 會傳回特定事件記錄檔中事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="af7a2-109">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="af7a2-110">**List**和**LogName**參數會識別兩個不同的參數集。</span><span class="sxs-lookup"><span data-stu-id="af7a2-110">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="af7a2-111">唯一參數</span><span class="sxs-lookup"><span data-stu-id="af7a2-111">Unique parameter</span></span>

<span data-ttu-id="af7a2-112">每個參數集都必須有一個唯一的參數，讓 PowerShell 執行時間用來公開適當的參數集。</span><span class="sxs-lookup"><span data-stu-id="af7a2-112">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="af7a2-113">可能的話，unique 參數應該是必要參數。</span><span class="sxs-lookup"><span data-stu-id="af7a2-113">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="af7a2-114">當參數為強制性時，使用者必須指定參數，而且 PowerShell 執行時間會使用該參數來識別參數集。</span><span class="sxs-lookup"><span data-stu-id="af7a2-114">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="af7a2-115">如果您的 Cmdlet 設計成在不指定任何參數的情況下執行，則唯一的參數不能是強制的。</span><span class="sxs-lookup"><span data-stu-id="af7a2-115">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="af7a2-116">多個參數集</span><span class="sxs-lookup"><span data-stu-id="af7a2-116">Multiple parameter sets</span></span>

<span data-ttu-id="af7a2-117">在下圖中，左邊的資料行顯示三個有效的參數集。</span><span class="sxs-lookup"><span data-stu-id="af7a2-117">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="af7a2-118">**參數 A**對第一個參數集而言是唯一的，**參數 B**對第二個參數集而言是唯一的，而**參數 C**則是第三個參數集獨有的。</span><span class="sxs-lookup"><span data-stu-id="af7a2-118">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="af7a2-119">在右邊的資料行中，參數集沒有唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="af7a2-119">In the right column, the parameter sets don't have a unique parameter.</span></span>

![ps_parametersets](media/cmdlet-parameter-sets/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="af7a2-121">參數集需求</span><span class="sxs-lookup"><span data-stu-id="af7a2-121">Parameter set requirements</span></span>

<span data-ttu-id="af7a2-122">下列需求適用于所有參數集。</span><span class="sxs-lookup"><span data-stu-id="af7a2-122">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="af7a2-123">每個參數集必須至少有一個唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="af7a2-123">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="af7a2-124">可能的話，請將此參數設為必要參數。</span><span class="sxs-lookup"><span data-stu-id="af7a2-124">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="af7a2-125">包含多個位置參數的參數集必須為每個參數定義唯一的位置。</span><span class="sxs-lookup"><span data-stu-id="af7a2-125">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="af7a2-126">沒有兩個位置參數可以指定相同的位置。</span><span class="sxs-lookup"><span data-stu-id="af7a2-126">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="af7a2-127">在集合中，只有一個參數可以宣告具有 `true`值的 `ValueFromPipeline` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="af7a2-127">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="af7a2-128">多個參數可以定義具有 `true`值的 `ValueFromPipelineByPropertyName` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="af7a2-128">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="af7a2-129">如果沒有為參數指定參數集，參數就會屬於所有參數集。</span><span class="sxs-lookup"><span data-stu-id="af7a2-129">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="af7a2-130">Cmdlet 或函式的限制為32個參數集。</span><span class="sxs-lookup"><span data-stu-id="af7a2-130">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="af7a2-131">預設參數集</span><span class="sxs-lookup"><span data-stu-id="af7a2-131">Default parameter sets</span></span>

<span data-ttu-id="af7a2-132">定義多個參數集時，您可以使用**Cmdlet**屬性的 `DefaultParameterSetName` 關鍵字來指定預設參數集。</span><span class="sxs-lookup"><span data-stu-id="af7a2-132">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="af7a2-133">如果 PowerShell 無法根據命令所提供的資訊來判斷要使用的參數，則會使用預設參數集。</span><span class="sxs-lookup"><span data-stu-id="af7a2-133">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="af7a2-134">如需**Cmdlet**屬性的詳細資訊，請參閱[Cmdlet 屬性](./cmdlet-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="af7a2-134">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="af7a2-135">宣告參數集</span><span class="sxs-lookup"><span data-stu-id="af7a2-135">Declaring parameter sets</span></span>

<span data-ttu-id="af7a2-136">若要建立參數集，您必須在宣告參數集內每個參數的**參數**屬性時，指定 `ParameterSetName` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="af7a2-136">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="af7a2-137">針對屬於多個參數集的參數，請為每個參數集新增**參數**屬性。</span><span class="sxs-lookup"><span data-stu-id="af7a2-137">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="af7a2-138">這個屬性可讓您針對每個參數集定義不同的參數。</span><span class="sxs-lookup"><span data-stu-id="af7a2-138">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="af7a2-139">例如，您可以將參數定義為一個集合中的必要項，並在另一個集合中將其設為選擇性。</span><span class="sxs-lookup"><span data-stu-id="af7a2-139">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="af7a2-140">不過，每個參數集都必須包含一個唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="af7a2-140">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="af7a2-141">如需詳細資訊，請參閱[參數屬性](parameter-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="af7a2-141">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="af7a2-142">在下列範例中， **UserName**參數是 `Test01` 參數集的唯一參數，而**ComputerName**參數是 `Test02` 參數集的唯一參數。</span><span class="sxs-lookup"><span data-stu-id="af7a2-142">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="af7a2-143">**SharedParam**參數同時屬於這兩個集合，而且對 `Test01` 參數集而言是必要的，但 `Test02` 參數集則是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="af7a2-143">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test02")]
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
private string sharedParam;
```
