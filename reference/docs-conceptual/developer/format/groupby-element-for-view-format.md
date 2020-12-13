---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視的 GroupBy 元素 (格式)
description: 檢視的 GroupBy 元素 (格式)
ms.openlocfilehash: d8ca93a3b2c1490928885579919c07f5eb274cd8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652108"
---
# <a name="groupby-element-for-view-format"></a>檢視的 GroupBy 元素 (格式)

定義如何顯示新的物件群組。 定義資料表、清單、寬或自訂控制項時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) GroupBy 專案的格式 (

## <a name="syntax"></a>語法

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomControl 元素 (格式)](./customcontrol-element-for-groupby-format.md)|選擇性項目。<br /><br /> 定義顯示新群組的自訂控制項。|
|[GroupBy 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-groupby-format.md)|選擇性項目。<br /><br /> 指定用來顯示新群組的控制項名稱。|
|[GroupBy 的標籤元素 (格式)](./label-element-for-groupby-format.md)|選擇性項目。<br /><br /> 指定當遇到新群組時所顯示的標籤。|
|[GroupBy 的 PropertyName 元素 (格式)](./propertyname-element-for-groupby-format.md)|選擇性項目。<br /><br /> 指定每當新群組值變更時，就會啟動新群組的 .NET 屬性。|
|[GroupBy 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-groupby-format.md)|選擇性項目。<br /><br /> 指定每當新群組值變更時，會啟動新群組的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視元素 (格式)](./view-element-format.md)|定義顯示一或多個 .NET 物件的視圖。|

## <a name="remarks"></a>備註

定義如何顯示新的物件群組時，您必須指定將啟動新群組的屬性或腳本。不過，您不能同時指定這兩者。

## <a name="see-also"></a>另請參閱

[GroupBy 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-groupby-format.md)

[GroupBy 的標籤元素 (格式)](./label-element-for-groupby-format.md)

[GroupBy 的 PropertyName 元素 (格式)](./propertyname-element-for-groupby-format.md)

[GroupBy 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-groupby-format.md)

[檢視元素 (格式)](./view-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
