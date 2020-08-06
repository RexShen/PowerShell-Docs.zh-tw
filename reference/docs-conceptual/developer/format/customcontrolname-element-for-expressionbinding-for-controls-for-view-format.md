---
title: View (Format) 的控制項之 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 871c6afd89db9360ea5012191b08863a9441f899
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786011"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)

指定通用控制項或 view 控制項的名稱。 定義可供視圖使用的控制項時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl， (格式控制項的控制項) CustomEntries 元素用於 view (針對 (格式的控制項，) CustomEntry 元素格式) CustomItem 專案的 CustomEntry for view (Format) ExpressionBinding 元素 for view (format) CustomItem 元素 for 控制項 for view (format) CustomControlName 專案

## <a name="syntax"></a>語法

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `CustomControlName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|定義控制項所顯示的資料。|

## <a name="text-value"></a>文字值

指定控制項的名稱。

## <a name="remarks"></a>備註

您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。 下列元素會指定這些控制項的名稱：

- [設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

- [檢視之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

[檢視之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-view-format.md)

[檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
