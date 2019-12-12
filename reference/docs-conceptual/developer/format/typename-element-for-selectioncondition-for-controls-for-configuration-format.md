---
title: 設定之控制項的 SelectionCondition 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361607"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)

指定觸發條件的 .NET 類型。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素（格式）控制項的設定（格式）控制項元素的元素，用於控制項的設定（format） CustomControl 元素，用於控制項的 CustomControl 的設定（格式） CustomEntries 元素設定（格式） CustomEntry 元素，用於 CustomControl 的設定（格式）之 entryselectedby 元素（適用于 SelectionCondition for 之 entryselectedby 的設定（Format） CustomEntry 元素）之控制項的 CustomEntry設定之控制項的 SelectionCondition 設定（格式） TypeName 元素（格式）

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
|[適用于 CustomEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|定義必須存在的條件，才能使用控制項定義。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[適用于 CustomEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
