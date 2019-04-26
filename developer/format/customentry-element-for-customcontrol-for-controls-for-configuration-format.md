---
title: CustomEntry CustomControl 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066460"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)

提供通用控制項的定義。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl 控制項組態 （格式） 的格式） CustomEntry 項目

## <a name="syntax"></a>語法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`CustomEntry`項目。 您必須指定定義所顯示的項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EntrySelectedBy CustomEntry 組態 （格式） 的控制項的項目](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 定義使用的通用控制項或條件必須存在於要使用這個控制項定義的.NET 類型。|
|[組態控制項 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|必要項目。<br /><br /> 定義控制項所顯示的資料和顯示方式。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CustomEntries CustomControl 組態 （格式） 的項目](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|提供通用控制項的定義。|

## <a name="remarks"></a>備註

在大部分情況下，只有一個定義需要針對每個常見的自訂控制項，但可以有多個定義，如果您想要使用相同的控制項來顯示不同的.NET 物件。 在這些情況下，您可以針對每個物件或一組物件提供不同的定義。

## <a name="see-also"></a>另請參閱

[CustomEntries CustomControl 組態 （格式） 的項目](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[組態控制項 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
