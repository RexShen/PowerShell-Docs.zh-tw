---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用檔案及資料夾
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 6b1fcd438570c8708aa87e4b213f33474921d5f8
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31201014"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="2bc4a-103">使用檔案及資料夾</span><span class="sxs-lookup"><span data-stu-id="2bc4a-103">Working with Files and Folders</span></span>

<span data-ttu-id="2bc4a-104">瀏覽 Windows PowerShell 磁碟機和操作磁碟機上的項目，類似於在 Windows 實體磁碟機上操作檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="2bc4a-105">本節會討論如何使用 PowerShell 來處理特定檔案和資料夾操作工作。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

### <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="2bc4a-106">列出資料夾內所有的檔案和資料夾</span><span class="sxs-lookup"><span data-stu-id="2bc4a-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="2bc4a-107">您可以使用 **Get-ChildItem** 直接取得資料夾內的所有項目。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="2bc4a-108">加入選用的 **Force** 參數，以顯示隱藏或系統項目。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="2bc4a-109">例如，這個命令會顯示 Windows PowerShell 磁碟機 C (和 Windows 實體磁碟機 C 相同) 的直接內容︰</span><span class="sxs-lookup"><span data-stu-id="2bc4a-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="2bc4a-110">命令只會列出直接包含的項目，很像使用 Cmd.exe 的 **DIR** 命令或 UNIX 殼層的 **ls**。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="2bc4a-111">若要顯示包含的項目，您也必須要指定 **-Recurse** 參數。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="2bc4a-112">(這可能需要很長時間才能完成)。列出 C 磁碟機上的所有項目︰</span><span class="sxs-lookup"><span data-stu-id="2bc4a-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="2bc4a-113">**Get-ChildItem** 可以用它的 **Path**、**Filter**、**Include** 和 **Exclude** 參數來篩選項目，但這些通常只以名稱為基礎。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="2bc4a-114">您可以使用 **Where-Object** 根據項目的其他屬性來執行複雜的篩選。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="2bc4a-115">下列命令會在 Program Files 資料夾內尋找在 2005 年 10 月 1 日之後修改的、介於 1 MB 到 10 MB 之間的全部可執行檔︰</span><span class="sxs-lookup"><span data-stu-id="2bc4a-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

### <a name="copying-files-and-folders"></a><span data-ttu-id="2bc4a-116">複製檔案與資料夾</span><span class="sxs-lookup"><span data-stu-id="2bc4a-116">Copying Files and Folders</span></span>

<span data-ttu-id="2bc4a-117">以 **Copy-Item** 完成複製。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="2bc4a-118">下列命令會將 C:\\boot.ini 備份到 C:\\boot.bak：</span><span class="sxs-lookup"><span data-stu-id="2bc4a-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="2bc4a-119">如果目的地檔案已經存在，則複製嘗試就會失敗。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="2bc4a-120">若要覆寫既有的目的地，請使用 **Force** 參數：</span><span class="sxs-lookup"><span data-stu-id="2bc4a-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="2bc4a-121">這個命令對唯讀的目的地也有效。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="2bc4a-122">複製資料夾的方式也相同。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-122">Folder copying works the same way.</span></span> <span data-ttu-id="2bc4a-123">這個命令會將資料夾 C:\\temp\\test1 以遞迴方式複製到新的資料夾 C:\\temp\\DeleteMe：</span><span class="sxs-lookup"><span data-stu-id="2bc4a-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="2bc4a-124">您也可以複製選取的項目。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-124">You can also copy a selection of items.</span></span> <span data-ttu-id="2bc4a-125">下列命令會將 c:\\data 中任何位置的所有 .txt 檔案複製到 c:\\temp\\text︰</span><span class="sxs-lookup"><span data-stu-id="2bc4a-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="2bc4a-126">您仍然可以使用其他工具執行檔案系統複製。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="2bc4a-127">XCOPY、ROBOCOPY 和 COM 物件，如 **Scripting.FileSystemObject**，在 Windows PowerShell 中都有效。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="2bc4a-128">例如，您可以使用 Windows Script Host **Scripting.FileSystem COM** 類別將 C:\\boot.ini 備份到 C:\\boot.bak︰</span><span class="sxs-lookup"><span data-stu-id="2bc4a-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

### <a name="creating-files-and-folders"></a><span data-ttu-id="2bc4a-129">建立檔案與資料夾</span><span class="sxs-lookup"><span data-stu-id="2bc4a-129">Creating Files and Folders</span></span>

<span data-ttu-id="2bc4a-130">所有 Windows PowerShell 提供者的建立新項目功能都一樣。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="2bc4a-131">如果 Windows PowerShell 提供者有多個項目類型—例如，FileSystem Windows PowerShell 提供者區分目錄和檔案—您就需要指定項目類型。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="2bc4a-132">這個命令會建立新的資料夾 C:\\temp\\New Folder：</span><span class="sxs-lookup"><span data-stu-id="2bc4a-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="2bc4a-133">這個命令會建立新的空檔案 C:\\temp\\New Folder\\file.txt</span><span class="sxs-lookup"><span data-stu-id="2bc4a-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

### <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="2bc4a-134">移除資料夾內所有的檔案和資料夾</span><span class="sxs-lookup"><span data-stu-id="2bc4a-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="2bc4a-135">您可以使用 **Remove-Item** 移除包含的項目，但如果項目包含任何其他項目，系統會提示您確認移除。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="2bc4a-136">例如，如果您嘗試刪除包含其他項目的資料夾 C:\\temp\\DeleteMe，Windows PowerShell 就會先提示您確認再刪除資料夾︰</span><span class="sxs-lookup"><span data-stu-id="2bc4a-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="2bc4a-137">如果不想每個包含項目都出現提示，請指定 **Recurse** 參數：</span><span class="sxs-lookup"><span data-stu-id="2bc4a-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a><span data-ttu-id="2bc4a-138">將本機資料夾對應為 Windows 可存取磁碟機</span><span class="sxs-lookup"><span data-stu-id="2bc4a-138">Mapping a Local Folder as a Windows Accessible Drive</span></span>

<span data-ttu-id="2bc4a-139">您也可以使用 **subst** 命令對應本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-139">You can also map a local folder, using the **subst** command.</span></span> <span data-ttu-id="2bc4a-140">下列命令會在本機的 Program Files 目錄下建立本機磁碟機 P:︰</span><span class="sxs-lookup"><span data-stu-id="2bc4a-140">The following command creates a local drive P: rooted in the local Program Files directory:</span></span>

```powershell
subst p: $env:programfiles
```

<span data-ttu-id="2bc4a-141">就像使用網路磁碟機，Windows PowerShell 殼層可以立即看到使用 **subst** 在 Windows PowerShell 內對應的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-141">Just as with network drives, drives mapped within Windows PowerShell using **subst** are immediately visible to the Windows PowerShell shell.</span></span>

### <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="2bc4a-142">將文字檔讀入陣列</span><span class="sxs-lookup"><span data-stu-id="2bc4a-142">Reading a Text File into an Array</span></span>

<span data-ttu-id="2bc4a-143">文字資料最常見的儲存體格式之一，是將檔案中分隔的各行視為不同的資料元素。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-143">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="2bc4a-144">**Get-Content** Cmdlet 可以用一個步驟讀取整個檔案，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="2bc4a-144">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

<span data-ttu-id="2bc4a-145">**Get-Content** 已經將從檔案讀取的資料視為陣列，檔案內容為每行一個元素。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-145">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="2bc4a-146">您可以藉由檢查只要核取傳回內容的 **長度** 即可確認︰</span><span class="sxs-lookup"><span data-stu-id="2bc4a-146">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="2bc4a-147">這個命令在將資訊清單直接放入 Windows PowerShell 非常有用。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-147">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="2bc4a-148">例如，您可能會在檔案 C:\\temp\\domainMembers.txt 中儲存電腦名稱或 IP 位址的清單，一行一個名稱。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-148">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="2bc4a-149">您可以使用 **Get-Content** 擷取檔案內容並將內容放入變數 **$Computers**：</span><span class="sxs-lookup"><span data-stu-id="2bc4a-149">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="2bc4a-150">**$Computers** 現在是每個元素包含一個電腦名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="2bc4a-150">**$Computers** is now an array containing a computer name in each element.</span></span>
