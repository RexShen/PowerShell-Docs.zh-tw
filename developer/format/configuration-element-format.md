---
title: 組態項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066816"
---
# <a name="configuration-element-format"></a>設定元素 (格式)

表示格式化檔案的最上層項目。

組態項目

## <a name="syntax"></a>語法

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`Configuration`項目。 此元素必須是每個格式檔案的根項目及這個項目必須包含至少一個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[組態 （格式） 的 controls 項目](./controls-element-for-configuration-format.md)|選擇性的項目。<br /><br /> 定義可由格式檔案的所有檢視通用控制項。|
|[DefaultSettings 項目 （格式）](./defaultsettings-element-format.md)|選擇性的項目。<br /><br /> 定義套用至的格式化檔案的所有檢視的常見設定。|
|[SelectionSets 項目格式](./selectionsets-element-format.md)|選擇性的項目。<br /><br /> 定義通用的集合，可供所有檢視的格式化檔案的.NET 物件。|
|[ViewDefinitions 項目 （格式）](./viewdefinitions-element-format.md)|選擇性的項目。<br /><br /> 定義用來顯示物件的檢視。|

### <a name="parent-elements"></a>父項目

無。

## <a name="remarks"></a>備註

格式檔案會定義物件的顯示方式。 在大部分情況下，此根項目包含[ViewDefinitions](./viewdefinitions-element-format.md)定義資料表、 清單和格式檔案的寬型檢視的項目。 檢視定義中，除了一般的選取項目集、 設定和這些檢視可以使用的控制項，可以定義的格式化檔案。

## <a name="see-also"></a>另請參閱

[組態 （格式） 的 controls 項目](./controls-element-for-configuration-format.md)

[DefaultSettings 項目 （格式）](./defaultsettings-element-format.md)

[SelectionSets 項目 （格式）](./selectionsets-element-format.md)

[ViewDefinitions 項目 （格式）](./viewdefinitions-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
