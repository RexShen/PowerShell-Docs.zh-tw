---
title: GroupBy (格式) 的 CustomControlName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4e3102f12cd37fa72a2de1bf1db5d1f82db31222
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783733"
---
# <a name="customcontrolname-element-for-groupby-format"></a>GroupBy 的 CustomControlName 元素 (格式)

指定用來顯示新群組的自訂控制項名稱。 定義資料表、清單、寬型或自訂控制項視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（GroupBy (格式）) CustomControlName 元素 (

## <a name="syntax"></a>語法

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `CustomControlName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)|定義 Windows PowerShell 如何顯示新的物件群組。|

## <a name="text-value"></a>文字值

指定用來顯示新群組的自訂控制項名稱。

## <a name="remarks"></a>備註

您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。 下列元素會指定這些自訂控制項的名稱：

- [設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

- [檢視之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)

[設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

[檢視之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
