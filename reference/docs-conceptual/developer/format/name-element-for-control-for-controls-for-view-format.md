---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的控制項的名稱元素 (格式)
description: 檢視之控制項的控制項的名稱元素 (格式)
ms.openlocfilehash: 52b7170777a35596767c34f2d58106dfa6479567
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666479"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>檢視之控制項的控制項的名稱元素 (格式)

指定控制項的名稱。

設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) 控制項專案 (格式) 控制項專案 (格式) 控制項的控制項 (格式) 格式控制項的控制項的控制項元素

## <a name="syntax"></a>語法

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `Name` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[View (格式之控制項的控制項元素) ](./control-element-for-controls-for-view-format.md)|定義可供視圖使用的控制項，以及用來參考控制項的名稱。|

## <a name="text-value"></a>文字值

指定用來參考控制項的名稱。

## <a name="remarks"></a>備註

此處指定的名稱可用於下列元素，以參考此控制項。

- 當您建立資料表、清單、寬或自訂控制項時，您可以透過下列元素指定控制項： [view (格式的 GroupBy 元素) ](./groupby-element-for-view-format.md)

- 建立可供視圖使用的另一個控制項時，此控制項可以由下列元素指定： [view (格式之控制項的 CustomItem 的 ExpressionBinding 元素) ](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)

[檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[View (格式之控制項的控制項元素) ](./control-element-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
