---
title: Configuration 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363497"
---
# <a name="configuration-element-format"></a>設定元素 (格式)

代表格式化檔案的最上層元素。

Configuration 元素

## <a name="syntax"></a>語法

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `Configuration` 元素的父元素。 此元素必須是每個格式化檔案的根項目，且此元素必須包含至少一個子專案。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定的 Controls 元素（格式）](./controls-element-for-configuration-format.md)|選擇性元素。<br /><br /> 定義可供格式檔案的所有視圖使用的通用控制項。|
|[DefaultSettings 元素（格式）](./defaultsettings-element-format.md)|選擇性元素。<br /><br /> 定義套用至格式化檔案所有視圖的一般設定。|
|[SelectionSets 元素格式](./selectionsets-element-format.md)|選擇性元素。<br /><br /> 定義一組通用的 .NET 物件，可供格式化檔案的所有視圖使用。|
|[ViewDefinitions 元素（格式）](./viewdefinitions-element-format.md)|選擇性元素。<br /><br /> 定義用來顯示物件的視圖。|

### <a name="parent-elements"></a>父元素

無。

## <a name="remarks"></a>備註

格式化檔案會定義物件的顯示方式。 在大部分的情況下，這個根項目包含[ViewDefinitions](./viewdefinitions-element-format.md)元素，可定義格式檔案的資料表、清單和寬視圖。 除了 view 定義以外，格式檔案也可以定義這些視圖可以使用的一般選取範圍、設定和控制項。

## <a name="see-also"></a>另請參閱

[設定的 Controls 元素（格式）](./controls-element-for-configuration-format.md)

[DefaultSettings 元素（格式）](./defaultsettings-element-format.md)

[SelectionSets 元素（格式）](./selectionsets-element-format.md)

[ViewDefinitions 元素（格式）](./viewdefinitions-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
