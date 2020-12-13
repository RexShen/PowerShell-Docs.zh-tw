---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 的 ScriptBlock 元素 (格式)
description: GroupBy 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 117cbef93889046626741449886a1caaa39815cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665240"
---
# <a name="scriptblock-element-for-groupby-format"></a>GroupBy 的 ScriptBlock 元素 (格式)

指定每當新群組值變更時，會啟動新群組的腳本。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) groupby 專案的 (格式)  (格式的 ScriptBlock 元素) 

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)|定義如何顯示 .NET 物件的群組。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

每當此腳本的值變更時，PowerShell 就會啟動新的群組。

當指定這個專案時，您無法指定 [PropertyName](propertyname-element-for-groupby-format.md) 元素來啟動新群組。

## <a name="see-also"></a>另請參閱

[GroupBy 的 PropertyName 元素 (格式)](propertyname-element-for-groupby-format.md)

[檢視的 GroupBy 元素 (格式)](groupby-element-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](writing-a-powershell-formatting-file.md)
