---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 管理 Windows PowerShell 磁碟機
description: PowerShell 磁碟機是一個資料存放區位置，存取該位置的方式就像存取 PowerShell 中的檔案系統磁碟機一樣。 根據預設，PowerShell 包含支援檔案系統、登錄、憑證存放區等等的提供者。
ms.openlocfilehash: e4e5347c3f3458f25cea31c8e5a499474985220a
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500329"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="4c981-105">管理 Windows PowerShell 磁碟機</span><span class="sxs-lookup"><span data-stu-id="4c981-105">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="4c981-106">「Windows PowerShell 磁碟機」  是一個資料存放區位置，存取該位置的方式就像存取 Windows PowerShell 中的檔案系統磁碟機一樣。</span><span class="sxs-lookup"><span data-stu-id="4c981-106">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="4c981-107">Windows PowerShell 提供者會為您建立一些磁碟機，例如檔案系統磁碟機 (包括 C: 與 D:)、登錄磁碟機 (HKCU: 與 HKLM:) 與憑證磁碟機 (Cert:)，而且您可以建立自己的 Windows PowerShell 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="4c981-107">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="4c981-108">這些磁碟機非常實用，但只能在 Windows PowerShell 中使用。</span><span class="sxs-lookup"><span data-stu-id="4c981-108">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="4c981-109">您無法使用其他 Windows 工具 (例如 [檔案總管] 或 Cmd.exe) 來存取它們。</span><span class="sxs-lookup"><span data-stu-id="4c981-109">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="4c981-110">Windows PowerShell 會為可搭配 Windows PowerShell 磁碟機使用的命令使用名詞 **PSDrive** 。</span><span class="sxs-lookup"><span data-stu-id="4c981-110">Windows PowerShell uses the noun, **PSDrive** , for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="4c981-111">如需 Windows PowerShell 工作階段中的 Windows PowerShell 磁碟機清單，請使用 **Get-PSDrive** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4c981-111">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

<span data-ttu-id="4c981-112">雖然顯示中的磁碟機視您系統上的磁碟機而異，清單看起來會像是上面顯示的 **Get-PSDrive** 命令輸出。</span><span class="sxs-lookup"><span data-stu-id="4c981-112">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="4c981-113">檔案系統磁碟機是 Windows PowerShell 磁碟機的子集。</span><span class="sxs-lookup"><span data-stu-id="4c981-113">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="4c981-114">您可以透過 [提供者] 欄中的 FileSystem 項目來識別檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="4c981-114">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="4c981-115">(Windows PowerShell 中的檔案系統磁碟機受 Windows PowerShell FileSystem 提供者支援。)</span><span class="sxs-lookup"><span data-stu-id="4c981-115">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="4c981-116">若要檢視 **Get-PSDrive** Cmdlet 的語法，請輸入 **Get-Command** 命令並指定 **Syntax** 參數：</span><span class="sxs-lookup"><span data-stu-id="4c981-116">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="4c981-117">**PSProvider** 參數可讓您只顯示受特定提供者支援的 Windows PowerShell 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="4c981-117">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="4c981-118">例如，若只要顯示受 Windows PowerShell FileSystem 提供者支援的 Windows PowerShell 磁碟機，請輸入 **Get-PSDrive** 命令並指定 **PSProvider** 參數與 **FileSystem** 值：</span><span class="sxs-lookup"><span data-stu-id="4c981-118">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="4c981-119">若要檢視代表登錄區的 Windows PowerShell 磁碟機，請使用 **PSProvider** 參數以便只顯示受 Windows PowerShell 登錄提供者支援的 Windows PowerShell 磁碟機：</span><span class="sxs-lookup"><span data-stu-id="4c981-119">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="4c981-120">您也可以使用標準 Location Cmdlet 來搭配 Windows PowerShell 磁碟機：</span><span class="sxs-lookup"><span data-stu-id="4c981-120">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="4c981-121">新增 Windows PowerShell 磁碟機 (New-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="4c981-121">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="4c981-122">您可以使用 **New-PSDrive** 命令來新增自己的 Windows PowerShell 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="4c981-122">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="4c981-123">若要取得 **New-PSDrive** 命令的語法，請輸入 **Get-Command** 命令並指定 **Syntax** 參數：</span><span class="sxs-lookup"><span data-stu-id="4c981-123">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="4c981-124">若要建立新的 Windows PowerShell 磁碟機，您必須提供三個參數：</span><span class="sxs-lookup"><span data-stu-id="4c981-124">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="4c981-125">磁碟機的名稱 (您可以使用任何有效的 Windows PowerShell 名稱)</span><span class="sxs-lookup"><span data-stu-id="4c981-125">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="4c981-126">PSProvider (使用 "FileSystem" 代表檔案系統位置；使用 "Registry" 代表登錄位置)</span><span class="sxs-lookup"><span data-stu-id="4c981-126">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="4c981-127">根目錄，亦即新磁碟機的根目錄路徑</span><span class="sxs-lookup"><span data-stu-id="4c981-127">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="4c981-128">例如，您可以建立名為 "Office" 的磁碟機，將它對應到您電腦上包含 Microsoft Office 應用程式的資料夾，例如 **C:\\Program Files\\Microsoft Office\\OFFICE11** 。</span><span class="sxs-lookup"><span data-stu-id="4c981-128">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11** .</span></span> <span data-ttu-id="4c981-129">若要建立該磁碟機，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="4c981-129">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="4c981-130">一般而言，路徑不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="4c981-130">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="4c981-131">您可以使用參照所有 Windows 磁碟機的方式參照新的 Windows PowerShell 磁碟機，亦即輸入磁碟機名稱並加上冒號 ( **:** )。</span><span class="sxs-lookup"><span data-stu-id="4c981-131">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon ( **:** ).</span></span>

<span data-ttu-id="4c981-132">Windows PowerShell 磁碟機可以讓許多工作變得更簡單。</span><span class="sxs-lookup"><span data-stu-id="4c981-132">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="4c981-133">例如，Windows 登錄中的某些重要機碼具有極長的路徑，使得它們不容易存取且難以記住。</span><span class="sxs-lookup"><span data-stu-id="4c981-133">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="4c981-134">重要設定資訊位於 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion** 。</span><span class="sxs-lookup"><span data-stu-id="4c981-134">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion** .</span></span> <span data-ttu-id="4c981-135">若要檢視及變更 CurrentVersion 登錄機碼中的項目，您可以建立根目錄為該機碼的 Windows PowerShell 磁碟機，方式是輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="4c981-135">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="4c981-136">接著，您可以將位置變更至 **cvkey:** 磁碟機，就像存取任何其他磁碟機一樣：</span><span class="sxs-lookup"><span data-stu-id="4c981-136">You can then change location to the **cvkey:** drive as you would any other drive:</span></span>

```
PS> cd cvkey:
```

<span data-ttu-id="4c981-137">或者：</span><span class="sxs-lookup"><span data-stu-id="4c981-137">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="4c981-138">New-PsDrive Cmdlet 會將新磁碟機只新增到目前的 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="4c981-138">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="4c981-139">若關閉該 Windows PowerShell 視窗，該新磁碟機就會消失。</span><span class="sxs-lookup"><span data-stu-id="4c981-139">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="4c981-140">若要儲存 Windows PowerShell 磁碟機，請使用 Export-Console Cmdlet 來匯出目前的 Windows PowerShell 工作階段，然後使用 PowerShell.exe **PSConsoleFile** 參數來匯入它。</span><span class="sxs-lookup"><span data-stu-id="4c981-140">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="4c981-141">或者，將新磁碟機新增到您的 Windows PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="4c981-141">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="4c981-142">刪除 Windows PowerShell 磁碟機 (Remove-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="4c981-142">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="4c981-143">您可以使用 **Remove-PSDrive** Cmdlet 從 Windows PowerShell 刪除磁碟機。</span><span class="sxs-lookup"><span data-stu-id="4c981-143">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="4c981-144">**Remove-PSDrive** Cmdlet 使用方式很簡單；若要刪除特定 Windows PowerShell 磁碟機，您只需要提供 Windows PowerShell 磁碟機名稱即可。</span><span class="sxs-lookup"><span data-stu-id="4c981-144">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="4c981-145">例如：如果您新增了 **Office:** Windows PowerShell 磁碟機 (如 **New-PSDrive** 主題所示)，您可以鍵入下列命令予以刪除：</span><span class="sxs-lookup"><span data-stu-id="4c981-145">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="4c981-146">若要刪除 **cvkey:** Windows PowerShell 磁碟機 (如 **New-PSDrive** 主題所示)，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="4c981-146">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="4c981-147">刪除 Windows PowerShell 磁碟機的方式非常簡單，但您無法在位於磁碟機中時刪除該磁碟機。</span><span class="sxs-lookup"><span data-stu-id="4c981-147">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="4c981-148">例如：</span><span class="sxs-lookup"><span data-stu-id="4c981-148">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="4c981-149">在 Windows PowerShell 之外新增及移除磁碟機</span><span class="sxs-lookup"><span data-stu-id="4c981-149">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="4c981-150">Windows PowerShell 會偵測 Windows 中新增或移除的檔案系統磁碟機，包括對應的網路磁碟機、連接的 USB 磁碟機，以及使用 **net use** 命令或從 Windows Script Host (WSH) 指令碼使用 **WScript.NetworkMapNetworkDrive** 與 **RemoveNetworkDrive** 方法刪除的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="4c981-150">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>
