---
title: "管理目前的位置"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
translationtype: Human Translation
ms.sourcegitcommit: ffd2151603eb87f007e6596624a126585840f8a4
ms.openlocfilehash: 22c5df4f62f21f690800eaffe47afee604cc61d3

---

# 管理目前的位置
瀏覽檔案總管中的資料夾系統時，您通常有特定的工作位置，亦即目前開啟的資料夾。 只要按一下目前資料夾中的項目，即可輕鬆地操作這些項目。 對於命令列介面 (例如 Cmd.exe)，當位在與特定檔案相同的資料夾中時，您可以指定相對短的名稱來存取該檔案，而不需要指定該檔案的完整路徑。 目前的目錄稱為工作目錄。

Windows PowerShell 使用名詞 **Location** 來參照工作目錄，並實作一系列的 Cmdlet 來檢查及操作您的位置。

### 取得目前的位置 (Get\-Location)
若要判斷目前目錄位置的路徑，請輸入 **Get\-Location** 命令：

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Get\-Location Cmdlet 類似 BASH 殼層中的 **pwd** 命令。 Set\-Location Cmdlet 類似 Cmd.exe 中的 **cd** 命令。

### 設定目前的位置 (Set\-Location)
**Get\-Location** 命令是用來搭配 **Set\-Location** 命令使用。 **Set\-Location** 命令可讓您指定目前的目錄位置。

```
PS> Set-Location -Path C:\Windows
```

輸入命令之後，您將會注意到您沒有收到有關該命令之效果的任何直接回饋。 執行動作的大部分 Windows PowerShell 命令都只會產生一些輸出或甚至不產生輸出，因為輸出不見得實用。 當您輸入 **Set\-Location** 命令時，若要確定已順利變更目錄，請在輸入 **Set\-Location** 命令時包含 **\-PassThru** 參數：

```
PS> Set-Location -Path C:\Windows -PassThru
Path
----
C:\WINDOWS
```

**\-PassThru** 參數可以搭配 Windows PowerShell 中的許多 Set 命令使用以傳回結果的相關資訊，這在沒有預設輸出的情況下可能會有用。

您可以指定目前位置的相對路徑，就像您在大部分的 UNIX 與 Windows 命令殼層中所指定一樣。 在相對路徑的標準標記法中，句點 (**.**) 代表目前的資料夾，而雙句點 (**..**) 代表目前位置的上層目錄。

例如，若目前資料夾為 **C:\\Windows**，則句點 (**.**) 代表 **C:\\Windows**，而雙句點 (**..**) 代表 **C:**。 輸入下列命令，即可從目前的位置變更到 C: 磁碟機的根目錄：

<pre>PS> Set-Location -Path .. -PassThru Path ---- C:\</pre>

相同的方法在並非檔案系統磁碟機的 Windows PowerShell 磁碟機 (例如 **HKLM:**) 上也適用。 輸入下列命令，即可將您的位置設定為登錄中的 HKLM\\Software 機碼：

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

接著，您可以使用相對路徑，將該目錄位置變更為上層目錄 (Windows PowerShell HKLM: 磁碟機的根目錄)：

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

您可以輸入 Set\-Location 或使用 Set\--Location 的任一內建 Windows PowerShell 別名 (cd、chdir、sl)。 例如：

```
cd -Path C:\Windows
```

```
chdir -Path .. -PassThru
```

```
sl -Path HKLM:\SOFTWARE -PassThru
```

### 儲存及重新叫用最近的位置 (Push\-Location 與 Pop\-Location)
變更位置時，記錄曾使用的位置以及回到先前的位置可能是非常實用的功能。 Windows PowerShell 中的 **Push\-Location** Cmdlet 會建立您曾使用之目錄路徑的已排序歷程記錄 (堆疊)，而且您可以使用對應的 **Pop\-Location** Cmdlet 來重新叫用歷程記錄中的目錄路徑。

例如，Windows PowerShell 通常會在使用者的主目錄啟動。

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> *堆疊*一詞在許多程式設計設定中具有特殊意義，包括 .NET Framework。 就像項目的實體堆疊，您最後放入堆疊中的項目，是您可以從堆疊中取出第一個項目。 將項目新增到堆疊是將項目「推送」到堆疊。 從堆疊取出項目是將項目從堆疊「取出」。

若要將目前位置推送到堆疊，然後將它移動到 Local Settings 資料夾，請輸入：

```
PS> Push-Location -Path "Local Settings"
```

輸入下列命令，即可接著將 Local Settings 位置推送到堆疊，然後將它移動到 Temp 資料夾：

```
PS> Push-Location -Path Temp
```

您可以輸入 **Get\-Location** 命令，確認已順利變更目錄：

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

您可以輸入 **Pop\-Location** 命令以取回最近瀏覽的目錄，並輸入 **Get\-Location** 命令以確認變更：

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

就像使用 **Set\-Location** Cmdlet 一樣，您可以在輸入 **Pop\-Location** Cmdlet 時包含 **\-PassThru** 參數，以顯示您輸入的目錄：

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

您也可以使用 Location Cmdlet 來搭配網路路徑。 若您有名為 FS01 的伺服器與名為 Public 的共用，您可以變更位置，方式是輸入

```
Set-Location \\FS01\Public
```

或

```
Push-Location \\FS01\Public
```

您可以使用 **Push\-Location** 和 **Set\-Location** 命令將位置變更至任何可用的磁碟機。 例如，若您有磁碟機代號為 D 的本機 CD\-ROM 光碟機，且其中有資料 CD，您可以輸入 **Set\-Location D:** 命令，以將位置變更到該 CD 光碟機。

若該磁碟機是空的，您將會看到下列錯誤訊息：

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

使用命令列介面時，用檔案總管來檢查可用的實體磁碟機並不方便。 此外，[檔案總管] 將不會顯示所有 Windows PowerShell 磁碟機。 Windows PowerShell 提供一組可用於操作 Windows PowerShell 磁碟機的命令，稍後我們將討論這些命令。




<!--HONumber=Jul16_HO1-->


