---
title: WideControl 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367987"
---
# <a name="widecontrol-element-format"></a>WideControl 元素 (格式)

定義視圖的寬（單一值）清單格式。 此視圖會顯示每個物件的單一屬性值或腳本值。

Configuration 元素（格式） ViewDefinitions 元素（格式） WideControl 元素（格式）

## <a name="syntax"></a>語法

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明 `WideControl` 元素的屬性、子專案和父元素。 您不能同時指定 `AutoSize` 和 `ColumnNumber` 個元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideControl 的 AutoSize 元素（格式）](./autosize-element-for-widecontrol-format.md)|選擇性元素。<br /><br /> 指定是否根據資料大小來調整資料行大小和資料行數目。|
|[WideControl 的 ColumnNumber 元素（格式）](./columnnumber-element-for-widecontrol-format.md)|選擇性元素。<br /><br /> 指定在寬視圖中顯示的資料行數目。|
|[WideEntries 元素（格式）](./wideentries-element-for-widecontrol-format.md)|必要元素。<br /><br /> 提供寬視圖的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 元素（格式）](./view-element-format.md)|定義用來顯示一個或多個 .NET 物件的視圖。|

## <a name="remarks"></a>備註

定義寬視圖時，您可以新增 `AutoSize` 元素或 `ColumnNumber`，但無法同時新增這兩個專案。

在大部分情況下，每個寬視圖只需要一個定義，但是如果您想要使用相同的視圖來顯示不同的 .NET 物件，則可能會有多個定義。 在這些情況下，您可以為每個物件或一組物件提供個別的定義。

如需有關寬視圖元件的詳細資訊，請參閱[寬視圖元件](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例示範用來顯示[system.servicemodel 物件之](/dotnet/api/System.Diagnostics.Process)屬性的 `WideControl` 元素。

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

如需寬視圖的完整範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[WideControl 的 Autosize 元素（格式）](./autosize-element-for-widecontrol-format.md)

[WideControl 的 ColumnNumber 元素（格式）](./columnnumber-element-for-widecontrol-format.md)

[View 元素（格式）](./view-element-format.md)

[WideEntries 元素（格式）](./wideentries-element-for-widecontrol-format.md)

[寬視圖（基本）](./wide-view-basic.md)

[建立寬型視圖](./creating-a-wide-view.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
