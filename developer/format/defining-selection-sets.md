---
title: 定義選取範圍 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066306"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="3cf16-102">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="3cf16-102">Defining Selection Sets</span></span>

<span data-ttu-id="3cf16-103">在建立多個檢視和控制項時，您可以定義所參考的物件集為選取項目集。</span><span class="sxs-lookup"><span data-stu-id="3cf16-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="3cf16-104">選取項目集可讓您定義的物件一次，而不必針對每一個檢視或控制重複定義。</span><span class="sxs-lookup"><span data-stu-id="3cf16-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="3cf16-105">一般而言，當您有一組相關的.NET 物件時，會使用選取項目集。</span><span class="sxs-lookup"><span data-stu-id="3cf16-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="3cf16-106">比方說，`FileSystem`格式化檔案 (FileSystem.format.ps1xml) 定義數種檢視所使用的檔案系統類型選取項目組。</span><span class="sxs-lookup"><span data-stu-id="3cf16-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="3cf16-107">選取項目集，會定義和參考</span><span class="sxs-lookup"><span data-stu-id="3cf16-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="3cf16-108">您可以定義選取項目集可供所有檢視和控制項的格式化檔案中定義的一般資料的一部分。</span><span class="sxs-lookup"><span data-stu-id="3cf16-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="3cf16-109">下列範例示範如何定義三個選取項目集。</span><span class="sxs-lookup"><span data-stu-id="3cf16-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="3cf16-110">您可以參考的選取項目以下列方式設定：</span><span class="sxs-lookup"><span data-stu-id="3cf16-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="3cf16-111">每個檢視有`ViewSelectedBy`項目會定義要使用檢視來顯示哪些物件。</span><span class="sxs-lookup"><span data-stu-id="3cf16-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="3cf16-112">`ViewSelectedBy`項目具有`SelectionSetName`子項目，指定選取項目集的檢視使用的所有定義。</span><span class="sxs-lookup"><span data-stu-id="3cf16-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="3cf16-113">沒有任何限制，您可以從檢視參考的選取項目集數目。</span><span class="sxs-lookup"><span data-stu-id="3cf16-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="3cf16-114">在每個定義的檢視或控制項，`EntrySelectedBy`項目會定義哪些物件會顯示使用該定義。</span><span class="sxs-lookup"><span data-stu-id="3cf16-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="3cf16-115">通常是檢視或控制項有只有一個定義因此物件由定義`ViewSelectedBy`項目。</span><span class="sxs-lookup"><span data-stu-id="3cf16-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="3cf16-116">`EntrySelectedBy`定義的項目具有`SelectionSetName`指定選取項目集的子項目。</span><span class="sxs-lookup"><span data-stu-id="3cf16-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="3cf16-117">如果您指定定義設定的選取項目時，您不能指定任何其他子項目的`EntrySelectedBy`項目。</span><span class="sxs-lookup"><span data-stu-id="3cf16-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="3cf16-118">在每個定義的檢視或控制項，`SelectionCondition`項目可用來指定當使用定義的條件。</span><span class="sxs-lookup"><span data-stu-id="3cf16-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="3cf16-119">`SelectionCondition`項目具有`SelectionSetName`子項目會指定選取項目設定的觸發條件。</span><span class="sxs-lookup"><span data-stu-id="3cf16-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="3cf16-120">會顯示任何選取項目集合中定義的物件時，會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="3cf16-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="3cf16-121">如需如何設定這些條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="3cf16-122">選取項目集範例</span><span class="sxs-lookup"><span data-stu-id="3cf16-122">Selection Set Example</span></span>

<span data-ttu-id="3cf16-123">下列範例顯示的選取項目集直接取自`FileSystem`格式化 Windows PowerShell 所提供的檔案。</span><span class="sxs-lookup"><span data-stu-id="3cf16-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="3cf16-124">如需有關其他 Windows PowerShell 格式化檔案的詳細資訊，請參閱 < [Windows PowerShell 格式化檔案](./powershell-formatting-files.md)。</span><span class="sxs-lookup"><span data-stu-id="3cf16-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

<span data-ttu-id="3cf16-125">中會參考先前的選取項目集`ViewSelectedBy`資料表檢視項目。</span><span class="sxs-lookup"><span data-stu-id="3cf16-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a><span data-ttu-id="3cf16-126">XML 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-126">XML Elements</span></span>

 <span data-ttu-id="3cf16-127">沒有任何限制，您可以定義的選取項目集數目。</span><span class="sxs-lookup"><span data-stu-id="3cf16-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="3cf16-128">下列 XML 元素用來建立選取項目集。</span><span class="sxs-lookup"><span data-stu-id="3cf16-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="3cf16-129">[SelectionSets](./selectionsets-element-format.md)項目會定義檢視所參考的.NET 物件的集合和控制項的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="3cf16-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="3cf16-130">[SelectionSet](./selectionset-element-format.md)項目會定義一組.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="3cf16-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="3cf16-131">[名稱](./name-element-for-selectionset-format.md)項目會指定用來參考的選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="3cf16-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="3cf16-132">[型別](./types-element-for-selectionset-format.md)項目會指定.NET 類型的選取項目集的物件。</span><span class="sxs-lookup"><span data-stu-id="3cf16-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="3cf16-133">（在格式化檔案，物件是由指定它們的.NET 型別。）</span><span class="sxs-lookup"><span data-stu-id="3cf16-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="3cf16-134">下列 XML 元素用來指定選取項目集。</span><span class="sxs-lookup"><span data-stu-id="3cf16-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="3cf16-135">下列項目會指定設定為使用中的檢視所有定義的選取項目：</span><span class="sxs-lookup"><span data-stu-id="3cf16-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="3cf16-136">SelectionSetName ViewSelectedBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="3cf16-137">GroupBy （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="3cf16-138">下列項目會指定單一檢視定義所使用的選取項目集：</span><span class="sxs-lookup"><span data-stu-id="3cf16-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="3cf16-139">ListControl （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="3cf16-140">TableControl （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="3cf16-141">WideControl （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="3cf16-142">CustomControl 檢視 （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="3cf16-143">下列項目會指定使用一般的選取項目集及檢視的控制項定義：</span><span class="sxs-lookup"><span data-stu-id="3cf16-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="3cf16-144">用於檢視 （格式） 的控制項 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="3cf16-145">SelectionSetName EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="3cf16-146">下列項目會指定用於當您定義的物件，以展開選取項目集：</span><span class="sxs-lookup"><span data-stu-id="3cf16-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="3cf16-147">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="3cf16-148">下列項目會指定所選取條件使用的選取項目集。</span><span class="sxs-lookup"><span data-stu-id="3cf16-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="3cf16-149">SelectionSetName SelectionCondition 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="3cf16-150">用於檢視 （格式） 的控制項 SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="3cf16-151">CustomControl 檢視 （格式） 的 SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="3cf16-152">針對 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="3cf16-153">針對 ListEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="3cf16-154">TableControl （格式） 的 EntrySelectedBy 的 SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="3cf16-155">針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="3cf16-156">GroupBy （格式） 的 SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="3cf16-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="3cf16-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cf16-157">See Also</span></span>

[<span data-ttu-id="3cf16-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="3cf16-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="3cf16-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="3cf16-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="3cf16-160">名稱</span><span class="sxs-lookup"><span data-stu-id="3cf16-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="3cf16-161">型別</span><span class="sxs-lookup"><span data-stu-id="3cf16-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="3cf16-162">PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="3cf16-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="3cf16-163">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="3cf16-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3cf16-164">撰寫 PowerShell 格式和類型的檔案</span><span class="sxs-lookup"><span data-stu-id="3cf16-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
