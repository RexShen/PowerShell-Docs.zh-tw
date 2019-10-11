---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用 DSC 報表伺服器
ms.openlocfilehash: 1ccd4f96b782b41b7d7c953735cb41b3ba3d2bce
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953575"
---
# <a name="using-a-dsc-report-server"></a><span data-ttu-id="da928-103">使用 DSC 報表伺服器</span><span class="sxs-lookup"><span data-stu-id="da928-103">Using a DSC report server</span></span>

<span data-ttu-id="da928-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="da928-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="da928-105">提取伺服器 (Windows 功能「DSC 服務」  ) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。</span><span class="sxs-lookup"><span data-stu-id="da928-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="da928-106">建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。</span><span class="sxs-lookup"><span data-stu-id="da928-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>
>
> [!NOTE]
> <span data-ttu-id="da928-107">本主題所描述的報表伺服器不適用於 PowerShell 4.0。</span><span class="sxs-lookup"><span data-stu-id="da928-107">The report server described in this topic is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="da928-108">節點的本機設定管理員 (LCM) 可以設定為將設定狀態相關報表傳送至提取伺服器，然後可查詢以擷取該資料。</span><span class="sxs-lookup"><span data-stu-id="da928-108">The Local Configuration Manager (LCM) of a node can be configured to send reports about its configuration status to a pull server, which can then be queried to retrieve that data.</span></span> <span data-ttu-id="da928-109">每次節點檢查並套用設定時，皆會將報表傳送至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="da928-109">Each time the node checks and applies a configuration, it sends a report to the report server.</span></span> <span data-ttu-id="da928-110">這些報表會儲存在伺服器上的資料庫，而且可以藉由呼叫報告 Web 服務來擷取。</span><span class="sxs-lookup"><span data-stu-id="da928-110">These reports are stored in a database on the server, and can be retrieved by calling the reporting web service.</span></span> <span data-ttu-id="da928-111">每份報表包含已套用的設定、是否成功套用、使用的資源、所擲回的任何錯誤，以及開始和完成時間等資訊。</span><span class="sxs-lookup"><span data-stu-id="da928-111">Each report contains information such as what configurations were applied and whether they succeeded, the resources used, any errors that were thrown, and start and finish times.</span></span>

## <a name="configuring-a-node-to-send-reports"></a><span data-ttu-id="da928-112">設定要傳送報表的節點</span><span class="sxs-lookup"><span data-stu-id="da928-112">Configuring a node to send reports</span></span>

<span data-ttu-id="da928-113">您可告知節點將報表傳送至伺服器，方法是使用該節點 LCM 設定內的 **ReportServerWeb** 區塊 (如需關於設定 LCM 的相關資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md))。</span><span class="sxs-lookup"><span data-stu-id="da928-113">You tell a node to send reports to a server by using a **ReportServerWeb** block in the node's LCM configuration (for information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)).</span></span> <span data-ttu-id="da928-114">節點傳送報表的目標伺服器必須設定為 Web 提取伺服器 (您無法將報表傳送至 SMB 共用)。</span><span class="sxs-lookup"><span data-stu-id="da928-114">The server to which the node sends reports must be set up as a web pull server (you cannot send reports to an SMB share).</span></span> <span data-ttu-id="da928-115">如需設定提取伺服器的資訊，請參閱[設定 DSC Web 提取伺服器](pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="da928-115">For information about setting up a pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span> <span data-ttu-id="da928-116">報表伺服器的服務可以與節點從中提取設定和取得資源的服務相同，或可以是不同的服務。</span><span class="sxs-lookup"><span data-stu-id="da928-116">The report server can be the same service from which the node pulls configurations and gets resources, or it can be a different service.</span></span>

<span data-ttu-id="da928-117">在 **ReportServerWeb** 區塊中，您可指定提取服務的 URL 和該伺服器已知的註冊金鑰。</span><span class="sxs-lookup"><span data-stu-id="da928-117">In the **ReportServerWeb** block, you specify the URL of the pull service and a registration key that is known to the server.</span></span>

<span data-ttu-id="da928-118">下列設定會設定節點從一項服務提取設定，並傳送報表至不同伺服器上的服務。</span><span class="sxs-lookup"><span data-stu-id="da928-118">The following configuration configures a node to pull configurations from one service, and send reports to a service on a different server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCPullServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}

ReportClientConfig
```

<span data-ttu-id="da928-119">下列設定會設定節點針對設定、資源和報告使用單一伺服器。</span><span class="sxs-lookup"><span data-stu-id="da928-119">The following configuration configures a node to use a single server for configurations, resources, and reporting.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }



        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfig
```

> [!NOTE]
> <span data-ttu-id="da928-120">當您設定提取伺服器時，可以為 Web 服務指定任何名稱，但 **ServerURL** 屬性必須符合服務名稱。</span><span class="sxs-lookup"><span data-stu-id="da928-120">You can name the web service whatever you want when you set up a pull server, but the **ServerURL** property must match the service name.</span></span>

## <a name="getting-report-data"></a><span data-ttu-id="da928-121">取得報表資料</span><span class="sxs-lookup"><span data-stu-id="da928-121">Getting report data</span></span>

<span data-ttu-id="da928-122">傳送到提取伺服器的報表會輸入到該伺服器上的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="da928-122">Reports sent to the pull server are entered into a database on the server.</span></span> <span data-ttu-id="da928-123">可透過呼叫 Web 服務使用報表。</span><span class="sxs-lookup"><span data-stu-id="da928-123">The reports are available through calls to the web service.</span></span> <span data-ttu-id="da928-124">若要擷取特定節點的報告，請以下列形式將 HTTP 要求傳送到報表 Web 服務：`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span><span class="sxs-lookup"><span data-stu-id="da928-124">To retrieve reports for a specific node, send an HTTP request to the report web service in the following form: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span></span>
<span data-ttu-id="da928-125">其中 `MyNodeAgentId` 是您要取得報表之節點的 AgentId。</span><span class="sxs-lookup"><span data-stu-id="da928-125">where `MyNodeAgentId` is the AgentId of the node for which you want to get reports.</span></span> <span data-ttu-id="da928-126">您也可以呼叫該節點上的 [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) 以取得節點的 AgentID。</span><span class="sxs-lookup"><span data-stu-id="da928-126">You can get the AgentID for a node by calling [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) on that node.</span></span>

<span data-ttu-id="da928-127">報表會以 JSON 物件的陣列傳回。</span><span class="sxs-lookup"><span data-stu-id="da928-127">The reports are returned as an array of JSON objects.</span></span>

<span data-ttu-id="da928-128">下列指令碼會傳回執行所在之節點的報表：</span><span class="sxs-lookup"><span data-stu-id="da928-128">The following script returns the reports for the node on which it is run:</span></span>

```powershell
function GetReport
{
    param
    (
        $AgentId = "$((glcm).AgentId)", 
        $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCPullServer.svc"
    )

    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```

## <a name="viewing-report-data"></a><span data-ttu-id="da928-129">檢視報表資料</span><span class="sxs-lookup"><span data-stu-id="da928-129">Viewing report data</span></span>

<span data-ttu-id="da928-130">如果您將變數設定為 **GetReport** 函式的結果，您就可以在傳回陣列的項目中檢視個別欄位：</span><span class="sxs-lookup"><span data-stu-id="da928-130">If you set a variable to the result of the **GetReport** function, you can view the individual fields in an element of the array that is returned:</span></span>

```powershell
$reports = GetReport
$reports[1]
```

```output
JobId                : 019dfbe5-f99f-11e5-80c6-001dd8b8065c
OperationType        : Consistency
RefreshMode          : Pull
Status               : Success
ReportFormatVersion  : 2.0
ConfigurationVersion : 2.0.0
StartTime            : 04/03/2016 06:21:43
EndTime              : 04/03/2016 06:22:04
RebootRequested      : False
Errors               : {}
StatusData           : {{"StartDate":"2016-04-03T06:21:43.7220000-07:00","IPV6Addresses":["2001:4898:d8:f2f2:852b:b255:b071:283b","fe80::852b:b255:b071
                       :283b%12","::2000:0:0:0","::1","::2000:0:0:0"],"DurationInSeconds":"21","JobID":"{019DFBE5-F99F-11E5-80C6-001DD8B8065C}","Curren
                       tChecksum":"A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F","MetaData":"Author: configAuthor; Name:
                       Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost: CONTOSO-PullSrv;","RebootRequested":"False
                       ","Status":"Success","IPV4Addresses":["10.240.179.151","127.0.0.1"],"LCMVersion":"2.0","ResourcesNotInDesiredState":[{"SourceInf
                       o":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall","ModuleName":"xNetworking","DurationInSeconds":"8.785",
                       "InstanceName":"Firewall","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"xFirewall","ModuleVersion":"2.7.0.0","
                       RebootRequested":"False","ResourceId":"[xFirewall]Firewall","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"False
                       "}],"NumberOfResources":"2","Type":"Consistency","HostName":"CONTOSO-PULLCLI","ResourcesInDesiredState":[{"SourceInfo":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive","ModuleName":"PSDesiredStateConfiguration","DurationInSeconds":"1.848",
                       "InstanceName":"ArchiveExample","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"Archive","ModuleVersion":"1.1","
                       RebootRequested":"False","ResourceId":"[Archive]ArchiveExample","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"T
                       rue"}],"MACAddresses":["00-1D-D8-B8-06-5C","00-00-00-00-00-00-00-E0"],"MetaConfiguration":{"AgentId":"52DA826D-00DE-4166-8ACB-73F2B46A7E00",
                       "ConfigurationDownloadManagers":[{"SourceInfo":"C:\\ReportTest\\LCMConfig.ps1::14::9::ConfigurationRepositoryWeb","A
                       llowUnsecureConnection":"True","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","RegistrationKey":"","ResourceId":"[Config
                       urationRepositoryWeb]CONTOSO-PullSrv","ConfigurationNames":["ClientConfig"]}],"ActionAfterReboot":"ContinueConfiguration","LCMCo
                       mpatibleVersions":["1.0","2.0"],"LCMState":"Idle","ResourceModuleManagers":[],"ReportManagers":[{"AllowUnsecureConnection":"True
                       ","RegistrationKey":"","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","ResourceId":"[ReportServerWeb]CONTOSO-PullSrv","S
                       ourceInfo":"C:\\ReportTest\\LCMConfig.ps1::24::9::ReportServerWeb"}],"StatusRetentionTimeInDays":"10","LCMVersion":"2.0","Config
                       urationMode":"ApplyAndMonitor","RefreshFrequencyMins":"30","RebootNodeIfNeeded":"True","RefreshMode":"Pull","DebugMode":["NONE"]
                       ,"LCMStateDetail":"","AllowModuleOverwrite":"False","ConfigurationModeFrequencyMins":"15"},"Locale":"en-US","Mode":"Pull"}}
AdditionalData       : {}
```

<span data-ttu-id="da928-131">根據預設，報表會依 **JobID** 排序。</span><span class="sxs-lookup"><span data-stu-id="da928-131">By default, the reports are sorted by **JobID**.</span></span> <span data-ttu-id="da928-132">若要取得最新報表，您可以依 **StartTime** 屬性遞減排序報表，然後取得陣列的第一個項目︰</span><span class="sxs-lookup"><span data-stu-id="da928-132">To get the most recent report, you can sort the reports by descending **StartTime** property, and then get the first element of the array:</span></span>

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

<span data-ttu-id="da928-133">請注意，**StatusData** 屬性是具有一些屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="da928-133">Notice that the **StatusData** property is an object with a number of properties.</span></span> <span data-ttu-id="da928-134">這是大部分報告資料的所在位置。</span><span class="sxs-lookup"><span data-stu-id="da928-134">This is where much of the reporting data is.</span></span> <span data-ttu-id="da928-135">讓我們看看最新報表之 **StatusData** 屬性的個別欄位：</span><span class="sxs-lookup"><span data-stu-id="da928-135">Let's look at the individual fields of the **StatusData** property for the most recent report:</span></span>

```powershell
$statusData = $reportMostRecent.StatusData | ConvertFrom-Json
$statusData
```

```output
StartDate                  : 2016-04-04T11:21:41.2990000-07:00
IPV6Addresses              : {2001:4898:d8:f2f2:852b:b255:b071:283b, fe80::852b:b255:b071:283b%12, ::2000:0:0:0, ::1...}
DurationInSeconds          : 25
JobID                      : {135D230E-FA92-11E5-80C6-001DD8B8065C}
CurrentChecksum            : A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F
MetaData                   : Author: configAuthor; Name: Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost:
                             CONTOSO-PullSrv;
RebootRequested            : False
Status                     : Success
IPV4Addresses              : {10.240.179.151, 127.0.0.1}
LCMVersion                 : 2.0
ResourcesNotInDesiredState : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall; ModuleName=xNetworking;
                             DurationInSeconds=10.725; InstanceName=Firewall; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=xFirewall;
                             ModuleVersion=2.7.0.0; RebootRequested=False; ResourceId=[xFirewall]Firewall; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=False}}
NumberOfResources          : 2
Type                       : Consistency
HostName                   : CONTOSO-PULLCLI
ResourcesInDesiredState    : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive; ModuleName=PSDesiredStateConfiguration;
                             DurationInSeconds=2.672; InstanceName=ArchiveExample; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=Archive;
                             ModuleVersion=1.1; RebootRequested=False; ResourceId=[Archive]ArchiveExample; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=True}}
MACAddresses               : {00-1D-D8-B8-06-5C, 00-00-00-00-00-00-00-E0}
MetaConfiguration          : @{AgentId=52DA826D-00DE-4166-8ACB-73F2B46A7E00; ConfigurationDownloadManagers=System.Object[];
                             ActionAfterReboot=ContinueConfiguration; LCMCompatibleVersions=System.Object[]; LCMState=Idle;
                             ResourceModuleManagers=System.Object[]; ReportManagers=System.Object[]; StatusRetentionTimeInDays=10; LCMVersion=2.0;
                             ConfigurationMode=ApplyAndMonitor; RefreshFrequencyMins=30; RebootNodeIfNeeded=True; RefreshMode=Pull;
                             DebugMode=System.Object[]; LCMStateDetail=; AllowModuleOverwrite=False; ConfigurationModeFrequencyMins=15}
Locale                     : en-US
Mode                       : Pull
```

<span data-ttu-id="da928-136">除了其他屬性，這還會顯示最新設定呼叫的兩項資源，其中一項處於預期狀態，另一項處於非預期狀態。</span><span class="sxs-lookup"><span data-stu-id="da928-136">Among other things, this shows that the most recent configuration called two resources, and that one of them was in the desired state, and one of them was not.</span></span> <span data-ttu-id="da928-137">您可取得僅限 **ResourcesNotInDesiredState** 屬性之更容易讀取的輸出：</span><span class="sxs-lookup"><span data-stu-id="da928-137">You can get a more readable output of just the **ResourcesNotInDesiredState** property:</span></span>

```powershell
$statusData.ResourcesInDesiredState
```

```output
SourceInfo        : C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive
ModuleName        : PSDesiredStateConfiguration
DurationInSeconds : 2.672
InstanceName      : ArchiveExample
StartDate         : 2016-04-04T11:21:55.7200000-07:00
ResourceName      : Archive
ModuleVersion     : 1.1
RebootRequested   : False
ResourceId        : [Archive]ArchiveExample
ConfigurationName : Sample_ArchiveFirewall
InDesiredState    : True
```

<span data-ttu-id="da928-138">請注意，這些範例主要供您了解可以如何處理報表資料。</span><span class="sxs-lookup"><span data-stu-id="da928-138">Note that these examples are meant to give you an idea of what you can do with report data.</span></span> <span data-ttu-id="da928-139">如需在 PowerShell 中搭配使用 JSON 的簡介，請參閱[Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/) (以 JSON 和 PowerShell 播放)。</span><span class="sxs-lookup"><span data-stu-id="da928-139">For an introduction on working with JSON in PowerShell, see [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span></span>

## <a name="see-also"></a><span data-ttu-id="da928-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da928-140">See Also</span></span>

[<span data-ttu-id="da928-141">設定本機設定管理員</span><span class="sxs-lookup"><span data-stu-id="da928-141">Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="da928-142">設定 DSC Web 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="da928-142">Setting up a DSC web pull server</span></span>](pullServer.md)

[<span data-ttu-id="da928-143">使用設定名稱設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="da928-143">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
