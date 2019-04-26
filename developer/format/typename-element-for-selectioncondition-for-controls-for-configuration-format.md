---
title: TypeName SelectionCondition 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083938"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)

指定觸發條件的.NET 型別。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） CustomControl 項目控制項的 CustomControl 的組態 （格式） CustomEntries 項目控制項的控制項的控制項項目的組態項目 （格式） 的控制項項目針對 CustomEntry 的 EntrySelectedBy 的組態 （格式） SelectionCondition 項目控制項的 CustomEntry 的組態 （格式） EntrySelectedBy 項目控制項的 CustomControl 的組態 （格式） CustomEntry 項目SelectionCondition 控制項組態 （格式） 的組態 （格式） 類型名稱項目

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`TypeName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CustomEntry 組態 （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|定義必須存在，要使用的控制項定義的條件。|

## <a name="text-value"></a>文字值

指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[CustomEntry 組態 （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
