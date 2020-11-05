---
ms.date: 06/12/2017
title: 組件庫搜尋語法
description: 此文章描述用來搜尋 PowerShell 資源庫內容的使用者介面。
ms.openlocfilehash: 7ad486095647f99056b37c2ca1a50db099a166c0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661365"
---
# <a name="gallery-search-syntax"></a>組件庫搜尋語法

您可以使用 [PowerShell 資源庫的網站](https://www.powershellgallery.com/) \(英文\) 來搜尋 PowerShell 資源庫。 PowerShell 資源庫網站提供文字搜尋方塊，讓您可以使用字組、片語和關鍵字運算式來縮小搜尋結果範圍。

## <a name="search-by-keywords"></a>依關鍵字搜尋

```Syntax
dsc azure sql
```

搜尋會嘗試尋找包含所有 3 個關鍵字的相關文件，並傳回相符文件。

## <a name="search-using-phrases-and-keywords"></a>使用片語和關鍵字搜尋

```Syntax
"azure sql" deployment
```

輸入加上引號 ("") 的片語，會變更搜尋以尋找特定片語，而非個別關鍵字。 相符文件通常應該會包含精確片語 "azure sql" (包含大寫變化，例如"Azure SQL")，通常也會包含 'deployment' 這個字。

## <a name="filtering-on-fields"></a>根據欄位進行篩選

您可以搜尋特定套件識別碼 (或者 'Id' 或 'id')，或在搜尋詞彙前面加上欄位名稱來搜尋特定其他欄位。

可搜尋的欄位目前是 'Id'、'Version'、'Tags'、'Author'、'Owner'、'Functions'、'Cmdlets'、'DscResources' 和 'PowerShellVersion'。

- 識別碼是您在主控台中使用的名稱。
- 標題是搜尋結果中套件頁面頂端所顯示的內容。

## <a name="examples"></a>範例

```Syntax
ID:PSReadline
```

尋找識別碼包含 "PSReadline" 的套件。

```Syntax
Id:"AzureRM.Profile"
```

是尋找 [識別碼] 欄位中有 "AzureRM.Profile" 之套件的另一種方式。

'Id' 篩選是子字串比對，因此，如果您搜尋下列項目︰

```Syntax
Id:"azure"
```

這會提供包含 'AzureRM.Profile' 和 'Azure.Storage' 的結果。

您也可以在單一欄位中搜尋多個關鍵字。

```Syntax
id:azure tags:intellisense
```

而且，您可以使用雙引號來執行片語搜尋：

```Syntax
id:"azure.storage"
```

使用 DSC 標記搜尋所有套件。

```Syntax
Tags:DSC
```

使用指定的函數搜尋所有套件。

```Syntax
Functions:Get-TreeSize
```

使用指定的 Cmdlet 搜尋所有套件。

```Syntax
Cmdlets:Get-AzureRmEnvironment
```

使用指定的「DSC 資源」名稱搜尋所有套件。

```Syntax
DscResources:xArchive
```

使用指定的 PowerShellVersion 搜尋所有套件

```Syntax
PowerShellVersion:2.0
```

最後，如果您使用不支援的欄位 (例如 'commands')，則只會略過它，並搜尋所有欄位。 因此，下列查詢

```Syntax
commands:blobs storage
```

會解譯成與這個查詢完全相同︰

```Syntax
blobs storage
```
