---
title: 設定的 Controls 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368997"
---
# <a name="controls-element-for-configuration-format"></a>設定的控制項元素 (格式)

定義可供格式檔案的所有視圖使用的通用控制項。

Configuration 元素（格式）控制設定的元素（格式）

## <a name="syntax"></a>語法

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `Controls` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的控制項元素（格式）](./control-element-for-controls-for-configuration-format.md)|必要元素。<br /><br /> 定義可供格式檔案的所有視圖使用的通用控制項。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[Configuration 元素（格式）](./configuration-element-format.md)|代表格式化檔案的最上層元素。|

## <a name="remarks"></a>備註

您可以建立任意數目的通用控制項。 您必須針對每個控制項指定用來參考控制項的名稱，以及控制項的元件。

## <a name="see-also"></a>另請參閱

[Configuration 元素（格式）](./configuration-element-format.md)

[設定之控制項的控制項元素（格式）](./control-element-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
