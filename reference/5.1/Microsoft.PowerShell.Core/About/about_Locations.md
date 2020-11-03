---
description: 說明如何從 PowerShell 中的工作位置存取專案。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_locations?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Locations
ms.openlocfilehash: ed8d17b7f217c86ba3161f017e2794524d5da829
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207628"
---
# <a name="about_locations"></a><span data-ttu-id="f51d3-104">about_Locations</span><span class="sxs-lookup"><span data-stu-id="f51d3-104">about_Locations</span></span>

## <a name="short-description"></a><span data-ttu-id="f51d3-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="f51d3-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="f51d3-106">說明如何從 PowerShell 中的工作位置存取專案。</span><span class="sxs-lookup"><span data-stu-id="f51d3-106">Describes how to access items from the working location in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="f51d3-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="f51d3-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="f51d3-108">目前的工作位置是命令指向的預設位置。</span><span class="sxs-lookup"><span data-stu-id="f51d3-108">The current working location is the default location to which commands point.</span></span>
<span data-ttu-id="f51d3-109">換句話說，如果您未提供指向受命令影響的專案或位置的明確路徑，則這是 PowerShell 所使用的位置。</span><span class="sxs-lookup"><span data-stu-id="f51d3-109">In other words, this is the location that PowerShell uses if you do not supply an explicit path to the item or location that is affected by the command.</span></span> <span data-ttu-id="f51d3-110">在大部分情況下，目前的工作位置是透過 PowerShell FileSystem 提供者存取的磁片磁碟機，在某些情況下，則是該磁片磁碟機上的目錄。</span><span class="sxs-lookup"><span data-stu-id="f51d3-110">In most cases, the current working location is a drive accessed through the PowerShell FileSystem provider and, in some cases, a directory on that drive.</span></span>
<span data-ttu-id="f51d3-111">例如，您可以將目前的工作位置設定為下列位置：</span><span class="sxs-lookup"><span data-stu-id="f51d3-111">For example, you might set your current working location to the following location:</span></span>

```powershell
C:\Program Files\Windows PowerShell
```

<span data-ttu-id="f51d3-112">因此，除非明確提供另一個路徑，否則所有命令都會從這個位置處理。</span><span class="sxs-lookup"><span data-stu-id="f51d3-112">As a result, all commands are processed from this location unless another path is explicitly provided.</span></span>

<span data-ttu-id="f51d3-113">即使磁片磁碟機不是目前磁片磁碟機，PowerShell 仍會維護每個磁片磁碟機目前的工作位置。</span><span class="sxs-lookup"><span data-stu-id="f51d3-113">PowerShell maintains the current working location for each drive even when the drive is not the current drive.</span></span> <span data-ttu-id="f51d3-114">這可讓您只參考另一個位置的磁片磁碟機，從目前的工作位置存取專案。</span><span class="sxs-lookup"><span data-stu-id="f51d3-114">This allows you to access items from the current working location by referring only to the drive of another location.</span></span>
<span data-ttu-id="f51d3-115">例如，假設您目前的工作位置是 C： \\ Windows。</span><span class="sxs-lookup"><span data-stu-id="f51d3-115">For example, suppose that your current working location is C:\\Windows.</span></span> <span data-ttu-id="f51d3-116">現在，假設您使用下列命令將目前的工作位置變更為 HKLM：磁片磁碟機：</span><span class="sxs-lookup"><span data-stu-id="f51d3-116">Now, suppose you use the following command to change your current working location to the HKLM: drive:</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="f51d3-117">雖然目前的位置現在是登錄磁片磁碟機，但您仍然可以 \\ 使用 c：磁片磁碟機存取 c： Windows 目錄中的專案，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f51d3-117">Although your current location is now the registry drive, you can still access items in the C:\\Windows directory simply by using the C: drive, as shown in the following example:</span></span>

```powershell
Get-ChildItem C:
```

<span data-ttu-id="f51d3-118">PowerShell 會記住，該磁片磁碟機目前的工作位置是 Windows 目錄，因此它會從該目錄抓取專案。</span><span class="sxs-lookup"><span data-stu-id="f51d3-118">PowerShell remembers that your current working location for that drive is the Windows directory, so it retrieves items from that directory.</span></span> <span data-ttu-id="f51d3-119">如果您執行下列命令，結果會相同：</span><span class="sxs-lookup"><span data-stu-id="f51d3-119">The results would be the same if you ran the following command:</span></span>

```powershell
Get-ChildItem C:\Windows
```

<span data-ttu-id="f51d3-120">在 PowerShell 中，您可以使用 Get-Location 命令判斷目前的工作位置，也可以使用 Set-Location 命令來設定目前的工作位置。</span><span class="sxs-lookup"><span data-stu-id="f51d3-120">In PowerShell, you can use the Get-Location command to determine the current working location, and you can use the Set-Location command to set the current working location.</span></span> <span data-ttu-id="f51d3-121">例如，下列命令會將目前的工作位置設定為 C：磁片磁碟機的 Windows 目錄：</span><span class="sxs-lookup"><span data-stu-id="f51d3-121">For example, the following command sets the current working location to the Windows directory of the C: drive:</span></span>

```powershell
Set-Location c:\windows
```

<span data-ttu-id="f51d3-122">設定目前的工作位置之後，您仍然可以從其他磁片磁碟機存取專案，只要在命令中包含磁片磁碟機名稱 (後面加上冒號) 即可，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f51d3-122">After you set the current working location, you can still access items from other drives simply by including the drive name (followed by a colon) in the command, as shown in the following example:</span></span>

```powershell
Get-ChildItem HKLM:\software
```

<span data-ttu-id="f51d3-123">範例命令會抓取登錄中 HKEY 本機電腦 hive 的 Software 容器中的專案清單。</span><span class="sxs-lookup"><span data-stu-id="f51d3-123">The example command retrieves a list of items in the Software container of the HKEY Local Machine hive in the registry.</span></span>

<span data-ttu-id="f51d3-124">PowerShell 也可讓您使用特殊字元來代表目前的工作位置和其父位置。</span><span class="sxs-lookup"><span data-stu-id="f51d3-124">PowerShell also allows you to use special characters to represent the current working location and its parent location.</span></span> <span data-ttu-id="f51d3-125">若要表示目前的工作位置，請使用單一句點。</span><span class="sxs-lookup"><span data-stu-id="f51d3-125">To represent the current working location, use a single period.</span></span> <span data-ttu-id="f51d3-126">若要表示目前工作位置的父系，請使用兩個句點。</span><span class="sxs-lookup"><span data-stu-id="f51d3-126">To represent the parent of the current working location, use two periods.</span></span> <span data-ttu-id="f51d3-127">例如，下列程式會指定目前工作位置中的系統子目錄：</span><span class="sxs-lookup"><span data-stu-id="f51d3-127">For example, the following specifies the System subdirectory in the current working location:</span></span>

```powershell
Get-ChildItem .\system
```

<span data-ttu-id="f51d3-128">如果目前的工作位置是 C： \\ windows，此命令會傳回 c： windows 系統中所有專案的 \\ 清單 \\ 。</span><span class="sxs-lookup"><span data-stu-id="f51d3-128">If the current working location is C:\\Windows, this command returns a list of all the items in C:\\Windows\\System.</span></span> <span data-ttu-id="f51d3-129">但是，如果您使用兩個句點，則會使用目前工作目錄的父目錄，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f51d3-129">However, if you use two periods, the parent directory of the current working directory is used, as shown in the following example:</span></span>

```powershell
Get-ChildItem ..\"program files"
```

<span data-ttu-id="f51d3-130">在此情況下，PowerShell 會將兩個句點視為 C：磁片磁碟機，因此命令會抓取 C： Program Files 目錄中的所有專案 \\ 。</span><span class="sxs-lookup"><span data-stu-id="f51d3-130">In this case, PowerShell treats the two periods as the C: drive, so the command retrieves all the items in the C:\\Program Files directory.</span></span>

<span data-ttu-id="f51d3-131">開頭為斜線的路徑會識別來自目前磁片磁碟機根目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="f51d3-131">A path beginning with a slash identifies a path from the root of the current drive.</span></span> <span data-ttu-id="f51d3-132">例如，如果您目前的工作位置是 C： \\ Program Files \\ PowerShell，則磁片磁碟機的根目錄是 c。因此，下列命令會列出 C： Windows 目錄中的所有專案 \\ ：</span><span class="sxs-lookup"><span data-stu-id="f51d3-132">For example, if your current working location is C:\\Program Files\\PowerShell, the root of your drive is C. Therefore, the following command lists all items in the C:\\Windows directory:</span></span>

```powershell
Get-ChildItem \windows
```

<span data-ttu-id="f51d3-133">如果您在提供容器或專案的名稱時，未指定以磁片磁碟機名稱、斜線或句號開頭的路徑，則會假設容器或專案位於目前的工作位置。</span><span class="sxs-lookup"><span data-stu-id="f51d3-133">If you do not specify a path beginning with a drive name, slash, or period when supplying the name of a container or item, the container or item is assumed to be located in the current working location.</span></span> <span data-ttu-id="f51d3-134">例如，如果您目前的工作位置是 C： \\ windows，則下列命令會傳回 c： \\ windows 系統目錄中的所有專案 \\ ：</span><span class="sxs-lookup"><span data-stu-id="f51d3-134">For example, if your current working location is C:\\Windows, the following command returns all the items in the C:\\Windows\\System directory:</span></span>

```powershell
Get-ChildItem system
```

<span data-ttu-id="f51d3-135">如果您指定檔案名而不是目錄名稱，則 PowerShell 會傳回該檔案的詳細資料， (假設該檔案位於目前工作位置) 。</span><span class="sxs-lookup"><span data-stu-id="f51d3-135">If you specify a file name rather than a directory name, PowerShell returns details about that file (assuming that file is located in the current working location).</span></span>

## <a name="see-also"></a><span data-ttu-id="f51d3-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f51d3-136">SEE ALSO</span></span>

[<span data-ttu-id="f51d3-137">Set-Location</span><span class="sxs-lookup"><span data-stu-id="f51d3-137">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

[<span data-ttu-id="f51d3-138">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f51d3-138">about_Providers</span></span>](about_Providers.md)

[<span data-ttu-id="f51d3-139">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="f51d3-139">about_Path_Syntax</span></span>](about_Path_Syntax.md)
