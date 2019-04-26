---
title: ListControl （格式） 的 ListEntry ListItems 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065235"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListControl 之 ListEntry 的 ListItems 元素 (格式)

定義屬性和其值會顯示在清單檢視的資料列中的指令碼。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 ListControl （格式） 的 ListControl （格式） ListItems 元素的清單控制項 （格式） ListEntry 項目

## <a name="syntax"></a>語法

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`ListItems`項目。 沒有任何限制，您可以指定的子項目數目。 子元素的順序定義的值會顯示在清單檢視中的順序。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl （格式） 的 ListItem 項目](./listitem-element-for-listitems-for-listcontrol-format.md)|必要項目。<br /><br /> 定義屬性或其值會顯示 [清單] 檢視的指令碼。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[ListEntry ListControl （格式） 的項目](./listentry-element-for-listcontrol-format.md)|提供清單檢視的定義。|

## <a name="remarks"></a>備註

如需這種檢視類型的詳細資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。

## <a name="example"></a>範例

這個範例示範定義清單檢視的三個資料列的 XML 項目。

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>另請參閱

[ListEntry ListControl （格式） 的項目](./listentry-element-for-listcontrol-format.md)

[ListControl （格式） 的 ListItem 項目](./listitem-element-for-listitems-for-listcontrol-format.md)

[建立清單檢視](./creating-a-list-view.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
