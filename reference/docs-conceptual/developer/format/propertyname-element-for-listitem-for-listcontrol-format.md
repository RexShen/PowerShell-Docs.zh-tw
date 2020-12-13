---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ListItem 的 PropertyName 元素 (格式)
description: ListControl 之 ListItem 的 PropertyName 元素 (格式)
ms.openlocfilehash: 30cd48f9549e1a091776cd5f8395e1a71314ea1b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665969"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的 PropertyName 元素 (格式)

指定其值會顯示在清單中的 .NET 屬性。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 專案 (格式) 專案名稱 (格式) 專案名稱 (格式) 

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `PropertyName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ (格式) 的 [專案] 元素 ](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

## <a name="text-value"></a>文字值

指定顯示其值的屬性名稱。

## <a name="remarks"></a>備註

當指定這個專案時，您無法指定 [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 元素。

除了顯示內容值，您也可以指定值的標籤，或可用於變更值顯示的格式字串。 如需在清單視圖中指定資料的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例示範如何指定會顯示其值的標籤和屬性。

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>另請參閱

[ListControl 之 ListItem 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[建立清單檢視](./creating-a-list-view.md)

[ListControl (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
