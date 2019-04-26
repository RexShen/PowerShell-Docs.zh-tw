---
title: CustomControlName GroupBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066530"
---
# <a name="customcontrolname-element-for-groupby-format"></a>GroupBy 的 CustomControlName 元素 (格式)

指定用來顯示新的群組的自訂控制項的名稱。 定義資料表、 清單、 寬或自訂的控制項檢視時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） 的 GroupBy （格式） 的 CustomControlName 項目

## <a name="syntax"></a>語法

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`CustomControlName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)|定義 Windows PowerShell 顯示新的一整組物件的方式。|

## <a name="text-value"></a>文字值

指定自訂控制項是用來顯示新的群組名稱。

## <a name="remarks"></a>備註

您可以建立可供所有的格式化檔案，檢視的通用控制項，而且您可以建立可供特定檢視的檢視控制項。 下列項目會指定這些自訂控制項的名稱：

- [組態 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-configuration-format.md)

- [用於檢視 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[組態 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-configuration-format.md)

[用於檢視 （格式） 的控制項的控制項的 name 元素](./name-element-for-control-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
