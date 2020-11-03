---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 6a03d5a644e3d4be515a93a702d0ef0aff23a8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202380"
---
# <span data-ttu-id="44bb1-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="44bb1-103">Test-Connection</span></span>

## <span data-ttu-id="44bb1-104">概要</span><span class="sxs-lookup"><span data-stu-id="44bb1-104">SYNOPSIS</span></span>
<span data-ttu-id="44bb1-105">將 ICMP echo 要求封包或 ping 傳送至一或多部電腦。</span><span class="sxs-lookup"><span data-stu-id="44bb1-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="44bb1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="44bb1-106">SYNTAX</span></span>

### <span data-ttu-id="44bb1-107">DefaultPing (預設) </span><span class="sxs-lookup"><span data-stu-id="44bb1-107">DefaultPing (Default)</span></span>

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="44bb1-108">RepeatPing</span><span class="sxs-lookup"><span data-stu-id="44bb1-108">RepeatPing</span></span>

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="44bb1-109">MtuSizeDetect</span><span class="sxs-lookup"><span data-stu-id="44bb1-109">MtuSizeDetect</span></span>

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="44bb1-110">追蹤路由</span><span class="sxs-lookup"><span data-stu-id="44bb1-110">TraceRoute</span></span>

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="44bb1-111">TcpPort</span><span class="sxs-lookup"><span data-stu-id="44bb1-111">TcpPort</span></span>

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## <span data-ttu-id="44bb1-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="44bb1-112">DESCRIPTION</span></span>

<span data-ttu-id="44bb1-113">此 `Test-Connection` Cmdlet 會將網際網路控制訊息通訊協定 (ICMP) echo 要求封包或 ping 傳送至一或多部遠端電腦，並傳迴響應回應回復。</span><span class="sxs-lookup"><span data-stu-id="44bb1-113">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="44bb1-114">您可以使用這個 Cmdlet 來判斷是否可以透過 IP 網路來連線到特定電腦。</span><span class="sxs-lookup"><span data-stu-id="44bb1-114">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="44bb1-115">您可以使用的參數 `Test-Connection` 來指定傳送和接收電腦、以背景工作方式執行命令、設定超時和偵測次數，以及設定連接和驗證。</span><span class="sxs-lookup"><span data-stu-id="44bb1-115">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="44bb1-116">不同于熟悉的 **ping** 命令， `Test-Connection` 會傳回您可以在 PowerShell 中調查的 **TestConnectionCommand + PingStatus** 物件。</span><span class="sxs-lookup"><span data-stu-id="44bb1-116">Unlike the familiar **ping** command, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="44bb1-117">**Quiet** 參數會針對每個已測試的連接，傳回 **system.string 物件中** 的 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="44bb1-117">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="44bb1-118">如果測試了多個連接，則會傳回 **布林** 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="44bb1-118">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="44bb1-119">範例</span><span class="sxs-lookup"><span data-stu-id="44bb1-119">EXAMPLES</span></span>

### <span data-ttu-id="44bb1-120">範例1：將 echo 要求傳送至遠端電腦</span><span class="sxs-lookup"><span data-stu-id="44bb1-120">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="44bb1-121">此範例會將 echo 要求封包從本機電腦傳送到 Server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="44bb1-121">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

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

<span data-ttu-id="44bb1-122">`Test-Connection` 使用 **TargetName** 參數指定 Server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="44bb1-122">`Test-Connection` uses the **TargetName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="44bb1-123">**IPv4** 參數指定測試的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="44bb1-123">The **IPv4** parameter specifies the protocol for the test.</span></span>

<span data-ttu-id="44bb1-124">系統會將一連串的 **TestConnectionCommand + PingStatus** 物件傳送到輸出資料流程，從目的電腦的每個 ping 回復都有一個物件。</span><span class="sxs-lookup"><span data-stu-id="44bb1-124">A series of **TestConnectionCommand+PingStatus** objects are sent to the output stream, one object per ping reply from the target machine.</span></span>

### <span data-ttu-id="44bb1-125">範例2：傳送 echo 要求至數部電腦</span><span class="sxs-lookup"><span data-stu-id="44bb1-125">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="44bb1-126">此範例會將 ping 從本機電腦傳送到多部遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="44bb1-126">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### <span data-ttu-id="44bb1-127">範例3：使用參數自訂測試命令</span><span class="sxs-lookup"><span data-stu-id="44bb1-127">Example 3: Use parameters to customize the test command</span></span>

<span data-ttu-id="44bb1-128">這個範例會使用的參數 `Test-Connection` 來自訂命令。</span><span class="sxs-lookup"><span data-stu-id="44bb1-128">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="44bb1-129">本機電腦會將 ping 測試傳送至遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="44bb1-129">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

<span data-ttu-id="44bb1-130">`Test-Connection` 使用 **TargetName** 參數指定 Server01。</span><span class="sxs-lookup"><span data-stu-id="44bb1-130">`Test-Connection` uses the **TargetName** parameter to specify Server01.</span></span> <span data-ttu-id="44bb1-131">**Count** 參數指定將三個 ping 傳送至 Server01 電腦， **延遲** 間隔為2秒。</span><span class="sxs-lookup"><span data-stu-id="44bb1-131">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="44bb1-132">當偵測回應預期需要比平常更長的躍點數目或高流量網路情況時，您可能會使用這些選項。</span><span class="sxs-lookup"><span data-stu-id="44bb1-132">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="44bb1-133">範例4：以背景工作的形式執行測試</span><span class="sxs-lookup"><span data-stu-id="44bb1-133">Example 4: Run a test as a background job</span></span>

<span data-ttu-id="44bb1-134">此範例示範如何以 `Test-Connection` PowerShell 背景工作執行命令。</span><span class="sxs-lookup"><span data-stu-id="44bb1-134">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

<span data-ttu-id="44bb1-135">此 `Start-Job` 命令會使用 `Test-Connection` Cmdlet 來偵測企業中的許多電腦。</span><span class="sxs-lookup"><span data-stu-id="44bb1-135">The `Start-Job` command uses the `Test-Connection` cmdlet to ping many computers in an enterprise.</span></span>
<span data-ttu-id="44bb1-136">**TargetName** 參數的值是 `Get-Content` 從檔案讀取電腦名稱稱清單的命令 `Servers.txt` 。</span><span class="sxs-lookup"><span data-stu-id="44bb1-136">The value of the **TargetName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="44bb1-137">此命令會使用 `Start-Job` Cmdlet 以背景工作方式執行命令，並將工作儲存在 `$job` 變數中。</span><span class="sxs-lookup"><span data-stu-id="44bb1-137">The command uses the `Start-Job` cmdlet to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="44bb1-138">在 `Receive-Job` `-Wait` 作業完成之前，會指示命令，然後取得結果，並將其儲存在 `$Results` 變數中。</span><span class="sxs-lookup"><span data-stu-id="44bb1-138">The `Receive-Job` command is instructed to `-Wait` until the job is completed, and then gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="44bb1-139">範例5：只有在連接測試成功時才建立會話</span><span class="sxs-lookup"><span data-stu-id="44bb1-139">Example 5: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="44bb1-140">此範例只會在至少一個傳送至電腦的 ping 成功時，才會在 Server01 電腦上建立會話。</span><span class="sxs-lookup"><span data-stu-id="44bb1-140">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

<span data-ttu-id="44bb1-141">`Test-Connection`Cmdlet 會 `Server01` 使用提供的 **Quiet** 參數來 ping 電腦。</span><span class="sxs-lookup"><span data-stu-id="44bb1-141">The `Test-Connection` cmdlet pings the `Server01` computer, with the **Quiet** parameter provided.</span></span>
<span data-ttu-id="44bb1-142">`$True`如果四個 ping 中有任何一個成功，則產生的值為。</span><span class="sxs-lookup"><span data-stu-id="44bb1-142">The resulting value is `$True` if any of the four pings succeed.</span></span> <span data-ttu-id="44bb1-143">如果 ping 都沒有成功，則值為 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="44bb1-143">If none of the pings succeed, the value is `$False`.</span></span>

<span data-ttu-id="44bb1-144">如果命令傳回的 `Test-Connection` 值為 `$True` ，則命令會使用 `New-PSSession` Cmdlet 來建立 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="44bb1-144">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession** .</span></span>

### <span data-ttu-id="44bb1-145">範例6：使用追蹤路由參數</span><span class="sxs-lookup"><span data-stu-id="44bb1-145">Example 6: Use the Traceroute parameter</span></span>

<span data-ttu-id="44bb1-146">在 PowerShell 6.0 中引進的 **追蹤路由** 參數會將本機電腦和您指定的遠端目的地之間的路由對應到您以 **TargetName** 參數指定的路由。</span><span class="sxs-lookup"><span data-stu-id="44bb1-146">Introduced in PowerShell 6.0, the **Traceroute** parameter maps a route between the local computer and the remote destination you specify with the **TargetName** parameter.</span></span>

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

<span data-ttu-id="44bb1-147">此 `Test-Connection` 命令會使用 **追蹤路由** 參數來呼叫。</span><span class="sxs-lookup"><span data-stu-id="44bb1-147">The `Test-Connection` command is called with the **Traceroute** parameter.</span></span> <span data-ttu-id="44bb1-148">結果（即 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` 物件）會輸出至 **成功** 輸出資料流程。</span><span class="sxs-lookup"><span data-stu-id="44bb1-148">The results, which are `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objects, are output to the **Success** output stream.</span></span>

## <span data-ttu-id="44bb1-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="44bb1-149">PARAMETERS</span></span>

### <span data-ttu-id="44bb1-150">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="44bb1-150">-BufferSize</span></span>

<span data-ttu-id="44bb1-151">指定與這個命令一起傳送之緩衝區的大小 (單位為位元組)。</span><span class="sxs-lookup"><span data-stu-id="44bb1-151">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="44bb1-152">預設值為 32。</span><span class="sxs-lookup"><span data-stu-id="44bb1-152">The default value is 32.</span></span>

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

### <span data-ttu-id="44bb1-153">-重複</span><span class="sxs-lookup"><span data-stu-id="44bb1-153">-Repeat</span></span>

<span data-ttu-id="44bb1-154">導致 Cmdlet 持續傳送 ping 要求。</span><span class="sxs-lookup"><span data-stu-id="44bb1-154">Causes the cmdlet to send ping requests continuously.</span></span> <span data-ttu-id="44bb1-155">此參數不能與 **Count** 參數一起使用。</span><span class="sxs-lookup"><span data-stu-id="44bb1-155">This parameter can't be used with the **Count** parameter.</span></span>

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

### <span data-ttu-id="44bb1-156">-Count</span><span class="sxs-lookup"><span data-stu-id="44bb1-156">-Count</span></span>

<span data-ttu-id="44bb1-157">指定要傳送的回應要求數目。</span><span class="sxs-lookup"><span data-stu-id="44bb1-157">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="44bb1-158">預設值為 4。</span><span class="sxs-lookup"><span data-stu-id="44bb1-158">The default value is 4.</span></span>

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

### <span data-ttu-id="44bb1-159">-Delay</span><span class="sxs-lookup"><span data-stu-id="44bb1-159">-Delay</span></span>

<span data-ttu-id="44bb1-160">指定 ping 的間隔 (單位為秒)。</span><span class="sxs-lookup"><span data-stu-id="44bb1-160">Specifies the interval between pings, in seconds.</span></span>

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

### <span data-ttu-id="44bb1-161">-DontFragment</span><span class="sxs-lookup"><span data-stu-id="44bb1-161">-DontFragment</span></span>

<span data-ttu-id="44bb1-162">此參數會設定 IP 標頭中的「 **不要片段** 」旗標。</span><span class="sxs-lookup"><span data-stu-id="44bb1-162">This parameter sets the **Don't Fragment** flag in the IP header.</span></span> <span data-ttu-id="44bb1-163">您可以使用此參數搭配 **BufferSize** 參數來測試路徑 MTU 大小。</span><span class="sxs-lookup"><span data-stu-id="44bb1-163">You can use this parameter with the **BufferSize** parameter to test the Path MTU size.</span></span> <span data-ttu-id="44bb1-164">如需路徑 MTU 的詳細資訊，請參閱維琪百科中的 [PATH Mtu Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) 文章。</span><span class="sxs-lookup"><span data-stu-id="44bb1-164">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="44bb1-165">-IPv4</span><span class="sxs-lookup"><span data-stu-id="44bb1-165">-IPv4</span></span>

<span data-ttu-id="44bb1-166">強制 Cmdlet 將 IPv4 通訊協定用於測試。</span><span class="sxs-lookup"><span data-stu-id="44bb1-166">Forces the cmdlet to use the IPv4 protocol for the test.</span></span>

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

### <span data-ttu-id="44bb1-167">-IPv6</span><span class="sxs-lookup"><span data-stu-id="44bb1-167">-IPv6</span></span>

<span data-ttu-id="44bb1-168">強制 Cmdlet 針對測試使用 IPv6 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="44bb1-168">Forces the cmdlet to use the IPv6 protocol for the test.</span></span>

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

### <span data-ttu-id="44bb1-169">-MaxHops</span><span class="sxs-lookup"><span data-stu-id="44bb1-169">-MaxHops</span></span>

<span data-ttu-id="44bb1-170">設定可傳送 ICMP 要求訊息的躍點數目上限。</span><span class="sxs-lookup"><span data-stu-id="44bb1-170">Sets the maximum number of hops that an ICMP request message can be sent.</span></span> <span data-ttu-id="44bb1-171">預設值是由作業系統所控制。</span><span class="sxs-lookup"><span data-stu-id="44bb1-171">The default value is controlled by the operating system.</span></span> <span data-ttu-id="44bb1-172">Windows 10 的預設值為128躍點。</span><span class="sxs-lookup"><span data-stu-id="44bb1-172">The default value for Windows 10 is 128 hops.</span></span>

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

### <span data-ttu-id="44bb1-173">-Ping</span><span class="sxs-lookup"><span data-stu-id="44bb1-173">-Ping</span></span>

<span data-ttu-id="44bb1-174">導致 Cmdlet 執行 ping 測試。</span><span class="sxs-lookup"><span data-stu-id="44bb1-174">Causes the cmdlet to do a ping test.</span></span> <span data-ttu-id="44bb1-175">這是 Cmdlet 的預設模式 `Test-Connection` 。</span><span class="sxs-lookup"><span data-stu-id="44bb1-175">This is the default mode for the `Test-Connection` cmdlet.</span></span>

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

### <span data-ttu-id="44bb1-176">-Quiet</span><span class="sxs-lookup"><span data-stu-id="44bb1-176">-Quiet</span></span>

<span data-ttu-id="44bb1-177">**Quiet** 參數會傳回 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="44bb1-177">The **Quiet** parameter returns a **Boolean** value.</span></span> <span data-ttu-id="44bb1-178">使用此參數會隱藏所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="44bb1-178">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="44bb1-179">每個測試的連接都會傳回一個 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="44bb1-179">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="44bb1-180">如果 **TargetName** 參數指定多部電腦，則會傳回 **布林** 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="44bb1-180">If the **TargetName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="44bb1-181">如果對指定目標的 **任何** 偵測成功， `$True` 則會傳回。</span><span class="sxs-lookup"><span data-stu-id="44bb1-181">If **any** ping to a given target succeeds, `$True` is returned.</span></span>

<span data-ttu-id="44bb1-182">如果指定目標的 **所有** ping 都失敗， `$False` 則會傳回。</span><span class="sxs-lookup"><span data-stu-id="44bb1-182">If **all** pings to a given target fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="44bb1-183">-ResolveDestination</span><span class="sxs-lookup"><span data-stu-id="44bb1-183">-ResolveDestination</span></span>

<span data-ttu-id="44bb1-184">導致 Cmdlet 嘗試解析目標的 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="44bb1-184">Causes the cmdlet to attempt to resolve the DNS name of the target.</span></span> <span data-ttu-id="44bb1-185">搭配 **追蹤路由** 參數使用時，如果可能的話，也會取出所有轉送主機的 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="44bb1-185">When used in conjunction with the **Traceroute** parameter, the DNS names of all intermediate hosts will also be retrieved, if possible.</span></span>

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

### <span data-ttu-id="44bb1-186">-Source</span><span class="sxs-lookup"><span data-stu-id="44bb1-186">-Source</span></span>

<span data-ttu-id="44bb1-187">指定 ping 之來源電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="44bb1-187">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="44bb1-188">請以逗號分隔的清單方式輸入電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="44bb1-188">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="44bb1-189">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="44bb1-189">The default is the local computer.</span></span>

<span data-ttu-id="44bb1-190">**注意：** 此參數在 PowerShell 版本6和更新版本中無法運作。</span><span class="sxs-lookup"><span data-stu-id="44bb1-190">**NOTE:** This parameter is not functional in PowerShell versions 6 and up.</span></span>
<span data-ttu-id="44bb1-191">提供此參數將不會影響此命令。</span><span class="sxs-lookup"><span data-stu-id="44bb1-191">Supplying this parameter will have no effect on the command.</span></span>

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

### <span data-ttu-id="44bb1-192">-TargetName</span><span class="sxs-lookup"><span data-stu-id="44bb1-192">-TargetName</span></span>

<span data-ttu-id="44bb1-193">指定要測試) 的電腦 (。</span><span class="sxs-lookup"><span data-stu-id="44bb1-193">Specifies the computer(s) to test.</span></span> <span data-ttu-id="44bb1-194">請輸入電腦名稱或輸入 IPv4 或 IPv6 格式的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="44bb1-194">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span>

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

### <span data-ttu-id="44bb1-195">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="44bb1-195">-TimeoutSeconds</span></span>

<span data-ttu-id="44bb1-196">設定測試的超時值。</span><span class="sxs-lookup"><span data-stu-id="44bb1-196">Sets the timeout value for the test.</span></span> <span data-ttu-id="44bb1-197">如果在超時時間過期之前未收到回應，測試就會失敗。</span><span class="sxs-lookup"><span data-stu-id="44bb1-197">The test fails if a response isn't received before the timeout expires.</span></span> <span data-ttu-id="44bb1-198">預設為五秒鐘。</span><span class="sxs-lookup"><span data-stu-id="44bb1-198">The default is five seconds.</span></span>

<span data-ttu-id="44bb1-199">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="44bb1-199">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="44bb1-200">-追蹤路由</span><span class="sxs-lookup"><span data-stu-id="44bb1-200">-Traceroute</span></span>

<span data-ttu-id="44bb1-201">導致 Cmdlet 進行追蹤路由測試。</span><span class="sxs-lookup"><span data-stu-id="44bb1-201">Causes the cmdlet to do a traceroute test.</span></span> <span data-ttu-id="44bb1-202">使用這個參數時，此 Cmdlet 會傳回 `TestConnectionCommand+TraceStatus` 物件。</span><span class="sxs-lookup"><span data-stu-id="44bb1-202">When this parameter is used, the cmdlet returns a `TestConnectionCommand+TraceStatus` object.</span></span>

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

### <span data-ttu-id="44bb1-203">-MtuSize</span><span class="sxs-lookup"><span data-stu-id="44bb1-203">-MtuSize</span></span>

<span data-ttu-id="44bb1-204">這個參數是用來探索 Path MTU 大小。</span><span class="sxs-lookup"><span data-stu-id="44bb1-204">This parameter is used to discover the Path MTU size.</span></span> <span data-ttu-id="44bb1-205">Cmdlet 會傳回 **PingReply # MTUSize** 物件，其中包含目標的路徑 MTU 大小。</span><span class="sxs-lookup"><span data-stu-id="44bb1-205">The cmdlet returns a **PingReply#MTUSize** object that contains the Path MTU size to the target.</span></span> <span data-ttu-id="44bb1-206">如需路徑 MTU 的詳細資訊，請參閱維琪百科中的 [PATH Mtu Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) 文章。</span><span class="sxs-lookup"><span data-stu-id="44bb1-206">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="44bb1-207">-TcpPort</span><span class="sxs-lookup"><span data-stu-id="44bb1-207">-TcpPort</span></span>

<span data-ttu-id="44bb1-208">指定要在 TCP 連接測試中使用之目標上的 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="44bb1-208">Specifies the TCP port number on the target to be used in the TCP connection test.</span></span> <span data-ttu-id="44bb1-209">此 Cmdlet 會嘗試對目標上的指定埠進行 TCP 連接。</span><span class="sxs-lookup"><span data-stu-id="44bb1-209">The cmdlet will attempt to make a TCP connection to the specified port on the target.</span></span>

<span data-ttu-id="44bb1-210">如果可以建立連接， `$True` 則會傳回。</span><span class="sxs-lookup"><span data-stu-id="44bb1-210">If a connection can be made, `$True` will be returned.</span></span>

<span data-ttu-id="44bb1-211">如果無法進行連接， `$False` 則會傳回。</span><span class="sxs-lookup"><span data-stu-id="44bb1-211">If a connection cannot be made, `$False` will be returned.</span></span>

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

### <span data-ttu-id="44bb1-212">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="44bb1-212">CommonParameters</span></span>

<span data-ttu-id="44bb1-213">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="44bb1-213">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="44bb1-214">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="44bb1-214">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="44bb1-215">輸入</span><span class="sxs-lookup"><span data-stu-id="44bb1-215">INPUTS</span></span>

### <span data-ttu-id="44bb1-216">無</span><span class="sxs-lookup"><span data-stu-id="44bb1-216">None</span></span>

<span data-ttu-id="44bb1-217">您無法透過管道傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="44bb1-217">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="44bb1-218">輸出</span><span class="sxs-lookup"><span data-stu-id="44bb1-218">OUTPUTS</span></span>

### <span data-ttu-id="44bb1-219">TestConnectionCommand + PingStatus、TestConnectionCommand + TraceStatus、Boolean、TestConnectionCommand + PingMtuStatus</span><span class="sxs-lookup"><span data-stu-id="44bb1-219">TestConnectionCommand+PingStatus, TestConnectionCommand+TraceStatus, Boolean, TestConnectionCommand+PingMtuStatus</span></span>

<span data-ttu-id="44bb1-220">根據預設，會 `Test-Connection` 針對每個偵測回復傳回 **TestConnectionCommand + PingStatus** 物件。</span><span class="sxs-lookup"><span data-stu-id="44bb1-220">By default, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object for each ping reply.</span></span>

<span data-ttu-id="44bb1-221">如果您指定 **追蹤路由** 參數，則此 Cmdlet 會在路由中傳回每個偵測回復的 **TestConnectionCommand + TraceStatus** 物件。</span><span class="sxs-lookup"><span data-stu-id="44bb1-221">If you specify the **Traceroute** parameter, the cmdlet will return a **TestConnectionCommand+TraceStatus** object for each ping reply along the route.</span></span>

<span data-ttu-id="44bb1-222">如果您指定 **Quiet** 或 **TcpPort** 參數，則會傳回 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="44bb1-222">If you specify the **Quiet** or **TcpPort** parameters, it returns a **Boolean** value.</span></span> <span data-ttu-id="44bb1-223">如果測試了多個連接，則會傳回 **布林** 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="44bb1-223">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="44bb1-224">注意</span><span class="sxs-lookup"><span data-stu-id="44bb1-224">NOTES</span></span>

## <span data-ttu-id="44bb1-225">相關連結</span><span class="sxs-lookup"><span data-stu-id="44bb1-225">RELATED LINKS</span></span>

[<span data-ttu-id="44bb1-226">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="44bb1-226">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="44bb1-227">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="44bb1-227">Stop-Computer</span></span>](Stop-Computer.md)

