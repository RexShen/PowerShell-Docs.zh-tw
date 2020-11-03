---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSession
ms.openlocfilehash: 04d0b272995538e88fff2725eb8806c66d217460
ms.sourcegitcommit: 9a53e53e7a3ef9ac0a212c61005efff9e9902452
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "93206092"
---
# <span data-ttu-id="12cbd-103">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="12cbd-103">New-CimSession</span></span>

## <span data-ttu-id="12cbd-104">概要</span><span class="sxs-lookup"><span data-stu-id="12cbd-104">SYNOPSIS</span></span>

<span data-ttu-id="12cbd-105">建立 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="12cbd-105">Creates a CIM session.</span></span>

## <span data-ttu-id="12cbd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="12cbd-106">SYNTAX</span></span>

### <span data-ttu-id="12cbd-107">CredentialParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="12cbd-107">CredentialParameterSet (Default)</span></span>

```
New-CimSession [-Authentication <PasswordAuthenticationMechanism>] [[-Credential] <PSCredential>]
 [[-ComputerName] <String[]>] [-Name <String>] [-OperationTimeoutSec <UInt32>] [-SkipTestConnection]
 [-Port <UInt32>] [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

### <span data-ttu-id="12cbd-108">CertificatePrameterSet</span><span class="sxs-lookup"><span data-stu-id="12cbd-108">CertificatePrameterSet</span></span>

```
New-CimSession [-CertificateThumbprint <String>] [[-ComputerName] <String[]>] [-Name <String>]
 [-OperationTimeoutSec <UInt32>] [-SkipTestConnection] [-Port <UInt32>]
 [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

## <span data-ttu-id="12cbd-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="12cbd-109">DESCRIPTION</span></span>

<span data-ttu-id="12cbd-110">此 `New-CimSession` Cmdlet 會建立 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="12cbd-110">The `New-CimSession` cmdlet creates a CIM session.</span></span> <span data-ttu-id="12cbd-111">CIM 會話是代表連接到本機電腦或遠端電腦的用戶端物件。</span><span class="sxs-lookup"><span data-stu-id="12cbd-111">A CIM session is a client-side object representing a connection to a local computer or a remote computer.</span></span> <span data-ttu-id="12cbd-112">CIM 會話包含連接的相關資訊，例如 **ComputerName** 、使用的通訊協定或不同的識別碼。</span><span class="sxs-lookup"><span data-stu-id="12cbd-112">The CIM session contains information about the connection, such as **ComputerName** , the protocol used, or various identifiers.</span></span>

<span data-ttu-id="12cbd-113">此 Cmdlet 會傳回可供所有其他 CIM Cmdlet 使用的 CIM 會話物件。</span><span class="sxs-lookup"><span data-stu-id="12cbd-113">This cmdlet returns a CIM session object that can be used by all other CIM cmdlets.</span></span>

## <span data-ttu-id="12cbd-114">範例</span><span class="sxs-lookup"><span data-stu-id="12cbd-114">EXAMPLES</span></span>

### <span data-ttu-id="12cbd-115">範例1：使用預設選項建立 CIM 會話</span><span class="sxs-lookup"><span data-stu-id="12cbd-115">Example 1: Create a CIM session with default options</span></span>

<span data-ttu-id="12cbd-116">此範例會使用預設選項建立本機 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="12cbd-116">This example creates a local CIM session with default options.</span></span> <span data-ttu-id="12cbd-117">如果未指定 **ComputerName** ，則會在 `New-CimSession` 本機電腦上建立 DCOM 會話。</span><span class="sxs-lookup"><span data-stu-id="12cbd-117">If **ComputerName** is not specified, `New-CimSession` creates a DCOM session to the local computer.</span></span>

```powershell
New-CimSession
```

### <span data-ttu-id="12cbd-118">範例2：建立特定電腦的 CIM 會話</span><span class="sxs-lookup"><span data-stu-id="12cbd-118">Example 2: Create a CIM session to a specific computer</span></span>

<span data-ttu-id="12cbd-119">此範例會建立 **ComputerName** 所指定電腦的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="12cbd-119">This example creates a CIM session to the computer specified by **ComputerName** .</span></span>
<span data-ttu-id="12cbd-120">依預設， `New-CimSession` 會在指定 **ComputerName** 時建立 WSMan 會話。</span><span class="sxs-lookup"><span data-stu-id="12cbd-120">By default, `New-CimSession` creates a WSMan session when **ComputerName** is specified.</span></span>

```powershell
New-CimSession -ComputerName Server01
```

### <span data-ttu-id="12cbd-121">範例3：建立多部電腦的 CIM 會話</span><span class="sxs-lookup"><span data-stu-id="12cbd-121">Example 3: Create a CIM session to multiple computers</span></span>

<span data-ttu-id="12cbd-122">此範例會在以逗號分隔的清單中，為 **ComputerName** 指定的每一部電腦建立 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="12cbd-122">This example creates a CIM session to each of the computers specified by **ComputerName** , in the comma separated list.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02,Server03
```

### <span data-ttu-id="12cbd-123">範例4：建立具有易記名稱的 CIM 會話</span><span class="sxs-lookup"><span data-stu-id="12cbd-123">Example 4: Create a CIM session with a friendly name</span></span>

<span data-ttu-id="12cbd-124">此範例會在以逗號分隔的清單中，為 **ComputerName** 指定的每一部電腦建立遠端 CIM 會話，並藉由指定 **名稱** 將易記名稱指派給新的會話。</span><span class="sxs-lookup"><span data-stu-id="12cbd-124">This example creates a remote CIM session to each of the computers specified by **ComputerName** , in the comma separated list, and assigns a friendly name to the new sessions, by specifying **Name** .</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02 -Name FileServers
Get-CimSession -Name File*
```

<span data-ttu-id="12cbd-125">您可以使用 CIM 會話的易記名稱，參考其他 CIM Cmdlet 中的會話，例如， [CimSession](Get-CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="12cbd-125">You can use the friendly name of a CIM session to refer to the session in other CIM cmdlets, for example, [Get-CimSession](Get-CimSession.md).</span></span>

### <span data-ttu-id="12cbd-126">範例5：使用 PSCredential 物件建立電腦的 CIM 會話</span><span class="sxs-lookup"><span data-stu-id="12cbd-126">Example 5: Create a CIM session to a computer using a PSCredential object</span></span>

<span data-ttu-id="12cbd-127">此範例會使用 **Credential** 指定的 **PSCredential** 物件，以及 **驗證** 所指定的驗證類型，建立與 **ComputerName** 所指定電腦的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="12cbd-127">This example creates a CIM session to the computer specified by **ComputerName** , using the **PSCredential** object specified by **Credential** , and the authentication type specified by **Authentication** .</span></span>

```powershell
New-CimSession -ComputerName Server01 -Credential $cred -Authentication Negotiate
```

<span data-ttu-id="12cbd-128">您可以使用 Cmdlet 來建立 **PSCredential** 物件 [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) 。</span><span class="sxs-lookup"><span data-stu-id="12cbd-128">You can create a **PSCredential** object using the [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet.</span></span>

### <span data-ttu-id="12cbd-129">範例6：使用特定埠建立電腦的 CIM 會話</span><span class="sxs-lookup"><span data-stu-id="12cbd-129">Example 6: Create a CIM session to a computer using a specific port</span></span>

<span data-ttu-id="12cbd-130">此範例會使用 **埠** 指定的 TCP 通訊埠，建立電腦 **名稱** 所指定之電腦的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="12cbd-130">This example creates a CIM session to the computer specified by **ComputerName** using the TCP port specified by **Port** .</span></span>

```powershell
New-CimSession -ComputerName Server01 -Port 1234
```

### <span data-ttu-id="12cbd-131">範例7：使用 DCOM 建立 CIM 會話</span><span class="sxs-lookup"><span data-stu-id="12cbd-131">Example 7: Create a CIM session using DCOM</span></span>

<span data-ttu-id="12cbd-132">此範例會使用分散式 COM (DCOM) 通訊協定（而非 WSMan）來建立 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="12cbd-132">This example creates a CIM session using the Distributed COM (DCOM) protocol instead of WSMan.</span></span>

```powershell
$SessionOption = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server1 -SessionOption $SessionOption
```

## <span data-ttu-id="12cbd-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12cbd-133">PARAMETERS</span></span>

### <span data-ttu-id="12cbd-134">-Authentication</span><span class="sxs-lookup"><span data-stu-id="12cbd-134">-Authentication</span></span>

<span data-ttu-id="12cbd-135">指定用於使用者認證的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="12cbd-135">Specifies the authentication type used for the user's credentials.</span></span> <span data-ttu-id="12cbd-136">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="12cbd-136">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="12cbd-137">預設</span><span class="sxs-lookup"><span data-stu-id="12cbd-137">Default</span></span>
- <span data-ttu-id="12cbd-138">Digest</span><span class="sxs-lookup"><span data-stu-id="12cbd-138">Digest</span></span>
- <span data-ttu-id="12cbd-139">交涉</span><span class="sxs-lookup"><span data-stu-id="12cbd-139">Negotiate</span></span>
- <span data-ttu-id="12cbd-140">基本</span><span class="sxs-lookup"><span data-stu-id="12cbd-140">Basic</span></span>
- <span data-ttu-id="12cbd-141">Kerberos</span><span class="sxs-lookup"><span data-stu-id="12cbd-141">Kerberos</span></span>
- <span data-ttu-id="12cbd-142">NtlmDomain</span><span class="sxs-lookup"><span data-stu-id="12cbd-142">NtlmDomain</span></span>
- <span data-ttu-id="12cbd-143">CredSsp</span><span class="sxs-lookup"><span data-stu-id="12cbd-143">CredSsp</span></span>

<span data-ttu-id="12cbd-144">您無法使用 **NtlmDomain** authentication 類型連接到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="12cbd-144">You cannot use the **NtlmDomain** authentication type for connection to the local computer.</span></span> <span data-ttu-id="12cbd-145">**CredSSP** 驗證只有在 windows Vista、windows Server 2008 和更新版本的 windows 中才能使用。</span><span class="sxs-lookup"><span data-stu-id="12cbd-145">**CredSSP** authentication is available only in Windows Vista, Windows Server 2008, and later versions of Windows.</span></span>

> [!CAUTION]
> <span data-ttu-id="12cbd-146">認證安全性服務提供者 (CredSSP) 驗證是針對需要在多個資源上進行驗證的命令所設計，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="12cbd-146">Credential Security Service Provider (CredSSP) authentication is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="12cbd-147">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="12cbd-147">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="12cbd-148">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="12cbd-148">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: CredentialParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12cbd-149">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="12cbd-149">-CertificateThumbprint</span></span>

<span data-ttu-id="12cbd-150">指定具有執行此動作之許可權的使用者帳戶的數位公開金鑰憑證 (x.509) 。</span><span class="sxs-lookup"><span data-stu-id="12cbd-150">Specifies the digital public key certificate (X.509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="12cbd-151">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="12cbd-151">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="12cbd-152">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="12cbd-152">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="12cbd-153">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="12cbd-153">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="12cbd-154">若要取得憑證指紋，請使用 [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) PowerShell 憑證提供者中的或 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12cbd-154">To get a certificate thumbprint, use the [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) or [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) cmdlets in the PowerShell Certificate Provider.</span></span>

<span data-ttu-id="12cbd-155">如需詳細資訊，請參閱 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)。</span><span class="sxs-lookup"><span data-stu-id="12cbd-155">For more information, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

```yaml
Type: System.String
Parameter Sets: CertificatePrameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12cbd-156">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="12cbd-156">-ComputerName</span></span>

<span data-ttu-id="12cbd-157">指定要建立 CIM 會話的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="12cbd-157">Specifies the name of the computer to which to create the CIM session.</span></span> <span data-ttu-id="12cbd-158">指定單一電腦名稱稱，或以逗號分隔的多個電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="12cbd-158">Specify either a single computer name, or multiple computer names separated by a comma.</span></span>

<span data-ttu-id="12cbd-159">如果未指定 **ComputerName** ，則會建立本機電腦的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="12cbd-159">If **ComputerName** is not specified, a CIM session to the local computer is created.</span></span> <span data-ttu-id="12cbd-160">您可以用下列其中一種格式來指定電腦名稱稱的值：</span><span class="sxs-lookup"><span data-stu-id="12cbd-160">You can specify the value for computer name in one of the following formats:</span></span>

- <span data-ttu-id="12cbd-161">一或多個 NetBIOS 名稱</span><span class="sxs-lookup"><span data-stu-id="12cbd-161">One or more NetBIOS names</span></span>
- <span data-ttu-id="12cbd-162">一或多個 IP 位址</span><span class="sxs-lookup"><span data-stu-id="12cbd-162">One or more IP addresses</span></span>
- <span data-ttu-id="12cbd-163">一或多個完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="12cbd-163">One or more fully qualified domain names.</span></span>

<span data-ttu-id="12cbd-164">如果電腦與使用者位於不同的網域，您必須指定完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="12cbd-164">If the computer is in a different domain than the user, you must specify the fully qualified domain name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12cbd-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="12cbd-165">-Credential</span></span>

<span data-ttu-id="12cbd-166">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="12cbd-166">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="12cbd-167">如果未指定 **認證** ，則會使用目前的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="12cbd-167">If **Credential** is not specified, the current user account is used.</span></span>

<span data-ttu-id="12cbd-168">使用下列其中一種格式來指定 **認證** 的值：</span><span class="sxs-lookup"><span data-stu-id="12cbd-168">Specify the value for **Credential** using one of the following formats:</span></span>

- <span data-ttu-id="12cbd-169">使用者名稱： "User01"</span><span class="sxs-lookup"><span data-stu-id="12cbd-169">A user name: "User01"</span></span>
- <span data-ttu-id="12cbd-170">功能變數名稱和使用者名稱： "Domain01\User01"</span><span class="sxs-lookup"><span data-stu-id="12cbd-170">A domain name and a user name: "Domain01\User01"</span></span>
- <span data-ttu-id="12cbd-171">使用者主體名稱： " User@Domain.com "</span><span class="sxs-lookup"><span data-stu-id="12cbd-171">A user principal name: "User@Domain.com"</span></span>
- <span data-ttu-id="12cbd-172">PSCredential 物件，例如 Cmdlet 所傳回的物件 [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) 。</span><span class="sxs-lookup"><span data-stu-id="12cbd-172">A PSCredential object, such as one returned by the [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet.</span></span>

<span data-ttu-id="12cbd-173">當您輸入使用者名稱時，會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="12cbd-173">When you type a user name, you are prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialParameterSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12cbd-174">-Name</span><span class="sxs-lookup"><span data-stu-id="12cbd-174">-Name</span></span>

<span data-ttu-id="12cbd-175">指定 CIM 會話的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="12cbd-175">Specifies a friendly name for the CIM session.</span></span>

<span data-ttu-id="12cbd-176">使用其他 Cmdlet （例如 Cmdlet）時，您可以使用此名稱來參考 CIM 會話 [`Get-CimSession`](Get-CimSession.md) 。</span><span class="sxs-lookup"><span data-stu-id="12cbd-176">You can use the name to refer to the CIM session when using other cmdlets, such as the [`Get-CimSession`](Get-CimSession.md) cmdlet.</span></span>
<span data-ttu-id="12cbd-177">該名稱對電腦或目前工作階段而言不需要是唯一的。</span><span class="sxs-lookup"><span data-stu-id="12cbd-177">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12cbd-178">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="12cbd-178">-OperationTimeoutSec</span></span>

<span data-ttu-id="12cbd-179">Cmdlet 等候伺服器回應的持續時間。</span><span class="sxs-lookup"><span data-stu-id="12cbd-179">Duration for which the cmdlet waits for a response from the server.</span></span>

<span data-ttu-id="12cbd-180">根據預設，此參數的值為0，表示此 Cmdlet 會使用伺服器的預設超時值。</span><span class="sxs-lookup"><span data-stu-id="12cbd-180">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="12cbd-181">如果 **OperationTimeoutSec** 參數設定為小於健全連接重試超時時間3分鐘的值，則超過 **OperationTimeoutSec** 參數值的網路失敗就無法復原，因為伺服器上的作業會在用戶端重新連線之前超時。</span><span class="sxs-lookup"><span data-stu-id="12cbd-181">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12cbd-182">-Port</span><span class="sxs-lookup"><span data-stu-id="12cbd-182">-Port</span></span>

<span data-ttu-id="12cbd-183">指定遠端電腦上要供此連線使用的網路連接埠。</span><span class="sxs-lookup"><span data-stu-id="12cbd-183">Specifies the network port on the remote computer that is used for this connection.</span></span>
<span data-ttu-id="12cbd-184">若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="12cbd-184">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span>
<span data-ttu-id="12cbd-185">預設連接埠是 5985 (用於 HTTP 的 WinRM 連接埠) 和 5986 (用於 HTTPS 的 WinRM 連接埠)。</span><span class="sxs-lookup"><span data-stu-id="12cbd-185">The default ports are 5985 (the WinRM port for HTTP) and 5986 (the WinRM port for HTTPS).</span></span>

<span data-ttu-id="12cbd-186">使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。</span><span class="sxs-lookup"><span data-stu-id="12cbd-186">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span>
<span data-ttu-id="12cbd-187">使用下列命令來設定接聽程式：</span><span class="sxs-lookup"><span data-stu-id="12cbd-187">Use the following commands to configure the listener:</span></span>

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number>"}`

<span data-ttu-id="12cbd-188">除非必要，否則請勿使用 **Port** 參數。</span><span class="sxs-lookup"><span data-stu-id="12cbd-188">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="12cbd-189">命令中的連接埠設定會套用到所有電腦或命令執行所在工作階段。</span><span class="sxs-lookup"><span data-stu-id="12cbd-189">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="12cbd-190">替代的連接埠設定可能使得命令無法在全部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="12cbd-190">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12cbd-191">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="12cbd-191">-SessionOption</span></span>

<span data-ttu-id="12cbd-192">設定新 CIM 會話的 advanced 選項。</span><span class="sxs-lookup"><span data-stu-id="12cbd-192">Sets advanced options for the new CIM session.</span></span> <span data-ttu-id="12cbd-193">輸入使用 Cmdlet 建立之 **CimSessionOption** 物件的名稱 [`New-CimSessionOption`](New-CimSessionOption.md) 。</span><span class="sxs-lookup"><span data-stu-id="12cbd-193">Enter the name of a **CimSessionOption** object created using the [`New-CimSessionOption`](New-CimSessionOption.md) cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.CimSessionOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12cbd-194">-SkipTestConnection</span><span class="sxs-lookup"><span data-stu-id="12cbd-194">-SkipTestConnection</span></span>

<span data-ttu-id="12cbd-195">根據預設，此 `New-CimSession` Cmdlet 會建立與遠端 WS-Management 端點的連線，有兩個原因：驗證遠端伺服器是否正在接聽使用 **port** 參數指定的埠號碼，以及驗證指定的帳號認證。</span><span class="sxs-lookup"><span data-stu-id="12cbd-195">By default, the `New-CimSession` cmdlet establishes a connection with a remote WS-Management endpoint for two reasons: to verify that the remote server is listening on the port number that is specified using the **Port** parameter, and to verify the specified account credentials.</span></span> <span data-ttu-id="12cbd-196">您可以使用標準 WS-Identity 操作來完成驗證。</span><span class="sxs-lookup"><span data-stu-id="12cbd-196">The verification is accomplished using a standard WS-Identity operation.</span></span> <span data-ttu-id="12cbd-197">如果遠端 WS-Management 端點無法使用 WS 識別，或減少一些資料傳輸時間，您可以新增 **SkipTestConnection** 交換器參數。</span><span class="sxs-lookup"><span data-stu-id="12cbd-197">You can add the **SkipTestConnection** switch parameter if the remote WS-Management endpoint cannot use WS-Identify, or to reduce some data transmission time.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12cbd-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12cbd-198">CommonParameters</span></span>

<span data-ttu-id="12cbd-199">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="12cbd-199">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12cbd-200">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="12cbd-200">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="12cbd-201">輸入</span><span class="sxs-lookup"><span data-stu-id="12cbd-201">INPUTS</span></span>

### <span data-ttu-id="12cbd-202">無</span><span class="sxs-lookup"><span data-stu-id="12cbd-202">None</span></span>

<span data-ttu-id="12cbd-203">此 Cmdlet 不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="12cbd-203">This cmdlet accepts no inputs.</span></span>

## <span data-ttu-id="12cbd-204">輸出</span><span class="sxs-lookup"><span data-stu-id="12cbd-204">OUTPUTS</span></span>

### <span data-ttu-id="12cbd-205">Microsoft.Management.Infrastructure.CimSession</span><span class="sxs-lookup"><span data-stu-id="12cbd-205">Microsoft.Management.Infrastructure.CimSession</span></span>

## <span data-ttu-id="12cbd-206">注意</span><span class="sxs-lookup"><span data-stu-id="12cbd-206">NOTES</span></span>

## <span data-ttu-id="12cbd-207">相關連結</span><span class="sxs-lookup"><span data-stu-id="12cbd-207">RELATED LINKS</span></span>

[<span data-ttu-id="12cbd-208">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="12cbd-208">Get-ChildItem</span></span>](../Microsoft.Powershell.Management/Get-ChildItem.md)

[<span data-ttu-id="12cbd-209">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="12cbd-209">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="12cbd-210">Get-Item</span><span class="sxs-lookup"><span data-stu-id="12cbd-210">Get-Item</span></span>](../Microsoft.Powershell.Management/Get-Item.md)

[<span data-ttu-id="12cbd-211">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="12cbd-211">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="12cbd-212">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="12cbd-212">Remove-CimSession</span></span>](Remove-CimSession.md)

[<span data-ttu-id="12cbd-213">New-CimSessionOption</span><span class="sxs-lookup"><span data-stu-id="12cbd-213">New-CimSessionOption</span></span>](New-CimSessionOption.md)

[<span data-ttu-id="12cbd-214">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="12cbd-214">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)
