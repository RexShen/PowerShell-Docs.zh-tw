---
title: GroupBy 的 CustomControlName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368877"
---
# <a name="customcontrolname-element-for-groupby-format"></a>GroupBy 的 CustomControlName 元素 (格式)

指定用來顯示新群組的自訂控制項名稱。 定義資料表、清單、寬型或自訂控制項視圖時，會使用這個元素。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） groupby 元素（格式） GroupBy 的 CustomControlName 元素（格式）

## <a name="syntax"></a>語法

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述 `CustomControlName` 專案的屬性、子專案和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)|定義 Windows PowerShell 如何顯示新的物件群組。|

## <a name="text-value"></a>文字值

指定用來顯示新群組的自訂控制項名稱。

## <a name="remarks"></a>備註

您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。 下列元素會指定這些自訂控制項的名稱：

- [設定之控制項的控制項的名稱元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

- [View 控制項控制項的 Name 元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另請參閱

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[設定之控制項的控制項的名稱元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

[View 控制項控制項的 Name 元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
