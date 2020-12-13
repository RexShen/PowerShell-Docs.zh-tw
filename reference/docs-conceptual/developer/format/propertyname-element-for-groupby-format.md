---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 的 PropertyName 元素 (格式)
description: GroupBy 的 PropertyName 元素 (格式)
ms.openlocfilehash: 44351c46ff2386f967644fef4f423b3858dc1619
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666139"
---
# <a name="propertyname-element-for-groupby-format"></a>GroupBy 的 PropertyName 元素 (格式)

指定每當新群組值變更時，會啟動新群組的 .NET 屬性。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) groupby (格式的 groupby 元素) 

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)|定義如何顯示 .NET 物件的群組。|

## <a name="text-value"></a>文字值

指定 .NET 屬性名稱。

## <a name="remarks"></a>備註

每當這個屬性的值變更時，Windows PowerShell 就會啟動新的群組。

當指定這個專案時，您無法指定 [ScriptBlock](./scriptblock-element-for-groupby-format.md) 元素來啟動新群組。

## <a name="example"></a>範例

下列範例示範如何在屬性值變更時，啟動新的群組。

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

如需包含此專案之完整格式化檔案的範例，請參閱 [Wide View (GroupBy) ](./wide-view-groupby.md)。

## <a name="see-also"></a>另請參閱

[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)

[GroupBy 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
