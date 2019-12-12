---
title: 格式架構 XML 參考 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 437b3d6bb62fdd3a74f3392ec71df360c01a1974
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363717"
---
# <a name="format-schema-xml-reference"></a>格式結構描述 XML 參考

本節中的主題描述格式化檔案（types.ps1xml 檔案）所使用的 XML 元素。 格式化檔案會定義 .NET 物件的顯示方式;它們不會變更物件本身。

## <a name="in-this-section"></a>在本節中

[TableControl 之之 tablecolumnheader 的對齊元素（格式）](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)定義資料行標頭中的資料顯示方式。

[TableControl 之之 tablecolumnitem 的對齊元素（格式）](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)定義如何顯示資料列中的資料。

[TableControl 的 AutoSize 元素（格式）](./autosize-element-for-tablecontrol-format.md)指定是否根據資料大小來調整資料行大小和資料行數目。

[WideControl 的 Autosize 元素（格式）](./autosize-element-for-widecontrol-format.md)指定是否根據資料大小來調整資料行大小和資料行數目。

[WideControl 的 ColumnNumber 元素（格式）](./columnnumber-element-for-widecontrol-format.md)指定在寬視圖中顯示的資料行數目。

[Configuration 元素（格式）](./configuration-element-format.md)代表格式檔案的最上層元素。

[設定之控制項的控制項元素（格式）](./control-element-for-controls-for-configuration-format.md)定義可供格式檔案的所有視圖使用的通用控制項，以及用來參考控制項的名稱。

[View 控制項的控制項元素（格式）](./control-element-for-controls-for-view-format.md)定義可供視圖使用的控制項，以及用來參考控制項的名稱。

[設定的 Controls 元素（格式）](./controls-element-for-configuration-format.md)定義可供格式檔案的所有視圖使用的通用控制項。

[View 的 Controls 元素（格式）](./controls-element-for-view-format.md)定義可供特定視圖使用的 view 控制項。

[設定之控制項的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-configuration-format.md)定義控制項。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 控制項的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-view-format.md)定義視圖所使用的控制項。

[GroupBy 的 CustomControl 元素（格式）](./customcontrol-element-for-groupby-format.md)定義顯示新群組的自訂控制項。

[CustomControl 元素（格式）](./customcontrol-element-for-groupby-format.md)定義視圖的自訂控制項格式。

[設定之控制項的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)指定通用控制項的名稱。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 ExpressionBindine 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)指定通用控制項或 view 控制項的名稱。 定義可供視圖使用的控制項時，會使用這個元素。

[GroupBy 的 CustomControlName 元素（格式）](./customcontrolname-element-for-groupby-format.md)指定用來顯示新群組的自訂控制項名稱。 定義資料表、清單、寬型或自訂控制項視圖時，會使用這個元素。

[設定之控制項的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)提供通用控制項的定義。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-controls-for-view-format.md)提供控制項的定義。 定義可供視圖使用的控制項時，會使用這個元素。

[CustomEntries For View 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)提供自訂控制項視圖的定義。

[GroupBy 之 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-groupby-format.md)提供控制項的定義。 此元素是在定義新物件群組的顯示方式時使用。

[設定之 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)提供通用控制項的定義。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-controls-for-view-format.md)提供控制項的定義。 定義可供視圖使用的控制項時，會使用這個元素。

[GroupBy 之 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-groupby-format.md)提供控制項的定義。 此元素是在定義新物件群組的顯示方式時使用。

[CustomControl For View 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-view-format.md)提供自訂控制項視圖的定義。 自訂控制項視圖必須指定一或多個定義。

設定之[控制項的 CustomEntry 的 CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)定義控制項所顯示的資料及其顯示方式。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-controls-for-view-format.md)定義控制項所顯示的資料及其顯示方式。 定義可供視圖使用的控制項時，會使用這個元素。

[CustomEntry For View 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)定義自訂控制項視圖顯示的資料，以及顯示的方式。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 之 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-groupby-format.md)定義自訂控制項視圖顯示的資料，以及顯示的方式。 此元素是在定義新物件群組的顯示方式時使用。

[DefaultSettings 元素（格式）](./defaultsettings-element-format.md)定義套用至格式化檔案所有視圖的一般設定。 一般設定包括顯示錯誤、在資料表中將文字換行、定義如何擴充集合等等。

[DisplayError 元素（格式）](./displayerror-element-format.md)指定在顯示一段資料時發生錯誤時，顯示 #ERR 的字串。

[設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)定義使用通用控制項定義的 .NET 類型，或必須存在才能使用此控制項的條件。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。 定義可供視圖使用的控制項時，會使用這個元素。

[CustomEntry For View 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)定義使用此自訂專案的 .NET 類型，或必須存在才能使用此專案的條件。

[EnumerableExpansion 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-enumerableexpansion-format.md)定義使用此定義的 .NET 類型，或必須存在才能使用此定義的條件。

[GroupBy 之 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-groupby-format.md)定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。 此元素是在定義新物件群組的顯示方式時使用。

[ListControl 之 ListEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-listentry-for-listcontrol-format.md)定義使用此清單視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。 在大部分情況下，清單視圖只需要一個定義。 不過，如果您想要使用相同的清單視圖來顯示不同物件的不同資料，可以為清單視圖提供多個定義。

[TableRowEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)定義其屬性值會顯示在資料列中的 .NET 類型。

[WideEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-wideentry-format.md)定義使用此寬視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。

[EnumerableExpansion 元素（格式）](./enumerableexpansion-element-format.md)定義特定 .NET 集合物件在視圖中顯示時的擴充方式。

[EnumerableExpansions 元素（格式）](./enumerableexpansions-element-format.md)定義 .NET 集合物件在視圖中顯示時的展開方式。

[設定之控制項的 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)指定控制項會顯示集合的元素。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)指定會顯示集合的元素。 定義可供視圖使用的控制項時，會使用這個元素。

[CustomControl For View 的運算式系結的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)指定顯示集合的元素。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 之 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)指定顯示集合的元素。 此元素是在定義新物件群組的顯示方式時使用。

[展開元素（格式）](./expand-element-format.md)指定如何展開這個定義的集合物件。

[設定之控制項的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)定義控制項所顯示的資料。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)定義控制項所顯示的資料。 定義可供視圖使用的控制項時，會使用這個元素。

[CustomControl For View 的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)定義控制項所顯示的資料。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-groupby-format.md)定義控制項所顯示的資料。 此元素是在定義新物件群組的顯示方式時使用。

[設定之控制項的框架的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)指定第一行資料向左移動的字元數。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 控制項框架的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)指定第一行資料向左移動的字元數。 定義可供視圖使用的控制項時，會使用這個元素。

[CustomControl For View 的 Frame 的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)指定第一行資料向左移動的字元數。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 之框架的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-groupby-format.md)指定第一行資料向左移動的字元數。 此元素是在定義新物件群組的顯示方式時使用。

[設定之控制項的框架的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)指定第一行資料向右移動的字元數。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 控制項框架的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-controls-for-view-format.md)指定第一行資料向右移動的字元數。 定義可供視圖使用的控制項時，會使用這個元素。

[FirstLineIndent 元素](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)指定第一行資料向右移動的字元數。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 之框架的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-groupby-format.md)指定第一行資料向右移動的字元數。 此元素是在定義新物件群組的顯示方式時使用。

專案[的字串格式元素（格式）](./formatstring-element-for-listitem-for-listcontrol-format.md)指定定義屬性或腳本值顯示方式的格式模式。

[之 tablecolumnitem 的格式字串元素（格式）](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)指定定義如何顯示資料表之屬性或腳本值的格式模式。

[WideControl 之之 wideitem 的格式字串元素（格式）](./formatstring-element-for-wideitem-for-widecontrol-format.md)指定定義屬性或腳本值在視圖中顯示方式的格式模式。

用於[設定之控制項的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-controls-for-configuration-format.md)定義資料的顯示方式，例如將資料向左或向右移位。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-controls-for-view-format.md)定義資料的顯示方式，例如將資料向左或向右移位。 定義可供視圖使用的控制項時，會使用這個元素。

適用于[CustomControl For View 的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-customcontrol-for-view-format.md)定義資料的顯示方式，例如將資料向左或向右移位。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 之 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-groupby-format.md)定義資料的顯示方式，例如將資料向左或向右移位。 此元素是在定義新物件群組的顯示方式時使用。

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)定義 Windows PowerShell 如何顯示新的物件群組。

[HideTableHeaders 元素（格式）](./hidetableheaders-element-format.md)指定不顯示資料表的標頭。

[設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)定義必須存在才能使用此控制項的條件。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)定義必須存在才能使用此控制項的條件。 定義可供視圖使用的控制項時，會使用這個元素。

[CustomControl For View 的運算式系結的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)定義必須存在才能使用此控制項的條件。 可以針對控制項專案指定的選取條件數目沒有限制。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)定義必須存在才能使用此控制項的條件。 可以針對控制項專案指定的選取條件數目沒有限制。 此元素是在定義新物件群組的顯示方式時使用。

專案[的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)定義必須存在才能使用此清單專案的條件。

ListControl 之專案的[標籤元素（格式）](./label-element-for-listitem-for-listcontrol-format.md)指定資料列中屬性或腳本值的標籤。

[GroupBy 的標籤元素（格式）](./label-element-for-groupby-format.md)指定遇到新群組時所顯示的標籤。

[之 tablecolumnheader 的標籤元素（格式）](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)定義顯示在資料行頂端的標籤。

[設定之控制項的框架的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-controls-for-configuration-format.md)指定資料從左邊界下移的字元數。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 控制項框架的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-controls-for-view-format.md)指定資料從左邊界下移的字元數。 定義可供視圖使用的控制項時，會使用這個元素。

[CustomControl For View 的 Frame 的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)指定資料從左邊界下移的字元數。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 之框架的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-groupby-format.md)指定資料從左邊界下移的字元數。 此元素是在定義新物件群組的顯示方式時使用。

[ListControl 元素（格式）](./listcontrol-element-format.md)定義視圖的清單格式。

[ListEntry 元素（格式）](./listentry-element-for-listcontrol-format.md)提供清單視圖的定義。

[ListEntries 元素（格式）](./listentries-element-for-listcontrol-format.md)定義如何顯示清單視圖的資料列。

[[專案] 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)定義屬性或腳本，其值會顯示在清單視圖的資料列中。

[ListItems 元素（格式）](./listitems-element-for-listentry-for-listcontrol-format.md)定義顯示在清單視圖中的屬性和腳本。

設定之控制項的[控制項的名稱元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)指定控制項的名稱。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[SelectionSet 的名稱元素（格式）](./name-element-for-selectionset-format.md)指定用來參考選取集的名稱。

[View 的 Name 元素（格式）](./name-element-for-view-format.md)指定用來識別此視圖的名稱。

[設定之控制項的 CustomItem 的新行元素（格式）](./newline-element-for-customitem-for-controls-for-configuration-format.md)將空白行加入控制項的顯示中。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 CustomItem 的分行符號元素（格式）](./newline-element-for-customitem-for-controls-for-view-format.md)將空白行加入控制項的顯示中。 定義可供視圖使用的控制項時，會使用這個元素。

[CustomControl For View 的 CustomItem 的換行元素（格式）](./newline-element-for-customitem-for-customcontrol-for-view-format.md)將空白行加入控制項的顯示中。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 的 CustomItem 的分行符號元素（格式）](./newline-element-for-customitem-for-groupby-format.md)將空白行加入控制項的顯示中。 此元素是在定義新物件群組的顯示方式時使用。

[設定之控制項的 ExpressionBinding 的 PropertyName 元素（格式）](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)指定由通用控制項顯示其值的 .NET 屬性。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 ExpressionBinding 的 PropertyName 元素（格式）](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)指定控制項顯示其值的 .NET 屬性。 定義可供視圖使用的控制項時，會使用這個元素。

[ExpressionBinding For CustomControl For View 的 PropertyName 元素（格式）](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)指定控制項顯示其值的 .NET 屬性。 定義自訂控制項視圖時，會使用這個元素

[GroupBy 之 ExpressionBinding 的 PropertyName 元素（格式）](./propertyname-element-for-expressionbinding-for-groupby-format.md)指定控制項顯示其值的 .NET 屬性。 此元素是在定義新物件群組的顯示方式時使用。

[GroupBy 的 PropertyName 元素（格式）](./propertyname-element-for-groupby-format.md)指定在每次其值變更時啟動新群組的 .NET 屬性。

[設定之控制項的 itemselectioncondition 的 PropertyName 元素（格式）](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用控制項。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 ItemSelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用控制項。 定義可供視圖使用的控制項時，會使用這個元素。

[ItemSelectionCondition For CustomControl For View 的 PropertyName 元素（Format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)會指定觸發條件的 .net 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用控制項。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 之 ItemSelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用控制項。 此元素是在定義新物件群組的顯示方式時使用。

專案[名稱之 ItemSelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用此視圖。 定義清單視圖時，會使用這個元素。

[ListControl 之專案名稱的 PropertyName 元素（格式）](./propertyname-element-for-listitem-for-listcontrol-format.md)指定其值顯示在清單中的 .NET 屬性。

[ListEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用專案。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用專案。 定義可供視圖使用的控制項時，會使用這個元素。

[SelectionCondition For CustomControl For View 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用定義。 定義自訂控制項視圖時，會使用這個元素。

[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用定義。

[GroupBy 之 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-groupby-format.md)指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用定義。 此元素是在定義新物件群組的顯示方式時使用。

[ListEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，而且會使用清單專案。

[TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用資料表專案。

[WideEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用定義。

[之 tablecolumnitem 的 PropertyName 元素（格式）](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)指定屬性，其值會顯示在資料列的資料行中。

[之 wideitem 的 PropertyName 元素（格式）](./propertyname-element-for-wideitem-for-widecontrol-format.md)指定物件的屬性，其值會顯示在寬視圖中。

[設定之控制項的框架的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-controls-for-configuration-format.md)指定資料從右邊界向外移動的字元數。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 控制項框架的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-controls-for-view-format.md)指定資料從右邊界向外移動的字元數。 定義可供視圖使用的控制項時，會使用這個元素。

[RightIndent 元素](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)指定資料從右邊界向外移動的字元數。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 之框架的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-groupby-format.md)指定資料從右邊界向外移動的字元數。 此元素是在定義新物件群組的顯示方式時使用。

[設定之控制項的 ExpressionBinding 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)指定由通用控制項顯示其值的腳本。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 ExpressionBinding 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)指定控制項顯示其值的腳本。 定義可供視圖使用的控制項時，會使用這個元素。

[ExpressionBinding For CustomCustomControl For View 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)指定控制項顯示其值的腳本。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 的 ExpressionBinding 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-groupby-format.md)指定控制項顯示其值的腳本。 此元素是在定義新物件群組的顯示方式時使用。

[GroupBy 的 ScriptBlock 元素（格式）](./scriptblock-element-for-groupby-format.md)指定每當新群組的值變更時，就會啟動的腳本。

[設定之控制項的 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)指定觸發條件的腳本。 當此腳本評估為 `true`時，就會符合條件，並使用控制項。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)指定觸發條件的腳本。 當此腳本評估為 `true`時，就會符合條件，並使用控制項。 定義可供視圖使用的控制項時，會使用這個元素。

[ItemSelectionCondition For CustomControl For View 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)指定觸發條件的腳本。 當此腳本評估為 `true`時，就會符合條件，並使用控制項。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 的 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)指定觸發條件的腳本。 當此腳本評估為 `true`時，就會符合條件，並使用控制項。 此元素是在定義新物件群組的顯示方式時使用。

[ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)指定觸發條件的腳本。 當此腳本評估為 `true`時，會符合條件，而且會使用清單專案。 定義清單視圖時，會使用這個元素。

專案[的 ScriptBlock 元素（格式）](./scriptblock-element-for-listitem-for-listcontrol-format.md)指定其值顯示在清單資料列中的腳本。

[設定之控制項的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)指定觸發條件的腳本。 當此腳本評估為 `true`時，就會符合條件，並使用定義。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)指定觸發條件的腳本。 當此腳本評估為 `true`時，就會符合條件，並使用定義。 定義可供視圖使用的控制項時，會使用這個元素。

[SelectionCondition For CustomControl For View 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)指定觸發條件的腳本。 當此腳本評估為 `true`時，就會符合條件，並使用定義。 定義自訂控制項視圖時，會使用這個元素。

[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定觸發條件的腳本。

[GroupBy 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)指定觸發條件的腳本。 當此腳本評估為 `true`時，就會符合條件，並使用定義。 此元素是在定義新物件群組的顯示方式時使用。

[ListEntry 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)指定觸發條件的腳本。 當此腳本評估為 `true`時，就會符合條件，並使用清單專案。

[TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)指定觸發條件的腳本區塊。 當此腳本評估為 `true`時，就會符合條件，並使用資料表專案。

[WideEntry 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)指定觸發條件的腳本。 當此腳本評估為 `true`時，就會符合條件，並使用寬專案定義。

[之 tablecolumnitem 的 ScriptBlock 元素（格式）](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)指定其值顯示在資料列資料行中的腳本。

[之 wideitem 的 ScriptBlock 元素（格式）](./scriptblock-element-for-wideitem-for-widecontrol-format.md)指定在寬視圖中顯示其值的腳本。

適用于[CustomEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)定義必須存在的條件，才能使用通用控制項定義。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)定義必須存在的條件，才能使用控制項定義。 定義可供視圖使用的控制項時，會使用這個元素。

[CustomControl For View 的之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)定義必須存在的條件，才能使用控制項定義。 定義自訂控制項視圖時，會使用這個元素。

[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)定義必須存在的條件，才能展開這個定義的集合物件。

[GroupBy 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)定義必須存在的條件，才能使用控制項定義。 此元素是在定義新物件群組的顯示方式時使用。

[ListEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)定義必須存在才能使用此清單視圖定義的條件。 可以為清單定義指定的選取條件數目沒有限制。

[TableRowEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)定義必須存在的條件，才能用於這個資料表視圖定義。 可以針對資料表定義指定的選取條件數目沒有限制。

[WideEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)定義必須存在才能使用此定義的條件。 針對寬專案定義可以指定的選取條件數目沒有限制。

[SelectionSet 元素（格式）](./selectionset-element-format.md)定義一組可由集合名稱參考的 .NET 物件。

[設定之控制項的之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)指定一組使用此控制項定義的 .NET 類型。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)指定一組使用此控制項定義的 .NET 類型。 定義可供視圖使用的控制項時，會使用這個元素。

[CustomEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)為清單專案指定一組 .NET 物件。 可以為專案指定的選擇集數目沒有限制。

[EnumerableExpansion 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)指定由這個定義擴充的 .NET 類型集合。

[GroupBy 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)為清單專案指定一組 .NET 物件。 可以為專案指定的選擇集數目沒有限制。 此元素是在定義新物件群組的顯示方式時使用。

[ListEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)為清單專案指定一組 .NET 物件。 可以為專案指定的選擇集數目沒有限制。

[TableRowEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)指定一組 .NET 類型，使用此資料表視圖的專案。 可以為專案指定的選擇集數目沒有限制。

[WideEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)為定義指定一組 .NET 物件。 每當顯示這些物件的其中一個時，就會使用定義。

[設定之控制項的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件，並使用此控制項來顯示該物件。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件，並使用此控制項來顯示該物件。 定義可供視圖使用的控制項時，會使用這個元素。

[CustomEntry For View 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件，並使用此控制項來顯示該物件。 定義自訂控制項視圖時，會使用這個元素。

[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件。

[GroupBy 之 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件，並使用此控制項來顯示該物件。 此元素是在定義新物件群組的顯示方式時使用。

[ListEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件，並使用此清單視圖的定義來顯示該物件。

[TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件，並使用資料表視圖的這個定義來顯示該物件。

[WideEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件，並使用此寬視圖的定義來顯示該物件。

[ViewSelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-viewselectedby-format.md)指定由視圖顯示的一組 .NET 物件。

[SelectionSets 元素（格式）](./selectionsets-element-format.md)定義可供個別格式視圖使用的 .NET 物件集合。

[ShowError 元素（格式）](./showerror-element-format.md)指定顯示資料時，如果發生錯誤，就會顯示完整的錯誤記錄。

[TableControl 之 TableHeaders 的之 tablecolumnheader 元素（格式）](./tablecolumnheader-element-format.md)定義標籤、資料行的寬度，以及資料表資料行的標籤對齊方式。

[之 tablecolumnitem 元素（格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)定義屬性或腳本，其值會顯示在資料列的資料行中。

[TableColumnItems 元素（格式）](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)定義其值會顯示在資料列中的屬性或腳本。

[TableControl 元素（格式）](./tablecontrol-element-format.md)定義視圖的資料表格式。

[TableHeaders 元素（格式）](./tableheaders-element-format.md)定義資料表之資料行的標頭。

[TableRowEntries 元素（格式）](./tablerowentries-element-for-tablecontrol-format.md)定義資料表的資料列。

[TableRowEntry 元素（格式）](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)定義在資料表的資料列中顯示的資料。

[設定之控制項的 CustomItem 的文字元素（格式）](./text-element-for-customitem-for-controls-for-configuration-format.md)指定要加入控制項所顯示之資料的文字，例如標籤、用來括住資料的括弧，以及用來縮排資料的空格。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 CustomItem 的文字元素（格式）](./text-element-for-customitem-for-controls-for-view-format.md)指定要加入控制項所顯示之資料的文字，例如標籤、用來括住資料的括弧，以及用來縮排資料的空格。 定義可供視圖使用的控制項時，會使用這個元素。

[CustomItem 的 Text 元素（格式）](./text-element-for-customitem-for-customview-for-view-format.md)指定要加入控制項所顯示之資料的文字，例如標籤、用來括住資料的括弧，以及用來縮排資料的空格。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy 的 CustomItem 的文字元素（格式）](./text-element-for-customitem-for-groupby-format.md)指定要加入控制項所顯示之資料的文字，例如標籤、用來括住資料的括弧，以及用來縮排資料的空格。 此元素是在定義新物件群組的顯示方式時使用。

[設定之控制項的之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)指定使用此控制項定義的 .NET 類型。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-controls-for-view-format.md)指定使用此控制項定義的 .NET 類型。 定義可供視圖使用的控制項時，會使用這個元素。

[之 entryselectedby For CustomEntry For View 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-customentry-for-view-format.md)指定使用自訂控制項視圖之定義的 .NET 類型。 可以針對定義指定的類型數目沒有限制。

[EnumerableExpansion 之之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)指定由這個定義擴充的 .NET 類型。 定義預設設定時，會使用這個元素。

[GroupBy 之之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-groupby-format.md)指定使用自訂控制項定義的 .NET 類型。 此元素是在定義新物件群組的顯示方式時使用。

[ListControl 之之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-listcontrol-format.md)指定使用此清單視圖專案的 .NET 類型。 可以為清單專案指定的類型數目沒有限制。

[TableRowEntry 之之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-tablecontrol-format.md)指定使用此資料表視圖專案的 .NET 類型。 可以針對資料表專案指定的類型數目沒有限制。

[WideEntry 之之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-wideentry-format.md)指定定義的 .NET 類型。 每當顯示此物件時，就會使用此定義。

[設定之控制項的 SelectionCondition 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)指定觸發條件的 .NET 類型。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

[View 之控制項的 SelectionCondition 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-controls-for-view-format.md)指定觸發條件的 .NET 類型。 定義可供視圖使用的控制項時，會使用這個元素。

[SelectionCondition For CustomControl For View 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)指定觸發條件的 .NET 類型。 定義自訂控制項視圖時，會使用這個元素。

[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定觸發條件的 .NET 類型。

[GroupBy 之 SelectionCondition 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-groupby-format.md)指定觸發條件的 .NET 類型。 此元素是在定義新物件群組的顯示方式時使用。

[ListControl 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)指定觸發條件的 .NET 類型。 當此類型存在時，會使用清單專案。

[TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)指定觸發條件的 .NET 類型。 當此型別存在時，就會符合條件，並使用資料表資料列。

[WideEntry 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)指定觸發條件的 .NET 類型。 當此型別存在時，就會使用定義。

[類型的 TypeName 元素（格式）](./typename-element-for-types-format.md)指定屬於選取集之物件的 .NET 類型。

[ViewSelectedBy 的 TypeName 元素（格式）](./typename-element-for-viewselectedby-format.md)指定由視圖顯示的 .NET 物件。

[Types 元素（格式）](./types-element-for-selectionset-format.md)定義選取集中的 .NET 物件。

[View 元素（格式）](./view-element-format.md)定義用來顯示一個或多個 .NET 物件的視圖。

[ViewDefinitions 元素（格式）](./viewdefinitions-element-format.md)定義用來顯示物件的視圖。

[ViewSelectedBy 元素（格式）](./viewselectedby-element-format.md)定義視圖所顯示的 .NET 物件。

[WideControl 元素（格式）](./widecontrol-element-format.md)定義視圖的寬（單一值）清單格式。 此視圖會顯示每個物件的單一屬性值或腳本值。

[WideEntries 元素（格式）](./wideentries-element-for-widecontrol-format.md)提供寬視圖的定義。 寬視圖必須指定一或多個定義。

[WideEntry 元素（格式）](./wideentry-element-for-widecontrol-format.md)提供寬視圖的定義。

[之 wideitem 元素（格式）](./wideitem-element-for-widecontrol-format.md)定義顯示其值的屬性或腳本。

[Width 元素（格式）](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)定義資料行的寬度（以字元為單位）。

[Wrap 元素（格式）](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)指定超過欄寬度的文字會顯示在下一行。

[WrapTables 元素（格式）](./wraptables-element-format.md)指定如果資料的長度超過資料行的寬度，則會將資料表單元格中的資料移至下一行。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
