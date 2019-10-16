---
title: EnumerableExpansions 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363297"
---
# <a name="enumerableexpansions-element-format"></a>EnumerableExpansions 元素 (格式)

定義 .NET 集合物件在視圖中顯示時的展開方式。

Configuration 元素（格式） DefaultSettings 元素（格式） EnumerableExpansions 元素（格式）

## <a name="syntax"></a>語法

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `EnumerableExpansions` 元素的父元素。 您可以使用的子項目數目沒有限制。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 元素（格式）](./enumerableexpansion-element-format.md)|選擇性元素。<br /><br /> 定義在視圖中顯示時展開的特定 .NET 集合物件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[DefaultSettings 元素（格式）](./defaultsettings-element-format.md)|定義套用至格式化檔案所有視圖的一般設定。|

## <a name="remarks"></a>備註

這個元素是用來定義集合物件和集合中物件的顯示方式。 在此情況下，集合物件會參考支援**system.object**介面的任何物件。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
