---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 排序物件
ms.openlocfilehash: ed78e7e333f3468781c9cd96df2194fbdfebe753
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030779"
---
# <a name="sorting-objects"></a>排序物件

我們會組織顯示的資料，讓您可以使用 `Sort-Object` Cmdlet 更輕鬆地進行掃描。 `Sort-Object` 會使用一或多個屬性的名稱作為排序依據，並傳回根據這些屬性值進行排序的資料。

## <a name="basic-sorting"></a>基本排序

考量在目前目錄中列出子目錄和檔案的問題。
如果我們要依序根據 **LastWriteTime** 和 **Name** 進行排序，方式是輸入：

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

您也可以指定 **Descending** 切換參數，以相反順序來排序物件。

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

## <a name="using-hash-tables"></a>使用雜湊表

您可以在陣列中使用雜湊表來以不同的順序排序不同的屬性。
每個雜湊表都會使用 **Expression** 索引鍵來指定屬性名稱與 **Ascending** 或 **Descending** 索引鍵，以依據 `$true` 或 `$false` 指定排序順序。
**Expression** 索引鍵為強制項目。
**Ascending** 或 **Descending** 索引鍵是選擇性的。

下列範例會以遞減的 **LastWriteTime** 順序和遞增的 **Name** 順序排序物件。

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

您也可以對 **Expression** 索引鍵設定 scriptblock。
執行 `Sort-Object` Cmdlet 時，scriptblock 會執行，而且會將結果用於排序。

以下範例會依據 **CreationTime** 和 **LastWriteTime** 之間的時間範圍，以遞減順序排序物件。

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

您可以如下所示省略 **Property** 參數名稱：

```powershell
Sort-Object LastWriteTime, Name
```

此外，您也可以使用 `Sort-Object` 的內建別名 `sort` 來參考它：

```powershell
sort LastWriteTime, Name
```

雜湊表中的索引鍵可縮寫以用於排序，如下所示：

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

在這個範例中，**e** 代表 **Expression**、**d** 代表 **Descending**，而 **a** 代表 **Ascending**。

為提升可讀性，您可以將雜湊表放入個別的變數中：

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
