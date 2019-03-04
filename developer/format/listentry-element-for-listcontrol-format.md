---
title: ListEntry ListControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862244"
---
# <a name="listentry-element-for-listcontrol-format"></a>ListControl 的 ListEntry 元素 (格式)

提供清單檢視的定義。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目 （格式）

## <a name="syntax"></a>語法

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`ListEntry`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EntrySelectedBy ListEntry （格式） 的項目](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|選擇性的項目。<br /><br /> 定義使用此清單檢視定義或必須存在於要使用此定義條件的.NET 物件。|
|[ListItems 項目 （格式）](./listitems-element-for-listentry-for-listcontrol-format.md)|必要項目。<br /><br /> 定義屬性和其值會顯示 [清單] 檢視的指令碼。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListEntries 項目 （格式）](./listentries-element-for-listcontrol-format.md)|提供清單檢視的定義。|

## <a name="remarks"></a>備註

清單檢視會顯示屬性值或每個物件的指令碼值以清單格式。 如需清單檢視的詳細資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。

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

[建立清單檢視](./creating-a-list-view.md)

[EntrySelectedBy ListEntry （格式） 的項目](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntries 項目 （格式）](./listentries-element-for-listcontrol-format.md)

[ListItems 項目 （格式）](./listitems-element-for-listentry-for-listcontrol-format.md)

[撰寫 Windows PowerShell 格式和類型的檔案](./writing-a-powershell-formatting-file.md)
