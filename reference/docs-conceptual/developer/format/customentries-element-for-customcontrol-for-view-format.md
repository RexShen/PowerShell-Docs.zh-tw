---
title: CustomControl for View 的 CustomEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364077"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntries 元素 (格式)

提供自訂控制項視圖的定義。 自訂控制項視圖必須指定一或多個定義。

CustomControl for View 的設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（格式） CustomEntries 元素

## <a name="syntax"></a>語法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `CustomControlEntries` 專案的父元素。 您必須指定一或多個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomEntries for View 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|必要項目。<br /><br /> 提供自訂控制項視圖的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 的 CustomControl 元素（格式）](./customcontrol-element-for-view-format.md)|必要項目。<br /><br /> 定義視圖的自訂控制項格式。|

## <a name="remarks"></a>備註

在大部分的情況下，控制項只有一個定義，在單一 `CustomEntry` 專案中定義。 不過，如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可能會有多個定義。 在這些情況下，您可以為每個物件或一組物件定義一個 `CustomEntry` 元素。

## <a name="see-also"></a>另請參閱

[View 的 CustomControl 元素（格式）](./customcontrol-element-for-view-format.md)

[CustomEntries for View 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
