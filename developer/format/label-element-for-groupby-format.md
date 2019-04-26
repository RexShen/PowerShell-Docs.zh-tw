---
title: GroupBy （格式） 供標籤項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065405"
---
# <a name="label-element-for-groupby-format"></a>GroupBy 的標籤元素 (格式)

指定在發現新的群組時，會顯示的標籤。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） 的 GroupBy （格式） 的標籤項目

## <a name="syntax"></a>語法

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`Label`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)|定義新的一整組物件的顯示方式。|

## <a name="text-value"></a>文字值

指定 Windows PowerShell 會遇到新的屬性或指令碼的值時，即顯示的文字。

## <a name="remarks"></a>備註

除了這個項目所指定的文字，Windows PowerShell 會顯示新的值開始群組，並新增一個空白行之前, 和之後的群組。

## <a name="example"></a>範例

下列範例示範新的群組的標籤。 顯示的標籤會看起來像這樣： `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

如需完整的格式化檔案，其中包含這個元素的範例，請參閱 <<c0> [ 寬型檢視 (GroupBy)](./wide-view-groupby.md)。

## <a name="see-also"></a>另請參閱

[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
