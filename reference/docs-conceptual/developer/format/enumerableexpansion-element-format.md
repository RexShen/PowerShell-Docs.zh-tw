---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion 元素 (格式)
description: EnumerableExpansion 元素 (格式)
ms.openlocfilehash: 207ad99d5335e99701660159ab77279b55b0b6b5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668009"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion 元素 (格式)

定義當特定 .NET 集合物件顯示在視圖中時，如何展開這些物件。

Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `EnumerableExpansion` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-enumerableexpansion-format.md)|選擇性項目。<br /><br /> 定義由這個定義擴充的 .NET 集合物件。|
|[展開元素 (格式)](./expand-element-format.md)|指定如何針對此定義展開集合物件。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansions 元素 (格式)](./enumerableexpansions-element-format.md)|定義在顯示于視圖中時，.NET 集合物件展開的不同方式。|

## <a name="remarks"></a>備註

這個元素用來定義集合物件和集合中的物件如何顯示。 在此情況下，集合物件會參考支援  **system.object** 介面的任何物件。

預設行為是只顯示集合中物件的屬性。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
