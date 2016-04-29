---
title: 收集電腦的相關資訊
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
---
# 收集電腦的相關資訊
**Get-WmiObject** 是一般系統管理工作的最重要 Cmdlet。 所有重要的子系統設定都是透過 WMI 公開。 此外，WMI 會將資料視為一或多個項目集合中的物件。 由於 Windows PowerShell 也適用於物件，並具有管線可讓您以相同的方式來處理單一物件或多個物件，因此一般 WMI 存取可讓您不費吹灰之力就能執行一些進階工作。

下列範例示範如何對任意電腦使用 **Get-WmiObject** 來收集特定資訊。 我們以點值 (**.**) 指定 **ComputerName** 參數，以代表本機電腦。 您可以指定與可透過 WMI 連線之任何電腦來建立關聯的名稱或 IP 位址。 若要擷取本機電腦的相關資訊，您可以省略 **-ComputerName**。

### 列出桌面設定
我們一開始會使用命令，收集本機電腦上的桌面資訊。

```
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

這會傳回所有桌面資訊，而不論其是否正在使用。

> [!NOTE]
> 有些 WMI 類別傳回的資訊可能非常詳細，通常包含 WMI 類別的相關中繼資料。 由於大多數中繼資料屬性具有以雙底線開頭的名稱，因此您可以使用 Select-Object 篩選屬性。 使用 **[a-z]&#42;** 作為屬性值，可指定只以字母字元開頭的屬性。 例如：

```
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

若要篩選出中繼資料，請使用管線運算子 (|) 將 Get-WmiObject 命令的結果傳送至 **Select-Object -Property [a-z]&#42;**。

### 列出 BIOS 資訊
WMI Win32_BIOS 類別會傳回有關本機電腦上 BIOS 系統的相當精簡且完整的資訊︰

```
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### 列出處理器資訊
您可以使用 WMI 的 **Win32_Processor** 類別擷取一般處理器資訊，不過您可能會想要篩選此資訊︰

```
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

針對處理器系列的一般描述字串，您可以只傳回 **Win32_ComputerSystemSystemType** 屬性︰

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType
SystemType
----------
X86-based PC
```

### 列出電腦製造商和型號
**Win32_ComputerSystem** 也會提供電腦型號資訊。 顯示的標準輸出不需要任何篩選，就能提供 OEM 資料︰

```
PS> Get-WmiObject -Class Win32_ComputerSystem
Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

類似此命令的輸出會直接傳回一些硬體的資訊，只會顯示您擁有的資料。 有些資訊未經過硬體製造商的正確設定，因此可能無法使用。

### 列出安裝的 Hotfix
您可以使用 **Win32_QuickFixEngineering** ，列出所有安裝的 Hotfix：

```
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

此類別會傳回類似如下的 Hotfix 清單：

```
Description         : Update for Windows XP (KB910437)
FixComments         : Update
HotFixID            : KB910437
Install Date        :
InstalledBy         : Administrator
InstalledOn         : 12/16/2005
Name                :
ServicePackInEffect : SP3
Status              :
```

如需更簡潔的輸出，您可能需要排除一些屬性。 雖然您可以使用 **Get-WmiObject Property** 參數只選擇 **HotFixID**，但這麼做實際上會傳回更多資訊，因為預設會顯示所有中繼資料︰

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId
HotFixID         : KB910437
__GENUS          : 2
__CLASS          : Win32_QuickFixEngineering
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
```

由於 **Get-WmiObject** 中的 Property 參數會限制從 WMI 類別執行個體傳回的屬性，而不是傳回至 Windows PowerShell 的物件，因此會傳回更多資料。 若要縮減輸出，請使用 **Select-Object**：

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property Hot
FixId | Select-Object -Property HotFixId
HotFixId
--------
KB910437
```

### 列出作業系統版本資訊
**Win32_OperatingSystem** 類別屬性包含版本和 Service Pack 資訊。 您可以明確地只選取這些屬性，以從 **Win32_OperatingSystem** 取得版本資訊摘要：

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

您也可以針對 **Select-Object Property** 參數使用萬用字元。 由於必須在此使用以 **Build** 或 **ServicePack** 開頭的所有屬性，因此可將此縮短為下列格式：

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### 列出本機使用者和擁有者
選取 **Win32_OperatingSystem** 屬性可找到本機使用者的一般資訊 (授權使用者數目、目前的使用者數目和擁有者名稱)。 您可以明確地選取要顯示的屬性，如下所示︰

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

使用萬用字元的更簡潔版本為︰

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### 取得可用的磁碟空間
若要查看本機磁碟機的磁碟空間和可用空間，您可以使用 WMI Win32_LogicalDisk 類別。 您只需要查看 DriveType 為 3 的執行個體 (WMI 針對固定式硬碟使用此值)。

```
Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 65541357568
Size         : 203912880128
VolumeName   : Local Disk

DeviceID     : Q:
DriveType    : 3
ProviderName :
FreeSpace    : 44298250240
Size         : 122934034432
VolumeName   : New Volume

PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum

Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum
```

### 取得登入工作階段資訊
您可以透過 WMI Win32_LogonSession 類別，取得與使用者相關聯之登入工作階段的一般資訊︰

```
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### 取得登入電腦的使用者
您可以使用 Win32_ComputerSystem，顯示登入特定電腦系統的使用者。 此命令只會傳回登入系統桌面的使用者︰

```
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### 取得電腦的當地時間
您可以使用 WMI Win32_LocalTime 類別，擷取特定電腦上的目前當地時間。 由於此類別預設會顯示所有中繼資料，因此您可能會想要使用 **Select-Object** 加以篩選：

```
PS> Get-WmiObject -Class Win32_LocalTime -ComputerName . | Select-Object -Property [a-z]*

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2006
```

### 顯示服務狀態
若要檢視特定電腦上的所有服務狀態，您可以在本機使用上述 **Get-Service** Cmdlet。 若為遠端系統，您可以使用 WMI Win32_Service 類別。 如果您同時使用 **Select-Object** 將結果篩選為 **Status**、**Name** 和 **DisplayName**，輸出格式會與 **Get-Service** 的輸出格式幾乎完全相同：

```
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

若要允許完整顯示名稱很長的不定期服務名稱，您可將 **Format-Table** 和 **AutoSize** 及 **Wrap** 參數搭配使用，以最佳化資料行寬度，並允許長名稱換行而不是被截斷︰

```
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```



<!--HONumber=Apr16_HO1-->


