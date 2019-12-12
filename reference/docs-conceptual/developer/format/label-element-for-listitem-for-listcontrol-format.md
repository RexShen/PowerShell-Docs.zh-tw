---
title: ListControl 之專案的標籤元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362887"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的標籤元素 (格式)

指定顯示在資料列中屬性或腳本值左邊的標籤。

ListEntry for ListControl 元素的 ListItems （Format） ListEntry 專案之 ListControl （format） ListControl 元素的設定元素（格式） ViewDefinitions 元素（格式） ListEntries 元素（格式）專案（Format） ListControl 的 ListControl （format） Label 元素的 ListItems 的專案。

## <a name="syntax"></a>語法

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `Label` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[適用于 ListControl 之 ListItems 的專案專案元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

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

[建立清單視圖](./creating-a-list-view.md)

[[專案] 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
