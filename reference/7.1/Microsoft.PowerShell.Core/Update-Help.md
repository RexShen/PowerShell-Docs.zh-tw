---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: d2b80640a5cdc985d34e39fe608950ea5f4dfe2d
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "93205856"
---
# Update-Help

## 概要
下載最新的說明檔並安裝於電腦上。

## SYNTAX

### 路徑 (預設值)

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### LiteralPath

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`Update-Help`Cmdlet 會下載適用于 PowerShell 模組的最新說明檔案，並將其安裝在您的電腦上。 您不需要重新開機 PowerShell 來使變更生效。 您可以使用 `Get-Help` Cmdlet 立即查看新的說明檔。

`Update-Help` 檢查電腦上的說明檔版本。 如果您沒有模組的說明檔，或您的說明檔已過期，則會 `Update-Help` 下載最新的說明檔。 您可以從網際網路或檔案共用下載和安裝說明檔。

如果沒有參數， `Update-Help` 則會更新會話中模組的說明檔，以及所有支援「可更新的說明」的已安裝模組。 包含在目前會話中安裝但未載入的模組。 PowerShell 模組會儲存在環境變數中所列的位置 `$env:PSModulePath` 。 如需詳細資訊，請參閱 [about_Updatable_Help](./About/about_Updatable_Help.md)。

您可以使用 **Module** 參數來更新特定模組的說明檔。 使用 **UICulture** 參數以多種語言和地區設定下載說明檔。

您也可以 `Update-Help` 在未連線到網際網路的電腦上使用。 首先，使用 `Save-Help` Cmdlet 從網際網路下載說明檔，並將其儲存在未連線至網際網路之系統可存取的共用資料夾中。 然後使用的 **SourcePath** 參數 `Update-Help` ，從共用下載已更新的說明檔，並安裝在電腦上。

您可以藉由將指令程式新增 `Update-Help` 至 PowerShell 設定檔，將說明更新自動化。 依預設， `Update-Help` 每一部電腦上只會執行一次一次。 若要覆寫每天一次的限制，請使用 **Force** 參數。

`Update-Help`Cmdlet 是在 Windows PowerShell 3.0 中引進。

> [!IMPORTANT]
> `Update-Help` 需要 PowerShell 6.0 和以下的系統管理許可權。
> PowerShell 6.1 和更新版本會將預設 **範圍** 設定為 `CurrentUser` 。
> 在 PowerShell 6.1 之前，無法使用 **範圍** 參數。
>
> 您必須是電腦上 Administrators 群組的成員，才能更新 PowerShell Core 模組的說明檔。
>
> 若要下載或更新 PowerShell 安裝目錄中模組的說明檔 (`$PSHOME\Modules`) （包括 PowerShell Core 模組），請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。
> 例如： `Start-Process pwsh.exe -Verb RunAs` 。

## 範例

### 範例1：更新所有模組的說明檔

指令 `Update-Help` 程式會更新支援「可更新的說明」之已安裝模組的說明檔。 系統會在作業系統中設定使用者介面 (UI) 文化特性語言。

```powershell
Update-Help
```

### 範例2：更新指定模組的說明檔

此 `Update-Help` Cmdlet 只會更新以 **Microsoft. PowerShell** 開頭之模組名稱的說明檔。

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### 範例3：更新不同語言的說明檔

此 `Update-Help` Cmdlet 會為所有模組更新日文 (ja-jp) 和英文 (en-us) 說明檔。

如果模組未提供指定 UI 文化特性的說明檔，則會顯示模組和 UI 文化特性的錯誤訊息。 在此範例中，錯誤訊息會指出找不 **到模組的** **ja-jp** 說明檔。

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### 範例4：從檔案共用更新多部電腦上的說明檔

在此範例中，會從網際網路下載已更新的說明檔，並將其儲存在檔案共用中。 需要擁有存取檔案共用和安裝更新之許可權的使用者認證。 使用檔案共用時，可以更新位於防火牆後方或未連線到網際網路的電腦。

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

此 `Save-Help` 命令會為所有支援「可更新的說明」的模組下載最新的說明檔。
**DestinationPath** 參數會將檔案儲存在檔案 `\\Server01\Share\PSHelp` 共用中。 **Credential** 參數指定有權存取檔案共用的使用者。

此 `Invoke-Command` Cmdlet 會 `Update-Help` 在多部電腦上執行遠端命令。 **ComputerName** 參數會從 **Servers.txt** 檔案取得遠端電腦的清單。 **ScriptBlock** 參數會執行 `Update-Help` 命令，並使用 **SourcePath** 參數指定包含已更新說明檔的檔案共用。 **Credential** 參數會指定可以存取檔案共用並執行遠端命令的使用者 `Update-Help` 。

### 範例5：取得已更新說明檔的清單

此 `Update-Help` Cmdlet 會更新指定模組的說明。 此 Cmdlet 會使用 **Verbose** 一般參數來顯示已更新的說明檔清單。 您可以使用 [ **詳細** 資訊] 來查看特定模組的所有說明檔或說明檔的輸出。

如果沒有 **Verbose** 參數，則 `Update-Help` 不會顯示命令的結果。 **詳細** 資訊參數輸出適用于驗證說明檔是否已更新，或是否已安裝最新版本。

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### 範例6：尋找支援「可更新的說明」的模組

此範例會列出支援「可更新的說明」的模組。 此命令會使用模組的 **HelpInfoUri** 屬性，識別支援「可更新的說明」的模組。 **HelpInfoUri** 屬性包含在執行 Cmdlet 時重新導向的位址 `Update-Help` 。

```powershell
Get-Module -ListAvailable | Where-Object -Property HelpInfoUri
```

```output
   Directory: C:\program files\powershell\6\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   6.1.0.0    CimCmdlets                          Core      {Get-CimAssociatedInstance... }
Manifest   1.2.2.0    Microsoft.PowerShell.Archive        Desk      {Compress-Archive... }
Manifest   6.1.0.0    Microsoft.PowerShell.Diagnostics    Core      {Get-WinEvent, New-WinEvent}

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, ... }
Script     1.0.0.0    AssignedAccess                      Core,Desk {Clear-AssignedAccess, ... }
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, ... }
```

### 範例7：清查已更新的說明檔

在此範例中，腳本會 `Get-UpdateHelpVersion.ps1` 為每個模組和其版本號碼建立可更新說明檔的清查。

腳本會使用模組的 **HelpInfoUri** 屬性，識別支援「可更新的說明」的模組。 針對支援「可更新的說明」的模組，腳本會尋找並剖析說明資訊檔 ( * helpinfo.xml) 以尋找最新的版本號碼。

腳本會使用 **PSCustomObject** 類別和雜湊表來建立自訂輸出物件。

```powershell
# Get-UpdateHelpVersion.ps1
Param(
    [parameter(Mandatory=$False)]
    [String[]]
    $Module
)
$HelpInfoNamespace = @{helpInfo='http://schemas.microsoft.com/powershell/help/2010/05'}

if ($Module) { $Modules = Get-Module $Module -ListAvailable | where {$_.HelpInfoUri} }
else { $Modules = Get-Module -ListAvailable | where {$_.HelpInfoUri} }

foreach ($mModule in $Modules)
{
    $mDir = $mModule.ModuleBase

    if (Test-Path $mdir\*helpinfo.xml)
    {
        $mName=$mModule.Name
        $mNodes = dir $mdir\*helpinfo.xml -ErrorAction SilentlyContinue |
            Select-Xml -Namespace $HelpInfoNamespace -XPath "//helpInfo:UICulture"
        foreach ($mNode in $mNodes)
        {
            $mCulture=$mNode.Node.UICultureName
            $mVer=$mNode.Node.UICultureVersion

            [PSCustomObject]@{"ModuleName"=$mName; "Culture"=$mCulture; "Version"=$mVer}
        }
    }
}
```

```Output
ModuleName                              Culture                                 Version
----------                              -------                                 -------
ActiveDirectory                         en-US                                   3.0.0.0
ADCSAdministration                      en-US                                   3.0.0.0
ADCSDeployment                          en-US                                   3.0.0.0
ADDSDeployment                          en-US                                   3.0.0.0
ADFS                                    en-US                                   3.0.0.0
```

## PARAMETERS

### -Credential

指定有權存取 **SourcePath** 所指定之檔案系統位置的使用者認證。 只有當命令中使用 **SourcePath** 或 **LiteralPath** 參數時，此參數才有效。

**Credential** 參數可讓您 `Update-Help` 在遠端電腦上執行具有 **SourcePath** 參數的命令。 藉由提供明確的認證，您可以在遠端電腦上執行命令，並存取第三部電腦上的檔案共用，而不會遇到拒絕存取錯誤，或使用 CredSSP 驗證來委派認證。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指出此 Cmdlet 不會遵循每天一次的限制、略過版本檢查，以及下載超過 1 GB 限制的檔案。

如果沒有這個參數，則 `Update-Help` 每24小時內只會執行一次。 每個模組的下載限制為 1 GB 的未壓縮內容，而且說明檔只有在比電腦上的現有檔案更新時才會安裝。

每日一次的限制可保護裝載說明檔的伺服器，並讓您能夠將 `Update-Help` 命令新增至 PowerShell 設定檔，而不會產生重複連線或下載的資源成本。

若要不使用 **Force** 參數來更新多重 UI 文化特性中的模組說明，請在同一個命令中包含所有 UI 文化特性，例如：

`Update-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedModule

指定以 **ModuleSpecification** 物件形式指定之名稱的模組。
這些模組會在 [ModuleSpecification (雜湊表) ](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)的「備註」一節中描述。

例如， **FullyQualifiedModule** 參數會接受以下列格式指定的模組名稱：

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

或

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。

您無法在與 **模組** 參數相同的命令中指定 **FullyQualifiedModule** 參數。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

指定已更新說明檔的資料夾，而不是從網際網路下載。 如果您已使用此 Cmdlet 將說明檔下載至目錄，請使用此參數或 **SourcePath** `Save-Help` 。

您可以將目錄物件（例如從 `Get-Item` 或 `Get-ChildItem` Cmdlet）管線至 `Update-Help` 。

與 **SourcePath** 的值不同， **LiteralPath** 的值會完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Module

更新指定模組的說明。 在以逗號分隔的清單中輸入一或多個模組名稱或名稱模式，或指定每一行列出一個模組名稱的檔案。 允許使用萬用字元。 您可以從 Cmdlet 將模組管線 `Get-Module` 到 `Update-Help` Cmdlet。

您所指定的模組必須安裝在電腦上，但不需要將它們匯入到目前的會話。 您可以指定會話中的任何模組，或安裝在環境變數所列位置中的任何模組 `$env:PSModulePath` 。

`*`所有) 的值 (會嘗試更新電腦上所安裝之所有模組的說明。
包含不支援「可更新的說明」的模組。 當命令遇到不支援「可更新的說明」的模組時，這個值可能會產生錯誤。 請改為執行 `Update-Help` 但不包含參數。

Cmdlet 的 **module** 參數 `Update-Help` 不接受模組檔案或模組資訊清單檔案的完整路徑。 若要更新不在某個位置的模組說明 `$env:PSModulePath` ，請在執行命令之前將模組匯入到目前的會話 `Update-Help` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Recurse

在指定的目錄中執行說明檔的遞迴搜尋。 只有當命令使用 **SourcePath** 參數時，此參數才有效。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scope

指定說明更新的系統範圍。 在 **AllUsers** 範圍更新需要 Windows 系統的系統管理許可權。 `-Scope`參數是在 PowerShell Core 版本6.1 中引進。

**CurrentUser** 是 PowerShell 6.1 和更新版本中說明檔的預設範圍。 您可以指定 **AllUsers** 來安裝或更新所有使用者的說明。 `sudo`需要有 Unix 系統許可權，才能更新所有使用者的說明。 例如：`sudo pwsh -c Update-Help`

可接受的值如下：

- CurrentUser
- AllUsers

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourcePath

指定可取得已更新說明檔的檔系統資料夾 `Update-Help` ，而不是從網際網路下載。 輸入資料夾的路徑。 請勿指定檔案名或副檔名。 您可以將資料夾（例如）從 `Get-Item` 或 `Get-ChildItem` Cmdlet 管線至 `Update-Help` 。

根據預設，會 `Update-Help` 從網際網路下載已更新的說明檔。 當 **SourcePath** 您使用此 `Save-Help` Cmdlet 將已更新的說明檔下載至目錄時，請使用 SourcePath。

若要指定 **SourcePath** 的預設值，請移至 **群組原則** 、 **電腦** 設定，並 **設定 update-help 的預設來源路徑** 。 此群組原則設定可防止使用者使用 `Update-Help` 從網際網路下載說明檔。
如需詳細資訊，請參閱 [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md)。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UICulture

指定 `Update-Help` 用來取得已更新說明檔的 UI 文化特性值。 輸入一或多個語言代碼（例如 **es** ）、包含文化特性物件的變數，或可取得文化特性物件的命令，例如 `Get-Culture` 或 `Get-UICulture` 命令。 不允許使用萬用字元，且您無法提交部分語言代碼，例如 **de** 。

根據預設，會 `Update-Help` 取得為作業系統設定的 UI 文化特性中的說明檔。 如果您指定 **UICulture** 參數，只會尋找 `Update-Help` 所指定 UI 文化特性的說明。

> [!NOTE]
> Ubuntu 18.04 已將預設地區設定變更為 `C.UTF.8` ，這不是可辨識的 UI 文化特性。 `Update-Help` 除非您使用此參數搭配支援的地區設定（例如），否則無法以無訊息方式下載說明 `en-US` 。 這可能會發生在任何使用不支援值的平臺上。

只有當模組有提供所指定 UI 文化特性的說明檔時，使用 **UICulture** 參數的命令才會成功。 如果命令因為不支援指定的 UI 文化特性而失敗，則會顯示錯誤訊息。

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredentials

表示 `Update-Help` 使用目前使用者的認證執行命令，包括網際網路下載。 根據預設，該命令執行時不會使用明確宣告的認證。

只有當 web 下載使用 NT LAN Manager (NTLM) 、negotiate 或 Kerberos 驗證時，此參數才有效。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 不會執行此 Cmdlet。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### DirectoryInfo

您可以使用管線將目錄路徑傳送至 `Update-Help` 。

### System.Management.Automation.PSModuleInfo

您可以使用管線將模組物件從 `Get-Module` Cmdlet 傳送至 `Update-Help` 。

## 輸出

### 無

`Update-Help` 不會產生任何輸出。

## 注意

若要更新 PowerShell Core 模組的說明，其中包含與 PowerShell 一起安裝的命令，或目錄中的任何模組 `$PSHOME\Modules` ，請啟動 PowerShell 並使用 [以 **系統管理員身分執行** ] 選項。

只有電腦上 Administrators 群組的成員可以更新 PowerShell Core 模組的說明、隨 PowerShell 一起安裝的命令，以及資料夾中的模組 `$PSHOME\Modules` 。 如果您沒有更新說明檔的許可權，您可以在線上閱讀說明檔。 例如： `Get-Help Update-Help -Online` 。

模組是可更新的說明之最小單位。 您無法更新特定 Cmdlet 的說明。 若要尋找包含特定 Cmdlet 的模組，請使用 Cmdlet 的 **ModuleName** 屬性 `Get-Command` ，例如 `(Get-Command Update-Help).ModuleName` 。

因為說明檔安裝在模組目錄中，此 `Update-Help` Cmdlet 只能針對安裝在電腦上的模組安裝已更新的說明檔。 不過，此 `Save-Help` Cmdlet 可以儲存未安裝在電腦上之模組的說明。

如果找 `Update-Help` 不到模組的已更新說明檔，或找不到指定語言的已更新說明檔，它會繼續以無訊息模式繼續，而不會顯示錯誤訊息。 若要查看狀態和進度的詳細資訊，請使用 **Verbose** 參數。

`Update-Help`Cmdlet 是在 Windows PowerShell 3.0 中引進。 不適用於舊版 PowerShell。 在同時具有 Windows PowerShell 2.0 和 Windows PowerShell 3.0 的電腦上，請使用 `Update-Help` Windows PowerShell 3.0 會話中的 Cmdlet 來下載和更新說明檔。 Windows PowerShell 2.0 和 Windows PowerShell 3.0 都提供說明檔。

`Update-Help`和 `Save-Help` Cmdlet 使用下列埠下載說明檔：適用于 HTTP 的埠80和 HTTPS 的埠443。

`Update-Help` 支援所有模組和 PowerShell Core 嵌入式管理單元。它不支援任何其他嵌入式管理單元。

若要更新未列在環境變數中之位置的模組說明 `$env:PSModulePath` ，請將模組匯入目前的會話，然後執行 `Update-Help` 命令。 `Update-Help`在不使用參數的情況下執行，或使用 **module** 參數指定模組名稱。 和 Cmdlet 的 **module** 參數 `Update-Help` `Save-Help` 不接受模組檔案或模組資訊清單檔案的完整路徑。

任何模組都能支援「可更新的說明」。 如需在您撰寫的模組中支援「可更新的說明」的指示，請參閱 [支援可更新](/powershell/scripting/developer/module/supporting-updatable-help)的說明。

`Update-Help` `Save-Help` Windows 預先安裝環境 (Windows PE) 不支援和 Cmdlet。

## 相關連結

[Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)

[Get-Help](Get-Help.md)

[Get-Module](Get-Module.md)

[Get-UICulture](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[Start-Job](Start-Job.md)

[Save-Help](Save-Help.md)
