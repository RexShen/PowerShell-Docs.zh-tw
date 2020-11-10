---
description: 說明如何在 PowerShell 中使用 Cmdlet 和命令的替代名稱。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_aliases?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Aliases
ms.openlocfilehash: 827fceb9169882bf082c46e25c690f8a56eb5cba
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94386983"
---
# <a name="about-aliases"></a>關於別名

## <a name="short-description"></a>簡短描述
說明如何在 PowerShell 中使用 Cmdlet 和命令的替代名稱。

## <a name="long-description"></a>詳細描述

別名是 Cmdlet 或命令元素的替代名稱或昵稱，例如函數、腳本、檔案或可執行檔。 您可以使用別名來取代任何 PowerShell 命令中的命令名稱。

若要建立別名，請使用 New-Alias Cmdlet。 例如，下列命令會建立 Cmdlet 的「天然氣」別名 `Get-AuthenticodeSignature` ：

```powershell
New-Alias -Name gas -Value Get-AuthenticodeSignature
```

建立 Cmdlet 名稱的別名之後，您可以使用別名，而不是 Cmdlet 名稱。 例如，若要取得 SqlScript.ps1 檔案的 Authenticode 簽章，請輸入：

```powershell
Get-AuthenticodeSignature SqlScript.ps1
```

或者，輸入：

```powershell
gas SqlScript.ps1
```

如果您建立 "word" 做為 Microsoft Office Word 的別名，您可以輸入 "word" 而非下列內容：

```powershell
"C:\Program Files\Microsoft Office\Office11\Winword.exe"
```

## <a name="built-in-aliases"></a>內建別名

PowerShell 包含一組內建的別名，包括 Set-Location Cmdlet 的 "cd" 和 "chdir"，以及 Get-ChildItem Cmdlet 的 "ls" 和 "dir"。

若要取得電腦上的所有別名（包括內建的別名），請輸入：

```powershell
Get-Alias
```

## <a name="alias-cmdlets"></a>別名 CMDLET

PowerShell 包含下列適用于使用別名的 Cmdlet：

- `Get-Alias` -取得目前會話中的所有別名。
- `New-Alias` -建立新的別名。
- `Set-Alias` -建立或變更別名。
- `Export-Alias` -將一或多個別名匯出到檔案。
- `Import-Alias` -將別名檔案匯入 PowerShell。

如需 Cmdlet 的詳細資訊，請輸入：

```powershell
Get-Help <cmdlet-Name> -Detailed
```

例如，輸入：

```powershell
Get-Help Export-Alias -Detailed
```

## <a name="creating-an-alias"></a>建立別名

若要建立新的別名，請使用 New-Alias Cmdlet。 例如，若要建立 Get-help 的 "gh" 別名，請輸入：

```powershell
New-Alias -Name gh -Value Get-Help
```

您可以使用命令中的別名，就像使用完整 Cmdlet 名稱一樣，您也可以使用別名搭配參數。

例如，若要取得 Get-WmiObject Cmdlet 的詳細說明，請輸入：

```powershell
Get-Help Get-WmiObject -Detailed
```

或者，輸入：

```powershell
gh Get-WmiObject -Detailed
```

## <a name="saving-aliases"></a>正在儲存別名

您建立的別名只會儲存在目前的會話中。 若要在不同的會話中使用別名，請將別名新增至 PowerShell 設定檔。 或者，使用 Export-Alias Cmdlet 將別名儲存至檔案。

如需詳細資訊，請鍵入：

```powershell
Get-Help about_Profiles
```

## <a name="getting-aliases"></a>取得別名

若要取得目前會話中的所有別名，包括內建的別名、您 PowerShell 設定檔中的別名，以及您在目前會話中建立的別名，請輸入：

```powershell
Get-Alias
```

若要取得特定別名，請使用 Get-Alias Cmdlet 的 Name 參數。 例如，若要取得以 "p" 開頭的別名，請輸入：

```powershell
Get-Alias -Name p*
```

若要取得特定專案的別名，請使用定義參數。 例如，若要取得 Get-ChildItem Cmdlet 類型的別名：

```powershell
Get-Alias -Definition Get-ChildItem
```

### <a name="get-alias-output"></a>取得別名輸出

Get-Alias 只會傳回一種類型的物件，也就是 System.management.automation.aliasinfo 物件 (System.management.automation.aliasinfo) 。 不含連字號的別名名稱（例如 "cd"）會以下列格式顯示：

```powershell
Get-Alias ac
```

```Output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Alias           ac -> Add-Content
```

這可讓您快速且輕鬆地取得所需的資訊。

箭號型別名名稱格式不會用於含連字號的別名。 這些可能是 Cmdlet 和函式的慣用替代名稱，而不是一般的縮寫或昵稱，而且作者可能不會想要它們都能顯而易見。

## <a name="alternate-names-for-commands-with-parameters"></a>具有參數之命令的替代名稱

您可以將別名指派給 Cmdlet、腳本、函式或可執行檔。 您無法將別名指派給命令及其參數。 例如，您可以將別名指派給 `Get-Eventlog` Cmdlet，但是不能將別名指派給 `Get-Eventlog -LogName System` 命令。

您可以建立包含命令的函式。 若要建立函式，請輸入 "function" 這個字，後面接著函式的名稱。 輸入命令，並將它括在大括弧 ({}) 中。

例如，下列命令會建立 syslog 函數。 此函數代表 `Get-Eventlog -LogName System` 命令：

```powershell
function Get-SystemEventlog {Get-Eventlog -LogName System}
Set-Alias -Name syslog -Value Get-SystemEventlog
```

您現在可以輸入 "syslog"，而不是命令。 而且，您可以為新的函式建立別名。

如需函數的詳細資訊，請輸入：

```powershell
Get-Help about_Functions
```

## <a name="alias-objects"></a>別名物件

PowerShell 別名會以 System.management.automation.aliasinfo 類別實例的物件來表示。 如需此類型之物件的詳細資訊，請參閱 PowerShell SDK 中的 [System.management.automation.aliasinfo 類別][aliasinfo] 。

若要查看別名物件的屬性和方法，請取得別名。
然後，將它們輸送至 Get-Member Cmdlet。 例如：

```powershell
Get-Alias | Get-Member
```

若要查看特定別名（例如別名）的屬性值， `dir` 請取得別名。 然後，將它輸送至 Format-List Cmdlet。 例如，下列命令會取得 "dir" 別名。 接著，命令會以管道將別名傳送至 Format-List Cmdlet。 然後，此命令會使用 Format-List 的 Property 參數搭配萬用字元字元 (\*) 來顯示別名的所有屬性 `dir` 。 下列命令會執行下列工作：

```powershell
Get-Alias -Name dir | Format-List -Property *
```

## <a name="powershell-alias-provider"></a>PowerShell 別名提供者

PowerShell 包含別名提供者。 別名提供者可讓您在 PowerShell 中查看別名，就好像它們是在檔案系統磁片磁碟機上一樣。

別名提供者會公開 Alias：磁片磁碟機。 若要進入 Alias：磁片磁碟機，請輸入：

```powershell
Set-Location Alias:
```

若要查看磁片磁碟機的內容，請輸入：

```powershell
Get-ChildItem
```

若要從另一個 PowerShell 磁片磁碟機查看磁片磁碟機的內容，請使用磁片磁碟機名稱來開始路徑。 包含冒號 (： ) 。 例如：

```powershell
Get-ChildItem -Path Alias:
```

若要取得特定別名的相關資訊，請輸入磁片磁碟機名稱和別名名稱。 或者，輸入名稱模式。 例如，若要取得以 "p" 開頭的所有別名，請輸入：

```powershell
Get-ChildItem -Path Alias:p*
```

如需 PowerShell 別名提供者的詳細資訊，請輸入：

```powershell
Get-Help Alias
```

## <a name="see-also"></a>另請參閱

- [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias)
- [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [Set-Alias](xref:Microsoft.PowerShell.Utility.Set-Alias)
- [Export-Alias](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [Import-Alias](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)
- [Get-PSDrive](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [about_functions](about_functions.md)
- [about_profiles](about_profiles.md)
- [about_providers](about_providers.md)

<!-- External links -->
[aliasinfo]: /dotnet/api/system.management.automation.aliasinfo
