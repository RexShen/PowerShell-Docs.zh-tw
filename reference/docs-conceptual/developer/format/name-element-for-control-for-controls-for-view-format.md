---
title: View 之控制項的控制項的名稱元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365097"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>檢視之控制項的控制項的名稱元素 (格式)

指定控制項的名稱。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（格式）控制項元素（格式）控制項專案（適用于 view 的 View （Format） Name 元素）（格式）

## <a name="syntax"></a>語法

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `Name` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 控制項的控制項元素（格式）](./control-element-for-controls-for-view-format.md)|定義可供視圖使用的控制項，以及用來參考控制項的名稱。|

## <a name="text-value"></a>文字值

指定用來參考控制項的名稱。

## <a name="remarks"></a>備註

這裡指定的名稱可用於下列專案，以參考此控制項。

- 建立 [資料表]、[清單]、[寬] 或 [自訂] 控制項時，控制項可以由下列元素指定： [ [GroupBy] 元素（格式）](./groupby-element-for-view-format.md)

- 建立可供視圖使用的另一個控制項時，這個控制項可以由下列元素指定： [ExpressionBinding 元素用於 CustomItem 的控制項（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[View 控制項的控制項元素（格式）](./control-element-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
