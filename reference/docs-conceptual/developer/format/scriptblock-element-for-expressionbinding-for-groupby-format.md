---
title: GroupBy 的 ExpressionBinding 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e022ec4-8531-468e-96ff-77607755ec92
caps.latest.revision: 6
ms.openlocfilehash: 9afa53e1c7d1edabdbff56c4e59fcef0cf1647e3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362167"
---
# <a name="scriptblock-element-for-expressionbinding-for-groupby-format"></a>GroupBy 之 ExpressionBinding 的 ScriptBlock 元素 (格式)

指定控制項顯示其值的腳本。 此元素是在定義新物件群組的顯示方式時使用。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 CustomEntry 之 groupby （format） ExpressionBinding 元素的 GroupBy （format） CustomItem 元素的 CustomControl，適用于 CustomItem 的 groupby （format） ScriptBlock 元素（格式）

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `ScriptBlock` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-groupby-format.md)|定義控制項所顯示的資料。|

## <a name="text-value"></a>文字值

指定控制項顯示其值的腳本。

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
