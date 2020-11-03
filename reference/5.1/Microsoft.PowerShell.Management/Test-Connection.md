---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: a8d3923db69a20cfada58391944b592cf999e6ef
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203455"
---
# Test-Connection

## 概要
將 ICMP echo 要求封包或 ping 傳送至一或多部電腦。

## SYNTAX

### Default (預設值)

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-TimeToLive <Int32>]
 [-Delay <Int32>] [<CommonParameters>]
```

### 來源

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Credential <PSCredential>] [-Source] <String[]> [-Impersonation <ImpersonationLevel>]
 [-ThrottleLimit <Int32>] [-TimeToLive <Int32>] [-Delay <Int32>] [<CommonParameters>]
```

### Quiet

```
Test-Connection [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-TimeToLive <Int32>] [-Delay <Int32>] [-Quiet]
 [<CommonParameters>]
```

## DESCRIPTION

此 `Test-Connection` Cmdlet 會將網際網路控制訊息通訊協定 (ICMP) echo 要求封包或 ping 傳送至一或多部遠端電腦，並傳迴響應回應回復。 您可以使用這個 Cmdlet 來判斷是否可以透過 IP 網路來連線到特定電腦。

您可以使用的參數 `Test-Connection` 來指定傳送和接收電腦、以背景工作方式執行命令、設定超時和偵測次數，以及設定連接和驗證。

不同于熟悉的 **ping** 命令， `Test-Connection` 會傳回您可以在 PowerShell 中調查的 **Win32_PingStatus** 物件。 **Quiet** 參數會針對每個已測試的連接，傳回 **system.string 物件中** 的 **布林** 值。 如果測試了多個連接，則會傳回 **布林** 值的陣列。

## 範例

### 範例1：將 echo 要求傳送至遠端電腦

此範例會將 echo 要求封包從本機電腦傳送到 Server01 電腦。

```powershell
Test-Connection -ComputerName Server01
```

```Output
Source        Destination     IPV4Address     IPV6Address  Bytes    Time(ms)
------        -----------     -----------     -----------  -----    --------
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       1
```

`Test-Connection` 使用 **ComputerName** 參數來指定 Server01 電腦。

### 範例2：傳送 echo 要求至數部電腦

此範例會將 ping 從本機電腦傳送到多部遠端電腦。

```powershell
Test-Connection -ComputerName Server01, Server02, Server12
```

### 範例3：從數部電腦傳送 echo 要求到電腦

此範例會將來自不同來源電腦的 ping 傳送到單一遠端電腦 Server01。

```powershell
Test-Connection -Source Server02, Server12, localhost -ComputerName Server01 -Credential Domain01\Admin01
```

`Test-Connection` 使用 **Credential** 參數來指定具有從來源電腦傳送 ping 要求之許可權的使用者認證。 請使用這個命令格式來測試來自多個點的連線延遲。

### 範例4：使用參數自訂測試命令

這個範例會使用的參數 `Test-Connection` 來自訂命令。 本機電腦會將 ping 測試傳送至遠端電腦。

```powershell
Test-Connection -ComputerName Server01 -Count 3 -Delay 2 -TTL 255 -BufferSize 256 -ThrottleLimit 32
```

`Test-Connection` 使用 **ComputerName** 參數來指定 Server01。 **Count** 參數指定將三個 ping 傳送至 Server01 電腦， **延遲** 間隔為2秒。

當偵測回應預期需要比平常更長的躍點數目或高流量網路情況時，您可能會使用這些選項。

### 範例5：以背景工作的形式執行測試

此範例示範如何以 `Test-Connection` PowerShell 背景工作執行命令。

```powershell
$job = Test-Connection -ComputerName (Get-Content Servers.txt) -AsJob
if ($job.JobStateInfo.State -ne "Running") {$Results = Receive-Job $job}
```

`Test-Connection`命令會 ping 企業中的許多電腦。 **ComputerName** 參數的值是 `Get-Content` 從讀取電腦名稱稱清單的命令 `Servers.txt file` 。 此命令會使用 **AsJob** 參數將命令當作背景工作來執行，並將工作儲存在變數中 `$job` 。

此 `if` 命令會檢查作業是否仍在執行中。 如果工作未執行，則會 `Receive-Job` 取得結果，並將其儲存在 `$Results` 變數中。

### 範例6：使用認證偵測遠端電腦

此命令會使用 `Test-Connection` Cmdlet 來 ping 遠端電腦。

```powershell
Test-Connection Server55 -Credential Domain55\User01 -Impersonation Identify
```

此命令會使用 **Credential** 參數來指定具有 ping 遠端電腦之許可權的使用者帳戶，以及 **模擬參數將** 模擬等級變更為 **可識別** 的使用者帳戶。

### 範例7：只有在連接測試成功時才建立會話

此範例只會在至少一個傳送至電腦的 ping 成功時，才會在 Server01 電腦上建立會話。

```powershell
if (Test-Connection -ComputerName Server01 -Quiet) {New-PSSession Server01}
```

此 `if` 命令會使用 `Test-Connection` Cmdlet 來偵測 Server01 電腦。 此命令會使用 **Quiet** 參數，它會傳回 **布林** 值，而不是 **Win32_PingStatus** 物件。 `$True`如果四個 ping 中有任何一個成功，則值為，否則為 `$False` 。

如果命令傳回的 `Test-Connection` 值為 `$True` ，則命令會使用 `New-PSSession` Cmdlet 來建立 **PSSession** 。

## PARAMETERS

### -AsJob

指出此 Cmdlet 會以背景工作的形式執行。

若要使用這個參數，本機電腦和遠端電腦必須設定為進行遠端處理，而在 Windows Vista 和更新版本的 Windows 作業系統上，您必須使用 [以 **系統管理員身分執行** ] 選項開啟 PowerShell。 如需詳細資訊，請參閱[about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md)。

當您指定 **AsJob** 參數時，此命令會立即傳回代表背景工作的物件。 工作完成後，您可以繼續在工作階段中工作。 工作會在本機電腦上建立，而來自遠端電腦的結果則會自動傳回到本機電腦。 若要取得工作結果，請使用 `Receive-Job` Cmdlet。

如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) 和 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md)。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default, Source
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -BufferSize

指定與這個命令一起傳送之緩衝區的大小 (單位為位元組)。 預設值為 32。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定要 ping 的電腦。 請輸入電腦名稱或輸入 IPv4 或 IPv6 格式的 IP 位址。 不允許使用萬用字元。 這是必要參數。

此參數不依賴 PowerShell 遠端功能。 即使您的電腦未設定為執行遠端命令，您也可以使用 **ComputerName** 參數。

> [!NOTE]
> **ComputerName** 參數已重新命名為 PowerShell 6.0 和更新版本中的 **TargetName** 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, IPAddress, __SERVER, Server, Destination

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Count

指定要傳送的回應要求數目。 預設值為 4。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定具有從來源電腦傳送 ping 要求之權限的使用者帳戶。 輸入使用者名稱（例如 User01 或 Domain01\User01），或輸入 **PSCredential** 物件，例如 Cmdlet 中的物件 `Get-Credential` 。

只有當命令中使用 **Source** 參數時， **Credential** 參數才有效。 認證不會影響目的地電腦。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Source
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DcomAuthentication

指定此 Cmdlet 與 WMI 搭配使用的驗證層級。
`Test-Connection` 使用 WMI。
此參數可接受的值為：

- **Default** 。 Windows 驗證
- **None** ： 沒有 COM 驗證。
- **連接** 。 連線等級 COM 驗證。
- **呼叫** 。 呼叫等級 COM 驗證。
- 封 **包** 。 封包層級 COM 驗證
- **PacketIntegrity** 。 封包完整性等級 COM 驗證。
- **PacketPrivacy** 。 封包隱私權層級 COM 驗證
- **未** 變更。 與前一個命令相同

預設值是列舉值為 **4** 的封 **包** 。 如需此參數值的詳細資訊，請參閱 [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel) 列舉。

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet (enumerated value of 4)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Delay

指定 ping 的間隔 (單位為秒)。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1 (second)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Impersonation

指定此 Cmdlet 呼叫 WMI 時要使用的模擬等級。 `Test-Connection` 使用 WMI。

此參數可接受的值如下：

- **Default** 。 預設模擬。
- **匿名** 。 隱藏呼叫端的身分識別。
- **識別** 。 允許物件查詢呼叫端的認證。
- **Impersonate** 模擬。 允許物件使用呼叫端的認證。

預設值為 [模擬 **]。**

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

指定通訊協定。 此參數可接受的值為 DCOM 和 WSMan。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

**Quiet** 參數會在 **system.string 物件中** 傳回 **布林** 值。 使用此參數會隱藏所有錯誤。

每個測試的連接都會傳回一個 **布林** 值。 如果 **ComputerName** 參數指定多部電腦，則會傳回 **布林** 值的陣列。

如果 **任何** ping 成功， `$True` 則會傳回。

如果 **所有** ping 都失敗， `$False` 則會傳回。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Quiet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

指定 ping 之來源電腦的名稱。 請以逗號分隔的清單方式輸入電腦名稱。 預設是本機電腦。

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: FCN, SRC

Required: True
Position: 1
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定為執行此命令可建立的最大同時連線數。
若省略此參數，或輸入值為 0，則會使用預設值 32。

節流限制僅適用於目前命令，不適用於工作階段或電腦。

```yaml
Type: System.Int32
Parameter Sets: Default, Source
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeToLive

指定封包可以轉寄的最長時間。 針對閘道、路由器等中的每個躍點， **TimeToLive** 值會減少一。 若為零，則會捨棄封包，並傳回錯誤。
在 **Windows** 中，預設值是 **128** 。 **TimeToLive** 參數的別名是 **TTL** 。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TTL

Required: False
Position: Named
Default value: 128 in Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### -WsmanAuthentication

指定當此 Cmdlet 使用 WSMan 通訊協定時，用來驗證使用者認證的機制。
此參數可接受的值為：

- 基本
- CredSSP
- 預設
- Digest
- Kerberos
- Negotiate。

預設值為 Default。

如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0)。

注意：認證安全性服務提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，它是針對需要在多個資源（例如存取遠端網路共用）進行驗證的命令所設計。
此機制會使得遠端作業的安全性風險變高。
若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

此參數是在 Windows PowerShell 3.0 引進。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法透過管道傳送輸入至此 Cmdlet。

## 輸出

### System.management.managementobject # root\cimv2\ Win32_PingStatus，，System.object. System.management.automation.remotingjob，system.string

如果您指定 **AsJob** 參數，此 Cmdlet 會傳回工作物件。

如果您指定 **Quiet** 參數，它會傳回 **布林** 值。 如果測試了多個連接，則會傳回 **布林** 值的陣列。 否則，會傳回 `Test-Connection` 每個 ping 的 **Win32_PingStatus** 物件。

## 注意

此 Cmdlet 會使用 **Win32_PingStatus** 類別。 `Get-WMIObject Win32_PingStatus`命令相當於 `Test-Connection` 命令。

PowerShell 3.0 中引進了 **Source** 參數集。

## 相關連結

[Add-Computer](Add-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
