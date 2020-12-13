---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 參數集
description: Cmdlet 參數集
ms.openlocfilehash: e84af7faf5b7459d8dbe06847526efe804e2c5e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668281"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="7d1c8-103">Cmdlet 參數集</span><span class="sxs-lookup"><span data-stu-id="7d1c8-103">Cmdlet parameter sets</span></span>

<span data-ttu-id="7d1c8-104">PowerShell 會使用參數集，讓您撰寫可針對不同案例執行不同動作的單一 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-104">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="7d1c8-105">參數集可讓您向使用者公開不同的參數。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-105">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="7d1c8-106">和，根據使用者指定的參數傳回不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-106">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="7d1c8-107">參數集的範例</span><span class="sxs-lookup"><span data-stu-id="7d1c8-107">Examples of parameter sets</span></span>

<span data-ttu-id="7d1c8-108">例如，PowerShell Cmdlet 會 `Get-EventLog` 根據使用者是否指定 **清單** 或 **LogName** 參數，傳回不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-108">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="7d1c8-109">如果指定了 **List** 參數，Cmdlet 會傳回記錄檔本身的相關資訊，但不會傳回它們所包含的事件資訊。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-109">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="7d1c8-110">如果指定了 **LogName** 參數，Cmdlet 會傳回特定事件記錄檔中事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-110">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="7d1c8-111">**List** 和 **LogName** 參數會識別兩個不同的參數集。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-111">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="7d1c8-112">唯一參數</span><span class="sxs-lookup"><span data-stu-id="7d1c8-112">Unique parameter</span></span>

<span data-ttu-id="7d1c8-113">每個參數集都必須有一個唯一的參數，PowerShell 執行時間會使用此參數來公開適當的參數集。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-113">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="7d1c8-114">可能的話，唯一的參數應該是必要參數。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-114">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="7d1c8-115">當參數是必要參數時，使用者必須指定參數，且 PowerShell 執行時間會使用該參數來識別參數集。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-115">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="7d1c8-116">如果您的 Cmdlet 是設計為在未指定任何參數的情況下執行，則唯一的參數不可以是必要的。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-116">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="7d1c8-117">多個參數集</span><span class="sxs-lookup"><span data-stu-id="7d1c8-117">Multiple parameter sets</span></span>

<span data-ttu-id="7d1c8-118">在下圖中，左邊的資料行顯示三個有效的參數集。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-118">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="7d1c8-119">**參數 A** 對第一個參數集而言是唯一的，第二個參數集的 **參數 B** 是唯一的，而 **參數 C** 對第三個參數集是唯一的。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-119">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="7d1c8-120">在右邊的資料行中，參數集沒有唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-120">In the right column, the parameter sets don't have a unique parameter.</span></span>

![參數集的圖例](media/cmdlet-parameter-sets/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="7d1c8-122">參數集需求</span><span class="sxs-lookup"><span data-stu-id="7d1c8-122">Parameter set requirements</span></span>

<span data-ttu-id="7d1c8-123">下列需求適用于所有參數集。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-123">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="7d1c8-124">每個參數集都必須至少有一個唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-124">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="7d1c8-125">可能的話，請將此參數設為必要參數。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-125">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="7d1c8-126">包含多個位置參數的參數集必須定義每個參數的唯一位置。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-126">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="7d1c8-127">沒有兩個位置參數可以指定相同的位置。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-127">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="7d1c8-128">只有一個集合中的參數可以宣告 `ValueFromPipeline` 具有值的關鍵字 `true` 。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-128">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="7d1c8-129">多個參數可以定義 `ValueFromPipelineByPropertyName` 具有值的關鍵字 `true` 。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-129">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="7d1c8-130">如果未指定參數的參數集，參數將屬於所有參數集。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-130">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="7d1c8-131">針對 Cmdlet 或函式，有32個參數集的限制。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-131">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="7d1c8-132">預設參數集</span><span class="sxs-lookup"><span data-stu-id="7d1c8-132">Default parameter sets</span></span>

<span data-ttu-id="7d1c8-133">定義多個參數集時，您可以使用 `DefaultParameterSetName` **Cmdlet** 屬性的關鍵字來指定預設參數集。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-133">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="7d1c8-134">如果 PowerShell 無法根據命令所提供的資訊來判斷要使用的參數集，則會使用預設參數集。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-134">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="7d1c8-135">如需 **Cmdlet** 屬性的詳細資訊，請參閱 [Cmdlet 屬性聲明](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-135">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="7d1c8-136">宣告參數集</span><span class="sxs-lookup"><span data-stu-id="7d1c8-136">Declaring parameter sets</span></span>

<span data-ttu-id="7d1c8-137">若要建立參數集，您必須在 `ParameterSetName` 針對參數集內的每個參數宣告 **參數** 屬性時，指定關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-137">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="7d1c8-138">對於屬於多個參數集的參數，請為每個參數集加入 **參數** 屬性。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-138">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="7d1c8-139">這個屬性可讓您針對每個參數集定義不同的參數。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-139">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="7d1c8-140">例如，您可以在一個集合中將參數定義為強制，並在另一個集合中定義選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-140">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="7d1c8-141">不過，每個參數集都必須包含一個唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-141">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="7d1c8-142">如需詳細資訊，請參閱 [參數屬性聲明](parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-142">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="7d1c8-143">在下列範例中，使用者 **名稱** 參數是參數集的唯一參數 `Test01` ，而 **ComputerName** 參數是參數集的唯一參數 `Test02` 。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-143">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="7d1c8-144">**SharedParam** 參數屬於這兩個集合，而且對參數集而言是必要的， `Test01` 但參數集則是選擇性的 `Test02` 。</span><span class="sxs-lookup"><span data-stu-id="7d1c8-144">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

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
