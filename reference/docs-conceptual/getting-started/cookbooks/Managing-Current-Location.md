---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 管理目前的位置
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: d1ebc9507a45841e6d4d8219e45c002990e1328c
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225772"
---
# <a name="managing-current-location"></a><span data-ttu-id="ba6fc-103">管理目前的位置</span><span class="sxs-lookup"><span data-stu-id="ba6fc-103">Managing Current Location</span></span>

<span data-ttu-id="ba6fc-104">瀏覽 [檔案總管] 中的資料夾系統時，您通常有特定的工作位置，亦即目前開啟的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="ba6fc-105">只要按一下目前資料夾中的項目，即可輕鬆地操作這些項目。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="ba6fc-106">對於命令列介面 (例如 Cmd.exe)，當位在與特定檔案相同的資料夾中時，您可以指定相對短的名稱來存取該檔案，而不需要指定該檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="ba6fc-107">目前的目錄稱為工作目錄。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="ba6fc-108">Windows PowerShell 使用名詞 **Location** 來參照工作目錄，並實作一系列的 Cmdlet 來檢查及操作您的位置。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

### <a name="getting-your-current-location-get-location"></a><span data-ttu-id="ba6fc-109">取得目前的位置 (Get-Location)</span><span class="sxs-lookup"><span data-stu-id="ba6fc-109">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="ba6fc-110">若要判斷目前目錄位置的路徑，請輸入 **Get-Location** 命令：</span><span class="sxs-lookup"><span data-stu-id="ba6fc-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="ba6fc-111">Get-Location Cmdlet 類似 BASH 殼層中的 **pwd** 命令。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="ba6fc-112">Set-Location Cmdlet 類似 Cmd.exe 中的 **cd** 命令。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

### <a name="setting-your-current-location-set-location"></a><span data-ttu-id="ba6fc-113">設定目前的位置 (Set-Location)</span><span class="sxs-lookup"><span data-stu-id="ba6fc-113">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="ba6fc-114">**Get-Location** 命令是用來搭配 **Set-Location** 命令使用。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="ba6fc-115">**Set-Location** 命令可讓您指定目前的目錄位置。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="ba6fc-116">輸入命令之後，您將會注意到您沒有收到有關該命令之效果的任何直接回饋。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="ba6fc-117">執行動作的大部分 Windows PowerShell 命令都只會產生一些輸出或甚至不產生輸出，因為輸出不見得實用。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="ba6fc-118">當您輸入 **Set-Location** 命令時，若要確定已順利變更目錄，請在輸入 **Set-Location** 命令時包含 **-PassThru** 參數：</span><span class="sxs-lookup"><span data-stu-id="ba6fc-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="ba6fc-119">**-PassThru** 參數可以搭配 Windows PowerShell 中的許多 Set 命令使用以傳回結果的相關資訊，這在沒有預設輸出的情況下可能會有用。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="ba6fc-120">您可以指定目前位置的相對路徑，就像您在大部分的 UNIX 與 Windows 命令殼層中所指定一樣。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="ba6fc-121">在相對路徑的標準標記法中，句點 (**.**) 代表目前的資料夾，而雙句點 (**..**) 代表目前位置的上層目錄。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="ba6fc-122">例如，若目前資料夾為 **C:\\Windows**，則句點 (**.**) 代表 **C:\\Windows**，而雙句點 (**..**) 代表 **C:**。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="ba6fc-123">輸入下列命令，即可從目前的位置變更到 C: 磁碟機的根目錄：</span><span class="sxs-lookup"><span data-stu-id="ba6fc-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="ba6fc-124">相同的方法在並非檔案系統磁碟機的 Windows PowerShell 磁碟機 (例如 **HKLM:**) 上也適用。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="ba6fc-125">輸入下列命令，即可將您的位置設定為登錄中的 HKLM\\Software 機碼：</span><span class="sxs-lookup"><span data-stu-id="ba6fc-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="ba6fc-126">接著，您可以使用相對路徑，將該目錄位置變更為上層目錄 (Windows PowerShell HKLM: 磁碟機的根目錄)：</span><span class="sxs-lookup"><span data-stu-id="ba6fc-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="ba6fc-127">您可以輸入 Set-Location 或使用 Set-Location 的任一內建 Windows PowerShell 別名 (cd、chdir、sl)。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="ba6fc-128">例如：</span><span class="sxs-lookup"><span data-stu-id="ba6fc-128">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="ba6fc-129">儲存及重新叫用最近的位置 (Push-Location 與 Pop-Location)</span><span class="sxs-lookup"><span data-stu-id="ba6fc-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="ba6fc-130">變更位置時，記錄曾使用的位置以及回到先前的位置可能是非常實用的功能。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="ba6fc-131">Windows PowerShell 中的 **Push-Location** Cmdlet 會建立您曾使用之目錄路徑的已排序歷程記錄 (堆疊)，而且您可以使用對應的 **Pop-Location** Cmdlet 來重新叫用歷程記錄中的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="ba6fc-132">例如，Windows PowerShell 通常會在使用者的主目錄啟動。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="ba6fc-133">*堆疊*一詞在許多程式設計設定中具有特殊意義，包括 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="ba6fc-134">就像項目的實體堆疊，您最後放入堆疊中的項目，是您可以從堆疊中取出第一個項目。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="ba6fc-135">將項目新增到堆疊是將項目「推送」到堆疊。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="ba6fc-136">從堆疊取出項目是將項目從堆疊「取出」。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="ba6fc-137">若要將目前位置推送到堆疊，然後將它移動到 Local Settings 資料夾，請輸入：</span><span class="sxs-lookup"><span data-stu-id="ba6fc-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="ba6fc-138">輸入下列命令，即可接著將 Local Settings 位置推送到堆疊，然後將它移動到 Temp 資料夾：</span><span class="sxs-lookup"><span data-stu-id="ba6fc-138">You can then push the Local Settings location onto the stack and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="ba6fc-139">您可以輸入 **Get-Location** 命令，確認已順利變更目錄：</span><span class="sxs-lookup"><span data-stu-id="ba6fc-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="ba6fc-140">您可以輸入 **Pop-Location** 命令以取回最近瀏覽的目錄，並輸入 **Get-Location** 命令以確認變更：</span><span class="sxs-lookup"><span data-stu-id="ba6fc-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="ba6fc-141">就像使用 **Set-Location** Cmdlet 一樣，您可以在輸入 **Pop-Location** Cmdlet 時包含 **-PassThru** 參數，以顯示您輸入的目錄：</span><span class="sxs-lookup"><span data-stu-id="ba6fc-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="ba6fc-142">您也可以使用 Location Cmdlet 來搭配網路路徑。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="ba6fc-143">若您有名為 FS01 的伺服器與名為 Public 的共用，您可以變更位置，方式是輸入</span><span class="sxs-lookup"><span data-stu-id="ba6fc-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="ba6fc-144">或</span><span class="sxs-lookup"><span data-stu-id="ba6fc-144">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="ba6fc-145">您可以使用 **Push-Location** 與 **Set-Location** 命令將位置變更至任何可用的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="ba6fc-146">例如，若您有磁碟機代號為 D 的本機 CD-ROM 光碟機，且其中有資料 CD，您可以輸入 **Set-Location D:** 命令，以將位置變更到該 CD 光碟機。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="ba6fc-147">若該磁碟機是空的，您將會看到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="ba6fc-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="ba6fc-148">使用命令列介面時，用 [檔案總管] 來檢查可用的實體磁碟機並不方便。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="ba6fc-149">此外，[檔案總管] 將不會顯示所有 Windows PowerShell 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="ba6fc-150">Windows PowerShell 提供一組可用於操作 Windows PowerShell 磁碟機的命令，稍後我們將討論這些命令。</span><span class="sxs-lookup"><span data-stu-id="ba6fc-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>
