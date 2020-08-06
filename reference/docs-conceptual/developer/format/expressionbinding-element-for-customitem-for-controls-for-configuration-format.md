---
title: CustomItem 之控制項的 ExpressionBinding 元素，用於設定 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1ad83fa9d915822eaefb490658f8a219defdddf2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773907"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 專案 (格式) 控制設定的控制項元素 (格式設定 (格式的控制項) 控制元素) 設定 (格式的 CustomControl 的 CustomEntries 元素) 設定 (格式) CustomControl 元素適用于設定 (格式的控制項 CustomItem 的 Configuration CustomEntry 元素的 ExpressionBinding 專案) 的控制

## <a name="syntax"></a>語法

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ExpressionBinding` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomControl Element`|選擇性項目。<br /><br /> 定義此控制項所使用的控制項。|
|[設定之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定通用控制項或 view 控制項的名稱。|
|[設定之控制項的 ExpressionBinding 的 EnumerateCollection 元素 (格式)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定控制項會顯示集合的元素。|
|[設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 定義必須存在的條件，才能使用此通用控制項。|
|[設定之控制項的 ExpressionBinding 的 PropertyName 元素 (格式)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定由通用控制項顯示其值的 .NET 屬性。|
|[設定之控制項的 ExpressionBinding 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定由通用控制項顯示其值的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomEntry 的 CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|定義自訂控制項視圖顯示的資料，以及顯示的方式。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[設定之控制項的 CustomEntry 的 CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
