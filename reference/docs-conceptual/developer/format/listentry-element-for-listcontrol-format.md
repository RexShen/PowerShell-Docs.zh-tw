---
title: ListControl (格式的 ListEntry 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d98f0b5215eea7668f866d2733214ade79d748f1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785688"
---
# <a name="listentry-element-for-listcontrol-format"></a>ListControl 的 ListEntry 元素 (格式)

提供清單視圖的定義。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntries 專案 (格式) ListEntry 專案 (格式) 

## <a name="syntax"></a>語法

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ListEntry` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|選擇性項目。<br /><br /> 定義使用此清單視圖定義的 .NET 物件，或必須存在才能使用此定義的條件。|
|[ListItems 元素 (格式) ](./listitems-element-for-listentry-for-listcontrol-format.md)|必要元素。<br /><br /> 定義清單視圖會顯示其值的屬性和腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListEntries 元素 (格式) ](./listentries-element-for-listcontrol-format.md)|提供清單視圖的定義。|

## <a name="remarks"></a>備註

清單視圖是一種清單格式，可顯示每個物件的屬性值或腳本值。 如需清單視圖的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

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

[建立清單檢視](./creating-a-list-view.md)

[ListEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntries 元素 (格式) ](./listentries-element-for-listcontrol-format.md)

[ListItems 元素 (格式) ](./listitems-element-for-listentry-for-listcontrol-format.md)

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
