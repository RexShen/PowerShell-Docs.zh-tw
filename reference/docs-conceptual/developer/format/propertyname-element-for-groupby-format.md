---
title: GroupBy (格式的 PropertyName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e83ebd49e4f3087c817b3cc8772889dbe85113aa
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785603"
---
# <a name="propertyname-element-for-groupby-format"></a>GroupBy 的 PropertyName 元素 (格式)

指定在每次其值變更時啟動新群組的 .NET 屬性。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素用於 GroupBy (格式) 

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
|[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)|定義一組 .NET 物件的顯示方式。|

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

如需包含此元素的完整格式檔案範例，請參閱[Wide View (GroupBy) ](./wide-view-groupby.md)。

## <a name="see-also"></a>另請參閱

[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)

[GroupBy 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
