---
title: EnumerableExpansions 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860254"
---
# <a name="enumerableexpansions-element-format"></a>EnumerableExpansions 元素 (格式)

定義在檢視中顯示時，如何展開.NET 集合物件。

組態項目 （格式） DefaultSettings 項目 （格式） EnumerableExpansions 項目 （格式）

## <a name="syntax"></a>語法

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`EnumerableExpansions`項目。 沒有任何限制，您可以使用的子元素的數目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 項目 （格式）](./enumerableexpansion-element-format.md)|選擇性的項目。<br /><br /> 定義在檢視中顯示時，會展開的特定.NET 集合物件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[DefaultSettings 項目 （格式）](./defaultsettings-element-format.md)|定義套用至的格式化檔案的所有檢視的常見設定。|

## <a name="remarks"></a>備註

這個項目用來定義集合物件和集合中的物件的顯示方式。 集合物件在此情況下，任何支援的物件是指**System.Collections.ICollection**介面。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
