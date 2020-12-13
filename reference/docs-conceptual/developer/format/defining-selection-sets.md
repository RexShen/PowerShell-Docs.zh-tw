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
# <a name="defining-selection-sets"></a>定義選取範圍集合

建立多個視圖和控制項時，您可以定義一組稱為選取集合的物件。 選取集可讓您一次定義物件，而不需要為每個視圖或控制項重複定義這些物件。 一般來說，當您有一組相關的 .NET 物件時，會使用選取集。 例如，格式化檔案 `FileSystem` ( # B0 xml) 會定義許多視圖所使用的一組檔案系統類型。

## <a name="where-selection-sets-are-defined-and-referenced"></a>定義和參考選取集的位置

您可以將選取範圍定義為一般資料的一部分，以供在格式化檔案中定義的所有視圖和控制項使用。 下列範例示範如何定義三個選取集。

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

您可以透過下列方式參考選取集合：

- 每個視圖都有一個專案 `ViewSelectedBy` ，用來定義要使用視圖來顯示的物件。 `ViewSelectedBy` `SelectionSetName` 專案具有子專案，此專案會指定視圖的所有定義所使用的選取集。 您可以從視圖參考的選取集合數目沒有任何限制。

- 在每個 view 或 control 的定義中，專案 `EntrySelectedBy` 會定義使用該定義所顯示的物件。 視圖或控制項通常只有一個定義，因此物件是由元素所定義 `ViewSelectedBy` 。 `EntrySelectedBy`定義的元素具有 `SelectionSetName` 指定選取專案集的子專案。 如果您指定定義的選取範圍，就不能指定專案的任何其他子項目 `EntrySelectedBy` 。

- 在每個 view 或 control 的定義中， `SelectionCondition` 元素都可以用來指定使用定義的條件。 `SelectionCondition`元素有 `SelectionSetName` 子項目，可指定觸發條件的選取集。 當選取專案集合中定義的任何物件顯示時，就會觸發此條件。 如需如何設定這些條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

## <a name="selection-set-example"></a>選擇集範例

下列範例顯示的是從 Windows PowerShell 所提供的格式化檔案中直接取得的選取集 `FileSystem` 。 如需其他 Windows PowerShell 格式檔案的詳細資訊，請參閱 [Windows PowerShell 格式化](./powershell-formatting-files.md)檔案。

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

在資料表視圖的元素中，會參考先前的選取集 `ViewSelectedBy` 。

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

 您可以定義的選擇集數目沒有任何限制。 下列 XML 元素可用來建立選取集。

- [SelectionSets](./selectionsets-element-format.md)元素定義了格式化檔案的視圖和控制項所參考的 .net 物件集合。

- [SelectionSet](./selectionset-element-format.md)元素會定義一組 .net 物件。

- [Name](./name-element-for-selectionset-format.md)元素會指定用來參考選取集的名稱。

- [Types](./types-element-for-selectionset-format.md)元素會指定選取專案集合之物件的 .net 類型。  (在格式化檔案中，物件是由其 .NET 類型所指定。 ) 

 下列 XML 元素可用來指定選取集。

- 下列專案會指定要在視圖的所有定義中使用的選取範圍：

  - [ViewSelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-viewselectedby-format.md)

  - [GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- 下列元素會指定單一視圖定義所使用的選取集：

  - [ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

  - [TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

  - [WideControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

  - [檢視之 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- 下列元素會指定通用和 view 控制項定義所使用的選取集：

  - [檢視之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

  - [設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- 下列元素會指定當您定義要展開的物件時，所使用的選取集：

  - [EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- 下列元素會指定選取條件所使用的選取集。

  - [設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

  - [檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

  - [檢視之 CustomControl 的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

  - [EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

  - [ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

  - [TableControl 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

  - [WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

  - [GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>另請參閱

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[名稱](./name-element-for-selectionset-format.md)

[類型](./types-element-for-selectionset-format.md)

[PowerShell 格式設定檔案](./powershell-formatting-files.md)

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[撰寫 PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
