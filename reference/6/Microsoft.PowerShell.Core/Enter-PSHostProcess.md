---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: dcc0fc0ddb9486d4bf1f24b7366622c011266a04
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204908"
---
# <span data-ttu-id="5a8ba-103">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="5a8ba-103">Enter-PSHostProcess</span></span>

## <span data-ttu-id="5a8ba-104">概要</span><span class="sxs-lookup"><span data-stu-id="5a8ba-104">SYNOPSIS</span></span>
<span data-ttu-id="5a8ba-105">連線到互動式工作階段並進入具本機處理程序的互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-105">Connects to and enters into an interactive session with a local process.</span></span>

## <span data-ttu-id="5a8ba-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5a8ba-106">SYNTAX</span></span>

### <span data-ttu-id="5a8ba-107">ProcessIdParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="5a8ba-107">ProcessIdParameterSet (Default)</span></span>

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="5a8ba-108">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="5a8ba-108">ProcessParameterSet</span></span>

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="5a8ba-109">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="5a8ba-109">ProcessNameParameterSet</span></span>

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="5a8ba-110">PSHostProcessInfoParameterSet</span><span class="sxs-lookup"><span data-stu-id="5a8ba-110">PSHostProcessInfoParameterSet</span></span>

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="5a8ba-111">PipeNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="5a8ba-111">PipeNameParameterSet</span></span>

```
Enter-PSHostProcess -CustomPipeName <String> [<CommonParameters>]
```

## <span data-ttu-id="5a8ba-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5a8ba-112">DESCRIPTION</span></span>

<span data-ttu-id="5a8ba-113">指令 `Enter-PSHostProcess` 程式會連接到具有本機進程的互動式會話並進入其中。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-113">The `Enter-PSHostProcess` cmdlet connects to and enters into an interactive session with a local process.</span></span> <span data-ttu-id="5a8ba-114">從 PowerShell 6.2 開始，非 Windows 平臺支援此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-114">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

<span data-ttu-id="5a8ba-115">遠端互動式會話會在已執行 PowerShell 的現有進程中執行，而不是建立新的進程來裝載 PowerShell 並執行遠端會話。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-115">Instead of creating a new process to host PowerShell and run a remote session, the remote, interactive session is run in an existing process that is already running PowerShell.</span></span> <span data-ttu-id="5a8ba-116">當您在指定的處理常式上與遠端會話進行互動時，您可以列舉執行中的執行空間，然後藉由執行或來選取要進行偵錯工具的執行時間 `Debug-Runspace` `Enable-RunspaceDebug` 。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-116">When you are interacting with a remote session on a specified process, you can enumerate running runspaces, and then select a runspace to debug by running either `Debug-Runspace` or `Enable-RunspaceDebug`.</span></span>

<span data-ttu-id="5a8ba-117">您要輸入的進程必須將 PowerShell 裝載 ( # A0) 。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-117">The process that you want to enter must be hosting PowerShell (System.Management.Automation.dll).</span></span>
<span data-ttu-id="5a8ba-118">您在找到處理序的電腦上必須是 Administrators 群組的成員，或者您必須是執行啟動處理序之指令碼的使用者。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-118">You must be either a member of the Administrators group on the computer on which the process is found, or you must be the user who is running the script that started the process.</span></span>

<span data-ttu-id="5a8ba-119">選取要進行偵錯的 Runspace 之後，如果該 Runspace 目前正在執行命令，或已在偵錯工具中停止，就會為該 Runspace 開啟遠端偵錯工作階段。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-119">After you have selected a runspace to debug, a remote debug session is opened for the runspace if it is either currently running a command or is stopped in the debugger.</span></span> <span data-ttu-id="5a8ba-120">然後您可以使用對其他遠端工作階段指令碼進行偵錯相同的方式對 Runspace 指令碼進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-120">You can then debug the runspace script in the same way you would debug other remote session scripts.</span></span>

<span data-ttu-id="5a8ba-121">與偵錯工作階段中斷，然後執行兩次 exit 中斷具處理程序的互動式工作階段，或在現有的偵錯工具執行 quit 命令停止指令碼執行。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-121">Detach from a debugging session, and then the interactive session with the process, by running exit twice, or stop script execution by running the existing debugger quit command.</span></span>

<span data-ttu-id="5a8ba-122">如果您使用 **Name** 參數指定處理程序，而且只找到一個具指定名稱的處理程序，就會進入該處理程序。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-122">If you specify a process by using the **Name** parameter, and there is only one process found with the specified name, the process is entered.</span></span> <span data-ttu-id="5a8ba-123">如果找到一個以上具有指定名稱的進程，則 PowerShell 會傳回錯誤，並列出以指定名稱找到的所有進程。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-123">If more than one process with the specified name is found, PowerShell returns an error, and lists all processes found with the specified name.</span></span>

<span data-ttu-id="5a8ba-124">為了支援連接到遠端電腦上的處理常式，已 `Enter-PSHostProcess` 在指定的遠端電腦上啟用 Cmdlet，讓您可以附加至遠端 PowerShell 會話內的本機進程。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-124">To support attaching to processes on remote computers, the `Enter-PSHostProcess` cmdlet is enabled in a specified remote computer, so that you can attach to a local process within a remote PowerShell session.</span></span>

## <span data-ttu-id="5a8ba-125">範例</span><span class="sxs-lookup"><span data-stu-id="5a8ba-125">EXAMPLES</span></span>

### <span data-ttu-id="5a8ba-126">範例1：在 PowerShell ISE 進程中開始對執行時間進行偵錯工具</span><span class="sxs-lookup"><span data-stu-id="5a8ba-126">Example 1: Start debugging a runspace within the PowerShell ISE process</span></span>

<span data-ttu-id="5a8ba-127">在此範例中，您會在 `Enter-PSHostProcess` powershell 主控台內執行以進入 POWERSHELL ISE 進程。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-127">In this example, you run `Enter-PSHostProcess` from within the PowerShell console to enter the PowerShell ISE process.</span></span> <span data-ttu-id="5a8ba-128">在產生的互動式會話中，您可以藉由執行來尋找您想要進行偵錯工具的運行空間 `Get-Runspace` ，然後再進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-128">In the resulting interactive session, you can find a runspace that you want to debug by running `Get-Runspace`, and then debug the runspace.</span></span>

```
PS C:\> Enter-PSHostProcess -Name powershell_ise
[Process:1520]: PS C:\Test\Documents>

Next, get available runspaces within the process you have entered.
PS C:\> [Process:1520]: PS C:\>  Get-Runspace
Id    Name          InstanceId                               State           Availability
--    -------       -----------                              ------          -------------
1     Runspace1     2d91211d-9cce-42f0-ab0e-71ac258b32b5     Opened          Available
2     Runspace2     a3855043-cb16-424a-a616-685360c3763b     Opened          RemoteDebug
3     MyLocalRS     2236dbd8-2105-4dec-a15a-a27d0bfaacb5     Opened          LocalDebug
4     MyRunspace    771356e9-8c44-4b70-9de5-dd17cb41e48e     Opened          Busy
5     Runspace8     3e517382-a97a-49ba-9c3c-fd21f6664288     Broken          None

The runspace objects returned by Get-Runspace also have a NoteProperty called ScriptStackTrace of
the running command stack, if available.Next, debug runspace ID 4, that is running another user's
long-running script. From the list returned from Get-Runspace, note that the runspace state is
Opened, and Availability is Busy, meaning that the runspace is still running the long-running
script.

PS C:\> [Process:1520]: PS C:\>  (Get-Runspace -Id 4).ScriptStackTrace
Command                    Arguments                           Location
-------                    ---------                           --------
MyModuleWorkflowF1         {}                                  TestNoFile3.psm1: line 6
WFTest1                    {}                                  TestNoFile2.ps1: line 14
TestNoFile2.ps1            {}                                  TestNoFile2.ps1: line 22
<ScriptBlock>              {}                                  <No file>

Start an interactive debugging session with this runspace by running the Debug-Runspace cmdlet.

PS C:\> [Process: 1520]: PS C:\>  Debug-Runspace -Id 4
Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'

At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[Process: 1520]: [RSDBG: 4]: PS C:\> >

After you are finished debugging, allow the script to continue running without the debugger attached
by running the exit debugger command. Alternatively, you can quit the debugger with the q or Stop
commands.

PS C:\> [Process:346]: [RSDBG: 3]: PS C:\> > exit
[Process:1520]: PS C:\>

When you are finished working in the process, exit the process by running the Exit-PSHostProcess
cmdlet. This returns you to the PS C:\> prompt.

PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

## <span data-ttu-id="5a8ba-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5a8ba-129">PARAMETERS</span></span>

### <span data-ttu-id="5a8ba-130">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="5a8ba-130">-AppDomainName</span></span>

<span data-ttu-id="5a8ba-131">如果省略，則指定要連接的應用程式功能變數名稱，使用 **DefaultAppDomain** 。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-131">Specifies an application domain name to connect to if omitted, uses **DefaultAppDomain** .</span></span> <span data-ttu-id="5a8ba-132">用 `Get-PSHostProcessInfo` 來顯示應用程式功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-132">Use `Get-PSHostProcessInfo` to display the application domain names.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessIdParameterSet, ProcessParameterSet, ProcessNameParameterSet, PSHostProcessInfoParameterSet
Aliases:

Required: False
Position: 1
Default value: DefaultAppDomain
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a8ba-133">-HostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="5a8ba-133">-HostProcessInfo</span></span>

<span data-ttu-id="5a8ba-134">指定可使用 PowerShell 連接的 **exit-pshostprocessinfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-134">Specifies a **PSHostProcessInfo** object that can be connected to with PowerShell.</span></span> <span data-ttu-id="5a8ba-135">使用 `Get-PSHostProcessInfo` 取得物件。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-135">Use `Get-PSHostProcessInfo` to get the object.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSHostProcessInfo
Parameter Sets: PSHostProcessInfoParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5a8ba-136">-Id</span><span class="sxs-lookup"><span data-stu-id="5a8ba-136">-Id</span></span>

<span data-ttu-id="5a8ba-137">依處理序識別碼指定處理程序。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-137">Specifies a process by the process ID.</span></span> <span data-ttu-id="5a8ba-138">若要取得處理序識別碼，請執行 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-138">To get a process ID, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a8ba-139">-Name</span><span class="sxs-lookup"><span data-stu-id="5a8ba-139">-Name</span></span>

<span data-ttu-id="5a8ba-140">依處理程序名稱指定處理程序。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-140">Specifies a process by the process name.</span></span> <span data-ttu-id="5a8ba-141">若要取得處理常式名稱，請執行 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-141">To get a process name, run the `Get-Process` cmdlet.</span></span> <span data-ttu-id="5a8ba-142">您也可以從 [工作管理員] 中處理程序的 [內容] 對話方塊取得處理程序名稱。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-142">You can also get process names from the Properties dialog box of a process in Task Manager.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a8ba-143">-Process</span><span class="sxs-lookup"><span data-stu-id="5a8ba-143">-Process</span></span>

<span data-ttu-id="5a8ba-144">依處理程序物件指定處理程序。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-144">Specifies a process by the process object.</span></span> <span data-ttu-id="5a8ba-145">使用此參數最簡單的方式是儲存命令的結果，此 `Get-Process` 命令會傳回您要在變數中輸入的進程，然後將變數指定為此參數的值。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-145">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Diagnostics.Process
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5a8ba-146">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="5a8ba-146">-CustomPipeName</span></span>

<span data-ttu-id="5a8ba-147">取得或設定要連接的自訂具名管道名稱。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-147">Gets or sets the custom named pipe name to connect to.</span></span> <span data-ttu-id="5a8ba-148">這通常會與一起使用 `pwsh -CustomPipeName` 。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-148">This is usually used in conjunction with `pwsh -CustomPipeName`.</span></span>

<span data-ttu-id="5a8ba-149">此參數是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-149">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String
Parameter Sets: PipeNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a8ba-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5a8ba-150">CommonParameters</span></span>

<span data-ttu-id="5a8ba-151">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5a8ba-152">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5a8ba-153">輸入</span><span class="sxs-lookup"><span data-stu-id="5a8ba-153">INPUTS</span></span>

### <span data-ttu-id="5a8ba-154">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="5a8ba-154">System.Diagnostics.Process</span></span>

## <span data-ttu-id="5a8ba-155">輸出</span><span class="sxs-lookup"><span data-stu-id="5a8ba-155">OUTPUTS</span></span>

## <span data-ttu-id="5a8ba-156">注意</span><span class="sxs-lookup"><span data-stu-id="5a8ba-156">NOTES</span></span>

<span data-ttu-id="5a8ba-157">`Enter-PSHostProcess` 無法輸入您執行命令所在的 PowerShell 會話的處理常式。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-157">`Enter-PSHostProcess` cannot enter the process of the PowerShell session in which you are running the command.</span></span> <span data-ttu-id="5a8ba-158">不過，您可以輸入另一個 PowerShell 會話的處理常式，或輸入與執行中的會話相同的時間執行的 PowerShell ISE 會話 `Enter-PSHostProcess` 。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-158">You can, however, enter the process of another PowerShell session, or a PowerShell ISE session that is running at the same time as the session in which you are running `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="5a8ba-159">`Enter-PSHostProcess` 只能輸入裝載 PowerShell 的處理常式。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-159">`Enter-PSHostProcess` can enter only those processes that are hosting PowerShell.</span></span> <span data-ttu-id="5a8ba-160">也就是說，他們已載入 PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-160">That is, they have loaded the PowerShell engine.</span></span>

<span data-ttu-id="5a8ba-161">若要從進程內結束處理常式，請輸入 **exit** ，然後按 <kbd>enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="5a8ba-161">To exit a process from within the process, type **exit** , and then press <kbd>Enter</kbd>.</span></span>

## <span data-ttu-id="5a8ba-162">相關連結</span><span class="sxs-lookup"><span data-stu-id="5a8ba-162">RELATED LINKS</span></span>

[<span data-ttu-id="5a8ba-163">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="5a8ba-163">Exit-PSHostProcess</span></span>](Exit-PSHostProcess.md)

[<span data-ttu-id="5a8ba-164">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="5a8ba-164">Get-PSHostProcessInfo</span></span>](Get-PSHostProcessInfo.md)
