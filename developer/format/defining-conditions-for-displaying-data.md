---
title: 定義用於顯示資料的條件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066323"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="5ea84-102">定義用於顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="5ea84-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="5ea84-103">在定義檢視或控制項所顯示的資料時，您可以指定要顯示的資料必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="5ea84-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="5ea84-104">可以觸發條件，依特定屬性，或當指令碼或屬性的值評估為`true`。</span><span class="sxs-lookup"><span data-stu-id="5ea84-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="5ea84-105">當符合選取條件時，可檢視或控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="5ea84-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="5ea84-106">指定選取條件的定義</span><span class="sxs-lookup"><span data-stu-id="5ea84-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="5ea84-107">當建立檢視或控制項，定義`EntrySelectedBy`項目用來指定哪些物件會使用定義或何種條件必須存在，要使用的定義。</span><span class="sxs-lookup"><span data-stu-id="5ea84-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="5ea84-108">藉由指定的條件`SelectionCondition`項目。</span><span class="sxs-lookup"><span data-stu-id="5ea84-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="5ea84-109">在下列範例中，選擇條件指定的資料表檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="5ea84-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="5ea84-110">在此範例中，此定義會用來評估指定的指令碼時，才`true`。</span><span class="sxs-lookup"><span data-stu-id="5ea84-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="5ea84-111">沒有任何限制，選擇條件，您可以檢視或控制項的定義中指定的數目。</span><span class="sxs-lookup"><span data-stu-id="5ea84-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="5ea84-112">唯一的條件如下所示：</span><span class="sxs-lookup"><span data-stu-id="5ea84-112">The only requirements are the following:</span></span>

- <span data-ttu-id="5ea84-113">選取條件必須指定一個屬性名稱或條件，觸發程序的指令碼，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="5ea84-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="5ea84-114">選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="5ea84-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="5ea84-115">指定選取條件的項目</span><span class="sxs-lookup"><span data-stu-id="5ea84-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="5ea84-116">您也可以指定當使用清單檢視或控制項的項目包括`ItemSelectionCondition`項目定義中的項目。</span><span class="sxs-lookup"><span data-stu-id="5ea84-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="5ea84-117">在下列範例中，選擇條件被指定之清單檢視項目。</span><span class="sxs-lookup"><span data-stu-id="5ea84-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="5ea84-118">在此範例中，項目用來評估指令碼時，才`true`。</span><span class="sxs-lookup"><span data-stu-id="5ea84-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="5ea84-119">您可以指定只有一個選擇條件的項目。</span><span class="sxs-lookup"><span data-stu-id="5ea84-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="5ea84-120">與條件必須指定一個屬性名稱或條件，觸發程序的指令碼，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="5ea84-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="5ea84-121">XML 項目</span><span class="sxs-lookup"><span data-stu-id="5ea84-121">XML Elements</span></span>

 <span data-ttu-id="5ea84-122">下列 XML 元素用來建立選取範圍的條件。</span><span class="sxs-lookup"><span data-stu-id="5ea84-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="5ea84-123">下列項目指定檢視定義的選取範圍的條件：</span><span class="sxs-lookup"><span data-stu-id="5ea84-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="5ea84-124">TableControl （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="5ea84-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="5ea84-125">ListControl （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="5ea84-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="5ea84-126">WideControl （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="5ea84-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="5ea84-127">CustomControl （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="5ea84-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="5ea84-128">下列項目指定的選取範圍的一般條件並檢視控制定義：</span><span class="sxs-lookup"><span data-stu-id="5ea84-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="5ea84-129">SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="5ea84-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="5ea84-130">用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="5ea84-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="5ea84-131">下列項目會指定擴充集合物件的選取範圍條件：</span><span class="sxs-lookup"><span data-stu-id="5ea84-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="5ea84-132">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="5ea84-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="5ea84-133">下列項目會指定選取條件來顯示資料的新群組：</span><span class="sxs-lookup"><span data-stu-id="5ea84-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="5ea84-134">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="5ea84-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="5ea84-135">下列項目會指定清單檢視項目選取項目條件：</span><span class="sxs-lookup"><span data-stu-id="5ea84-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="5ea84-136">ItemSelectionCondition ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="5ea84-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="5ea84-137">下列項目會指定控制項的項目選取範圍條件：</span><span class="sxs-lookup"><span data-stu-id="5ea84-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="5ea84-138">ItemSelectionCondition ExpressionBinding 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="5ea84-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="5ea84-139">用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="5ea84-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="5ea84-140">ItemSelectionCondition CustomControl （格式） 的 ExpressionBinding 的項目</span><span class="sxs-lookup"><span data-stu-id="5ea84-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="5ea84-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ea84-141">See Also</span></span>

[<span data-ttu-id="5ea84-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="5ea84-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
