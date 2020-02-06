---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 取得 WMI 物件 Get-CimInstance
ms.openlocfilehash: 4ff47844fd367a49f554c7c05c491bdddf28eabc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "77002648"
---
# <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="7aafa-103">取得 WMI 物件 (Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="7aafa-103">Getting WMI Objects (Get-CimInstance)</span></span>

## <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="7aafa-104">取得 WMI 物件 (Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="7aafa-104">Getting WMI Objects (Get-CimInstance)</span></span>

<span data-ttu-id="7aafa-105">Windows Management Instrumentation (WMI) 可以一致地公開各種不同的資訊，因此成為 Windows 系統管理的核心技術。</span><span class="sxs-lookup"><span data-stu-id="7aafa-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="7aafa-106">由於 WMI 的強大功能，使得用於存取 WMI 物件的 PowerShell Cmdlet `Get-CimInstance` 成為執行實際工作的最實用工具之一。</span><span class="sxs-lookup"><span data-stu-id="7aafa-106">Because of how much WMI makes possible, the PowerShell cmdlet for accessing WMI objects, `Get-CimInstance`, is one of the most useful for doing real work.</span></span> <span data-ttu-id="7aafa-107">我們將討論如何使用 CimCmdlets 來存取 WMI 物件，並接著討論如何使用 WMI 物件來執行特定動作。</span><span class="sxs-lookup"><span data-stu-id="7aafa-107">We are going to discuss how to use the CimCmdlets to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="7aafa-108">列出 WMI 類別</span><span class="sxs-lookup"><span data-stu-id="7aafa-108">Listing WMI Classes</span></span>

<span data-ttu-id="7aafa-109">大多數 WMI 使用者遇到的第一個問題，就是嘗試了解使用 WMI 可執行的動作。</span><span class="sxs-lookup"><span data-stu-id="7aafa-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="7aafa-110">WMI 類別描述可管理的資源。</span><span class="sxs-lookup"><span data-stu-id="7aafa-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="7aafa-111">有數百個 WMI 類別，其中一些類別包含數十個屬性。</span><span class="sxs-lookup"><span data-stu-id="7aafa-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="7aafa-112">`Get-CimClass` 會藉由讓 WMI 變成可探索來解決此問題。</span><span class="sxs-lookup"><span data-stu-id="7aafa-112">`Get-CimClass` addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="7aafa-113">您可以輸入下列命令，取得本機電腦上可用的 WMI 類別清單：</span><span class="sxs-lookup"><span data-stu-id="7aafa-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

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

<span data-ttu-id="7aafa-114">您可以藉由使用 **ComputerName** 並參數指定電腦名稱或 IP 位址，從遠端電腦擷取相同的資訊︰</span><span class="sxs-lookup"><span data-stu-id="7aafa-114">You can retrieve the same information from a remote computer by using the **ComputerName** parameter, specifying a computer name or IP address:</span></span>

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

<span data-ttu-id="7aafa-115">遠端電腦所傳回的類別清單可能會因電腦執行的特定作業系統，以及已安裝應用程式新增的特定 WMI 擴充功能 而異。</span><span class="sxs-lookup"><span data-stu-id="7aafa-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="7aafa-116">使用 CIM Cmdlet 來連線到遠端電腦時，遠端電腦必須執行 WMI，而且您使用的帳戶必須在遠端電腦上的本機 Administrators 群組中。</span><span class="sxs-lookup"><span data-stu-id="7aafa-116">When using CIM cmdlets to connect to a remote computer, the remote computer must be running WMI and the account you are using must be in the local administrators group on the remote computer.</span></span>
> <span data-ttu-id="7aafa-117">遠端系統不需要安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="7aafa-117">The remote system does not need to have PowerShell installed.</span></span> <span data-ttu-id="7aafa-118">這可讓您管理未執行 PowerShell 但有 WMI 可用的作業系統。</span><span class="sxs-lookup"><span data-stu-id="7aafa-118">This allows you to administer operating systems that are not running PowerShell, but do have WMI available.</span></span>

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="7aafa-119">顯示 WMI 類別詳細資料</span><span class="sxs-lookup"><span data-stu-id="7aafa-119">Displaying WMI Class Details</span></span>

<span data-ttu-id="7aafa-120">如果您已經知道 WMI 類別的名稱，您可以使用它來立即取得資訊。</span><span class="sxs-lookup"><span data-stu-id="7aafa-120">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="7aafa-121">例如，常用於擷取電腦相關資訊的其中一個 WMI 類別是 **Win32_OperatingSystem**。</span><span class="sxs-lookup"><span data-stu-id="7aafa-121">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

<span data-ttu-id="7aafa-122">雖然我們會顯示所有參數，但命令可以更簡潔的方式來表示。</span><span class="sxs-lookup"><span data-stu-id="7aafa-122">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span>
<span data-ttu-id="7aafa-123">連線到本機系統時，不需要 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="7aafa-123">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="7aafa-124">顯示此參數是為了示範最常見的案例，並提醒您有此參數。</span><span class="sxs-lookup"><span data-stu-id="7aafa-124">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="7aafa-125">**Namespace** 預設為 `root/CIMV2`，您也可以予以省略。</span><span class="sxs-lookup"><span data-stu-id="7aafa-125">The **Namespace** defaults to `root/CIMV2`, and can be omitted as well.</span></span> <span data-ttu-id="7aafa-126">最後，大多數 Cmdlet 允許您省略一般參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="7aafa-126">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="7aafa-127">使用 `Get-CimInstance` 時，如果未指定第一個參數的名稱，PowerShell 會將它視為 **Class** 參數。</span><span class="sxs-lookup"><span data-stu-id="7aafa-127">With `Get-CimInstance`, if no name is specified for the first parameter, PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="7aafa-128">這表示最後一個命令可能已藉由輸入下列命令發出︰</span><span class="sxs-lookup"><span data-stu-id="7aafa-128">This means the last command could have been issued by typing:</span></span>

```powershell
Get-CimInstance Win32_OperatingSystem
```

<span data-ttu-id="7aafa-129">**Win32_OperatingSystem** 類別具有比此處顯示更多的屬性。</span><span class="sxs-lookup"><span data-stu-id="7aafa-129">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="7aafa-130">您可以使用 Get-Member 查看所有屬性。</span><span class="sxs-lookup"><span data-stu-id="7aafa-130">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="7aafa-131">WMI 類別的屬性與其他物件屬性一樣會自動提供使用︰</span><span class="sxs-lookup"><span data-stu-id="7aafa-131">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="7aafa-132">使用 Format Cmdlet 顯示非預設屬性</span><span class="sxs-lookup"><span data-stu-id="7aafa-132">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="7aafa-133">如果您需要預設未顯示之 **Win32_OperatingSystem** 類別中所包含的資訊，您可以使用 **Format** Cmdlet 顯示此類別。</span><span class="sxs-lookup"><span data-stu-id="7aafa-133">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="7aafa-134">例如，如果您想要顯示可用記憶體資料，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="7aafa-134">For example, if you want to display available memory data, type:</span></span>

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
> <span data-ttu-id="7aafa-135">萬用字元可在 `Format-Table` 中搭配屬性名稱使用，因此最後的管線元素可縮減成 `Format-Table -Property Total*Memory*, Free*`</span><span class="sxs-lookup"><span data-stu-id="7aafa-135">Wildcards work with property names in `Format-Table`, so the final pipeline element can be reduced to `Format-Table -Property Total*Memory*, Free*`</span></span>

<span data-ttu-id="7aafa-136">如果您輸入下列命令，將記憶體資料格式化為清單，可能更容易閱讀︰</span><span class="sxs-lookup"><span data-stu-id="7aafa-136">The memory data might be more readable if you format it as a list by typing:</span></span>

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
