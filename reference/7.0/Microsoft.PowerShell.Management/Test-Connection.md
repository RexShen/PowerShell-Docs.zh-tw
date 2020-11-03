---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 04e9e47055610ef8120b44f2418a0843e5901062
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201580"
---
# Test-Connection

## 概要
將 ICMP echo 要求封包或 ping 傳送至一或多部電腦。

## SYNTAX

### DefaultPing (預設) 

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### RepeatPing

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### MtuSizeDetect

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### 追蹤路由

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### TcpPort

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## DESCRIPTION

此 `Test-Connection` Cmdlet 會將網際網路控制訊息通訊協定 (ICMP) echo 要求封包或 ping 傳送至一或多部遠端電腦，並傳迴響應回應回復。 您可以使用這個 Cmdlet 來判斷是否可以透過 IP 網路來連線到特定電腦。

您可以使用的參數 `Test-Connection` 來指定傳送和接收電腦、以背景工作方式執行命令、設定超時和偵測次數，以及設定連接和驗證。

不同于熟悉的 **ping** 命令， `Test-Connection` 會傳回您可以在 PowerShell 中調查的 **TestConnectionCommand + PingStatus** 物件。 **Quiet** 參數會針對每個已測試的連接，傳回 **system.string 物件中** 的 **布林** 值。 如果測試了多個連接，則會傳回 **布林** 值的陣列。

## 範例

### 範例1：將 echo 要求傳送至遠端電腦

此範例會將 echo 要求封包從本機電腦傳送到 Server01 電腦。

```powershell
Test-Connection -TargetName Server01 -IPv4
```

```Output
   Destination: Server01

Ping Source           Address                   Latency BufferSize Status
                                                   (ms)        (B)
---- ------           -------                   ------- ---------- ------
   1 ADMIN1           10.59.137.44                   24         32 Success
   2 ADMIN1           10.59.137.44                   39         32 Success
   3 ADMIN1           *                               *          * TimedOut
   4 ADMIN1           10.59.137.44                   28         32 Success
```

`Test-Connection` 使用 **TargetName** 參數指定 Server01 電腦。 **IPv4** 參數指定測試的通訊協定。

系統會將一連串的 **TestConnectionCommand + PingStatus** 物件傳送到輸出資料流程，從目的電腦的每個 ping 回復都有一個物件。

### 範例2：傳送 echo 要求至數部電腦

此範例會將 ping 從本機電腦傳送到多部遠端電腦。

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### 範例3：使用參數自訂測試命令

這個範例會使用的參數 `Test-Connection` 來自訂命令。 本機電腦會將 ping 測試傳送至遠端電腦。

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

`Test-Connection` 使用 **TargetName** 參數指定 Server01。 **Count** 參數指定將三個 ping 傳送至 Server01 電腦， **延遲** 間隔為2秒。

當偵測回應預期需要比平常更長的躍點數目或高流量網路情況時，您可能會使用這些選項。

### 範例4：以背景工作的形式執行測試

此範例示範如何以 `Test-Connection` PowerShell 背景工作執行命令。

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

此 `Start-Job` 命令會使用 `Test-Connection` Cmdlet 來偵測企業中的許多電腦。
**TargetName** 參數的值是 `Get-Content` 從檔案讀取電腦名稱稱清單的命令 `Servers.txt` 。 此命令會使用 `Start-Job` Cmdlet 以背景工作方式執行命令，並將工作儲存在 `$job` 變數中。

在 `Receive-Job` `-Wait` 作業完成之前，會指示命令，然後取得結果，並將其儲存在 `$Results` 變數中。

### 範例5：只有在連接測試成功時才建立會話

此範例只會在至少一個傳送至電腦的 ping 成功時，才會在 Server01 電腦上建立會話。

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

`Test-Connection`Cmdlet 會 `Server01` 使用提供的 **Quiet** 參數來 ping 電腦。
`$True`如果四個 ping 中有任何一個成功，則產生的值為。 如果 ping 都沒有成功，則值為 `$False` 。

如果命令傳回的 `Test-Connection` 值為 `$True` ，則命令會使用 `New-PSSession` Cmdlet 來建立 **PSSession** 。

### 範例6：使用追蹤路由參數

在 PowerShell 6.0 中引進的 **追蹤路由** 參數會將本機電腦和您指定的遠端目的地之間的路由對應到您以 **TargetName** 參數指定的路由。

```powershell
Test-Connection -TargetName www.google.com -Traceroute
```

```Output
   Target: google.com

Hop Hostname                  Ping Latency Status           Source       TargetAddress
                                      (ms)
--- --------                  ---- ------- ------           ------       -------------
  1 172.20.0.1                   1       4 Success          Lira         172.217.9.174
  1 172.20.0.1                   2       3 Success          Lira         172.217.9.174
  1 172.20.0.1                   3       2 Success          Lira         172.217.9.174
  2 12.108.153.193               1       3 Success          Lira         172.217.9.174
  2 12.108.153.193               2       3 Success          Lira         172.217.9.174
  2 12.108.153.193               3       2 Success          Lira         172.217.9.174
  3 12.244.85.177                1      11 Success          Lira         172.217.9.174
  3 12.244.85.177                2      12 Success          Lira         172.217.9.174
  3 12.244.85.177                3      12 Success          Lira         172.217.9.174
  4 *                            1      14 DestinationNetw… Lira         172.217.9.174
  4 *                            2       * TimedOut         Lira         172.217.9.174
  4 *                            3      20 DestinationNetw… Lira         172.217.9.174
  5 *                            1       * TimedOut         Lira         172.217.9.174
  5 *                            2      15 DestinationNetw… Lira         172.217.9.174
  5 *                            3       * TimedOut         Lira         172.217.9.174
  6 *                            1      18 DestinationNetw… Lira         172.217.9.174
  6 *                            2       * TimedOut         Lira         172.217.9.174
  6 *                            3      16 DestinationNetw… Lira         172.217.9.174
  7 *                            1       * TimedOut         Lira         172.217.9.174
  7 *                            2       * TimedOut         Lira         172.217.9.174
  7 *                            3       * TimedOut         Lira         172.217.9.174
  8 *                            1       * TimedOut         Lira         172.217.9.174
  8 *                            2       * TimedOut         Lira         172.217.9.174
  8 *                            3       * TimedOut         Lira         172.217.9.174
  9 *                            1       * TimedOut         Lira         172.217.9.174
  9 *                            2       * TimedOut         Lira         172.217.9.174
  9 *                            3       * TimedOut         Lira         172.217.9.174
 10 *                            1       * TimedOut         Lira         172.217.9.174
 10 *                            2       * TimedOut         Lira         172.217.9.174
 10 *                            3       * TimedOut         Lira         172.217.9.174
 11 172.217.9.174                1      23 Success          Lira         172.217.9.174
 11 172.217.9.174                2      21 Success          Lira         172.217.9.174
 11 172.217.9.174                3      22 Success          Lira         172.217.9.174
```

此 `Test-Connection` 命令會使用 **追蹤路由** 參數來呼叫。 結果（即 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` 物件）會輸出至 **成功** 輸出資料流程。

## PARAMETERS

### -BufferSize

指定與這個命令一起傳送之緩衝區的大小 (單位為位元組)。 預設值為 32。

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -重複

導致 Cmdlet 持續傳送 ping 要求。 此參數不能與 **Count** 參數一起使用。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RepeatPing
Aliases: Continuous

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Count

指定要傳送的回應要求數目。 預設值為 4。

```yaml
Type: System.Int32
Parameter Sets: DefaultPing
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### -Delay

指定 ping 的間隔 (單位為秒)。

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DontFragment

此參數會設定 IP 標頭中的「 **不要片段** 」旗標。 您可以使用此參數搭配 **BufferSize** 參數來測試路徑 MTU 大小。 如需路徑 MTU 的詳細資訊，請參閱維琪百科中的 [PATH Mtu Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) 文章。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -IPv4

強制 Cmdlet 將 IPv4 通訊協定用於測試。

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

### -IPv6

強制 Cmdlet 針對測試使用 IPv6 通訊協定。

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

### -MaxHops

設定可傳送 ICMP 要求訊息的躍點數目上限。 預設值是由作業系統所控制。 Windows 10 的預設值為128躍點。

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -Ping

導致 Cmdlet 執行 ping 測試。 這是 Cmdlet 的預設模式 `Test-Connection` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

**Quiet** 參數會傳回 **布林** 值。 使用此參數會隱藏所有錯誤。

每個測試的連接都會傳回一個 **布林** 值。 如果 **TargetName** 參數指定多部電腦，則會傳回 **布林** 值的陣列。

如果對指定目標的 **任何** 偵測成功， `$True` 則會傳回。

如果指定目標的 **所有** ping 都失敗， `$False` 則會傳回。

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

### -ResolveDestination

導致 Cmdlet 嘗試解析目標的 DNS 名稱。 搭配 **追蹤路由** 參數使用時，如果可能的話，也會取出所有轉送主機的 DNS 名稱。

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

### -Source

指定 ping 之來源電腦的名稱。 請以逗號分隔的清單方式輸入電腦名稱。 預設是本機電腦。

**注意：** 此參數在 PowerShell 版本6和更新版本中無法運作。
提供此參數將不會影響此命令。

```yaml
Type: System.String
Parameter Sets: DefaultPing, RepeatPing, TraceRoute, TcpPort
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetName

指定要測試) 的電腦 (。 請輸入電腦名稱或輸入 IPv4 或 IPv6 格式的 IP 位址。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ComputerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -TimeoutSeconds

設定測試的超時值。 如果在超時時間過期之前未收到回應，測試就會失敗。 預設為五秒鐘。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5 seconds
Accept pipeline input: False
Accept wildcard characters: False
```

### -追蹤路由

導致 Cmdlet 進行追蹤路由測試。 使用這個參數時，此 Cmdlet 會傳回 `TestConnectionCommand+TraceStatus` 物件。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TraceRoute
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -MtuSize

這個參數是用來探索 Path MTU 大小。 Cmdlet 會傳回 **PingReply # MTUSize** 物件，其中包含目標的路徑 MTU 大小。 如需路徑 MTU 的詳細資訊，請參閱維琪百科中的 [PATH Mtu Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) 文章。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MtuSizeDetect
Aliases: MtuSizeDetect

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -TcpPort

指定要在 TCP 連接測試中使用之目標上的 TCP 通訊埠編號。 此 Cmdlet 會嘗試對目標上的指定埠進行 TCP 連接。

如果可以建立連接， `$True` 則會傳回。

如果無法進行連接， `$False` 則會傳回。

```yaml
Type: System.Int32
Parameter Sets: TcpPort
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法透過管道傳送輸入至此 Cmdlet。

## 輸出

### TestConnectionCommand + PingStatus、TestConnectionCommand + TraceStatus、Boolean、TestConnectionCommand + PingMtuStatus

根據預設，會 `Test-Connection` 針對每個偵測回復傳回 **TestConnectionCommand + PingStatus** 物件。

如果您指定 **追蹤路由** 參數，則此 Cmdlet 會在路由中傳回每個偵測回復的 **TestConnectionCommand + TraceStatus** 物件。

如果您指定 **Quiet** 或 **TcpPort** 參數，則會傳回 **布林** 值。 如果測試了多個連接，則會傳回 **布林** 值的陣列。

## 注意

## 相關連結

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
