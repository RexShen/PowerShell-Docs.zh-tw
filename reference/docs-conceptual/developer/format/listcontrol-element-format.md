---
title: ListControl 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0173b9797bffcca74f1a32903686f771366ebb1b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785722"
---
# <a name="listcontrol-element-format"></a>ListControl 元素 (格式)

定義視圖的清單格式。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ListControl` 。 此元素必須只包含單一子專案。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListEntries 元素 (格式) ](./listentries-element-for-listcontrol-format.md)|必要元素。<br /><br /> 提供清單視圖的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視元素 (格式)](./view-element-format.md)|定義用來顯示一或多個物件成員的視圖。|

## <a name="remarks"></a>備註

如需建立清單視圖的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

這個範例會顯示[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件的清單視圖。

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>另請參閱

[檢視元素 (格式)](./view-element-format.md)

[ListEntries 元素 (格式) ](./listentries-element-for-listcontrol-format.md)

[建立清單檢視](./creating-a-list-view.md)

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
