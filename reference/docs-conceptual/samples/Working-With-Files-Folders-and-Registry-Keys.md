---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用檔案、資料夾與登錄機碼
ms.openlocfilehash: 0c8716c384827d0816e2847ff81232c14638681b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030752"
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="6dda8-103">使用檔案、資料夾與登錄機碼</span><span class="sxs-lookup"><span data-stu-id="6dda8-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="6dda8-104">Windows PowerShell 使用名詞 **Item** 參照在 Windows PowerShell 磁碟機上找到的項目。</span><span class="sxs-lookup"><span data-stu-id="6dda8-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="6dda8-105">使用 Windows PowerShell FileSystem 提供者時，**Item** 可能是檔案、資料夾或 Windows PowerShell 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="6dda8-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="6dda8-106">在大部分的系統管理設定中，列出及使用這些項目是很重要的基本工作，因此，我們要詳細討論這些工作。</span><span class="sxs-lookup"><span data-stu-id="6dda8-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="6dda8-107">列舉檔案、資料夾與登錄機碼 (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="6dda8-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="6dda8-108">從特定位置取得項目集合是很常見的工作，因此，**Get-ChildItem** Cmdlet 專門設計為傳回容器 (例如資料夾) 內的所有項目。</span><span class="sxs-lookup"><span data-stu-id="6dda8-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="6dda8-109">若要傳回直接包含於資料夾 C:\\Windows 內的所有檔案和資料夾，請輸入：</span><span class="sxs-lookup"><span data-stu-id="6dda8-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

<span data-ttu-id="6dda8-110">清單看起來會與您在 **Cmd.exe** 中輸入 **dir** 命令 (或在 UNIX 命令殼層中輸入 **ls** 命令) 時看到的類似。</span><span class="sxs-lookup"><span data-stu-id="6dda8-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="6dda8-111">您可以使用 **Get-ChildItem** Cmdlet 的參數執行極為複雜的清單。</span><span class="sxs-lookup"><span data-stu-id="6dda8-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="6dda8-112">我們接下來會介紹幾個案例。</span><span class="sxs-lookup"><span data-stu-id="6dda8-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="6dda8-113">您可以輸入以下命令以查看 **Get-ChildItem** Cmdlet 的語法：</span><span class="sxs-lookup"><span data-stu-id="6dda8-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="6dda8-114">這些參數可混合使用以得到高度自訂的輸出。</span><span class="sxs-lookup"><span data-stu-id="6dda8-114">These parameters can be mixed and matched to get highly customized output.</span></span>

### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="6dda8-115">列出所有包含的項目 (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="6dda8-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="6dda8-116">若要查看 Windows 資料夾內的項目和子資料夾中包含的任何項目，請使用 **Get-ChildItem** 的 **Recurse** 參數。</span><span class="sxs-lookup"><span data-stu-id="6dda8-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="6dda8-117">清單會顯示 Windows 資料夾中的所有項目和子資料夾中的項目。</span><span class="sxs-lookup"><span data-stu-id="6dda8-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="6dda8-118">例如：</span><span class="sxs-lookup"><span data-stu-id="6dda8-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a><span data-ttu-id="6dda8-119">依名稱篩選項目 (-Name)</span><span class="sxs-lookup"><span data-stu-id="6dda8-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="6dda8-120">若只要顯示項目的名稱，請使用 **Get-Childitem** 的 **Name** 參數：</span><span class="sxs-lookup"><span data-stu-id="6dda8-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="6dda8-121">強制列出隱藏的項目 (-Force)</span><span class="sxs-lookup"><span data-stu-id="6dda8-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="6dda8-122">通常在 [檔案總管] 或 Cmd.exe 中不可見的項目，則不會顯示在 **Get-ChildItem** 命令的輸出中。</span><span class="sxs-lookup"><span data-stu-id="6dda8-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="6dda8-123">若要顯示隱藏的項目，請使用 **Get-ChildItem** 的 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="6dda8-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="6dda8-124">例如：</span><span class="sxs-lookup"><span data-stu-id="6dda8-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="6dda8-125">此參數之所以名為 Force，是因為您可以強制覆寫 **Get-ChildItem** 命令的正常行為。</span><span class="sxs-lookup"><span data-stu-id="6dda8-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="6dda8-126">Force 是廣泛使用的參數，會強制執行 Cmdlet 一般不會執行的動作，但並不會執行危害系統安全性的任何動作。</span><span class="sxs-lookup"><span data-stu-id="6dda8-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="6dda8-127">使用萬用字元比對項目名稱</span><span class="sxs-lookup"><span data-stu-id="6dda8-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="6dda8-128">**Get-ChildItem** 命令可接受在要列出的項目路徑中使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6dda8-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="6dda8-129">因為萬用字元比對是由 Windows PowerShell 引擎處理，接受萬用字元的所有 Cmdlet 都會使用相同的標記法，並有相同的比對行為。</span><span class="sxs-lookup"><span data-stu-id="6dda8-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="6dda8-130">Windows PowerShell 萬用字元標記法包括：</span><span class="sxs-lookup"><span data-stu-id="6dda8-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="6dda8-131">星號 (\*) 會比對任一字元零次或更多次。</span><span class="sxs-lookup"><span data-stu-id="6dda8-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="6dda8-132">問號 (?) 會精確比對一個字元。</span><span class="sxs-lookup"><span data-stu-id="6dda8-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="6dda8-133">左中括弧 (\[) 字元與右中括弧 (]) 字元是用來夾住要比對的一組字元。</span><span class="sxs-lookup"><span data-stu-id="6dda8-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="6dda8-134">以下是萬用字元規格如何運作的一些範例。</span><span class="sxs-lookup"><span data-stu-id="6dda8-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="6dda8-135">若要在 Windows 目錄中尋找具有副檔名 **.log** 且基底名稱為剛好 5 個字元的所有檔案，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="6dda8-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

<span data-ttu-id="6dda8-136">若要在 Windows 目錄中尋找開頭是字母 **x** 的所有檔案，請輸入：</span><span class="sxs-lookup"><span data-stu-id="6dda8-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="6dda8-137">若要尋找名稱開頭是 **x** 或 **z** 的所有檔案，請輸入：</span><span class="sxs-lookup"><span data-stu-id="6dda8-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a><span data-ttu-id="6dda8-138">排除項目 (-Exclude)</span><span class="sxs-lookup"><span data-stu-id="6dda8-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="6dda8-139">您可以使用 Get-ChildItem 的 **Exclude** 參數排除特定項目。</span><span class="sxs-lookup"><span data-stu-id="6dda8-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="6dda8-140">這可讓您在單一陳述式中執行複雜的篩選。</span><span class="sxs-lookup"><span data-stu-id="6dda8-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="6dda8-141">例如，假設您嘗試在 [System32] 資料夾中尋找 Windows 時間服務 DLL，而您只記得 DLL 名稱的開頭是 "W" 且其中含有 "32"。</span><span class="sxs-lookup"><span data-stu-id="6dda8-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="6dda8-142">類似 **w\&#42;32\&#42;.dll** 的運算式會尋找滿足上述條件的所有 DLL，但也會傳回名稱中包含 "95" 或 "16" 的 Windows 95 及 16 位元的 Windows 相容 DLL。</span><span class="sxs-lookup"><span data-stu-id="6dda8-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="6dda8-143">您可以使用 **Exclude** 參數搭配模式 **\&#42;\[9516]\&#42;** ，以省略名稱中含有這些數字中之任一數字的檔案：</span><span class="sxs-lookup"><span data-stu-id="6dda8-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="6dda8-144">混合使用 Get-ChildItem 參數</span><span class="sxs-lookup"><span data-stu-id="6dda8-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="6dda8-145">您可以在同一個命令中使用 **Get-ChildItem** Cmdlet 的數個參數。</span><span class="sxs-lookup"><span data-stu-id="6dda8-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="6dda8-146">在混合使用參數之前，請確定您了解萬用字元比對的原則。</span><span class="sxs-lookup"><span data-stu-id="6dda8-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="6dda8-147">例如，下列命令不會傳回任何結果：</span><span class="sxs-lookup"><span data-stu-id="6dda8-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="6dda8-148">即使 Windows 資料夾中有兩個開頭是字母 "z" 的 DLL 也不會有任何結果。</span><span class="sxs-lookup"><span data-stu-id="6dda8-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="6dda8-149">因為我們將萬用字元指定為路徑的一部分，因此不會傳回任何結果。</span><span class="sxs-lookup"><span data-stu-id="6dda8-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="6dda8-150">即使命令是遞迴命令，**Get-ChildItem** Cmdlet 也會將項目限制為 Windows 資料夾中名稱結尾是 ".dll" 的項目。</span><span class="sxs-lookup"><span data-stu-id="6dda8-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="6dda8-151">若要為名稱符合特殊模式的檔案指定遞迴搜尋，請使用 **-Include** 參數。</span><span class="sxs-lookup"><span data-stu-id="6dda8-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```
