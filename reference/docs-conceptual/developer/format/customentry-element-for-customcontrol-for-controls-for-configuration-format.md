---
title: 設定之控制項的 CustomControl 的 CustomEntry 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364067"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)

提供通用控制項的定義。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format）用於設定之控制項 CustomControl 的 CustomEntry 元素（格式）

## <a name="syntax"></a>語法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `CustomEntry` 專案的父元素。 您必須指定定義所顯示的專案。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 定義使用通用控制項定義的 .NET 類型，或必須存在才能使用此控制項的條件。|
|[設定之控制項的 CustomEntry 的 CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|必要項目。<br /><br /> 定義控制項所顯示的資料及其顯示方式。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[設定之 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|提供通用控制項的定義。|

## <a name="remarks"></a>備註

在大部分情況下，每個一般自訂控制項只需要一個定義，但是如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可以有多個定義。 在這些情況下，您可以為每個物件或一組物件提供個別的定義。

## <a name="see-also"></a>另請參閱

[設定之 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[設定之控制項的 CustomEntry 的 CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
