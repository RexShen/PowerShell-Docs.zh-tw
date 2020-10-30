---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 取得 WMI 物件 Get-CimInstance
description: 本文會示範數個範例，說明如何從電腦系統取得 WMI 物件的執行個體。
ms.openlocfilehash: f7a005bbf39cf141e6474815d3e050314830453c
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500448"
---
# <a name="getting-wmi-objects-get-ciminstance"></a>取得 WMI 物件 (Get-CimInstance)

## <a name="getting-wmi-objects-get-ciminstance"></a>取得 WMI 物件 (Get-CimInstance)

Windows Management Instrumentation (WMI) 可以一致地公開各種不同的資訊，因此成為 Windows 系統管理的核心技術。 由於 WMI 的強大功能，使得用於存取 WMI 物件的 PowerShell Cmdlet `Get-CimInstance` 成為執行實際工作的最實用工具之一。 我們將討論如何使用 CimCmdlets 來存取 WMI 物件，並接著討論如何使用 WMI 物件來執行特定動作。

### <a name="listing-wmi-classes"></a>列出 WMI 類別

大多數 WMI 使用者遇到的第一個問題，就是嘗試了解使用 WMI 可執行的動作。 WMI 類別描述可管理的資源。 有數百個 WMI 類別，其中一些類別包含數十個屬性。

`Get-CimClass` 會藉由讓 WMI 變成可探索來解決此問題。 您可以輸入下列命令，取得本機電腦上可用的 WMI 類別清單：

```powershell
Get-CimClass -Namespace root/CIMV2 |
  Where-Object CimClassName -like Win32* |
    Select-Object CimClassName
```

```Output
CimClassName
------------
Win32_DeviceChangeEvent
Win32_SystemConfigurationChangeEvent
Win32_VolumeChangeEvent
Win32_SystemTrace
Win32_ProcessTrace
Win32_ProcessStartTrace
Win32_ProcessStopTrace
Win32_ThreadTrace
Win32_ThreadStartTrace
Win32_ThreadStopTrace
...
```

您可以藉由使用 **ComputerName** 並參數指定電腦名稱或 IP 位址，從遠端電腦擷取相同的資訊︰

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

遠端電腦所傳回的類別清單可能會因電腦執行的特定作業系統，以及已安裝應用程式新增的特定 WMI 擴充功能 而異。

> [!NOTE]
> 使用 CIM Cmdlet 來連線到遠端電腦時，遠端電腦必須執行 WMI，而且您使用的帳戶必須在遠端電腦上的本機 Administrators 群組中。
> 遠端系統不需要安裝 PowerShell。 這可讓您管理未執行 PowerShell 但有 WMI 可用的作業系統。

### <a name="displaying-wmi-class-details"></a>顯示 WMI 類別詳細資料

如果您已經知道 WMI 類別的名稱，您可以使用它來立即取得資訊。 例如，常用於擷取電腦相關資訊的其中一個 WMI 類別是 **Win32_OperatingSystem** 。

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

雖然我們會顯示所有參數，但命令可以更簡潔的方式來表示。
連線到本機系統時，不需要 **ComputerName** 參數。 顯示此參數是為了示範最常見的案例，並提醒您有此參數。 **Namespace** 預設為 `root/CIMV2`，您也可以予以省略。 最後，大多數 Cmdlet 允許您省略一般參數的名稱。 使用 `Get-CimInstance` 時，如果未指定第一個參數的名稱，PowerShell 會將它視為 **Class** 參數。 這表示最後一個命令可能已藉由輸入下列命令發出︰

```powershell
Get-CimInstance Win32_OperatingSystem
```

**Win32_OperatingSystem** 類別具有比此處顯示更多的屬性。 您可以使用 Get-Member 查看所有屬性。 WMI 類別的屬性與其他物件屬性一樣會自動提供使用︰

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Get-Member -MemberType Property
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_OperatingSystem
Name                                      MemberType Definition
----                                      ---------- ----------
BootDevice                                Property   string BootDevice {get;}
BuildNumber                               Property   string BuildNumber {get;}
BuildType                                 Property   string BuildType {get;}
Caption                                   Property   string Caption {get;}
CodeSet                                   Property   string CodeSet {get;}
CountryCode                               Property   string CountryCode {get;}
CreationClassName                         Property   string CreationClassName {get;}
CSCreationClassName                       Property   string CSCreationClassName {get;}
CSDVersion                                Property   string CSDVersion {get;}
CSName                                    Property   string CSName {get;}
CurrentTimeZone                           Property   short CurrentTimeZone {get;}
DataExecutionPrevention_32BitApplications Property   bool DataExecutionPrevention_32BitApplications {get;}
DataExecutionPrevention_Available         Property   bool DataExecutionPrevention_Available {get;}
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>使用 Format Cmdlet 顯示非預設屬性

如果您需要預設未顯示之 **Win32_OperatingSystem** 類別中所包含的資訊，您可以使用 **Format** Cmdlet 顯示此類別。 例如，如果您想要顯示可用記憶體資料，請輸入︰

```powershell
Get-CimInstance -Class Win32_OperatingSystem |
  Format-Table -Property TotalVirtualMemorySize, TotalVisibleMemorySize,
    FreePhysicalMemory, FreeVirtualMemory, FreeSpaceInPagingFiles
```

```Output
TotalVirtualMemorySize TotalVisibleMemorySize FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------------- ------------------ ----------------- ----------------------
              33449088               16671872            6451868          18424496               16285032
```

> [!NOTE]
> 萬用字元可在 `Format-Table` 中搭配屬性名稱使用，因此最後的管線元素可縮減成 `Format-Table -Property Total*Memory*, Free*`

如果您輸入下列命令，將記憶體資料格式化為清單，可能更容易閱讀︰

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Format-List Total*Memory*, Free*
```

```Output
TotalVirtualMemorySize : 33449088
TotalVisibleMemorySize : 16671872
FreePhysicalMemory     : 6524456
FreeSpaceInPagingFiles : 16285808
FreeVirtualMemory      : 18393668
Name                   : Microsoft Windows 10 Pro|C:\WINDOWS|\Device\Harddisk0\Partition2
```
