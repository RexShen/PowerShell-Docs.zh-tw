---
title: 定義選取範圍集合 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 95eeb037b3b9190fec1212a68029624993f3fd9f
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692291"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="a061e-102">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="a061e-102">Defining Selection Sets</span></span>

<span data-ttu-id="a061e-103">建立多個視圖和控制項時，您可以定義稱為選取集的一組物件。</span><span class="sxs-lookup"><span data-stu-id="a061e-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="a061e-104">選取集可讓您一次定義物件，而不需要針對每個視圖或控制項重複定義它們。</span><span class="sxs-lookup"><span data-stu-id="a061e-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="a061e-105">一般而言，當您有一組相關的 .NET 物件時，會使用選取範圍。</span><span class="sxs-lookup"><span data-stu-id="a061e-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="a061e-106">例如，格式配置 `FileSystem` 檔案（types.ps1xml）會定義數個 views 使用的檔案系統類型的選擇集。</span><span class="sxs-lookup"><span data-stu-id="a061e-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="a061e-107">定義和參考選擇集的位置</span><span class="sxs-lookup"><span data-stu-id="a061e-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="a061e-108">您可以將選取範圍定義為可供格式檔案中定義的所有視圖和控制項使用的一般資料的一部分。</span><span class="sxs-lookup"><span data-stu-id="a061e-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="a061e-109">下列範例顯示如何定義三個選取範圍。</span><span class="sxs-lookup"><span data-stu-id="a061e-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="a061e-110">您可以透過下列方式參考選擇集：</span><span class="sxs-lookup"><span data-stu-id="a061e-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="a061e-111">每個 view 都有一個專案 `ViewSelectedBy` ，用來定義要使用 view 來顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="a061e-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="a061e-112">`ViewSelectedBy`元素具有 `SelectionSetName` 子專案，可指定所有視圖定義所使用的選擇集。</span><span class="sxs-lookup"><span data-stu-id="a061e-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="a061e-113">您可以從視圖參考的選擇集數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="a061e-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="a061e-114">在視圖或控制項的每個定義中， `EntrySelectedBy` 元素會使用該定義來定義要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="a061e-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="a061e-115">通常，視圖或控制項只有一個定義，因此物件是由元素所定義 `ViewSelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="a061e-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="a061e-116">`EntrySelectedBy`定義的元素具有 `SelectionSetName` 指定選取集的子項目。</span><span class="sxs-lookup"><span data-stu-id="a061e-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="a061e-117">如果您指定定義的選取範圍，就不能指定元素的任何其他子項目 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="a061e-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="a061e-118">在視圖或控制項的每個定義中，專案 `SelectionCondition` 可以用來指定使用定義時的條件。</span><span class="sxs-lookup"><span data-stu-id="a061e-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="a061e-119">`SelectionCondition`元素具有 `SelectionSetName` 子專案，可指定觸發條件的選擇集。</span><span class="sxs-lookup"><span data-stu-id="a061e-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="a061e-120">當選取範圍中定義的任何物件顯示時，就會觸發此條件。</span><span class="sxs-lookup"><span data-stu-id="a061e-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="a061e-121">如需如何設定這些條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a061e-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="a061e-122">選擇集範例</span><span class="sxs-lookup"><span data-stu-id="a061e-122">Selection Set Example</span></span>

<span data-ttu-id="a061e-123">下列範例顯示直接從 Windows PowerShell 所提供的格式化檔案中取得的選擇集 `FileSystem` 。</span><span class="sxs-lookup"><span data-stu-id="a061e-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="a061e-124">如需其他 Windows PowerShell 格式化檔案的詳細資訊，請參閱[Windows Powershell 格式化](./powershell-formatting-files.md)檔案。</span><span class="sxs-lookup"><span data-stu-id="a061e-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

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

<span data-ttu-id="a061e-125">在資料表視圖的元素中，會參考先前的選取專案集 `ViewSelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="a061e-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

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

## <a name="xml-elements"></a><span data-ttu-id="a061e-126">XML 元素</span><span class="sxs-lookup"><span data-stu-id="a061e-126">XML Elements</span></span>

 <span data-ttu-id="a061e-127">您可以定義的選擇集數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="a061e-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="a061e-128">下列 XML 元素可用來建立選取專案集。</span><span class="sxs-lookup"><span data-stu-id="a061e-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="a061e-129">[SelectionSets](./selectionsets-element-format.md)元素會定義格式檔案的視圖和控制項所參考的 .net 物件集合。</span><span class="sxs-lookup"><span data-stu-id="a061e-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="a061e-130">[SelectionSet](./selectionset-element-format.md)元素會定義一組 .net 物件。</span><span class="sxs-lookup"><span data-stu-id="a061e-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="a061e-131">[Name](./name-element-for-selectionset-format.md)元素會指定用來參考選取集的名稱。</span><span class="sxs-lookup"><span data-stu-id="a061e-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="a061e-132">[Types](./types-element-for-selectionset-format.md)元素會指定選取集之物件的 .net 類型。</span><span class="sxs-lookup"><span data-stu-id="a061e-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="a061e-133">（在格式化檔案中，物件是由其 .NET 類型指定）。</span><span class="sxs-lookup"><span data-stu-id="a061e-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="a061e-134">下列 XML 元素可用來指定選擇集。</span><span class="sxs-lookup"><span data-stu-id="a061e-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="a061e-135">下列元素會指定要在視圖的所有定義中使用的選取範圍：</span><span class="sxs-lookup"><span data-stu-id="a061e-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

  - [<span data-ttu-id="a061e-136">ViewSelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

  - [<span data-ttu-id="a061e-137">GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="a061e-138">下列元素會指定單一 view 定義所使用的選擇集：</span><span class="sxs-lookup"><span data-stu-id="a061e-138">The following elements specify the selection set used by a single view definition:</span></span>

  - [<span data-ttu-id="a061e-139">ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="a061e-140">TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="a061e-141">WideControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="a061e-142">檢視之 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="a061e-143">下列專案指定通用和視圖控制項定義所使用的選擇集：</span><span class="sxs-lookup"><span data-stu-id="a061e-143">The following elements specify the selection set used by common and view control definitions:</span></span>

  - [<span data-ttu-id="a061e-144">檢視之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

  - [<span data-ttu-id="a061e-145">設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="a061e-146">下列專案會指定當您定義要展開的物件時，所使用的選擇集：</span><span class="sxs-lookup"><span data-stu-id="a061e-146">The following elements specify the selection set used when you define which object to expand:</span></span>

  - [<span data-ttu-id="a061e-147">EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="a061e-148">下列專案會指定選取條件所使用的選擇集。</span><span class="sxs-lookup"><span data-stu-id="a061e-148">The following elements specify the selection set used by selection conditions.</span></span>

  - [<span data-ttu-id="a061e-149">設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="a061e-150">檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

  - [<span data-ttu-id="a061e-151">檢視之 CustomControl 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

  - [<span data-ttu-id="a061e-152">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

  - [<span data-ttu-id="a061e-153">ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

  - [<span data-ttu-id="a061e-154">TableControl 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="a061e-155">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

  - [<span data-ttu-id="a061e-156">GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a061e-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="a061e-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a061e-157">See Also</span></span>

[<span data-ttu-id="a061e-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="a061e-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="a061e-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="a061e-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="a061e-160">名稱</span><span class="sxs-lookup"><span data-stu-id="a061e-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="a061e-161">型別</span><span class="sxs-lookup"><span data-stu-id="a061e-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="a061e-162">PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="a061e-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="a061e-163">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="a061e-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a061e-164">撰寫 PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="a061e-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
