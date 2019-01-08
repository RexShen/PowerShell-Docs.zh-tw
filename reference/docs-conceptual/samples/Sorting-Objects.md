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
# <a name="sorting-objects"></a>排序物件

我們會組織顯示的資料，讓您更輕鬆地使用掃描`Sort-Object`cmdlet。 `Sort-Object` 會據以排序的一或多個屬性的名稱，並傳回這些屬性的值來排序的資料。

## <a name="basic-sorting"></a>基本的排序

請考慮列出目前的目錄中子目錄和檔案的問題。
如果我們想要依排序**LastWriteTime**再依**名稱**，我們可以將則做法是輸入：

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

您也可以排序物件以反向順序藉由指定**遞減**切換參數。

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

## <a name="using-hash-tables"></a>使用雜湊資料表

您可以使用雜湊表陣列中排序以不同的順序不同的屬性。
每個雜湊表會使用**運算式**指定為字串的屬性名稱的索引鍵和**Ascending**或**遞減**索引鍵來指定排序次序所`$true`或`$false`.
**運算式**是必要的索引鍵。
**遞增**或是**遞減**是選擇性的索引鍵。

下列範例會排序以遞減的物件**LastWriteTime**順序和遞增**名稱**順序。

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

您也可以設定指令碼區塊**運算式**索引鍵。
當執行`Sort-Object`cmdlet，執行指令碼區塊，以及結果用來排序。

下列範例會排序以遞減順序之間的時間範圍的物件**CreationTime**並**LastWriteTime**。

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

## <a name="tips"></a>提示

您可以省略**屬性**參數名稱，如下所示：

```powershell
Sort-Object LastWriteTime, Name
```

此外，您可以參考`Sort-Object`內建的別名， `sort`:

```powershell
sort LastWriteTime, Name
```

雜湊資料表中的索引鍵，排序可以縮寫如下所示：

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

在此範例中，**電子**代表**運算式**，則**d**代表**遞減**，而代表**遞增**。

若要改善可讀性，您可以將雜湊資料表放入個別的變數：

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```