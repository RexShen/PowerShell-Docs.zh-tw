---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用登錄項目
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 8483b6f98739697b24a13055dfffbc7b5bacc2cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677153"
---
# <a name="working-with-registry-entries"></a>使用登錄項目

因為登錄項目是機碼的屬性，所以無法直接瀏覽，在使用時，必須採取稍微不同的方法。

### <a name="listing-registry-entries"></a>列出登錄項目

有許多方法可以檢查登錄項目。 最簡單的方法是取得與機碼相關聯的屬性名稱。 例如，若要查看登錄機碼中的項目名稱`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`，使用`Get-Item`。 登錄機碼有一個具有一般名稱 "Property" 的屬性，是機碼中之登錄項目的清單。
下列命令會選取 Property 屬性並展開項目，使項目顯示於清單中：

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

若要更容易閱讀的形式檢視登錄項目，請使用`Get-ItemProperty`:

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

您可以使用 "`*.*`." 標記法以參照目前的位置。 您可以使用`Set-Location`變更為**CurrentVersion**登錄容器第一次：

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

或者，您可以使用與內建的 HKLM PSDrive `Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

接著，您可以使用 "`*.*`." 標記法來表示目前的位置，以列出屬性而不指定完整路徑：

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

路徑擴充的作用相同檔案系統中，以便從這個位置取得**ItemProperty**清單`HKLM:\SOFTWARE\Microsoft\Windows\Help`使用`Get-ItemProperty -Path ..\Help`。

### <a name="getting-a-single-registry-entry"></a>取得單一登錄項目

若要抓取登錄機碼中的特定項目，您可以使用數種可行方法之一。 此範例會尋找的值**DevicePath**在`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`。

使用`Get-ItemProperty`，使用**路徑**參數來指定名稱的金鑰，而**名稱**參數指定的名稱**DevicePath**項目。

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
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
> 雖然`Get-ItemProperty`已經**篩選**， **Include**，和**排除**參數，它們無法用來篩選屬性名稱。 這些參數指的登錄機碼，也就是項目路徑和登錄項目。 登錄項目是項目屬性。

另一個選項是使用 Reg.exe 命令列工具。 如需 reg.exe 的說明，請輸入`reg.exe /?`在命令提示字元。 若要尋找 DevicePath 項目，請使用 reg.exe，如下列命令所示：

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

您也可以使用 **WshShell COM** 物件來尋找某些登錄項目，雖然此方法無法處理大型二進位資料或包含 "\\" 等字元的登錄項目名稱)。 使用 \\ 分隔符號將屬性名稱附加至項目路徑：

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a>設定單一登錄項目

如果您想要變更登錄機碼中的特定項目，您可以使用數種可行方法之一。 此範例會修改**路徑**下方的項目`HKEY_CURRENT_USER\Environment`。 **路徑**項目指定何處可找到可執行檔。

1. 擷取目前的值**路徑**項目使用`Get-ItemProperty`。
2. 加入新的值，並將其與`;`。
3. 使用`Set-ItemProperty`使用指定的索引鍵、 項目名稱和值，若要修改的登錄項目。

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> 雖然`Set-ItemProperty`已經**篩選**， **Include**，和**排除**參數，它們無法用來篩選屬性名稱。 這些參數指的是登錄機碼 (它們是項目路徑，不是登錄項目)，即項目屬性。

另一個選項是使用 Reg.exe 命令列工具。 如需 reg.exe 的說明，請輸入 **reg.exe /?**
。

下列範例會變更**路徑**藉由移除在上述範例中所加入的路徑的項目。
`Get-ItemProperty` 仍然用來擷取目前的值，以避免需剖析傳回的字串`reg query`。 **SubString**並**LastIndexOf**方法來擷取最後一個路徑新增至**路徑**項目。

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a>建立新的登錄項目

若要將名為"PowerShellPath"的新項目新增至**CurrentVersion**鍵，使用`New-ItemProperty`索引鍵、 項目名稱和值的項目路徑。 對於此範例中，我們將接受 Windows PowerShell 變數的值`$PSHome`，它儲存 Windows PowerShell 安裝目錄的路徑。

您可以使用下列命令將新項目新增至機碼，此命令也會傳回關於新項目的資訊：

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
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

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

您可以藉由新增也覆寫現有的登錄項目值**Force**參數，以任何`New-ItemProperty`命令。

### <a name="renaming-registry-entries"></a>重新命名登錄項目

若要重新命名**PowerShellPath**項目為"PSHome"，使用`Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

若要顯示重新命名的值，請將 **PassThru** 參數新增至命令。

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>刪除登錄項目

若要刪除 PSHome 與 PowerShellPath 登錄項目，請使用`Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
