---
title: 項目名稱 （格式） 檢視 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859504"
---
# <a name="name-element-for-view-format"></a>檢視的名稱元素 (格式)

指定用來識別檢視的名稱。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 名稱項目 （格式）

## <a name="syntax"></a>語法

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`Name`項目。 只有一個`Name`元素可在每個檢視。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[檢視項目 （格式）](./view-element-format.md)|定義用來顯示的一或多個.NET 物件成員的檢視。|

## <a name="text-value"></a>文字值

指定檢視的唯一易記名稱。 此名稱可以包含的哪些物件或一組物件使用的檢視中，哪些命令可傳回物件或這些項目的組合 （例如以資料表或清單檢視），檢視類型的參考。

## <a name="remarks"></a>備註

如需有關檢視的不同類型的詳細資訊，請參閱下列主題：[資料表檢視](./creating-a-table-view.md)，[清單檢視](./creating-a-list-view.md)，[寬型檢視](./creating-a-wide-view.md)，和[自訂檢視](./creating-custom-controls.md)。

## <a name="example"></a>範例

下列範例所示`View`定義的資料表檢視項目[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。 檢視的名稱是 「 服務 」。

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[建立資料表檢視](./creating-a-table-view.md)

[建立寬型檢視](./creating-a-wide-view.md)

[建立自訂控制項](./creating-custom-controls.md)

[檢視項目 （格式）](./view-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
