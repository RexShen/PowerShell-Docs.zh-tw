---
title: SelectionSetName ViewSelectedBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076220"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>ViewSelectedBy 的 SelectionSetName 元素 (格式)

指定一份檢視所顯示的.NET 物件。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ViewSelectedBy 項目 （格式） SelectionSetName 項目 ViewSelectedBy （格式）

## <a name="syntax"></a>語法

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[ViewSelectedBy 項目 （格式）](./viewselectedby-element-format.md)|定義檢視所顯示的.NET 物件。|

## <a name="text-value"></a>文字值

指定選取項目集所定義的名稱`Name`選取項目集的項目。

## <a name="remarks"></a>備註

當您有一組您想要使用單一的名稱，例如一組透過繼承相關聯的物件參考的相關物件時，您可以使用選取項目集。 如需有關定義和參考選取項目集的詳細資訊，請參閱[定義設定的物件](./defining-selection-sets.md)。

## <a name="example"></a>範例

下列範例示範如何指定設定的清單檢視的選取範圍。 相同的結構描述用於資料表，，和自訂檢視。

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>另請參閱

[定義選取範圍](./defining-selection-sets.md)

[ViewSelectedBy 項目 （格式）](./viewselectedby-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
