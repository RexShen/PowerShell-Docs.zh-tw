---
title: ViewSelectedBy 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863184"
---
# <a name="viewselectedby-element-format"></a>ViewSelectedBy 元素 (格式)

定義檢視所顯示的.NET 物件。 每個檢視都必須指定至少一個.NET 物件。

ViewDefinitions 項目 （格式） 檢視項目 （格式） ViewSelectedBy 項目 （格式）

## <a name="syntax"></a>語法

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`ViewSelectedBy`項目。 這個項目必須包含至少一個`TypeName`或`SelectionSetName`子項目。 您可以指定的子元素的數目沒有限制也不是重要的順序。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TypeName ViewSelectedBy （格式） 的項目](./typename-element-for-viewselectedby-format.md)|選擇性的項目。<br /><br /> 指定檢視所顯示的.NET 物件。|
|[SelectionSetName ViewSelectedBy （格式） 的項目](./selectionsetname-element-for-viewselectedby-format.md)|選擇性的項目。<br /><br /> 指定一份檢視所顯示的.NET 物件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[檢視項目 （格式）](./view-element-format.md)|定義顯示一或多個.NET 物件的檢視。|

## <a name="remarks"></a>備註

如需如何在不同的檢視會使用這個元素的詳細資訊，請參閱[資料表的檢視元件](./creating-a-table-view.md)，[清單檢視元件](./creating-a-list-view.md)，[寬型檢視元件](./creating-a-wide-view.md)，以及[自訂控制項元件](./creating-custom-controls.md)。

`SelectionSetName`時的格式化檔案會定義一組的多個檢視所顯示的物件，會使用項目。 如需有關如何選取項目集所定義，且參考的詳細資訊，請參閱 <<c0> [ 定義設定的物件](./defining-selection-sets.md)。

## <a name="example"></a>範例

下列範例示範如何指定[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)針對清單檢視的物件。 相同的結構描述用於資料表，，和自訂檢視。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[建立資料表檢視](./creating-a-table-view.md)

[建立寬型檢視](./creating-a-wide-view.md)

[建立自訂控制項](./creating-custom-controls.md)

[定義選取範圍](./defining-selection-sets.md)

[SelectionSetName ViewSelectedBy （格式） 的項目](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName 項目 （格式）](./typename-element-for-viewselectedby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
