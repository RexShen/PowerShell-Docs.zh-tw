---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 的 ListEntry 元素 (格式)
description: ListControl 的 ListEntry 元素 (格式)
ms.openlocfilehash: 96ae5fcdd837d2491d6c7ff6a375fef1d83ae3e9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666564"
---
# <a name="listentry-element-for-listcontrol-format"></a>ListControl 的 ListEntry 元素 (格式)

提供清單視圖的定義。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `ListEntry` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|選擇性項目。<br /><br /> 定義使用此清單視圖定義或必須存在才能使用此定義之條件的 .NET 物件。|
|[ListItems 元素 (格式) ](./listitems-element-for-listentry-for-listcontrol-format.md)|必要元素。<br /><br /> 定義清單視圖顯示其值的屬性和腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListEntries 元素 (格式) ](./listentries-element-for-listcontrol-format.md)|提供清單視圖的定義。|

## <a name="remarks"></a>備註

清單視圖是一種清單格式，可顯示每個物件的屬性值或腳本值。 如需清單視圖的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。

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

[建立清單檢視](./creating-a-list-view.md)

[ListEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntries 元素 (格式) ](./listentries-element-for-listcontrol-format.md)

[ListItems 元素 (格式) ](./listitems-element-for-listentry-for-listcontrol-format.md)

[寫入 Windows PowerShell 格式和類型檔案](./writing-a-powershell-formatting-file.md)
