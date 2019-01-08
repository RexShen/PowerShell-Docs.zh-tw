---
ms.date: 08/23/2018
keywords: powershell,cmdlet
title: 了解 PowerShell 管線
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: fc7c7f57bdce458185a0f5bdb8bc1fbbd81d0d61
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400644"
---
# <a name="understanding-pipelines"></a>了解管線

管線就像是一系列連接的管道區段。 沿著管線移動的項目會通過每個區段。 若要在 PowerShell 中建立管線，您可以將命令與管道運算子 "|" 連接在一起。 每個命令的輸出可作為下一個命令的輸入。

用於管線的標記法類似於其他殼層中所使用的標記法。 乍看之下，PowerShell 中的管線差異可能並不明顯。 雖然您會在畫面上看到文字，但 PowerShell 會在命令之間使用管線來傳送物件 (而非文字)。

## <a name="the-powershell-pipeline"></a>PowerShell 管線

管線可說是用於命令列介面中最重要的概念。 如果運用得當，管線會減少使用複雜命令所耗費的心力，並且能夠更輕鬆地查看命令的工作流程。 管線中的每個命令 (稱為管線元素) 會將其輸出逐項目傳遞至管線中的下一個命令。 命令不需要每次處理一個以上的項目。 結果就是減少資源耗用量，並能立即開始取得輸出。

例如，如果您使用 `Out-Host` Cmdlet 強制逐頁顯示另一個命令的輸出，則輸出看起來就像畫面上所顯示的一般文字 (分成數頁)：

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

分頁還會降低 CPU 使用率，因為處理控制權會在其已準備好要顯示的完成頁面時移轉給 `Out-Host` Cmdlet。 管線中在它前面的 Cmdlet 會暫停執行，直到輸出的下一個分頁可供使用為止。

您可以看到不同的 Windows 工作管理員監視 PowerShell 所使用的 CPU 和記憶體。 執行下列命令：`Get-ChildItem C:\Windows -Recurse`。 將 CPU 和記憶體使用量與這個命令進行比較：`Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`。

## <a name="objects-in-the-pipeline"></a>管線中的物件

當您在 PowerShell 中執行 Cmdlet 時，您會看到文字輸出，這是因為在主控台視窗中必須將物件呈現為文字。 文字輸出可能不會顯示要輸出之物件的所有屬性。

例如，請考慮 `Get-Location` Cmdlet。 如果您在目前位置是 C 磁碟機的根目錄時執行 `Get-Location`，就會看到下列輸出：

```
PS> Get-Location

Path
----
C:\
```

文字輸出是資訊的摘要，並不是由 `Get-Location` 所傳回之物件的完整呈現。 輸出中的標題是由處理序新增的，它會將資料格式化以便在畫面上顯示。

當您使用管線將輸出傳送到 `Get-Member` Cmdlet 時，會取得由 `Get-Location` 所傳回的物件相關資訊。

```powershell
PS> Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location` 會傳回 **PathInfo** 物件，其中包含目前的路徑與其他資訊。
