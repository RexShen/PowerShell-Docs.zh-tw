---
title: DisplayError 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5d46c2fbd48f592db5ba1b33eb6cead8dc1c4698
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774281"
---
# <a name="displayerror-element-format"></a>DisplayError 元素 (格式)

指定在顯示一段資料時發生錯誤時，顯示 #ERR 的字串。

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
|[DefaultSettings 元素 (格式)](./defaultsettings-element-format.md)|定義套用至格式化檔案所有視圖的一般設定。|

## <a name="remarks"></a>備註

根據預設，當嘗試顯示資料時，如果發生錯誤，資料的位置會保留空白。 當此元素設定為 true 時，將會顯示 #ERR 字串。

## <a name="see-also"></a>另請參閱

[DefaultSettings 元素 (格式)](./defaultsettings-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
