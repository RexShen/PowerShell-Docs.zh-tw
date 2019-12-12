---
title: WideControl 的 AutoSize 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369047"
---
# <a name="autosize-element-for-widecontrol-format"></a>WideControl 的 AutoSize 元素 (格式)

指定是否根據資料大小來調整資料行大小和資料行數目。

WideControl 的 Configuration 元素（格式） ViewDefinitions 元素（格式） WideControl 元素（格式） Autosize 元素（格式）

## <a name="syntax"></a>語法

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `AutoSize` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideControl 元素（格式）](./widecontrol-element-format.md)|定義視圖的寬（單一值）清單格式。|

## <a name="remarks"></a>備註

定義寬視圖時，您可以加入 `AutoSize` 專案或[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)專案，但無法同時新增這兩個元素。

如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

如需寬視圖的範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[WideControl 的 ColumnNumber 元素（格式）](./columnnumber-element-for-widecontrol-format.md)

[建立寬型視圖](./creating-a-wide-view.md)

[WideControl 元素（格式）](./widecontrol-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
