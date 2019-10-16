---
title: CustomControl for View 的 ExpressionBinding 的 CustomControlName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364107"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)

指定通用控制項或 view 控制項的名稱。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl Element for view （format） CustomEntries Element for view （format） CustomEntry for View （format） CustomEntries 元素CustomEntry for View （Format） ExpressionBinding 元素的元素，適用于 CustomItem 的運算式系結的 CustomItem （Format） CustomControlName 元素

## <a name="syntax"></a>語法

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `CustomControlName` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|定義控制項所顯示的資料。|

## <a name="text-value"></a>文字值

指定控制項的名稱。

## <a name="remarks"></a>備註

您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。 這些控制項的名稱是由下列元素所指定。

- [設定之控制項的控制項的名稱元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

- [View 控制項控制項的 Name 元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[設定之控制項的控制項的名稱元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

[View 控制項控制項的 Name 元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

[CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
