---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 設定提取用戶端使用設定名稱，在 PowerShell 5.0 和更新版本
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400896"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>設定提取用戶端使用設定名稱，在 PowerShell 5.0 和更新版本

> 適用於：Windows PowerShell 5.0

> [!IMPORTANT]
> 提取伺服器 (Windows 功能「DSC 服務」) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。 建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。

設定提取用戶端之前, 您應該設定提取伺服器。 雖然此順序並不需要，它會協助進行疑難排解，並幫助您確認註冊成功。 若要設定提取伺服器，您可以使用下列指南：

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)

若要下載組態中，資源，並甚至報告其狀態，可以設定每個目標節點。 下列各節會示範如何設定提取用戶端與 SMB 共用或 HTTP DSC 提取伺服器。 當節點 LCM 重新整理時，它會連至下載任何指派的組態設定的位置。 如果任何必要的資源不存在的節點上，它會從設定的位置自動下載它們。 如果節點已設有[報表伺服器](reportServer.md)，它接著會報告作業的狀態。

> **注意**：本主題適用於 PowerShell 5.0。
如需設定 PowerShell 4.0 中提取用戶端的詳細資訊，請參閱[設定提取用戶端在 PowerShell 4.0 使用設定識別碼](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>設定提取用戶端 LCM

執行任何下列範例會建立新的輸出資料夾，名為**PullClientConfigName**和該處放入中繼設定 MOF 檔案。 在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。

若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。 例如：

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>設定名稱

下列設定範例**ConfigurationName**針對這個用途建立的先前已編譯的設定，名稱將 lcm 的屬性。 **ConfigurationName**供 LCM 用來尋找適當設定提取伺服器上。 提取伺服器的設定 MOF 檔案必須命名為`<ConfigurationName>.mof`，在此案例中，「 ClientConfig.mof"。 如需詳細資訊，請參閱 <<c0> [ 發佈到提取伺服器 (v4/v5) 的組態](publishConfigs.md)。

## <a name="set-up-a-pull-client-to-download-configurations"></a>若要下載組態設定提取用戶端

必須設定每個用戶端**提取**模式和指定的提取伺服器的 url 儲存其組態。 若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。 若要設定 LCM，必須先建立一種特殊設定，再加上 **DSCLocalConfigurationManager** 屬性裝飾。 如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)。

下列指令碼會設定 LCM 從名為 "CONTOSO-PullSrv" 的伺服器提取設定。

- 在此指令碼中，**ConfigurationRepositoryWeb** 區塊會定義提取伺服器。 **ServerURL** 屬性會指定提取伺服器的端點。

- **RegistrationKey** 屬性是提取伺服器的所有用戶端節點與該提取伺服器之間的共用金鑰。 相同的值儲存在提取伺服器上的檔案。
  > **注意**：註冊金鑰僅適用於**web**提取伺服器。 您在 **SMB** 提取伺服器仍必須使用 **ConfigurationID**。
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

## <a name="set-up-a-pull-client-to-download-resources"></a>設定提取用戶端下載資源

如果您只有指定**ConfigurationRepositoryWeb**或是**ConfigurationRepositoryShare**封鎖在 LCM 設定 （如同上例），提取用戶端會從相同的資源儲存 「.mof 」 檔案的位置。 您也可以指定不同的位置，其中用戶端可以下載資源。 若要指定資源伺服器，您可使用 **ResourceRepositoryWeb** (適用於 Web 提取伺服器) 或 **ResourceRepositoryShare** 區塊 (適用於 SMB 提取伺服器)。

下列範例示範中繼設定，將用戶端設定來設定從提取伺服器，並從 SMB 共用的資源。

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

## <a name="set-up-a-pull-client-to-report-status"></a>設定提取用戶端報告狀態

您可以針對設定、 資源和報告使用單一提取伺服器。 報告未設定用戶端的預設。 若要設定的用戶端報告狀態，您必須建立**ReportRepositoryWeb**區塊。 下列範例示範中繼設定，該中繼設定會設定用戶端以提取設定和資源，並將報告資料傳送至單一提取伺服器。

> [!NOTE]
> 報表伺服器不是 SMB 共用。

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
