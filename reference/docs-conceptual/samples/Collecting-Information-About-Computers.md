---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 收集電腦的相關資訊
description: 本文說明如何使用 WMI 與 CIM Cmdlet，收集電腦組態的相關資訊。
ms.openlocfilehash: 5088960ab7c049085a9d7c05ec4571b6fd7e3545
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500584"
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="ab584-104">收集電腦的相關資訊</span><span class="sxs-lookup"><span data-stu-id="ab584-104">Collecting Information About Computers</span></span>

<span data-ttu-id="ab584-105">針對一般系統管理作業， **CimCmdlet** 模組的 Cmdlet 是最重要的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ab584-105">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span> <span data-ttu-id="ab584-106">所有重要的子系統設定都是透過 WMI 公開。</span><span class="sxs-lookup"><span data-stu-id="ab584-106">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="ab584-107">此外，WMI 會將資料視為一或多個項目集合中的物件。</span><span class="sxs-lookup"><span data-stu-id="ab584-107">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="ab584-108">由於 Windows PowerShell 也適用於物件，並具有管線可讓您以相同的方式來處理單一物件或多個物件，因此一般 WMI 存取可讓您不費吹灰之力就能執行一些進階工作。</span><span class="sxs-lookup"><span data-stu-id="ab584-108">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

## <a name="listing-desktop-settings"></a><span data-ttu-id="ab584-109">列出桌面設定</span><span class="sxs-lookup"><span data-stu-id="ab584-109">Listing Desktop Settings</span></span>

<span data-ttu-id="ab584-110">我們一開始會使用命令，收集本機電腦上的桌面資訊。</span><span class="sxs-lookup"><span data-stu-id="ab584-110">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop
```

<span data-ttu-id="ab584-111">這會傳回所有桌面資訊，而不論其是否正在使用。</span><span class="sxs-lookup"><span data-stu-id="ab584-111">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="ab584-112">有些 WMI 類別傳回的資訊可能非常詳細，通常包含 WMI 類別的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ab584-112">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>

<span data-ttu-id="ab584-113">由於大多數中繼資料屬性的名稱均以 **Cim** 開頭，因此您可以使用 `Select-Object` 來篩選屬性。</span><span class="sxs-lookup"><span data-stu-id="ab584-113">Because most of these metadata properties have names that begin with **Cim** , you can filter the properties using `Select-Object`.</span></span> <span data-ttu-id="ab584-114">搭配使用 **-ExcludeProperty** 參數與 "Cim\*"，將其指定為值。</span><span class="sxs-lookup"><span data-stu-id="ab584-114">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span> <span data-ttu-id="ab584-115">例如：</span><span class="sxs-lookup"><span data-stu-id="ab584-115">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="ab584-116">若要篩選出中繼資料，請使用管線運算子 (|) 將 `Get-CimInstance` 命令的結果傳送至 `Select-Object -ExcludeProperty "CIM*"`。</span><span class="sxs-lookup"><span data-stu-id="ab584-116">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

## <a name="listing-bios-information"></a><span data-ttu-id="ab584-117">列出 BIOS 資訊</span><span class="sxs-lookup"><span data-stu-id="ab584-117">Listing BIOS Information</span></span>

<span data-ttu-id="ab584-118">WMI **Win32_BIOS** 類別會傳回本機電腦系統 BIOS 的精簡與完整相關資訊︰</span><span class="sxs-lookup"><span data-stu-id="ab584-118">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

## <a name="listing-processor-information"></a><span data-ttu-id="ab584-119">列出處理器資訊</span><span class="sxs-lookup"><span data-stu-id="ab584-119">Listing Processor Information</span></span>

<span data-ttu-id="ab584-120">您可以使用 WMI 的 **Win32_Processor** 類別擷取一般處理器資訊，不過您可能會想要篩選此資訊︰</span><span class="sxs-lookup"><span data-stu-id="ab584-120">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="ab584-121">針對處理器系列的一般描述字串，您可以只傳回 **SystemType** 屬性︰</span><span class="sxs-lookup"><span data-stu-id="ab584-121">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="ab584-122">列出電腦製造商和型號</span><span class="sxs-lookup"><span data-stu-id="ab584-122">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="ab584-123">**Win32_ComputerSystem** 也會提供電腦型號資訊。</span><span class="sxs-lookup"><span data-stu-id="ab584-123">Computer model information is also available from **Win32_ComputerSystem** .</span></span> <span data-ttu-id="ab584-124">顯示的標準輸出不需要任何篩選，就能提供 OEM 資料︰</span><span class="sxs-lookup"><span data-stu-id="ab584-124">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```Output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="ab584-125">類似此命令的輸出會直接傳回一些硬體的資訊，只會顯示您擁有的資料。</span><span class="sxs-lookup"><span data-stu-id="ab584-125">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="ab584-126">有些資訊未經過硬體製造商的正確設定，因此可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="ab584-126">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

## <a name="listing-installed-hotfixes"></a><span data-ttu-id="ab584-127">列出安裝的 Hotfix</span><span class="sxs-lookup"><span data-stu-id="ab584-127">Listing Installed Hotfixes</span></span>

<span data-ttu-id="ab584-128">您可以使用 **Win32_QuickFixEngineering** ，列出所有安裝的 Hotfix：</span><span class="sxs-lookup"><span data-stu-id="ab584-128">You can list all installed hotfixes by using **Win32_QuickFixEngineering** :</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering
```

<span data-ttu-id="ab584-129">此類別會傳回類似如下的 Hotfix 清單：</span><span class="sxs-lookup"><span data-stu-id="ab584-129">This class returns a list of hotfixes that looks like this:</span></span>

```Output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="ab584-130">如需更簡潔的輸出，您可能需要排除一些屬性。</span><span class="sxs-lookup"><span data-stu-id="ab584-130">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="ab584-131">雖然您可以使用 `Get-CimInstance` 的 **Property** 參數來僅選擇 **HotFixID** ，但這麼做實際上會傳回更多資訊，因為預設為顯示所有中繼資料︰</span><span class="sxs-lookup"><span data-stu-id="ab584-131">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID** , doing so will actually return more information, because all the metadata is displayed by default:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixID
```

```Output
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4533002
InstalledBy           :
ServicePackInEffect   :
PSComputerName        :
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name…}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
...
```

<span data-ttu-id="ab584-132">由於 `Get-CimInstance` 中的 **Property** 參數會限制從 WMI 類別執行個體傳回的屬性，而不是傳回給 PowerShell 的物件，因此會傳回額外的資料。</span><span class="sxs-lookup"><span data-stu-id="ab584-132">The additional data is returned, because the **Property** parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to PowerShell.</span></span> <span data-ttu-id="ab584-133">若要縮減輸出，請使用 `Select-Object`：</span><span class="sxs-lookup"><span data-stu-id="ab584-133">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixId | Select-Object -Property HotFixId
```

```Output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a><span data-ttu-id="ab584-134">列出作業系統版本資訊</span><span class="sxs-lookup"><span data-stu-id="ab584-134">Listing Operating System Version Information</span></span>

<span data-ttu-id="ab584-135">**Win32_OperatingSystem** 類別屬性包含版本和 Service Pack 資訊。</span><span class="sxs-lookup"><span data-stu-id="ab584-135">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="ab584-136">您可以明確地只選取這些屬性，以從 **Win32_OperatingSystem** 取得版本資訊摘要：</span><span class="sxs-lookup"><span data-stu-id="ab584-136">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem** :</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="ab584-137">`Select-Object` 的 **Property** 參數也可以使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ab584-137">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span> <span data-ttu-id="ab584-138">由於必須在此使用以 **Build** 或 **ServicePack** 開頭的所有屬性，因此可將此縮短為下列格式：</span><span class="sxs-lookup"><span data-stu-id="ab584-138">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property Build*,OSType,ServicePack*
```

```Output
BuildNumber             : 18362
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

## <a name="listing-local-users-and-owner"></a><span data-ttu-id="ab584-139">列出本機使用者和擁有者</span><span class="sxs-lookup"><span data-stu-id="ab584-139">Listing Local Users and Owner</span></span>

<span data-ttu-id="ab584-140">使用精選的 **Win32_OperatingSystem** 類別屬性即可找到本機一般使用者資訊 (授權使用者數目、目前的使用者數目和擁有者名稱)。</span><span class="sxs-lookup"><span data-stu-id="ab584-140">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class properties.</span></span> <span data-ttu-id="ab584-141">您可以明確地選取要顯示的屬性，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="ab584-141">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="ab584-142">使用萬用字元的更簡潔版本為︰</span><span class="sxs-lookup"><span data-stu-id="ab584-142">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a><span data-ttu-id="ab584-143">取得可用的磁碟空間</span><span class="sxs-lookup"><span data-stu-id="ab584-143">Getting Available Disk Space</span></span>

<span data-ttu-id="ab584-144">若要查看本機磁碟機的磁碟空間和可用空間，您可以使用 Win32_LogicalDisk WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="ab584-144">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="ab584-145">您只需要查看 DriveType 為 3 的執行個體，因為 WMI 會針對固定式硬碟使用這個值。</span><span class="sxs-lookup"><span data-stu-id="ab584-145">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3"
```

```Output
DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .
```

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" |
  Measure-Object -Property FreeSpace,Size -Sum |
    Select-Object -Property Property,Sum
```

```Output
Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

## <a name="getting-logon-session-information"></a><span data-ttu-id="ab584-146">取得登入工作階段資訊</span><span class="sxs-lookup"><span data-stu-id="ab584-146">Getting Logon Session Information</span></span>

<span data-ttu-id="ab584-147">您可以透過 **Win32_LogonSession** WMI 類別，取得與使用者相關聯的登入工作階段一般資訊︰</span><span class="sxs-lookup"><span data-stu-id="ab584-147">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession
```

## <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="ab584-148">取得登入電腦的使用者</span><span class="sxs-lookup"><span data-stu-id="ab584-148">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="ab584-149">您可以使用 Win32_ComputerSystem，顯示登入特定電腦系統的使用者。</span><span class="sxs-lookup"><span data-stu-id="ab584-149">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="ab584-150">此命令只會傳回登入系統桌面的使用者︰</span><span class="sxs-lookup"><span data-stu-id="ab584-150">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName
```

## <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="ab584-151">取得電腦的當地時間</span><span class="sxs-lookup"><span data-stu-id="ab584-151">Getting Local Time from a Computer</span></span>

<span data-ttu-id="ab584-152">您可以使用 **Win32_LocalTime** WMI 類別，擷取特定電腦上的目前當地時間。</span><span class="sxs-lookup"><span data-stu-id="ab584-152">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LocalTime
```

```Output
Day            : 23
DayOfWeek      : 1
Hour           : 8
Milliseconds   :
Minute         : 52
Month          : 12
Quarter        : 4
Second         : 55
WeekInMonth    : 4
Year           : 2019
PSComputerName :
```

## <a name="displaying-service-status"></a><span data-ttu-id="ab584-153">顯示服務狀態</span><span class="sxs-lookup"><span data-stu-id="ab584-153">Displaying Service Status</span></span>

<span data-ttu-id="ab584-154">若要檢視特定電腦的所有服務狀態，您可以在本機上使用 `Get-Service` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ab584-154">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span> <span data-ttu-id="ab584-155">若為遠端系統，您可以使用 **Win32_Service** WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="ab584-155">For remote systems, you can use the **Win32_Service** WMI class.</span></span> <span data-ttu-id="ab584-156">如果您同時使用 `Select-Object` 將結果篩選為 **Status** 、 **Name** 和 **DisplayName** ，輸出格式會與 `Get-Service` 的輸出格式幾乎完全相同：</span><span class="sxs-lookup"><span data-stu-id="ab584-156">If you also use `Select-Object` to filter the results to **Status** , **Name** , and **DisplayName** , the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="ab584-157">若要完整顯示名稱很長的不定期服務名稱，您可將 `Format-Table` 與 **AutoSize** 及 **Wrap** 參數搭配使用，以最佳化資料行寬度，並讓長名稱換行而不是被截斷︰</span><span class="sxs-lookup"><span data-stu-id="ab584-157">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
