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
# <a name="defining-selection-sets"></a>定義選取範圍集合

在建立多個檢視和控制項時，您可以定義所參考的物件集為選取項目集。 選取項目集可讓您定義的物件一次，而不必針對每一個檢視或控制重複定義。 一般而言，當您有一組相關的.NET 物件時，會使用選取項目集。 比方說，`FileSystem`格式化檔案 (FileSystem.format.ps1xml) 定義數種檢視所使用的檔案系統類型選取項目組。

## <a name="where-selection-sets-are-defined-and-referenced"></a>選取項目集，會定義和參考

您可以定義選取項目集可供所有檢視和控制項的格式化檔案中定義的一般資料的一部分。 下列範例示範如何定義三個選取項目集。

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

您可以參考的選取項目以下列方式設定：

- 每個檢視有`ViewSelectedBy`項目會定義要使用檢視來顯示哪些物件。 `ViewSelectedBy`項目具有`SelectionSetName`子項目，指定選取項目集的檢視使用的所有定義。 沒有任何限制，您可以從檢視參考的選取項目集數目。

- 在每個定義的檢視或控制項，`EntrySelectedBy`項目會定義哪些物件會顯示使用該定義。 通常是檢視或控制項有只有一個定義因此物件由定義`ViewSelectedBy`項目。 `EntrySelectedBy`定義的項目具有`SelectionSetName`指定選取項目集的子項目。 如果您指定定義設定的選取項目時，您不能指定任何其他子項目的`EntrySelectedBy`項目。

- 在每個定義的檢視或控制項，`SelectionCondition`項目可用來指定當使用定義的條件。 `SelectionCondition`項目具有`SelectionSetName`子項目會指定選取項目設定的觸發條件。 會顯示任何選取項目集合中定義的物件時，會觸發條件。 如需如何設定這些條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。

## <a name="selection-set-example"></a>選取項目集範例

下列範例顯示的選取項目集直接取自`FileSystem`格式化 Windows PowerShell 所提供的檔案。 如需有關其他 Windows PowerShell 格式化檔案的詳細資訊，請參閱 < [Windows PowerShell 格式化檔案](./powershell-formatting-files.md)。

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

中會參考先前的選取項目集`ViewSelectedBy`資料表檢視項目。

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

## <a name="xml-elements"></a>XML 項目

 沒有任何限制，您可以定義的選取項目集數目。 下列 XML 元素用來建立選取項目集。

- [SelectionSets](./selectionsets-element-format.md)項目會定義檢視所參考的.NET 物件的集合和控制項的格式化檔案。

- [SelectionSet](./selectionset-element-format.md)項目會定義一組.NET 物件。

- [名稱](./name-element-for-selectionset-format.md)項目會指定用來參考的選取項目集的名稱。

- [型別](./types-element-for-selectionset-format.md)項目會指定.NET 類型的選取項目集的物件。 （在格式化檔案，物件是由指定它們的.NET 型別。）

 下列 XML 元素用來指定選取項目集。

- 下列項目會指定設定為使用中的檢視所有定義的選取項目：

    - [SelectionSetName ViewSelectedBy （格式） 的項目](./selectionsetname-element-for-viewselectedby-format.md)

    - [GroupBy （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- 下列項目會指定單一檢視定義所使用的選取項目集：

    - [ListControl （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [TableControl （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [WideControl （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [CustomControl 檢視 （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- 下列項目會指定使用一般的選取項目集及檢視的控制項定義：

    - [用於檢視 （格式） 的控制項 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [SelectionSetName EntrySelectedBy 組態 （格式） 的控制項的項目](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- 下列項目會指定用於當您定義的物件，以展開選取項目集：

    - [EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- 下列項目會指定所選取條件使用的選取項目集。

    - [SelectionSetName SelectionCondition 組態 （格式） 的控制項的項目](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [用於檢視 （格式） 的控制項 SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [CustomControl 檢視 （格式） 的 SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [針對 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [針對 ListEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [TableControl （格式） 的 EntrySelectedBy 的 SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [GroupBy （格式） 的 SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>另請參閱

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[名稱](./name-element-for-selectionset-format.md)

[型別](./types-element-for-selectionset-format.md)

[PowerShell 格式化檔案](./powershell-formatting-files.md)

[定義何時顯示資料的條件](./defining-conditions-for-displaying-data.md)

[撰寫 PowerShell 格式和類型的檔案](./writing-a-powershell-formatting-file.md)
