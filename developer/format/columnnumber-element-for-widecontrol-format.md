---
title: ColumnNumber WideControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066901"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>WideControl 的 ColumnNumber 元素 (格式)

指定在寬型檢視中顯示的資料行數目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） ColumnNumber 項目 WideControl （格式）

## <a name="syntax"></a>語法

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`ColumnNumber`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[WideControl 項目 （格式）](./widecontrol-element-format.md)|寬 （單一值） 會定義檢視的清單格式。|

## <a name="text-value"></a>文字值

指定正整數值。

## <a name="remarks"></a>備註

當定義的寬型檢視，您可以加入`AutoSize`項目或`ColumnNumber`項目，但是您無法新增這兩個。

如需詳細的寬型檢視元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。

如需寬型檢視的範例，請參閱 < [（基本） 的寬型檢視](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[Autosize WideControl （格式） 的項目](./autosize-element-for-widecontrol-format.md)

[建立寬型檢視](./creating-a-wide-view.md)

[寬型檢視 （基本）](./wide-view-basic.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
