---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視的名稱元素 (格式)
description: 檢視的名稱元素 (格式)
ms.openlocfilehash: 5781bcdf7a0e1eb5e9c7e97bb6acc0a383dc0262
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666447"
---
# <a name="name-element-for-view-format"></a>檢視的名稱元素 (格式)

指定用來識別視圖的名稱。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 名稱元素 (格式) 

## <a name="syntax"></a>語法

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `Name` 。 `Name`每個視圖只允許一個元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視元素 (格式)](./view-element-format.md)|定義用來顯示一或多個 .NET 物件成員的視圖。|

## <a name="text-value"></a>文字值

為視圖指定唯一的易記名稱。 這個名稱可以包含檢視類型的參考 (例如，資料表視圖或清單視圖) 、使用 view 的物件或物件集、哪個命令傳回物件或這些的組合。

## <a name="remarks"></a>備註

如需不同類型之視圖的詳細資訊，請參閱下列主題： [資料表視圖](./creating-a-table-view.md)、 [清單視圖](./creating-a-list-view.md)、 [寬視圖](./creating-a-wide-view.md)和 [自訂視圖](./creating-custom-controls.md)。

## <a name="example"></a>範例

下列範例 `View` 會顯示定義 [system.serviceprocess.dll Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 物件之資料表視圖的元素。 視圖的名稱為「服務」。

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[建立表格檢視](./creating-a-table-view.md)

[建立寬型檢視](./creating-a-wide-view.md)

[建立自訂控制項](./creating-custom-controls.md)

[檢視元素 (格式)](./view-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
