---
title: GroupBy 的標籤元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365197"
---
# <a name="label-element-for-groupby-format"></a>GroupBy 的標籤元素 (格式)

指定遇到新群組時所顯示的標籤。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） groupby 元素（格式） GroupBy 專案（格式）

## <a name="syntax"></a>語法

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述 `Label` 專案的屬性、子專案和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)|定義新群組物件的顯示方式。|

## <a name="text-value"></a>文字值

指定每當 Windows PowerShell 遇到新的屬性或腳本值時所顯示的文字。

## <a name="remarks"></a>備註

除了此元素所指定的文字之外，Windows PowerShell 還會顯示啟動群組的新值，並在群組前後加上一個空白行。

## <a name="example"></a>範例

下列範例會顯示新群組的標籤。 顯示的標籤看起來會像這樣： `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

如需包含此元素之完整格式檔案的範例，請參閱[寬視圖（GroupBy）](./wide-view-groupby.md)。

## <a name="see-also"></a>另請參閱

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
