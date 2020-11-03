---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: 814be4153687268123114b4036b640eeb0f0da71
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93196720"
---
# <span data-ttu-id="dc5bf-103">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="dc5bf-103">Get-WSManCredSSP</span></span>

## <span data-ttu-id="dc5bf-104">概要</span><span class="sxs-lookup"><span data-stu-id="dc5bf-104">SYNOPSIS</span></span>
<span data-ttu-id="dc5bf-105">取得用戶端的「認證安全性支援提供者」相關設定。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-105">Gets the Credential Security Support Provider-related configuration for the client.</span></span>

## <span data-ttu-id="dc5bf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dc5bf-106">SYNTAX</span></span>

```
Get-WSManCredSSP [<CommonParameters>]
```

## <span data-ttu-id="dc5bf-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc5bf-107">DESCRIPTION</span></span>
<span data-ttu-id="dc5bf-108">**WSManCredSSP** 指令程式會取得用戶端和伺服器的「認證安全性支援提供者」相關設定。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-108">The **Get-WSManCredSSP** cmdlet gets the Credential Security Support Provider-related configuration of the client and the server.</span></span>
<span data-ttu-id="dc5bf-109">輸出會指出「認證安全性支援提供者 (CredSSP)」驗證已啟用或已停用。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-109">The output indicates whether Credential Security Support Provider (CredSSP) authentication is enabled or disabled.</span></span>
<span data-ttu-id="dc5bf-110">此 Cmdlet 也會顯示 CredSSP 之 **AllowFreshCredentials** 原則的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-110">This cmdlet also displays configuration information for the **AllowFreshCredentials** policy of CredSSP.</span></span>

<span data-ttu-id="dc5bf-111">當您使用 CredSSP 驗證時，使用者的認證會被傳遞到遠端電腦進行驗證。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-111">When you use CredSSP authentication, the user credentials are passed to a remote computer to be authenticated.</span></span>
<span data-ttu-id="dc5bf-112">此類型的驗證是針對會從另一個遠端工作階段建立遠端工作階段的命令所設計。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-112">This type of authentication is designed for commands that create a remote session from another remote session.</span></span>
<span data-ttu-id="dc5bf-113">例如，若您想在遠端電腦上執行背景工作，請使用此類型的驗證。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-113">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="dc5bf-114">此 Cmdlet 會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="dc5bf-114">The cmdlet performs the following actions:</span></span>

- <span data-ttu-id="dc5bf-115">取得用戶端 ( **\<localhost|computername\> \Client\Auth\CredSSP** ) 上的 WS-Management CredSSP 設定。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-115">Gets the WS-Management CredSSP setting on the client ( **\<localhost|computername\>\Client\Auth\CredSSP** ).</span></span>
- <span data-ttu-id="dc5bf-116">取得 Windows CredSSP 原則設定 **AllowFreshCredentials** 。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-116">Gets the Windows CredSSP policy setting **AllowFreshCredentials** .</span></span>
- <span data-ttu-id="dc5bf-117">取得伺服器上的 WS-Management CredSSP 設定 ( **\<localhost|computername\> \Service\Auth\CredSSP** ) 。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-117">Gets the WS-Management CredSSP setting on the server ( **\<localhost|computername\>\Service\Auth\CredSSP** ).</span></span>

<span data-ttu-id="dc5bf-118">注意：CredSSP 驗證會將使用者認證從本機電腦委派給遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-118">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="dc5bf-119">此做法會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-119">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="dc5bf-120">若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-120">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="dc5bf-121">範例</span><span class="sxs-lookup"><span data-stu-id="dc5bf-121">EXAMPLES</span></span>

### <span data-ttu-id="dc5bf-122">範例 1︰顯示 CredSSP 設定</span><span class="sxs-lookup"><span data-stu-id="dc5bf-122">Example 1: Display CredSSP configuration</span></span>

```
PS C:\> Get-WSManCredSSP
```

<span data-ttu-id="dc5bf-123">此命令會顯示用戶端與伺服器的 CredSSP 設定資訊。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-123">This command displays CredSSP configuration information for both the client and server.</span></span>

<span data-ttu-id="dc5bf-124">輸出會識別此電腦是否已針對 CredSSP 設定。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-124">The output identifies that this computer is or is not configured for CredSSP.</span></span>

<span data-ttu-id="dc5bf-125">若電腦已針對 CredSSP 設定，輸出如下：</span><span class="sxs-lookup"><span data-stu-id="dc5bf-125">If the computer is configured for CredSSP, this is the output:</span></span>

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

<span data-ttu-id="dc5bf-126">若電腦未針對 CredSSP 設定，輸出如下：</span><span class="sxs-lookup"><span data-stu-id="dc5bf-126">If the computer is not configured for CredSSP, this is the output:</span></span>

`The machine is not configured to allow delegating fresh credentials.`

## <span data-ttu-id="dc5bf-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dc5bf-127">PARAMETERS</span></span>

### <span data-ttu-id="dc5bf-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dc5bf-128">CommonParameters</span></span>
<span data-ttu-id="dc5bf-129">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dc5bf-130">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dc5bf-131">輸入</span><span class="sxs-lookup"><span data-stu-id="dc5bf-131">INPUTS</span></span>

### <span data-ttu-id="dc5bf-132">無</span><span class="sxs-lookup"><span data-stu-id="dc5bf-132">None</span></span>
<span data-ttu-id="dc5bf-133">此 Cmdlet 不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-133">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="dc5bf-134">輸出</span><span class="sxs-lookup"><span data-stu-id="dc5bf-134">OUTPUTS</span></span>

### <span data-ttu-id="dc5bf-135">無</span><span class="sxs-lookup"><span data-stu-id="dc5bf-135">None</span></span>
<span data-ttu-id="dc5bf-136">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-136">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="dc5bf-137">注意</span><span class="sxs-lookup"><span data-stu-id="dc5bf-137">NOTES</span></span>

* <span data-ttu-id="dc5bf-138">若要停用 CredSSP 驗證，請使用 Disable-WSManCredSSP Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-138">To disable CredSSP authentication, use the Disable-WSManCredSSP cmdlet.</span></span> <span data-ttu-id="dc5bf-139">若要啟用 CredSSP 驗證，請使用 Enable-WSManCredSSP Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dc5bf-139">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

## <span data-ttu-id="dc5bf-140">相關連結</span><span class="sxs-lookup"><span data-stu-id="dc5bf-140">RELATED LINKS</span></span>

[<span data-ttu-id="dc5bf-141">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="dc5bf-141">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="dc5bf-142">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="dc5bf-142">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="dc5bf-143">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="dc5bf-143">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="dc5bf-144">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="dc5bf-144">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="dc5bf-145">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="dc5bf-145">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="dc5bf-146">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="dc5bf-146">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="dc5bf-147">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="dc5bf-147">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="dc5bf-148">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="dc5bf-148">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="dc5bf-149">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="dc5bf-149">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="dc5bf-150">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="dc5bf-150">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="dc5bf-151">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="dc5bf-151">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="dc5bf-152">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="dc5bf-152">Test-WSMan</span></span>](Test-WSMan.md)
