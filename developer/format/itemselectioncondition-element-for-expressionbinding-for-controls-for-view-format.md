---
title: 用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065473"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>檢視之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)

定義要使用這個控制項必須存在的條件。 定義可供檢視的控制項時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry CustomItem 用於檢視 （格式） 的控制項的檢視 （格式） ExpressionBinding 元素的控制項的檢視 （格式） CustomItem 元素的控制項的檢視 （格式） CustomEntry 元素用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目

## <a name="syntax"></a>語法

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`ItemSelectionCondition`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[PropertyName ItemSelectionCondition 用於檢視 （格式） 的控制項的項目](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 屬性。|
|[用於檢視 （格式） 的控制項 ItemSelectionCondition 的指令碼區塊項目](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定的指令碼，就會觸發條件。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|定義控制項所顯示的資料。|

## <a name="remarks"></a>備註

您可以指定一個屬性名稱或用於這種狀況的指令碼，但不能同時指定。

## <a name="see-also"></a>另請參閱

[PropertyName ItemSelectionCondition 用於檢視 （格式） 的控制項的項目](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項 ItemSelectionCondition 的指令碼區塊項目](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
