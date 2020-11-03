---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: e88f230575e1e3106efc211e3f95dd82ec62146c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202147"
---
# <span data-ttu-id="f6398-103">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="f6398-103">Disable-WSManCredSSP</span></span>

## <span data-ttu-id="f6398-104">概要</span><span class="sxs-lookup"><span data-stu-id="f6398-104">SYNOPSIS</span></span>
<span data-ttu-id="f6398-105">停用電腦上的 CredSSP 驗證。</span><span class="sxs-lookup"><span data-stu-id="f6398-105">Disables CredSSP authentication on a computer.</span></span>

## <span data-ttu-id="f6398-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f6398-106">SYNTAX</span></span>

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="f6398-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f6398-107">DESCRIPTION</span></span>
<span data-ttu-id="f6398-108">**Disable-WSManCredSSP** Cmdlet 會在用戶端或伺服器電腦上停用「認證安全性支援提供者 (CredSSP)」驗證。</span><span class="sxs-lookup"><span data-stu-id="f6398-108">The **Disable-WSManCredSSP** cmdlet disables Credential Security Support Provider (CredSSP) authentication on a client or on a server computer.</span></span>
<span data-ttu-id="f6398-109">使用 CredSSP 驗證時，會將使用者認證傳遞到遠端電腦進行驗證。</span><span class="sxs-lookup"><span data-stu-id="f6398-109">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span>

<span data-ttu-id="f6398-110">使用此 Cmdlet，透過在 *Role* 參數中指定 Client 來停用用戶端上的 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="f6398-110">Use this cmdlet to disable CredSSP on the client by specifying Client in the *Role* parameter.</span></span>
<span data-ttu-id="f6398-111">此 Cmdlet 會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f6398-111">This cmdlet performs the following actions:</span></span>

- <span data-ttu-id="f6398-112">停用用戶端上的 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="f6398-112">Disables CredSSP on the client.</span></span> <span data-ttu-id="f6398-113">此 Cmdlet 會將 WS-Management 設定 **\<localhost|computername\> \Client\Auth\CredSSP** 設定為 false。</span><span class="sxs-lookup"><span data-stu-id="f6398-113">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="f6398-114">從用戶端上的 Windows CredSSP 原則 **AllowFreshCredentials** 移除任何 WSMan/\* 設定。</span><span class="sxs-lookup"><span data-stu-id="f6398-114">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="f6398-115">使用此 Cmdlet，透過在 *Role* 中指定 Server 來停用 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="f6398-115">Use this cmdlet to disable CredSSP on the server by specifying Server in *Role* .</span></span>
<span data-ttu-id="f6398-116">此 Cmdlet 會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f6398-116">This cmdlet performs the following action:</span></span>

- <span data-ttu-id="f6398-117">停用伺服器上的 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="f6398-117">Disables CredSSP on the server.</span></span> <span data-ttu-id="f6398-118">此 Cmdlet 會將 WS-Management 設定 **\<localhost|computername\> \Service\Auth\CredSSP** 設定為 false。</span><span class="sxs-lookup"><span data-stu-id="f6398-118">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

<span data-ttu-id="f6398-119">注意：CredSSP 驗證會將使用者認證從本機電腦委派給遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="f6398-119">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="f6398-120">此做法會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="f6398-120">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="f6398-121">若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="f6398-121">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="f6398-122">範例</span><span class="sxs-lookup"><span data-stu-id="f6398-122">EXAMPLES</span></span>

### <span data-ttu-id="f6398-123">範例 1︰停用用戶端上的 CredSSP</span><span class="sxs-lookup"><span data-stu-id="f6398-123">Example 1: Disable CredSSP on a client</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Client
```

<span data-ttu-id="f6398-124">此命令會停用用戶端上的 CredSSP，這樣會防止委派給伺服器。</span><span class="sxs-lookup"><span data-stu-id="f6398-124">This command disables CredSSP on the client, which prevents delegation to servers.</span></span>

### <span data-ttu-id="f6398-125">範例 2︰停用用戶端上的 CredSSP</span><span class="sxs-lookup"><span data-stu-id="f6398-125">Example 2: Disable CredSSP on a server</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Server
```

<span data-ttu-id="f6398-126">此命令會停用伺服器上的 CredSSP，這樣會防止接受用戶端的委派。</span><span class="sxs-lookup"><span data-stu-id="f6398-126">This command disables CredSSP on the server, which prevents delegation from clients.</span></span>

## <span data-ttu-id="f6398-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f6398-127">PARAMETERS</span></span>

### <span data-ttu-id="f6398-128">-Role</span><span class="sxs-lookup"><span data-stu-id="f6398-128">-Role</span></span>
<span data-ttu-id="f6398-129">指定是否要停用 CredSSP 做為用戶端或伺服器。</span><span class="sxs-lookup"><span data-stu-id="f6398-129">Specifies whether to disable CredSSP as a client or as a server.</span></span>
<span data-ttu-id="f6398-130">此參數可接受的值包括：Client 和 Server。</span><span class="sxs-lookup"><span data-stu-id="f6398-130">The acceptable values for this parameter are: Client and Server.</span></span>

<span data-ttu-id="f6398-131">如果您指定 Client，此 Cmdlet 會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f6398-131">If you specify Client, this cmdlet performs the following actions:</span></span>

- <span data-ttu-id="f6398-132">停用用戶端上的 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="f6398-132">Disables CredSSP on the client.</span></span> <span data-ttu-id="f6398-133">此 Cmdlet 會將 WS-Management 設定 **\<localhost|computername\> \Client\Auth\CredSSP** 設定為 false。</span><span class="sxs-lookup"><span data-stu-id="f6398-133">This cmdlet sets WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="f6398-134">從用戶端上的 Windows CredSSP 原則 **AllowFreshCredentials** 移除任何 WSMan/\* 設定。</span><span class="sxs-lookup"><span data-stu-id="f6398-134">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="f6398-135">如果您指定 Server，此 Cmdlet 會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f6398-135">If you specify Server, this cmdlet performs the following action:</span></span>

- <span data-ttu-id="f6398-136">停用伺服器上的 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="f6398-136">Disables CredSSP on the server.</span></span> <span data-ttu-id="f6398-137">此 Cmdlet 會將 WS-Management 設定 **\<localhost|computername\> \Service\Auth\CredSSP** 設定為 false。</span><span class="sxs-lookup"><span data-stu-id="f6398-137">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

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

### <span data-ttu-id="f6398-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f6398-138">CommonParameters</span></span>
<span data-ttu-id="f6398-139">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f6398-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f6398-140">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f6398-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f6398-141">輸入</span><span class="sxs-lookup"><span data-stu-id="f6398-141">INPUTS</span></span>

### <span data-ttu-id="f6398-142">無</span><span class="sxs-lookup"><span data-stu-id="f6398-142">None</span></span>
<span data-ttu-id="f6398-143">此 Cmdlet 不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="f6398-143">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="f6398-144">輸出</span><span class="sxs-lookup"><span data-stu-id="f6398-144">OUTPUTS</span></span>

### <span data-ttu-id="f6398-145">無</span><span class="sxs-lookup"><span data-stu-id="f6398-145">None</span></span>
<span data-ttu-id="f6398-146">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f6398-146">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f6398-147">注意</span><span class="sxs-lookup"><span data-stu-id="f6398-147">NOTES</span></span>

* <span data-ttu-id="f6398-148">若要啟用 CredSSP 驗證，請使用 Enable-WSManCredSSP Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f6398-148">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

*

## <span data-ttu-id="f6398-149">相關連結</span><span class="sxs-lookup"><span data-stu-id="f6398-149">RELATED LINKS</span></span>

[<span data-ttu-id="f6398-150">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="f6398-150">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="f6398-151">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="f6398-151">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="f6398-152">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="f6398-152">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="f6398-153">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="f6398-153">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="f6398-154">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f6398-154">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="f6398-155">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="f6398-155">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="f6398-156">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f6398-156">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="f6398-157">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="f6398-157">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="f6398-158">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f6398-158">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="f6398-159">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f6398-159">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="f6398-160">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="f6398-160">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="f6398-161">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="f6398-161">Test-WSMan</span></span>](Test-WSMan.md)

