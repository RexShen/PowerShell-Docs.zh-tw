---
title: View (格式) 的 GroupBy 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2f9071a3ebbc7cc2ccb7721dd518e82723e9cc4e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781421"
---
# <a name="groupby-element-for-view-format"></a>檢視的 GroupBy 元素 (格式)

定義新群組物件的顯示方式。 當定義資料表、清單、寬型或自訂控制項視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) GroupBy 元素以查看 (格式) 

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
|[GroupBy 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-groupby-format.md)|選擇性項目。<br /><br /> 指定用來顯示新群組之控制項的名稱。|
|[GroupBy 的標籤元素 (格式)](./label-element-for-groupby-format.md)|選擇性項目。<br /><br /> 指定遇到新群組時所顯示的標籤。|
|[GroupBy 的 PropertyName 元素 (格式)](./propertyname-element-for-groupby-format.md)|選擇性項目。<br /><br /> 指定 .NET 屬性，每當其值變更時，就會啟動新的群組。|
|[GroupBy 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-groupby-format.md)|選擇性項目。<br /><br /> 指定每當新群組的值變更時，就會啟動的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視元素 (格式)](./view-element-format.md)|定義顯示一或多個 .NET 物件的視圖。|

## <a name="remarks"></a>備註

當定義新群組物件的顯示方式時，您必須指定將啟動新群組的屬性或腳本。不過，您不能同時指定這兩者。

## <a name="see-also"></a>另請參閱

[GroupBy 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-groupby-format.md)

[GroupBy 的標籤元素 (格式)](./label-element-for-groupby-format.md)

[GroupBy 的 PropertyName 元素 (格式)](./propertyname-element-for-groupby-format.md)

[GroupBy 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-groupby-format.md)

[檢視元素 (格式)](./view-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
