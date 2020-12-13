---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 元素 (格式)
description: WideControl 元素 (格式)
ms.openlocfilehash: f88e1ce18f87e5e47de473298b3ecf070b71c192
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651267"
---
# <a name="widecontrol-element-format"></a>WideControl 元素 (格式)

為視圖定義寬 (單一值) 清單格式。 這個視圖會顯示每個物件的單一屬性值或腳本值。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) WideControl 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `WideControl` 。 您無法同時指定 `AutoSize` 和 `ColumnNumber` 元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideControl 的 AutoSize 元素 (格式)](./autosize-element-for-widecontrol-format.md)|選擇性項目。<br /><br /> 指定是否根據資料的大小調整資料行大小和資料行數目。|
|[WideControl 的 ColumnNumber 元素 (格式)](./columnnumber-element-for-widecontrol-format.md)|選擇性項目。<br /><br /> 指定以寬視圖顯示的資料行數目。|
|[WideEntries 元素 (格式) ](./wideentries-element-for-widecontrol-format.md)|必要元素。<br /><br /> 提供寬視圖的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視元素 (格式)](./view-element-format.md)|定義用來顯示一或多個 .NET 物件的視圖。|

## <a name="remarks"></a>備註

定義廣泛的視圖時，您可以加入 `AutoSize` 元素或， `ColumnNumber` 但無法同時加入兩者。

在大部分的情況下，每個寬視圖都只需要一個定義，但如果您想要使用相同的視圖來顯示不同的 .NET 物件，則可以有多個定義。 在這些情況下，您可以為每個物件或一組物件提供個別的定義。

如需廣泛視圖元件的詳細資訊，請參閱 [Wide View 元件](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例顯示的專案 `WideControl` 是用來顯示 [system.object](/dotnet/api/System.Diagnostics.Process) 物件的屬性。

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

如需完整的完整範例，請參閱 [ (基本) 的寬量視圖 ](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[WideControl (格式的 Autosize 元素) ](./autosize-element-for-widecontrol-format.md)

[WideControl 的 ColumnNumber 元素 (格式)](./columnnumber-element-for-widecontrol-format.md)

[檢視元素 (格式)](./view-element-format.md)

[WideEntries 元素 (格式) ](./wideentries-element-for-widecontrol-format.md)

[寬型檢視 (基本)](./wide-view-basic.md)

[建立寬型檢視](./creating-a-wide-view.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
