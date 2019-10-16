---
title: GroupBy 之 CustomControl 的 CustomEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364087"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)

提供控制項的定義。 此元素是在定義新物件群組的顯示方式時使用。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 元素（適用于 GroupBy 的 CustomControl）的 CustomControl 元素（格式）

## <a name="syntax"></a>語法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述 `CustomEntries` 元素的屬性、子項目和父元素。 可以指定的子項目數目沒有上限。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-groupby-format.md)|必要元素。<br /><br /> 提供控制項的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomControl 元素（格式）](./customcontrol-element-for-groupby-format.md)|定義顯示新群組的自訂控制項。|

## <a name="remarks"></a>備註

在大部分情況下，控制項只有一個定義，在單一 @no__t 0 元素中指定。 不過，如果您想要使用相同的控制項來顯示不同的群組，也可以提供多個定義。 在這些情況下，您可以定義群組的 @no__t 0 元素。

## <a name="see-also"></a>另請參閱

[View 之控制項的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-controls-for-view-format.md)

[GroupBy 的 CustomControl 元素（格式）](./customcontrol-element-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
