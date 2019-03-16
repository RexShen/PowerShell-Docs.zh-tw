---
title: DisplayError 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056476"
---
# <a name="displayerror-element-format"></a>DisplayError 元素 (格式)

指定顯示一段資料時，發生錯誤時，會顯示 #ERR 的字串。

組態項目 （格式） DefaultSettings 項目 （格式） DisplayError 項目 （格式）

## <a name="syntax"></a>語法

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`DisplayError`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[DefaultSettings 項目 （格式）](./defaultsettings-element-format.md)|定義套用至的格式化檔案的所有檢視的常見設定。|

## <a name="remarks"></a>備註

根據預設，當發生錯誤時嘗試顯示某份資料，資料的位置會保留空白。 當這個項目設定為 true，#ERR 字串將會顯示。

## <a name="see-also"></a>另請參閱

[DefaultSettings 項目 （格式）](./defaultsettings-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
