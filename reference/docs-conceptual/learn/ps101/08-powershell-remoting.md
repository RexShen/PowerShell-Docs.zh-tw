---
title: PowerShell 遠端
description: 在 PowerShell 中有許多不同的方式，可以對遠端電腦執行命令。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: ee83af41b53b254dd3dd993931333edac2f44f5a
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438209"
---
# <a name="chapter-8---powershell-remoting"></a><span data-ttu-id="00fce-103">第 8 章 - PowerShell 遠端</span><span class="sxs-lookup"><span data-stu-id="00fce-103">Chapter 8 - PowerShell remoting</span></span>

<span data-ttu-id="00fce-104">PowerShell 有許多不同的方式，可以對遠端電腦執行命令。</span><span class="sxs-lookup"><span data-stu-id="00fce-104">PowerShell has many different ways to run commands against remote computers.</span></span> <span data-ttu-id="00fce-105">在上一章中，您已看到如何使用 CIM Cmdlet 從遠端查詢 WMI。</span><span class="sxs-lookup"><span data-stu-id="00fce-105">In the last chapter, you saw how to remotely query WMI using the CIM cmdlets.</span></span> <span data-ttu-id="00fce-106">PowerShell 也包含具有內建 **ComputerName** 參數的數個 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="00fce-106">PowerShell also includes several cmdlets that have a built-in **ComputerName** parameter.</span></span>

<span data-ttu-id="00fce-107">如下列範例所示，`Get-Command` 可以與 **ParameterName** 參數搭配使用，以判斷哪些命令具有 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="00fce-107">As shown in the following example, `Get-Command` can be used with the **ParameterName** parameter to determine what commands have a **ComputerName** parameter.</span></span>

```powershell
Get-Command -ParameterName ComputerName
```

```Output
CommandType Name                        Version Source
----------- ----                        ------- ------
Cmdlet      Connect-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Connect-WSMan               7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Disconnect-WSMan            7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Enter-PSSession             7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-CimAssociatedInstance   7.0.0.0 CimCmdlets
Cmdlet      Get-CimClass                7.0.0.0 CimCmdlets
Cmdlet      Get-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Get-CimSession              7.0.0.0 CimCmdlets
Cmdlet      Get-Counter                 7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-HotFix                  7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Get-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-WinEvent                7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Invoke-CimMethod            7.0.0.0 CimCmdlets
Cmdlet      Invoke-Command              7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Invoke-WSManAction          7.0.0.0 Microsoft.WSMan.Management
Cmdlet      New-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      New-CimSession              7.0.0.0 CimCmdlets
Cmdlet      New-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      New-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Receive-Job                 7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Receive-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Register-CimIndicationEvent 7.0.0.0 CimCmdlets
Cmdlet      Remove-CimInstance          7.0.0.0 CimCmdlets
Cmdlet      Remove-CimSession           7.0.0.0 CimCmdlets
Cmdlet      Remove-PSSession            7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Remove-WSManInstance        7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Rename-Computer             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Restart-Computer            7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Send-MailMessage            7.0.0.0 Microsoft.PowerShell.Utility
Cmdlet      Set-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Set-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Stop-Computer               7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-Connection             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-WSMan                  7.0.0.0 Microsoft.WSMan.Management
```

<span data-ttu-id="00fce-108">`Get-Process` 和 `Get-Hotfix` 之類的命令具有 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="00fce-108">Commands such as `Get-Process` and `Get-Hotfix` have a **ComputerName** parameter.</span></span> <span data-ttu-id="00fce-109">這不是 Microsoft 對遠端電腦上執行命令將採取的長期指示。</span><span class="sxs-lookup"><span data-stu-id="00fce-109">This isn't the long-term direction that Microsoft is heading for running commands against remote computers.</span></span> <span data-ttu-id="00fce-110">即使您發現某個命令具有 **ComputerName** 參數，您還是需要指定替代的認證，而且其不會有 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="00fce-110">Even if you find a command that has a **ComputerName** parameter, chances are that you'll need to specify alternate credentials and it won't have a **Credential** parameter.</span></span> <span data-ttu-id="00fce-111">而如果您決定從提高權限的帳戶執行 PowerShell，則您與遠端電腦之間的防火牆可能會封鎖要求。</span><span class="sxs-lookup"><span data-stu-id="00fce-111">And if you decided to run PowerShell from an elevated account, a firewall between you and the remote computer can block the request.</span></span>

<span data-ttu-id="00fce-112">若要使用本章所示範的 PowerShell 遠端命令，您必須在遠端電腦上啟用 PowerShell 遠端。</span><span class="sxs-lookup"><span data-stu-id="00fce-112">To use the PowerShell remoting commands that are demonstrated in this chapter, PowerShell remoting must be enabled on the remote computer.</span></span> <span data-ttu-id="00fce-113">使用 `Enable-PSRemoting` Cmdlet 來啟用 PowerShell 遠端。</span><span class="sxs-lookup"><span data-stu-id="00fce-113">Use the `Enable-PSRemoting` cmdlet to enable PowerShell remoting.</span></span>

```powershell
Enable-PSRemoting
```

```Output
WinRM has been updated to receive requests.
WinRM service type changed successfully.
WinRM service started.

WinRM has been updated for remote management.
WinRM firewall exception enabled.
```

## <a name="one-to-one-remoting"></a><span data-ttu-id="00fce-114">一對一遠端</span><span class="sxs-lookup"><span data-stu-id="00fce-114">One-To-One Remoting</span></span>

<span data-ttu-id="00fce-115">如果您想要讓遠端工作階段成為互動式，則您需要一對一遠端。</span><span class="sxs-lookup"><span data-stu-id="00fce-115">If you want your remote session to be interactive, then one-to-one remoting is what you want.</span></span>
<span data-ttu-id="00fce-116">此類型的遠端是透過 `Enter-PSSession` Cmdlet 提供。</span><span class="sxs-lookup"><span data-stu-id="00fce-116">This type of remoting is provided via the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="00fce-117">在上一章中，我將我的網域系統管理員認證儲存在名為 `$Cred` 的變數中。</span><span class="sxs-lookup"><span data-stu-id="00fce-117">In the last chapter, I stored my domain admin credentials in a variable named `$Cred`.</span></span> <span data-ttu-id="00fce-118">如果您尚未這麼做，請繼續將您的網域系統管理員認證儲存在 `$Cred` 變數中。</span><span class="sxs-lookup"><span data-stu-id="00fce-118">If you haven't already done so, go ahead and store your domain admin credentials in the `$Cred` variable.</span></span>

<span data-ttu-id="00fce-119">這麼做可讓您輸入認證一次，並只要您目前的 PowerShell 工作階段作用中，就以每個命令為基礎來使用它們。</span><span class="sxs-lookup"><span data-stu-id="00fce-119">This allows you to enter the credentials once and use them on a per command basis as long as your current PowerShell session is active.</span></span>

```powershell
$Cred = Get-Credential
```

<span data-ttu-id="00fce-120">在名為 dc01 的網域控制站上建立一對一的 PowerShell 遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="00fce-120">Create a one-to-one PowerShell remoting session to the domain controller named dc01.</span></span>

```powershell
Enter-PSSession -ComputerName dc01 -Credential $Cred
```

```Output
[dc01]: PS C:\Users\Administrator\Documents>
```

<span data-ttu-id="00fce-121">請注意，在上一個範例中，PowerShell 提示前面會加上 `[dc01]`。</span><span class="sxs-lookup"><span data-stu-id="00fce-121">Notice that in the previous example that the PowerShell prompt is preceded by `[dc01]`.</span></span> <span data-ttu-id="00fce-122">這表示您處於與名為 dc01 遠端電腦的互動式 PowerShell 工作階段中。</span><span class="sxs-lookup"><span data-stu-id="00fce-122">This means you're in an interactive PowerShell session to the remote computer named dc01.</span></span> <span data-ttu-id="00fce-123">您執行的任何命令會在 dc01 上執行，而不是在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="00fce-123">Any commands you execute run on dc01, not on your local computer.</span></span> <span data-ttu-id="00fce-124">此外，請記住，您只能存取存在於遠端電腦上的 PowerShell 命令，而不是本機電腦上的命令。</span><span class="sxs-lookup"><span data-stu-id="00fce-124">Also, keep in mind that you only have access to the PowerShell commands that exist on the remote computer and not the ones on your local computer.</span></span> <span data-ttu-id="00fce-125">換句話說，如果您在電腦上安裝了其他模組，在遠端電腦上就無法存取它們。</span><span class="sxs-lookup"><span data-stu-id="00fce-125">In other words, if you've installed additional modules on your computer, they aren't accessible on the remote computer.</span></span>

<span data-ttu-id="00fce-126">當您透過一對一的互動式 PowerShell 遠端工作階段連接到遠端電腦時，您實際上是身處於遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="00fce-126">When you're connected to a remote computer via a one-to-one interactive PowerShell remoting session, you're effectively sitting at the remote computer.</span></span> <span data-ttu-id="00fce-127">這些物件是一般物件，就像您在這整個書籍中使用的一樣。</span><span class="sxs-lookup"><span data-stu-id="00fce-127">The objects are normal objects just like the ones you've been working with throughout this entire book.</span></span>

```powershell
[dc01]:  Get-Process | Get-Member
```

```Output
   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
NPM                        AliasProperty  NPM = NonpagedSystemMemorySize64
PM                         AliasProperty  PM = PagedMemorySize64
SI                         AliasProperty  SI = SessionId
VM                         AliasProperty  VM = VirtualMemorySize64
WS                         AliasProperty  WS = WorkingSet64
Disposed                   Event          System.EventHandler Disposed(System.Object, ...
ErrorDataReceived          Event          System.Diagnostics.DataReceivedEventHandler ...
Exited                     Event          System.EventHandler Exited(System.Object, Sy...
OutputDataReceived         Event          System.Diagnostics.DataReceivedEventHandler ...
BeginErrorReadLine         Method         void BeginErrorReadLine()
BeginOutputReadLine        Method         void BeginOutputReadLine()
CancelErrorRead            Method         void CancelErrorRead()
CancelOutputRead           Method         void CancelOutputRead()
Close                      Method         void Close()
CloseMainWindow            Method         bool CloseMainWindow()
CreateObjRef               Method         System.Runtime.Remoting.ObjRef CreateObjRef(...
Dispose                    Method         void Dispose(), void IDisposable.Dispose()
Equals                     Method         bool Equals(System.Object obj)
GetHashCode                Method         int GetHashCode()
GetLifetimeService         Method         System.Object GetLifetimeService()
GetType                    Method         type GetType()
InitializeLifetimeService  Method         System.Object InitializeLifetimeService()
Kill                       Method         void Kill()
Refresh                    Method         void Refresh()
Start                      Method         bool Start()
ToString                   Method         string ToString()
WaitForExit                Method         bool WaitForExit(int milliseconds), void Wai...
WaitForInputIdle           Method         bool WaitForInputIdle(int milliseconds), boo...
__NounName                 NoteProperty   string __NounName=Process
BasePriority               Property       int BasePriority {get;}
Container                  Property       System.ComponentModel.IContainer Container {...
EnableRaisingEvents        Property       bool EnableRaisingEvents {get;set;}
ExitCode                   Property       int ExitCode {get;}
ExitTime                   Property       datetime ExitTime {get;}
Handle                     Property       System.IntPtr Handle {get;}
HandleCount                Property       int HandleCount {get;}
HasExited                  Property       bool HasExited {get;}
Id                         Property       int Id {get;}
MachineName                Property       string MachineName {get;}
MainModule                 Property       System.Diagnostics.ProcessModule MainModule ...
MainWindowHandle           Property       System.IntPtr MainWindowHandle {get;}
MainWindowTitle            Property       string MainWindowTitle {get;}
MaxWorkingSet              Property       System.IntPtr MaxWorkingSet {get;set;}
MinWorkingSet              Property       System.IntPtr MinWorkingSet {get;set;}
Modules                    Property       System.Diagnostics.ProcessModuleCollection M...
NonpagedSystemMemorySize   Property       int NonpagedSystemMemorySize {get;}
NonpagedSystemMemorySize64 Property       long NonpagedSystemMemorySize64 {get;}
PagedMemorySize            Property       int PagedMemorySize {get;}
PagedMemorySize64          Property       long PagedMemorySize64 {get;}
PagedSystemMemorySize      Property       int PagedSystemMemorySize {get;}
PagedSystemMemorySize64    Property       long PagedSystemMemorySize64 {get;}
PeakPagedMemorySize        Property       int PeakPagedMemorySize {get;}
PeakPagedMemorySize64      Property       long PeakPagedMemorySize64 {get;}
PeakVirtualMemorySize      Property       int PeakVirtualMemorySize {get;}
PeakVirtualMemorySize64    Property       long PeakVirtualMemorySize64 {get;}
PeakWorkingSet             Property       int PeakWorkingSet {get;}
PeakWorkingSet64           Property       long PeakWorkingSet64 {get;}
PriorityBoostEnabled       Property       bool PriorityBoostEnabled {get;set;}
PriorityClass              Property       System.Diagnostics.ProcessPriorityClass Prio...
PrivateMemorySize          Property       int PrivateMemorySize {get;}
PrivateMemorySize64        Property       long PrivateMemorySize64 {get;}
PrivilegedProcessorTime    Property       timespan PrivilegedProcessorTime {get;}
ProcessName                Property       string ProcessName {get;}
ProcessorAffinity          Property       System.IntPtr ProcessorAffinity {get;set;}
Responding                 Property       bool Responding {get;}
SafeHandle                 Property       Microsoft.Win32.SafeHandles.SafeProcessHandl...
SessionId                  Property       int SessionId {get;}
Site                       Property       System.ComponentModel.ISite Site {get;set;}
StandardError              Property       System.IO.StreamReader StandardError {get;}
StandardInput              Property       System.IO.StreamWriter StandardInput {get;}
StandardOutput             Property       System.IO.StreamReader StandardOutput {get;}
StartInfo                  Property       System.Diagnostics.ProcessStartInfo StartInf...
StartTime                  Property       datetime StartTime {get;}
SynchronizingObject        Property       System.ComponentModel.ISynchronizeInvoke Syn...
Threads                    Property       System.Diagnostics.ProcessThreadCollection T...
TotalProcessorTime         Property       timespan TotalProcessorTime {get;}
UserProcessorTime          Property       timespan UserProcessorTime {get;}
VirtualMemorySize          Property       int VirtualMemorySize {get;}
VirtualMemorySize64        Property       long VirtualMemorySize64 {get;}
WorkingSet                 Property       int WorkingSet {get;}
WorkingSet64               Property       long WorkingSet64 {get;}
PSConfiguration            PropertySet    PSConfiguration {Name, Id, PriorityClass, Fi...
PSResources                PropertySet    PSResources {Name, Id, Handlecount, WorkingS...
Company                    ScriptProperty System.Object Company {get=$this.Mainmodule....
CPU                        ScriptProperty System.Object CPU {get=$this.TotalProcessorT...
Description                ScriptProperty System.Object Description {get=$this.Mainmod...
FileVersion                ScriptProperty System.Object FileVersion {get=$this.Mainmod...
Path                       ScriptProperty System.Object Path {get=$this.Mainmodule.Fil...
Product                    ScriptProperty System.Object Product {get=$this.Mainmodule....
ProductVersion             ScriptProperty System.Object ProductVersion {get=$this.Main...
[dc01]:
```

<span data-ttu-id="00fce-128">完成遠端電腦的使用時，請使用 `Exit-PSSession` Cmdlet 結束一對一遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="00fce-128">When you're done working with the remote computer, exit the one-to-one remoting session by using the `Exit-PSSession` cmdlet.</span></span>

```powershell
[dc01]:  Exit-PSSession
```

## <a name="one-to-many-remoting"></a><span data-ttu-id="00fce-129">一對多遠端</span><span class="sxs-lookup"><span data-stu-id="00fce-129">One-To-Many Remoting</span></span>

<span data-ttu-id="00fce-130">有時候您可能需要在遠端電腦上以互動方式執行工作。</span><span class="sxs-lookup"><span data-stu-id="00fce-130">Sometimes you may need to perform a task interactively on a remote computer.</span></span> <span data-ttu-id="00fce-131">但若需要同時在多部遠端電腦上執行工作時，遠端的功能就會變得強大得多。</span><span class="sxs-lookup"><span data-stu-id="00fce-131">But remoting is much more powerful when performing a task on multiple remote computers at the same time.</span></span> <span data-ttu-id="00fce-132">使用 `Invoke-Command` Cmdlet，同時對一或多部遠端電腦執行命令。</span><span class="sxs-lookup"><span data-stu-id="00fce-132">Use the `Invoke-Command` cmdlet to run a command against one or more remote computers at the same time.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="00fce-133">在上述範例中，會查詢三部伺服器以取得 Windows 時間服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="00fce-133">In the previous example, three servers were queried for the status of the Windows Time service.</span></span> <span data-ttu-id="00fce-134">`Get-Service` Cmdlet 放在 `Invoke-Command` 的指令碼區塊內。</span><span class="sxs-lookup"><span data-stu-id="00fce-134">The `Get-Service` cmdlet was placed inside the script block of `Invoke-Command`.</span></span> <span data-ttu-id="00fce-135">`Get-Service` 實際上會在遠端電腦上執行，而結果則會以已還原序列化物件的形式傳回到您的本機電腦。</span><span class="sxs-lookup"><span data-stu-id="00fce-135">`Get-Service` actually runs on the remote computer and the results are returned to your local computer as deserialized objects.</span></span>

<span data-ttu-id="00fce-136">將前一個命令以管線傳送至 `Get-Member` 顯示結果確實為已還原序列化的物件。</span><span class="sxs-lookup"><span data-stu-id="00fce-136">Piping the previous command to `Get-Member` shows that the results are indeed deserialized objects.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred | Get-Member
```

```Output
   TypeName: Deserialized.System.ServiceProcess.ServiceController

Name                MemberType   Definition
----                ----------   ----------
GetType             Method       type GetType()
ToString            Method       string ToString(), string ToString(string format, Sys...
Name                NoteProperty string Name=W32time
PSComputerName      NoteProperty string PSComputerName=sql02
PSShowComputerName  NoteProperty bool PSShowComputerName=True
RequiredServices    NoteProperty Deserialized.System.ServiceProcess.ServiceController[...
RunspaceId          NoteProperty guid RunspaceId=570313c4-ac84-4109-bf67-c6b33236af0a
CanPauseAndContinue Property     System.Boolean {get;set;}
CanShutdown         Property     System.Boolean {get;set;}
CanStop             Property     System.Boolean {get;set;}
Container           Property      {get;set;}
DependentServices   Property     Deserialized.System.ServiceProcess.ServiceController[...
DisplayName         Property     System.String {get;set;}
MachineName         Property     System.String {get;set;}
ServiceHandle       Property     System.String {get;set;}
ServiceName         Property     System.String {get;set;}
ServicesDependedOn  Property     Deserialized.System.ServiceProcess.ServiceController[...
ServiceType         Property     System.String {get;set;}
Site                Property      {get;set;}
StartType           Property     System.String {get;set;}
Status              Property     System.String {get;set;}
```

<span data-ttu-id="00fce-137">請注意，已還原序列化的物件上會缺少大部分的方法。</span><span class="sxs-lookup"><span data-stu-id="00fce-137">Notice that the majority of the methods are missing on deserialized objects.</span></span> <span data-ttu-id="00fce-138">這表示它們不是即時物件，而是惰性的。</span><span class="sxs-lookup"><span data-stu-id="00fce-138">This means they're not live objects; they're inert.</span></span> <span data-ttu-id="00fce-139">您無法使用已還原序列化的物件來啟動或停止服務，因為它是在遠端電腦上執行命令時，該物件狀態的快照集。</span><span class="sxs-lookup"><span data-stu-id="00fce-139">You can't start or stop a service using a deserialized object because it's a snapshot of the state of that object the point when the command ran on the remote computer.</span></span>

<span data-ttu-id="00fce-140">不過，這並不表示您無法使用方法搭配 `Invoke-Command` 來啟動或停止服務。</span><span class="sxs-lookup"><span data-stu-id="00fce-140">That doesn't mean you can't start or stop a service using a method with `Invoke-Command` though.</span></span> <span data-ttu-id="00fce-141">只是表示必須在遠端工作階段中呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="00fce-141">It just means that the method has to be called in the remote session.</span></span>

<span data-ttu-id="00fce-142">我將使用 **Stop()** 方法來停止這三部遠端伺服器上的 Windows 時間服務，以證明這點。</span><span class="sxs-lookup"><span data-stu-id="00fce-142">I'll stop the Windows Time service on all three of those remote servers using the **Stop()** method to prove this point.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {(Get-Service -Name W32time).Stop()} -Credential $Cred
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="00fce-143">如前一章所述，如果有 Cmdlet 可用於完成工作，我建議使用它，而不是使用方法。</span><span class="sxs-lookup"><span data-stu-id="00fce-143">As mentioned in a previous chapter, if a cmdlet exists for accomplishing a task, I recommend using it instead of using a method.</span></span> <span data-ttu-id="00fce-144">在先前的案例中，我建議使用 `Stop-Service` Cmdlet，而不是 stop 方法。</span><span class="sxs-lookup"><span data-stu-id="00fce-144">In the previous scenario, I recommend using the `Stop-Service` cmdlet instead of the stop method.</span></span> <span data-ttu-id="00fce-145">我選擇使用 **Stop()** 方法來證明一點，因為許多人對於在使用 PowerShell 遠端時無法呼叫方法有所誤解。</span><span class="sxs-lookup"><span data-stu-id="00fce-145">I chose to use the **Stop()** method to prove a point since many people are under the misconception that methods can't be called when using PowerShell remoting.</span></span> <span data-ttu-id="00fce-146">因為其已還原序列化，所有無法在傳回的物件上呼叫它們，但可以在遠端工作階段本身呼叫。</span><span class="sxs-lookup"><span data-stu-id="00fce-146">They can't be called on the object that's returned because it's deserialized, but they can be called in the remote session itself.</span></span>

## <a name="powershell-sessions"></a><span data-ttu-id="00fce-147">PowerShell 工作階段</span><span class="sxs-lookup"><span data-stu-id="00fce-147">PowerShell Sessions</span></span>

<span data-ttu-id="00fce-148">在上一節的最後一個範例中，我使用 `Invoke-Command` Cmdlet 執行了兩個命令。</span><span class="sxs-lookup"><span data-stu-id="00fce-148">In the last example in the previous section, I ran two commands using the `Invoke-Command` cmdlet.</span></span>
<span data-ttu-id="00fce-149">這表示必須設定兩個不同的工作階段，並終止才能執行這兩個命令。</span><span class="sxs-lookup"><span data-stu-id="00fce-149">That means two separate sessions had to be set up and torn down to run those two commands.</span></span>

<span data-ttu-id="00fce-150">類似於第 7 章所討論的 CIM 工作階段，連線至遠端電腦的 PowerShell 工作階段可以用來對遠端電腦執行多個命令，而不會有每個個別命令使用新工作階段的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="00fce-150">Similar to the CIM sessions discussed in Chapter 7, a PowerShell session to a remote computer can be used to run multiple commands against the remote computer without the overhead of a new session for each individual command.</span></span>

<span data-ttu-id="00fce-151">對我們在本章中所使用的三部電腦 (即 DC01、SQL02 和 WEB01) 建立 PowerShell 工作階段連線。</span><span class="sxs-lookup"><span data-stu-id="00fce-151">Create a PowerShell session to each of the three computers we've been working with in this chapter, DC01, SQL02, and WEB01.</span></span>

```powershell
$Session = New-PSSession -ComputerName dc01, sql02, web01 -Credential $Cred
```

<span data-ttu-id="00fce-152">現在使用名為 `$Session` 的變數，使用方法來啟動 Windows 時間服務，並檢查服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="00fce-152">Now use the variable named `$Session` to start the Windows Time service using a method and check the status of the service.</span></span>

```powershell
Invoke-Command -Session $Session {(Get-Service -Name W32time).Start()}
Invoke-Command -Session $Session {Get-Service -Name W32time}
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="00fce-153">一旦使用替代認證建立工作階段，就不再需要在每次執行命令時指定認證。</span><span class="sxs-lookup"><span data-stu-id="00fce-153">Once the session is created using alternate credentials, it's no longer necessary to specify the credentials each time a command is run.</span></span>

<span data-ttu-id="00fce-154">當您使用完工作階段時，請務必將它們移除。</span><span class="sxs-lookup"><span data-stu-id="00fce-154">When you're finished using the sessions, be sure to remove them.</span></span>

```powershell
Get-PSSession | Remove-PSSession
```

## <a name="summary"></a><span data-ttu-id="00fce-155">摘要</span><span class="sxs-lookup"><span data-stu-id="00fce-155">Summary</span></span>

<span data-ttu-id="00fce-156">在本章中，您已了解 PowerShell 遠端、如何在與一部遠端電腦的互動式工作階段中執行命令，以及如何使用一對多遠端對多部電腦執行命令。</span><span class="sxs-lookup"><span data-stu-id="00fce-156">In this chapter you've learned about PowerShell remoting, how to run commands in an interactive session with one remote computer, and how to run commands against multiple computers using one-to-many remoting.</span></span> <span data-ttu-id="00fce-157">您也已了解在對同一部遠端電腦執行多個命令時，使用 PowerShell 工作階段的優點。</span><span class="sxs-lookup"><span data-stu-id="00fce-157">You've also learned the benefits of using a PowerShell session when running multiple commands against the same remote computer.</span></span>

## <a name="review"></a><span data-ttu-id="00fce-158">檢閱</span><span class="sxs-lookup"><span data-stu-id="00fce-158">Review</span></span>

1. <span data-ttu-id="00fce-159">如何啟用 PowerShell 遠端？</span><span class="sxs-lookup"><span data-stu-id="00fce-159">How do you enable PowerShell remoting?</span></span>
1. <span data-ttu-id="00fce-160">用於啟動與遠端電腦的互動式工作階段的 PowerShell 命令為何？</span><span class="sxs-lookup"><span data-stu-id="00fce-160">What is the PowerShell command for starting an interactive session with a remote computer?</span></span>
1. <span data-ttu-id="00fce-161">使用 PowerShell 遠端工作階段相較於對每個命令指定電腦名稱的優點為何？</span><span class="sxs-lookup"><span data-stu-id="00fce-161">What is a benefit of using a PowerShell remoting session versus just specifying the computer name with each command?</span></span>
1. <span data-ttu-id="00fce-162">PowerShell 遠端工作階段可以搭配一對一遠端工作階段使用嗎？</span><span class="sxs-lookup"><span data-stu-id="00fce-162">Can a PowerShell remoting session be used with a one-to-one remoting session?</span></span>
1. <span data-ttu-id="00fce-163">Cmdlet 傳回的物件類型，與使用 `Invoke-Command` 對遠端電腦執行這些相同的 Cmdlet 時所傳回的有何差異？</span><span class="sxs-lookup"><span data-stu-id="00fce-163">What is the difference in the type of objects that are returned by cmdlets versus those returned when running those same cmdlets against remote computers with `Invoke-Command`?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="00fce-164">建議閱讀資料</span><span class="sxs-lookup"><span data-stu-id="00fce-164">Recommended Reading</span></span>

- <span data-ttu-id="00fce-165">[about_Remote][]</span><span class="sxs-lookup"><span data-stu-id="00fce-165">[about_Remote][]</span></span>
- <span data-ttu-id="00fce-166">[about_Remote_FAQ][]</span><span class="sxs-lookup"><span data-stu-id="00fce-166">[about_Remote_FAQ][]</span></span>
- <span data-ttu-id="00fce-167">[about_Remote_Output][]</span><span class="sxs-lookup"><span data-stu-id="00fce-167">[about_Remote_Output][]</span></span>
- <span data-ttu-id="00fce-168">[about_Remote_Requirements][]</span><span class="sxs-lookup"><span data-stu-id="00fce-168">[about_Remote_Requirements][]</span></span>
- <span data-ttu-id="00fce-169">[about_Remote_Troubleshooting][]</span><span class="sxs-lookup"><span data-stu-id="00fce-169">[about_Remote_Troubleshooting][]</span></span>
- <span data-ttu-id="00fce-170">[about_Remote_Variables][]</span><span class="sxs-lookup"><span data-stu-id="00fce-170">[about_Remote_Variables][]</span></span>

<!-- link references -->
[about_Remote]: /powershell/module/microsoft.powershell.core/about/about_remote
[about_Remote_FAQ]: /powershell/module/microsoft.powershell.core/about/about_remote_faq
[about_Remote_Output]: /powershell/module/microsoft.powershell.core/about/about_remote_output
[about_Remote_Requirements]: /powershell/module/microsoft.powershell.core/about/about_remote_requirements
[about_Remote_Troubleshooting]: /powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting
[about_Remote_Variables]: /powershell/module/microsoft.powershell.core/about/about_remote_variables
[Breaking changes in PowerShell 6.0]: /powershell/scripting/whats-new/breaking-changes-ps6#remove--protocol-from--computer-cmdlets-5277
