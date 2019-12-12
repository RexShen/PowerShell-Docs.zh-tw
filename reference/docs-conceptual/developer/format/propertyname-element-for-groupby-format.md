---
title: GroupBy 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362517"
---
# <a name="propertyname-element-for-groupby-format"></a>GroupBy 的 PropertyName 元素 (格式)

指定在每次其值變更時啟動新群組的 .NET 屬性。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（格式） GroupBy （格式）的 PropertyName 元素

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `PropertyName` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)|定義一組 .NET 物件的顯示方式。|

## <a name="text-value"></a>文字值

指定 .NET 屬性名稱。

## <a name="remarks"></a>備註

每當這個屬性的值變更時，Windows PowerShell 就會啟動新的群組。

當指定此元素時，您無法指定[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素來啟動新的群組。

## <a name="example"></a>範例

下列範例示範當屬性的值變更時，如何啟動新的群組。

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

如需包含此元素之完整格式檔案的範例，請參閱[寬視圖（GroupBy）](./wide-view-groupby.md)。

## <a name="see-also"></a>另請參閱

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[GroupBy 的 ScriptBlock 元素（格式）](./scriptblock-element-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
