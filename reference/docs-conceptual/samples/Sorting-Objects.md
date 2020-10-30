---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 排序物件
description: Sort-Object Cmdlet 可讓您在一或多個屬性上排序物件的集合。
ms.openlocfilehash: 836207adfc566003e9714e45920d9b4e24a677e9
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501009"
---
# <a name="sorting-objects"></a><span data-ttu-id="06f94-104">排序物件</span><span class="sxs-lookup"><span data-stu-id="06f94-104">Sorting Objects</span></span>

<span data-ttu-id="06f94-105">我們會組織顯示的資料，讓您可以使用 `Sort-Object` Cmdlet 更輕鬆地進行掃描。</span><span class="sxs-lookup"><span data-stu-id="06f94-105">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="06f94-106">`Sort-Object` 會使用一或多個屬性的名稱作為排序依據，並傳回根據這些屬性值進行排序的資料。</span><span class="sxs-lookup"><span data-stu-id="06f94-106">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="06f94-107">基本排序</span><span class="sxs-lookup"><span data-stu-id="06f94-107">Basic sorting</span></span>

<span data-ttu-id="06f94-108">考量在目前目錄中列出子目錄和檔案的問題。</span><span class="sxs-lookup"><span data-stu-id="06f94-108">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="06f94-109">如果我們要依序根據 **LastWriteTime** 和 **Name** 進行排序，方式是輸入：</span><span class="sxs-lookup"><span data-stu-id="06f94-109">If we want to sort by **LastWriteTime** and then by **Name** , we can do it by typing:</span></span>

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

<span data-ttu-id="06f94-110">您也可以指定 **Descending** 切換參數，以相反順序來排序物件。</span><span class="sxs-lookup"><span data-stu-id="06f94-110">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

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

## <a name="using-hash-tables"></a><span data-ttu-id="06f94-111">使用雜湊表</span><span class="sxs-lookup"><span data-stu-id="06f94-111">Using hash tables</span></span>

<span data-ttu-id="06f94-112">您可以在陣列中使用雜湊表來以不同的順序排序不同的屬性。</span><span class="sxs-lookup"><span data-stu-id="06f94-112">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="06f94-113">每個雜湊表都會使用 **Expression** 索引鍵來指定屬性名稱與 **Ascending** 或 **Descending** 索引鍵，以依據 `$true` 或 `$false` 指定排序順序。</span><span class="sxs-lookup"><span data-stu-id="06f94-113">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="06f94-114">**Expression** 索引鍵為強制項目。</span><span class="sxs-lookup"><span data-stu-id="06f94-114">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="06f94-115">**Ascending** 或 **Descending** 索引鍵是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="06f94-115">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="06f94-116">下列範例會以遞減的 **LastWriteTime** 順序和遞增的 **Name** 順序排序物件。</span><span class="sxs-lookup"><span data-stu-id="06f94-116">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

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

<span data-ttu-id="06f94-117">您也可以對 **Expression** 索引鍵設定 scriptblock。</span><span class="sxs-lookup"><span data-stu-id="06f94-117">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="06f94-118">執行 `Sort-Object` Cmdlet 時，scriptblock 會執行，而且會將結果用於排序。</span><span class="sxs-lookup"><span data-stu-id="06f94-118">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="06f94-119">以下範例會依據 **CreationTime** 和 **LastWriteTime** 之間的時間範圍，以遞減順序排序物件。</span><span class="sxs-lookup"><span data-stu-id="06f94-119">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime** .</span></span>

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

## <a name="tips"></a><span data-ttu-id="06f94-120">提示</span><span class="sxs-lookup"><span data-stu-id="06f94-120">Tips</span></span>

<span data-ttu-id="06f94-121">您可以如下所示省略 **Property** 參數名稱：</span><span class="sxs-lookup"><span data-stu-id="06f94-121">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="06f94-122">此外，您也可以使用 `Sort-Object` 的內建別名 `sort` 來參考它：</span><span class="sxs-lookup"><span data-stu-id="06f94-122">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="06f94-123">雜湊表中的索引鍵可縮寫以用於排序，如下所示：</span><span class="sxs-lookup"><span data-stu-id="06f94-123">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="06f94-124">在這個範例中， **e** 代表 **Expression** 、 **d** 代表 **Descending** ，而 **a** 代表 **Ascending** 。</span><span class="sxs-lookup"><span data-stu-id="06f94-124">In this example, the **e** stands for **Expression** , the **d** stands for **Descending** , and the **a** stands for **Ascending** .</span></span>

<span data-ttu-id="06f94-125">為提升可讀性，您可以將雜湊表放入個別的變數中：</span><span class="sxs-lookup"><span data-stu-id="06f94-125">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
