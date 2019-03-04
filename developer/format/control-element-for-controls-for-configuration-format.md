---
title: 控制控制項的項目，組態 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858884"
---
# <a name="control-element-for-controls-for-configuration-format"></a>設定之控制項的控制項元素 (格式)

定義可供的格式化檔案以及用來參考的控制項名稱的所有檢視通用控制項。

組態 （格式） 的組態 （格式） 的控制項的控制項項目的組態項目 （格式） 的控制項項目

## <a name="syntax"></a>語法

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目，如`Control`項目。 您必須指定其中一個每個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomControl 組態 （格式） 的控制項的控制項的項目](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|必要項目。<br /><br /> 定義控制項。|
|[組態 （格式） 的控制項的 name 元素](./name-element-for-control-for-controls-for-configuration-format.md)|必要項目。<br /><br /> 指定用來參考該控制項的名稱。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[組態 （格式） 的 controls 項目](./controls-element-for-configuration-format.md)|定義可用的格式化檔案的所有檢視，或其他控制項的通用控制項。|

## <a name="remarks"></a>備註

提供給這個控制項的名稱可以在下列項目中參考：

- [ExpressionBinding CustomItem （格式） 的項目](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [GroupBy View(Format) 的項目](./groupby-element-for-view-format.md)

## <a name="see-also"></a>另請參閱

[組態 （格式） 的 controls 項目](./controls-element-for-configuration-format.md)

[CustomControl 組態 （格式） 的控制項的項目](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[ExpressionBinding CustomItem （格式） 的項目](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[GroupBy View(Format) 的項目](./groupby-element-for-view-format.md)

[組態 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
