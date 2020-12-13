---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 之 WideItem 的 ScriptBlock 元素 (格式)
description: WideControl 之 WideItem 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 68e47926e5e6b846c8a0a3dbc16d1f0d59f11dee
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659876"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>WideControl 之 WideItem 的 ScriptBlock 元素 (格式)

指定以寬視圖顯示其值的腳本。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 wideitem 專案 (格式) 之 wideitem (格式的 ScriptBlock 元素) 

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `ScriptBlock` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[之 wideitem 元素 (格式) ](./wideitem-element-for-widecontrol-format.md)|定義其值顯示在寬視圖中的屬性或腳本區塊。|

## <a name="text-value"></a>文字值

指定顯示其值的腳本。

## <a name="remarks"></a>備註

如需有關廣泛視圖元件的詳細資訊，請參閱 [建立廣泛的視圖](./creating-a-wide-view.md)。

## <a name="example"></a>範例

這個範例會示範 `WideItem` 定義腳本的元素，此腳本會在 view 中顯示其值。

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>另請參閱

[之 wideitem 元素 (格式) ](./wideitem-element-for-widecontrol-format.md)

[建立寬型檢視](./creating-a-wide-view.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
