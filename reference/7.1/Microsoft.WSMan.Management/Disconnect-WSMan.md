---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disconnect-wsman?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-WSMan
ms.openlocfilehash: 7e2cfc6db38d6537ba83c4dced769dd41a351602
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202143"
---
# <span data-ttu-id="95a1b-103">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="95a1b-103">Disconnect-WSMan</span></span>

## <span data-ttu-id="95a1b-104">概要</span><span class="sxs-lookup"><span data-stu-id="95a1b-104">SYNOPSIS</span></span>
<span data-ttu-id="95a1b-105">中斷用戶端與遠端電腦上之 WinRM 服務的連線。</span><span class="sxs-lookup"><span data-stu-id="95a1b-105">Disconnects the client from the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="95a1b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="95a1b-106">SYNTAX</span></span>

```
Disconnect-WSMan [[-ComputerName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="95a1b-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="95a1b-107">DESCRIPTION</span></span>
<span data-ttu-id="95a1b-108">**Disconnect-WSMan** Cmdlet 會中斷用戶端與遠端電腦上 WinRM 服務的連線。</span><span class="sxs-lookup"><span data-stu-id="95a1b-108">The **Disconnect-WSMan** cmdlet disconnects the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="95a1b-109">如果您將 WS-Management 會話儲存在變數中，會話物件仍會保留在變數中，但 WS-Management 會話的狀態會是 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="95a1b-109">If you saved the WS-Management session in a variable, the session object remains in the variable, but the state of the WS-Management session is Closed.</span></span>
<span data-ttu-id="95a1b-110">您可以在 WSMan 提供者中使用此 Cmdlet 來中斷用戶端與遠端電腦上之 WinRM 服務的連線。</span><span class="sxs-lookup"><span data-stu-id="95a1b-110">You can use this cmdlet within the context of the WSMan provider to disconnect the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="95a1b-111">不過，您也可以使用此 Cmdlet 來中斷與遠端電腦上之 WinRM 服務的連線，再變更為 WSMan 提供者。</span><span class="sxs-lookup"><span data-stu-id="95a1b-111">However, you can also use this cmdlet to disconnect from the WinRM service on remote computers before you change to the WSMan provider.</span></span>

<span data-ttu-id="95a1b-112">如需如何連線到遠端電腦上之 WinRM 服務的詳細資訊，請參閱 Connect-WSMan。</span><span class="sxs-lookup"><span data-stu-id="95a1b-112">For more information about how to connect to the WinRM service on a remote computer, see Connect-WSMan.</span></span>

## <span data-ttu-id="95a1b-113">範例</span><span class="sxs-lookup"><span data-stu-id="95a1b-113">EXAMPLES</span></span>

### <span data-ttu-id="95a1b-114">範例1：刪除遠端電腦的連接</span><span class="sxs-lookup"><span data-stu-id="95a1b-114">Example 1: Delete a connection to a remote computer</span></span>

```
PS C:\> Disconnect-WSMan -computer server01
PS C:\> cd WSMan:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
```

<span data-ttu-id="95a1b-115">此命令會刪除名為 server01 之遠端電腦的連接。</span><span class="sxs-lookup"><span data-stu-id="95a1b-115">This command deletes the connection to the remote computer named server01.</span></span>

<span data-ttu-id="95a1b-116">此 Cmdlet 通常是在 WSMan 提供者中用來中斷與遠端電腦 (在此案例中是 server01 電腦) 的連線。</span><span class="sxs-lookup"><span data-stu-id="95a1b-116">This cmdlet is generally used within the context of the WSMan provider to disconnect from a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="95a1b-117">不過，您也可以使用「 **中斷連線-WSMan** 」來移除與遠端電腦的連線，然後再變更為 WSMan 提供者。</span><span class="sxs-lookup"><span data-stu-id="95a1b-117">However, you can also use **Disconnect-WSMan** to remove connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="95a1b-118">這些連接不會出現在 ComputerName 清單中。</span><span class="sxs-lookup"><span data-stu-id="95a1b-118">Those connections do not appear in the ComputerName list.</span></span>

## <span data-ttu-id="95a1b-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="95a1b-119">PARAMETERS</span></span>

### <span data-ttu-id="95a1b-120">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="95a1b-120">-ComputerName</span></span>
<span data-ttu-id="95a1b-121">指定要執行管理作業的電腦。</span><span class="sxs-lookup"><span data-stu-id="95a1b-121">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="95a1b-122">值可以是完整網域名稱、NetBIOS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="95a1b-122">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="95a1b-123">使用本機電腦名稱、使用 localhost，或使用句點 (.) 來指定本機電腦。</span><span class="sxs-lookup"><span data-stu-id="95a1b-123">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="95a1b-124">預設值是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="95a1b-124">The local computer is the default.</span></span>
<span data-ttu-id="95a1b-125">當遠端電腦與使用者位於不同網域，您必須使用完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="95a1b-125">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="95a1b-126">您可以使用管線將此參數的值傳送至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="95a1b-126">You can pipe a value for this parameter to the cmdlet.</span></span>

<span data-ttu-id="95a1b-127">您無法中斷與本機主機的連線。</span><span class="sxs-lookup"><span data-stu-id="95a1b-127">You cannot disconnect from the local host.</span></span>
<span data-ttu-id="95a1b-128">也就是說，您無法中斷與本機電腦的預設連接。</span><span class="sxs-lookup"><span data-stu-id="95a1b-128">That is, you cannot disconnect the default connection to the local computer.</span></span>
<span data-ttu-id="95a1b-129">但是，如果您建立與本機電腦的個別連接，例如使用電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="95a1b-129">However, if you create a separate connection to the local computer, for example, by using the computer name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="95a1b-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="95a1b-130">CommonParameters</span></span>
<span data-ttu-id="95a1b-131">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="95a1b-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="95a1b-132">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="95a1b-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="95a1b-133">輸入</span><span class="sxs-lookup"><span data-stu-id="95a1b-133">INPUTS</span></span>

### <span data-ttu-id="95a1b-134">無</span><span class="sxs-lookup"><span data-stu-id="95a1b-134">None</span></span>
<span data-ttu-id="95a1b-135">此 Cmdlet 不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="95a1b-135">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="95a1b-136">輸出</span><span class="sxs-lookup"><span data-stu-id="95a1b-136">OUTPUTS</span></span>

### <span data-ttu-id="95a1b-137">無</span><span class="sxs-lookup"><span data-stu-id="95a1b-137">None</span></span>
<span data-ttu-id="95a1b-138">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="95a1b-138">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="95a1b-139">注意</span><span class="sxs-lookup"><span data-stu-id="95a1b-139">NOTES</span></span>

## <span data-ttu-id="95a1b-140">相關連結</span><span class="sxs-lookup"><span data-stu-id="95a1b-140">RELATED LINKS</span></span>

[<span data-ttu-id="95a1b-141">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="95a1b-141">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="95a1b-142">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="95a1b-142">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="95a1b-143">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="95a1b-143">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="95a1b-144">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="95a1b-144">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="95a1b-145">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="95a1b-145">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="95a1b-146">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="95a1b-146">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="95a1b-147">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="95a1b-147">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="95a1b-148">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="95a1b-148">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="95a1b-149">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="95a1b-149">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="95a1b-150">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="95a1b-150">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="95a1b-151">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="95a1b-151">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="95a1b-152">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="95a1b-152">Test-WSMan</span></span>](Test-WSMan.md)

