---
title: 用於檢視 （格式） 的控制項 CustomEntries CustomEntry 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858774"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)

提供控制項的定義。 定義可供檢視的控制項時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries 用於檢視 （格式） 的控制項的檢視 （格式） CustomEntry 元素

## <a name="syntax"></a>語法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目，以及的父項目`CustomEntry`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用於檢視 （格式） 的控制項 CustomEntry EntrySelectedBy 項目](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。|
|[用於檢視 （格式） 的控制項 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-controls-for-view-format.md)|必要項目。<br /><br /> 定義控制項顯示資料的方式。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CustomEntries CustomControl 檢視 （格式） 的項目](./customentries-element-for-customcontrol-for-view-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[CustomEntries CustomControl 檢視 （格式） 的項目](./customentries-element-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
