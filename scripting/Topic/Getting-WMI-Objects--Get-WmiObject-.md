---
title: 取得 WMI 物件 (Get-WmiObject)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
---
# 取得 WMI 物件 (Get-WmiObject)

## 取得 WMI 物件 (Get-WmiObject)
Windows Management Instrumentation (WMI) 可以一致地公開各種不同的資訊，因此成為 Windows 系統管理的核心技術。 由於 WMI 的強大功能，用於存取 WMI 物件的 Windows PowerShell Cmdlet **Get-WmiObject** 是執行實際工作的最實用工具之一。 我們將討論如何使用 Get-WmiObject 存取 WMI 物件，並接著討論如何使用 WMI 物件執行特定動作。

### 列出 WMI 類別
大多數 WMI 使用者遇到的第一個問題，就是嘗試了解使用 WMI 可執行的動作。 WMI 類別描述可管理的資源。 有數百個 WMI 類別，其中一些類別包含數十個屬性。

**Get-WmiObject** 讓 WMI 變成可搜尋，以解決此問題。 您可以輸入下列命令，取得本機電腦上可用的 WMI 類別清單：

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

您可以使用 ComputerName 參數指定電腦名稱或 IP 位址，從遠端電腦擷取相同的資訊︰

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

遠端電腦所傳回的類別清單可能會因電腦執行的特定作業系統，以及已安裝應用程式新增的特定 WMI 擴充功能 而異。

> [!NOTE]
> 使用 Get-WmiObject 連線到遠端電腦時，遠端電腦必須執行 WMI，而且根據預設設定，您使用的帳戶必須在遠端電腦上的本機 Administrators 群組中。 遠端系統不需要安裝 Windows PowerShell。 這可讓您管理未執行 Windows PowerShell 但有可用 WMI 的作業系統。

您甚至可以在連線到本機系統時包含 ComputerName。 您可以使用本機電腦的名稱、其 IP 位址 (或迴路位址 127.0.0.1) 或 WMI 樣式 '.' 作為電腦名稱。 如果您在名為 Admin01 且 IP 位址為 192.168.1.90 的電腦上執行 Windows PowerShell，下列命令全部會傳回該電腦的 WMI 類別清單︰

```
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject 預設使用 root/cimv2 命名空間。 如果您想要指定其他 WMI 命名空間，請使用 **Namespace** 參數並指定對應的命名空間路徑︰

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### 顯示 WMI 類別詳細資料
如果您已經知道 WMI 類別的名稱，您可以使用它來立即取得資訊。 例如，常用於擷取電腦相關資訊的其中一個 WMI 類別是 **Win32_OperatingSystem**。

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

雖然我們會顯示所有參數，但命令可以更簡潔的方式來表示。 連線到本機系統時，不需要 **ComputerName** 參數。 顯示此參數是為了示範最常見的案例，並提醒您有此參數。 **Namespace** 預設為 root/cimv2，您也可以加以省略。 最後，大多數 Cmdlet 允許您省略一般參數的名稱。 使用 Get-WmiObject，如果未指定第一個參數的名稱，Windows PowerShell 會將它視為 **Class** 參數。 這表示最後一個命令可能已藉由輸入下列命令發出︰

```
Get-WmiObject Win32_OperatingSystem
```

**Win32_OperatingSystem** 類別具有比此處顯示更多的屬性。 您可以使用 Get-Member 查看所有屬性。 WMI 類別的屬性與其他物件屬性一樣會自動提供使用︰

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### 使用 Format Cmdlet 顯示非預設屬性
如果您需要預設未顯示之 **Win32_OperatingSystem** 類別中所包含的資訊，您可以使用 **Format** Cmdlet 顯示此類別。 例如，如果您想要顯示可用記憶體資料，請輸入︰

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMem FreePhysicalMem FreeVirtualMemo FreeSpaceInPagi
                              ory              ry         ngFiles
--------------- --------------- --------------- --------------- ---------------
        2097024          785904          305808         2056724         1558232
```

> [!NOTE]
> **Format-Table** 中的屬性名稱可以使用萬用字元，因此最後的管線項目可縮減為 **Format-Table -Property TotalV&#42;,Free&#42;**

如果您輸入下列命令，將記憶體資料格式化為清單，可能更容易閱讀︰

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```



<!--HONumber=Apr16_HO1-->


