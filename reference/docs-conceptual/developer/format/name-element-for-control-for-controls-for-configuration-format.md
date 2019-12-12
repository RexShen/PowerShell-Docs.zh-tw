---
title: 設定之控制項的控制項的名稱元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362707"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>設定之控制項的控制項的名稱元素 (格式)

指定控制項的名稱。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

設定專案（格式）控制項的設定（格式）控制項元素的元素，用於設定（格式）控制項的控制項（格式）

## <a name="syntax"></a>語法

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `Name` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的控制項元素（格式）](./control-element-for-controls-for-configuration-format.md)|定義可供格式檔案的所有視圖使用的通用控制項，以及用來參考控制項的名稱。|

## <a name="text-value"></a>文字值

指定用來參考此控制項的名稱。

## <a name="remarks"></a>備註

這裡指定的名稱可用於下列專案，以參考此控制項。

- 建立 [資料表]、[清單]、[寬] 或 [自訂] 控制項時，控制項可以由下列元素指定： [ [GroupBy] 元素（格式）](./groupby-element-for-view-format.md)

- 建立另一個通用控制項時，這個控制項可以由下列元素指定： [CustomItem 的 ExpressionBinding 元素（用於設定）（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- 建立可供視圖使用的控制項時，這個控制項可以由下列元素指定： [ExpressionBinding 元素，用於 CustomItem 的控制項（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[設定之控制項的控制項元素（格式）](./control-element-for-controls-for-configuration-format.md)

[設定之控制項的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
