---
title: " (基本) 的清單視圖 |Microsoft Docs"
ms.date: 09/13/2016
ms.openlocfilehash: 74ff8f6eee0a9358c123455aa00736a11e7f085d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783546"
---
# <a name="list-view-basic"></a>清單檢視 (基本)

這個範例示範如何執行會顯示 System.serviceprocess.dll. Servicecontroller 的基本欄表視圖[？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)由[Get-服務](/powershell/module/microsoft.powershell.management/get-service)Cmdlet 傳回的 Fullname 物件。 如需清單視圖之元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

### <a name="to-load-this-formatting-file"></a>載入此格式檔案

1. 將本主題的範例一節中的 XML 複製到文字檔中。

2. 儲存文字檔案。 請務必將擴充功能新增 `format.ps1xml` 至檔案，以將其識別為格式化檔案。

3. 開啟 Windows PowerShell，然後執行下列命令，將格式檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile` 。

   > [!WARNING]
   > 此格式檔案會定義已由 Windows PowerShell 格式化檔案所定義的物件顯示。 `prependPath`當您執行 Cmdlet 時，必須使用參數，而且無法將此格式檔案載入為模組。

## <a name="demonstrates"></a>示範

此格式檔案會示範下列 XML 元素：

- View 的[Name](./name-element-for-view-format.md)元素。

- 定義視圖所要顯示之物件的[ViewSelectedBy](./viewselectedby-element-format.md)元素。

- 定義視圖所要顯示之屬性的[ListControl](./listcontrol-element-format.md)元素。

- 定義要在清單視圖的資料列中顯示之專案[的 [專案](./listitem-element-for-listitems-for-listcontrol-format.md)類型] 元素。

- 定義要顯示哪一個屬性的[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。

## <a name="example"></a>範例

下列 XML 定義的清單視圖會顯示 System.serviceprocess.dll. Servicecontroller 的四個屬性[？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)物件。 在每個資料列中，屬性的名稱後面會顯示內容的值。

```xml
<Configuration>
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
</Configuration>
```

下列範例顯示 Windows PowerShell 如何顯示[system.serviceprocess.dll. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)載入此格式檔案後的 Fullname 物件。

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a>另請參閱

[格式設定檔案的範例](./examples-of-formatting-files.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
