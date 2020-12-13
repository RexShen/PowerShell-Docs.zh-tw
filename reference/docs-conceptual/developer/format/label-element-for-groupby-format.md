---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 的標籤元素 (格式)
description: GroupBy 的標籤元素 (格式)
ms.openlocfilehash: ff4b0dec01bb5b472b1813540661791b91568eed
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649798"
---
# <a name="label-element-for-groupby-format"></a>GroupBy 的標籤元素 (格式)

指定當遇到新群組時所顯示的標籤。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) groupby 的 GroupBy 專案 (格式) GroupBy (格式的 Label 元素) 

## <a name="syntax"></a>語法

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `Label` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)|定義如何顯示新的物件群組。|

## <a name="text-value"></a>文字值

指定每當 Windows PowerShell 遇到新的屬性或腳本值時，所顯示的文字。

## <a name="remarks"></a>備註

除了這個專案所指定的文字之外，Windows PowerShell 會顯示啟動群組的新值，並在群組前後加入空白行。

## <a name="example"></a>範例

下列範例顯示新群組的標籤。 顯示的標籤看起來會像這樣： `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

如需包含此專案之完整格式化檔案的範例，請參閱 [Wide View (GroupBy) ](./wide-view-groupby.md)。

## <a name="see-also"></a>另請參閱

[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
