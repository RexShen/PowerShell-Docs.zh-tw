---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ListItem 的 ScriptBlock 元素 (格式)
description: ListControl 之 ListItem 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 0635ac2622cc203a2dc895873621901d956f87da
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664979"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的 ScriptBlock 元素 (格式)

指定其值會顯示在資料列中的腳本。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 元素 for ListControl (Format) ListEntry for ListEntries for ListControl (ListItems 專案) ListEntry 的 ListControl 專案 ListItems (格式) 專案的 ListControl 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `ScriptBlock` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ (格式) 的 [專案] 元素 ](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

## <a name="text-value"></a>文字值

指定其值會顯示在資料列中的腳本。

## <a name="remarks"></a>備註

當指定這個專案時，您無法指定 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 元素。

如需在清單視圖中指定腳本的詳細資訊，請參閱 [清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例示範如何指定顯示其值的屬性。

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>另請參閱

[ListControl 之 ListItem 的 PropertyName 元素 (格式)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[建立清單檢視](./creating-a-list-view.md)

[ListControl 之 ListItems 的 ListItem 元素 (格式)](./listitem-element-for-listitems-for-listcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
