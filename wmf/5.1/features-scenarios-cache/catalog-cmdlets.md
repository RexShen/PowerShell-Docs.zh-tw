
---
標題︰類別目錄 Cmdlet 作者︰jaimeo 參與者︰？
---
# 類別目錄 Cmdlet  

[Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) 模組中新增了兩個新的 Cmdlet，以產生和驗證 Windows 類別目錄檔案。  

New-FileCatalog 
--------------------------------

[新的檔案] 類別目錄會建立 Windows 類別目錄檔案，供資料夾和檔案集合使用。 類別目錄檔案包含指定路徑中的所有檔案雜湊。 使用者可以散發資料夾集合以及代表這些資料夾的對應類別目錄檔案。 內容接收者可以用它來驗證資料夾在類別目錄建立後是否有任何變更。    

```PowerShell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
我們支援建立類別目錄第 1 版和第 2 版。 第 1 版使用 SHA1 雜湊演算法建立檔案雜湊，第 2 版使用 SHA256。 *Windows Server 2008 R2* 和 *Windows 7* 不支援第 2 版的類別目錄。 如果使用 *Windows 8*、*Windows Server 2012* 和更新版本的平台，建議使用第 2 版的類別目錄。  

![](../../images/NewFileCatalog.jpg)

這會建立類別目錄檔案。 

![](../../images/CatalogFile1.jpg)  

![](../../images/CatalogFile2.jpg) 

若要驗證類別目錄檔案 (上例中為 Pester.cat) 的完整性，應使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) Cmdlet 來加以簽署。   


Test-FileCatalog 
--------------------------------

[測試檔案] 類別目錄會驗證代表資料夾集合的類別目錄。 

```PowerShell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../../images/TestFileCatalog.jpg)

此 Cmdlet 會比較所有的檔案雜湊及在 *catalog* 和 *disk* 中找到的相對路徑。 如果檔案雜湊和路徑中偵測到任何不相符的項目，狀態就會顯示 *ValidationFailed*。 使用者可以使用 *-Detailed* 旗標擷取此資訊的完整內容。 它也會在歸檔的 *Signature* 中顯示類別目錄的簽署狀態，和呼叫 [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) Cmdlet 一樣。 使用者也可以使用 *-FilesToSkip* 參數，在驗證期間略過任何檔案。 



<!--HONumber=Jul16_HO3-->


