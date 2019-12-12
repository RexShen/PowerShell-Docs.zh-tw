---
title: View 的 Name 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362637"
---
# <a name="name-element-for-view-format"></a>檢視的名稱元素 (格式)

指定用來識別此視圖的名稱。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） Name 元素（格式）

## <a name="syntax"></a>語法

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `Name` 專案的父元素。 每個視圖只允許一個 `Name` 元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 元素（格式）](./view-element-format.md)|定義用來顯示一或多個 .NET 物件成員的視圖。|

## <a name="text-value"></a>文字值

為視圖指定唯一的易記名稱。 這個名稱可以包含對檢視類型的參考（例如，資料表視圖或清單視圖）、物件或物件集使用此視圖、哪個命令會傳回物件，或這些的組合。

## <a name="remarks"></a>備註

如需不同類型之視圖的詳細資訊，請參閱下列主題：[資料表視圖](./creating-a-table-view.md)、[清單視圖](./creating-a-list-view.md)、[寬視圖](./creating-a-wide-view.md)和[自訂視圖](./creating-custom-controls.md)。

## <a name="example"></a>範例

下列範例會顯示定義[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件之資料表視圖的 `View` 元素。 此視圖的名稱為 "service"。

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

[建立清單視圖](./creating-a-list-view.md)

[建立資料表視圖](./creating-a-table-view.md)

[建立寬型視圖](./creating-a-wide-view.md)

[建立自訂控制項](./creating-custom-controls.md)

[View 元素（格式）](./view-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
