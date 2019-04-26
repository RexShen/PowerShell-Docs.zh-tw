---
title: SelectionSetName EntrySelectedBy 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063967"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a>設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定一組使用這個控制項定義的.NET 型別。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry EntrySelectedBy 控制項組態 （格式） 的組態 （格式） SelectionSetName 元素的控制項的組態 （格式） EntrySelectedBy 元素的控制項的格式） CustomEntry 項目

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。

### <a name="attributes"></a>屬性

無

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[EntrySelectedBy CustomEntry 組態 （格式） 的控制項的項目](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。|

## <a name="text-value"></a>文字值

指定選取項目集的名稱。

## <a name="remarks"></a>備註

每個控制項定義必須至少一個型別名稱、 選取項目集或選擇條件的定義。

您想要在多個檢視中定義一組所使用的物件時，會通常會使用選取項目集。 如需定義選取項目集的詳細資訊，請參閱[定義的選取項目設定](./defining-selection-sets.md)。

## <a name="see-also"></a>另請參閱

[EntrySelectedBy CustomEntry 組態 （格式） 的控制項的項目](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
