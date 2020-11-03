---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 54ba1d7db60db7b4bb64f3161bba9c1fba124219
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202384"
---
# Test-Connection

## 概要
將 ICMP echo 要求封包或 ping 傳送至一或多部電腦。

## SYNTAX

### PingCount (預設) 

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Count <Int32>] [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### PingContinues

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-Continues] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### DetectionOfMTUSize

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -MTUSizeDetect [-Quiet] [<CommonParameters>]
```

### 追蹤路由

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-TimeoutSeconds <Int32>] [-TargetName] <String[]> -Traceroute [-Quiet] [<CommonParameters>]
```

### ConnectionByTCPPort

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -TCPPort <Int32> [-Quiet] [<CommonParameters>]
```

## DESCRIPTION

此 `Test-Connection` Cmdlet 會將網際網路控制訊息通訊協定 (ICMP) echo 要求封包或 ping 傳送至一或多部遠端電腦，並傳迴響應回應回復。 您可以使用這個 Cmdlet 來判斷是否可以透過 IP 網路來連線到特定電腦。

您可以使用的參數 `Test-Connection` 來指定傳送和接收電腦、以背景工作方式執行命令、設定超時和偵測次數，以及設定連接和驗證。

不同于熟悉的 **ping** 命令， `Test-Connection` 會傳回您可以在 PowerShell 中調查的 **TestConnectionCommand + PingReport** 物件。 **Quiet** 參數會針對每個已測試的連接，傳回 **system.string 物件中** 的 **布林** 值。 如果測試了多個連接，則會傳回 **布林** 值的陣列。

## 範例

### 範例1：將 echo 要求傳送至遠端電腦

此範例會將 echo 要求封包從本機電腦傳送到 Server01 電腦。

```powershell
Test-Connection -TargetName Server01 -IPv4
```

```Output
Pinging Server01 [10.59.137.44] with 32 bytes of data:
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Ping complete.

Source     Destination Replies
------     ----------- -------
Server01   Server01    {System.Net.NetworkInformation.PingReply, System.Net.NetworkInformation ...
```

`Test-Connection` 使用 **TargetName** 參數指定 Server01 電腦。 **IPv4** 參數指定測試的通訊協定。

將 **TestConnectionCommand + PingReport** 物件傳送至 **成功** 資料流程時，會將 Ping 輸出傳送至 **資訊** 串流。 如需有關輸出資料流程的詳細資訊，請參閱 [about_Redirection](../microsoft.powershell.core/about/about_redirection.md)。

### 範例2：傳送 echo 要求至數部電腦

此範例會將 ping 從本機電腦傳送到多部遠端電腦。

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### 範例3：從數部電腦傳送 echo 要求到電腦

此範例會將來自不同來源電腦的 ping 傳送到單一遠端電腦 Server01。

```powershell
Test-Connection -Source Server02, Server12, localhost -TargetName Server01
```

請使用這個命令格式來測試來自多個點的連線延遲。

### 範例4：使用參數自訂測試命令

這個範例會使用的參數 `Test-Connection` 來自訂命令。 本機電腦會將 ping 測試傳送至遠端電腦。

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

`Test-Connection` 使用 **TargetName** 參數指定 Server01。 **Count** 參數指定將三個 ping 傳送至 Server01 電腦， **延遲** 間隔為2秒。

當偵測回應預期需要比平常更長的躍點數目或高流量網路情況時，您可能會使用這些選項。

### 範例5：以背景工作的形式執行測試

此範例示範如何以 `Test-Connection` PowerShell 背景工作執行命令。

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content "Servers.txt") }
if ($job.JobStateInfo.State -ne "Running") { $Results = Receive-Job $job }
```

此 `Start-Job` 命令會使用 `Test-Connection` Cmdlet 來偵測企業中的許多電腦。
**TargetName** 參數的值是 `Get-Content` 從檔案讀取電腦名稱稱清單的命令 `Servers.txt` 。 此命令會使用 `Start-Job` Cmdlet 以背景工作方式執行命令，並將工作儲存在 `$job` 變數中。

此 `if` 命令會檢查作業是否仍在執行中。 如果工作未執行，則會 `Receive-Job` 取得結果，並將其儲存在 `$Results` 變數中。

### 範例6：只有在連接測試成功時才建立會話

此範例只會在至少一個傳送至電腦的 ping 成功時，才會在 Server01 電腦上建立會話。

```powershell
if (Test-Connection -TargetName Server01 -Quiet) {New-PSSession Server01}
```

此 `if` 命令會使用 `Test-Connection` Cmdlet 來偵測 Server01 電腦。 此命令會使用 **Quiet** 參數，它會傳回 **布林** 值，而不是 **TestConnectionCommand + PingReport** 物件。

`$True`如果四個 ping 中有任何一個成功，則值為。 如果 ping 都沒有成功，則值為 `$False` 。

如果命令傳回的 `Test-Connection` 值為 `$True` ，則命令會使用 `New-PSSession` Cmdlet 來建立 **PSSession** 。

### 範例7：使用追蹤路由參數

從 PowerShell 6.0 開始， **追蹤路由** 參數會將本機電腦和您指定的遠端目的地之間的路由對應到您以 **TargetName** 參數指定的路由。

```powershell
Test-Connection -TargetName www.microsoft.com -Traceroute | ForEach-Object {
  $_ | Format-Table Source, DestinationAddress, DestinationHost
  $_.Replies | ForEach-Object {
      $_ | Format-Table Hop, ReplyRouterAddress
      $_.PingReplies | Format-Table
  }
}
```

```Output
Tracing route to www.microsoft.com [96.6.27.90] over a maximum of 128 hops:
  1   0 ms   0 ms   0 ms   192.168.0.3 [192.168.0.3]
  2   0 ms   0 ms   0 ms   192.168.1.1 [192.168.1.1]
  3   3 ms   29 ms   4 ms   96.6.27.90 [96.6.27.90]
Trace complete.

Source      DestinationAddress DestinationHost   Replies
------      ------------------ ---------------   -------
SERVER01    96.6.27.90         www.microsoft.com {, , }

Hop ReplyRouterAddress
--- ------------------
  1 192.168.0.3

    Status Address      RoundtripTime Options Buffer
    ------ -------      ------------- ------- ------
TtlExpired 192.168.86.1             0         {}
TtlExpired 192.168.86.1             0         {}
TtlExpired 192.168.86.1             0         {}

Hop ReplyRouterAddress
--- ------------------
  2 192.168.1.1

    Status Address     RoundtripTime Options Buffer
    ------ -------     ------------- ------- ------
TtlExpired 192.168.1.1             0         {}
TtlExpired 192.168.1.1             0         {}
TtlExpired 192.168.1.1             0         {}

Hop ReplyRouterAddress
--- ------------------
  3 96.6.27.90

 Status Address    RoundtripTime Options                                   Buffer
 ------ -------    ------------- -------                                   ------
Success 96.6.27.90             3 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
Success 96.6.27.90             2 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
Success 96.6.27.90             4 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
```

此 `Test-Connection` 命令會使用 **追蹤路由** 參數。 結果（即 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` 物件）會透過管道傳送至 `ForEach-Object` Cmdlet。 `ForEach-Object` 建立包含的 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` 物件和後續物件的結構化輸出 `[System.Net.NetworkInformation.PingReply]` 。

## PARAMETERS

### -BufferSize

指定與這個命令一起傳送之緩衝區的大小 (單位為位元組)。 預設值為 32。

```yaml
Type: System.Int32
Parameter Sets: PingCount, PingContinues
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -Count

指定要傳送的回應要求數目。 預設值為 4。

```yaml
Type: System.Int32
Parameter Sets: PingCount
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
Parameter Sets: PingCount, PingContinues
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
Parameter Sets: PingCount, PingContinues
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
Parameter Sets: PingCount, PingContinues, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -Ping

使 Cmdlet 執行 ping 測試，這是預設動作。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingCount, PingContinues
Aliases:

Required: False
Position: Named
Default value: Ping test
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

**Quiet** 參數會在 **system.string 物件中** 傳回 **布林** 值。 使用此參數會隱藏所有錯誤。

每個測試的連接都會傳回一個 **布林** 值。 如果 **TargetName** 參數指定多部電腦，則會傳回 **布林** 值的陣列。

如果 **任何** ping 成功， `$True` 則會傳回。

如果 **所有** ping 都失敗， `$False` 則會傳回。

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

導致 Cmdlet 嘗試解析目標的 DNS 名稱。

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

```yaml
Type: System.String
Parameter Sets: PingCount, PingContinues, TraceRoute, ConnectionByTCPPort
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetName

指定要測試的電腦。 請輸入電腦名稱或輸入 IPv4 或 IPv6 格式的 IP 位址。 不允許使用萬用字元。 這是必要參數。 **ComputerName** 是此參數的別名。

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

### -TCPPort

指定要在 TCP 連接測試中使用之目標上的 TCP 通訊埠編號。 此 Cmdlet 會嘗試對目標上的指定埠進行 TCP 連接。

```yaml
Type: System.Int32
Parameter Sets: ConnectionByTCPPort
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
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

導致 Cmdlet 進行追蹤路由測試。 使用這個參數時，此 Cmdlet 會傳回 `TestConnectionCommand+TraceRouteResult` 物件。

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

### -繼續

導致 Cmdlet 持續傳送 ping 要求。 此參數不能與 **Count** 參數一起使用。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingContinues
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MTUSizeDetect

這個參數是用來探索 Path MTU 大小。 Cmdlet 會傳回 **PingReply # MTUSize** 物件，其中包含目標的路徑 MTU 大小。 如需路徑 MTU 的詳細資訊，請參閱維琪百科中的 [PATH Mtu Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) 文章。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetectionOfMTUSize
Aliases:

Required: True
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

### TestConnectionCommand + PingReport、TestConnectionCommand + TraceRouteResult、Boolean、PingReply # MTUSize

如果您指定 **Quiet** 參數，它會傳回 **布林** 值。 如果測試了多個連接，則會傳回 **布林** 值的陣列。 否則，會 `Test-Connection` 針對每個 ping 傳回 **TestConnectionCommand + PingReport** 物件。

## 注意

## 相關連結

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
