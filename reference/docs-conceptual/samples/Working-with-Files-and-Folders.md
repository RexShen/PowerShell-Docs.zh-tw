---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用檔案及資料夾
ms.openlocfilehash: 0f7cb233918b59475417ec49b611ecc25a94ebe1
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030698"
---
# <a name="working-with-files-and-folders"></a>使用檔案及資料夾

瀏覽 Windows PowerShell 磁碟機和操作磁碟機上的項目，類似於在 Windows 實體磁碟機上操作檔案和資料夾。 本節會討論如何使用 PowerShell 來處理特定檔案和資料夾操作工作。

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>列出資料夾內所有的檔案和資料夾

您可以使用 **Get-ChildItem** 直接取得資料夾內的所有項目。 加入選用的 **Force** 參數，以顯示隱藏或系統項目。 例如，這個命令會顯示 Windows PowerShell 磁碟機 C (和 Windows 實體磁碟機 C 相同) 的直接內容︰

```powershell
Get-ChildItem -Path C:\ -Force
```

命令只會列出直接包含的項目，很像使用 Cmd.exe 的 **DIR** 命令或 UNIX 殼層的 **ls**。 若要顯示包含的項目，您也必須要指定 **-Recurse** 參數。 (這可能需要很長時間才能完成)。列出 C 磁碟機上的所有項目︰

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

**Get-ChildItem** 可以用它的 **Path**、**Filter**、**Include** 和 **Exclude** 參數來篩選項目，但這些通常只以名稱為基礎。 您可以使用 **Where-Object** 根據項目的其他屬性來執行複雜的篩選。

下列命令會在 Program Files 資料夾內尋找在 2005 年 10 月 1 日之後修改的、介於 1 MB 到 10 MB 之間的全部可執行檔︰

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>複製檔案與資料夾

以 **Copy-Item** 完成複製。 下列命令會將 C:\\boot.ini 備份到 C:\\boot.bak：

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

如果目的地檔案已經存在，則複製嘗試就會失敗。 若要覆寫既有的目的地，請使用 **Force** 參數：

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

這個命令對唯讀的目的地也有效。

複製資料夾的方式也相同。 這個命令會將資料夾 C:\\temp\\test1 以遞迴方式複製到新的資料夾 C:\\temp\\DeleteMe：

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

您也可以複製選取的項目。 下列命令會將 c:\\data 中任何位置的所有 .txt 檔案複製到 c:\\temp\\text︰

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

您仍然可以使用其他工具執行檔案系統複製。 XCOPY、ROBOCOPY 和 COM 物件，如 **Scripting.FileSystemObject**，在 Windows PowerShell 中都有效。 例如，您可以使用 Windows Script Host **Scripting.FileSystem COM** 類別將 C:\\boot.ini 備份到 C:\\boot.bak︰

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>建立檔案與資料夾

所有 Windows PowerShell 提供者的建立新項目功能都一樣。 如果 Windows PowerShell 提供者有多個項目類型—例如，FileSystem Windows PowerShell 提供者區分目錄和檔案—您就需要指定項目類型。

這個命令會建立新的資料夾 C:\\temp\\New Folder：

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

這個命令會建立新的空檔案 C:\\temp\\New Folder\\file.txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a>移除資料夾內所有的檔案和資料夾

您可以使用 **Remove-Item** 移除包含的項目，但如果項目包含任何其他項目，系統會提示您確認移除。 例如，如果您嘗試刪除包含其他項目的資料夾 C:\\temp\\DeleteMe，Windows PowerShell 就會先提示您確認再刪除資料夾︰

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

如果不想每個包含項目都出現提示，請指定 **Recurse** 參數：

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>將本機資料夾對應為 Windows 可存取磁碟機

您也可以使用 **subst** 命令對應本機資料夾。 下列命令會在本機的 Program Files 目錄下建立本機磁碟機 P:︰

```powershell
subst p: $env:programfiles
```

就像使用網路磁碟機，Windows PowerShell 殼層可以立即看到使用 **subst** 在 Windows PowerShell 內對應的磁碟機。

## <a name="reading-a-text-file-into-an-array"></a>將文字檔讀入陣列

文字資料最常見的儲存體格式之一，是將檔案中分隔的各行視為不同的資料元素。 **Get-Content** Cmdlet 可以用一個步驟讀取整個檔案，如下所示︰

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

**Get-Content** 已經將從檔案讀取的資料視為陣列，檔案內容為每行一個元素。 您可以藉由檢查只要核取傳回內容的 **長度** 即可確認︰

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

這個命令在將資訊清單直接放入 Windows PowerShell 非常有用。 例如，您可能會在檔案 C:\\temp\\domainMembers.txt 中儲存電腦名稱或 IP 位址的清單，一行一個名稱。 您可以使用 **Get-Content** 擷取檔案內容並將內容放入變數 **$Computers**：

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** 現在是每個元素包含一個電腦名稱的陣列。
