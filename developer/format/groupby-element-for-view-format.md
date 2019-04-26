---
title: 檢視 （格式） 的 GroupBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065530"
---
# <a name="groupby-element-for-view-format"></a>檢視的 GroupBy 元素 (格式)

定義新的一整組物件的顯示方式。 定義資料表、 清單、 寬，或自訂的控制項檢視時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目進行檢視 （格式）

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

下列各節說明屬性、 子項目和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomControl GroupBy （格式） 的項目](./customcontrol-element-for-groupby-format.md)|選擇性的項目。<br /><br /> 定義自訂控制項，顯示新的群組。|
|[CustomControlName GroupBy （格式） 的項目](./customcontrolname-element-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定用來顯示新的群組控制項的名稱。|
|[GroupBy （格式） 的 label 項目](./label-element-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定在發現新的群組時，會顯示的標籤。|
|[GroupBy （格式） 的屬性名稱項目](./propertyname-element-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定.NET 屬性在啟動新的群組，其值變更時。|
|[GroupBy （格式） 的指令碼區塊項目](./scriptblock-element-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定的指令碼，其值變更時，會啟動新的群組。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[檢視項目 （格式）](./view-element-format.md)|定義顯示一或多個.NET 物件的檢視。|

## <a name="remarks"></a>備註

在定義新的群組物件的顯示方式時，您必須指定屬性或指令碼會啟動新的群組;不過，您無法同時指定。

## <a name="see-also"></a>另請參閱

[CustomControlName GroupBy （格式） 的項目](./customcontrolname-element-for-groupby-format.md)

[GroupBy （格式） 的 label 項目](./label-element-for-groupby-format.md)

[GroupBy （格式） 的屬性名稱項目](./propertyname-element-for-groupby-format.md)

[GroupBy （格式） 的指令碼區塊項目](./scriptblock-element-for-groupby-format.md)

[檢視項目 （格式）](./view-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
