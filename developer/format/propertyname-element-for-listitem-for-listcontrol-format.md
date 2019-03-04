---
title: PropertyName ListControl （格式） 的 ListItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855734"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的 PropertyName 元素 (格式)

指定其值會顯示在清單中的.NET 屬性。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目 （格式） ListItems 項目 （格式） ListItem 項目 （格式） PropertyName 項目ListItem （格式）

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`PropertyName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListItem 項目 （格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。|

## <a name="text-value"></a>文字值

指定其值會顯示屬性的名稱。

## <a name="remarks"></a>備註

當指定這個項目時，您無法指定[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)項目。

除了顯示的屬性值，您也可以指定的值或可用來變更值的顯示格式字串的標籤。 如需在清單檢視中指定資料的詳細資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例示範如何指定標籤和其值會顯示的屬性。

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>另請參閱

[ScriptBlock ListControl （格式） 的 ListItem 元素](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[建立清單檢視](./creating-a-list-view.md)

[ListControl(Format) 的 ListItem 項目](./listitem-element-for-listitems-for-listcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
