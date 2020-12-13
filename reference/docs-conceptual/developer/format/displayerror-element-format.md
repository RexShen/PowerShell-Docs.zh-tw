---
ms.date: 09/13/2016
ms.topic: reference
title: DisplayError 元素 (格式)
description: DisplayError 元素 (格式)
ms.openlocfilehash: fb54df86a3558263687a8c417870495b7066f563
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649929"
---
# <a name="displayerror-element-format"></a>DisplayError 元素 (格式)

指定在顯示資料的錯誤發生時，顯示 #ERR 的字串。

Configuration 元素 (格式) DefaultSettings 元素 (格式) DisplayError 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `DisplayError` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[DefaultSettings 元素 (格式)](./defaultsettings-element-format.md)|定義適用于格式檔案所有視圖的一般設定。|

## <a name="remarks"></a>備註

根據預設，當嘗試顯示資料時，如果發生錯誤，資料的位置會保留空白。 當這個元素設定為 true 時，將會顯示 #ERR 字串。

## <a name="see-also"></a>另請參閱

[DefaultSettings 元素 (格式)](./defaultsettings-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
