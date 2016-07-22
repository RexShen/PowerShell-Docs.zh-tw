---
title: "WMF 5.1 (預覽) 的新案例和功能"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 01d7ac9815a8650f36150e36b4f6942f451dc368

---

# WMF 5.1 (預覽) 的新案例和功能 #

> 注意：本資訊尚屬初始版本，後續有可能變更。

## PowerShell 版本 ##
從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。

- **Desktop Edition︰**建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行之 PowerShell 版本的指令碼和模組相容。
- **Core Edition︰**建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行之 PowerShell 版本的指令碼和模組相容。

**深入了解使用 PowerShell 版本**
- [判斷執行的 PowerShell 版本]()
- [宣告特定 PowerShell 版本的模組相容性]()
- [依據 CompatiblePSEditions 篩選 Get-Module 結果]()
- [只有在相容的 PowerShell 版本上執行才會執行指令碼]()

## 類別目錄 Cmdlet  

[Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) 模組中新增了兩個新的 Cmdlet，它們會產生和驗證 Windows 類別目錄檔案。  

###New-FileCatalog 
--------------------------------

[新的檔案] 類別目錄會建立 Windows 類別目錄檔案，供資料夾和檔案集合使用。 此類別目錄檔案包含指定路徑中的所有檔案雜湊。 使用者可以散發資料夾集合以及代表這些資料夾的對應類別目錄檔案。 這項資訊對驗證資料夾在類別目錄建立後是否有任何變更，非常有用。    

```PowerShell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
支援類別目錄第 1 版和第 2 版。 第 1 版使用 SHA1 雜湊演算法建立檔案雜湊，第 2 版使用 SHA256。 *Windows Server 2008 R2* 或 *Windows 7* 不支援第 2 版的類別目錄。 *Windows 8*、*Windows Server 2012* 和更新版本的作業系統，應該使用類別目錄第 2 版。  

![](../../images/NewFileCatalog.jpg)

這會建立類別目錄檔案。 

![](../../images/CatalogFile1.jpg)  

![](../../images/CatalogFile2.jpg) 

若要驗證類別目錄檔案 (上例中為 Pester.cat) 的完整性，請使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) Cmdlet 來加以簽署。   


###Test-FileCatalog 
--------------------------------

[測試檔案] 類別目錄會驗證代表資料夾集合的類別目錄。 

```PowerShell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../../images/TestFileCatalog.jpg)

此 Cmdlet 會比較所有的檔案雜湊及在 *catalog* 和 *disk* 中找到的相對路徑。 如果檔案雜湊和路徑中偵測到任何不相符的項目，就會傳回 *ValidationFailed* 狀態。 使用者可以使用 *-Detailed* 旗標來擷取此資訊的完整內容。 它也會在歸檔的 *Signature* 中顯示類別目錄的簽署狀態，和呼叫 [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) Cmdlet 一模一樣。 使用者也可以使用 *-FilesToSkip* 參數，在驗證期間略過任何檔案。 


## 模組分析快取 ##
從 WMF 5.1 開始，PowerShell 可以控制快取模組資料所用的檔案，例如匯出的命令。

此快取預設儲存在 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 檔案中。
快取一般在啟動同時搜尋命令時讀取，並在模組匯入一段時間後寫入背景執行緒。

若要變更快取的預設位置，請先設定環境變數 PSModuleAnalysisCachePath 再啟動 PowerShell。 此環境變數的變更只會影響子處理程序。
該值應該命名 PowerShell 有權建立和寫入檔案的完整路徑 (包括檔名)。
若要停用檔案快取，請將此值設定於無效的位置，例如︰

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

這會將路徑設定到無效的裝置。 如果 PowerShell 無法寫入該路徑，就不會傳回任何錯誤，但您可以透過追蹤查看錯誤報告︰

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

寫出快取時，PowerShell 會檢查確認模組已不存在，避免不必要的大型快取。
有時候不需要這些檢查，在此情況下，您可以透過設定下列項目關閉這些檢查：

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

此環境變數設定會立即在目前的程序中生效。

##指定模組版本

在 WMF 5.1 中，`using module` 與 PowerShell 中其他模組相關的語法結構表現一致。 以往，您無法指定特定的模組版本；如果有多個版本存在，這會導致錯誤。


在 WMF 5.1 中：

* 您可以使用 `ModuleSpecification` [雜湊表](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx)。 此雜湊表與 `Get-Module -FullyQualifiedName` 有相同的格式。

**範例：** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* 如果模組有多個版本，PowerShell 會使用與 `Import-Module` **相同的解析邏輯**，不傳回錯誤，和 `Import-Module` 及 `Import-DscResource` 的行為一樣。








##Pester 的改善
在 WMF 5.1 中，PowerShell 隨附的 Pester 版本已從 3.3.5 更新至 3.4.0，加上認可 https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e，讓 Pester 在 Nano 上有更好的表現。 

您可以檢查 https://github.com/pester/Pester/blob/master/CHANGELOG.md 的 ChangeLog.md 檔案，檢閱 3.3.5 版至 3.4.0 版的變更。



<!--HONumber=Jul16_HO3-->


