---
ms.date: 09/13/2016
ms.topic: reference
title: 格式結構描述 XML 參考
description: 格式結構描述 XML 參考
ms.openlocfilehash: f59016df91fe458393655853b9eada0875a8dcb1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667924"
---
# <a name="format-schema-xml-reference"></a>格式結構描述 XML 參考

本節中的主題描述格式化檔案 ( # B0 XML 檔案) 所使用的 XML 元素。 格式化檔案會定義 .NET 物件的顯示方式;它們不會變更物件本身。

## <a name="in-this-section"></a>本節內容

適用于[TableControl 的之 tablecolumnheader 的對齊元素 (格式) ](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)定義如何顯示資料行標題中的資料。

適用于[TableControl 的之 tablecolumnitem 的對齊元素 (格式) ](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)定義如何顯示資料列中的資料。

[TableControl (格式的 AutoSize 元素) ](./autosize-element-for-tablecontrol-format.md) 指定是否根據資料的大小調整資料行大小和資料行數目。

[WideControl (格式的 Autosize 元素) ](./autosize-element-for-widecontrol-format.md) 指定是否根據資料的大小調整資料行大小和資料行數目。

[WideControl (格式的 ColumnNumber 元素) ](./columnnumber-element-for-widecontrol-format.md) 指定以寬視圖顯示的資料行數目。

[Configuration 元素 (格式) ](./configuration-element-format.md) 代表格式化檔案的最上層元素。

[Configuration (格式之控制項的控制項元素) ](./control-element-for-controls-for-configuration-format.md) 定義通用控制項，可供格式化檔案的所有視圖和用來參考控制項的名稱使用。

[View (格式之控制項的控制項元素) ](./control-element-for-controls-for-view-format.md) 定義可供視圖使用的控制項，以及用來參考控制項的名稱。

[Configuration (格式的 Controls 元素) ](./controls-element-for-configuration-format.md) 定義可供格式化檔案的所有視圖使用的通用控制項。

[View (Format 的 Controls 元素) ](./controls-element-for-view-format.md) 定義可供特定視圖使用的 view 控制項。

[CustomControl 元素，可控制設定 (格式) ](./customcontrol-element-for-control-for-controls-for-configuration-format.md) 定義控制項。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[CustomControl 元素，可控制 View (格式的控制項) ](./customcontrol-element-for-control-for-controls-for-view-format.md) 定義視圖所使用的控制項。

[GroupBy (格式的 CustomControl 元素) ](./customcontrol-element-for-groupby-format.md) 定義顯示新群組的自訂控制項。

[CustomControl 元素 (格式) ](./customcontrol-element-for-groupby-format.md) 定義視圖的自訂控制項格式。

[設定 (格式之控制項的 ExpressionBinding 的 CustomControlName 元素) ](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) 指定通用控制項的名稱。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 ExpressionBindine 的 CustomControlName 元素) ](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) 指定通用控制項或 view 控制項的名稱。 當定義可供視圖使用的控制項時，會使用這個元素。

[GroupBy (格式的 CustomControlName 元素) ](./customcontrolname-element-for-groupby-format.md) 指定用來顯示新群組的自訂控制項名稱。 定義資料表、清單、寬或自訂控制項時，會使用這個元素。

[設定 (格式之控制項的 CustomControl 的 CustomEntry 元素) ](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) 提供通用控制項的定義。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 CustomEntries 的 CustomEntry 元素) ](./customentry-element-for-customentries-for-controls-for-view-format.md) 提供控制項的定義。 當定義可供視圖使用的控制項時，會使用這個元素。

適用[于 CustomEntries 的 CustomEntry 元素 (格式) ](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)提供自訂控制項視圖的定義。

[GroupBy (格式之 CustomControl 的 CustomEntry 元素) ](./customentry-element-for-customcontrol-for-groupby-format.md) 提供控制項的定義。 定義如何顯示新的物件群組時，會使用這個元素。

適用于[CustomControl 的 CustomEntries 元素，適用于 Configuration (格式) ](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)提供通用控制項的定義。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 CustomControl 的 CustomEntries 元素) ](./customentries-element-for-customcontrol-for-controls-for-view-format.md) 提供控制項的定義。 當定義可供視圖使用的控制項時，會使用這個元素。

[GroupBy (格式之 CustomControl 的 CustomEntries 元素) ](./customentries-element-for-customcontrol-for-groupby-format.md) 提供控制項的定義。 定義如何顯示新的物件群組時，會使用這個元素。

適用[于 CustomControl 的 CustomEntries 元素 (格式) ](./customentries-element-for-customcontrol-for-view-format.md)提供自訂控制項視圖的定義。 自訂控制項視圖必須指定一或多個定義。

適用于設定之[控制項的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)定義控制項顯示的資料以及其顯示方式。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 CustomEntry 的 CustomItem 元素) ](./customitem-element-for-customentry-for-controls-for-view-format.md) 定義控制項顯示的資料以及其顯示方式。 當定義可供視圖使用的控制項時，會使用這個元素。

適用[于 CustomEntry 的 CustomItem 元素 (格式) ](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)定義自訂控制項視圖所顯示的資料，以及其顯示方式。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式之 CustomEntry 的 CustomItem 元素) ](./customitem-element-for-customentry-for-groupby-format.md) 定義自訂控制項視圖所顯示的資料，以及其顯示方式。 定義如何顯示新的物件群組時，會使用這個元素。

[DefaultSettings 元素 (格式) ](./defaultsettings-element-format.md) 定義適用于格式檔案所有視圖的一般設定。 一般設定包括顯示錯誤、在資料表中包裝文字、定義集合的擴充方式等等。

[DisplayError 元素 (格式) ](./displayerror-element-format.md) 指定在顯示資料的錯誤發生時，顯示 #ERR 的字串。

[設定 (格式之控制項的 CustomEntry 的之 entryselectedby 元素) ](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) 定義 .NET 型別，這些型別會使用通用控制項的定義或必須存在才能使用此控制項的條件。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 CustomEntry 的之 entryselectedby 元素) ](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) 定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。 當定義可供視圖使用的控制項時，會使用這個元素。

適用[于 CustomEntry 的之 entryselectedby 元素 (格式) ](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)定義使用此自訂專案的 .NET 型別，或必須存在才能使用此專案的條件。

[EnumerableExpansion (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-enumerableexpansion-format.md) 定義使用此定義的 .NET 類型或必須存在的條件，才能使用這個定義。

[GroupBy (格式之 CustomEntry 的之 entryselectedby 元素) ](./entryselectedby-element-for-customentry-for-groupby-format.md) 定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。 定義如何顯示新的物件群組時，會使用這個元素。

適用于[ListEntry 的 ListControl (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-listentry-for-listcontrol-format.md)定義使用此清單視圖定義或必須存在才能使用此定義之條件的 .NET 類型。 在大部分情況下，清單視圖只需要一個定義。 但是，如果您想要使用相同的清單視圖來顯示不同物件的不同資料，則可以為清單視圖提供多個定義。

[TableRowEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 定義其屬性值會顯示在資料列中的 .NET 類型。

[WideEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-wideentry-format.md) 定義 .NET 型別，這些型別會使用此寬視圖的定義或必須存在的條件，才能使用這個定義。

[EnumerableExpansion 元素 (格式) ](./enumerableexpansion-element-format.md) 定義當特定 .NET 集合物件顯示在視圖中時，如何展開這些物件。

[EnumerableExpansions 元素 (格式) ](./enumerableexpansions-element-format.md) 定義當 .NET 集合物件顯示在視圖中時，如何展開這些物件。

[設定 (格式之控制項的 ExpressionBinding 的 EnumerateCollection 元素) ](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) 指定控制項會顯示集合的元素。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 ExpressionBinding 的 EnumerateCollection 元素) ](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) 指定會顯示集合的元素。 當定義可供視圖使用的控制項時，會使用這個元素。

適用于 CustomControl 之 EnumerateCollection 運算式系結的[元素 (格式) ](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)指定要顯示集合的元素。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式之 ExpressionBinding 的 EnumerateCollection 元素) ](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) 指定要顯示集合的元素。 定義如何顯示新的物件群組時，會使用這個元素。

[展開元素 (格式) ](./expand-element-format.md) 指定如何針對此定義展開集合物件。

[設定 (格式之控制項的 CustomItem 的 ExpressionBinding 元素) ](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) 定義控制項所顯示的資料。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 CustomItem 的 ExpressionBinding 元素) ](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) 定義控制項所顯示的資料。 當定義可供視圖使用的控制項時，會使用這個元素。

適用于[CustomControl 的 CustomItem ExpressionBinding 元素 (格式) ](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)定義控制項所顯示的資料。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式之 CustomItem 的 ExpressionBinding 元素) ](./expressionbinding-element-for-customitem-for-groupby-format.md) 定義控制項所顯示的資料。 定義如何顯示新的物件群組時，會使用這個元素。

[設定 (格式之控制項的框架的 FirstLineHanging 元素) ](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) 指定將第一行資料向左移動的字元數。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項框架的 FirstLineHanging 元素) ](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) 指定將第一行資料向左移動的字元數。 當定義可供視圖使用的控制項時，會使用這個元素。

適用于[CustomControl (格式之框架的 FirstLineHanging 元素) ](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)指定將第一行資料向左移動的字元數。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式之框架的 FirstLineHanging 元素) ](./firstlinehanging-element-for-frame-for-groupby-format.md) 指定將第一行資料向左移動的字元數。 定義如何顯示新的物件群組時，會使用這個元素。

[設定 (格式之控制項的框架的 FirstLineIndent 元素) ](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) 指定第一行資料向右移動的字元數。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項框架的 FirstLineIndent 元素) ](./firstlineindent-element-for-frame-for-controls-for-view-format.md) 指定第一行資料向右移動的字元數。 當定義可供視圖使用的控制項時，會使用這個元素。

[FirstLineIndent 元素](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 指定第一行資料向右移動的字元數。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式之框架的 FirstLineIndent 元素) ](./firstlineindent-element-for-frame-for-groupby-format.md) 指定第一行資料向右移動的字元數。 定義如何顯示新的物件群組時，會使用這個元素。

專案[的格式字串專案 (格式) ](./formatstring-element-for-listitem-for-listcontrol-format.md)指定定義屬性或腳本值顯示方式的格式模式。

[之 tablecolumnitem (格式的格式字串元素) ](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) 指定格式模式，定義資料表的屬性或腳本值的顯示方式。

適用于[WideControl (格式的之 wideitem 格式格式元素) ](./formatstring-element-for-wideitem-for-widecontrol-format.md)指定格式模式，定義屬性或腳本值在視圖中的顯示方式。

[設定 (格式之控制項的 CustomItem 的框架元素) ](./frame-element-for-customitem-for-controls-for-configuration-format.md) 定義顯示資料的方式，例如將資料向左或向右移動。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 CustomItem 的框架元素) ](./frame-element-for-customitem-for-controls-for-view-format.md) 定義顯示資料的方式，例如將資料向左或向右移動。 當定義可供視圖使用的控制項時，會使用這個元素。

適用于[CustomControl 的 CustomItem 的框架元素 (格式) ](./frame-element-for-customitem-for-customcontrol-for-view-format.md)定義顯示資料的方式，例如將資料向左或向右移動。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式的 CustomItem 的框架元素) ](./frame-element-for-customitem-for-groupby-format.md) 定義顯示資料的方式，例如將資料向左或向右移動。 定義如何顯示新的物件群組時，會使用這個元素。

[View (格式的 GroupBy 元素) ](./groupby-element-for-view-format.md) 定義 Windows PowerShell 如何顯示新的物件群組。

[HideTableHeaders 元素 (格式) ](./hidetableheaders-element-format.md) 指定不顯示資料表的標頭。

[設定 (格式之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素) ](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) 定義必須存在才能使用此控制項的條件。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (Format) 的控制項之 ExpressionBinding 元素 ItemSelectionCondition ](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) 定義必須存在才能使用此控制項的條件。 當定義可供視圖使用的控制項時，會使用這個元素。

適用于 CustomControl 之 ItemSelectionCondition 運算式系結的[元素 (格式) ](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)定義必須存在才能使用此控制項的條件。 可以針對控制項專案指定的選取條件數目沒有任何限制。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式之 ExpressionBinding 的 ItemSelectionCondition 元素) ](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) 定義必須存在才能使用此控制項的條件。 可以針對控制項專案指定的選取條件數目沒有任何限制。 定義如何顯示新的物件群組時，會使用這個元素。

專案[ (格式) 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)定義必須存在才能使用此清單專案的條件。

[ListControl (格式之專案的標籤元素) ](./label-element-for-listitem-for-listcontrol-format.md) 指定資料列中屬性或腳本值的標籤。

[GroupBy (格式的 Label 元素) ](./label-element-for-groupby-format.md) 指定當遇到新群組時所顯示的標籤。

[之 tablecolumnheader (格式的標籤元素) ](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) 定義顯示在資料行頂端的標籤。

[設定 (格式之控制項的框架的 LeftIndent 元素) ](./leftindent-element-for-frame-for-controls-for-configuration-format.md) 指定資料從左邊界向外移動的字元數。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項框架的 LeftIndent 元素) ](./leftindent-element-for-frame-for-controls-for-view-format.md) 指定資料從左邊界向外移動的字元數。 當定義可供視圖使用的控制項時，會使用這個元素。

適用于[CustomControl (格式之框架的 LeftIndent 元素) ](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)指定資料從左邊界向外移動的字元數。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式之框架的 LeftIndent 元素) ](./leftindent-element-for-frame-for-groupby-format.md) 指定資料從左邊界向外移動的字元數。 定義如何顯示新的物件群組時，會使用這個元素。

[ListControl 元素 (格式) ](./listcontrol-element-format.md) 定義視圖的清單格式。

[ListEntry 元素 (格式) ](./listentry-element-for-listcontrol-format.md) 提供清單視圖的定義。

[ListEntries 元素 (格式) ](./listentries-element-for-listcontrol-format.md) 定義如何顯示清單視圖的資料列。

[ (格式) ](./listitem-element-for-listitems-for-listcontrol-format.md) 的 [專案] 元素定義屬性或腳本，其值會顯示在清單視圖的資料列中。

[ListItems 元素 (格式) ](./listitems-element-for-listentry-for-listcontrol-format.md) 定義顯示在清單視圖中的屬性和腳本。

[Configuration (格式之控制項的控制項的名稱元素) ](./name-element-for-control-for-controls-for-configuration-format.md) 指定控制項的名稱。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[SelectionSet (格式的 Name 元素) ](./name-element-for-selectionset-format.md) 指定用來參考選取集的名稱。

[View (Format 的 Name 元素) ](./name-element-for-view-format.md) 指定用來識別視圖的名稱。

[CustomItem 設定 (格式之控制項的新行元素) ](./newline-element-for-customitem-for-controls-for-configuration-format.md) 在控制項的顯示中加入空白行。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 CustomItem 的分行符號元素) ](./newline-element-for-customitem-for-controls-for-view-format.md) 在控制項的顯示中加入空白行。 當定義可供視圖使用的控制項時，會使用這個元素。

適用于[CustomControl 的 CustomItem 的分行符號元素 (格式) ](./newline-element-for-customitem-for-customcontrol-for-view-format.md)在控制項的顯示中加入空白行。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式的 CustomItem 的分行符號元素) ](./newline-element-for-customitem-for-groupby-format.md) 在控制項的顯示中加入空白行。 定義如何顯示新的物件群組時，會使用這個元素。

[ (格式之控制項的 ExpressionBinding 的 PropertyName 元素) ](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) 指定由通用控制項顯示其值的 .NET 屬性。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 ExpressionBinding 的 PropertyName 元素) ](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) 指定控制項顯示其值的 .NET 屬性。 當定義可供視圖使用的控制項時，會使用這個元素。

[View (格式之 CustomControl 的 ExpressionBinding 的 PropertyName 元素) ](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) 指定控制項顯示其值的 .NET 屬性。 定義自訂控制項視圖時，會使用這個元素

[GroupBy (格式的 ExpressionBinding 的 PropertyName 元素) ](./propertyname-element-for-expressionbinding-for-groupby-format.md) 指定控制項顯示其值的 .NET 屬性。 定義如何顯示新的物件群組時，會使用這個元素。

[GroupBy (格式的 PropertyName 元素) ](./propertyname-element-for-groupby-format.md) 指定每當新群組值變更時，會啟動新群組的 .NET 屬性。

[ (格式之控制項的 itemselectioncondition 的 PropertyName 元素) ](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) 指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時，就 `true` 會符合條件，並且會使用控制項。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 ItemSelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) 指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時，就 `true` 會符合條件，並且會使用控制項。 當定義可供視圖使用的控制項時，會使用這個元素。

[View (格式之 CustomControl 的 ItemSelectionCondition 的 PropertyName 元素](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) 指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時，就 `true` 會符合條件，並且會使用控制項。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式的 ItemSelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) 指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時，就 `true` 會符合條件，並且會使用控制項。 定義如何顯示新的物件群組時，會使用這個元素。

專案[名稱的 ItemSelectionCondition 的 PropertyName 元素 (格式) ](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時， `true` 就會符合條件，並使用 view。 定義清單視圖時，會使用這個元素。

[ListControl (格式的專案名稱名稱元素) ](./propertyname-element-for-listitem-for-listcontrol-format.md) 指定其值會顯示在清單中的 .NET 屬性。

[ListEntry (格式之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) 指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時， `true` 就會符合條件，並且會使用此專案。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 SelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) 指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時， `true` 就會符合條件，並且會使用此專案。 當定義可供視圖使用的控制項時，會使用這個元素。

[View (格式之 CustomControl 的 SelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) 指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時， `true` 就會符合條件，並使用定義。 定義自訂控制項視圖時，會使用這個元素。

[EnumerableExpansion (格式之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) 指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時， `true` 就會符合條件，並使用定義。

[GroupBy (格式的 SelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-selectioncondition-for-groupby-format.md) 指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時， `true` 就會符合條件，並使用定義。 定義如何顯示新的物件群組時，會使用這個元素。

[ListEntry (格式之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) 指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時，就 `true` 會符合條件，並且會使用清單專案。

[TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) 指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時，就 `true` 會符合條件，並且會使用資料表專案。

[WideEntry (格式之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) 指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時， `true` 就會符合條件，並使用定義。

[之 tablecolumnitem (格式的 PropertyName 元素) ](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) 指定其值會顯示在資料列的資料行中的屬性。

[之 wideitem (格式的 PropertyName 元素) ](./propertyname-element-for-wideitem-for-widecontrol-format.md) 指定物件的屬性，其值會顯示在寬視圖中。

[設定 (格式之控制項的框架的 RightIndent 元素) ](./rightindent-element-for-frame-for-controls-for-configuration-format.md) 指定資料從右邊界向外移動的字元數。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項框架的 RightIndent 元素) ](./rightindent-element-for-frame-for-controls-for-view-format.md) 指定資料從右邊界向外移動的字元數。 當定義可供視圖使用的控制項時，會使用這個元素。

[RightIndent 元素](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) 指定資料從右邊界向外移動的字元數。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式之框架的 RightIndent 元素) ](./rightindent-element-for-frame-for-groupby-format.md) 指定資料從右邊界向外移動的字元數。 定義如何顯示新的物件群組時，會使用這個元素。

[設定 (格式之控制項的 ExpressionBinding 的 ScriptBlock 元素) ](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) 指定由通用控制項顯示其值的腳本。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 ExpressionBinding 的 ScriptBlock 元素) ](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) 指定控制項顯示其值的腳本。 當定義可供視圖使用的控制項時，會使用這個元素。

[ExpressionBinding For CustomCustomControl For View (格式的 ScriptBlock 元素) ](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) 指定控制項顯示其值的腳本。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式的 ExpressionBinding 的 ScriptBlock 元素) ](./scriptblock-element-for-expressionbinding-for-groupby-format.md) 指定控制項顯示其值的腳本。 定義如何顯示新的物件群組時，會使用這個元素。

[GroupBy (格式的 ScriptBlock 元素) ](./scriptblock-element-for-groupby-format.md) 指定每當新群組值變更時，會啟動新群組的腳本。

[設定 (格式之控制項的 ItemSelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) 指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並且會使用控制項。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 ItemSelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) 指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並且會使用控制項。 當定義可供視圖使用的控制項時，會使用這個元素。

[ItemSelectionCondition For CustomControl For View (格式的 ScriptBlock 元素) ](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) 指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並且會使用控制項。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式的 ItemSelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) 指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並且會使用控制項。 定義如何顯示新的物件群組時，會使用這個元素。

適用于[ListControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式) ](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並且會使用清單專案。 定義清單視圖時，會使用這個元素。

專案專案[的 ScriptBlock 元素 (格式) ](./scriptblock-element-for-listitem-for-listcontrol-format.md)指定其值顯示在清單資料列中的腳本。

[設定 (格式之控制項的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) 指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並使用定義。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) 指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並使用定義。 當定義可供視圖使用的控制項時，會使用這個元素。

[SelectionCondition For CustomControl For View (格式的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) 指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並使用定義。 定義自訂控制項視圖時，會使用這個元素。

適用于[EnumerableExpansion (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定觸發條件的腳本。

[GroupBy (格式的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) 指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並使用定義。 定義如何顯示新的物件群組時，會使用這個元素。

適用于[ListEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並且會使用清單專案。

適用于[TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)指定觸發條件的腳本區塊。 當此腳本評估為時 `true` ，就會符合條件，並且會使用資料表專案。

適用于[WideEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並且會使用寬專案定義。

[之 tablecolumnitem (格式的 ScriptBlock 元素) ](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) 指定其值會顯示在資料列的資料行中的腳本。

[之 wideitem (格式的 ScriptBlock 元素) ](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 指定以寬視圖顯示其值的腳本。

適用于[CustomEntry 之之 entryselectedby 的 SelectionCondition 元素 (格式設定格式) ](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)定義必須存在才能使用通用控制項定義的條件。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的之 entryselectedby 的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) 定義必須存在才能使用控制項定義的條件。 當定義可供視圖使用的控制項時，會使用這個元素。

適用于[CustomControl 的之 entryselectedby SelectionCondition 元素 (格式) ](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)定義必須存在才能使用控制項定義的條件。 定義自訂控制項視圖時，會使用這個元素。

適用于[之 entryselectedby 的 EnumerableExpansion (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)定義必須存在才能展開這個定義之集合物件的條件。

[GroupBy (格式之之 entryselectedby 的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) 定義必須存在才能使用控制項定義的條件。 定義如何顯示新的物件群組時，會使用這個元素。

適用于[之 entryselectedby 的 ListEntry (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)定義必須存在的條件，才能使用此清單視圖的定義。 可以針對清單定義指定的選取條件數目沒有任何限制。

適用于[之 entryselectedby 的 TableRowEntry (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)定義必須存在的條件，才能用於此資料表視圖的定義。 可以針對資料表定義指定的選取條件數目沒有任何限制。

適用于[之 entryselectedby 的 WideEntry (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)定義必須存在的條件，才能使用這個定義。 可以針對寬專案定義指定的選取條件數目沒有任何限制。

[SelectionSet 元素 (格式) ](./selectionset-element-format.md) 定義一組可由集合名稱參考的 .NET 物件。

[設定 (格式之控制項的之 entryselectedby 的 SelectionSetName 元素) ](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) 指定一組使用此控制項定義的 .NET 類型。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的之 entryselectedby 的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) 指定一組使用此控制項定義的 .NET 類型。 當定義可供視圖使用的控制項時，會使用這個元素。

適用于[之 entryselectedby 的 CustomEntry (格式的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)指定清單專案的一組 .NET 物件。 可以針對專案指定的選取範圍數目沒有任何限制。

適用于[之 entryselectedby 的 EnumerableExpansion (格式的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)指定由這個定義擴充的 .NET 類型集合。

[GroupBy (格式之之 entryselectedby 的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) 指定清單專案的一組 .NET 物件。 可以針對專案指定的選取範圍數目沒有任何限制。 定義如何顯示新的物件群組時，會使用這個元素。

適用于[之 entryselectedby 的 ListEntry (格式的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)指定清單專案的一組 .NET 物件。 可以針對專案指定的選取範圍數目沒有任何限制。

適用于[之 entryselectedby 的 TableRowEntry (格式的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)指定使用此資料表視圖專案的一組 .NET 類型。 可以針對專案指定的選取範圍數目沒有任何限制。

適用于[之 entryselectedby 的 WideEntry (格式的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)指定定義的一組 .NET 物件。 每當顯示這些物件的其中一個時，就會使用定義。

[設定 (格式之控制項的 SelectionCondition 的 SelectionSetName 元素) ](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) 指定一組觸發條件的 .NET 類型。 當這個集合中的任何型別存在時，就會符合條件，並使用此控制項來顯示該物件。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 SelectionCondition 的 SelectionSetName 元素) ](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) 指定一組觸發條件的 .NET 類型。 當這個集合中的任何類型存在時，就會符合條件，並使用此控制項來顯示該物件。 當定義可供視圖使用的控制項時，會使用這個元素。

適用[于 CustomEntry 的之 entryselectedby 元素 (格式) ](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)指定一組觸發條件的 .NET 類型。 當這個集合中的任何類型存在時，就會符合條件，並使用此控制項來顯示該物件。 定義自訂控制項視圖時，會使用這個元素。

適用于[EnumerableExpansion 的之 entryselectedby (格式的 SelectionCondition SelectionSetName 元素) ](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定一組觸發條件的 .NET 類型。 當此集合中的任何類型存在時，就會符合條件。

[GroupBy (格式之 SelectionCondition 的 SelectionSetName 元素) ](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) 指定一組觸發條件的 .NET 類型。 當這個集合中的任何型別存在時，就會符合條件，並使用此控制項來顯示該物件。 定義如何顯示新的物件群組時，會使用這個元素。

適用于[ListEntry 的之 entryselectedby (格式的 SelectionCondition SelectionSetName 元素) ](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)指定一組觸發條件的 .NET 類型。 當這個集合中的任何類型存在時，就會符合條件，並且使用清單視圖的這項定義來顯示該物件。

適用于[TableRowEntry 的之 entryselectedby (格式的 SelectionCondition SelectionSetName 元素) ](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)指定一組觸發條件的 .NET 類型。 當這個集合中的任何型別存在時，就會符合條件，並且會使用資料表視圖的這項定義來顯示該物件。

適用于[WideEntry 的之 entryselectedby (格式的 SelectionCondition SelectionSetName 元素) ](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)指定一組觸發條件的 .NET 類型。 當這個集合中的任何型別存在時，就會符合條件，而且會使用此寬視圖的定義來顯示該物件。

[ViewSelectedBy (格式的 SelectionSetName 元素) ](./selectionsetname-element-for-viewselectedby-format.md) 指定由視圖顯示的一組 .NET 物件。

[SelectionSets 元素 (格式) ](./selectionsets-element-format.md) 定義可供個別格式視圖使用的 .NET 物件集合。

[ShowError 元素 (格式) ](./showerror-element-format.md) 指定當顯示資料時，發生錯誤時，就會顯示完整的錯誤記錄。

適用于[TableHeaders 的 TableControl (格式的之 tablecolumnheader 元素) ](./tablecolumnheader-element-format.md)定義標籤、資料行的寬度，以及資料表資料行之標籤的對齊方式。

[之 tablecolumnitem 元素 (格式) ](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 定義其值會顯示在資料列的資料行中的屬性或腳本。

[TableColumnItems 元素 (格式) ](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) 定義其值會顯示在資料列中的屬性或腳本。

[TableControl 元素 (格式) ](./tablecontrol-element-format.md) 定義視圖的資料表格式。

[TableHeaders 元素 (格式) ](./tableheaders-element-format.md) 定義資料表之資料行的標頭。

[TableRowEntries 元素 (格式) ](./tablerowentries-element-for-tablecontrol-format.md) 定義資料表的資料列。

[TableRowEntry 元素 (格式) ](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) 定義顯示在資料表資料列中的資料。

[設定 (格式之控制項的 CustomItem 文字元素) ](./text-element-for-customitem-for-controls-for-configuration-format.md) 指定要加入至控制項所顯示之資料的文字，例如標籤、用來括住資料的括弧，以及用來縮排資料的空格。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 CustomItem 文字元素) ](./text-element-for-customitem-for-controls-for-view-format.md) 指定要加入至控制項所顯示之資料的文字，例如標籤、用來括住資料的括弧，以及用來縮排資料的空格。 當定義可供視圖使用的控制項時，會使用這個元素。

[CustomItem (格式的 Text 元素) ](./text-element-for-customitem-for-customview-for-view-format.md) 指定要加入至控制項所顯示之資料的文字，例如標籤、用來括住資料的括弧，以及用來縮排資料的空格。 定義自訂控制項視圖時，會使用這個元素。

[GroupBy (格式的 CustomItem 文字元素) ](./text-element-for-customitem-for-groupby-format.md) 指定要加入至控制項所顯示之資料的文字，例如標籤、用來括住資料的括弧，以及用來縮排資料的空格。 定義如何顯示新的物件群組時，會使用這個元素。

[Configuration (格式之控制項的之 entryselectedby 的 TypeName 元素) ](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) 指定使用此控制項定義的 .NET 類型。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的之 entryselectedby TypeName 元素) ](./typename-element-for-entryselectedby-for-controls-for-view-format.md) 指定使用此控制項定義的 .NET 類型。 當定義可供視圖使用的控制項時，會使用這個元素。

[View (格式之 CustomEntry 的之 entryselectedby 的 TypeName 元素) ](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) 指定使用自訂控制項視圖之定義的 .NET 類型。 可以針對定義指定的類型數目沒有任何限制。

[適用于 EnumerableExpansion 的之 entryselectedby 的 TypeName 元素 (格式) ](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) 指定由這個定義擴充的 .NET 型別。 定義預設設定時，會使用這個元素。

[GroupBy (格式的之 entryselectedby TypeName 元素) ](./typename-element-for-entryselectedby-for-groupby-format.md) 指定使用此自訂控制項定義的 .NET 類型。 定義如何顯示新的物件群組時，會使用這個元素。

[適用于 ListControl 的之 entryselectedby 的 TypeName 元素 (格式) ](./typename-element-for-entryselectedby-for-listcontrol-format.md) 指定使用此清單視圖專案的 .NET 型別。 可以針對清單專案指定的類型數目沒有任何限制。

[適用于 TableRowEntry 的之 entryselectedby 的 TypeName 元素 (格式) ](./typename-element-for-entryselectedby-for-tablecontrol-format.md) 指定使用此資料表視圖專案的 .NET 型別。 可以針對資料表專案指定的類型數目沒有任何限制。

[適用于 WideEntry 的之 entryselectedby 的 TypeName 元素 (格式) ](./typename-element-for-entryselectedby-for-wideentry-format.md) 指定定義的 .NET 類型。 只要顯示這個物件，就會使用定義。

[Configuration (格式之控制項的 SelectionCondition 的 TypeName 元素) ](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) 指定觸發條件的 .NET 型別。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

[View (格式之控制項的 SelectionCondition TypeName 元素) ](./typename-element-for-selectioncondition-for-controls-for-view-format.md) 指定觸發條件的 .NET 型別。 當定義可供視圖使用的控制項時，會使用這個元素。

[View (格式之 CustomControl 的 SelectionCondition 的 TypeName 元素) ](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) 指定觸發條件的 .NET 型別。 定義自訂控制項視圖時，會使用這個元素。

[EnumerableExpansion (格式之之 entryselectedby 的 SelectionCondition 的 TypeName 元素) ](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) 指定觸發條件的 .NET 型別。

[GroupBy (格式的 SelectionCondition TypeName 元素) ](./typename-element-for-selectioncondition-for-groupby-format.md) 指定觸發條件的 .NET 型別。 定義如何顯示新的物件群組時，會使用這個元素。

[ListControl (格式之之 entryselectedby 的 SelectionCondition 的 TypeName 元素) ](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) 指定觸發條件的 .NET 型別。 當這個型別存在時，就會使用清單專案。

[TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 TypeName 元素) ](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) 指定觸發條件的 .NET 型別。 當此類型存在時，就會符合條件，並且會使用資料表資料列。

[WideEntry (格式之之 entryselectedby 的 SelectionCondition 的 TypeName 元素) ](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) 指定觸發條件的 .NET 型別。 當這個型別存在時，就會使用定義。

[類型 (格式的 TypeName 元素) ](./typename-element-for-types-format.md) 指定屬於選取集之物件的 .NET 類型。

[ViewSelectedBy (格式的 TypeName 元素) ](./typename-element-for-viewselectedby-format.md) 指定由視圖顯示的 .NET 物件。

[類型元素 (格式) ](./types-element-for-selectionset-format.md) 定義選取專案集中的 .NET 物件。

[View 元素 (格式) ](./view-element-format.md) 定義用來顯示一或多個 .NET 物件的視圖。

[ViewDefinitions 元素 (格式) ](./viewdefinitions-element-format.md) 定義用來顯示物件的視圖。

[ViewSelectedBy 元素 (格式) ](./viewselectedby-element-format.md) 定義由視圖顯示的 .NET 物件。

[WideControl 元素 (格式) ](./widecontrol-element-format.md) 為視圖定義寬 (單一值) 清單格式。 這個視圖會顯示每個物件的單一屬性值或腳本值。

[WideEntries 元素 (格式) ](./wideentries-element-for-widecontrol-format.md) 提供寬視圖的定義。 寬型視圖必須指定一或多個定義。

[WideEntry 元素 (格式) ](./wideentry-element-for-widecontrol-format.md) 提供寬視圖的定義。

[之 wideitem 元素 (格式) ](./wideitem-element-for-widecontrol-format.md) 定義顯示其值的屬性或腳本。

[寬度元素 (格式) ](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) 定義資料行) 字元 (的寬度。

[Wrap 元素 (格式) ](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) 指定在下一行顯示超過欄寬度的文字。

[WrapTables 元素 (格式) ](./wraptables-element-format.md) 指定當資料的長度超過資料行的寬度時，資料表資料格中的資料會移至下一行。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
