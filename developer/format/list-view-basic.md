---
title: 清單檢視 (Basic) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065303"
---
# <a name="list-view-basic"></a>清單檢視 (基本)

此範例示範如何實作基本的清單檢視會顯示[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)所傳回的物件[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。 清單檢視元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。

### <a name="to-load-this-formatting-file"></a>若要載入此格式的檔案

1. 本主題的範例 > 一節的 XML 複製到文字檔。

2. 儲存文字檔案。 請務必新增`format.ps1xml`至檔案，以將它識別為格式化檔案的副檔名。

3. 開啟 Windows PowerShell，然後執行下列命令將目前的工作階段中載入的格式化檔案： `Update-formatdata -prependpath PathToFormattingFile`。

   > [!WARNING]
   > 此格式檔案會定義顯示的 Windows PowerShell 格式化檔案已經定義的物件。 您必須使用`prependPath`參數，當您執行 cmdlet，而且您無法載入此格式檔案為模組。

## <a name="demonstrates"></a>示範

這個格式檔會示範下列的 XML 項目：

- [名稱](./name-element-for-view-format.md)檢視的項目。

- [ViewSelectedBy](./viewselectedby-element-format.md)會定義哪些物件檢視所顯示的項目。

- [ListControl](./listcontrol-element-format.md)定義哪些屬性會顯示由檢視項目。

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)項目，定義 [清單] 檢視的資料列中顯示的內容。

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)定義會顯示哪一個屬性的項目。

## <a name="example"></a>範例

下列 XML 定義顯示的四個屬性的清單檢視[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)物件。 在每個資料列中，屬性的名稱會顯示後面之屬性的值。

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

下列範例會示範 Windows PowerShell 的顯示方式[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)物件載入這個格式檔案之後。

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

[格式檔案的範例](./examples-of-formatting-files.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
