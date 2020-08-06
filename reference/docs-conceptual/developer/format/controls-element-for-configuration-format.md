---
title: 設定 (格式) 的 Controls 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 44b9db0d3523e5e9086da9911882b258a2a54ca6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783784"
---
# <a name="controls-element-for-configuration-format"></a>設定的控制項元素 (格式)

定義可供格式檔案的所有視圖使用的通用控制項。

Configuration 元素 (格式) Controls 設定 (格式的元素) 

## <a name="syntax"></a>語法

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `Controls` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的控制項元素 (格式)](./control-element-for-controls-for-configuration-format.md)|必要元素。<br /><br /> 定義可供格式檔案的所有視圖使用的通用控制項。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定元素 (格式)](./configuration-element-format.md)|代表格式化檔案的最上層元素。|

## <a name="remarks"></a>備註

您可以建立任意數目的通用控制項。 您必須針對每個控制項指定用來參考控制項的名稱，以及控制項的元件。

## <a name="see-also"></a>另請參閱

[設定元素 (格式)](./configuration-element-format.md)

[設定之控制項的控制項元素 (格式)](./control-element-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
