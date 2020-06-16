---
title: 單行式與管線
description: PowerShell 單行程式碼是包含多個命令的一個連續管線，用來完成單一工作。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4244c34628e8f2ee8d54471fc2d5ad81a870e739
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438059"
---
# <a name="chapter-4---one-liners-and-the-pipeline"></a>第 4 章 - 單行程式碼與管線

當我初次開始學習 PowerShell 時，如果我無法使用 PowerShell 單行程式碼來完成某個工作，我就會回到 GUI。 一段時間後，我加強了我撰寫指令碼、函式和模組的技能。 不要讓您自己被可能會在網際網路上看到的一些更進階範例擊敗了。 沒有人是使用 PowerShell 的自然專家。 我們都曾經是新手。

我有個建議可以給仍在使用 GUI 進行管理的您：在系統管理工作站上安裝管理工具，並從遠端系統管理您的伺服器。 這麼一來，伺服器是否執行作業系統的 GUI 或 Server Core 安裝並不重要。
它將協助您為使用 PowerShell 從遠端管理伺服器進行準備。

如同前幾章，請務必在您的 Windows 10 實驗室環境電腦上按照步驟執行。

## <a name="one-liners"></a>單行程式碼

PowerShell 單行程式碼是一個連續管線，但不一定是在一個實體行上的命令。 並非在單一實體行上的所有命令都是單行程式碼。

即使下列命令在多個實體行上，但它是 PowerShell 單行程式碼，因為它是一個連續的管線。 我可以在一個實體行上撰寫這些命令，但是我選擇在管線符號處換行。 管線符號是在 PowerShell 中所允許自然換行符號的其中一個字元。

```powershell
Get-Service |
  Where-Object CanPauseAndContinue -eq $true |
    Select-Object -Property *
```

```Output
Name                : LanmanWorkstation
RequiredServices    : {NSI, MRxSmb20, Bowser}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Workstation
DependentServices   : {SessionEnv, Netlogon, Browser}
MachineName         : .
ServiceName         : LanmanWorkstation
ServicesDependedOn  : {NSI, MRxSmb20, Bowser}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : Netlogon
RequiredServices    : {LanmanWorkstation}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Netlogon
DependentServices   : {}
MachineName         : .
ServiceName         : Netlogon
ServicesDependedOn  : {LanmanWorkstation}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : vmicheartbeat
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Heartbeat Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicheartbeat
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmickvpexchange
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Data Exchange Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmickvpexchange
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicrdv
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Remote Desktop Virtualization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicrdv
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicshutdown
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Guest Shutdown Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicshutdown
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmictimesync
RequiredServices    : {VmGid}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Time Synchronization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmictimesync
ServicesDependedOn  : {VmGid}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicvss
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Volume Shadow Copy Requestor
DependentServices   : {}
MachineName         : .
ServiceName         : vmicvss
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : Winmgmt
RequiredServices    : {RPCSS}
CanPauseAndContinue : True
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Management Instrumentation
DependentServices   : {wscsvc, NcaSvc, iphlpsvc}
MachineName         : .
ServiceName         : Winmgmt
ServicesDependedOn  : {RPCSS}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :
```

自然換行符號可能發生在常用的字元，包括逗號 (`,`) 和左括弧 (`[`)、大括弧 (`{`) 和括弧 (`(`)。 其他不常用的項目包括分號 (`;`)、等號 (`=`)，以及開頭的左單引號和雙引號 (`'`、`"`)。

使用反引號 (`` ` ``) 或抑音符號字元作為行接續字元，是具爭議的主題。 我的建議是儘量試著避免這種情況。 我經常看到在自然換行符號字元之後緊接著使用反引號撰寫的 PowerShell 命令。
沒有任何原因應該在那裡使用該符號。

```powershell
Get-Service -Name w32time |
>> Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

以上兩個範例中所顯示的命令可在 PowerShell 主控台中正常執行。 但是，如果您嘗試在 PowerShell ISE 的主控台窗格中執行它們，就會產生錯誤。 PowerShell ISE 的主控台窗格不會如同 PowerShell 主控台般，等候在下一行輸入命令的其餘部分。 若要在 PowerShell ISE 的主控台窗格中避免此問題，請使用 <kbd>Shift</kbd>+<kbd>Enter</kbd>，而不只是在另一行繼續命令時按 <kbd>Enter</kbd>。

下一個範例不是 PowerShell 單行程式碼，因為它不是連續管線。 這是在一行上的兩個不同命令，以分號分隔。

```powershell
$Service = 'w32time'; Get-Service -Name $Service
```

```powershell
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

許多程式設計和指令碼語言要求在每一行的結尾都需要分號。 雖然可以在 PowerShell 中使用該方式，但不建議您這樣做，因為這是不必要的。

## <a name="filtering-left"></a>篩選左側

本章所示的命令結果已篩選至子集。 例如，`Get-Service` 與 **Name** 參數搭配使用，以篩選只傳回至 Windows 時間服務的服務清單。

在管線中，您一定會想要儘快將結果篩選到您要尋找的內容。 這是在第一個 (或最左邊的) 命令上使用參數來完成。
這有時稱為_篩選左側_。

下列範例使用 `Get-Service` 的 **Name** 參數，立即將結果篩選為僅 Windows 時間服務。

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

要看到將命令以管線傳送至 `Where-Object` 以執行篩選的範例並不常見。

```powershell
Get-Service | Where-Object Name -eq w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Windows Time
```

第一個範例會在來源篩選，並僅傳回 Windows 時間服務的結果。
第二個範例會傳回所有服務，然後將它們傳送至另一個命令，以執行篩選。 雖然此動作在此範例中看起來問題不重要，但請想像一下，如果是要查詢 Active Directory 使用者的清單。 您是否真的想要從 Active Directory 傳回數千個使用者帳戶的資訊，只是為了將該資訊以管線傳送至可將它們篩選成較小子集的另一個命令？ 我的建議是，即使看起來似乎不重要，也一律進行篩選左側。 這麼做的話，當自動篩選左側真的很重要的時候，您就會習慣它了。

曾經有人告訴我，指定命令的順序並不重要。 那絕不是事實。 執行篩選時，指定命令的順序確實很重要。 例如，假設您使用 `Select-Object` 來僅選取幾個屬性，以及使用 `Where-Object` 來篩選不在選取範圍中的屬性。 在該案例中，必須先進行篩選，否則當嘗試執行篩選時，屬性將不會存在於管線中。

```powershell
Get-Service |
Select-Object -Property DisplayName, Running, Status |
Where-Object CanPauseAndContinue
```

上一個範例中的命令不會傳回任何結果，因為當 `Select-Object` 的結果以管線傳送至 `Where-Object`時，**CanStopAndContinue** 屬性不存在。 該特定屬性未被「選取」。 基本上，它已被篩選掉。反轉 `Select-Object` 和 `Where-Object` 的順序會產生所需的結果。

```powershell
Get-Service |
Where-Object CanPauseAndContinue |
Select-Object -Property DisplayName, Status
```

```Output
DisplayName                                    Status
-----------                                    ------
Workstation                                    Running
Netlogon                                       Running
Hyper-V Heartbeat Service                      Running
Hyper-V Data Exchange Service                  Running
Hyper-V Remote Desktop Virtualization Service  Running
Hyper-V Guest Shutdown Service                 Running
Hyper-V Time Synchronization Service           Running
Hyper-V Volume Shadow Copy Requestor           Running
Windows Management Instrumentation             Running
```

## <a name="the-pipeline"></a>管線

正如您目前在本書中所看到的許多範例，許多時候一個命令的輸出可以作為另一個命令的輸入。 在第 3 章中，`Get-Member` 是用來判斷命令所產生的物件類型。 第 3 章也示範如何使用 `Get-Command` 的 **ParameterType** 參數來判斷接受該類型輸入的是哪些命令，但不一定是透過管線輸入。

視命令說明的詳盡程度而定，可能會包含 **INPUTS** 和 **OUTPUTS** 區段。

```powershell
help Stop-Service -Full
```

```Output
...
INPUTS
    System.ServiceProcess.ServiceController, System.String
        You can pipe a service object or a string that contains the name of a service
        to this cmdlet.

OUTPUTS
    None, System.ServiceProcess.ServiceController
        This cmdlet generates a System.ServiceProcess.ServiceController object that
        represents the service, if you use the PassThru parameter. Otherwise, this
        cmdlet does not generate any output.
...
```

在先前的結果中只顯示說明的相關區段。 如您所見，**INPUTS** 區段指出您可以將 **ServiceController** 或 **String** 物件以管線傳送至 `Stop-Service` Cmdlet。 它不會告訴您接受該類型輸入的是哪些參數。 用來判斷該資訊最簡單的方法之一，就是查看 `Stop-Service` Cmdlet 的完整版本說明中的不同參數。

```powershell
help Stop-Service -Full
```

```powershell
...
-DisplayName <String[]>
    Specifies the display names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false

-InputObject <ServiceController[]>
    Specifies ServiceController objects that represent the services to stop. Enter a
    variable that contains the objects, or type a command or expression that gets the
    objects.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByValue)
    Accept wildcard characters?  false

-Name <String[]>
    Specifies the service names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  false
...
```

重申，我只會在先前的結果集中顯示說明的相關部分。 請注意，**DisplayName** 參數不會接受管線輸入，**InputObject** 參數會接受管線輸入 **by value** 作為 **ServiceController** 物件，而 **Name** 參數會接受管線輸入 **by value** 作為 **string** 物件。 它也會接受管線輸入 **by property name**。

當參數同時接受 by property name 和 by value 的管線輸入時，它一律會先嘗試 **by value**。 如果 **by value** 失敗，則會嘗試 **by property name**。 **by value** 有點誤導。 我偏好稱它為 **by type**。 這表示如果您將產生 **ServiceController** 物件類型之命令的結果傳送至 `Stop-Service`，它會將該輸入的繫結以管線傳送至 **InputObject** 參數。 但是，如果您將產生 **String** 輸出命令的結果傳送至 `Stop-Service`，它會將它繫結至 **Name** 參數。 如果您將不會產生 **ServiceController** 或 **String** 物件的命令結果以管線傳送至 `Stop-Service`，但它確實產生包含名為 **Name** 屬性的輸出，則會將 **Name** 屬性從輸出繫結至 `Stop-Service` 的 **Name** 參數。

判斷 `Get-Service` 命令所產生的輸出類型。

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController
```

`Get-Service` 會產生 ServiceController 物件類型。

如先前在說明中所見，`Stop-Service` 的 **InputObject** 參數會透過管線 **by value** (by type) 接受 **ServiceController** 物件。 這表示當 `Get-Service` Cmdlet 的結果透過管線傳送到 `Stop-Service` 時，它們會繫結至 `Stop-Service` 的 **InputObject** 參數。

```powershell
Get-Service -Name w32time | Stop-Service
```

現在嘗試字串輸入。 將 `w32time` 以管線傳送至 `Get-Member` 只是為了確認它是字串。

```powershell
'w32time' | Get-Member
```

```Output
   TypeName: System.String
```

如先前在說明中所顯示，將字串以管線傳送至 `Stop-Service`，會將它 **by value** 繫結至 `Stop-Service` 的 **Name** 參數。 藉由將 `w32time` 以管線傳送至 `Stop-Service` 來測試此行為。

```powershell
'w32time' | Stop-Service
```

請注意，在上一個範例中，我使用了單引號來括住字串 `w32time`。 在 PowerShell 中，除非加上引號的字串內容包含需要展開為其實際值的變數，否則您應該一律使用單引號，而不是雙引號。 藉由使用單引號，PowerShell 就不需要剖析引號內包含的內容，因此您的程式碼執行速度會更快。

建立自訂物件，以依據屬性名稱，針對 `Stop-Service` 的 **Name** 參數來測試管線輸入。

```powershell
$CustomObject = [pscustomobject]@{
>> Name = 'w32time'
>> }
```

**CustomObject** 變數的內容是 **PSCustomObject** 物件類型，而其包含名為 **Name** 的屬性。

```powershell
$CustomObject | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty string Name=w32time
```

如果您要以引號括住 `$CustomObject` 變數，您會想要使用雙引號。
否則，使用單引號，會將常值字串 `$CustomObject` (而非變數所包含的值) 以管線傳送至 `Get-Member`。

雖然將 `$CustomObject` 的內容以管線傳送至 `Stop-Service` Cmdlet 會繫結至 **Name** 參數，但這次它會 **by property name** 繫結，而不是 **by value**，因為 `$CustomObject` 的內容是具有名為 **Name** 屬性的物件。

在此範例中，我使用不同的屬性名稱 (例如 **Service**) 來建立另一個自訂物件。

```powershell
$CustomObject = [pscustomobject]@{
  Service = 'w32time'
}
```

嘗試使用管線將 `$CustomObject` 傳送至 `Stop-Service` 時，會產生錯誤，因為它不會產生 **ServiceController** 或 **String** 物件，而且沒有名為 **Name** 的屬性。

```powershell
$CustomObject | Stop-Service
```

```Output
Stop-Service : Cannot find any service with service name '@{Service=w32time}'.
At line:1 char:17
+ $CustomObject | Stop-Service
+
    + CategoryInfo          : ObjectNotFound: (@{Service=w32time}:String) [Stop-Service]
   , ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.S
   topServiceCommand
```

如果某個命令的輸出未與另一個命令的管線輸入選項對齊，則可以使用 `Select-Object` 來重新命名屬性，使得屬性正確對齊。

```powershell
$CustomObject |
  Select-Object -Property @{name='Name';expression={$_.Service}} |
    Stop-Service
```

在此範例中，`Select-Object` 用來將 **Service** 屬性重新命名為 **Name** 的屬性。

此範例的語法一開始可能有點複雜。 我所了解到的是，您永遠不需透過複製並貼上程式碼來學習語法。 花時間輸入程式碼。 幾次之後，就會變成您的第二個本質。 有多個監視器是一項很大的優點，因為您可以在一個畫面上顯示範例程式碼，並在另一個螢幕上輸入程式碼。

有時候，您可能會想要使用不接受管線輸入的參數。 下列範例示範如何使用一個命令的輸出作為另一個命令的輸入。 首先，將幾個 Windows 服務的顯示名稱儲存至文字檔中。

```powershell
'Background Intelligent Transfer Service', 'Windows Time' |
Out-File -FilePath $env:TEMP\services.txt
```

您可以執行命令，在括弧中提供所需的輸出，作為需要輸入之命令的參數值。

```powershell
Stop-Service -DisplayName (Get-Content -Path $env:TEMP\services.txt)
```

對於記得其運作方式的您，這就像是代數中的運算順序。 括弧內的命令一律在命令的外部部分之前執行。

## <a name="powershellget"></a>PowerShellGet

PowerShellGet 是 PowerShell 模組，其中包含用於往返 NuGet 儲存庫探索、安裝、發佈及更新 PowerShell 模組 (和其他成品) 的命令。 PowerShellGet 隨附 PowerShell 5.0 版和更新版本。 其以 PowerShell 3.0 版和更新版本的個別下載形式提供。

Microsoft 會主控名為 [PowerShell 資源庫][]的線上 NuGet 儲存庫。 雖然此儲存庫是由 Microsoft 所主控，但儲存庫中包含的大部分模組都不是由 Microsoft 所撰寫。 從 PowerShell 資源庫取得的任何程式碼，都應該在隔離的測試環境中徹底檢閱，然後才將其視為適合在生產環境中使用。

大部分的公司都想要主控自己的內部私人 NuGet 儲存庫，在其中，他們能夠張貼僅限內部使用的模組，以及從其他來源下載的模組 (在將其驗證為非惡意的情況下)。

使用 PowerShellGet 模組中的 `Find-Module` Cmdlet，在 PowerShell 資源庫中尋找我撰寫、名為 MrToolkit 的模組。

```powershell
Find-Module -Name MrToolkit
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with
NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or
'C:\Users\MrAdmin\AppData\Local\PackageManagement\ProviderAssemblies'. You can also
install the NuGet provider by running 'Install-PackageProvider -Name NuGet
-MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the
NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1        MrToolkit                           PSGallery            Misc PowerShell Tools
```

第一次使用 PowerShellGet 模組中的其中一個命令時，系統會提示您安裝 NuGet 提供者。

若要安裝 MrToolkit 模組，請將前一個命令以管線傳送至 `Install-Module`。

```powershell
Find-Module -Name MrToolkit | Install-Module
```

```Output
Untrusted repository
You are installing the modules from an untrusted repository. If you trust this
repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet.
Are you sure you want to install the modules from
'https://www.powershellgallery.com/api/v2/'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): y
```

由於 PowerShell 資源庫是未受信任的儲存庫，因此系統會提示您核准安裝模組。

## <a name="finding-pipeline-input-the-easy-way"></a>以簡單的方式尋找管線輸入

MrToolkit 模組包含名為 `Get-MrPipelineInput` 的函式。 此 Cmdlet 可以用來輕鬆地判斷命令的哪些參數會接受管線輸入、所接受的物件類型，以及它們是否接受管線輸入 **by value** 或 **by property name**。

```powershell
Get-MrPipelineInput -Name Stop-Service
```

```Output
ParameterName ParameterType                             ValueFromPipeline ValueFromPipelineByPropertyName
------------- -------------                             ----------------- ---------------
InputObject   System.ServiceProcess.ServiceController[]              True           False
Name          System.String[]                                        True            True
```

如您所見，我們先前透過篩檢說明所判斷的資訊，很容易就能使用此函式來判斷。

## <a name="summary"></a>摘要

在本章中，您已了解 PowerShell 單行程式碼。 您已了解命令所在的實際行數，與它是否為 PowerShell 單行程式碼無關。 您也已了解有關篩選左側、管線和 PowerShellGet。

## <a name="review"></a>檢閱

1. 什麼是 PowerShell 單行程式碼？
1. PowerShell 中可能會發生自然換行符號的部分字元有哪些？
1. 為什麼應使用左側篩選？
1. PowerShell 命令可以接受管線輸入的兩個方式為何？
1. 為什麼您不應該信任在 PowerShell 資源庫中找到的命令？

## <a name="recommended-reading"></a>建議閱讀資料

- [about_Pipelines][]
- [about_Command_Syntax][]
- [about_Parameters][]
- [PowerShellGet：探索、安裝和更新 PowerShell 模組的最簡單方式][psget]

<!-- link references-->
[about_Pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[about_Parameters]: /powershell/module/microsoft.powershell.core/about/about_parameters
[psget]: https://mikefrobbins.com/2015/04/23/powershellget-the-big-easy-way-to-discover-install-and-update-powershell-modules/
[PowerShell 資源庫]: https://www.powershellgallery.com/
