---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視元素 (格式)
description: 檢視元素 (格式)
ms.openlocfilehash: 6fed1304d94339cc90b6ae53e06483c08d937c12
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649738"
---
# <a name="view-element-format"></a>檢視元素 (格式)

定義顯示一或多個 .NET 物件的視圖。 在格式化檔案中可定義的視圖數目沒有任何限制。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `View` 。 您只能指定一個控制項子項目，而且您必須指定視圖的名稱和使用此視圖的物件。 定義自訂控制項、如何將物件分組，以及指定視圖是否為頻外的選項。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[檢視的控制項元素 (格式)](./controls-element-for-view-format.md)|選擇性項目。<br /><br /> 定義一組可從視圖內依名稱參考的控制項。|
|[CustomControl 元素 (格式) ](./customcontrol-element-for-groupby-format.md)|選擇性項目。<br /><br /> 定義視圖的自訂控制項格式。|
|[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)|選擇性項目。<br /><br /> 定義如何將 .NET 物件的成員分組。|
|[ListControl 元素 (格式)](./listcontrol-element-format.md)|選擇性項目。<br /><br /> 定義視圖的清單格式。|
|[檢視的名稱元素 (格式)](./name-element-for-view-format.md)|必要元素。<br /><br /> 指定用來參考視圖的名稱。|
|[TableControl 元素 (格式)](./tablecontrol-element-format.md)|選擇性項目。<br /><br /> 定義視圖的資料表格式。|
|[View (格式的 ViewSelectedBy 元素) ](./viewselectedby-element-format.md)|必要元素。<br /><br /> 定義此視圖所顯示的 .NET 物件。|
|[WideControl 元素 (格式)](./widecontrol-element-format.md)|選擇性項目。<br /><br /> 為視圖定義寬 (單一值) 清單格式。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ViewDefinitions 元素 (格式)](./viewdefinitions-element-format.md)|定義用來顯示物件的視圖。|

## <a name="remarks"></a>備註

如需不同 views 和自訂控制群組件的詳細資訊，請參閱下列主題：

- [資料表視圖元件](./creating-a-table-view.md)

- [清單視圖元件](./creating-a-list-view.md)

- [寬視圖元件](./creating-a-wide-view.md)

- [自訂控制項](./creating-custom-controls.md)

## <a name="example"></a>範例

這個範例會顯示 `View` 定義 [system.serviceprocess.dll Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 物件之資料表視圖的元素。

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>另請參閱

[ViewDefinitions 元素 (格式)](./viewdefinitions-element-format.md)

[檢視的名稱元素 (格式)](./name-element-for-view-format.md)

[ViewSelectedBy 元素 (格式)](./viewselectedby-element-format.md)

[檢視的控制項元素 (格式)](./controls-element-for-view-format.md)

[檢視的 GroupBy 元素 (格式)](./groupby-element-for-view-format.md)

[TableControl 元素 (格式)](./tablecontrol-element-format.md)

[ListControl 元素 (格式)](./listcontrol-element-format.md)

[WideControl 元素 (格式)](./widecontrol-element-format.md)

[CustomControl 元素 (格式) ](./customcontrol-element-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
