---
title: EnumerableExpansion 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856834"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion 元素 (格式)

定義在檢視中顯示時，會展開物件的特定.NET 集合。

組態項目 （格式） DefaultSettings 項目 （格式） EnumerableExpansions 項目 （格式） EnumerableExpansion 項目 （格式）

## <a name="syntax"></a>語法

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`EnumerableExpansion`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EntrySelectedBy EnumerableExpansion （格式） 的項目](./entryselectedby-element-for-enumerableexpansion-format.md)|選擇性的項目。<br /><br /> 定義此定義會展開.NET 集合物件。|
|[展開項目 （格式）](./expand-element-format.md)|指定如何展開此定義的集合物件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansions 項目 （格式）](./enumerableexpansions-element-format.md)|該檢視中顯示時，會展開物件的.NET 集合定義不同的方式。|

## <a name="remarks"></a>備註

這個項目用來定義集合物件和集合中的物件的顯示方式。 集合物件在此情況下，任何支援的物件是指**System.Collections.ICollection**介面。

預設行為是只顯示屬性的物件集合中。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
