---
title: AutoSize WideControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857084"
---
# <a name="autosize-element-for-widecontrol-format"></a>WideControl 的 AutoSize 元素 (格式)

指定是否資料行大小和資料行數目根據調整大小的資料大小。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） 自動調整項目 WideControl （格式）

## <a name="syntax"></a>語法

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`AutoSize`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideControl 項目 （格式）](./widecontrol-element-format.md)|寬 （單一值） 會定義檢視的清單格式。|

## <a name="remarks"></a>備註

當定義的寬型檢視，您可以加入`AutoSize`項目或[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)項目，但是您無法新增這兩個。

如需詳細的寬型檢視元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。

如需寬型檢視的範例，請參閱 < [（基本） 的寬型檢視](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[ColumnNumber WideControl （格式） 的項目](./columnnumber-element-for-widecontrol-format.md)

[建立寬型檢視](./creating-a-wide-view.md)

[WideControl 項目 （格式）](./widecontrol-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
