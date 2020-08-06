---
title: 適用于 ExpressionBinding 之 GroupBy (格式的 CustomControlName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 06e612b25accf81467108ca48500943153efd575
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785994"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)

指定通用控制項或 view 控制項的名稱。 此元素是在定義新物件群組的顯示方式時使用。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) GroupBy 元素以取得 (格式) CustomEntries 專案（適用于 groupby (format）) CustomEntry 元素（適用于 CustomControl 的 groupby (格式) CustomItem 元素，適用于 groupby (格式的 CustomEntry) ExpressionBinding 專案 (]

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
|[GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-groupby-format.md)|定義控制項所顯示的資料。|

## <a name="text-value"></a>文字值

指定控制項的名稱。

## <a name="remarks"></a>備註

您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。 下列元素會指定這些控制項的名稱：

- [設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

- [檢視之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

[檢視之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-view-format.md)

[GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
