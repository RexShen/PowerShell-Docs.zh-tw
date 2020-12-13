---
ms.date: 09/13/2016
ms.topic: reference
title: 定義用於顯示資料的條件
description: 定義用於顯示資料的條件
ms.openlocfilehash: 9a8b7a618da8c64de978c13b527435a2d7793677
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660314"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="bf6c4-103">定義用於顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="bf6c4-103">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="bf6c4-104">定義 view 或控制項所顯示的資料時，您可以指定必須存在才能顯示資料的條件。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-104">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="bf6c4-105">條件可以由特定屬性觸發，或當腳本或屬性值評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-105">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="bf6c4-106">當符合選取條件時，就會使用 view 或 control 的定義。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-106">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="bf6c4-107">指定定義的選取條件</span><span class="sxs-lookup"><span data-stu-id="bf6c4-107">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="bf6c4-108">當您建立 view 或 control 的定義時， `EntrySelectedBy` 會使用元素來指定哪些物件將使用定義，或必須有何種條件存在，才能使用定義。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-108">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="bf6c4-109">條件是由元素所指定 `SelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-109">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="bf6c4-110">在下列範例中，會針對資料表視圖的定義指定選取條件。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-110">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="bf6c4-111">在此範例中，只有在指定的腳本評估為時，才會使用定義 `true` 。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-111">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="bf6c4-112">您可以針對視圖或控制項的定義指定的選取條件數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-112">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="bf6c4-113">唯一的需求如下：</span><span class="sxs-lookup"><span data-stu-id="bf6c4-113">The only requirements are the following:</span></span>

- <span data-ttu-id="bf6c4-114">選取條件必須指定一個屬性名稱或腳本來觸發條件，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-114">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="bf6c4-115">選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-115">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="bf6c4-116">指定專案的選取條件</span><span class="sxs-lookup"><span data-stu-id="bf6c4-116">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="bf6c4-117">您也可以在專案定義中包含元素，以指定何時使用清單視圖或控制項的專案 `ItemSelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-117">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="bf6c4-118">在下列範例中，會針對清單視圖的專案指定選取條件。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-118">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="bf6c4-119">在此範例中，只有在將腳本評估為時，才會使用此專案 `true` 。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-119">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="bf6c4-120">您只能為專案指定一個選取條件。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-120">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="bf6c4-121">而且條件必須指定一個屬性名稱或腳本來觸發條件，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-121">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="bf6c4-122">XML 元素</span><span class="sxs-lookup"><span data-stu-id="bf6c4-122">XML Elements</span></span>

 <span data-ttu-id="bf6c4-123">下列 XML 元素可用來建立選取條件。</span><span class="sxs-lookup"><span data-stu-id="bf6c4-123">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="bf6c4-124">下列元素會指定視圖定義的選取條件：</span><span class="sxs-lookup"><span data-stu-id="bf6c4-124">The following elements specify selection conditions for view definitions:</span></span>

  - [<span data-ttu-id="bf6c4-125">TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bf6c4-125">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="bf6c4-126">ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bf6c4-126">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="bf6c4-127">WideControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bf6c4-127">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="bf6c4-128">CustomControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bf6c4-128">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="bf6c4-129">下列元素會指定通用和 view 控制項定義的選取條件：</span><span class="sxs-lookup"><span data-stu-id="bf6c4-129">The following elements specify selection conditions for common and view control definitions:</span></span>

  - [<span data-ttu-id="bf6c4-130">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bf6c4-130">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="bf6c4-131">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bf6c4-131">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="bf6c4-132">下列元素會指定展開集合物件的選取條件：</span><span class="sxs-lookup"><span data-stu-id="bf6c4-132">The following element specifies the selection condition for expanding collection objects:</span></span>

  - [<span data-ttu-id="bf6c4-133">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bf6c4-133">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="bf6c4-134">下列元素會指定用於顯示新資料群組的選取條件：</span><span class="sxs-lookup"><span data-stu-id="bf6c4-134">The following element specifies the selection condition for displaying a new group of data:</span></span>

  - [<span data-ttu-id="bf6c4-135">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bf6c4-135">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="bf6c4-136">下列元素會指定清單視圖的專案選取條件：</span><span class="sxs-lookup"><span data-stu-id="bf6c4-136">The following element specifies an item selection condition for a list view:</span></span>

  - [<span data-ttu-id="bf6c4-137">ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bf6c4-137">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="bf6c4-138">下列元素會指定控制項的專案選取條件：</span><span class="sxs-lookup"><span data-stu-id="bf6c4-138">The following elements specify an item selection condition for controls:</span></span>

  - [<span data-ttu-id="bf6c4-139">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bf6c4-139">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="bf6c4-140">檢視之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bf6c4-140">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

  - [<span data-ttu-id="bf6c4-141">CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bf6c4-141">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="bf6c4-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf6c4-142">See Also</span></span>

[<span data-ttu-id="bf6c4-143">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="bf6c4-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
