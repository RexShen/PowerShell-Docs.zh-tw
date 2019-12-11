---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 在 PowerShell 4.0 中使用設定識別碼來設定提取用戶端
ms.openlocfilehash: 9259c624c8725f7d76f61e9ad7caa42e1bfa308c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71955145"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>在 PowerShell 4.0 中使用設定識別碼來設定提取用戶端

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

> [!IMPORTANT]
> 提取伺服器 (Windows 功能「DSC 服務」  ) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。 建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。

在設定提取用戶端前，您應先設定提取伺服器。 雖然此順序非必要，但它有助於疑難排解，且可協助您確認註冊成功。 若要設定提取伺服器，您可以使用下列指南：

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)

每個目標節點都設定為下載設定、資源，甚至是報告其狀態。 下列各節會示範如何使用 SMB 共用或 HTTP DSC 提取伺服器來設定提取用戶端。 當節點的 LCM 重新整理時，它會連到設定的位置來下載任何所指派設定。 若有任何必要資源不存在於節點上，則其會自動從設定的位置下載它們。 若節點已使用[報表伺服器](reportServer.md)進行設定，它接著便會報告作業的狀態。

## <a name="configure-the-pull-client-lcm"></a>設定提取用戶端 LCM

執行以下任何一個範例，便會建立名為 **PullClientConfigID** 的新輸出資料夾，並在該處放入中繼設定 MOF 檔案。 在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。

若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。 例如：

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>設定識別碼

下列範例會將 LCM 的 **ConfigurationID** 屬性設定為先前基於此用途建立的 **Guid**。 **ConfigurationID** 供 LCM 用來在提取伺服器上尋找適當設定。 提取伺服器上的設定 MOF 檔案必須命名為 `ConfigurationID.mof`，其中 *ConfigurationID* 是目標節點 LCM 的 **ConfigurationID** 屬性值。 如需詳細資訊，請參閱[將設定發佈到提取伺服器 (v4/v5)](publishConfigs.md)。

您可以使用下列範例來建立隨機的 **Guid**。

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>設定提取用戶端來下載設定

每個用戶端都必須在**提取**模式中設定，並提供儲存其設定的提取伺服器 URL。 若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。 若要設定 LCM，您可以搭配 **DSCLocalConfigurationManager** 區塊來建立特殊類型的設定。 如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig4.md)。

## <a name="http-dsc-pull-server"></a>HTTP DSC 提取伺服器

如果將提取伺服器設定為 Web 服務，您就要將 **DownloadManagerName** 設定為 **WebDownloadManager**。 **WebDownloadManager** 要求您為 **DownloadManagerCustomData** 索引碼指定 **ServerUrl**。 您也可以指定 **AllowUnsecureConnection** 的值，如下列範例所示。 下列指令碼會設定 LCM 從名為 "PullServer" 的伺服器提取設定。

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = "TRUE"}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>SMB 共用

如果將提取伺服器設定為 SMB 檔案共用，而不是 Web 服務，您就要將 **DownloadManagerName** 設定為 **DscFileDownloadManager**，而不是 **WebDownLoadManager**。 **DscFileDownloadManager** 要求您在 **DownloadManagerCustomData** 中指定 **SourcePath** 屬性。 下列指令碼會設定 LCM，使其從名為 "CONTOSO-SERVER" 的伺服器上名為 "SmbDscShare" 的 SMB 共用提取設定。

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a>後續步驟

設定提取用戶端之後，您可以使用下列指南來執行後續步驟：

- [將設定發佈至提取伺服器 (v4/v5)](publishConfigs.md)
- [封裝資源並上傳到提取伺服器 (v4)](package-upload-resources.md)

## <a name="see-also"></a>另請參閱

- [設定 DSC Web 提取伺服器](pullServer.md)
- [設定 DSC SMB 提取伺服器](pullServerSMB.md)
