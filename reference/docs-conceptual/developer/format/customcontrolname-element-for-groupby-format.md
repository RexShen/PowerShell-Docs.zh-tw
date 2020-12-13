---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 的 CustomControlName 元素 (格式)
description: GroupBy 的 CustomControlName 元素 (格式)
ms.openlocfilehash: 03664fe4d5559312e2720a3892493c90c15f7501
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655417"
---
# <a name="customcontrolname-element-for-groupby-format"></a>GroupBy 的 CustomControlName 元素 (格式)

指定用來顯示新群組的自訂控制項名稱。 定義資料表、清單、寬或自訂控制項時，會使用這個元素。

ViewDefinitions 元素格式的設定元素 (格式) 元素 (格式) View 元素 (格式) groupby (格式) groupby 的元素 (格式) 

## <a name="syntax"></a>語法

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `CustomControlName` 。

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

您可以建立可供格式化檔案的所有視圖使用的通用控制項，也可以建立可供特定視圖使用的 view 控制項。 下列元素會指定這些自訂控制項的名稱：

- [設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

- [檢視之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)

[設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

[檢視之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
