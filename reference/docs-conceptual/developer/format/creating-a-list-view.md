---
ms.date: 09/13/2016
ms.topic: reference
title: 建立清單檢視
description: 建立清單檢視
ms.openlocfilehash: c34c4fddc27d4fd016fba37fc465924d693756a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655637"
---
# <a name="creating-a-list-view"></a>建立清單檢視

清單視圖會依序顯示單一資料行中的資料 (順序) 。 清單中顯示的資料可以是 .NET 屬性的值或腳本的值。

## <a name="a-list-view-display"></a>清單視圖顯示

下列輸出顯示 Windows PowerShell 如何顯示 [system.serviceprocess.dll. Servicecontroller 的屬性？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) [取得服務](/powershell/module/microsoft.powershell.management/get-service) Cmdlet 所傳回的 Fullname 物件。 在此範例中，傳回了三個物件，每個物件都以空白行分隔。

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a>定義清單視圖

下列 XML 會顯示清單視圖架構，以顯示 System.serviceprocess.dll Servicecontroller 的數個屬性。 [Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) 物件。 您必須指定要顯示在清單視圖中的每個屬性。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

下列 XML 元素用來定義清單視圖：

- [View](./view-element-format.md)元素是清單視圖的父元素。  (此為數據表、寬和自訂控制項視圖的相同父元素。 ) 

- [Name](./name-element-for-view-format.md)元素會指定視圖的名稱。 所有視圖都需要這個元素。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義使用 view 的物件。 這個元素是必要的。

- [GroupBy](./groupby-element-for-view-format.md)元素會定義何時會顯示新的物件群組。 每當特定屬性或腳本的值變更時，就會啟動新的群組。 這是選擇性的項目。

- [Controls](./controls-element-for-view-format.md)元素會定義清單視圖所定義的自訂控制項。 控制項可讓您進一步指定顯示資料的方式。 這是選擇性的項目。 View 可以定義自己的自訂控制項，也可以使用格式檔案中任何視圖都可使用的通用控制項。 如需自訂控制項的詳細資訊，請參閱 [建立自訂控制項](./creating-custom-controls.md)。

- [ListControl](./listcontrol-element-format.md)元素會定義要顯示在視圖中的內容，以及其格式化方式。 清單視圖類似于所有其他的視圖，可顯示物件屬性的值或腳本所產生的值。

如需定義簡單列表視圖的完整格式化檔案範例，請參閱 [清單視圖 (基本) ](./list-view-basic.md)。

## <a name="providing-definitions-for-your-list-view"></a>提供清單視圖的定義

清單視圖可以使用 [ListControl](./listcontrol-element-format.md) 元素的子項目來提供一或多個定義。 一般而言，視圖只會有一個定義。 在下列範例中，此視圖會提供單一定義，以顯示系統的數個屬性 [。Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) 物件。 清單視圖可以顯示內容的值或腳本的值 (未顯示在範例) 中。

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

下列 XML 元素可用來提供清單視圖的定義：

- [ListControl](./listcontrol-element-format.md)元素和其子項目會定義要顯示在視圖中的內容。

- [ListEntries](./listentries-element-for-listcontrol-format.md)元素會提供視圖的定義。 在大部分的情況下，view 只會有一個定義。 這個元素是必要的。

- [ListEntry](./listentry-element-for-listcontrol-format.md)元素會提供視圖的定義。 至少需要一個 [ListEntry](./listentry-element-for-listcontrol-format.md) ;不過，您可以新增的元素數目沒有最大限制。 在大部分的情況下，view 只會有一個定義。

- [之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素會指定特定定義所顯示的物件。 這個元素是選擇性的，只有當您定義多個顯示不同物件的 [ListEntry](./listentry-element-for-listcontrol-format.md) 專案時，才需要此專案。

- [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md)元素會指定屬性和腳本，其值會顯示在清單視圖的資料列中。

- 專案 [清單元素會](./listitems-element-for-listentry-for-listcontrol-format.md) 指定屬性或腳本，其值會顯示在清單視圖的資料列中。 清單視圖必須指定至少一個屬性或腳本。 可指定的資料列數目沒有最大限制。

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素會指定屬性，其值會顯示在資料列中。 您必須指定屬性或腳本，但不能同時指定這兩種方法。

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素會指定其值會顯示在資料列中的腳本。 您必須指定腳本或屬性，但不能同時指定兩者。

- [Label](./label-element-for-listitem-for-listcontrol-format.md)元素會指定在資料列中屬性或腳本值的左邊顯示的標籤。 這是選擇性的項目。 如果未指定標籤，則會顯示內容或腳本的名稱。 如需完整範例，請參閱 [清單視圖 (標籤) ](./list-view-labels.md)。

- [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)元素會指定必須存在才能顯示資料列的條件。 如需有關在清單視圖中加入條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。 這是選擇性的項目。

- [格式](./formatstring-element-for-listitem-for-listcontrol-format.md)值元素會指定用來顯示內容或腳本值的模式。 這是選擇性的項目。

如需定義簡單列表視圖的完整格式化檔案範例，請參閱 [清單視圖 (基本) ](./list-view-basic.md)。

## <a name="defining-the-objects-that-use-the-list-view"></a>定義使用清單視圖的物件

有兩種方式可以定義使用清單視圖的 .NET 物件。 您可以使用 [ViewSelectedBy](./viewselectedby-element-format.md) 專案來定義可由視圖的所有定義顯示的物件，或者，您可以使用 [之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 元素來定義由視圖的特定定義所顯示的物件。 在大部分的情況下，視圖只有一個定義，因此物件通常是由 [ViewSelectedBy](./viewselectedby-element-format.md) 元素定義。

下列範例示範如何使用 [ViewSelectedBy](./viewselectedby-element-format.md) 和 [TypeName](./typename-element-for-viewselectedby-format.md) 元素，定義清單視圖所顯示的物件。 您可以指定的 [TypeName](./typename-element-for-viewselectedby-format.md) 元素數目沒有任何限制，而且其順序並不重要。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

下列 XML 元素可以用來指定清單視圖所使用的物件：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義清單視圖要顯示的物件。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素會指定視圖所顯示的 .net 物件。 需要完整的 .NET 型別名稱。 您必須為此視圖指定至少一個類型或選取範圍，但無法指定的元素數目上限。

如需完整格式化檔案的範例，請參閱 [清單視圖 (基本) ](./list-view-basic.md)。

下列範例會使用 [ViewSelectedBy](./viewselectedby-element-format.md) 和 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 元素。 如果您有一組相關的物件會使用多個視圖顯示，例如當您針對相同物件定義清單視圖和資料表視圖時，請使用選取集。 如需有關如何建立選取範圍的詳細資訊，請參閱 [定義選取集合](./defining-selection-sets.md)。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

下列 XML 元素可以用來指定清單視圖所使用的物件：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義清單視圖要顯示的物件。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素會指定可供視圖顯示的一組物件。 您必須為此視圖指定至少一個選擇集或類型，但無法指定的元素數目上限。

下列範例示範如何使用 [之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 元素定義清單視圖的特定定義所顯示的物件。 您可以使用這個專案，指定物件的 .NET 類型名稱、一組選取的物件，或指定使用定義時指定的選取條件。 如需如何建立選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

下列 XML 專案可以用來指定清單視圖的特定定義所使用的物件：

- [之 entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素會定義定義所顯示的物件。

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素會指定定義所顯示的 .net 物件。 使用這個專案時，需要完整的 .NET 型別名稱。 您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素 (未顯示) 指定可由此定義顯示的一組物件。 您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素 (未顯示) 指定必須存在才能使用此定義的條件。 您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。 如需定義選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="displaying-groups-of-objects-in-a-list-view"></a>在清單視圖中顯示物件群組

您可以將清單視圖所顯示的物件分隔成群組。 這並不表示您定義了群組，只有當特定屬性或腳本的值變更時，Windows PowerShell 才會啟動新群組。 下列範例會在 [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 屬性的值變更時，啟動新的群組。

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

下列 XML 元素可用來定義何時啟動群組：

- [GroupBy](./groupby-element-for-view-format.md)元素會定義可啟動新群組的屬性或腳本，並定義如何顯示群組。

- [PropertyName](./propertyname-element-for-groupby-format.md)元素會指定在其值變更時啟動新群組的屬性。 您必須指定屬性或腳本來啟動群組，但不能同時指定兩者。

- [ScriptBlock](./scriptblock-element-for-groupby-format.md)元素會指定在其值變更時啟動新群組的腳本。 您必須指定腳本或屬性來啟動群組，但不能同時指定兩者。

- [Label](./label-element-for-groupby-format.md)元素會定義在每個群組的開頭顯示的標籤。 除了這個專案所指定的文字之外，Windows PowerShell 會顯示觸發新群組的值，並在標籤前後加上空白行。 這是選擇性的項目。

- [CustomControl](./customcontrol-element-for-groupby-format.md)元素會定義用來顯示資料的控制項。 這是選擇性的項目。

- [CustomControlName](./customcontrolname-element-for-groupby-format.md)元素會指定用來顯示資料的通用或視圖控制項。 這是選擇性的項目。

如需定義群組之完整格式化檔案的範例，請參閱 [清單視圖 (GroupBy) ](./list-view-groupby.md)。

## <a name="using-format-strings"></a>使用格式字串

您可以將字串格式設定加入至視圖，以進一步定義資料的顯示方式。 下列範例顯示如何定義屬性值的格式化字串 `StartTime` 。

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

下列 XML 元素可以用來指定格式模式：

- [專案 [] 元素會](./listitem-element-for-listitems-for-listcontrol-format.md) 指定視圖所顯示的資料。

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素會指定屬性，其值會由視圖顯示。 您必須指定屬性或腳本，但不能同時指定這兩種方法。

- 格式 [值元素會](./formatstring-element-for-listitem-for-listcontrol-format.md) 指定格式模式，以定義屬性或腳本值在視圖中的顯示方式。

-  (不會顯示 [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 元素) 指定由視圖顯示其值的腳本。 您必須指定腳本或屬性，但不能同時指定兩者。

在下列範例中， `ToString` 會呼叫方法來格式化腳本的值。 腳本可以呼叫物件的任何方法。 因此，如果物件具有具有格式化參數的方法（例如 `ToString` ），則腳本可以呼叫該方法來格式化腳本的輸出值。

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

下列 XML 元素可以用來呼叫 `ToString` 方法：

- [專案 [] 元素會](./listitem-element-for-listitems-for-listcontrol-format.md) 指定視圖所顯示的資料。

-  (不會顯示 [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 元素) 指定由視圖顯示其值的腳本。 您必須指定腳本或屬性，但不能同時指定兩者。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
