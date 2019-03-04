---
title: GroupBy （格式） 的 CustomControl CustomEntries 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853674"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)

提供控制項的定義。 定義新的群組物件的顯示方式時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 元素 CustomControl 的 GroupBy （格式） 的 GroupBy （格式） CustomEntries 元素的檢視 （格式） CustomControl 項目

## <a name="syntax"></a>語法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`CustomEntries`項目。 沒有任何最大的限制，您可以指定的子項目數目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomControl CustomEntry 項目](./customentry-element-for-customcontrol-for-groupby-format.md)|必要項目。<br /><br /> 提供控制項的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CustomControl GroupBy （格式） 的項目](./customcontrol-element-for-groupby-format.md)|定義自訂控制項，則會顯示新的群組。|

## <a name="remarks"></a>備註

在大部分情況下，控制項有只有一個定義中，指定在單一`CustomEntry`項目。 不過，就可以提供多個定義，如果您想要使用相同的控制項來顯示不同的群組。 在這些情況下，您可以定義`CustomEntry`群組的項目。

## <a name="see-also"></a>另請參閱

[用於檢視 （格式） 的控制項 CustomEntries CustomEntry 項目](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl GroupBy （格式） 的項目](./customcontrol-element-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
