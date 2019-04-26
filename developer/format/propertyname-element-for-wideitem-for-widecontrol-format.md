---
title: PropertyName WideItem 如 WideControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064640"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>WideControl 之 WideItem 的 PropertyName 元素 (格式)

指定其值會顯示在寬型檢視物件的屬性。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） WideItem 項目 （格式） PropertyName 項目 WideItem （格式）

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`PropertyName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[WideItem 項目 （格式）](./wideitem-element-for-widecontrol-format.md)|定義屬性或其值會顯示在寬型檢視的指令碼。|

## <a name="text-value"></a>文字值

指定其值會顯示屬性的名稱。

## <a name="remarks"></a>備註

如需詳細的寬型檢視元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。

## <a name="example"></a>範例

此範例示範顯示之 ProcessName 屬性的值的寬型檢視[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a>另請參閱

[WideItem 項目 （格式）](./wideitem-element-for-widecontrol-format.md)

[建立寬型檢視](./creating-a-wide-view.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
