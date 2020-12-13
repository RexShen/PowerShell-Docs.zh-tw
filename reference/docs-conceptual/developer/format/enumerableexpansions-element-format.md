---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansions 元素 (格式)
description: EnumerableExpansions 元素 (格式)
ms.openlocfilehash: 789599e6ff368b4685c7937d5b6eb38618752f9e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660170"
---
# <a name="enumerableexpansions-element-format"></a>EnumerableExpansions 元素 (格式)

定義當 .NET 集合物件顯示在視圖中時，如何展開這些物件。

Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `EnumerableExpansions` 。 您可以使用的子項目數目沒有任何限制。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 元素 (格式)](./enumerableexpansion-element-format.md)|選擇性項目。<br /><br /> 定義特定的 .NET 集合物件，這些物件會在顯示于視圖時展開。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[DefaultSettings 元素 (格式)](./defaultsettings-element-format.md)|定義適用于格式檔案所有視圖的一般設定。|

## <a name="remarks"></a>備註

這個元素用來定義集合物件和集合中的物件如何顯示。 在此情況下，集合物件會參考支援  **system.object** 介面的任何物件。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
