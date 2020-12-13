---
ms.date: 09/13/2016
ms.topic: reference
title: 設定元素 (格式)
description: 設定元素 (格式)
ms.openlocfilehash: 0524736d40dd7a7acb0b6fb61d1438b75672c240
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655685"
---
# <a name="configuration-element-format"></a>設定元素 (格式)

代表格式化檔案的最上層元素。

組態元素

## <a name="syntax"></a>語法

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `Configuration` 。 這個元素必須是每個格式化檔案的根項目，而且此元素必須包含至少一個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定的控制項元素 (格式)](./controls-element-for-configuration-format.md)|選擇性項目。<br /><br /> 定義可供格式化檔案的所有視圖使用的通用控制項。|
|[DefaultSettings 元素 (格式)](./defaultsettings-element-format.md)|選擇性項目。<br /><br /> 定義適用于格式檔案所有視圖的一般設定。|
|[SelectionSets 元素格式](./selectionsets-element-format.md)|選擇性項目。<br /><br /> 定義可供格式化檔案的所有視圖使用的通用 .NET 物件集。|
|[ViewDefinitions 元素 (格式)](./viewdefinitions-element-format.md)|選擇性項目。<br /><br /> 定義用來顯示物件的視圖。|

### <a name="parent-elements"></a>父項目

無。

## <a name="remarks"></a>備註

格式化檔案會定義物件的顯示方式。 在大部分的情況下，此根項目包含定義格式檔案之資料表、清單和寬視圖的 [ViewDefinitions](./viewdefinitions-element-format.md) 專案。 除了 view 定義，格式化檔案也可以定義這些視圖可使用的常用選項群組、設定和控制項。

## <a name="see-also"></a>另請參閱

[設定的控制項元素 (格式)](./controls-element-for-configuration-format.md)

[DefaultSettings 元素 (格式)](./defaultsettings-element-format.md)

[SelectionSets 元素 (格式)](./selectionsets-element-format.md)

[ViewDefinitions 元素 (格式)](./viewdefinitions-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
