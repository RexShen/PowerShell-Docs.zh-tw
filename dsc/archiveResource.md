---
title: "DSC 封存資源"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 1d4d2d9106ef76d6628f93cf86234807dbb121ed

---

# DSC 封存資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的封存資源會提供一個機制，將封存 (.zip) 檔案解壓縮在特定路徑。

## 語法 
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## [內容]

|  屬性  |  描述   | 
|---|---| 
| Destination| 指定您想要確保的封存內容解壓縮位置。| 
| 路徑| 指定封存檔案的來源路徑。| 
| __總和檢查碼__| 定義判斷兩個檔案是否相同時所使用的類型。 如不指定 __Checksum__，只會使用檔案或目錄名稱進行比較。 有效值包括：SHA-1、SHA-256、SHA-512、createdDate、modifiedDate、none (預設值)。 如果指定 __Checksum__ 但無 __Validate__，設定會失敗。| 
| Ensure| 當__目的地__有封存內容時，決定是否要檢查。 請將這個屬性設為 __Present__ 以確保有內容。 設為 __Absent__ 以確保它們不存在。 預設值為 __Present__。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 ResourceName，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 
| 驗證| 使用 Checksum 屬性判斷封存是否符合簽章。 如果指定 Checksum 但無 Validate，設定會失敗。 如果指定 Validate 但無 Checksum，預設使用 SHA-256 總和檢查碼。| 
| Force| 某些檔案作業 (例如覆寫檔案，或刪除不是空的目錄) 會導致錯誤。 使用 Force 屬性會覆寫此類錯誤。 預設值為 False。| 

## 範例

下列範例示範如何使用封存資源以確保 Test.zip 封存檔案的內容存在，並會解壓縮在指定的目的地。

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
} 
```




<!--HONumber=Jun16_HO4-->


