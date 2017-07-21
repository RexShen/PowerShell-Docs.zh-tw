---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "處理軟體安裝"
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 2078376a8be19c9ff8ecc44183eb89f14bc388ed
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="working-with-software-installations"></a><span data-ttu-id="22e6c-103">處理軟體安裝</span><span class="sxs-lookup"><span data-stu-id="22e6c-103">Working with Software Installations</span></span>
<span data-ttu-id="22e6c-104">設計成使用 Windows Installer 的應用程式可以透過 WMI 的 **Win32_Product** 類別存取，但並非所有現今使用的應用程式都使用 Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="22e6c-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="22e6c-105">因為 Windows Installer 對處理可安裝的應用程式提供最廣泛的標準技術，我們主要將著重在那些應用程式。</span><span class="sxs-lookup"><span data-stu-id="22e6c-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="22e6c-106">使用替代安裝常式的應用程式通常不受 Windows Installer 管理。</span><span class="sxs-lookup"><span data-stu-id="22e6c-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="22e6c-107">處理那些應用程式的特定技術將視安裝程式軟體與應用程式開發人員的決定而定。</span><span class="sxs-lookup"><span data-stu-id="22e6c-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="22e6c-108">透過將應用程式檔案複製到電腦來安裝的應用程式通常無法使用這裡討論的技術來管理。</span><span class="sxs-lookup"><span data-stu-id="22e6c-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="22e6c-109">您可以使用＜處理檔案與資料夾＞一節中所討論的技術，將這些應用程式當成檔案與資料夾來管理。</span><span class="sxs-lookup"><span data-stu-id="22e6c-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

### <a name="listing-windows-installer-applications"></a><span data-ttu-id="22e6c-110">列出 Windows Installer 應用程式</span><span class="sxs-lookup"><span data-stu-id="22e6c-110">Listing Windows Installer Applications</span></span>
<span data-ttu-id="22e6c-111">若要列出在本機或遠端系統上使用 Windows Installer 安裝的應用程式，請使用下列簡單的 WMI 查詢：</span><span class="sxs-lookup"><span data-stu-id="22e6c-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="22e6c-112">若要在螢幕上顯示 Win32_Product 物件的所有屬性，請使用格式化 Cmdlet (例如 Format-List Cmdlet) 的 Properties 參數，加上 \* (全部) 值。</span><span class="sxs-lookup"><span data-stu-id="22e6c-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *
Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

<span data-ttu-id="22e6c-113">或者，您可以使用 **Get-WmiObject Filter** 參數來只選取 Microsoft .NET Framework 2.0。</span><span class="sxs-lookup"><span data-stu-id="22e6c-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="22e6c-114">因為此命令中使用的篩選器是 WMI 篩選器，所以它使用 WMI 查詢語言 (WQL) 語法，而不是 Windows PowerShell 語法。</span><span class="sxs-lookup"><span data-stu-id="22e6c-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="22e6c-115">而是：</span><span class="sxs-lookup"><span data-stu-id="22e6c-115">Instead,:</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="22e6c-116">請注意，WQL 查詢經常使用在 Windows PowerShell 中有特殊意義的字元，例如空格或等號。</span><span class="sxs-lookup"><span data-stu-id="22e6c-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="22e6c-117">基於此原因，最好一律將 Filter 參數的值用引號括住。</span><span class="sxs-lookup"><span data-stu-id="22e6c-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="22e6c-118">您也可以使用 Windows PowerShell 的逸出字元倒引號 (\\`)，但這麼做可能無法改善可讀性。</span><span class="sxs-lookup"><span data-stu-id="22e6c-118">You can also use the Windows PowerShell escape character, a backtick (\\`), although it may not improve readability.</span></span> <span data-ttu-id="22e6c-119">下列命令相當於先前的命令且傳回相同的結果，但它使用倒引號來逸出特殊字元，而不是將整個篩選字串用引號括住。</span><span class="sxs-lookup"><span data-stu-id="22e6c-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="22e6c-120">若只要列出您感興趣的屬性，請使用格式化 Cmdlet 的 Property 參數來列出想要的屬性。</span><span class="sxs-lookup"><span data-stu-id="22e6c-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

<span data-ttu-id="22e6c-121">最後，如果只要尋找已安裝應用程式的名稱，使用簡單的 **Format-Wide** 陳述式可簡化輸出：</span><span class="sxs-lookup"><span data-stu-id="22e6c-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="22e6c-122">雖然我們現在有數種方式可查看使用 Windows Installer 安裝的應用程式，但我們還沒有考慮其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="22e6c-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="22e6c-123">因為大部分的標準應用程式會向 Windows 登錄其解除安裝程式，所以我們可以透過在 Windows 登錄中尋找這些應用程式，以在本機處理它們。</span><span class="sxs-lookup"><span data-stu-id="22e6c-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

### <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="22e6c-124">列出所有可解除安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="22e6c-124">Listing All Uninstallable Applications</span></span>
<span data-ttu-id="22e6c-125">雖然沒有方法可以保證找出系統上所有應用程式，但可以尋找 [新增或移除程式] 對話方塊顯示之清單中的所有程式。</span><span class="sxs-lookup"><span data-stu-id="22e6c-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="22e6c-126">[新增或移除程式] 會在下列登錄機碼中尋找這些應用程式：</span><span class="sxs-lookup"><span data-stu-id="22e6c-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="22e6c-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**。</span><span class="sxs-lookup"><span data-stu-id="22e6c-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="22e6c-128">我們也可以檢查此機碼來尋找應用程式。</span><span class="sxs-lookup"><span data-stu-id="22e6c-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="22e6c-129">為了讓您更輕鬆地檢視 Uninstall 機碼，我們可以將 Windows PowerShell 磁碟機對應至此登錄位置：</span><span class="sxs-lookup"><span data-stu-id="22e6c-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall    

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="22e6c-130">**HKLM:** 磁碟機已對應到 **HKEY_LOCAL_MACHINE** 的根目錄，因此我們在指向 Uninstall 機碼的路徑中使用該磁碟機。</span><span class="sxs-lookup"><span data-stu-id="22e6c-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="22e6c-131">除了 **HKLM:** 之外，我們可以使用 **HKLM** 或 **HKEY_LOCAL_MACHINE** 其中之一指定登錄路徑。</span><span class="sxs-lookup"><span data-stu-id="22e6c-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="22e6c-132">使用現有登錄磁碟機的好處是可以使用 Tab 鍵自動完成來填入機碼名稱，因此我們不需要手動輸入。</span><span class="sxs-lookup"><span data-stu-id="22e6c-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="22e6c-133">我們現在有了名為 "Uninstall" 的磁碟機，它可以用來快速又方便地尋找應用程式安裝。</span><span class="sxs-lookup"><span data-stu-id="22e6c-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="22e6c-134">我們可以計算 Uninstall: Windows PowerShell 磁碟機中的登錄機碼數目，找出安裝的應用程式數目：</span><span class="sxs-lookup"><span data-stu-id="22e6c-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="22e6c-135">我們可以使用各種不同的技術來進一步搜尋此應用程式清單，首先是 **Get-ChildItem**。</span><span class="sxs-lookup"><span data-stu-id="22e6c-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="22e6c-136">若要取得應用程式清單並將它們儲存在 **$UninstallableApplications** 變數中，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="22e6c-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="22e6c-137">為了清楚說明，在這裡我們使用冗長的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="22e6c-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="22e6c-138">在實際使用時，就沒有必要使用長名稱。</span><span class="sxs-lookup"><span data-stu-id="22e6c-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="22e6c-139">雖然您可以使用 Tab 鍵自動完成輸入變數名稱，但您也可以為了加快速度使用 1 至 2 個字元的名稱。</span><span class="sxs-lookup"><span data-stu-id="22e6c-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="22e6c-140">較長的描述性名稱在您開發重複使用的程式碼時最有幫助。</span><span class="sxs-lookup"><span data-stu-id="22e6c-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="22e6c-141">若要顯示 Uninstall 下登錄機碼中登錄項目的值，請使用登錄機碼的 GetValue 方法。</span><span class="sxs-lookup"><span data-stu-id="22e6c-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="22e6c-142">方法的值是登錄項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="22e6c-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="22e6c-143">例如，若要尋找 Uninstall 機碼中應用程式的顯示名稱，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="22e6c-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```
PS> Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("DisplayName") }
```

<span data-ttu-id="22e6c-144">這些值並不保證是唯一的。</span><span class="sxs-lookup"><span data-stu-id="22e6c-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="22e6c-145">在下列範例中，有兩個已安裝項目顯示為 "Windows Media Encoder 9 Series"：</span><span class="sxs-lookup"><span data-stu-id="22e6c-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### <a name="installing-applications"></a><span data-ttu-id="22e6c-146">安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="22e6c-146">Installing Applications</span></span>
<span data-ttu-id="22e6c-147">您可以在遠端或本機使用 **Win32_Product** 類別來安裝 Windows Installer 封裝。</span><span class="sxs-lookup"><span data-stu-id="22e6c-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="22e6c-148">在 Windows Vista、Windows Server 2008 與更新版本的 Windows 中，您必須使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell 才能安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="22e6c-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="22e6c-149">進行遠端安裝時，請使用通用命名慣例 (UNC) 網路路徑來指定 .msi 套件的路徑，因為 WMI 子系統不了解 Windows PowerShell 路徑。</span><span class="sxs-lookup"><span data-stu-id="22e6c-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="22e6c-150">例如，若要安裝位於遠端電腦 PC01 上網路共用 \\\\AppServ\\dsp 中的 NewPackage.msi 套件，請在 Windows PowerShell 提示字元輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="22e6c-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq "Win32_Product"}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="22e6c-151">不使用 Windows Installer 技術的應用程式可能會有應用程式專屬，且適用於自動化部署的方法。</span><span class="sxs-lookup"><span data-stu-id="22e6c-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="22e6c-152">若要判斷是否有自動化部署的方法，請檢查應用程式的文件或洽詢應用程式廠商的支援系統。</span><span class="sxs-lookup"><span data-stu-id="22e6c-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="22e6c-153">在某些情況下，即使應用程式廠商沒有特別將應用程式設計成自動化安裝，但安裝程式軟體製造商可能會有一些自動化技術。</span><span class="sxs-lookup"><span data-stu-id="22e6c-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

### <a name="removing-applications"></a><span data-ttu-id="22e6c-154">移除應用程式</span><span class="sxs-lookup"><span data-stu-id="22e6c-154">Removing Applications</span></span>
<span data-ttu-id="22e6c-155">使用 Windows PowerShell 移除 Windows Installer 套件的方法，與安裝套件的方法大致相同。</span><span class="sxs-lookup"><span data-stu-id="22e6c-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="22e6c-156">以下是範例，其中根據封裝的名稱選取要解除安裝的封裝；在某些情況下，使用 **IdentifyingNumber** 來篩選可能會比較容易：</span><span class="sxs-lookup"><span data-stu-id="22e6c-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="22e6c-157">即使是在本機上要移除其他應用程式，有時候也不太容易。</span><span class="sxs-lookup"><span data-stu-id="22e6c-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="22e6c-158">我們可以透過擷取 **UninstallString** 屬性，來尋找這些應用程式的命令列解除安裝字串。</span><span class="sxs-lookup"><span data-stu-id="22e6c-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="22e6c-159">此方法可用於 Windows Installer 應用程式，以及出現在 Uninstall 機碼下的舊版程式：</span><span class="sxs-lookup"><span data-stu-id="22e6c-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

<span data-ttu-id="22e6c-160">您也可以使用顯示名稱來篩選輸出：</span><span class="sxs-lookup"><span data-stu-id="22e6c-160">You can filter the output by the display name, if you like:</span></span>

```
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -like "Win*"} | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

<span data-ttu-id="22e6c-161">不過，這些字串在未經修改之前，可能無法直接用於 Windows PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="22e6c-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

### <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="22e6c-162">升級 Windows Installer 應用程式</span><span class="sxs-lookup"><span data-stu-id="22e6c-162">Upgrading Windows Installer Applications</span></span>
<span data-ttu-id="22e6c-163">若要升級應用程式，您需要知道應用程式的名稱，以及應用程式升級套件的路徑。</span><span class="sxs-lookup"><span data-stu-id="22e6c-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="22e6c-164">有了該資訊之後，您就可以使用單一的 Windows PowerShell 命令升級應用程式：</span><span class="sxs-lookup"><span data-stu-id="22e6c-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```

