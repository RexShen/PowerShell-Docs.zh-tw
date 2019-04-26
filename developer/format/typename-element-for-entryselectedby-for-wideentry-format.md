---
title: WideEntry （格式） 的 EntrySelectedBy TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083921"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)

指定.NET 型別定義。 每當此物件會顯示，則會使用定義。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） EntrySelectedBy 項目 WideEntry （WideEntry （格式） 類型名稱項目格式）

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
|[EntrySelectedBy WideEntry （格式） 的項目](./entryselectedby-element-for-wideentry-format.md)|定義.NET 型別，使用此寬的項目或要使用此項目必須存在的條件。|

## <a name="text-value"></a>文字值

指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>備註

一或多個.NET 類型、 選取項目集或選取條件，來定義必須存在，則必須指定每個寬的項目。

寬型檢視的其他元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[EntrySelectedBy WideEntry （格式） 的項目](./entryselectedby-element-for-wideentry-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
