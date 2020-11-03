---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-executionpolicy
ms.openlocfilehash: d33961d9c0b1980d84d35a33c45d965e84231914
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205035"
---
# Get-executionpolicy

## 概要
取得目前工作階段的執行原則。

## SYNTAX

### 全部

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## DESCRIPTION

若要以優先順序順序顯示每個範圍的執行原則，請使用 `Get-ExecutionPolicy -List` 。 若要查看適用于 PowerShell 會話的有效執行原則，請使用 `Get-ExecutionPolicy` 沒有參數的。

有效的執行原則取決於由設定的執行原則， `Set-ExecutionPolicy` 以及群組原則設定。

如需詳細資訊，請參閱 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)。

## 範例

### 範例1：取得所有執行原則

此命令顯示每個範圍的執行原則（依優先順序排列）。

```powershell
Get-ExecutionPolicy -List
```

```Output
Scope          ExecutionPolicy
-----          ---------------
MachinePolicy  Undefined
UserPolicy     Undefined
Process        Undefined
CurrentUser    AllSigned
LocalMachine   Undefined
```

此 `Get-ExecutionPolicy` Cmdlet 會使用 **List** 參數來顯示每個範圍的執行原則。

### 範例2：設定執行原則

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
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

此 `Set-ExecutionPolicy` Cmdlet 會使用 **ExecutionPolicy** 參數來指定 **RemoteSigned** 原則。 **Scope** 參數會指定預設的範圍值： **LocalMachine** 。 若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。

### 範例3：取得有效的執行原則

此範例說明如何顯示 PowerShell 會話的有效執行原則。

```
PS> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned

PS> Get-ExecutionPolicy

AllSigned
```

此 `Get-ExecutionPolicy` Cmdlet 會使用 **List** 參數來顯示每個範圍的執行原則。 此 `Get-ExecutionPolicy` Cmdlet 會在沒有參數的情況下執行，以顯示有效的執行原則 **AllSigned** 。

### 範例4：解除封鎖腳本以在不變更執行原則的情況下執行

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

### -List

取得工作階段的所有執行原則值，依照優先順序列出。 根據預設， `Get-ExecutionPolicy` 只會取得有效的執行原則。

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

指定受執行原則影響的範圍。

有效的執行原則取決於優先順序順序，如下所示：

- **MachinePolicy** 。 由電腦的所有使用者的群組原則設定。
- **>userpolicy** 。 由電腦目前使用者的群組原則設定。
- **處理** 。 只會影響目前的 PowerShell 會話。
- **CurrentUser** 。 只會影響目前的使用者。
- **LocalMachine** 。 預設範圍會影響電腦的所有使用者。

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 0
Default value: Effective execution policy
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

`Get-ExecutionPolicy` 不接受來自管線的輸入。

## 輸出

### Microsoft.PowerShell.ExecutionPolicy

## 注意

執行原則是 PowerShell 安全性策略的一部分。 執行原則會決定您是否可以載入設定檔，例如 PowerShell 設定檔或執行腳本。 而且，腳本在執行前是否必須經過數位簽署。

## 相關連結

[about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[about_Group_Policy_Settings](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)

