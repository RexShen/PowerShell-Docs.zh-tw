---
ms.date: 09/13/2016
ms.topic: reference
title: 設定的控制項元素 (格式)
description: 設定的控制項元素 (格式)
ms.openlocfilehash: 53f874ddccf3b4f1f0a23aad608e786524bde830
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668094"
---
# <a name="controls-element-for-configuration-format"></a>設定的控制項元素 (格式)

定義可供格式化檔案的所有視圖使用的通用控制項。

Configuration 元素 (格式) 控制項設定 (格式的元素) 

## <a name="syntax"></a>語法

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `Controls` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的控制項元素 (格式)](./control-element-for-controls-for-configuration-format.md)|必要元素。<br /><br /> 定義可供格式化檔案的所有視圖使用的通用控制項。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定元素 (格式)](./configuration-element-format.md)|代表格式化檔案的最上層元素。|

## <a name="remarks"></a>備註

您可以建立任意數目的通用控制項。 您必須為每個控制項指定用來參考控制項的名稱，以及控制項的元件。

## <a name="see-also"></a>另請參閱

[設定元素 (格式)](./configuration-element-format.md)

[設定之控制項的控制項元素 (格式)](./control-element-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
