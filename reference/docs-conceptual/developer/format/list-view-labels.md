---
title: 清單視圖（標籤） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362787"
---
# <a name="list-view-labels"></a>清單檢視 (標籤)

這個範例示範如何執行清單視圖，以顯示清單中每個資料列的自訂標籤。 此清單視圖會顯示[system.serviceprocess.dll. Servicecontroller 的屬性？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)由[Get-服務](/powershell/module/Microsoft.PowerShell.Management/Get-Service)Cmdlet 傳回的 Fullname 物件。 如需清單視圖之元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

### <a name="to-load-this-formatting-file"></a>載入此格式檔案

1. 將本主題的範例一節中的 XML 複製到文字檔中。

2. 儲存文字檔。 請務必將 `format.ps1xml` 擴充功能新增至檔案，以將其識別為格式化檔案。

3. 開啟 Windows PowerShell，然後執行下列命令，將格式檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile`。

   > [!WARNING]
   > 此格式檔案會定義已由 Windows PowerShell 格式化檔案所定義的物件顯示。 當您執行 Cmdlet 時，必須使用 `prependPath` 參數，而且無法將此格式檔案載入為模組。

## <a name="demonstrates"></a>示範

此格式檔案會示範下列 XML 元素：

- View 的[Name](./name-element-for-view-format.md)元素。

- 定義視圖所要顯示之物件的[ViewSelectedBy](./viewselectedby-element-format.md)元素。

- 定義視圖所要顯示之屬性的[ListControl](./listcontrol-element-format.md)元素。

- 定義要在清單視圖的資料列中顯示之專案[的 [專案](./listitem-element-for-listitems-for-listcontrol-format.md)類型] 元素。

- [Label](./label-element-for-listitem-for-listcontrol-format.md)元素，定義要在清單視圖的資料列中顯示的內容。

- 定義要顯示哪一個屬性的[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。

## <a name="example"></a>範例

下列 XML 會定義清單視圖，以在每個資料列中顯示自訂標籤。 在此情況下，標籤會包含屬性名稱，其中每個字母都大寫，而 "property" 一字。 在每個資料列中，屬性的名稱後面會顯示內容的值。

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

下列範例顯示 Windows PowerShell 如何顯示[system.serviceprocess.dll. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)載入此格式檔案後的 Fullname 物件。

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

[格式檔案的範例](./examples-of-formatting-files.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
