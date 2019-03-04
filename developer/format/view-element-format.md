---
title: 檢視項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856144"
---
# <a name="view-element-format"></a>檢視元素 (格式)

定義顯示一或多個.NET 物件的檢視。 可以格式化檔案中定義的檢視表的數目沒有限制。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式）

## <a name="syntax"></a>語法

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`View`項目。 您必須指定其中一個控制項子項目，而且您必須指定名稱的檢視和使用檢視的物件。 定義自訂控制項，如何分組的物件，並指定檢視是否超出訊號範圍是選擇性的。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[檢視 （格式） 的 controls 項目](./controls-element-for-view-format.md)|選擇性的項目。<br /><br /> 定義一組可依據其名稱，從檢視中參考的控制項。|
|[CustomControl 項目 （格式）](./customcontrol-element-for-groupby-format.md)|選擇性的項目。<br /><br /> 定義檢視的自訂控制項格式。|
|[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)|選擇性的項目。<br /><br /> 定義.NET 物件的成員分組的方式。|
|[ListControl 項目 （格式）](./listcontrol-element-format.md)|選擇性的項目。<br /><br /> 定義檢視的清單格式。|
|[檢視 （格式） 的 name 元素](./name-element-for-view-format.md)|必要項目。<br /><br /> 指定用來參考檢視的名稱。|
|[TableControl 項目 （格式）](./tablecontrol-element-format.md)|選擇性的項目。<br /><br /> 定義檢視以資料表格式。|
|[ViewSelectedBy 檢視 （格式） 的項目](./viewselectedby-element-format.md)|必要項目。<br /><br /> 定義此檢視會顯示的.NET 物件。|
|[WideControl 項目 （格式）](./widecontrol-element-format.md)|選擇性的項目。<br /><br /> 寬 （單一值） 會定義檢視的清單格式。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ViewDefinitions 項目 （格式）](./viewdefinitions-element-format.md)|定義用來顯示物件的檢視。|

## <a name="remarks"></a>備註

如需詳細的不同檢視和自訂控制項之元件的相關資訊，請參閱下列主題：

- [資料表檢視元件](./creating-a-table-view.md)

- [清單檢視元件](./creating-a-list-view.md)

- [寬型檢視元件](./creating-a-wide-view.md)

- [自訂控制項](./creating-custom-controls.md)

## <a name="example"></a>範例

此範例示範`View`定義的資料表檢視項目[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>另請參閱

[ViewDefinitions 項目 （格式）](./viewdefinitions-element-format.md)

[檢視 （格式） 的 name 元素](./name-element-for-view-format.md)

[ViewSelectedBy 項目 （格式）](./viewselectedby-element-format.md)

[檢視 （格式） 的 controls 項目](./controls-element-for-view-format.md)

[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[TableControl 項目 （格式）](./tablecontrol-element-format.md)

[ListControl 項目 （格式）](./listcontrol-element-format.md)

[WideControl 項目 （格式）](./widecontrol-element-format.md)

[CustomControl 項目 （格式）](./customcontrol-element-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
