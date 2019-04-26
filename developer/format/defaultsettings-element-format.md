---
title: DefaultSettings 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066340"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings 元素 (格式)

定義套用至的格式化檔案的所有檢視的常見設定。 一般設定包括顯示錯誤，定義集合展開的資料表中的文字換行。

組態項目 （格式） DefaultSettings 項目 （格式）

## <a name="syntax"></a>語法

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`DefaultSettings`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[DisplayError 項目 （格式）](./displayerror-element-format.md)|選擇性的項目。<br /><br /> 指定顯示一段資料時，發生錯誤時，會顯示 #ERR 的字串。|
|[EnumerableExpansions 項目 （格式）](./enumerableexpansions-element-format.md)|選擇性的項目。<br /><br /> 定義.NET 物件會展開檢視中顯示時的不同方式。|
|[PropertyCountForTable （格式）](./propertycountfortable-element-format.md)|選擇性的項目。<br /><br /> 指定物件必須具有在資料表檢視中顯示物件的屬性的數目下限。|
|[ShowError 項目 （格式）](./showerror-element-format.md)|選擇性的項目。<br /><br /> 指定顯示一段資料時，發生錯誤時，會顯示完整的錯誤記錄。|
|[WrapTables 項目 （格式）](./wraptables-element-format.md)|選擇性的項目。<br /><br /> 指定資料表中的資料會移至下一行，是否無法納入資料行的寬度。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[組態項目](./configuration-element-format.md)|表示格式化檔案的最上層項目。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[組態項目](./configuration-element-format.md)

[DisplayError 項目 （格式）](./displayerror-element-format.md)

[EnumerableExpansions 項目 （格式）](./enumerableexpansions-element-format.md)

[PropertyCountForTable （格式）](./propertycountfortable-element-format.md)

[ShowError 項目 （格式）](./showerror-element-format.md)

[WrapTables 項目 （格式）](./wraptables-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
