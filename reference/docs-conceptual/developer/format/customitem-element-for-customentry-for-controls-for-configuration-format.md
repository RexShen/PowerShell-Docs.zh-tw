---
title: 設定之控制項的 CustomEntry 的 CustomItem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364027"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>設定之控制項的 CustomEntry 的 CustomItem 元素 (格式)

定義控制項所顯示的資料及其顯示方式。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl 控制項的設定（Format） CustomItem 元素

## <a name="syntax"></a>語法

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `CustomItem` 專案的父元素。 如需詳細資訊，請參閱備註。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 定義控制項所顯示的資料。|
|[用於設定之控制項的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 定義資料的顯示方式，例如將資料向左或向右移位。|
|[設定之控制項的 CustomItem 的新行元素（格式）](./newline-element-for-customitem-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 將空白行加入控制項的顯示中。|
|[設定之控制項的 CustomItem 的文字元素（格式）](./text-element-for-customitem-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 將文字（例如括弧或括弧）新增至控制項的顯示。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

指定 `CustomItem` 元素的子項目時，請記住下列事項：

- 子項目必須以下列順序加入： `ExpressionBinding`、`NewLine`、`Text`和 `Frame`。

- 您可以指定的序列數目沒有上限。

- 在每個序列中，您可以使用的 `ExpressionBinding` 元素數目沒有上限。

## <a name="see-also"></a>另請參閱

[設定之控制項的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[用於設定之控制項的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[設定之控制項的 CustomItem 的新行元素（格式）](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[設定之控制項的 CustomItem 的文字元素（格式）](./text-element-for-customitem-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
