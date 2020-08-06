---
title: GroupBy (格式的標籤元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 07b4d037472a9dd2329e94576ec10f5b82f46b34
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785773"
---
# <a name="label-element-for-groupby-format"></a>GroupBy 的標籤元素 (格式)

指定遇到新群組時所顯示的標籤。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素，用於 GroupBy (格式) 標籤元素 (

## <a name="syntax"></a>語法

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `Label` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)|定義新群組物件的顯示方式。|

## <a name="text-value"></a>文字值

指定每當 Windows PowerShell 遇到新的屬性或腳本值時所顯示的文字。

## <a name="remarks"></a>備註

除了此元素所指定的文字之外，Windows PowerShell 還會顯示啟動群組的新值，並在群組前後加上一個空白行。

## <a name="example"></a>範例

下列範例會顯示新群組的標籤。 顯示的標籤看起來會像這樣：`Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

如需包含此元素的完整格式檔案範例，請參閱[Wide View (GroupBy) ](./wide-view-groupby.md)。

## <a name="see-also"></a>另請參閱

[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
