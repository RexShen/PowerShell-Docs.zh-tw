---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 使用設定識別碼發佈至提取伺服器 (v4/v5)
ms.openlocfilehash: 3b094308338e62c783b19f4d3bb41634feee63f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417248"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>使用設定識別碼發佈至提取伺服器 (v4/v5)

下列各節假設您已經設定提取伺服器。 如果尚未設定提取伺服器，您可以使用下列指南：

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)

每個目標節點都設定為下載設定、資源，甚至是報告其狀態。 此文章顯示如何上傳資源，讓它們可供下載，並設定用戶端以自動下載資源。 當節點透過**提取**或**推送** (v5) 收到指派的設定時，它會自動從本機 Configuration Manager (LCM) 中指定的位置下載設定所需的任何資源。

## <a name="compile-configurations"></a>編譯設定

在提取伺服器上儲存[設定](../configurations/configurations.md)的第一個步驟是將它們編譯成 `.mof` 檔案。 若要使設定通用且適用於更多用戶端，請在節點區塊中使用 `localhost`。 下列範例示範使用 `localhost` 而非特定用戶端名稱的設定殼層。

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

當您編譯一般設定之後，應該會有一個 `localhost.mof` 檔案。

## <a name="renaming-the-mof-file"></a>將 MOF 檔案重新命名

您可以依 **ConfigurationName** 或 **ConfigurationID**，在提取伺服器上儲存設定`.mof` 檔案。 視您計劃設定提取用戶端的方式，您可以選擇下列任一節，適當地將已編譯的 `.mof` 檔案重新命名。

### <a name="configuration-ids-guid"></a>設定識別碼 (GUID)

您必須將您的 `localhost.mof` 檔案重新命名為 `<GUID>.mof` 檔案。 您可以使用以下範例建立隨機 **Guid**，或是使用 [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) Cmdlet。

```powershell
[System.Guid]::NewGuid()
```

取樣輸出

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

您接著可以使用任何可接受的方法來將 `.mof` 檔案重新命名。 下列範例會使用 [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) Cmdlet。

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

如需在您環境中使用 **Guid** 的詳細資訊，請參閱[為 GUID 規劃](/powershell/scripting/dsc/secureserver#guids)。

### <a name="configuration-names"></a>設定名稱

您必須將您的 `localhost.mof` 檔案重新命名為 `<Configuration Name>.mof` 檔案。 在下列範例中，會使用上一節的設定名稱。 您接著可以使用任何可接受的方法來將 `.mof` 檔案重新命名。 下列範例會使用 [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) Cmdlet。

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>建立總和檢查碼

儲存於提取伺服器或 SMB 共用上的每個 `.mof` 檔案都需要有相關聯的 `.checksum` 檔案。
此檔案可讓用戶端知道相關聯的 `.mof` 檔案何時已變更且應再次下載。

您可以使用 [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) Cmdlet 來建立**總和檢查碼**。 您也可以使用 `-Path` 參數，針對檔案的目錄執行 `New-DSCCheckSum`。
如果總和檢查碼已經存在，您可以使用 `-Force` 參數強制重新建立它。 下列範例會指定包含上一節 `.mof` 檔案的目錄，並使用 `-Force` 參數。

```powershell
New-DscChecksum -Path '.\' -Force
```

系統將不會顯示任何輸出，但您現在應該會看到 `<GUID or Configuration Name>.mof.checksum` 檔案。

## <a name="where-to-store-mof-files-and-checksums"></a>儲存 MOF 檔案與總和檢查碼的位置

### <a name="on-a-dsc-http-pull-server"></a>在 DSC HTTP 提取伺服器上

當您設定 HTTP 提取伺服器時，如[設定 DSC HTTP 提取伺服器](pullServer.md)中所述，您會針對 **ModulePath** 和 **ConfigurationPath** 索引碼指定目錄。 **ModulePath** 機碼指出應儲存模組的封裝 `.zip` 檔案的位置。 **ConfigurationPath** 指出應儲存所有 `.mof` 檔案與 `.checksum` 檔案的位置。

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>在 SMB 共用上

當您設定提取用戶端來使用 SMB 共用時，您會指定 **ConfigurationRepositoryShare**。
所有 `.mof` 檔案和 `.checksum` 檔案接著都應儲存於 **ConfigurationRepositoryShare** 區塊的 **SourcePath** 目錄中。

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>接下來的步驟

接下來，您可以設定提取用戶端來提取指定的設定。 如需詳細資訊，請參閱下列任一份指南：

- [使用設定識別碼設定提取用戶端 (v4)](pullClientConfigId4.md)
- [使用設定識別碼設定提取用戶端 (v5)](pullClientConfigId.md)
- [使用設定名稱設定提取用戶端 (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>另請參閱

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)
- [封裝資源並上傳到提取伺服器](package-upload-resources.md)
