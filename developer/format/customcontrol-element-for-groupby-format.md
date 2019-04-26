---
title: CustomControl GroupBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2472e256-8f4f-4288-8b67-a3300649dafa
caps.latest.revision: 9
ms.openlocfilehash: 2e84e770a345e272d4c5917b00afe7520840e1db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066748"
---
# <a name="customcontrol-element-for-groupby-format"></a>GroupBy 的 CustomControl 元素 (格式)

定義自訂控制項，則會顯示新的群組。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） 的 GroupBy （格式） 的 CustomControl 項目

## <a name="syntax"></a>語法

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`CustomControl`項目。 您可以指定任意數目的子項目，並以任何順序列出。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomControl CustomEntries 項目](./customentries-element-for-customcontrol-for-groupby-format.md)|必要項目。<br /><br /> 提供控制項的定義。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)|定義 Windows PowerShell 顯示新的一整組物件的方式。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[GroupBy （格式） 的 CustomControl CustomEntries 項目](./customentries-element-for-customcontrol-for-groupby-format.md)

[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
