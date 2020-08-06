---
title: ListControl (格式之專案的標籤元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ad80cc0478e7567b12d264ab661d843248ba48e1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783631"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的標籤元素 (格式)

指定顯示在資料列中屬性或腳本值左邊的標籤。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListControl (格式) ListEntry 元素 ListControl (格式) ListItems 專案（ListEntry 的 ListControl 專案 () Label 元素，ListItems (格式的 ListEntries 的標籤) 格式 (

## <a name="syntax"></a>語法

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `Label` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListControl 之 ListItems 的 ListItem 元素 (格式)](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

## <a name="text-value"></a>文字值

指定要在屬性或腳本值左邊顯示的標籤。

## <a name="remarks"></a>備註

如果未指定標籤，則會顯示內容或腳本的名稱。 如需在清單視圖中使用標籤的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例顯示如何將標籤加入至資料列。

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[ (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
