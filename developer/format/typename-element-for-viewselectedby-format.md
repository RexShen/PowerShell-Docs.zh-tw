---
title: TypeName ViewSelectedBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857894"
---
# <a name="typename-element-for-viewselectedby-format"></a>ViewSelectedBy 的 TypeName 元素 (格式)

指定檢視所顯示的.NET 物件。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ViewSelectedBy 項目 （格式） 類型名稱項目 ViewSelectedBy （格式）

## <a name="syntax"></a>語法

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目，以及的父項目`TypeName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ViewSelectedBy 項目 （格式）](./viewselectedby-element-format.md)|定義檢視所顯示的.NET 物件。|

## <a name="text-value"></a>文字值

指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>備註

如需如何在不同的檢視會使用這個元素的詳細資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)，[建立清單檢視](./creating-a-list-view.md)，[建立寬型檢視](./creating-a-wide-view.md)，和[自訂的檢視元件](./creating-custom-controls.md)。

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

[ViewSelectedBy 項目 （格式）](./viewselectedby-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
