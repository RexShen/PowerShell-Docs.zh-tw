---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 針對多個物件重複工作 ForEach Object
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 64d85edad4a6931b2376b95b6d1f5b4d5194399f
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587256"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="04e05-103">針對多個物件重複工作 (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="04e05-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="04e05-104">**ForEach-Object** Cmdlet 針對目前的管線物件使用指令碼區塊和 `$_` 描述元，讓您能夠在管線中的每個物件上執行命令。</span><span class="sxs-lookup"><span data-stu-id="04e05-104">The **ForEach-Object** cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="04e05-105">這可以用來執行一些複雜的工作。</span><span class="sxs-lookup"><span data-stu-id="04e05-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="04e05-106">一個可能適用的情況是操控資料，使其更加實用。</span><span class="sxs-lookup"><span data-stu-id="04e05-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="04e05-107">例如，您可以使用 WMI 中的 Win32_LogicalDisk 類別，傳回每個本機磁碟的可用空間資訊。</span><span class="sxs-lookup"><span data-stu-id="04e05-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="04e05-108">傳回的資料是以位元組為單位，不過這會很難閱讀︰</span><span class="sxs-lookup"><span data-stu-id="04e05-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="04e05-109">我們可以將 FreeSpace 值轉換成 MB，方法是將每個值除以 1024 兩次；第一次相除之後，資料會以 KB 為單位，第二次相除之後，資料會以 MB 為單位。</span><span class="sxs-lookup"><span data-stu-id="04e05-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="04e05-110">您可以輸入下列命令，在 ForEach-Object 指令碼區塊中執行這項操作︰</span><span class="sxs-lookup"><span data-stu-id="04e05-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="04e05-111">不過，輸出現在會是沒有相關聯標籤的資料。</span><span class="sxs-lookup"><span data-stu-id="04e05-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="04e05-112">因為這類 WMI 屬性是唯讀的，所以您無法直接轉換 FreeSpace。</span><span class="sxs-lookup"><span data-stu-id="04e05-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="04e05-113">如果您輸入︰</span><span class="sxs-lookup"><span data-stu-id="04e05-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="04e05-114">您會收到錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="04e05-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="04e05-115">您可以使用一些進階技術來重新組織資料，但更簡單的方法是使用 **Select-Object** 建立新的物件。</span><span class="sxs-lookup"><span data-stu-id="04e05-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>