---
title: 設定之控制項的之 entryselectedby 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364787"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a>設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定一組使用此控制項定義的 .NET 類型。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl for 控制項的之 entryselectedby 元素（格式為 CustomEntry 的控制項，適用于 configuration （格式） SelectionSetName 元素的控制項）。

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `SelectionSetName` 專案的父元素。

### <a name="attributes"></a>屬性

無

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

每個控制項定義都必須定義至少一個型別名稱、選擇集或選取條件。

當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。 如需定義選取集的詳細資訊，請參閱[定義選取範圍集合](./defining-selection-sets.md)。

## <a name="see-also"></a>另請參閱

[設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
