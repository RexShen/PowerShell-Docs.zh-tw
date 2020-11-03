---
description: 描述如何在 PowerShell 中使用萬用字元。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 4778de5022f35f354e7783cedc5019198d11604b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208267"
---
# <a name="about-wildcards"></a>關於萬用字元

## <a name="short-description"></a>簡短描述

描述如何在 PowerShell 中使用萬用字元。

## <a name="long-description"></a>詳細描述

萬用字元代表一或多個字元。 您可以使用它們，在命令中建立單字模式。 例如，若要取得具有副檔名的目錄中的所有檔案 `C:\Techdocs` `.ppt` ，請輸入：

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

在此情況下，星號 (`*`) 萬用字元表示在副檔名之前出現的任何字元 `.ppt` 。

PowerShell 支援下列萬用字元：

|萬用字元|描述               |範例 |相符項目        |無相符|
|--------|--------------------------|--------|-------------|--------|
|\*      |符合零或多個字元 | 的\*  | aA、ag、Apple | 香蕉 |
|?       |符合該位置中的一個字元 | ？ n | a、in、on | 跑 |
|\[ \]   |符合字元範圍 | \[a-l \] ook | 著作、庫、尋找 | 接管 |
|\[ \]   |符合特定字元 | \[bc \] ook | 書籍，庫 | 鉤 |

您可以在相同的字組模式中包含多個萬用字元。 例如，若要尋找名稱開頭為字母 **a** 到 **l** 的文字檔，請輸入：

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

許多 Cmdlet 接受參數值中的萬用字元。 每個 Cmdlet 的說明主題會說明哪些參數接受萬用字元。 對於接受萬用字元的參數，其用法不區分大小寫。

您可以在命令和腳本區塊中使用萬用字元，例如，建立代表屬性值的文字模式。 例如，下列命令會取得 **ServiceType** 屬性值包含 **互動式** 的服務。

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

在下列範例中， `If` 語句包含使用萬用字元來尋找屬性值的條件。 如果還原點的 **描述** 包含 **PowerShell** ，此命令會將還原點的 **CreationTime** 屬性值新增至記錄檔。

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a>另請參閱

[about_Language_Keywords](about_Language_Keywords.md)

[about_If](about_If.md)

[about_Script_Blocks](about_Script_Blocks.md)

