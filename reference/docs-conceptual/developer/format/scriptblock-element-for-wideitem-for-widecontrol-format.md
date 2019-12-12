---
title: WideControl 之之 wideitem 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362027"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>WideControl 之 WideItem 的 ScriptBlock 元素 (格式)

指定在寬視圖中顯示其值的腳本。

之 wideitem 的設定元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 wideitem 元素（格式） ScriptBlock 元素（格式）

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述 `ScriptBlock` 專案的屬性、子專案和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[之 wideitem 元素（格式）](./wideitem-element-for-widecontrol-format.md)|定義屬性或腳本區塊，其值會顯示在寬視圖中。|

## <a name="text-value"></a>文字值

指定顯示其值的腳本。

## <a name="remarks"></a>備註

如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

## <a name="example"></a>範例

這個範例會顯示一個 `WideItem` 專案，定義一個腳本，其值會顯示在視圖中。

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>另請參閱

[之 wideitem 元素（格式）](./wideitem-element-for-widecontrol-format.md)

[建立寬型視圖](./creating-a-wide-view.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
