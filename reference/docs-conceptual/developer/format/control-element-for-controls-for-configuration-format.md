---
title: 設定 (格式之控制項的控制項元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9447efac84cff3cc33468aeebc97a8bdd6137518
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783818"
---
# <a name="control-element-for-controls-for-configuration-format"></a>設定之控制項的控制項元素 (格式)

定義可供格式檔案的所有視圖使用的通用控制項，以及用來參考控制項的名稱。

Configuration 元素 (格式) Controls 設定的控制項元素 (格式設定 (格式控制項的) 控制項專案) 

## <a name="syntax"></a>語法

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `Control` 。 您必須只指定其中一個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的控制項 CustomControl 元素 (格式)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|必要元素。<br /><br /> 定義控制項。|
|[設定 (格式之控制項的名稱元素) ](./name-element-for-control-for-controls-for-configuration-format.md)|必要元素。<br /><br /> 指定用來參考控制項的名稱。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[控制設定 (格式的元素) ](./controls-element-for-configuration-format.md)|定義可供格式檔案或其他控制項的所有視圖使用的通用控制項。|

## <a name="remarks"></a>備註

提供給這個控制項的名稱可以在下列元素中參考：

- [CustomItem (格式的 ExpressionBinding 元素) ](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [View (格式的 GroupBy 元素) ](./groupby-element-for-view-format.md)

## <a name="see-also"></a>另請參閱

[控制設定 (格式的元素) ](./controls-element-for-configuration-format.md)

[CustomControl 元素，用於控制設定 (格式) ](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[CustomItem (格式的 ExpressionBinding 元素) ](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[View (格式的 GroupBy 元素) ](./groupby-element-for-view-format.md)

[設定之控制項的控制項的名稱元素 (格式)](./name-element-for-control-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
