---
title: ListEntries ListControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065385"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListControl 的 ListEntries 元素 (格式)

提供清單檢視的定義。 清單檢視中必須指定一個或多個定義。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式）

## <a name="syntax"></a>語法

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`ListEntries`項目。 必須指定至少一個子系項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListEntry 項目 （格式）](./listentry-element-for-listcontrol-format.md)|提供清單檢視的定義。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[ListControl 項目 （格式）](./listcontrol-element-format.md)|定義檢視的清單格式。|

## <a name="remarks"></a>備註

如需清單檢視的詳細資訊，請參閱[清單檢視](./creating-a-list-view.md)。

## <a name="example"></a>範例

此範例示範定義的清單檢視的 XML 項目[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。

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

[ListControl 項目 （格式）](./listcontrol-element-format.md)

[ListEntry 項目 （格式）](./listentry-element-for-listcontrol-format.md)

[清單檢視](./creating-a-list-view.md)

[撰寫 Windows PowerShell 格式和類型的檔案](./writing-a-powershell-formatting-file.md)
