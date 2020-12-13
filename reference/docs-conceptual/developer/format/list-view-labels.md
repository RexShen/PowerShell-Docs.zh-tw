---
ms.date: 09/13/2016
ms.topic: reference
title: 清單檢視 (標籤)
description: 清單檢視 (標籤)
ms.openlocfilehash: 2d341ae95d025e0f95b5d88b96afb846b62b092f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666683"
---
# <a name="list-view-labels"></a>清單檢視 (標籤)

此範例示範如何執行清單視圖，以針對清單中的每個資料列顯示自訂標籤。 此清單視圖會顯示 System.serviceprocess.dll 的屬性 [。 Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) [取得服務](/powershell/module/Microsoft.PowerShell.Management/Get-Service) Cmdlet 所傳回的 Fullname 物件。 如需清單視圖元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。

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

- [ListControl](./listcontrol-element-format.md)元素，定義視圖顯示的屬性。

- 專案 [清單元素，](./listitem-element-for-listitems-for-listcontrol-format.md) 定義清單視圖的資料列中顯示的內容。

- [Label](./label-element-for-listitem-for-listcontrol-format.md)元素，定義清單視圖的資料列中顯示的內容。

- 定義要顯示之屬性的 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 元素。

## <a name="example"></a>範例

下列 XML 定義的清單視圖會在每個資料列中顯示自訂標籤。 在此情況下，標籤會包含每個字母大寫的屬性名稱和 "property" 這個字。 在每個資料列中，屬性的名稱後面會顯示內容的值。

```xml
<Configuration>
  <ViewDefinitions>
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
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
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

下列範例顯示 Windows PowerShell 如何顯示 [system.serviceprocess.dll. Servicecontroller？](/dotnet/api/System.ServiceProcess.ServiceController) 在載入此格式檔案之後，Displayproperty = Fullname 物件。

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a>另請參閱

[格式設定檔案的範例](./examples-of-formatting-files.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
