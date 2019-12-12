---
title: View 之控制項的 SelectionCondition 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7141aefc-6656-4c52-8a9c-c2bfc9c87be9
caps.latest.revision: 6
ms.openlocfilehash: 7a697c286ec9efe750930739cdfa2580003365dd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361597"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a>檢視之控制項的 SelectionCondition 的 TypeName 元素 (格式)

指定觸發條件的 .NET 類型。 定義可供視圖使用的控制項時，會使用這個元素。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素的 CustomEntries for view （format）之 entryselectedby 元素 for CustomEntry for view （format） SelectionCondition 元素 for controls 的控制項（格式）Format）控制項的 SelectionCondition 的 TypeName 元素（格式）

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `TypeName` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|定義必須存在的條件，才能使用控制項定義。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[View 之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
