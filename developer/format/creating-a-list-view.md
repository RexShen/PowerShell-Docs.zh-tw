---
title: 建立清單檢視 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066850"
---
# <a name="creating-a-list-view"></a>建立清單檢視

清單檢視會顯示資料 （在循序順序） 的單一資料行中。 顯示在清單中的資料可以是.NET 屬性的值或值的指令碼。

## <a name="a-list-view-display"></a>以清單檢視顯示

下列輸出顯示 Windows PowerShell 如何顯示的屬性[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)所傳回的物件[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。 在此範例中，已傳回三個物件，與上述物件使用空白行來分隔每個物件。

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

## <a name="defining-the-list-view"></a>定義清單檢視

下列 XML 說明顯示的數個屬性的清單檢視結構描述[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)物件。 您必須指定您想要顯示在清單檢視中的每一個屬性。

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

下列 XML 元素用來定義清單檢視：

- [檢視](./view-element-format.md)項目是清單檢視中的父項目。 （這是資料表，和自訂的控制項檢視相同的父項目）。

- [名稱](./name-element-for-view-format.md)項目會指定檢視的名稱。 所有檢視需要此項目。

- [ViewSelectedBy](./viewselectedby-element-format.md)項目會定義使用檢視的物件。 需要此項目。

- [GroupBy](./groupby-element-for-view-format.md)項目會定義當物件的新群組就會顯示。 每次特定的屬性或指令碼的值變更時，會啟動新的群組。 這是選擇性元素。

- [控制項](./controls-element-for-view-format.md)項目會定義 [清單] 檢視所定義的自訂控制項。 控制項可讓您進一步指定 顯示資料的方式。 這是選擇性元素。 檢視可以定義自己的自訂控制項，或可以使用通用控制項，可供任何檢視中的格式化檔案。 如需有關自訂控制項的詳細資訊，請參閱 <<c0> [ 建立自訂控制項](./creating-custom-controls.md)。

- [ListControl](./listcontrol-element-format.md)項目會定義在檢視中顯示的內容和格式的方式。 類似於其他所有的檢視，清單檢視可以顯示指令碼所產生的值或物件屬性的值。

如需完整的格式化檔案，定義簡單的清單檢視的範例，請參閱 <<c0> [ 清單檢視 （基本）](./list-view-basic.md)。

## <a name="providing-definitions-for-your-list-view"></a>提供您的清單檢視的定義

清單檢視可提供一個或多個定義所使用之子項目的[ListControl](./listcontrol-element-format.md)項目。 通常，檢視必須只有一個定義。 在下列範例中，此檢視會提供顯示的數個屬性的單一定義[System.Diagnostics.Process 嗎？Displayproperty = Fullname>](/dotnet/api/System.Diagnostics.Process)物件。 清單檢視可以顯示屬性的值或 （在範例中未顯示） 的指令碼的值。

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

下列的 XML 項目可以用來提供針對清單檢視的定義中：

- [ListControl](./listcontrol-element-format.md)元素和其子項目會定義在檢視中顯示的內容。

- [ListEntries](./listentries-element-for-listcontrol-format.md)項目會提供檢視的定義。 在大部分情況下，檢視必須只有一個定義。 需要此項目。

- [ListEntry](./listentry-element-for-listcontrol-format.md)項目會提供檢視的定義。 至少一個[ListEntry](./listentry-element-for-listcontrol-format.md)是必要項; 不過，還有您可以新增的項目數沒有上限限制。 在大部分情況下，檢視必須只有一個定義。

- [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)項目會指定特定的定義所顯示的物件。 這個項目是選擇性的只有在您定義多個時，才需要[ListEntry](./listentry-element-for-listcontrol-format.md)顯示不同的物件項目。

- [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md)項目指定的屬性和其值會顯示在清單檢視的資料列中的指令碼。

- [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md)元素會指定屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。 至少一個屬性或指令碼，必須指定清單檢視。 沒有任何最大的限制，您可以指定的資料列數目。

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)項目會指定資料列中顯示其值的屬性。 您必須指定屬性或指令碼，但您無法同時指定。

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)項目會指定其值會顯示資料列中的指令碼。 您必須指定指令碼或屬性，但您無法同時指定。

- [標籤](./label-element-for-listitem-for-listcontrol-format.md)項目會指定顯示屬性或指令碼中值的資料列左邊的標籤。 這是選擇性元素。 如果未指定標籤，則會顯示屬性或指令碼的名稱。 如需完整範例，請參閱 <<c0> [ 清單檢視 （標籤）](./list-view-labels.md)。

- [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)項目會指定要顯示的資料列必須存在的條件。 如需有關如何將條件新增至 [清單] 檢視的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。 這是選擇性元素。

- [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md)項目會指定用來顯示屬性或指令碼的值的模式。 這是選擇性元素。

如需完整的格式化檔案，定義簡單的清單檢視的範例，請參閱 <<c0> [ 清單檢視 （基本）](./list-view-basic.md)。

## <a name="defining-the-objects-that-use-the-list-view"></a>定義使用清單檢視的物件

有兩種方式可定義的.NET 物件會使用清單檢視。 您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)項目來定義可顯示的檢視，或您的所有定義的物件可以使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)項目來定義會顯示哪些物件特定檢視的定義。 在大部分情況下，檢視有只有一個定義，因此物件通常會定義所[ViewSelectedBy](./viewselectedby-element-format.md)項目。

下列範例示範如何定義會顯示清單檢視使用的物件[ViewSelectedBy](./viewselectedby-element-format.md)並[TypeName](./typename-element-for-viewselectedby-format.md)項目。 沒有任何限制的數目[TypeName](./typename-element-for-viewselectedby-format.md) ，您可以指定，且其順序並不重要的項目。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

下列的 XML 項目可以用來指定物件所使用的清單檢視中：

- [ViewSelectedBy](./viewselectedby-element-format.md)項目會定義 [清單] 檢視會顯示哪些物件。

- [TypeName](./typename-element-for-viewselectedby-format.md)項目會指定檢視所顯示的.NET 物件。 需要完整的.NET 型別名稱。 您必須指定至少一個型別或設定檢視中，選取項目，但可以指定的項目沒有最大數目。

如需完整的格式化檔案的範例，請參閱 <<c0> [ 清單檢視 （基本）](./list-view-basic.md)。

下列範例會使用[ViewSelectedBy](./viewselectedby-element-format.md)並[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)項目。 使用選取項目集都有一組相關的物件，會顯示使用多個檢視，例如當您定義清單檢視和資料表檢視表相同的物件的位置。 如需如何建立選取項目集的詳細資訊，請參閱[定義的選取項目集](./defining-selection-sets.md)。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

下列的 XML 項目可以用來指定物件所使用的清單檢視中：

- [ViewSelectedBy](./viewselectedby-element-format.md)項目會定義 [清單] 檢視會顯示哪些物件。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)項目會指定一組可以檢視所顯示的物件。 您必須指定至少一個選取項目集或類型檢視中，但您可以指定的項目沒有最大數目。

下列範例示範如何定義顯示清單檢視使用特定定義的物件[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)項目。 您可以使用這個項目，來指定物件、 選取項目集的物件或選取條件，指定當使用定義的.NET 型別名稱。 如需如何建立選取項目條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

下列的 XML 項目可以用來指定物件所使用的特定檢視的定義清單中：

- [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)項目會定義哪些物件會定義所顯示。

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)項目會指定定義所顯示的.NET 物件。 使用這個項目，完整的.NET 型別名稱時需要。 您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) （未顯示） 的項目會指定一組可顯示的這個定義的物件。 您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) （未顯示） 的項目會指定要使用此定義必須存在的條件。 您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。 如需定義選擇條件的詳細資訊，請參閱 <<c0> [ 定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

## <a name="displaying-groups-of-objects-in-a-list-view"></a>在 清單檢視中顯示之物件的群組

您可以分隔成群組的 [清單] 檢視所顯示的物件。 這不表示您定義一個群組，只有特定的屬性或指令碼的值變更時，Windows PowerShell 會啟動新的群組。 在下列範例中，啟動新的群組時的值[System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)屬性變更。

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

下列 XML 元素用來定義一組啟動時：

- [GroupBy](./groupby-element-for-view-format.md)項目定義之屬性或啟動新的群組，並定義群組的顯示方式的指令碼。

- [PropertyName](./propertyname-element-for-groupby-format.md)項目會指定開始新的群組，其值變更時的屬性。 您必須指定屬性或指令碼，以啟動群組中，但您無法同時指定。

- [ScriptBlock](./scriptblock-element-for-groupby-format.md)項目會指定指令碼，其值變更時，會啟動新的群組。 您必須指定指令碼或屬性，以啟動群組中，但您無法同時指定。

- [標籤](./label-element-for-groupby-format.md)項目會定義每個群組的開頭所顯示的標籤。 除了這個項目所指定的文字，Windows PowerShell 會顯示觸發新的群組，並新增一個空白行，標籤前後的值。 這是選擇性元素。

- [CustomControl](./customcontrol-element-for-groupby-format.md)項目會定義用來顯示資料的控制項。 這是選擇性元素。

- [CustomControlName](./customcontrolname-element-for-groupby-format.md)項目會指定一般或檢視來顯示資料的控制項。 這是選擇性元素。

如需完整的格式化檔案，定義群組的範例，請參閱 <<c0> [ 清單檢視 (GroupBy)](./list-view-groupby.md)。

## <a name="using-format-strings"></a>使用格式字串

格式字串可以加入檢視，以進一步定義資料的顯示方式。 下列範例示範如何定義的格式化字串的值，`StartTime`屬性。

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

下列的 XML 項目可以用來指定之格式模式中：

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)項目會指定檢視所顯示的資料。

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)項目會指定其值會顯示由檢視的屬性。 您必須指定屬性或指令碼，但您無法同時指定。

- [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md)項目會指定定義的屬性或指令碼的值在檢視中的顯示方式的格式模式。

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) （未顯示） 的項目會指定其值會顯示檢視指令碼。 您必須指定指令碼或屬性，但您無法同時指定。

在下列範例中，`ToString`來格式化值的指令碼會呼叫方法。 指令碼可以呼叫任何方法的物件。 因此，如果物件有一個方法，例如`ToString`具有格式設定的參數，指令碼可以呼叫該方法，來設定指令碼的輸出值的格式。

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

下列的 XML 項目可以用來呼叫`ToString`方法：

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)項目會指定檢視所顯示的資料。

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) （未顯示） 的項目會指定其值會顯示檢視指令碼。 您必須指定指令碼或屬性，但您無法同時指定。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
