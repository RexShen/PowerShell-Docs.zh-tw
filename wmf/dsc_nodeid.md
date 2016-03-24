# 隔離節點和設定識別碼

## 概觀

為了在 Pull 模式中使用 DSC 時提供更有彈性且有效率的體驗，我們在此版本中加入了多種功能。 這些功能可讓您更有彈性地輕鬆設定及部署跨多個節點的設定，同時仍然可以個別追蹤每個節點的狀態及報告資訊。 這些功能如下所示︰

* 用來識別電腦設定的設定名稱。 此名稱可由多個目標節點共用 
* 可唯一識別單一節點的代理程式識別碼
* 只在目標節點第一次連線到提取伺服器時發生的註冊步驟

**注意︰**這些功能已經加入，而且不會取代現有的提取功能和概念。 您可以使用這些新功能或具有此版本中發送之新提取伺服器的舊功能。

## 代理程式識別碼

這項功能是提供給不想設定及管理每個目標節點唯一識別碼的使用者使用。 現在，再也不需要對所需的 GUID 進行記錄。 DSC 會自動產生與提取伺服器通訊時，會使用代理程式識別碼。 此識別碼由提取伺服器使用，用於唯一識別指定節點的所有資訊。 這也代表您不需要使用包含唯一識別碼的唯一中繼設定來設定每個目標節點，因此單一中繼設定可供許多目標節點使用，同時仍然保留每個節點的唯一識別。 

## 設定名稱

設定名稱是易記的名稱，用來定義目標節點會套用的設定名稱。 與此相關聯的變更如下︰  

### 易記的命名

可以使用任何字串！ 不需要是 GUID 的格式，所以設定 SQL server 的設定可簡單的命名為 'SQL_Server'。 這可讓您更容易識別指定設定的用途。

### 工作分派

在提取伺服器上集中管理有指派目標節點的設定。 這可以藉由定義中繼設定中的 ConfigrationName 屬性來啟動，但這只適用於登錄期間。 登錄後，伺服器會告訴目標節點它會取得的設定。 對內部部署提取伺服器來說，設定和目標節點之間的對應只能夠在登錄期間執行，但在 Azure 自動化中，這些變更可輕鬆地在 UI 內或透過其 Cmdlet 執行。 若要變更指派給目標節點的內部提取伺服器設定，您可以重新執行登錄。

### 多個/部分設定

如果多個設定名稱指派給目標節點時，它們會被視為部分設定。 為了讓此步驟能正常運作，目標節點上的中繼設定必須設定為接受部分設定。 **注意︰**這僅在內部部署提取伺服器上支援。 Azure 自動化不支援部分設定。

## 註冊

因為設定名稱不再是 GUID (它們現在是易記的名稱)，任何人都可以猜出它們。 為了減輕這固有的安全性問題，我們在節點可以從伺服器要求設定之前，加入了註冊的步驟。 節點使用共用密碼 (節點和伺服器皆知道密碼) 向提取伺服器進行註冊，而且 (選擇性的) 註冊將要求的設定名稱。 此共用密碼在每一部電腦上不需要是唯一的。 假設︰共用密碼是難以猜測的識別碼，就像 GUID。 此共用的密碼由目標節點中繼設定中的 **RegistrationKey** 屬性所定義。

### 中繼設定範例

```powershell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "PULL";
        AllowModuleOverwrite = $true;
        RebootNodeIfNeeded = $true;
        ConfigurationModeFrequencyMins = 60;
    }

    ConfigurationRepositoryWeb ConfigurationManager
    {
        ServerURL = “https://PullServerMachine:8080/psdscpullserver.svc”
        RegistrationKey = "140a952b-b9d6-406b-b416-e0f759c9c0e4"
        ConfigurationNames = @(“WebRole”)
    }
}

SampleMetaConfig
```

RegistrationKey 值必須在提取伺服器上定義。 為了設定提取伺服器時執行此步驟，請在特定位置建立一個名稱為 **RegistrationKeys.txt** 的文字檔案，然後在提取伺服器的 web.config 中設定此位置，如下所示。  

```XML
<add key="ConfigurationPath" value="C:\Program Files\WindowsPowerShell\DscService\Configuration">

<add key="ModulePath" value="C:\Program Files\WindowsPowerShell\DscService\Modules">

<add key="RegistrationKeyPath" value="C:\Program Files\WindowsPowerShell\DscService">
```

使用 xDSCWebService DSC 資源的最新版本，完全部署內部部署提取伺服器，以與此搭配使用。 如須完成設定的相關資訊，請參閱 [Example Configuration](https://github.com/grayzu/PSSummitEU2015/blob/master/PullServer/02%20-%20PullServer%20Config.ps1)。

**注意︰**提取伺服器設定為檔案共用時，不支援此功能。 只支援網頁導向提取伺服器。<!--HONumber=Mar16_HO2-->
