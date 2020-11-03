---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: e5dedf3d161f2687bddfbd09740812d8c5cbaa77
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205672"
---
# <span data-ttu-id="0aeb5-103">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="0aeb5-103">New-PSSession</span></span>

## <span data-ttu-id="0aeb5-104">概要</span><span class="sxs-lookup"><span data-stu-id="0aeb5-104">SYNOPSIS</span></span>
<span data-ttu-id="0aeb5-105">建立連到本機或遠端電腦的持續連線。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-105">Creates a persistent connection to a local or remote computer.</span></span>

## <span data-ttu-id="0aeb5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0aeb5-106">SYNTAX</span></span>

### <span data-ttu-id="0aeb5-107">ComputerName (預設值)</span><span class="sxs-lookup"><span data-stu-id="0aeb5-107">ComputerName (Default)</span></span>

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="0aeb5-108">Uri</span><span class="sxs-lookup"><span data-stu-id="0aeb5-108">Uri</span></span>

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="0aeb5-109">VMId</span><span class="sxs-lookup"><span data-stu-id="0aeb5-109">VMId</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="0aeb5-110">VMName</span><span class="sxs-lookup"><span data-stu-id="0aeb5-110">VMName</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="0aeb5-111">工作階段</span><span class="sxs-lookup"><span data-stu-id="0aeb5-111">Session</span></span>

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="0aeb5-112">ContainerId</span><span class="sxs-lookup"><span data-stu-id="0aeb5-112">ContainerId</span></span>

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="0aeb5-113">UseWindowsPowerShellParameterSet</span><span class="sxs-lookup"><span data-stu-id="0aeb5-113">UseWindowsPowerShellParameterSet</span></span>

```
New-PSSession [-Name <String[]>] [-UseWindowsPowerShell] [<CommonParameters>]
```

### <span data-ttu-id="0aeb5-114">SSHHost</span><span class="sxs-lookup"><span data-stu-id="0aeb5-114">SSHHost</span></span>

```
New-PSSession [-Name <String[]>] [-Port <Int32>] [-HostName] <String[]> [-UserName <String>]
 [-KeyFilePath <String>] [-SSHTransport] [-Subsystem <String>] [<CommonParameters>]
```

### <span data-ttu-id="0aeb5-115">SSHHostHashParam</span><span class="sxs-lookup"><span data-stu-id="0aeb5-115">SSHHostHashParam</span></span>

```
New-PSSession [-Name <String[]>] -SSHConnection <Hashtable[]> [<CommonParameters>]
```

## <span data-ttu-id="0aeb5-116">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0aeb5-116">DESCRIPTION</span></span>

<span data-ttu-id="0aeb5-117">`New-PSSession`Cmdlet 會在本機或遠端電腦上建立 ( **PSSession** ) 的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-117">The `New-PSSession` cmdlet creates a PowerShell session ( **PSSession** ) on a local or remote computer.</span></span> <span data-ttu-id="0aeb5-118">當您建立 **PSSession** 時，PowerShell 會建立與遠端電腦的持續連線。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-118">When you create a **PSSession** , PowerShell establishes a persistent connection to the remote computer.</span></span>

<span data-ttu-id="0aeb5-119">使用 **PSSession** 來執行多個共用資料的命令，例如函數或變數的值。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-119">Use a **PSSession** to run multiple commands that share data, such as a function or the value of a variable.</span></span> <span data-ttu-id="0aeb5-120">若要在 **PSSession** 中執行命令，請使用 `Invoke-Command` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-120">To run commands in a **PSSession** , use the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="0aeb5-121">若要使用 **PSSession** 與遠端電腦直接互動，請使用 `Enter-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-121">To use the **PSSession** to interact directly with a remote computer, use the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="0aeb5-122">如需詳細資訊，請參閱 [about_PSSessions](about/about_PSSessions.md)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-122">For more information, see [about_PSSessions](about/about_PSSessions.md).</span></span>

<span data-ttu-id="0aeb5-123">您可以使用或的 **ComputerName** 參數，在遠端電腦上執行命令，而不需要建立 **PSSession** `Enter-PSSession` `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-123">You can run commands on a remote computer without creating a **PSSession** by using the **ComputerName** parameters of `Enter-PSSession` or `Invoke-Command`.</span></span> <span data-ttu-id="0aeb5-124">當您使用 **ComputerName** 參數時，PowerShell 會建立用於命令的暫時連接，然後關閉。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-124">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that is used for the command and is then closed.</span></span>

<span data-ttu-id="0aeb5-125">從 PowerShell 6.0 開始，您可以使用安全殼層 (SSH) 來建立連線，並在遠端電腦上建立會話，如果本機電腦上有 SSH，而且遠端電腦已設定 PowerShell SSH 端點。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-125">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to and create a session on a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="0aeb5-126">以 SSH 為基礎之 PowerShell 遠端會話的優點是，它可以跨多個平臺運作， (Windows、Linux、macOS) 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-126">The benefit of an SSH based PowerShell remote session is that it can work across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="0aeb5-127">針對以 SSH 為基礎的會話，您可以使用 **HostName** 或 **SSHConnection** 參數集來指定遠端電腦和相關的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-127">For SSH based sessions you use the **HostName** or **SSHConnection** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="0aeb5-128">如需有關如何設定 PowerShell SSH 遠端的詳細資訊，請參閱透過 [SSH 的 Powershell 遠端](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)功能。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-128">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="0aeb5-129">從 Linux 或 macOS 用戶端使用 WSMan 遠端處理時，伺服器憑證不受信任的 HTTPS 端點 (例如，自我簽署的憑證) 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-129">When using WSMan remoting from a Linux or macOS client with a HTTPS endpoint where the server certificate is not trusted (e.g., a self-signed certificate).</span></span> <span data-ttu-id="0aeb5-130">您必須提供 `PSSessionOption` 包含和的 `-SkipCACheck` ， `-SkipCNCheck` 才能成功建立連接。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-130">You must provide a `PSSessionOption` that includes `-SkipCACheck` and `-SkipCNCheck` to successfully establish the connection.</span></span> <span data-ttu-id="0aeb5-131">只有在您的環境中，您可以確定伺服器憑證和目標系統的網路連接時，才需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-131">Only do this if you are in an environment where you can be certain of the server certificate and the network connection to the target system.</span></span>

## <span data-ttu-id="0aeb5-132">範例</span><span class="sxs-lookup"><span data-stu-id="0aeb5-132">EXAMPLES</span></span>

### <span data-ttu-id="0aeb5-133">範例1：在本機電腦上建立會話</span><span class="sxs-lookup"><span data-stu-id="0aeb5-133">Example 1: Create a session on the local computer</span></span>

```powershell
$s = New-PSSession
```

<span data-ttu-id="0aeb5-134">此命令會在本機電腦上建立新的 **pssession** ，並將 **pssession** 儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-134">This command creates a new **PSSession** on the local computer and saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="0aeb5-135">您現在可以使用這個 **PSSession** 在本機電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-135">You can now use this **PSSession** to run commands on the local computer.</span></span>

### <span data-ttu-id="0aeb5-136">範例2：在遠端電腦上建立會話</span><span class="sxs-lookup"><span data-stu-id="0aeb5-136">Example 2: Create a session on a remote computer</span></span>

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

<span data-ttu-id="0aeb5-137">此命令會在 Server01 電腦上建立新的 **PSSession** ，並將它儲存在 `$Server01` 變數中。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-137">This command creates a new **PSSession** on the Server01 computer and saves it in the `$Server01` variable.</span></span>

<span data-ttu-id="0aeb5-138">建立多個 **PSSession** 物件時，請將它們指派給具有有用名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-138">When creating multiple **PSSession** objects, assign them to variables with useful names.</span></span> <span data-ttu-id="0aeb5-139">這可協助您管理後續命令中的 **PSSession** 物件。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-139">This will help you manage the **PSSession** objects in subsequent commands.</span></span>

### <span data-ttu-id="0aeb5-140">範例3：在多部電腦上建立會話</span><span class="sxs-lookup"><span data-stu-id="0aeb5-140">Example 3: Create sessions on multiple computers</span></span>

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

<span data-ttu-id="0aeb5-141">此命令會建立三個 **PSSession** 物件，在 **ComputerName** 參數所指定的每一部電腦上建立一個。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-141">This command creates three **PSSession** objects, one on each of the computers specified by the **ComputerName** parameter.</span></span>

<span data-ttu-id="0aeb5-142">此命令會使用指派運算子 (=) 將新的 **PSSession** 物件指派給變數： `$s1` 、 `$s2` 、 `$s3` 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-142">The command uses the assignment operator (=) to assign the new **PSSession** objects to variables: `$s1`, `$s2`, `$s3`.</span></span> <span data-ttu-id="0aeb5-143">它會將 Server01 **pssession** 指派給 `$s1` 、將 Server02 **pssession** 指派給 `$s2` ，以及將 Server03 **pssession** 指派給 `$s3` 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-143">It assigns the Server01 **PSSession** to `$s1`, the Server02 **PSSession** to `$s2`, and the Server03 **PSSession** to `$s3`.</span></span>

<span data-ttu-id="0aeb5-144">當您將多個物件指派給一系列的變數時，PowerShell 會將每個物件分別指派給數列中的變數。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-144">When you assign multiple objects to a series of variables, PowerShell assigns each object to a variable in the series respectively.</span></span> <span data-ttu-id="0aeb5-145">如果物件數目多於變數數目，就會將所有剩餘的物件指派給最後一個變數。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-145">If there are more objects than variables, all remaining objects are assigned to the last variable.</span></span> <span data-ttu-id="0aeb5-146">如果變數數目多於物件數目，則剩餘的變數會是空的 (null)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-146">If there are more variables than objects, the remaining variables are empty (null).</span></span>

### <span data-ttu-id="0aeb5-147">範例4：建立具有指定埠的會話</span><span class="sxs-lookup"><span data-stu-id="0aeb5-147">Example 4: Create a session with a specified port</span></span>

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

<span data-ttu-id="0aeb5-148">此命令會在連線到伺服器埠8081並使用 SSL 通訊協定的 Server01 電腦上建立新的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-148">This command creates a new **PSSession** on the Server01 computer that connects to server port 8081 and uses the SSL protocol.</span></span> <span data-ttu-id="0aeb5-149">新的 **PSSession** 會使用稱為 E12 的替代會話設定。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-149">The new **PSSession** uses an alternative session configuration called E12.</span></span>

<span data-ttu-id="0aeb5-150">設定連接埠之前，您必須先將遠端電腦上的 WinRM 接聽程式設定為在連接埠 8081 進行接聽。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-150">Before setting the port, you must configure the WinRM listener on the remote computer to listen on port 8081.</span></span> <span data-ttu-id="0aeb5-151">如需詳細資訊，請參閱 **Port** 參數的描述。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-151">For more information, see the description of the **Port** parameter.</span></span>

### <span data-ttu-id="0aeb5-152">範例5：根據現有的會話建立會話</span><span class="sxs-lookup"><span data-stu-id="0aeb5-152">Example 5: Create a session based on an existing session</span></span>

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

<span data-ttu-id="0aeb5-153">此命令會使用與現有 **PSSession** 相同的屬性來建立 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-153">This command creates a **PSSession** with the same properties as an existing **PSSession** .</span></span> <span data-ttu-id="0aeb5-154">當現有 **PSSession** 的資源已用盡，且需要新的 **pssession** 來卸載部分需求時，您可以使用此命令格式。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-154">You can use this command format when the resources of an existing **PSSession** are exhausted and a new **PSSession** is needed to offload some of the demand.</span></span>

<span data-ttu-id="0aeb5-155">命令使用的 **Session** 參數 `New-PSSession` 來指定儲存在變數中的 **PSSession** `$s` 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-155">The command uses the **Session** parameter of `New-PSSession` to specify the **PSSession** saved in the `$s` variable.</span></span> <span data-ttu-id="0aeb5-156">它使用 Domain1\Admin01 使用者的認證來完成命令。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-156">It uses the credentials of the Domain1\Admin01 user to complete the command.</span></span>

### <span data-ttu-id="0aeb5-157">範例6：在不同網域中建立具有全域領域的會話</span><span class="sxs-lookup"><span data-stu-id="0aeb5-157">Example 6: Create a session with a global scope in a different domain</span></span>

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

<span data-ttu-id="0aeb5-158">此範例示範如何在不同網域中的電腦上建立具有全域領域的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-158">This example shows how to create a **PSSession** with a global scope on a computer in a different domain.</span></span>

<span data-ttu-id="0aeb5-159">根據預設，在命令列建立的 **pssession** 物件是使用區域範圍所建立，而在腳本中建立的 **pssession** 物件具有腳本領域。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-159">By default, **PSSession** objects created at the command line are created with local scope and **PSSession** objects created in a script have script scope.</span></span>

<span data-ttu-id="0aeb5-160">若要建立具有全域領域的 **pssession** ，請建立新的 **pssession** ，然後將 **pssession** 儲存在轉換成全域領域的變數中。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-160">To create a **PSSession** with global scope, create a new **PSSession** and then store the **PSSession** in a variable that is cast to a global scope.</span></span> <span data-ttu-id="0aeb5-161">在此情況下， `$s` 變數會轉換成全域領域。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-161">In this case, the `$s` variable is cast to a global scope.</span></span>

<span data-ttu-id="0aeb5-162">此命令使用 **ComputerName** 參數來指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-162">The command uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="0aeb5-163">由於電腦是在與使用者帳戶不同的網域中，因此電腦的完整名稱會與使用者的認證一起指定。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-163">Because the computer is in a different domain than the user account, the full name of the computer is specified together with the credentials of the user.</span></span>

### <span data-ttu-id="0aeb5-164">範例7：建立許多電腦的會話</span><span class="sxs-lookup"><span data-stu-id="0aeb5-164">Example 7: Create sessions for many computers</span></span>

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

<span data-ttu-id="0aeb5-165">此命令會在 Servers.txt 檔案中列出的每一部200電腦上建立 **pssession** ，並將產生的 **pssession** 儲存在 `$rs` 變數中。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-165">This command creates a **PSSession** on each of the 200 computers listed in the Servers.txt file and it stores the resulting **PSSession** in the `$rs` variable.</span></span> <span data-ttu-id="0aeb5-166">**PSSession** 物件的節流閥限制為50。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-166">The **PSSession** objects have a throttle limit of 50.</span></span>

<span data-ttu-id="0aeb5-167">當電腦的名稱是儲存在資料庫、試算表、文字檔或其他可轉換成文字的格式中時，可以使用此命令格式。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-167">You can use this command format when the names of computers are stored in a database, spreadsheet, text file, or other text-convertible format.</span></span>

### <span data-ttu-id="0aeb5-168">範例8：使用 URI 建立會話</span><span class="sxs-lookup"><span data-stu-id="0aeb5-168">Example 8: Create a session by using a URI</span></span>

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

<span data-ttu-id="0aeb5-169">此命令會在 Server01 電腦上建立 **PSSession** ，並將它儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-169">This command creates a **PSSession** on the Server01 computer and stores it in the `$s` variable.</span></span> <span data-ttu-id="0aeb5-170">它使用 **URI** 參數來指定傳輸通訊協定、遠端電腦、埠，以及替代會話設定。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-170">It uses the **URI** parameter to specify the transport protocol, the remote computer, the port, and an alternate session configuration.</span></span> <span data-ttu-id="0aeb5-171">它也會使用 **Credential** 參數來指定具有在遠端電腦上建立會話之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-171">It also uses the **Credential** parameter to specify a user account that has permission to create a session on the remote computer.</span></span>

### <span data-ttu-id="0aeb5-172">範例9：在一組會話中執行背景工作</span><span class="sxs-lookup"><span data-stu-id="0aeb5-172">Example 9: Run a background job in a set of sessions</span></span>

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

<span data-ttu-id="0aeb5-173">這些命令會建立一組 **pssession** 物件，然後在每個 **pssession** 物件中執行背景工作。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-173">These commands create a set of **PSSession** objects and then run a background job in each of the **PSSession** objects.</span></span>

<span data-ttu-id="0aeb5-174">第一個命令會在 Servers.txt 檔案中列出的每一部電腦上建立新的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-174">The first command creates a new **PSSession** on each of the computers listed in the Servers.txt file.</span></span> <span data-ttu-id="0aeb5-175">它會使用 `New-PSSession` Cmdlet 來建立 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-175">It uses the `New-PSSession` cmdlet to create the **PSSession** .</span></span> <span data-ttu-id="0aeb5-176">**ComputerName** 參數的值是一個命令，此命令會使用 `Get-Content` Cmdlet 取得 Servers.txt 檔案的電腦名稱稱清單。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-176">The value of the **ComputerName** parameter is a command that uses the `Get-Content` cmdlet to get the list of computer names the Servers.txt file.</span></span>

<span data-ttu-id="0aeb5-177">此命令會使用 **Credential** 參數來建立具有網域系統管理員許可權的 **PSSession** 物件，並使用 **ThrottleLimit** 參數將命令限制為16個並行連接。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-177">The command uses the **Credential** parameter to create the **PSSession** objects that have the permission of a domain administrator, and it uses the **ThrottleLimit** parameter to limit the command to 16 concurrent connections.</span></span> <span data-ttu-id="0aeb5-178">此命令會將 **PSSession** 物件儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-178">The command saves the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="0aeb5-179">第二個命令會使用 Cmdlet 的 **AsJob** 參數 `Invoke-Command` 啟動背景工作，在 `Get-Process PowerShell` 中的每個 **PSSession** 物件中執行命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-179">The second command uses the **AsJob** parameter of the `Invoke-Command` cmdlet to start a background job that runs a `Get-Process PowerShell` command in each of the **PSSession** objects in `$s`.</span></span>

<span data-ttu-id="0aeb5-180">如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](About/about_Jobs.md) 和 [about_Remote_Jobs](About/about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-180">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

### <span data-ttu-id="0aeb5-181">範例10：使用其 URI 建立電腦的會話</span><span class="sxs-lookup"><span data-stu-id="0aeb5-181">Example 10: Create a session for a computer by using its URI</span></span>

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

<span data-ttu-id="0aeb5-182">此命令會建立 **PSSession** 物件，以連接到由 URI 指定的電腦，而不是電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-182">This command creates a **PSSession** objects that connects to a computer that is specified by a URI instead of a computer name.</span></span>

### <span data-ttu-id="0aeb5-183">範例11：建立會話選項</span><span class="sxs-lookup"><span data-stu-id="0aeb5-183">Example 11: Create a session option</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

<span data-ttu-id="0aeb5-184">這個範例示範如何建立會話選項物件，並使用 **SessionOption** 參數。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-184">This example shows how to create a session option object and use the **SessionOption** parameter.</span></span>

<span data-ttu-id="0aeb5-185">第一個命令會使用 `New-PSSessionOption` Cmdlet 來建立會話選項。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-185">The first command uses the `New-PSSessionOption` cmdlet to create a session option.</span></span> <span data-ttu-id="0aeb5-186">它會將產生的 **SessionOption** 物件儲存在 `$so` 變數中。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-186">It saves the resulting **SessionOption** object in the `$so` variable.</span></span>

<span data-ttu-id="0aeb5-187">第二個命令會在新的工作階段中使用該選項。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-187">The second command uses the option in a new session.</span></span> <span data-ttu-id="0aeb5-188">此命令會使用 `New-PSSession` Cmdlet 來建立新的會話。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-188">The command uses the `New-PSSession` cmdlet to create a new session.</span></span> <span data-ttu-id="0aeb5-189">SessionOption 參數的值是變數中的 **SessionOption** 物件 `$so` 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-189">The value of the SessionOption parameter is the **SessionOption** object in the `$so` variable.</span></span>

### <span data-ttu-id="0aeb5-190">範例12：使用 SSH 建立會話</span><span class="sxs-lookup"><span data-stu-id="0aeb5-190">Example 12: Create a session using SSH</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="0aeb5-191">此範例說明如何使用安全殼層 (SSH) 來建立新的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-191">This example shows how to create a new **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="0aeb5-192">如果在遠端電腦上設定 SSH 以提示輸入密碼，您將會收到密碼提示。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-192">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span> <span data-ttu-id="0aeb5-193">否則，您必須使用以 SSH 金鑰為基礎的使用者驗證。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-193">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="0aeb5-194">範例13：使用 SSH 建立會話，並指定埠和使用者驗證金鑰</span><span class="sxs-lookup"><span data-stu-id="0aeb5-194">Example 13: Create a session using SSH and specify the port and user authentication key</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="0aeb5-195">此範例說明如何使用安全殼層 (SSH) 來建立 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-195">This example shows how to create a **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="0aeb5-196">它會使用 **port** 參數來指定要使用的埠，並使用 **KeyFilePath** 參數來指定用來識別和驗證遠端電腦上使用者的 RSA 金鑰。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-196">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to identify and authenticate the user on the remote computer.</span></span>

### <span data-ttu-id="0aeb5-197">範例14：使用 SSH 建立多個會話</span><span class="sxs-lookup"><span data-stu-id="0aeb5-197">Example 14: Create multiple sessions using SSH</span></span>

```powershell
$sshConnections = @{ HostName="WinServer1"; UserName="domain\userA"; KeyFilePath="c:\users\UserA\id_rsa" }, @{ HostName="UserB@LinuxServer5"; KeyFilePath="c:\UserB\<path>\id_rsa" }
New-PSSession -SSHConnection $sshConnections
```

<span data-ttu-id="0aeb5-198">此範例說明如何使用安全殼層 (SSH) 和 **SSHConnection** 參數集來建立多個會話。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-198">This example shows how to create multiple sessions using Secure Shell (SSH) and the **SSHConnection** parameter set.</span></span> <span data-ttu-id="0aeb5-199">**SSHConnection** 參數會採用雜湊表的陣列，其中包含每個會話的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-199">The **SSHConnection** parameter takes an array of hash tables that contain connection information for each session.</span></span> <span data-ttu-id="0aeb5-200">請注意，此範例需要目標遠端電腦設定 SSH 以支援金鑰型使用者驗證。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-200">Note that this example requires that the target remote computers have SSH configured to support key based user authentication.</span></span>

## <span data-ttu-id="0aeb5-201">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0aeb5-201">PARAMETERS</span></span>

### <span data-ttu-id="0aeb5-202">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="0aeb5-202">-AllowRedirection</span></span>

<span data-ttu-id="0aeb5-203">指出此 Cmdlet 允許將此連線重新導向至替代的統一資源識別項 (URI) 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-203">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="0aeb5-204">使用 **ConnectionURI** 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-204">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="0aeb5-205">根據預設，PowerShell 不會重新導向連線，但是您可以使用這個參數讓它重新導向連接。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-205">By default, PowerShell does not redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="0aeb5-206">您也可以變更 **MaximumConnectionRedirectionCount** 工作階段選項值，限制連線重新導向的次數。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-206">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="0aeb5-207">使用 Cmdlet 的 **MaximumRedirection** 參數， `New-PSSessionOption` 或設定 **$PSSessionOption** 喜好設定變數的 **MaximumConnectionRedirectionCount** 屬性。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-207">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="0aeb5-208">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-208">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-209">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="0aeb5-209">-ApplicationName</span></span>

<span data-ttu-id="0aeb5-210">指定連線 URI 的應用程式名稱區段。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-210">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="0aeb5-211">當您沒有在命令中使用 **ConnectionURI** 參數時，請使用這個參數來指定應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-211">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="0aeb5-212">預設值是 `$PSSessionApplicationName` 本機電腦上喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-212">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="0aeb5-213">若未定義此喜好設定變數，則預設值是 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-213">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="0aeb5-214">這個值適用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-214">This value is appropriate for most uses.</span></span> <span data-ttu-id="0aeb5-215">如需詳細資訊，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-215">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="0aeb5-216">WinRM 服務會使用應用程式名稱來選取要用來為連線要求提供服務的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-216">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="0aeb5-217">此參數的值應該符合遠端電腦上接聽程式之 **URLPrefix** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-217">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-218">-Authentication</span><span class="sxs-lookup"><span data-stu-id="0aeb5-218">-Authentication</span></span>

<span data-ttu-id="0aeb5-219">指定用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-219">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="0aeb5-220">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="0aeb5-220">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0aeb5-221">預設</span><span class="sxs-lookup"><span data-stu-id="0aeb5-221">Default</span></span>
- <span data-ttu-id="0aeb5-222">基本</span><span class="sxs-lookup"><span data-stu-id="0aeb5-222">Basic</span></span>
- <span data-ttu-id="0aeb5-223">Credssp</span><span class="sxs-lookup"><span data-stu-id="0aeb5-223">Credssp</span></span>
- <span data-ttu-id="0aeb5-224">Digest</span><span class="sxs-lookup"><span data-stu-id="0aeb5-224">Digest</span></span>
- <span data-ttu-id="0aeb5-225">Kerberos</span><span class="sxs-lookup"><span data-stu-id="0aeb5-225">Kerberos</span></span>
- <span data-ttu-id="0aeb5-226">交涉</span><span class="sxs-lookup"><span data-stu-id="0aeb5-226">Negotiate</span></span>
- <span data-ttu-id="0aeb5-227">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="0aeb5-227">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="0aeb5-228">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-228">The default value is Default.</span></span>

<span data-ttu-id="0aeb5-229">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-229">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="0aeb5-230">認證安全性支援提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-230">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="0aeb5-231">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-231">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="0aeb5-232">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-232">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-233">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="0aeb5-233">-CertificateThumbprint</span></span>

<span data-ttu-id="0aeb5-234">對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-234">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="0aeb5-235">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-235">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="0aeb5-236">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-236">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="0aeb5-237">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-237">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="0aeb5-238">若要取得憑證，請使用 `Get-Item` `Get-ChildItem` PowerShell Cert：磁片磁碟機中的或命令。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-238">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-239">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="0aeb5-239">-ComputerName</span></span>

<span data-ttu-id="0aeb5-240">指定電腦名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-240">Specifies an array of names of computers.</span></span> <span data-ttu-id="0aeb5-241">此 Cmdlet 會建立 ( **PSSession** ) 至指定電腦的持續連線。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-241">This cmdlet creates a persistent connection ( **PSSession** ) to the specified computer.</span></span> <span data-ttu-id="0aeb5-242">如果您輸入多個電腦名稱稱，則會 `New-PSSession` 建立多個 **PSSession** 物件（每一部電腦各一個）。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-242">If you enter multiple computer names, `New-PSSession` creates multiple **PSSession** objects, one for each computer.</span></span> <span data-ttu-id="0aeb5-243">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-243">The default is the local computer.</span></span>

<span data-ttu-id="0aeb5-244">輸入一或多部遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-244">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="0aeb5-245">若要指定本機電腦，請輸入電腦名稱、localhost 或句點 (.)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-245">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="0aeb5-246">當電腦與使用者位於不同網域，則必須使用完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-246">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="0aeb5-247">您也可以使用管線將電腦名稱稱（以引號括住）傳送至 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-247">You can also pipe a computer name, in quotation marks, to `New-PSSession`.</span></span>

<span data-ttu-id="0aeb5-248">若要在 **ComputerName** 參數的值中使用 IP 位址，命令必須包含 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-248">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="0aeb5-249">此外，必須將電腦設定為使用 HTTPS 傳輸，或必須在本機電腦的 WinRM TrustedHosts 清單中包含遠端電腦的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-249">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="0aeb5-250">如需將電腦名稱稱新增到 TrustedHosts 清單的指示，請參閱 [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md)中的「如何將電腦新增到信任的主機清單」。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-250">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="0aeb5-251">若要在 **ComputerName** 參數的值中包含本機電腦，請使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-251">To include the local computer in the value of the **ComputerName** parameter, start Windows PowerShell by using the Run as administrator option.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-252">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="0aeb5-252">-ConfigurationName</span></span>

<span data-ttu-id="0aeb5-253">指定用於新 **PSSession** 的會話設定。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-253">Specifies the session configuration that is used for the new **PSSession** .</span></span>

<span data-ttu-id="0aeb5-254">輸入工作階段設定的設定名稱或完整資源 URI。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-254">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="0aeb5-255">如果您只指定設定名稱，則會在前面加上下列架構 URI： `http://schemas.microsoft.com/PowerShell` 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-255">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="0aeb5-256">工作階段的工作階段設定是位於遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-256">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="0aeb5-257">如果遠端電腦上沒有指定的工作階段設定，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-257">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="0aeb5-258">預設值是 `$PSSessionConfigurationName` 本機電腦上喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-258">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="0aeb5-259">若未設定此喜好設定變數，則預設為 Microsoft.PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-259">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="0aeb5-260">如需詳細資訊，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-260">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-261">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="0aeb5-261">-ConnectionUri</span></span>

<span data-ttu-id="0aeb5-262">指定定義會話之連接端點的 URI。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-262">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="0aeb5-263">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-263">The URI must be fully qualified.</span></span> <span data-ttu-id="0aeb5-264">這個字串的格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="0aeb5-264">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="0aeb5-265">預設值如下：</span><span class="sxs-lookup"><span data-stu-id="0aeb5-265">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="0aeb5-266">如果您未指定 **ConnectionURI** ，可以使用 **UseSSL** 、 **ComputerName** 、 **Port** 及 **ApplicationName** 參數來指定 **ConnectionURI** 值。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-266">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="0aeb5-267">URI 的 Transport 區段有效值為 HTTP 與 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-267">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="0aeb5-268">若指定含傳輸區段的連線 URI，但未指定連接埠，將會以標準連接埠 80 (適用於 HTTP) 和 443 (適用於 HTTPS) 建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-268">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="0aeb5-269">若要使用 PowerShell 遠端的預設埠，請指定 HTTP 的埠5985或 HTTPS 的5986。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-269">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="0aeb5-270">如果目的地電腦將連線重新導向至不同的 URI，除非您在命令中使用 **AllowRedirection** 參數，否則 PowerShell 會禁止重新導向。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-270">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: Uri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-271">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="0aeb5-271">-ContainerId</span></span>

<span data-ttu-id="0aeb5-272">指定容器的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-272">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="0aeb5-273">此 Cmdlet 會啟動每個指定容器的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-273">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="0aeb5-274">使用 `docker ps` 命令來取得容器識別碼的清單。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-274">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="0aeb5-275">如需詳細資訊，請參閱 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 命令的說明。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-275">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-276">-Credential</span><span class="sxs-lookup"><span data-stu-id="0aeb5-276">-Credential</span></span>

<span data-ttu-id="0aeb5-277">指定具有執行此動作之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-277">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="0aeb5-278">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-278">The default is the current user.</span></span>

<span data-ttu-id="0aeb5-279">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-279">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="0aeb5-280">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-280">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="0aeb5-281">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-281">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="0aeb5-282">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-282">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-283">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="0aeb5-283">-EnableNetworkAccess</span></span>

<span data-ttu-id="0aeb5-284">指出此 Cmdlet 會將互動式安全性權杖新增至回送會話。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-284">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="0aeb5-285">互動式權杖可讓您在會從其他電腦取得資料的回送工作階段中執行命令。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-285">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="0aeb5-286">例如，您可以在會將 XML 檔案從遠端電腦複製到本機電腦的工作階段中執行命令。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-286">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="0aeb5-287">回送會話是在同一部電腦上產生和結束的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-287">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="0aeb5-288">若要建立回送會話，請省略 **ComputerName** 參數，或將其值設為點 (. ) 、localhost 或本機電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-288">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (.), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="0aeb5-289">根據預設，此 Cmdlet 會使用網路權杖建立回送會話，這可能不會提供足夠的許可權來驗證遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-289">By default, this cmdlet creates loopback sessions by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="0aeb5-290">**EnableNetworkAccess** 參數只在回送工作階段中有效。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-290">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="0aeb5-291">如果您在遠端電腦上建立會話時使用 **EnableNetworkAccess** ，則命令會成功，但是會忽略參數。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-291">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="0aeb5-292">您也可以在回送會話中啟用遠端存取，方法是使用 **驗證** 參數的 CredSSP 值，該參數會將會話認證委派給其他電腦。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-292">You can also enable remote access in a loopback session by using the CredSSP value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="0aeb5-293">為了保護電腦免于惡意存取，具有互動式權杖（使用 **EnableNetworkAccess** 參數所建立）的已中斷連線回送會話，只能從建立會話的電腦重新連接。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-293">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="0aeb5-294">使用 CredSSP 驗證且已中斷連線的工作階段可從其他電腦重新連線。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-294">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="0aeb5-295">如需詳細資訊，請參閱`Disconnect-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-295">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="0aeb5-296">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-296">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri, Session
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-297">-HostName</span><span class="sxs-lookup"><span data-stu-id="0aeb5-297">-HostName</span></span>

<span data-ttu-id="0aeb5-298">針對安全殼層 (SSH) 基礎的連線，指定電腦名稱稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-298">Specifies an array of computer names for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="0aeb5-299">這類似于 ComputerName 參數，不同之處在于遠端電腦的連線是使用 SSH 而非 Windows WinRM 進行。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-299">This is similar to the ComputerName parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span>

<span data-ttu-id="0aeb5-300">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-300">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-301">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="0aeb5-301">-KeyFilePath</span></span>

<span data-ttu-id="0aeb5-302">指定安全殼層 (SSH) 用來驗證遠端電腦上使用者的金鑰檔路徑。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-302">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="0aeb5-303">SSH 允許透過私用/公開金鑰來執行使用者驗證，作為基本密碼驗證的替代方案。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-303">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="0aeb5-304">如果遠端電腦設定為進行金鑰驗證，則此參數可以用來提供識別使用者的金鑰。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-304">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="0aeb5-305">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-305">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-306">-Name</span><span class="sxs-lookup"><span data-stu-id="0aeb5-306">-Name</span></span>

<span data-ttu-id="0aeb5-307">指定 **PSSession** 的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-307">Specifies a friendly name for the **PSSession** .</span></span>

<span data-ttu-id="0aeb5-308">當您使用其他 Cmdlet 時，您可以使用名稱來參考 **PSSession** ，例如 `Get-PSSession` 和 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-308">You can use the name to refer to the **PSSession** when you use other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="0aeb5-309">該名稱對電腦或目前工作階段而言不需要是唯一的。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-309">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-310">-Port</span><span class="sxs-lookup"><span data-stu-id="0aeb5-310">-Port</span></span>

<span data-ttu-id="0aeb5-311">指定遠端電腦上要供此連線使用的網路連接埠。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-311">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="0aeb5-312">若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-312">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="0aeb5-313">預設的埠是5985，也就是 HTTP 的 WinRM 埠和5986，也就是 HTTPS 的 WinRM 埠。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-313">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="0aeb5-314">使用其他埠之前，您必須先將遠端電腦上的 WinRM 接聽程式設定為在該埠上接聽。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-314">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="0aeb5-315">使用下列命令來設定接聽程式：</span><span class="sxs-lookup"><span data-stu-id="0aeb5-315">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="0aeb5-316">除非必要，否則請勿使用 **Port** 參數。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-316">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="0aeb5-317">命令中的連接埠設定會套用到所有電腦或命令執行所在工作階段。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-317">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="0aeb5-318">替代的連接埠設定可能使得命令無法在全部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-318">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-319">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="0aeb5-319">-RunAsAdministrator</span></span>

<span data-ttu-id="0aeb5-320">指出 **PSSession** 以系統管理員身分執行。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-320">Indicates that the **PSSession** runs as administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-321">-Session</span><span class="sxs-lookup"><span data-stu-id="0aeb5-321">-Session</span></span>

<span data-ttu-id="0aeb5-322">指定 **pssession** 物件的陣列，這個 Cmdlet 會使用這個陣列做為新 **PSSession** 的模型。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-322">Specifies an array of **PSSession** objects that this cmdlet uses as a model for the new **PSSession** .</span></span> <span data-ttu-id="0aeb5-323">此參數會建立新的 **pssession** 物件，這些物件與指定的 **pssession** 物件具有相同的屬性。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-323">This parameter creates new **PSSession** objects that have the same properties as the specified **PSSession** objects.</span></span>

<span data-ttu-id="0aeb5-324">輸入包含 **pssession** 物件的變數，或輸入可建立或取得 **pssession** 物件的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-324">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="0aeb5-325">產生的 **PSSession** 物件具有相同的電腦名稱稱、應用程式名稱、連線 URI、埠、設定名稱、節流限制，以及安全通訊端層 (SSL) 值做為原始，但它們具有不同的顯示名稱、識別碼和實例識別碼 (GUID) 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-325">The resulting **PSSession** objects have the same computer name, application name, connection URI, port, configuration name, throttle limit, and Secure Sockets Layer (SSL) value as the originals, but they have a different display name, ID, and instance ID (GUID).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-326">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="0aeb5-326">-SessionOption</span></span>

<span data-ttu-id="0aeb5-327">指定會話的 advanced 選項。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-327">Specifies advanced options for the session.</span></span> <span data-ttu-id="0aeb5-328">輸入 **SessionOption** 物件（例如您使用 Cmdlet 建立的物件 `New-PSSessionOption` ），或輸入雜湊表，其中索引鍵為會話選項名稱，而值為會話選項值。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-328">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="0aeb5-329">選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-329">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="0aeb5-330">否則，將以工作階段設定中設定的選項建立預設值。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-330">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="0aeb5-331">會話選項值的優先順序高於 `$PSSessionOption` 喜好設定變數和會話設定中設定之會話的預設值。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-331">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="0aeb5-332">不過，它們的優先順序不會高於工作階段設定中設定的最大值、配額或限制。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-332">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="0aeb5-333">如需包含預設值之會話選項的描述，請參閱 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-333">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="0aeb5-334">如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-334">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="0aeb5-335">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-335">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-336">-SSHConnection</span><span class="sxs-lookup"><span data-stu-id="0aeb5-336">-SSHConnection</span></span>

<span data-ttu-id="0aeb5-337">此參數會採用雜湊表的陣列，其中每個雜湊表都包含一個或多個必要的連接參數，以建立安全殼層 (SSH) 連接 (HostName、Port、UserName、KeyFilePath) 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-337">This parameter takes an array of hashtables where each hashtable contains one or more connection parameters needed to establish a Secure Shell (SSH) connection (HostName, Port, UserName, KeyFilePath).</span></span>

<span data-ttu-id="0aeb5-338">雜湊表連接參數與 **主機名稱** 參數集所定義的相同。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-338">The hashtable connection parameters are the same as defined for the **HostName** parameter set.</span></span>

<span data-ttu-id="0aeb5-339">**SSHConnection** 參數適用于建立多個會話，其中每個會話都需要不同的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-339">The **SSHConnection** parameter is useful for creating multiple sessions where each session requires different connection information.</span></span>

<span data-ttu-id="0aeb5-340">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-340">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-341">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="0aeb5-341">-SSHTransport</span></span>

<span data-ttu-id="0aeb5-342">指出使用安全殼層 (SSH) 來建立遠端連線。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-342">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="0aeb5-343">PowerShell 預設會使用 Windows WinRM 連接到遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-343">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="0aeb5-344">此參數會強制 PowerShell 使用 HostName 參數集來建立以 SSH 為基礎的遠端連線。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-344">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="0aeb5-345">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-345">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-346">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="0aeb5-346">-ThrottleLimit</span></span>

<span data-ttu-id="0aeb5-347">指定為執行此命令可建立的最大同時連線數。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-347">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="0aeb5-348">若省略此參數，或輸入值為 0 (零)，則會使用預設值 32。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-348">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span>

<span data-ttu-id="0aeb5-349">節流限制僅適用於目前命令，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-349">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, Uri, VMId, VMName, Session, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-350">-UserName</span><span class="sxs-lookup"><span data-stu-id="0aeb5-350">-UserName</span></span>

<span data-ttu-id="0aeb5-351">指定用於在遠端電腦上建立會話之帳戶的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-351">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="0aeb5-352">使用者驗證方法將取決於遠端電腦上如何設定安全殼層 (SSH) 。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-352">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="0aeb5-353">如果 SSH 設定為基本密碼驗證，則系統會提示您輸入使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-353">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="0aeb5-354">如果設定 SSH 以進行金鑰型使用者驗證，則可透過 KeyFilePath 參數提供金鑰檔案路徑，而且不會出現任何密碼提示。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-354">If SSH is configured for key based user authentication then a key file path can be provided via the KeyFilePath parameter and no password prompt will occur.</span></span> <span data-ttu-id="0aeb5-355">請注意，如果用戶端使用者金鑰檔位於 SSH 已知的位置，則金鑰型驗證不需要 KeyFilePath 參數，且使用者驗證會根據使用者名稱自動進行。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-355">Note that if the client user key file is located in an SSH known location then the KeyFilePath parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="0aeb5-356">如需詳細資訊，請參閱關於金鑰型使用者驗證的 SSH 檔。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-356">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="0aeb5-357">這不是必要的參數。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-357">This is not a required parameter.</span></span> <span data-ttu-id="0aeb5-358">如果未指定 UserName 參數，則會使用目前登入的使用者名稱做為連接。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-358">If no UserName parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="0aeb5-359">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-359">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-360">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="0aeb5-360">-UseSSL</span></span>

<span data-ttu-id="0aeb5-361">指出此 Cmdlet 會使用 SSL 通訊協定來建立與遠端電腦的連接。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-361">Indicates that this cmdlet uses the SSL protocol to establish a connection to the remote computer.</span></span>
<span data-ttu-id="0aeb5-362">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-362">By default, SSL is not used.</span></span>

<span data-ttu-id="0aeb5-363">WS-Management 加密透過網路傳輸的所有 PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-363">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="0aeb5-364">**UseSSL** 參數提供額外的保護，可跨 HTTPS 連接（而非 HTTP 連線）傳送資料。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-364">The **UseSSL** parameter offers an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="0aeb5-365">如果您使用此參數，但是命令所用的埠上無法使用 SSL，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-365">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-366">-VMId</span><span class="sxs-lookup"><span data-stu-id="0aeb5-366">-VMId</span></span>

<span data-ttu-id="0aeb5-367">指定虛擬機器的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-367">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="0aeb5-368">此 Cmdlet 會在每個指定的虛擬機器之間啟動互動式會話。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-368">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="0aeb5-369">若要查看可供您使用的虛擬機器，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="0aeb5-369">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-370">-VMName</span><span class="sxs-lookup"><span data-stu-id="0aeb5-370">-VMName</span></span>

<span data-ttu-id="0aeb5-371">指定虛擬機器名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-371">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="0aeb5-372">此 Cmdlet 會在每個指定的虛擬機器之間啟動互動式會話。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-372">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="0aeb5-373">若要查看可供您使用的虛擬機器，請使用 `Get-VM` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-373">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-374">-子系統</span><span class="sxs-lookup"><span data-stu-id="0aeb5-374">-Subsystem</span></span>

<span data-ttu-id="0aeb5-375">指定用於新 **PSSession** 的 SSH 子系統。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-375">Specifies the SSH subsystem used for the new **PSSession** .</span></span>

<span data-ttu-id="0aeb5-376">這會指定要在目標上使用的子系統，如 sshd_config 中所定義。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-376">This specifies the subsystem to use on the target as defined in sshd_config.</span></span>
<span data-ttu-id="0aeb5-377">子系統會使用預先定義的參數啟動特定版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-377">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span>
<span data-ttu-id="0aeb5-378">如果指定的子系統不存在於遠端電腦上，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-378">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="0aeb5-379">如果未使用此參數，則預設值為 ' powershell ' 子系統。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-379">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-380">-UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="0aeb5-380">-UseWindowsPowerShell</span></span>

<span data-ttu-id="0aeb5-381">{{填寫 UseWindowsPowerShell 描述}}</span><span class="sxs-lookup"><span data-stu-id="0aeb5-381">{{ Fill UseWindowsPowerShell Description }}</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseWindowsPowerShellParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aeb5-382">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0aeb5-382">CommonParameters</span></span>

<span data-ttu-id="0aeb5-383">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-383">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0aeb5-384">如需詳細資訊，請參閱 about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-384">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0aeb5-385">輸入</span><span class="sxs-lookup"><span data-stu-id="0aeb5-385">INPUTS</span></span>

### <span data-ttu-id="0aeb5-386">System.String、System.URI、System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="0aeb5-386">System.String, System.URI, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="0aeb5-387">您可以使用管線將字串、URI 或會話物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-387">You can pipe a string, URI, or session object to this cmdlet.</span></span>

## <span data-ttu-id="0aeb5-388">輸出</span><span class="sxs-lookup"><span data-stu-id="0aeb5-388">OUTPUTS</span></span>

### <span data-ttu-id="0aeb5-389">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="0aeb5-389">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="0aeb5-390">注意</span><span class="sxs-lookup"><span data-stu-id="0aeb5-390">NOTES</span></span>

- <span data-ttu-id="0aeb5-391">此 Cmdlet 會使用 PowerShell 遠端基礎結構。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-391">This cmdlet uses the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="0aeb5-392">若要使用這個 Cmdlet，本機電腦和任何遠端電腦都必須設定 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-392">To use this cmdlet, the local computer and any remote computers must be configured for PowerShell remoting.</span></span> <span data-ttu-id="0aeb5-393">如需詳細資訊，請參閱[about_Remote_Requirements](About/about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-393">For more information, see [about_Remote_Requirements](About/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="0aeb5-394">若要在本機電腦上建立 **PSSession** ，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-394">To create a **PSSession** on the local computer, start PowerShell with the Run as administrator option.</span></span>
- <span data-ttu-id="0aeb5-395">當您完成 **pssession** 之後，請使用 `Remove-PSSession` Cmdlet 來刪除 **pssession** 並釋放其資源。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-395">When you are finished with the **PSSession** , use the `Remove-PSSession` cmdlet to delete the **PSSession** and release its resources.</span></span>
- <span data-ttu-id="0aeb5-396">從 PowerShell 6.0 開始包含 **主機名稱** 和 **SSHConnection** 參數集。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-396">The **HostName** and **SSHConnection** parameter sets were included starting with PowerShell 6.0.</span></span>
  <span data-ttu-id="0aeb5-397">已新增它們，以根據安全殼層 (SSH) 提供 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-397">They were added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="0aeb5-398">在多個平臺上都支援 SSH 和 PowerShell (Windows、Linux、macOS) 和 PowerShell 遠端處理會在安裝和設定 PowerShell 和 SSH 的平臺上運作。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-398">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="0aeb5-399">這與先前僅限 Windows 的遠端處理（以 WinRM 為基礎）和大部分的 WinRM 特定功能和限制都不適用。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-399">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="0aeb5-400">例如，目前不支援以 WinRM 為基礎的配額、會話選項、自訂端點設定以及中斷連線/重新連線功能。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-400">For example WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="0aeb5-401">如需有關如何設定 PowerShell SSH 遠端的詳細資訊，請參閱透過 [SSH 的 Powershell 遠端](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)功能。</span><span class="sxs-lookup"><span data-stu-id="0aeb5-401">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <span data-ttu-id="0aeb5-402">相關連結</span><span class="sxs-lookup"><span data-stu-id="0aeb5-402">RELATED LINKS</span></span>

[<span data-ttu-id="0aeb5-403">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="0aeb5-403">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="0aeb5-404">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="0aeb5-404">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="0aeb5-405">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="0aeb5-405">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="0aeb5-406">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="0aeb5-406">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="0aeb5-407">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="0aeb5-407">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="0aeb5-408">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="0aeb5-408">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="0aeb5-409">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="0aeb5-409">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="0aeb5-410">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="0aeb5-410">Remove-PSSession</span></span>](Remove-PSSession.md)

