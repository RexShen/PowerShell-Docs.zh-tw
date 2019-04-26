---
title: 標籤 ListControl （格式） 的 ListItem 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065422"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的標籤元素 (格式)

指定顯示屬性或指令碼中值的資料列左邊的標籤。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 ListEntry ListControl 項目 （如的 ListControl （格式） ListItems ListControl （格式） ListEntry 項目ListItems ListControl （格式） 的 ListItem ListControl （格式） 標籤元素的格式） ListItem 項目

## <a name="syntax"></a>語法

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`Label`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[ListItems ListControl （格式） 的 ListItem 項目](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。|

## <a name="text-value"></a>文字值

指定要顯示的屬性或指令碼的值的左邊的標籤。

## <a name="remarks"></a>備註

如果未指定標籤，則會顯示屬性或指令碼的名稱。 如需在清單檢視中使用標籤的詳細資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例示範如何將標籤新增至一個資料列。

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[ListItem 項目 （格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
