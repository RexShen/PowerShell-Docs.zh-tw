---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Command
ms.openlocfilehash: 652ff321ea1c6507915be9748715604166207200
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205404"
---
# <span data-ttu-id="c6e8c-103">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="c6e8c-103">Invoke-Command</span></span>

## <span data-ttu-id="c6e8c-104">概要</span><span class="sxs-lookup"><span data-stu-id="c6e8c-104">SYNOPSIS</span></span>
<span data-ttu-id="c6e8c-105">在本機與遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-105">Runs commands on local and remote computers.</span></span>

## <span data-ttu-id="c6e8c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c6e8c-106">SYNTAX</span></span>

### <span data-ttu-id="c6e8c-107"> (預設) 的進程</span><span class="sxs-lookup"><span data-stu-id="c6e8c-107">InProcess (Default)</span></span>

```
Invoke-Command [-ScriptBlock] <ScriptBlock> [-NoNewScope] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="c6e8c-108">工作階段</span><span class="sxs-lookup"><span data-stu-id="c6e8c-108">Session</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="c6e8c-109">FilePathRunspace</span><span class="sxs-lookup"><span data-stu-id="c6e8c-109">FilePathRunspace</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="c6e8c-110">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="c6e8c-110">FilePathComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-FilePath] <String> [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="c6e8c-111">ComputerName</span><span class="sxs-lookup"><span data-stu-id="c6e8c-111">ComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="c6e8c-112">Uri</span><span class="sxs-lookup"><span data-stu-id="c6e8c-112">Uri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="c6e8c-113">FilePathUri</span><span class="sxs-lookup"><span data-stu-id="c6e8c-113">FilePathUri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="c6e8c-114">VMId</span><span class="sxs-lookup"><span data-stu-id="c6e8c-114">VMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="c6e8c-115">VMName</span><span class="sxs-lookup"><span data-stu-id="c6e8c-115">VMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="c6e8c-116">FilePathVMId</span><span class="sxs-lookup"><span data-stu-id="c6e8c-116">FilePathVMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="c6e8c-117">FilePathVMName</span><span class="sxs-lookup"><span data-stu-id="c6e8c-117">FilePathVMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="c6e8c-118">ContainerId</span><span class="sxs-lookup"><span data-stu-id="c6e8c-118">ContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RunAsAdministrator] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="c6e8c-119">FilePathContainerId</span><span class="sxs-lookup"><span data-stu-id="c6e8c-119">FilePathContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RunAsAdministrator] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

## <span data-ttu-id="c6e8c-120">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c6e8c-120">DESCRIPTION</span></span>

<span data-ttu-id="c6e8c-121">此 `Invoke-Command` Cmdlet 會在本機或遠端電腦上執行命令，並傳回來自命令的所有輸出，包括錯誤。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-121">The `Invoke-Command` cmdlet runs commands on a local or remote computer and returns all output from the commands, including errors.</span></span> <span data-ttu-id="c6e8c-122">`Invoke-Command`您可以使用單一命令，在多部電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-122">Using a single `Invoke-Command` command, you can run commands on multiple computers.</span></span>

<span data-ttu-id="c6e8c-123">若要在遠端電腦上執行單一命令，請使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-123">To run a single command on a remote computer, use the **ComputerName** parameter.</span></span> <span data-ttu-id="c6e8c-124">若要執行一系列共用資料的相關命令，請使用 `New-PSSession` Cmdlet 在遠端電腦上建立 (持續連線) 的 **PSSession** ，然後使用的 **Session** 參數 `Invoke-Command` 在 **PSSession** 中執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-124">To run a series of related commands that share data, use the `New-PSSession` cmdlet to create a **PSSession** (a persistent connection) on the remote computer, and then use the **Session** parameter of `Invoke-Command` to run the command in the **PSSession** .</span></span> <span data-ttu-id="c6e8c-125">若要在中斷連線的工作階段中執行命令，請使用 **InDisconnectedSession** 參數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-125">To run a command in a disconnected session, use the **InDisconnectedSession** parameter.</span></span> <span data-ttu-id="c6e8c-126">若要在背景工作中執行命令，請使用 **AsJob** 參數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-126">To run a command in a background job, use the **AsJob** parameter.</span></span>

<span data-ttu-id="c6e8c-127">您也可以使用 `Invoke-Command` 本機電腦上的腳本區塊做為命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-127">You can also use `Invoke-Command` on a local computer to a script block as a command.</span></span> <span data-ttu-id="c6e8c-128">PowerShell 會在目前範圍的子範圍內立即執行腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-128">PowerShell runs the script block immediately in a child scope of the current scope.</span></span>

<span data-ttu-id="c6e8c-129">使用在 `Invoke-Command` 遠端電腦上執行命令之前，請先閱讀 [about_Remote](./About/about_Remote.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-129">Before using `Invoke-Command` to run commands on a remote computer, read [about_Remote](./About/about_Remote.md).</span></span>

<span data-ttu-id="c6e8c-130">某些程式碼範例會使用展開來縮減行長度。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-130">Some code samples use splatting to reduce the line length.</span></span> <span data-ttu-id="c6e8c-131">如需詳細資訊，請參閱 [about_Splatting](./About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-131">For more information, see [about_Splatting](./About/about_Splatting.md).</span></span>

## <span data-ttu-id="c6e8c-132">範例</span><span class="sxs-lookup"><span data-stu-id="c6e8c-132">EXAMPLES</span></span>

### <span data-ttu-id="c6e8c-133">範例1：在伺服器上執行腳本</span><span class="sxs-lookup"><span data-stu-id="c6e8c-133">Example 1: Run a script on a server</span></span>

<span data-ttu-id="c6e8c-134">此範例會在 `Test.ps1` Server01 電腦上執行腳本。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-134">This example runs the `Test.ps1` script on the Server01 computer.</span></span>

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

<span data-ttu-id="c6e8c-135">**FilePath** 參數指定的腳本位於本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-135">The **FilePath** parameter specifies a script that is located on the local computer.</span></span> <span data-ttu-id="c6e8c-136">指令碼會在遠端電腦上執行，而結果則會傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-136">The script runs on the remote computer and the results are returned to the local computer.</span></span>

### <span data-ttu-id="c6e8c-137">範例2：在遠端伺服器上執行命令</span><span class="sxs-lookup"><span data-stu-id="c6e8c-137">Example 2: Run a command on a remote server</span></span>

<span data-ttu-id="c6e8c-138">此範例會 `Get-Culture` 在 Server01 遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-138">This example runs a `Get-Culture` command on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

<span data-ttu-id="c6e8c-139">**ComputerName** 參數指定遠端電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-139">The **ComputerName** parameter specifies the name of the remote computer.</span></span> <span data-ttu-id="c6e8c-140">**Credential** 參數是用來在 Domain01\User01 的安全性內容中執行命令，這是具有執行命令之許可權的使用者。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-140">The **Credential** parameter is used to run the command in the security context of Domain01\User01, a user who has permission to run commands.</span></span> <span data-ttu-id="c6e8c-141">**ScriptBlock** 參數指定要在遠端電腦上執行的命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-141">The **ScriptBlock** parameter specifies the command to be run on the remote computer.</span></span>

<span data-ttu-id="c6e8c-142">為了回應，PowerShell 要求 User01 帳戶的密碼和驗證方法。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-142">In response, PowerShell requests the password and an authentication method for the User01 account.</span></span>
<span data-ttu-id="c6e8c-143">然後，它會在 Server01 電腦上執行命令並傳回結果。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-143">It then runs the command on the Server01 computer and returns the result.</span></span>

### <span data-ttu-id="c6e8c-144">範例3：在持續連接中執行命令</span><span class="sxs-lookup"><span data-stu-id="c6e8c-144">Example 3: Run a command in a persistent connection</span></span>

<span data-ttu-id="c6e8c-145">此範例會在 `Get-Culture` 名為 Server02 的遠端電腦上，使用持續連線在會話中執行相同的命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-145">This example runs the same `Get-Culture` command in a session, using a persistent connection, on the remote computer named Server02.</span></span>

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="c6e8c-146">此 `New-PSSession` Cmdlet 會在 Server02 遠端電腦上建立會話，並將它儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-146">The `New-PSSession` cmdlet creates a session on the Server02 remote computer and saves it in the `$s` variable.</span></span> <span data-ttu-id="c6e8c-147">一般來說，只有當您在遠端電腦上執行一連串命令時，才會建立會話。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-147">Typically, you create a session only when you run a series of commands on the remote computer.</span></span>

<span data-ttu-id="c6e8c-148">此 `Invoke-Command` Cmdlet 會 `Get-Culture` 在 Server02 上執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-148">The `Invoke-Command` cmdlet runs the `Get-Culture` command on Server02.</span></span> <span data-ttu-id="c6e8c-149">**Session** 參數會指定儲存在變數中的會話 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-149">The **Session** parameter specifies the session saved in the `$s` variable.</span></span>

<span data-ttu-id="c6e8c-150">在回應中，PowerShell 會在 Server02 電腦上的會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-150">In response, PowerShell runs the command in the session on the Server02 computer.</span></span>

### <span data-ttu-id="c6e8c-151">範例4：使用會話來執行一系列共用資料的命令</span><span class="sxs-lookup"><span data-stu-id="c6e8c-151">Example 4: Use a session to run a series of commands that share data</span></span>

<span data-ttu-id="c6e8c-152">這個範例會比較使用 **ComputerName** 和 **會話** 參數的效果 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-152">This example compares the effects of using **ComputerName** and **Session** parameters of `Invoke-Command`.</span></span> <span data-ttu-id="c6e8c-153">它示範如何使用工作階段來執行一系列共用相同資料的命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-153">It shows how to use a session to run a series of commands that share the same data.</span></span>

```powershell
Invoke-Command -ComputerName Server02 -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -ComputerName Server02 -ScriptBlock {$p.VirtualMemorySize}
$s = New-PSSession -ComputerName Server02
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -Session $s -ScriptBlock {$p.VirtualMemorySize}
```

```Output
17930240
```

<span data-ttu-id="c6e8c-154">前兩個命令使用的 **ComputerName** 參數 `Invoke-Command` ，在 Server02 遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-154">The first two commands use the **ComputerName** parameter of `Invoke-Command` to run commands on the Server02 remote computer.</span></span> <span data-ttu-id="c6e8c-155">第一個命令會使用 `Get-Process` Cmdlet 來取得遠端電腦上的 PowerShell 處理常式，並將它儲存在 `$p` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-155">The first command uses the `Get-Process` cmdlet to get the PowerShell process on the remote computer and to save it in the `$p` variable.</span></span> <span data-ttu-id="c6e8c-156">第二個命令會取得 PowerShell 處理程序的 **VirtualMemorySize** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-156">The second command gets the value of the **VirtualMemorySize** property of the PowerShell process.</span></span>

<span data-ttu-id="c6e8c-157">當您使用 **ComputerName** 參數時，PowerShell 會建立新的會話來執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-157">When you use the **ComputerName** parameter, PowerShell creates a new session to run the command.</span></span>
<span data-ttu-id="c6e8c-158">當命令完成時，會話就會關閉。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-158">The session is closed when the command completes.</span></span> <span data-ttu-id="c6e8c-159">`$p`變數是在一個連接中建立的，但不存在於為第二個命令所建立的連接中。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-159">The `$p` variable was created in one connection, but it doesn't exist in the connection created for the second command.</span></span>

<span data-ttu-id="c6e8c-160">問題的解決方式是在遠端電腦上建立持續性會話，然後在相同的會話中執行這兩個命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-160">The problem is solved by creating a persistent session on the remote computer, then running both of the commands in the same session.</span></span>

<span data-ttu-id="c6e8c-161">此 `New-PSSession` Cmdlet 會在電腦 Server02 上建立持續性會話，並將會話儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-161">The `New-PSSession` cmdlet creates a persistent session on the computer Server02 and saves the session in the `$s` variable.</span></span> <span data-ttu-id="c6e8c-162">`Invoke-Command`接下來的幾行使用 **Session** 參數在相同的會話中執行這兩個命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-162">The `Invoke-Command` lines that follow use the **Session** parameter to run both of the commands in the same session.</span></span> <span data-ttu-id="c6e8c-163">因為這兩個命令都在相同的會話中執行，所以此值會維持作用中 `$p` 狀態。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-163">Since both commands run in the same session, the `$p` value remains active.</span></span>

### <span data-ttu-id="c6e8c-164">範例5：輸入儲存在本機變數中的命令</span><span class="sxs-lookup"><span data-stu-id="c6e8c-164">Example 5: Enter a command stored in a local variable</span></span>

<span data-ttu-id="c6e8c-165">這個範例示範如何建立一個命令，該命令會以腳本區塊的形式儲存在本機變數中。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-165">This example shows how to create a command that is stored as a script block in a local variable.</span></span>
<span data-ttu-id="c6e8c-166">當腳本區塊儲存在本機變數中時，您可以將變數指定為 **ScriptBlock** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-166">When the script block is saved in a local variable, you can specify the variable as the value of the **ScriptBlock** parameter.</span></span>

```powershell
$command = { Get-EventLog -LogName "Windows PowerShell" |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

<span data-ttu-id="c6e8c-167">`$command`變數 `Get-EventLog` 會儲存格式化為腳本區塊的命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-167">The `$command` variable stores the `Get-EventLog` command that's formatted as a script block.</span></span> <span data-ttu-id="c6e8c-168">會 `Invoke-Command` 執行儲存在 `$command` S1 和 S2 遠端電腦上的命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-168">The `Invoke-Command` runs the command stored in `$command` on the S1 and S2 remote computers.</span></span>

### <span data-ttu-id="c6e8c-169">範例6：在數部電腦上執行單一命令</span><span class="sxs-lookup"><span data-stu-id="c6e8c-169">Example 6: Run a single command on several computers</span></span>

<span data-ttu-id="c6e8c-170">此範例示範如何使用 `Invoke-Command` 在多部電腦上執行單一命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-170">This example demonstrates how to use `Invoke-Command` to run a single command on multiple computers.</span></span>

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-EventLog "Windows PowerShell" }
}
Invoke-Command @parameters
```

<span data-ttu-id="c6e8c-171">**ComputerName** 參數會指定以逗號分隔的電腦名稱稱清單。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-171">The **ComputerName** parameter specifies a comma-separated list of computer names.</span></span> <span data-ttu-id="c6e8c-172">電腦的清單包含 localhost 值（代表本機電腦）。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-172">The list of computers includes the localhost value, which represents the local computer.</span></span> <span data-ttu-id="c6e8c-173">**ConfigurationName** 參數會指定替代的會話設定。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-173">The **ConfigurationName** parameter specifies an alternate session configuration.</span></span> <span data-ttu-id="c6e8c-174">**ScriptBlock** 參數會執行 `Get-EventLog` 以取得每部電腦的 Windows PowerShell 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-174">The **ScriptBlock** parameter runs `Get-EventLog` to get the Windows PowerShell event logs from each computer.</span></span>

### <span data-ttu-id="c6e8c-175">範例7：在多部電腦上取得主機程式的版本</span><span class="sxs-lookup"><span data-stu-id="c6e8c-175">Example 7: Get the version of the host program on multiple computers</span></span>

<span data-ttu-id="c6e8c-176">此範例會取得在200遠端電腦上執行之 PowerShell 主機程式的版本。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-176">This example gets the version of the PowerShell host program running on 200 remote computers.</span></span>

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

<span data-ttu-id="c6e8c-177">由於只有一個命令執行，因此您不需要為每部電腦建立持續連線。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-177">Because only one command is run, you don't have to create persistent connections to each of the computers.</span></span> <span data-ttu-id="c6e8c-178">此命令是改用 **ComputerName** 參數來指出電腦。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-178">Instead, the command uses the **ComputerName** parameter to indicate the computers.</span></span> <span data-ttu-id="c6e8c-179">為了指定電腦，它會使用 `Get-Content` Cmdlet 來取得 Machine.txt 檔案的內容，也就是電腦名稱稱的檔案。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-179">To specify the computers, it uses the `Get-Content` cmdlet to get the contents of the Machine.txt file, a file of computer names.</span></span>

<span data-ttu-id="c6e8c-180">此 `Invoke-Command` Cmdlet 會 `Get-Host` 在遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-180">The `Invoke-Command` cmdlet runs a `Get-Host` command on the remote computers.</span></span> <span data-ttu-id="c6e8c-181">它會使用點標記法來取得 PowerShell 主機的 **Version** 屬性。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-181">It uses dot notation to get the **Version** property of the PowerShell host.</span></span>

<span data-ttu-id="c6e8c-182">這些命令會一次執行一個。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-182">These commands run one at a time.</span></span> <span data-ttu-id="c6e8c-183">當命令完成時，所有電腦的命令輸出都會儲存在 `$version` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-183">When the commands complete, the output of the commands from all of the computers is saved in the `$version` variable.</span></span> <span data-ttu-id="c6e8c-184">輸出會包括資料的來源電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-184">The output includes the name of the computer from which the data originated.</span></span>

### <span data-ttu-id="c6e8c-185">範例8：在數部遠端電腦上執行背景工作</span><span class="sxs-lookup"><span data-stu-id="c6e8c-185">Example 8: Run a background job on several remote computers</span></span>

<span data-ttu-id="c6e8c-186">此範例會在兩部遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-186">This example runs a command on two remote computers.</span></span> <span data-ttu-id="c6e8c-187">此 `Invoke-Command` 命令會使用 **AsJob** 參數，讓命令以背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-187">The `Invoke-Command` command uses the **AsJob** parameter so that the command runs as a background job.</span></span> <span data-ttu-id="c6e8c-188">這些命令會在遠端電腦上執行，但是該作業存在於本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-188">The commands run on the remote computers, but the job exists on the local computer.</span></span> <span data-ttu-id="c6e8c-189">結果會傳輸到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-189">The results are transmitted to the local computer.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
Invoke-Command -Session $s -ScriptBlock {Get-EventLog system} -AsJob
```

```Output
Id   Name    State      HasMoreData   Location           Command
---  ----    -----      -----         -----------        ---------------
1    Job1    Running    True          Server01,Server02  Get-EventLog system
```

```powershell
$j = Get-Job
$j | Format-List -Property *
```

```Output
HasMoreData   : True
StatusMessage :
Location      : Server01,Server02
Command       : Get-EventLog system
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : e124bb59-8cb2-498b-a0d2-2e07d4e030ca
Id            : 1
Name          : Job1
ChildJobs     : {Job2, Job3}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
$results = $j | Receive-Job
```

<span data-ttu-id="c6e8c-190">此 `New-PSSession` Cmdlet 會在 Server01 和 Server02 遠端電腦上建立會話。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-190">The `New-PSSession` cmdlet creates sessions on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="c6e8c-191">此 `Invoke-Command` Cmdlet 會在每個會話中執行背景工作。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-191">The `Invoke-Command` cmdlet runs a background job in each of the sessions.</span></span> <span data-ttu-id="c6e8c-192">此命令使用 **AsJob** 參數將命令當作背景工作來執行。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-192">The command uses the **AsJob** parameter to run the command as a background job.</span></span> <span data-ttu-id="c6e8c-193">這個命令會傳回一個工作物件，其中包含兩個子工作物件，分別用於在兩部遠端電腦上執行的每個工作。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-193">This command returns a job object that contains two child job objects, one for each of the jobs run on the two remote computers.</span></span>

<span data-ttu-id="c6e8c-194">此 `Get-Job` 命令會將工作物件儲存在 `$j` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-194">The `Get-Job` command saves the job object in the `$j` variable.</span></span> <span data-ttu-id="c6e8c-195">然後，會使用管線 `$j` 將變數輸送到 `Format-List` Cmdlet，以顯示清單中工作物件的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-195">The `$j` variable is then piped to the `Format-List` cmdlet to display all properties of the job object in a list.</span></span> <span data-ttu-id="c6e8c-196">最後一個命令會取得工作的結果。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-196">The last command gets the results of the jobs.</span></span> <span data-ttu-id="c6e8c-197">它會以管線將工作物件傳送 `$j` 至 `Receive-Job` Cmdlet，並將結果儲存在 `$results` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-197">It pipes the job object in `$j` to the `Receive-Job` cmdlet and stores the results in the `$results` variable.</span></span>

### <span data-ttu-id="c6e8c-198">範例9：在遠端電腦上執行的命令中包含本機變數</span><span class="sxs-lookup"><span data-stu-id="c6e8c-198">Example 9: Include local variables in a command run on a remote computer</span></span>

<span data-ttu-id="c6e8c-199">這個範例示範如何將區域變數的值包含在遠端電腦上執行的命令中。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-199">This example shows how to include the values of local variables in a command run on a remote computer.</span></span> <span data-ttu-id="c6e8c-200">此命令會使用 `Using` 範圍修飾符來識別遠端命令中的本機變數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-200">The command uses the `Using` scope modifier to identify a local variable in a remote command.</span></span> <span data-ttu-id="c6e8c-201">預設會假設所有變數都已在遠端工作階段中定義。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-201">By default, all variables are assumed to be defined in the remote session.</span></span> <span data-ttu-id="c6e8c-202">`Using`範圍修飾詞是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-202">The `Using` scope modifier was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="c6e8c-203">如需範圍修飾符的詳細資訊 `Using` ，請參閱 [about_Remote_Variables](./About/about_Remote_Variables.md) 和 [about_Scopes](./about/about_scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-203">For more information about the `Using` scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md) and [about_Scopes](./about/about_scopes.md).</span></span>

```powershell
$Log = "Windows PowerShell"
Invoke-Command -ComputerName Server01 -ScriptBlock { Get-EventLog -LogName $Using:Log -Newest 10 }
```

<span data-ttu-id="c6e8c-204">`$Log`變數會儲存事件記錄檔的名稱，Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-204">The `$Log` variable stores the name of the event log, Windows PowerShell.</span></span> <span data-ttu-id="c6e8c-205">`Invoke-Command`Cmdlet 會 `Get-EventLog` 在 Server01 上執行，以從事件記錄檔取得十個最新的事件。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-205">The `Invoke-Command` cmdlet runs `Get-EventLog` on Server01 to get the ten newest events from the event log.</span></span> <span data-ttu-id="c6e8c-206">**LogName** 參數的值為 `$Log` 變數，此變數的前面會加上 `Using` 範圍修飾符，以指出它是在本機會話中建立，而不是在遠端會話中建立的。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-206">The value of the **LogName** parameter is the `$Log` variable, which is prefixed by the `Using` scope modifier to indicate that it was created in the local session, not in the remote session.</span></span>

### <span data-ttu-id="c6e8c-207">範例10：隱藏電腦名稱稱</span><span class="sxs-lookup"><span data-stu-id="c6e8c-207">Example 10: Hide the computer name</span></span>

<span data-ttu-id="c6e8c-208">此範例顯示使用的 **HideComputerName** 參數的效果 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-208">This example shows the effect of using the **HideComputerName** parameter of `Invoke-Command`.</span></span>
<span data-ttu-id="c6e8c-209">**HideComputerName** 不會變更此 Cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-209">**HideComputerName** doesn't change the object that this cmdlet returns.</span></span> <span data-ttu-id="c6e8c-210">它只會變更顯示。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-210">It changes only the display.</span></span> <span data-ttu-id="c6e8c-211">您仍然可以使用 **Format** Cmdlet 來顯示任何受影響物件的 **PsComputerName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-211">You can still use the **Format** cmdlets to display the **PsComputerName** property of any of the affected objects.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell}
```

```Output
PSComputerName    Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
--------------    -------  ------    -----      ----- -----   ------     --   -----------
S1                575      15        45100      40988   200     4.68     1392 PowerShell
S2                777      14        35100      30988   150     3.68     67   PowerShell
```

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell} -HideComputerName
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
575      15        45100      40988   200     4.68     1392 PowerShell
777      14        35100      30988   150     3.68     67   PowerShell
```

<span data-ttu-id="c6e8c-212">前兩個命令會用 `Invoke-Command` 來執行 `Get-Process` PowerShell 處理常式的命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-212">The first two commands use `Invoke-Command` to run a `Get-Process` command for the PowerShell process.</span></span> <span data-ttu-id="c6e8c-213">第一個命令的輸出包括 **PsComputerName** 屬性，這包含命令執行所在的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-213">The output of the first command includes the **PsComputerName** property, which contains the name of the computer on which the command ran.</span></span> <span data-ttu-id="c6e8c-214">第二個命令的輸出（使用 **HideComputerName** ）不包含 **PsComputerName** 資料行。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-214">The output of the second command, which uses **HideComputerName** , doesn't include the **PsComputerName** column.</span></span>

### <span data-ttu-id="c6e8c-215">範例11：在腳本區塊中使用 Param 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c6e8c-215">Example 11: Use the Param keyword in a script block</span></span>

<span data-ttu-id="c6e8c-216">`Param`關鍵字和 **ArgumentList** 參數是用來將變數值傳遞至腳本區塊中的具名引數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-216">The `Param` keyword and the **ArgumentList** parameter are used to pass variable values to named parameters in a script block.</span></span> <span data-ttu-id="c6e8c-217">此範例會顯示以字母開頭 `a` 且副檔名為的檔案名 `.pdf` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-217">This example displays filenames that begin with the letter `a` and have the `.pdf` extension.</span></span>

<span data-ttu-id="c6e8c-218">如需關鍵字的詳細資訊 `Param` ，請參閱 [about_Language_Keywords](./about/about_language_keywords.md#param)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-218">For more information about the `Param` keyword, see [about_Language_Keywords](./about/about_language_keywords.md#param).</span></span>

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Param ($param1,$param2) Get-ChildItem -Name $param1 -Include $param2 }
    ArgumentList = "a*", "*.pdf"
}
Invoke-Command @parameters
```

```Output
aa.pdf
ab.pdf
ac.pdf
az.pdf
```

<span data-ttu-id="c6e8c-219">`Invoke-Command` 使用定義兩個變數的 **ScriptBlock** 參數： `$param1` 和 `$param2` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-219">`Invoke-Command` uses the **ScriptBlock** parameter that defines two variables, `$param1` and `$param2`.</span></span> <span data-ttu-id="c6e8c-220">`Get-ChildItem` 使用具名引數、 **名稱** 和 **包含** 變數名稱。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-220">`Get-ChildItem` uses the named parameters, **Name** and **Include** with the variable names.</span></span> <span data-ttu-id="c6e8c-221">**ArgumentList** 會將這些值傳遞給變數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-221">The **ArgumentList** passes the values to the variables.</span></span>

### <span data-ttu-id="c6e8c-222">範例12：在腳本區塊中使用 $args 自動變數</span><span class="sxs-lookup"><span data-stu-id="c6e8c-222">Example 12: Use the $args automatic variable in a script block</span></span>

<span data-ttu-id="c6e8c-223">`$args`自動變數和 **ArgumentList** 參數是用來將陣列值傳遞至腳本區塊中的參數位置。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-223">The `$args` automatic variable and the **ArgumentList** parameter are used to pass array values to parameter positions in a script block.</span></span> <span data-ttu-id="c6e8c-224">此範例會顯示伺服器的目錄內容 `.txt` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-224">This example displays a server's directory contents of `.txt` files.</span></span> <span data-ttu-id="c6e8c-225">`Get-ChildItem`**路徑** 參數為位置0，而 **篩選** 參數為位置</span><span class="sxs-lookup"><span data-stu-id="c6e8c-225">The `Get-ChildItem` **Path** parameter is position 0 and the **Filter** parameter is position</span></span>
1.

<span data-ttu-id="c6e8c-226">如需變數的詳細資訊 `$args` ，請參閱 [about_Automatic_Variables](./about/about_automatic_variables.md#args)</span><span class="sxs-lookup"><span data-stu-id="c6e8c-226">For more information about the `$args` variable, see [about_Automatic_Variables](./about/about_automatic_variables.md#args)</span></span>

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Get-ChildItem $args[0] $args[1] }
    ArgumentList = "C:\Test", "*.txt*"
}
Invoke-Command @parameters
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           6/12/2019    15:15            128 alog.txt
-a---           7/27/2019    15:16            256 blog.txt
-a---           9/28/2019    17:10             64 zlog.txt
```

<span data-ttu-id="c6e8c-227">`Invoke-Command` 使用 **ScriptBlock** 參數，並 `Get-ChildItem` 指定 `$args[0]` 和 `$args[1]` 陣列值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-227">`Invoke-Command` uses a **ScriptBlock** parameter and `Get-ChildItem` specifies the `$args[0]` and `$args[1]` array values.</span></span> <span data-ttu-id="c6e8c-228">**ArgumentList** 會將 `$args` 陣列值傳遞給 `Get-ChildItem` **Path** 和 **Filter** 的參數位置。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-228">The **ArgumentList** passes the `$args` array values to the `Get-ChildItem` parameter positions for **Path** and **Filter** .</span></span>

### <span data-ttu-id="c6e8c-229">範例13：在文字檔中列出的所有電腦上執行腳本</span><span class="sxs-lookup"><span data-stu-id="c6e8c-229">Example 13: Run a script on all the computers listed in a text file</span></span>

<span data-ttu-id="c6e8c-230">這個範例會使用 `Invoke-Command` Cmdlet，在檔案 `Sample.ps1` 中列出的所有電腦上執行腳本 `Servers.txt` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-230">This example uses the `Invoke-Command` cmdlet to run the `Sample.ps1` script on all the computers listed in the `Servers.txt` file.</span></span> <span data-ttu-id="c6e8c-231">此命令使用 **FilePath** 參數來指定指令檔。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-231">The command uses the **FilePath** parameter to specify the script file.</span></span> <span data-ttu-id="c6e8c-232">此命令可讓您在遠端電腦上執行腳本，即使遠端電腦無法存取腳本檔也是如此。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-232">This command lets you run the script on the remote computers, even if the script file isn't accessible to the remote computers.</span></span>

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

<span data-ttu-id="c6e8c-233">當您提交命令時，會將檔案的內容 `Sample.ps1` 複製到腳本區塊中，而腳本區塊則會在每部遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-233">When you submit the command, the content of the `Sample.ps1` file is copied into a script block and the script block is run on each of the remote computers.</span></span> <span data-ttu-id="c6e8c-234">這個程序相當於使用 **ScriptBlock** 參數來送出指令碼的內容。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-234">This procedure is equivalent to using the **ScriptBlock** parameter to submit the contents of the script.</span></span>

### <span data-ttu-id="c6e8c-235">範例14：使用 URI 在遠端電腦上執行命令</span><span class="sxs-lookup"><span data-stu-id="c6e8c-235">Example 14: Run a command on a remote computer using a URI</span></span>

<span data-ttu-id="c6e8c-236">此範例示範如何在遠端電腦上執行命令，該遠端電腦的 (URI) 的統一資源識別元。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-236">This example shows how to run a command on a remote computer that's identified by a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="c6e8c-237">這個特定的範例會 `Set-Mailbox` 在遠端 Exchange 伺服器上執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-237">This particular example runs a `Set-Mailbox` command on a remote Exchange server.</span></span>

```powershell
$LiveCred = Get-Credential
$parameters = @{
  ConfigurationName = 'Microsoft.Exchange'
  ConnectionUri = 'https://ps.exchangelabs.com/PowerShell'
  Credential = $LiveCred
  Authentication = 'Basic'
  ScriptBlock = {Set-Mailbox Dan -DisplayName "Dan Park"}
}
Invoke-Command @parameters
```

<span data-ttu-id="c6e8c-238">第一行使用 Cmdlet 將 `Get-Credential` Windows LIVE ID 認證儲存在 `$LiveCred` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-238">The first line uses the `Get-Credential` cmdlet to store Windows Live ID credentials in the `$LiveCred` variable.</span></span> <span data-ttu-id="c6e8c-239">PowerShell 會提示使用者輸入 Windows Live ID 認證。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-239">PowerShell prompts the user to enter Windows Live ID credentials.</span></span>

<span data-ttu-id="c6e8c-240">`$parameters`變數是包含要傳遞給 Cmdlet 之參數的雜湊表 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-240">The `$parameters` variable is a hash table containing the parameters to be passed to the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="c6e8c-241">此 `Invoke-Command` Cmdlet 會 `Set-Mailbox` 使用 **Microsoft. Exchange** 會話設定來執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-241">The `Invoke-Command` cmdlet runs a `Set-Mailbox` command using the **Microsoft.Exchange** session configuration.</span></span> <span data-ttu-id="c6e8c-242">**ConnectionURI** 參數指定 Exchange 伺服器端點的 URL。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-242">The **ConnectionURI** parameter specifies the URL of the Exchange server endpoint.</span></span> <span data-ttu-id="c6e8c-243">**Credential** 參數會指定儲存在變數中的認證 `$LiveCred` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-243">The **Credential** parameter specifies the credentials stored in the `$LiveCred` variable.</span></span> <span data-ttu-id="c6e8c-244">**AuthenticationMechanism** 參數指定使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-244">The **AuthenticationMechanism** parameter specifies the use of basic authentication.</span></span> <span data-ttu-id="c6e8c-245">**ScriptBlock** 參數指定包含命令的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-245">The **ScriptBlock** parameter specifies a script block that contains the command.</span></span>

### <span data-ttu-id="c6e8c-246">範例15：使用會話選項</span><span class="sxs-lookup"><span data-stu-id="c6e8c-246">Example 15: Use a session option</span></span>

<span data-ttu-id="c6e8c-247">此範例顯示如何建立和使用 **SessionOption** 參數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-247">This example shows how to create and use a **SessionOption** parameter.</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

<span data-ttu-id="c6e8c-248">此 `New-PSSessionOption` Cmdlet 會建立會話選項物件，此物件會導致遠端端點在評估連入的 HTTPS 連線時，不會驗證憑證授權單位單位、標準名稱和撤銷清單。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-248">The `New-PSSessionOption` cmdlet creates a session option object that causes the remote end not to verify the Certificate Authority, Canonical Name, and Revocation Lists while evaluating the incoming HTTPS connection.</span></span> <span data-ttu-id="c6e8c-249">**SessionOption** 物件會儲存在變數中 `$so` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-249">The **SessionOption** object is saved in the `$so` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e8c-250">停用這些檢查對於疑難排解很方便，但顯然並不安全。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-250">Disabling these checks is convenient for troubleshooting, but obviously not secure.</span></span>

<span data-ttu-id="c6e8c-251">`Invoke-Command`Cmdlet 會 `Get-HotFix` 從遠端執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-251">The `Invoke-Command` cmdlet runs a `Get-HotFix` command remotely.</span></span> <span data-ttu-id="c6e8c-252">提供變數給 **SessionOption** 參數 `$so` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-252">The **SessionOption** parameter is given the `$so` variable.</span></span>

### <span data-ttu-id="c6e8c-253">範例16：管理遠端命令中的 URI 重新導向</span><span class="sxs-lookup"><span data-stu-id="c6e8c-253">Example 16: Manage URI redirection in a remote command</span></span>

<span data-ttu-id="c6e8c-254">此範例示範如何使用 **AllowRedirection** 和 **SessionOption** 參數來管理遠端命令中的 URI 重新導向。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-254">This example shows how to use the **AllowRedirection** and **SessionOption** parameters to manage URI redirection in a remote command.</span></span>

```powershell
$max = New-PSSessionOption -MaximumRedirection 1
$parameters = @{
  ConnectionUri = "https://ps.exchangelabs.com/PowerShell"
  ScriptBlock = { Get-Mailbox dan }
  AllowRedirection = $true
  SessionOption = $max
}
Invoke-Command @parameters
```

<span data-ttu-id="c6e8c-255">此 `New-PSSessionOption` Cmdlet 會建立儲存在變數中的 **PSSessionOption** 物件 `$max` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-255">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object that is saved in the `$max` variable.</span></span> <span data-ttu-id="c6e8c-256">此命令使用 **MaximumRedirection** 參數將 **PSSessionOption** 物件的 **MaximumConnectionRedirectionCount** 屬性設定為 1。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-256">The command uses the **MaximumRedirection** parameter to set the **MaximumConnectionRedirectionCount** property of the **PSSessionOption** object to 1.</span></span>

<span data-ttu-id="c6e8c-257">此 `Invoke-Command` Cmdlet 會 `Get-Mailbox` 在遠端 Microsoft Exchange 伺服器上執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-257">The `Invoke-Command` cmdlet runs a `Get-Mailbox` command on a remote Microsoft Exchange Server.</span></span> <span data-ttu-id="c6e8c-258">**AllowRedirection** 參數提供明確的許可權，以將連接重新導向至替代端點。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-258">The **AllowRedirection** parameter provides explicit permission to redirect the connection to an alternate endpoint.</span></span> <span data-ttu-id="c6e8c-259">**SessionOption** 參數會使用儲存在變數中的會話物件 `$max` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-259">The **SessionOption** parameter uses the session object stored in the `$max` variable.</span></span>

<span data-ttu-id="c6e8c-260">如此一來，如果 **ConnectionURI** 所指定的遠端電腦傳回重新導向訊息，則 PowerShell 會將連接重新導向，但是如果新的目的地傳回另一個重新導向訊息，則會超過重新導向計數值1，並傳回 `Invoke-Command` 非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-260">As a result, if the remote computer specified by **ConnectionURI** returns a redirection message, PowerShell redirects the connection, but if the new destination returns another redirection message, the redirection count value of 1 is exceeded, and `Invoke-Command` returns a non-terminating error.</span></span>

### <span data-ttu-id="c6e8c-261">範例17：在遠端會話中存取網路共用</span><span class="sxs-lookup"><span data-stu-id="c6e8c-261">Example 17: Access a network share in a remote session</span></span>

<span data-ttu-id="c6e8c-262">此範例說明如何從遠端會話存取網路共用。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-262">This example shows how to access a network share from a remote session.</span></span> <span data-ttu-id="c6e8c-263">使用三部電腦來示範範例。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-263">Three computers are used to demonstrate the example.</span></span> <span data-ttu-id="c6e8c-264">Server01 是本機電腦、Server02 是遠端電腦，而 Net03 則包含網路共用。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-264">Server01 is the local computer, Server02 is the remote computer, and Net03 contains the network share.</span></span> <span data-ttu-id="c6e8c-265">Server01 會連線到 Server02，然後 Server02 會執行第二個躍點來 Net03 來存取網路共用。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-265">Server01 connects to Server02, and then Server02 does a second hop to Net03 to access the network share.</span></span> <span data-ttu-id="c6e8c-266">如需 PowerShell 遠端功能如何支援電腦之間的躍點的詳細資訊，請參閱 [在 Powershell 遠端中進行第二個躍點](/powershell/scripting/learn/remoting/ps-remoting-second-hop)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-266">For more information about how PowerShell Remoting supports hops between computers, see [Making the second hop in PowerShell Remoting](/powershell/scripting/learn/remoting/ps-remoting-second-hop).</span></span>

<span data-ttu-id="c6e8c-267">在本機電腦的用戶端設定中，以及遠端電腦上的服務設定中，已啟用必要的認證安全性支援提供者 (CredSSP) 委派。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-267">The required Credential Security Support Provider (CredSSP) delegation is enabled in the client settings on the local computer, and in the service settings on the remote computer.</span></span> <span data-ttu-id="c6e8c-268">若要執行此範例中的命令，您必須是本機電腦和遠端電腦上的 **Administrators** 群組成員。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-268">To run the commands in this example, you must be a member of the **Administrators** group on the local computer and the remote computer.</span></span>

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer Server02
$s = New-PSSession Server02
Invoke-Command -Session $s -ScriptBlock {Enable-WSManCredSSP -Role Server -Force}
$parameters = @{
  Session = $s
  ScriptBlock = { Get-Item \\Net03\Scripts\LogFiles.ps1 }
  Authentication = "CredSSP"
  Credential = "Domain01\Admin01"
}
Invoke-Command @parameters
```

<span data-ttu-id="c6e8c-269">此 `Enable-WSManCredSSP` Cmdlet 會啟用從 Server01 本機電腦至 Server02 遠端電腦的 CredSSP 委派。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-269">The `Enable-WSManCredSSP` cmdlet enables CredSSP delegation from the Server01 local computer to the Server02 remote computer.</span></span> <span data-ttu-id="c6e8c-270">**Role** 參數會指定 **用戶端** ，以在本機電腦上設定 CredSSP 用戶端設定。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-270">The **Role** parameter specifies **Client** to configure the CredSSP client setting on the local computer.</span></span>

<span data-ttu-id="c6e8c-271">`New-PSSession` 建立 Server02 的 **PSSession** 物件，並將物件儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-271">`New-PSSession` creates a **PSSession** object for Server02 and stores the object in the `$s` variable.</span></span>

<span data-ttu-id="c6e8c-272">此 `Invoke-Command` Cmdlet 會使用 `$s` 變數來連線到遠端電腦 Server02。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-272">The `Invoke-Command` cmdlet uses the `$s` variable to connect to the remote computer, Server02.</span></span> <span data-ttu-id="c6e8c-273">**ScriptBlock** 參數會 `Enable-WSManCredSSP` 在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-273">The **ScriptBlock** parameter runs `Enable-WSManCredSSP` on the remote computer.</span></span> <span data-ttu-id="c6e8c-274">**Role** 參數指定要在遠端電腦上設定 CredSSP 伺服器設定的 **伺服器** 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-274">The **Role** parameter specifies **Server** to configure the CredSSP server setting on the remote computer.</span></span>

<span data-ttu-id="c6e8c-275">`$parameters`變數包含用來連接到網路共用的參數值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-275">The `$parameters` variable contains the parameter values to connect to the network share.</span></span> <span data-ttu-id="c6e8c-276">Cmdlet 會在 `Invoke-Command` `Get-Item` 的會話中執行命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-276">The `Invoke-Command` cmdlet runs a `Get-Item` command in the session in `$s`.</span></span> <span data-ttu-id="c6e8c-277">此命令會從 `\\Net03\Scripts` 網路共用取得腳本。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-277">This command gets a script from the `\\Net03\Scripts` network share.</span></span> <span data-ttu-id="c6e8c-278">此命令會使用具有 **CredSSP** 值的 **驗證** 參數，並使用 **Domain01\Admin01** 的值來使用 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-278">The command uses the **Authentication** parameter with a value of **CredSSP** and the **Credential** parameter with a value of **Domain01\Admin01** .</span></span>

### <span data-ttu-id="c6e8c-279">範例18：在許多遠端電腦上啟動腳本</span><span class="sxs-lookup"><span data-stu-id="c6e8c-279">Example 18: Start scripts on many remote computers</span></span>

<span data-ttu-id="c6e8c-280">此範例會在一百部以上的電腦上執行腳本。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-280">This example runs a script on more than a hundred computers.</span></span> <span data-ttu-id="c6e8c-281">為了將對本機電腦的影響降到最低，它會連線到每一部電腦、啟動指令碼，然後再與每一部電腦中斷連線。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-281">To minimize the impact on the local computer, it connects to each computer, starts the script, and then disconnects from each computer.</span></span>
<span data-ttu-id="c6e8c-282">指令碼會繼續在中斷連線的工作階段中執行。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-282">The script continues to run in the disconnected sessions.</span></span>

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

<span data-ttu-id="c6e8c-283">命令使用 `Invoke-Command` 來執行腳本。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-283">The command uses `Invoke-Command` to run the script.</span></span> <span data-ttu-id="c6e8c-284">**ComputerName** 參數的值是 `Get-Content` 從文字檔取得遠端電腦名稱稱的命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-284">The value of the **ComputerName** parameter is a `Get-Content` command that gets the names of the remote computers from a text file.</span></span> <span data-ttu-id="c6e8c-285">**InDisconnectedSession** 參數會在一啟動命令時就將工作階段中斷連線。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-285">The **InDisconnectedSession** parameter disconnects the sessions as soon as it starts the command.</span></span> <span data-ttu-id="c6e8c-286">**FilePath** 參數的值是 `Invoke-Command` 在每部電腦上執行的腳本。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-286">The value of the **FilePath** parameter is the script that `Invoke-Command` runs on each computer.</span></span>

<span data-ttu-id="c6e8c-287">**SessionOption** 的值是雜湊表。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-287">The value of **SessionOption** is a hash table.</span></span> <span data-ttu-id="c6e8c-288">**OutputBufferingMode** 值設定為 **Drop** ，且 **IdleTimeout** 值設定為 **43200000** 毫秒 (12 小時) 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-288">The **OutputBufferingMode** value is set to **Drop** and the **IdleTimeout** value is set to **43200000** milliseconds (12 hours).</span></span>

<span data-ttu-id="c6e8c-289">若要取得在已中斷連線的會話中執行的命令和腳本結果，請使用 `Receive-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-289">To get the results of commands and scripts that run in disconnected sessions, use the `Receive-PSSession` cmdlet.</span></span>

## <span data-ttu-id="c6e8c-290">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c6e8c-290">PARAMETERS</span></span>

### <span data-ttu-id="c6e8c-291">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="c6e8c-291">-AllowRedirection</span></span>

<span data-ttu-id="c6e8c-292">允許重新導向此連線至替代「統一資源識別項 (URI)」。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-292">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="c6e8c-293">使用 **ConnectionURI** 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-293">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="c6e8c-294">根據預設，PowerShell 不會重新導向連線，但是您可以使用此參數允許它重新導向連接。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-294">By default, PowerShell doesn't redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="c6e8c-295">您也可以變更 **MaximumConnectionRedirectionCount** 工作階段選項值，限制連線重新導向的次數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-295">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="c6e8c-296">使用 Cmdlet 的 **MaximumRedirection** 參數， `New-PSSessionOption` 或設定喜好設定變數的 **MaximumConnectionRedirectionCount** 屬性 `$PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-296">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="c6e8c-297">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-297">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-298">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="c6e8c-298">-ApplicationName</span></span>

<span data-ttu-id="c6e8c-299">指定連線 URI 的應用程式名稱區段。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-299">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="c6e8c-300">當您未在命令中使用 **ConnectionURI** 參數時，請使用此參數來指定應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-300">Use this parameter to specify the application name when you aren't using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="c6e8c-301">預設值是 `$PSSessionApplicationName` 本機電腦上喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-301">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="c6e8c-302">如果未定義此喜好設定變數，則預設值為 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-302">If this preference variable isn't defined, the default value is WSMAN.</span></span> <span data-ttu-id="c6e8c-303">這個值適用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-303">This value is appropriate for most uses.</span></span> <span data-ttu-id="c6e8c-304">如需詳細資訊，請參閱 [about_Preference_Variables](./About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-304">For more information, see [about_Preference_Variables](./About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="c6e8c-305">WinRM 服務會使用應用程式名稱來選取要用來為連線要求提供服務的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-305">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="c6e8c-306">此參數的值應該符合遠端電腦上接聽程式之 **URLPrefix** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-306">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: $PSSessionApplicationName if set on the local computer, otherwise WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-307">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="c6e8c-307">-ArgumentList</span></span>

<span data-ttu-id="c6e8c-308">提供命令中區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-308">Supplies the values of local variables in the command.</span></span> <span data-ttu-id="c6e8c-309">在遠端電腦上執行命令之前，會先以這些值取代命令中的變數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-309">The variables in the command are replaced by these values before the command is run on the remote computer.</span></span> <span data-ttu-id="c6e8c-310">以逗號分隔的清單方式輸入值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-310">Enter the values in a comma-separated list.</span></span> <span data-ttu-id="c6e8c-311">值會依照其列出的順序與變數相關聯。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-311">Values are associated with variables in the order that they're listed.</span></span> <span data-ttu-id="c6e8c-312">**ArgumentList** 的別名是 Args。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-312">The alias for **ArgumentList** is Args.</span></span>

<span data-ttu-id="c6e8c-313">**ArgumentList** 參數中的值可以是實際值（例如1024），也可以是區域變數（例如）的參考 `$max` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-313">The values in the **ArgumentList** parameter can be actual values, such as 1024, or they can be references to local variables, such as `$max`.</span></span>

<span data-ttu-id="c6e8c-314">若要在命令中使用區域變數，請使用下列命令格式：</span><span class="sxs-lookup"><span data-stu-id="c6e8c-314">To use local variables in a command, use the following command format:</span></span>

<span data-ttu-id="c6e8c-315">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` -或- `<local-variable>`</span><span class="sxs-lookup"><span data-stu-id="c6e8c-315">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` -or- `<local-variable>`</span></span>

<span data-ttu-id="c6e8c-316">**Param** 關鍵字會列出命令中使用的本機變數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-316">The **param** keyword lists the local variables that are used in the command.</span></span> <span data-ttu-id="c6e8c-317">**ArgumentList** 會依列出的順序提供變數的值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-317">**ArgumentList** supplies the values of the variables, in the order that they're listed.</span></span> <span data-ttu-id="c6e8c-318">如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-318">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-319">-AsJob</span><span class="sxs-lookup"><span data-stu-id="c6e8c-319">-AsJob</span></span>

<span data-ttu-id="c6e8c-320">指出此 Cmdlet 會在遠端電腦上以背景工作的方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-320">Indicates that this cmdlet runs the command as a background job on a remote computer.</span></span> <span data-ttu-id="c6e8c-321">您可以使用此參數執行需要很長時間才能完成的命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-321">Use this parameter to run commands that take an extensive time to finish.</span></span>

<span data-ttu-id="c6e8c-322">當您使用 **AsJob** 參數時，此命令會傳回代表工作的物件，然後顯示命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-322">When you use the **AsJob** parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span> <span data-ttu-id="c6e8c-323">工作完成後，您可以繼續在工作階段中工作。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-323">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="c6e8c-324">若要管理工作，請使用 `*-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-324">To manage the job, use the `*-Job` cmdlets.</span></span> <span data-ttu-id="c6e8c-325">若要取得工作結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-325">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="c6e8c-326">**AsJob** 參數類似于使用 `Invoke-Command` Cmdlet `Start-Job` 從遠端執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-326">The **AsJob** parameter resembles using the `Invoke-Command` cmdlet to run a `Start-Job` cmdlet remotely.</span></span> <span data-ttu-id="c6e8c-327">不過，使用 **AsJob** 時，會在本機電腦上建立作業，即使是在遠端電腦上執行作業也一樣。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-327">However, with **AsJob** , the job is created on the local computer, even though the job runs on a remote computer.</span></span> <span data-ttu-id="c6e8c-328">遠端作業的結果會自動傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-328">The results of the remote job are automatically returned to the local computer.</span></span>

<span data-ttu-id="c6e8c-329">如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](About/about_Jobs.md) 和 [about_Remote_Jobs](About/about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-329">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-330">-Authentication</span><span class="sxs-lookup"><span data-stu-id="c6e8c-330">-Authentication</span></span>

<span data-ttu-id="c6e8c-331">指定用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-331">Specifies the mechanism that's used to authenticate the user's credentials.</span></span> <span data-ttu-id="c6e8c-332">CredSSP 驗證僅適用于 Windows Vista、Windows Server 2008 和更新版本的 Windows 作業系統。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-332">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="c6e8c-333">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="c6e8c-333">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c6e8c-334">預設</span><span class="sxs-lookup"><span data-stu-id="c6e8c-334">Default</span></span>
- <span data-ttu-id="c6e8c-335">基本</span><span class="sxs-lookup"><span data-stu-id="c6e8c-335">Basic</span></span>
- <span data-ttu-id="c6e8c-336">Credssp</span><span class="sxs-lookup"><span data-stu-id="c6e8c-336">Credssp</span></span>
- <span data-ttu-id="c6e8c-337">Digest</span><span class="sxs-lookup"><span data-stu-id="c6e8c-337">Digest</span></span>
- <span data-ttu-id="c6e8c-338">Kerberos</span><span class="sxs-lookup"><span data-stu-id="c6e8c-338">Kerberos</span></span>
- <span data-ttu-id="c6e8c-339">交涉</span><span class="sxs-lookup"><span data-stu-id="c6e8c-339">Negotiate</span></span>
- <span data-ttu-id="c6e8c-340">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="c6e8c-340">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="c6e8c-341">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-341">The default value is Default.</span></span>

<span data-ttu-id="c6e8c-342">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-342">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="c6e8c-343">使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-343">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="c6e8c-344">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-344">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="c6e8c-345">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-345">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span> <span data-ttu-id="c6e8c-346">如需詳細資訊，請參閱 [認證安全性支援提供者](/windows/win32/secauthn/credential-security-support-provider)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-346">For more information, see [Credential Security Support Provider](/windows/win32/secauthn/credential-security-support-provider).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-347">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="c6e8c-347">-CertificateThumbprint</span></span>

<span data-ttu-id="c6e8c-348">指定具有連線至已中斷連線工作階段權限之使用者帳戶的數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-348">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="c6e8c-349">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-349">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="c6e8c-350">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-350">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="c6e8c-351">這些帳戶只能對應至本機使用者帳戶，而且無法使用網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-351">They can be mapped only to local user accounts and they don't work with domain accounts.</span></span>

<span data-ttu-id="c6e8c-352">若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` PowerShell Cert：磁片磁碟機中的或命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-352">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="c6e8c-353">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="c6e8c-353">-ComputerName</span></span>

<span data-ttu-id="c6e8c-354">指定命令執行所在的電腦。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-354">Specifies the computers on which the command runs.</span></span> <span data-ttu-id="c6e8c-355">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-355">The default is the local computer.</span></span>

<span data-ttu-id="c6e8c-356">當您使用 **ComputerName** 參數時，PowerShell 會建立僅用來執行指定命令的暫時連接，然後關閉。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-356">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that's used only to run the specified command and is then closed.</span></span> <span data-ttu-id="c6e8c-357">如果您需要持續連線，請使用 **Session** 參數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-357">If you need a persistent connection, use the **Session** parameter.</span></span>

<span data-ttu-id="c6e8c-358">請輸入一或多部電腦的 NETBIOS 名稱、IP 位址或完整網域名稱 (以逗號分隔的清單方式)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-358">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="c6e8c-359">若要指定本機電腦，請輸入電腦名稱稱、localhost 或點 (`.`) 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-359">To specify the local computer, type the computer name, localhost, or a dot (`.`).</span></span>

<span data-ttu-id="c6e8c-360">若要在 **ComputerName** 的值中使用 IP 位址，命令必須包含 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-360">To use an IP address in the value of **ComputerName** , the command must include the **Credential** parameter.</span></span> <span data-ttu-id="c6e8c-361">電腦必須設定為 HTTPS 傳輸，或必須在本機電腦的 WinRM **TrustedHosts** 清單中包含遠端電腦的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-361">The computer must be configured for the HTTPS transport or the IP address of the remote computer must be included in the local computer's WinRM **TrustedHosts** list.</span></span> <span data-ttu-id="c6e8c-362">如需將電腦名稱稱新增到 **TrustedHosts** 清單的指示，請參閱 [如何將電腦新增到信任的主機清單](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-362">For instructions to add a computer name to the **TrustedHosts** list, see [How to Add a Computer to the Trusted Host List](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list).</span></span>

<span data-ttu-id="c6e8c-363">在 Windows Vista 和更新版本的 Windows 作業系統上，若要在 **ComputerName** 的值中包含本機電腦，您必須使用 [以 **系統管理員身分執行** ] 選項來執行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-363">On Windows Vista and later versions of the Windows operating system, to include the local computer in the value of **ComputerName** , you must run PowerShell using the **Run as administrator** option.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FilePathComputerName, ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-364">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="c6e8c-364">-ConfigurationName</span></span>

<span data-ttu-id="c6e8c-365">指定用於新 **PSSession** 的會話設定。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-365">Specifies the session configuration that is used for the new **PSSession** .</span></span>

<span data-ttu-id="c6e8c-366">輸入工作階段設定的設定名稱或完整資源 URI。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-366">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="c6e8c-367">如果您只指定設定名稱，則會在前面加上下列架構 URI： `http://schemas.microsoft.com/PowerShell` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-367">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="c6e8c-368">工作階段的工作階段設定是位於遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-368">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="c6e8c-369">如果遠端電腦上不存在指定的會話設定，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-369">If the specified session configuration doesn't exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="c6e8c-370">預設值是 `$PSSessionConfigurationName` 本機電腦上喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-370">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="c6e8c-371">如果未設定此喜好設定變數，則預設值為 [ **Microsoft. PowerShell** ]。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-371">If this preference variable isn't set, the default is **Microsoft.PowerShell** .</span></span> <span data-ttu-id="c6e8c-372">如需詳細資訊，請參閱 [about_Preference_Variables](about/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-372">For more information, see [about_Preference_Variables](about/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: $PSSessionConfigurationName if set on the local computer, otherwise Microsoft.PowerShell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-373">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="c6e8c-373">-ConnectionUri</span></span>

<span data-ttu-id="c6e8c-374">指定定義工作階段之連線端點的「統一資源識別項」(URI)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-374">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint of the session.</span></span>
<span data-ttu-id="c6e8c-375">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-375">The URI must be fully qualified.</span></span>

<span data-ttu-id="c6e8c-376">這個字串的格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="c6e8c-376">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="c6e8c-377">預設值如下：</span><span class="sxs-lookup"><span data-stu-id="c6e8c-377">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="c6e8c-378">如果您未指定連接 URI，您可以使用 **UseSSL** 和 **Port** 參數來指定連接 uri 值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-378">If you don't specify a connection URI, you can use the **UseSSL** and **Port** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="c6e8c-379">URI 的 **Transport** 區段有效值為 HTTP 與 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-379">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="c6e8c-380">如果您指定具有傳輸區段的連線 URI，但未指定埠，則會使用標準埠：80（適用于 HTTP）和443（適用于 HTTPS）來建立會話。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-380">If you specify a connection URI with a Transport segment, but don't specify a port, the session is created with the standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="c6e8c-381">若要使用 PowerShell 遠端的預設埠，請指定 HTTP 的埠5985或 HTTPS 的5986。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-381">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="c6e8c-382">如果目的地電腦將連線重新導向至不同的 URI，除非您在命令中使用 **AllowRedirection** 參數，否則 PowerShell 會禁止重新導向。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-382">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: Uri, FilePathUri
Aliases: URI, CU

Required: False
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-383">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="c6e8c-383">-ContainerId</span></span>

<span data-ttu-id="c6e8c-384">指定容器識別碼的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-384">Specifies an array of container IDs.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-385">-Credential</span><span class="sxs-lookup"><span data-stu-id="c6e8c-385">-Credential</span></span>

<span data-ttu-id="c6e8c-386">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-386">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="c6e8c-387">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-387">The default is the current user.</span></span>

<span data-ttu-id="c6e8c-388">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-388">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="c6e8c-389">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-389">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="c6e8c-390">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-390">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="c6e8c-391">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-391">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName
Aliases:

Required: True (VMId, VMName, FilePathVMId, FilePathVMName), False (ComputerName, FilePathComputerName, Uri, FilePathUri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-392">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="c6e8c-392">-EnableNetworkAccess</span></span>

<span data-ttu-id="c6e8c-393">指出此 Cmdlet 會將互動式安全性權杖新增至回送會話。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-393">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="c6e8c-394">互動式權杖可讓您在會從其他電腦取得資料的回送工作階段中執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-394">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="c6e8c-395">例如，您可以在會將 XML 檔案從遠端電腦複製到本機電腦的工作階段中執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-395">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="c6e8c-396">回送會話是在同一部電腦上產生和結束的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-396">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="c6e8c-397">若要建立回送會話，請省略 **ComputerName** 參數，或將其值設為點 (`.`) 、localhost 或本機電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-397">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (`.`), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="c6e8c-398">根據預設，系統會使用網路權杖建立回送會話，這可能不會提供足夠的許可權來驗證遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-398">By default, loopback sessions are created using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="c6e8c-399">**EnableNetworkAccess** 參數只在回送工作階段中有效。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-399">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="c6e8c-400">如果您在遠端電腦上建立會話時使用 **EnableNetworkAccess** ，則命令會成功，但是會忽略參數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-400">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="c6e8c-401">您可以使用 **驗證** 參數的 **CredSSP** 值（將會話認證委派給其他電腦），允許回送會話中的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-401">You can allow remote access in a loopback session using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="c6e8c-402">為了保護電腦免于惡意存取，具有互動式權杖的已中斷連線回送會話（使用 **EnableNetworkAccess** 所建立的權杖）只能從建立會話的電腦重新連接。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-402">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created using **EnableNetworkAccess** , can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="c6e8c-403">使用 CredSSP 驗證且已中斷連線的工作階段可從其他電腦重新連線。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-403">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="c6e8c-404">如需詳細資訊，請參閱`Disconnect-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-404">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="c6e8c-405">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-405">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-406">-FilePath</span><span class="sxs-lookup"><span data-stu-id="c6e8c-406">-FilePath</span></span>

<span data-ttu-id="c6e8c-407">指定此 Cmdlet 在一或多部遠端電腦上執行的本機腳本。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-407">Specifies a local script that this cmdlet runs on one or more remote computers.</span></span> <span data-ttu-id="c6e8c-408">輸入腳本的路徑和檔案名，或使用管線將腳本路徑傳送至 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-408">Enter the path and filename of the script, or pipe a script path to `Invoke-Command`.</span></span> <span data-ttu-id="c6e8c-409">腳本必須存在於本機電腦或本機電腦可以存取的目錄中。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-409">The script must exist on the local computer or in a directory that the local computer can access.</span></span> <span data-ttu-id="c6e8c-410">使用 **ArgumentList** 來指定腳本中參數的值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-410">Use **ArgumentList** to specify the values of parameters in the script.</span></span>

<span data-ttu-id="c6e8c-411">當您使用此參數時，PowerShell 會將指定之指令檔的內容轉換成腳本區塊、將腳本區塊傳輸到遠端電腦，然後在遠端電腦上執行它。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-411">When you use this parameter, PowerShell converts the contents of the specified script file to a script block, transmits the script block to the remote computer, and runs it on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, FilePathComputerName, FilePathUri, FilePathVMId, FilePathVMName, FilePathContainerId
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-412">-HideComputerName</span><span class="sxs-lookup"><span data-stu-id="c6e8c-412">-HideComputerName</span></span>

<span data-ttu-id="c6e8c-413">指出此 Cmdlet 會從輸出顯示中省略每個物件的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-413">Indicates that this cmdlet omits the computer name of each object from the output display.</span></span> <span data-ttu-id="c6e8c-414">預設會在顯示中出現產生物件的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-414">By default, the name of the computer that generated the object appears in the display.</span></span>

<span data-ttu-id="c6e8c-415">這個參數只會影響輸出顯示。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-415">This parameter affects only the output display.</span></span> <span data-ttu-id="c6e8c-416">它不會變更物件。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-416">It doesn't change the object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases: HCN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-417">-InDisconnectedSession</span><span class="sxs-lookup"><span data-stu-id="c6e8c-417">-InDisconnectedSession</span></span>

<span data-ttu-id="c6e8c-418">指出此 Cmdlet 會在已中斷連線的會話中執行命令或腳本。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-418">Indicates that this cmdlet runs a command or script in a disconnected session.</span></span>

<span data-ttu-id="c6e8c-419">當您使用 **InDisconnectedSession** 參數時，會 `Invoke-Command` 在每一部遠端電腦上建立持續性會話、啟動 **ScriptBlock** 或 **FilePath** 參數所指定的命令，然後與會話中斷連線。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-419">When you use the **InDisconnectedSession** parameter, `Invoke-Command` creates a persistent session on each remote computer, starts the command specified by the **ScriptBlock** or **FilePath** parameter, and then disconnects from the session.</span></span> <span data-ttu-id="c6e8c-420">命令會繼續在中斷連線的會話中執行。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-420">The commands continue to run in the disconnected sessions.</span></span> <span data-ttu-id="c6e8c-421">**InDisconnectedSession** 可讓您執行命令，而不需要維護遠端會話的連接。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-421">**InDisconnectedSession** enables you to run commands without maintaining a connection to the remote sessions.</span></span> <span data-ttu-id="c6e8c-422">而且，由於會話會在傳回任何結果之前中斷連線，因此 **InDisconnectedSession** 會確定所有命令結果都會傳回到重新連線的會話，而不是在會話之間進行分割。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-422">And, because the session is disconnected before any results are returned, **InDisconnectedSession** makes sure that all command results are returned to the reconnected session, instead of being split between sessions.</span></span>

<span data-ttu-id="c6e8c-423">您無法使用 **InDisconnectedSession** 搭配 **Session** 參數或 **AsJob** 參數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-423">You can't use **InDisconnectedSession** with the **Session** parameter or the **AsJob** parameter.</span></span>

<span data-ttu-id="c6e8c-424">使用 **InDisconnectedSession** 的命令會傳回代表中斷連接之會話的 **PSSession** 物件。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-424">Commands that use **InDisconnectedSession** return a **PSSession** object that represents the disconnected session.</span></span> <span data-ttu-id="c6e8c-425">它們不會傳回命令輸出。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-425">They don't return the command output.</span></span> <span data-ttu-id="c6e8c-426">若要連接到中斷連線的會話，請使用 `Connect-PSSession` 或 `Receive-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-426">To connect to the disconnected session, use the `Connect-PSSession` or `Receive-PSSession` cmdlets.</span></span> <span data-ttu-id="c6e8c-427">若要取得會話中執行之命令的結果，請使用 `Receive-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-427">To get the results of commands that ran in the session, use the `Receive-PSSession` cmdlet.</span></span> <span data-ttu-id="c6e8c-428">若要在中斷連線的會話中執行產生輸出的命令，請將 **OutputBufferingMode** 會話選項的值設為 **Drop** 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-428">To run commands that generate output in a disconnected session, set the value of the **OutputBufferingMode** session option to **Drop** .</span></span> <span data-ttu-id="c6e8c-429">如果您想要連線到中斷連線的會話，請在會話中設定閒置超時，讓它提供足夠的時間讓您能夠在刪除會話之前先連接。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-429">If you intend to connect to the disconnected session, set the idle time-out in the session so that it provides sufficient time for you to connect before deleting the session.</span></span>

<span data-ttu-id="c6e8c-430">您可以在 **SessionOption** 參數或喜好設定變數中設定輸出緩衝處理模式和閒置超時時間 `$PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-430">You can set the output buffering mode and idle time-out in the **SessionOption** parameter or in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="c6e8c-431">如需會話選項的詳細資訊，請參閱 `New-PSSessionOption` 和 [about_Preference_Variables](./about/about_preference_variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-431">For more information about session options, see `New-PSSessionOption` and [about_Preference_Variables](./about/about_preference_variables.md).</span></span>

<span data-ttu-id="c6e8c-432">如需中斷連線工作階段功能的詳細資訊，請參閱 [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-432">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="c6e8c-433">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-433">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases: Disconnected

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-434">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c6e8c-434">-InputObject</span></span>

<span data-ttu-id="c6e8c-435">指定命令的輸入。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-435">Specifies input to the command.</span></span> <span data-ttu-id="c6e8c-436">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-436">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="c6e8c-437">使用 **InputObject** 參數時，請 `$Input` 在 **ScriptBlock** 參數的值中使用自動變數來代表輸入物件。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-437">When using the **InputObject** parameter, use the `$Input` automatic variable in the value of the **ScriptBlock** parameter to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-438">-JobName</span><span class="sxs-lookup"><span data-stu-id="c6e8c-438">-JobName</span></span>

<span data-ttu-id="c6e8c-439">指定背景工作的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-439">Specifies a friendly name for the background job.</span></span> <span data-ttu-id="c6e8c-440">依預設，作業會命名為 `Job<n>` ，其中 `<n>` 是序號。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-440">By default, jobs are named `Job<n>`, where `<n>` is an ordinal number.</span></span>

<span data-ttu-id="c6e8c-441">如果您在命令中使用 **JobName** 參數，命令就會以工作的形式執行，並傳回 `Invoke-Command` 工作物件，即使您未在命令中包含 **AsJob** 也一樣。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-441">If you use the **JobName** parameter in a command, the command is run as a job, and `Invoke-Command` returns a job object, even if you don't include **AsJob** in the command.</span></span>

<span data-ttu-id="c6e8c-442">如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](./About/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-442">For more information about PowerShell background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

```yaml
Type: System.String
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: Job<n>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-443">-NoNewScope</span><span class="sxs-lookup"><span data-stu-id="c6e8c-443">-NoNewScope</span></span>

<span data-ttu-id="c6e8c-444">指出此 Cmdlet 會在目前的範圍中執行指定的命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-444">Indicates that this cmdlet runs the specified command in the current scope.</span></span> <span data-ttu-id="c6e8c-445">依預設，會 `Invoke-Command` 在自己的範圍中執行命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-445">By default, `Invoke-Command` runs commands in their own scope.</span></span>

<span data-ttu-id="c6e8c-446">這個參數只有在於目前的工作階段中執行的命令 (亦即省略 **ComputerName** 和 **Session** 這兩個參數的命令) 中才有效。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-446">This parameter is valid only in commands that are run in the current session, that is, commands that omit both the **ComputerName** and **Session** parameters.</span></span>

<span data-ttu-id="c6e8c-447">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-447">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InProcess
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-448">-Port</span><span class="sxs-lookup"><span data-stu-id="c6e8c-448">-Port</span></span>

<span data-ttu-id="c6e8c-449">指定遠端電腦上用於此命令的網路埠。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-449">Specifies the network port on the remote computer that is used for this command.</span></span> <span data-ttu-id="c6e8c-450">若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-450">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="c6e8c-451">預設通訊埠為 5985 (WinRM 埠（適用于 HTTP）) 和 5986 (適用于 HTTPS) 的 WinRM 埠。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-451">The default ports are 5985 (WinRM port for HTTP) and 5986 (WinRM port for HTTPS).</span></span>

<span data-ttu-id="c6e8c-452">使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-452">Before using an alternate port, configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="c6e8c-453">若要設定接聽程式，請在 PowerShell 提示字元中輸入下列兩個命令：</span><span class="sxs-lookup"><span data-stu-id="c6e8c-453">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="c6e8c-454">除非您必須這樣做，否則請勿使用 **Port** 參數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-454">Don't use the **Port** parameter unless you must.</span></span> <span data-ttu-id="c6e8c-455">在命令中設定的連接埠，將套用於執行命令所在的所有電腦或工作階段。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-455">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="c6e8c-456">替代的連接埠設定可能使得命令無法在全部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-456">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-457">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="c6e8c-457">-RunAsAdministrator</span></span>

<span data-ttu-id="c6e8c-458">指出此 Cmdlet 會以系統管理員的身分叫用命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-458">Indicates that this cmdlet invokes a command as an Administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-459">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="c6e8c-459">-ScriptBlock</span></span>

<span data-ttu-id="c6e8c-460">指定要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-460">Specifies the commands to run.</span></span> <span data-ttu-id="c6e8c-461">以大括弧括住命令 `{ }` 以建立腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-461">Enclose the commands in curly braces `{ }` to create a script block.</span></span>
<span data-ttu-id="c6e8c-462">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-462">This parameter is required.</span></span>

<span data-ttu-id="c6e8c-463">預設會在遠端電腦上評估命令中的所有變數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-463">By default, any variables in the command are evaluated on the remote computer.</span></span> <span data-ttu-id="c6e8c-464">若要在命令中包含區域變數，請使用 **ArgumentList** 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-464">To include local variables in the command, use **ArgumentList** .</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: InProcess, Session, ComputerName, Uri, VMId, VMName, ContainerId
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-465">-Session</span><span class="sxs-lookup"><span data-stu-id="c6e8c-465">-Session</span></span>

<span data-ttu-id="c6e8c-466">指定此 Cmdlet 在其中執行命令的會話陣列。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-466">Specifies an array of sessions in which this cmdlet runs the command.</span></span> <span data-ttu-id="c6e8c-467">輸入包含 **pssession** 物件的變數，或輸入可建立或取得 **pssession** 物件的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-467">Enter a variable that contains **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="c6e8c-468">當您建立 **PSSession** 時，PowerShell 會建立與遠端電腦的持續連線。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-468">When you create a **PSSession** , PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="c6e8c-469">使用 **PSSession** 來執行一系列共用資料的相關命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-469">Use a **PSSession** to run a series of related commands that share data.</span></span> <span data-ttu-id="c6e8c-470">若要執行單一命令或一系列不相關的命令，請使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-470">To run a single command or a series of unrelated commands, use the **ComputerName** parameter.</span></span> <span data-ttu-id="c6e8c-471">如需詳細資訊，請參閱 [about_PSSessions](./About/about_PSSessions.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-471">For more information, see [about_PSSessions](./About/about_PSSessions.md).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session, FilePathRunspace
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-472">-SessionName</span><span class="sxs-lookup"><span data-stu-id="c6e8c-472">-SessionName</span></span>

<span data-ttu-id="c6e8c-473">指定中斷連線之工作階段的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-473">Specifies a friendly name for a disconnected session.</span></span> <span data-ttu-id="c6e8c-474">您可以使用此名稱，在後續命令中參考會話，例如 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-474">You can use the name to refer to the session in subsequent commands, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="c6e8c-475">這個參數是只有搭配 **InDisconnectedSession** 參數時才有效。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-475">This parameter is valid only with the **InDisconnectedSession** parameter.</span></span>

<span data-ttu-id="c6e8c-476">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-476">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-477">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="c6e8c-477">-SessionOption</span></span>

<span data-ttu-id="c6e8c-478">指定會話的 advanced 選項。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-478">Specifies advanced options for the session.</span></span> <span data-ttu-id="c6e8c-479">輸入 **SessionOption** 物件（例如您使用 Cmdlet 建立的物件 `New-PSSessionOption` ）或雜湊表，其中索引鍵為會話選項名稱，而值為會話選項值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-479">Enter a **SessionOption** object, such as one that you create using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="c6e8c-480">選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-480">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it's set.</span></span> <span data-ttu-id="c6e8c-481">否則，將以工作階段設定中設定的選項建立預設值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-481">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="c6e8c-482">會話選項值的優先順序高於 `$PSSessionOption` 喜好設定變數和會話設定中設定之會話的預設值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-482">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="c6e8c-483">不過，它們的優先順序不會高於會話設定中所設定的最大值、配額或限制。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-483">However, they don't take precedence over maximum values, quotas, or limits set in the session configuration.</span></span>

<span data-ttu-id="c6e8c-484">如需包含預設值之會話選項的描述，請參閱 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-484">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="c6e8c-485">如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-485">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="c6e8c-486">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-486">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-487">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="c6e8c-487">-ThrottleLimit</span></span>

<span data-ttu-id="c6e8c-488">指定為執行此命令可建立的最大同時連線數。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-488">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="c6e8c-489">若省略此參數，或輸入值為 0，則會使用預設值 32。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-489">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="c6e8c-490">節流限制僅適用於目前命令，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-490">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-491">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="c6e8c-491">-UseSSL</span></span>

<span data-ttu-id="c6e8c-492">指出此 Cmdlet 會使用安全通訊端層 (SSL) 通訊協定來建立與遠端電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-492">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="c6e8c-493">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-493">By default, SSL isn't used.</span></span>

<span data-ttu-id="c6e8c-494">WS-Management 加密透過網路傳輸的所有 PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-494">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="c6e8c-495">**UseSSL** 參數是額外的保護，可跨 HTTPS （而非 HTTP）傳送資料。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-495">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span>

<span data-ttu-id="c6e8c-496">如果您使用此參數，但是命令所用的埠上無法使用 SSL，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-496">If you use this parameter, but SSL isn't available on the port that's used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-497">-VMId</span><span class="sxs-lookup"><span data-stu-id="c6e8c-497">-VMId</span></span>

<span data-ttu-id="c6e8c-498">指定虛擬機器的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-498">Specifies an array of IDs of virtual machines.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: VMId, FilePathVMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-499">-VMName</span><span class="sxs-lookup"><span data-stu-id="c6e8c-499">-VMName</span></span>

<span data-ttu-id="c6e8c-500">指定虛擬機器名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-500">Specifies an array of names of virtual machines.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName, FilePathVMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c6e8c-501">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c6e8c-501">CommonParameters</span></span>

<span data-ttu-id="c6e8c-502">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-502">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c6e8c-503">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-503">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c6e8c-504">輸入</span><span class="sxs-lookup"><span data-stu-id="c6e8c-504">INPUTS</span></span>

### <span data-ttu-id="c6e8c-505">系統管理. ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="c6e8c-505">System.Management.Automation.ScriptBlock</span></span>

<span data-ttu-id="c6e8c-506">您可以使用管線將腳本區塊中的命令傳送至 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-506">You can pipe a command in a script block to `Invoke-Command`.</span></span> <span data-ttu-id="c6e8c-507">使用 `$Input` 自動變數來代表命令中的輸入物件。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-507">Use the `$Input` automatic variable to represent the input objects in the command.</span></span>

## <span data-ttu-id="c6e8c-508">輸出</span><span class="sxs-lookup"><span data-stu-id="c6e8c-508">OUTPUTS</span></span>

### <span data-ttu-id="c6e8c-509">PSRemotingJob、system.servicemodel 或已叫用之命令的輸出（或輸出）。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-509">System.Management.Automation.PSRemotingJob, System.Management.Automation.Runspaces.PSSession, or the output of the invoked command</span></span>

<span data-ttu-id="c6e8c-510">如果您使用 **AsJob** 參數，此 Cmdlet 會傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-510">This cmdlet returns a job object, if you use the **AsJob** parameter.</span></span> <span data-ttu-id="c6e8c-511">如果您指定 **InDisconnectedSession** 參數，則會傳回 `Invoke-Command` **PSSession** 物件。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-511">If you specify the **InDisconnectedSession** parameter, `Invoke-Command` returns a **PSSession** object.</span></span> <span data-ttu-id="c6e8c-512">否則，它會傳回叫用命令的輸出，這是 **ScriptBlock** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-512">Otherwise, it returns the output of the invoked command, which is the value of the **ScriptBlock** parameter.</span></span>

## <span data-ttu-id="c6e8c-513">注意</span><span class="sxs-lookup"><span data-stu-id="c6e8c-513">NOTES</span></span>

<span data-ttu-id="c6e8c-514">在 Windows Vista 和更新版本的 Windows 作業系統上，若要使用的 **ComputerName** 參數在 `Invoke-Command` 本機電腦上執行命令，您必須使用 [以 **系統管理員身分執行** ] 選項來執行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-514">On Windows Vista, and later versions of the Windows operating system, to use the **ComputerName** parameter of `Invoke-Command` to run a command on the local computer, you must run PowerShell using the **Run as administrator** option.</span></span>

<span data-ttu-id="c6e8c-515">當您在多部電腦上執行命令時，PowerShell 會依它們出現在清單中的順序連接到電腦。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-515">When you run commands on multiple computers, PowerShell connects to the computers in the order in which they appear in the list.</span></span> <span data-ttu-id="c6e8c-516">但是，命令輸出會以從遠端電腦收到的順序顯示，可能會不同。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-516">However, the command output is displayed in the order that it's received from the remote computers, which might be different.</span></span>

<span data-ttu-id="c6e8c-517">執行命令所產生的錯誤 `Invoke-Command` 會包含在命令結果中。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-517">Errors that result from the command that `Invoke-Command` runs are included in the command results.</span></span>
<span data-ttu-id="c6e8c-518">在本機命令中會是終止錯誤的錯誤在遠端命令中會被視為非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-518">Errors that would be terminating errors in a local command are treated as non-terminating errors in a remote command.</span></span> <span data-ttu-id="c6e8c-519">此策略可確保一部電腦上的終止錯誤不會在其執行所在的所有電腦上關閉命令。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-519">This strategy makes sure that terminating errors on one computer don't close the command on all computers on which it's run.</span></span> <span data-ttu-id="c6e8c-520">甚至是在單一電腦上執行遠端命令時，也會採用這種做法。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-520">This practice is used even when a remote command is run on a single computer.</span></span>

<span data-ttu-id="c6e8c-521">如果遠端電腦不是在本機電腦信任的網域中，則電腦可能無法驗證使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-521">If the remote computer isn't in a domain that the local computer trusts, the computer might not be able to authenticate the user's credentials.</span></span> <span data-ttu-id="c6e8c-522">若要將遠端電腦新增至 WS-MANAGEMENT 中受信任的主機清單，請在提供者中使用下列命令 `WSMAN` ，其中 `<Remote-Computer-Name>` 是遠端電腦的名稱：</span><span class="sxs-lookup"><span data-stu-id="c6e8c-522">To add the remote computer to the list of trusted hosts in WS-Management, use the following command in the `WSMAN` provider, where `<Remote-Computer-Name>` is the name of the remote computer:</span></span>

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

<span data-ttu-id="c6e8c-523">當您使用 **InDisconnectedSession** 參數中斷連接 **PSSession** 時，會話狀態會 **中斷** 連線，而且可用性為 **None** 。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-523">When you disconnect a **PSSession** using the **InDisconnectedSession** parameter, the session state is **Disconnected** and the availability is **None** .</span></span> <span data-ttu-id="c6e8c-524">**State** 屬性的值是相對於目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-524">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="c6e8c-525">值為「已 **中斷** 連線」表示 **PSSession** 未連接到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-525">A value of **Disconnected** means that the **PSSession** isn't connected to the current session.</span></span> <span data-ttu-id="c6e8c-526">但是，它並不表示 **PSSession** 與所有會話中斷連接。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-526">However, it doesn't mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="c6e8c-527">它可能連線不同的工作階段。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-527">It might be connected to a different session.</span></span> <span data-ttu-id="c6e8c-528">若要判斷是否可以連線或重新連線工作階段，請使用 **Availability** 屬性。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-528">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

<span data-ttu-id="c6e8c-529">**Availability** 值為 **None** 表示您可以連線工作階段。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-529">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="c6e8c-530">「 **忙碌** 」值表示您無法連接到 **PSSession** ，因為它已連接到另一個會話。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-530">A value of **Busy** indicates that you can't connect to the **PSSession** because it's connected to another session.</span></span> <span data-ttu-id="c6e8c-531">如需會話的 **State** 屬性值的詳細資訊，請參閱 [ runspacestate](/dotnet/api/system.management.automation.runspaces.runspacestate)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-531">For more information about the values of the **State** property of sessions, see [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span> <span data-ttu-id="c6e8c-532">如需會話的 **Availability** 屬性值的詳細資訊，請參閱 [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。</span><span class="sxs-lookup"><span data-stu-id="c6e8c-532">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="c6e8c-533">相關連結</span><span class="sxs-lookup"><span data-stu-id="c6e8c-533">RELATED LINKS</span></span>

[<span data-ttu-id="c6e8c-534">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="c6e8c-534">about_PSSessions</span></span>](./About/about_PSSessions.md)

[<span data-ttu-id="c6e8c-535">about_Remote</span><span class="sxs-lookup"><span data-stu-id="c6e8c-535">about_Remote</span></span>](./About/about_Remote.md)

[<span data-ttu-id="c6e8c-536">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="c6e8c-536">about_Remote_Disconnected_Sessions</span></span>](./About/about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="c6e8c-537">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="c6e8c-537">about_Remote_Troubleshooting</span></span>](./About/about_remote_troubleshooting.md)

[<span data-ttu-id="c6e8c-538">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="c6e8c-538">about_Remote_Variables</span></span>](./About/about_Remote_Variables.md)

[<span data-ttu-id="c6e8c-539">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="c6e8c-539">about_Scopes</span></span>](./About/about_scopes.md)

[<span data-ttu-id="c6e8c-540">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="c6e8c-540">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="c6e8c-541">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="c6e8c-541">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="c6e8c-542">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="c6e8c-542">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="c6e8c-543">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="c6e8c-543">Invoke-Item</span></span>](../Microsoft.PowerShell.Management/Invoke-Item.md)

[<span data-ttu-id="c6e8c-544">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="c6e8c-544">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="c6e8c-545">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="c6e8c-545">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="c6e8c-546">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="c6e8c-546">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
