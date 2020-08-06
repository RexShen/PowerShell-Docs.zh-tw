---
title: CustomEntry 之控制項的 CustomItem 元素，用於設定 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bb8124242496f192717127f201674bc1428e5de0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785858"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>設定之控制項的 CustomEntry 的 CustomItem 元素 (格式)

定義控制項所顯示的資料及其顯示方式。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 專案 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的 CustomControl 的 CustomControl 元素 CustomControl 的設定) 格式 (CustomItem 元素適用于設定的控制項的 CustomEntry 的 CustomEntry 元素

## <a name="syntax"></a>語法

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `CustomItem` 。 如需詳細資訊，請參閱＜備註＞。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 定義控制項所顯示的資料。|
|[設定之控制項的 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 定義資料的顯示方式，例如將資料向左或向右移位。|
|[設定之控制項的 CustomItem 的 NewLine 元素 (格式)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 將空白行加入控制項的顯示中。|
|[設定之控制項的 CustomItem 的文字元素 (格式)](./text-element-for-customitem-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 將文字（例如括弧或括弧）新增至控制項的顯示。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

指定元素的子項目時 `CustomItem` ，請記住下列事項：

- 子項目必須以下列順序加入： `ExpressionBinding` 、 `NewLine` 、 `Text` 和 `Frame` 。

- 您可以指定的序列數目沒有上限。

- 在每個序列中， `ExpressionBinding` 您可以使用的元素數目沒有上限。

## <a name="see-also"></a>另請參閱

[設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[設定之控制項的 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[設定之控制項的 CustomItem 的 NewLine 元素 (格式)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[設定之控制項的 CustomItem 的文字元素 (格式)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
