---
title: ViewSelectedBy 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367967"
---
# <a name="viewselectedby-element-format"></a>ViewSelectedBy 元素 (格式)

定義視圖所顯示的 .NET 物件。 每個視圖都必須指定至少一個 .NET 物件。

ViewDefinitions 元素（格式） View 元素（Format） ViewSelectedBy 元素（格式）

## <a name="syntax"></a>語法

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述 `ViewSelectedBy` 專案的屬性、子專案和父項目。 此元素必須包含至少一個 `TypeName` 或 `SelectionSetName` 子項目。 可以指定的子項目數目沒有限制，也沒有排序次序。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ViewSelectedBy 的 TypeName 元素（格式）](./typename-element-for-viewselectedby-format.md)|選擇性項目。<br /><br /> 指定由視圖顯示的 .NET 物件。|
|[ViewSelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-viewselectedby-format.md)|選擇性項目。<br /><br /> 指定由視圖顯示的一組 .NET 物件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 元素（格式）](./view-element-format.md)|定義顯示一或多個 .NET 物件的視圖。|

## <a name="remarks"></a>備註

如需如何在不同的視圖中使用此元素的詳細資訊，請參閱[資料表視圖元件](./creating-a-table-view.md)、[清單視圖元件](./creating-a-list-view.md)、[寬視圖元件](./creating-a-wide-view.md)和[自訂控制群組件](./creating-custom-controls.md)。

當格式設定檔案定義多個視圖所顯示的一組物件時，會使用 `SelectionSetName` 元素。 如需如何定義和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。

## <a name="example"></a>範例

下列範例示範如何指定清單視圖的[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。 資料表、寬型和自訂視圖會使用相同的架構。

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

[建立清單視圖](./creating-a-list-view.md)

[建立資料表視圖](./creating-a-table-view.md)

[建立寬型視圖](./creating-a-wide-view.md)

[建立自訂控制項](./creating-custom-controls.md)

[定義選取範圍集合](./defining-selection-sets.md)

[ViewSelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName 元素（格式）](./typename-element-for-viewselectedby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
