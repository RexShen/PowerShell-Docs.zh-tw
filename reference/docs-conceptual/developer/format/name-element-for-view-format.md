---
title: View (格式的 Name 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 670b089f850fa4b39b7b100ca1e1ce45b05ea72d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773227"
---
# <a name="name-element-for-view-format"></a>檢視的名稱元素 (格式)

指定用來識別此視圖的名稱。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) Name 元素 (格式) 

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

為視圖指定唯一的易記名稱。 這個名稱可以包含檢視類型的參考 (例如資料表視圖或清單視圖) 、物件或物件集使用此視圖、哪個命令會傳回物件，或其組合。

## <a name="remarks"></a>備註

如需不同類型之視圖的詳細資訊，請參閱下列主題：[資料表視圖](./creating-a-table-view.md)、[清單視圖](./creating-a-list-view.md)、[寬視圖](./creating-a-wide-view.md)和[自訂視圖](./creating-custom-controls.md)。

## <a name="example"></a>範例

下列範例顯示的 `View` 元素會定義[System.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件的資料表視圖。 此視圖的名稱為 "service"。

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
