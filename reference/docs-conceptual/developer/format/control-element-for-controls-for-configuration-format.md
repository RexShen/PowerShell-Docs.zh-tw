---
title: 設定之控制項的控制項元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369007"
---
# <a name="control-element-for-controls-for-configuration-format"></a>設定之控制項的控制項元素 (格式)

定義可供格式檔案的所有視圖使用的通用控制項，以及用來參考控制項的名稱。

Configuration 元素（Format）控制設定之控制項的設定（格式）控制項元素（格式）

## <a name="syntax"></a>語法

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `Control` 元素的父元素。 您必須只指定其中一個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項控制項的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|必要元素。<br /><br /> 定義控制項。|
|[設定之控制項的名稱元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)|必要元素。<br /><br /> 指定用來參考控制項的名稱。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[設定的控制項元素（格式）](./controls-element-for-configuration-format.md)|定義可供格式檔案或其他控制項的所有視圖使用的通用控制項。|

## <a name="remarks"></a>備註

提供給這個控制項的名稱可以在下列元素中參考：

- [CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

## <a name="see-also"></a>另請參閱

[設定的控制項元素（格式）](./controls-element-for-configuration-format.md)

[設定之控制項的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[設定之控制項的控制項的名稱元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
