---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用檔案及資料夾
ms.openlocfilehash: 8876ff70adbd10c9019f6d80ce7ad327f2932c74
ms.sourcegitcommit: 08acbea14c69a347f2f46aafcb215a5233c7d830
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/01/2020
ms.locfileid: "82691493"
---
# <a name="working-with-files-and-folders"></a>使用檔案及資料夾

瀏覽 Windows PowerShell 磁碟機和操作磁碟機上的項目，類似於在 Windows 實體磁碟機上操作檔案和資料夾。 本節會討論如何使用 PowerShell 來處理特定檔案和資料夾操作工作。

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>列出資料夾內所有的檔案和資料夾

您可以使用 `Get-ChildItem` 直接取得資料夾內的所有項目。 加入選用的 **Force** 參數，以顯示隱藏或系統項目。 例如，這個命令會顯示 Windows PowerShell 磁碟機 C (和 Windows 實體磁碟機 C 相同) 的直接內容︰

```powershell
Get-ChildItem -Path C:\ -Force
```

此命令只會列出直接包含的項目，這跟使用 `Cmd.exe` 的 `DIR` 命令或 UNIX 殼層中的 `ls` 很像。 若要顯示包含的項目，您也必須指定 `-Recurse` 參數。 (這可能需要很長時間才能完成)。列出 C 磁碟機上的所有項目︰

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

`Get-ChildItem` 可以使用項目的 **Path**、**Filter**、**Include** 與 **Exclude** 參數來加以篩選，但那些參數通常只以名稱為基礎。 您可以使用 `Where-Object` 以根據項目的其他屬性來執行複雜的篩選。

下列命令會在 Program Files 資料夾內尋找在 2005 年 10 月 1 日之後修改的、介於 1 MB 到 10 MB 之間的全部可執行檔︰

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>複製檔案與資料夾

使用 `Copy-Item` 即可進行複製。 下列命令會將 C:\\boot.ini 備份到 C:\\boot.bak：

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

如果目的地檔案已經存在，則複製嘗試就會失敗。 若要覆寫既有的目的地，請使用 **Force** 參數：

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

這個命令對唯讀的目的地也有效。

複製資料夾的方式也相同。 此命令會以遞迴方式將資料夾 `C:\temp\test1` 複製到新的資料夾 `C:\temp\DeleteMe`：

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

您也可以複製選取的項目。 下列命令會將 `C:\data` 中任何位置的所有 .txt 檔案複製到 `C:\temp\text`︰

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

您仍然可以使用其他工具執行檔案系統複製。 XCOPY、ROBOCOPY 和 COM 物件，如 **Scripting.FileSystemObject**，在 Windows PowerShell 中都有效。 例如，您可以使用 Windows Script Host **Scripting.FileSystem COM** 類別將 `C:\boot.ini` 備份到 `C:\boot.bak`︰

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>建立檔案與資料夾

所有 Windows PowerShell 提供者的建立新項目功能都一樣。 如果 Windows PowerShell 提供者有多個項目類型—例如，FileSystem Windows PowerShell 提供者區分目錄和檔案—您就需要指定項目類型。

此命令會建立新資料夾 `C:\temp\New Folder`：

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

此命令會建立新空白檔案 `C:\temp\New Folder\file.txt`

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

> [!IMPORTANT]
> 在搭配 `New-Item` 命令使用 **Force** 參數來建立資料夾，且該資料夾已經存在的情況下，其「將不會」  覆寫或取代該資料夾， 而只會傳回現有的資料夾物件。 不過，如果您對已經存在的檔案使用 `New-Item -Force`，系統「將會」  完全覆寫該檔案。

## <a name="removing-all-files-and-folders-within-a-folder"></a>移除資料夾內所有的檔案和資料夾

您可以使用 `Remove-Item` 來移除包含的項目，但如果項目包含任何其他項目，系統會提示您確認移除。 例如，如果您嘗試刪除包含其他項目的資料夾 `C:\temp\DeleteMe`，Windows PowerShell 會先提示您確認再刪除該資料夾︰

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the Recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

如果不想每個包含項目都出現提示，請指定 **Recurse** 參數：

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a>將本機資料夾對應為磁碟機

您也可以使用 `New-PSDrive` 命令來對應本機資料夾。 下列命令會建立本機磁碟機 `P:`，該磁碟機以 [Program Files] 目錄為根目錄，而且只能從 PowerShell 工作階段看到︰

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

就像使用網路磁碟機，Windows PowerShell 殼層可以立即看到在 Windows PowerShell 內對應的磁碟機。 若要建立可從 [檔案總管] 看到的對應磁碟機，則需要參數 `-Persist`。 不過，只有遠端路徑可以搭配 -Persist 使用。

## <a name="reading-a-text-file-into-an-array"></a>將文字檔讀入陣列

文字資料最常見的儲存體格式之一，是將檔案中分隔的各行視為不同的資料元素。 您可以使用 `Get-Content` Cmdlet 透過單一步驟讀取整個檔案，如下所示︰

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

`Get-Content` 已經將從檔案讀取的資料視為陣列，並將檔案內容的每一行視為單一元素。 您可以藉由檢查只要核取傳回內容的 **長度** 即可確認︰

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

這個命令在將資訊清單直接放入 Windows PowerShell 非常有用。 例如，您可能會在檔案 `C:\temp\domainMembers.txt` 中儲存電腦名稱或 IP 位址的清單，並使檔案的每一行皆包含一個名稱。 您可以使用 `Get-Content` 來擷取檔案內容，並將內容放入變數 `$Computers` 中：

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

`$Computers` 現在是每個元素中皆包含一個電腦名稱的陣列。
