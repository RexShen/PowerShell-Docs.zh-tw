---
description: 登錄
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 登錄提供者
ms.openlocfilehash: efed68c42d46d5a44864af6b8892413c680c6b4e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206775"
---
# <a name="registry-provider"></a>登錄提供者

## <a name="provider-name"></a>提供者名稱

登錄

## <a name="drives"></a>磁碟機

`HKLM:`, `HKCU:`

## <a name="capabilities"></a>功能

**ShouldProcess** 、 **UseTransactions**

## <a name="short-description"></a>簡短描述

提供 PowerShell 中登錄機碼、專案和值的存取權。

## <a name="detailed-description"></a>詳細描述

PowerShell 登錄 **提供者** 可讓您在 powershell 中取得、新增、變更、清除和刪除登錄機碼、專案和值。

登錄 **磁片磁碟機** 是階層式命名空間，其中包含電腦上的登錄機碼和子機碼。 登錄項目和值不是該階層的元件。 相反地，它們是每個機碼的屬性。

登錄 **提供者** 支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Get-Acl](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-Acl](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a>此提供者公開的類型

登錄機碼會以 [node.js 類別的](/dotnet/api/microsoft.win32.registrykey) 實例來表示。 登錄專案會以 [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) 類別的實例來表示。

## <a name="navigating-the-registry-drives"></a>流覽登錄磁片磁碟機

登錄 **提供者會將其** 資料存放區公開為兩個預設磁片磁碟機。 登錄位置 HKEY_LOCAL_MACHINE 會對應到 `HKLM:` 磁片磁碟機，HKEY_CURRENT_USER 對應到 `HKCU:` 磁片磁碟機。 若要使用登錄，您可以使用下列命令將位置變更為 `HKLM:` 磁片磁碟機。

```powershell
Set-Location HKLM:
```

若要返回檔案系統磁碟機，請輸入磁碟機名稱。 例如，輸入：

```powershell
Set-Location C:
```

您也可以從任何其他 PowerShell 磁片磁碟機使用 **登錄提供者** 。 若要參考另一個位置的登錄機碼，請使用路徑中的磁片磁碟機名稱 (`HKLM:` ， `HKCU:`) 。 使用反斜線 (\\) 或正斜線 (/) 來表示登錄磁片磁碟機的層 **Registry** 級。

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。 和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名，而且 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。

最後一個範例會示範另一個路徑語法，您可以用來流覽 **登錄提供者** 。 此語法會使用提供者名稱，後面加上兩個冒號 `::` 。 此語法可讓您使用完整的 HIVE 名稱，而不是對應的磁片磁碟機名稱 `HKLM` 。

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a>顯示登錄機碼的內容

登錄會分割成機碼、子機碼和專案。 如需登錄結構的詳細資訊，請參閱登錄 [結構](/windows/desktop/sysinfo/structure-of-the-registry)。

**在登錄磁片磁碟機** 中，每個金鑰都是一個容器。 索引鍵可以包含任意數目的索引鍵。 具有父機碼的登錄機碼稱為子機碼。 您可以使用 `Get-ChildItem` 來查看登錄機碼，並 `Set-Location` 流覽至金鑰路徑。

登錄值是登錄機碼的屬性。 **在登錄磁片磁碟機** 中，它們稱為 **專案屬性** 。 登錄機碼可以同時具有子系索引鍵和專案屬性。

在此範例中， `Get-Item` 會顯示和之間的差異 `Get-ChildItem` 。 當您在「多工緩衝處理器」 `Get-Item` 登錄機碼上使用時，可以看到它的屬性。

```
PS C:\ > Get-Item -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services


Name        Property
----        --------
Spooler     DependOnService    : {RPCSS, http}
            Description        : @%systemroot%\system32\spoolsv.exe,-2
            DisplayName        : @%systemroot%\system32\spoolsv.exe,-1
            ErrorControl       : 1
            FailureActions     : {16, 14, 0, 0...}
            Group              : SpoolerGroup
            ImagePath          : C:\WINDOWS\System32\spoolsv.exe
            ObjectName         : LocalSystem
            RequiredPrivileges : {SeTcbPrivilege, SeImpersonatePrivilege, ...
            ServiceSidType     : 1
            Start              : 2
            Type               : 27
```

每個登錄機碼也可以有子機碼。 當您使用 `Get-Item` 登錄機碼時，不會顯示子機碼。 此 Cmdlet 會顯示「多工緩衝處理器」索引 `Get-ChildItem` 鍵的子專案，包括每個子機碼的屬性。 使用時，不會顯示父索引鍵屬性 `Get-ChildItem` 。

```
PS C:\> Get-ChildItem -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler


Name             Property
----             --------
Performance      Close           : PerfClose
                 Collect         : PerfCollect
                 Collect Timeout : 2000
                 Library         : C:\Windows\System32\winspool.drv
                 Object List     : 1450
                 Open            : PerfOpen
                 Open Timeout    : 4000
Security         Security : {1, 0, 20, 128...}
```

`Get-Item`Cmdlet 也可以在目前的位置上使用。 下列範例會流覽至「多工緩衝處理器」登錄機碼，並取得專案屬性。
點 `.` 用來表示目前的位置。

```
PS C:\> cd HKLM:\System\CurrentControlSet\Services\Spooler
PS HKLM:\SYSTEM\CurrentControlSet\Services\Spooler> Get-Item .

    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services

Name             Property
----             --------
Spooler          DependOnService    : {RPCSS, http}
                 Description        : @%systemroot%\system32\spoolsv.exe,-2
...
```

如需本節所涵蓋之 Cmdlet 的詳細資訊，請參閱下列文章。

-[取得專案](xref:Microsoft.PowerShell.Management.Get-Item) 
-[Get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

## <a name="viewing-registry-key-values"></a>查看登錄機碼值

登錄機碼值會儲存為每個登錄機碼的屬性。 此 `Get-ItemProperty` Cmdlet 會使用您指定的名稱來查看登錄機碼屬性。 結果是包含您指定之屬性的 **PSCustomObject** 。

下列範例會使用 `Get-ItemProperty` Cmdlet 來查看所有屬性。 將產生的物件儲存在變數中，可讓您存取所需的屬性值。

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

指定參數的值 `-Name` 會選取您指定的屬性，並傳回 **PSCustomObject** 。  下列範例顯示當您使用參數時，輸出中的差異 `-Name` 。

```
PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem

BUILD                      : 17134.1
Installation Directory     : C:\WINDOWS\system32\WBEM
MOF Self-Install Directory : C:\WINDOWS\system32\WBEM\MOF
PSPath                     : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName                : Wbem
PSDrive                    : HKLM
PSProvider                 : Microsoft.PowerShell.Core\Registry

PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD

BUILD        : 17134.1
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName  : Wbem
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
```

從 PowerShell 5.0 開始，此 `Get-ItemPropertyValue` Cmdlet 只會傳回您指定的屬性值。

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

如需本節中所使用之 Cmdlet 的詳細資訊，請參閱下列文章。

- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Get-ItemPropertyValue](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a>變更登錄機碼值

此 `Set-ItemProperty` Cmdlet 會設定登錄機碼的屬性。 下列範例會使用 `Set-ItemProperty` 將多工緩衝處理器服務啟動類型變更為手動。 此範例會使用 Cmdlet 將 **StartType** 變更回 *自動* `Set-Service` 。

```
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler Automatic

PS C:\> $path = "HKLM:\SYSTEM\CurrentControlSet\Services\Spooler\"
PS C:\> Set-ItemProperty -Path $path -Name Start -Value 3
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler    Manual

PS C:\> Set-Service -Name Spooler -StartupType Automatic
```

每個登錄機碼都有 *預設* 值。 您可以使用或來變更登錄機碼的 *預設* 值 `Set-Item` `Set-ItemProperty` 。

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

如需本節中所使用之 Cmdlet 的詳細資訊，請參閱下列文章。

- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a>建立登錄機碼和值

`New-Item`Cmdlet 會以您提供的名稱建立登錄機碼。
您也可以使用函式 `mkdir` ，它會 `New-Item` 在內部呼叫 Cmdlet。

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

您可以使用 `New-ItemProperty` Cmdlet，在您指定的登錄機碼中建立值。 下列範例會在 ContosoCompany 登錄機碼上建立新的 DWORD 值。

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> 請參閱本文中的「動態參數」一節，以瞭解其他允許的類型值。

如需詳細的 Cmdlet 用法，請參閱 [ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty)。

## <a name="copying-registry-keys-and-values"></a>複製登錄機碼和值

**在登錄提供者** 中，使用 `Copy-Item` Cmdlet 複製登錄機碼和值。 使用 `Copy-ItemProperty` Cmdlet 只複製登錄值。
下列命令會將 "Contoso" 登錄機碼及其屬性複製到指定的位置 "HKLM： \ Software\Fabrikam"。

`Copy-Item` 建立目的地金鑰（如果不存在）。 如果目的地金鑰存在，會 `Copy-Item` 建立來源金鑰的複本做為子專案， (子機碼) 的子專案。

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

下列命令會使用 `Copy-ItemProperty` Cmdlet，將 "Server" 值從 "Contoso" 機碼複製到 "Fabrikam" 機碼。

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

如需本節中所使用之 Cmdlet 的詳細資訊，請參閱下列文章。

- [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item)
- [Copy-ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a>移動登錄機碼和值

`Move-Item`和 `Move-ItemProperty` Cmdlet 的行為就像其「複製」的對應專案。 如果目的地存在，請 `Move-Item` 將來源金鑰移至目的地機碼下方。 如果目的地機碼不存在，則會將來源索引鍵移至目的地路徑。

下列命令會將 "Contoso" 機碼移至 "HKLM： \ SOFTWARE\Fabrikam" 路徑。

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

此命令會將所有屬性從 "HKLM： \ SOFTWARE\ContosoCompany" 移至 "HKLM： \ SOFTWARE\Fabrikam"。

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

如需本節中所使用之 Cmdlet 的詳細資訊，請參閱下列文章。

- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [Move-ItemProperty](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a>重新命名登錄機碼和值

您可以重新命名登錄機碼和值，就像是檔案和資料夾一樣。
`Rename-Item` 重新命名登錄機碼，同時重新 `Rename-ItemProperty` 命名登錄值。

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a>變更安全描述項

您可以使用和 Cmdlet 來限制對登錄機碼的存取 `Get-Acl` `Set-Acl` 。 下列範例會將具有完整控制權的新使用者新增至 "HKLM： \ SOFTWARE\Contoso" 登錄機碼。

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

如需更多範例和 Cmdlet 使用方式的詳細資料，請參閱下列文章。

- [Get-Acl](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-Acl](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a>移除和清除登錄機碼和值

您可以使用 [ **移除專案** ] 移除包含的專案，但如果專案包含任何其他專案，系統會提示您確認移除。 下列範例會嘗試刪除機碼 "HKLM： \ SOFTWARE\Contoso"。

```
PS C:\> dir HKLM:\SOFTWARE\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Contoso

Name                           Property
----                           --------
ChildKey

PS C:\> Remove-Item -Path HKLM:\SOFTWARE\Contoso

Confirm
The item at HKLM:\SOFTWARE\Contoso has children and the -Recurse
parameter was not specified. If you continue, all children will be removed
with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

若要在不提示的情況下刪除包含的專案，請指定 `-Recurse` 參數。

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

如果您想要移除 "HKLM： \ SOFTWARE\Contoso" 中的所有專案，而不是 "HKLM： \ SOFTWARE\Contoso" 本身，請使用尾端反斜線， `\` 後面接著萬用字元。

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

此命令會刪除 "HKLM： \ SOFTWARE\Contoso" 登錄機碼中的 "ContosoTest" 登錄值。

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

`Clear-Item` 清除機碼的所有登錄值。 下列範例會清除 "HKLM： \ SOFTWARE\Contoso" 登錄機碼中的所有值。 若只要清除特定的屬性，請使用 `Clear-ItemProperty` 。

```
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name           Property
----           --------
Contoso        Server     : {a, b, c}
               HereString : {This is text which contains
               newlines. It also contains "quoted" strings}
               (default)  : 1

PS HKLM:\SOFTWARE\> Clear-Item .\Contoso\
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
Contoso
```

如需更多範例和 Cmdlet 使用方式的詳細資料，請參閱下列文章。

- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a>動態參數

動態參數是 PowerShell 提供者新增的 Cmdlet 參數，而且只有在提供者啟用的磁片磁碟機中使用 Cmdlet 時才能使用。

### <a name="type-microsoftwin32registryvaluekind"></a>輸入 <>microsoft.win32.registryvaluekind>

建立或變更登錄值的資料類型。 預設值為 `String` (REG_SZ) 。

這個參數是設計來在 [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) Cmdlet 上運作的。 它也可以在登錄磁碟機中的 [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) Cmdlet 上使用，但不會有任何作用。

|值 | 描述 |
| ---- | ----------- |
| `String` | 指定以 null 終止的字串。 相當於 REG_SZ。 |
| `ExpandString` | 指定包含未展開的 null 終止字串 |
|                | 環境變數的參考，這些變數是在 |
|                | 此值為已抓取。 相當於 REG_EXPAND_SZ。 |
| `Binary` | 指定任意形式的二進位資料。 相當於 REG_BINARY。 |
| `DWord` | 指定 32 位元的二進位數字。 相當於 REG_DWORD。 |
| `MultiString` | 指定以 null 終止的字串陣列，由 |
|               | 兩個 null 字元。 相當於 REG_MULTI_SZ。 |
| `QWord` | 指定 64 位元的二進位數字。 相當於 REG_QWORD。 |
| `Unknown` | 指出不支援的登錄資料類型，例如 |
|           | REG_RESOURCE_LIST。 |

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a>使用管線

提供者 Cmdlet 接受管線輸入。 您可以使用管線將提供者資料從一個 Cmdlet 傳送到另一個提供者 Cmdlet，以簡化工作。 若要深入瞭解如何搭配使用管線與提供者 Cmdlet，請參閱本文中提供的 Cmdlet 參考。

## <a name="getting-help"></a>取得說明

從 Windows PowerShell 3.0 開始，您可以取得提供者 Cmdlet 的自訂說明主題，這些主題說明這些 Cmdlet 在檔案系統磁碟機中的行為方式。

若要取得針對檔案系統磁片磁碟機自訂的說明主題，請 `Get-Help` 在檔案系統磁片磁碟機中執行命令，或使用 **Path** 參數來指定檔案系統磁片磁碟機。

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a>另請參閱

 [about_Providers](../About/about_Providers.md)
