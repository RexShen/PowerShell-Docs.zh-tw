---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 的 ListEntries 元素 (格式)
description: ListControl 的 ListEntries 元素 (格式)
ms.openlocfilehash: d4d6625bb92ea27863fc30d5bf5625f9275e4f69
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666598"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListControl 的 ListEntries 元素 (格式)

提供清單視圖的定義。 清單視圖必須指定一或多個定義。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListEntries 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `ListEntries` 。 至少必須指定一個子項目。

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

如需清單視圖的詳細資訊，請參閱 [清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

這個範例會顯示定義 [System.serviceprocess.dll Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 物件清單視圖的 XML 元素。

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

[寫入 Windows PowerShell 格式和類型檔案](./writing-a-powershell-formatting-file.md)
