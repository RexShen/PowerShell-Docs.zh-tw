---
title: CustomEntries CustomControl 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066595"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>設定之控制項的 CustomControl 的 CustomEntries 元素 (格式)

提供通用控制項的定義。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目格式）

## <a name="syntax"></a>語法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`CustomEntries`項目。 您必須指定一個以上的子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomEntry CustomControl 組態 （格式） 的控制項的項目](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供通用控制項的定義。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CustomControl 組態 （格式） 的控制項的項目](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|定義通用的控制項。|

## <a name="remarks"></a>備註

在大部分情況下，控制項有只有一個定義，其定義於單一`CustomEntry`項目。 不過，它是可以有多個定義，如果您想要使用相同的控制項來顯示不同的.NET 物件。 在這些情況下，您可以定義`CustomEntry`每個物件或一組物件的項目。

## <a name="see-also"></a>另請參閱

[CustomControl 組態 （格式） 的控制項的項目](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[CustomEntry CustomControl 組態 （格式） 的控制項的項目](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
