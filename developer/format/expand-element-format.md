---
title: 展開項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858574"
---
# <a name="expand-element-format"></a>展開元素 (格式)

指定如何展開此定義的集合物件。

組態項目 （格式） DefaultSettings 項目 （格式） EnumerableExpansions 項目 （格式） EnumerableExpansion 項目 （格式） 展開項目 （格式）

## <a name="syntax"></a>語法

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`Expand`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 項目 （格式）](./enumerableexpansion-element-format.md)|定義在檢視中顯示時，會展開物件的特定.NET 集合。|

## <a name="text-value"></a>文字值

指定下列值之一：

- EnumOnly:顯示物件的屬性集合中。

- CoreOnly:顯示集合物件的屬性。

- 兩者：集合和集合物件的屬性中顯示之物件的屬性。

## <a name="remarks"></a>備註

這個項目用來定義集合物件和集合中的物件的顯示方式。 集合物件在此情況下，任何支援的物件是指**System.Collections.ICollection**介面。

預設行為是只顯示屬性的物件集合中。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
