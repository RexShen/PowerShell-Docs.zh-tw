---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 3a281786f99b2a46d0aeb9785480f02b35b2b433
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202339"
---
# Disable-PSRemoting

## 概要
防止 PowerShell 端點接收遠端連線。

## SYNTAX

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Disable-PSRemoting` Cmdlet 會封鎖對本機電腦上所有 Windows PowerShell 交談端點設定的遠端存取。 這包括 PowerShell 6 或更新版本所建立的任何端點。

若要重新啟用對所有會話設定的遠端存取，請使用 `Enable-PSRemoting` Cmdlet。 這包括 PowerShell 6 或更新版本所建立的任何端點。 若要啟用對所選會話設定的遠端存取，請使用 Cmdlet 的 **AccessMode** 參數 `Set-PSSessionConfiguration` 。
您也可以使用 `Enable-PSSessionConfiguration` 和 `Disable-PSSessionConfiguration` Cmdlet 來啟用和停用所有使用者的會話設定。 如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。

> [!NOTE]
> 即使在 `Disable-PSRemoting` 執行之後，您仍然可以在本機電腦上建立回送連接。 回送連線是來自的 PowerShell 遠端會話，並連接到相同的本機電腦。 外部來源的遠端會話仍會被封鎖。 針對回送連接，您必須在 **EnableNetworkAccess** 參數中使用隱含的認證。 如需回送連接的詳細資訊，請參閱 [新的-PSSession](New-PSSession.md)。

若要執行此 Cmdlet，請使用 [以 **系統管理員身分執行** ] 選項啟動 Windows PowerShell。

## 範例

### 範例1：防止所有會話設定的遠端存取

此範例會防止遠端存取電腦上的所有 PowerShell 交談端點設定。

```powershell
Disable-PSRemoting
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### 範例2：防止遠端存取所有會話設定，而不需要確認提示

此範例會防止遠端存取電腦上的所有 PowerShell 交談端點設定，而不提示。

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### 範例3：執行此 Cmdlet 的效果

此範例顯示使用 Cmdlet 的效果 `Disable-PSRemoting` 。 若要執行此命令順序，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。

停用會話設定之後， `New-PSSession` Cmdlet 會嘗試在本機電腦上建立遠端會話 (也稱為「回送」 ) 。 因為本機電腦上已停用遠端存取，所以命令會失敗。

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error
 message : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

### 範例4：執行此 Cmdlet 和 Enable-PSRemoting 的效果

此範例顯示使用和 Cmdlet 的會話設定效果 `Disable-PSRemoting` `Enable-PSRemoting` 。

`Disable-PSRemoting` 用來停用對所有 PowerShell 交談端點設定的遠端存取。 **Force** 參數會抑制所有使用者提示。 `Get-PSSessionConfiguration`和 `Format-Table` Cmdlet 會顯示電腦上的會話設定。

輸出顯示所有具有網路權杖的遠端使用者都會遭到拒絕存取端點設定。 本機電腦上的 Administrators 群組可存取端點設定，只要它們是在本機連線 (也稱為回送) 和使用隱含的認證。

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow BUILTIN\Administrators AccessAllowed
microsoft.powershell32        BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   BUILTIN\Administrators AccessAllowed
```

此 `Enable-PSRemoting` Cmdlet 會重新啟用對電腦上所有 PowerShell 交談端點設定的遠端存取。 **Force** 參數會抑制所有使用者提示，並在不提示的情況下重新開機 WinRM 服務。 新的輸出顯示已從所有會話設定中移除 **AccessDenied** 安全描述項。

### 範例5：已停用交談端點設定的回送連接

此範例示範如何停用端點設定，並示範如何對已停用的端點進行成功的回送連接。 `Disable-PSRemoting` 停用所有 PowerShell 交談端點設定。

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message : Access is
denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [New-PSSession], PSRemotin
   gTransportException
    + FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed

```

```powershell
New-PSSession -ComputerName localhost -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

第一次使用 `New-PSSession` 嘗試建立本機電腦的遠端會話。 這種類型的連線會通過網路堆疊，且不是回送。 因此，對已停用端點的連線嘗試會失敗，並出現「 **拒絕存取** 」錯誤。

第二次使用時， `New-PSSession` 也會嘗試建立本機電腦的遠端會話。
在此情況下，它會成功，因為它是略過網路堆疊的回送連接。

當符合下列條件時，就會建立回送連接：

- 要連接的電腦名稱稱是 ' localhost '。
- 未傳入任何認證。 目前登入的使用者 (隱含認證) 用於連接。
- 使用 **EnableNetworkAccess** 切換參數。

如需回送連接的詳細資訊，請參閱 [新的-PSSession](New-PSSession.md) 檔。

### 範例6：防止遠端存取具有自訂安全描述項的會話設定

此範例示範此 `Disable-PSRemoting` Cmdlet 會停用所有會話設定的遠端存取，這些設定包括具有自訂安全描述項的會話設定。

`Register-PSSessionConfiguration` 建立 **測試** 會話設定。 **FilePath** 參數指定可自訂會話的會話設定檔。 **ShowSecurityDescriptorUI** 參數會顯示對話方塊，該對話方塊會設定會話設定的許可權。 在 [許可權] 對話方塊中，我們會為指定的使用者建立自訂的完整存取權限。

`Get-PSSessionConfiguration`和 `Format-Table` Cmdlet 會顯示會話設定和其屬性。 輸出顯示 **測試** 會話設定允許指定使用者的互動式訪問和特殊許可權。

`Disable-PSRemoting` 停用對所有會話設定的遠端存取。

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
DOMAIN01\User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\NETWORK AccessDenied, NTAUTHORITY\INTERACTIVE AccessAllowed,
BUILTIN\Administrators AccessAllowed, DOMAIN01\User01 AccessAllowed


[Server01] Connecting to remote server failed with the following error message : Access is denied. For more information, see the about_Rem
ote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

現在 `Get-PSSessionConfiguration` 和 `Format-Table` Cmdlet 會顯示所有網路使用者的 **AccessDenied** 安全描述項都已新增至所有會話設定，包括 **測試** 會話設定。 雖然其他安全描述項並未變更，但 "network_deny_all" 安全描述項的優先順序較高。 這會由嘗試用 `New-PSSession` 來連接到 **測試** 會話設定來說明。

### 範例7：重新啟用對所選會話設定的遠端存取

此範例顯示如何只對選取的工作階段設定重新啟用遠端存取。 停用所有會話設定之後，我們會重新啟用特定的會話。

此 `Set-PSSessionConfiguration` Cmdlet 是用來變更 **microsoft。ServerManager** 會話設定。 **AccessMode** 參數的值為 [ **遠端** 重新啟用對設定的遠端存取]。

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name Microsoft.ServerManager -AccessMode Remote -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
```

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

### -Force
強制執行命令而不要求使用者確認。

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

### 無

您無法透過管線將任何物件傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

- 停用會話設定不會復原或 Cmdlet 所做的所有變更 `Enable-PSRemoting` `Enable-PSSessionConfiguration` 。 您可能必須手動復原下列變更。

  1. 停止及停用 WinRM 服務。
  2. 刪除接受任何 IP 位址上之要求的接聽程式。
  3. 停用 WS-Management 通訊的防火牆例外。
  4. 將 LocalAccountTokenFilterPolicy 的值還原為 0，以限制對電腦上之 Administrators 群組成員的遠端存取。

  工作階段設定是定義工作階段環境的一組設定。 連線到電腦的每個工作階段都必須使用在本機電腦上註冊的其中一項工作階段設定。 如果拒絕對所有工作階段設定的遠端存取，即可有效防止遠端使用者建立連線到電腦的工作階段。

  在 Windows PowerShell 2.0 中，會 `Disable-PSRemoting` 將 Deny_All 專案加入至所有會話設定的安全描述項。 此設定可防止所有使用者在本機電腦上建立使用者管理的會話。 在 Windows PowerShell 3.0 中，會 `Disable-PSRemoting` 將 Network_Deny_All 專案加入至所有會話設定的安全描述項。 這項設定可防止其他電腦上的使用者在本機電腦上建立使用者管理的會話，但允許本機電腦的使用者建立使用者管理的回送會話。

  在 Windows PowerShell 2.0 中， `Disable-PSRemoting` 相當於 `Disable-PSSessionConfiguration -Name *` 。 在 Windows PowerShell 3.0 和更新版本中， `Disable-PSRemoting` 相當於 `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`

## 相關連結

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSRemoting](Enable-PSRemoting.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供者](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
