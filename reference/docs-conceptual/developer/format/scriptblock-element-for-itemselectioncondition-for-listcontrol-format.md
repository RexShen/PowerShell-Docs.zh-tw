---
title: ItemSelectionCondition for ListControl (格式的 ScriptBlock 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 38dc952bfadd6aed24bae8cbef05adcd22e61dd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787626"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)

指定觸發條件的腳本。 當此腳本評估為時 `true` ，會符合條件，且會使用清單專案。 定義清單視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntry for ListEntries 的 ListControl 專案的 ListControl (format) ListItems 元素（ListEntry for ListControl (format) ListItems 專案 for ItemSelectionCondition for ListControl (format) ScriptBlock 元素 for ItemSelectionCondition 的 ListControl (format) 

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
|[ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|定義必須存在才能使用此清單專案的條件。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

如果使用這個元素，則在 `PropertyName` 定義選取條件時，不能指定元素。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
