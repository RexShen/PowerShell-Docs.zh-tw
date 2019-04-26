---
title: 用於檢視 （格式） 的控制項 CustomEntry CustomItem 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066374"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)

定義控制項所顯示的資料和顯示方式。 定義可供檢視的控制項時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry 用於檢視 （格式） 的控制項的檢視 （格式） CustomItem 元素的控制項的檢視 （格式） CustomEntry 元素

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

下列各節說明屬性、 子項目和父項目`CustomItem`項目。 如需詳細資訊，請參閱 < 備註 >。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 定義控制項所顯示的資料。|
|[用於檢視 （格式） 的控制項 CustomItem 的框架項目](./frame-element-for-customitem-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 定義資料的顯示方式，例如將資料轉移至左邊或右邊。|
|[CustomItem 控制項的檢視 （格式） 的新行項目](./newline-element-for-customitem-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 將控制項的顯示中的空白行。|
|[CustomItem 用於檢視 （格式） 的控制項的文字項目](./text-element-for-customitem-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 將控制項的顯示文字，例如括號或括號。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[用於檢視 （格式） 的控制項 CustomEntries CustomEntry 項目](./customentry-element-for-customentries-for-controls-for-view-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

當指定的子項目`CustomItem`項目，請記住下列：

- 必須依照以下順序新增子項目： `ExpressionBinding`， `NewLine`， `Text`，和`Frame`。

- ，您可以指定序列的數目沒有上限限制。

- 在每個序列中，沒有任何數目的最大限制`ExpressionBinding`您可以使用的項目。

## <a name="see-also"></a>另請參閱

[ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項 CustomItem 的框架項目](./frame-element-for-customitem-for-controls-for-view-format.md)

[CustomItem 控制項的檢視 （格式） 的新行項目](./newline-element-for-customitem-for-controls-for-view-format.md)

[CustomItem 用於檢視 （格式） 的控制項的文字項目](./text-element-for-customitem-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
