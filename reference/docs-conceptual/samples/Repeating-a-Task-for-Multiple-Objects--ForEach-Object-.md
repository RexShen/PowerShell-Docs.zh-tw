---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 針對多個物件重複工作 ForEach Object
description: ForEach-Object 可讓您針對每個透過管線傳遞的物件重複執行一組命令。
ms.openlocfilehash: 7353be833dc8bf77dd18b7fc45bdd97e092ff6ef
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499950"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="a57b7-104">針對多個物件重複工作 (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="a57b7-104">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="a57b7-105">`ForEach-Object`Cmdlet 可針對目前的管線物件使用指令碼區塊和 `$_` 描述元，讓您能夠在管線中的每個物件上執行命令。</span><span class="sxs-lookup"><span data-stu-id="a57b7-105">The `ForEach-Object` cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="a57b7-106">這可以用來執行一些複雜的工作。</span><span class="sxs-lookup"><span data-stu-id="a57b7-106">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="a57b7-107">一個可能適用的情況是操控資料，使其更加實用。</span><span class="sxs-lookup"><span data-stu-id="a57b7-107">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="a57b7-108">例如，您可以使用 WMI 中的 **Win32_LogicalDisk** 類別來傳回每個本機磁碟的可用空間資訊。</span><span class="sxs-lookup"><span data-stu-id="a57b7-108">For example, the **Win32_LogicalDisk** class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="a57b7-109">傳回的資料是以位元組為單位，不過這會很難閱讀︰</span><span class="sxs-lookup"><span data-stu-id="a57b7-109">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

<span data-ttu-id="a57b7-110">我們可以將 **FreeSpace** 值轉換成 MB，方法是將每個值除以 1 MB。</span><span class="sxs-lookup"><span data-stu-id="a57b7-110">We can convert the **FreeSpace** value to megabytes by dividing each value by 1MB.</span></span> <span data-ttu-id="a57b7-111">您可以輸入下列命令，在 `ForEach-Object` 指令碼區塊中執行這項操作︰</span><span class="sxs-lookup"><span data-stu-id="a57b7-111">You can do that in a `ForEach-Object` script block by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

<span data-ttu-id="a57b7-112">不過，輸出現在會是沒有相關聯標籤的資料。</span><span class="sxs-lookup"><span data-stu-id="a57b7-112">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="a57b7-113">因為此類 WMI 屬性是唯讀的，所以您無法直接轉換 **FreeSpace** 。</span><span class="sxs-lookup"><span data-stu-id="a57b7-113">Because WMI properties such as this are read-only, you cannot directly convert **FreeSpace** .</span></span> <span data-ttu-id="a57b7-114">如果您輸入︰</span><span class="sxs-lookup"><span data-stu-id="a57b7-114">If you type this:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

<span data-ttu-id="a57b7-115">您會收到錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="a57b7-115">You get an error message:</span></span>

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

<span data-ttu-id="a57b7-116">您可以使用一些進階技術來重新組織資料，但有一個較簡單的方法，就是使用 `Select-Object` 來建立新物件。</span><span class="sxs-lookup"><span data-stu-id="a57b7-116">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using `Select-Object`.</span></span>
