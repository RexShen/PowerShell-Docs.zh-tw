---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 針對多個物件重複工作 ForEach Object
ms.openlocfilehash: bf89070fd9b006fa9b0b262ab63ffadd81072ecc
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736874"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="4de88-103">針對多個物件重複工作 (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="4de88-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="4de88-104">`ForEach-Object`Cmdlet 可針對目前的管線物件使用指令碼區塊和 `$_` 描述元，讓您能夠在管線中的每個物件上執行命令。</span><span class="sxs-lookup"><span data-stu-id="4de88-104">The `ForEach-Object` cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="4de88-105">這可以用來執行一些複雜的工作。</span><span class="sxs-lookup"><span data-stu-id="4de88-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="4de88-106">一個可能適用的情況是操控資料，使其更加實用。</span><span class="sxs-lookup"><span data-stu-id="4de88-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="4de88-107">例如，您可以使用 WMI 中的 **Win32_LogicalDisk** 類別來傳回每個本機磁碟的可用空間資訊。</span><span class="sxs-lookup"><span data-stu-id="4de88-107">For example, the **Win32_LogicalDisk** class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="4de88-108">傳回的資料是以位元組為單位，不過這會很難閱讀︰</span><span class="sxs-lookup"><span data-stu-id="4de88-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

<span data-ttu-id="4de88-109">我們可以將 **FreeSpace** 值轉換成 MB，方法是將每個值除以 1 MB。</span><span class="sxs-lookup"><span data-stu-id="4de88-109">We can convert the **FreeSpace** value to megabytes by dividing each value by 1MB.</span></span> <span data-ttu-id="4de88-110">您可以輸入下列命令，在 `ForEach-Object` 指令碼區塊中執行這項操作︰</span><span class="sxs-lookup"><span data-stu-id="4de88-110">You can do that in a `ForEach-Object` script block by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

<span data-ttu-id="4de88-111">不過，輸出現在會是沒有相關聯標籤的資料。</span><span class="sxs-lookup"><span data-stu-id="4de88-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="4de88-112">因為此類 WMI 屬性是唯讀的，所以您無法直接轉換 **FreeSpace**。</span><span class="sxs-lookup"><span data-stu-id="4de88-112">Because WMI properties such as this are read-only, you cannot directly convert **FreeSpace**.</span></span> <span data-ttu-id="4de88-113">如果您輸入︰</span><span class="sxs-lookup"><span data-stu-id="4de88-113">If you type this:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

<span data-ttu-id="4de88-114">您會收到錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="4de88-114">You get an error message:</span></span>

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

<span data-ttu-id="4de88-115">您可以使用一些進階技術來重新組織資料，但有一個較簡單的方法，就是使用 `Select-Object` 來建立新物件。</span><span class="sxs-lookup"><span data-stu-id="4de88-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using `Select-Object`.</span></span>
