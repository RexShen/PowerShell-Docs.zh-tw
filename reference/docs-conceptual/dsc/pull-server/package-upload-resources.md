---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 封裝資源並上傳到提取伺服器
ms.openlocfilehash: 8aac343d7495ecda94ed76d1d97079397eecd65f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278491"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>封裝資源並上傳到提取伺服器

下列各節假設您已經設定提取伺服器。 如果尚未設定提取伺服器，您可以使用下列指南：

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)

每個目標節點都設定為下載設定、資源，甚至是報告其狀態。 本文將示範如何上傳資源，讓它們可供下載，並設定用戶端以自動下載資源。 當節點收到指派的設定時，透過**提取**或**推送** (v5)，它就會自動從 LCM 中指定的位置下載設定所需的任何資源。

## <a name="package-resource-modules"></a>封裝資源模組

每個可供用戶端下載的資源都必須儲存為 ".zip" 檔案。 下列範例將示範使用 [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) \(英文\) 資源所需的步驟。

> [!NOTE]
> 如果您有任何使用 PowerShell 4.0 的用戶端，您將需要使資源資料夾結構成為單層式，並移除任何版本資料夾。 如需詳細資訊，請參閱[多個資源版本](../configurations/import-dscresource.md#multiple-resource-versions)。

您可以使用任何慣用的公用程式、指令碼或方法來壓縮資源目錄。 在 Windows 中，您可「以滑鼠右鍵按一下」  "xPSDesiredStateConfiguration" 目錄，然後依序選取 [傳送到] 和 [壓縮資料夾]。

![以滑鼠右鍵按一下](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a>為資源封存命名

資源封存必須使用下列格式來命名：

```
{ModuleName}_{Version}.zip
```

在上述範例中，應該將 "xPSDesiredStateConfiguration.zip" 重新命名為 "xPSDesiredStateConfiguration_8.4.4.0.zip"。

### <a name="create-checksums"></a>建立總和檢查碼

一旦將資源模組壓縮並重新命名之後，您必須建立**總和檢查碼**。  用戶端上的 LCM 會使用**總和檢查碼**來判斷資源是否已變更且需要再次下載。 您可以使用 **New-DSCCheckSum** Cmdlet 來建立[總和檢查碼](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)，如以下範例所示。

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

系統將不會顯示任何輸出，但您現在應該會看到 "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum"。 您也可以使用 `New-DSCCheckSum` 參數，針對檔案的目錄執行 `-Path`。 如果總和檢查碼已經存在，您可以使用 `-Force` 參數強制重新建立它。

### <a name="where-to-store-resource-archives"></a>儲存資源封存的位置

#### <a name="on-a-dsc-http-pull-server"></a>在 DSC HTTP 提取伺服器上

當您設定 HTTP 提取伺服器時，如[設定 DSC HTTP 提取伺服器](pullServer.md)中所述，您會針對 **ModulePath** 和 **ConfigurationPath** 索引碼指定目錄。 **ConfigurationPath** 索引碼指出應儲存所有 ".mof" 檔案的位置。 **ModulePath** 指出應儲存所有 DSC 資源模組的位置。

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>在 SMB 共用上

如果您指定了 **ResourceRepositoryShare**，當您設定提取用戶端時，需將封存與總和檢查碼儲存於 **ResourceRepositoryShare** 區塊的 **SourcePath** 目錄中。

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

如果您只指定 **ConfigurationRepositoryShare**，當您設定提取用戶端時，則需將封存與總和檢查碼儲存於 **ConfigurationRepositoryShare** 區塊的 **SourcePath** 目錄中。

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>更新資源

您可以藉由變更封存名稱中的版本號碼，或建立新的總和檢查碼，來強制節點更新其資源。 提取用戶端將檢查較新版本的必要資源，而且會在其 LCM 重新整理時更新總和檢查碼。

## <a name="see-also"></a>另請參閱

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)
