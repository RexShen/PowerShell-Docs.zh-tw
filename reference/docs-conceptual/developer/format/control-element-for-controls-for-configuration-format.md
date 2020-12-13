---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的控制項元素 (格式)
description: 設定之控制項的控制項元素 (格式)
ms.openlocfilehash: 43424de025cb89d81533e973abd7c39c09533747
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655653"
---
# <a name="control-element-for-controls-for-configuration-format"></a>設定之控制項的控制項元素 (格式)

定義通用控制項，可供格式化檔案的所有視圖和用來參考控制項的名稱使用。

Configuration 元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式的控制項元素) 

## <a name="syntax"></a>語法

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父項目 `Control` 。 您必須只指定每個子專案的其中一個。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的控制項 CustomControl 元素 (格式)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|必要元素。<br /><br /> 定義控制項。|
|[Configuration (格式的控制項名稱元素) ](./name-element-for-control-for-controls-for-configuration-format.md)|必要元素。<br /><br /> 指定用來參考控制項的名稱。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[Configuration (格式的 Controls 元素) ](./controls-element-for-configuration-format.md)|定義可供格式化檔案的所有視圖或其他控制項使用的通用控制項。|

## <a name="remarks"></a>備註

您可以在下列專案中參考提供給這個控制項的名稱：

- [CustomItem (格式的 ExpressionBinding 元素) ](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [View (格式的 GroupBy 元素) ](./groupby-element-for-view-format.md)

## <a name="see-also"></a>另請參閱

[Configuration (格式的 Controls 元素) ](./controls-element-for-configuration-format.md)

[CustomControl 元素，可控制設定 (格式) ](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[CustomItem (格式的 ExpressionBinding 元素) ](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[View (格式的 GroupBy 元素) ](./groupby-element-for-view-format.md)

[設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
