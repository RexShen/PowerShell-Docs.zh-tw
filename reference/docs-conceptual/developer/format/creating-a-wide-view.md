---
title: 建立寬視圖 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368947"
---
# <a name="creating-a-wide-view"></a>建立寬型檢視

寬型視圖會針對每個顯示的物件顯示單一值。 顯示的值可以是 .NET 物件屬性的值或腳本的值。 根據預設，沒有此視圖的標籤或標頭。

## <a name="a-wide-view-display"></a>寬視圖顯示

下列範例示範 Windows PowerShell 如何顯示由[取得處理](/powershell/module/Microsoft.PowerShell.Management/Get-Process)程式 Cmdlet 將其輸出輸送至[全格式](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide)的 Cmdlet 時，所傳回的[system.servicemodel 物件。](/dotnet/api/System.Diagnostics.Process) （根據預設， [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet 會傳回資料表視圖）。在此範例中，會使用這兩個數據行來顯示每個傳回之物件的進程名稱。 物件的屬性名稱不會顯示，只有屬性的值。

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

## <a name="defining-the-wide-view"></a>定義全形視圖

下列 XML 顯示[system.object](/dotnet/api/System.Diagnostics.Process)物件的寬視圖架構。

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

下列 XML 元素可用來定義寬視圖：

- [View](./view-element-format.md)元素是寬視圖的父元素。 （這是資料表、清單和自訂控制項視圖的相同父元素）。

- [Name](./name-element-for-view-format.md)元素會指定視圖的名稱。 所有的視圖都需要此元素。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義使用此視圖的物件。 此為必要元素。

- [GroupBy](./groupby-element-for-view-format.md)元素會定義何時顯示新的物件群組。 每當特定屬性或腳本的值變更時，就會啟動新的群組。 這個元素是選擇性的。

- [Controls](./controls-element-for-view-format.md)元素會定義寬視圖所定義的自訂控制項。 控制項可讓您進一步指定資料的顯示方式。 這個元素是選擇性的。 View 可以定義自己的自訂控制項，也可以使用格式檔案中任何視圖可以使用的通用控制項。 如需自訂控制項的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。

- [WideControl](./widecontrol-element-format.md)元素及其子項目會定義要在視圖中顯示的內容。 在上述範例中，此視圖設計為顯示[Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)屬性。

如需定義簡單寬視圖的完整格式檔案範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。

## <a name="providing-definitions-for-your-wide-view"></a>提供全形視圖的定義

寬視圖可以使用[WideControl](./widecontrol-element-format.md)專案的子專案來提供一或多個定義。 一般而言，視圖只會有一個定義。 在下列範例中，此視圖提供單一定義來顯示[Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)屬性的值。 寬型視圖可以顯示內容的值或腳本的值（在此範例中未顯示）。

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

下列 XML 元素可以用來提供寬視圖的定義：

- [WideControl](./widecontrol-element-format.md)元素及其子項目會定義要在視圖中顯示的內容。

- [AutoSize](./autosize-element-for-widecontrol-format.md)元素會指定資料行大小和資料行數目是否根據資料的大小來調整。 這個元素是選擇性的。

- [ColumnNumber](./columnnumber-element-for-widecontrol-format.md)元素會指定在寬視圖中顯示的資料行數目。 這個元素是選擇性的。

- [WideEntries](./wideentries-element-for-widecontrol-format.md)元素會提供視圖的定義。 在大部分的情況下，視圖只會有一個定義。 此為必要元素。

- [WideEntry](./wideentry-element-for-widecontrol-format.md)元素會提供 view 的定義。 至少需要一個[WideEntry](./wideentry-element-for-widecontrol-format.md) ;不過，您可以新增的專案數沒有最大限制。 在大部分的情況下，視圖只會有一個定義。

- [之 entryselectedby](./entryselectedby-element-for-wideentry-format.md)元素會指定特定定義所顯示的物件。 這個元素是選擇性的，只有當您定義多個[WideEntry](./wideentry-element-for-widecontrol-format.md)專案來顯示不同的物件時，才需要此專案。

- [之 wideitem](./wideitem-element-for-widecontrol-format.md)元素會指定視圖所顯示的資料。 相較于其他類型的視圖，寬型控制項只能顯示一個專案。

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素會指定屬性，其值會由視圖顯示。 您必須指定屬性或腳本，但不能同時指定這兩者。

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素會指定由視圖顯示其值的腳本。 您必須指定腳本或屬性，但不能同時指定這兩者。

- [[字串](./formatstring-element-for-wideitem-for-widecontrol-format.md)類型] 元素會指定用來顯示資料的模式。 這個元素是選擇性的。

如需定義寬視圖定義的完整格式檔案範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。

## <a name="defining-the-objects-that-use-the-wide-view"></a>定義使用寬視圖的物件

有兩種方式可定義哪些 .NET 物件使用寬視圖。 您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)專案來定義可由視圖的所有定義顯示的物件，也可以使用[之 entryselectedby](./entryselectedby-element-for-wideentry-format.md)專案來定義由視圖的特定定義所顯示的物件。 在大部分情況下，一個 view 只有一個定義，因此物件通常是由[ViewSelectedBy](./viewselectedby-element-format.md)元素所定義。

下列範例示範如何使用[ViewSelectedBy](./viewselectedby-element-format.md)和[TypeName](./typename-element-for-viewselectedby-format.md)元素定義寬視圖所顯示的物件。 您可以指定的[TypeName](./typename-element-for-viewselectedby-format.md)元素數目沒有限制，而且其順序並不重要。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

下列 XML 元素可以用來指定寬視圖所使用的物件：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義寬視圖所要顯示的物件。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素會指定視圖所顯示的 .net。 需要完整的 .NET 類型名稱。 您必須為此視圖指定至少一個類型或選取範圍，但不能指定的元素數目上限。

如需完整格式檔案的範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。

下列範例會使用[ViewSelectedBy](./viewselectedby-element-format.md)和[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。 使用 [選取專案集]，您可以在其中擁有一組使用多個視圖顯示的相關物件，例如當您為相同的物件定義寬視圖和資料表視圖時。 如需有關如何建立選擇集的詳細資訊，請參閱[定義選取範圍集](./defining-selection-sets.md)。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

下列 XML 元素可以用來指定寬視圖所使用的物件：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素會定義寬視圖所要顯示的物件。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素會指定一組可由視圖顯示的物件。 您必須為此視圖指定至少一個選取範圍或類型，但不能指定的元素數目上限。

下列範例示範如何使用[之 entryselectedby](./entryselectedby-element-for-wideentry-format.md)專案，定義以寬視圖的特定定義所顯示的物件。 使用這個專案，您可以指定物件的 .NET 型別名稱、物件的選擇集，或指定何時使用定義的選取條件。 如需如何建立選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

下列 XML 元素可以用來指定寬視圖的特定定義所使用的物件：

- [之 entryselectedby](./entryselectedby-element-for-wideentry-format.md)元素會定義定義要顯示的物件。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素會指定定義所顯示的 .net。 使用此元素時，需要完整的 .NET 類型名稱。 您必須為定義至少指定一個類型、選擇集或選取條件，但不能指定的元素數目上限。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素（未顯示）會指定一組可由這個定義顯示的物件。 您必須為定義至少指定一個類型、選擇集或選取條件，但不能指定的元素數目上限。

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)元素（未顯示）會指定必須存在才能使用此定義的條件。 您必須為定義至少指定一個類型、選擇集或選取條件，但不能指定的元素數目上限。 如需定義選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>以寬視圖顯示物件群組

您可以將寬視圖所顯示的物件分隔成群組。 這並不表示您定義群組，只有當特定屬性或腳本的值變更時，Windows PowerShell 才會啟動新的群組。 在下列範例中，每當 [ [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) ] 屬性的值變更時，就會啟動新的群組。

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

下列 XML 元素可用來定義何時啟動群組：

- [GroupBy](./groupby-element-for-view-format.md)元素會定義啟動新群組的屬性或腳本，並定義群組的顯示方式。

- [PropertyName](./propertyname-element-for-groupby-format.md)元素會指定在每次其值變更時啟動新群組的屬性。 您必須指定要啟動群組的屬性或腳本，但不能同時指定兩者。

- [ScriptBlock](./scriptblock-element-for-groupby-format.md)元素會指定在每次其值變更時啟動新群組的腳本。 您必須指定腳本或屬性來啟動群組，但不能同時指定這兩者。

- [Label](./label-element-for-groupby-format.md)元素會定義在每個群組的開頭顯示的標籤。 除了此元素所指定的文字之外，Windows PowerShell 還會顯示觸發新群組的值，並在標籤前後加上空白行。 這個元素是選擇性的。

- [CustomControl](./customcontrol-element-for-groupby-format.md)元素會定義用來顯示資料的控制項。 這個元素是選擇性的。

- [CustomControlName](./customcontrolname-element-for-groupby-format.md)元素會指定用來顯示資料的通用或 view 控制項。 這個元素是選擇性的。

如需定義群組之完整格式檔案的範例，請參閱[寬視圖（GroupBy）](./wide-view-groupby.md)。

## <a name="using-format-strings"></a>使用格式字串

將字串格式化可以加入至寬視圖，以進一步定義資料的顯示方式。 下列範例顯示如何為 `StartTime` 屬性的值定義格式字串。

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

下列 XML 元素可以用來指定格式模式：

- [之 wideitem](./wideitem-element-for-widecontrol-format.md)元素會指定視圖所顯示的資料。

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素會指定屬性，其值會由視圖顯示。 您必須指定屬性或腳本，但不能同時指定這兩者。

- [[字串](./formatstring-element-for-wideitem-for-widecontrol-format.md)類型] 元素會指定格式模式，以定義屬性或腳本值在視圖中的顯示方式。

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素（未顯示）會指定由視圖顯示其值的腳本。 您必須指定腳本或屬性，但不能同時指定這兩者。

在下列範例中，會呼叫 `ToString` 方法來格式化腳本的值。 腳本可以呼叫物件的任何方法。 因此，如果物件具有具有格式化參數的方法（例如 `ToString`），則腳本可以呼叫該方法來格式化腳本的輸出值。

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

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素（未顯示）會指定由視圖顯示其值的腳本。 您必須指定腳本或屬性，但不能同時指定這兩者。

## <a name="see-also"></a>另請參閱

[寬視圖（基本）](./wide-view-basic.md)

[全形視圖（GroupBy）](./wide-view-groupby.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
