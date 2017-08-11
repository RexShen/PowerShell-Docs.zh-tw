---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "收集電腦的相關資訊"
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: c0b7ec9ed7d2b07c66d2b1cf3342f971d71da481
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="a2c2c-103">收集電腦的相關資訊</span><span class="sxs-lookup"><span data-stu-id="a2c2c-103">Collecting Information About Computers</span></span>
<span data-ttu-id="a2c2c-104">**Get-WmiObject** 是一般系統管理工作最重要的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-104">**Get-WmiObject** is the most important cmdlet for general system management tasks.</span></span> <span data-ttu-id="a2c2c-105">所有重要的子系統設定都是透過 WMI 公開。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-105">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="a2c2c-106">此外，WMI 會將資料視為一或多個項目集合中的物件。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="a2c2c-107">由於 Windows PowerShell 也適用於物件，並具有管線可讓您以相同的方式來處理單一物件或多個物件，因此一般 WMI 存取可讓您不費吹灰之力就能執行一些進階工作。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="a2c2c-108">下列範例示範如何對任意電腦使用 **Get-WmiObject** 來收集特定資訊。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-108">The following examples demonstrate how to collect specific information by using **Get-WmiObject** against an arbitrary computer.</span></span> <span data-ttu-id="a2c2c-109">我們以點值 (**.**) 指定 **ComputerName** 參數，以代表本機電腦。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span> <span data-ttu-id="a2c2c-110">您可以指定與可透過 WMI 連線之任何電腦來建立關聯的名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span> <span data-ttu-id="a2c2c-111">若要擷取本機電腦的相關資訊，您可以省略 **-ComputerName.**。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-111">To retrieve information about the local computer, you could omit the **-ComputerName.**</span></span>

### <a name="listing-desktop-settings"></a><span data-ttu-id="a2c2c-112">列出桌面設定</span><span class="sxs-lookup"><span data-stu-id="a2c2c-112">Listing Desktop Settings</span></span>
<span data-ttu-id="a2c2c-113">我們一開始會使用命令，收集本機電腦上的桌面資訊。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

<span data-ttu-id="a2c2c-114">這會傳回所有桌面資訊，而不論其是否正在使用。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="a2c2c-115">有些 WMI 類別傳回的資訊可能非常詳細，通常包含 WMI 類別的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span> <span data-ttu-id="a2c2c-116">由於大多數中繼資料屬性具有以雙底線開頭的名稱，因此您可以使用 Select-Object 篩選屬性。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-116">Because most of these metadata properties have names that begin with a double underscore, you can filter the properties using Select-Object.</span></span> <span data-ttu-id="a2c2c-117">使用 **[a-z]*** 作為屬性值，可指定只以字母字元開頭的屬性。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-117">Specify only properties that begin with alphabetic characters by using **[a-z]*** as the Property value.</span></span> <span data-ttu-id="a2c2c-118">例如：</span><span class="sxs-lookup"><span data-stu-id="a2c2c-118">For example:</span></span>

```
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="a2c2c-119">若要篩選出中繼資料，請使用管線運算子 (|) 將 Get-WmiObject 命令的結果傳送至 **Select-Object -Property [a-z]***。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-119">To filter out the metadata, use a pipeline operator (|) to send the results of the Get-WmiObject command to **Select-Object -Property [a-z]***.</span></span>

### <a name="listing-bios-information"></a><span data-ttu-id="a2c2c-120">列出 BIOS 資訊</span><span class="sxs-lookup"><span data-stu-id="a2c2c-120">Listing BIOS Information</span></span>
<span data-ttu-id="a2c2c-121">WMI Win32_BIOS 類別會傳回本機電腦上 BIOS 系統極精簡且完整的相關資訊︰</span><span class="sxs-lookup"><span data-stu-id="a2c2c-121">The WMI Win32_BIOS class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a><span data-ttu-id="a2c2c-122">列出處理器資訊</span><span class="sxs-lookup"><span data-stu-id="a2c2c-122">Listing Processor Information</span></span>
<span data-ttu-id="a2c2c-123">您可以使用 WMI 的 **Win32_Processor** 類別擷取一般處理器資訊，不過您可能會想要篩選此資訊︰</span><span class="sxs-lookup"><span data-stu-id="a2c2c-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="a2c2c-124">針對處理器系列的一般描述字串，您可以只傳回 **SystemType** 屬性︰</span><span class="sxs-lookup"><span data-stu-id="a2c2c-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType
SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="a2c2c-125">列出電腦製造商和型號</span><span class="sxs-lookup"><span data-stu-id="a2c2c-125">Listing Computer Manufacturer and Model</span></span>
<span data-ttu-id="a2c2c-126">**Win32_ComputerSystem** 也會提供電腦型號資訊。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span> <span data-ttu-id="a2c2c-127">顯示的標準輸出不需要任何篩選，就能提供 OEM 資料︰</span><span class="sxs-lookup"><span data-stu-id="a2c2c-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem
Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

<span data-ttu-id="a2c2c-128">類似此命令的輸出會直接傳回一些硬體的資訊，只會顯示您擁有的資料。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="a2c2c-129">有些資訊未經過硬體製造商的正確設定，因此可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

### <a name="listing-installed-hotfixes"></a><span data-ttu-id="a2c2c-130">列出安裝的 Hotfix</span><span class="sxs-lookup"><span data-stu-id="a2c2c-130">Listing Installed Hotfixes</span></span>
<span data-ttu-id="a2c2c-131">您可以使用 **Win32_QuickFixEngineering** ，列出所有安裝的 Hotfix：</span><span class="sxs-lookup"><span data-stu-id="a2c2c-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="a2c2c-132">此類別會傳回類似如下的 Hotfix 清單：</span><span class="sxs-lookup"><span data-stu-id="a2c2c-132">This class returns a list of hotfixes that looks like this:</span></span>

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

<span data-ttu-id="a2c2c-133">如需更簡潔的輸出，您可能需要排除一些屬性。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-133">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="a2c2c-134">雖然您可以使用 **Get-WmiObject 的 Property** 參數只選擇 **HotFixID**，但這麼做實際上會傳回更多資訊，因為預設會顯示所有中繼資料︰</span><span class="sxs-lookup"><span data-stu-id="a2c2c-134">Although you can use the **Get-WmiObject's Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixID
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

<span data-ttu-id="a2c2c-135">由於 **Get-WmiObject** 中的 Property 參數會限制從 WMI 類別執行個體傳回的屬性，而不是傳回至 Windows PowerShell 的物件，因此會傳回更多資料。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-135">The additional data is returned, because the Property parameter in **Get-WmiObject** restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span> <span data-ttu-id="a2c2c-136">若要縮減輸出，請使用 **Select-Object**：</span><span class="sxs-lookup"><span data-stu-id="a2c2c-136">To reduce the output, use **Select-Object**:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property Hot
FixId | Select-Object -Property HotFixId
HotFixId
--------
KB910437
```

### <a name="listing-operating-system-version-information"></a><span data-ttu-id="a2c2c-137">列出作業系統版本資訊</span><span class="sxs-lookup"><span data-stu-id="a2c2c-137">Listing Operating System Version Information</span></span>
<span data-ttu-id="a2c2c-138">**Win32_OperatingSystem** 類別屬性包含版本和 Service Pack 資訊。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="a2c2c-139">您可以明確地只選取這些屬性，以從 **Win32_OperatingSystem** 取得版本資訊摘要：</span><span class="sxs-lookup"><span data-stu-id="a2c2c-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="a2c2c-140">**Select-Object 的 Property** 參數也可以使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-140">You can also use wildcards with the **Select-Object's Property** parameter.</span></span> <span data-ttu-id="a2c2c-141">由於必須在此使用以 **Build** 或 **ServicePack** 開頭的所有屬性，因此可將此縮短為下列格式：</span><span class="sxs-lookup"><span data-stu-id="a2c2c-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a><span data-ttu-id="a2c2c-142">列出本機使用者和擁有者</span><span class="sxs-lookup"><span data-stu-id="a2c2c-142">Listing Local Users and Owner</span></span>
<span data-ttu-id="a2c2c-143">選取 **Win32_OperatingSystem** 屬性可找到本機使用者的一般資訊 (授權使用者數目、目前的使用者數目和擁有者名稱)。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-143">Local general user information—number of licensed users, current number of users, and owner name—can be found with a selection of **Win32_OperatingSystem** properties.</span></span> <span data-ttu-id="a2c2c-144">您可以明確地選取要顯示的屬性，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="a2c2c-144">You can explicitly select the properties to display like this:</span></span>

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="a2c2c-145">使用萬用字元的更簡潔版本為︰</span><span class="sxs-lookup"><span data-stu-id="a2c2c-145">A more succinct version using wildcards is:</span></span>

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a><span data-ttu-id="a2c2c-146">取得可用的磁碟空間</span><span class="sxs-lookup"><span data-stu-id="a2c2c-146">Getting Available Disk Space</span></span>
<span data-ttu-id="a2c2c-147">若要查看本機磁碟機的磁碟空間和可用空間，您可以使用 WMI Win32_LogicalDisk 類別。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-147">To see the disk space and free space for local drives, you can use the WMI Win32_LogicalDisk class.</span></span> <span data-ttu-id="a2c2c-148">您只需要查看 DriveType 為 3 的執行個體 (WMI 針對固定式硬碟使用此值)。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-148">You need to see only instances with a DriveType of 3—the value WMI uses for fixed hard disks.</span></span>

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

Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum
```

### <a name="getting-logon-session-information"></a><span data-ttu-id="a2c2c-149">取得登入工作階段資訊</span><span class="sxs-lookup"><span data-stu-id="a2c2c-149">Getting Logon Session Information</span></span>
<span data-ttu-id="a2c2c-150">您可以透過 WMI Win32_LogonSession 類別，取得與使用者相關聯之登入工作階段的一般資訊︰</span><span class="sxs-lookup"><span data-stu-id="a2c2c-150">You can get general information about logon sessions associated with users through the WMI Win32_LogonSession class:</span></span>

```
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="a2c2c-151">取得登入電腦的使用者</span><span class="sxs-lookup"><span data-stu-id="a2c2c-151">Getting the User Logged on to a Computer</span></span>
<span data-ttu-id="a2c2c-152">您可以使用 Win32_ComputerSystem，顯示登入特定電腦系統的使用者。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="a2c2c-153">此命令只會傳回登入系統桌面的使用者︰</span><span class="sxs-lookup"><span data-stu-id="a2c2c-153">This command returns only the user logged on to the system desktop:</span></span>

```
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="a2c2c-154">取得電腦的當地時間</span><span class="sxs-lookup"><span data-stu-id="a2c2c-154">Getting Local Time from a Computer</span></span>
<span data-ttu-id="a2c2c-155">您可以使用 WMI Win32_LocalTime 類別，擷取特定電腦上的目前當地時間。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-155">You can retrieve the current local time on a specific computer by using the WMI Win32_LocalTime class.</span></span> <span data-ttu-id="a2c2c-156">由於此類別預設會顯示所有中繼資料，因此建議您使用 **Select-Object** 加以篩選：</span><span class="sxs-lookup"><span data-stu-id="a2c2c-156">Because this class by default displays all metadata, you may want to filter it using **Select-Object**:</span></span>

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

### <a name="displaying-service-status"></a><span data-ttu-id="a2c2c-157">顯示服務狀態</span><span class="sxs-lookup"><span data-stu-id="a2c2c-157">Displaying Service Status</span></span>
<span data-ttu-id="a2c2c-158">若要檢視特定電腦上的所有服務狀態，您可以在本機使用上述 **Get-Service** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-158">To view the status of all services on a specific computer, you can locally use the **Get-Service** cmdlet as mentioned earlier.</span></span> <span data-ttu-id="a2c2c-159">若為遠端系統，您可以使用 WMI Win32_Service 類別。</span><span class="sxs-lookup"><span data-stu-id="a2c2c-159">For remote systems, you can use the WMI Win32_Service class.</span></span> <span data-ttu-id="a2c2c-160">如果您同時使用 **Select-Object** 將結果篩選為 **Status**、**Name** 和 **DisplayName**，輸出格式會與 **Get-Service** 的輸出格式幾乎完全相同：</span><span class="sxs-lookup"><span data-stu-id="a2c2c-160">If you also use **Select-Object** to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from **Get-Service**:</span></span>

```
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="a2c2c-161">若要允許完整顯示名稱很長的不定期服務名稱，您可將 **Format-Table** 和 **AutoSize** 及 **Wrap** 參數搭配使用，以將資料行寬度最佳化，並允許長名稱換行而不是被截斷︰</span><span class="sxs-lookup"><span data-stu-id="a2c2c-161">To allow the complete display of names for the occasional services with extremely long names, you may want to use **Format-Table** with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```

