# 使用 DSC 報表伺服器

> 適用於：Windows PowerShell 5.0

> **注意**：本主題所描述的報表伺服器不適用於 PowerShell 4.0。 如需 PowerShell 4.0 中的報表，請參閱＜使用 DSC 更新狀態伺服器＞。

節點的本機設定管理員 (LCM) 可以設定為將設定狀態相關報表傳送至提取伺服器，然後可查詢以擷取該資料。 每次節點檢查並套用
設定時，會將報表傳送至報表伺服器。 這些報表會儲存在伺服器上的資料庫，而且可以藉由呼叫報告 Web 服務來擷取。 每份報表包含
已套用的設定、是否成功套用、使用的資源、所擲回的任何錯誤，以及開始和完成時間等資訊。

## 設定要傳送報表的節點

您可告知節點將報表傳送至伺服器，方法是使用該節點 LCM 設定內的 **ReportServerWeb** 區塊 (如需設定 LCM 的資訊，
請參閱[設定本機設定管理員](metaConfig.md))。 節點傳送報表的目標伺服器必須設定為 Web 提取伺服器 (您無法將報表傳送
至 SMB 共用)。 如需設定提取伺服器的資訊，請參閱[設定 DSC Web 提取伺服器](pullServer.md)。 報表伺服器的服務可以與節點從中提取設定和取得資源的服務相同，
或可以是不同的服務。
 
 在 **ReportServerWeb** 區塊中，您可指定提取服務的 URL
和該伺服器已知的註冊金鑰。
 
  下列設定會設定節點從一項服務提取設定，並傳送報表
至不同伺服器上的服務。 
 
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
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCReportServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}
PullClientConfigID
```

## 取得報表資料

傳送到提取伺服器的報表會輸入到該伺服器上的資料庫中。 可透過呼叫 Web 服務使用報表。 若要擷取特定節點的報表，
請以下列形式將 HTTP 要求傳送到報表 Web 服務：
`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentID = MyNodeAgentId)/Reports`
其中 `MyNodeAgentId` 是您要取得報表之節點的 AgentId。 您也可以呼叫該節點上的 [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) 以取得節點的 AgentID
。

報表會以 JSON 物件的陣列傳回。

下列指令碼會傳回執行所在之節點的報表：

```powershell
function GetReport
{
    param($AgentId = "$((glcm).AgentId)", $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCReportServer.svc")
    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```
    
## 檢視報表資料

如果您將變數設定為 **GetReport** 函式的結果，您就可以在傳回陣列的項目中檢視個別欄位：

```powershell
$reports = GetReport
$reports[1]

JobId                : 71515ae8-7294-40a3-8137-fc85bf4b678f
OperationType        : Consistency
RefreshMode          : 
Status               : 
ReportFormatVersion  : 1.0
ConfigurationVersion : 2.0.0
StartTime            : 02/08/2016 01:28:54
EndTime              : 02/08/2016 01:28:57
RebootRequested      : False
Errors               : {}
StatusData           : {{"NumberOfResources":"2","Locale":"en-US","ResourcesInDesiredState":[{"ResourceId":"[WindowsFeature]MyFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::4::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"},{"ResourceId":"[WindowsFeature]My2ndFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::8::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"}]}}
```

請注意，**StatusData** 欄位是具有三個屬性的物件：**NumberOfResources**、**Locale** 和 **ResourcesInDesiredState**。 **ResourcesInDesiredState**
屬性是物件陣列，其中的物件各有許多屬性。 下列指令碼會採用單一報表作為參數，逐一查看其 **ResourcesInDesiredState**
陣列，並將其寫入主控台：
 
```powershell
function GetStatusData
{
    param ($Report)
    $statusData = $Report.StatusData | ConvertFrom-Json

    $Resources = $statusData.ResourcesInDesiredState

    Foreach ($Resource in $Resources)
    {
        Write-Host 'ResourceId: ' $Resource.ResourceId
        Write-Host 'SourceInfo: ' $Resource.SourceInfo
        Write-Host 'ModuleName: ' $Resource.ModuleName
        Write-Host 'ModuleVersion: ' $Resource.ModuleVersion
        Write-Host 'ConfigurationName: ' $Resource.ConfigurationName
        Write-Host 'ResourceName: ' $Resource.ResourceName
        Write-Host
    }
}
```

以下是呼叫 **GetStatusData** 函式之後的範例輸出：

```powershell
GetStatusData -Report $report[1]

ResourceId:  [WindowsFeature]MyFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::4::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature

ResourceId:  [WindowsFeature]My2ndFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::8::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature
```

請注意，這些範例主要供您了解可以如何處理報表資料。 如需在 PowerShell 中搭配使用 JSON 的簡介，請參閱
[Playing with JSON and PowerShell (以 JSON 和 PowerShell 播放)](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/)。

## 另請參閱
>[設定本機設定管理員](metaConfig.md)
>[設定 DSC Web 提取伺服器](pullServer.md)
>[使用設定名稱設定提取用戶端](pullClientConfigNames.md)
<!--HONumber=Feb16_HO4-->
