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
# <span data-ttu-id="64868-103">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="64868-103">Stop-Computer</span></span>

## <span data-ttu-id="64868-104">概要</span><span class="sxs-lookup"><span data-stu-id="64868-104">SYNOPSIS</span></span>
<span data-ttu-id="64868-105">將本機電腦和遠端電腦停止 (關機)。</span><span class="sxs-lookup"><span data-stu-id="64868-105">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="64868-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="64868-106">SYNTAX</span></span>

### <span data-ttu-id="64868-107">全部</span><span class="sxs-lookup"><span data-stu-id="64868-107">All</span></span>

```
Stop-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="64868-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="64868-108">DESCRIPTION</span></span>

<span data-ttu-id="64868-109">此 `Stop-Computer` Cmdlet 會將本機電腦和遠端電腦關機。</span><span class="sxs-lookup"><span data-stu-id="64868-109">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="64868-110">您可以使用的參數 `Stop-Computer` ，以背景工作方式執行關機作業、指定驗證等級和替代認證、限制為了執行命令所建立的並行連線，以及強制立即關機。</span><span class="sxs-lookup"><span data-stu-id="64868-110">You can use the parameters of `Stop-Computer` to run the shutdown operations as a background job, to specify the authentication levels and alternate credentials, to limit the concurrent connections that are created to run the command, and to force an immediate shut down.</span></span>

<span data-ttu-id="64868-111">除非您使用 **AsJob** 參數，否則這個 Cmdlet 不需要 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="64868-111">This cmdlet doesn't require PowerShell remoting unless you use the **AsJob** parameter.</span></span>

## <span data-ttu-id="64868-112">範例</span><span class="sxs-lookup"><span data-stu-id="64868-112">EXAMPLES</span></span>

### <span data-ttu-id="64868-113">範例1：關閉本機電腦</span><span class="sxs-lookup"><span data-stu-id="64868-113">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="64868-114">此範例會將本機電腦關機。</span><span class="sxs-lookup"><span data-stu-id="64868-114">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="64868-115">範例2：關閉兩部遠端電腦和本機電腦</span><span class="sxs-lookup"><span data-stu-id="64868-115">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="64868-116">此範例會停止兩部遠端電腦和本機電腦。</span><span class="sxs-lookup"><span data-stu-id="64868-116">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="64868-117">`Stop-Computer` 使用 **ComputerName** 參數來指定兩部遠端電腦和本機電腦。</span><span class="sxs-lookup"><span data-stu-id="64868-117">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="64868-118">每部電腦都已關閉。</span><span class="sxs-lookup"><span data-stu-id="64868-118">Each computer is shut down.</span></span>

### <span data-ttu-id="64868-119">範例3：將遠端電腦關閉為背景工作</span><span class="sxs-lookup"><span data-stu-id="64868-119">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="64868-120">在此範例中，會 `Stop-Computer` 在兩部遠端電腦上以背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="64868-120">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" -AsJob
$results = $j | Receive-Job
$results
```

<span data-ttu-id="64868-121">`Stop-Computer` 使用 **ComputerName** 參數來指定兩部遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="64868-121">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="64868-122">**AsJob** 參數會以背景工作的方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="64868-122">The **AsJob** parameter runs the command as a background job.</span></span> <span data-ttu-id="64868-123">工作物件會儲存在變數中 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="64868-123">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="64868-124">變數中的工作物件 `$j` 會向下傳送至管線 `Receive-Job` ，以取得工作結果。</span><span class="sxs-lookup"><span data-stu-id="64868-124">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="64868-125">物件會儲存在變數中 `$results` 。</span><span class="sxs-lookup"><span data-stu-id="64868-125">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="64868-126">此 `$results` 變數會在 PowerShell 主控台中顯示工作資訊。</span><span class="sxs-lookup"><span data-stu-id="64868-126">The `$results` variable displays the job information in the PowerShell console.</span></span>

<span data-ttu-id="64868-127">由於 **AsJob** 會在本機電腦上建立工作，並自動將結果傳回本機電腦，因此您可以用 `Receive-Job` 本機命令的形式執行。</span><span class="sxs-lookup"><span data-stu-id="64868-127">Because **AsJob** creates the job on the local computer and automatically returns the results to the local computer, you can run `Receive-Job` as a local command.</span></span>

### <span data-ttu-id="64868-128">範例4：將遠端電腦關機</span><span class="sxs-lookup"><span data-stu-id="64868-128">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="64868-129">此範例會使用指定的驗證來關閉遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="64868-129">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

<span data-ttu-id="64868-130">`Stop-Computer` 使用 **ComputerName** 參數來指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="64868-130">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="64868-131">模擬 **參數會** 指定自訂的模擬，而 **DcomAuthentication** 參數會指定驗證層級設定。</span><span class="sxs-lookup"><span data-stu-id="64868-131">The **Impersonation** parameter specifies a customized impersonation and the **DcomAuthentication** parameter specifies authentication-level settings.</span></span>

### <span data-ttu-id="64868-132">範例5：關閉網域中的電腦</span><span class="sxs-lookup"><span data-stu-id="64868-132">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="64868-133">在此範例中，命令會強制立即關閉指定網域中的所有電腦。</span><span class="sxs-lookup"><span data-stu-id="64868-133">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -ThrottleLimit 10 -Credential $c
```

<span data-ttu-id="64868-134">`Get-Content` 使用 **Path** 參數，以網域電腦清單取得目前目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="64868-134">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="64868-135">物件會儲存在變數中 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="64868-135">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="64868-136">`Get-Credential` 使用 **Credential** 參數來指定網域系統管理員的認證。</span><span class="sxs-lookup"><span data-stu-id="64868-136">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="64868-137">認證會儲存在變數中 `$c` 。</span><span class="sxs-lookup"><span data-stu-id="64868-137">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="64868-138">`Stop-Computer` 以變數中 **電腦的電腦** 清單，關閉指定的電腦 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="64868-138">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="64868-139">**Force** 參數會強制立即關機。</span><span class="sxs-lookup"><span data-stu-id="64868-139">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="64868-140">**ThrottleLimit** 參數會將命令限制為10個並行連接。</span><span class="sxs-lookup"><span data-stu-id="64868-140">The **ThrottleLimit** parameter limits the command to 10 concurrent connections.</span></span> <span data-ttu-id="64868-141">**Credential** 參數會提交儲存在變數中的認證 `$c` 。</span><span class="sxs-lookup"><span data-stu-id="64868-141">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="64868-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="64868-142">PARAMETERS</span></span>

### <span data-ttu-id="64868-143">-AsJob</span><span class="sxs-lookup"><span data-stu-id="64868-143">-AsJob</span></span>

<span data-ttu-id="64868-144">指出此 Cmdlet 會以背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="64868-144">Indicates that this cmdlet runs as a background job.</span></span>

<span data-ttu-id="64868-145">若要使用這個參數，本機電腦和遠端電腦必須設定為進行遠端處理，而在 Windows Vista 和更新版本的 Windows 作業系統上，您必須使用 [以 **系統管理員身分執行** ] 選項開啟 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="64868-145">To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="64868-146">如需詳細資訊，請參閱[about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64868-146">For more information, see [about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md).</span></span>

<span data-ttu-id="64868-147">當您指定 **AsJob** 參數時，此命令會立即傳回代表背景工作的物件。</span><span class="sxs-lookup"><span data-stu-id="64868-147">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="64868-148">工作完成後，您可以繼續在工作階段中工作。</span><span class="sxs-lookup"><span data-stu-id="64868-148">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="64868-149">工作會在本機電腦上建立，而來自遠端電腦的結果則會自動傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="64868-149">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="64868-150">若要取得工作結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64868-150">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="64868-151">如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) 和 [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="64868-151">For more information about PowerShell background jobs, see [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) and [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md).</span></span>

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

### <span data-ttu-id="64868-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="64868-152">-ComputerName</span></span>

<span data-ttu-id="64868-153">指定要停止的電腦。</span><span class="sxs-lookup"><span data-stu-id="64868-153">Specifies the computers to stop.</span></span> <span data-ttu-id="64868-154">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="64868-154">The default is the local computer.</span></span>

<span data-ttu-id="64868-155">請輸入一或多部電腦的 NETBIOS 名稱、IP 位址或完整網域名稱 (以逗號分隔的清單方式)。</span><span class="sxs-lookup"><span data-stu-id="64868-155">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="64868-156">若要指定本機電腦，請輸入電腦名稱稱或 localhost。</span><span class="sxs-lookup"><span data-stu-id="64868-156">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="64868-157">此參數不依賴 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="64868-157">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="64868-158">即使您的電腦未設定為執行遠端命令，您也可以使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="64868-158">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

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

### <span data-ttu-id="64868-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="64868-159">-Confirm</span></span>

<span data-ttu-id="64868-160">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="64868-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="64868-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="64868-161">-Credential</span></span>

<span data-ttu-id="64868-162">指定具有執行此動作之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="64868-162">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="64868-163">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="64868-163">The default is the current user.</span></span>

<span data-ttu-id="64868-164">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="64868-164">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="64868-165">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="64868-165">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="64868-166">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="64868-166">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="64868-167">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="64868-167">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="64868-168">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="64868-168">-DcomAuthentication</span></span>

<span data-ttu-id="64868-169">指定此 Cmdlet 與 WMI 搭配使用的驗證層級。</span><span class="sxs-lookup"><span data-stu-id="64868-169">Specifies the authentication level that this cmdlet uses with WMI.</span></span> <span data-ttu-id="64868-170">`Stop-Computer` 使用 WMI。</span><span class="sxs-lookup"><span data-stu-id="64868-170">`Stop-Computer` uses WMI.</span></span> <span data-ttu-id="64868-171">預設值為 **Packet** 。</span><span class="sxs-lookup"><span data-stu-id="64868-171">The default value is **Packet** .</span></span>

<span data-ttu-id="64868-172">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="64868-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="64868-173">**預設值** ： Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="64868-173">**Default** : Windows Authentication.</span></span>
- <span data-ttu-id="64868-174">**None** ：沒有 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="64868-174">**None** : No COM authentication.</span></span>
- <span data-ttu-id="64868-175">**Connect** ：連接層級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="64868-175">**Connect** : Connect-level COM authentication.</span></span>
- <span data-ttu-id="64868-176">**呼叫** ：呼叫層級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="64868-176">**Call** : Call-level COM authentication.</span></span>
- <span data-ttu-id="64868-177">封 **包** ：封包層級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="64868-177">**Packet** : Packet-level COM authentication.</span></span>
- <span data-ttu-id="64868-178">**PacketIntegrity** ：封包完整性等級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="64868-178">**PacketIntegrity** : Packet Integrity-level COM authentication.</span></span>
- <span data-ttu-id="64868-179">**PacketPrivacy** ：封包隱私權等級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="64868-179">**PacketPrivacy** : Packet Privacy-level COM authentication.</span></span>
- <span data-ttu-id="64868-180">**未** 變更：與上一個命令相同。</span><span class="sxs-lookup"><span data-stu-id="64868-180">**Unchanged** : Same as the previous command.</span></span>

<span data-ttu-id="64868-181">如需此參數值的詳細資訊，請參閱 [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel)。</span><span class="sxs-lookup"><span data-stu-id="64868-181">For more information about the values of this parameter, see [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel).</span></span>

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

### <span data-ttu-id="64868-182">-Force</span><span class="sxs-lookup"><span data-stu-id="64868-182">-Force</span></span>

<span data-ttu-id="64868-183">強制立即關閉電腦。</span><span class="sxs-lookup"><span data-stu-id="64868-183">Forces an immediate shut down of the computer.</span></span>

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

### <span data-ttu-id="64868-184">-Impersonation</span><span class="sxs-lookup"><span data-stu-id="64868-184">-Impersonation</span></span>

<span data-ttu-id="64868-185">指定此 Cmdlet 呼叫 WMI 時要使用的模擬等級。</span><span class="sxs-lookup"><span data-stu-id="64868-185">Specifies the impersonation level to use when this cmdlet calls WMI.</span></span> <span data-ttu-id="64868-186">預設值為 [模擬 **]。**</span><span class="sxs-lookup"><span data-stu-id="64868-186">The default value is **Impersonate** .</span></span>

<span data-ttu-id="64868-187">`Stop-Computer` 使用 WMI。</span><span class="sxs-lookup"><span data-stu-id="64868-187">`Stop-Computer` uses WMI.</span></span> <span data-ttu-id="64868-188">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="64868-188">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="64868-189">**預設** 值：預設模擬。</span><span class="sxs-lookup"><span data-stu-id="64868-189">**Default** : Default impersonation.</span></span>
- <span data-ttu-id="64868-190">**匿名** ：隱藏呼叫端的身分識別。</span><span class="sxs-lookup"><span data-stu-id="64868-190">**Anonymous** : Hides the identity of the caller.</span></span>
- <span data-ttu-id="64868-191">**識別** ：允許物件查詢呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="64868-191">**Identify** : Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="64868-192">模擬 **：允許** 物件使用呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="64868-192">**Impersonate** : Allows objects to use the credentials of the caller.</span></span>

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

### <span data-ttu-id="64868-193">-Protocol</span><span class="sxs-lookup"><span data-stu-id="64868-193">-Protocol</span></span>

<span data-ttu-id="64868-194">指定要用來重新啟動電腦的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="64868-194">Specifies which protocol to use to restart the computers.</span></span> <span data-ttu-id="64868-195">此參數可接受的值為： **WSMan** 和 **DCOM** 。</span><span class="sxs-lookup"><span data-stu-id="64868-195">The acceptable values for this parameter are: **WSMan** and **DCOM** .</span></span> <span data-ttu-id="64868-196">預設值為 **DCOM** 。</span><span class="sxs-lookup"><span data-stu-id="64868-196">The default value is **DCOM** .</span></span>

<span data-ttu-id="64868-197">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="64868-197">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="64868-198">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="64868-198">-ThrottleLimit</span></span>

<span data-ttu-id="64868-199">指定為執行此命令可建立的最大同時連線數。</span><span class="sxs-lookup"><span data-stu-id="64868-199">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="64868-200">若省略此參數，或輸入值為 0，則會使用預設值 32。</span><span class="sxs-lookup"><span data-stu-id="64868-200">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="64868-201">節流限制僅適用於目前命令，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="64868-201">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="64868-202">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="64868-202">-WsmanAuthentication</span></span>

<span data-ttu-id="64868-203">指定當此 Cmdlet 使用 WSMan 通訊協定時，用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="64868-203">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="64868-204">預設值為 **Default** 。</span><span class="sxs-lookup"><span data-stu-id="64868-204">The default value is **Default** .</span></span>

<span data-ttu-id="64868-205">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="64868-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="64868-206">基本</span><span class="sxs-lookup"><span data-stu-id="64868-206">Basic</span></span>
- <span data-ttu-id="64868-207">CredSSP</span><span class="sxs-lookup"><span data-stu-id="64868-207">CredSSP</span></span>
- <span data-ttu-id="64868-208">預設</span><span class="sxs-lookup"><span data-stu-id="64868-208">Default</span></span>
- <span data-ttu-id="64868-209">Digest</span><span class="sxs-lookup"><span data-stu-id="64868-209">Digest</span></span>
- <span data-ttu-id="64868-210">Kerberos</span><span class="sxs-lookup"><span data-stu-id="64868-210">Kerberos</span></span>
- <span data-ttu-id="64868-211">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="64868-211">Negotiate.</span></span>

<span data-ttu-id="64868-212">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="64868-212">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="64868-213">認證安全性服務提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="64868-213">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="64868-214">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="64868-214">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="64868-215">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="64868-215">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="64868-216">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="64868-216">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="64868-217">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="64868-217">-WhatIf</span></span>

<span data-ttu-id="64868-218">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="64868-218">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="64868-219">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64868-219">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="64868-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="64868-220">CommonParameters</span></span>

<span data-ttu-id="64868-221">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="64868-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="64868-222">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="64868-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="64868-223">輸入</span><span class="sxs-lookup"><span data-stu-id="64868-223">INPUTS</span></span>

### <span data-ttu-id="64868-224">無</span><span class="sxs-lookup"><span data-stu-id="64868-224">None</span></span>

<span data-ttu-id="64868-225">您無法透過管道傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64868-225">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="64868-226">輸出</span><span class="sxs-lookup"><span data-stu-id="64868-226">OUTPUTS</span></span>

### <span data-ttu-id="64868-227">無或 System.Management.Automation.RemotingJob</span><span class="sxs-lookup"><span data-stu-id="64868-227">None or System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="64868-228">如果您指定 **AsJob** 參數，Cmdlet 會傳回 **system.management.automation.remotingjob** 物件。</span><span class="sxs-lookup"><span data-stu-id="64868-228">The cmdlet returns a **System.Management.Automation.RemotingJob** object, if you specify the **AsJob** parameter.</span></span> <span data-ttu-id="64868-229">否則，它不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="64868-229">Otherwise, it doesn't generate any output.</span></span>

## <span data-ttu-id="64868-230">注意</span><span class="sxs-lookup"><span data-stu-id="64868-230">NOTES</span></span>

<span data-ttu-id="64868-231">此 Cmdlet 會使用 **Win32_OperatingSystem** WMI 類別的 **Win32Shutdown** 方法。</span><span class="sxs-lookup"><span data-stu-id="64868-231">This cmdlet uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="64868-232">此方法需要針對用來重新開機電腦的使用者帳戶啟用 **SeShutdownPrivilege** 許可權。</span><span class="sxs-lookup"><span data-stu-id="64868-232">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

## <span data-ttu-id="64868-233">相關連結</span><span class="sxs-lookup"><span data-stu-id="64868-233">RELATED LINKS</span></span>

[<span data-ttu-id="64868-234">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="64868-234">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="64868-235">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="64868-235">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="64868-236">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="64868-236">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="64868-237">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="64868-237">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="64868-238">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="64868-238">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="64868-239">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="64868-239">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="64868-240">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="64868-240">Test-Connection</span></span>](Test-Connection.md)
