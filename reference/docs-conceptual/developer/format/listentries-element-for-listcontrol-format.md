---
title: ListControl 的 ListEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362757"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListControl 的 ListEntries 元素 (格式)

提供清單視圖的定義。 清單視圖必須指定一或多個定義。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（格式） ListEntries 元素（格式）

## <a name="syntax"></a>語法

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `ListEntries` 專案的父元素。 至少必須指定一個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListEntry 元素（格式）](./listentry-element-for-listcontrol-format.md)|提供清單視圖的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListControl 元素（格式）](./listcontrol-element-format.md)|定義視圖的清單格式。|

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

[ListControl 元素（格式）](./listcontrol-element-format.md)

[ListEntry 元素（格式）](./listentry-element-for-listcontrol-format.md)

[清單檢視](./creating-a-list-view.md)

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
