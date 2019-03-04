---
title: 寬型檢視 (GroupBy) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861624"
---
# <a name="wide-view-groupby"></a>寬型檢視 (GroupBy)

此範例示範如何實作顯示群組的寬型檢視[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)所傳回的物件`Get-Service`cmdlet。 如需詳細的寬型檢視元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。

### <a name="to-load-this-formatting-file"></a>若要載入此格式的檔案

1. 本主題的範例 > 一節的 XML 複製到文字檔。

2. 儲存文字檔案。 請務必新增`format.ps1xml`至檔案，以將它識別為格式化檔案的副檔名。

3. 開啟 Windows PowerShell，然後執行下列命令將目前的工作階段中載入的格式化檔案： `Update-formatdata -prependpath PathToFormattingFile`。

   > [!WARNING]
   > 此格式的檔案定義 Windows PowerShell 格式化檔案已經定義的物件的顯示。 您必須使用`prependPath`參數，當您執行 cmdlet，而且您無法載入此格式檔案為模組。

## <a name="demonstrates"></a>示範

這個格式檔會示範下列的 XML 項目：

- [名稱](./name-element-for-view-format.md)檢視的項目。

- [ViewSelectedBy](./viewselectedby-element-format.md)會定義哪些物件檢視所顯示的項目。

- [GroupBy](./groupby-element-for-view-format.md)定義新的群組時顯示的項目。

- [WideItem](./wideitem-element-for-widecontrol-format.md)定義哪些屬性會顯示由檢視項目。

## <a name="example"></a>範例

下列 XML 定義的寬型檢視，顯示物件的群組。 在啟動每個新的群組時的值[System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)屬性變更。

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

下列範例會示範 Windows PowerShell 的顯示方式[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)物件載入這個格式檔案之後。

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

[格式檔案的範例](./examples-of-formatting-files.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
