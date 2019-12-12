---
title: 寬視圖（基本） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367937"
---
# <a name="wide-view-basic"></a>寬型檢視 (基本)

這個範例示範如何執行會顯示 System.serviceprocess.dll. Servicecontroller 的基本寬視圖[？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) `Get-Service` Cmdlet 所傳回的 Fullname 物件。 如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

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

- 定義視圖所要顯示之屬性的[之 wideitem](./wideitem-element-for-widecontrol-format.md)元素。

## <a name="example"></a>範例

下列 XML 會定義顯示[system.serviceprocess.dll. Servicecontroller. Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName)屬性值的寬視圖。

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

下列範例顯示 Windows PowerShell 如何顯示[system.serviceprocess.dll. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)載入此格式檔案後的 Fullname 物件。

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
