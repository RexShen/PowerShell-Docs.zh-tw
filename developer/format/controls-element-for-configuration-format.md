---
title: 組態 （格式） 的 controls 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066867"
---
# <a name="controls-element-for-configuration-format"></a>設定的控制項元素 (格式)

定義可由格式檔案的所有檢視通用控制項。

組態 （格式） 的組態項目 （格式） 的控制項項目

## <a name="syntax"></a>語法

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`Controls`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[組態 （格式） 的控制項的控制項項目](./control-element-for-controls-for-configuration-format.md)|必要項目。<br /><br /> 定義可由格式檔案的所有檢視通用控制項。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[組態項目 （格式）](./configuration-element-format.md)|表示格式化檔案的最上層項目。|

## <a name="remarks"></a>備註

您可以建立任意數目的通用控制項。 針對每個控制項中，您必須指定用來參考控制項和控制項的元件名稱。

## <a name="see-also"></a>另請參閱

[組態項目 （格式）](./configuration-element-format.md)

[組態 （格式） 的控制項的控制項項目](./control-element-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
