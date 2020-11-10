---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Computer
ms.openlocfilehash: e3d1c5c071a334bddbfbc547ef2cc07e9e5c90aa
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388343"
---
# Add-Computer

## 概要
將本機電腦新增到網域或工作群組。

## SYNTAX

### 網域 (預設) 

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>]
 [-UnjoinDomainCredential <PSCredential>] -Credential <PSCredential> [-DomainName] <String> [-OUPath <String>]
 [-Server <String>] [-Unsecure] [-Options <JoinOptions>] [-Restart] [-PassThru] [-NewName <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 工作群組

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>] [-Credential <PSCredential>]
 [-WorkgroupName] <String> [-Restart] [-PassThru] [-NewName <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`Add-Computer`Cmdlet 會將本機電腦或遠端電腦新增到網域或工作組，或將它們從一個網域移到另一個網域。 如果將電腦新增到網域時沒有帳戶，它也會一併建立網域帳戶。

您可以使用這個 Cmdlet 的參數來指定組織單位 (OU) 和網域控制站，或是執行非安全性加入。

若要取得此命令的結果，請使用 **Verbose** 和 **PassThru** 參數。

## 範例

### 範例1：將本機電腦新增至網域，然後重新開機電腦

```powershell
Add-Computer -DomainName Domain01 -Restart
```

這個命令會將本機電腦新增到 Domain01 網域，然後重新啟動電腦以使變更生效。

### 範例2：將本機電腦新增至工作組

```powershell
Add-Computer -WorkgroupName WORKGROUP-A
```

這個命令會將本機電腦新增到 Workgroup-A 工作群組。

### 範例3：將本機電腦新增至網域

```powershell
Add-Computer -DomainName Domain01 -Server Domain01\DC01 -PassThru -Verbose
```

這個命令使用 Domain01\DC01 網域控制站將本機電腦新增到 Domain01 網域。

此命令使用 **PassThru** 和 **Verbose** 參數來取得有關命令結果的詳細資訊。

### 範例4：使用 OUPath 參數將本機電腦新增至網域

```powershell
Add-Computer -DomainName Domain02 -OUPath "OU=testOU,DC=domain,DC=Domain,DC=com"
```

這個命令會將本機電腦新增到 Domain02 網域。
它使用 OUPath 參數來指定新帳戶的組織單位。

### 範例5：使用認證將本機電腦新增至網域

```powershell
Add-Computer -ComputerName Server01 -LocalCredential Server01\Admin01 -DomainName Domain02 -Credential Domain02\Admin02 -Restart -Force
```

這個命令會將 Server01 電腦新增到 Domain02 網域。 它使用 **LocalCredential** 參數來指定具有連線到 Server01 電腦之權限的使用者帳戶。 它使用 **Credential** 參數來指定具有將電腦加入網域之權限的使用者帳戶。 它使用 **Restart** 參數，以在加入操作完成後重新啟動電腦，並且使用 **Force** 參數，以抑制使用者確認訊息。

### 範例6：將電腦群組移至新網域

```powershell
Add-Computer -ComputerName Server01, Server02, localhost -DomainName Domain02 -LocalCredential Domain01\User01 -UnjoinDomainCredential Domain01\Admin01 -Credential Domain02\Admin01 -Restart
```

這個命令會將 Server01 和 Server02 電腦以及本機電腦從 Domain01 移到 Domain02。

它使用 **LocalCredential** 參數來指定具有連線到這三部受影響電腦之權限的使用者帳戶。 它使用 **UnjoinDomainCredential** 參數來指定具有將電腦從 Domain01 網域退出之權限的使用者帳戶，並且使用 **Credential** 參數來指定具有將電腦加入 Domain02 網域之權限的使用者帳戶。 它使用 **Restart** 參數，以在完成移動後重新啟動這三部電腦。

### 範例7：將電腦移至新網域，並變更電腦的名稱

```powershell
Add-Computer -ComputerName Server01 -DomainName Domain02 -NewName Server044 -Credential Domain02\Admin01 -Restart
```

這個命令會將 Server01 電腦移到 Domain02，並將電腦名稱變更為 Server044。

此命令使用目前使用者的認證來連線到 Server01 電腦，以及將它從其目前的網域退出。 它會使用 **Credential** 參數來指定具有將電腦加入 Domain02 網域之許可權的使用者帳戶。

### 範例8：將檔案中列出的電腦新增至新的網域

```powershell
Add-Computer -ComputerName (Get-Content Servers.txt) -DomainName Domain02 -Credential Domain02\Admin02 -Options Win9xUpgrade  -Restart
```

這個命令會將 Servers.txt 檔案中所列的電腦新增到 Domain02 網域。 它使用 **Options** 參數來指定 **Win9xUpgrade** 選項。 **Restart** 參數會在加入操作完成後，重新啟動所有新加入的電腦。

### 範例9：使用預先定義的電腦認證將電腦新增至網域

第一個命令應該由系統管理員從已加入網域的電腦執行 `Domain03` ：

```powershell
New-ADComputer -Name "Server02" -AccountPassword (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)

# Then this command is run from `Server02` which is not yet domain-joined:

$joinCred = New-Object pscredential -ArgumentList ([pscustomobject]@{
    UserName = $null
    Password = (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)[0]
})
Add-Computer -Domain "Domain03" -Options UnsecuredJoin,PasswordPass -Credential $joinCred
```

這項命令組合會使用已加入網域的現有電腦，在網域中建立具有預先定義名稱和暫時聯結密碼的新電腦帳戶。 接著，如果電腦具有預先定義的名稱，則只會使用電腦名稱稱和暫時聯結密碼來加入網域。
預先定義的密碼只是用來支援聯結作業，而且會在電腦完成聯結之後，被取代為一般電腦帳戶程式的一部分。

## PARAMETERS

### -ComputerName

指定要新增到網域或工作群組的電腦。
預設是本機電腦。

輸入 NetBIOS 名稱、網際網路通訊協定 (IP) 位址，或每部遠端電腦的完整功能變數名稱。 若要指定本機電腦，請輸入電腦名稱稱、點 (`.`) 或 "localhost"。

此參數不必依賴 Windows PowerShell 遠端功能。 **ComputerName** `Add-Computer` 即使您的電腦未設定為執行遠端命令，您也可以使用 ComputerName 參數。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

指定具有將電腦加入新網域之權限的使用者帳戶。
預設為目前使用者。

輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。 若您輸入使用者名稱，將會提示您輸入密碼。

若要指定具有將電腦從其目前網域中移除之權限的使用者帳戶，請使用 **UnjoinDomainCredential** 參數。 若要指定具有連線到遠端電腦之權限的使用者帳戶，請使用 **LocalCredential** 參數。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain, Workgroup
Aliases: DomainCredential

Required: True (Domain), False (Workgroup)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DomainName

指定要將電腦新增到其中的網域。 將電腦新增到網域時，必須使用這個參數。

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DN, Domain

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

抑制使用者確認提示。 如果沒有這個參數， `Add-Computer` 則會要求您確認新增每部電腦。

此參數是在 Windows PowerShell 3.0 引進。

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

### -LocalCredential

指定具有連線到 **ComputerName** 參數所指定電腦之權限的使用者帳戶。 預設為目前使用者。

輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。 若您輸入使用者名稱，將會提示您輸入密碼。

若要指定具有將電腦新增到新網域之權限的使用者帳戶，請使用 **Credential** 參數。 若要指定具有將電腦從其目前網域中移除之權限的使用者帳戶，請使用 **UnjoinDomainCredential** 參數。

此參數是在 Windows PowerShell 3.0 引進。

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

### -NewName

指定新網域中電腦的新名稱。 這個參數只有在新增或移除電腦時才有效。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -選項

指定 **載入電腦** 聯結作業的 advanced 選項。 請以逗號分隔的字串方式輸入一個或多個值。

此參數可接受的值為：

- **帳戶** ：建立網域帳戶。 **新增** 電腦指令 Cmdlet 會在將電腦新增到網域時自動建立網域帳戶。 包含這個選項是為了完整性。

- **Win9XUpgrade** ：表示聯結作業是 Windows 作業系統升級的一部分。

- **UnsecuredJoin** ：執行不安全的聯結。 若要要求不安全的聯結，請使用不 *安全* 的參數或這個選項。 如果您想要傳遞電腦密碼，則必須將此選項與選項搭配使用 `PasswordPass` 。

- **PasswordPass** ：在執行不安全的聯結之後，將電腦密碼設定為 *Credential* (DomainCredential) 參數的值。 這個選項也會指出 *Credential* (DomainCredential) 參數的值是電腦密碼，而不是使用者密碼。 只有在指定選項時，這個選項才有效 `UnsecuredJoin` 。 使用此選項時，提供給參數的認證 `-Credential` *必須* 有 null 使用者名稱。

- **JoinWithNewName** ：將新網域中的電腦名稱稱重新命名為 *NewName* 參數所指定的名稱。 使用 *NewName* 參數時，會自動設定這個選項。 此選項的設計目的是要搭配 Rename-Computer Cmdlet 使用。 如果您使用「 **重新命名電腦** 」 Cmdlet 來重新命名電腦，但並未重新開機電腦以使變更生效，您可以使用此參數將電腦加入具有新名稱的網域。

- **JoinReadOnly** ：使用現有的電腦帳戶將電腦加入唯讀網域控制站。 您必須將電腦帳戶新增到密碼複寫原則的允許清單中，而且必須先將帳戶密碼複寫到唯讀網域控制站，才能進行聯結操作。

- **InstallInvoke** ：設定 **JoinDomainOrWorkgroup** 方法之 **joindomainorworkgroup** 參數的 create (0x2) 和 delete (0x4) 旗標。 如需 **JoinDomainOrWorkgroup** 方法的詳細資訊，請參閱 [Win32_ComputerSystem 類別的 JoinDomainOrWorkgroup 方法](/windows/win32/cimwin32prov/joindomainorworkgroup-method-in-class-win32-computersystem)。
  如需這些選項的詳細資訊，請參閱 [NetJoinDomain 函數](/windows/win32/api/lmjoin/nf-lmjoin-netjoindomain)。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: Microsoft.PowerShell.Commands.JoinOptions
Parameter Sets: Domain
Aliases:
Accepted values: AccountCreate, Win9XUpgrade, UnsecuredJoin, PasswordPass, DeferSPNSet, JoinWithNewName, JoinReadOnly, InstallInvoke

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OUPath

指定網域帳戶的組織單位 (OU)。 請以引號括住的方式輸入 OU 的完整辨別名稱。 預設值是網域中電腦物件的預設 OU。

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: OU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

傳回代表您正在使用之項目的物件。 根據預設，此 Cmdlet 不會產生任何輸出。

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

### -Restart

重新啟動已新增到網域或工作群組的電腦。 通常必須重新啟動才能使變更生效。

此參數是在 Windows PowerShell 3.0 引進。

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

### -Server

指定將電腦新增到網域的網域控制站名稱。 請以 DomainName\ComputerName 格式輸入名稱。 預設不會指定任何網域控制站。

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UnjoinDomainCredential

指定具有將電腦從其目前網域中移除之權限的使用者帳戶。 預設為目前使用者。

輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。 若您輸入使用者名稱，將會提示您輸入密碼。

當您要將電腦移到不同的網域時，請使用此參數。 若要指定具有將電腦加入新網域之權限的使用者帳戶，請使用 **Credential** 參數。 若要指定具有連線到遠端電腦之權限的使用者帳戶，請使用 **LocalCredential** 參數。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -不安全

執行對指定之網域的非安全性加入。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkgroupName

指定要將電腦新增到其中的工作群組名稱。 預設值為 "WORKGROUP"。

```yaml
Type: System.String
Parameter Sets: Workgroup
Aliases: WGN

Required: True
Position: 0
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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

您可以透過管線將電腦名稱稱和新名稱傳送至 `Add-Computer` Cmdlet。

## 輸出

### Microsoft.PowerShell.Commands.ComputerChangeInfo

當您使用 **PassThru** 參數時，會傳回 `Add-Computer` **ComputerChangeInfo** 物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

- 在 Windows PowerShell 2.0 中，即使伺服器存在， **伺服器** 參數也 `Add-Computer` 會失敗。 在 Windows PowerShell 3.0 中， **Server** 參數的實作已變更，使其能夠可靠地運作。

## 相關連結

[Checkpoint-Computer](Checkpoint-Computer.md)

[Remove-Computer](Remove-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Rename-Computer](Rename-Computer.md)

[Restore-Computer](Restore-Computer.md)

[Stop-Computer](Stop-Computer.md)

[Test-Connection](Test-Connection.md)
