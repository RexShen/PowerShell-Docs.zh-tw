---
title: 建立寬型檢視 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066714"
---
# <a name="creating-a-wide-view"></a>建立寬型檢視

寬型檢視會顯示每個物件，會顯示單一值。 顯示的值可以是.NET 物件屬性的值或值的指令碼。 根據預設，沒有任何標籤或標頭，此檢視。

## <a name="a-wide-view-display"></a>寬型檢視顯示

下列範例會示範 Windows PowerShell 的會顯示[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)所傳回的物件[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 時其輸出輸送到[Format-wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet。 (根據預設， [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)指令程式可傳回資料表的檢視。)在此範例中，兩個資料行用來顯示每個傳回的物件的程序的名稱。 未顯示物件的屬性名稱，屬性的值。

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

## <a name="defining-the-wide-view"></a>定義的寬型檢視

下列 XML 顯示的寬型檢視結構描述[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。

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

下列 XML 元素用來定義的寬型檢視中：

- [檢視](./view-element-format.md)項目是寬型檢視的父項目。 （這是資料表、 清單和自訂的控制項檢視的相同父項目）。

- [名稱](./name-element-for-view-format.md)項目會指定檢視的名稱。 所有檢視需要此項目。

- [ViewSelectedBy](./viewselectedby-element-format.md)項目會定義使用檢視的物件。 需要此項目。

- [GroupBy](./groupby-element-for-view-format.md)項目會定義當物件的新群組就會顯示。 每次特定的屬性或指令碼的值變更時，會啟動新的群組。 這是選擇性元素。

- [控制項](./controls-element-for-view-format.md)項目定義的寬型檢視所定義的自訂控制項。 控制項可讓您進一步指定 顯示資料的方式。 這是選擇性元素。 檢視可以定義自己的自訂控制項，或可以使用通用控制項，可供任何檢視中的格式化檔案。 如需有關自訂控制項的詳細資訊，請參閱 <<c0> [ 建立自訂控制項](./creating-custom-controls.md)。

- [WideControl](./widecontrol-element-format.md)元素和其子項目會定義在檢視中顯示的內容。 在上述範例中，檢視設計來顯示[System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)屬性。

如需完整的格式化檔案，定義簡單的寬型檢視的範例，請參閱 < [（基本） 的寬型檢視](./wide-view-basic.md)。

## <a name="providing-definitions-for-your-wide-view"></a>提供您的寬型檢視的定義

寬型檢視可以使用的子元素，提供一個或多個定義[WideControl](./widecontrol-element-format.md)項目。 通常，檢視必須只有一個定義。 在下列範例中，此檢視會提供顯示的值的單一定義[System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)屬性。 寬型檢視可以顯示屬性的值或 （在範例中未顯示） 的指令碼的值。

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

下列的 XML 項目可以用來提供的寬型檢視定義中：

- [WideControl](./widecontrol-element-format.md)元素和其子項目會定義在檢視中顯示的內容。

- [AutoSize](./autosize-element-for-widecontrol-format.md)項目會指定是否資料行大小和資料行數目根據調整大小的資料大小。 這是選擇性元素。

- [ColumnNumber](./columnnumber-element-for-widecontrol-format.md)項目會指定寬型檢視中顯示的資料行數目。 這是選擇性元素。

- [WideEntries](./wideentries-element-for-widecontrol-format.md)項目會提供檢視的定義。 在大部分情況下，檢視必須只有一個定義。 需要此項目。

- [WideEntry](./wideentry-element-for-widecontrol-format.md)項目會提供檢視的定義。 至少一個[WideEntry](./wideentry-element-for-widecontrol-format.md)是必要項; 不過，還有您可以新增的項目數沒有上限限制。 在大部分情況下，檢視必須只有一個定義。

- [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)項目會指定特定的定義所顯示的物件。 這個項目是選擇性的只有在您定義多個時，才需要[WideEntry](./wideentry-element-for-widecontrol-format.md)顯示不同的物件項目。

- [WideItem](./wideitem-element-for-widecontrol-format.md)項目會指定檢視所顯示的資料。 相較於其他類型的檢視，廣泛的控制項可以顯示一個項目。

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)項目會指定其值會顯示由檢視的屬性。 您必須指定屬性或指令碼，但您無法同時指定。

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)項目會指定其值會顯示檢視指令碼。 您必須指定指令碼或屬性，但您無法同時指定。

- [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md)項目會指定用來顯示資料的模式。 這是選擇性元素。

如需完整的格式化檔案定義的寬型檢視定義的範例，請參閱 < [（基本） 的寬型檢視](./wide-view-basic.md)。

## <a name="defining-the-objects-that-use-the-wide-view"></a>定義使用寬型檢視的物件

有兩種方式可定義的.NET 物件使用寬型檢視。 您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)項目來定義可顯示的檢視，或您的所有定義的物件可以使用[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)項目來定義會顯示哪些物件特定檢視的定義。 在大部分情況下，檢視有只有一個定義，因此物件通常會定義所[ViewSelectedBy](./viewselectedby-element-format.md)項目。

下列範例示範如何定義會顯示寬型檢視使用的物件[ViewSelectedBy](./viewselectedby-element-format.md)並[TypeName](./typename-element-for-viewselectedby-format.md)項目。 沒有任何限制的數目[TypeName](./typename-element-for-viewselectedby-format.md) ，您可以指定，且其順序並不重要的項目。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

下列的 XML 項目可以用來指定物件所使用的寬型檢視中：

- [ViewSelectedBy](./viewselectedby-element-format.md)項目可讓您定義的寬型檢視會顯示哪些物件。

- [TypeName](./typename-element-for-viewselectedby-format.md)項目會指定.NET 所顯示的檢視。 需要完整的.NET 型別名稱。 您必須指定至少一個型別或設定檢視中，選取項目，但可以指定的項目沒有最大數目。

如需完整的格式化檔案的範例，請參閱 < [（基本） 的寬型檢視](./wide-view-basic.md)。

下列範例會使用[ViewSelectedBy](./viewselectedby-element-format.md)並[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)項目。 使用選取項目集都有一組相關的物件，會顯示使用多個檢視，例如當您定義的寬型檢視和資料表檢視表相同的物件的位置。 如需如何建立選取項目集的詳細資訊，請參閱[定義的選取項目集](./defining-selection-sets.md)。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

下列的 XML 項目可以用來指定物件所使用的寬型檢視中：

- [ViewSelectedBy](./viewselectedby-element-format.md)項目可讓您定義的寬型檢視會顯示哪些物件。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)項目會指定一組可以檢視所顯示的物件。 您必須指定至少一個選取項目集或類型檢視中，但您可以指定的項目沒有最大數目。

下列範例示範如何定義的寬型檢視使用特定定義所顯示的物件[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)項目。 您可以使用這個項目，來指定物件、 選取項目集的物件或選取條件，指定當使用定義的.NET 型別名稱。 如需如何建立選取項目條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

下列的 XML 項目可用來指定特定的寬型檢視定義所使用的物件：

- [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)項目會定義哪些物件會定義所顯示。

- [TypeName](./typename-element-for-viewselectedby-format.md)項目會指定.NET 所定義顯示。 使用此項目的完整的.NET 型別名稱時需要。 您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) （未顯示） 的項目會指定一組可顯示的這個定義的物件。 您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) （未顯示） 的項目會指定要使用此定義必須存在的條件。 您必須指定至少一個型別、 選取項目集或選擇條件的定義，但您可以指定的項目沒有最大數目。 如需定義選擇條件的詳細資訊，請參閱 <<c0> [ 定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>在寬型檢視中顯示物件的群組

您可以分隔成群組寬型檢視所顯示的物件。 這不表示您定義一個群組，只有特定的屬性或指令碼的值變更時，Windows PowerShell 會啟動新的群組。 在下列範例中，啟動新的群組時的值[System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)屬性變更。

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

如需完整的格式化檔案，定義群組的範例，請參閱 <<c0> [ 寬型檢視 (GroupBy)](./wide-view-groupby.md)。

## <a name="using-format-strings"></a>使用格式字串

格式字串可以加入成寬型檢視，以進一步定義資料的顯示方式。 下列範例示範如何定義的格式化字串的值，`StartTime`屬性。

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

下列的 XML 項目可以用來指定之格式模式中：

- [WideItem](./wideitem-element-for-widecontrol-format.md)項目會指定檢視所顯示的資料。

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)項目會指定其值會顯示由檢視的屬性。 您必須指定屬性或指令碼，但您無法同時指定。

- [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md)項目會指定之格式模式所定義的屬性或指令碼的值在檢視中的顯示方式

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) （未顯示） 的項目會指定其值會顯示檢視指令碼。 您必須指定指令碼或屬性，但您無法同時指定。

在下列範例中，`ToString`來格式化值的指令碼會呼叫方法。 指令碼可以呼叫任何方法的物件。 因此，如果物件有一個方法，例如`ToString`具有格式設定的參數，指令碼可以呼叫該方法，來設定指令碼的輸出值的格式。

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

下列的 XML 項目可以用來呼叫`ToString`方法：

- [WideItem](./wideitem-element-for-widecontrol-format.md)項目會指定檢視所顯示的資料。

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) （未顯示） 的項目會指定其值會顯示檢視指令碼。 您必須指定指令碼或屬性，但您無法同時指定。

## <a name="see-also"></a>另請參閱

[寬型檢視 （基本）](./wide-view-basic.md)

[寬型檢視 (GroupBy)](./wide-view-groupby.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
