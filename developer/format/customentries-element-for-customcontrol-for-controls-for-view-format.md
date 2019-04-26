---
title: 用於檢視 （格式） 的控制項 CustomControl CustomEntries 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066574"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>檢視之控制項的 CustomControl 的 CustomEntries 元素 (格式)

提供控制項的定義。 定義可供檢視的控制項時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目用於檢視 （格式） 的控制項 CustomControl

## <a name="syntax"></a>語法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`CustomEntries`項目。 沒有任何最大的限制，您可以指定的子項目數目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用於檢視 （格式） 的控制項 CustomEntries CustomEntry 項目](./customentry-element-for-customentries-for-controls-for-view-format.md)|必要項目。<br /><br /> 提供控制項的定義。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[用於檢視 （格式） 的控制項的控制項 CustomControl 項目](./customcontrol-element-for-control-for-controls-for-view-format.md)|定義檢視所使用的控制項。|

## <a name="remarks"></a>備註

在大部分情況下，控制項有只有一個定義中，指定在單一`CustomEntry`項目。 不過，就可以提供多個定義，如果您想要使用相同的控制項來顯示不同的.NET 物件。 在這些情況下，您可以定義`CustomEntry`每個物件或一組物件的項目。

## <a name="see-also"></a>另請參閱

[用於檢視 （格式） 的控制項 CustomEntries CustomEntry 項目](./customentry-element-for-customentries-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項的控制項 CustomControl 項目](./customcontrol-element-for-control-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
