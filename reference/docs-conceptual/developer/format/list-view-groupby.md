---
ms.date: 09/13/2016
ms.topic: reference
title: 清單檢視 (GroupBy)
description: 清單檢視 (GroupBy)
ms.openlocfilehash: e039c38d1e4e93f65a508fe60aaaf35c64ebe2ed
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666615"
---
# <a name="list-view-groupby"></a>清單檢視 (GroupBy)

這個範例示範如何執行清單視圖，將清單中的資料列分隔成群組。 此清單視圖會顯示 System.serviceprocess.dll 的屬性 [。 Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) [取得服務](/powershell/module/Microsoft.PowerShell.Management/Get-Service) Cmdlet 所傳回的 Fullname 物件。 如需清單視圖元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。

### <a name="to-load-this-formatting-file"></a>載入此格式化檔案

1. 將本主題的範例一節中的 XML 複製到文字檔。

2. 儲存文字檔案。 請務必將副檔名新增 `format.ps1xml` 至檔案，以將它識別為格式化檔案。

3. 開啟 Windows PowerShell，然後執行下列命令，將格式化檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile` 。

   > [!WARNING]
   > 此格式化檔案會定義已由 Windows PowerShell 格式設定檔案定義之物件的顯示。 `prependPath`當您執行 Cmdlet 時，您必須使用參數，而且無法將此格式化檔案載入為模組。

## <a name="demonstrates"></a>示範

此格式化檔案示範下列 XML 元素：

- 視圖的 [名稱](./name-element-for-view-format.md) 元素。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素，定義視圖要顯示的物件。

- [GroupBy](./viewselectedby-element-format.md)專案，定義如何顯示新的物件群組。

- [ListControl](./listcontrol-element-format.md)元素，定義視圖顯示的屬性。

- 專案 [清單元素，](./listitem-element-for-listitems-for-listcontrol-format.md) 定義清單視圖的資料列中顯示的內容。

- 定義要顯示之屬性的 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 元素。

## <a name="example"></a>範例

下列 XML 會定義每次 [System.serviceprocess.dll Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.Status) 的值變更時，會啟動新群組的清單視圖。 當每個群組都啟動時，會顯示包含屬性新值的自訂標籤。

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
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
                <PropertyName>ServiceType</PropertyName>
              </ListItem>
            </ListItems>
          </ListEntry>
        </ListEntries>
      </ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

下列範例顯示 Windows PowerShell 如何顯示 [system.serviceprocess.dll. Servicecontroller？](/dotnet/api/System.ServiceProcess.ServiceController) 在載入此格式檔案之後，Displayproperty = Fullname 物件。 Windows PowerShell 會自動加入群組標籤前後新增的空白行。

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a>另請參閱

[格式設定檔案的範例](./examples-of-formatting-files.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
