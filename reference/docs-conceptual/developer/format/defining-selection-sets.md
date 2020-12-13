---
ms.date: 09/13/2016
ms.topic: reference
title: 定義選取範圍集合
description: 定義選取範圍集合
ms.openlocfilehash: d709a368a45623d56fdbf4e98a11a5e5f8a193fa
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648255"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="0afe3-103">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="0afe3-103">Defining Selection Sets</span></span>

<span data-ttu-id="0afe3-104">建立多個視圖和控制項時，您可以定義一組稱為選取集合的物件。</span><span class="sxs-lookup"><span data-stu-id="0afe3-104">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="0afe3-105">選取集可讓您一次定義物件，而不需要為每個視圖或控制項重複定義這些物件。</span><span class="sxs-lookup"><span data-stu-id="0afe3-105">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="0afe3-106">一般來說，當您有一組相關的 .NET 物件時，會使用選取集。</span><span class="sxs-lookup"><span data-stu-id="0afe3-106">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="0afe3-107">例如，格式化檔案 `FileSystem` ( # B0 xml) 會定義許多視圖所使用的一組檔案系統類型。</span><span class="sxs-lookup"><span data-stu-id="0afe3-107">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="0afe3-108">定義和參考選取集的位置</span><span class="sxs-lookup"><span data-stu-id="0afe3-108">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="0afe3-109">您可以將選取範圍定義為一般資料的一部分，以供在格式化檔案中定義的所有視圖和控制項使用。</span><span class="sxs-lookup"><span data-stu-id="0afe3-109">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="0afe3-110">下列範例示範如何定義三個選取集。</span><span class="sxs-lookup"><span data-stu-id="0afe3-110">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="0afe3-111">您可以透過下列方式參考選取集合：</span><span class="sxs-lookup"><span data-stu-id="0afe3-111">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="0afe3-112">每個視圖都有一個專案 `ViewSelectedBy` ，用來定義要使用視圖來顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="0afe3-112">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="0afe3-113">`ViewSelectedBy` `SelectionSetName` 專案具有子專案，此專案會指定視圖的所有定義所使用的選取集。</span><span class="sxs-lookup"><span data-stu-id="0afe3-113">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="0afe3-114">您可以從視圖參考的選取集合數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="0afe3-114">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="0afe3-115">在每個 view 或 control 的定義中，專案 `EntrySelectedBy` 會定義使用該定義所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="0afe3-115">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="0afe3-116">視圖或控制項通常只有一個定義，因此物件是由元素所定義 `ViewSelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="0afe3-116">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="0afe3-117">`EntrySelectedBy`定義的元素具有 `SelectionSetName` 指定選取專案集的子專案。</span><span class="sxs-lookup"><span data-stu-id="0afe3-117">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="0afe3-118">如果您指定定義的選取範圍，就不能指定專案的任何其他子項目 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="0afe3-118">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="0afe3-119">在每個 view 或 control 的定義中， `SelectionCondition` 元素都可以用來指定使用定義的條件。</span><span class="sxs-lookup"><span data-stu-id="0afe3-119">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="0afe3-120">`SelectionCondition`元素有 `SelectionSetName` 子項目，可指定觸發條件的選取集。</span><span class="sxs-lookup"><span data-stu-id="0afe3-120">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="0afe3-121">當選取專案集合中定義的任何物件顯示時，就會觸發此條件。</span><span class="sxs-lookup"><span data-stu-id="0afe3-121">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="0afe3-122">如需如何設定這些條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="0afe3-122">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="0afe3-123">選擇集範例</span><span class="sxs-lookup"><span data-stu-id="0afe3-123">Selection Set Example</span></span>

<span data-ttu-id="0afe3-124">下列範例顯示的是從 Windows PowerShell 所提供的格式化檔案中直接取得的選取集 `FileSystem` 。</span><span class="sxs-lookup"><span data-stu-id="0afe3-124">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="0afe3-125">如需其他 Windows PowerShell 格式檔案的詳細資訊，請參閱 [Windows PowerShell 格式化](./powershell-formatting-files.md)檔案。</span><span class="sxs-lookup"><span data-stu-id="0afe3-125">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

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

<span data-ttu-id="0afe3-126">在資料表視圖的元素中，會參考先前的選取集 `ViewSelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="0afe3-126">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

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

## <a name="xml-elements"></a><span data-ttu-id="0afe3-127">XML 元素</span><span class="sxs-lookup"><span data-stu-id="0afe3-127">XML Elements</span></span>

 <span data-ttu-id="0afe3-128">您可以定義的選擇集數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="0afe3-128">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="0afe3-129">下列 XML 元素可用來建立選取集。</span><span class="sxs-lookup"><span data-stu-id="0afe3-129">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="0afe3-130">[SelectionSets](./selectionsets-element-format.md)元素定義了格式化檔案的視圖和控制項所參考的 .net 物件集合。</span><span class="sxs-lookup"><span data-stu-id="0afe3-130">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="0afe3-131">[SelectionSet](./selectionset-element-format.md)元素會定義一組 .net 物件。</span><span class="sxs-lookup"><span data-stu-id="0afe3-131">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="0afe3-132">[Name](./name-element-for-selectionset-format.md)元素會指定用來參考選取集的名稱。</span><span class="sxs-lookup"><span data-stu-id="0afe3-132">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="0afe3-133">[Types](./types-element-for-selectionset-format.md)元素會指定選取專案集合之物件的 .net 類型。</span><span class="sxs-lookup"><span data-stu-id="0afe3-133">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="0afe3-134"> (在格式化檔案中，物件是由其 .NET 類型所指定。 ) </span><span class="sxs-lookup"><span data-stu-id="0afe3-134">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="0afe3-135">下列 XML 元素可用來指定選取集。</span><span class="sxs-lookup"><span data-stu-id="0afe3-135">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="0afe3-136">下列專案會指定要在視圖的所有定義中使用的選取範圍：</span><span class="sxs-lookup"><span data-stu-id="0afe3-136">The following element specifies the selection set to use in all the definitions of the view:</span></span>

  - [<span data-ttu-id="0afe3-137">ViewSelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-137">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

  - [<span data-ttu-id="0afe3-138">GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-138">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="0afe3-139">下列元素會指定單一視圖定義所使用的選取集：</span><span class="sxs-lookup"><span data-stu-id="0afe3-139">The following elements specify the selection set used by a single view definition:</span></span>

  - [<span data-ttu-id="0afe3-140">ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="0afe3-141">TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-141">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="0afe3-142">WideControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-142">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="0afe3-143">檢視之 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-143">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="0afe3-144">下列元素會指定通用和 view 控制項定義所使用的選取集：</span><span class="sxs-lookup"><span data-stu-id="0afe3-144">The following elements specify the selection set used by common and view control definitions:</span></span>

  - [<span data-ttu-id="0afe3-145">檢視之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-145">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

  - [<span data-ttu-id="0afe3-146">設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-146">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="0afe3-147">下列元素會指定當您定義要展開的物件時，所使用的選取集：</span><span class="sxs-lookup"><span data-stu-id="0afe3-147">The following elements specify the selection set used when you define which object to expand:</span></span>

  - [<span data-ttu-id="0afe3-148">EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-148">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="0afe3-149">下列元素會指定選取條件所使用的選取集。</span><span class="sxs-lookup"><span data-stu-id="0afe3-149">The following elements specify the selection set used by selection conditions.</span></span>

  - [<span data-ttu-id="0afe3-150">設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-150">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="0afe3-151">檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-151">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

  - [<span data-ttu-id="0afe3-152">檢視之 CustomControl 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-152">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

  - [<span data-ttu-id="0afe3-153">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

  - [<span data-ttu-id="0afe3-154">ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

  - [<span data-ttu-id="0afe3-155">TableControl 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="0afe3-156">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-156">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

  - [<span data-ttu-id="0afe3-157">GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0afe3-157">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="0afe3-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0afe3-158">See Also</span></span>

[<span data-ttu-id="0afe3-159">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="0afe3-159">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="0afe3-160">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="0afe3-160">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="0afe3-161">名稱</span><span class="sxs-lookup"><span data-stu-id="0afe3-161">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="0afe3-162">類型</span><span class="sxs-lookup"><span data-stu-id="0afe3-162">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="0afe3-163">PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="0afe3-163">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="0afe3-164">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="0afe3-164">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0afe3-165">撰寫 PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="0afe3-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
