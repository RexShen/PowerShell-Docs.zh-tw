---
title: 控制項名稱項目控制項的組態 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860084"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>設定之控制項的控制項的名稱元素 (格式)

指定控制項的名稱。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） 名稱的項目組態 （格式） 的控制項的控制項的控制項的控制項項目的組態項目 （格式） 的控制項項目

## <a name="syntax"></a>語法

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`Name`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[組態 （格式） 的控制項的控制項項目](./control-element-for-controls-for-configuration-format.md)|定義可供的格式化檔案以及用來參考的控制項名稱的所有檢視通用控制項。|

## <a name="text-value"></a>文字值

指定用來參考這個控制項的名稱。

## <a name="remarks"></a>備註

在這裡指定的名稱可以用於下列項目，來參考這個控制項。

- 在建立資料表、 清單、 寬或自訂的控制項檢視時，可以指定的控制項，由下列項目：[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

- 當建立另一個常見的控制項，此控制項可以指定由下列項目：[ExpressionBinding CustomItem 組態 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- 當建立控制項，可供檢視時，這個控制項可以指定下列項目：[ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[組態 （格式） 的控制項的控制項項目](./control-element-for-controls-for-configuration-format.md)

[ExpressionBinding CustomItem 組態 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
