---
title: 寬型檢視 (Basic) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083734"
---
# <a name="wide-view-basic"></a>寬型檢視 (基本)

此範例示範如何實作基本的寬型檢視會顯示[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)所傳回的物件`Get-Service`cmdlet。 如需詳細的寬型檢視元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。

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

- [WideItem](./wideitem-element-for-widecontrol-format.md)定義哪些屬性會顯示由檢視項目。

## <a name="example"></a>範例

下列 XML 定義顯示值的寬型檢視[System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName)屬性。

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a>另請參閱

[格式檔案的範例](./examples-of-formatting-files.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
