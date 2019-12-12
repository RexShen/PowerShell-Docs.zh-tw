---
title: ViewSelectedBy 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368257"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>ViewSelectedBy 的 SelectionSetName 元素 (格式)

指定由視圖顯示的一組 .NET 物件。

ViewSelectedBy （格式）的設定元素（格式） ViewDefinitions 元素（格式） ViewSelectedBy 元素（格式） SelectionSetName 元素

## <a name="syntax"></a>語法

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `SelectionSetName` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ViewSelectedBy 元素（格式）](./viewselectedby-element-format.md)|定義視圖所顯示的 .NET 物件。|

## <a name="text-value"></a>文字值

指定選取集的 [`Name`] 元素所定義的選取範圍名稱。

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

[ViewSelectedBy 元素（格式）](./viewselectedby-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
