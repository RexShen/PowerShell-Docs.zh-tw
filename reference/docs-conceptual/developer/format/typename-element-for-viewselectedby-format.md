---
title: ViewSelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361437"
---
# <a name="typename-element-for-viewselectedby-format"></a>ViewSelectedBy 的 TypeName 元素 (格式)

指定由視圖顯示的 .NET 物件。

ViewSelectedBy 的 Configuration 元素（格式） ViewDefinitions 元素（格式） ViewSelectedBy 元素（格式） TypeName 元素（格式）

## <a name="syntax"></a>語法

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `TypeName` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ViewSelectedBy 元素（格式）](./viewselectedby-element-format.md)|定義視圖所顯示的 .NET 物件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。

## <a name="remarks"></a>備註

如需如何在不同的視圖中使用此元素的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)、[建立清單視圖](./creating-a-list-view.md)、[建立寬視圖](./creating-a-wide-view.md)和[自訂視圖元件](./creating-custom-controls.md)。

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

[ViewSelectedBy 元素（格式）](./viewselectedby-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
