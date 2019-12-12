---
title: View 的 CustomControl 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363357"
---
# <a name="customcontrol-element-for-view-format"></a>檢視的 CustomControl 元素 (格式)

定義視圖的自訂控制項格式。

Configuration 元素（格式） ViewDefinitions 元素（格式） CustomControl 元素（格式）

## <a name="syntax"></a>語法

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `CustomControl` 專案的父元素。 您必須指定一個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomControl for View 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-view-format.md)|必要項目。<br /><br /> 提供自訂控制項視圖的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 元素（格式）](./view-element-format.md)|定義用來顯示一個或多個 .NET 物件的視圖。|

## <a name="remarks"></a>備註

在大部分情況下，每個控制項視圖只需要一個定義，但是如果您想要使用相同的視圖來顯示不同的 .NET 物件，則可以提供多個定義。 在這些情況下，您可以為每個物件或一組物件提供個別的定義。

## <a name="see-also"></a>另請參閱

[CustomControl for View 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-view-format.md)

[View 元素（格式）](./view-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
