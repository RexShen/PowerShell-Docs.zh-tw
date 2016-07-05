---
title: "直接操作項目"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: b7e752a1615da4540106ec32754f873c5d7aa5d9

---

# 直接操作項目
您在 Windows PowerShell 磁碟機中看到的項目 (例如檔案系統磁碟機中的檔案與資料夾，以及 Windows PowerShell 登錄磁碟機中的登錄機碼) 在 Windows PowerShell 中稱為*項目*。 用於處理項目之 Cmdlet 的名稱中具有名詞 **Item**。

**Get\-Command \-Noun Item** 命令的輸出顯示有九個 Windows PowerShell 項目 Cmdlet。

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

### 建立新項目 (New\-Item)
若要在檔案系統中建立新項目，請使用 **New\-Item** Cmdlet。 包含 **Path** 參數並指定項目路徑作為參數值，以及包含 **ItemType** 參數並指定 "file" 或 "directory" 的值。

例如，若要在 C:\\Temp 目錄中建立名為 "New.Directory" 的新目錄，請輸入：

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

若要建立檔案，請將 **ItemType** 參數的值變更為 "file"。 例如，若要在 New.Directory 目錄中建立名為 "file1.txt" 的檔案，請輸入：

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

您可以使用相同的方式來建立新的登錄機碼。 事實上，建立登錄機碼的方式較簡單，因為 Windows 登錄中唯一的項目類型是機碼。 (登錄項目是項目*屬性*。)例如，若要在 CurrentVersion 子機碼中建立名為 "\_Test" 的機碼，請輸入：

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

輸入登錄路徑時，請務必在 Windows PowerShell 磁碟機名稱中包含冒號 (**:**)，亦即 HKLM: 與 HKCU:。 若未使用冒號，Windows PowerShell 將無法識別該路徑中的磁碟機名稱。

### 為什麼登錄值不是項目
當您使用 **Get\-ChildItem** Cmdlet 來尋找登錄機碼中的項目時，您將永遠不會看到實際的登錄項目或其值。

例如，登錄機碼 **HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** 通常包含數個登錄項目，這些登錄項目代表系統啟動時執行的應用程式。

不過，當您使用 **Get\-ChildItem** 來尋找機碼中的子項目時，您只會看到該機碼的 **OptionalComponents** 子機碼：

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

雖然將登錄項目視為項目很方便，但您無法在指定登錄項目路徑時確保其唯一性。 路徑標記法無法區分名為 **Run** 的登錄子機碼與 **Run** 子機碼中的 **(Default)** 登錄項目。 此外，因為登錄項目名稱可以包含反斜線字元 (**\\**)，若登錄項目是項目，您無法使用路徑標記法來區分名為 **Windows\\CurrentVersion\\Run** 的登錄項目與該路徑中的子機碼。

### 重新命名現有的項目 (Rename\-Item)
若要變更檔案或資料夾的名稱，請使用 **Rename\-Item** Cmdlet。 下列命令會將 **file1.txt** 檔案的名稱變更為 **fileOne.txt**。

```
PS> Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

**Rename\-Item** Cmdlet 可以變更檔案或資料夾的名稱，但無法移動項目。 下列命令會失敗。因為它會嘗試將檔案從 New.Directory 目錄移動到 Temp 目錄。

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### 移動項目 (Move\-Item)
若要移動檔案或資料夾，請使用 **Move\-Item** Cmdlet。

例如，下列命令會將 New.Directory 目錄從 C:\\temp 目錄移動到 C: 磁碟機的根目錄。 若要確定項目已移動，請包含 **Move\-Item** Cmdlet 的 **PassThru** 參數。 若未指定 **Passthru**，**Move\-Item** Cmdlet 不會顯示任何結果。

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### 複製項目 (Copy\-Item)
若您熟悉其他殼層中的複製操作，您可能會發現 Windows PowerShell 中 **Copy\-Item** Cmdlet 的行為不尋常。 當您將某個項目從一個位置複製到另一個位置時，Copy\-Item 預設不會複製其內容。

例如，若您將 **New.Directory** 目錄從 C: 磁碟機複製到 C:\\temp 目錄，該命令會成功，但不會複製 New.Directory 目錄中的檔案。

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp
```

若顯示 **C:\\temp\\New.Directory** 的內容，您會發現其中未包含任何檔案：

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

為什麼 **Copy\-Item** Cmdlet 不會將內容複製到新位置？

**Copy\-Item** Cmdlet 被設計為泛型，它不是只能用來複製檔案與資料夾。 此外，即使複製檔案與資料夾時，您可能只想複製容器，而非其中的項目。

若要複製資料夾中的所有內容，請在命令中包含 **Copy\-Item** Cmdlet 的 **Recurse** 參數。 若已複製目錄但未複製其內容，請新增 **Force** 參數，這樣可以讓您覆寫空資料夾。

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

### 刪除項目 (Remove\-Item)
若要刪除檔案與資料夾，請使用 **Remove\-Item** Cmdlet。 會造成大幅且無法復原之變更的 Windows PowerShell Cmdlet (例如 **Remove\-Item**) 通常會在您輸入其命令時提示您確認。 例如，若嘗試移除 **New.Directory** 資料夾，系統會提示您確認要執行該命令，因為資料夾包含檔案：

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

因為 **[是]** 是預設回應，若要刪除資料夾與其中的檔案，請按 **Enter** 鍵。 若要在不確認的情況下移除資料夾，請使用 **\-Recurse** 參數。

```
PS> Remove-Item C:\temp\New.Directory -Recurse
```

### 執行項目 (Invoke\-Item)
Windows PowerShell 使用 **Invoke\-Item** Cmdlet 來針對檔案或資料夾執行預設動作。 此預設動作是由登錄中的預設應用程式處理常式決定，效果等同於在檔案總管中按兩下該項目。

例如，假設您執行下列命令：

```
PS> Invoke-Item C:\WINDOWS
```

位在 C:\\Windows 的檔案總管視窗隨即出現，就像您按兩下 C:\\Windows 資料夾一樣。

若在 Windows Vista 之前的系統上叫用 **Boot.ini** 檔案：

```
PS> Invoke-Item C:\boot.ini
```

若 .ini 檔案類型與 [記事本] 關聯，boot.ini 檔案會在 [記事本] 中開啟。




<!--HONumber=Jun16_HO4-->


