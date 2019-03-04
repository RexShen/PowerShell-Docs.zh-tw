---
title: CustomControlName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860434"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)

指定通用控制項的檢視控制項的名稱。 定義自訂控制項的檢視時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目進行檢視 （格式） 的檢視 （格式） CustomItem CustomEntries CustomEntry 元素 CustomControl 的檢視 （格式） CustomEntries 項目CustomEntry CustomItem （格式） CustomControlName 元素 CustomItem （格式） 的運算式繫結的檢視 （格式） ExpressionBinding 項目的項目

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
|[ExpressionBinding CustomItem （格式） 的項目](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|定義控制項所顯示的資料。|

## <a name="text-value"></a>文字值

指定控制項的名稱。

## <a name="remarks"></a>備註

您可以建立可供的格式化檔案的所有檢視通用控制項，而且您可以建立可都供特定檢視的檢視控制項。 這些控制項的名稱是由下列項目指定。

- [組態 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-configuration-format.md)

- [用於檢視 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[組態 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-configuration-format.md)

[用於檢視 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding CustomItem （格式） 的項目](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
