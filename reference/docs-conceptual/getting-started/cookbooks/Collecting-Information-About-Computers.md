---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 收集電腦的相關資訊
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: ca92474eaf6fa546c3d6450f5a282e45157018a8
ms.sourcegitcommit: 4a841ebda3339ae2477e0f5f5be8c01740221232
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33677309"
---
# <a name="collecting-information-about-computers"></a>收集電腦的相關資訊

針對一般系統管理作業，**CimCmdlet** 模組的 Cmdlet 是最重要的 Cmdlet。
所有重要的子系統設定都是透過 WMI 公開。
此外，WMI 會將資料視為一或多個項目集合中的物件。
由於 Windows PowerShell 也適用於物件，並具有管線可讓您以相同的方式來處理單一物件或多個物件，因此一般 WMI 存取可讓您不費吹灰之力就能執行一些進階工作。

下列範例示範如何對任意電腦使用 `Get-CimInstance` 來收集特定資訊。
我們以點值 (**.**) 指定 **ComputerName** 參數，以代表本機電腦。
您可以指定與可透過 WMI 連線之任何電腦來建立關聯的名稱或 IP 位址。
若要擷取本機電腦的相關資訊，您可以省略 **ComputerName** 參數。

### <a name="listing-desktop-settings"></a>列出桌面設定

我們一開始會使用命令，收集本機電腦上的桌面資訊。

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

這會傳回所有桌面資訊，而不論其是否正在使用。

> [!NOTE]
> 有些 WMI 類別傳回的資訊可能非常詳細，通常包含 WMI 類別的相關中繼資料。
由於大多數中繼資料屬性的名稱均以 **Cim** 開頭，因此您可以使用 `Select-Object` 來篩選屬性。
搭配使用 **-ExcludeProperty** 參數與 "Cim*"，將其指定為值。
例如：

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

若要篩選出中繼資料，請使用管線運算子 (|) 將 `Get-CimInstance` 命令的結果傳送至 `Select-Object -ExcludeProperty "CIM*"`。

### <a name="listing-bios-information"></a>列出 BIOS 資訊

WMI **Win32_BIOS** 類別會傳回本機電腦系統 BIOS 的精簡與完整相關資訊︰

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>列出處理器資訊

您可以使用 WMI 的 **Win32_Processor** 類別擷取一般處理器資訊，不過您可能會想要篩選此資訊︰

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

針對處理器系列的一般描述字串，您可以只傳回 **SystemType** 屬性︰

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>列出電腦製造商和型號

**Win32_ComputerSystem** 也會提供電腦型號資訊。
顯示的標準輸出不需要任何篩選，就能提供 OEM 資料︰

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

類似此命令的輸出會直接傳回一些硬體的資訊，只會顯示您擁有的資料。
有些資訊未經過硬體製造商的正確設定，因此可能無法使用。

### <a name="listing-installed-hotfixes"></a>列出安裝的 Hotfix

您可以使用 **Win32_QuickFixEngineering** ，列出所有安裝的 Hotfix：

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

此類別會傳回類似如下的 Hotfix 清單：

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

如需更簡潔的輸出，您可能需要排除一些屬性。
雖然您可以使用 `Get-CimInstance` 的 **Property** 參數來僅選擇 **HotFixID**，但這麼做實際上會傳回更多資訊，因為預設為顯示所有中繼資料︰

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID
```

```output
PSShowComputerName    : True
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4048951
InstalledBy           :
ServicePackInEffect   :
PSComputerName        : .
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

由於 `Get-CimInstance` 中的 Property 參數會限制從 WMI 類別執行個體傳回的屬性，而不是傳回給 Windows PowerShell 的物件，因此會傳回更多資料。
若要縮減輸出，請使用 `Select-Object`：

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a>列出作業系統版本資訊

**Win32_OperatingSystem** 類別屬性包含版本和 Service Pack 資訊。
您可以明確地只選取這些屬性，以從 **Win32_OperatingSystem** 取得版本資訊摘要：

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

`Select-Object` 的 **Property** 參數也可以使用萬用字元。
由於必須在此使用以 **Build** 或 **ServicePack** 開頭的所有屬性，因此可將此縮短為下列格式：

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*
```

```output
BuildNumber             : 16299
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a>列出本機使用者和擁有者

選取 **Win32_OperatingSystem** 類別的屬性可找到本機使用者的一般資訊 (授權使用者數目、目前的使用者數目和擁有者名稱)。
您可以明確地選取要顯示的屬性，如下所示︰

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

使用萬用字元的更簡潔版本為︰

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>取得可用的磁碟空間

若要查看本機磁碟機的磁碟空間和可用空間，您可以使用 Win32_LogicalDisk WMI 類別。
您只需要查看 DriveType 為 3 的執行個體，因為 WMI 會針對固定式硬碟使用這個值。

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .

Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a>取得登入工作階段資訊

您可以透過 **Win32_LogonSession** WMI 類別，取得與使用者相關聯的登入工作階段一般資訊︰

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>取得登入電腦的使用者

您可以使用 Win32_ComputerSystem，顯示登入特定電腦系統的使用者。
此命令只會傳回登入系統桌面的使用者︰

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>取得電腦的當地時間

您可以使用 **Win32_LocalTime** WMI 類別，擷取特定電腦上的目前當地時間。

```powershell
Get-CimInstance -ClassName Win32_LocalTime -ComputerName .

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2017
PSComputerName : .
```

### <a name="displaying-service-status"></a>顯示服務狀態

若要檢視特定電腦的所有服務狀態，您可以在本機上使用 `Get-Service` Cmdlet。
若為遠端系統，您可以使用 **Win32_Service** WMI 類別。
如果您同時使用 `Select-Object` 將結果篩選為 **Status**、**Name** 和 **DisplayName**，輸出格式會與 `Get-Service` 的輸出格式幾乎完全相同：

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

若要完整顯示名稱很長的不定期服務名稱，您可將 `Format-Table` 與 **AutoSize** 及 **Wrap** 參數搭配使用，以最佳化資料行寬度，並讓長名稱換行而不是被截斷︰

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
