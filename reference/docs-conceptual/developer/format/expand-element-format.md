---
ms.date: 09/13/2016
ms.topic: reference
title: 展開元素 (格式)
description: 展開元素 (格式)
ms.openlocfilehash: 518e132e3e74b921d4e51966fc60088a22ef63f1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667941"
---
# <a name="expand-element-format"></a>展開元素 (格式)

指定如何針對此定義展開集合物件。

Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式)  (展開元素) 格式 (

## <a name="syntax"></a>語法

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `Expand` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 元素 (格式)](./enumerableexpansion-element-format.md)|定義當特定 .NET 集合物件顯示在視圖中時，如何展開這些物件。|

## <a name="text-value"></a>文字值

指定下列其中一個值：

- EnumOnly：只顯示集合中物件的屬性。

- CoreOnly：只顯示集合物件的屬性。

- Both：顯示集合中物件的屬性，以及集合物件的屬性。

## <a name="remarks"></a>備註

這個元素用來定義集合物件和集合中的物件如何顯示。 在此情況下，集合物件會參考支援  **system.object** 介面的任何物件。

預設行為是只顯示集合中物件的屬性。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
