# 使用設定名稱設定提取用戶端

> 適用於：Windows PowerShell 5.0

必須告知每個目標節點使用提取模式和指定的 URL，其中它可連絡提取伺服器以取得設定。 若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。若要設定 LCM，您可以建立一種特殊的設定，加上 **DSCLocalConfigurationManager** 屬性裝飾。 如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](metaConfig.md)。

> **注意**：本主題適用於 PowerShell 5.0。 如需設定 PowerShell 4.0 中提取用戶端的資訊，請參閱[使用 PowerShell 4.0 中的設定識別碼設定提取用戶端](pullClientConfigID4.md)。

下列指令碼會設定 LCM 從名為 "CONTOSO-PullSrv" 的伺服器提取設定：

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
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
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
            
        }      
    }
}
PullClientConfigID
```

在此指令碼中，**ConfigurationRepositoryWeb** 區塊會定義提取伺服器。 **ServerURL** 屬性會指定提取伺服器的端點。

**RegistrationKey** 屬性是提取伺服器的所有用戶端節點與該提取伺服器之間的共用金鑰。 相同的值儲存在提取伺服器上的檔案。 **ConfigurationNames** 屬性會指定用於該用戶端節點的設定名稱。 在該提取伺服器上，此用戶端節點的設定 MOF 檔案名稱必須為 *ConfigurationNames*.mof，其中 *ConfigurationNames* 符合您在此中繼設定中設定的 **ConfigurationNames** 屬性值。

執行這個指令碼之後，它會建立新的輸出資料夾，名為 **PullClientConfigID**，並在該處放入中繼設定 MOF 檔案。 在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。

若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。 例如：`Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

> **注意**：註冊金鑰僅適用於 Web 提取伺服器。 您仍然必須使用 **ConfigurationID** 與 SMB 提取伺服器。 如需使用 **ConfigurationID** 設定提取伺服器的資訊，請參閱[使用設定識別碼設定提取用戶端](pullClientConfigID.md)

## 資源和報表伺服器

根據預設，用戶端節點會從設定提取伺服器取得所需的資源，並向其報告狀態。 不過，您可以對資源和報告指定不同的提取伺服器。
若要指定資源伺服器，您可使用 **ResourceRepositoryWeb** (適用於 Web 提取伺服器) 或 **ResourceRepositoryShare** 區塊 (適用於 SMB 提取伺服器)。
若要指定報表伺服器，您可使用 **ReportRepositoryWeb** 區塊。 報表伺服器不得為 SMB 伺服器。
下列中繼設定會設定提取用戶端從 **CONTOSO-PullSrv** 取得其設定，並從 **CONTOSO-ResourceSrv** 取得其資源，然後傳送狀態報表給 **CONTOSO-ReportSrv**：

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
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
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## 另請參閱

* [以設定識別碼設定提取用戶端](pullClientConfigID.md)
* [設定 DSC Web 提取伺服器](pullServer.md)
<!--HONumber=Feb16_HO4-->
