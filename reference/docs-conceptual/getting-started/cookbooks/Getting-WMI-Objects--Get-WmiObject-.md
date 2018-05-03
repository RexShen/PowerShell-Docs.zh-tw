---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 取得 WMI 物件 Get WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 279e656b4affd27450be71015a5d6bd21af9f7ad
ms.sourcegitcommit: a9aa5e8d0fab0cbb3e4e6cff0e3ca8c0339ab4e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="8cdf0-103">取得 WMI 物件 (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="8cdf0-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="8cdf0-104">取得 WMI 物件 (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="8cdf0-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="8cdf0-105">Windows Management Instrumentation (WMI) 可以一致地公開各種不同的資訊，因此成為 Windows 系統管理的核心技術。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="8cdf0-106">由於 WMI 的強大功能，用於存取 WMI 物件的 Windows PowerShell Cmdlet **Get-WmiObject** 是執行實際工作的最實用工具之一。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="8cdf0-107">我們將討論如何使用 Get-WmiObject 存取 WMI 物件，並接著討論如何使用 WMI 物件執行特定動作。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="8cdf0-108">列出 WMI 類別</span><span class="sxs-lookup"><span data-stu-id="8cdf0-108">Listing WMI Classes</span></span>

<span data-ttu-id="8cdf0-109">大多數 WMI 使用者遇到的第一個問題，就是嘗試了解使用 WMI 可執行的動作。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="8cdf0-110">WMI 類別描述可管理的資源。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="8cdf0-111">有數百個 WMI 類別，其中一些類別包含數十個屬性。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="8cdf0-112">**Get-WmiObject** 讓 WMI 變成可搜尋，以解決此問題。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="8cdf0-113">您可以輸入下列命令，取得本機電腦上可用的 WMI 類別清單：</span><span class="sxs-lookup"><span data-stu-id="8cdf0-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="8cdf0-114">您可以使用 ComputerName 參數指定電腦名稱或 IP 位址，從遠端電腦擷取相同的資訊︰</span><span class="sxs-lookup"><span data-stu-id="8cdf0-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="8cdf0-115">遠端電腦所傳回的類別清單可能會因電腦執行的特定作業系統，以及已安裝應用程式新增的特定 WMI 擴充功能 而異。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="8cdf0-116">使用 Get-WmiObject 連線到遠端電腦時，遠端電腦必須執行 WMI，而且根據預設設定，您使用的帳戶必須在遠端電腦上的本機 Administrators 群組中。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="8cdf0-117">遠端系統不需要安裝 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="8cdf0-118">這可讓您管理未執行 Windows PowerShell 但有可用 WMI 的作業系統。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="8cdf0-119">您甚至可以在連線到本機系統時包含 ComputerName。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="8cdf0-120">您可以使用本機電腦的名稱、其 IP 位址 (或迴路位址 127.0.0.1) 或 WMI 樣式 '.' 作為電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="8cdf0-121">如果您在名為 Admin01 且 IP 位址為 192.168.1.90 的電腦上執行 Windows PowerShell，下列命令全部會傳回該電腦的 WMI 類別清單︰</span><span class="sxs-lookup"><span data-stu-id="8cdf0-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="8cdf0-122">Get-WmiObject 預設使用 root/cimv2 命名空間。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="8cdf0-123">如果您想要指定其他 WMI 命名空間，請使用 **Namespace** 參數並指定對應的命名空間路徑︰</span><span class="sxs-lookup"><span data-stu-id="8cdf0-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="8cdf0-124">顯示 WMI 類別詳細資料</span><span class="sxs-lookup"><span data-stu-id="8cdf0-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="8cdf0-125">如果您已經知道 WMI 類別的名稱，您可以使用它來立即取得資訊。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="8cdf0-126">例如，常用於擷取電腦相關資訊的其中一個 WMI 類別是 **Win32_OperatingSystem**。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="8cdf0-127">雖然我們會顯示所有參數，但命令可以更簡潔的方式來表示。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="8cdf0-128">連線到本機系統時，不需要 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="8cdf0-129">顯示此參數是為了示範最常見的案例，並提醒您有此參數。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="8cdf0-130">**Namespace** 預設為 root/cimv2，您也可以加以省略。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="8cdf0-131">最後，大多數 Cmdlet 允許您省略一般參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="8cdf0-132">使用 Get-WmiObject，如果未指定第一個參數的名稱，Windows PowerShell 會將它視為 **Class** 參數。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="8cdf0-133">這表示最後一個命令可能已藉由輸入下列命令發出︰</span><span class="sxs-lookup"><span data-stu-id="8cdf0-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="8cdf0-134">**Win32_OperatingSystem** 類別具有比此處顯示更多的屬性。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="8cdf0-135">您可以使用 Get-Member 查看所有屬性。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="8cdf0-136">WMI 類別的屬性與其他物件屬性一樣會自動提供使用︰</span><span class="sxs-lookup"><span data-stu-id="8cdf0-136">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="8cdf0-137">使用 Format Cmdlet 顯示非預設屬性</span><span class="sxs-lookup"><span data-stu-id="8cdf0-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="8cdf0-138">如果您需要預設未顯示之 **Win32_OperatingSystem** 類別中所包含的資訊，您可以使用 **Format** Cmdlet 顯示此類別。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="8cdf0-139">例如，如果您想要顯示可用記憶體資料，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="8cdf0-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="8cdf0-140">**Format-Table** 中的屬性名稱可以使用萬用字元，因此最後的管線元素可縮減為 `Format-Table -Property Total,Free`。</span><span class="sxs-lookup"><span data-stu-id="8cdf0-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to `Format-Table -Property Total,Free`</span></span>

<span data-ttu-id="8cdf0-141">如果您輸入下列命令，將記憶體資料格式化為清單，可能更容易閱讀︰</span><span class="sxs-lookup"><span data-stu-id="8cdf0-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
