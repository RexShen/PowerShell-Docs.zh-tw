---
title: ListControl 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857454"
---
# <a name="listcontrol-element-format"></a>ListControl 元素 (格式)

定義檢視的清單格式。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式）

## <a name="syntax"></a>語法

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`ListControl`項目。 此元素必須包含單一子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListEntries 項目 （格式）](./listentries-element-for-listcontrol-format.md)|必要項目。<br /><br /> 提供清單檢視的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[檢視項目 （格式）](./view-element-format.md)|定義的檢視，用來顯示一或多個物件的成員。|

## <a name="remarks"></a>備註

如需建立清單檢視的詳細資訊，請參閱 <<c0> [ 建立清單檢視](./creating-a-list-view.md)。

## <a name="example"></a>範例

此範例中顯示的清單檢視[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。

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

[檢視項目 （格式）](./view-element-format.md)

[ListEntries 項目 （格式）](./listentries-element-for-listcontrol-format.md)

[建立清單檢視](./creating-a-list-view.md)

[撰寫 Windows PowerShell 格式和類型的檔案](./writing-a-powershell-formatting-file.md)
