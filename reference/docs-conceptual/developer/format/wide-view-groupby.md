---
ms.date: 09/13/2016
ms.topic: reference
title: 寬型檢視 (GroupBy)
description: 寬型檢視 (GroupBy)
ms.openlocfilehash: 807bea2a5d44c38e2c9977f792bea2fb9bca0fc3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667669"
---
# <a name="wide-view-groupby"></a>寬型檢視 (GroupBy)

此範例示範如何執行會顯示 System.serviceprocess.dll Servicecontroller 群組的廣泛視圖 [？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) Cmdlet 所傳回的 Fullname 物件 `Get-Service` 。 如需有關廣泛視圖元件的詳細資訊，請參閱 [建立廣泛的視圖](./creating-a-wide-view.md)。

### <a name="to-load-this-formatting-file"></a>載入此格式化檔案

1. 將本主題的範例一節中的 XML 複製到文字檔。

2. 儲存文字檔案。 請務必將副檔名新增 `format.ps1xml` 至檔案，以將它識別為格式化檔案。

3. 開啟 Windows PowerShell，然後執行下列命令，將格式化檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile` 。

   > [!WARNING]
   > 這個格式化檔案會定義已由 Windows PowerShell 格式檔案定義之物件的顯示。 `prependPath`當您執行 Cmdlet 時，您必須使用參數，而且無法將此格式化檔案載入為模組。

## <a name="demonstrates"></a>示範

此格式化檔案示範下列 XML 元素：

- 視圖的 [名稱](./name-element-for-view-format.md) 元素。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素，定義視圖要顯示的物件。

- 在顯示新群組時定義的 [GroupBy](./groupby-element-for-view-format.md) 元素。

- [之 wideitem](./wideitem-element-for-widecontrol-format.md)元素，定義視圖顯示的屬性。

## <a name="example"></a>範例

下列 XML 定義了顯示物件群組的廣泛視圖。 當 [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 屬性的值變更時，就會啟動每個新群組。

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

下列範例顯示 Windows PowerShell 如何顯示 [system.serviceprocess.dll. Servicecontroller？](/dotnet/api/System.ServiceProcess.ServiceController) 在載入此格式檔案之後，Displayproperty = Fullname 物件。

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a>另請參閱

[格式設定檔案的範例](./examples-of-formatting-files.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
