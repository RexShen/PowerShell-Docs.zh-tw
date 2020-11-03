---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-computersecurechannel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ComputerSecureChannel
ms.openlocfilehash: 20ea76e725a8ab53d7090078dc819a6297a639ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203459"
---
# Test-ComputerSecureChannel

## 概要
測試和修復本機電腦和其網域之間的安全通道。

## SYNTAX

```
Test-ComputerSecureChannel [-Repair] [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
**Test-computersecurechannel** 指令程式會檢查其信任關係的狀態，以確認本機電腦與其網域之間的通道是否正常運作。
如果連線失敗，您可以使用 *Repair* 參數嘗試還原它。

如果通道正常運作， **test-computersecurechannel** 會傳回 $True，並 $False。
此結果可讓您在函式和指令碼中的條件陳述式使用此 Cmdlet。
若要取得更詳細的測試結果，請使用 *Verbose* 參數。

此 Cmdlet 的運作方式與 NetDom.exe 非常類似。
NetDom 和 **測試 test-computersecurechannel** 都使用 **NetLogon** 服務來執行動作。

## 範例

### 範例1：測試本機電腦與其網域之間的通道

```
PS C:\> Test-ComputerSecureChannel
True
```

此命令會測試本機電腦與其聯結網域之間的通道。

### 範例2：在本機電腦和網域控制站之間測試通道

```
PS C:\> Test-ComputerSecureChannel -Server "DCName.fabrikam.com"
True
```

此命令會指定測試的慣用網域控制站。

### 範例3：重設本機電腦和其網域之間的通道

```
PS C:\> Test-ComputerSecureChannel -Repair
True
```

此命令會重設本機電腦和其網域之間的通道。

### 範例4：顯示測試的詳細資訊

```
PS C:\> Test-ComputerSecureChannel -verbose
VERBOSE: Performing operation "Test-ComputerSecureChannel" on Target "SERVER01".
True
VERBOSE: "The secure channel between 'SERVER01' and 'net.fabrikam.com' is alive and working correctly."
```

此命令會使用 *Verbose* 一般參數來要求有關作業的詳細訊息。
如需 *詳細* 資訊的詳細資訊，請參閱 about_CommonParameters。

### 範例5：執行腳本之前先測試連接

```
PS C:\> Set-Alias tcsc Test-ComputerSecureChannel
if (!(tcsc))
{Write-Host "Connection failed. Reconnect and retry."}
else { &(.\Get-Servers.ps1) }
```

這個範例示範如何在執行需要連線的腳本之前，先使用 **測試 test-computersecurechannel** 來測試連接。

第一個命令會使用 Set-Alias Cmdlet 建立 Cmdlet 名稱的別名。
如此可節省空間和避免輸入錯誤。

**If** 語句會在執行腳本之前檢查 **test-computersecurechannel** 傳回的值。

## PARAMETERS

### -Credential
指定具有執行此動作權限的使用者帳戶。
輸入使用者名稱（例如 User01 或 Domain01\User01），或輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 所傳回的物件。
根據預設，Cmdlet 會使用目前使用者的認證。

*Credential* 參數是設計用於使用 *repair* 參數修復電腦與網域之間通道的命令。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Repair
指出此 Cmdlet 會移除並重建 NetLogon 服務所建立的通道。
使用這個參數來嘗試還原測試失敗的連接。

如果要使用這個參數，目前使用者必須是本機電腦上之 Administrators 群組的成員。

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

### -Server
指定要執行命令的網域控制站。
如果未指定這個參數，此 Cmdlet 會為作業選取預設網域控制站。

```yaml
Type: System.String
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
顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

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

### 無
您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.Boolean
如果連線正常運作，此 Cmdlet 會傳回 $True，如果沒有，則會 $False。

## 注意

* 若要在 Windows Vista 和更新版本的 Windows 作業系統上執行 **test-computersecurechannel** 命令，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。
* **測試 test-computersecurechannel** 是使用 **I_NetLogonControl2** 函式來執行，此函式會控制 Netlogon 服務的各個層面。

## 相關連結

[Checkpoint-Computer](Checkpoint-Computer.md)

[Reset-ComputerMachinePassword](Reset-ComputerMachinePassword.md)

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
