---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)
description: ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)
ms.openlocfilehash: 6fc5a2385fde3140abbc984e3da6a4dda483b2a8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645668"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)

指定使用此清單視圖專案的 .NET 型別。 可以針對清單專案指定的類型數目沒有任何限制。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 專案 (格式) ListEntries 專案 (格式) ListEntry 專案 (格式) 之 entryselectedby 專案的 ListEntry (格式) 之 entryselectedby 的 ListControl (格式) 

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `TypeName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|定義使用此清單專案的 .NET 型別，或必須存在才能使用此專案的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

每個清單專案都必須定義至少一個類型名稱、選取集或選取條件。

如需如何在清單視圖中使用這個元素的詳細資訊，請參閱 [清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例示範如何為清單視圖的專案指定選取集。

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[ListEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[適用于之 entryselectedby 的 ListEntry (格式的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
