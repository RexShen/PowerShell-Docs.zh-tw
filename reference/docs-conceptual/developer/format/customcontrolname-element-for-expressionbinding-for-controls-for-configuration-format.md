---
title: 設定之控制項的 ExpressionBinding 的 CustomControlName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5242935-2782-4d23-84f5-2446b2b7ba83
caps.latest.revision: 8
ms.openlocfilehash: c9abd9f22907b87323c16d603a9f75bb3d375a03
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364117"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a>設定之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)

指定通用控制項的名稱。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl for 控制項的 CustomItem 元素（格式為 ExpressionBinding 的 configuration CustomItem 元素）之控制項的 CustomEntry for 控制項（格式） CustomControlName設定之控制項的 ExpressionBinding 元素（格式）

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
|[設定之控制項的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|定義控制項所顯示的資料。|

## <a name="text-value"></a>文字值

指定控制項的名稱。

## <a name="remarks"></a>備註

您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。 下列元素會指定這些控制項的名稱：

- [設定之控制項的控制項的名稱元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

- [View 控制項控制項的 Name 元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[設定之控制項的控制項的名稱元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

[View 控制項控制項的 Name 元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

[設定之控制項的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
