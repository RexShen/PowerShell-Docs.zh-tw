---
title: WideEntries WideControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083683"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideControl 的 WideEntries 元素 (格式)

提供的寬型檢視的定義。 寬型檢視必須指定一個或多個定義。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式）

## <a name="syntax"></a>語法

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`WideEntries`項目。 必須指定至少一個子系項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 項目 （格式）](./wideentry-element-for-widecontrol-format.md)|提供寬型檢視的定義。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[WideControl 項目 （格式）](./widecontrol-element-format.md)|寬 （單一值） 會定義檢視的清單格式。|

## <a name="remarks"></a>備註

寬型檢視是顯示單一屬性值或每個物件的指令碼值以清單格式。 如需詳細的寬型檢視元件的相關資訊，請參閱[寬型檢視元件](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例所示`WideEntries`項目，定義單一`WideEntry`項目。 `WideEntry`元素包含單一`WideItem`項目，定義在檢視中顯示哪些屬性或指令碼的值。

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

寬型檢視的完整範例，請參閱[（基本） 的寬型檢視](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[WideControl 項目 （格式）](./widecontrol-element-format.md)

[WideEntry 項目 （格式）](./wideentry-element-for-widecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
