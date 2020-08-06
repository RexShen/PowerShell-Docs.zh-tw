---
title: GroupBy (格式的 ScriptBlock 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e761e02a7910cd598449d564e827889162da9f25
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787677"
---
# <a name="scriptblock-element-for-groupby-format"></a>GroupBy 的 ScriptBlock 元素 (格式)

指定每當新群組的值變更時，就會啟動的腳本。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素用於 GroupBy (格式) ScriptBlock 元素 (

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)|定義一組 .NET 物件的顯示方式。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

每當此腳本的值變更時，PowerShell 就會啟動新的群組。

當指定此元素時，您無法指定[PropertyName](propertyname-element-for-groupby-format.md)元素來啟動新的群組。

## <a name="see-also"></a>另請參閱

[GroupBy 的 PropertyName 元素 (格式)](propertyname-element-for-groupby-format.md)

[檢視的 GroupBy 元素 (格式)](groupby-element-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](writing-a-powershell-formatting-file.md)
