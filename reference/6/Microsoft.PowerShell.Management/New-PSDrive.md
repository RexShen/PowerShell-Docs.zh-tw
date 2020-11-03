---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSDrive
ms.openlocfilehash: 04346a3bd324b2d7033405546f131d2d56c5a2bd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202863"
---
# <span data-ttu-id="64567-103">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="64567-103">New-PSDrive</span></span>

## <span data-ttu-id="64567-104">概要</span><span class="sxs-lookup"><span data-stu-id="64567-104">SYNOPSIS</span></span>
<span data-ttu-id="64567-105">建立暫存和持續連線的網路磁碟機。</span><span class="sxs-lookup"><span data-stu-id="64567-105">Creates temporary and persistent mapped network drives.</span></span>

## <span data-ttu-id="64567-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="64567-106">SYNTAX</span></span>

### <span data-ttu-id="64567-107">全部</span><span class="sxs-lookup"><span data-stu-id="64567-107">All</span></span>

```
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Description <String>]
 [-Scope <String>] [-Persist] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="64567-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="64567-108">DESCRIPTION</span></span>

<span data-ttu-id="64567-109">此 `New-PSDrive` Cmdlet 會建立與資料存放區中的位置對應或相關聯的暫存和持續磁片磁碟機，例如網路磁碟機機、本機電腦上的目錄或登錄機碼，以及與遠端電腦上的檔案系統位置相關聯的持續性 Windows 對應網路磁碟機機。</span><span class="sxs-lookup"><span data-stu-id="64567-109">The `New-PSDrive` cmdlet creates temporary and persistent drives that are mapped to or associated with a location in a data store, such as a network drive, a directory on the local computer, or a registry key, and persistent Windows mapped network drives that are associated with a file system location on a remote computer.</span></span>

<span data-ttu-id="64567-110">暫存磁片磁碟機只存在於目前的 PowerShell 會話，以及您在目前會話中建立的會話中。</span><span class="sxs-lookup"><span data-stu-id="64567-110">Temporary drives exist only in the current PowerShell session and in sessions that you create in the current session.</span></span> <span data-ttu-id="64567-111">它們可以擁有任何在 PowerShell 中有效的名稱，而且可以對應到任何本機或遠端資源。</span><span class="sxs-lookup"><span data-stu-id="64567-111">They can have any name that is valid in PowerShell and can be mapped to any local or remote resource.</span></span> <span data-ttu-id="64567-112">您可以使用暫存的 PowerShell 磁片磁碟機來存取相關聯資料存放區中的資料，就像使用任何對應的網路磁碟機機一樣。</span><span class="sxs-lookup"><span data-stu-id="64567-112">You can use temporary PowerShell drives to access data in the associated data store, just as you would do with any mapped network drive.</span></span> <span data-ttu-id="64567-113">您可以使用或存取磁片磁碟機的內容，以將位置變更為磁片磁碟機 `Set-Location` `Get-Item` `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="64567-113">You can change locations into the drive, by using `Set-Location`, and access the contents of the drive by using `Get-Item` or `Get-ChildItem`.</span></span>

<span data-ttu-id="64567-114">因為暫存磁片磁碟機只有 PowerShell 知道，所以您無法使用檔案總管、Windows Management Instrumentation (WMI) 、元件物件模型 (COM) 、Microsoft .NET Framework，或使用 **NET use** 之類的工具來存取它們。</span><span class="sxs-lookup"><span data-stu-id="64567-114">Because temporary drives are known only to PowerShell, you can't access them by using File Explorer, Windows Management Instrumentation (WMI), Component Object Model (COM), Microsoft .NET Framework, or with tools such as **net use** .</span></span>

<span data-ttu-id="64567-115">PowerShell 3.0 中已新增下列功能 `New-PSDrive` ：</span><span class="sxs-lookup"><span data-stu-id="64567-115">The following features were added to `New-PSDrive` in PowerShell 3.0:</span></span>

- <span data-ttu-id="64567-116">對應的網路磁碟機。</span><span class="sxs-lookup"><span data-stu-id="64567-116">Mapped network drives.</span></span> <span data-ttu-id="64567-117">您可以使用的 [ **保存** ] 參數 `New-PSDrive` 建立 Windows 對應的網路磁碟機機。</span><span class="sxs-lookup"><span data-stu-id="64567-117">You can use the **Persist** parameter of `New-PSDrive` to create Windows mapped network drives.</span></span> <span data-ttu-id="64567-118">不同于暫存的 PowerShell 磁片磁碟機，Windows 對應的網路磁碟機機不是會話特定的。</span><span class="sxs-lookup"><span data-stu-id="64567-118">Unlike temporary PowerShell drives, Windows mapped network drives aren't session-specific.</span></span> <span data-ttu-id="64567-119">它們會儲存在 Windows 中，並可使用標準 Windows 工具（例如檔案總管和 **net use** ）進行管理。</span><span class="sxs-lookup"><span data-stu-id="64567-119">They're saved in Windows and they can be managed by using standard Windows tools, such as File Explorer and **net use** .</span></span> <span data-ttu-id="64567-120">連線的網路磁碟機必須擁有磁碟機代號名稱並連線至遠端檔案系統位置。</span><span class="sxs-lookup"><span data-stu-id="64567-120">Mapped network drives must have a drive-letter name and be connected to a remote file system location.</span></span> <span data-ttu-id="64567-121">當您的命令設定在本機的範圍時，如果沒有任何點來源，則 **保存** 參數不會在命令執行的範圍之外保存 **new-psdrive** 的建立。</span><span class="sxs-lookup"><span data-stu-id="64567-121">When your command is scoped locally, no dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which the command is running.</span></span> <span data-ttu-id="64567-122">如果您是在 `New-PSDrive` 腳本內部執行，而且您想要讓磁片磁碟機無限期保存，則必須以點為來源的腳本。</span><span class="sxs-lookup"><span data-stu-id="64567-122">If you're running `New-PSDrive` inside a script, and you want the drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="64567-123">為了獲得最佳結果，若要強制無限期保留新的磁碟機，請在命令中加入 **Scope** 參數，並將其值設定為 **Global** 。</span><span class="sxs-lookup"><span data-stu-id="64567-123">For best results, to force a new drive to persist indefinitely, add the **Scope** parameter to your command, and set its value to **Global** .</span></span> <span data-ttu-id="64567-124">如需有關點出來源的詳細資訊，請參閱 [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing)。</span><span class="sxs-lookup"><span data-stu-id="64567-124">For more information about dot-sourcing, see [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing).</span></span>
- <span data-ttu-id="64567-125">外部磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="64567-125">External drives.</span></span> <span data-ttu-id="64567-126">當外部磁片磁碟機連接到電腦時，PowerShell 會自動將 **new-psdrive** 新增至代表新磁片磁碟機的檔案系統。</span><span class="sxs-lookup"><span data-stu-id="64567-126">When an external drive is connected to the computer, PowerShell automatically adds a **PSDrive** to the file system that represents the new drive.</span></span> <span data-ttu-id="64567-127">您不需要重新開機 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="64567-127">You don't have to restart PowerShell.</span></span> <span data-ttu-id="64567-128">同樣地，當外部磁片磁碟機與電腦中斷連線時，PowerShell 會自動刪除代表已移除之磁片磁碟機的 **new-psdrive** 。</span><span class="sxs-lookup"><span data-stu-id="64567-128">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the **PSDrive** that represents the removed drive.</span></span>
- <span data-ttu-id="64567-129">通用命名慣例的認證 (UNC) 路徑。</span><span class="sxs-lookup"><span data-stu-id="64567-129">Credentials for Universal Naming Convention (UNC) paths.</span></span>

<span data-ttu-id="64567-130">當 **Root** 參數的值是 UNC 路徑時（例如 `\\Server\Share` ），會使用 **credential** 參數值中指定的認證來建立 **new-psdrive** 。</span><span class="sxs-lookup"><span data-stu-id="64567-130">When the value of the **Root** parameter is a UNC path, such as `\\Server\Share`, the credential specified in the value of the **Credential** parameter is used to create the **PSDrive** .</span></span> <span data-ttu-id="64567-131">否則，當您建立新的檔案系統磁片磁碟機時， **認證** 將不會生效。</span><span class="sxs-lookup"><span data-stu-id="64567-131">Otherwise, **Credential** isn't effective when you're creating new file system drives.</span></span>

<span data-ttu-id="64567-132">某些程式碼範例會使用展開來減少行長度，並提高可讀性。</span><span class="sxs-lookup"><span data-stu-id="64567-132">Some code samples use splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="64567-133">如需詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="64567-133">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="64567-134">範例</span><span class="sxs-lookup"><span data-stu-id="64567-134">EXAMPLES</span></span>

### <span data-ttu-id="64567-135">範例1：建立對應至網路共用的暫存磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="64567-135">Example 1: Create a temporary drive mapped to a network share</span></span>

<span data-ttu-id="64567-136">此範例會建立對應至網路共用的暫存 PowerShell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="64567-136">This example creates a temporary PowerShell drive that's mapped to a network share.</span></span>

```powershell
New-PSDrive -Name "Public" -PSProvider "FileSystem" -Root "\\Server01\Public"
```

```Output
Name       Provider      Root
----       --------      ----
Public     FileSystem    \\Server01\Public
```

<span data-ttu-id="64567-137">`New-PSDrive` 使用 **Name** 參數來指定名為的 powershell 磁片磁碟機 `Public` ，並使用 **PSProvider** 參數來指定 powershell `FileSystem` 提供者。</span><span class="sxs-lookup"><span data-stu-id="64567-137">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `Public` and the **PSProvider** parameter to specify the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="64567-138">**Root** 參數指定網路共用的 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="64567-138">The **Root** parameter specifies the network share's UNC path.</span></span>

<span data-ttu-id="64567-139">若要從 PowerShell 會話中查看內容： `Get-ChildItem -Path Public:`</span><span class="sxs-lookup"><span data-stu-id="64567-139">To view the contents from a PowerShell session: `Get-ChildItem -Path Public:`</span></span>

### <span data-ttu-id="64567-140">範例2：建立對應至本機目錄的暫存磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="64567-140">Example 2: Create a temporary drive mapped to a local directory</span></span>

<span data-ttu-id="64567-141">這個範例會建立暫存的 PowerShell 磁片磁碟機，以提供本機電腦上目錄的存取權。</span><span class="sxs-lookup"><span data-stu-id="64567-141">This example creates a temporary PowerShell drive that provides access to a directory on the local computer.</span></span>

```powershell
$parameters = @{
    Name = "MyDocs"
    PSProvider = "FileSystem"
    Root = "C:\Users\User01\Documents"
    Description = "Maps to my My Documents folder."
}
New-PSDrive @parameters
```

```Output
Name        Provider      Root
----        --------      ----
MyDocs      FileSystem    C:\Users\User01\Documents
```

<span data-ttu-id="64567-142">展開會建立參數索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="64567-142">Splatting creates the parameter keys and values.</span></span> <span data-ttu-id="64567-143">**Name** 參數會指定磁片磁碟機名稱 **MyDocs** 。</span><span class="sxs-lookup"><span data-stu-id="64567-143">The **Name** parameter specifies the drive name, **MyDocs** .</span></span> <span data-ttu-id="64567-144">**PSProvider** 參數會指定 PowerShell `FileSystem` 提供者。</span><span class="sxs-lookup"><span data-stu-id="64567-144">The **PSProvider** parameter specifies the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="64567-145">**Root** 指定本機電腦的目錄。</span><span class="sxs-lookup"><span data-stu-id="64567-145">**Root** specifies the local computer's directory.</span></span> <span data-ttu-id="64567-146">**Description** 參數描述磁片磁碟機的用途。</span><span class="sxs-lookup"><span data-stu-id="64567-146">The **Description** parameter describes the drive's purpose.</span></span> <span data-ttu-id="64567-147">`New-PSDrive` 使用 splatted 參數來建立 `MyDocs` 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="64567-147">`New-PSDrive` uses the splatted parameters to create the `MyDocs` drive.</span></span>

<span data-ttu-id="64567-148">若要從 PowerShell 會話中查看內容： `Get-ChildItem -Path MyDocs:`</span><span class="sxs-lookup"><span data-stu-id="64567-148">To view the contents from a PowerShell session: `Get-ChildItem -Path MyDocs:`</span></span>

### <span data-ttu-id="64567-149">範例3：建立登錄機碼的暫存磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="64567-149">Example 3: Create a temporary drive for a registry key</span></span>

<span data-ttu-id="64567-150">這個範例會建立暫存的 PowerShell 磁片磁碟機，以提供登錄機碼的存取權。</span><span class="sxs-lookup"><span data-stu-id="64567-150">This example creates a temporary PowerShell drive that provides access to a registry key.</span></span> <span data-ttu-id="64567-151">它會建立一個名為 MyCompany 的磁片磁碟機，它會對應到登錄機 `HKLM:\Software\MyCompany` 碼。</span><span class="sxs-lookup"><span data-stu-id="64567-151">It creates a drive named MyCompany that is mapped to the `HKLM:\Software\MyCompany` registry key.</span></span>

```powershell
New-PSDrive -Name "MyCompany" -PSProvider "Registry" -Root "HKLM:\Software\MyCompany"
```

```Output
Name           Provider      Root
----           --------      ----
MyCompany      Registry      HKLM:\Software\MyCompany
```

<span data-ttu-id="64567-152">`New-PSDrive` 使用 **Name** 參數來指定名為的 powershell 磁片磁碟機 `MyCompany` ，並使用 **PSProvider** 參數來指定 powershell `Registry` 提供者。</span><span class="sxs-lookup"><span data-stu-id="64567-152">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `MyCompany` and the **PSProvider** parameter to specify the PowerShell `Registry` provider.</span></span> <span data-ttu-id="64567-153">**Root** 參數指定登錄位置。</span><span class="sxs-lookup"><span data-stu-id="64567-153">The **Root** parameter specifies the registry location.</span></span>

<span data-ttu-id="64567-154">若要從 PowerShell 會話中查看內容： `Get-ChildItem -Path MyCompany:`</span><span class="sxs-lookup"><span data-stu-id="64567-154">To view the contents from a PowerShell session: `Get-ChildItem -Path MyCompany:`</span></span>

### <span data-ttu-id="64567-155">範例4：使用認證建立持續性對應的網路磁碟機機</span><span class="sxs-lookup"><span data-stu-id="64567-155">Example 4: Create a persistent mapped network drive using credentials</span></span>

<span data-ttu-id="64567-156">此範例會對應以網域服務帳戶的認證進行驗證的網路磁碟機機。</span><span class="sxs-lookup"><span data-stu-id="64567-156">This example maps a network drive that's authenticated with a domain service account's credentials.</span></span>
<span data-ttu-id="64567-157">如需有關用來儲存認證的 **PSCredential** 物件，以及密碼如何儲存為 **SecureString** 的詳細資訊，請參閱 **Credential** 參數的描述。</span><span class="sxs-lookup"><span data-stu-id="64567-157">For more information about the **PSCredential** object that stores credentials and how passwords are stored as a **SecureString** , see the **Credential** parameter's description.</span></span>

```powershell
$cred = Get-Credential -Credential Contoso\ServiceAccount
New-PSDrive -Name "S" -Root "\\Server01\Scripts" -Persist -PSProvider "FileSystem" -Credential $cred
Net Use
```

```Output
Status       Local     Remote                    Network
---------------------------------------------------------
OK           S:        \\Server01\Scripts        Microsoft Windows Network
```

> [!NOTE]
> <span data-ttu-id="64567-158">請記住，如果您在腳本中使用上述程式碼片段，請將 **範圍** 參數值設定為 "Global"，以確保磁片磁碟機在目前的範圍之外保持不變。</span><span class="sxs-lookup"><span data-stu-id="64567-158">Remember, if you use the above snippet in a script, set the **Scope** parameter value to "Global" to ensure the drive persists outside the current scope.</span></span>

<span data-ttu-id="64567-159">`$cred`變數會儲存一個 **PSCredential** 物件，其中包含服務帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="64567-159">The `$cred` variable stores a **PSCredential** object that contains the service account's credentials.</span></span> <span data-ttu-id="64567-160">`Get-Credential` 提示您輸入儲存在 **SecureString** 中的密碼。</span><span class="sxs-lookup"><span data-stu-id="64567-160">`Get-Credential` prompts you to enter the password that's stored in a **SecureString** .</span></span>

<span data-ttu-id="64567-161">`New-PSDrive` 使用數個參數建立對應的網路磁碟機機。</span><span class="sxs-lookup"><span data-stu-id="64567-161">`New-PSDrive` creates the mapped network drive by using several parameters.</span></span> <span data-ttu-id="64567-162">**名稱** 會指定 `S` Windows 接受的磁碟機號。</span><span class="sxs-lookup"><span data-stu-id="64567-162">**Name** specifies the `S` drive letter that Windows accepts.</span></span> <span data-ttu-id="64567-163">和 **Root** 定義 `\\Server01\Scripts` 為遠端電腦上的位置。</span><span class="sxs-lookup"><span data-stu-id="64567-163">and **Root** defines `\\Server01\Scripts` as the location on a remote computer.</span></span> <span data-ttu-id="64567-164">[ **保存** ] 會建立儲存在本機電腦上的 Windows 對應網路磁碟機機。</span><span class="sxs-lookup"><span data-stu-id="64567-164">**Persist** creates a Windows mapped network drive that's saved on the local computer.</span></span> <span data-ttu-id="64567-165">**PSProvider** 指定 `FileSystem` 提供者。</span><span class="sxs-lookup"><span data-stu-id="64567-165">**PSProvider** specifies the `FileSystem` provider.</span></span> <span data-ttu-id="64567-166">**認證會** 使用 `$cred` 變數來取得服務帳戶認證以進行驗證。</span><span class="sxs-lookup"><span data-stu-id="64567-166">**Credential** uses the `$cred` variable to get the service account credentials for authentication.</span></span>

<span data-ttu-id="64567-167">您可以在本機電腦上的 PowerShell 會話中、檔案總管，以及利用 **net use** 之類的工具，來查看對應的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="64567-167">The mapped drive can be viewed on the local computer in PowerShell sessions, File Explorer, and with tools such as **net use** .</span></span> <span data-ttu-id="64567-168">若要從 PowerShell 會話中查看內容： `Get-ChildItem -Path S:`</span><span class="sxs-lookup"><span data-stu-id="64567-168">To view the contents from a PowerShell session: `Get-ChildItem -Path S:`</span></span>

### <span data-ttu-id="64567-169">範例5：建立持續性和暫存磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="64567-169">Example 5: Create persistent and temporary drives</span></span>

<span data-ttu-id="64567-170">此範例顯示持續連線的網路磁碟機機與對應到相同網路共用的暫存 PowerShell 磁片磁碟機之間的差異。</span><span class="sxs-lookup"><span data-stu-id="64567-170">This example shows the difference between a persistent mapped network drive and a temporary PowerShell drive that is mapped to the same network share.</span></span>

<span data-ttu-id="64567-171">如果您關閉 PowerShell 會話，然後開啟新的會話，則暫時 `PSDrive:` 無法使用，但仍 `X:` 可使用持續性磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="64567-171">If you close the PowerShell session and then open a new session, the temporary `PSDrive:` isn't available, but the persistent `X:` drive is available.</span></span> <span data-ttu-id="64567-172">當您決定要使用哪一種方法來對應網路磁碟機機時，請考慮您將如何使用該磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="64567-172">When deciding which method to use to map network drives, consider how you'll use the drive.</span></span> <span data-ttu-id="64567-173">例如，它是否必須是持續性，以及其他 Windows 功能是否都能看到磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="64567-173">For example, whether it has to be persistent, and whether the drive has to be visible to other Windows features.</span></span>

```powershell
# Create a temporary PowerShell drive called PSDrive:
# that's mapped to the \\Server01\Public network share.
New-PSDrive -Name "PSDrive" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Use the Persist parameter of New-PSDrive to create the X: mapped network drive,
# which is also mapped to the \\Server01\Public network share.
New-PSDrive -Persist -Name "X" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Now, you can use the Get-PSDrive drive cmdlet to examine the two drives.
# The drives appear to be the same, although the network share name appears only
# in the root of the PSDrive: drive.
Get-PSDrive -Name "PSDrive", "X"
```

```Output
Name       Provider      Root
----       --------      ----

PsDrive    FileSystem    \\Server01\public
X          FileSystem    X:\
```

```powershell
# Get-Member cmdlet shows that the drives have the same object type,
# System.Management.Automation.PSDriveInfo.
Get-PSDrive "PSDrive", "x" | Get-Member
```

```Output
TypeName: System.Management.Automation.PSDriveInfo

Name                MemberType   Definition
----                ----------   ----------
CompareTo           Method       System.Int32 CompareTo(PSDriveInfo drive),
Equals              Method       System.Boolean Equals(Object obj),
GetHashCode         Method       System.Int32 GetHashCode()
...
```

```powershell
# Net Use and Get-CimInstance for the Win32_LogicalDisk class,
# and Win32_NetworkConnection class find only the persistent X: drive.
# PowerShell temporary drives are known only to PowerShell.
Net Use
Get-CimInstance Win32_LogicalDisk | Format-Table -Property DeviceID
Get-CimInstance Win32_NetworkConnection
```

```Output
Status       Local     Remote                    Network
--------------------------------------------------------
OK           X:        \\contoso-pc\data         Microsoft Windows Network

deviceid
--------
C:
D:
X:

LocalName    RemoteName              ConnectionState          Status
---------    ----------              ---------------          ------
X:           \\products\public       Disconnected             Unavailable
```

## <span data-ttu-id="64567-174">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="64567-174">PARAMETERS</span></span>

### <span data-ttu-id="64567-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="64567-175">-Confirm</span></span>

<span data-ttu-id="64567-176">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="64567-176">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="64567-177">-Credential</span><span class="sxs-lookup"><span data-stu-id="64567-177">-Credential</span></span>

<span data-ttu-id="64567-178">指定具有執行此動作之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="64567-178">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="64567-179">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="64567-179">The default is the current user.</span></span>

<span data-ttu-id="64567-180">從 PowerShell 3.0 開始，當 **Root** 參數的值是 UNC 路徑時，您可以使用認證來建立檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="64567-180">Since PowerShell 3.0, when the value of the **Root** parameter is a UNC path, you can use credentials to create file system drives.</span></span>

<span data-ttu-id="64567-181">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="64567-181">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="64567-182">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="64567-182">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="64567-183">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="64567-183">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="64567-184">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="64567-184">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="64567-185">-Description</span><span class="sxs-lookup"><span data-stu-id="64567-185">-Description</span></span>

<span data-ttu-id="64567-186">指定磁碟機的簡短文字描述。</span><span class="sxs-lookup"><span data-stu-id="64567-186">Specifies a brief text description of the drive.</span></span> <span data-ttu-id="64567-187">輸入任何字串。</span><span class="sxs-lookup"><span data-stu-id="64567-187">Type any string.</span></span>

<span data-ttu-id="64567-188">若要查看所有會話磁片磁碟機的描述，請參閱 `Get-PSDrive | Format-Table Name, Description` 。</span><span class="sxs-lookup"><span data-stu-id="64567-188">To see the descriptions of all the session's drives, `Get-PSDrive | Format-Table Name, Description`.</span></span>

<span data-ttu-id="64567-189">若要查看特定磁片磁碟機的描述，請輸入 `(Get-PSDrive <DriveName>).Description` 。</span><span class="sxs-lookup"><span data-stu-id="64567-189">To see the description of a particular drive, type `(Get-PSDrive <DriveName>).Description`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="64567-190">-Name</span><span class="sxs-lookup"><span data-stu-id="64567-190">-Name</span></span>

<span data-ttu-id="64567-191">指定新磁碟機的名稱。</span><span class="sxs-lookup"><span data-stu-id="64567-191">Specifies a name for the new drive.</span></span> <span data-ttu-id="64567-192">若為持續連線的網路磁碟機機，請使用磁碟機號。</span><span class="sxs-lookup"><span data-stu-id="64567-192">For persistent mapped network drives, use a drive letter.</span></span> <span data-ttu-id="64567-193">針對暫存的 PowerShell 磁片磁碟機，您不限於磁碟機號，請使用任何有效的字串。</span><span class="sxs-lookup"><span data-stu-id="64567-193">For temporary PowerShell drives, you aren't limited to drive letters, use any valid string.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="64567-194">-Persist</span><span class="sxs-lookup"><span data-stu-id="64567-194">-Persist</span></span>

<span data-ttu-id="64567-195">指出此 Cmdlet 會建立 Windows 對應的網路磁碟機機。</span><span class="sxs-lookup"><span data-stu-id="64567-195">Indicates that this cmdlet creates a Windows mapped network drive.</span></span> <span data-ttu-id="64567-196">**保存** 參數只能在 Windows 上使用。</span><span class="sxs-lookup"><span data-stu-id="64567-196">The **Persist** parameter is only available on Windows.</span></span>

<span data-ttu-id="64567-197">連線的網路磁碟機會儲存在本機電腦的 Windows 中。</span><span class="sxs-lookup"><span data-stu-id="64567-197">Mapped network drives are saved in Windows on the local computer.</span></span> <span data-ttu-id="64567-198">它們是持續性的，不是會話特定的，而且可以在檔案總管和其他工具中加以查看和管理。</span><span class="sxs-lookup"><span data-stu-id="64567-198">They're persistent, not session-specific, and can be viewed and managed in File Explorer and other tools.</span></span>

<span data-ttu-id="64567-199">當您在本機將命令範圍限定在本機（沒有點對端）時， **保存** 參數不會在您執行命令的範圍之外保存 **new-psdrive** 的建立。</span><span class="sxs-lookup"><span data-stu-id="64567-199">When you scope the command locally, without dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which you run the command.</span></span> <span data-ttu-id="64567-200">如果您在 `New-PSDrive` 腳本內執行，而您想要讓新的磁片磁碟機無限期保存，則必須以點為來源的腳本。</span><span class="sxs-lookup"><span data-stu-id="64567-200">If you run `New-PSDrive` inside a script, and you want the new drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="64567-201">為了獲得最佳結果，若要強制保留新的磁片磁碟機，請指定 **Global** 作為 **Scope** 參數的值，並在您的命令中包含 **保存** 。</span><span class="sxs-lookup"><span data-stu-id="64567-201">For best results, to force a new drive to persist, specify **Global** as the value of the **Scope** parameter and include **Persist** in your command.</span></span>

<span data-ttu-id="64567-202">磁片磁碟機的名稱必須是字母，例如 `D` 或 `E` 。</span><span class="sxs-lookup"><span data-stu-id="64567-202">The name of the drive must be a letter, such as `D` or `E`.</span></span> <span data-ttu-id="64567-203">**Root** 參數的值必須是不同電腦的 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="64567-203">The value of **Root** parameter must be a UNC path of a different computer.</span></span> <span data-ttu-id="64567-204">**PSProvider** 參數的值必須是 `FileSystem` 。</span><span class="sxs-lookup"><span data-stu-id="64567-204">The **PSProvider** parameter's value must be `FileSystem`.</span></span>

<span data-ttu-id="64567-205">若要中斷 Windows 對應網路磁碟機機的連線，請使用 `Remove-PSDrive` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64567-205">To disconnect a Windows mapped network drive, use the `Remove-PSDrive` cmdlet.</span></span> <span data-ttu-id="64567-206">當您中斷 Windows 連線網路磁碟機的連線時，該連線會永久從該電腦上刪除，而不是只從目前的工作階段中刪除。</span><span class="sxs-lookup"><span data-stu-id="64567-206">When you disconnect a Windows mapped network drive, the mapping is permanently deleted from the computer, not just deleted from the current session.</span></span>

<span data-ttu-id="64567-207">連線網路磁碟機僅適用於特定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="64567-207">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="64567-208">使用不同的認證來啟動的會話中，不會顯示在提高許可權的會話中建立的對應磁片磁碟機或使用另一個使用者認證的會話。</span><span class="sxs-lookup"><span data-stu-id="64567-208">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="64567-209">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="64567-209">-PSProvider</span></span>

<span data-ttu-id="64567-210">指定支援此類型磁片磁碟機的 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="64567-210">Specifies the PowerShell provider that supports drives of this kind.</span></span>

<span data-ttu-id="64567-211">例如，如果磁片磁碟機與網路共用或檔案系統目錄相關聯，則 PowerShell 提供者為 `FileSystem` 。</span><span class="sxs-lookup"><span data-stu-id="64567-211">For example, if the drive is associated with a network share or file system directory, the PowerShell provider is `FileSystem`.</span></span> <span data-ttu-id="64567-212">如果磁片磁碟機與登錄機碼關聯，則提供者為 `Registry` 。</span><span class="sxs-lookup"><span data-stu-id="64567-212">If the drive is associated with a registry key, the provider is `Registry`.</span></span>

<span data-ttu-id="64567-213">暫存的 PowerShell 磁片磁碟機可以與任何 PowerShell 提供者相關聯。</span><span class="sxs-lookup"><span data-stu-id="64567-213">Temporary PowerShell drives can be associated with any PowerShell provider.</span></span> <span data-ttu-id="64567-214">對應的網路磁碟機機只能與 `FileSystem` 提供者相關聯。</span><span class="sxs-lookup"><span data-stu-id="64567-214">Mapped network drives can be associated only with the `FileSystem` provider.</span></span>

<span data-ttu-id="64567-215">若要查看 PowerShell 會話中的提供者清單，請使用 `Get-PSProvider` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64567-215">To see a list of the providers in your PowerShell session, use the `Get-PSProvider` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="64567-216">-Root</span><span class="sxs-lookup"><span data-stu-id="64567-216">-Root</span></span>

<span data-ttu-id="64567-217">指定 PowerShell 磁片磁碟機對應的資料存放區位置。</span><span class="sxs-lookup"><span data-stu-id="64567-217">Specifies the data store location to which a PowerShell drive is mapped.</span></span>

<span data-ttu-id="64567-218">例如，指定網路共用，例如，本機目錄（例如）或登錄機 `\\Server01\Public` `C:\Program Files` 碼（例如） `HKLM:\Software\Microsoft` 。</span><span class="sxs-lookup"><span data-stu-id="64567-218">For example, specify a network share, such as `\\Server01\Public`, a local directory, such as `C:\Program Files`, or a registry key, such as `HKLM:\Software\Microsoft`.</span></span>

<span data-ttu-id="64567-219">暫存的 PowerShell 磁片磁碟機可以與任何支援的提供者磁片磁碟機上的本機或遠端位置相關聯。</span><span class="sxs-lookup"><span data-stu-id="64567-219">Temporary PowerShell drives can be associated with a local or remote location on any supported provider drive.</span></span> <span data-ttu-id="64567-220">連線的網路磁碟機只能與遠端電腦上的檔案系統位置關聯。</span><span class="sxs-lookup"><span data-stu-id="64567-220">Mapped network drives can be associated only with a file system location on a remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="64567-221">-Scope</span><span class="sxs-lookup"><span data-stu-id="64567-221">-Scope</span></span>

<span data-ttu-id="64567-222">指定磁碟機的範圍。</span><span class="sxs-lookup"><span data-stu-id="64567-222">Specifies a scope for the drive.</span></span> <span data-ttu-id="64567-223">此參數可接受的值為： **Global** 、 **Local** 和 **Script** ，或相對於目前範圍的數位。</span><span class="sxs-lookup"><span data-stu-id="64567-223">The acceptable values for this parameter are: **Global** , **Local** , and **Script** , or a number relative to the current scope.</span></span> <span data-ttu-id="64567-224">範圍編號0至範圍數目。</span><span class="sxs-lookup"><span data-stu-id="64567-224">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="64567-225">目前的範圍號碼為0，而其父系為1。</span><span class="sxs-lookup"><span data-stu-id="64567-225">The current scope number is 0 and its parent is 1.</span></span> <span data-ttu-id="64567-226">如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="64567-226">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="64567-227">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="64567-227">-WhatIf</span></span>

<span data-ttu-id="64567-228">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="64567-228">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="64567-229">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64567-229">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="64567-230">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="64567-230">CommonParameters</span></span>

<span data-ttu-id="64567-231">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="64567-231">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="64567-232">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="64567-232">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="64567-233">輸入</span><span class="sxs-lookup"><span data-stu-id="64567-233">INPUTS</span></span>

### <span data-ttu-id="64567-234">無</span><span class="sxs-lookup"><span data-stu-id="64567-234">None</span></span>

<span data-ttu-id="64567-235">您無法對此 Cmdlet 進行管線輸入。</span><span class="sxs-lookup"><span data-stu-id="64567-235">You can't pipeline input to this cmdlet.</span></span>

## <span data-ttu-id="64567-236">輸出</span><span class="sxs-lookup"><span data-stu-id="64567-236">OUTPUTS</span></span>

### <span data-ttu-id="64567-237">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="64567-237">System.Management.Automation.PSDriveInfo</span></span>

## <span data-ttu-id="64567-238">注意</span><span class="sxs-lookup"><span data-stu-id="64567-238">NOTES</span></span>

<span data-ttu-id="64567-239">`New-PSDrive` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="64567-239">`New-PSDrive` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="64567-240">若要列出會話中可用的提供者，請使用 `Get-PSProvider` 。</span><span class="sxs-lookup"><span data-stu-id="64567-240">To list the providers available in your session, use `Get-PSProvider`.</span></span> <span data-ttu-id="64567-241">如需提供者的詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="64567-241">For more information about providers, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="64567-242">連線網路磁碟機僅適用於特定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="64567-242">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="64567-243">使用不同的認證來啟動的會話中，不會顯示在提高許可權的會話中建立的對應磁片磁碟機或使用另一個使用者認證的會話。</span><span class="sxs-lookup"><span data-stu-id="64567-243">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

## <span data-ttu-id="64567-244">相關連結</span><span class="sxs-lookup"><span data-stu-id="64567-244">RELATED LINKS</span></span>

[<span data-ttu-id="64567-245">about_Providers</span><span class="sxs-lookup"><span data-stu-id="64567-245">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="64567-246">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="64567-246">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="64567-247">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="64567-247">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="64567-248">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="64567-248">Remove-PSDrive</span></span>](Remove-PSDrive.md)
