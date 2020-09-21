---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
title: WMF 5.1 的 DSC 改善
ms.openlocfilehash: 445d0f7bb54c6b21b6af26c4174f3d6422caf6dd
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771544"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>WMF 5.1 的預期狀態設定 (DSC) 改善

## <a name="dsc-class-resource-improvements"></a>DSC 類別資源改善

WMF 5.1 中已修正下列已知問題︰

- 如果類別型 DSC 資源的 Get() 函式傳回複雜/雜湊表類型，Get-DscConfiguration 可能會傳回空值 (null) 或錯誤。
- 當 DSC 設定使用 RunAs 認證時，Get-DscConfiguration 就會傳回錯誤。
- 類別型資源無法用於複合設定中。
- 如果類別型資源有其本身類型的屬性，Start-DscConfiguration 會停止回應。
- 類別型資源不能用為獨佔資源。

## <a name="dsc-resource-debugging-improvements"></a>DSC 資源偵錯改善

在 WMF 5.0 中，PowerShell 偵錯工具並未直接停在類別資源方法 (Get/Set/Test)。 在 WMF 5.1 中，偵錯工具會停在類別資源方法，方式如同 MOF 資源方法。

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>DSC 提取用戶端支援 TLS1.1 和 TLS1.2

DSC 提取用戶端過去只支援 HTTPS 連線的 SSL3.0 和 TLS1.0。 強制使用更安全的通訊協定時，提取用戶端就會停止運作。 在 WMF 5.1 中，DSC 提取用戶端不再支援 SSL 3.0，卻新增了更安全的 TLS 1.1 和 TLS 1.2 通訊協定支援。

## <a name="improved-pull-server-registration"></a>改善的提取伺服器登錄

在舊版的 WMF 中，在使用 ESENT 資料庫時，同時登錄/報告 DSC 提取伺服器的要求，會導致 LCM 無法登錄及 (或) 報告。 在這種情況下，提取伺服器的事件記錄檔會出現「執行個體名稱已在使用中」的錯誤。 這是因為在多執行緒的案例中使用不正確的模式來存取 ESENT 資料庫所導致的。 WMF 5.1 已修正此問題。 WMF 5.1 中可以正常同時登錄或報告 (包含 ESENT 資料庫)。 只有 ESENT 資料庫會發生這個問題，OLEDB 資料庫無此問題。

## <a name="enable-circular-log-on-esent-database-instance"></a>在 ESENT 資料庫執行個體上啟用循環記錄

在舊版的 DSC-PullServer 中，ESENT 資料庫記錄檔會填滿提取伺服器的磁碟空間，因為資料庫執行個體是在沒有循環記錄的情況下建立的。 在此版本中，您可以選擇使用提取伺服器的 web.config，控制執行個體的循環記錄行為。 根據預設，CircularLogging 會設定為 TRUE。

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a>WOW64 支援設定關鍵字

64 位元電腦上的 WOW64 現在支援 `Configuration` 關鍵字。 這代表可以定義 DSC 設定，以及可於 32 位元處理序中編譯，例如在 64 位元電腦上執行的 Windows PowerShell ISE (x86)。

## <a name="pull-partial-configuration-naming-convention"></a>提取命名慣例的部分設定

在舊版中，提取伺服器/服務的部分設定命名慣例 MOF 檔案名稱，應該符合本機設定管理員設定中指定的部分設定名稱，該本機設定管理員設定必須依次比對 MOF 檔案中內嵌的設定名稱。

請參閱下方的快照集︰

- 本機組態設定，當中定義了允許節點接收的部分設定。

  ![中繼設定範例](media/DSC-improvements/MetaConfigPartialOne.png)

- 部分設定定義範例

  ```powershell
  Configuration PartialOne
  {
      Node('localhost')
      {
          File test
          {
              DestinationPath = "$env:TEMP\partialconfigexample.txt"
              Contents = 'Partial Config Example'
          }
      }
  }
  PartialOne
  ```

- 內嵌在所產生 MOF 檔案中的 'ConfigurationName'。

  ![產生的 MOF 檔案範例](media/DSC-improvements/PartialGeneratedMof.png)

- 提取設定存放庫中的檔案名稱

  ![設定存放庫中的檔案名稱](media/DSC-improvements/PartialInConfigRepository.png)

  Azure 自動化服務名稱以前產生的 MOF 檔案為 `<ConfigurationName>.<NodeName>.mof`。 因此下面的設定會編譯為 PartialOne.localhost.mof。

  如此即不可能從 Azure 自動化服務提取您其中一項部分設定。

  ```powershell
  Configuration PartialOne
  {
      Node('localhost')
      {
          File test
          {
              DestinationPath = "$env:TEMP\partialconfigexample.txt"
              Contents = 'Partial Config Example'
          }
      }
  }
  PartialOne
  ```

  在 WMF 5.1 中，提取伺服器/服務中的部分設定可以命名為 `<ConfigurationName>.<NodeName>.mof`。 但若電腦從提取伺服器/服務中提取了單一設定，則提取伺服器存放庫上的設定檔可以有任意的檔案名稱。 此命名彈性可讓您使用 Azure 自動化服務部分管理節點，其中節點的某些設定來自 Azure 自動化 DSC，且某項部分設定是您在本機管理的。

  下面的中繼設定會設定由本機及 Azure 自動化服務管理的節點。

  ```powershell
  [DscLocalConfigurationManager()]
  Configuration RegistrationMetaConfig
  {
      Settings
      {
          RefreshFrequencyMins = 30
          RefreshMode = "PULL"
      }

      ConfigurationRepositoryWeb web
      {
          ServerURL =  $endPoint
          RegistrationKey = $registrationKey
          ConfigurationNames = $configurationName
      }

      # Partial configuration managed by Azure Automation service.
      PartialConfiguration PartialConfigurationManagedByAzureAutomation
      {
          ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
      }

      # This partial configuration is managed locally.
      PartialConfiguration OnPremisesConfig
      {
          RefreshMode = "PUSH"
          ExclusiveResources = @("Script")
      }

  }

  RegistrationMetaConfig
  Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
  ```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>使用 PsDscRunAsCredential 和 DSC 複合資源

我們已新增搭配使用 [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) 和 DSC [複合](/powershell/scripting/dsc/resources/authoringresourcecomposite)資源的支援。

在設定內使用複合資源時，您現在可以指定 **PsDscRunAsCredential** 的值。 指定後，複合資源內的所有資源都會以 RunAs 使用者身分執行。 如果複合資源會呼叫另一個複合資源，也會以 RunAs 使用者身分執行所有那些資源。 RunAs 認證會傳播至複合資源階層的所有層級。 如果複合資源內的任何資源會針對 **PsDscRunAsCredential** 指定自己的值，則會在設定編譯期間發生合併錯誤。

本範例示範如何使用包含在 PSDesiredStateConfiguration 模組內的 [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) 複合資源。

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>允許在設定中的相同重複資源

DSC 不允許或不處理設定中定義的衝突資源。 它並不會去嘗試解決衝突，而是只會失敗。 當設定重複使用透過複合資源而變得更有用時，衝突發生頻率將會提高。 當衝突資源的定義相同時，DSC 應該進行智慧判斷並允許此情況。 在此版本中，我們支援具有相同定義的多個資源執行個體︰

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

在舊版中，因為 WindowsFeature FE_IIS 和 WindowsFeature Worker_IIS 執行個體在盡力確保 「網頁伺服器」 角色已安裝時發生衝突，因此會出現編譯失敗的結果。 請注意在這兩種設定中，*所有*正在設定的屬性都是相同的。 由於這兩個資源中的*所有*屬性相同，現在這會讓編譯成功完成。

如果這兩個資源之間有任何不同的屬性，則不會將它們視為相同，且編譯將會失敗。

## <a name="dsc-module-and-configuration-signing-validations"></a>DSC 模組和設定簽署驗證

在 DSC 中，設定和模組會從提取伺服器散發到受管理的電腦。 如果提取伺服器遭到入侵，攻擊者或許就能修改提取伺服器上的設定和模組，並將其散發到所有受控節點。

在 WMF 5.1 中，DSC 支援驗證類別目錄和設定 (.MOF) 檔案的數位簽章。 這項功能會防止節點執行未經受信任簽署者簽署的設定或模組檔案，或經受信任簽署者簽署後遭竄改的檔案。

### <a name="how-to-sign-configuration-and-module"></a>如何簽署設定和模組

- 設定檔 (.MOF)：現有的 PowerShell Cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) 已擴充，可支援簽署 MOF 檔案。
- 模組：已透過簽署對應的模組類別目錄完成模組簽署，使用步驟如下：
  1. 建立類別目錄檔案︰類別目錄檔案包含密碼編譯雜湊或指紋的集合。 每個指紋都會對應至模組所包含的檔案。 已新增新的 [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog) Cmdlet，讓使用者為其模組建立類別目錄檔案。
  2. 簽署類別目錄檔案︰使用 [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) 簽署類別目錄檔案。
  3. 將類別目錄檔案放在模組資料夾內。 依照慣例，模組類別目錄檔案應該位於與模組同名的模組資料夾內。

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>啟用簽署驗證的 LocalConfigurationManager 設定

#### <a name="pull"></a>提取

節點的 LocalConfigurationManager 會根據其目前的設定，執行模組和設定的簽署驗證。 預設停用簽章驗證。 將 'SignatureValidation' 區塊加入節點的中繼設定定義可啟用簽章驗證，如下所示：

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

在節點上設定上述中繼設定，可在下載的設定和模組上啟用簽章驗證。 本機設定管理員會執行下列步驟來驗證數位簽章。

1. 使用 `Get-AuthenticodeSignature` Cmdlet 來驗證設定檔 (.MOF) 上的簽章有效。
2. 驗證授權簽署者的憑證授權單位是否受信任。
3. 將設定的模組/資源相依性下載至暫存位置。
4. 驗證模組內是否包含類別目錄簽章。
   - 尋找 `<moduleName>.cat` 檔案，並使用 `Get-AuthenticodeSignature` 來驗證它的簽章。
   - 驗證授權簽署者的憑證授權單位是否受信任。
   - 使用新的 `Test-FileCatalog` Cmdlet 來驗證模組的內容未經竄改。
5. `Install-Module` 到 `$env:ProgramFiles\WindowsPowerShell\Modules\`
6. 處理設定

> [!NOTE]
> 只有第一次在系統上套用設定時，或下載並安裝模組時，才會執行模組類別目錄和設定上的簽章驗證。
> 一致性執行不會驗證 Current.mof 或其模組相依性的簽章。 如果驗證在任何階段失敗，例如從提取伺服器提取的設定未經簽署，則會終止處理設定並顯示下列錯誤，以及刪除所有暫存檔案。

![錯誤輸出設定範例](media/DSC-improvements/PullUnsignedConfigFail.png)

同樣地，提取目錄未經簽署的模組也會產生下列錯誤：

![錯誤輸出模組範例](media/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a>發送

透過使用推入所傳遞的設定，可能在傳送到節點之前即已在來源遭到竄改。 本機設定管理員會對已推入或發行的設定，執行類似的簽章驗證步驟。 以下是推入簽章驗證的完整範例。

- 在節點上啟用簽章驗證。

  ```powershell
  [DSCLocalConfigurationManager()]
  Configuration EnableSignatureValidation
  {
      Settings
      {
          RefreshMode = 'PUSH'
      }
      SignatureValidation validations{
          TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
          SignedItemType =  'Configuration','Module'
      }

  }
  EnableSignatureValidation
  Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
  ```

- 建立設定檔範例。

  ```powershell
  # Sample configuration
  Configuration Test
  {

      File foo
      {
          DestinationPath =  "$env:TEMP\signingTest.txt"
          Contents = "ABC"
      }
  }
  Test
  ```

- 嘗試將未經簽署的設定檔推入至節點。

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![錯誤 - 推送了未經簽署的 MOF 檔案](media/DSC-improvements/PushUnsignedMof.png)

- 使用程式碼簽署憑證簽署設定檔。

  ![簽署 MOF 檔案](media/DSC-improvements/SignMofFile.png)

- 嘗試推入簽署的 MOF 檔案。

  ![推送簽署的 MOF 檔案](media/DSC-improvements/PushSignedMof.png)
