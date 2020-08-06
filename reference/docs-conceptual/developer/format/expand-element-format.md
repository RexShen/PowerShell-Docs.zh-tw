---
title: 展開元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: deee832254bb8a774ee2c1f5bd451d3ced1bd47a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783648"
---
# <a name="expand-element-format"></a>展開元素 (格式)

指定如何展開這個定義的集合物件。

Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 專案 (格式) Expand 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `Expand` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 元素 (格式)](./enumerableexpansion-element-format.md)|定義特定 .NET 集合物件在視圖中顯示時的擴充方式。|

## <a name="text-value"></a>文字值

指定下列其中一個值：

- EnumOnly：只顯示集合中物件的屬性。

- CoreOnly：只顯示集合物件的屬性。

- Both：顯示集合中物件的屬性，以及集合物件的屬性。

## <a name="remarks"></a>備註

這個元素是用來定義集合物件和集合中物件的顯示方式。 在此情況下，集合物件會參考支援**system.object**介面的任何物件。

預設行為是只顯示集合中物件的屬性。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
