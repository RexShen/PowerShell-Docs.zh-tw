---
title: 設定之控制項的 CustomControl 的 CustomEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368817"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>設定之控制項的 CustomControl 的 CustomEntries 元素 (格式)

提供通用控制項的定義。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）編排

## <a name="syntax"></a>語法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `CustomEntries` 專案的父元素。 您必須指定一或多個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|項目|說明|
|-------------|-----------------|
|[設定之控制項的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供通用控制項的定義。|

### <a name="parent-elements"></a>父元素

|項目|說明|
|-------------|-----------------|
|[設定之控制項的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|定義通用控制項。|

## <a name="remarks"></a>備註

在大部分的情況下，控制項只有一個定義，在單一 `CustomEntry` 專案中定義。 不過，如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可能會有多個定義。 在這些情況下，您可以為每個物件或一組物件定義一個 `CustomEntry` 元素。

## <a name="see-also"></a>另請參閱

[設定之控制項的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[設定之控制項的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
