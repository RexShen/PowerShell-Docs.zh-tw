---
title: CustomItem CustomEntry 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862934"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>設定之控制項的 CustomEntry 的 CustomItem 元素 (格式)

定義控制項所顯示的資料和顯示方式。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry 控制項組態的組態 （格式） CustomItem 元素的控制項的格式） CustomEntry 項目

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

下列各節說明屬性、 子項目和父項目`CustomItem`項目。 如需詳細資訊，請參閱 < 備註 >。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ExpressionBinding CustomItem 組態 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 定義控制項所顯示的資料。|
|[CustomItem 組態 （格式） 的控制項的框架項目](./frame-element-for-customitem-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 定義資料的顯示方式，例如將資料轉移至左邊或右邊。|
|[CustomItem 組態 （格式） 的控制項的新行項目](./newline-element-for-customitem-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 將控制項的顯示中的空白行。|
|[CustomItem 組態 （格式） 的控制項的文字項目](./text-element-for-customitem-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 將控制項的顯示文字，例如括號或括號。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CustomEntry CustomControl 組態 （格式） 的控制項的項目](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

當指定的子項目`CustomItem`項目，請記住下列：

- 必須依照以下順序新增子項目： `ExpressionBinding`， `NewLine`， `Text`，和`Frame`。

- ，您可以指定序列的數目沒有上限限制。

- 在每個序列中，沒有任何數目的最大限制`ExpressionBinding`您可以使用的項目。

## <a name="see-also"></a>另請參閱

[ExpressionBinding CustomItem 組態 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[CustomItem 組態 （格式） 的控制項的框架項目](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[CustomItem 組態 （格式） 的控制項的新行項目](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[CustomItem 組態 （格式） 的控制項的文字項目](./text-element-for-customitem-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
