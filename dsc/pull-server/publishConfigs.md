---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 發佈至提取伺服器，使用設定識別碼 (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400676"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>發佈至提取伺服器，使用設定識別碼 (v4/v5)

下列各節假設您有已設定提取伺服器。 如果您還沒有設定提取伺服器，您可以使用下列指南：

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)

若要下載組態中，資源，並甚至報告其狀態，可以設定每個目標節點。 本文將說明如何上傳資源，讓它們可被下載，並設定用戶端會自動下載的資源。 當節點會收到指派的組態，透過**提取**或是**推送**(v5)，便會自動下載從 LCM 中指定的位置組態所需的任何資源。

## <a name="compile-configurations"></a>編譯組態

若要儲存的第一個步驟[組態](../configurations/configurations.md)在提取伺服器上，是將它們編譯成 「.mof 」 檔案。 若要進行組態，一般和適用於多個用戶端，使用`localhost`節點區塊中。 下列範例顯示使用的設定殼層`localhost`而不是特定用戶端名稱。

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

當您編譯您的一般設定時，您應該有"localhost.mof 」 檔案。

## <a name="renaming-the-mof-file"></a>重新命名的 MOF 檔案

您可以設定 「.mof 」 檔案，提取伺服器上的儲存**ConfigurationName**或是**ConfigurationID**。 根據您計劃如何設定提取用戶端，您可以選擇適當地重新命名已編譯的 「.mof"檔案下一節。

### <a name="configuration-ids-guid"></a>設定識別碼 (GUID)

您必須重新命名您的 「 localhost.mof"檔案，以 「<GUID>.mof 」 檔案。 您可以建立的隨機**Guid**下方，或使用範例[New-guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet。

```powershell
[System.Guid]::NewGuid()
```

取樣輸出

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

然後，您可以重新命名 「.mof"檔案使用任何可接受的方法。 下列範例中，使用[重新命名項目](/powershell/module/microsoft.powershell.management/rename-item)cmdlet。

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

如需使用詳細資訊**Guid**在您環境中，請參閱[Guid 的計劃](/powershell/dsc/secureserver#guids)。

### <a name="configuration-names"></a>設定名稱

您必須重新命名您的 「 localhost.mof"檔案，以 「<Configuration Name>.mof 」 檔案。 在下列範例中，會使用上一節的組態名稱。 然後，您可以重新命名 「.mof"檔案使用任何可接受的方法。 下列範例中，使用[重新命名項目](/powershell/module/microsoft.powershell.management/rename-item)cmdlet。

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>建立總和檢查碼

每個".mof"檔案會儲存在提取伺服器或 SMB 共用上必須有相關聯的 「.checksum"檔案。 此檔案可讓用戶端知道當相關聯的 「.mof"檔案已變更，而且應該會再次下載。

您可以建立**總和檢查碼**具有[New-dscchecksum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet。 您也可以執行`New-DSCCheckSum`檔案的目錄對`-Path`參數。 如果總和檢查碼已經存在，您可以強制它重新建立與`-Force`參數。 下列範例會指定包含上一節中，「.mof 」 檔案的目錄，並使用`-Force`參數。

```powershell
New-DscChecksum -Path '.\' -Force
```

將會顯示任何輸出，但您現在應該會看到 「<GUID or Configuration Name>。 mof.checksum"檔案。

## <a name="where-to-store-mof-files-and-checksums"></a>要儲存 MOF 檔案與總和檢查碼

### <a name="on-a-dsc-http-pull-server"></a>在 DSC HTTP 提取伺服器

當您設定您的 HTTP 提取伺服器，如所述[設定 DSC HTTP 提取伺服器](pullServer.md)，您指定的目錄**ModulePath**並**ConfigurationPath**索引鍵。 **ConfigurationPath**而 key 則代表儲存的任何 「.mof 」 檔案的位置。 **ConfigurationPath**表示來儲存任何 「.mof 「 檔案和".checksum 」 檔案。

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>在 SMB 共用

當您設定提取用戶端使用之 SMB 共用時，您會指定**ConfigurationRepositoryShare**。 所有 「.mof 「 檔案和".checksum"檔案應該則會儲存在**SourcePath**目錄**ConfigurationRepositoryShare**區塊。

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>後續步驟

接下來，您會想要設定提取用戶端提取指定的組態。 如需詳細資訊，請參閱下列指南：

- [設定提取用戶端使用設定識別碼 (v4)](pullClientConfigId4.md)
- [設定提取用戶端使用設定識別碼 (v5)](pullClientConfigId.md)
- [設定提取用戶端使用設定名稱 (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>另請參閱

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)
- [封裝並上傳到提取伺服器的資源](package-upload-resources.md)
