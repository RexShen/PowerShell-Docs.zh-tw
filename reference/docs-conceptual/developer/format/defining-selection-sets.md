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
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368847"
---
# <a name="defining-selection-sets"></a>定義選取範圍集合

建立多個視圖和控制項時，您可以定義稱為選取集的一組物件。 選取集可讓您一次定義物件，而不需要針對每個視圖或控制項重複定義它們。 一般而言，當您有一組相關的 .NET 物件時，會使用選取範圍。 例如，`FileSystem` 格式設定檔案（types.ps1xml）會定義數個 views 使用的檔案系統類型的選取集合。

## <a name="where-selection-sets-are-defined-and-referenced"></a>定義和參考選擇集的位置

您可以將選取範圍定義為可供格式檔案中定義的所有視圖和控制項使用的一般資料的一部分。 下列範例顯示如何定義三個選取範圍。

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

您可以透過下列方式參考選擇集：

- 每個 view 都有一個 `ViewSelectedBy` 專案，可定義要使用 view 來顯示的物件。 `ViewSelectedBy` 元素具有 `SelectionSetName` 子項目，可指定所有視圖定義所使用的選取範圍。 您可以從視圖參考的選擇集數目沒有限制。

- 在視圖或控制項的每個定義中，`EntrySelectedBy` 元素會使用該定義來定義要顯示的物件。 通常，視圖或控制項只有一個定義，因此物件是由 `ViewSelectedBy` 元素所定義。 定義的 `EntrySelectedBy` 元素具有指定選取範圍的 `SelectionSetName` 子項目。 如果您指定定義的選取範圍，就不能指定 `EntrySelectedBy` 元素的任何其他子項目。

- 在視圖或控制項的每個定義中，`SelectionCondition` 元素可以用來指定使用定義時的條件。 `SelectionCondition` 元素具有 `SelectionSetName` 子項目，可指定觸發條件的選取範圍。 當選取範圍中定義的任何物件顯示時，就會觸發此條件。 如需如何設定這些條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

## <a name="selection-set-example"></a>選擇集範例

下列範例顯示的是直接從 Windows PowerShell 所提供的 `FileSystem` 格式檔案取得的選擇集。 如需其他 Windows PowerShell 格式化檔案的詳細資訊，請參閱[Windows Powershell 格式化](./powershell-formatting-files.md)檔案。

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

在資料表視圖的 `ViewSelectedBy` 元素中，會參考先前的選取專案集。

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

## <a name="xml-elements"></a>XML 元素

 您可以定義的選擇集數目沒有限制。 下列 XML 元素可用來建立選取專案集。

- [SelectionSets](./selectionsets-element-format.md)元素會定義格式檔案的視圖和控制項所參考的 .net 物件集合。

- [SelectionSet](./selectionset-element-format.md)元素會定義一組 .net 物件。

- [Name](./name-element-for-selectionset-format.md)元素會指定用來參考選取集的名稱。

- [Types](./types-element-for-selectionset-format.md)元素會指定選取集之物件的 .net 類型。 （在格式化檔案中，物件是由其 .NET 類型指定）。

 下列 XML 元素可用來指定選擇集。

- 下列元素會指定要在視圖的所有定義中使用的選取範圍：

    - [ViewSelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-viewselectedby-format.md)

    - [GroupBy 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- 下列元素會指定單一 view 定義所使用的選擇集：

    - [ListControl 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [TableControl 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [WideControl 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [CustomControl for View 的之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- 下列專案指定通用和視圖控制項定義所使用的選擇集：

    - [View 之控制項的之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [設定之控制項的之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- 下列專案會指定當您定義要展開的物件時，所使用的選擇集：

    - [EnumerableExpansion 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- 下列專案會指定選取條件所使用的選擇集。

    - [設定之控制項的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [View 之控制項的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [CustomControl for View 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [ListEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [TableControl 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [WideEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [GroupBy 之 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>另請參閱

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[名稱](./name-element-for-selectionset-format.md)

[各種](./types-element-for-selectionset-format.md)

[PowerShell 格式化檔案](./powershell-formatting-files.md)

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[撰寫 PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
