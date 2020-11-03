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
# <span data-ttu-id="9a88c-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="9a88c-103">Test-Connection</span></span>

## <span data-ttu-id="9a88c-104">概要</span><span class="sxs-lookup"><span data-stu-id="9a88c-104">SYNOPSIS</span></span>
<span data-ttu-id="9a88c-105">將 ICMP echo 要求封包或 ping 傳送至一或多部電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="9a88c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9a88c-106">SYNTAX</span></span>

### <span data-ttu-id="9a88c-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="9a88c-107">Default (Default)</span></span>

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-TimeToLive <Int32>]
 [-Delay <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="9a88c-108">來源</span><span class="sxs-lookup"><span data-stu-id="9a88c-108">Source</span></span>

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Credential <PSCredential>] [-Source] <String[]> [-Impersonation <ImpersonationLevel>]
 [-ThrottleLimit <Int32>] [-TimeToLive <Int32>] [-Delay <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="9a88c-109">Quiet</span><span class="sxs-lookup"><span data-stu-id="9a88c-109">Quiet</span></span>

```
Test-Connection [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-TimeToLive <Int32>] [-Delay <Int32>] [-Quiet]
 [<CommonParameters>]
```

## <span data-ttu-id="9a88c-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a88c-110">DESCRIPTION</span></span>

<span data-ttu-id="9a88c-111">此 `Test-Connection` Cmdlet 會將網際網路控制訊息通訊協定 (ICMP) echo 要求封包或 ping 傳送至一或多部遠端電腦，並傳迴響應回應回復。</span><span class="sxs-lookup"><span data-stu-id="9a88c-111">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="9a88c-112">您可以使用這個 Cmdlet 來判斷是否可以透過 IP 網路來連線到特定電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-112">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="9a88c-113">您可以使用的參數 `Test-Connection` 來指定傳送和接收電腦、以背景工作方式執行命令、設定超時和偵測次數，以及設定連接和驗證。</span><span class="sxs-lookup"><span data-stu-id="9a88c-113">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="9a88c-114">不同于熟悉的 **ping** 命令， `Test-Connection` 會傳回您可以在 PowerShell 中調查的 **Win32_PingStatus** 物件。</span><span class="sxs-lookup"><span data-stu-id="9a88c-114">Unlike the familiar **ping** command, `Test-Connection` returns a **Win32_PingStatus** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="9a88c-115">**Quiet** 參數會針對每個已測試的連接，傳回 **system.string 物件中** 的 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="9a88c-115">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="9a88c-116">如果測試了多個連接，則會傳回 **布林** 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="9a88c-116">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="9a88c-117">範例</span><span class="sxs-lookup"><span data-stu-id="9a88c-117">EXAMPLES</span></span>

### <span data-ttu-id="9a88c-118">範例1：將 echo 要求傳送至遠端電腦</span><span class="sxs-lookup"><span data-stu-id="9a88c-118">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="9a88c-119">此範例會將 echo 要求封包從本機電腦傳送到 Server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-119">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

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

<span data-ttu-id="9a88c-120">`Test-Connection` 使用 **ComputerName** 參數來指定 Server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-120">`Test-Connection` uses the **ComputerName** parameter to specify the Server01 computer.</span></span>

### <span data-ttu-id="9a88c-121">範例2：傳送 echo 要求至數部電腦</span><span class="sxs-lookup"><span data-stu-id="9a88c-121">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="9a88c-122">此範例會將 ping 從本機電腦傳送到多部遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-122">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -ComputerName Server01, Server02, Server12
```

### <span data-ttu-id="9a88c-123">範例3：從數部電腦傳送 echo 要求到電腦</span><span class="sxs-lookup"><span data-stu-id="9a88c-123">Example 3: Send echo requests from several computers to a computer</span></span>

<span data-ttu-id="9a88c-124">此範例會將來自不同來源電腦的 ping 傳送到單一遠端電腦 Server01。</span><span class="sxs-lookup"><span data-stu-id="9a88c-124">This example sends pings from different source computers to a single remote computer, Server01.</span></span>

```powershell
Test-Connection -Source Server02, Server12, localhost -ComputerName Server01 -Credential Domain01\Admin01
```

<span data-ttu-id="9a88c-125">`Test-Connection` 使用 **Credential** 參數來指定具有從來源電腦傳送 ping 要求之許可權的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="9a88c-125">`Test-Connection` uses the **Credential** parameter to specify the credentials of a user who has permission to send a ping request from the source computers.</span></span> <span data-ttu-id="9a88c-126">請使用這個命令格式來測試來自多個點的連線延遲。</span><span class="sxs-lookup"><span data-stu-id="9a88c-126">Use this command format to test the latency of connections from multiple points.</span></span>

### <span data-ttu-id="9a88c-127">範例4：使用參數自訂測試命令</span><span class="sxs-lookup"><span data-stu-id="9a88c-127">Example 4: Use parameters to customize the test command</span></span>

<span data-ttu-id="9a88c-128">這個範例會使用的參數 `Test-Connection` 來自訂命令。</span><span class="sxs-lookup"><span data-stu-id="9a88c-128">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="9a88c-129">本機電腦會將 ping 測試傳送至遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-129">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -ComputerName Server01 -Count 3 -Delay 2 -TTL 255 -BufferSize 256 -ThrottleLimit 32
```

<span data-ttu-id="9a88c-130">`Test-Connection` 使用 **ComputerName** 參數來指定 Server01。</span><span class="sxs-lookup"><span data-stu-id="9a88c-130">`Test-Connection` uses the **ComputerName** parameter to specify Server01.</span></span> <span data-ttu-id="9a88c-131">**Count** 參數指定將三個 ping 傳送至 Server01 電腦， **延遲** 間隔為2秒。</span><span class="sxs-lookup"><span data-stu-id="9a88c-131">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="9a88c-132">當偵測回應預期需要比平常更長的躍點數目或高流量網路情況時，您可能會使用這些選項。</span><span class="sxs-lookup"><span data-stu-id="9a88c-132">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="9a88c-133">範例5：以背景工作的形式執行測試</span><span class="sxs-lookup"><span data-stu-id="9a88c-133">Example 5: Run a test as a background job</span></span>

<span data-ttu-id="9a88c-134">此範例示範如何以 `Test-Connection` PowerShell 背景工作執行命令。</span><span class="sxs-lookup"><span data-stu-id="9a88c-134">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Test-Connection -ComputerName (Get-Content Servers.txt) -AsJob
if ($job.JobStateInfo.State -ne "Running") {$Results = Receive-Job $job}
```

<span data-ttu-id="9a88c-135">`Test-Connection`命令會 ping 企業中的許多電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-135">The `Test-Connection` command pings many computers in an enterprise.</span></span> <span data-ttu-id="9a88c-136">**ComputerName** 參數的值是 `Get-Content` 從讀取電腦名稱稱清單的命令 `Servers.txt file` 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-136">The value of the **ComputerName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt file`.</span></span> <span data-ttu-id="9a88c-137">此命令會使用 **AsJob** 參數將命令當作背景工作來執行，並將工作儲存在變數中 `$job` 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-137">The command uses the **AsJob** parameter to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="9a88c-138">此 `if` 命令會檢查作業是否仍在執行中。</span><span class="sxs-lookup"><span data-stu-id="9a88c-138">The `if` command checks to see that the job isn't still running.</span></span> <span data-ttu-id="9a88c-139">如果工作未執行，則會 `Receive-Job` 取得結果，並將其儲存在 `$Results` 變數中。</span><span class="sxs-lookup"><span data-stu-id="9a88c-139">If the job isn't running, `Receive-Job` gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="9a88c-140">範例6：使用認證偵測遠端電腦</span><span class="sxs-lookup"><span data-stu-id="9a88c-140">Example 6: Ping a remote computer with credentials</span></span>

<span data-ttu-id="9a88c-141">此命令會使用 `Test-Connection` Cmdlet 來 ping 遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-141">This command uses the `Test-Connection` cmdlet to ping a remote computer.</span></span>

```powershell
Test-Connection Server55 -Credential Domain55\User01 -Impersonation Identify
```

<span data-ttu-id="9a88c-142">此命令會使用 **Credential** 參數來指定具有 ping 遠端電腦之許可權的使用者帳戶，以及 **模擬參數將** 模擬等級變更為 **可識別** 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9a88c-142">The command uses the **Credential** parameter to specify a user account that has permission to ping the remote computer and the **Impersonation** parameter to change the impersonation level to **Identify** .</span></span>

### <span data-ttu-id="9a88c-143">範例7：只有在連接測試成功時才建立會話</span><span class="sxs-lookup"><span data-stu-id="9a88c-143">Example 7: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="9a88c-144">此範例只會在至少一個傳送至電腦的 ping 成功時，才會在 Server01 電腦上建立會話。</span><span class="sxs-lookup"><span data-stu-id="9a88c-144">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -ComputerName Server01 -Quiet) {New-PSSession Server01}
```

<span data-ttu-id="9a88c-145">此 `if` 命令會使用 `Test-Connection` Cmdlet 來偵測 Server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-145">The `if` command uses the `Test-Connection` cmdlet to ping the Server01 computer.</span></span> <span data-ttu-id="9a88c-146">此命令會使用 **Quiet** 參數，它會傳回 **布林** 值，而不是 **Win32_PingStatus** 物件。</span><span class="sxs-lookup"><span data-stu-id="9a88c-146">The command uses the **Quiet** parameter, which returns a **Boolean** value, instead of a **Win32_PingStatus** object.</span></span> <span data-ttu-id="9a88c-147">`$True`如果四個 ping 中有任何一個成功，則值為，否則為 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-147">The value is `$True` if any of the four pings succeed and is, otherwise, `$False`.</span></span>

<span data-ttu-id="9a88c-148">如果命令傳回的 `Test-Connection` 值為 `$True` ，則命令會使用 `New-PSSession` Cmdlet 來建立 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-148">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession** .</span></span>

## <span data-ttu-id="9a88c-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9a88c-149">PARAMETERS</span></span>

### <span data-ttu-id="9a88c-150">-AsJob</span><span class="sxs-lookup"><span data-stu-id="9a88c-150">-AsJob</span></span>

<span data-ttu-id="9a88c-151">指出此 Cmdlet 會以背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="9a88c-151">Indicates that this cmdlet runs as a background job.</span></span>

<span data-ttu-id="9a88c-152">若要使用這個參數，本機電腦和遠端電腦必須設定為進行遠端處理，而在 Windows Vista 和更新版本的 Windows 作業系統上，您必須使用 [以 **系統管理員身分執行** ] 選項開啟 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9a88c-152">To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="9a88c-153">如需詳細資訊，請參閱[about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9a88c-153">For more information, see [about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md).</span></span>

<span data-ttu-id="9a88c-154">當您指定 **AsJob** 參數時，此命令會立即傳回代表背景工作的物件。</span><span class="sxs-lookup"><span data-stu-id="9a88c-154">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="9a88c-155">工作完成後，您可以繼續在工作階段中工作。</span><span class="sxs-lookup"><span data-stu-id="9a88c-155">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="9a88c-156">工作會在本機電腦上建立，而來自遠端電腦的結果則會自動傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-156">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="9a88c-157">若要取得工作結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9a88c-157">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="9a88c-158">如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) 和 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="9a88c-158">For more information about PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md).</span></span>

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

### <span data-ttu-id="9a88c-159">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="9a88c-159">-BufferSize</span></span>

<span data-ttu-id="9a88c-160">指定與這個命令一起傳送之緩衝區的大小 (單位為位元組)。</span><span class="sxs-lookup"><span data-stu-id="9a88c-160">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="9a88c-161">預設值為 32。</span><span class="sxs-lookup"><span data-stu-id="9a88c-161">The default value is 32.</span></span>

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

### <span data-ttu-id="9a88c-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="9a88c-162">-ComputerName</span></span>

<span data-ttu-id="9a88c-163">指定要 ping 的電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-163">Specifies the computers to ping.</span></span> <span data-ttu-id="9a88c-164">請輸入電腦名稱或輸入 IPv4 或 IPv6 格式的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="9a88c-164">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span> <span data-ttu-id="9a88c-165">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9a88c-165">Wildcard characters are not permitted.</span></span> <span data-ttu-id="9a88c-166">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="9a88c-166">This parameter is required.</span></span>

<span data-ttu-id="9a88c-167">此參數不依賴 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="9a88c-167">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="9a88c-168">即使您的電腦未設定為執行遠端命令，您也可以使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="9a88c-168">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

> [!NOTE]
> <span data-ttu-id="9a88c-169">**ComputerName** 參數已重新命名為 PowerShell 6.0 和更新版本中的 **TargetName** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-169">The **ComputerName** parameter is renamed to **TargetName** in PowerShell 6.0 and above.</span></span>

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

### <span data-ttu-id="9a88c-170">-Count</span><span class="sxs-lookup"><span data-stu-id="9a88c-170">-Count</span></span>

<span data-ttu-id="9a88c-171">指定要傳送的回應要求數目。</span><span class="sxs-lookup"><span data-stu-id="9a88c-171">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="9a88c-172">預設值為 4。</span><span class="sxs-lookup"><span data-stu-id="9a88c-172">The default value is 4.</span></span>

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

### <span data-ttu-id="9a88c-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="9a88c-173">-Credential</span></span>

<span data-ttu-id="9a88c-174">指定具有從來源電腦傳送 ping 要求之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9a88c-174">Specifies a user account that has permission to send a ping request from the source computer.</span></span> <span data-ttu-id="9a88c-175">輸入使用者名稱（例如 User01 或 Domain01\User01），或輸入 **PSCredential** 物件，例如 Cmdlet 中的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-175">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="9a88c-176">只有當命令中使用 **Source** 參數時， **Credential** 參數才有效。</span><span class="sxs-lookup"><span data-stu-id="9a88c-176">The **Credential** parameter is valid only when the **Source** parameter is used in the command.</span></span> <span data-ttu-id="9a88c-177">認證不會影響目的地電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-177">The credentials don't affect the destination computer.</span></span>

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

### <span data-ttu-id="9a88c-178">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="9a88c-178">-DcomAuthentication</span></span>

<span data-ttu-id="9a88c-179">指定此 Cmdlet 與 WMI 搭配使用的驗證層級。</span><span class="sxs-lookup"><span data-stu-id="9a88c-179">Specifies the authentication level that this cmdlet uses with WMI.</span></span>
<span data-ttu-id="9a88c-180">`Test-Connection` 使用 WMI。</span><span class="sxs-lookup"><span data-stu-id="9a88c-180">`Test-Connection` uses WMI.</span></span>
<span data-ttu-id="9a88c-181">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="9a88c-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9a88c-182">**Default** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-182">**Default** .</span></span> <span data-ttu-id="9a88c-183">Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="9a88c-183">Windows Authentication</span></span>
- <span data-ttu-id="9a88c-184">**None** ：</span><span class="sxs-lookup"><span data-stu-id="9a88c-184">**None** .</span></span> <span data-ttu-id="9a88c-185">沒有 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="9a88c-185">No COM authentication</span></span>
- <span data-ttu-id="9a88c-186">**連接** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-186">**Connect** .</span></span> <span data-ttu-id="9a88c-187">連線等級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="9a88c-187">Connect-level COM authentication</span></span>
- <span data-ttu-id="9a88c-188">**呼叫** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-188">**Call** .</span></span> <span data-ttu-id="9a88c-189">呼叫等級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="9a88c-189">Call-level COM authentication</span></span>
- <span data-ttu-id="9a88c-190">封 **包** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-190">**Packet** .</span></span> <span data-ttu-id="9a88c-191">封包層級 COM 驗證</span><span class="sxs-lookup"><span data-stu-id="9a88c-191">Packet-level COM authentication</span></span>
- <span data-ttu-id="9a88c-192">**PacketIntegrity** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-192">**PacketIntegrity** .</span></span> <span data-ttu-id="9a88c-193">封包完整性等級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="9a88c-193">Packet Integrity-level COM authentication</span></span>
- <span data-ttu-id="9a88c-194">**PacketPrivacy** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-194">**PacketPrivacy** .</span></span> <span data-ttu-id="9a88c-195">封包隱私權層級 COM 驗證</span><span class="sxs-lookup"><span data-stu-id="9a88c-195">Packet Privacy-level COM authentication</span></span>
- <span data-ttu-id="9a88c-196">**未** 變更。</span><span class="sxs-lookup"><span data-stu-id="9a88c-196">**Unchanged** .</span></span> <span data-ttu-id="9a88c-197">與前一個命令相同</span><span class="sxs-lookup"><span data-stu-id="9a88c-197">Same as the previous command</span></span>

<span data-ttu-id="9a88c-198">預設值是列舉值為 **4** 的封 **包** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-198">The default value is **Packet** that has an enumerated value of **4** .</span></span> <span data-ttu-id="9a88c-199">如需此參數值的詳細資訊，請參閱 [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel) 列舉。</span><span class="sxs-lookup"><span data-stu-id="9a88c-199">For more information about the values of this parameter, see [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel) enumeration.</span></span>

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

### <span data-ttu-id="9a88c-200">-Delay</span><span class="sxs-lookup"><span data-stu-id="9a88c-200">-Delay</span></span>

<span data-ttu-id="9a88c-201">指定 ping 的間隔 (單位為秒)。</span><span class="sxs-lookup"><span data-stu-id="9a88c-201">Specifies the interval between pings, in seconds.</span></span>

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

### <span data-ttu-id="9a88c-202">-Impersonation</span><span class="sxs-lookup"><span data-stu-id="9a88c-202">-Impersonation</span></span>

<span data-ttu-id="9a88c-203">指定此 Cmdlet 呼叫 WMI 時要使用的模擬等級。</span><span class="sxs-lookup"><span data-stu-id="9a88c-203">Specifies the impersonation level to use when this cmdlet calls WMI.</span></span> <span data-ttu-id="9a88c-204">`Test-Connection` 使用 WMI。</span><span class="sxs-lookup"><span data-stu-id="9a88c-204">`Test-Connection` uses WMI.</span></span>

<span data-ttu-id="9a88c-205">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="9a88c-205">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="9a88c-206">**Default** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-206">**Default** .</span></span> <span data-ttu-id="9a88c-207">預設模擬。</span><span class="sxs-lookup"><span data-stu-id="9a88c-207">Default impersonation.</span></span>
- <span data-ttu-id="9a88c-208">**匿名** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-208">**Anonymous** .</span></span> <span data-ttu-id="9a88c-209">隱藏呼叫端的身分識別。</span><span class="sxs-lookup"><span data-stu-id="9a88c-209">Hides the identity of the caller.</span></span>
- <span data-ttu-id="9a88c-210">**識別** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-210">**Identify** .</span></span> <span data-ttu-id="9a88c-211">允許物件查詢呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="9a88c-211">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="9a88c-212">**Impersonate** 模擬。</span><span class="sxs-lookup"><span data-stu-id="9a88c-212">**Impersonate** .</span></span> <span data-ttu-id="9a88c-213">允許物件使用呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="9a88c-213">Allows objects to use the credentials of the caller.</span></span>

<span data-ttu-id="9a88c-214">預設值為 [模擬 **]。**</span><span class="sxs-lookup"><span data-stu-id="9a88c-214">The default value is **Impersonate** .</span></span>

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

### <span data-ttu-id="9a88c-215">-Protocol</span><span class="sxs-lookup"><span data-stu-id="9a88c-215">-Protocol</span></span>

<span data-ttu-id="9a88c-216">指定通訊協定。</span><span class="sxs-lookup"><span data-stu-id="9a88c-216">Specifies a protocol.</span></span> <span data-ttu-id="9a88c-217">此參數可接受的值為 DCOM 和 WSMan。</span><span class="sxs-lookup"><span data-stu-id="9a88c-217">The acceptable values for this parameter are DCOM and WSMan.</span></span>

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

### <span data-ttu-id="9a88c-218">-Quiet</span><span class="sxs-lookup"><span data-stu-id="9a88c-218">-Quiet</span></span>

<span data-ttu-id="9a88c-219">**Quiet** 參數會在 **system.string 物件中** 傳回 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="9a88c-219">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object.</span></span> <span data-ttu-id="9a88c-220">使用此參數會隱藏所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="9a88c-220">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="9a88c-221">每個測試的連接都會傳回一個 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="9a88c-221">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="9a88c-222">如果 **ComputerName** 參數指定多部電腦，則會傳回 **布林** 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="9a88c-222">If the **ComputerName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="9a88c-223">如果 **任何** ping 成功， `$True` 則會傳回。</span><span class="sxs-lookup"><span data-stu-id="9a88c-223">If **any** ping succeeds, `$True` is returned.</span></span>

<span data-ttu-id="9a88c-224">如果 **所有** ping 都失敗， `$False` 則會傳回。</span><span class="sxs-lookup"><span data-stu-id="9a88c-224">If **all** pings fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="9a88c-225">-Source</span><span class="sxs-lookup"><span data-stu-id="9a88c-225">-Source</span></span>

<span data-ttu-id="9a88c-226">指定 ping 之來源電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="9a88c-226">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="9a88c-227">請以逗號分隔的清單方式輸入電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="9a88c-227">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="9a88c-228">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-228">The default is the local computer.</span></span>

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

### <span data-ttu-id="9a88c-229">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="9a88c-229">-ThrottleLimit</span></span>

<span data-ttu-id="9a88c-230">指定為執行此命令可建立的最大同時連線數。</span><span class="sxs-lookup"><span data-stu-id="9a88c-230">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="9a88c-231">若省略此參數，或輸入值為 0，則會使用預設值 32。</span><span class="sxs-lookup"><span data-stu-id="9a88c-231">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="9a88c-232">節流限制僅適用於目前命令，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="9a88c-232">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="9a88c-233">-TimeToLive</span><span class="sxs-lookup"><span data-stu-id="9a88c-233">-TimeToLive</span></span>

<span data-ttu-id="9a88c-234">指定封包可以轉寄的最長時間。</span><span class="sxs-lookup"><span data-stu-id="9a88c-234">Specifies the maximum times a packet can be forwarded.</span></span> <span data-ttu-id="9a88c-235">針對閘道、路由器等中的每個躍點， **TimeToLive** 值會減少一。</span><span class="sxs-lookup"><span data-stu-id="9a88c-235">For every hop in gateways, routers etc. the **TimeToLive** value is decreased by one.</span></span> <span data-ttu-id="9a88c-236">若為零，則會捨棄封包，並傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="9a88c-236">At zero the packet is discarded and an error is returned.</span></span>
<span data-ttu-id="9a88c-237">在 **Windows** 中，預設值是 **128** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-237">In **Windows** , The default value is **128** .</span></span> <span data-ttu-id="9a88c-238">**TimeToLive** 參數的別名是 **TTL** 。</span><span class="sxs-lookup"><span data-stu-id="9a88c-238">The alias of the **TimeToLive** parameter is **TTL** .</span></span>

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

### <span data-ttu-id="9a88c-239">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="9a88c-239">-WsmanAuthentication</span></span>

<span data-ttu-id="9a88c-240">指定當此 Cmdlet 使用 WSMan 通訊協定時，用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="9a88c-240">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span>
<span data-ttu-id="9a88c-241">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="9a88c-241">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9a88c-242">基本</span><span class="sxs-lookup"><span data-stu-id="9a88c-242">Basic</span></span>
- <span data-ttu-id="9a88c-243">CredSSP</span><span class="sxs-lookup"><span data-stu-id="9a88c-243">CredSSP</span></span>
- <span data-ttu-id="9a88c-244">預設</span><span class="sxs-lookup"><span data-stu-id="9a88c-244">Default</span></span>
- <span data-ttu-id="9a88c-245">Digest</span><span class="sxs-lookup"><span data-stu-id="9a88c-245">Digest</span></span>
- <span data-ttu-id="9a88c-246">Kerberos</span><span class="sxs-lookup"><span data-stu-id="9a88c-246">Kerberos</span></span>
- <span data-ttu-id="9a88c-247">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="9a88c-247">Negotiate.</span></span>

<span data-ttu-id="9a88c-248">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="9a88c-248">The default value is Default.</span></span>

<span data-ttu-id="9a88c-249">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0)。</span><span class="sxs-lookup"><span data-stu-id="9a88c-249">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0).</span></span>

<span data-ttu-id="9a88c-250">注意：認證安全性服務提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，它是針對需要在多個資源（例如存取遠端網路共用）進行驗證的命令所設計。</span><span class="sxs-lookup"><span data-stu-id="9a88c-250">Caution: Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
<span data-ttu-id="9a88c-251">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="9a88c-251">This mechanism increases the security risk of the remote operation.</span></span>
<span data-ttu-id="9a88c-252">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="9a88c-252">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="9a88c-253">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9a88c-253">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="9a88c-254">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9a88c-254">CommonParameters</span></span>

<span data-ttu-id="9a88c-255">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9a88c-255">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9a88c-256">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9a88c-256">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9a88c-257">輸入</span><span class="sxs-lookup"><span data-stu-id="9a88c-257">INPUTS</span></span>

### <span data-ttu-id="9a88c-258">無</span><span class="sxs-lookup"><span data-stu-id="9a88c-258">None</span></span>

<span data-ttu-id="9a88c-259">您無法透過管道傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9a88c-259">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="9a88c-260">輸出</span><span class="sxs-lookup"><span data-stu-id="9a88c-260">OUTPUTS</span></span>

### <span data-ttu-id="9a88c-261">System.management.managementobject # root\cimv2\ Win32_PingStatus，，System.object. System.management.automation.remotingjob，system.string</span><span class="sxs-lookup"><span data-stu-id="9a88c-261">System.Management.ManagementObject#root\cimv2\Win32_PingStatus, System.Management.Automation.RemotingJob, System.Boolean</span></span>

<span data-ttu-id="9a88c-262">如果您指定 **AsJob** 參數，此 Cmdlet 會傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="9a88c-262">This cmdlet returns a job object, if you specify the **AsJob** parameter.</span></span>

<span data-ttu-id="9a88c-263">如果您指定 **Quiet** 參數，它會傳回 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="9a88c-263">If you specify the **Quiet** parameter, it returns a **Boolean** value.</span></span> <span data-ttu-id="9a88c-264">如果測試了多個連接，則會傳回 **布林** 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="9a88c-264">If multiple connections are tested, an array of **Boolean** values is returned.</span></span> <span data-ttu-id="9a88c-265">否則，會傳回 `Test-Connection` 每個 ping 的 **Win32_PingStatus** 物件。</span><span class="sxs-lookup"><span data-stu-id="9a88c-265">Otherwise, `Test-Connection` returns a **Win32_PingStatus** object for each ping.</span></span>

## <span data-ttu-id="9a88c-266">注意</span><span class="sxs-lookup"><span data-stu-id="9a88c-266">NOTES</span></span>

<span data-ttu-id="9a88c-267">此 Cmdlet 會使用 **Win32_PingStatus** 類別。</span><span class="sxs-lookup"><span data-stu-id="9a88c-267">This cmdlet uses the **Win32_PingStatus** class.</span></span> <span data-ttu-id="9a88c-268">`Get-WMIObject Win32_PingStatus`命令相當於 `Test-Connection` 命令。</span><span class="sxs-lookup"><span data-stu-id="9a88c-268">A `Get-WMIObject Win32_PingStatus` command is equivalent to a `Test-Connection` command.</span></span>

<span data-ttu-id="9a88c-269">PowerShell 3.0 中引進了 **Source** 參數集。</span><span class="sxs-lookup"><span data-stu-id="9a88c-269">The **Source** parameter set was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="9a88c-270">相關連結</span><span class="sxs-lookup"><span data-stu-id="9a88c-270">RELATED LINKS</span></span>

[<span data-ttu-id="9a88c-271">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="9a88c-271">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="9a88c-272">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="9a88c-272">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="9a88c-273">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="9a88c-273">Stop-Computer</span></span>](Stop-Computer.md)
