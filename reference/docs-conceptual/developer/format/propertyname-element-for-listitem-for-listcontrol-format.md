---
title: ListControl (格式的專案名稱的 PropertyName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9ee466d7f73e53b129f8d46f49a21549683bb32c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780826"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的 PropertyName 元素 (格式)

指定其值顯示在清單中的 .NET 屬性。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListEntries 專案 (格式) ListEntry 專案 (格式) ListItems 元素 (格式) 專案名稱專案 (格式專案的) PropertyName 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

## <a name="text-value"></a>文字值

指定顯示其值的屬性名稱。

## <a name="remarks"></a>備註

當指定此元素時，您不能指定[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素。

除了顯示內容值之外，您也可以指定值的標籤，或可用於變更值顯示的格式字串。 如需在清單視圖中指定資料的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例顯示如何指定其值顯示的標籤和屬性。

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
