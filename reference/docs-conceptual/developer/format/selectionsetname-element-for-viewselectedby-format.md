---
title: ViewSelectedBy (格式的 SelectionSetName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f6410b463bcb00d2758849c2f7e13cd839277e50
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772598"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>ViewSelectedBy 的 SelectionSetName 元素 (格式)

指定由視圖顯示的一組 .NET 物件。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ViewSelectedBy 元素 (格式) ViewSelectedBy (格式的 SelectionSetName 元素) 

## <a name="syntax"></a>語法

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ViewSelectedBy 元素 (格式)](./viewselectedby-element-format.md)|定義視圖所顯示的 .NET 物件。|

## <a name="text-value"></a>文字值

針對選取集指定專案所定義的選取範圍名稱 `Name` 。

## <a name="remarks"></a>備註

當您有一組想要使用單一名稱來參考的相關物件（例如透過繼承相關的一組物件）時，您可以使用 [選擇集]。 如需定義和參考選取集的詳細資訊，請參閱[定義物件的集合](./defining-selection-sets.md)。

## <a name="example"></a>範例

下列範例顯示如何指定清單視圖的選擇集。 資料表、寬型和自訂視圖會使用相同的架構。

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
