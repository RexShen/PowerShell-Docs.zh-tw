---
title: CustomControlName ExpressionBinding 的 GroupBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066561"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)

指定通用控制項的檢視控制項的名稱。 定義新的群組物件的顯示方式時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry CustomItem ExpressionBinding 的 GroupBy （格式） 的 GroupBy （格式） CustomControlName 元素的 GroupBy （格式） ExpressionBinding 元素的 GroupBy （格式） CustomItem 元素

## <a name="syntax"></a>語法

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`CustomControlName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[ExpressionBinding CustomItem 的 GroupBy （格式） 的項目](./expressionbinding-element-for-customitem-for-groupby-format.md)|定義控制項所顯示的資料。|

## <a name="text-value"></a>文字值

指定控制項的名稱。

## <a name="remarks"></a>備註

您可以建立可供所有的格式化檔案，檢視的通用控制項，而且您可以建立可供特定檢視的檢視控制項。 下列項目會指定這些控制項的名稱：

- [組態 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-configuration-format.md)

- [用於檢視 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[組態 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-configuration-format.md)

[用於檢視 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding CustomItem 的 GroupBy （格式） 的項目](./expressionbinding-element-for-customitem-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
