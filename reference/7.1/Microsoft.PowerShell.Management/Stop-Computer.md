---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: a1fa09116e7069f3fc7f3d196bffd20f491a93e2
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205659"
---
# <span data-ttu-id="38578-103">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="38578-103">Stop-Computer</span></span>

## <span data-ttu-id="38578-104">概要</span><span class="sxs-lookup"><span data-stu-id="38578-104">SYNOPSIS</span></span>
<span data-ttu-id="38578-105">將本機電腦和遠端電腦停止 (關機)。</span><span class="sxs-lookup"><span data-stu-id="38578-105">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="38578-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="38578-106">SYNTAX</span></span>

### <span data-ttu-id="38578-107">全部</span><span class="sxs-lookup"><span data-stu-id="38578-107">All</span></span>

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="38578-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="38578-108">DESCRIPTION</span></span>

<span data-ttu-id="38578-109">此 `Stop-Computer` Cmdlet 會將本機電腦和遠端電腦關機。</span><span class="sxs-lookup"><span data-stu-id="38578-109">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="38578-110">您可以使用的參數 `Stop-Computer` 來指定驗證等級和替代認證，以及強制立即關機。</span><span class="sxs-lookup"><span data-stu-id="38578-110">You can use the parameters of `Stop-Computer` to specify the authentication levels and alternate credentials, and to force an immediate shut down.</span></span>

<span data-ttu-id="38578-111">在 PowerShell 7.1 中， `Stop-Computer` 已為 Linux 和 macOS 新增。</span><span class="sxs-lookup"><span data-stu-id="38578-111">In PowerShell 7.1, `Stop-Computer` was added for Linux and macOS.</span></span> <span data-ttu-id="38578-112">這些參數在這些平臺上不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="38578-112">The parameters have no effect on these platforms.</span></span> <span data-ttu-id="38578-113">此 Cmdlet 只會呼叫原生命令 `/sbin/shutdown` 。</span><span class="sxs-lookup"><span data-stu-id="38578-113">The cmdlet is just calling the native command `/sbin/shutdown`.</span></span>

## <span data-ttu-id="38578-114">範例</span><span class="sxs-lookup"><span data-stu-id="38578-114">EXAMPLES</span></span>

### <span data-ttu-id="38578-115">範例1：關閉本機電腦</span><span class="sxs-lookup"><span data-stu-id="38578-115">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="38578-116">此範例會將本機電腦關機。</span><span class="sxs-lookup"><span data-stu-id="38578-116">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="38578-117">範例2：關閉兩部遠端電腦和本機電腦</span><span class="sxs-lookup"><span data-stu-id="38578-117">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="38578-118">此範例會停止兩部遠端電腦和本機電腦。</span><span class="sxs-lookup"><span data-stu-id="38578-118">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="38578-119">`Stop-Computer` 使用 **ComputerName** 參數來指定兩部遠端電腦和本機電腦。</span><span class="sxs-lookup"><span data-stu-id="38578-119">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="38578-120">每部電腦都已關閉。</span><span class="sxs-lookup"><span data-stu-id="38578-120">Each computer is shut down.</span></span>

### <span data-ttu-id="38578-121">範例3：將遠端電腦關閉為背景工作</span><span class="sxs-lookup"><span data-stu-id="38578-121">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="38578-122">在此範例中，會 `Stop-Computer` 在兩部遠端電腦上以背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="38578-122">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

<span data-ttu-id="38578-123">背景運算子會 `&` `Stop-Computer` 以背景工作的方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="38578-123">The background operator `&` runs the `Stop-Computer` command as a background job.</span></span> <span data-ttu-id="38578-124">如需詳細資訊，請參閱 [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-)。</span><span class="sxs-lookup"><span data-stu-id="38578-124">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

<span data-ttu-id="38578-125">`Stop-Computer` 使用 **ComputerName** 參數來指定兩部遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="38578-125">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="38578-126">`&`背景運算子會以背景工作的方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="38578-126">The `&` background operator runs the command as a background job.</span></span> <span data-ttu-id="38578-127">工作物件會儲存在變數中 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="38578-127">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="38578-128">變數中的工作物件 `$j` 會向下傳送至管線 `Receive-Job` ，以取得工作結果。</span><span class="sxs-lookup"><span data-stu-id="38578-128">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="38578-129">物件會儲存在變數中 `$results` 。</span><span class="sxs-lookup"><span data-stu-id="38578-129">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="38578-130">此 `$results` 變數會在 PowerShell 主控台中顯示工作資訊。</span><span class="sxs-lookup"><span data-stu-id="38578-130">The `$results` variable displays the job information in the PowerShell console.</span></span>

### <span data-ttu-id="38578-131">範例4：將遠端電腦關機</span><span class="sxs-lookup"><span data-stu-id="38578-131">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="38578-132">此範例會使用指定的驗證來關閉遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="38578-132">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

<span data-ttu-id="38578-133">`Stop-Computer` 使用 **ComputerName** 參數來指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="38578-133">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="38578-134">**WsmanAuthentication** 參數會指定使用 Kerberos 來建立遠端連線。</span><span class="sxs-lookup"><span data-stu-id="38578-134">The **WsmanAuthentication** parameter specifies to use Kerberos to establish a remote connection.</span></span>

### <span data-ttu-id="38578-135">範例5：關閉網域中的電腦</span><span class="sxs-lookup"><span data-stu-id="38578-135">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="38578-136">在此範例中，命令會強制立即關閉指定網域中的所有電腦。</span><span class="sxs-lookup"><span data-stu-id="38578-136">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

<span data-ttu-id="38578-137">`Get-Content` 使用 **Path** 參數，以網域電腦清單取得目前目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="38578-137">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="38578-138">物件會儲存在變數中 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="38578-138">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="38578-139">`Get-Credential` 使用 **Credential** 參數來指定網域系統管理員的認證。</span><span class="sxs-lookup"><span data-stu-id="38578-139">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="38578-140">認證會儲存在變數中 `$c` 。</span><span class="sxs-lookup"><span data-stu-id="38578-140">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="38578-141">`Stop-Computer` 以變數中 **電腦的電腦** 清單，關閉指定的電腦 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="38578-141">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="38578-142">**Force** 參數會強制立即關機。</span><span class="sxs-lookup"><span data-stu-id="38578-142">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="38578-143">**Credential** 參數會提交儲存在變數中的認證 `$c` 。</span><span class="sxs-lookup"><span data-stu-id="38578-143">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="38578-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="38578-144">PARAMETERS</span></span>

### <span data-ttu-id="38578-145">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="38578-145">-ComputerName</span></span>

<span data-ttu-id="38578-146">指定要停止的電腦。</span><span class="sxs-lookup"><span data-stu-id="38578-146">Specifies the computers to stop.</span></span> <span data-ttu-id="38578-147">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="38578-147">The default is the local computer.</span></span>

<span data-ttu-id="38578-148">請輸入一或多部電腦的 NETBIOS 名稱、IP 位址或完整網域名稱 (以逗號分隔的清單方式)。</span><span class="sxs-lookup"><span data-stu-id="38578-148">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="38578-149">若要指定本機電腦，請輸入電腦名稱稱或 localhost。</span><span class="sxs-lookup"><span data-stu-id="38578-149">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="38578-150">此參數不依賴 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="38578-150">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="38578-151">即使您的電腦未設定為執行遠端命令，您也可以使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="38578-151">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

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

### <span data-ttu-id="38578-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="38578-152">-Confirm</span></span>

<span data-ttu-id="38578-153">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="38578-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="38578-154">-Credential</span><span class="sxs-lookup"><span data-stu-id="38578-154">-Credential</span></span>

<span data-ttu-id="38578-155">指定具有執行此動作之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="38578-155">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="38578-156">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="38578-156">The default is the current user.</span></span>

<span data-ttu-id="38578-157">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="38578-157">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="38578-158">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="38578-158">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="38578-159">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="38578-159">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="38578-160">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="38578-160">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="38578-161">-Force</span><span class="sxs-lookup"><span data-stu-id="38578-161">-Force</span></span>

<span data-ttu-id="38578-162">強制立即關閉電腦。</span><span class="sxs-lookup"><span data-stu-id="38578-162">Forces an immediate shut down of the computer.</span></span>

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

### <span data-ttu-id="38578-163">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="38578-163">-WsmanAuthentication</span></span>

<span data-ttu-id="38578-164">指定當此 Cmdlet 使用 WSMan 通訊協定時，用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="38578-164">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="38578-165">預設值為 **Default** 。</span><span class="sxs-lookup"><span data-stu-id="38578-165">The default value is **Default** .</span></span>

<span data-ttu-id="38578-166">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="38578-166">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="38578-167">基本</span><span class="sxs-lookup"><span data-stu-id="38578-167">Basic</span></span>
- <span data-ttu-id="38578-168">CredSSP</span><span class="sxs-lookup"><span data-stu-id="38578-168">CredSSP</span></span>
- <span data-ttu-id="38578-169">預設</span><span class="sxs-lookup"><span data-stu-id="38578-169">Default</span></span>
- <span data-ttu-id="38578-170">Digest</span><span class="sxs-lookup"><span data-stu-id="38578-170">Digest</span></span>
- <span data-ttu-id="38578-171">Kerberos</span><span class="sxs-lookup"><span data-stu-id="38578-171">Kerberos</span></span>
- <span data-ttu-id="38578-172">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="38578-172">Negotiate.</span></span>

<span data-ttu-id="38578-173">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="38578-173">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="38578-174">認證安全性服務提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="38578-174">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="38578-175">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="38578-175">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="38578-176">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="38578-176">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="38578-177">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="38578-177">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="38578-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="38578-178">-WhatIf</span></span>

<span data-ttu-id="38578-179">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="38578-179">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="38578-180">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="38578-180">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="38578-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="38578-181">CommonParameters</span></span>

<span data-ttu-id="38578-182">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="38578-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="38578-183">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="38578-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="38578-184">輸入</span><span class="sxs-lookup"><span data-stu-id="38578-184">INPUTS</span></span>

### <span data-ttu-id="38578-185">無</span><span class="sxs-lookup"><span data-stu-id="38578-185">None</span></span>

<span data-ttu-id="38578-186">您無法透過管道傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="38578-186">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="38578-187">輸出</span><span class="sxs-lookup"><span data-stu-id="38578-187">OUTPUTS</span></span>

### <span data-ttu-id="38578-188">無</span><span class="sxs-lookup"><span data-stu-id="38578-188">None</span></span>

## <span data-ttu-id="38578-189">注意</span><span class="sxs-lookup"><span data-stu-id="38578-189">NOTES</span></span>

<span data-ttu-id="38578-190">此 Cmdlet 會使用 **Win32_OperatingSystem** WMI 類別的 **Win32Shutdown** 方法。</span><span class="sxs-lookup"><span data-stu-id="38578-190">This cmdlet uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="38578-191">此方法需要針對用來重新開機電腦的使用者帳戶啟用 **SeShutdownPrivilege** 許可權。</span><span class="sxs-lookup"><span data-stu-id="38578-191">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

<span data-ttu-id="38578-192">在 PowerShell 7.1 中， `Stop-Computer` 已為 Linux 和 macOS 新增。</span><span class="sxs-lookup"><span data-stu-id="38578-192">In PowerShell 7.1, `Stop-Computer` was added for Linux and macOS.</span></span> <span data-ttu-id="38578-193">針對這些平臺，此 Cmdlet 會呼叫原生命令 `/sbin/shutdown` 。</span><span class="sxs-lookup"><span data-stu-id="38578-193">For these platorms, the cmdlet calls the native command `/sbin/shutdown`.</span></span>

## <span data-ttu-id="38578-194">相關連結</span><span class="sxs-lookup"><span data-stu-id="38578-194">RELATED LINKS</span></span>

[<span data-ttu-id="38578-195">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="38578-195">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="38578-196">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="38578-196">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="38578-197">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="38578-197">Test-Connection</span></span>](Test-Connection.md)

