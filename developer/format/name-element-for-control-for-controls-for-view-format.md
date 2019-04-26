---
title: 控制項名稱項目控制項的檢視 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065088"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>檢視之控制項的控制項的名稱元素 (格式)

指定控制項的名稱。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） 名稱的項目控制項的檢視 （格式）

## <a name="syntax"></a>語法

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`Name`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[用於檢視 （格式） 的控制項的控制項項目](./control-element-for-controls-for-view-format.md)|定義可供檢視和名稱，用來參考控制項的控制項。|

## <a name="text-value"></a>文字值

指定用來參考控制項的名稱。

## <a name="remarks"></a>備註

在這裡指定的名稱可以用於下列項目，來參考這個控制項。

- 在建立資料表、 清單、 寬或自訂的控制項檢視時，可以指定的控制項，由下列項目：[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

- 當建立另一個控制項，可供檢視時，此控制項可以指定下列項目：[ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項的控制項項目](./control-element-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
