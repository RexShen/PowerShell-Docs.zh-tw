---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxArchive 資源
ms.openlocfilehash: 56f8df65945f16a93c69407ea30f51878a201b63
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560911"
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC for Linux nxArchive 資源

PowerShell 預期狀態設定 (DSC) 的 **nxArchive** 資源會提供一個機制，將封存 (.tar、.zip) 檔案解壓縮在 Linux 節點上的特定路徑。

## <a name="syntax"></a>語法

```Syntax
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|SourcePath |指定封存檔案的來源路徑。 這應該是 .tar、.zip 或 .tar.gz 檔案。 |
|DestinationPath |指定您想要確保的封存內容解壓縮位置。 |
|總和檢查碼 |定義判斷是否已更新來源封存檔時所使用的類型。 值為：**ctime**、**mtime** 或 **md5**。 預設值為 **md5**。 |
|Force |某些檔案作業 (例如覆寫檔案，或刪除不是空的目錄) 會導致錯誤。 使用 **Force** 屬性會覆寫此類錯誤。 預設值是 `$false`。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |當**目的地**有封存內容時，決定是否要檢查。 請將這個屬性設為 **Present** 以確保有內容。 設為 **Absent** 以確保它們不存在。 預設值為 **Present**。 |

## <a name="example"></a>範例

下列範例示範如何使用 **nxArchive** 資源以確保 `website.tar` 封存檔案的內容存在，並會解壓縮在指定的目的地。

```powershell
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = "http://release.contoso.com/releases/website.tar"
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = "mtime"
}

nxArchive SyncWebDir
{
   SourcePath = "/usr/release/staging/website.tar"
   DestinationPath = "/usr/local/apache2/htdocs/"
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```
