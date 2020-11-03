---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: 8062210aa94cb46d5e5557ede1bac672cae39622
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205415"
---
# Stop-Computer

## 概要
將本機電腦和遠端電腦停止 (關機)。

## SYNTAX

### 全部

```
Stop-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

此 `Stop-Computer` Cmdlet 會將本機電腦和遠端電腦關機。

您可以使用的參數 `Stop-Computer` ，以背景工作方式執行關機作業、指定驗證等級和替代認證、限制為了執行命令所建立的並行連線，以及強制立即關機。

除非您使用 **AsJob** 參數，否則這個 Cmdlet 不需要 PowerShell 遠端功能。

## 範例

### 範例1：關閉本機電腦

此範例會將本機電腦關機。

```powershell
Stop-Computer -ComputerName localhost
```

### 範例2：關閉兩部遠端電腦和本機電腦

此範例會停止兩部遠端電腦和本機電腦。

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

`Stop-Computer` 使用 **ComputerName** 參數來指定兩部遠端電腦和本機電腦。 每部電腦都已關閉。

### 範例3：將遠端電腦關閉為背景工作

在此範例中，會 `Stop-Computer` 在兩部遠端電腦上以背景工作的形式執行。

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" -AsJob
$results = $j | Receive-Job
$results
```

`Stop-Computer` 使用 **ComputerName** 參數來指定兩部遠端電腦。 **AsJob** 參數會以背景工作的方式執行命令。 工作物件會儲存在變數中 `$j` 。

變數中的工作物件 `$j` 會向下傳送至管線 `Receive-Job` ，以取得工作結果。 物件會儲存在變數中 `$results` 。 此 `$results` 變數會在 PowerShell 主控台中顯示工作資訊。

由於 **AsJob** 會在本機電腦上建立工作，並自動將結果傳回本機電腦，因此您可以用 `Receive-Job` 本機命令的形式執行。

### 範例4：將遠端電腦關機

此範例會使用指定的驗證來關閉遠端電腦。

```powershell
Stop-Computer -ComputerName "Server01" -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

`Stop-Computer` 使用 **ComputerName** 參數來指定遠端電腦。 模擬 **參數會** 指定自訂的模擬，而 **DcomAuthentication** 參數會指定驗證層級設定。

### 範例5：關閉網域中的電腦

在此範例中，命令會強制立即關閉指定網域中的所有電腦。

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -ThrottleLimit 10 -Credential $c
```

`Get-Content` 使用 **Path** 參數，以網域電腦清單取得目前目錄中的檔案。 物件會儲存在變數中 `$s` 。

`Get-Credential` 使用 **Credential** 參數來指定網域系統管理員的認證。 認證會儲存在變數中 `$c` 。

`Stop-Computer` 以變數中 **電腦的電腦** 清單，關閉指定的電腦 `$s` 。 **Force** 參數會強制立即關機。 **ThrottleLimit** 參數會將命令限制為10個並行連接。 **Credential** 參數會提交儲存在變數中的認證 `$c` 。

## PARAMETERS

### -AsJob

指出此 Cmdlet 會以背景工作的形式執行。

若要使用這個參數，本機電腦和遠端電腦必須設定為進行遠端處理，而在 Windows Vista 和更新版本的 Windows 作業系統上，您必須使用 [以 **系統管理員身分執行** ] 選項開啟 PowerShell。 如需詳細資訊，請參閱[about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md)。

當您指定 **AsJob** 參數時，此命令會立即傳回代表背景工作的物件。 工作完成後，您可以繼續在工作階段中工作。 工作會在本機電腦上建立，而來自遠端電腦的結果則會自動傳回到本機電腦。 若要取得工作結果，請使用 `Receive-Job` Cmdlet。

如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) 和 [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md)。

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

### -ComputerName

指定要停止的電腦。 預設是本機電腦。

請輸入一或多部電腦的 NETBIOS 名稱、IP 位址或完整網域名稱 (以逗號分隔的清單方式)。 若要指定本機電腦，請輸入電腦名稱稱或 localhost。

此參數不依賴 PowerShell 遠端功能。 即使您的電腦未設定為執行遠端命令，您也可以使用 **ComputerName** 參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### -Credential

指定具有執行此動作之許可權的使用者帳戶。 預設為目前使用者。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DcomAuthentication

指定此 Cmdlet 與 WMI 搭配使用的驗證層級。 `Stop-Computer` 使用 WMI。 預設值為 **Packet** 。

此參數可接受的值為：

- **預設值** ： Windows 驗證。
- **None** ：沒有 COM 驗證。
- **Connect** ：連接層級 COM 驗證。
- **呼叫** ：呼叫層級 COM 驗證。
- 封 **包** ：封包層級 COM 驗證。
- **PacketIntegrity** ：封包完整性等級 COM 驗證。
- **PacketPrivacy** ：封包隱私權等級 COM 驗證。
- **未** 變更：與上一個命令相同。

如需此參數值的詳細資訊，請參閱 [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel)。

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

強制立即關閉電腦。

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

### -Impersonation

指定此 Cmdlet 呼叫 WMI 時要使用的模擬等級。 預設值為 [模擬 **]。**

`Stop-Computer` 使用 WMI。 此參數可接受的值為：

- **預設** 值：預設模擬。
- **匿名** ：隱藏呼叫端的身分識別。
- **識別** ：允許物件查詢呼叫端的認證。
- 模擬 **：允許** 物件使用呼叫端的認證。

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: Impersonate
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

指定要用來重新啟動電腦的通訊協定。 此參數可接受的值為： **WSMan** 和 **DCOM** 。 預設值為 **DCOM** 。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: DCOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定為執行此命令可建立的最大同時連線數。
若省略此參數，或輸入值為 0，則會使用預設值 32。

節流限制僅適用於目前命令，不適用於工作階段或電腦。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WsmanAuthentication

指定當此 Cmdlet 使用 WSMan 通訊協定時，用來驗證使用者認證的機制。 預設值為 **Default** 。

此參數可接受的值為：

- 基本
- CredSSP
- 預設
- Digest
- Kerberos
- Negotiate。

如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

> [!CAUTION]
> 認證安全性服務提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。 此機制會使得遠端作業的安全性風險變高。 若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
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

### 無

您無法透過管道傳送輸入至此 Cmdlet。

## 輸出

### 無或 System.Management.Automation.RemotingJob

如果您指定 **AsJob** 參數，Cmdlet 會傳回 **system.management.automation.remotingjob** 物件。 否則，它不會產生任何輸出。

## 注意

此 Cmdlet 會使用 **Win32_OperatingSystem** WMI 類別的 **Win32Shutdown** 方法。 此方法需要針對用來重新開機電腦的使用者帳戶啟用 **SeShutdownPrivilege** 許可權。

## 相關連結

[Add-Computer](Add-Computer.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Remove-Computer](Remove-Computer.md)

[Rename-Computer](Rename-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Restore-Computer](Restore-Computer.md)

[Test-Connection](Test-Connection.md)
