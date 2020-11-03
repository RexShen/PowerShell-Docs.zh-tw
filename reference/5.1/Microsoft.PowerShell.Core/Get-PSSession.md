---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSession
ms.openlocfilehash: c9c927ccdbc70d07ad8fa2cf13f3e2fe4a83f8c5
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205395"
---
# <span data-ttu-id="49594-103">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="49594-103">Get-PSSession</span></span>

## <span data-ttu-id="49594-104">概要</span><span class="sxs-lookup"><span data-stu-id="49594-104">SYNOPSIS</span></span>
<span data-ttu-id="49594-105">取得本機和遠端電腦上的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="49594-105">Gets the PowerShell sessions on local and remote computers.</span></span>

## <span data-ttu-id="49594-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="49594-106">SYNTAX</span></span>

### <span data-ttu-id="49594-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="49594-107">Name (Default)</span></span>

```
Get-PSSession [-Name <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="49594-108">ComputerName</span><span class="sxs-lookup"><span data-stu-id="49594-108">ComputerName</span></span>

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="49594-109">ComputerInstanceId</span><span class="sxs-lookup"><span data-stu-id="49594-109">ComputerInstanceId</span></span>

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="49594-110">ConnectionUriInstanceId</span><span class="sxs-lookup"><span data-stu-id="49594-110">ConnectionUriInstanceId</span></span>

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] -InstanceId <Guid[]>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="49594-111">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="49594-111">ConnectionUri</span></span>

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="49594-112">ContainerId</span><span class="sxs-lookup"><span data-stu-id="49594-112">ContainerId</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="49594-113">ContainerIdInstanceId</span><span class="sxs-lookup"><span data-stu-id="49594-113">ContainerIdInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="49594-114">VMId</span><span class="sxs-lookup"><span data-stu-id="49594-114">VMId</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### <span data-ttu-id="49594-115">VMIdInstanceId</span><span class="sxs-lookup"><span data-stu-id="49594-115">VMIdInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### <span data-ttu-id="49594-116">VMName</span><span class="sxs-lookup"><span data-stu-id="49594-116">VMName</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMName <String[]>
 [<CommonParameters>]
```

### <span data-ttu-id="49594-117">VMNameInstanceId</span><span class="sxs-lookup"><span data-stu-id="49594-117">VMNameInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="49594-118">InstanceId</span><span class="sxs-lookup"><span data-stu-id="49594-118">InstanceId</span></span>

```
Get-PSSession [-InstanceId <Guid[]>] [<CommonParameters>]
```

### <span data-ttu-id="49594-119">Id</span><span class="sxs-lookup"><span data-stu-id="49594-119">Id</span></span>

```
Get-PSSession [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="49594-120">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="49594-120">DESCRIPTION</span></span>

<span data-ttu-id="49594-121">Cmdlet 會在 `Get-PSSession` 本機和遠端電腦上 ( **pssession** ) 取得使用者管理的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="49594-121">The `Get-PSSession` cmdlet gets the user-managed PowerShell sessions ( **PSSessions** ) on local and remote computers.</span></span>

<span data-ttu-id="49594-122">從 Windows PowerShell 3.0 開始，會話會儲存在每個連線遠端端的電腦上。</span><span class="sxs-lookup"><span data-stu-id="49594-122">Starting in Windows PowerShell 3.0, sessions are stored on the computers at the remote end of each connection.</span></span> <span data-ttu-id="49594-123">您可以使用的 **ComputerName** 或 **ConnectionUri** 參數 `Get-PSSession` 取得連接到本機電腦或遠端電腦的會話，即使它們不是在目前的會話中建立也一樣。</span><span class="sxs-lookup"><span data-stu-id="49594-123">You can use the **ComputerName** or **ConnectionUri** parameters of `Get-PSSession` to get the sessions that connect to the local computer or remote computers, even if they were not created in the current session.</span></span>

<span data-ttu-id="49594-124">如果沒有參數，會 `Get-PSSession` 取得在目前會話中建立的所有會話。</span><span class="sxs-lookup"><span data-stu-id="49594-124">Without parameters, `Get-PSSession` gets all sessions that were created in the current session.</span></span>

<span data-ttu-id="49594-125">使用篩選參數，包括 **Name** 、 **ID** 、 **InstanceID** 、 **State** 、 **ApplicationName** 和 **ConfigurationName** ，以便從傳回的會話中進行選取 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="49594-125">Use the filtering parameters, including **Name** , **ID** , **InstanceID** , **State** , **ApplicationName** , and **ConfigurationName** to select from among the sessions that `Get-PSSession` returns.</span></span>

<span data-ttu-id="49594-126">`Get-PSSession`當您使用 **ComputerName** 或 **ConnectionUri** 參數時，請使用其餘的參數來設定執行命令的暫存連接。</span><span class="sxs-lookup"><span data-stu-id="49594-126">Use the remaining parameters to configure the temporary connection in which the `Get-PSSession` command runs when you use the **ComputerName** or **ConnectionUri** parameters.</span></span>

<span data-ttu-id="49594-127">注意：在 Windows PowerShell 2.0 中，如果沒有參數， `Get-PSSession` 則會取得在目前會話中建立的所有會話。</span><span class="sxs-lookup"><span data-stu-id="49594-127">NOTE: In Windows PowerShell 2.0, without parameters, `Get-PSSession` gets all sessions that were created in the current session.</span></span> <span data-ttu-id="49594-128">**ComputerName** 參數會取得在目前會話中建立的會話，並連接到指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="49594-128">The **ComputerName** parameter gets sessions that were created in the current session and connect to the specified computer.</span></span>

<span data-ttu-id="49594-129">如需 PowerShell 會話的詳細資訊，請參閱 [about_PSSessions](about/about_PSSessions.md)。</span><span class="sxs-lookup"><span data-stu-id="49594-129">For more information about PowerShell sessions, see [about_PSSessions](about/about_PSSessions.md).</span></span>

## <span data-ttu-id="49594-130">範例</span><span class="sxs-lookup"><span data-stu-id="49594-130">EXAMPLES</span></span>

### <span data-ttu-id="49594-131">範例1：取得在目前會話中建立的會話</span><span class="sxs-lookup"><span data-stu-id="49594-131">Example 1: Get sessions created in the current session</span></span>

```powershell
Get-PSSession
```

<span data-ttu-id="49594-132">此命令會取得在目前會話中建立的所有 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="49594-132">This command gets all of the **PSSessions** that were created in the current session.</span></span> <span data-ttu-id="49594-133">它不會取得在其他會話或其他電腦上建立的 **pssession** ，即使它們已連線到這部電腦。</span><span class="sxs-lookup"><span data-stu-id="49594-133">It does not get **PSSessions** that were created in other sessions or on other computers, even if they connect to this computer.</span></span>

### <span data-ttu-id="49594-134">範例2：取得連接到本機電腦的會話</span><span class="sxs-lookup"><span data-stu-id="49594-134">Example 2: Get sessions connected to the local computer</span></span>

```powershell
Get-PSSession -ComputerName "localhost"
```

<span data-ttu-id="49594-135">此命令會取得連接到本機電腦的 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="49594-135">This command gets the **PSSessions** that are connected to the local computer.</span></span> <span data-ttu-id="49594-136">若要指示本機電腦，請輸入電腦名稱稱、localhost 或點 (。 ) </span><span class="sxs-lookup"><span data-stu-id="49594-136">To indicate the local computer, type the computer name, localhost, or a dot (.)</span></span>

<span data-ttu-id="49594-137">此命令傳回本機電腦上的所有工作階段，即使它們是在不同的工作階段中或不同的電腦上所建立。</span><span class="sxs-lookup"><span data-stu-id="49594-137">The command returns all of the sessions on the local computer, even if they were created in different sessions or on different computers.</span></span>

### <span data-ttu-id="49594-138">範例3：取得連接到電腦的會話</span><span class="sxs-lookup"><span data-stu-id="49594-138">Example 3: Get sessions connected to a computer</span></span>

```powershell
Get-PSSession -ComputerName "Server02"
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  2 Session3        Server02       Disconnected  ITTasks                       Busy
  1 ScheduledJobs   Server02       Opened        Microsoft.PowerShell     Available
  3 Test            Server02       Disconnected  Microsoft.PowerShell          Busy
```

<span data-ttu-id="49594-139">此命令取得連線到 Server02 電腦的 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="49594-139">This command gets the **PSSessions** that are connected to the Server02 computer.</span></span>

<span data-ttu-id="49594-140">此命令傳回 Server02 上的所有工作階段，即使它們是在不同的工作階段中或不同的電腦上所建立。</span><span class="sxs-lookup"><span data-stu-id="49594-140">The command returns all of the sessions on Server02, even if they were created in different sessions or on different computers.</span></span>

<span data-ttu-id="49594-141">輸出顯示有兩個工作階段的狀態為 Disconnected，且可用性為 Busy。</span><span class="sxs-lookup"><span data-stu-id="49594-141">The output shows that two of the sessions have a Disconnected state and a Busy availability.</span></span> <span data-ttu-id="49594-142">它們是在不同的工作階段中所建立，並且目前都正在使用中。</span><span class="sxs-lookup"><span data-stu-id="49594-142">They were created in different sessions and are currently in use.</span></span> <span data-ttu-id="49594-143">ScheduledJobs 會話是在目前的會話中建立的，且已開啟且可用。</span><span class="sxs-lookup"><span data-stu-id="49594-143">The ScheduledJobs session, which is Opened and Available, was created in the current session.</span></span>

### <span data-ttu-id="49594-144">範例4：儲存此命令的結果</span><span class="sxs-lookup"><span data-stu-id="49594-144">Example 4: Save results of this command</span></span>

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
$s1, $s2, $s3 = Get-PSSession
```

<span data-ttu-id="49594-145">此範例顯示如何將命令的結果儲存 `Get-PSSession` 在多個變數中。</span><span class="sxs-lookup"><span data-stu-id="49594-145">This example shows how to save the results of a `Get-PSSession` command in multiple variables.</span></span>

<span data-ttu-id="49594-146">第一個命令會使用 `New-PSSession` Cmdlet，在三部遠端電腦上建立 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="49594-146">The first command uses the `New-PSSession` cmdlet to create **PSSessions** on three remote computers.</span></span>

<span data-ttu-id="49594-147">第二個命令會使用 `Get-PSSession` Cmdlet 來取得三個 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="49594-147">The second command uses a `Get-PSSession` cmdlet to get the three **PSSessions** .</span></span> <span data-ttu-id="49594-148">然後，它會將每個 **pssession** 儲存在個別的變數中。</span><span class="sxs-lookup"><span data-stu-id="49594-148">It then saves each of the **PSSessions** in a separate variable.</span></span>

<span data-ttu-id="49594-149">當 PowerShell 將物件陣列指派給變數陣列時，它會將第一個物件指派給第一個變數，將第二個物件指派給第二個變數，依此類推。</span><span class="sxs-lookup"><span data-stu-id="49594-149">When PowerShell assigns an array of objects to an array of variables, it assigns the first object to the first variable, the second object to the second variable, and so on.</span></span> <span data-ttu-id="49594-150">如果物件數目多於變數數目，它會將所有剩餘的物件指派給陣列中的最後一個變數。</span><span class="sxs-lookup"><span data-stu-id="49594-150">If there are more objects than variables, it assigns all remaining objects to the last variable in the array.</span></span> <span data-ttu-id="49594-151">如果變數數目多於物件數目，便不使用多餘的變數。</span><span class="sxs-lookup"><span data-stu-id="49594-151">If there are more variables than objects, the extra variables are not used.</span></span>

### <span data-ttu-id="49594-152">範例5：使用實例識別碼刪除會話</span><span class="sxs-lookup"><span data-stu-id="49594-152">Example 5: Delete a session by using an instance ID</span></span>

```powershell
Get-PSSession | Format-Table -Property ComputerName, InstanceID
$s = Get-PSSession -InstanceID a786be29-a6bb-40da-80fb-782c67f7db0f
Remove-PSSession -Session $s
```

<span data-ttu-id="49594-153">這個範例示範如何使用其實例 ID 取得 **pssession** ，然後再刪除 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="49594-153">This example shows how to get a **PSSession** by using its instance ID, and then to delete the **PSSession** .</span></span>

<span data-ttu-id="49594-154">第一個命令會取得在目前會話中建立的所有 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="49594-154">The first command gets all of the **PSSessions** that were created in the current session.</span></span> <span data-ttu-id="49594-155">它會將 **pssession** 傳送至 Format-Table Cmdlet，此 Cmdlet 會顯示每個 **PSSession** 的 **ComputerName** 和 **InstanceID** 屬性。</span><span class="sxs-lookup"><span data-stu-id="49594-155">It sends the **PSSessions** to the Format-Table cmdlet, which displays the **ComputerName** and **InstanceID** properties of each **PSSession** .</span></span>

<span data-ttu-id="49594-156">第二個命令 `Get-PSSession` 會使用 Cmdlet 來取得特定的 **PSSession** ，並將它儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="49594-156">The second command uses the `Get-PSSession` cmdlet to get a particular **PSSession** and to save it in the `$s` variable.</span></span> <span data-ttu-id="49594-157">此命令會使用 **InstanceID** 參數來識別 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="49594-157">The command uses the **InstanceID** parameter to identify the **PSSession** .</span></span>

<span data-ttu-id="49594-158">第三個命令使用 Remove-PSSession Cmdlet 來刪除變數 **PSSession** 中的 PSSession `$s` 。</span><span class="sxs-lookup"><span data-stu-id="49594-158">The third command uses the Remove-PSSession cmdlet to delete the **PSSession** in the `$s` variable.</span></span>

### <span data-ttu-id="49594-159">範例6：取得具有特定名稱的會話</span><span class="sxs-lookup"><span data-stu-id="49594-159">Example 6: Get a session that has a particular name</span></span>

<span data-ttu-id="49594-160">此範例中的命令會尋找具有特定名稱格式且使用特定工作階段設定的工作階段，然後連線到該工作階段。</span><span class="sxs-lookup"><span data-stu-id="49594-160">The commands in this example find a session that has a particular name format and uses a particular session configuration and then connect to the session.</span></span> <span data-ttu-id="49594-161">您可以使用與此類似的命令來尋找同事在其中啟動工作的工作階段，然後進行連線來完成工作。</span><span class="sxs-lookup"><span data-stu-id="49594-161">You can use a command like this one to find a session in which a colleague started a task and connect to finish the task.</span></span>

```powershell
Get-PSSession -ComputerName Server02, Server12 -Name BackupJob* -ConfigurationName ITTasks -SessionOption @{OperationTimeout=240000}
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  3 BackupJob04     Server02        Disconnected        ITTasks                  None
```

```powershell
$s = Get-PSSession -ComputerName Server02 -Name BackupJob04 -ConfigurationName ITTasks | Connect-PSSession
$s
```

```Output
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 5 BackupJob04     Server02        Opened        ITTasks                  Available
```

<span data-ttu-id="49594-162">第一個命令會取得 Server02 和 Server12 遠端電腦上名稱開頭為 BackupJob 並使用 ITTasks 會話設定的會話。此命令會使用 **name** 參數來指定名稱模式，並使用 **ConfigurationName** 參數來指定會話設定。</span><span class="sxs-lookup"><span data-stu-id="49594-162">The first command gets sessions on the Server02 and Server12 remote computers that have names that begin with BackupJob and use the ITTasks session configuration.The command uses the **Name** parameter to specify the name pattern and the **ConfigurationName** parameter to specify the session configuration.</span></span> <span data-ttu-id="49594-163">**SessionOption** 參數的值是一個雜湊表，它會將 **OperationTimeout** 的值設定為 240000 毫秒 (4 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="49594-163">The value of the **SessionOption** parameter is a hash table that sets the value of the **OperationTimeout** to 240000 milliseconds (4 minutes).</span></span> <span data-ttu-id="49594-164">此設定可讓命令更多時間完成。 **ConfigurationName** 和 **SessionOption** 參數是用來設定在每部 `Get-PSSession` 電腦上執行 Cmdlet 的臨時會話。輸出會顯示命令傳回 BackupJob04 會話。</span><span class="sxs-lookup"><span data-stu-id="49594-164">This setting gives the command more time to complete.The **ConfigurationName** and **SessionOption** parameters are used to configure the temporary sessions in which the `Get-PSSession` cmdlet runs on each computer.The output shows that the command returns the BackupJob04 session.</span></span> <span data-ttu-id="49594-165">會話已中斷連線，而且 **可用性** 為 None，表示它不在使用中。</span><span class="sxs-lookup"><span data-stu-id="49594-165">The session is disconnected and the **Availability** is None, which indicates that it is not in use.</span></span>

<span data-ttu-id="49594-166">第二個命令會使用 `Get-PSSession` Cmdlet 來取得 BackupJob04 會話，並使用 Connect-PSSession Cmdlet 來連接會話。</span><span class="sxs-lookup"><span data-stu-id="49594-166">The second command uses the `Get-PSSession` cmdlet to get to the BackupJob04 session and the Connect-PSSession cmdlet to connect to the session.</span></span> <span data-ttu-id="49594-167">命令會將工作階段儲存於 $s 變數中。</span><span class="sxs-lookup"><span data-stu-id="49594-167">The command saves the session in the $s variable.</span></span>

<span data-ttu-id="49594-168">第三個命令取得 $s 變數中的工作階段。</span><span class="sxs-lookup"><span data-stu-id="49594-168">The third command gets the session in the $s variable.</span></span> <span data-ttu-id="49594-169">輸出顯示 `Connect-PSSession` 命令成功。</span><span class="sxs-lookup"><span data-stu-id="49594-169">The output shows that the `Connect-PSSession` command was successful.</span></span> <span data-ttu-id="49594-170">工作階段的狀態為 **Opened** 並且可供使用。</span><span class="sxs-lookup"><span data-stu-id="49594-170">The session is in the **Opened** state and is available for use.</span></span>

### <span data-ttu-id="49594-171">範例7：使用識別碼來取得會話</span><span class="sxs-lookup"><span data-stu-id="49594-171">Example 7: Get a session by using its ID</span></span>

```powershell
Get-PSSession -Id 2
```

<span data-ttu-id="49594-172">此命令會取得識別碼為2的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="49594-172">This command gets the **PSSession** with ID 2.</span></span> <span data-ttu-id="49594-173">由於 **id** 屬性的值只有在目前的會話中是唯一的，因此 **id** 參數僅對本機命令有效。</span><span class="sxs-lookup"><span data-stu-id="49594-173">Because the value of the **ID** property is unique only in the current session, the **Id** parameter is valid only for local commands.</span></span>

## <span data-ttu-id="49594-174">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="49594-174">PARAMETERS</span></span>

### <span data-ttu-id="49594-175">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="49594-175">-AllowRedirection</span></span>

<span data-ttu-id="49594-176">指出此 Cmdlet 允許將此連線重新導向至替代的統一資源識別項 (URI) 。</span><span class="sxs-lookup"><span data-stu-id="49594-176">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="49594-177">根據預設，PowerShell 不會重新導向連接。</span><span class="sxs-lookup"><span data-stu-id="49594-177">By default, PowerShell does not redirect connections.</span></span>

<span data-ttu-id="49594-178">此參數會設定 `Get-PSSession` 使用 **ConnectionUri** 參數來執行命令所建立的暫時連接。</span><span class="sxs-lookup"><span data-stu-id="49594-178">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ConnectionUri** parameter.</span></span>

<span data-ttu-id="49594-179">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="49594-179">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49594-180">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="49594-180">-ApplicationName</span></span>

<span data-ttu-id="49594-181">指定應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="49594-181">Specifies the name of an application.</span></span> <span data-ttu-id="49594-182">此 Cmdlet 只會連接到使用指定應用程式的會話。</span><span class="sxs-lookup"><span data-stu-id="49594-182">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="49594-183">輸入連線 URI 的應用程式名稱區段。</span><span class="sxs-lookup"><span data-stu-id="49594-183">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="49594-184">例如，在下列連接 URI 中，應用程式名稱為 WSMan： `http://localhost:5985/WSMAN` 。</span><span class="sxs-lookup"><span data-stu-id="49594-184">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span> <span data-ttu-id="49594-185">工作階段的應用程式名稱儲存在工作階段的 **Runspace.ConnectionInfo.AppName** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="49594-185">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="49594-186">此參數的值可用來選取與篩選工作階段。</span><span class="sxs-lookup"><span data-stu-id="49594-186">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="49594-187">它不會變更工作階段使用的應用程式。</span><span class="sxs-lookup"><span data-stu-id="49594-187">It does not change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="49594-188">-Authentication</span><span class="sxs-lookup"><span data-stu-id="49594-188">-Authentication</span></span>

<span data-ttu-id="49594-189">指定用來驗證命令執行所在之會話認證的機制 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="49594-189">Specifies the mechanism that is used to authenticate credentials for the session in which the `Get-PSSession` command runs.</span></span>

<span data-ttu-id="49594-190">此參數會設定建立的暫存連接，以 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 參數來執行命令。</span><span class="sxs-lookup"><span data-stu-id="49594-190">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="49594-191">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="49594-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="49594-192">預設</span><span class="sxs-lookup"><span data-stu-id="49594-192">Default</span></span>
- <span data-ttu-id="49594-193">基本</span><span class="sxs-lookup"><span data-stu-id="49594-193">Basic</span></span>
- <span data-ttu-id="49594-194">Credssp</span><span class="sxs-lookup"><span data-stu-id="49594-194">Credssp</span></span>
- <span data-ttu-id="49594-195">Digest</span><span class="sxs-lookup"><span data-stu-id="49594-195">Digest</span></span>
- <span data-ttu-id="49594-196">Kerberos</span><span class="sxs-lookup"><span data-stu-id="49594-196">Kerberos</span></span>
- <span data-ttu-id="49594-197">交涉</span><span class="sxs-lookup"><span data-stu-id="49594-197">Negotiate</span></span>
- <span data-ttu-id="49594-198">NegotiateWithImplicitCredential.</span><span class="sxs-lookup"><span data-stu-id="49594-198">NegotiateWithImplicitCredential.</span></span>

<span data-ttu-id="49594-199">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="49594-199">The default value is Default.</span></span>

<span data-ttu-id="49594-200">如需此參數值的詳細資訊，請參閱 MSDN library 中的 [AuthenticationMechanism 列舉](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) 。</span><span class="sxs-lookup"><span data-stu-id="49594-200">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) in the MSDN library.</span></span>

<span data-ttu-id="49594-201">注意：使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="49594-201">CAUTION: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="49594-202">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="49594-202">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="49594-203">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="49594-203">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="49594-204">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="49594-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49594-205">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="49594-205">-CertificateThumbprint</span></span>

<span data-ttu-id="49594-206">指定使用者帳戶的數位公開金鑰憑證 (X509) ，該帳戶有權建立 `Get-PSSession` 執行命令的會話。</span><span class="sxs-lookup"><span data-stu-id="49594-206">Specifies the digital public key certificate (X509) of a user account that has permission to create the session in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="49594-207">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="49594-207">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="49594-208">此參數會設定建立的暫存連接，以 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 參數來執行命令。</span><span class="sxs-lookup"><span data-stu-id="49594-208">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="49594-209">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="49594-209">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="49594-210">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="49594-210">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="49594-211">若要取得憑證指紋，請使用 PowerShell Cert：磁片磁碟機中的 Get-Item 或 Get-ChildItem 命令。</span><span class="sxs-lookup"><span data-stu-id="49594-211">To get a certificate thumbprint, use a Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

<span data-ttu-id="49594-212">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="49594-212">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49594-213">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="49594-213">-ComputerName</span></span>

<span data-ttu-id="49594-214">指定電腦名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="49594-214">Specifies an array of names of computers.</span></span> <span data-ttu-id="49594-215">取得連線到指定之電腦的工作階段。</span><span class="sxs-lookup"><span data-stu-id="49594-215">Gets the sessions that connect to the specified computers.</span></span>
<span data-ttu-id="49594-216">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="49594-216">Wildcard characters are not permitted.</span></span> <span data-ttu-id="49594-217">沒有任何預設值。</span><span class="sxs-lookup"><span data-stu-id="49594-217">There is no default value.</span></span>

<span data-ttu-id="49594-218">從 Windows PowerShell 3.0 開始， **PSSession** 物件會儲存在每個連接遠端的電腦上。</span><span class="sxs-lookup"><span data-stu-id="49594-218">Beginning in Windows PowerShell 3.0, **PSSession** objects are stored on the computers at the remote end of each connection.</span></span> <span data-ttu-id="49594-219">為了取得指定電腦上的會話，PowerShell 會建立每台電腦的暫時連線，然後執行 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="49594-219">To get the sessions on the specified computers, PowerShell creates a temporary connection to each computer and runs a `Get-PSSession` command.</span></span>

<span data-ttu-id="49594-220">輸入一或多部電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="49594-220">Type the NetBIOS name, an IP address, or a fully-qualified domain name of one or more computers.</span></span> <span data-ttu-id="49594-221">若要指定本機電腦，請輸入電腦名稱、localhost 或句點 (.)。</span><span class="sxs-lookup"><span data-stu-id="49594-221">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

<span data-ttu-id="49594-222">注意：此參數只會從執行 Windows PowerShell 3.0 或更新版本之 PowerShell 的電腦取得會話。</span><span class="sxs-lookup"><span data-stu-id="49594-222">Note: This parameter gets sessions only from computers that run Windows PowerShell 3.0 or later versions of PowerShell.</span></span> <span data-ttu-id="49594-223">舊版不會儲存工作階段。</span><span class="sxs-lookup"><span data-stu-id="49594-223">Earlier versions do not store sessions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerInstanceId, ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="49594-224">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="49594-224">-ConfigurationName</span></span>

<span data-ttu-id="49594-225">指定設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="49594-225">Specifies the name of a configuration.</span></span> <span data-ttu-id="49594-226">此 Cmdlet 只會取得使用指定會話設定的會話。</span><span class="sxs-lookup"><span data-stu-id="49594-226">This cmdlet gets only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="49594-227">輸入工作階段設定的設定名稱或完整資源 URI。</span><span class="sxs-lookup"><span data-stu-id="49594-227">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="49594-228">如果您只指定設定名稱，則會在前面加上下列架構 URI： `http://schemas.microsoft.com/powershell` 。</span><span class="sxs-lookup"><span data-stu-id="49594-228">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span> <span data-ttu-id="49594-229">工作階段的設定名稱儲存在工作階段的 **ConfigurationName** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="49594-229">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="49594-230">此參數的值可用來選取與篩選工作階段。</span><span class="sxs-lookup"><span data-stu-id="49594-230">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="49594-231">它不會變更工作階段使用的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="49594-231">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="49594-232">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="49594-232">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="49594-233">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="49594-233">-ConnectionUri</span></span>

<span data-ttu-id="49594-234">指定 URI，以定義執行命令之暫存會話的連接端點 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="49594-234">Specifies a URI that defines the connection endpoint for the temporary session in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="49594-235">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="49594-235">The URI must be fully qualified.</span></span>

<span data-ttu-id="49594-236">此參數會設定 `Get-PSSession` 使用 **ConnectionUri** 參數來執行命令所建立的暫時連接。</span><span class="sxs-lookup"><span data-stu-id="49594-236">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ConnectionUri** parameter.</span></span>

<span data-ttu-id="49594-237">此字串的格式為：</span><span class="sxs-lookup"><span data-stu-id="49594-237">The format of this string is:</span></span>

`<Transport>://<ComputerName>:<Port\>/<ApplicationName>`

<span data-ttu-id="49594-238">預設值為： `http://localhost:5985/WSMAN` 。</span><span class="sxs-lookup"><span data-stu-id="49594-238">The default value is: `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="49594-239">如果您未指定 **ConnectionUri** ，您可以使用 **UseSSL** 、 **ComputerName** 、 **Port** 及 **ApplicationName** 參數來指定 **ConnectionUri** 值。</span><span class="sxs-lookup"><span data-stu-id="49594-239">If you do not specify a **ConnectionUri** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span> <span data-ttu-id="49594-240">URI 的 Transport 區段有效值為 HTTP 與 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="49594-240">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="49594-241">若指定含傳輸區段的連線 URI，但未指定連接埠，將會以標準連接埠 80 (適用於 HTTP) 和 443 (適用於 HTTPS) 建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="49594-241">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="49594-242">若要使用 PowerShell 遠端的預設埠，請指定 HTTP 的埠5985或 HTTPS 的5986。</span><span class="sxs-lookup"><span data-stu-id="49594-242">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="49594-243">如果目的地電腦將連線重新導向至不同的 URI，除非您在命令中使用 **AllowRedirection** 參數，否則 PowerShell 會禁止重新導向。</span><span class="sxs-lookup"><span data-stu-id="49594-243">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

<span data-ttu-id="49594-244">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="49594-244">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="49594-245">此參數只會從執行 Windows PowerShell Windows PowerShell 3.0 或更新版本的電腦取得會話。</span><span class="sxs-lookup"><span data-stu-id="49594-245">This parameter gets sessions only from computers that run Windows PowerShell 3.0 or later versions of Windows PowerShell.</span></span> <span data-ttu-id="49594-246">舊版不會儲存工作階段。</span><span class="sxs-lookup"><span data-stu-id="49594-246">Earlier versions do not store sessions.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUri, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: Http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="49594-247">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="49594-247">-ContainerId</span></span>

<span data-ttu-id="49594-248">指定容器的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="49594-248">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="49594-249">此 Cmdlet 會啟動每個指定容器的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="49594-249">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="49594-250">使用 `docker ps` 命令來取得容器識別碼的清單。</span><span class="sxs-lookup"><span data-stu-id="49594-250">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="49594-251">如需詳細資訊，請參閱 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 命令的說明。</span><span class="sxs-lookup"><span data-stu-id="49594-251">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId, ContainerIdInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="49594-252">-Credential</span><span class="sxs-lookup"><span data-stu-id="49594-252">-Credential</span></span>

<span data-ttu-id="49594-253">指定使用者認證。</span><span class="sxs-lookup"><span data-stu-id="49594-253">Specifies a user credential.</span></span> <span data-ttu-id="49594-254">此 Cmdlet 會以指定使用者的許可權執行命令。</span><span class="sxs-lookup"><span data-stu-id="49594-254">This cmdlet runs the command with the permissions of the specified user.</span></span> <span data-ttu-id="49594-255">指定具有連線到遠端電腦之許可權的使用者帳戶，然後執行 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="49594-255">Specify a user account that has permission to connect to the remote computer and run a `Get-PSSession` command.</span></span> <span data-ttu-id="49594-256">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="49594-256">The default is the current user.</span></span>

<span data-ttu-id="49594-257">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="49594-257">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="49594-258">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="49594-258">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="49594-259">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="49594-259">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="49594-260">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="49594-260">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="49594-261">此參數會設定為 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 參數來執行命令所建立的暫時連接。</span><span class="sxs-lookup"><span data-stu-id="49594-261">This parameter configures to the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="49594-262">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="49594-262">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49594-263">-Id</span><span class="sxs-lookup"><span data-stu-id="49594-263">-Id</span></span>

<span data-ttu-id="49594-264">指定會話識別碼的陣列。</span><span class="sxs-lookup"><span data-stu-id="49594-264">Specifies an array of session IDs.</span></span> <span data-ttu-id="49594-265">此 Cmdlet 只會取得具有指定識別碼的會話。</span><span class="sxs-lookup"><span data-stu-id="49594-265">This cmdlet gets only the sessions with the specified IDs.</span></span> <span data-ttu-id="49594-266">輸入一或多個識別碼 (以逗號分隔)，或使用範圍運算子 (..) 來指定某個範圍的識別碼。</span><span class="sxs-lookup"><span data-stu-id="49594-266">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span> <span data-ttu-id="49594-267">您不能使用 ID 參數搭配 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="49594-267">You cannot use the ID parameter together with the **ComputerName** parameter.</span></span>

<span data-ttu-id="49594-268">識別碼是一個整數，可唯一識別目前會話中的使用者管理會話。</span><span class="sxs-lookup"><span data-stu-id="49594-268">An ID is an integer that uniquely identifies the user-managed sessions in the current session.</span></span> <span data-ttu-id="49594-269">它比較容易記住並輸入 **InstanceId** ，但是它只有在目前的會話內是唯一的。</span><span class="sxs-lookup"><span data-stu-id="49594-269">It is easier to remember and type than the **InstanceId** , but it is unique only within the current session.</span></span> <span data-ttu-id="49594-270">工作階段的識別碼儲存在工作階段的 ID 屬性中。</span><span class="sxs-lookup"><span data-stu-id="49594-270">The ID of a session is stored in the ID property of the session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="49594-271">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="49594-271">-InstanceId</span></span>

<span data-ttu-id="49594-272">指定會話的實例識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="49594-272">Specifies an array of instance IDs of sessions.</span></span> <span data-ttu-id="49594-273">此 Cmdlet 只會取得具有指定實例識別碼的會話。</span><span class="sxs-lookup"><span data-stu-id="49594-273">This cmdlet gets only the sessions with the specified instance IDs.</span></span>

<span data-ttu-id="49594-274">執行個體識別碼是 GUID，可唯一識別本機或遠端電腦上的某個階段作業。</span><span class="sxs-lookup"><span data-stu-id="49594-274">The instance ID is a GUID that uniquely identifies a session on a local or remote computer.</span></span> <span data-ttu-id="49594-275">**InstanceID** 是唯一的，即使您有多個會話在 PowerShell 中執行也是一樣。</span><span class="sxs-lookup"><span data-stu-id="49594-275">The **InstanceID** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="49594-276">工作階段的執行個體識別碼儲存在工作階段的 **InstanceID** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="49594-276">The instance ID of a session is stored in the **InstanceID** property of the session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId, InstanceId
Aliases:

Required: True (ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId), False (InstanceId)
Position: Named
Default value: All sessions
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49594-277">-Name</span><span class="sxs-lookup"><span data-stu-id="49594-277">-Name</span></span>

<span data-ttu-id="49594-278">指定會話名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="49594-278">Specifies an array of session names.</span></span> <span data-ttu-id="49594-279">此 Cmdlet 只會取得具有指定易記名稱的會話。</span><span class="sxs-lookup"><span data-stu-id="49594-279">This cmdlet gets only the sessions that have the specified friendly names.</span></span> <span data-ttu-id="49594-280">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="49594-280">Wildcard characters are permitted.</span></span>

<span data-ttu-id="49594-281">工作階段的好記名稱儲存在工作階段的 **Name** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="49594-281">The friendly name of a session is stored in the **Name** property of the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri, ContainerId, VMId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="49594-282">-Port</span><span class="sxs-lookup"><span data-stu-id="49594-282">-Port</span></span>

<span data-ttu-id="49594-283">指定用於執行命令的暫存連接所指定的網路埠 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="49594-283">Specifies the specified network port that is used for the temporary connection in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="49594-284">若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="49594-284">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="49594-285">預設的埠是5985，也就是 HTTP 的 WinRM 埠和5986，也就是 HTTPS 的 WinRM 埠。</span><span class="sxs-lookup"><span data-stu-id="49594-285">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="49594-286">使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。</span><span class="sxs-lookup"><span data-stu-id="49594-286">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="49594-287">若要設定接聽程式，請在 PowerShell 提示字元中輸入下列兩個命令：</span><span class="sxs-lookup"><span data-stu-id="49594-287">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="49594-288">此參數會設定為 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 參數來執行命令所建立的暫時連接。</span><span class="sxs-lookup"><span data-stu-id="49594-288">This parameter configures to the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="49594-289">除非必要，否則請勿使用 **Port** 參數。</span><span class="sxs-lookup"><span data-stu-id="49594-289">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="49594-290">命令中設定的 **埠** 會套用到命令執行所在的所有電腦或會話。</span><span class="sxs-lookup"><span data-stu-id="49594-290">The **Port** set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="49594-291">替代的連接埠設定可能使得命令無法在全部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="49594-291">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="49594-292">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="49594-292">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: 5985, 5986
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49594-293">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="49594-293">-SessionOption</span></span>

<span data-ttu-id="49594-294">指定會話的 advanced 選項。</span><span class="sxs-lookup"><span data-stu-id="49594-294">Specifies advanced options for the session.</span></span> <span data-ttu-id="49594-295">輸入 **SessionOption** 物件 (例如您使用 New-PSSessionOption Cmdlet 建立的物件) 或者雜湊表，其中索引鍵為工作階段選項名稱，而值為工作階段選項值。</span><span class="sxs-lookup"><span data-stu-id="49594-295">Enter a **SessionOption** object, such as one that you create by using the New-PSSessionOption cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="49594-296">選項的預設值是由 $PSSessionOption 喜好設定變數的值所決定 (若設定了該變數)。</span><span class="sxs-lookup"><span data-stu-id="49594-296">The default values for the options are determined by the value of the $PSSessionOption preference variable, if it is set.</span></span> <span data-ttu-id="49594-297">否則，將以工作階段設定中設定的選項建立預設值。</span><span class="sxs-lookup"><span data-stu-id="49594-297">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="49594-298">工作階段選項值優先順序高於 $PSSessionOption 喜好設定變數與工作階段設定中設定的工作階段預設值。</span><span class="sxs-lookup"><span data-stu-id="49594-298">The session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span> <span data-ttu-id="49594-299">不過，它們的優先順序不會高於工作階段設定中設定的最大值、配額或限制。</span><span class="sxs-lookup"><span data-stu-id="49594-299">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="49594-300">如需會話選項的描述（包括預設值），請參閱 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="49594-300">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="49594-301">如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="49594-301">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="49594-302">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="49594-302">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49594-303">-State</span><span class="sxs-lookup"><span data-stu-id="49594-303">-State</span></span>

<span data-ttu-id="49594-304">指定會話狀態。</span><span class="sxs-lookup"><span data-stu-id="49594-304">Specifies a session state.</span></span> <span data-ttu-id="49594-305">此 Cmdlet 只會取得處於指定狀態的會話。</span><span class="sxs-lookup"><span data-stu-id="49594-305">This cmdlet gets only sessions in the specified state.</span></span> <span data-ttu-id="49594-306">此參數可接受的值包括：全部、已開啟、已中斷連線、已關閉和已中斷。</span><span class="sxs-lookup"><span data-stu-id="49594-306">The acceptable values for this parameter are: All, Opened, Disconnected, Closed, and Broken.</span></span> <span data-ttu-id="49594-307">預設值為 All。</span><span class="sxs-lookup"><span data-stu-id="49594-307">The default value is All.</span></span>

<span data-ttu-id="49594-308">工作階段狀態值是相對於目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="49594-308">The session state value is relative to the current sessions.</span></span> <span data-ttu-id="49594-309">不是在目前的工作階段中建立，也未連線到目前之工作階段的工作階段，即使它們已連線到不同的工作階段，其狀態也會是 Disconnected。</span><span class="sxs-lookup"><span data-stu-id="49594-309">Sessions that were not created in the current sessions and are not connected to the current session have a state of Disconnected even when they are connected to a different session.</span></span>

<span data-ttu-id="49594-310">工作階段的狀態儲存在工作階段的 **State** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="49594-310">The state of a session is stored in the **State** property of the session.</span></span>

<span data-ttu-id="49594-311">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="49594-311">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.SessionFilterState
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:
Accepted values: All, Opened, Disconnected, Closed, Broken

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49594-312">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="49594-312">-ThrottleLimit</span></span>

<span data-ttu-id="49594-313">指定可建立以執行命令的並行連接數目上限 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="49594-313">Specifies the maximum number of concurrent connections that can be established to run the `Get-PSSession` command.</span></span> <span data-ttu-id="49594-314">若省略此參數，或輸入值為 0 (零)，則會使用預設值 32。</span><span class="sxs-lookup"><span data-stu-id="49594-314">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span> <span data-ttu-id="49594-315">節流限制僅適用於目前命令，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="49594-315">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

<span data-ttu-id="49594-316">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="49594-316">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49594-317">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="49594-317">-UseSSL</span></span>

<span data-ttu-id="49594-318">指出此 Cmdlet 會使用安全通訊端層 (SSL) 通訊協定來建立命令執行所在的連接 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="49594-318">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish the connection in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="49594-319">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="49594-319">By default, SSL is not used.</span></span> <span data-ttu-id="49594-320">若您使用此參數，但是命令所用的連接埠上無法使用 SSL，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="49594-320">If you use this parameter, but SSL is not available on the port used for the command, the command fails.</span></span>

<span data-ttu-id="49594-321">此參數會設定建立的暫存連接，以 `Get-PSSession` 使用 **ComputerName** 參數執行命令。</span><span class="sxs-lookup"><span data-stu-id="49594-321">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** parameter.</span></span>

<span data-ttu-id="49594-322">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="49594-322">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49594-323">-VMId</span><span class="sxs-lookup"><span data-stu-id="49594-323">-VMId</span></span>

<span data-ttu-id="49594-324">指定虛擬機器的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="49594-324">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="49594-325">此 Cmdlet 會在每個指定的虛擬機器之間啟動互動式會話。</span><span class="sxs-lookup"><span data-stu-id="49594-325">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="49594-326">若要查看可供您使用的虛擬機器，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="49594-326">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId, VMIdInstanceId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="49594-327">-VMName</span><span class="sxs-lookup"><span data-stu-id="49594-327">-VMName</span></span>

<span data-ttu-id="49594-328">指定虛擬機器名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="49594-328">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="49594-329">此 Cmdlet 會在每個指定的虛擬機器之間啟動互動式會話。</span><span class="sxs-lookup"><span data-stu-id="49594-329">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="49594-330">若要查看可供您使用的虛擬機器，請使用 `Get-VM` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="49594-330">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName, VMNameInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="49594-331">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="49594-331">CommonParameters</span></span>

<span data-ttu-id="49594-332">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="49594-332">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="49594-333">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="49594-333">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="49594-334">輸入</span><span class="sxs-lookup"><span data-stu-id="49594-334">INPUTS</span></span>

### <span data-ttu-id="49594-335">無</span><span class="sxs-lookup"><span data-stu-id="49594-335">None</span></span>

<span data-ttu-id="49594-336">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="49594-336">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="49594-337">輸出</span><span class="sxs-lookup"><span data-stu-id="49594-337">OUTPUTS</span></span>

### <span data-ttu-id="49594-338">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="49594-338">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="49594-339">注意</span><span class="sxs-lookup"><span data-stu-id="49594-339">NOTES</span></span>

- <span data-ttu-id="49594-340">此 Cmdlet 會取得使用者管理的會話 **PSSession** 物件，例如使用新的-PSSession、 `Enter-PSSession` 和 Invoke-Command Cmdlet 所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="49594-340">This cmdlet gets user-managed sessions **PSSession** objects" such as those that are created by using the New-PSSession, `Enter-PSSession`, and Invoke-Command cmdlets.</span></span> <span data-ttu-id="49594-341">它不會取得當您啟動 PowerShell 時所建立的系統管理會話。</span><span class="sxs-lookup"><span data-stu-id="49594-341">It does not get the system-managed session that is created when you start PowerShell.</span></span>
- <span data-ttu-id="49594-342">從 Windows PowerShell 3.0 開始， **PSSession** 物件會儲存在位於伺服器端或接收端連接端的電腦上。</span><span class="sxs-lookup"><span data-stu-id="49594-342">Starting in Windows PowerShell 3.0, **PSSession** objects are stored on the computer that is at the server-side or receiving end of a connection.</span></span> <span data-ttu-id="49594-343">為了取得儲存在本機電腦或遠端電腦上的會話，PowerShell 會為指定的電腦建立暫時的會話，並在會話中執行查詢命令。</span><span class="sxs-lookup"><span data-stu-id="49594-343">To get the sessions that are stored on the local computer or a remote computer, PowerShell establishes a temporary session to the specified computer and runs query commands in the session.</span></span>
- <span data-ttu-id="49594-344">若要取得連線到遠端電腦的工作階段，請使用 **ComputerName** 或 **ConnectionUri** 參數來指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="49594-344">To get sessions that connect to a remote computer, use the **ComputerName** or **ConnectionUri** parameters to specify the remote computer.</span></span> <span data-ttu-id="49594-345">若要篩選取得的會話 `Get-PSSession` ，請使用 **Name** 、 **ID** 、 **InstanceID** 和 **State** 參數。</span><span class="sxs-lookup"><span data-stu-id="49594-345">To filter the sessions that `Get-PSSession` gets, use the **Name** , **ID** , **InstanceID** , and **State** parameters.</span></span> <span data-ttu-id="49594-346">使用其餘的參數來設定使用的暫時會話 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="49594-346">Use the remaining parameters to configure the temporary session that `Get-PSSession` uses.</span></span>
- <span data-ttu-id="49594-347">當您使用 **ComputerName** 或 **ConnectionUri** 參數時， `Get-PSSession` 只會從執行 Windows PowerShell 3.0 和更新版本 PowerShell 的電腦取得會話。</span><span class="sxs-lookup"><span data-stu-id="49594-347">When you use the **ComputerName** or **ConnectionUri** parameters, `Get-PSSession` gets only sessions from computers running Windows PowerShell 3.0 and later versions of PowerShell.</span></span>
- <span data-ttu-id="49594-348">**PSSession** 的 **State** 屬性值是相對於目前的會話。</span><span class="sxs-lookup"><span data-stu-id="49594-348">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
  <span data-ttu-id="49594-349">因此，[已 **中斷** 連線] 值表示 **PSSession** 未連接到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="49594-349">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="49594-350">但是，它並不表示 **PSSession** 與所有會話中斷連接。</span><span class="sxs-lookup"><span data-stu-id="49594-350">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="49594-351">它可能連線不同的工作階段。</span><span class="sxs-lookup"><span data-stu-id="49594-351">It might be connected to a different session.</span></span> <span data-ttu-id="49594-352">若要判斷您是否可以從目前的會話連線或重新連線到 **PSSession** ，請使用 **Availability** 屬性。</span><span class="sxs-lookup"><span data-stu-id="49594-352">To determine whether you can connect or reconnect to the **PSSession** from the current session, use the **Availability** property.</span></span>

<span data-ttu-id="49594-353">**Availability** 值為 **None** 表示您可以連線工作階段。</span><span class="sxs-lookup"><span data-stu-id="49594-353">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="49594-354">「 **忙碌** 」值表示您無法連接到 **PSSession** ，因為它已連接到另一個會話。</span><span class="sxs-lookup"><span data-stu-id="49594-354">A value of **Busy** indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

<span data-ttu-id="49594-355">如需會話的 **State** 屬性值的詳細資訊，請參閱 [ runspacestate 列舉](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate)。</span><span class="sxs-lookup"><span data-stu-id="49594-355">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate).</span></span>

<span data-ttu-id="49594-356">如需會話的 **Availability** 屬性值的詳細資訊，請參閱 [RunspaceAvailability 列舉](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability)。</span><span class="sxs-lookup"><span data-stu-id="49594-356">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="49594-357">相關連結</span><span class="sxs-lookup"><span data-stu-id="49594-357">RELATED LINKS</span></span>

[<span data-ttu-id="49594-358">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="49594-358">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="49594-359">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="49594-359">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="49594-360">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="49594-360">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="49594-361">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="49594-361">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="49594-362">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="49594-362">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="49594-363">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="49594-363">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="49594-364">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="49594-364">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="49594-365">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="49594-365">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="49594-366">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="49594-366">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="49594-367">about_Remote</span><span class="sxs-lookup"><span data-stu-id="49594-367">about_Remote</span></span>](About/about_Remote.md)
