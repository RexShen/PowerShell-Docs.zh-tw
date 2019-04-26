---
title: 格式化 XML 的結構描述參考 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 437b3d6bb62fdd3a74f3392ec71df360c01a1974
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065779"
---
# <a name="format-schema-xml-reference"></a>格式結構描述 XML 參考

在本節中的主題描述使用格式檔案 （Format.ps1xml 檔案） 的 XML 項目。 格式檔案會定義.NET 物件的顯示方式;不會變更物件本身。

## <a name="in-this-section"></a>在本節中

[TableControl （格式） 的 TableColumnHeader 對齊項目](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)定義的資料行標頭中的資料的顯示方式。

[TableControl （格式） 的 TableColumnItem 對齊項目](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)定義資料列中的顯示方式。

[TableControl （格式） 的自動調整項目](./autosize-element-for-tablecontrol-format.md)指定是否會調整欄大小和資料行數目為基礎的資料大小。

[Autosize WideControl （格式） 的項目](./autosize-element-for-widecontrol-format.md)指定是否會調整欄大小和資料行數目為基礎的資料大小。

[ColumnNumber WideControl （格式） 的項目](./columnnumber-element-for-widecontrol-format.md)指定寬型檢視中顯示的資料行數目。

[組態項目 （格式）](./configuration-element-format.md)表示的格式化檔案的最上層項目。

[Control 項目組態 （格式） 的控制項](./control-element-for-controls-for-configuration-format.md)定義可用的格式化檔案以及用來參考的控制項名稱的所有檢視通用控制項。

[控制控制項的檢視 （格式） 的項目](./control-element-for-controls-for-view-format.md)定義可供檢視和名稱，用來參考控制項的控制項。

[控制組態 （格式） 的元素](./controls-element-for-configuration-format.md)定義可用的格式化檔案的所有檢視通用控制項。

[檢視 （格式） 的項目會控制](./controls-element-for-view-format.md)定義可供特定檢視的檢視控制項。

[CustomControl 組態 （格式） 的控制項的項目](./customcontrol-element-for-control-for-controls-for-configuration-format.md)定義的控制項。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項的控制項 CustomControl 元素](./customcontrol-element-for-control-for-controls-for-view-format.md)定義控制項，以供檢視。

[CustomControl GroupBy （格式） 的項目](./customcontrol-element-for-groupby-format.md)定義自訂控制，則會顯示新的群組。

[CustomControl 項目 （格式）](./customcontrol-element-for-groupby-format.md)定義檢視的自訂控制項格式。

[CustomControlName ExpressionBinding 組態 （格式） 的控制項的項目](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)指定通用控制項的名稱。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 ExpressionBindine CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)指定通用控制項的檢視控制項的名稱。 定義可供檢視的控制項時，會使用這個項目。

[CustomControlName 的 GroupBy （格式） 的項目](./customcontrolname-element-for-groupby-format.md)指定自訂控制項是用來顯示新的群組的名稱。 定義資料表、 清單、 寬或自訂的控制項檢視時，會使用這個項目。

[CustomEntry CustomControl 組態 （格式） 的控制項的項目](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)提供通用控制項的定義。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-controls-for-view-format.md)提供控制項的定義。 定義可供檢視的控制項時，會使用這個項目。

[CustomEntry CustomEntries 檢視 （格式） 的項目](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)提供自訂的控制項檢視的定義。

[GroupBy （格式） 的 CustomControl CustomEntry 元素](./customentry-element-for-customcontrol-for-groupby-format.md)提供控制項的定義。 定義新的群組物件的顯示方式時，會使用這個項目。

[CustomEntries CustomControl 組態 （格式） 的項目](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)提供通用控制項的定義。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-controls-for-view-format.md)提供控制項的定義。 定義可供檢視的控制項時，會使用這個項目。

[GroupBy （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-groupby-format.md)提供控制項的定義。 定義新的群組物件的顯示方式時，會使用這個項目。

[CustomEntries CustomControl 檢視 （格式） 的項目](./customentries-element-for-customcontrol-for-view-format.md)提供自訂的控制項檢視的定義。 自訂控制項的檢視必須指定一個或多個定義。

[組態控制項 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)定義控制項所顯示的資料和顯示方式。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-view-format.md)定義控制項所顯示的資料和顯示方式。 定義可供檢視的控制項時，會使用這個項目。

[CustomItem CustomEntry 檢視 （格式） 的項目](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)定義自訂的控制項檢視所顯示的資料和顯示方式。 定義自訂控制項的檢視時，會使用這個項目。

[GroupBy （格式） 的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-groupby-format.md)定義自訂的控制項檢視所顯示的資料和顯示方式。 定義新的群組物件的顯示方式時，會使用這個項目。

[DefaultSettings 項目 （格式）](./defaultsettings-element-format.md)定義套用至的格式化檔案的所有檢視的一般設定。 一般設定包括顯示錯誤，定義集合展開的資料表中的文字換行。

[DisplayError 項目 （格式）](./displayerror-element-format.md)指定字串 #ERR 顯示一段資料時，發生錯誤時顯示。

[EntrySelectedBy CustomEntry 組態 （格式） 的控制項的項目](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)定義使用的通用控制項或條件必須存在於要使用這個控制項定義的.NET 類型。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。 定義可供檢視的控制項時，會使用這個項目。

[EntrySelectedBy CustomEntry 檢視 （格式） 的項目](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)定義使用此自訂的項目或條件必須為要使用此項目存在於.NET 型別。

[EntrySelectedBy EnumerableExpansion （格式） 的項目](./entryselectedby-element-for-enumerableexpansion-format.md)定義.NET 類型使用這個定義或必須存在於要使用此定義的條件。

[GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-groupby-format.md)定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。 定義新的群組物件的顯示方式時，會使用這個項目。

[ListControl （格式） 的 ListEntry EntrySelectedBy 元素](./entryselectedby-element-for-listentry-for-listcontrol-format.md)定義使用此清單檢視定義或必須存在於要使用此定義條件的.NET 類型。 在大部分情況下只有一個定義所需的清單檢視。 不過，您可以提供多個定義清單檢視，如果您想要使用相同的清單檢視來顯示不同的資料，針對不同物件中。

[EntrySelectedBy TableRowEntry （格式） 的項目](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)定義其屬性值會顯示資料列中的.NET 型別。

[EntrySelectedBy WideEntry （格式） 的項目](./entryselectedby-element-for-wideentry-format.md)定義使用此定義的寬型檢視或條件必須存在於要使用此定義的.NET 類型。

[EnumerableExpansion 項目 （格式）](./enumerableexpansion-element-format.md)定義在檢視中顯示時，會展開物件的特定.NET 集合。

[EnumerableExpansions 項目 （格式）](./enumerableexpansions-element-format.md)定義在檢視中顯示時，如何展開.NET 集合物件。

[EnumerateCollection ExpressionBinding 組態 （格式） 的控制項的項目](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)指定集合的項目會顯示控制項。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 ExpressionBinding EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)指定集合的項目會顯示。 定義可供檢視的控制項時，會使用這個項目。

[運算式繫結的檢視 （格式） 的 CustomControl EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)指定集合的項目會顯示。 定義自訂控制項的檢視時，會使用這個項目。

[EnumerateCollection ExpressionBinding 的 GroupBy （格式） 的項目](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)指定集合的項目會顯示。 定義新的群組物件的顯示方式時，會使用這個項目。

[展開項目 （格式）](./expand-element-format.md)指定如何展開此定義的集合物件。

[ExpressionBinding CustomItem 組態 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)定義控制項所顯示的資料。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)定義控制項所顯示的資料。 定義可供檢視的控制項時，會使用這個項目。

[ExpressionBinding 元素 CustomControl 檢視 （格式） 的 CustomItem](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)定義控制項所顯示的資料。 定義自訂控制項的檢視時，會使用這個項目。

[GroupBy （格式） 的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-groupby-format.md)定義控制項所顯示的資料。 定義新的群組物件的顯示方式時，會使用這個項目。

[組態 （格式） 的控制項的畫面格 FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)指定資料的第一行向左移動的字元數。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[FirstLineHanging 框架的控制項的檢視元件 （格式）](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)指定資料的第一行向左移動的字元數。 定義可供檢視的控制項時，會使用這個項目。

[FirstLineHanging CustomControl 檢視 （格式） 的畫面格的項目](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)指定資料的第一行向左移動的字元數。 定義自訂控制項的檢視時，會使用這個項目。

[GroupBy （格式） 的畫面格 FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-groupby-format.md)指定資料的第一行向左移動的字元數。 定義新的群組物件的顯示方式時，會使用這個項目。

[組態 （格式） 的控制項的畫面格 FirstLineIndent 元素](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)指定資料的第一行向右移位的字元數。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[FirstLineIndent 框架的控制項的檢視元件 （格式）](./firstlineindent-element-for-frame-for-controls-for-view-format.md)指定資料的第一行向右移位的字元數。 定義可供檢視的控制項時，會使用這個項目。

[FirstLineIndent 元素](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)指定資料的第一行向右移位的字元數。 定義自訂控制項的檢視時，會使用這個項目。

[GroupBy （格式） 的畫面格 FirstLineIndent 元素](./firstlineindent-element-for-frame-for-groupby-format.md)指定資料的第一行向右移位的字元數。 定義新的群組物件的顯示方式時，會使用這個項目。

[ListItem （格式） 的 FormatString 元素](./formatstring-element-for-listitem-for-listcontrol-format.md)指定之格式模式所定義的屬性或指令碼的值的顯示方式。

[TableColumnItem （格式） 的 FormatString 元素](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)指定之格式模式所定義的屬性或指令碼的值之資料表的顯示方式。

[FormatString 元素 WideControl （格式） 的 WideItem](./formatstring-element-for-wideitem-for-widecontrol-format.md)指定之格式模式所定義的屬性或指令碼的值在檢視中的顯示方式。

[CustomItem 組態 （格式） 的控制項的畫面格元素](./frame-element-for-customitem-for-controls-for-configuration-format.md)定義資料的顯示方式，例如將資料轉移至左邊或右邊。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[CustomItem 用於檢視 （格式） 的控制項的畫面格元素](./frame-element-for-customitem-for-controls-for-view-format.md)定義資料的顯示方式，例如將資料轉移至左邊或右邊。 定義可供檢視的控制項時，會使用這個項目。

[框架 CustomItem CustomControl 檢視 （格式） 的項目](./frame-element-for-customitem-for-customcontrol-for-view-format.md)定義資料的顯示方式，例如將資料轉移至左邊或右邊。 定義自訂控制項的檢視時，會使用這個項目。

[框架 CustomItem GroupBy （格式） 的項目](./frame-element-for-customitem-for-groupby-format.md)定義資料的顯示方式，例如將資料轉移至左邊或右邊。 定義新的群組物件的顯示方式時，會使用這個項目。

[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)定義 Windows PowerShell 顯示新的一整組物件的方式。

[HideTableHeaders 項目 （格式）](./hidetableheaders-element-format.md)指定資料表的標頭不會顯示。

[ItemSelectionCondition ExpressionBinding 組態 （格式） 的控制項的項目](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)定義要使用這個控制項必須存在的條件。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)定義要使用這個控制項必須存在的條件。 定義可供檢視的控制項時，會使用這個項目。

[運算式繫結的檢視 （格式） 的 CustomControl ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)定義要使用這個控制項必須存在的條件。 沒有任何限制，選擇條件，您可以指定的控制項項目數目。 定義自訂控制項的檢視時，會使用這個項目。

[ItemSelectionCondition ExpressionBinding 的 GroupBy （格式） 的項目](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)定義要使用這個控制項必須存在的條件。 沒有任何限制，選擇條件，您可以指定的控制項項目數目。 定義新的群組物件的顯示方式時，會使用這個項目。

[ListItem （格式） 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)定義要使用此清單項目必須存在的條件。

[供 ListItem 標籤項目，如 ListControl(Format)](./label-element-for-listitem-for-listcontrol-format.md)資料列中指定的屬性或指令碼的值的標籤。

[GroupBy （格式） 供標籤項目](./label-element-for-groupby-format.md)指定會在遇到新的群組時所顯示的標籤。

[TableColumnHeader （格式） 供標籤項目](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)定義顯示在資料行頂端的標籤。

[組態 （格式） 的控制項的畫面格 LeftIndent 元素](./leftindent-element-for-frame-for-controls-for-configuration-format.md)指定的字元數的資料會移離左邊界。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[LeftIndent 框架的控制項的檢視元件 （格式）](./leftindent-element-for-frame-for-controls-for-view-format.md)指定的字元數的資料會移離左邊界。 定義可供檢視的控制項時，會使用這個項目。

[LeftIndent CustomControl 檢視 （格式） 的畫面格的項目](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)指定的字元數的資料會移離左邊界。 定義自訂控制項的檢視時，會使用這個項目。

[GroupBy （格式） 的畫面格 LeftIndent 元素](./leftindent-element-for-frame-for-groupby-format.md)指定的字元數的資料會移離左邊界。 定義新的群組物件的顯示方式時，會使用這個項目。

[ListControl 項目 （格式）](./listcontrol-element-format.md)定義檢視的清單格式。

[ListEntry 項目 （格式）](./listentry-element-for-listcontrol-format.md)提供 [清單] 檢視的定義。

[ListEntries 項目 （格式）](./listentries-element-for-listcontrol-format.md)定義 [清單] 檢視的資料列的顯示方式。

[ListItem 項目 （格式）](./listitem-element-for-listitems-for-listcontrol-format.md)定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。

[ListItems 項目 （格式）](./listitems-element-for-listentry-for-listcontrol-format.md)定義的屬性和清單檢視中顯示的指令碼。

[組態 （格式） 的控制項的控制項名稱項目](./name-element-for-control-for-controls-for-configuration-format.md)指定控制項的名稱。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[項目名稱 （格式） SelectionSet](./name-element-for-selectionset-format.md)指定用來參考選取項目集的名稱。

[項目名稱 （格式） 檢視](./name-element-for-view-format.md)指定用來識別檢視的名稱。

[CustomItem 組態 （格式） 的控制項的新行項目](./newline-element-for-customitem-for-controls-for-configuration-format.md)將空白的行加入至控制項的顯示。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[CustomItem 控制項的檢視 （格式） 的新行項目](./newline-element-for-customitem-for-controls-for-view-format.md)將空白的行加入至控制項的顯示。 定義可供檢視的控制項時，會使用這個項目。

[CustomItem CustomControl 檢視 （格式） 的新行項目](./newline-element-for-customitem-for-customcontrol-for-view-format.md)將空白的行加入至控制項的顯示。 定義自訂控制項的檢視時，會使用這個項目。

[CustomItem 的 GroupBy （格式） 的新行項目](./newline-element-for-customitem-for-groupby-format.md)將空白的行加入至控制項的顯示。 定義新的群組物件的顯示方式時，會使用這個項目。

[PropertyName ExpressionBinding 組態 （格式） 的控制項的項目](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)指定其值會顯示通用控制項的.NET 屬性。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[PropertyName ExpressionBinding 的控制項檢視 （格式） 的項目](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)指定其值控制項所顯示的.NET 屬性。 定義可供檢視的控制項時，會使用這個項目。

[PropertyName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)指定其值控制項所顯示的.NET 屬性。 定義自訂的控制項檢視時，會使用這個元素

[PropertyName ExpressionBinding 的 GroupBy （格式） 的項目](./propertyname-element-for-expressionbinding-for-groupby-format.md)指定其值控制項所顯示的.NET 屬性。 定義新的群組物件的顯示方式時，會使用這個項目。

[GroupBy （格式） 的屬性名稱項目](./propertyname-element-for-groupby-format.md)指定.NET 屬性，其值變更時，會啟動新的群組。

[PropertyName ItemSeclectionCondition 組態 （格式） 的控制項的項目](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和使用控制項。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 ItemSelectionCondition PropertyName 元素](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和使用控制項。 定義可供檢視的控制項時，會使用這個項目。

[檢視 CustomControl 的 ItemSelectionCondition PropertyName 項目 (格式](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和使用控制項。 定義自訂控制項的檢視時，會使用這個項目。

[GroupBy （格式） 的 ItemSelectionCondition PropertyName 元素](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和使用控制項。 定義新的群組物件的顯示方式時，會使用這個項目。

[ListItem （格式） 的 ItemSelectionCondition PropertyName 元素](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和在所用的檢視。 定義清單檢視時，會使用這個項目。

[PropertyName ListControl （格式） 的 ListItem 元素](./propertyname-element-for-listitem-for-listcontrol-format.md)指定其值會顯示在清單中的.NET 屬性。

[ListEntry （格式） 的 EntrySelectedBy 的 SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和使用的項目。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和使用的項目。 定義可供檢視的控制項時，會使用這個項目。

[PropertyName 元素 CustomControl 檢視 （格式） 的 SelectionCondition](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和在使用定義。 定義自訂控制項的檢視時，會使用這個項目。

[EnumerableExpansion （格式） 的 EntrySelectedBy 的 SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和在使用定義。

[GroupBy （格式） 的 SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-groupby-format.md)指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和在使用定義。 定義新的群組物件的顯示方式時，會使用這個項目。

[ListEntry （格式） 的 EntrySelectedBy 的 SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和使用清單項目。

[TableRowEntry （格式） 的 EntrySelectedBy 的 SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，並使用資料表項目。

[WideEntry （格式） 的 EntrySelectedBy 的 SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和在使用定義。

[PropertyName TableColumnItem （格式） 的項目](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)指定其值會顯示在資料列的資料行的屬性。

[PropertyName WideItem （格式） 的項目](./propertyname-element-for-wideitem-for-widecontrol-format.md)指定其值會顯示在寬型檢視物件的屬性。

[組態 （格式） 的控制項的畫面格 RightIndent 元素](./rightindent-element-for-frame-for-controls-for-configuration-format.md)指定的字元數的資料會移離右邊界。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[RightIndent 框架的控制項的檢視元件 （格式）](./rightindent-element-for-frame-for-controls-for-view-format.md)指定的字元數的資料會移離右邊界。 定義可供檢視的控制項時，會使用這個項目。

[RightIndent 元素](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)指定的字元數的資料會移離右邊界。 定義自訂控制項的檢視時，會使用這個項目。

[GroupBy （格式） 的畫面格 RightIndent 元素](./rightindent-element-for-frame-for-groupby-format.md)指定的字元數的資料會移離右邊界。 定義新的群組物件的顯示方式時，會使用這個項目。

[ExpressionBinding 組態 （格式） 的控制項的指令碼區塊項目](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)指定其值常見的控制項所顯示的指令碼。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[ExpressionBinding 的控制項檢視 （格式） 的指令碼區塊項目](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)指定其值控制項所顯示的指令碼。 定義可供檢視的控制項時，會使用這個項目。

[ExpressionBinding CustomCustomControl 檢視 （格式） 的指令碼區塊項目](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)指定其值控制項所顯示的指令碼。 定義自訂控制項的檢視時，會使用這個項目。

[ExpressionBinding 的 GroupBy （格式） 的指令碼區塊項目](./scriptblock-element-for-expressionbinding-for-groupby-format.md)指定其值控制項所顯示的指令碼。 定義新的群組物件的顯示方式時，會使用這個項目。

[GroupBy （格式） 的指令碼區塊項目](./scriptblock-element-for-groupby-format.md)指定其值變更時，會啟動新的群組的指令碼。

[ScriptBlock ItemSelectionCondition 組態 （格式） 的控制項的項目](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)指定觸發條件的指令碼。 此指令碼會評估為`true`、 符合條件，和使用控制項。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 ItemSelectionCondition 的指令碼區塊項目](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)指定觸發條件的指令碼。 此指令碼會評估為`true`、 符合條件，和使用控制項。 定義可供檢視的控制項時，會使用這個項目。

[ItemSelectionCondition CustomControl 檢視 （格式） 的指令碼區塊項目](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)指定觸發條件的指令碼。 此指令碼會評估為`true`、 符合條件，和使用控制項。 定義自訂控制項的檢視時，會使用這個項目。

[GroupBy （格式） 的 ItemSelectionCondition 的指令碼區塊項目](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)指定觸發條件的指令碼。 此指令碼會評估為`true`、 符合條件，和使用控制項。 定義新的群組物件的顯示方式時，會使用這個項目。

[ItemSelectionCondition ListControl （格式） 的指令碼區塊項目](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)指定觸發條件的指令碼。 此指令碼會評估為`true`、 符合條件，和使用的清單項目。 定義清單檢視時，會使用這個項目。

[ListItem （格式） 的指令碼區塊項目](./scriptblock-element-for-listitem-for-listcontrol-format.md)指定其值會顯示在清單中的資料列的指令碼。

[ScriptBlock SelectionCondition 組態 （格式） 的控制項的項目](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)指定觸發條件的指令碼。 此指令碼會評估為`true`、 符合條件，和在使用定義。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)指定觸發條件的指令碼。 此指令碼會評估為`true`、 符合條件，和在使用定義。 定義可供檢視的控制項時，會使用這個項目。

[SelectionCondition CustomControl 檢視 （格式） 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)指定觸發條件的指令碼。 此指令碼會評估為`true`、 符合條件，和在使用定義。 定義自訂控制項的檢視時，會使用這個項目。

[針對 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定觸發條件的指令碼。

[GroupBy （格式） 的 SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)指定觸發條件的指令碼。 此指令碼會評估為`true`、 符合條件，和在使用定義。 定義新的群組物件的顯示方式時，會使用這個項目。

[針對 ListEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)指定觸發條件的指令碼。 此指令碼會評估為`true`、 符合條件，和使用清單項目。

[針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)指定觸發條件的指令碼區塊。 此指令碼會評估為`true`、 符合條件，並使用資料表項目。

[針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)指定觸發條件的指令碼。 此指令碼會評估為`true`、 符合條件，和使用寬的項目定義。

[ScriptBlock TableColumnItem （格式） 的項目](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)指定其值會顯示在資料列的資料行的指令碼。

[ScriptBlock WideItem （格式） 的項目](./scriptblock-element-for-wideitem-for-widecontrol-format.md)指定其值會顯示在寬型檢視的指令碼。

[CustomEntry 組態 （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)定義必須存在，要使用的通用控制項定義的條件。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)定義必須存在，要使用的控制項定義的條件。 定義可供檢視的控制項時，會使用這個項目。

[CustomControl 檢視 （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)定義必須存在於要使用的控制項定義的條件。 定義自訂控制項的檢視時，會使用這個項目。

[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)定義必須存在以展開此定義的集合物件的條件。

[GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)定義必須存在於要使用的控制項定義的條件。 定義新的群組物件的顯示方式時，會使用這個項目。

[ListEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)定義要使用此清單檢視的定義必須存在的條件。 選取範圍條件可指定在清單定義的數目沒有限制。

[TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)定義要用於此 [資料表] 檢視的定義必須存在的條件。 選取範圍可以針對資料表定義指定的條件數目沒有限制。

[WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)定義必須存在於要使用此定義的條件。 選取範圍條件可指定寬的項目定義的數目沒有限制。

[SelectionSet 項目 （格式）](./selectionset-element-format.md)定義一組.NET 物件可以參考的集合的名稱。

[SelectionSetName EntrySelectedBy 組態 （格式） 的控制項的項目](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)指定一組使用這個控制項定義的.NET 型別。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)指定一組使用這個控制項定義的.NET 型別。 定義可供檢視的控制項時，會使用這個項目。

[CustomEntry （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)指定一組.NET 物件清單項目。 可供指定的項目選取項目集的數目沒有限制。

[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)指定.NET 型別，此定義會擴展集。

[GroupBy （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)指定一組.NET 物件清單項目。 可供指定的項目選取項目集的數目沒有限制。 定義新的群組物件的顯示方式時，會使用這個項目。

[ListEntry （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)指定一組.NET 物件清單項目。 可供指定的項目選取項目集的數目沒有限制。

[TableRowEntry （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)指定一組.NET 型別使用 [資料表] 檢視的此項目。 可供指定的項目選取項目集的數目沒有限制。

[WideEntry （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)指定一組定義的.NET 物件。 每當顯示下列其中一個這些物件，則會使用定義。

[SelectionSetName SelectionCondition 組態 （格式） 的控制項的項目](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)指定的觸發條件的.NET 型別集。 當有任何在這組型別時，符合條件，並使用這個控制項顯示物件。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)指定的觸發條件的.NET 型別集。 當有任何在這組型別時，即符合此條件，並使用這個控制項來顯示物件。 定義可供檢視的控制項時，會使用這個項目。

[EntrySelectedBy CustomEntry 檢視 （格式） 的項目](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)指定的觸發條件的.NET 型別集。 當有任何在這組型別時，即符合此條件，並使用這個控制項來顯示物件。 定義自訂控制項的檢視時，會使用這個項目。

[如 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定的觸發條件的.NET 型別集。 當有任何在這組型別時，即符合條件。

[GroupBy （格式） 的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)指定的觸發條件的.NET 型別集。 當有任何在這組型別時，符合條件，並使用這個控制項顯示物件。 定義新的群組物件的顯示方式時，會使用這個項目。

[如 ListEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)指定的觸發條件的.NET 型別集。 當有任何在這組型別時，符合條件，並使用此定義清單檢視中顯示物件。

[如 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)指定的觸發條件的.NET 型別集。 當有任何在這組型別時，符合條件，並使用此定義的資料表檢視中顯示物件。

[如 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)指定的觸發條件的.NET 型別集。 當有任何在這組型別時，符合條件，並使用此定義的寬型檢視來顯示物件。

[SelectionSetName ViewSelectedBy （格式） 的項目](./selectionsetname-element-for-viewselectedby-format.md)指定一份檢視所顯示的.NET 物件。

[SelectionSets 項目 （格式）](./selectionsets-element-format.md)定義可由個別的格式檢視的.NET 物件的集合。

[ShowError 項目 （格式）](./showerror-element-format.md)指定，顯示一段資料時，發生錯誤時，會顯示完整的錯誤記錄。

[TableControl （格式） 的 TableHeaders TableColumnHeader 元素](./tablecolumnheader-element-format.md)定義標籤、 資料行的寬度和資料表資料行的標籤對齊方式。

[TableColumnItem 項目 （格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)定義屬性或其值會顯示在資料列的資料行的指令碼。

[TableColumnItems 項目 （格式）](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)定義屬性或其值會顯示資料列中的指令碼。

[TableControl 項目 （格式）](./tablecontrol-element-format.md)定義檢視的資料表格式。

[TableHeaders 項目 （格式）](./tableheaders-element-format.md)定義資料表的資料行的標頭。

[TableRowEntries 項目 （格式）](./tablerowentries-element-for-tablecontrol-format.md)定義之資料表的資料列。

[TableRowEntry 項目 （格式）](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)定義會顯示在資料表資料列的資料。

[CustomItem 組態 （格式） 的控制項的文字項目](./text-element-for-customitem-for-controls-for-configuration-format.md)會加入至控制項，例如標籤，即可顯示資料的指定文字方括號來括住的資料和空格來縮排的資料。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[CustomItem 用於檢視 （格式） 的控制項的文字項目](./text-element-for-customitem-for-controls-for-view-format.md)會加入至控制項，例如標籤，即可顯示資料的指定文字方括號來括住的資料和空格來縮排的資料。 定義可供檢視的控制項時，會使用這個項目。

[CustomItem （格式） 的文字項目](./text-element-for-customitem-for-customview-for-view-format.md)會加入至控制項，例如標籤，即可顯示資料的指定文字方括號來括住的資料和空格來縮排的資料。 定義自訂控制項的檢視時，會使用這個項目。

[GroupBy （格式） 的 CustomItem 的文字項目](./text-element-for-customitem-for-groupby-format.md)會加入至控制項，例如標籤，即可顯示資料的指定文字方括號來括住的資料和空格來縮排的資料。 定義新的群組物件的顯示方式時，會使用這個項目。

[TypeName EntrySelectedBy 組態 （格式） 的控制項的項目](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)指定使用這個控制項定義的.NET 型別。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 EntrySelectedBy TypeName 項目](./typename-element-for-entryselectedby-for-controls-for-view-format.md)指定使用這個控制項定義的.NET 型別。 定義可供檢視的控制項時，會使用這個項目。

[CustomEntry 檢視 （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-entryselectedby-for-customentry-for-view-format.md)指定使用自訂的控制項檢視此定義的.NET 型別。 類型可定義指定的數目沒有限制。

[TypeName 項目 EnumerableExpansion （格式） 的 EntrySelectedBy](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)指定展開此定義的.NET 型別。 定義預設設定時，會使用這個項目。

[GroupBy （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-entryselectedby-for-groupby-format.md)指定會使用這個定義的自訂控制項的.NET 型別。 定義新的群組物件的顯示方式時，會使用這個項目。

[TypeName 項目 ListControl （格式） 的 EntrySelectedBy](./typename-element-for-entryselectedby-for-listcontrol-format.md)指定使用此項目清單檢視的.NET 型別。 類型可指定清單項目數目沒有限制。

[TypeName 項目 TableRowEntry （格式） 的 EntrySelectedBy](./typename-element-for-entryselectedby-for-tablecontrol-format.md)指定.NET 型別，使用 [資料表] 檢視的這個項目。 可供指定的資料表項目類型的數目沒有限制。

[TypeName 項目 WideEntry （格式） 的 EntrySelectedBy](./typename-element-for-entryselectedby-for-wideentry-format.md)指定.NET 型別定義。 每當此物件會顯示，則會使用定義。

[TypeName SelectionCondition 組態 （格式） 的控制項的項目](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)指定觸發條件的.NET 型別。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

[用於檢視 （格式） 的控制項 SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-controls-for-view-format.md)指定觸發條件的.NET 型別。 定義可供檢視的控制項時，會使用這個項目。

[CustomControl 檢視 （格式） 的 SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)指定觸發條件的.NET 型別。 定義自訂控制項的檢視時，會使用這個項目。

[TypeName 項目如 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定觸發條件的.NET 型別。

[GroupBy （格式） 的 SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-groupby-format.md)指定觸發條件的.NET 型別。 定義新的群組物件的顯示方式時，會使用這個項目。

[TypeName 項目如 ListControl （格式） 的 EntrySelectedBy SelectionCondition](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)指定觸發條件的.NET 型別。 當有此類型，則會使用清單項目。

[TypeName 項目如 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)指定觸發條件的.NET 型別。 有這種類型時，符合條件，並用資料表資料列。

[TypeName 項目如 WideEntry （格式） 的 EntrySelectedBy SelectionCondition](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)指定觸發條件的.NET 型別。 有這種類型時，會使用定義。

[類型名稱的項目類型 （格式）](./typename-element-for-types-format.md)指定屬於選取項目集之物件的.NET 類型。

[TypeName ViewSelectedBy （格式） 的項目](./typename-element-for-viewselectedby-format.md)指定檢視所顯示的.NET 物件。

[類型項目 （格式）](./types-element-for-selectionset-format.md)定義選取範圍中設定的.NET 物件。

[檢視項目 （格式）](./view-element-format.md)定義用來顯示一或多個.NET 物件的檢視。

[ViewDefinitions 項目 （格式）](./viewdefinitions-element-format.md)定義用來顯示物件的檢視。

[ViewSelectedBy 項目 （格式）](./viewselectedby-element-format.md)定義檢視所顯示的.NET 物件。

[WideControl 項目 （格式）](./widecontrol-element-format.md)寬 （單一值） 清單格式檢視的定義。 此檢視會顯示單一屬性值或每個物件的指令碼值。

[WideEntries 項目 （格式）](./wideentries-element-for-widecontrol-format.md)提供寬型檢視的定義。 寬型檢視必須指定一個或多個定義。

[WideEntry 項目 （格式）](./wideentry-element-for-widecontrol-format.md)提供寬型檢視的定義。

[WideItem 項目 （格式）](./wideitem-element-for-widecontrol-format.md)定義屬性或其值會顯示指令碼。

[Width 元素 （格式）](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)定義資料行的寬度 （以字元為單位）。

[包裝項目 （格式）](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)指定超過欄寬度的文字會顯示在下一行。

[WrapTables 項目 （格式）](./wraptables-element-format.md)指定表格儲存格的資料會移至下一行，是否資料的長度超過資料行的寬度。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
