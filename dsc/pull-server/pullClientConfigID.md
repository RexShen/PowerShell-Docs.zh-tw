---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 設定提取用戶端使用設定識別碼，在 PowerShell 5.0 和更新版本
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400772"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>設定提取用戶端使用設定識別碼，在 PowerShell 5.0 和更新版本

> 適用於：Windows PowerShell 5.0

> [!IMPORTANT]
> 提取伺服器 (Windows 功能「DSC 服務」) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。 建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。

設定提取用戶端之前, 您應該設定提取伺服器。 雖然此順序並不需要，它會協助進行疑難排解，並幫助您確認註冊成功。 若要設定提取伺服器，您可以使用下列指南：

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)

若要下載組態中，資源，並甚至報告其狀態，可以設定每個目標節點。 下列各節會示範如何設定提取用戶端與 SMB 共用或 HTTP DSC 提取伺服器。 當節點 LCM 重新整理時，它會連至下載任何指派的組態設定的位置。 如果任何必要的資源不存在的節點上，它會從設定的位置自動下載它們。 如果節點已設有[報表伺服器](reportServer.md)，它接著會報告作業的狀態。

> **注意**：本主題適用於 PowerShell 5.0。 如需設定 PowerShell 4.0 中提取用戶端的資訊，請參閱[在 PowerShell 4.0 中使用設定識別碼設定提取用戶端](pullClientConfigID4.md)。

## <a name="configure-the-pull-client-lcm"></a>設定提取用戶端 LCM

執行任何下列範例會建立新的輸出資料夾，名為**PullClientConfigID**和該處放入中繼設定 MOF 檔案。 在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。

若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。 例如：

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>設定識別碼

下列設定範例**ConfigurationID**屬性將 lcm **Guid** ，先前針對此目的。 **ConfigurationID** 供 LCM 用來在提取伺服器上尋找適當設定。 提取伺服器上的設定 MOF 檔案必須命名為 `ConfigurationID.mof`，其中 *ConfigurationID* 是目標節點 LCM 的 **ConfigurationID** 屬性值。 如需詳細資訊，請參閱[發佈到提取伺服器 (v4/v5) 的組態](publishConfigs.md)。

您可以建立的隨機**Guid**下方，或使用範例[New-guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet。

```powershell
[System.Guid]::NewGuid()
```

如需使用詳細資訊**Guid**在您環境中，請參閱[Guid 的計劃](/powershell/dsc/secureserver#guids)。

## <a name="set-up-a-pull-client-to-download-configurations"></a>若要下載組態設定提取用戶端

必須設定每個用戶端**提取**模式和指定的提取伺服器的 url 儲存其組態。 若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。 若要設定 LCM，必須先建立一種特殊設定，再加上 **DSCLocalConfigurationManager** 屬性裝飾。 如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)。

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

在此指令碼中，**ConfigurationRepositoryWeb** 區塊會定義提取伺服器。 **ServerUrl**指定 DSC 提取的 url

### <a name="smb-share"></a>SMB 共用

下列指令碼會設定 LCM 提取設定從 SMB 共用`\\SMBPullServer\Pull`。

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

在 指令碼**ConfigurationRepositoryShare**區塊定義提取伺服器，即在此情況下，只是 SMB 共用。

## <a name="set-up-a-pull-client-to-download-resources"></a>設定提取用戶端下載資源

如果您只有指定**ConfigurationRepositoryWeb**或是**ConfigurationRepositoryShare**封鎖在 LCM 設定 （如同上述範例中），提取用戶端會從相同的資源它會擷取其組態的位置。 您也可以指定不同資源的位置。 若要指定資源位置做為個別的伺服器，請使用**ResourceRepositoryWeb**區塊。 若要指定為 SMB 共用的資源位置，請使用**ResourceRepositoryShare**區塊。

> [!NOTE]
> 您可以結合**ConfigurationRepositoryWeb**具有**ResourceRepositoryShare**或是**ConfigurationRepositoryShare**具有**ResourceRepositoryWeb**. 這個範例不會顯示如下。

### <a name="http-dsc-pull-server"></a>HTTP DSC 提取伺服器

下列中繼設定會設定提取用戶端取得其組態，從**Contoso-pullsrv**和其資源**Contoso-resourcesrv**。

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

下列範例示範中繼設定會設定用戶端以提取設定從 SMB 共用的中繼`\\SMBPullServer\Configurations`，並從 SMB 共用的資源`\\SMBPullServer\Resources`。

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

#### <a name="automatically-download-resources-in-push-mode"></a>自動下載在推送模式中的資源

從 PowerShell 5.0 開始，您的提取用戶端可以下載模組從 SMB 共用，即使它們已針對**推播**模式。 這是在情況下您不想設定提取伺服器中特別有用。 **ResourceRepositoryShare**區塊可以用未指定**ConfigurationRepositoryShare**。 下列範例示範中繼設定會設定用戶端以提取資源從 SMB 共用， `\\SMBPullServer\Resources`。 當節點已**PUSHED**設定時，它會自動下載任何必要的資源，從指定的共用。

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

## <a name="set-up-a-pull-client-to-report-status"></a>設定提取用戶端報告狀態

根據預設，節點不會傳送報表至已設定的提取伺服器。 您可以針對設定、資源和報告使用單一提取伺服器，但必須建立 **ReportRepositoryWeb** 區塊才可設定報告功能。

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

報表伺服器不是 SMB 共用。

## <a name="next-steps"></a>後續步驟

設定提取用戶端之後, 您可以使用下列指南來執行後續步驟：

- [將設定發佈至提取伺服器 (v4/v5)](publishConfigs.md)
- [封裝資源並上傳到提取伺服器 (v4)](package-upload-resources.md)

## <a name="see-also"></a>另請參閱

* [以設定名稱設定提取用戶端](pullClientConfigNames.md)
