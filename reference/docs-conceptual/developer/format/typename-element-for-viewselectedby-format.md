---
ms.date: 09/13/2016
ms.topic: reference
title: ViewSelectedBy 的 TypeName 元素 (格式)
description: ViewSelectedBy 的 TypeName 元素 (格式)
ms.openlocfilehash: 62edc2fe4b4c1c5f1b17dd2f8b0943f28ff5dfb7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667720"
---
# <a name="typename-element-for-viewselectedby-format"></a>ViewSelectedBy 的 TypeName 元素 (格式)

指定由視圖顯示的 .NET 物件。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) ViewSelectedBy 元素 (format) ViewSelectedBy (格式的 TypeName 元素) 

## <a name="syntax"></a>語法

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `TypeName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ViewSelectedBy 元素 (格式)](./viewselectedby-element-format.md)|定義由視圖顯示的 .NET 物件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

如需如何在不同的視圖中使用這個元素的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)、 [建立清單視圖](./creating-a-list-view.md)、 [建立寬視圖](./creating-a-wide-view.md)，以及 [自訂視圖元件](./creating-custom-controls.md)。

## <a name="example"></a>範例

下列範例示範如何指定清單視圖的 [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 物件。 資料表、寬和自訂視圖都使用相同的架構。

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

[建立表格檢視](./creating-a-table-view.md)

[建立寬型檢視](./creating-a-wide-view.md)

[建立自訂控制項](./creating-custom-controls.md)

[ViewSelectedBy 元素 (格式)](./viewselectedby-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
