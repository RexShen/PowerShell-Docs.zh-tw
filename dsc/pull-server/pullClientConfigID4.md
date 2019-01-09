---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 設定提取用戶端在 PowerShell 4.0 中使用設定識別碼
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400876"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>設定提取用戶端在 PowerShell 4.0 中使用設定識別碼

>適用於：Windows PowerShell 4.0 中，Windows PowerShell 5.0

> [!IMPORTANT]
> 提取伺服器 (Windows 功能「DSC 服務」) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。 建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。

設定提取用戶端之前, 您應該設定提取伺服器。 雖然此順序並不需要，它會協助進行疑難排解，並幫助您確認註冊成功。 若要設定提取伺服器，您可以使用下列指南：

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)

若要下載組態中，資源，並甚至報告其狀態，可以設定每個目標節點。 下列各節會示範如何設定提取用戶端與 SMB 共用或 HTTP DSC 提取伺服器。 當節點 LCM 重新整理時，它會連至下載任何指派的組態設定的位置。 如果任何必要的資源不存在的節點上，它會從設定的位置自動下載它們。 如果節點已設有[報表伺服器](reportServer.md)，它接著會報告作業的狀態。

## <a name="configure-the-pull-client-lcm"></a>設定提取用戶端 LCM

執行任何下列範例會建立新的輸出資料夾，名為**PullClientConfigID**和該處放入中繼設定 MOF 檔案。 在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。

若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。 例如：

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>設定識別碼

下列範例**ConfigurationID**屬性將 lcm **Guid** ，先前針對此目的。 **ConfigurationID** 供 LCM 用來在提取伺服器上尋找適當設定。 提取伺服器上的設定 MOF 檔案必須命名為 `ConfigurationID.mof`，其中 *ConfigurationID* 是目標節點 LCM 的 **ConfigurationID** 屬性值。 如需詳細資訊，請參閱 <<c0> [ 發佈到提取伺服器 (v4/v5) 的組態](publishConfigs.md)。

您可以建立的隨機**Guid**使用下列範例。

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>若要下載組態設定提取用戶端

必須設定每個用戶端**提取**模式和指定的提取伺服器的 url 儲存其組態。 若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。 若要設定 LCM，您必須建立一種特殊的設定，與**LocalConfigurationManager**區塊。 如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig4.md)。

## <a name="http-dsc-pull-server"></a>HTTP DSC 提取伺服器

如果提取伺服器設定為 web 服務，您會設定**DownloadManagerName**要**WebDownloadManager**。 **WebDownloadManager**會要求您指定**ServerUrl**來**DownloadManagerCustomData**索引鍵。 您也可以指定的值**AllowUnsecureConnection**，如下列範例所示。 下列指令碼會設定 LCM 從名為 "PullServer" 的伺服器提取設定。

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
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>SMB 共用

如果提取伺服器設定為 SMB 檔案共用，而不是 web 服務，您會設定**DownloadManagerName**要**DscFileDownloadManager**而非**WebDownLoadManager**. **DscFileDownloadManager**會要求您指定**SourcePath**中的屬性**DownloadManagerCustomData**。 下列指令碼會設定 LCM，使其從名為 "CONTOSO-SERVER" 的伺服器上名為 "SmbDscShare" 的 SMB 共用提取設定。

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

設定提取用戶端之後, 您可以使用下列指南來執行後續步驟：

- [將設定發佈至提取伺服器 (v4/v5)](publishConfigs.md)
- [封裝資源並上傳到提取伺服器 (v4)](package-upload-resources.md)

## <a name="see-also"></a>另請參閱

- [設定 DSC web 提取伺服器](pullServer.md)
- [設定 DSC SMB 提取伺服器](pullServerSMB.md)
