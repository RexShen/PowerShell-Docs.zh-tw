---
ms.date: 07/28/2020
keywords: powershell,cmdlet
title: 使用檔案、資料夾與登錄機碼
ms.openlocfilehash: 7ead5d0e82feb852845468fb3a012a0908a4ce75
ms.sourcegitcommit: 339e5fc8a4cc18b4ff6956fe5180343588e40e30
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87410184"
---
# <a name="working-with-files-folders-and-registry-keys"></a>使用檔案、資料夾與登錄機碼

Windows PowerShell 使用名詞 **Item** 參照在 Windows PowerShell 磁碟機上找到的項目。
使用 Windows PowerShell FileSystem 提供者時，**Item** 可能是檔案、資料夾或 Windows PowerShell 磁碟機。 在大部分的系統管理設定中，列出及使用這些項目是很重要的基本工作，因此，我們要詳細討論這些工作。

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>列舉檔案、資料夾與登錄機碼 (Get-ChildItem)

因為從特定位置取得項目集合是很常見的工作；所以，`Get-ChildItem` Cmdlet 專門設計成傳回在容器 (例如資料夾) 中找到的所有項目。

若要傳回直接包含於資料夾 C:\\Windows 內的所有檔案和資料夾，請輸入：

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

此清單看起來與在 **Cmd.exe** 中輸入 `dir` 命令，或在 UNIX 命令殼層中輸入 `ls` 命令時所看到的清單類似。

您可使用 `Get-ChildItem` Cmdlet 的參數來執行極為複雜的清單。 我們接下來會介紹幾個案例。 您可鍵入以下命令來查看 `Get-ChildItem` Cmdlet 的語法：

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

這些參數可混合使用以得到高度自訂的輸出。

### <a name="listing-all-contained-items--recurse"></a>列出所有包含的項目 (-Recurse)

若要查看 Windows 資料夾內的項目和子資料夾中包含的任一項目，請使用 `Get-ChildItem` 的 **Recurse** 參數。 清單會顯示 Windows 資料夾中的所有項目和子資料夾中的項目。 例如：

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a>依名稱篩選項目 (-Name)

若只要顯示項目的名稱，請使用 `Get-Childitem` 的 **Name** 參數：

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a>強制列出隱藏的項目 (-Force)

通常檔案總管或 Cmd.exe 所隱藏項目都不會出現在 `Get-ChildItem` 命令的輸出中。 若要顯示隱藏的項目，請使用 `Get-ChildItem` 的 **Force** 參數。
例如：

```powershell
Get-ChildItem -Path C:\Windows -Force
```

此參數所以命名為 Force，是因為您可強制覆寫 `Get-ChildItem` 命令的正常行為。 Force 是廣泛使用的參數，會強制執行 Cmdlet 一般不會執行的動作，但並不會執行危害系統安全性的任何動作。

### <a name="matching-item-names-with-wildcards"></a>使用萬用字元比對項目名稱

`Get-ChildItem` 命令接受在清單項目路徑中使用萬用字元。

因為萬用字元比對是由 Windows PowerShell 引擎處理，接受萬用字元的所有 Cmdlet 都會使用相同的標記法，並有相同的比對行為。 Windows PowerShell 萬用字元標記法包括：

- 星號 (`*`) 會不比對或多次比對任一字元。

- 問號 (`?`) 只比對一個字元。

- 左中括弧 (`[`) 字元與右中括弧 (`]`) 字元是用來夾住要比對的一組字元。

以下是萬用字元規格如何運作的一些範例。

若要在 Windows 目錄中尋找副檔名為 `.log` 且基底名稱剛好 5 個字元的所有檔案，請輸入下列命令：

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

若要在 Windows 目錄中尋找開頭是字母為 `x` 的所有檔案，請鍵入：

```powershell
Get-ChildItem -Path C:\Windows\x*
```

若要尋找名稱開頭是 "x" 或 "z" 的所有檔案，請鍵入：

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

如需萬用字元的詳細資訊，請參閱 [about_Modules](/powershell/module/microsoft.powershell.core/about/about_wildcards)。

### <a name="excluding-items--exclude"></a>排除項目 (-Exclude)

您可使用 `Get-ChildItem` 的 **Exclude** 參數來排除特定項目。 這可讓您在單一陳述式中執行複雜的篩選。

例如，假設嘗試在 **System32** 資料夾中尋找 Windows 時間服務 DLL，但您只記得該 DLL 的名稱以 "W" 開頭且包含 "32"。

`w*32*.dll` 之類運算式會尋找所有符合條件的 DLL，但您想要進一步篩選檔案，並略過所有 win32 檔案。 您可使用 **Exclude** 參數配合模式 `win*` 來略過這些檔案：

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude win*

    Directory: C:\WINDOWS\System32

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           3/18/2019  9:43 PM         495616 w32time.dll
-a---           3/18/2019  9:44 PM          35328 w32topl.dll
-a---           1/24/2020  5:44 PM         401920 Wldap32.dll
-a---          10/10/2019  5:40 PM         442704 ws2_32.dll
-a---           3/18/2019  9:44 PM          66048 wsnmp32.dll
-a---           3/18/2019  9:44 PM          18944 wsock32.dll
-a---           3/18/2019  9:44 PM          64792 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a>混合使用 Get-ChildItem 參數

您可在同一個命令中使用 `Get-ChildItem` Cmdlet 的數個參數。 在混合使用參數之前，請確定您了解萬用字元比對的原則。 例如，下列命令不會傳回任何結果：

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

即使 Windows 資料夾中有兩個開頭是字母 "z" 的 DLL 也不會有任何結果。

因為我們將萬用字元指定為路徑的一部分，因此不會傳回任何結果。 即使命令是遞迴命令，`Get-ChildItem` Cmdlet 也會將項目限制在 Windows 資料夾中名稱結尾是 `.dll` 的項目。

若要為名稱符合特殊模式的檔案指定遞迴搜尋，請使用 **Include** 參數。

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```
