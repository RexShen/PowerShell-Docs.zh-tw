---
ms.date: 06/12/2017
title: 啟動載入 NuGet
description: 此文章說明如何安裝支援使用 PowerShell 資源庫所需的 NuGet 元件。
ms.openlocfilehash: eddbe15e7a765ad8b6df2b317a090269f06661d5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661114"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="86eb5-103">NuGet 提供者與 NuGet.exe 的啟動程序</span><span class="sxs-lookup"><span data-stu-id="86eb5-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="86eb5-104">NuGet.exe 不包含在最新的 NuGet 提供者中。</span><span class="sxs-lookup"><span data-stu-id="86eb5-104">NuGet.exe is not included in the latest NuGet provider.</span></span> <span data-ttu-id="86eb5-105">若要執行模組或指令碼的發行作業，PowerShellGet 需要二進位可執行檔 **NuGet.exe** 。</span><span class="sxs-lookup"><span data-stu-id="86eb5-105">For publish operations of either a module or script, PowerShellGet requires the binary executable **NuGet.exe**.</span></span> <span data-ttu-id="86eb5-106">所有其他作業 (包括「尋找」、「安裝」、「儲存」及「解除安裝」) 則只需要 NuGet 提供者。</span><span class="sxs-lookup"><span data-stu-id="86eb5-106">Only the NuGet provider is required for all other operations, including **find** , **install** , **save** , and **uninstall**.</span></span>
<span data-ttu-id="86eb5-107">PowerShellGet 包含可處理 NuGet 提供者與 NuGet.exe 之組合啟動載入或僅 NuGet 提供者之啟動載入的邏輯。</span><span class="sxs-lookup"><span data-stu-id="86eb5-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span> <span data-ttu-id="86eb5-108">在上述任一情況下，都應該只會顯示單一提示訊息。</span><span class="sxs-lookup"><span data-stu-id="86eb5-108">In either case, only a single prompt message should occur.</span></span> <span data-ttu-id="86eb5-109">如果電腦未連線至網際網路，使用者或管理員就必須將受信任之 NuGet 提供者和/或 NuGet.exe 檔案的執行個體複製到未連線的電腦。</span><span class="sxs-lookup"><span data-stu-id="86eb5-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

> [!NOTE]
> <span data-ttu-id="86eb5-110">從版本 6 開始，NuGet 提供者會包含在 PowerShell 的安裝中。</span><span class="sxs-lookup"><span data-stu-id="86eb5-110">Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span>

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="86eb5-111">解決在已連線至網際網路之電腦上尚未安裝 NuGet 提供者時的錯誤</span><span class="sxs-lookup"><span data-stu-id="86eb5-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based
repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\user1\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet
provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you
want PowerShellGet to install and import the NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure
that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based
repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\user1\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet
provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you
want PowerShellGet to install and import the NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="86eb5-112">解決在已連線至網際網路之電腦上執行發行作業的期間有 NuGet 提供者可用但沒有 NuGet.exe 可用時的錯誤</span><span class="sxs-lookup"><span data-stu-id="86eb5-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must
be available under one of the paths specified in PATH environment variable value. Do you want
PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure
that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must
be available under one of the paths specified in PATH environment variable value. Do you want
PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'.
Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="86eb5-113">解決在已連線至網際網路之電腦上執行發行作業的期間既沒有 NuGet 提供者也沒有 NuGet.exe 可用時的錯誤</span><span class="sxs-lookup"><span data-stu-id="86eb5-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with
the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer
to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of
NuGet provider is installed and NuGet.exe is available under one of the paths specified in PATH
environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with
the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'.
 Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="86eb5-114">在未連線至網際網路的電腦上手動啟動載入 NuGet 提供者</span><span class="sxs-lookup"><span data-stu-id="86eb5-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="86eb5-115">上面示範的程序是假設電腦已連線至網際網路，並且可從公用位置下載檔案。</span><span class="sxs-lookup"><span data-stu-id="86eb5-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span> <span data-ttu-id="86eb5-116">如果無法那麼做，則只能選擇使用上述程序來啟動載入電腦，然後透過受信任的離線程序將提供者手動複製到隔離的節點上。</span><span class="sxs-lookup"><span data-stu-id="86eb5-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span> <span data-ttu-id="86eb5-117">此情況最常見的使用案例是有可用的私用資源庫來支援隔離的環境時。</span><span class="sxs-lookup"><span data-stu-id="86eb5-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="86eb5-118">依照上述程序來啟動載入已連線至網際網路的電腦之後，您將可在下列位置找到提供者檔案：</span><span class="sxs-lookup"><span data-stu-id="86eb5-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

`C:\Program Files\PackageManagement\ProviderAssemblies\`

<span data-ttu-id="86eb5-119">NuGet 提供者的資料夾/檔案結構將會是 (版本號碼可能不同):</span><span class="sxs-lookup"><span data-stu-id="86eb5-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

<span data-ttu-id="86eb5-120">請使用受信任的程序將這些資料夾和檔案複製到離線電腦。</span><span class="sxs-lookup"><span data-stu-id="86eb5-120">Copy these folders and file using a trusted process to the offline machines.</span></span> <span data-ttu-id="86eb5-121">若要在離線電腦上使用提供者，便必須將其匯入。</span><span class="sxs-lookup"><span data-stu-id="86eb5-121">To use the provider on the offline machine, it must be imported.</span></span> <span data-ttu-id="86eb5-122">在離線電腦上執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="86eb5-122">Run the following command on the offline machine:</span></span>

```powershell
Import-PackageProvider -Name NuGet
```

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="86eb5-123">手動啟動載入 NuGet.exe 以支援在未連線至網際網路的電腦上執行發行作業</span><span class="sxs-lookup"><span data-stu-id="86eb5-123">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="86eb5-124">除了手動啟動載入 NuGet 提供者的程序之外，如果會使用 `Publish-Module` 或 `Publish-Script` Cmdlet 從該電腦將模組或指令碼發行至私用資源庫，將需要 NuGet.exe 二進位可執行檔。</span><span class="sxs-lookup"><span data-stu-id="86eb5-124">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the `Publish-Module` or `Publish-Script` cmdlets, the NuGet.exe binary executable file will be required.</span></span>

<span data-ttu-id="86eb5-125">此情況最常見的使用案例是有可用的私用資源庫來支援隔離的環境時。</span><span class="sxs-lookup"><span data-stu-id="86eb5-125">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span> <span data-ttu-id="86eb5-126">有兩個選項可取得 NuGet.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="86eb5-126">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="86eb5-127">其中一個選項是啟動載入已連線至網際網路的電腦，然後使用受信任的程序將檔案複製到離線電腦。</span><span class="sxs-lookup"><span data-stu-id="86eb5-127">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span> <span data-ttu-id="86eb5-128">啟動載入已連線至網際網路的電腦之後，NuGet.exe 二進位檔將會位於下列兩個資料夾其中之一：</span><span class="sxs-lookup"><span data-stu-id="86eb5-128">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

- <span data-ttu-id="86eb5-129">若使用提升的權限 (以系統管理員身分) 執行 `Publish-Module` 或 `Publish-Script` Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="86eb5-129">If the `Publish-Module` or `Publish-Script` cmdlets were executed with elevated permissions (As  an Administrator):</span></span>

   ```powershell
   $env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
   ```

- <span data-ttu-id="86eb5-130">如果以未提升權限的使用者身分執行 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="86eb5-130">If the cmdlets were executed as a user without elevated permissions:</span></span>

  ```powershell
  $env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
  ```

<span data-ttu-id="86eb5-131">第二個選項是從 NuGet.Org 網站下載 NuGet.exe：[https://dist.nuget.org/index.html](https://www.nuget.org/downloads) 為生產環境電腦選取 NugGet 版本時，請確定該版本比 2.8.5.208 還新，並確認已將該版本標示為「建議使用」。</span><span class="sxs-lookup"><span data-stu-id="86eb5-131">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span> <span data-ttu-id="86eb5-132">如果該檔案是透過瀏覽器下載的，請記得將檔案解除鎖定。</span><span class="sxs-lookup"><span data-stu-id="86eb5-132">Remember to unblock the file if it was downloaded using a browser.</span></span> <span data-ttu-id="86eb5-133">您可以使用 `Unblock-File` Cmdlet 來執行此操作。</span><span class="sxs-lookup"><span data-stu-id="86eb5-133">This can be performed by using the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="86eb5-134">不論使用哪一個選項，都可將 NuGet.exe 檔案複製到 `$env:path` 中的任何位置，但標準位置是：</span><span class="sxs-lookup"><span data-stu-id="86eb5-134">In either case, the NuGet.exe file can be copied to any location in `$env:path`, but the standard locations are:</span></span>

- <span data-ttu-id="86eb5-135">若要將可執行檔設為可用，以便讓所有使用者都可使用 `Publish-Module` 和 `Publish-Script` Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="86eb5-135">To make the executable available so that all users can use `Publish-Module` and `Publish-Script` cmdlets:</span></span>

  ```powershell
  $env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
  ```

- <span data-ttu-id="86eb5-136">若要將可執行檔設為僅供特定使用者使用，請只複製到該使用者之設定檔內的位置：</span><span class="sxs-lookup"><span data-stu-id="86eb5-136">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

  ```powershell
  $env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
  ```
