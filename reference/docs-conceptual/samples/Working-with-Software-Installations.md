---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 處理軟體安裝
description: 本文說明如何使用 WMI 來管理安裝於 Windows 中的軟體。
ms.openlocfilehash: 3cf8e3c58e9f2814e2551b3602bd7b47b375aed8
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500873"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="a84d6-104">處理軟體安裝</span><span class="sxs-lookup"><span data-stu-id="a84d6-104">Working with Software Installations</span></span>

<span data-ttu-id="a84d6-105">設計成使用 Windows Installer 的應用程式可以透過 WMI 的 **Win32_Product** 類別存取，但並非所有現今使用的應用程式都使用 Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="a84d6-105">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="a84d6-106">使用替代安裝常式的應用程式通常不受 Windows Installer 管理。</span><span class="sxs-lookup"><span data-stu-id="a84d6-106">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="a84d6-107">處理那些應用程式的特定技術視安裝程式軟體與應用程式開發人員的決定而定。</span><span class="sxs-lookup"><span data-stu-id="a84d6-107">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="a84d6-108">例如，透過將應用程式檔案複製到電腦上資料夾來安裝的應用程式，通常無法使用這裡討論的技術來管理。</span><span class="sxs-lookup"><span data-stu-id="a84d6-108">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="a84d6-109">您可以使用[處理檔案與資料夾](Working-with-Files-and-Folders.md)一節中所討論的技術，將這些應用程式當成檔案與資料夾來管理。</span><span class="sxs-lookup"><span data-stu-id="a84d6-109">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="a84d6-110">**Win32_Product** 類別未針對查詢最佳化。</span><span class="sxs-lookup"><span data-stu-id="a84d6-110">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="a84d6-111">使用萬用字元篩選條件的查詢，會造成 WMI 使用 MSI 提供者來列舉所有已安裝產品，然後依序剖析完整清單來處理篩選條件。</span><span class="sxs-lookup"><span data-stu-id="a84d6-111">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="a84d6-112">這也會起始已安裝套件的一致性檢查，驗證並修復安裝。</span><span class="sxs-lookup"><span data-stu-id="a84d6-112">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="a84d6-113">驗證是緩慢的程序，而且可能會導致事件記錄檔中有錯誤。</span><span class="sxs-lookup"><span data-stu-id="a84d6-113">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="a84d6-114">如需詳細資訊，請參閱[知識庫文章 974524](https://support.microsoft.com/help/974524) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="a84d6-114">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="a84d6-115">列出 Windows Installer 應用程式</span><span class="sxs-lookup"><span data-stu-id="a84d6-115">Listing Windows Installer Applications</span></span>

<span data-ttu-id="a84d6-116">若要列出在本機或遠端系統上使用 Windows Installer 安裝的應用程式，請使用下列簡單的 WMI 查詢：</span><span class="sxs-lookup"><span data-stu-id="a84d6-116">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

<span data-ttu-id="a84d6-117">若要在螢幕上顯示 **Win32_Product** 物件的所有屬性，請使用格式設定 Cmdlet (例如 `Format-List` Cmdlet) 的 **Properties** 參數，加上 `*` (全部) 值。</span><span class="sxs-lookup"><span data-stu-id="a84d6-117">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.5 (x64)
Version               : 16.84.26919
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.5 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.5 (x64)
IdentifyingNumber     : {BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20181105
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}v16.84.26919\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\4f97a771.msi
PackageCache          : C:\WINDOWS\Installer\4f97a771.msi
PackageCode           : {9A271A10-039D-49EA-8D24-043D91B9F915}
PackageName           : dotnet-runtime-2.1.5-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

<span data-ttu-id="a84d6-118">或者，您可以使用 `Get-CimInstance` **Filter** 參數，以只選取 Microsoft .NET 2.0 執行階段。</span><span class="sxs-lookup"><span data-stu-id="a84d6-118">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET 2.0 Runtime.</span></span> <span data-ttu-id="a84d6-119">**Filter** 參數的值使用 WMI 查詢語言 (WQL) 語法，而不是 Windows PowerShell 語法。</span><span class="sxs-lookup"><span data-stu-id="a84d6-119">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="a84d6-120">例如：</span><span class="sxs-lookup"><span data-stu-id="a84d6-120">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="a84d6-121">若只要列出您感興趣的屬性，請使用格式設定 Cmdlet 的 **Property** 參數來列出想要的屬性。</span><span class="sxs-lookup"><span data-stu-id="a84d6-121">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.5 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\4f97a771.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="a84d6-122">列出所有可解除安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="a84d6-122">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="a84d6-123">因為大部分的標準應用程式會向 Windows 登錄解除安裝程式，所以我們可以透過在 Windows 登錄中尋找這些應用程式，以在本機處理它們。</span><span class="sxs-lookup"><span data-stu-id="a84d6-123">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="a84d6-124">沒有方式保證能找出系統上的每個應用程式。</span><span class="sxs-lookup"><span data-stu-id="a84d6-124">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="a84d6-125">不過，在下列登錄機碼中找出在 [新增或移除程式]  中顯示清單的所有程式是可能的：</span><span class="sxs-lookup"><span data-stu-id="a84d6-125">However, it is possible to find all programs with listings displayed in **Add or Remove Programs** in the following registry key:</span></span>

<span data-ttu-id="a84d6-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="a84d6-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="a84d6-127">我們可以檢查此機碼來尋找應用程式。</span><span class="sxs-lookup"><span data-stu-id="a84d6-127">We can examine this key to find applications.</span></span> <span data-ttu-id="a84d6-128">為了讓您更輕鬆地檢視 Uninstall 機碼，我們可以將 PowerShell 磁碟機對應至此登錄位置：</span><span class="sxs-lookup"><span data-stu-id="a84d6-128">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

<span data-ttu-id="a84d6-129">我們現在有了名為 "Uninstall:" 的磁碟機，它可以用來快速又方便地尋找應用程式安裝。</span><span class="sxs-lookup"><span data-stu-id="a84d6-129">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="a84d6-130">我們可以透過計算 Uninstall:PowerShell 磁碟機：</span><span class="sxs-lookup"><span data-stu-id="a84d6-130">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

<span data-ttu-id="a84d6-131">我們可以使用各種技術來進一步搜尋此應用程式清單，首先是 `Get-ChildItem`。</span><span class="sxs-lookup"><span data-stu-id="a84d6-131">We can search this list of applications further by using a variety of techniques, beginning with `Get-ChildItem`.</span></span> <span data-ttu-id="a84d6-132">若要取得應用程式清單並將它們儲存在 `$UninstallableApplications` 變數中，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="a84d6-132">To get a list of applications and save them in the `$UninstallableApplications` variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="a84d6-133">若要顯示 Uninstall 下登錄機碼中登錄項目的值，請使用登錄機碼的 GetValue 方法。</span><span class="sxs-lookup"><span data-stu-id="a84d6-133">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="a84d6-134">方法的值是登錄項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="a84d6-134">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="a84d6-135">例如，若要尋找 Uninstall 機碼中應用程式的顯示名稱，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="a84d6-135">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="a84d6-136">這些值並不保證是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a84d6-136">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="a84d6-137">在下列範例中，有兩個已安裝項目顯示為 "Windows Media Encoder 9 Series"：</span><span class="sxs-lookup"><span data-stu-id="a84d6-137">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```powershell
$UninstallableApplications | Where-Object -FilterScript {
  $_.GetValue("DisplayName") -eq "Microsoft Silverlight"
}
```

```Output
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name                           Property
----                           --------
{89F4137D-6C26-4A84-BDB8-2E5A4 AuthorizedCDFPrefix :
BB71E00}                       Comments            :
                               Contact             :
                               DisplayVersion      : 5.1.50918.0
                               HelpLink            : https://go.microsoft.com/fwlink/?LinkID=91955
                               HelpTelephone       :
                               InstallDate         : 20190115
                               InstallLocation     : C:\Program Files\Microsoft Silverlight\
                               InstallSource       : c:\ef64c54526db9c34cd477c103e68a254\
                               ModifyPath          : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               NoModify            : 1
                               NoRepair            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 236432
                               UninstallString     : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 5
                               VersionMinor        : 1
                               WindowsInstaller    : 1
                               Version             : 84002534
                               Language            : 1033
                               DisplayName         : Microsoft Silverlight
                               sEstimatedSize2     : 79214
```

## <a name="installing-applications"></a><span data-ttu-id="a84d6-138">安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="a84d6-138">Installing Applications</span></span>

<span data-ttu-id="a84d6-139">您可以在遠端或本機使用 **Win32_Product** 類別來安裝 Windows Installer 套件。</span><span class="sxs-lookup"><span data-stu-id="a84d6-139">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="a84d6-140">若要安裝應用程式，您必須使用 [以系統管理員身分執行] 選項來啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a84d6-140">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="a84d6-141">進行遠端安裝時，請使用通用命名慣例 (UNC) 網路路徑來指定 .msi 套件的路徑，因為 WMI 子系統不了解 PowerShell 路徑。</span><span class="sxs-lookup"><span data-stu-id="a84d6-141">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="a84d6-142">例如，若要在遠端電腦 PC01 上安裝位於網路共用 `\\AppServ\dsp` 中的 NewPackage.msi 套件，請在 PowerShell 提示字元輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="a84d6-142">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="a84d6-143">不使用 Windows Installer 技術的應用程式可能會有適用於自動化部署的應用程式專屬方法。</span><span class="sxs-lookup"><span data-stu-id="a84d6-143">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="a84d6-144">請檢查應用程式的文件或洽詢應用程式廠商的支援系統。</span><span class="sxs-lookup"><span data-stu-id="a84d6-144">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="a84d6-145">移除應用程式</span><span class="sxs-lookup"><span data-stu-id="a84d6-145">Removing Applications</span></span>

<span data-ttu-id="a84d6-146">使用 PowerShell 移除 Windows Installer 套件的方法，與安裝套件的方法大致相同。</span><span class="sxs-lookup"><span data-stu-id="a84d6-146">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="a84d6-147">以下是範例，其中根據套件的名稱選取要解除安裝的套件；在某些情況下，使用 **IdentifyingNumber** 來篩選可能會比較容易：</span><span class="sxs-lookup"><span data-stu-id="a84d6-147">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber** :</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="a84d6-148">即使是在本機上要移除其他應用程式，有時候也不太容易。</span><span class="sxs-lookup"><span data-stu-id="a84d6-148">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="a84d6-149">我們可以透過擷取 **UninstallString** 屬性，來尋找這些應用程式的命令列解除安裝字串。</span><span class="sxs-lookup"><span data-stu-id="a84d6-149">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="a84d6-150">此方法可用於 Windows Installer 應用程式，以及出現在 Uninstall 機碼下的舊版程式：</span><span class="sxs-lookup"><span data-stu-id="a84d6-150">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="a84d6-151">您也可以使用顯示名稱來篩選輸出：</span><span class="sxs-lookup"><span data-stu-id="a84d6-151">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="a84d6-152">不過，這些字串在未經修改之前，可能無法直接用於 PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="a84d6-152">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="a84d6-153">升級 Windows Installer 應用程式</span><span class="sxs-lookup"><span data-stu-id="a84d6-153">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="a84d6-154">若要升級應用程式，您需要知道應用程式的名稱，以及應用程式升級套件的路徑。</span><span class="sxs-lookup"><span data-stu-id="a84d6-154">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="a84d6-155">有了該資訊之後，您就可以使用單一的 PowerShell 命令升級應用程式：</span><span class="sxs-lookup"><span data-stu-id="a84d6-155">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
