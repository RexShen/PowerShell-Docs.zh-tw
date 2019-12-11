---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 在 PowerShell 5.0 及更新版本中使用設定識別碼來設定提取用戶端
ms.openlocfilehash: bd173a1079b916c450a0292dca7a595a9bcff985
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417227"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>在 PowerShell 5.0 及更新版本中使用設定識別碼來設定提取用戶端

> 適用於：Windows PowerShell 5.0

> [!IMPORTANT]
> 提取伺服器 (Windows 功能「DSC 服務」  ) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。 建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。

在設定提取用戶端前，您應先設定提取伺服器。 雖然此順序非必要，但它有助於疑難排解，且可協助您確認註冊成功。 若要設定提取伺服器，您可以使用下列指南：

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)

每個目標節點都設定為下載設定、資源，甚至是報告其狀態。 下列各節會示範如何使用 SMB 共用或 HTTP DSC 提取伺服器來設定提取用戶端。 當節點的 LCM 重新整理時，它會連到設定的位置來下載任何所指派設定。 若有任何必要資源不存在於節點上，則其會自動從設定的位置下載它們。 若節點已使用[報表伺服器](reportServer.md)進行設定，它接著便會報告作業的狀態。

> [!NOTE]
> 本主題適用於 PowerShell 5.0。 如需設定 PowerShell 4.0 中提取用戶端的資訊，請參閱[在 PowerShell 4.0 中使用設定識別碼設定提取用戶端](pullClientConfigID4.md)。

## <a name="configure-the-pull-client-lcm"></a>設定提取用戶端 LCM

執行以下任何一個範例，便會建立名為 **PullClientConfigID** 的新輸出資料夾，並在該處放入中繼設定 MOF 檔案。 在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。

若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。 例如：

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>設定識別碼

下列範例會將 LCM 的 **ConfigurationID** 屬性設為先前針對這個用途建立的 **Guid**。 **ConfigurationID** 供 LCM 用來在提取伺服器上尋找適當設定。 提取伺服器上的設定 MOF 檔案必須命名為 `ConfigurationID.mof`，其中 *ConfigurationID* 是目標節點 LCM 的 **ConfigurationID** 屬性值。 如需詳細資訊，請參閱[將設定發佈到提取伺服器 (v4/v5)](publishConfigs.md)。

您可以使用以下範例建立隨機 **Guid**，或是使用 [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) Cmdlet。

```powershell
[System.Guid]::NewGuid()
```

如需在您環境中使用 **Guid** 的詳細資訊，請參閱[為 GUID 規劃](/powershell/scripting/dsc/secureserver#guids)。

## <a name="set-up-a-pull-client-to-download-configurations"></a>設定提取用戶端來下載設定

每個用戶端都必須在**提取**模式中設定，並提供儲存其設定的提取伺服器 URL。 若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。 若要設定 LCM，必須先建立一種特殊設定，再加上 **DSCLocalConfigurationManager** 屬性裝飾。 如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)。

### <a name="http-dsc-pull-server"></a>HTTP DSC 提取伺服器

下列指令碼會設定 LCM 從名為 "CONTOSO-PullSrv" 的伺服器提取設定。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

在此指令碼中，**ConfigurationRepositoryWeb** 區塊會定義提取伺服器。 **ServerUrl** 會指定 DSC 提取的 URL

### <a name="smb-share"></a>SMB 共用

下列指令碼會設定 LCM，從 SMB 共用 `\\SMBPullServer\Pull` 提取設定。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

在指令碼中，**ConfigurationRepositoryShare** 區塊會定義提取伺服器 (在此案例中只是一個 SMB 共用)。

## <a name="set-up-a-pull-client-to-download-resources"></a>設定提取用戶端以下載資源

若您在 LCM 設定中只指定 **ConfigurationRepositoryWeb** 或 **ConfigurationRepositoryShare** 區塊 (如同先前範例)，提取用戶端會從擷取其設定的相同位置提取資源。 您也可以為資源指定不同的位置。 若要將資源位置指定為不同的伺服器，請使用 **ResourceRepositoryWeb** 區塊。 若要將資源位置指定為 SMB 共用，請使用 **ResourceRepositoryShare** 區塊。

> [!NOTE]
> 您可以將 **ConfigurationRepositoryWeb** 與 **ResourceRepositoryShare** 合併，或是將 **ConfigurationRepositoryShare** 與 **ResourceRepositoryWeb** 合併。 此範例不會在以下顯示。

### <a name="http-dsc-pull-server"></a>HTTP DSC 提取伺服器

下列中繼設定會設定提取用戶端，以從 **CONTOSO-PullSrv** 取得其設定，並從 **CONTOSO-ResourceSrv** 取得其資源。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB 共用

下列範例會顯示中繼設定，其設定用戶端從 SMB 共用 `\\SMBPullServer\Configurations` 提取設定，並從 SMB 共用 `\\SMBPullServer\Resources` 提取資源。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a>在推送模式中自動下載資源

從 PowerShell 5.0 開始，您的提取用戶端可從 SMB 共用下載模組，即使它們已針對 [推送]  模式設定也一樣。 這在您不想要設定提取伺服器的案例中特別有用。 **ResourceRepositoryShare** 區塊可在不指定 **ConfigurationRepositoryShare** 的情況下使用。 下列範例會顯示中繼設定，其設定用戶端從 SMB 共用 `\\SMBPullServer\Resources` 提取資源。 當節點獲得**推送**設定時，它便會從指定的共用自動下載任何必要資源。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a>設定提取用戶端以報告狀態

根據預設，節點不會將報告傳送到設定的提取伺服器。 您可以針對設定、資源和報告使用單一提取伺服器，但必須建立 **ReportRepositoryWeb** 區塊才可設定報告功能。

### <a name="http-dsc-pull-server"></a>HTTP DSC 提取伺服器

下列範例示範中繼設定，該中繼設定會設定用戶端以提取設定和資源，並將報告資料傳送至單一提取伺服器。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

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
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB 共用

報表伺服器不可以是 SMB 共用。

## <a name="next-steps"></a>後續步驟

設定提取用戶端之後，您可以使用下列指南來執行後續步驟：

- [將設定發佈至提取伺服器 (v4/v5)](publishConfigs.md)
- [封裝資源並上傳到提取伺服器 (v4)](package-upload-resources.md)

## <a name="see-also"></a>另請參閱

* [以設定名稱設定提取用戶端](pullClientConfigNames.md)
