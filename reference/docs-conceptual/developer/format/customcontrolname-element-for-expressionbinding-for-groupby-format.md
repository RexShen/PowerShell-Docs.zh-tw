---
title: GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368907"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)

指定通用控制項或 view 控制項的名稱。 此元素是在定義新物件群組的顯示方式時使用。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 CustomItem for groupby （format） CustomControlName 元素的 groupby （format） ExpressionBinding 元素的 GroupBy （格式） CustomItem 元素的 CustomControl

## <a name="syntax"></a>語法

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `CustomControlName` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-groupby-format.md)|定義控制項所顯示的資料。|

## <a name="text-value"></a>文字值

指定控制項的名稱。

## <a name="remarks"></a>備註

您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。 下列元素會指定這些控制項的名稱：

- [設定之控制項的控制項的名稱元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

- [View 控制項控制項的 Name 元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[設定之控制項的控制項的名稱元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

[View 控制項控制項的 Name 元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

[GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
