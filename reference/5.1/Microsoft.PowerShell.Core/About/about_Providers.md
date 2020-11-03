---
description: 描述 PowerShell 提供者如何提供無法在命令列輕鬆存取之資料和元件的存取權。 資料是以一致的格式呈現，類似于檔案系統磁片磁碟機。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: 952ab618f1e47f0f912209ba56c37a667c596aaf
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207595"
---
# <a name="about-providers"></a>關於提供者

## <a name="short-description"></a>簡短描述
描述 PowerShell 提供者如何提供無法在命令列輕鬆存取之資料和元件的存取權。
資料是以一致的格式呈現，類似于檔案系統磁片磁碟機。

## <a name="long-description"></a>完整描述

PowerShell 提供者是 .NET 程式，可讓您存取特定的資料存放區，以便更輕鬆地進行流覽和管理。 資料會出現在磁片磁碟機中，您可以像在硬碟一樣存取路徑中的資料。 您可以使用提供者支援的任何內建 Cmdlet 來管理提供者磁片磁碟機中的資料。 而且，您可以使用特別針對資料設計的自訂 Cmdlet。

提供者也可以將動態參數新增至內建的 Cmdlet。 只有當您搭配提供者資料使用 Cmdlet 時，才能使用這些參數。

## <a name="built-in-providers"></a>內建提供者

PowerShell 包含一組內建提供者，可讓您用來存取不同類型的資料存放區。

| 提供者   |   磁片磁碟機 (s)   |OutputType                                                    |
|----------- |------------ |--------------------------------------------------------------|
|Alias       |Alias:       |System.Management.Automation.AliasInfo                        |
|憑證 |Cert:        |Microsoft.powershell.commands.x509storelocation。               |
|            |             |System.Security.Cryptography.X509Certificates.X509Certificate2|
|環境 |Env:         |DictionaryEntry                            |
|FileSystem  |C： ( * )        |System.IO.FileInfo                                            |
|            |             |DirectoryInfo                                       |
|函式    |函式：    |System.Management.Automation.FunctionInfo                     |
|登錄    |HKLM： HKCU：  |Microsoft. RegistryKey                                   |
|變數    |Variable:    |System.Management.Automation.PSVariable                       |
|WSMan       |WSMan:       |Microsoft.WSMan.Management.WSManConfigContainerElement        |

 ( * ) 每個系統上的 FileSystem 磁片磁碟機各不相同。

您也可以建立自己的 PowerShell 提供者，而且可以安裝其他人所開發的提供者。 若要列出您的會話中可用的提供者，請輸入：

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a>安裝和移除提供者

提供者通常會透過 PowerShell 模組安裝。 匯入模組會將提供者載入您的會話中。 您無法卸載內建的提供者。 您可以卸載其他模組所載入的提供者。

您可以使用 Cmdlet 從目前的會話中卸載提供者 `Remove-Module` 。 此 Cmdlet 不會卸載提供者，但它會讓提供者無法在會話中使用。

您也可以使用 `Remove-PSDrive` Cmdlet 來移除目前會話中的任何磁片磁碟機。 磁片磁碟機上的此資料不會受到影響，但該會話無法再使用該磁片磁碟機。

## <a name="viewing-providers"></a>查看提供者

若要在您的電腦上查看 PowerShell 提供者，請輸入：

```powershell
Get-PSProvider
```

輸出會列出內建提供者，以及您新增至會話的提供者。

## <a name="the-provider-cmdlets"></a>提供者 Cmdlet

下列 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 您可以用相同的方式使用相同的 Cmdlet 來管理提供者公開的不同資料類型。 在您瞭解如何管理某個提供者的資料之後，您可以使用來自任何提供者之資料的相同程式。

例如，Cmdlet 會 `New-Item` 建立新專案。 在 `C:` **FileSystem** 提供者所支援的磁片磁碟機中，您可以使用 `New-Item` 建立新的檔案或資料夾。 在 **登錄提供者所支援的磁片** 磁碟機中，您可以使用 `New-Item` 建立新的登錄機碼。 在 `Alias:` 磁片磁碟機中，您可以使用 `New-Item` 建立新的別名。

如需下列任何 Cmdlet 的詳細資訊，請輸入：

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a>Get-childitem Cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a>Content Cmdlet

- [Add-Content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Clear-Content](xref:Microsoft.PowerShell.Management.Clear-Content)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a>Item Cmdlet

- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Rename-Item](xref:Microsoft.PowerShell.Management.Rename-Item)
- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a>ItemProperty Cmdlet

- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Copy-ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Move-ItemProperty](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Rename-ItemProperty](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a>Location Cmdlet

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Pop-Location](xref:Microsoft.PowerShell.Management.Pop-Location)
- [Push-Location](xref:Microsoft.PowerShell.Management.Push-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a>路徑 Cmdlet

- [Join-Path](xref:Microsoft.PowerShell.Management.Join-Path)
- [Convert-Path](xref:Microsoft.PowerShell.Management.Convert-Path)
- [Split-Path](xref:Microsoft.PowerShell.Management.Split-Path)
- [Resolve-Path](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [Test-Path](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a>New-psdrive Cmdlet

- [Get-PSDrive](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [New-PSDrive](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [Remove-PSDrive](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a>PSProvider Cmdlet

- [Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a>查看提供者資料

提供者的主要優點是它會以熟悉且一致的方式公開其資料。 資料展示的模型是檔案系統磁片磁碟機。

此提供者可讓您查看、流覽和變更資料存放區中的專案，就好像它們是檔案系統中的資料一樣。 資料存放區是由它所支援的磁片磁碟機名稱存取。

磁片磁碟機會列在 Cmdlet 的預設顯示中 `Get-PSProvider` ，但您可以使用 Cmdlet 取得提供者磁片磁碟機的相關資訊 `Get-PSDrive` 。 例如，若要取得 Function：磁片磁碟機的所有屬性，請輸入：

```powershell
Get-PSDrive Function | Format-List *
```

您可以在提供者磁片磁碟機中查看和移動資料，就像在檔案系統磁片磁碟機上一樣。

若要查看提供者磁片磁碟機的內容，請使用 Get-Item 或 Get-ChildItem Cmdlet。 輸入磁片磁碟機名稱，後面接著冒號 (： ) 。 例如，若要查看 Alias：磁片磁碟機的內容，請輸入：

```powershell
Get-Item alias:
```

您可以在路徑中包含磁片磁碟機名稱，以從另一個磁片磁碟機查看及管理任何磁片磁碟機中的資料。 例如，若要從另一個磁片磁碟機查看 HKLM：磁片磁碟機中的 HKLM\Software 登錄機碼，請輸入：

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

若要開啟磁片磁碟機，請使用 Set-Location Cmdlet。 當您指定磁片磁碟機路徑時，請記住冒號。 例如，若要將您的位置變更為 Cert：磁片磁碟機的根目錄，請輸入：

```powershell
Set-Location cert:
```

然後，若要查看 Cert：磁片磁碟機的內容，請輸入：

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a>透過階層式資料移動

您可以透過提供者磁片磁碟機來移動，就像硬碟一樣。
如果資料是在專案內的專案階層中排列，請使用反斜線 (`\`) 來表示子專案。 請使用下列格式：

```
drive:\location\child-location\...
```

例如，若要將您的位置變更為 HKLM\Software 登錄機碼，請輸入 Set-Location 命令，例如：

```powershell
Set-Location HKLM:\SOFTWARE\
```

如果完整名稱中的任何元素包含空格，您必須將名稱括在雙引號中 (`"`) 。 下列範例顯示包含空格的完整路徑。

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

您也可以使用位置的相對參考。 點 (`.`) 代表目前的位置。 例如，如果您是在登錄機 `HKLM:\Software\Microsoft` 碼中，而您想要列出機碼中的登錄子機碼 `HKLM:\Software\Microsoft\PowerShell` ，請輸入下列命令：

```powershell
Get-ChildItem .\PowerShell
```

此外，雙點 (`..`) 指的是您目前位置正上方的目錄或容器。 您可以使用雙點 (`..`) 來流覽提供者階層。

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a>提供者首頁

提供者也有一個 **主** 位置。  此位置會由 `PSDrives` 提供者的所有支援共用。 您可以藉由查看提供者的 **Home** 屬性來加以取出。

```powershell
Get-PSProvider | Format-Table Name, Home
```

```Output
Name        Home
----        ----
Registry
Alias
Environment
FileSystem  C:\Users\username
Function
Variable
Certificate
```

**FileSystem** 提供者是唯一具有 **Home** 預設值的提供者。 它的值與相同 `$Home` 。 如需詳細資訊，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)。

您可以使用屬性，為目前的會話設定提供者的 **主** 目錄。

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

`~`字元可以用來代表提供者的主目錄。
如果提供者沒有設定 **主** 位置，您會看到錯誤。

```powershell
Cert:\> Set-Location ~
```

```Output
Set-Location : Home location for this provider isn't set. To set the home
location, call "(get-psprovider 'Certificate').Home = 'path'".
At line:1 char:1
+ Set-Location ~
+ ~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Set-Location],
                              PSInvalidOperationException
...
```

## <a name="finding-dynamic-parameters"></a>尋找動態參數

動態參數是由提供者新增至 Cmdlet 的 Cmdlet 參數。 只有當 Cmdlet 與新增的提供者搭配使用時，才能使用這些參數。

例如， `Cert:` 磁片磁碟機會將 **CodeSigningCert** 參數新增至 `Get-Item` 和 `Get-ChildItem` Cmdlet。 只有當您在 `Get-Item` `Get-ChildItem` 磁片磁碟機中使用或時，才能使用此參數 `Cert:` 。

如需提供者所支援動態參數的清單，請參閱提供者的說明檔。 輸入：

```
Get-Help <provider-name>
```

例如：

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a>瞭解提供者

雖然所有提供者資料都會出現在磁片磁碟機中，而且您可以使用相同的方法來移動它們，但相似性會停止。 提供者所公開的資料存放區，可以像 Active Directory 位置和 Microsoft Exchange Server 信箱一樣變化。

如需個別 PowerShell 提供者的相關資訊，請輸入：

```
Get-Help <ProviderName>
```

例如：

```powershell
Get-Help registry
```

如需提供者的說明主題清單，請輸入：

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a>另請參閱

[about_Locations](about_Locations.md)

[about_Path_Syntax](about_Path_Syntax.md)
