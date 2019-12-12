---
title: DisplayError 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363987"
---
# <a name="displayerror-element-format"></a>DisplayError 元素 (格式)

指定在顯示一段資料時發生錯誤時，顯示 #ERR 的字串。

Configuration 元素（格式） DefaultSettings 元素（格式） DisplayError 元素（格式）

## <a name="syntax"></a>語法

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `DisplayError` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[DefaultSettings 元素（格式）](./defaultsettings-element-format.md)|定義套用至格式化檔案所有視圖的一般設定。|

## <a name="remarks"></a>備註

根據預設，當嘗試顯示資料時，如果發生錯誤，資料的位置會保留空白。 當此元素設定為 true 時，將會顯示 #ERR 字串。

## <a name="see-also"></a>另請參閱

[DefaultSettings 元素（格式）](./defaultsettings-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
