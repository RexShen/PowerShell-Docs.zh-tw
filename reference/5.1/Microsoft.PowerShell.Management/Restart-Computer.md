---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 553b61c9669afab325e9feec101d701c2b9a7c83
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205419"
---
# <span data-ttu-id="d4986-103">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="d4986-103">Restart-Computer</span></span>

## <span data-ttu-id="d4986-104">概要</span><span class="sxs-lookup"><span data-stu-id="d4986-104">SYNOPSIS</span></span>
<span data-ttu-id="d4986-105">重新開機本機電腦和遠端電腦上的作業系統。</span><span class="sxs-lookup"><span data-stu-id="d4986-105">Restarts the operating system on local and remote computers.</span></span>

## <span data-ttu-id="d4986-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d4986-106">SYNTAX</span></span>

### <span data-ttu-id="d4986-107">DefaultSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="d4986-107">DefaultSet (Default)</span></span>

```
Restart-Computer [-DcomAuthentication <AuthenticationLevel>] [-Impersonation <ImpersonationLevel>]
 [-WsmanAuthentication <String>] [-Protocol <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d4986-108">AsJobSet</span><span class="sxs-lookup"><span data-stu-id="d4986-108">AsJobSet</span></span>

```
Restart-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>]
 [-Impersonation <ImpersonationLevel>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Force] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d4986-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d4986-109">DESCRIPTION</span></span>

<span data-ttu-id="d4986-110">`Restart-Computer`Cmdlet 會重新開機本機電腦和遠端電腦上的作業系統。</span><span class="sxs-lookup"><span data-stu-id="d4986-110">The `Restart-Computer` cmdlet restarts the operating system on the local and remote computers.</span></span>

<span data-ttu-id="d4986-111">您可以使用的參數 `Restart-Computer` ，以背景工作方式執行重新開機作業、指定驗證等級和替代認證、限制同時執行的作業，以及強制立即重新開機。</span><span class="sxs-lookup"><span data-stu-id="d4986-111">You can use the parameters of `Restart-Computer` to run the restart operations as a background job, to specify the authentication levels and alternate credentials, to limit the operations that run at the same time, and to force an immediate restart.</span></span>

<span data-ttu-id="d4986-112">從 Windows PowerShell 3.0 開始，您可以先等候重新開機完成，再執行下一個命令。</span><span class="sxs-lookup"><span data-stu-id="d4986-112">Starting in Windows PowerShell 3.0, you can wait for the restart to complete before you run the next command.</span></span> <span data-ttu-id="d4986-113">指定等候超時和查詢間隔，並等候特定服務可在重新開機的電腦上使用。</span><span class="sxs-lookup"><span data-stu-id="d4986-113">Specify a waiting time-out and query interval, and wait for particular services to be available on the restarted computer.</span></span> <span data-ttu-id="d4986-114">這項功能可讓您在腳本和函式中使用非常實用 `Restart-Computer` 。</span><span class="sxs-lookup"><span data-stu-id="d4986-114">This feature makes it practical to use `Restart-Computer` in scripts and functions.</span></span>

<span data-ttu-id="d4986-115">您可以使用 WS-Management (WSMan) 通訊協定來重新開機電腦，以防分散式元件物件模型 (DCOM) 呼叫遭到封鎖，例如由企業防火牆封鎖。</span><span class="sxs-lookup"><span data-stu-id="d4986-115">You can use the WS-Management (WSMan) protocol to restart the computer, in case Distributed Component Object Model (DCOM) calls are blocked, such as by an enterprise firewall.</span></span> <span data-ttu-id="d4986-116">如需詳細資訊，請參閱 [WS-Management 通訊協定](/windows/desktop/WinRM/ws-management-protocol)。</span><span class="sxs-lookup"><span data-stu-id="d4986-116">For more information, see [WS-Management Protocol](/windows/desktop/WinRM/ws-management-protocol).</span></span>

<span data-ttu-id="d4986-117">只有當您在命令中使用 **AsJob** 參數時，這個 Cmdlet 才需要 Windows PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="d4986-117">This cmdlet requires Windows PowerShell remoting only when you use the **AsJob** parameter in a command.</span></span>

## <span data-ttu-id="d4986-118">範例</span><span class="sxs-lookup"><span data-stu-id="d4986-118">EXAMPLES</span></span>

### <span data-ttu-id="d4986-119">範例1：重新開機本機電腦</span><span class="sxs-lookup"><span data-stu-id="d4986-119">Example 1: Restart the local computer</span></span>

<span data-ttu-id="d4986-120">`Restart-Computer` 重新開機本機電腦。</span><span class="sxs-lookup"><span data-stu-id="d4986-120">`Restart-Computer` restarts the local computer.</span></span>

```powershell
Restart-Computer
```

### <span data-ttu-id="d4986-121">範例2：重新開機多部電腦</span><span class="sxs-lookup"><span data-stu-id="d4986-121">Example 2: Restart multiple computers</span></span>

<span data-ttu-id="d4986-122">`Restart-Computer` 可以重新開機遠端和本機電腦。</span><span class="sxs-lookup"><span data-stu-id="d4986-122">`Restart-Computer` can restart remote and local computers.</span></span> <span data-ttu-id="d4986-123">**ComputerName** 參數接受電腦名稱稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="d4986-123">The **ComputerName** parameter accepts an array of computer names.</span></span>

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### <span data-ttu-id="d4986-124">範例3：將電腦重新開機為背景工作</span><span class="sxs-lookup"><span data-stu-id="d4986-124">Example 3: Restart computers as a background job</span></span>

<span data-ttu-id="d4986-125">這些命令會 `Restart-Computer` 在兩部遠端電腦上以背景工作方式執行命令，然後取得結果。</span><span class="sxs-lookup"><span data-stu-id="d4986-125">These commands run a `Restart-Computer` command as a background job on two remote computers, and then get the results.</span></span>

<span data-ttu-id="d4986-126">由於 **AsJob** 會在本機電腦上建立工作，並自動將結果傳回本機電腦，因此您可以用 `Receive-Job` 本機命令的形式執行。</span><span class="sxs-lookup"><span data-stu-id="d4986-126">Because **AsJob** creates the job on the local computer and automatically returns the results to the local computer, you can run `Receive-Job` as a local command.</span></span>

```powershell
$Job = Restart-Computer -ComputerName "Server01", "Server02" -AsJob
$Job | Receive-Job
```

<span data-ttu-id="d4986-127">`Restart-Computer` 使用 **ComputerName** 參數來指定 **Server01** 和 **Server02** 。</span><span class="sxs-lookup"><span data-stu-id="d4986-127">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01** and **Server02** .</span></span> <span data-ttu-id="d4986-128">**AsJob** 參數會以背景工作的方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="d4986-128">The **AsJob** parameter runs the command as a background job.</span></span> <span data-ttu-id="d4986-129">工作物件會儲存在變數中 `$Job` 。</span><span class="sxs-lookup"><span data-stu-id="d4986-129">The job object is stored in the `$Job` variable.</span></span> <span data-ttu-id="d4986-130">`$Job` 會向下傳送管線至 `Receive-Job` 取得結果的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d4986-130">`$Job` is sent down the pipeline to the `Receive-Job` cmdlet that gets the results.</span></span>

### <span data-ttu-id="d4986-131">範例4：重新開機遠端電腦</span><span class="sxs-lookup"><span data-stu-id="d4986-131">Example 4: Restart a remote computer</span></span>

<span data-ttu-id="d4986-132">`Restart-Computer` 使用自訂的模擬和驗證設定重新開機遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="d4986-132">`Restart-Computer` restarts a remote computer with customized impersonation and authentication settings.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

<span data-ttu-id="d4986-133">`Restart-Computer` 使用 **ComputerName** 參數來指定 **Server01** 。</span><span class="sxs-lookup"><span data-stu-id="d4986-133">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01** .</span></span> <span data-ttu-id="d4986-134">模擬 **參數會指定匿名，以** 隱藏要求者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="d4986-134">The **Impersonation** parameter specifies Anonymous to hide the requester's identity.</span></span> <span data-ttu-id="d4986-135">**DcomAuthentication** 參數會將 PacketIntegrity 指定為連接的驗證層級。</span><span class="sxs-lookup"><span data-stu-id="d4986-135">The **DcomAuthentication** parameter specifies PacketIntegrity as the connection's authentication level.</span></span>

### <span data-ttu-id="d4986-136">範例5：強制重新開機文字檔中列出的電腦</span><span class="sxs-lookup"><span data-stu-id="d4986-136">Example 5: Force restart of computers listed in a text file</span></span>

<span data-ttu-id="d4986-137">此範例會強制立即重新開機檔案中列出的電腦 `Domain01.txt` 。</span><span class="sxs-lookup"><span data-stu-id="d4986-137">This example forces an immediate restart of the computers listed in the `Domain01.txt` file.</span></span> <span data-ttu-id="d4986-138">文字檔中的電腦名稱稱會儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="d4986-138">The computer names from the text file are stored in a variable.</span></span> <span data-ttu-id="d4986-139">**Force** 參數會強制立即重新開機，而 **ThrottleLimit** 參數會限制並行連接的數目。</span><span class="sxs-lookup"><span data-stu-id="d4986-139">The **Force** parameter forces an immediate restart and the **ThrottleLimit** parameter limits the number of concurrent connections.</span></span>

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force -ThrottleLimit 10
```

<span data-ttu-id="d4986-140">`Get-Content` 使用 **Path** 參數從文字檔中取得電腦名稱稱的清單， **Domain01.txt** 。</span><span class="sxs-lookup"><span data-stu-id="d4986-140">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt** .</span></span> <span data-ttu-id="d4986-141">電腦名稱稱會儲存在變數中 `$Names` 。</span><span class="sxs-lookup"><span data-stu-id="d4986-141">The computer names are stored in the variable `$Names`.</span></span> <span data-ttu-id="d4986-142">`Get-Credential` 提示您輸入使用者名稱和密碼，並將值儲存在變數中 `$Creds` 。</span><span class="sxs-lookup"><span data-stu-id="d4986-142">`Get-Credential` prompts you for a username and password and stores the values in the variable `$Creds`.</span></span> <span data-ttu-id="d4986-143">`Restart-Computer` 使用 **ComputerName** 和 **Credential** 參數及其變數。</span><span class="sxs-lookup"><span data-stu-id="d4986-143">`Restart-Computer` uses the **ComputerName** and **Credential** parameters with their variables.</span></span> <span data-ttu-id="d4986-144">**Force** 參數會導致立即重新開機每一部電腦。</span><span class="sxs-lookup"><span data-stu-id="d4986-144">The **Force** parameter causes an immediate restart of each computer.</span></span> <span data-ttu-id="d4986-145">**ThrottleLimit** 參數會將命令限制為10個並行連接。</span><span class="sxs-lookup"><span data-stu-id="d4986-145">The **ThrottleLimit** parameter limits the command to 10 concurrent connections.</span></span>

### <span data-ttu-id="d4986-146">範例6：重新開機遠端電腦並等候 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d4986-146">Example 6: Restart a remote computer and wait for PowerShell</span></span>

<span data-ttu-id="d4986-147">`Restart-Computer` 重新開機遠端電腦，然後等候最多5分鐘的時間 (300 秒) ，讓 PowerShell 在重新開機的電腦上變成可用，然後再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="d4986-147">`Restart-Computer` restarts the remote computer and then waits up to 5 minutes (300 seconds) for PowerShell to become available on the restarted computer before it continues.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

<span data-ttu-id="d4986-148">`Restart-Computer` 使用 **ComputerName** 參數來指定 **Server01** 。</span><span class="sxs-lookup"><span data-stu-id="d4986-148">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01** .</span></span> <span data-ttu-id="d4986-149">**Wait** 參數會等候重新開機完成。</span><span class="sxs-lookup"><span data-stu-id="d4986-149">The **Wait** parameter waits for the restart to finish.</span></span> <span data-ttu-id="d4986-150">的 **會指定 PowerShell** 可以在遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="d4986-150">The **For** specifies that PowerShell can run commands on the remote computer.</span></span> <span data-ttu-id="d4986-151">Timeout 參數指定五分鐘的等候 **時間** 。</span><span class="sxs-lookup"><span data-stu-id="d4986-151">The **Timeout** parameter specifies a five-minute wait.</span></span> <span data-ttu-id="d4986-152">**Delay** 參數會每隔兩秒查詢一次遠端電腦，以判斷是否已重新開機。</span><span class="sxs-lookup"><span data-stu-id="d4986-152">The **Delay** parameter queries the remote computer every two seconds to determine whether it's restarted.</span></span>

### <span data-ttu-id="d4986-153">範例7：使用 WSMan 通訊協定重新開機電腦</span><span class="sxs-lookup"><span data-stu-id="d4986-153">Example 7: Restart a computer by using the WSMan Protocol</span></span>

<span data-ttu-id="d4986-154">`Restart-Computer` 使用 WSMan 通訊協定（而非預設的 DCOM）來重新開機遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="d4986-154">`Restart-Computer` restarts the remote computer by using the WSMan protocol instead of the default, DCOM.</span></span> <span data-ttu-id="d4986-155">Kerberos 驗證會決定目前使用者是否具有重新開機遠端電腦的許可權。</span><span class="sxs-lookup"><span data-stu-id="d4986-155">Kerberos authentication determines whether the current user has permission to restart the remote computer.</span></span>

<span data-ttu-id="d4986-156">這些設定是專為 DCOM 型重新開機因為 DCOM 遭到封鎖而失敗的企業所設計。</span><span class="sxs-lookup"><span data-stu-id="d4986-156">These settings are designed for enterprises in which DCOM-based restarts fail because DCOM is blocked.</span></span> <span data-ttu-id="d4986-157">例如，藉由防火牆。</span><span class="sxs-lookup"><span data-stu-id="d4986-157">For example, by a firewall.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Protocol WSMan -WsmanAuthentication Kerberos
```

<span data-ttu-id="d4986-158">`Restart-Computer` 使用 **ComputerName** 參數來指定遠端電腦 **Server01** 。</span><span class="sxs-lookup"><span data-stu-id="d4986-158">`Restart-Computer` uses the **ComputerName** parameter to specify the remote computer, **Server01** .</span></span>
<span data-ttu-id="d4986-159">**Protocol** 參數會指定使用 WSMan 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="d4986-159">The **Protocol** parameter specifies to use the WSMan protocol.</span></span> <span data-ttu-id="d4986-160">**WsmanAuthentication** 參數會將驗證方法指定為 **Kerberos** 。</span><span class="sxs-lookup"><span data-stu-id="d4986-160">The **WsmanAuthentication** parameter specifies the authentication method as **Kerberos** .</span></span>

## <span data-ttu-id="d4986-161">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d4986-161">PARAMETERS</span></span>

### <span data-ttu-id="d4986-162">-AsJob</span><span class="sxs-lookup"><span data-stu-id="d4986-162">-AsJob</span></span>

<span data-ttu-id="d4986-163">表示以 `Restart-Computer` 背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="d4986-163">Indicates that `Restart-Computer` runs as a background job.</span></span>

<span data-ttu-id="d4986-164">若要使用此參數，必須設定本機和遠端電腦以進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="d4986-164">To use this parameter, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="d4986-165">在 Windows Vista 和更新版本的 Windows 作業系統上，您必須使用 [以 **系統管理員身分執行** ] 選項開啟 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d4986-165">On Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as Administrator** option.</span></span> <span data-ttu-id="d4986-166">如需詳細資訊，請參閱[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4986-166">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="d4986-167">當您指定 **AsJob** 參數時，此命令會立即傳回代表背景工作的物件。</span><span class="sxs-lookup"><span data-stu-id="d4986-167">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="d4986-168">工作完成後，您可以繼續在工作階段中工作。</span><span class="sxs-lookup"><span data-stu-id="d4986-168">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="d4986-169">工作會在本機電腦上建立，而來自遠端電腦的結果則會自動傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="d4986-169">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="d4986-170">若要管理工作，請使用 **Job** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d4986-170">To manage the job, use the **Job** cmdlets.</span></span> <span data-ttu-id="d4986-171">若要取得工作結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d4986-171">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="d4986-172">如需 Windows PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) 和 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="d4986-172">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4986-173">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="d4986-173">-ComputerName</span></span>

<span data-ttu-id="d4986-174">指定一個電腦名稱稱或以逗號分隔的電腦名稱稱陣列。</span><span class="sxs-lookup"><span data-stu-id="d4986-174">Specifies one computer name or a comma-separated array of computer names.</span></span> <span data-ttu-id="d4986-175">`Restart-Computer` 接受管線或變數中的 **ComputerName** 物件。</span><span class="sxs-lookup"><span data-stu-id="d4986-175">`Restart-Computer` accepts **ComputerName** objects from the pipeline or variables.</span></span>

<span data-ttu-id="d4986-176">輸入遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="d4986-176">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="d4986-177">若要指定本機電腦，請輸入電腦名稱稱、點 `.` 或 localhost。</span><span class="sxs-lookup"><span data-stu-id="d4986-177">To specify the local computer, type the computer name, a dot `.`, or localhost.</span></span>

<span data-ttu-id="d4986-178">此參數不依賴 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="d4986-178">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="d4986-179">即使您的電腦未設定為執行遠端命令，您也可以使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="d4986-179">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

<span data-ttu-id="d4986-180">如果未指定 **ComputerName** 參數，則會 `Restart-Computer` 重新開機本機電腦。</span><span class="sxs-lookup"><span data-stu-id="d4986-180">If the **ComputerName** parameter isn't specified, `Restart-Computer` restarts the local computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d4986-181">-Credential</span><span class="sxs-lookup"><span data-stu-id="d4986-181">-Credential</span></span>

<span data-ttu-id="d4986-182">指定具有執行此動作之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d4986-182">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="d4986-183">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="d4986-183">The default is the current user.</span></span>

<span data-ttu-id="d4986-184">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="d4986-184">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="d4986-185">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="d4986-185">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="d4986-186">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="d4986-186">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="d4986-187">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="d4986-187">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="d4986-188">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="d4986-188">-DcomAuthentication</span></span>

<span data-ttu-id="d4986-189">指定用於 WMI 連接的驗證層級。</span><span class="sxs-lookup"><span data-stu-id="d4986-189">Specifies the authentication level that is used for the WMI connection.</span></span> <span data-ttu-id="d4986-190">`Restart-Computer` 使用 WMI。</span><span class="sxs-lookup"><span data-stu-id="d4986-190">`Restart-Computer` uses WMI.</span></span>

<span data-ttu-id="d4986-191">有效值為：</span><span class="sxs-lookup"><span data-stu-id="d4986-191">Valid values are:</span></span>

- <span data-ttu-id="d4986-192">**呼叫** ：呼叫層級 COM 驗證</span><span class="sxs-lookup"><span data-stu-id="d4986-192">**Call** :            Call-level COM authentication</span></span>
- <span data-ttu-id="d4986-193">**Connect** ：連接層級 COM 驗證</span><span class="sxs-lookup"><span data-stu-id="d4986-193">**Connect** :         Connect-level COM authentication</span></span>
- <span data-ttu-id="d4986-194">**預設值** ： Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="d4986-194">**Default** :         Windows Authentication</span></span>
- <span data-ttu-id="d4986-195">**None** ：沒有 COM 驗證</span><span class="sxs-lookup"><span data-stu-id="d4986-195">**None** :            No COM authentication</span></span>
- <span data-ttu-id="d4986-196">封 **包** ：封包層級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="d4986-196">**Packet** :          Packet-level COM authentication.</span></span>
- <span data-ttu-id="d4986-197">**PacketIntegrity** ：封包完整性等級 COM 驗證</span><span class="sxs-lookup"><span data-stu-id="d4986-197">**PacketIntegrity** : Packet Integrity-level COM authentication</span></span>
- <span data-ttu-id="d4986-198">**PacketPrivacy** ：封包隱私權等級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="d4986-198">**PacketPrivacy** :   Packet Privacy-level COM authentication.</span></span>
- <span data-ttu-id="d4986-199">**未** 變更：驗證等級與前一個命令相同。</span><span class="sxs-lookup"><span data-stu-id="d4986-199">**Unchanged** :       The authentication level is the same as the previous command.</span></span>

<span data-ttu-id="d4986-200">如需詳細資訊，請參閱 [AuthenticationLevel 列舉](/dotnet/api/system.management.authenticationlevel)。</span><span class="sxs-lookup"><span data-stu-id="d4986-200">For more information, see [AuthenticationLevel Enumeration](/dotnet/api/system.management.authenticationlevel).</span></span>

<span data-ttu-id="d4986-201">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="d4986-201">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4986-202">-Delay</span><span class="sxs-lookup"><span data-stu-id="d4986-202">-Delay</span></span>

<span data-ttu-id="d4986-203">指定查詢的頻率（以秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="d4986-203">Specifies the frequency of queries, in seconds.</span></span> <span data-ttu-id="d4986-204">PowerShell 會查詢 **For** 參數指定的服務，以判斷在重新開機電腦之後，服務是否可用。</span><span class="sxs-lookup"><span data-stu-id="d4986-204">PowerShell queries the service specified by the **For** parameter to determine whether the service is available after the computer is restarted.</span></span>

<span data-ttu-id="d4986-205">這個參數只適用于 **Wait** 和 **For** 參數。</span><span class="sxs-lookup"><span data-stu-id="d4986-205">This parameter is valid only together with the **Wait** and **For** parameters.</span></span>

<span data-ttu-id="d4986-206">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="d4986-206">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="d4986-207">如果未指定 **Delay** 參數，會 `Restart-Computer` 使用五秒的延遲。</span><span class="sxs-lookup"><span data-stu-id="d4986-207">If the **Delay** parameter isn't specified, `Restart-Computer` uses a five second delay.</span></span>

```yaml
Type: System.Int16
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4986-208">-For</span><span class="sxs-lookup"><span data-stu-id="d4986-208">-For</span></span>

<span data-ttu-id="d4986-209">指定 PowerShell 的行為，因為它會等候指定的服務或功能在電腦重新開機後變成可用。</span><span class="sxs-lookup"><span data-stu-id="d4986-209">Specifies the behavior of PowerShell as it waits for the specified service or feature to become available after the computer restarts.</span></span> <span data-ttu-id="d4986-210">這個參數只對 **Wait** 參數有效。</span><span class="sxs-lookup"><span data-stu-id="d4986-210">This parameter is only valid with the **Wait** parameter.</span></span>

<span data-ttu-id="d4986-211">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="d4986-211">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d4986-212">**預設值** ：等候 PowerShell 重新開機。</span><span class="sxs-lookup"><span data-stu-id="d4986-212">**Default** : Waits for PowerShell to restart.</span></span>
- <span data-ttu-id="d4986-213">**Powershell** ：可以在電腦上的 powershell 遠端會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="d4986-213">**PowerShell** : Can run commands in a PowerShell remote session on the computer.</span></span>
- <span data-ttu-id="d4986-214">**WMI** ：接收對電腦 Win32_ComputerSystem 查詢的回覆。</span><span class="sxs-lookup"><span data-stu-id="d4986-214">**WMI** : Receives a reply to a Win32_ComputerSystem query for the computer.</span></span>
- <span data-ttu-id="d4986-215">**WinRM** ：可以使用 WS-Management 來建立連到電腦的遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="d4986-215">**WinRM** : Can establish a remote session to the computer by using WS-Management.</span></span>

<span data-ttu-id="d4986-216">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="d4986-216">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: DefaultSet
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4986-217">-Force</span><span class="sxs-lookup"><span data-stu-id="d4986-217">-Force</span></span>

<span data-ttu-id="d4986-218">強制立即重新開機電腦。</span><span class="sxs-lookup"><span data-stu-id="d4986-218">Forces an immediate restart of the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: f

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4986-219">-Impersonation</span><span class="sxs-lookup"><span data-stu-id="d4986-219">-Impersonation</span></span>

<span data-ttu-id="d4986-220">指定此 Cmdlet 用來呼叫 WMI 的模擬等級。</span><span class="sxs-lookup"><span data-stu-id="d4986-220">Specifies the impersonation level that this cmdlet uses to call WMI.</span></span> <span data-ttu-id="d4986-221">`Restart-Computer` 使用 WMI。</span><span class="sxs-lookup"><span data-stu-id="d4986-221">`Restart-Computer` uses WMI.</span></span>
<span data-ttu-id="d4986-222">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="d4986-222">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d4986-223">**預設** 值：預設模擬。</span><span class="sxs-lookup"><span data-stu-id="d4986-223">**Default** : Default impersonation.</span></span> <span data-ttu-id="d4986-224">儘管名稱不是預設值，但這並不是預設值。</span><span class="sxs-lookup"><span data-stu-id="d4986-224">Despite the name, this isn't the default value.</span></span>
- <span data-ttu-id="d4986-225">**匿名** ：隱藏呼叫端的身分識別。</span><span class="sxs-lookup"><span data-stu-id="d4986-225">**Anonymous** : Hides the identity of the caller.</span></span>
- <span data-ttu-id="d4986-226">**識別** ：允許物件查詢呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="d4986-226">**Identify** : Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="d4986-227">模擬 **：允許** 物件使用呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="d4986-227">**Impersonate** : Allows objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4986-228">-Protocol</span><span class="sxs-lookup"><span data-stu-id="d4986-228">-Protocol</span></span>

<span data-ttu-id="d4986-229">指定要用來重新啟動電腦的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="d4986-229">Specifies which protocol to use to restart the computers.</span></span> <span data-ttu-id="d4986-230">有效的值為 **WSMan** 和 **DCOM** 。</span><span class="sxs-lookup"><span data-stu-id="d4986-230">The valid values are **WSMan** and **DCOM** .</span></span>

<span data-ttu-id="d4986-231">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="d4986-231">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4986-232">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="d4986-232">-ThrottleLimit</span></span>

<span data-ttu-id="d4986-233">指定為執行此命令可建立的最大同時連線數。</span><span class="sxs-lookup"><span data-stu-id="d4986-233">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="d4986-234">節流限制僅適用於目前命令，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="d4986-234">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

<span data-ttu-id="d4986-235">如果未指定 **ThrottleLimit** 參數或使用0值，則 `Restart-Computer` 最多會使用32的並行連接。</span><span class="sxs-lookup"><span data-stu-id="d4986-235">If the **ThrottleLimit** parameter isn't specified or a value of 0 is used, `Restart-Computer` uses a maximum of 32 concurrent connections.</span></span>

```yaml
Type: System.Int32
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4986-236">-Timeout</span><span class="sxs-lookup"><span data-stu-id="d4986-236">-Timeout</span></span>

<span data-ttu-id="d4986-237">指定等待的持續時間 (單位為秒)。</span><span class="sxs-lookup"><span data-stu-id="d4986-237">Specifies the duration of the wait, in seconds.</span></span> <span data-ttu-id="d4986-238">當超時時間過後， `Restart-Computer` 即使電腦未重新開機，也會回到命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="d4986-238">When the timeout elapses, `Restart-Computer` returns to the command prompt, even if the computers aren't restarted.</span></span>

<span data-ttu-id="d4986-239">**Timeout** 參數只對 **Wait** 參數有效。</span><span class="sxs-lookup"><span data-stu-id="d4986-239">The **Timeout** parameter is only valid with the **Wait** parameter.</span></span> <span data-ttu-id="d4986-240">**Timeout** 會覆寫 **等待** 參數的無限等待期間。</span><span class="sxs-lookup"><span data-stu-id="d4986-240">**Timeout** overrides the **Wait** parameter's indefinite waiting period.</span></span>

<span data-ttu-id="d4986-241">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="d4986-241">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultSet
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4986-242">-Wait</span><span class="sxs-lookup"><span data-stu-id="d4986-242">-Wait</span></span>

<span data-ttu-id="d4986-243">`Restart-Computer` 抑制 PowerShell 提示字元並封鎖管線，直到電腦重新開機為止。</span><span class="sxs-lookup"><span data-stu-id="d4986-243">`Restart-Computer` suppresses the PowerShell prompt and blocks the pipeline until the computers have restarted.</span></span> <span data-ttu-id="d4986-244">您可以在腳本中使用這個參數來重新開機電腦，然後在重新開機完成時繼續處理。</span><span class="sxs-lookup"><span data-stu-id="d4986-244">You can use this parameter in a script to restart computers and then continue to process when the restart is finished.</span></span>

<span data-ttu-id="d4986-245">**Wait** 參數會無限期地等候電腦重新開機。</span><span class="sxs-lookup"><span data-stu-id="d4986-245">The **Wait** parameter waits indefinitely for the computers to restart.</span></span> <span data-ttu-id="d4986-246">您可以使用 **Timeout** 來調整計時 **，以及使用和\*\*\*\*延遲** 參數來等待特定服務在重新開機的電腦上變成可用。</span><span class="sxs-lookup"><span data-stu-id="d4986-246">You can use **Timeout** to adjust the timing and the **For** and **Delay** parameters to wait for particular services to become available on the restarted computers.</span></span>

<span data-ttu-id="d4986-247">當您重新開機本機電腦時， **Wait** 參數無效。</span><span class="sxs-lookup"><span data-stu-id="d4986-247">The **Wait** parameter isn't valid when you're restarting the local computer.</span></span> <span data-ttu-id="d4986-248">如果 **ComputerName** 參數的值包含遠端電腦和本機電腦的名稱，則會產生在 `Restart-Computer` 本機電腦上 **等候** 的非終止錯誤，但是會等待遠端電腦重新開機。</span><span class="sxs-lookup"><span data-stu-id="d4986-248">If the value of the **ComputerName** parameter contains the names of remote computers and the local computer, `Restart-Computer` generates a non-terminating error for **Wait** on the local computer, but waits for the remote computers to restart.</span></span>

<span data-ttu-id="d4986-249">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="d4986-249">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4986-250">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="d4986-250">-WsmanAuthentication</span></span>

<span data-ttu-id="d4986-251">指定用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="d4986-251">Specifies the mechanism that is used to authenticate the user credentials.</span></span> <span data-ttu-id="d4986-252">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="d4986-252">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="d4986-253">此參數可接受的值為： **Basic** 、 **CredSSP** 、 **Default** 、 **Digest** 、 **Kerberos** 和 **Negotiate** 。</span><span class="sxs-lookup"><span data-stu-id="d4986-253">The acceptable values for this parameter are: **Basic** , **CredSSP** , **Default** , **Digest** , **Kerberos** , and **Negotiate** .</span></span>

<span data-ttu-id="d4986-254">如需詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="d4986-254">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="d4986-255">認證安全性服務提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="d4986-255">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="d4986-256">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="d4986-256">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="d4986-257">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="d4986-257">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4986-258">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d4986-258">-Confirm</span></span>

<span data-ttu-id="d4986-259">在執行之前提示您確認 `Restart-Computer` 。</span><span class="sxs-lookup"><span data-stu-id="d4986-259">Prompts you for confirmation before running `Restart-Computer`.</span></span>

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

### <span data-ttu-id="d4986-260">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d4986-260">-WhatIf</span></span>

<span data-ttu-id="d4986-261">顯示執行時所發生的情況 `Restart-Computer` 。</span><span class="sxs-lookup"><span data-stu-id="d4986-261">Shows what would happen if the `Restart-Computer` runs.</span></span> <span data-ttu-id="d4986-262">`Restart-Computer`Cmdlet 不會執行。</span><span class="sxs-lookup"><span data-stu-id="d4986-262">The `Restart-Computer` cmdlet isn't run.</span></span>

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

### <span data-ttu-id="d4986-263">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d4986-263">CommonParameters</span></span>

<span data-ttu-id="d4986-264">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d4986-264">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d4986-265">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d4986-265">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d4986-266">輸入</span><span class="sxs-lookup"><span data-stu-id="d4986-266">INPUTS</span></span>

### <span data-ttu-id="d4986-267">System.String</span><span class="sxs-lookup"><span data-stu-id="d4986-267">System.String</span></span>

<span data-ttu-id="d4986-268">`Restart-Computer` 接受來自管線或變數的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="d4986-268">`Restart-Computer` accepts computer names from the pipeline or variables.</span></span>

<span data-ttu-id="d4986-269">在 Windows PowerShell 2.0 中， **ComputerName** 參數只接受從管線輸入屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="d4986-269">In Windows PowerShell 2.0, the **ComputerName** parameter takes input from the pipeline only by property name.</span></span> <span data-ttu-id="d4986-270">在 Windows PowerShell 3.0 和更新版本中， **ComputerName** 參數會以傳值方式接受來自管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="d4986-270">In Windows PowerShell 3.0, and later, the **ComputerName** parameter takes input from the pipeline by value.</span></span>

## <span data-ttu-id="d4986-271">輸出</span><span class="sxs-lookup"><span data-stu-id="d4986-271">OUTPUTS</span></span>

### <span data-ttu-id="d4986-272">None、System.management.automation.remotingjob、Automation。</span><span class="sxs-lookup"><span data-stu-id="d4986-272">None, System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="d4986-273">如果您指定 **AsJob** 參數，會傳回 `Restart-Computer` 工作物件。</span><span class="sxs-lookup"><span data-stu-id="d4986-273">If you specify the **AsJob** parameter, `Restart-Computer` returns a job object.</span></span> <span data-ttu-id="d4986-274">否則，就不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="d4986-274">Otherwise, no output is generated.</span></span>

## <span data-ttu-id="d4986-275">注意</span><span class="sxs-lookup"><span data-stu-id="d4986-275">NOTES</span></span>

- <span data-ttu-id="d4986-276">`Restart-Computer` 只在執行 Windows 的電腦上工作，且需要 WinRM 和 WMI 來關閉系統，包括本機系統。</span><span class="sxs-lookup"><span data-stu-id="d4986-276">`Restart-Computer` only work on computers running Windows and requires WinRM and WMI to shutdown a system, including the local system.</span></span>
- <span data-ttu-id="d4986-277">`Restart-Computer`使用 Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem)類別的[Win32Shutdown 方法](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem)。</span><span class="sxs-lookup"><span data-stu-id="d4986-277">`Restart-Computer` uses the [Win32Shutdown method](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) of the Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) class.</span></span>  <span data-ttu-id="d4986-278">此方法需要針對用來重新開機電腦的使用者帳戶啟用 **SeShutdownPrivilege** 許可權。</span><span class="sxs-lookup"><span data-stu-id="d4986-278">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

<span data-ttu-id="d4986-279">在 Windows PowerShell 2.0 中，當您重新開機或停止遠端電腦時， **AsJob** 參數無法可靠地運作。</span><span class="sxs-lookup"><span data-stu-id="d4986-279">In Windows PowerShell 2.0, the **AsJob** parameter doesn't work reliably when you are restarting or stopping remote computers.</span></span> <span data-ttu-id="d4986-280">在 Windows PowerShell 3.0 中，已變更實作來解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="d4986-280">In Windows PowerShell 3.0, the implementation is changed to resolve this problem.</span></span>

## <span data-ttu-id="d4986-281">相關連結</span><span class="sxs-lookup"><span data-stu-id="d4986-281">RELATED LINKS</span></span>

[<span data-ttu-id="d4986-282">關於 Windows 遠端管理</span><span class="sxs-lookup"><span data-stu-id="d4986-282">About Windows Remote Management</span></span>](/windows/desktop/WinRM/about-windows-remote-management)

[<span data-ttu-id="d4986-283">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="d4986-283">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="d4986-284">WS-Management 通訊協定</span><span class="sxs-lookup"><span data-stu-id="d4986-284">WS-Management Protocol</span></span>](/windows/desktop/WinRM/ws-management-protocol)
