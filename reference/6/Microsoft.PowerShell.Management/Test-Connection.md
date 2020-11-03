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
# <span data-ttu-id="29f2b-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="29f2b-103">Test-Connection</span></span>

## <span data-ttu-id="29f2b-104">概要</span><span class="sxs-lookup"><span data-stu-id="29f2b-104">SYNOPSIS</span></span>
<span data-ttu-id="29f2b-105">將 ICMP echo 要求封包或 ping 傳送至一或多部電腦。</span><span class="sxs-lookup"><span data-stu-id="29f2b-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="29f2b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="29f2b-106">SYNTAX</span></span>

### <span data-ttu-id="29f2b-107">PingCount (預設) </span><span class="sxs-lookup"><span data-stu-id="29f2b-107">PingCount (Default)</span></span>

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Count <Int32>] [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="29f2b-108">PingContinues</span><span class="sxs-lookup"><span data-stu-id="29f2b-108">PingContinues</span></span>

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-Continues] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="29f2b-109">DetectionOfMTUSize</span><span class="sxs-lookup"><span data-stu-id="29f2b-109">DetectionOfMTUSize</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -MTUSizeDetect [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="29f2b-110">追蹤路由</span><span class="sxs-lookup"><span data-stu-id="29f2b-110">TraceRoute</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-TimeoutSeconds <Int32>] [-TargetName] <String[]> -Traceroute [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="29f2b-111">ConnectionByTCPPort</span><span class="sxs-lookup"><span data-stu-id="29f2b-111">ConnectionByTCPPort</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -TCPPort <Int32> [-Quiet] [<CommonParameters>]
```

## <span data-ttu-id="29f2b-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="29f2b-112">DESCRIPTION</span></span>

<span data-ttu-id="29f2b-113">此 `Test-Connection` Cmdlet 會將網際網路控制訊息通訊協定 (ICMP) echo 要求封包或 ping 傳送至一或多部遠端電腦，並傳迴響應回應回復。</span><span class="sxs-lookup"><span data-stu-id="29f2b-113">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="29f2b-114">您可以使用這個 Cmdlet 來判斷是否可以透過 IP 網路來連線到特定電腦。</span><span class="sxs-lookup"><span data-stu-id="29f2b-114">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="29f2b-115">您可以使用的參數 `Test-Connection` 來指定傳送和接收電腦、以背景工作方式執行命令、設定超時和偵測次數，以及設定連接和驗證。</span><span class="sxs-lookup"><span data-stu-id="29f2b-115">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="29f2b-116">不同于熟悉的 **ping** 命令， `Test-Connection` 會傳回您可以在 PowerShell 中調查的 **TestConnectionCommand + PingReport** 物件。</span><span class="sxs-lookup"><span data-stu-id="29f2b-116">Unlike the familiar **ping** command, `Test-Connection` returns a **TestConnectionCommand+PingReport** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="29f2b-117">**Quiet** 參數會針對每個已測試的連接，傳回 **system.string 物件中** 的 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="29f2b-117">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="29f2b-118">如果測試了多個連接，則會傳回 **布林** 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="29f2b-118">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="29f2b-119">範例</span><span class="sxs-lookup"><span data-stu-id="29f2b-119">EXAMPLES</span></span>

### <span data-ttu-id="29f2b-120">範例1：將 echo 要求傳送至遠端電腦</span><span class="sxs-lookup"><span data-stu-id="29f2b-120">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="29f2b-121">此範例會將 echo 要求封包從本機電腦傳送到 Server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="29f2b-121">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

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

<span data-ttu-id="29f2b-122">`Test-Connection` 使用 **TargetName** 參數指定 Server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="29f2b-122">`Test-Connection` uses the **TargetName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="29f2b-123">**IPv4** 參數指定測試的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="29f2b-123">The **IPv4** parameter specifies the protocol for the test.</span></span>

<span data-ttu-id="29f2b-124">將 **TestConnectionCommand + PingReport** 物件傳送至 **成功** 資料流程時，會將 Ping 輸出傳送至 **資訊** 串流。</span><span class="sxs-lookup"><span data-stu-id="29f2b-124">The ping output is sent to the **Information** stream while the **TestConnectionCommand+PingReport** object sent to the **Success** stream.</span></span> <span data-ttu-id="29f2b-125">如需有關輸出資料流程的詳細資訊，請參閱 [about_Redirection](../microsoft.powershell.core/about/about_redirection.md)。</span><span class="sxs-lookup"><span data-stu-id="29f2b-125">For more information about the output streams, see [about_Redirection](../microsoft.powershell.core/about/about_redirection.md).</span></span>

### <span data-ttu-id="29f2b-126">範例2：傳送 echo 要求至數部電腦</span><span class="sxs-lookup"><span data-stu-id="29f2b-126">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="29f2b-127">此範例會將 ping 從本機電腦傳送到多部遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="29f2b-127">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### <span data-ttu-id="29f2b-128">範例3：從數部電腦傳送 echo 要求到電腦</span><span class="sxs-lookup"><span data-stu-id="29f2b-128">Example 3: Send echo requests from several computers to a computer</span></span>

<span data-ttu-id="29f2b-129">此範例會將來自不同來源電腦的 ping 傳送到單一遠端電腦 Server01。</span><span class="sxs-lookup"><span data-stu-id="29f2b-129">This example sends pings from different source computers to a single remote computer, Server01.</span></span>

```powershell
Test-Connection -Source Server02, Server12, localhost -TargetName Server01
```

<span data-ttu-id="29f2b-130">請使用這個命令格式來測試來自多個點的連線延遲。</span><span class="sxs-lookup"><span data-stu-id="29f2b-130">Use this command format to test the latency of connections from multiple points.</span></span>

### <span data-ttu-id="29f2b-131">範例4：使用參數自訂測試命令</span><span class="sxs-lookup"><span data-stu-id="29f2b-131">Example 4: Use parameters to customize the test command</span></span>

<span data-ttu-id="29f2b-132">這個範例會使用的參數 `Test-Connection` 來自訂命令。</span><span class="sxs-lookup"><span data-stu-id="29f2b-132">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="29f2b-133">本機電腦會將 ping 測試傳送至遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="29f2b-133">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

<span data-ttu-id="29f2b-134">`Test-Connection` 使用 **TargetName** 參數指定 Server01。</span><span class="sxs-lookup"><span data-stu-id="29f2b-134">`Test-Connection` uses the **TargetName** parameter to specify Server01.</span></span> <span data-ttu-id="29f2b-135">**Count** 參數指定將三個 ping 傳送至 Server01 電腦， **延遲** 間隔為2秒。</span><span class="sxs-lookup"><span data-stu-id="29f2b-135">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="29f2b-136">當偵測回應預期需要比平常更長的躍點數目或高流量網路情況時，您可能會使用這些選項。</span><span class="sxs-lookup"><span data-stu-id="29f2b-136">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="29f2b-137">範例5：以背景工作的形式執行測試</span><span class="sxs-lookup"><span data-stu-id="29f2b-137">Example 5: Run a test as a background job</span></span>

<span data-ttu-id="29f2b-138">此範例示範如何以 `Test-Connection` PowerShell 背景工作執行命令。</span><span class="sxs-lookup"><span data-stu-id="29f2b-138">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content "Servers.txt") }
if ($job.JobStateInfo.State -ne "Running") { $Results = Receive-Job $job }
```

<span data-ttu-id="29f2b-139">此 `Start-Job` 命令會使用 `Test-Connection` Cmdlet 來偵測企業中的許多電腦。</span><span class="sxs-lookup"><span data-stu-id="29f2b-139">The `Start-Job` command uses the `Test-Connection` cmdlet to ping many computers in an enterprise.</span></span>
<span data-ttu-id="29f2b-140">**TargetName** 參數的值是 `Get-Content` 從檔案讀取電腦名稱稱清單的命令 `Servers.txt` 。</span><span class="sxs-lookup"><span data-stu-id="29f2b-140">The value of the **TargetName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="29f2b-141">此命令會使用 `Start-Job` Cmdlet 以背景工作方式執行命令，並將工作儲存在 `$job` 變數中。</span><span class="sxs-lookup"><span data-stu-id="29f2b-141">The command uses the `Start-Job` cmdlet to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="29f2b-142">此 `if` 命令會檢查作業是否仍在執行中。</span><span class="sxs-lookup"><span data-stu-id="29f2b-142">The `if` command checks to see that the job isn't still running.</span></span> <span data-ttu-id="29f2b-143">如果工作未執行，則會 `Receive-Job` 取得結果，並將其儲存在 `$Results` 變數中。</span><span class="sxs-lookup"><span data-stu-id="29f2b-143">If the job isn't running, `Receive-Job` gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="29f2b-144">範例6：只有在連接測試成功時才建立會話</span><span class="sxs-lookup"><span data-stu-id="29f2b-144">Example 6: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="29f2b-145">此範例只會在至少一個傳送至電腦的 ping 成功時，才會在 Server01 電腦上建立會話。</span><span class="sxs-lookup"><span data-stu-id="29f2b-145">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -TargetName Server01 -Quiet) {New-PSSession Server01}
```

<span data-ttu-id="29f2b-146">此 `if` 命令會使用 `Test-Connection` Cmdlet 來偵測 Server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="29f2b-146">The `if` command uses the `Test-Connection` cmdlet to ping the Server01 computer.</span></span> <span data-ttu-id="29f2b-147">此命令會使用 **Quiet** 參數，它會傳回 **布林** 值，而不是 **TestConnectionCommand + PingReport** 物件。</span><span class="sxs-lookup"><span data-stu-id="29f2b-147">The command uses the **Quiet** parameter, which returns a **Boolean** value, instead of a **TestConnectionCommand+PingReport** object.</span></span>

<span data-ttu-id="29f2b-148">`$True`如果四個 ping 中有任何一個成功，則值為。</span><span class="sxs-lookup"><span data-stu-id="29f2b-148">The value is `$True` if any of the four pings succeed.</span></span> <span data-ttu-id="29f2b-149">如果 ping 都沒有成功，則值為 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="29f2b-149">If none of the pings succeed, the value is `$False`.</span></span>

<span data-ttu-id="29f2b-150">如果命令傳回的 `Test-Connection` 值為 `$True` ，則命令會使用 `New-PSSession` Cmdlet 來建立 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="29f2b-150">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession** .</span></span>

### <span data-ttu-id="29f2b-151">範例7：使用追蹤路由參數</span><span class="sxs-lookup"><span data-stu-id="29f2b-151">Example 7: Use the Traceroute parameter</span></span>

<span data-ttu-id="29f2b-152">從 PowerShell 6.0 開始， **追蹤路由** 參數會將本機電腦和您指定的遠端目的地之間的路由對應到您以 **TargetName** 參數指定的路由。</span><span class="sxs-lookup"><span data-stu-id="29f2b-152">Beginning in PowerShell 6.0, the **Traceroute** parameter maps a route between the local computer and the remote destination you specify with the **TargetName** parameter.</span></span>

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

<span data-ttu-id="29f2b-153">此 `Test-Connection` 命令會使用 **追蹤路由** 參數。</span><span class="sxs-lookup"><span data-stu-id="29f2b-153">The `Test-Connection` command uses the **Traceroute** parameter.</span></span> <span data-ttu-id="29f2b-154">結果（即 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` 物件）會透過管道傳送至 `ForEach-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="29f2b-154">The results, which are `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` objects, are piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="29f2b-155">`ForEach-Object` 建立包含的 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` 物件和後續物件的結構化輸出 `[System.Net.NetworkInformation.PingReply]` 。</span><span class="sxs-lookup"><span data-stu-id="29f2b-155">`ForEach-Object` creates a structured output of the contained `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` objects and subsequent `[System.Net.NetworkInformation.PingReply]` objects.</span></span>

## <span data-ttu-id="29f2b-156">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="29f2b-156">PARAMETERS</span></span>

### <span data-ttu-id="29f2b-157">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="29f2b-157">-BufferSize</span></span>

<span data-ttu-id="29f2b-158">指定與這個命令一起傳送之緩衝區的大小 (單位為位元組)。</span><span class="sxs-lookup"><span data-stu-id="29f2b-158">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="29f2b-159">預設值為 32。</span><span class="sxs-lookup"><span data-stu-id="29f2b-159">The default value is 32.</span></span>

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

### <span data-ttu-id="29f2b-160">-Count</span><span class="sxs-lookup"><span data-stu-id="29f2b-160">-Count</span></span>

<span data-ttu-id="29f2b-161">指定要傳送的回應要求數目。</span><span class="sxs-lookup"><span data-stu-id="29f2b-161">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="29f2b-162">預設值為 4。</span><span class="sxs-lookup"><span data-stu-id="29f2b-162">The default value is 4.</span></span>

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

### <span data-ttu-id="29f2b-163">-Delay</span><span class="sxs-lookup"><span data-stu-id="29f2b-163">-Delay</span></span>

<span data-ttu-id="29f2b-164">指定 ping 的間隔 (單位為秒)。</span><span class="sxs-lookup"><span data-stu-id="29f2b-164">Specifies the interval between pings, in seconds.</span></span>

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

### <span data-ttu-id="29f2b-165">-DontFragment</span><span class="sxs-lookup"><span data-stu-id="29f2b-165">-DontFragment</span></span>

<span data-ttu-id="29f2b-166">此參數會設定 IP 標頭中的「 **不要片段** 」旗標。</span><span class="sxs-lookup"><span data-stu-id="29f2b-166">This parameter sets the **Don't Fragment** flag in the IP header.</span></span> <span data-ttu-id="29f2b-167">您可以使用此參數搭配 **BufferSize** 參數來測試路徑 MTU 大小。</span><span class="sxs-lookup"><span data-stu-id="29f2b-167">You can use this parameter with the **BufferSize** parameter to test the Path MTU size.</span></span> <span data-ttu-id="29f2b-168">如需路徑 MTU 的詳細資訊，請參閱維琪百科中的 [PATH Mtu Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) 文章。</span><span class="sxs-lookup"><span data-stu-id="29f2b-168">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="29f2b-169">-IPv4</span><span class="sxs-lookup"><span data-stu-id="29f2b-169">-IPv4</span></span>

<span data-ttu-id="29f2b-170">強制 Cmdlet 將 IPv4 通訊協定用於測試。</span><span class="sxs-lookup"><span data-stu-id="29f2b-170">Forces the cmdlet to use the IPv4 protocol for the test.</span></span>

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

### <span data-ttu-id="29f2b-171">-IPv6</span><span class="sxs-lookup"><span data-stu-id="29f2b-171">-IPv6</span></span>

<span data-ttu-id="29f2b-172">強制 Cmdlet 針對測試使用 IPv6 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="29f2b-172">Forces the cmdlet to use the IPv6 protocol for the test.</span></span>

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

### <span data-ttu-id="29f2b-173">-MaxHops</span><span class="sxs-lookup"><span data-stu-id="29f2b-173">-MaxHops</span></span>

<span data-ttu-id="29f2b-174">設定可傳送 ICMP 要求訊息的躍點數目上限。</span><span class="sxs-lookup"><span data-stu-id="29f2b-174">Sets the maximum number of hops that an ICMP request message can be sent.</span></span> <span data-ttu-id="29f2b-175">預設值是由作業系統所控制。</span><span class="sxs-lookup"><span data-stu-id="29f2b-175">The default value is controlled by the operating system.</span></span> <span data-ttu-id="29f2b-176">Windows 10 的預設值為128躍點。</span><span class="sxs-lookup"><span data-stu-id="29f2b-176">The default value for Windows 10 is 128 hops.</span></span>

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

### <span data-ttu-id="29f2b-177">-Ping</span><span class="sxs-lookup"><span data-stu-id="29f2b-177">-Ping</span></span>

<span data-ttu-id="29f2b-178">使 Cmdlet 執行 ping 測試，這是預設動作。</span><span class="sxs-lookup"><span data-stu-id="29f2b-178">Causes the cmdlet to do a ping test, which is the default action.</span></span>

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

### <span data-ttu-id="29f2b-179">-Quiet</span><span class="sxs-lookup"><span data-stu-id="29f2b-179">-Quiet</span></span>

<span data-ttu-id="29f2b-180">**Quiet** 參數會在 **system.string 物件中** 傳回 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="29f2b-180">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object.</span></span> <span data-ttu-id="29f2b-181">使用此參數會隱藏所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="29f2b-181">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="29f2b-182">每個測試的連接都會傳回一個 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="29f2b-182">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="29f2b-183">如果 **TargetName** 參數指定多部電腦，則會傳回 **布林** 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="29f2b-183">If the **TargetName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="29f2b-184">如果 **任何** ping 成功， `$True` 則會傳回。</span><span class="sxs-lookup"><span data-stu-id="29f2b-184">If **any** ping succeeds, `$True` is returned.</span></span>

<span data-ttu-id="29f2b-185">如果 **所有** ping 都失敗， `$False` 則會傳回。</span><span class="sxs-lookup"><span data-stu-id="29f2b-185">If **all** pings fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="29f2b-186">-ResolveDestination</span><span class="sxs-lookup"><span data-stu-id="29f2b-186">-ResolveDestination</span></span>

<span data-ttu-id="29f2b-187">導致 Cmdlet 嘗試解析目標的 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="29f2b-187">Causes the cmdlet to attempt to resolve the DNS name of the target.</span></span>

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

### <span data-ttu-id="29f2b-188">-Source</span><span class="sxs-lookup"><span data-stu-id="29f2b-188">-Source</span></span>

<span data-ttu-id="29f2b-189">指定 ping 之來源電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="29f2b-189">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="29f2b-190">請以逗號分隔的清單方式輸入電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="29f2b-190">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="29f2b-191">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="29f2b-191">The default is the local computer.</span></span>

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

### <span data-ttu-id="29f2b-192">-TargetName</span><span class="sxs-lookup"><span data-stu-id="29f2b-192">-TargetName</span></span>

<span data-ttu-id="29f2b-193">指定要測試的電腦。</span><span class="sxs-lookup"><span data-stu-id="29f2b-193">Specifies the computers to test.</span></span> <span data-ttu-id="29f2b-194">請輸入電腦名稱或輸入 IPv4 或 IPv6 格式的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="29f2b-194">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span> <span data-ttu-id="29f2b-195">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="29f2b-195">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="29f2b-196">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="29f2b-196">This parameter is required.</span></span> <span data-ttu-id="29f2b-197">**ComputerName** 是此參數的別名。</span><span class="sxs-lookup"><span data-stu-id="29f2b-197">**ComputerName** is an alias for this parameter.</span></span>

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

### <span data-ttu-id="29f2b-198">-TCPPort</span><span class="sxs-lookup"><span data-stu-id="29f2b-198">-TCPPort</span></span>

<span data-ttu-id="29f2b-199">指定要在 TCP 連接測試中使用之目標上的 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="29f2b-199">Specifies the TCP port number on the target to be used in the TCP connection test.</span></span> <span data-ttu-id="29f2b-200">此 Cmdlet 會嘗試對目標上的指定埠進行 TCP 連接。</span><span class="sxs-lookup"><span data-stu-id="29f2b-200">The cmdlet will attempt to make a TCP connection to the specified port on the target.</span></span>

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

### <span data-ttu-id="29f2b-201">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="29f2b-201">-TimeoutSeconds</span></span>

<span data-ttu-id="29f2b-202">設定測試的超時值。</span><span class="sxs-lookup"><span data-stu-id="29f2b-202">Sets the timeout value for the test.</span></span> <span data-ttu-id="29f2b-203">如果在超時時間過期之前未收到回應，測試就會失敗。</span><span class="sxs-lookup"><span data-stu-id="29f2b-203">The test fails if a response isn't received before the timeout expires.</span></span> <span data-ttu-id="29f2b-204">預設為五秒鐘。</span><span class="sxs-lookup"><span data-stu-id="29f2b-204">The default is five seconds.</span></span>

<span data-ttu-id="29f2b-205">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="29f2b-205">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="29f2b-206">-追蹤路由</span><span class="sxs-lookup"><span data-stu-id="29f2b-206">-Traceroute</span></span>

<span data-ttu-id="29f2b-207">導致 Cmdlet 進行追蹤路由測試。</span><span class="sxs-lookup"><span data-stu-id="29f2b-207">Causes the cmdlet to do a traceroute test.</span></span> <span data-ttu-id="29f2b-208">使用這個參數時，此 Cmdlet 會傳回 `TestConnectionCommand+TraceRouteResult` 物件。</span><span class="sxs-lookup"><span data-stu-id="29f2b-208">When this parameter is used, the cmdlet returns a `TestConnectionCommand+TraceRouteResult` object.</span></span>

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

### <span data-ttu-id="29f2b-209">-繼續</span><span class="sxs-lookup"><span data-stu-id="29f2b-209">-Continues</span></span>

<span data-ttu-id="29f2b-210">導致 Cmdlet 持續傳送 ping 要求。</span><span class="sxs-lookup"><span data-stu-id="29f2b-210">Causes the cmdlet to send ping requests continuously.</span></span> <span data-ttu-id="29f2b-211">此參數不能與 **Count** 參數一起使用。</span><span class="sxs-lookup"><span data-stu-id="29f2b-211">This parameter can't be used with the **Count** parameter.</span></span>

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

### <span data-ttu-id="29f2b-212">-MTUSizeDetect</span><span class="sxs-lookup"><span data-stu-id="29f2b-212">-MTUSizeDetect</span></span>

<span data-ttu-id="29f2b-213">這個參數是用來探索 Path MTU 大小。</span><span class="sxs-lookup"><span data-stu-id="29f2b-213">This parameter is used to discover the Path MTU size.</span></span> <span data-ttu-id="29f2b-214">Cmdlet 會傳回 **PingReply # MTUSize** 物件，其中包含目標的路徑 MTU 大小。</span><span class="sxs-lookup"><span data-stu-id="29f2b-214">The cmdlet returns a **PingReply#MTUSize** object that contains the Path MTU size to the target.</span></span> <span data-ttu-id="29f2b-215">如需路徑 MTU 的詳細資訊，請參閱維琪百科中的 [PATH Mtu Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) 文章。</span><span class="sxs-lookup"><span data-stu-id="29f2b-215">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="29f2b-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="29f2b-216">CommonParameters</span></span>

<span data-ttu-id="29f2b-217">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="29f2b-217">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="29f2b-218">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="29f2b-218">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="29f2b-219">輸入</span><span class="sxs-lookup"><span data-stu-id="29f2b-219">INPUTS</span></span>

### <span data-ttu-id="29f2b-220">無</span><span class="sxs-lookup"><span data-stu-id="29f2b-220">None</span></span>

<span data-ttu-id="29f2b-221">您無法透過管道傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="29f2b-221">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="29f2b-222">輸出</span><span class="sxs-lookup"><span data-stu-id="29f2b-222">OUTPUTS</span></span>

### <span data-ttu-id="29f2b-223">TestConnectionCommand + PingReport、TestConnectionCommand + TraceRouteResult、Boolean、PingReply # MTUSize</span><span class="sxs-lookup"><span data-stu-id="29f2b-223">TestConnectionCommand+PingReport, TestConnectionCommand+TraceRouteResult, Boolean, PingReply#MTUSize</span></span>

<span data-ttu-id="29f2b-224">如果您指定 **Quiet** 參數，它會傳回 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="29f2b-224">If you specify the **Quiet** parameter, it returns a **Boolean** value.</span></span> <span data-ttu-id="29f2b-225">如果測試了多個連接，則會傳回 **布林** 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="29f2b-225">If multiple connections are tested, an array of **Boolean** values is returned.</span></span> <span data-ttu-id="29f2b-226">否則，會 `Test-Connection` 針對每個 ping 傳回 **TestConnectionCommand + PingReport** 物件。</span><span class="sxs-lookup"><span data-stu-id="29f2b-226">Otherwise, `Test-Connection` returns a **TestConnectionCommand+PingReport** object for each ping.</span></span>

## <span data-ttu-id="29f2b-227">注意</span><span class="sxs-lookup"><span data-stu-id="29f2b-227">NOTES</span></span>

## <span data-ttu-id="29f2b-228">相關連結</span><span class="sxs-lookup"><span data-stu-id="29f2b-228">RELATED LINKS</span></span>

[<span data-ttu-id="29f2b-229">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="29f2b-229">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="29f2b-230">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="29f2b-230">Stop-Computer</span></span>](Stop-Computer.md)
