---
title: ListControl 之專案的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364807"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ListControl 之 ListItem 的 ScriptBlock 元素 (格式)

指定其值顯示在資料列中的腳本。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素（適用于 ListEntry 的 ListEntries for ListControl （Format） ListItems 元素） ListControl （Format） ListEntry 元素針對 ListControl （格式）之 ListControl 的 ListItems for ListControl （Format） ScriptBlock 元素的（格式）

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `ScriptBlock` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[[專案] 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

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

[ListControl 之專案名稱的 PropertyName 元素（格式）](./propertyname-element-for-listitem-for-listcontrol-format.md)

[建立清單視圖](./creating-a-list-view.md)

[適用于 ListControl 之 ListItems 的專案專案元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
