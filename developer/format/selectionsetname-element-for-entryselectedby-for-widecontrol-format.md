---
title: WideControl （格式） 的 EntrySelectedBy SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856794"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>WideControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定一組定義的.NET 物件。 每當顯示下列其中一個這些物件，則會使用定義。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） EntrySelectedBy 項目用於 WideEntry （格式） SelectionSetName 元素WideEntry （格式） 的 EntrySelectedBy

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EntrySelectedBy WideEntry （格式） 的項目](./entryselectedby-element-for-wideentry-format.md)|定義.NET 型別，使用此寬的項目或要使用此項目必須存在的條件。|

## <a name="text-value"></a>文字值

指定選取項目集的名稱。

## <a name="remarks"></a>備註

每個定義必須指定一個型別名稱、 選取項目集或選取條件。

您想要在多個檢視中定義一組所使用的物件時，會通常會使用選取項目集。 例如，您可能要建立的資料表檢視和相同的物件集的清單檢視。 如需定義選取項目集的詳細資訊，請參閱[定義設定的物件檢視](./defining-selection-sets.md)。

寬型檢視的其他元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[定義選取範圍](./defining-selection-sets.md)

[EntrySelectedBy WideEntry （格式） 的項目](./entryselectedby-element-for-wideentry-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
