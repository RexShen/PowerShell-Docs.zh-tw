---
title: 之 wideitem for WideControl (格式的 ScriptBlock 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: be649d6de0d2dfa6bad14f2d7476cced9cd6cb6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787592"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>WideControl 之 WideItem 的 ScriptBlock 元素 (格式)

指定在寬視圖中顯示其值的腳本。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 專案 (格式) WideEntries 專案 (格式) WideEntry 元素 (格式) 之 wideitem 元素 (格式) 之 wideitem (格式的 ScriptBlock 元素) 

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `ScriptBlock` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[之 wideitem 元素 (格式) ](./wideitem-element-for-widecontrol-format.md)|定義屬性或腳本區塊，其值會顯示在寬視圖中。|

## <a name="text-value"></a>文字值

指定顯示其值的腳本。

## <a name="remarks"></a>備註

如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

## <a name="example"></a>範例

這個範例示範的 `WideItem` 元素會定義一個腳本，其值會顯示在視圖中。

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>另請參閱

[之 wideitem 元素 (格式) ](./wideitem-element-for-widecontrol-format.md)

[建立寬型檢視](./creating-a-wide-view.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
