---
title: GroupBy 的 CustomControl 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2472e256-8f4f-4288-8b67-a3300649dafa
caps.latest.revision: 9
ms.openlocfilehash: 2e84e770a345e272d4c5917b00afe7520840e1db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368957"
---
# <a name="customcontrol-element-for-groupby-format"></a>GroupBy 的 CustomControl 元素 (格式)

定義顯示新群組的自訂控制項。

ViewDefinitions 元素（格式）的專案（格式） View 元素（格式） groupby 元素（格式） GroupBy 的 CustomControl 元素（格式）

## <a name="syntax"></a>語法

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明 `CustomControl` 元素的屬性、子專案和父元素。 您可以指定任意數目的子項目，並依任何順序列出它們。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-groupby-format.md)|必要元素。<br /><br /> 提供控制項的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)|定義 Windows PowerShell 如何顯示新的物件群組。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[GroupBy 之 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-groupby-format.md)

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
