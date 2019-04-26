---
title: CustomEntries CustomControl 檢視 （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066510"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntries 元素 (格式)

提供自訂的控制項檢視的定義。 自訂控制項的檢視必須指定一個或多個定義。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl 檢視 （格式）

## <a name="syntax"></a>語法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`CustomControlEntries`項目。 您必須指定一個以上的子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomEntry CustomEntries 檢視 （格式） 的項目](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|必要項目。<br /><br /> 提供自訂的控制項檢視的定義。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CustomControl 檢視 （格式） 的項目](./customcontrol-element-for-view-format.md)|必要項目。<br /><br /> 定義檢視的自訂控制項格式。|

## <a name="remarks"></a>備註

在大部分情況下，控制項有只有一個定義，其定義於單一`CustomEntry`項目。 不過，它是可以有多個定義，如果您想要使用相同的控制項來顯示不同的.NET 物件。 在這些情況下，您可以定義`CustomEntry`每個物件或一組物件的項目。

## <a name="see-also"></a>另請參閱

[CustomControl 檢視 （格式） 的項目](./customcontrol-element-for-view-format.md)

[CustomEntry CustomEntries 檢視 （格式） 的項目](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
