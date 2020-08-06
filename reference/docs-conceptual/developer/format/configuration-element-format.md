---
title: Configuration 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 90be02f8e27c0bd391e01da1a08ecd8eeb29b84c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783835"
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

下列各節說明屬性、子專案和元素的父元素 `Configuration` 。 此元素必須是每個格式化檔案的根項目，且此元素必須包含至少一個子專案。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定的控制項元素 (格式)](./controls-element-for-configuration-format.md)|選擇性項目。<br /><br /> 定義可供格式檔案的所有視圖使用的通用控制項。|
|[DefaultSettings 元素 (格式)](./defaultsettings-element-format.md)|選擇性項目。<br /><br /> 定義套用至格式化檔案所有視圖的一般設定。|
|[SelectionSets 元素格式](./selectionsets-element-format.md)|選擇性項目。<br /><br /> 定義一組通用的 .NET 物件，可供格式化檔案的所有視圖使用。|
|[ViewDefinitions 元素 (格式)](./viewdefinitions-element-format.md)|選擇性項目。<br /><br /> 定義用來顯示物件的視圖。|

### <a name="parent-elements"></a>父項目

無。

## <a name="remarks"></a>備註

格式化檔案會定義物件的顯示方式。 在大部分的情況下，這個根項目包含[ViewDefinitions](./viewdefinitions-element-format.md)元素，可定義格式檔案的資料表、清單和寬視圖。 除了 view 定義以外，格式檔案也可以定義這些視圖可以使用的一般選取範圍、設定和控制項。

## <a name="see-also"></a>另請參閱

[設定的控制項元素 (格式)](./controls-element-for-configuration-format.md)

[DefaultSettings 元素 (格式)](./defaultsettings-element-format.md)

[SelectionSets 元素 (格式)](./selectionsets-element-format.md)

[ViewDefinitions 元素 (格式)](./viewdefinitions-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
