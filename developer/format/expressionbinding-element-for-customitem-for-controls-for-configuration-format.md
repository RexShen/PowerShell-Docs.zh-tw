---
title: ExpressionBinding CustomItem 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855134"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry CustomItem 組態 （格式） 的控制項設定 ExpressionBinding 元素的控制項的組態 （格式） CustomItem 元素的控制項的格式） CustomEntry 項目

## <a name="syntax"></a>語法

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`ExpressionBinding`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomControl Element`|選擇性的項目。<br /><br /> 定義會使用這個控制項的控制項。|
|[CustomControlName ExpressionBinding 組態 （格式） 的控制項的項目](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定通用控制項的檢視控制項的名稱。|
|[EnumerateCollection ExpressionBinding 組態 （格式） 的控制項的項目](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定集合的項目會顯示控制項。|
|[ItemSelectionCondition ExpressionBinding 組態 （格式） 的控制項的項目](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 定義要使用這個通用控制項必須存在的條件。|
|[PropertyName ExpressionBinding 組態 （格式） 的控制項的項目](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定其值會顯示通用控制項的.NET 屬性。|
|[ExpressionBinding 組態 （格式） 的控制項的指令碼區塊項目](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定其值常見的控制項所顯示的指令碼。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[組態控制項 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|定義自訂的控制項檢視所顯示的資料和顯示方式。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[組態控制項 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
