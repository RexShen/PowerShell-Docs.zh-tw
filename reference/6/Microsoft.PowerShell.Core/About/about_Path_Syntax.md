---
description: 描述 PowerShell 中的完整和相對路徑名稱格式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_path_syntax?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Path_Syntax
ms.openlocfilehash: deffa484328434aa987b217f48f25af1c182ddf0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206980"
---
# <a name="about-path-syntax"></a><span data-ttu-id="8f9d2-104">關於路徑語法</span><span class="sxs-lookup"><span data-stu-id="8f9d2-104">About Path Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="8f9d2-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="8f9d2-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="8f9d2-106">描述 PowerShell 中的完整和相對路徑名稱格式。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-106">Describes the full and relative path name formats in  PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="8f9d2-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="8f9d2-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="8f9d2-108">可透過 PowerShell 提供者存取之資料存放區中的所有專案，都可以透過其路徑名稱來唯一識別。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-108">All items in a data store accessible through a PowerShell provider can be uniquely identified by their path names.</span></span> <span data-ttu-id="8f9d2-109">路徑名稱是專案名稱、專案所在的容器和子容器的組合，以及用來存取容器的 PowerShell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-109">A path name is a combination of the item name, the container and subcontainers in which the item is located, and the PowerShell drive through which the containers are accessed.</span></span>

<span data-ttu-id="8f9d2-110">在 PowerShell 中，路徑名稱分為兩種類型：完整和相對。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-110">In PowerShell, path names are divided into one of two types: fully qualified and relative.</span></span> <span data-ttu-id="8f9d2-111">完整路徑名稱由組成路徑的所有元素組成。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-111">A fully qualified path name consists of all elements that make up a path.</span></span> <span data-ttu-id="8f9d2-112">下列語法顯示完整路徑名稱中的元素：</span><span class="sxs-lookup"><span data-stu-id="8f9d2-112">The following syntax shows the elements in a fully qualified path name:</span></span>

```powershell
[<provider>::]<drive>:[\<container>[\<subcontainer>...]]\<item>
```

<span data-ttu-id="8f9d2-113">\<provider\>預留位置是指您用來存取資料存放區的 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-113">The \<provider\> placeholder refers to the PowerShell provider through which you access the data store.</span></span> <span data-ttu-id="8f9d2-114">例如，FileSystem 提供者可讓您存取電腦上的檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-114">For example, the FileSystem provider allows you to access the files and directories on your computer.</span></span> <span data-ttu-id="8f9d2-115">這個語法的元素是選擇性的，而且永遠不需要，因為磁片磁碟機名稱在所有提供者中都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-115">This element of the syntax is optional and is never needed because the drive names are unique across all providers.</span></span>

<span data-ttu-id="8f9d2-116">\<drive\>預留位置是指特定 powershell 提供者所支援的 powershell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-116">The \<drive\> placeholder refers to the PowerShell drive that is supported by a particular PowerShell provider.</span></span> <span data-ttu-id="8f9d2-117">在 FileSystem 提供者的情況下，PowerShell 磁片磁碟機對應至您系統上設定的 Windows 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-117">In the case of the FileSystem provider, the PowerShell drives map to the Windows drives that are configured on your system.</span></span> <span data-ttu-id="8f9d2-118">例如，如果您的系統包含 A：磁片磁碟機和 C：磁片磁碟機，FileSystem 提供者會在 PowerShell 中建立相同的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-118">For example, if your system includes an A: drive and a C: drive, the FileSystem provider creates the same drives in PowerShell.</span></span>

<span data-ttu-id="8f9d2-119">指定磁片磁碟機之後，您必須指定包含該專案的任何容器和子容器。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-119">After you have specified the drive, you must specify any containers and subcontainers that contain the item.</span></span> <span data-ttu-id="8f9d2-120">您必須以它們存在於資料存放區中的階層順序來指定容器。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-120">The containers must be specified in the hierarchical order in which they exist in the data store.</span></span> <span data-ttu-id="8f9d2-121">換句話說，您必須從父容器開始，然後是父容器中的子容器，依此類推。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-121">In other words, you must start with the parent container, then the child container in that parent container, and so on.</span></span> <span data-ttu-id="8f9d2-122">此外，每個容器的前面都必須加上反斜線。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-122">In addition, each container must be preceded by a backslash.</span></span> <span data-ttu-id="8f9d2-123"> (請注意，PowerShell 可讓您使用正斜線來與其他 PowerShells 相容。 ) </span><span class="sxs-lookup"><span data-stu-id="8f9d2-123">(Note that PowerShell allows you to use forward slashes for compatibility with other PowerShells.)</span></span>

<span data-ttu-id="8f9d2-124">指定容器和子容器之後，您必須提供專案名稱，並在前面加上反斜線。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-124">After the container and subcontainers have been specified, you must provide the item name, preceded by a backslash.</span></span> <span data-ttu-id="8f9d2-125">例如，C： \\ Windows System32 目錄中 Shell.dll 檔案的完整路徑名稱如下所示 \\ ：</span><span class="sxs-lookup"><span data-stu-id="8f9d2-125">For example, the fully qualified path name for the Shell.dll file in the C:\\Windows\\System32 directory is as follows:</span></span>

```powershell
C:\Windows\System32\Shell.dll
```

<span data-ttu-id="8f9d2-126">在此情況下，用於存取容器的磁片磁碟機為 C：磁片磁碟機、最上層容器是 Windows、subcontainer 是位於 Windows 容器) 內的 System32 (，且該專案 Shell.dll。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-126">In this case, the drive through which the containers are accessed is the C: drive, the top-level container is Windows, the subcontainer is System32 (located within the Windows container), and the item is Shell.dll.</span></span>

<span data-ttu-id="8f9d2-127">在某些情況下，您不需要指定完整路徑名稱，而可以改為使用相對路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-127">In some situations, you do not need to specify a fully qualified path name and can instead use a relative path name.</span></span> <span data-ttu-id="8f9d2-128">相對路徑名稱是根據目前的工作位置。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-128">A relative path name is based on the current working location.</span></span> <span data-ttu-id="8f9d2-129">PowerShell 可讓您根據目前工作位置的相對位置來識別專案。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-129">PowerShell allows you to identify an item based on its location relative to the current working location.</span></span> <span data-ttu-id="8f9d2-130">您可以使用特殊字元來指定相對路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-130">You can specify relative path names by using special characters.</span></span> <span data-ttu-id="8f9d2-131">下表說明每個字元，並提供相對路徑名稱和完整路徑名稱的範例。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-131">The following table describes each of these characters and provides examples of relative path names and fully qualified path names.</span></span> <span data-ttu-id="8f9d2-132">資料表中的範例是以目前正在設定為 C:\windows。的工作目錄為基礎。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-132">The examples in the table are based on the current working directory being set to C:\Windows.</span></span>

|<span data-ttu-id="8f9d2-133">符號</span><span class="sxs-lookup"><span data-stu-id="8f9d2-133">Symbol</span></span>|<span data-ttu-id="8f9d2-134">描述</span><span class="sxs-lookup"><span data-stu-id="8f9d2-134">Description</span></span>               |<span data-ttu-id="8f9d2-135">相對路徑</span><span class="sxs-lookup"><span data-stu-id="8f9d2-135">Relative path</span></span>    |<span data-ttu-id="8f9d2-136">完整路徑</span><span class="sxs-lookup"><span data-stu-id="8f9d2-136">Full path</span></span>          |
|------|--------------------------|-----------------|-------------------|
|<span data-ttu-id="8f9d2-137">.</span><span class="sxs-lookup"><span data-stu-id="8f9d2-137">.</span></span>     |<span data-ttu-id="8f9d2-138">目前的位置</span><span class="sxs-lookup"><span data-stu-id="8f9d2-138">Current location</span></span>          |<span data-ttu-id="8f9d2-139">.\\系統</span><span class="sxs-lookup"><span data-stu-id="8f9d2-139">.\\System</span></span>        |<span data-ttu-id="8f9d2-140">c： \\ Windows \\ 系統</span><span class="sxs-lookup"><span data-stu-id="8f9d2-140">c:\\Windows\\System</span></span>|
|<span data-ttu-id="8f9d2-141">..</span><span class="sxs-lookup"><span data-stu-id="8f9d2-141">..</span></span>    |<span data-ttu-id="8f9d2-142">目前位置的父系</span><span class="sxs-lookup"><span data-stu-id="8f9d2-142">Parent of current location</span></span>|<span data-ttu-id="8f9d2-143">..\\Program Files</span><span class="sxs-lookup"><span data-stu-id="8f9d2-143">..\\Program Files</span></span>|<span data-ttu-id="8f9d2-144">c： \\ Program Files</span><span class="sxs-lookup"><span data-stu-id="8f9d2-144">c:\\Program Files</span></span>  |
|\     |<span data-ttu-id="8f9d2-145">目前的磁片磁碟機根目錄</span><span class="sxs-lookup"><span data-stu-id="8f9d2-145">Drive root of current</span></span>     |<span data-ttu-id="8f9d2-146">\\Program Files</span><span class="sxs-lookup"><span data-stu-id="8f9d2-146">\\Program Files</span></span>  |<span data-ttu-id="8f9d2-147">c： \\ Program Files</span><span class="sxs-lookup"><span data-stu-id="8f9d2-147">c:\\Program Files</span></span>  |
|      |<span data-ttu-id="8f9d2-148">location</span><span class="sxs-lookup"><span data-stu-id="8f9d2-148">location</span></span>                  |                 |                   |
|<span data-ttu-id="8f9d2-149">以上</span><span class="sxs-lookup"><span data-stu-id="8f9d2-149">[none]</span></span>|<span data-ttu-id="8f9d2-150">沒有特殊字元</span><span class="sxs-lookup"><span data-stu-id="8f9d2-150">No special characters</span></span>     |<span data-ttu-id="8f9d2-151">系統</span><span class="sxs-lookup"><span data-stu-id="8f9d2-151">System</span></span>           |<span data-ttu-id="8f9d2-152">c： \\ Windows \\ 系統</span><span class="sxs-lookup"><span data-stu-id="8f9d2-152">c:\\Windows\\System</span></span>|

<span data-ttu-id="8f9d2-153">當您在命令中使用路徑名稱時，您可以使用完整路徑名稱或相對路徑名稱的相同方式來輸入該名稱。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-153">When using a path name in a command, you enter that name in the same way whether you use a fully qualified path name or a relative one.</span></span> <span data-ttu-id="8f9d2-154">例如，假設您目前的工作目錄是 C:\windows。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-154">For example, suppose that your current working directory is C:\Windows.</span></span> <span data-ttu-id="8f9d2-155">下列 Get-ChildItem 命令會捕獲 C:\Techdocs 目錄中的所有專案：</span><span class="sxs-lookup"><span data-stu-id="8f9d2-155">The following Get-ChildItem command retrieves all items in the C:\Techdocs directory:</span></span>

```powershell
Get-ChildItem \techdocs
```

<span data-ttu-id="8f9d2-156">反斜線表示應該使用目前工作位置的磁片磁碟機根目錄。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-156">The backslash indicates that the drive root of the current working location should be used.</span></span> <span data-ttu-id="8f9d2-157">因為工作目錄是 C： \\ Windows，磁片磁碟機根目錄是 c：磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-157">Because the working directory is C:\\Windows, the drive root is the C: drive.</span></span> <span data-ttu-id="8f9d2-158">因為 techdocs 目錄位於根目錄，所以您只需要指定反斜線。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-158">Because the techdocs directory is located off the root, you need to specify only the backslash.</span></span>

<span data-ttu-id="8f9d2-159">您可以使用下列命令來達到相同的結果：</span><span class="sxs-lookup"><span data-stu-id="8f9d2-159">You can achieve the same results by using the following command:</span></span>

```powershell
Get-ChildItem c:\techdocs
```

<span data-ttu-id="8f9d2-160">無論您使用的是完整路徑名稱或相對路徑名稱，路徑名稱都不是唯一的，因為它會找出一個專案，但也是因為它會唯一識別該專案，即使該專案與其他容器中的另一個專案共用相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-160">Regardless of whether you use a fully qualified path name or a relative path name, a path name is important not only because it locates an item but also because it uniquely identifies the item even if that item shares the same name as another item in a different container.</span></span>

<span data-ttu-id="8f9d2-161">比方說，假設您有兩個名為 Results.txt 的檔案。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-161">For instance, suppose that you have two files that are each named Results.txt.</span></span>
<span data-ttu-id="8f9d2-162">第一個檔案位於名稱為 C： Techdocs Jan 的目錄中 \\ \\ ，而第二個檔案則位於名稱為 c： Techdocs 的目錄中 \\ \\ 。第一個檔案的路徑名稱 (C： \\ Techdocs \\ Jan \\Results.txt) 和第二個檔案的路徑名稱 (c： \\ Techdocs \\ 二月Results.txt) \\ 可讓您清楚區分這兩個檔案。</span><span class="sxs-lookup"><span data-stu-id="8f9d2-162">The first file is in a directory named C:\\Techdocs\\Jan, and the second file is in a directory named C:\\Techdocs\\Feb. The path name for the first file (C:\\Techdocs\\Jan\\Results.txt) and the path name for the second file (C:\\Techdocs\\Feb\\Results.txt) allow you to clearly distinguish between the two files.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f9d2-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f9d2-163">SEE ALSO</span></span>

[<span data-ttu-id="8f9d2-164">about_Locations</span><span class="sxs-lookup"><span data-stu-id="8f9d2-164">about_Locations</span></span>](about_Locations.md)
