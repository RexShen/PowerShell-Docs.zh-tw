---
ms.date: 09/13/2016
ms.topic: reference
title: ViewSelectedBy 的 SelectionSetName 元素 (格式)
description: ViewSelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: a1a1816761715a138bcb3c2bd4cb9dbbb2f9cb92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654909"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>ViewSelectedBy 的 SelectionSetName 元素 (格式)

指定由視圖顯示的一組 .NET 物件。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ViewSelectedBy 元素 (格式) ViewSelectedBy (格式的 SelectionSetName 元素) 

## <a name="syntax"></a>語法

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `SelectionSetName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ViewSelectedBy 元素 (格式)](./viewselectedby-element-format.md)|定義由視圖顯示的 .NET 物件。|

## <a name="text-value"></a>文字值

指定選項群組的名稱，此選項群組是由 `Name` 選取專案集合的元素所定義。

## <a name="remarks"></a>備註

當您有一組要使用單一名稱來參考的相關物件時，例如一組透過繼承相關的物件，您可以使用選取集。 如需定義和參考選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。

## <a name="example"></a>範例

下列範例示範如何指定清單視圖的選取集合。 資料表、寬和自訂視圖都使用相同的架構。

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

[定義選取範圍集合](./defining-selection-sets.md)

[ViewSelectedBy 元素 (格式)](./viewselectedby-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
