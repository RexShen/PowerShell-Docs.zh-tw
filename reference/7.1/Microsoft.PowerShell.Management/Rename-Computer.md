---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: 1c8cde77d16452c9488ce3af62e8b5f761213c80
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202048"
---
# <span data-ttu-id="f43f2-103">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="f43f2-103">Rename-Computer</span></span>

## <span data-ttu-id="f43f2-104">概要</span><span class="sxs-lookup"><span data-stu-id="f43f2-104">SYNOPSIS</span></span>
<span data-ttu-id="f43f2-105">重新命名電腦。</span><span class="sxs-lookup"><span data-stu-id="f43f2-105">Renames a computer.</span></span>

## <span data-ttu-id="f43f2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f43f2-106">SYNTAX</span></span>

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f43f2-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f43f2-107">DESCRIPTION</span></span>

<span data-ttu-id="f43f2-108">Cmdlet 會重新 `Rename-Computer` 命名本機電腦或遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="f43f2-108">The `Rename-Computer` cmdlet renames the local computer or a remote computer.</span></span>
<span data-ttu-id="f43f2-109">它會在每個命令中重新命名一部電腦。</span><span class="sxs-lookup"><span data-stu-id="f43f2-109">It renames one computer in each command.</span></span>

<span data-ttu-id="f43f2-110">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="f43f2-110">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="f43f2-111">範例</span><span class="sxs-lookup"><span data-stu-id="f43f2-111">EXAMPLES</span></span>

### <span data-ttu-id="f43f2-112">範例1：重新命名本機電腦</span><span class="sxs-lookup"><span data-stu-id="f43f2-112">Example 1: Rename the local computer</span></span>

<span data-ttu-id="f43f2-113">此命令會將本機電腦重新命名為 `Server044` ，然後重新開機，以使變更生效。</span><span class="sxs-lookup"><span data-stu-id="f43f2-113">This command renames the local computer to `Server044` and then restarts it to make the change effective.</span></span>

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### <span data-ttu-id="f43f2-114">範例2：重新命名遠端電腦</span><span class="sxs-lookup"><span data-stu-id="f43f2-114">Example 2: Rename a remote computer</span></span>

<span data-ttu-id="f43f2-115">此命令會將 `Srv01` 電腦重新命名為 `Server001` 。</span><span class="sxs-lookup"><span data-stu-id="f43f2-115">This command renames the `Srv01` computer to `Server001`.</span></span> <span data-ttu-id="f43f2-116">電腦未重新開機。</span><span class="sxs-lookup"><span data-stu-id="f43f2-116">The computer is not restarted.</span></span>

<span data-ttu-id="f43f2-117">**DomainCredential** 參數會指定有權重新命名網域中電腦的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="f43f2-117">The **DomainCredential** parameter specifies the credentials of a user who has permission to rename computers in the domain.</span></span>

<span data-ttu-id="f43f2-118">**Force** 參數會抑制確認提示。</span><span class="sxs-lookup"><span data-stu-id="f43f2-118">The **Force** parameter suppresses the confirmation prompt.</span></span>

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## <span data-ttu-id="f43f2-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f43f2-119">PARAMETERS</span></span>

### <span data-ttu-id="f43f2-120">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f43f2-120">-ComputerName</span></span>

<span data-ttu-id="f43f2-121">重新命名指定的遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="f43f2-121">Renames the specified remote computer.</span></span>
<span data-ttu-id="f43f2-122">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="f43f2-122">The default is the local computer.</span></span>

<span data-ttu-id="f43f2-123">輸入遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="f43f2-123">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="f43f2-124">若要指定本機電腦，請輸入電腦名稱稱、點 (`.`) 或 `localhost` 。</span><span class="sxs-lookup"><span data-stu-id="f43f2-124">To specify the local computer, type the computer name, a dot (`.`), or `localhost`.</span></span>

<span data-ttu-id="f43f2-125">此參數不依賴 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="f43f2-125">This parameter does not rely on PowerShell remoting.</span></span>
<span data-ttu-id="f43f2-126">**ComputerName** `Rename-Computer` 即使您的電腦未設定為執行遠端命令，您也可以使用 ComputerName 參數。</span><span class="sxs-lookup"><span data-stu-id="f43f2-126">You can use the **ComputerName** parameter of `Rename-Computer` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local Computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f43f2-127">-DomainCredential</span><span class="sxs-lookup"><span data-stu-id="f43f2-127">-DomainCredential</span></span>

<span data-ttu-id="f43f2-128">指定具有連線網域權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="f43f2-128">Specifies a user account that has permission to connect to the domain.</span></span>
<span data-ttu-id="f43f2-129">需要明確認證才能重新命名已加入網域的電腦。</span><span class="sxs-lookup"><span data-stu-id="f43f2-129">Explicit credentials are required to rename a computer that is joined to a domain.</span></span>

<span data-ttu-id="f43f2-130">輸入使用者名稱（例如 `User01` 或）， `Domain01\User01` 或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="f43f2-130">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="f43f2-131">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="f43f2-131">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="f43f2-132">若要指定具有 **ComputerName** 參數指定電腦連線權限的使用者帳戶，請使用 **LocalCredential** 參數。</span><span class="sxs-lookup"><span data-stu-id="f43f2-132">To specify a user account that has permission to connect to the computer that is specified by the **ComputerName** parameter, use the **LocalCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f43f2-133">-Force</span><span class="sxs-lookup"><span data-stu-id="f43f2-133">-Force</span></span>

<span data-ttu-id="f43f2-134">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="f43f2-134">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="f43f2-135">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="f43f2-135">-LocalCredential</span></span>

<span data-ttu-id="f43f2-136">指定具有連線到 **ComputerName** 參數所指定電腦之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="f43f2-136">Specifies a user account that has permission to connect to the computer specified by the **ComputerName** parameter.</span></span> <span data-ttu-id="f43f2-137">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="f43f2-137">The default is the current user.</span></span>

<span data-ttu-id="f43f2-138">輸入使用者名稱（例如 `User01` 或）， `Domain01\User01` 或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="f43f2-138">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="f43f2-139">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="f43f2-139">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="f43f2-140">若要指定具有連線網域之權限的使用者帳戶，請使用 **DomainCredential** 參數。</span><span class="sxs-lookup"><span data-stu-id="f43f2-140">To specify a user account that has permission to connect to the domain, use the **DomainCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current User
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f43f2-141">-NewName</span><span class="sxs-lookup"><span data-stu-id="f43f2-141">-NewName</span></span>

<span data-ttu-id="f43f2-142">指定電腦的新名稱。</span><span class="sxs-lookup"><span data-stu-id="f43f2-142">Specifies a new name for the computer.</span></span>
<span data-ttu-id="f43f2-143">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="f43f2-143">This parameter is required.</span></span>

<span data-ttu-id="f43f2-144">標準名稱可包含字母 (`a-z`) 、 (`A-Z`) 、數位 (`0-9`) 和連字號 () `-` ，但 () 不能有空格或句號 `.` 。</span><span class="sxs-lookup"><span data-stu-id="f43f2-144">Standard names may contain letters (`a-z`), (`A-Z`), numbers (`0-9`), and hyphens (`-`), but no spaces or periods (`.`).</span></span> <span data-ttu-id="f43f2-145">名稱不能完全由數位組成，而且長度可能不能超過63個字元</span><span class="sxs-lookup"><span data-stu-id="f43f2-145">The name may not consist entirely of digits, and may not be longer than 63 characters</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f43f2-146">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f43f2-146">-PassThru</span></span>

<span data-ttu-id="f43f2-147">傳回命令的結果。</span><span class="sxs-lookup"><span data-stu-id="f43f2-147">Returns the results of the command.</span></span>
<span data-ttu-id="f43f2-148">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f43f2-148">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f43f2-149">-Restart</span><span class="sxs-lookup"><span data-stu-id="f43f2-149">-Restart</span></span>

<span data-ttu-id="f43f2-150">指出此 Cmdlet 會重新開機已重新命名的電腦。</span><span class="sxs-lookup"><span data-stu-id="f43f2-150">Indicates that this cmdlet restarts the computer that was renamed.</span></span>
<span data-ttu-id="f43f2-151">通常必須重新啟動才能使變更生效。</span><span class="sxs-lookup"><span data-stu-id="f43f2-151">A restart is often required to make the change effective.</span></span>

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

### <span data-ttu-id="f43f2-152">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="f43f2-152">-WsmanAuthentication</span></span>

<span data-ttu-id="f43f2-153">指定當此 Cmdlet 使用 WSMan 通訊協定時，用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="f43f2-153">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="f43f2-154">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="f43f2-154">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f43f2-155">**基本**</span><span class="sxs-lookup"><span data-stu-id="f43f2-155">**Basic**</span></span>
- <span data-ttu-id="f43f2-156">**CredSSP**</span><span class="sxs-lookup"><span data-stu-id="f43f2-156">**CredSSP**</span></span>
- <span data-ttu-id="f43f2-157">**預設值**</span><span class="sxs-lookup"><span data-stu-id="f43f2-157">**Default**</span></span>
- <span data-ttu-id="f43f2-158">**Digest**</span><span class="sxs-lookup"><span data-stu-id="f43f2-158">**Digest**</span></span>
- <span data-ttu-id="f43f2-159">**Kerberos**</span><span class="sxs-lookup"><span data-stu-id="f43f2-159">**Kerberos**</span></span>
- <span data-ttu-id="f43f2-160">**洽談**</span><span class="sxs-lookup"><span data-stu-id="f43f2-160">**Negotiate**</span></span>

<span data-ttu-id="f43f2-161">預設值為 **Default** 。</span><span class="sxs-lookup"><span data-stu-id="f43f2-161">The default value is **Default** .</span></span>

<span data-ttu-id="f43f2-162">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="f43f2-162">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="f43f2-163">認證安全性服務提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="f43f2-163">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
> <span data-ttu-id="f43f2-164">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="f43f2-164">This mechanism increases the security risk of the remote operation.</span></span>
> <span data-ttu-id="f43f2-165">如果遠端電腦遭到入侵，傳遞給它的認證可以用來控制 > 網路會話。</span><span class="sxs-lookup"><span data-stu-id="f43f2-165">If the remote computer is compromised, the credentials that are passed to it can be used to control > the network session.</span></span>

<span data-ttu-id="f43f2-166">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="f43f2-166">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f43f2-167">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f43f2-167">-Confirm</span></span>

<span data-ttu-id="f43f2-168">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f43f2-168">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f43f2-169">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f43f2-169">-WhatIf</span></span>

<span data-ttu-id="f43f2-170">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f43f2-170">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f43f2-171">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="f43f2-171">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f43f2-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f43f2-172">CommonParameters</span></span>

<span data-ttu-id="f43f2-173">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f43f2-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f43f2-174">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="f43f2-174">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f43f2-175">輸入</span><span class="sxs-lookup"><span data-stu-id="f43f2-175">INPUTS</span></span>

### <span data-ttu-id="f43f2-176">無</span><span class="sxs-lookup"><span data-stu-id="f43f2-176">None</span></span>

<span data-ttu-id="f43f2-177">此 Cmdlet 沒有透過值輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="f43f2-177">This cmdlet does not have parameters that take input by value.</span></span>
<span data-ttu-id="f43f2-178">不過，您可以使用管線將物件之 **ComputerName** 和 **NewName** 屬性的值傳送到此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f43f2-178">However, you can pipe the values of the **ComputerName** and **NewName** properties of objects to this cmdlet.</span></span>

## <span data-ttu-id="f43f2-179">輸出</span><span class="sxs-lookup"><span data-stu-id="f43f2-179">OUTPUTS</span></span>

### <span data-ttu-id="f43f2-180">Microsoft.PowerShell.Commands.ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="f43f2-180">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="f43f2-181">如果您指定 **PassThru** 參數，此 Cmdlet 會傳回 **ComputerChangeInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="f43f2-181">This cmdlet returns a **ComputerChangeInfo** object, if you specify the **PassThru** parameter.</span></span>
<span data-ttu-id="f43f2-182">否則，它不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f43f2-182">Otherwise, it does not return any output.</span></span>

## <span data-ttu-id="f43f2-183">注意</span><span class="sxs-lookup"><span data-stu-id="f43f2-183">NOTES</span></span>

## <span data-ttu-id="f43f2-184">相關連結</span><span class="sxs-lookup"><span data-stu-id="f43f2-184">RELATED LINKS</span></span>

[<span data-ttu-id="f43f2-185">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="f43f2-185">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="f43f2-186">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="f43f2-186">Stop-Computer</span></span>](Stop-Computer.md)

