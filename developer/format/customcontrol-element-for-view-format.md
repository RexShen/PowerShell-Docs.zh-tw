---
title: CustomControl 檢視 （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861254"
---
# <a name="customcontrol-element-for-view-format"></a>檢視的 CustomControl 元素 (格式)

定義檢視的自訂控制項格式。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式）

## <a name="syntax"></a>語法

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`CustomControl`項目。 您必須指定一個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomEntries CustomControl 檢視 （格式） 的項目](./customentries-element-for-customcontrol-for-view-format.md)|必要項目。<br /><br /> 提供自訂的控制項檢視的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[檢視項目 （格式）](./view-element-format.md)|定義用來顯示一或多個.NET 物件的檢視。|

## <a name="remarks"></a>備註

在大部分情況下，只有一個定義需要為每個控制項檢視中，但可提供多個定義，如果您想要使用相同的檢視來顯示不同的.NET 物件。 在這些情況下，您可以針對每個物件或一組物件提供不同的定義。

## <a name="see-also"></a>另請參閱

[CustomEntries CustomControl 檢視 （格式） 的項目](./customentries-element-for-customcontrol-for-view-format.md)

[檢視項目 （格式）](./view-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
