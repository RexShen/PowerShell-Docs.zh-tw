---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 在 PowerShell 5.0 及更新版本中使用設定名稱來設定提取用戶端
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953625"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>在 PowerShell 5.0 及更新版本中使用設定名稱來設定提取用戶端

> 適用於：Windows PowerShell 5.0

> [!IMPORTANT]
> 提取伺服器 (Windows 功能「DSC 服務」  ) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。 建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。

在設定提取用戶端前，您應先設定提取伺服器。 雖然此順序非必要，但它有助於疑難排解，且可協助您確認註冊成功。 若要設定提取伺服器，您可以使用下列指南：

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)

每個目標節點都設定為下載設定、資源，甚至是報告其狀態。 下列各節會示範如何使用 SMB 共用或 HTTP DSC 提取伺服器來設定提取用戶端。 當節點的 LCM 重新整理時，它會連到設定的位置來下載任何所指派設定。 若有任何必要資源不存在於節點上，則其會自動從設定的位置下載它們。 若節點已使用[報表伺服器](reportServer.md)進行設定，它接著便會報告作業的狀態。

> [!NOTE]
> 本主題適用於 PowerShell 5.0。
> 如需在 PowerShell 4.0 中設定提取用戶端的資訊，請參閱[在 PowerShell 4.0 中使用設定識別碼設定提取用戶端](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>設定提取用戶端 LCM

執行以下任何一個範例，便會建立名為 **PullClientConfigName** 的新輸出資料夾，並在該處放置中繼設定 MOF 檔案。 在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。

若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。 例如：

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>設定名稱

下列範例會將 LCM 的 **ConfigurationName** 屬性設為專為此用途建立的先前編譯設定名稱。 **ConfigurationName** 可讓 LCM 用來在提取伺服器上尋找適當設定。 提取伺服器上的設定 MOF 檔案必須命名為 `<ConfigurationName>.mof`，在此案例中為 "ClientConfig.mof"。 如需詳細資訊，請參閱[將設定發佈到提取伺服器 (v4/v5)](publishConfigs.md)。

## <a name="set-up-a-pull-client-to-download-configurations"></a>設定提取用戶端來下載設定

每個用戶端都必須在**提取**模式中設定，並提供儲存其設定的提取伺服器 URL。 若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。 若要設定 LCM，必須先建立一種特殊設定，再加上 **DSCLocalConfigurationManager** 屬性裝飾。 如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)。

下列指令碼會設定 LCM 從名為 "CONTOSO-PullSrv" 的伺服器提取設定。

- 在此指令碼中，**ConfigurationRepositoryWeb** 區塊會定義提取伺服器。 **ServerURL** 屬性會指定提取伺服器的端點。

- **RegistrationKey** 屬性是提取伺服器的所有用戶端節點與該提取伺服器之間的共用金鑰。 相同的值儲存在提取伺服器上的檔案。
  > [!NOTE]
  > 註冊金鑰僅適用於 **Web** 提取伺服器。 您在 **SMB** 提取伺服器仍必須使用 **ConfigurationID**。
  > 如需使用 **ConfigurationID** 設定提取伺服器的資訊，請參閱[使用設定識別碼設定提取用戶端](pullClientConfigId.md)

- **ConfigurationNames** 屬性是陣列，會指定用於用戶端節點的設定名稱。
  >**注意：** 如果您在 **ConfigurationNames** 中指定多個值，就也必須在設定中指定 **PartialConfiguration** 區塊。
  >如需部分設定的相關資訊，請參閱 [PowerShell 預期狀態設定部分設定](partialConfigs.md)。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a>設定提取用戶端以下載資源

若您在 LCM 設定中只指定 **ConfigurationRepositoryWeb** 或 **ConfigurationRepositoryShare** 區塊 (如同先前範例)，提取用戶端會從儲存您 ".mof" 檔案的相同位置提取資源。 您也可以指定不同位置，讓用戶端可以下載資源。 若要指定資源伺服器，您可使用 **ResourceRepositoryWeb** (適用於 Web 提取伺服器) 或 **ResourceRepositoryShare** 區塊 (適用於 SMB 提取伺服器)。

下列範例會顯示中繼設定，其設定用戶端從提取伺服器下載設定，並從 SMB 共用下載資源。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a>設定提取用戶端以報告狀態

您可以針對設定、資源和報告使用單一提取伺服器。 根據預設，不會針對用戶端設定報告。 若要設定用戶端報告狀態，您必須建立一個 **ReportRepositoryWeb** 區塊。 下列範例示範中繼設定，該中繼設定會設定用戶端以提取設定和資源，並將報告資料傳送至單一提取伺服器。

> [!NOTE]
> 報表伺服器不可以是 SMB 共用。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>另請參閱

* [以設定識別碼設定提取用戶端](PullClientConfigNames.md)
* [設定 DSC Web 提取伺服器](pullServer.md)
