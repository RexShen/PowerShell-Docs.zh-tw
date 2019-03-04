---
title: 用於檢視 （格式） 的控制項 ExpressionBinding CustomControlName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855594"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)

指定通用控制項的檢視控制項的名稱。 定義可供檢視的控制項時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry CustomItem 用於檢視 （格式） CustomControlName 的控制項的檢視 （格式） ExpressionBinding 元素的控制項的檢視 （格式） CustomItem 元素的控制項的檢視 （格式） CustomEntry 元素用於檢視 （格式） 的控制項 ExpressionBindine 的項目

## <a name="syntax"></a>語法

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`CustomControlName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|定義控制項所顯示的資料。|

## <a name="text-value"></a>文字值

指定控制項的名稱。

## <a name="remarks"></a>備註

您可以建立可供所有的格式化檔案，檢視的通用控制項，而且您可以建立可供特定檢視的檢視控制項。 下列項目會指定這些控制項的名稱：

- [組態 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-configuration-format.md)

- [用於檢視 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[組態 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-configuration-format.md)

[用於檢視 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
