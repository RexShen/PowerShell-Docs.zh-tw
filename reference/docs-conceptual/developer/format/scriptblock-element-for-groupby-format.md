---
title: GroupBy 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364927"
---
# <a name="scriptblock-element-for-groupby-format"></a>GroupBy 的 ScriptBlock 元素 (格式)

指定每當新群組的值變更時，就會啟動的腳本。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（格式）-GroupBy 的 ScriptBlock 元素（格式）

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `ScriptBlock` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)|定義一組 .NET 物件的顯示方式。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

每當此腳本的值變更時，PowerShell 就會啟動新的群組。

當指定此元素時，您無法指定[PropertyName](propertyname-element-for-groupby-format.md)元素來啟動新的群組。

## <a name="see-also"></a>另請參閱

[GroupBy 的 PropertyName 元素（格式）](propertyname-element-for-groupby-format.md)

[View 的 GroupBy 元素（格式）](groupby-element-for-view-format.md)

[撰寫 PowerShell 格式化檔案](writing-a-powershell-formatting-file.md)
