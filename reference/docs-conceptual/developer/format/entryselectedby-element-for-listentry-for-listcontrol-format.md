---
title: ListControl (格式) 的 ListEntry 的之 entryselectedby 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d6ab1c08dd353da74d1a7d27c569d2fa86e083c3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774111"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>ListControl 之 ListEntry 的 EntrySelectedBy 元素 (格式)

定義使用此清單視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。 在大部分情況下，清單視圖只需要一個定義。 不過，如果您想要使用相同的清單視圖來顯示不同物件的不同資料，可以為清單視圖提供多個定義。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListControl (格式) ListEntry 元素，ListEntry 的 ListControl (格式) 之 entryselectedby 元素 (

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl (格式的之 entryselectedby 的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此清單視圖定義的條件。|
|[ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定一組使用此清單視圖定義的 .NET 類型。|
|[ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定使用此清單視圖定義的 .NET 類型。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListControl 的 ListEntry 元素 (格式)](./listentry-element-for-listcontrol-format.md)|定義清單資料列的顯示方式。|

## <a name="remarks"></a>備註

您必須為清單視圖定義指定至少一個類型、選擇集或選取條件。 您可以使用的子項目數目沒有上限。

選取條件是用來定義要使用的定義必須存在的條件，例如，當物件具有特定屬性或特定屬性值或腳本評估為時 `true` 。 如需選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

如需清單視圖之元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例顯示如何使用 .NET 型別名稱來定義清單視圖的物件。

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>另請參閱

[ListControl 的 ListEntry 元素 (格式)](./listentry-element-for-listcontrol-format.md)

[ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[建立清單檢視](./creating-a-list-view.md)

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
