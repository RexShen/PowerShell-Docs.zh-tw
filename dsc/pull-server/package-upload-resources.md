---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 封裝並上傳到提取伺服器的資源
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400651"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>封裝並上傳到提取伺服器的資源

下列各節假設您有已設定提取伺服器。 如果您還沒有設定提取伺服器，您可以使用下列指南：

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)

若要下載組態中，資源，並甚至報告其狀態，可以設定每個目標節點。 本文將說明如何上傳資源，讓它們可被下載，並設定用戶端會自動下載的資源。 當節點會收到指派的組態，透過**提取**或是**推送**(v5)，便會自動下載從 LCM 中指定的位置組態所需的任何資源。

## <a name="package-resource-modules"></a>套件資源模組

若要下載的用戶端可用的每個資源必須儲存在 「.zip 」 檔案。 下列範例會顯示所需的步驟，使用[xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0)資源。

> [!NOTE]
> 如果您有任何使用 PowerShell 4.0 的用戶端時，您將需要 flaten 資源資料夾結構，並移除任何版本的資料夾。 如需詳細資訊，請參閱 <<c0> [ 多個資源版本](../configurations/import-dscresource.md#multiple-resource-versions)。

您可以壓縮任何公用程式、 指令碼或您偏好的方法所使用的資源目錄。 在 Windows 中，您可以*上按一下滑鼠右鍵*"xPSDesiredStateConfiguration"目錄，然後選取 「 傳送到"，則 「 壓縮資料夾 」。

![以滑鼠右鍵按一下](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>命名資源封存

資源封存，就必須使用下列格式命名：

```
{ModuleName}_{Version}.zip
```

在上述範例中，「 xPSDesiredStateConfiguration.zip"應該是已重新命名 「 xPSDesiredStateConfiguration_8.4.4.0.zip"。

### <a name="create-checksums"></a>建立總和檢查碼

一旦已壓縮並重新命名資源模組，您需要建立**總和檢查碼**。  **總和檢查碼**使用時，依用戶端上的 LCM 以判斷資源已變更，且必須再次下載。 您可以建立**總和檢查碼**具有[New-dscchecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet，如下列範例所示。

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

將會顯示任何輸出，但您現在應該會看到 「 xPSDesiredStateConfiguration_8.4.4.0.zip.checksum"。 您也可以執行`New-DSCCheckSum`檔案的目錄對`-Path`參數。 如果總和檢查碼已經存在，您可以強制它重新建立與`-Force`參數。

### <a name="where-to-store-resource-archives"></a>儲存資源封存位置

#### <a name="on-a-dsc-http-pull-server"></a>在 DSC HTTP 提取伺服器

當您設定您的 HTTP 提取伺服器，如所述[設定 DSC HTTP 提取伺服器](pullServer.md)，您指定的目錄**ModulePath**並**ConfigurationPath**索引鍵。 **ConfigurationPath**而 key 則代表儲存的任何 「.mof 」 檔案的位置。 **ModulePath**指出應儲存的任何 DSC 資源模組。

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>在 SMB 共用

如果您指定**ResourceRepositoryShare**，當您提取用戶端，設定存放區封存和總和檢查碼，在**SourcePath**目錄從**ResourceRepositoryShare**區塊。

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

如果您只指定**ConfigurationRepositoryShare**，當您提取用戶端，設定存放區封存和總和檢查碼，在**SourcePath**目錄從**ConfigurationRepositoryShare**區塊。

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>更新資源

您可以強制更新其資源，藉由變更版本號碼，在 封存的名稱，或建立新的總和檢查碼的節點。 提取用戶端會檢查所需的資源，較新版本，以及其 LCM 會重新整理時更新總和檢查碼。

## <a name="see-also"></a>另請參閱

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)
