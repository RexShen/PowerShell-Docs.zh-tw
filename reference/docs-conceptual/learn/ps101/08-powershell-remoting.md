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
# <a name="chapter-8---powershell-remoting"></a>第 8 章 - PowerShell 遠端

PowerShell 有許多不同的方式，可以對遠端電腦執行命令。 在上一章中，您已看到如何使用 CIM Cmdlet 從遠端查詢 WMI。 PowerShell 也包含具有內建 **ComputerName** 參數的數個 Cmdlet。

如下列範例所示，`Get-Command` 可以與 **ParameterName** 參數搭配使用，以判斷哪些命令具有 **ComputerName** 參數。

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

`Get-Process` 和 `Get-Hotfix` 之類的命令具有 **ComputerName** 參數。 這不是 Microsoft 對遠端電腦上執行命令將採取的長期指示。 即使您發現某個命令具有 **ComputerName** 參數，您還是需要指定替代的認證，而且其不會有 **Credential** 參數。 而如果您決定從提高權限的帳戶執行 PowerShell，則您與遠端電腦之間的防火牆可能會封鎖要求。

若要使用本章所示範的 PowerShell 遠端命令，您必須在遠端電腦上啟用 PowerShell 遠端。 使用 `Enable-PSRemoting` Cmdlet 來啟用 PowerShell 遠端。

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

## <a name="one-to-one-remoting"></a>一對一遠端

如果您想要讓遠端工作階段成為互動式，則您需要一對一遠端。
此類型的遠端是透過 `Enter-PSSession` Cmdlet 提供。

在上一章中，我將我的網域系統管理員認證儲存在名為 `$Cred` 的變數中。 如果您尚未這麼做，請繼續將您的網域系統管理員認證儲存在 `$Cred` 變數中。

這麼做可讓您輸入認證一次，並只要您目前的 PowerShell 工作階段作用中，就以每個命令為基礎來使用它們。

```powershell
$Cred = Get-Credential
```

在名為 dc01 的網域控制站上建立一對一的 PowerShell 遠端工作階段。

```powershell
Enter-PSSession -ComputerName dc01 -Credential $Cred
```

```Output
[dc01]: PS C:\Users\Administrator\Documents>
```

請注意，在上一個範例中，PowerShell 提示前面會加上 `[dc01]`。 這表示您處於與名為 dc01 遠端電腦的互動式 PowerShell 工作階段中。 您執行的任何命令會在 dc01 上執行，而不是在本機電腦上執行。 此外，請記住，您只能存取存在於遠端電腦上的 PowerShell 命令，而不是本機電腦上的命令。 換句話說，如果您在電腦上安裝了其他模組，在遠端電腦上就無法存取它們。

當您透過一對一的互動式 PowerShell 遠端工作階段連接到遠端電腦時，您實際上是身處於遠端電腦上。 這些物件是一般物件，就像您在這整個書籍中使用的一樣。

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

完成遠端電腦的使用時，請使用 `Exit-PSSession` Cmdlet 結束一對一遠端工作階段。

```powershell
[dc01]:  Exit-PSSession
```

## <a name="one-to-many-remoting"></a>一對多遠端

有時候您可能需要在遠端電腦上以互動方式執行工作。 但若需要同時在多部遠端電腦上執行工作時，遠端的功能就會變得強大得多。 使用 `Invoke-Command` Cmdlet，同時對一或多部遠端電腦執行命令。

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

在上述範例中，會查詢三部伺服器以取得 Windows 時間服務的狀態。 `Get-Service` Cmdlet 放在 `Invoke-Command` 的指令碼區塊內。 `Get-Service` 實際上會在遠端電腦上執行，而結果則會以已還原序列化物件的形式傳回到您的本機電腦。

將前一個命令以管線傳送至 `Get-Member` 顯示結果確實為已還原序列化的物件。

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

請注意，已還原序列化的物件上會缺少大部分的方法。 這表示它們不是即時物件，而是惰性的。 您無法使用已還原序列化的物件來啟動或停止服務，因為它是在遠端電腦上執行命令時，該物件狀態的快照集。

不過，這並不表示您無法使用方法搭配 `Invoke-Command` 來啟動或停止服務。 只是表示必須在遠端工作階段中呼叫方法。

我將使用 **Stop()** 方法來停止這三部遠端伺服器上的 Windows 時間服務，以證明這點。

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

如前一章所述，如果有 Cmdlet 可用於完成工作，我建議使用它，而不是使用方法。 在先前的案例中，我建議使用 `Stop-Service` Cmdlet，而不是 stop 方法。 我選擇使用 **Stop()** 方法來證明一點，因為許多人對於在使用 PowerShell 遠端時無法呼叫方法有所誤解。 因為其已還原序列化，所有無法在傳回的物件上呼叫它們，但可以在遠端工作階段本身呼叫。

## <a name="powershell-sessions"></a>PowerShell 工作階段

在上一節的最後一個範例中，我使用 `Invoke-Command` Cmdlet 執行了兩個命令。
這表示必須設定兩個不同的工作階段，並終止才能執行這兩個命令。

類似於第 7 章所討論的 CIM 工作階段，連線至遠端電腦的 PowerShell 工作階段可以用來對遠端電腦執行多個命令，而不會有每個個別命令使用新工作階段的額外負荷。

對我們在本章中所使用的三部電腦 (即 DC01、SQL02 和 WEB01) 建立 PowerShell 工作階段連線。

```powershell
$Session = New-PSSession -ComputerName dc01, sql02, web01 -Credential $Cred
```

現在使用名為 `$Session` 的變數，使用方法來啟動 Windows 時間服務，並檢查服務的狀態。

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

一旦使用替代認證建立工作階段，就不再需要在每次執行命令時指定認證。

當您使用完工作階段時，請務必將它們移除。

```powershell
Get-PSSession | Remove-PSSession
```

## <a name="summary"></a>摘要

在本章中，您已了解 PowerShell 遠端、如何在與一部遠端電腦的互動式工作階段中執行命令，以及如何使用一對多遠端對多部電腦執行命令。 您也已了解在對同一部遠端電腦執行多個命令時，使用 PowerShell 工作階段的優點。

## <a name="review"></a>檢閱

1. 如何啟用 PowerShell 遠端？
1. 用於啟動與遠端電腦的互動式工作階段的 PowerShell 命令為何？
1. 使用 PowerShell 遠端工作階段相較於對每個命令指定電腦名稱的優點為何？
1. PowerShell 遠端工作階段可以搭配一對一遠端工作階段使用嗎？
1. Cmdlet 傳回的物件類型，與使用 `Invoke-Command` 對遠端電腦執行這些相同的 Cmdlet 時所傳回的有何差異？

## <a name="recommended-reading"></a>建議閱讀資料

- [about_Remote][]
- [about_Remote_FAQ][]
- [about_Remote_Output][]
- [about_Remote_Requirements][]
- [about_Remote_Troubleshooting][]
- [about_Remote_Variables][]

<!-- link references -->
[about_Remote]: /powershell/module/microsoft.powershell.core/about/about_remote
[about_Remote_FAQ]: /powershell/module/microsoft.powershell.core/about/about_remote_faq
[about_Remote_Output]: /powershell/module/microsoft.powershell.core/about/about_remote_output
[about_Remote_Requirements]: /powershell/module/microsoft.powershell.core/about/about_remote_requirements
[about_Remote_Troubleshooting]: /powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting
[about_Remote_Variables]: /powershell/module/microsoft.powershell.core/about/about_remote_variables
[Breaking changes in PowerShell 6.0]: /powershell/scripting/whats-new/breaking-changes-ps6#remove--protocol-from--computer-cmdlets-5277
