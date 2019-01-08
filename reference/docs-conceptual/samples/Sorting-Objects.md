---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 排序物件
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400634"
---
# <a name="sorting-objects"></a><span data-ttu-id="ff8d1-103">排序物件</span><span class="sxs-lookup"><span data-stu-id="ff8d1-103">Sorting Objects</span></span>

<span data-ttu-id="ff8d1-104">我們會組織顯示的資料，讓您更輕鬆地使用掃描`Sort-Object`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ff8d1-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="ff8d1-105">`Sort-Object` 會據以排序的一或多個屬性的名稱，並傳回這些屬性的值來排序的資料。</span><span class="sxs-lookup"><span data-stu-id="ff8d1-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="ff8d1-106">基本的排序</span><span class="sxs-lookup"><span data-stu-id="ff8d1-106">Basic sorting</span></span>

<span data-ttu-id="ff8d1-107">請考慮列出目前的目錄中子目錄和檔案的問題。</span><span class="sxs-lookup"><span data-stu-id="ff8d1-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="ff8d1-108">如果我們想要依排序**LastWriteTime**再依**名稱**，我們可以將則做法是輸入：</span><span class="sxs-lookup"><span data-stu-id="ff8d1-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

<span data-ttu-id="ff8d1-109">您也可以排序物件以反向順序藉由指定**遞減**切換參數。</span><span class="sxs-lookup"><span data-stu-id="ff8d1-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a><span data-ttu-id="ff8d1-110">使用雜湊資料表</span><span class="sxs-lookup"><span data-stu-id="ff8d1-110">Using hash tables</span></span>

<span data-ttu-id="ff8d1-111">您可以使用雜湊表陣列中排序以不同的順序不同的屬性。</span><span class="sxs-lookup"><span data-stu-id="ff8d1-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="ff8d1-112">每個雜湊表會使用**運算式**指定為字串的屬性名稱的索引鍵和**Ascending**或**遞減**索引鍵來指定排序次序所`$true`或`$false`.</span><span class="sxs-lookup"><span data-stu-id="ff8d1-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="ff8d1-113">**運算式**是必要的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ff8d1-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="ff8d1-114">**遞增**或是**遞減**是選擇性的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ff8d1-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="ff8d1-115">下列範例會排序以遞減的物件**LastWriteTime**順序和遞增**名稱**順序。</span><span class="sxs-lookup"><span data-stu-id="ff8d1-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

<span data-ttu-id="ff8d1-116">您也可以設定指令碼區塊**運算式**索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ff8d1-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="ff8d1-117">當執行`Sort-Object`cmdlet，執行指令碼區塊，以及結果用來排序。</span><span class="sxs-lookup"><span data-stu-id="ff8d1-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="ff8d1-118">下列範例會排序以遞減順序之間的時間範圍的物件**CreationTime**並**LastWriteTime**。</span><span class="sxs-lookup"><span data-stu-id="ff8d1-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a><span data-ttu-id="ff8d1-119">提示</span><span class="sxs-lookup"><span data-stu-id="ff8d1-119">Tips</span></span>

<span data-ttu-id="ff8d1-120">您可以省略**屬性**參數名稱，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ff8d1-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="ff8d1-121">此外，您可以參考`Sort-Object`內建的別名， `sort`:</span><span class="sxs-lookup"><span data-stu-id="ff8d1-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="ff8d1-122">雜湊資料表中的索引鍵，排序可以縮寫如下所示：</span><span class="sxs-lookup"><span data-stu-id="ff8d1-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="ff8d1-123">在此範例中，**電子**代表**運算式**，則**d**代表**遞減**，而代表**遞增**。</span><span class="sxs-lookup"><span data-stu-id="ff8d1-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="ff8d1-124">若要改善可讀性，您可以將雜湊資料表放入個別的變數：</span><span class="sxs-lookup"><span data-stu-id="ff8d1-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```