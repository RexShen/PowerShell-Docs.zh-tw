---
title: GroupBy (格式) 的 CustomControl 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b8265e872d34ea5dbcedfaa1668d21df8c3b35eb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786062"
---
# <a name="customcontrol-element-for-groupby-format"></a>GroupBy 的 CustomControl 元素 (格式)

定義顯示新群組的自訂控制項。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（適用于 GroupBy (格式) CustomControl 元素） (

## <a name="syntax"></a>語法

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `CustomControl` 。 您可以指定任意數目的子項目，並依任何順序列出它們。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)](./customentries-element-for-customcontrol-for-groupby-format.md)|必要元素。<br /><br /> 提供控制項的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)|定義 Windows PowerShell 如何顯示新的物件群組。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)](./customentries-element-for-customcontrol-for-groupby-format.md)

[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
