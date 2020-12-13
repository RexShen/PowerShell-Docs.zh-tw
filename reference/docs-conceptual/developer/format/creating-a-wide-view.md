---
ms.date: 09/13/2016
ms.topic: reference
title: 建立寬型檢視
description: 建立寬型檢視
ms.openlocfilehash: 4230ef91a3612e962b2773b12e8016df6f760eae
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655604"
---
# <a name="creating-a-wide-view"></a>建立寬型檢視

寬型視圖會顯示每個顯示物件的單一值。 顯示的值可以是 .NET 物件屬性的值或腳本的值。 根據預設，此視圖沒有標籤或標頭。

## <a name="a-wide-view-display"></a>寬視圖顯示

下列範例顯示 Windows PowerShell 如何顯示在將其輸出輸送至[全格式](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide)Cmdlet 時，由[取得](/powershell/module/Microsoft.PowerShell.Management/Get-Process)程式 Cmdlet 傳回的[system.object](/dotnet/api/System.Diagnostics.Process)物件。  (根據預設， [取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet 會傳回資料表視圖。在此範例中，) 這兩個數據行用來顯示每個傳回物件之進程的名稱。 不會顯示物件屬性的名稱，只會顯示內容的值。

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a>定義寬視圖

下列 XML 會顯示適用于 [system.object](/dotnet/api/System.Diagnostics.Process) 物件的廣泛視圖架構。

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

下列 XML 元素用來定義寬視圖：

- [View](./view-element-format.md)元素是寬視圖的父元素。  (這是資料表、清單和自訂控制項視圖的相同父元素。 ) 

- [Name](./name-element-for-view-format.md)元素會指定視圖的名稱。 所有視圖都需要這個元素。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義使用 view 的物件。 這個元素是必要的。

- [GroupBy](./groupby-element-for-view-format.md)元素會定義何時會顯示新的物件群組。 每當特定屬性或腳本的值變更時，就會啟動新的群組。 這是選擇性的項目。

- [Controls](./controls-element-for-view-format.md)元素定義由寬視圖定義的自訂控制項。 控制項可讓您進一步指定顯示資料的方式。 這是選擇性的項目。 View 可以定義自己的自訂控制項，也可以使用格式檔案中任何視圖都可使用的通用控制項。 如需自訂控制項的詳細資訊，請參閱 [建立自訂控制項](./creating-custom-controls.md)。

- [WideControl](./widecontrol-element-format.md)元素和其子項目會定義要顯示在視圖中的內容。 在上述範例中，視圖是設計來顯示 [Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) 屬性。

如需完整格式化檔案的範例，以定義簡單的全視圖，請參閱 [wide (基本) ](./wide-view-basic.md)。

## <a name="providing-definitions-for-your-wide-view"></a>為您的寬視野提供定義

寬型視圖可以使用 [WideControl](./widecontrol-element-format.md) 元素的子項目來提供一或多個定義。 一般而言，視圖只會有一個定義。 在下列範例中，視圖會提供單一定義，以顯示 [Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) 屬性的值。 寬型視圖可以顯示內容的值或腳本的值 (未顯示在範例) 中。

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

下列 XML 元素可用來提供廣泛視圖的定義：

- [WideControl](./widecontrol-element-format.md)元素和其子項目會定義要顯示在視圖中的內容。

- [AutoSize](./autosize-element-for-widecontrol-format.md)元素會指定資料行大小和資料行數目是否根據資料的大小進行調整。 這是選擇性的項目。

- [ColumnNumber](./columnnumber-element-for-widecontrol-format.md)元素會指定在寬視圖中顯示的資料行數目。 這是選擇性的項目。

- [WideEntries](./wideentries-element-for-widecontrol-format.md)元素會提供視圖的定義。 在大部分的情況下，view 只會有一個定義。 這個元素是必要的。

- [WideEntry](./wideentry-element-for-widecontrol-format.md)元素會提供視圖的定義。 至少需要一個 [WideEntry](./wideentry-element-for-widecontrol-format.md) ;不過，您可以新增的元素數目沒有最大限制。 在大部分的情況下，view 只會有一個定義。

- [之 entryselectedby](./entryselectedby-element-for-wideentry-format.md)元素會指定特定定義所顯示的物件。 這個元素是選擇性的，只有當您定義多個顯示不同物件的 [WideEntry](./wideentry-element-for-widecontrol-format.md) 專案時，才需要此專案。

- [之 wideitem](./wideitem-element-for-widecontrol-format.md)元素會指定視圖所顯示的資料。 相較于其他類型的視圖，寬控制項只能顯示一個專案。

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素會指定屬性，其值會由視圖顯示。 您必須指定屬性或腳本，但不能同時指定這兩種方法。

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素會指定由視圖顯示其值的腳本。 您必須指定腳本或屬性，但不能同時指定兩者。

- [格式格式](./formatstring-element-for-wideitem-for-widecontrol-format.md)元素會指定用來顯示資料的模式。 這是選擇性的項目。

如需定義寬視圖定義之完整格式化檔案的範例，請參閱 [wide (基本) ](./wide-view-basic.md)。

## <a name="defining-the-objects-that-use-the-wide-view"></a>定義使用廣泛視圖的物件

有兩種方式可以定義使用寬視圖的 .NET 物件。 您可以使用 [ViewSelectedBy](./viewselectedby-element-format.md) 專案來定義可由視圖的所有定義顯示的物件，或者，您可以使用 [之 entryselectedby](./entryselectedby-element-for-wideentry-format.md) 元素來定義由視圖的特定定義所顯示的物件。 在大部分的情況下，視圖只有一個定義，因此物件通常是由 [ViewSelectedBy](./viewselectedby-element-format.md) 元素定義。

下列範例示範如何使用 [ViewSelectedBy](./viewselectedby-element-format.md) 和 [TypeName](./typename-element-for-viewselectedby-format.md) 元素，定義寬視圖所顯示的物件。 您可以指定的 [TypeName](./typename-element-for-viewselectedby-format.md) 元素數目沒有任何限制，而且其順序並不重要。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

下列 XML 元素可用來指定寬視圖所使用的物件：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義寬視圖所顯示的物件。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素會指定視圖所顯示的 .net。 需要完整的 .NET 型別名稱。 您必須為此視圖指定至少一個類型或選取範圍，但無法指定的元素數目上限。

如需完整格式化檔案的範例，請參閱 [Wide (基本) ](./wide-view-basic.md)。

下列範例會使用 [ViewSelectedBy](./viewselectedby-element-format.md) 和 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 元素。 如果您有一組相關的物件會使用多個視圖顯示，例如當您為相同的物件定義寬視圖和資料表視圖時，請使用選取集。 如需有關如何建立選取範圍的詳細資訊，請參閱 [定義選取集合](./defining-selection-sets.md)。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

下列 XML 元素可用來指定寬視圖所使用的物件：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義寬視圖所顯示的物件。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素會指定可供視圖顯示的一組物件。 您必須為此視圖指定至少一個選擇集或類型，但無法指定的元素數目上限。

下列範例示範如何使用 [之 entryselectedby](./entryselectedby-element-for-wideentry-format.md) 元素，定義寬視圖的特定定義所顯示的物件。 您可以使用這個專案，指定物件的 .NET 類型名稱、一組選取的物件，或指定使用定義時指定的選取條件。 如需如何建立選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

下列 XML 元素可用來指定廣泛視圖的特定定義所使用的物件：

- [之 entryselectedby](./entryselectedby-element-for-wideentry-format.md)元素會定義定義所顯示的物件。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素會指定定義所顯示的 .net。 使用這個專案時，需要完整的 .NET 型別名稱。 您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素 (未顯示) 指定可由此定義顯示的一組物件。 您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)元素 (未顯示) 指定必須存在才能使用此定義的條件。 您必須為定義指定至少一個類型、選取集或選取條件，但無法指定的元素數目上限。 如需定義選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>在寬型視圖中顯示物件群組

您可以將寬視圖所顯示的物件分隔成群組。 這並不表示您定義了群組，只有當特定屬性或腳本的值變更時，Windows PowerShell 才會啟動新群組。 下列範例會在 [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 屬性的值變更時，啟動新的群組。

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

如需定義群組之完整格式化檔案的範例，請參閱 [Wide View (GroupBy) ](./wide-view-groupby.md)。

## <a name="using-format-strings"></a>使用格式字串

您可以將格式化字串新增到廣泛的視圖，以進一步定義資料的顯示方式。 下列範例顯示如何定義屬性值的格式化字串 `StartTime` 。

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

下列 XML 元素可以用來指定格式模式：

- [之 wideitem](./wideitem-element-for-widecontrol-format.md)元素會指定視圖所顯示的資料。

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素會指定屬性，其值會由視圖顯示。 您必須指定屬性或腳本，但不能同時指定這兩種方法。

- 格式 [值元素指定](./formatstring-element-for-wideitem-for-widecontrol-format.md) 的格式模式定義屬性或腳本值在視圖中的顯示方式

-  (不會顯示 [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 元素) 指定由視圖顯示其值的腳本。 您必須指定腳本或屬性，但不能同時指定兩者。

在下列範例中， `ToString` 會呼叫方法來格式化腳本的值。 腳本可以呼叫物件的任何方法。 因此，如果物件具有具有格式化參數的方法（例如 `ToString` ），則腳本可以呼叫該方法來格式化腳本的輸出值。

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

下列 XML 元素可以用來呼叫 `ToString` 方法：

- [之 wideitem](./wideitem-element-for-widecontrol-format.md)元素會指定視圖所顯示的資料。

-  (不會顯示 [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 元素) 指定由視圖顯示其值的腳本。 您必須指定腳本或屬性，但不能同時指定兩者。

## <a name="see-also"></a>另請參閱

[寬型檢視 (基本)](./wide-view-basic.md)

[寬型檢視 (GroupBy)](./wide-view-groupby.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
