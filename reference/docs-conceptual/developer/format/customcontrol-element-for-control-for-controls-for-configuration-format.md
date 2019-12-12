---
title: 設定之控制項的控制項的 CustomControl 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9d92a9e-c680-46ca-962e-e82452726953
caps.latest.revision: 10
ms.openlocfilehash: 1d72ce5b18e89bd81c7f81b27f4b8c60bed99764
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368967"
---
# <a name="customcontrol-element-for-control-for-controls-for-configuration-format"></a>設定之控制項的控制項 CustomControl 元素 (格式)

定義控制項。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

設定專案（格式）控制項的設定（格式）控制項元素的元素，用於設定的控制項設定（格式） CustomControl 元素（格式）

## <a name="syntax"></a>語法

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `CustomControl` 專案的父元素。 此元素必須至少有一個子專案。 可以指定的子項目數目沒有上限。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|必要項目。<br /><br /> 提供控制項的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的控制項元素（格式）](./control-element-for-controls-for-configuration-format.md)|定義可供格式檔案的所有視圖使用的通用控制項，以及用來參考控制項的名稱。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[設定之控制項的控制項元素（格式）](./control-element-for-controls-for-configuration-format.md)

[設定之 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
