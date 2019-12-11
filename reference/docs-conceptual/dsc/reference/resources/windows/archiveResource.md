---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC 封存資源
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954765"
---
# <a name="dsc-archive-resource"></a>DSC 封存資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的封存資源會提供一個機制，將封存 (.zip) 檔案解壓縮在特定路徑。

## <a name="syntax"></a>語法

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Properties

|屬性 |描述 |
|---|---|
|Destination |指定您想要確保的封存內容解壓縮位置。 |
|路徑 |指定封存檔案的來源路徑。 |
|總和檢查碼 |定義判斷兩個檔案是否相同時所使用的類型。 如不指定 **Checksum**，只會使用檔案或目錄名稱進行比較。 有效值包括：**SHA-1**、**SHA-256**、**SHA-512**、**createdDate**、**modifiedDate**。 如果指定 **Checksum** 但無 **Validate**，設定會失敗。 |
|Force |某些檔案作業 (例如覆寫檔案，或刪除不是空的目錄) 會導致錯誤。 使用 **Force** 屬性會覆寫此類錯誤。 預設值為 **False**。 |
|驗證| 使用 **Checksum** 屬性判斷封存是否符合簽章。 如果指定 **Checksum** 但無 **Validate**，設定會失敗。 如果指定 **Validate** 但無 **Checksum**，則預設會使用 _SHA-256_ **Checksum**。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |當**目的地**有封存內容時，決定是否要檢查。 請將這個屬性設為 **Present** 以確保有內容。 設為 **Absent** 以確保它們不存在。 預設值為 **Present**。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

## <a name="example"></a>範例

下列範例示範如何使用封存資源以確保 `Test.zip` 封存檔案的內容存在，並會解壓縮在指定的目的地。

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```