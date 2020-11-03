---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 08/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/enable-wsmancredssp?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManCredSSP
ms.openlocfilehash: 3dd2aa9c1f35de80d86dde508aaa9a3c964dff05
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208688"
---
# <span data-ttu-id="33810-103">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="33810-103">Enable-WSManCredSSP</span></span>

## <span data-ttu-id="33810-104">概要</span><span class="sxs-lookup"><span data-stu-id="33810-104">SYNOPSIS</span></span>
<span data-ttu-id="33810-105">在電腦上啟用 (CredSSP) 驗證的認證安全性支援提供者。</span><span class="sxs-lookup"><span data-stu-id="33810-105">Enables Credential Security Support Provider (CredSSP) authentication on a computer.</span></span>

## <span data-ttu-id="33810-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="33810-106">SYNTAX</span></span>

### <span data-ttu-id="33810-107">全部</span><span class="sxs-lookup"><span data-stu-id="33810-107">All</span></span>

```
Enable-WSManCredSSP [[-DelegateComputer] <String[]>] [-Force] [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="33810-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="33810-108">DESCRIPTION</span></span>

<span data-ttu-id="33810-109">此 `Enable-WSManCredSSP` Cmdlet 會在用戶端或伺服器電腦上啟用 CredSSP 驗證。</span><span class="sxs-lookup"><span data-stu-id="33810-109">The `Enable-WSManCredSSP` cmdlet enables CredSSP authentication on a client or on a server computer.</span></span>
<span data-ttu-id="33810-110">使用 CredSSP 驗證時，會將使用者認證傳遞到遠端電腦進行驗證。</span><span class="sxs-lookup"><span data-stu-id="33810-110">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span> <span data-ttu-id="33810-111">此類型的驗證是針對會從另一個遠端工作階段建立遠端工作階段的命令所設計。</span><span class="sxs-lookup"><span data-stu-id="33810-111">This type of authentication is designed for commands that create a remote session from another remote session.</span></span> <span data-ttu-id="33810-112">例如，若您想在遠端電腦上執行背景工作，請使用此類型的驗證。</span><span class="sxs-lookup"><span data-stu-id="33810-112">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="33810-113">`Enable-WSManCredSSP` 可以在 **用戶端** 或 **伺服器** 上啟用 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="33810-113">`Enable-WSManCredSSP` can enable CredSSP on a **Client** or a **Server** .</span></span> <span data-ttu-id="33810-114">若要在用戶端上啟用 CredSSP，請在 **Role** 參數中指定 **client** 。</span><span class="sxs-lookup"><span data-stu-id="33810-114">To enable CredSSP on a client, specify **Client** in the **Role** parameter.</span></span> <span data-ttu-id="33810-115">用戶端會在伺服器驗證完成時，將明確的認證委派給伺服器。</span><span class="sxs-lookup"><span data-stu-id="33810-115">Clients delegate explicit credentials to a server when server authentication is achieved.</span></span> <span data-ttu-id="33810-116">若要在伺服器上啟用 CredSSP，請在 **Role** 參數中指定 **server** 。</span><span class="sxs-lookup"><span data-stu-id="33810-116">To enable CredSSP on a server, specify **Server** in the **Role** parameter.</span></span> <span data-ttu-id="33810-117">伺服器作為用戶端的委派。</span><span class="sxs-lookup"><span data-stu-id="33810-117">A server acts as a delegate for clients.</span></span> <span data-ttu-id="33810-118">如需詳細資訊，請參閱參數一節中的 **角色** 。</span><span class="sxs-lookup"><span data-stu-id="33810-118">For more details, see **Role** in the Parameters section.</span></span>

> [!CAUTION]
> <span data-ttu-id="33810-119">CredSSP 驗證會將使用者認證從本機電腦委派給遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="33810-119">CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="33810-120">此做法會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="33810-120">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="33810-121">若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="33810-121">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="33810-122">範例</span><span class="sxs-lookup"><span data-stu-id="33810-122">EXAMPLES</span></span>

### <span data-ttu-id="33810-123">範例 1︰委派用戶端認證</span><span class="sxs-lookup"><span data-stu-id="33810-123">Example 1: Delegate client credentials</span></span>

<span data-ttu-id="33810-124">此範例可讓您使用完整功能變數名稱將用戶端認證委派給電腦。</span><span class="sxs-lookup"><span data-stu-id="33810-124">This example allows the client credentials to be delegated to a computer by using the fully qualified domain name.</span></span>

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "Server02.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### <span data-ttu-id="33810-125">範例 2︰將用戶端認證委派給網域中的所有電腦</span><span class="sxs-lookup"><span data-stu-id="33810-125">Example 2: Delegate client credentials to all computers in a domain</span></span>

<span data-ttu-id="33810-126">此範例允許將用戶端認證委派給 **fabrikam.com** 網域中的所有電腦。</span><span class="sxs-lookup"><span data-stu-id="33810-126">This example allows the client credentials to be delegated to all the computers in the **fabrikam.com** domain.</span></span> <span data-ttu-id="33810-127">星號 (`*`) 萬用字元指定所有電腦。</span><span class="sxs-lookup"><span data-stu-id="33810-127">The asterisk (`*`) wildcard specifies all computers.</span></span>

> [!NOTE]
> <span data-ttu-id="33810-128">使用萬用字元搭配 **DelegateComputer** 參數可以在比所需更多的電腦上啟用 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="33810-128">Using wildcards with the **DelegateComputer** parameter can enable CredSSP on more computers than necessary.</span></span>

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "*.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### <span data-ttu-id="33810-129">範例 3︰將用戶端認證委派給多部電腦</span><span class="sxs-lookup"><span data-stu-id="33810-129">Example 3: Delegate client credentials to multiple computers</span></span>

<span data-ttu-id="33810-130">此範例允許將用戶端認證委派給多部電腦。</span><span class="sxs-lookup"><span data-stu-id="33810-130">This example allows the client credentials to be delegated to multiple computers.</span></span>

```powershell
$servers = "server02.fabrikam.com", "server03.fabrikam.com", "server04.fabrikam.com"
Enable-WSManCredSSP -Role "Client" -DelegateComputer $servers
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

<span data-ttu-id="33810-131">`$servers`變數包含伺服器名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="33810-131">The `$servers` variable contains a list of server names.</span></span> <span data-ttu-id="33810-132">`Enable-WSManCredSSP` 使用 **Role** 參數指定 **用戶端** 角色。</span><span class="sxs-lookup"><span data-stu-id="33810-132">`Enable-WSManCredSSP` uses the **Role** parameter to specify the **Client** role.</span></span> <span data-ttu-id="33810-133">**DelegateComputer** 會從變數中取得電腦名稱稱 `$servers` 。</span><span class="sxs-lookup"><span data-stu-id="33810-133">The **DelegateComputer** gets the computer names from the `$servers` variable.</span></span>

### <span data-ttu-id="33810-134">範例 4︰允許電腦做為委派對象</span><span class="sxs-lookup"><span data-stu-id="33810-134">Example 4: Allow a computer to act as a delegate</span></span>

<span data-ttu-id="33810-135">此範例可讓電腦做為另一部電腦的委派。</span><span class="sxs-lookup"><span data-stu-id="33810-135">This example allows a computer to act as a delegate for another.</span></span> <span data-ttu-id="33810-136">`Enable-WSManCredSSP`先前範例中所示的 Cmdlet 只會在用戶端上啟用 CredSSP 驗證，並指定可代表其採取動作的遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="33810-136">The `Enable-WSManCredSSP` cmdlet, shown in the earlier examples, only enables CredSSP authentication on the client, and specifies the remote computers that can act on its behalf.</span></span> <span data-ttu-id="33810-137">為了讓遠端電腦成為用戶端的委派，WSMan 的 **服務** 節點中的 CredSSP 專案必須設定為 true。</span><span class="sxs-lookup"><span data-stu-id="33810-137">In order for the remote computer to act as a delegate for the client, the CredSSP item in the **Service** node of WSMan must be set to true.</span></span> <span data-ttu-id="33810-138">此範例會將 WSMan 的 **服務** 節點中的 CredSSP 專案設定為 true。</span><span class="sxs-lookup"><span data-stu-id="33810-138">This example sets the CredSSP item in the **Service** node of WSMan to true.</span></span>

```powershell
Enable-WSManCredSSP -Role "Server"
```

### <span data-ttu-id="33810-139">範例 5︰使用 Set-Item 允許電腦做為委派對象</span><span class="sxs-lookup"><span data-stu-id="33810-139">Example 5: Allow a computer to act as a delegate by using Set-Item</span></span>

<span data-ttu-id="33810-140">此範例允許電腦做為另一部電腦的委派對象。</span><span class="sxs-lookup"><span data-stu-id="33810-140">This example allows a computer to act as a delegate for another computer.</span></span> <span data-ttu-id="33810-141">上述 `Enable-WSManCredSSP` 範例所示的命令只會在用戶端電腦上啟用 CredSSP 驗證，而且它們會指定可代表用戶端電腦採取行動的遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="33810-141">The `Enable-WSManCredSSP` commands, shown in the earlier examples, enable CredSSP authentication only on the client computer, and they specify the remote computers that can act on behalf of the client computer.</span></span> <span data-ttu-id="33810-142">若要讓遠端電腦可做為用戶端的委派對象，必須將 WSMan 提供者之 Service 目錄中的 CredSSP 項目設定為 True。</span><span class="sxs-lookup"><span data-stu-id="33810-142">For the remote computer to act as a delegate for the client computer, the CredSSP item in the Service directory of the WSMan provider must be set to true.</span></span>

```powershell
Connect-WSMan -ComputerName "server02"
Set-Item -Path "WSMan:\server02\service\auth\credSSP" -Value $True
```

<span data-ttu-id="33810-143">`Connect-WSMan` 建立與遠端電腦 server02 的連接。</span><span class="sxs-lookup"><span data-stu-id="33810-143">`Connect-WSMan` creates a connection to the remote computer, server02.</span></span> <span data-ttu-id="33810-144">`Set-Item` 使用 **Path** 參數來指定 **WSMan** 提供者的位置。</span><span class="sxs-lookup"><span data-stu-id="33810-144">`Set-Item` uses the **Path** parameter to specify the **WSMan** provider's location.</span></span> <span data-ttu-id="33810-145">**Value** 參數會將 **服務** 設定設定為 true。</span><span class="sxs-lookup"><span data-stu-id="33810-145">The **Value** parameter sets the **Service** setting to true.</span></span>

## <span data-ttu-id="33810-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="33810-146">PARAMETERS</span></span>

### <span data-ttu-id="33810-147">-DelegateComputer</span><span class="sxs-lookup"><span data-stu-id="33810-147">-DelegateComputer</span></span>

<span data-ttu-id="33810-148">指定要委派用戶端認證的伺服器。</span><span class="sxs-lookup"><span data-stu-id="33810-148">Specifies servers to which client credentials are delegated.</span></span> <span data-ttu-id="33810-149">最佳做法是使用完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="33810-149">The best practice is to use fully qualified domain names.</span></span>

<span data-ttu-id="33810-150">接受萬用字元，但可以在需要的電腦上啟用 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="33810-150">Wildcards are accepted, but can enable CredSSP on more computers than necessary.</span></span>

<span data-ttu-id="33810-151">如果 **Role** 參數是 **Client** ，您必須指定這個參數。</span><span class="sxs-lookup"><span data-stu-id="33810-151">If the **Role** parameter is **Client** , you must specify this parameter.</span></span> <span data-ttu-id="33810-152">如果 **Role** 是 **Server** ，請勿指定此參數。</span><span class="sxs-lookup"><span data-stu-id="33810-152">If **Role** is **Server** , don't specify this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="33810-153">-Force</span><span class="sxs-lookup"><span data-stu-id="33810-153">-Force</span></span>

<span data-ttu-id="33810-154">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="33810-154">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="33810-155">-Role</span><span class="sxs-lookup"><span data-stu-id="33810-155">-Role</span></span>

<span data-ttu-id="33810-156">指定是否要啟用 CredSSP 做為用戶端或伺服器。</span><span class="sxs-lookup"><span data-stu-id="33810-156">Specifies whether to enable CredSSP as a client or as a server.</span></span> <span data-ttu-id="33810-157">此參數可接受的值為： **用戶端** 和 **伺服器** 。</span><span class="sxs-lookup"><span data-stu-id="33810-157">The acceptable values for this parameter are: **Client** and **Server** .</span></span>

<span data-ttu-id="33810-158">如果您指定 **用戶端** ，則會執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="33810-158">If you specify **Client** , the following actions are performed.</span></span> <span data-ttu-id="33810-159">這些設定可讓用戶端將明確宣告的認證委派給伺服器 (當達成使用伺服器驗證時)。</span><span class="sxs-lookup"><span data-stu-id="33810-159">These settings allow the client to delegate explicit credentials to a server when server authentication is achieved.</span></span>

- <span data-ttu-id="33810-160">啟用用戶端上的 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="33810-160">Enables CredSSP on the client.</span></span>
- <span data-ttu-id="33810-161">將 WS-Management 設定設定 `\<localhost|computername\>\Client\Auth\CredSSP` 為 true。</span><span class="sxs-lookup"><span data-stu-id="33810-161">Sets the WS-Management setting `\<localhost|computername\>\Client\Auth\CredSSP` to true.</span></span>
- <span data-ttu-id="33810-162">將 Windows CredSSP 原則 **AllowFreshCredentials** 設定為用戶端上的 **WSMan/委派** 。</span><span class="sxs-lookup"><span data-stu-id="33810-162">Sets the Windows CredSSP policy **AllowFreshCredentials** to **WSMan/Delegate** on the client.</span></span>

<span data-ttu-id="33810-163">如果您指定 **Server** ，則會執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="33810-163">If you specify **Server** , the following actions are performed.</span></span> <span data-ttu-id="33810-164">此原則設定可讓伺服器做為用戶端的委派對象。</span><span class="sxs-lookup"><span data-stu-id="33810-164">This policy setting allows the server to act as a delegate for clients.</span></span>

- <span data-ttu-id="33810-165">啟用伺服器上的 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="33810-165">Enables CredSSP on the server.</span></span>
- <span data-ttu-id="33810-166">將 WS-Management 設定設定 `\<localhost|computername\>\Service\Auth\CredSSP` 為 true。</span><span class="sxs-lookup"><span data-stu-id="33810-166">Sets the WS-Management setting `\<localhost|computername\>\Service\Auth\CredSSP` to true.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="33810-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="33810-167">CommonParameters</span></span>

<span data-ttu-id="33810-168">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="33810-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="33810-169">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="33810-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="33810-170">輸入</span><span class="sxs-lookup"><span data-stu-id="33810-170">INPUTS</span></span>

### <span data-ttu-id="33810-171">無</span><span class="sxs-lookup"><span data-stu-id="33810-171">None</span></span>

<span data-ttu-id="33810-172">此 Cmdlet 不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="33810-172">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="33810-173">輸出</span><span class="sxs-lookup"><span data-stu-id="33810-173">OUTPUTS</span></span>

### <span data-ttu-id="33810-174">System.Xml.XmlElement</span><span class="sxs-lookup"><span data-stu-id="33810-174">System.Xml.XmlElement</span></span>

<span data-ttu-id="33810-175">如果已成功啟用 CredSSP 驗證，此 Cmdlet 會產生 **XMLElement** 物件。</span><span class="sxs-lookup"><span data-stu-id="33810-175">If CredSSP authentication is successfully enabled, this cmdlet generates an **XMLElement** object.</span></span>

## <span data-ttu-id="33810-176">注意</span><span class="sxs-lookup"><span data-stu-id="33810-176">NOTES</span></span>

<span data-ttu-id="33810-177">若要停用 CredSSP 驗證，請使用 `Disable-WSManCredSSP` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="33810-177">To disable CredSSP authentication, use the `Disable-WSManCredSSP` cmdlet.</span></span>

## <span data-ttu-id="33810-178">相關連結</span><span class="sxs-lookup"><span data-stu-id="33810-178">RELATED LINKS</span></span>

[<span data-ttu-id="33810-179">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="33810-179">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="33810-180">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="33810-180">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="33810-181">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="33810-181">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="33810-182">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="33810-182">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="33810-183">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="33810-183">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="33810-184">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="33810-184">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="33810-185">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="33810-185">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="33810-186">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="33810-186">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="33810-187">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="33810-187">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="33810-188">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="33810-188">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="33810-189">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="33810-189">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="33810-190">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="33810-190">Test-WSMan</span></span>](Test-WSMan.md)
