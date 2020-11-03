---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionConfiguration
ms.openlocfilehash: 4cb9c5537673642b74bd8ae03e9f66caf1e873b1
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205507"
---
# Get-PSSessionConfiguration

## 概要
取得電腦上已登錄的工作階段設定。

## SYNTAX

```
Get-PSSessionConfiguration [[-Name] <String[]>] [-Force] [<CommonParameters>]
```

## DESCRIPTION

此 `Get-PSSessionConfiguration` Cmdlet 會取得已在本機電腦上註冊的會話設定。 這是一個進階的 Cmdlet，專門設計給系統管理員用於管理其使用者的自訂工作階段設定。

從 PowerShell 3.0 開始，您可以使用會話設定 ( .pssc) 檔來定義會話設定的屬性。 此功能可讓您不必撰寫電腦程式，就能建立自訂且受限制的工作階段。 如需有關工作階段設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。

此外，從 PowerShell 3.0 開始，已將新的附注屬性新增至傳回的會話設定物件 `Get-PSSessionConfiguration` 。 這些屬性讓使用者和工作階段設定作者，能夠更輕鬆地檢查和比較工作階段設定。

若要建立並註冊會話設定，請使用 `Register-PSSessionConfiguration` Cmdlet。
如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。

## 範例

### 範例 1-取得本機電腦上的會話設定

```powershell
Get-PSSessionConfiguration
```

### 範例 2-取得兩個預設會話設定

命令使用的 **Name** 參數 `Get-PSSessionConfiguration` ，只取得名稱開頭為 "Microsoft" 的會話設定。

```powershell
Get-PSSessionConfiguration -Name Microsoft*
```

```Output
Name                      PSVersion  StartupScript        Permission
----                      ---------  -------------        ----------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll...
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll...
```

### 範例 3-取得會話設定的屬性和值

此範例示範使用工作階段設定檔建立工作階段設定的屬性和屬性值。

```powershell
Get-PSSessionConfiguration -Name Full  | Format-List -Property *
```

```Output
Copyright                     : (c) 2011 User01. All rights reserved.
AliasDefinitions              : {System.Collections.Hashtable}
SessionType                   : Default
CompanyName                   : Unknown
GUID                          : 1e9cb265-dae0-4bd3-89a9-8338a47698a1
Author                        : User01
ExecutionPolicy               : Restricted
SchemaVersion                 : 1.0.0.0
LanguageMode                  : FullLanguage
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/Full
MaxConcurrentCommandsPerShell : 1500
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 10
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
configfilepath                : C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 300
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 1
Name                          : Full
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 25
Enabled                       : True
MaxShellsPerUser              : 30
Permission                    :
```

此範例會使用 `Get-PSSessionConfiguration` Cmdlet 來取得完整的會話設定。 管線運算子會將完整會話設定傳送至 `Format-List` Cmdlet。 **Property** 參數的值為 `*` (all) 會指示 `Format-List` 在清單中顯示物件的所有屬性和值。

輸出中會包含有用的資訊，包括會話設定的作者、會話類型、語言模式，以及使用此會話設定建立之會話的執行原則、會話配額和會話設定檔的完整路徑。

此工作階段設定的檢視可用於包含工作階段設定檔的工作階段。
如需有關工作階段設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。

### 範例 4-查看會話設定的另一種方式

此範例會使用 `Get-ChildItem` `dir` WSMan： provider 磁片磁碟機中的 Cmdlet (別名) 來查看外掛程式節點的內容。 這是另一個檢視電腦上工作階段設定的方法。

```powershell
dir wsman:\localhost\plugin
```

```Output
Type            Keys                                Name
----            ----                                ----
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=WMI Provider}                 WMI Provider
```

**外掛程式** 節點包含 **ContainerElement** 物件 (WSManConfigContainerElement) ，代表已註冊的 PowerShell 會話設定，以及適用于 ws-management 的其他外掛程式。

### 範例 6-查看遠端電腦上的會話設定

此範例示範如何使用 WSMan 提供者檢視遠端電腦上的工作階段設定。 這個方法不會提供與命令一樣多的資訊 `Get-PSSessionConfiguration` ，但使用者不需要是 Administrators 群組的成員就能執行這個 Cmdlet。

```powershell
Connect-WSMan -ComputerName Server01
dir WSMan:\Server01\Plugin
```

```Output
   WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=Empty}                        Empty
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=NoLanguage}                   NoLanguage
Container       {Name=RestrictedLang}               RestrictedLang
Container       {Name=RRS}                          RRS
Container       {Name=SEL Plugin}                   SEL Plugin
Container       {Name=WithProfile}                  WithProfile
Container       {Name=WMI Provider}                 WMI Provider
```

`Connect-WSMan`Cmdlet 會連接到 Server01 遠端電腦上的 WinRM 服務。 `Get-ChildItem` `dir` WSMan：磁片磁碟機 (別名) 的 Cmdlet 會取得 **Server01\Plugin** 路徑中的專案。 輸出會顯示 Server01 電腦上 Plugin 目錄中的項目。 此項目包含工作階段設定 (一種 WSMan 外掛程式) 及電腦上其他類型的外掛程式。

### 範例 7-從遠端電腦取得詳細的會話設定

此範例顯示如何 `Get-PSSessionConfiguration` 在遠端電腦上執行命令。 此命令會要求在本機電腦上的用戶端設定及遠端電腦上的服務設定中啟用 CredSSP 委派。

若要執行此範例中的命令，您必須是本機電腦和遠端電腦上 Administrators 群組的成員，而且必須使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。

```powershell
Enable-WSManCredSSP -Delegate Server02
Connect-WSMan Server02
Set-Item WSMan:\Server02*\Service\Auth\CredSSP -Value $true
Invoke-Command -ScriptBlock {Get-PSSessionConfiguration} -ComputerName Server02 -Authentication CredSSP -Credential Domain01\Admin01
```

```Output
Name                      PSVersion  StartupScript        Permission                          PSComputerName
----                      ---------  -------------        ----------                          --------------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
MyX86Shell                5.1        c:\test\x86Shell.ps1 BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
```

此 `Enable-WSManCredSSP` Cmdlet 會在本機電腦上啟用 **CredSSP** 委派 Server01。 `Connect-WSMan`Cmdlet 會連接到 Server02 電腦。 此動作會將 Server02 的節點新增至本機電腦上的 WSMan：磁片磁碟機，讓您可以查看和變更 Server02 電腦上的 WS-Management 設定。 此 `Set-Item` Cmdlet 會將 Server02 電腦服務節點中的 **CredSSP** 專案值變更為 **True** 。 這會設定遠端電腦上的服務設定。 此 `Invoke-Command` Cmdlet 會 `Get-PSSessionConfiguration` 在 Server02 電腦上執行命令。 此命令使用 **Credential** 參數，並且使用 **Authentication** 參數搭配 **CredSSP** 值。 輸出結果顯示 Server02 遠端電腦上的工作階段設定。

### 範例 8-取得會話設定的資源 URI

此範例適用于設定喜好設定變數的值 `$PSSessionConfigurationName` ，此值會接受資源 URI。

```powershell
(Get-PSSessionConfiguration -Name CustomShell).resourceURI
```

```Output
http://schemas.microsoft.com/powershell/microsoft.CustomShell
```

`$PSSessionConfigurationName`變數會指定當您建立會話時使用的預設設定。 此變數設定在本機電腦上，但它會指定遠端電腦上的設定。 如需變數的詳細資訊 `$PSSessionConfiguration` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。

## PARAMETERS

### -Force

若服務尚未執行，抑制重新啟動 WinRM 服務的提示。

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

### -Name

只取得具有指定名稱或名稱模式的工作階段設定。 輸入一或多個工作階段設定名稱。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All session configurations on the local computer
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](./About/about_CommonParameters.md)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration

## 注意

- 若要執行此 Cmdlet，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。

- 若要檢視電腦上的工作階段設定，您必須是電腦上 Administrators 群組的成員。

- 若要 `Get-PSSessionConfiguration` 在遠端電腦上執行命令，您必須在本機 (電腦的用戶端設定中，使用指令程式 `Enable-WSManCredSSP`) 和遠端電腦上的服務設定中，啟用「認證安全性服務提供者」 (CredSSP) 驗證。 此外，在建立遠端會話時，您必須使用 **驗證** 參數的 **CredSSP** 值。 否則，會拒絕存取。

- `Get-PSSessionConfiguration`只有當物件具有值時，才會傳回物件的附注屬性。 只有使用會話設定檔建立的會話設定，才具有所有已定義的屬性。

- 工作階段設定物件的屬性取決於工作階段設定所設定的選項，以及這些選項的值。 此外，使用工作階段設定檔的工作階段設定會有額外的屬性。

- 您可以使用 WSMan: 磁碟機中的命令來變更工作階段設定的屬性。
  不過，您無法使用 PowerShell 2.0 中的 WSMan：磁片磁碟機來變更 PowerShell 3.0 中引進的會話設定屬性，例如 **OutputBufferingMode** 。 PowerShell 2.0 命令不會產生錯誤，但它們是不正確。 若要變更 PowerShell 3.0 中引進的屬性，請使用 PowerShell 3.0 中的 WSMan：磁片磁碟機。

## 相關連結

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供者](../microsoft.wsman.management/about/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
