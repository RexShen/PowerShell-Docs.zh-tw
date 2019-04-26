---
title: CustomEntry 檢視 （格式） 的 EntrySelectedBy TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083972"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>檢視之 CustomEntry 的 EntrySelectedBy 的 TypeName 元素 (格式)

指定使用自訂的控制項檢視此定義的.NET 型別。 類型可定義指定的數目沒有限制。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl 檢視 （格式） 的檢視 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry 檢視 （格式） 類型名稱的項目為 EntrySelectedBy CustomEntry 檢視 （格式） 的項目

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`TypeName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[EntrySelectedBy CustomEntry 檢視 （格式） 的項目](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定義使用此自訂控制項的檢視定義的.NET 類型或必須存在於要使用此定義的條件。|

## <a name="text-value"></a>文字值

指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>備註

每個自訂控制項的檢視定義必須至少一個型別名稱、 選取項目集或選擇條件的定義。

如需詳細的自訂控制項的檢視元件的相關資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。

## <a name="see-also"></a>另請參閱

[建立自訂控制項](./creating-custom-controls.md)

[EntrySelectedBy CustomEntry 檢視 （格式） 的項目](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
