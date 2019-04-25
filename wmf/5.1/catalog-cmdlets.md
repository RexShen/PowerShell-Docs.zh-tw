---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
title: 類別目錄 Cmdlet
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057609"
---
# <a name="catalog-cmdlets"></a>類別目錄 Cmdlet

[Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) 模組中新增了兩個新的 Cmdlet，以產生和驗證 Windows 類別目錄檔案。

## <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

`New-FileCatalog` 會為一組資料夾及檔案建立 Windows 類別目錄檔案。 類別目錄檔案包含指定路徑中所有檔案的雜湊。 使用者在散發資料夾組時，可以一併散發代表這些資料夾的對應類別目錄檔案。 內容接收者可以利用類別目錄檔案，驗證資料夾自類別目錄建立之後有無任何變更。

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
我們支援建立類別目錄第 1 版和第 2 版。 第 1 版使用 SHA1 雜湊演算法建立檔案雜湊，第 2 版使用 SHA256。 *Windows Server 2008 R2* 和 *Windows 7* 不支援第 2 版的類別目錄。 如果使用 *Windows 8*、*Windows Server 2012* 和更新版本的平台，建議使用第 2 版的類別目錄。

若要在現有的模組使用此命令，請指定 CatalogFilePath 和 Path 變數，以符合模組資訊清單的位置。 下列範例中，模組資訊清單位於 C:\Program Files\Windows PowerShell\Modules\Pester。

![](../images/NewFileCatalog.jpg)

這會建立類別目錄檔案。

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

為能確認類別目錄檔案 (在上例中為 Pester.cat) 的完整性，應使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) Cmdlet 簽署該檔案。


## <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

`Test-FileCatalog` 會驗證代表資料夾組的類別目錄。

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

此 Cmdlet 會將所有檔案及在類別目錄檔案中找到和其相關之路徑的雜湊，與磁碟上儲存的雜湊進行比較。 若在檔案雜湊與路徑之間偵測到任何不相符，其會傳回狀態 `ValidationFailed`。
使用者可以使用 `Detailed` 參數擷取所有此資訊。 和對類別目錄檔案類別目錄呼叫 [Get-authenticodesignature](https://technet.microsoft.com/library/hh849805.aspx) Cmdlet 一樣，類別目錄的簽署狀態也會顯示在 `Signature` 欄位中。
使用者也可使用 `FilesToSkip` 參數，在驗證期間跳過任何檔案。
