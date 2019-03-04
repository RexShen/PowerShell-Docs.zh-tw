---
title: WideControl 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859824"
---
# <a name="widecontrol-element-format"></a>WideControl 元素 (格式)

寬 （單一值） 會定義檢視的清單格式。 此檢視會顯示單一屬性值或每個物件的指令碼值。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式）

## <a name="syntax"></a>語法

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`WideControl`項目。 您無法指定`AutoSize`和`ColumnNumber`在同一時間的項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[AutoSize WideControl （格式） 的項目](./autosize-element-for-widecontrol-format.md)|選擇性的項目。<br /><br /> 指定是否資料行大小和資料行數目根據調整大小的資料大小。|
|[ColumnNumber WideControl （格式） 的項目](./columnnumber-element-for-widecontrol-format.md)|選擇性的項目。<br /><br /> 指定在寬型檢視中顯示的資料行數目。|
|[WideEntries 項目 （格式）](./wideentries-element-for-widecontrol-format.md)|必要項目。<br /><br /> 提供的寬型檢視的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[檢視項目 （格式）](./view-element-format.md)|定義用來顯示一或多個.NET 物件的檢視。|

## <a name="remarks"></a>備註

當定義的寬型檢視，您可以加入`AutoSize`項目或`ColumnNumber`但您無法新增。

在大部分情況下，只有一個定義需要針對每個寬型檢視，但可以有多個定義，如果您想要使用相同的檢視來顯示不同的.NET 物件。 在這些情況下，您可以針對每個物件或一組物件提供不同的定義。

如需詳細的寬型檢視元件的相關資訊，請參閱[寬型檢視元件](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例所示`WideControl`用來顯示屬性的項目[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

寬型檢視的完整範例，請參閱[（基本） 的寬型檢視](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[Autosize WideControl （格式） 的項目](./autosize-element-for-widecontrol-format.md)

[ColumnNumber WideControl （格式） 的項目](./columnnumber-element-for-widecontrol-format.md)

[檢視項目 （格式）](./view-element-format.md)

[WideEntries 項目 （格式）](./wideentries-element-for-widecontrol-format.md)

[寬型檢視 （基本）](./wide-view-basic.md)

[建立寬型檢視](./creating-a-wide-view.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
