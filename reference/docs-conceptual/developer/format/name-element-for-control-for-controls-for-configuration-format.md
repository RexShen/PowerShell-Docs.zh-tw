---
title: 設定 (格式) 的控制項之控制項的名稱元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3d45ba98b909ebee18e01d2b6985a48906ce39d9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783529"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>設定之控制項的控制項的名稱元素 (格式)

指定控制項的名稱。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) Name 元素用於設定 (格式的控制項) 

## <a name="syntax"></a>語法

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `Name` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定之控制項的控制項元素 (格式)](./control-element-for-controls-for-configuration-format.md)|定義可供格式檔案的所有視圖使用的通用控制項，以及用來參考控制項的名稱。|

## <a name="text-value"></a>文字值

指定用來參考此控制項的名稱。

## <a name="remarks"></a>備註

這裡指定的名稱可用於下列專案，以參考此控制項。

- 建立 [資料表]、[清單]、[寬] 或 [自訂] 控制項時，下列專案可以指定控制項： [view (格式的 GroupBy 元素) ](./groupby-element-for-view-format.md)

- 建立另一個通用控制項時，這個控制項可以由下列元素指定： [CustomItem 的 ExpressionBinding 元素，用於設定 (格式的控制項) ](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- 建立可供視圖使用的控制項時，這個控制項可以由下列元素指定： [CustomItem 的 ExpressionBinding 元素，用於 view (格式的控制項) ](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[設定之控制項的控制項元素 (格式)](./control-element-for-controls-for-configuration-format.md)

[設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
