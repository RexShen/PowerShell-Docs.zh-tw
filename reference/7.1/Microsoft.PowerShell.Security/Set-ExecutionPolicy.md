---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: d04fb0bb75906d18fecce17e4ceb581fe667eceb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202444"
---
# Set-ExecutionPolicy

## 概要
設定 Windows 電腦的 PowerShell 執行原則。

## SYNTAX

### 全部

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Set-ExecutionPolicy` Cmdlet 會變更 Windows 電腦的 PowerShell 執行原則。 如需詳細資訊，請參閱 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)。

從非 Windows 電腦的 PowerShell 6.0 開始，預設的執行原則不 **受限制** 且無法變更。 您 `Set-ExecutionPolicy` 可以使用此 Cmdlet，但 PowerShell 會顯示不支援的主控台訊息。

執行原則是 PowerShell 安全性策略的一部分。 執行原則會決定您是否可以載入設定檔，例如 PowerShell 設定檔或執行腳本。 而且，腳本在執行前是否必須經過數位簽署。

`Set-ExecutionPolicy`Cmdlet 的預設範圍是 **LocalMachine** ，會影響使用該電腦的每個人。 若要變更 **LocalMachine** 的執行原則，請使用 [以 **系統管理員身分執行** ] 啟動 PowerShell。

若要以優先順序順序顯示每個範圍的執行原則，請使用 `Get-ExecutionPolicy -List` 。 若要查看適用于 PowerShell 會話的有效執行原則，請使用 `Get-ExecutionPolicy` 沒有參數的。

## 範例

### 範例1：設定執行原則

此範例顯示如何設定本機電腦的執行原則。

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

此 `Set-ExecutionPolicy` Cmdlet 會使用 **ExecutionPolicy** 參數來指定 **RemoteSigned** 原則。 **Scope** 參數會指定預設的範圍值： **LocalMachine** 。 若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。

### 範例2：設定與群組原則衝突的執行原則

此命令會嘗試將 **LocalMachine** 範圍的執行原則設定為 [ **受限制** ]。
**LocalMachine** 的限制較多，但不是有效的原則，因為它與群組原則衝突。 **受限制** 的原則會寫入登錄 hive **HKEY_LOCAL_MACHINE** 。

```
PS> Set-ExecutionPolicy -ExecutionPolicy Restricted -Scope LocalMachine

Set-ExecutionPolicy : PowerShell updated your local preference successfully, but the setting is
overridden by the Group Policy applied to your system. Due to the override, your shell will retain
its current effective execution policy of "AllSigned". Contact your Group Policy administrator for
more information. At line:1 char:20 + Set-ExecutionPolicy <<<< restricted

PS> Get-ChildItem -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds

Name                    Property
----                    --------
Microsoft.PowerShell    Path            : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
                        ExecutionPolicy : Restricted
ScriptedDiagnostics     ExecutionPolicy : Unrestricted
```

此 `Set-ExecutionPolicy` Cmdlet 會使用 **ExecutionPolicy** 參數來指定 **受限制** 的原則。 **Scope** 參數會指定預設的範圍值： **LocalMachine** 。
此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數搭配 **HKLM** 提供者來指定登錄位置。

### 範例3：將執行原則從遠端電腦套用至本機電腦

此命令會從遠端電腦取得執行原則物件，並在本機電腦上設定原則。 `Get-ExecutionPolicy` 將 **Microsoft.PowerShell.ExecutionPolicy** 物件沿著管線向下傳送。 `Set-ExecutionPolicy` 接受管線輸入，且不需要 **ExecutionPolicy** 參數。

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

此 `Invoke-Command` Cmdlet 會在本機電腦上執行，並將 **ScriptBlock** 傳送至遠端電腦。 **ComputerName** 參數指定遠端電腦 **Server01** 。 **ScriptBlock** 參數會 `Get-ExecutionPolicy` 在遠端電腦上執行。 `Get-ExecutionPolicy`物件會向下傳送至 `Set-ExecutionPolicy` 。
`Set-ExecutionPolicy` 將執行原則套用到本機電腦的預設範圍 **LocalMachine** 。

### 範例4：設定執行原則的範圍

此範例示範如何為指定的範圍（ **CurrentUser** ）設定執行原則。 **CurrentUser** 範圍只會影響設定此領域的使用者。

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy` 使用 **ExecutionPolicy** 參數來指定 **AllSigned** 原則。
**Scope** 參數指定 **CurrentUser** 。 若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。

使用者的有效執行原則會變成 **AllSigned** 。

### 範例5：移除目前使用者的執行原則

此範例示範如何使用 **未定義** 的執行原則，來移除指定範圍的執行原則。

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy` 使用 **ExecutionPolicy** 參數指定 **未定義** 的原則。
**Scope** 參數指定 **CurrentUser** 。 若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。

### 範例6：設定目前 PowerShell 會話的執行原則

**進程** 範圍只會影響目前的 PowerShell 會話。 執行原則會儲存在環境變數中 `$env:PSExecutionPolicyPreference` ，並在會話關閉時刪除。

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope Process
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       AllSigned
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy`使用 **ExecutionPolicy** 參數來指定 **AllSigned** 原則。 **Scope** 參數會指定值 **處理** 。 若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。

### 範例7：解除封鎖腳本以在不變更執行原則的情況下執行

此範例顯示 **RemoteSigned** 執行原則如何防止您執行未簽署的腳本。

最佳做法是先閱讀腳本的程式碼，並確認它是安全的，然後 **再** 使用 `Unblock-File` Cmdlet。 此 `Unblock-File` Cmdlet 會解除封鎖腳本，使其可執行，但不會變更執行原則。

```
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

.\Start-ActivityTracker.ps1 : File .\Start-ActivityTracker.ps1 cannot be loaded.
The file .\Start-ActivityTracker.ps1 is not digitally signed.
The script will not execute on the system.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess

PS> Unblock-File -Path .\Start-ActivityTracker.ps1

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

Task 1:
```

`Set-ExecutionPolicy`使用 **ExecutionPolicy** 參數來指定 **RemoteSigned** 原則。 設定預設範圍 **LocalMachine** 的原則。

此 `Get-ExecutionPolicy` Cmdlet 會顯示 **RemoteSigned** 是目前 PowerShell 會話的有效執行原則。

**Start-ActivityTracker.ps1** 的腳本會從目前的目錄執行。 因為腳本未經過數位簽署，所以 **RemoteSigned** 會封鎖腳本。

在此範例中，腳本的程式碼已被審核並驗證為可安全執行。 此 `Unblock-File` Cmdlet 會使用 **Path** 參數將腳本解除封鎖。

若要確認 `Unblock-File` 未變更執行原則，請 `Get-ExecutionPolicy` 顯示有效的執行原則 **RemoteSigned** 。

腳本 **Start-ActivityTracker.ps1** 會從目前的目錄執行。 腳本開始執行的原因是 Cmdlet 已解除封鎖 `Unblock-File` 。

## PARAMETERS

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

### -ExecutionPolicy

指定執行原則。 如果沒有任何群組原則，且每個範圍的執行原則都設定為 **未定義** ，則 [ **受限制** ] 會成為所有使用者的有效原則。

可接受的執行原則值如下：

- **AllSigned** 。 要求所有腳本和設定檔都必須由信任的發行者簽署，包括在本機電腦上撰寫的腳本。
- **略過** 。 不會封鎖任何項目，且不會顯示警告或提示。
- **Default** 。 設定預設執行原則。 **受限於** windows 用戶端或 Windows server **RemoteSigned** 。
- **RemoteSigned** 。 要求從網際網路下載的所有腳本和設定檔都必須由信任的發行者簽署。 Windows server 電腦的預設執行原則。
- **受限制** 。 不會載入設定檔或執行腳本。 預設的執行原則 Windows 用戶端電腦。
- **未定義** 。 未設定範圍的執行原則。 從未由群組原則設定的範圍移除指派的執行原則。 如果未 **定義** 所有範圍中的執行原則，則會 **限制** 有效的執行原則。
- 不 **受限制** 。 從 PowerShell 6.0 開始，這是非 Windows 電腦的預設執行原則，無法變更。 載入所有設定檔並執行所有指令碼。 如果您執行從網際網路下載的未簽署腳本，系統會在執行之前提示您提供許可權。

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: AllSigned, Bypass, Default, RemoteSigned, Restricted, Undefined, Unrestricted

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Force

隱藏所有確認提示。 請小心使用此參數來避免非預期的結果。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scope

指定受執行原則影響的範圍。 預設範圍是 **LocalMachine** 。

有效的執行原則取決於優先順序順序，如下所示：

- **MachinePolicy** 。 由電腦的所有使用者的群組原則設定。
- **>userpolicy** 。 由電腦目前使用者的群組原則設定。
- **處理** 。 只會影響目前的 PowerShell 會話。
- **CurrentUser** 。 只會影響目前的使用者。
- **LocalMachine** 。 預設範圍會影響電腦的所有使用者。

**進程** 範圍只會影響目前的 PowerShell 會話。 執行原則會儲存在環境變數中，而不是儲存在登錄中 `$env:PSExecutionPolicyPreference` 。 當 PowerShell 會話關閉時，會刪除變數和值。

**CurrentUser** 範圍的執行原則會寫入登錄 hive **HKEY_LOCAL_USER** 。

**LocalMachine** 範圍的執行原則會寫入登錄 hive **HKEY_LOCAL_MACHINE** 。

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 1
Default value: LocalMachine
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

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

### Microsoft.PowerShell.ExecutionPolicy、System.String

您可以使用管線將執行原則物件或包含執行原則名稱的字串傳送至 `Set-ExecutionPolicy` 。

## 輸出

### 無

`Set-ExecutionPolicy` 不會傳回任何輸出。

## 注意

`Set-ExecutionPolicy` 不會變更 **MachinePolicy** 和 **>userpolicy** 範圍，因為它們是由群組原則設定。

`Set-ExecutionPolicy` 即使使用者喜好設定比原則更嚴格，也不會覆寫群組原則。

如果電腦或使用者的群組原則 **開啟腳本執行** ，則會儲存使用者喜好設定，但它並不會有效。 PowerShell 會顯示說明衝突的訊息。

## 相關連結

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Group_Policy_Settings](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-executionpolicy](Get-ExecutionPolicy.md)

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Unblock-File](../Microsoft.PowerShell.Utility/Unblock-File.md)

