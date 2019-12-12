---
title: View 的 GroupBy 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363627"
---
# <a name="groupby-element-for-view-format"></a>檢視的 GroupBy 元素 (格式)

定義新群組物件的顯示方式。 當定義資料表、清單、寬型或自訂控制項視圖時，會使用這個元素。

設定元素（格式） ViewDefinitions 元素（格式） View 元素（格式） GroupBy 元素（格式）

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

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomControl 元素（格式）](./customcontrol-element-for-groupby-format.md)|選擇性項目。<br /><br /> 定義顯示新群組的自訂控制項。|
|[GroupBy 的 CustomControlName 元素（格式）](./customcontrolname-element-for-groupby-format.md)|選擇性項目。<br /><br /> 指定用來顯示新群組之控制項的名稱。|
|[GroupBy 的標籤元素（格式）](./label-element-for-groupby-format.md)|選擇性項目。<br /><br /> 指定遇到新群組時所顯示的標籤。|
|[GroupBy 的 PropertyName 元素（格式）](./propertyname-element-for-groupby-format.md)|選擇性項目。<br /><br /> 指定 .NET 屬性，每當其值變更時，就會啟動新的群組。|
|[GroupBy 的 ScriptBlock 元素（格式）](./scriptblock-element-for-groupby-format.md)|選擇性項目。<br /><br /> 指定每當新群組的值變更時，就會啟動的腳本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 元素（格式）](./view-element-format.md)|定義顯示一或多個 .NET 物件的視圖。|

## <a name="remarks"></a>備註

當定義新群組物件的顯示方式時，您必須指定將啟動新群組的屬性或腳本。不過，您不能同時指定這兩者。

## <a name="see-also"></a>另請參閱

[GroupBy 的 CustomControlName 元素（格式）](./customcontrolname-element-for-groupby-format.md)

[GroupBy 的標籤元素（格式）](./label-element-for-groupby-format.md)

[GroupBy 的 PropertyName 元素（格式）](./propertyname-element-for-groupby-format.md)

[GroupBy 的 ScriptBlock 元素（格式）](./scriptblock-element-for-groupby-format.md)

[View 元素（格式）](./view-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
