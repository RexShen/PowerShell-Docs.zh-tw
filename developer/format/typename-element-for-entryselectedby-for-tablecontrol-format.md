---
title: TableControl （格式） 的 EntrySelectedBy TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083955"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl 之 EntrySelectedBy 的 TypeName 元素 (格式)

指定.NET 型別，使用 [資料表] 檢視的這個項目。 可供指定的資料表項目類型的數目沒有限制。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 （格式） 類型名稱項目 EntrySelectedBy針對 TableRowEntry （格式）

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
|[EntrySelectedBy 項目 （格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定義.NET 型別，使用此項目或要使用此項目必須存在的條件。|

## <a name="text-value"></a>文字值

指定.NET 型別名稱。

## <a name="remarks"></a>備註

每個清單項目必須至少一個型別名稱、 選取項目集或選擇條件的定義。

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="see-also"></a>另請參閱

[建立資料表檢視](./creating-a-table-view.md)

[EntrySelectedBy 項目 （格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
