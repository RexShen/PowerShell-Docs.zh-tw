---
title: GroupBy （格式） 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064504"
---
# <a name="scriptblock-element-for-groupby-format"></a>GroupBy 的 ScriptBlock 元素 (格式)

指定的指令碼，其值變更時，會啟動新的群組。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） 的 GroupBy （格式） 的指令碼區塊項目

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)|定義一組.NET 物件的顯示方式。|

## <a name="text-value"></a>文字值

指定評估指令碼。

## <a name="remarks"></a>備註

此指令碼的值變更時，Windows PowerShell 就會啟動新的群組。

當指定這個項目時，您無法指定[PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676)啟動新的群組項目。

## <a name="see-also"></a>另請參閱

[GroupBy （格式） 的屬性名稱項目](./propertyname-element-for-groupby-format.md)

[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
