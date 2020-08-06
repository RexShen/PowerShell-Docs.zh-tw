---
title: EnumerableExpansion 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 81a8959c19502a2e56f4cfa48a1e480509d84b6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774043"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion 元素 (格式)

定義特定 .NET 集合物件在視圖中顯示時的擴充方式。

Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `EnumerableExpansion` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-enumerableexpansion-format.md)|選擇性項目。<br /><br /> 定義由這個定義擴充的 .NET 集合物件。|
|[展開元素 (格式)](./expand-element-format.md)|指定如何展開這個定義的集合物件。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansions 元素 (格式)](./enumerableexpansions-element-format.md)|定義當 .NET 集合物件顯示在視圖中時，所展開的不同方式。|

## <a name="remarks"></a>備註

這個元素是用來定義集合物件和集合中物件的顯示方式。 在此情況下，集合物件會參考支援**system.object**介面的任何物件。

預設行為是只顯示集合中物件的屬性。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
