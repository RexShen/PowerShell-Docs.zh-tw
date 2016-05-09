---
title: 管理 Windows PowerShell 磁碟機
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
---
# 管理 Windows PowerShell 磁碟機
*Windows PowerShell 磁碟機*是一個資料存放區位置，存取該位置的方式就像存取 Windows PowerShell 中的檔案系統磁碟機一樣。 Windows PowerShell 提供者會為您建立一些磁碟機，例如檔案系統磁碟機 (包括 C: 與 D:)、登錄磁碟機 (HKCU: 與 HKLM:) 與憑證磁碟機 (Cert:)，而且您可以建立自己的 Windows PowerShell 磁碟機。 這些磁碟機非常實用，但只能在 Windows PowerShell 中使用。 您無法使用其他 Windows 工具 (例如 [檔案總管] 或 Cmd.exe) 來存取它們。

Windows PowerShell 會為可搭配 Windows PowerShell 磁碟機使用的命令使用名詞 **PSDrive**。 如需 Windows PowerShell 工作階段中的 Windows PowerShell 磁碟機清單，請使用 **Get-PSDrive** Cmdlet。

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

雖然顯示中的磁碟機視您系統上的磁碟機而異，清單看起來會像是上面顯示的 **Get-PSDrive** 命令輸出。

檔案系統磁碟機是 Windows PowerShell 磁碟機的子集。 您可以透過 [提供者] 欄中的 FileSystem 項目來識別檔案系統磁碟機。 (Windows PowerShell 中的檔案系統磁碟機受 Windows PowerShell FileSystem 提供者支援。)

若要檢視 **Get-PSDrive** Cmdlet 的語法，請輸入 **Get-Command** 命令並指定 **Syntax** 參數：

```
PS> Get-Command -Name Get-PSDrive -Syntax
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

**PSProvider** 參數可讓您只顯示受特定提供者支援的 Windows PowerShell 磁碟機。 例如，若只要顯示受 Windows PowerShell FileSystem 提供者支援的 Windows PowerShell 磁碟機，請輸入 **Get-PSDrive** 命令並指定 **PSProvider** 參數與 **FileSystem** 值：

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

若要檢視代表登錄區的 Windows PowerShell 磁碟機，請使用 **PSProvider** 參數以便只顯示 Windows PowerShell 登錄提供者所支援的 Windows PowerShell 磁碟機：

<pre>PS> Get-PSDrive -PSProvider Registry
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE</pre>

您也可以使用標準 Location Cmdlet 來搭配 Windows PowerShell 磁碟機：

<pre>PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location
路徑
----
HKLM:\SOFTWARE\Microsoft</pre>

### 新增 Windows PowerShell 磁碟機 (New-PSDrive)
您可以使用 **New-PSDrive** 命令來新增自己的 Windows PowerShell 磁碟機。 若要取得 **New-PSDrive** 命令的語法，請輸入 **Get-Command** 命令並指定 **Syntax** 參數：

```
PS> Get-Command -Name New-PSDrive -Syntax
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

若要建立新的 Windows PowerShell 磁碟機，您必須提供三個參數：

-   磁碟機的名稱 (您可以使用任何有效的 Windows PowerShell 名稱)

-   PSProvider (使用 "FileSystem" 代表檔案系統位置；使用 "Registry" 代表登錄位置)

-   根目錄，亦即新磁碟機的根目錄路徑

例如，您可以建立名為 "Office" 的磁碟機，將它對應到您電腦上包含 Microsoft Office 應用程式的資料夾，例如 **C:\Program Files\Microsoft Office\OFFICE11**。 若要建立該磁碟機，請輸入下列命令：

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> 一般而言，路徑不區分大小寫。

您可以使用參照所有 Windows 磁碟機的方式參照新的 Windows PowerShell 磁碟機，亦即輸入磁碟機名稱並加上冒號 (**:**)。

Windows PowerShell 磁碟機可以讓許多工作變得更簡單。 例如，Windows 登錄中的某些重要機碼具有極長的路徑，使得它們不容易存取且難以記住。 重要設定資訊位於 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion** 下。 若要檢視及變更 CurrentVersion 登錄機碼中的項目，您可以建立根目錄為該機碼的 Windows PowerShell 磁碟機，方式是輸入下列命令：

<pre>PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...</pre>

接著，您可以將位置變更至 **cvkey:** 磁碟機，就像存取任何其他磁碟機一樣：

`PS> cd cvkey:`

或者：

<pre>PS> Set-Location cvkey: -PassThru
路徑
----
cvkey:\</pre>

New-PsDrive Cmdlet 會將新磁碟機只新增到目前的 Windows PowerShell 工作階段。 若關閉該 Windows PowerShell 視窗，該新磁碟機就會消失。 若要儲存 Windows PowerShell 磁碟機，請使用 Export-Console Cmdlet 來匯出目前的 Windows PowerShell 工作階段，然後使用 PowerShell.exe **PSConsoleFile** 參數來匯入它。 或者，將新磁碟機新增到您的 Windows PowerShell 設定檔。

### 刪除 Windows PowerShell 磁碟機 (Remove-PSDrive)
您可以使用 **Remove-PSDrive** Cmdlet 從 Windows PowerShell 刪除磁碟機。 **Remove-PSDrive** Cmdlet 使用方式很簡單；若要刪除特定 Windows PowerShell 磁碟機，您只需要提供 Windows PowerShell 磁碟機名稱即可。

例如，若已新增 **Office:** Windows PowerShell 磁碟機 (如 **New-PSDrive** 主題所示)，您可以輸入下列命令將它刪除：

```
PS> Remove-PSDrive -Name Office
```

若要刪除 **cvkey:** Windows PowerShell 磁碟機 (如 **New-PSDrive** 主題所示)，請使用下列命令：

```
PS> Remove-PSDrive -Name cvkey
```

刪除 Windows PowerShell 磁碟機的方式非常簡單，但您無法在位於磁碟機中時刪除該磁碟機。 例如：

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### 在 Windows PowerShell 之外新增及移除磁碟機
Windows PowerShell 會偵測 Windows 中新增或移除的檔案系統磁碟機，包括對應的網路磁碟機、連接的 USB 磁碟機，以及使用 **net use** 命令或從 Windows Script Host (WSH) 指令碼使用 **WScript.NetworkMapNetworkDrive** 與 **RemoveNetworkDrive** 方法刪除的磁碟機。



<!--HONumber=Apr16_HO1-->


