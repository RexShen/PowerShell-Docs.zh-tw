---
title: " (格式) 設定控制項控制項的 CustomControl 元素 |Microsoft Docs"
ms.date: 09/13/2016
ms.openlocfilehash: 5aacf824421dfce19f1f495fc0a95e766cdbaf8b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786079"
---
# <a name="customcontrol-element-for-control-for-controls-for-configuration-format"></a>設定之控制項的控制項 CustomControl 元素 (格式)

定義控制項。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) CustomControl 元素用於設定 (格式的控制項) 

## <a name="syntax"></a>語法

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `CustomControl` 。 此元素必須至少有一個子專案。 可以指定的子項目數目沒有上限。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomControl 的 CustomEntries 元素，用於設定 (格式) ](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|必要元素。<br /><br /> 提供控制項的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定之控制項的控制項元素 (格式)](./control-element-for-controls-for-configuration-format.md)|定義可供格式檔案的所有視圖使用的通用控制項，以及用來參考控制項的名稱。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[設定之控制項的控制項元素 (格式)](./control-element-for-controls-for-configuration-format.md)

[CustomControl 的 CustomEntries 元素，用於設定 (格式) ](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
