---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: ce9e19140cb0bb8fd9172fa7ca7929fb696f9c65
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205503"
---
# <span data-ttu-id="503ae-103">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="503ae-103">Restart-Computer</span></span>

## <span data-ttu-id="503ae-104">概要</span><span class="sxs-lookup"><span data-stu-id="503ae-104">SYNOPSIS</span></span>
<span data-ttu-id="503ae-105">重新開機本機電腦和遠端電腦上的作業系統。</span><span class="sxs-lookup"><span data-stu-id="503ae-105">Restarts the operating system on local and remote computers.</span></span>

## <span data-ttu-id="503ae-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="503ae-106">SYNTAX</span></span>

### <span data-ttu-id="503ae-107">DefaultSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="503ae-107">DefaultSet (Default)</span></span>

```
Restart-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential]<PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="503ae-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="503ae-108">DESCRIPTION</span></span>

<span data-ttu-id="503ae-109">`Restart-Computer`Cmdlet 會重新開機本機電腦和遠端電腦上的作業系統。</span><span class="sxs-lookup"><span data-stu-id="503ae-109">The `Restart-Computer` cmdlet restarts the operating system on the local and remote computers.</span></span>

<span data-ttu-id="503ae-110">您可以使用的參數 `Restart-Computer` 來執行重新開機作業、指定驗證等級和替代認證、限制同時執行的作業，以及強制立即重新開機。</span><span class="sxs-lookup"><span data-stu-id="503ae-110">You can use the parameters of `Restart-Computer` to run the restart operations, to specify the authentication levels and alternate credentials, to limit the operations that run at the same time, and to force an immediate restart.</span></span>

<span data-ttu-id="503ae-111">從 Windows PowerShell 3.0 開始，您可以先等候重新開機完成，再執行下一個命令。</span><span class="sxs-lookup"><span data-stu-id="503ae-111">Starting in Windows PowerShell 3.0, you can wait for the restart to complete before you run the next command.</span></span> <span data-ttu-id="503ae-112">指定等候超時和查詢間隔，並等候特定服務可在重新開機的電腦上使用。</span><span class="sxs-lookup"><span data-stu-id="503ae-112">Specify a waiting time-out and query interval, and wait for particular services to be available on the restarted computer.</span></span> <span data-ttu-id="503ae-113">這項功能可讓您在腳本和函式中使用非常實用 `Restart-Computer` 。</span><span class="sxs-lookup"><span data-stu-id="503ae-113">This feature makes it practical to use `Restart-Computer` in scripts and functions.</span></span>

## <span data-ttu-id="503ae-114">範例</span><span class="sxs-lookup"><span data-stu-id="503ae-114">EXAMPLES</span></span>

### <span data-ttu-id="503ae-115">範例1：重新開機本機電腦</span><span class="sxs-lookup"><span data-stu-id="503ae-115">Example 1: Restart the local computer</span></span>

<span data-ttu-id="503ae-116">`Restart-Computer` 重新開機本機電腦。</span><span class="sxs-lookup"><span data-stu-id="503ae-116">`Restart-Computer` restarts the local computer.</span></span>

```powershell
Restart-Computer
```

### <span data-ttu-id="503ae-117">範例2：重新開機多部電腦</span><span class="sxs-lookup"><span data-stu-id="503ae-117">Example 2: Restart multiple computers</span></span>

<span data-ttu-id="503ae-118">`Restart-Computer` 可以重新開機遠端和本機電腦。</span><span class="sxs-lookup"><span data-stu-id="503ae-118">`Restart-Computer` can restart remote and local computers.</span></span> <span data-ttu-id="503ae-119">**ComputerName** 參數接受電腦名稱稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="503ae-119">The **ComputerName** parameter accepts an array of computer names.</span></span>

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### <span data-ttu-id="503ae-120">範例3：從文字檔取得電腦名稱稱</span><span class="sxs-lookup"><span data-stu-id="503ae-120">Example 3: Get computer names from a text file</span></span>

<span data-ttu-id="503ae-121">`Restart-Computer` 從文字檔取得電腦名稱稱的清單，並重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="503ae-121">`Restart-Computer` gets a list of computer names from a text file and restarts the computers.</span></span> <span data-ttu-id="503ae-122">未指定 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="503ae-122">The **ComputerName** parameter isn't specified.</span></span> <span data-ttu-id="503ae-123">但因為它是第一個位置參數，所以它會接受從管線傳送的文字檔中的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="503ae-123">But because it's the first position parameter, it accepts the computer names from the text file that are sent down the pipeline.</span></span>

```powershell
Get-Content -Path C:\Domain01.txt | Restart-Computer
```

<span data-ttu-id="503ae-124">`Get-Content` 使用 **Path** 參數從文字檔中取得電腦名稱稱的清單， **Domain01.txt** 。</span><span class="sxs-lookup"><span data-stu-id="503ae-124">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt** .</span></span> <span data-ttu-id="503ae-125">電腦名稱稱會沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="503ae-125">The computer names are sent down the pipeline.</span></span> <span data-ttu-id="503ae-126">`Restart-Computer` 重新開機每部電腦。</span><span class="sxs-lookup"><span data-stu-id="503ae-126">`Restart-Computer` restarts each computer.</span></span>

### <span data-ttu-id="503ae-127">範例4：強制重新開機文字檔中列出的電腦</span><span class="sxs-lookup"><span data-stu-id="503ae-127">Example 4: Force restart of computers listed in a text file</span></span>

<span data-ttu-id="503ae-128">此範例會強制立即重新開機檔案中列出的電腦 `Domain01.txt` 。</span><span class="sxs-lookup"><span data-stu-id="503ae-128">This example forces an immediate restart of the computers listed in the `Domain01.txt` file.</span></span> <span data-ttu-id="503ae-129">文字檔中的電腦名稱稱會儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="503ae-129">The computer names from the text file are stored in a variable.</span></span> <span data-ttu-id="503ae-130">**Force** 參數會強制立即重新開機。</span><span class="sxs-lookup"><span data-stu-id="503ae-130">The **Force** parameter forces an immediate restart.</span></span>

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force
```

<span data-ttu-id="503ae-131">`Get-Content` 使用 **Path** 參數從文字檔中取得電腦名稱稱的清單， **Domain01.txt** 。</span><span class="sxs-lookup"><span data-stu-id="503ae-131">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt** .</span></span> <span data-ttu-id="503ae-132">電腦名稱稱會儲存在變數中 `$Names` 。</span><span class="sxs-lookup"><span data-stu-id="503ae-132">The computer names are stored in the variable `$Names`.</span></span> <span data-ttu-id="503ae-133">`Get-Credential` 提示您輸入使用者名稱和密碼，並將值儲存在變數中 `$Creds` 。</span><span class="sxs-lookup"><span data-stu-id="503ae-133">`Get-Credential` prompts you for a username and password and stores the values in the variable `$Creds`.</span></span> <span data-ttu-id="503ae-134">`Restart-Computer` 使用 **ComputerName** 和 **Credential** 參數及其變數。</span><span class="sxs-lookup"><span data-stu-id="503ae-134">`Restart-Computer` uses the **ComputerName** and **Credential** parameters with their variables.</span></span> <span data-ttu-id="503ae-135">**Force** 參數會導致立即重新開機每一部電腦。</span><span class="sxs-lookup"><span data-stu-id="503ae-135">The **Force** parameter causes an immediate restart of each computer.</span></span>

### <span data-ttu-id="503ae-136">範例6：重新開機遠端電腦並等候 PowerShell</span><span class="sxs-lookup"><span data-stu-id="503ae-136">Example 6: Restart a remote computer and wait for PowerShell</span></span>

<span data-ttu-id="503ae-137">`Restart-Computer` 重新開機遠端電腦，然後等候最多5分鐘的時間 (300 秒) ，讓 PowerShell 在重新開機的電腦上變成可用，然後再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="503ae-137">`Restart-Computer` restarts the remote computer and then waits up to 5 minutes (300 seconds) for PowerShell to become available on the restarted computer before it continues.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

<span data-ttu-id="503ae-138">`Restart-Computer` 使用 **ComputerName** 參數來指定 **Server01** 。</span><span class="sxs-lookup"><span data-stu-id="503ae-138">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01** .</span></span> <span data-ttu-id="503ae-139">**Wait** 參數會等候重新開機完成。</span><span class="sxs-lookup"><span data-stu-id="503ae-139">The **Wait** parameter waits for the restart to finish.</span></span> <span data-ttu-id="503ae-140">的 **會指定 PowerShell** 可以在遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="503ae-140">The **For** specifies that PowerShell can run commands on the remote computer.</span></span> <span data-ttu-id="503ae-141">Timeout 參數指定五分鐘的等候 **時間** 。</span><span class="sxs-lookup"><span data-stu-id="503ae-141">The **Timeout** parameter specifies a five-minute wait.</span></span> <span data-ttu-id="503ae-142">**Delay** 參數會每隔兩秒查詢一次遠端電腦，以判斷是否已重新開機。</span><span class="sxs-lookup"><span data-stu-id="503ae-142">The **Delay** parameter queries the remote computer every two seconds to determine whether it's restarted.</span></span>

### <span data-ttu-id="503ae-143">範例7：使用 WsmanAuthentication 重新開機電腦</span><span class="sxs-lookup"><span data-stu-id="503ae-143">Example 7: Restart a computer by using WsmanAuthentication</span></span>

<span data-ttu-id="503ae-144">`Restart-Computer` 使用 **WsmanAuthentication** 機制重新開機遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="503ae-144">`Restart-Computer` restarts the remote computer using the **WsmanAuthentication** mechanism.</span></span>
<span data-ttu-id="503ae-145">Kerberos 驗證會決定目前使用者是否具有重新開機遠端電腦的許可權。</span><span class="sxs-lookup"><span data-stu-id="503ae-145">Kerberos authentication determines whether the current user has permission to restart the remote computer.</span></span> <span data-ttu-id="503ae-146">如需詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="503ae-146">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

```powershell
Restart-Computer -ComputerName Server01 -WsmanAuthentication Kerberos
```

<span data-ttu-id="503ae-147">`Restart-Computer` 使用 **ComputerName** 參數來指定遠端電腦 **Server01** 。</span><span class="sxs-lookup"><span data-stu-id="503ae-147">`Restart-Computer` uses the **ComputerName** parameter to specify the remote computer, **Server01** .</span></span>
<span data-ttu-id="503ae-148">**WsmanAuthentication** 參數會將驗證方法指定為 **Kerberos** 。</span><span class="sxs-lookup"><span data-stu-id="503ae-148">The **WsmanAuthentication** parameter specifies the authentication method as **Kerberos** .</span></span>

## <span data-ttu-id="503ae-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="503ae-149">PARAMETERS</span></span>

### <span data-ttu-id="503ae-150">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="503ae-150">-ComputerName</span></span>

<span data-ttu-id="503ae-151">指定一個電腦名稱稱或以逗號分隔的電腦名稱稱陣列。</span><span class="sxs-lookup"><span data-stu-id="503ae-151">Specifies one computer name or a comma-separated array of computer names.</span></span> <span data-ttu-id="503ae-152">`Restart-Computer` 接受管線或變數中的 **ComputerName** 物件。</span><span class="sxs-lookup"><span data-stu-id="503ae-152">`Restart-Computer` accepts **ComputerName** objects from the pipeline or variables.</span></span>

<span data-ttu-id="503ae-153">輸入遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="503ae-153">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="503ae-154">若要指定本機電腦，請輸入電腦名稱稱、點 `.` 或 localhost。</span><span class="sxs-lookup"><span data-stu-id="503ae-154">To specify the local computer, type the computer name, a dot `.`, or localhost.</span></span>

<span data-ttu-id="503ae-155">此參數不依賴 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="503ae-155">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="503ae-156">即使您的電腦未設定為執行遠端命令，您也可以使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="503ae-156">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

<span data-ttu-id="503ae-157">如果未指定 **ComputerName** 參數，則會 `Restart-Computer` 重新開機本機電腦。</span><span class="sxs-lookup"><span data-stu-id="503ae-157">If the **ComputerName** parameter isn't specified, `Restart-Computer` restarts the local computer.</span></span>

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

### <span data-ttu-id="503ae-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="503ae-158">-Credential</span></span>

<span data-ttu-id="503ae-159">指定具有執行此動作之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="503ae-159">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="503ae-160">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="503ae-160">The default is the current user.</span></span>

<span data-ttu-id="503ae-161">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="503ae-161">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="503ae-162">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="503ae-162">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="503ae-163">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="503ae-163">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="503ae-164">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="503ae-164">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="503ae-165">-Delay</span><span class="sxs-lookup"><span data-stu-id="503ae-165">-Delay</span></span>

<span data-ttu-id="503ae-166">指定查詢的頻率（以秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="503ae-166">Specifies the frequency of queries, in seconds.</span></span> <span data-ttu-id="503ae-167">PowerShell 會查詢 **For** 參數指定的服務，以判斷在重新開機電腦之後，服務是否可用。</span><span class="sxs-lookup"><span data-stu-id="503ae-167">PowerShell queries the service specified by the **For** parameter to determine whether the service is available after the computer is restarted.</span></span>

<span data-ttu-id="503ae-168">這個參數只適用于 **Wait** 和 **For** 參數。</span><span class="sxs-lookup"><span data-stu-id="503ae-168">This parameter is valid only together with the **Wait** and **For** parameters.</span></span>

<span data-ttu-id="503ae-169">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="503ae-169">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="503ae-170">如果未指定 **Delay** 參數，會 `Restart-Computer` 使用五秒的延遲。</span><span class="sxs-lookup"><span data-stu-id="503ae-170">If the **Delay** parameter isn't specified, `Restart-Computer` uses a five second delay.</span></span>

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="503ae-171">-For</span><span class="sxs-lookup"><span data-stu-id="503ae-171">-For</span></span>

<span data-ttu-id="503ae-172">指定 PowerShell 的行為，因為它會等候指定的服務或功能在電腦重新開機後變成可用。</span><span class="sxs-lookup"><span data-stu-id="503ae-172">Specifies the behavior of PowerShell as it waits for the specified service or feature to become available after the computer restarts.</span></span> <span data-ttu-id="503ae-173">這個參數只對 **Wait** 參數有效。</span><span class="sxs-lookup"><span data-stu-id="503ae-173">This parameter is only valid with the **Wait** parameter.</span></span>

<span data-ttu-id="503ae-174">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="503ae-174">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="503ae-175">**預設值** ：等候 PowerShell 重新開機。</span><span class="sxs-lookup"><span data-stu-id="503ae-175">**Default** : Waits for PowerShell to restart.</span></span>
- <span data-ttu-id="503ae-176">**Powershell** ：可以在電腦上的 powershell 遠端會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="503ae-176">**PowerShell** : Can run commands in a PowerShell remote session on the computer.</span></span>
- <span data-ttu-id="503ae-177">**WMI** ：接收對電腦 Win32_ComputerSystem 查詢的回覆。</span><span class="sxs-lookup"><span data-stu-id="503ae-177">**WMI** : Receives a reply to a Win32_ComputerSystem query for the computer.</span></span>
- <span data-ttu-id="503ae-178">**WinRM** ：可以使用 WS-Management 來建立連到電腦的遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="503ae-178">**WinRM** : Can establish a remote session to the computer by using WS-Management.</span></span>

<span data-ttu-id="503ae-179">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="503ae-179">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: (All)
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="503ae-180">-Force</span><span class="sxs-lookup"><span data-stu-id="503ae-180">-Force</span></span>

<span data-ttu-id="503ae-181">強制立即重新開機電腦。</span><span class="sxs-lookup"><span data-stu-id="503ae-181">Forces an immediate restart of the computer.</span></span>

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

### <span data-ttu-id="503ae-182">-Timeout</span><span class="sxs-lookup"><span data-stu-id="503ae-182">-Timeout</span></span>

<span data-ttu-id="503ae-183">指定等待的持續時間 (單位為秒)。</span><span class="sxs-lookup"><span data-stu-id="503ae-183">Specifies the duration of the wait, in seconds.</span></span> <span data-ttu-id="503ae-184">當超時時間過後， `Restart-Computer` 即使電腦未重新開機，也會回到命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="503ae-184">When the timeout elapses, `Restart-Computer` returns to the command prompt, even if the computers aren't restarted.</span></span>

<span data-ttu-id="503ae-185">**Timeout** 參數只對 **Wait** 參數有效。</span><span class="sxs-lookup"><span data-stu-id="503ae-185">The **Timeout** parameter is only valid with the **Wait** parameter.</span></span> <span data-ttu-id="503ae-186">**Timeout** 會覆寫 **等待** 參數的無限等待期間。</span><span class="sxs-lookup"><span data-stu-id="503ae-186">**Timeout** overrides the **Wait** parameter's indefinite waiting period.</span></span>

<span data-ttu-id="503ae-187">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="503ae-187">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="503ae-188">-Wait</span><span class="sxs-lookup"><span data-stu-id="503ae-188">-Wait</span></span>

<span data-ttu-id="503ae-189">`Restart-Computer` 抑制 PowerShell 提示字元並封鎖管線，直到電腦重新開機為止。</span><span class="sxs-lookup"><span data-stu-id="503ae-189">`Restart-Computer` suppresses the PowerShell prompt and blocks the pipeline until the computers have restarted.</span></span> <span data-ttu-id="503ae-190">您可以在腳本中使用這個參數來重新開機電腦，然後在重新開機完成時繼續處理。</span><span class="sxs-lookup"><span data-stu-id="503ae-190">You can use this parameter in a script to restart computers and then continue to process when the restart is finished.</span></span>

<span data-ttu-id="503ae-191">**Wait** 參數會無限期地等候電腦重新開機。</span><span class="sxs-lookup"><span data-stu-id="503ae-191">The **Wait** parameter waits indefinitely for the computers to restart.</span></span> <span data-ttu-id="503ae-192">您可以使用 **Timeout** 來調整計時 **，以及使用和\*\*\*\*延遲** 參數來等待特定服務在重新開機的電腦上變成可用。</span><span class="sxs-lookup"><span data-stu-id="503ae-192">You can use **Timeout** to adjust the timing and the **For** and **Delay** parameters to wait for particular services to become available on the restarted computers.</span></span>

<span data-ttu-id="503ae-193">當您重新開機本機電腦時， **Wait** 參數無效。</span><span class="sxs-lookup"><span data-stu-id="503ae-193">The **Wait** parameter isn't valid when you're restarting the local computer.</span></span> <span data-ttu-id="503ae-194">如果 **ComputerName** 參數的值包含遠端電腦和本機電腦的名稱，則會產生在 `Restart-Computer` 本機電腦上 **等候** 的非終止錯誤，但是會等待遠端電腦重新開機。</span><span class="sxs-lookup"><span data-stu-id="503ae-194">If the value of the **ComputerName** parameter contains the names of remote computers and the local computer, `Restart-Computer` generates a non-terminating error for **Wait** on the local computer, but waits for the remote computers to restart.</span></span>

<span data-ttu-id="503ae-195">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="503ae-195">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="503ae-196">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="503ae-196">-WsmanAuthentication</span></span>

<span data-ttu-id="503ae-197">指定用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="503ae-197">Specifies the mechanism that is used to authenticate the user credentials.</span></span> <span data-ttu-id="503ae-198">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="503ae-198">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="503ae-199">此參數可接受的值為： **Basic** 、 **CredSSP** 、 **Default** 、 **Digest** 、 **Kerberos** 和 **Negotiate** 。</span><span class="sxs-lookup"><span data-stu-id="503ae-199">The acceptable values for this parameter are: **Basic** , **CredSSP** , **Default** , **Digest** , **Kerberos** , and **Negotiate** .</span></span>

<span data-ttu-id="503ae-200">如需詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="503ae-200">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="503ae-201">認證安全性服務提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="503ae-201">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="503ae-202">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="503ae-202">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="503ae-203">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="503ae-203">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="503ae-204">-Confirm</span><span class="sxs-lookup"><span data-stu-id="503ae-204">-Confirm</span></span>

<span data-ttu-id="503ae-205">在執行之前提示您確認 `Restart-Computer` 。</span><span class="sxs-lookup"><span data-stu-id="503ae-205">Prompts you for confirmation before running `Restart-Computer`.</span></span>

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

### <span data-ttu-id="503ae-206">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="503ae-206">-WhatIf</span></span>

<span data-ttu-id="503ae-207">顯示執行時所發生的情況 `Restart-Computer` 。</span><span class="sxs-lookup"><span data-stu-id="503ae-207">Shows what would happen if the `Restart-Computer` runs.</span></span> <span data-ttu-id="503ae-208">`Restart-Computer`Cmdlet 不會執行。</span><span class="sxs-lookup"><span data-stu-id="503ae-208">The `Restart-Computer` cmdlet isn't run.</span></span>

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

### <span data-ttu-id="503ae-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="503ae-209">CommonParameters</span></span>

<span data-ttu-id="503ae-210">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="503ae-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="503ae-211">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="503ae-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="503ae-212">輸入</span><span class="sxs-lookup"><span data-stu-id="503ae-212">INPUTS</span></span>

### <span data-ttu-id="503ae-213">System.String</span><span class="sxs-lookup"><span data-stu-id="503ae-213">System.String</span></span>

<span data-ttu-id="503ae-214">`Restart-Computer` 接受來自管線或變數的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="503ae-214">`Restart-Computer` accepts computer names from the pipeline or variables.</span></span>

## <span data-ttu-id="503ae-215">輸出</span><span class="sxs-lookup"><span data-stu-id="503ae-215">OUTPUTS</span></span>

### <span data-ttu-id="503ae-216">無</span><span class="sxs-lookup"><span data-stu-id="503ae-216">None</span></span>

<span data-ttu-id="503ae-217">`Restart-Computer` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="503ae-217">`Restart-Computer` doesn't generate any output.</span></span>

## <span data-ttu-id="503ae-218">注意</span><span class="sxs-lookup"><span data-stu-id="503ae-218">NOTES</span></span>

- <span data-ttu-id="503ae-219">`Restart-Computer` 只適用于執行 Windows 的電腦，而且需要 WinRM 和 WMI 來關閉系統，包括本機系統。</span><span class="sxs-lookup"><span data-stu-id="503ae-219">`Restart-Computer` only works on computers running Windows and requires WinRM and WMI to shutdown a system, including the local system.</span></span>
- <span data-ttu-id="503ae-220">`Restart-Computer`使用 Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem)類別的[Win32Shutdown 方法](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem)。</span><span class="sxs-lookup"><span data-stu-id="503ae-220">`Restart-Computer` uses the [Win32Shutdown method](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) of the Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) class.</span></span> <span data-ttu-id="503ae-221">此方法需要針對用來重新開機電腦的使用者帳戶啟用 **SeShutdownPrivilege** 許可權。</span><span class="sxs-lookup"><span data-stu-id="503ae-221">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

## <span data-ttu-id="503ae-222">相關連結</span><span class="sxs-lookup"><span data-stu-id="503ae-222">RELATED LINKS</span></span>

[<span data-ttu-id="503ae-223">關於 Windows 遠端管理</span><span class="sxs-lookup"><span data-stu-id="503ae-223">About Windows Remote Management</span></span>](/windows/desktop/WinRM/about-windows-remote-management)

[<span data-ttu-id="503ae-224">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="503ae-224">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="503ae-225">WS-Management 通訊協定</span><span class="sxs-lookup"><span data-stu-id="503ae-225">WS-Management Protocol</span></span>](/windows/desktop/WinRM/ws-management-protocol)
