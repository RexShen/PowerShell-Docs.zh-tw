---
title: GroupBy （格式） 的屬性名稱項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075863"
---
# <a name="propertyname-element-for-groupby-format"></a>GroupBy 的 PropertyName 元素 (格式)

指定.NET 屬性，其值變更時，會啟動新的群組。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） 的 GroupBy （格式） 的屬性名稱項目

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`PropertyName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)|定義一組.NET 物件的顯示方式。|

## <a name="text-value"></a>文字值

指定.NET 屬性名稱。

## <a name="remarks"></a>備註

當這個屬性的值變更時，Windows PowerShell 會啟動新的群組。

當指定這個項目時，您無法指定[ScriptBlock](./scriptblock-element-for-groupby-format.md)啟動新的群組項目。

## <a name="example"></a>範例

下列範例示範如何啟動新的群組屬性的值變更時。

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

如需完整的格式化檔案，其中包含這個元素的範例，請參閱 <<c0> [ 寬型檢視 (GroupBy)](./wide-view-groupby.md)。

## <a name="see-also"></a>另請參閱

[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[GroupBy （格式） 的指令碼區塊項目](./scriptblock-element-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
