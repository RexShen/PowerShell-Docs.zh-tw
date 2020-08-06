---
title: 定義用於顯示資料的條件 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13de078e681708b02e378b2c7d531032b2ffdc05
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774332"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="80919-102">定義用於顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="80919-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="80919-103">定義視圖或控制項所顯示的資料時，您可以指定必須存在的條件，才會顯示資料。</span><span class="sxs-lookup"><span data-stu-id="80919-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="80919-104">條件可以由特定屬性觸發，或在腳本或屬性值評估為時觸發 `true` 。</span><span class="sxs-lookup"><span data-stu-id="80919-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="80919-105">當符合選取條件時，會使用視圖或控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="80919-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="80919-106">指定定義的選取條件</span><span class="sxs-lookup"><span data-stu-id="80919-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="80919-107">建立視圖或控制項的定義時，會使用專案 `EntrySelectedBy` 來指定要使用定義的物件，或必須存在哪些條件，才能使用定義。</span><span class="sxs-lookup"><span data-stu-id="80919-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="80919-108">條件是由元素所指定 `SelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="80919-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="80919-109">在下列範例中，會針對資料表視圖的定義指定選取條件。</span><span class="sxs-lookup"><span data-stu-id="80919-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="80919-110">在此範例中，只有在指定的腳本評估為時，才會使用此定義 `true` 。</span><span class="sxs-lookup"><span data-stu-id="80919-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

<span data-ttu-id="80919-111">針對視圖或控制項的定義，您可以指定的選取條件數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="80919-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="80919-112">唯一的需求如下：</span><span class="sxs-lookup"><span data-stu-id="80919-112">The only requirements are the following:</span></span>

- <span data-ttu-id="80919-113">選取條件必須指定一個屬性名稱或腳本來觸發條件，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="80919-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="80919-114">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="80919-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="80919-115">指定專案的選取條件</span><span class="sxs-lookup"><span data-stu-id="80919-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="80919-116">您也可以在專案定義中包含元素，以指定何時使用清單視圖或控制項的專案 `ItemSelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="80919-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="80919-117">在下列範例中，會為清單視圖的專案指定選取條件。</span><span class="sxs-lookup"><span data-stu-id="80919-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="80919-118">在此範例中，只有在將腳本評估為時，才會使用此專案 `true` 。</span><span class="sxs-lookup"><span data-stu-id="80919-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="80919-119">您只能為一個專案指定一個選取條件。</span><span class="sxs-lookup"><span data-stu-id="80919-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="80919-120">而且條件必須指定一個屬性名稱或腳本來觸發條件，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="80919-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="80919-121">XML 元素</span><span class="sxs-lookup"><span data-stu-id="80919-121">XML Elements</span></span>

 <span data-ttu-id="80919-122">下列 XML 元素可用來建立選取條件。</span><span class="sxs-lookup"><span data-stu-id="80919-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="80919-123">下列元素會指定視圖定義的選取條件：</span><span class="sxs-lookup"><span data-stu-id="80919-123">The following elements specify selection conditions for view definitions:</span></span>

  - [<span data-ttu-id="80919-124">TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80919-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="80919-125">ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80919-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="80919-126">WideControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80919-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="80919-127">CustomControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80919-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="80919-128">下列專案會指定通用和視圖控制項定義的選取條件：</span><span class="sxs-lookup"><span data-stu-id="80919-128">The following elements specify selection conditions for common and view control definitions:</span></span>

  - [<span data-ttu-id="80919-129">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80919-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="80919-130">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80919-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="80919-131">下列元素會指定展開集合物件的選取條件：</span><span class="sxs-lookup"><span data-stu-id="80919-131">The following element specifies the selection condition for expanding collection objects:</span></span>

  - [<span data-ttu-id="80919-132">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80919-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="80919-133">下列元素會指定用於顯示新資料群組的選取條件：</span><span class="sxs-lookup"><span data-stu-id="80919-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

  - [<span data-ttu-id="80919-134">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80919-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="80919-135">下列元素指定清單視圖的專案選取條件：</span><span class="sxs-lookup"><span data-stu-id="80919-135">The following element specifies an item selection condition for a list view:</span></span>

  - [<span data-ttu-id="80919-136">ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80919-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="80919-137">下列元素會指定控制項的專案選取條件：</span><span class="sxs-lookup"><span data-stu-id="80919-137">The following elements specify an item selection condition for controls:</span></span>

  - [<span data-ttu-id="80919-138">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80919-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="80919-139">檢視之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80919-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

  - [<span data-ttu-id="80919-140">CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80919-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="80919-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80919-141">See Also</span></span>

[<span data-ttu-id="80919-142">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="80919-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
