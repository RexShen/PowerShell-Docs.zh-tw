---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)
description: 檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)
ms.openlocfilehash: 67bff97c27cfedf046b17eea438efcd66ae2ee4a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666751"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)

定義控制項顯示的資料以及其顯示方式。 當定義可供視圖使用的控制項時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) Control 元素 (format) Control 元素 (format) format (CustomEntries) format 控制項控制項的控制項 (格式) 專案 (格式)  (格式控制項的控制項) 格式 CustomEntry 專案格式的控制項 CustomEntries 元素格式的控制項

## <a name="syntax"></a>語法

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `CustomItem` 。 如需詳細資訊，請參閱＜備註＞。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 定義控制項所顯示的資料。|
|[檢視之控制項的 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 定義顯示資料的方式，例如將資料向左或向右移動。|
|[檢視之控制項的 CustomItem 的 NewLine 元素 (格式)](./newline-element-for-customitem-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 在控制項的顯示中加入空白行。|
|[檢視之控制項的 CustomItem 的文字元素 (格式)](./text-element-for-customitem-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 將文字（例如括弧或括弧）新增至控制項的顯示。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)](./customentry-element-for-customentries-for-controls-for-view-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

指定元素的子項目時 `CustomItem` ，請記住下列事項：

- 子項目必須以下列順序加入： `ExpressionBinding` 、 `NewLine` 、 `Text` 和 `Frame` 。

- 您可以指定的序列數目沒有上限。

- 在每個序列中，您可以使用的元素數目沒有最大限制 `ExpressionBinding` 。

## <a name="see-also"></a>另請參閱

[檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[檢視之控制項的 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-controls-for-view-format.md)

[檢視之控制項的 CustomItem 的 NewLine 元素 (格式)](./newline-element-for-customitem-for-controls-for-view-format.md)

[檢視之控制項的 CustomItem 的文字元素 (格式)](./text-element-for-customitem-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
