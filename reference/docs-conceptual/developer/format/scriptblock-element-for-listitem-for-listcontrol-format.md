---
title: ListControl (格式) 的 ScriptBlock 元素Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 249d3e36b4246b7baa410815122f8e30340f1862
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785450"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的 ScriptBlock 元素 (格式)

指定其值顯示在資料列中的腳本。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListControl (格式) ListEntry 元素（ListEntries for ListControl (format) ListItems 元素 (ListEntry for ListControl) format (ScriptBlock 元素用於 ListItems) 格式的 ListEntries

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

## <a name="text-value"></a>文字值

指定其值顯示在資料列中的腳本。

## <a name="remarks"></a>備註

當指定此元素時，您無法指定[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。

如需在清單視圖中指定腳本的詳細資訊，請參閱[清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例顯示如何指定屬性，其值會顯示。

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
