---
title: View 之控制項的 CustomControl 的 CustomEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368807"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>檢視之控制項的 CustomControl 的 CustomEntries 元素 (格式)

提供控制項的定義。 定義可供視圖使用的控制項時，會使用這個元素。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素View （格式）控制項的 CustomControl

## <a name="syntax"></a>語法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `CustomEntries` 專案的父元素。 可以指定的子項目數目沒有上限。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[View 之控制項的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-controls-for-view-format.md)|必要項目。<br /><br /> 提供控制項的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 控制項的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-view-format.md)|定義視圖所使用的控制項。|

## <a name="remarks"></a>備註

在大部分情況下，控制項只有一個定義，在單一 `CustomEntry` 元素中指定。 不過，如果您想要使用相同的控制項來顯示不同的 .NET 物件，就可以提供多個定義。 在這些情況下，您可以為每個物件或一組物件定義一個 `CustomEntry` 元素。

## <a name="see-also"></a>另請參閱

[View 之控制項的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-controls-for-view-format.md)

[View 控制項的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
