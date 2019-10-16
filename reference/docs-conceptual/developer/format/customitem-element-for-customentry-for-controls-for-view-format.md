---
title: View 之控制項的 CustomEntry 的 CustomItem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363937"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)

定義控制項所顯示的資料及其顯示方式。 定義可供視圖使用的控制項時，會使用這個元素。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for View （Format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for view （格式）的控制項 CustomEntry

## <a name="syntax"></a>語法

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `CustomItem` 元素的父元素。 如需詳細資訊，請參閱備註。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|選擇性元素。<br /><br /> 定義控制項所顯示的資料。|
|[View 之控制項的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-controls-for-view-format.md)|選擇性元素。<br /><br /> 定義資料的顯示方式，例如將資料向左或向右移位。|
|[View 之控制項的 CustomItem 的分行符號元素（格式）](./newline-element-for-customitem-for-controls-for-view-format.md)|選擇性元素。<br /><br /> 將空白行加入控制項的顯示中。|
|[View 之控制項的 CustomItem 的文字元素（格式）](./text-element-for-customitem-for-controls-for-view-format.md)|選擇性元素。<br /><br /> 將文字（例如括弧或括弧）新增至控制項的顯示。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 之控制項的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-controls-for-view-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

指定 `CustomItem` 元素的子項目時，請記住下列事項：

- 子項目必須以下列順序加入： `ExpressionBinding`、`NewLine`、`Text` 和 `Frame`。

- 您可以指定的序列數目沒有上限。

- 在每個序列中，您可以使用的 @no__t 0 元素數目沒有上限。

## <a name="see-also"></a>另請參閱

[View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[View 之控制項的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-controls-for-view-format.md)

[View 之控制項的 CustomItem 的分行符號元素（格式）](./newline-element-for-customitem-for-controls-for-view-format.md)

[View 之控制項的 CustomItem 的文字元素（格式）](./text-element-for-customitem-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
