---
title: 使用登錄項目
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
---
# 使用登錄項目
因為登錄項目是機碼的屬性，所以無法直接瀏覽，在使用時，必須採取稍微不同的方法。

### 列出登錄項目
有許多方法可以檢查登錄項目。 最簡單的方法是取得與機碼相關聯的屬性名稱。 例如，若要查看登錄機碼 **HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion** 中的項目名稱，請使用 **Get-Item**。 登錄機碼有一個具有一般名稱 "Property" 的屬性，是機碼中之登錄項目的清單。 下列命令會選取 Property 屬性並展開項目，使項目顯示於清單中：

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

若要以更多可讀形式檢視登錄項目，請使用 **Get-ItemProperty**：

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

機碼的 Windows PowerShell 相關屬性都包含首碼 "PS"，例如 **PSPath**、**PSParentPath**、**PSChildName** 和 **PSProvider**。

您可以使用 "**.**" 標記法以參照目前的位置。 您可以先使用 **Set-Location** 來變更為 **CurrentVersion** 登錄容器：

```
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

或者，您可以使用內建的 HKLM PSDrive 來搭配 **Set-Location**：

```
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

接著，您可以使用 "**.**" 標記法來表示目前的位置，以列出屬性而不指定完整路徑：

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

路徑擴充的作用與在檔案系統中一致，因此從這個位置，您可以使用 **Get-ItemProperty -Path ..\Help** 取得 **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** 的 **ItemProperty** 清單。

### 取得單一登錄項目
若要抓取登錄機碼中的特定項目，您可以使用數種可行方法之一。 這個範例會尋找 **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion** 中 **DevicePath** 的值。

使用 **Get-ItemProperty** 時，請使用 **Path** 參數來指定機碼的名稱，並使用 **Name** 參數來指定 **DevicePath** 項目的名稱。

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

此命令會傳回標準的 Windows PowerShell 屬性與 **DevicePath** 屬性。

> [!NOTE]
> 雖然 **Get-ItemProperty** 包含 **Filter**、**Include** 與 **Exclude** 參數，但您無法使用它們來篩選屬性名稱。 這些參數指的是登錄機碼 (它們是項目路徑，不是登錄項目)，即項目屬性。

另一個選項是使用 Reg.exe 命令列工具。 如需 reg.exe 的說明，請在命令提示字元中輸入 **reg.exe /?** 。 若要尋找 DevicePath 項目，請使用 reg.exe，如下列命令所示：

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

您也可以使用 **WshShell COM** 物件來尋找某些登錄項目，雖然此方法無法處理大型二進位資料或包含 "\\" 等字元的登錄項目名稱)。 使用 \\ 分隔符號將屬性名稱附加至項目路徑：

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### 建立新的登錄項目
若要將名為 "PowerShellPath" 的新項目新增至 **CurrentVersion** 機碼，請搭配機碼路徑、項目名稱與項目值使用 **New\-ItemProperty**。 對於此範例，我們將接受 Windows PowerShell 變數 **$PSHome** 的值，它儲存 Windows PowerShell 安裝目錄的路徑。

您可以使用下列命令將新項目新增至機碼，此命令也會傳回關於新項目的資訊：

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

**PropertyType** 必須是下表之 **Microsoft.Win32.RegistryValueKind** 列舉成員的名稱：

|PropertyType 值|意義|
|----------------------|-----------|
|Binary|二進位資料|
|DWord|屬於有效 UInt32 的數字|
|ExpandString|可包含會動態展開之環境變數的字串|
|MultiString|多行字串|
|String|任何字串值|
|QWord|8 個位元組的二進位資料|

> [!NOTE]
> 為 **Path** 參數指定值陣列，可以將某個登錄項目新增至多個位置：

```
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

您也可以將 **Force** 參數新增至任一 **New\-ItemProperty** 命令，以覆寫已存在的登錄項目值。

### 重新命名登錄項目
若要將 **PowerShellPath** 項目重新命名為 "PSHome"，請使用 **Rename\-ItemProperty**：

```
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

若要顯示重新命名的值，請將 **PassThru** 參數新增至命令。

```
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### 刪除登錄項目
若要刪除 PSHome 與 PowerShellPath 登錄項目，請使用 **Remove\-ItemProperty**：

```
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```



<!--HONumber=Apr16_HO1-->


