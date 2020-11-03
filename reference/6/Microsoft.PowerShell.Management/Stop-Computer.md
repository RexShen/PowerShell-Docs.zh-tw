---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: e7732c1eb243c0a4737c3f08a413fd20bbf2bf38
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205592"
---
# <span data-ttu-id="d87a6-103">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="d87a6-103">Stop-Computer</span></span>

## <span data-ttu-id="d87a6-104">概要</span><span class="sxs-lookup"><span data-stu-id="d87a6-104">SYNOPSIS</span></span>
<span data-ttu-id="d87a6-105">將本機電腦和遠端電腦停止 (關機)。</span><span class="sxs-lookup"><span data-stu-id="d87a6-105">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="d87a6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d87a6-106">SYNTAX</span></span>

### <span data-ttu-id="d87a6-107">全部</span><span class="sxs-lookup"><span data-stu-id="d87a6-107">All</span></span>

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d87a6-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d87a6-108">DESCRIPTION</span></span>

<span data-ttu-id="d87a6-109">此 `Stop-Computer` Cmdlet 會將本機電腦和遠端電腦關機。</span><span class="sxs-lookup"><span data-stu-id="d87a6-109">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="d87a6-110">您可以使用的參數 `Stop-Computer` 來指定驗證等級和替代認證，以及強制立即關機。</span><span class="sxs-lookup"><span data-stu-id="d87a6-110">You can use the parameters of `Stop-Computer` to specify the authentication levels and alternate credentials, and to force an immediate shut down.</span></span>

## <span data-ttu-id="d87a6-111">範例</span><span class="sxs-lookup"><span data-stu-id="d87a6-111">EXAMPLES</span></span>

### <span data-ttu-id="d87a6-112">範例1：關閉本機電腦</span><span class="sxs-lookup"><span data-stu-id="d87a6-112">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="d87a6-113">此範例會將本機電腦關機。</span><span class="sxs-lookup"><span data-stu-id="d87a6-113">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="d87a6-114">範例2：關閉兩部遠端電腦和本機電腦</span><span class="sxs-lookup"><span data-stu-id="d87a6-114">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="d87a6-115">此範例會停止兩部遠端電腦和本機電腦。</span><span class="sxs-lookup"><span data-stu-id="d87a6-115">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="d87a6-116">`Stop-Computer` 使用 **ComputerName** 參數來指定兩部遠端電腦和本機電腦。</span><span class="sxs-lookup"><span data-stu-id="d87a6-116">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="d87a6-117">每部電腦都已關閉。</span><span class="sxs-lookup"><span data-stu-id="d87a6-117">Each computer is shut down.</span></span>

### <span data-ttu-id="d87a6-118">範例3：將遠端電腦關閉為背景工作</span><span class="sxs-lookup"><span data-stu-id="d87a6-118">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="d87a6-119">在此範例中，會 `Stop-Computer` 在兩部遠端電腦上以背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="d87a6-119">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

<span data-ttu-id="d87a6-120">背景運算子會 `&` `Stop-Computer` 以背景工作的方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="d87a6-120">The background operator `&` runs the `Stop-Computer` command as a background job.</span></span> <span data-ttu-id="d87a6-121">如需詳細資訊，請參閱 [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-)。</span><span class="sxs-lookup"><span data-stu-id="d87a6-121">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

<span data-ttu-id="d87a6-122">`Stop-Computer` 使用 **ComputerName** 參數來指定兩部遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="d87a6-122">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="d87a6-123">`&`背景運算子會以背景工作的方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="d87a6-123">The `&` background operator runs the command as a background job.</span></span> <span data-ttu-id="d87a6-124">工作物件會儲存在變數中 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="d87a6-124">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="d87a6-125">變數中的工作物件 `$j` 會向下傳送至管線 `Receive-Job` ，以取得工作結果。</span><span class="sxs-lookup"><span data-stu-id="d87a6-125">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="d87a6-126">物件會儲存在變數中 `$results` 。</span><span class="sxs-lookup"><span data-stu-id="d87a6-126">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="d87a6-127">此 `$results` 變數會在 PowerShell 主控台中顯示工作資訊。</span><span class="sxs-lookup"><span data-stu-id="d87a6-127">The `$results` variable displays the job information in the PowerShell console.</span></span>

### <span data-ttu-id="d87a6-128">範例4：將遠端電腦關機</span><span class="sxs-lookup"><span data-stu-id="d87a6-128">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="d87a6-129">此範例會使用指定的驗證來關閉遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="d87a6-129">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

<span data-ttu-id="d87a6-130">`Stop-Computer` 使用 **ComputerName** 參數來指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="d87a6-130">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="d87a6-131">**WsmanAuthentication** 參數會指定使用 Kerberos 來建立遠端連線。</span><span class="sxs-lookup"><span data-stu-id="d87a6-131">The **WsmanAuthentication** parameter specifies to use Kerberos to establish a remote connection.</span></span>

### <span data-ttu-id="d87a6-132">範例5：關閉網域中的電腦</span><span class="sxs-lookup"><span data-stu-id="d87a6-132">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="d87a6-133">在此範例中，命令會強制立即關閉指定網域中的所有電腦。</span><span class="sxs-lookup"><span data-stu-id="d87a6-133">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

<span data-ttu-id="d87a6-134">`Get-Content` 使用 **Path** 參數，以網域電腦清單取得目前目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="d87a6-134">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="d87a6-135">物件會儲存在變數中 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="d87a6-135">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="d87a6-136">`Get-Credential` 使用 **Credential** 參數來指定網域系統管理員的認證。</span><span class="sxs-lookup"><span data-stu-id="d87a6-136">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="d87a6-137">認證會儲存在變數中 `$c` 。</span><span class="sxs-lookup"><span data-stu-id="d87a6-137">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="d87a6-138">`Stop-Computer` 以變數中 **電腦的電腦** 清單，關閉指定的電腦 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="d87a6-138">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="d87a6-139">**Force** 參數會強制立即關機。</span><span class="sxs-lookup"><span data-stu-id="d87a6-139">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="d87a6-140">**Credential** 參數會提交儲存在變數中的認證 `$c` 。</span><span class="sxs-lookup"><span data-stu-id="d87a6-140">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="d87a6-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d87a6-141">PARAMETERS</span></span>

### <span data-ttu-id="d87a6-142">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="d87a6-142">-ComputerName</span></span>

<span data-ttu-id="d87a6-143">指定要停止的電腦。</span><span class="sxs-lookup"><span data-stu-id="d87a6-143">Specifies the computers to stop.</span></span> <span data-ttu-id="d87a6-144">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="d87a6-144">The default is the local computer.</span></span>

<span data-ttu-id="d87a6-145">請輸入一或多部電腦的 NETBIOS 名稱、IP 位址或完整網域名稱 (以逗號分隔的清單方式)。</span><span class="sxs-lookup"><span data-stu-id="d87a6-145">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="d87a6-146">若要指定本機電腦，請輸入電腦名稱稱或 localhost。</span><span class="sxs-lookup"><span data-stu-id="d87a6-146">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="d87a6-147">此參數不依賴 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="d87a6-147">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="d87a6-148">即使您的電腦未設定為執行遠端命令，您也可以使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="d87a6-148">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

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

### <span data-ttu-id="d87a6-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d87a6-149">-Confirm</span></span>

<span data-ttu-id="d87a6-150">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="d87a6-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d87a6-151">-Credential</span><span class="sxs-lookup"><span data-stu-id="d87a6-151">-Credential</span></span>

<span data-ttu-id="d87a6-152">指定具有執行此動作之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d87a6-152">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="d87a6-153">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="d87a6-153">The default is the current user.</span></span>

<span data-ttu-id="d87a6-154">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="d87a6-154">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="d87a6-155">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="d87a6-155">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="d87a6-156">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="d87a6-156">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="d87a6-157">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="d87a6-157">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="d87a6-158">-Force</span><span class="sxs-lookup"><span data-stu-id="d87a6-158">-Force</span></span>

<span data-ttu-id="d87a6-159">強制立即關閉電腦。</span><span class="sxs-lookup"><span data-stu-id="d87a6-159">Forces an immediate shut down of the computer.</span></span>

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

### <span data-ttu-id="d87a6-160">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="d87a6-160">-WsmanAuthentication</span></span>

<span data-ttu-id="d87a6-161">指定當此 Cmdlet 使用 WSMan 通訊協定時，用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="d87a6-161">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="d87a6-162">預設值為 **Default** 。</span><span class="sxs-lookup"><span data-stu-id="d87a6-162">The default value is **Default** .</span></span>

<span data-ttu-id="d87a6-163">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="d87a6-163">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d87a6-164">基本</span><span class="sxs-lookup"><span data-stu-id="d87a6-164">Basic</span></span>
- <span data-ttu-id="d87a6-165">CredSSP</span><span class="sxs-lookup"><span data-stu-id="d87a6-165">CredSSP</span></span>
- <span data-ttu-id="d87a6-166">預設</span><span class="sxs-lookup"><span data-stu-id="d87a6-166">Default</span></span>
- <span data-ttu-id="d87a6-167">Digest</span><span class="sxs-lookup"><span data-stu-id="d87a6-167">Digest</span></span>
- <span data-ttu-id="d87a6-168">Kerberos</span><span class="sxs-lookup"><span data-stu-id="d87a6-168">Kerberos</span></span>
- <span data-ttu-id="d87a6-169">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="d87a6-169">Negotiate.</span></span>

<span data-ttu-id="d87a6-170">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="d87a6-170">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="d87a6-171">認證安全性服務提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="d87a6-171">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="d87a6-172">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="d87a6-172">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="d87a6-173">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="d87a6-173">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="d87a6-174">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="d87a6-174">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="d87a6-175">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d87a6-175">-WhatIf</span></span>

<span data-ttu-id="d87a6-176">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="d87a6-176">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d87a6-177">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d87a6-177">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="d87a6-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d87a6-178">CommonParameters</span></span>

<span data-ttu-id="d87a6-179">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d87a6-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d87a6-180">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d87a6-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d87a6-181">輸入</span><span class="sxs-lookup"><span data-stu-id="d87a6-181">INPUTS</span></span>

### <span data-ttu-id="d87a6-182">無</span><span class="sxs-lookup"><span data-stu-id="d87a6-182">None</span></span>

<span data-ttu-id="d87a6-183">您無法透過管道傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d87a6-183">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d87a6-184">輸出</span><span class="sxs-lookup"><span data-stu-id="d87a6-184">OUTPUTS</span></span>

### <span data-ttu-id="d87a6-185">無</span><span class="sxs-lookup"><span data-stu-id="d87a6-185">None</span></span>

## <span data-ttu-id="d87a6-186">注意</span><span class="sxs-lookup"><span data-stu-id="d87a6-186">NOTES</span></span>

<span data-ttu-id="d87a6-187">此 Cmdlet 僅適用于 Windows，並使用 **Win32_OperatingSystem** WMI 類別的 **Win32Shutdown** 方法。</span><span class="sxs-lookup"><span data-stu-id="d87a6-187">This cmdlet only works on Windows and uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="d87a6-188">此方法需要針對用來重新開機電腦的使用者帳戶啟用 **SeShutdownPrivilege** 許可權。</span><span class="sxs-lookup"><span data-stu-id="d87a6-188">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

## <span data-ttu-id="d87a6-189">相關連結</span><span class="sxs-lookup"><span data-stu-id="d87a6-189">RELATED LINKS</span></span>

[<span data-ttu-id="d87a6-190">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="d87a6-190">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="d87a6-191">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="d87a6-191">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="d87a6-192">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="d87a6-192">Test-Connection</span></span>](Test-Connection.md)
