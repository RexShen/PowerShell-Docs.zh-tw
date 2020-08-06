---
title: ListControl (格式的 ListEntries 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0fe07e739c2d2fec153599ec6c0c0b3ecc14df18
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785705"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListControl 的 ListEntries 元素 (格式)

提供清單視圖的定義。 清單視圖必須指定一或多個定義。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntries 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ListEntries` 。 至少必須指定一個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListEntry 元素 (格式) ](./listentry-element-for-listcontrol-format.md)|提供清單視圖的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListControl 元素 (格式)](./listcontrol-element-format.md)|定義視圖的清單格式。|

## <a name="remarks"></a>備註

如需清單視圖的詳細資訊，請參閱[清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

這個範例會顯示定義[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件之清單視圖的 XML 元素。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>另請參閱

[ListControl 元素 (格式)](./listcontrol-element-format.md)

[ListEntry 元素 (格式) ](./listentry-element-for-listcontrol-format.md)

[清單視圖](./creating-a-list-view.md)

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
