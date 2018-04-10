---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 直接操作項目
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 688f9194bd16793331325999c69e88df3e94c976
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="6d44d-103">直接操作項目</span><span class="sxs-lookup"><span data-stu-id="6d44d-103">Manipulating Items Directly</span></span>

<span data-ttu-id="6d44d-104">您在 Windows PowerShell 磁碟機中看到的項目 (例如檔案系統磁碟機中的檔案與資料夾，以及 Windows PowerShell 登錄磁碟機中的登錄機碼) 在 Windows PowerShell 中稱為*項目*。</span><span class="sxs-lookup"><span data-stu-id="6d44d-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="6d44d-105">用於處理項目之 Cmdlet 的名稱中具有名詞 **Item**。</span><span class="sxs-lookup"><span data-stu-id="6d44d-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="6d44d-106">**Get-Command -Noun Item** 命令的輸出顯示有九個 Windows PowerShell 項目 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6d44d-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

### <a name="creating-new-items-new-item"></a><span data-ttu-id="6d44d-107">建立新項目 (New-Item)</span><span class="sxs-lookup"><span data-stu-id="6d44d-107">Creating New Items (New-Item)</span></span>

<span data-ttu-id="6d44d-108">若要在檔案系統中建立新項目，請使用 **New-Item** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6d44d-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="6d44d-109">包含 **Path** 參數並指定項目路徑作為參數值，以及包含 **ItemType** 參數並指定 "file" 或 "directory" 的值。</span><span class="sxs-lookup"><span data-stu-id="6d44d-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="6d44d-110">例如，若要在 C:\\Temp 目錄中建立名為 "New.Directory" 的新目錄，請輸入：</span><span class="sxs-lookup"><span data-stu-id="6d44d-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="6d44d-111">若要建立檔案，請將 **ItemType** 參數的值變更為 "file"。</span><span class="sxs-lookup"><span data-stu-id="6d44d-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="6d44d-112">例如，若要在 New.Directory 目錄中建立名為 "file1.txt" 的檔案，請輸入：</span><span class="sxs-lookup"><span data-stu-id="6d44d-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="6d44d-113">您可以使用相同的方式來建立新的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="6d44d-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="6d44d-114">事實上，建立登錄機碼的方式較簡單，因為 Windows 登錄中唯一的項目類型是機碼。</span><span class="sxs-lookup"><span data-stu-id="6d44d-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="6d44d-115">(登錄項目是項目*屬性*。)例如，若要在 CurrentVersion 子機碼中建立名為 "_Test" 的機碼，請輸入：</span><span class="sxs-lookup"><span data-stu-id="6d44d-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="6d44d-116">輸入登錄路徑時，請務必在 Windows PowerShell 磁碟機名稱中包含冒號 (**:**)，亦即 HKLM: 與 HKCU:。</span><span class="sxs-lookup"><span data-stu-id="6d44d-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="6d44d-117">若未使用冒號，Windows PowerShell 將無法識別該路徑中的磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="6d44d-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

### <a name="why-registry-values-are-not-items"></a><span data-ttu-id="6d44d-118">為什麼登錄值不是項目</span><span class="sxs-lookup"><span data-stu-id="6d44d-118">Why Registry Values are not Items</span></span>

<span data-ttu-id="6d44d-119">當您使用 **Get-ChildItem** Cmdlet 來尋找登錄機碼中的項目時，您將永遠不會看到實際的登錄項目或其值。</span><span class="sxs-lookup"><span data-stu-id="6d44d-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="6d44d-120">例如，登錄機碼 **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** 通常包含數個登錄項目，這些登錄項目代表系統啟動時執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6d44d-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="6d44d-121">不過，當您使用 **Get-ChildItem** 來尋找機碼中的子項目時，您只會看到該機碼的 **OptionalComponents** 子機碼：</span><span class="sxs-lookup"><span data-stu-id="6d44d-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="6d44d-122">雖然將登錄項目視為項目很方便，但您無法在指定登錄項目路徑時確保其唯一性。</span><span class="sxs-lookup"><span data-stu-id="6d44d-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="6d44d-123">路徑標記法無法區分名為 **Run** 的登錄子機碼與 **Run** 子機碼中的 **(Default)** 登錄項目。</span><span class="sxs-lookup"><span data-stu-id="6d44d-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="6d44d-124">此外，因為登錄項目名稱可以包含反斜線字元 (**\\**)，若登錄項目是項目，您無法使用路徑標記法來區分名為 **Windows\\CurrentVersion\\Run** 的登錄項目與該路徑中的子機碼。</span><span class="sxs-lookup"><span data-stu-id="6d44d-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if regsitry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

### <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="6d44d-125">重新命名現有的項目 (Rename-Item)</span><span class="sxs-lookup"><span data-stu-id="6d44d-125">Renaming Existing Items (Rename-Item)</span></span>

<span data-ttu-id="6d44d-126">若要變更檔案或資料夾的名稱，請使用 **Rename-Item** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6d44d-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="6d44d-127">下列命令會將 **file1.txt** 檔案的名稱變更為 **fileOne.txt**。</span><span class="sxs-lookup"><span data-stu-id="6d44d-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="6d44d-128">**Rename-Item** Cmdlet 可以變更檔案或資料夾的名稱，但無法移動項目。</span><span class="sxs-lookup"><span data-stu-id="6d44d-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="6d44d-129">下列命令會失敗。因為它會嘗試將檔案從 New.Directory 目錄移動到 Temp 目錄。</span><span class="sxs-lookup"><span data-stu-id="6d44d-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### <a name="moving-items-move-item"></a><span data-ttu-id="6d44d-130">移動項目 (Move-Item)</span><span class="sxs-lookup"><span data-stu-id="6d44d-130">Moving Items (Move-Item)</span></span>

<span data-ttu-id="6d44d-131">若要移動檔案或資料夾，請使用 **Move-Item** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6d44d-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="6d44d-132">例如，下列命令會將 New.Directory 目錄從 C:\\temp 目錄移動到 C: 磁碟機的根目錄。</span><span class="sxs-lookup"><span data-stu-id="6d44d-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="6d44d-133">若要確定項目已移動，請包含 **Move-Item** Cmdlet 的 **PassThru** 參數。</span><span class="sxs-lookup"><span data-stu-id="6d44d-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="6d44d-134">若未指定 **Passthru**，**Move-Item** Cmdlet 不會顯示任何結果。</span><span class="sxs-lookup"><span data-stu-id="6d44d-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### <a name="copying-items-copy-item"></a><span data-ttu-id="6d44d-135">複製項目 (Copy-Item)</span><span class="sxs-lookup"><span data-stu-id="6d44d-135">Copying Items (Copy-Item)</span></span>

<span data-ttu-id="6d44d-136">若您熟悉其他殼層中的複製操作，您可能會發現 Windows PowerShell 中 **Copy-Item** Cmdlet 的行為不尋常。</span><span class="sxs-lookup"><span data-stu-id="6d44d-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="6d44d-137">當您將某個項目從一個位置複製到另一個位置時，Copy-Item 預設不會複製其內容。</span><span class="sxs-lookup"><span data-stu-id="6d44d-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="6d44d-138">例如，若您將 **New.Directory** 目錄從 C: 磁碟機複製到 C:\\temp 目錄，該命令會成功，但不會複製 New.Directory 目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="6d44d-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="6d44d-139">若顯示 **C:\\temp\\New.Directory** 的內容，您會發現其中未包含任何檔案：</span><span class="sxs-lookup"><span data-stu-id="6d44d-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="6d44d-140">為什麼 **Copy-Item** Cmdlet 不會將內容複製到新位置？</span><span class="sxs-lookup"><span data-stu-id="6d44d-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="6d44d-141">**Copy-Item** Cmdlet 被設計為泛型；它不是只能用來複製檔案與資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d44d-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="6d44d-142">此外，即使複製檔案與資料夾時，您可能只想複製容器，而非其中的項目。</span><span class="sxs-lookup"><span data-stu-id="6d44d-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="6d44d-143">若要複製資料夾中的所有內容，請在命令中包含 **Copy-Item** Cmdlet 的 **Recurse** 參數。</span><span class="sxs-lookup"><span data-stu-id="6d44d-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="6d44d-144">若已複製目錄但未複製其內容，請新增 **Force** 參數，這樣可以讓您覆寫空資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d44d-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

### <a name="deleting-items-remove-item"></a><span data-ttu-id="6d44d-145">刪除項目 (Remove-Item)</span><span class="sxs-lookup"><span data-stu-id="6d44d-145">Deleting Items (Remove-Item)</span></span>

<span data-ttu-id="6d44d-146">若要刪除檔案與資料夾，請使用 **Remove-Item** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6d44d-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="6d44d-147">會造成大幅且無法復原之變更的 Windows PowerShell Cmdlet (例如 **Remove-Item**) 通常會在您輸入其命令時提示您確認。</span><span class="sxs-lookup"><span data-stu-id="6d44d-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="6d44d-148">例如，若嘗試移除 **New.Directory** 資料夾，系統會提示您確認要執行該命令，因為資料夾包含檔案：</span><span class="sxs-lookup"><span data-stu-id="6d44d-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="6d44d-149">因為 **[是]** 是預設回應，若要刪除資料夾與其中的檔案，請按 **Enter** 鍵。</span><span class="sxs-lookup"><span data-stu-id="6d44d-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="6d44d-150">若要在不確認的情況下移除資料夾，請使用 **-Recurse** 參數。</span><span class="sxs-lookup"><span data-stu-id="6d44d-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

### <a name="executing-items-invoke-item"></a><span data-ttu-id="6d44d-151">執行項目 (Invoke-Item)</span><span class="sxs-lookup"><span data-stu-id="6d44d-151">Executing Items (Invoke-Item)</span></span>

<span data-ttu-id="6d44d-152">Windows PowerShell 使用 **Invoke-Item** Cmdlet 來針對檔案或資料夾執行預設動作。</span><span class="sxs-lookup"><span data-stu-id="6d44d-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="6d44d-153">此預設動作是由登錄中的預設應用程式處理常式決定；效果等同於在 [檔案總管] 中按兩下該項目。</span><span class="sxs-lookup"><span data-stu-id="6d44d-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="6d44d-154">例如，假設您執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="6d44d-154">For example, suppose you run the following command:</span></span>

```powershell
Invoke-Item C:\WINDOWS
```

<span data-ttu-id="6d44d-155">隨即出現檔案總管視窗 (顯示 C:\\Windows)，就像您按兩下 C:\\Windows 資料夾一樣。</span><span class="sxs-lookup"><span data-stu-id="6d44d-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="6d44d-156">若在 Windows Vista 之前的系統上叫用 **Boot.ini** 檔案：</span><span class="sxs-lookup"><span data-stu-id="6d44d-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```powershell
Invoke-Item C:\boot.ini
```

<span data-ttu-id="6d44d-157">若 .ini 檔案類型與 [記事本] 關聯，boot.ini 檔案會在 [記事本] 中開啟。</span><span class="sxs-lookup"><span data-stu-id="6d44d-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>