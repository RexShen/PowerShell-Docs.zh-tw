---
title: ListControl （格式） 的 EntrySelectedBy TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059689"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)

指定使用此項目清單檢視的.NET 型別。 類型可指定清單項目數目沒有限制。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目 （格式） EntrySelectedBy 項目 ListEntry （格式） 類型名稱項目ListControl （格式） 的 EntrySelectedBy

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`TypeName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EntrySelectedBy ListEntry （格式） 的項目](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|定義.NET 型別，使用此清單項目或要使用此項目必須存在的條件。|

## <a name="text-value"></a>文字值

指定完整.NET 類型名稱，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>備註

每個清單項目必須至少一個型別名稱、 選取項目集或選擇條件的定義。

如需如何使用這個項目在清單檢視中的詳細資訊，請參閱[清單檢視](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例示範如何指定設定項目清單檢視的選取範圍。

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[EntrySelectedBy ListEntry （格式） 的項目](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntry （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
