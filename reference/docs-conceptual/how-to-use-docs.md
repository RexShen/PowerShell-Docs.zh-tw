---
ms.date: 09/25/2019
keywords: powershell,cmdlet
title: 如何使用 PowerShell 文件
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281644"
---
# <a name="how-to-use-the-powershell-documentation"></a>如何使用 PowerShell 文件

歡迎使用 PowerShell 線上文件。 此網站包含適用於下列 PowerShell 版本的 Cmdlet 參考：

- PowerShell 7 (預覽)
- PowerShell 6
- PowerShell 5.1
- PowerShell 5.0
- PowerShell 4.0
- PowerShell 3.0

## <a name="selecting-your-version"></a>選取您的版本

根據預設，此網站會顯示最新發行版本的 PowerShell 文件。 某些 Cmdlet 在各種 PowerShell 版本中的運作方式不同。 請確定您檢視您所使用 PowerShell 版本的文件。

使用頁面頂端的版本選擇器，選取您想要的 PowerShell 版本。

![版本選擇器](images/how-to-use-docs/picker-vall.gif)

您可以透過檢查 `$PSversionTable.PSVersion` 值來檢查您使用的 PowerShell 版本。 下列範例顯示 Windows PowerShell v5.1 的輸出。

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a>搜尋文章

有兩種方式可搜尋文件中的內容。最簡單方式是使用版本選擇器下方的 [篩選] 方塊。 只要輸入出現在文章標題中的字組即可。 此頁面會顯示相符的文章清單。 您也可以選取從該清單中搜尋整個網站的選項。

![篩選方塊](images/how-to-use-docs/filter-search.gif)
