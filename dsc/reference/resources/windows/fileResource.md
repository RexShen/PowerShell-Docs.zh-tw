---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 檔案資源
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679296"
---
# <a name="dsc-file-resource"></a>DSC 檔案資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的檔案資源會提供一個機制，在目標節點管理檔案和資料夾。 **DestinationPath**並**SourcePath**兩者都必須是供目標節點。

## <a name="syntax"></a>語法

```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>Properties

|屬性       |描述                                                                   |必要|Default|
|---------------|------------------------------------------------------------------------------|--------|-------|
|DestinationPath|您想要確保目標節點上的位置是`Present`或`Absent`。|是|否|
|屬性     |目標的檔案或目錄的屬性所需的狀態。 有效值**封存**， **Hidden**， **ReadOnly**，以及**系統**。|否|無|
|總和檢查碼      |要判斷是否有兩個檔案都是相同時所使用的總和檢查碼類型。 有效值包括：Sha-1、 SHA-256、 SHA-512、-512、createddate、modifieddate、 modifiedDate。|否|只有檔案或目錄名稱進行比較。|
|內容       |搭配使用時，唯一有效`File`型別。 表示內容，請確定`Present`或`Absent`從目標檔案。 |否|無|
|認證     |輸入的認證才能存取資源，例如來源檔案。|否|目標節點的電腦帳戶。 (*請參閱備註*)|
|Ensure         |目標檔案或目錄所需的狀態。 |否|**目前**|
|Force          |覆寫會導致錯誤 （例如覆寫檔案，或刪除不是空的目錄） 的存取作業。|否|`$false`|
|Recurse        |搭配使用時，唯一有效`Directory`型別。 執行狀態的作業以遞迴方式，所有子目錄中。|否|`$false`|
|DependsOn      |設定指定的資源相依性。 在成功執行的任何相依的資源後，才能執行這項資源。 您可以指定使用語法的相依資源`"[ResourceType]ResourceName"`。 請參閱 [about_DependsOn](../../../configurations/resource-depends-on.md)|否|無|
|SourcePath     |要從中複製檔案或資料夾資源的路徑。|否|無|
|類型           |正在設定的資源類型。 有效值`Directory`和`File`。|否|`File`|
|MatchSource    |決定是否資源應該監視有新檔案新增至來源目錄的初始複本之後。 值為`$true`表示，初始複製之後，任何新的原始程式檔應該要複製到目的地。 如果設定為`$False`，資源會快取來源目錄的內容，並忽略任何初始複本之後新增的檔案。|否|`$false`|

> [!WARNING]
> 如果您未指定的值`Credential`或是`PSRunAsCredential`(PS V.5)，資源會使用目標節點的電腦帳戶來存取`SourcePath`。  當`SourcePath`是 UNC 共用，這可能會導致 「 拒絕存取 」 錯誤。 請確定您的權限會相應地設定，或使用`Credential`或`PSRunAsCredential`屬性，以指定應該使用的帳戶。

## <a name="present-vs-absent"></a>提供 vs。不存在

每個 DSC 資源執行指定的值為基礎的不同作業`Ensure`屬性。 執行您指定的上述屬性決定狀態作業的值。

### <a name="existence"></a>存在

當您只指定`DestinationPath`，資源可確保此路徑是否存在 (`Present`) 或不存在 (`Absent`)。

### <a name="copy-operations"></a>複製作業

當您指定`SourcePath`和`DestinationPath`具有`Type`的值**Directory**，為目的路徑的資源複製來源目錄。 屬性`Recurse`， `Force`，並`MatchSource`變更複製作業的型別執行，而`Credential`判斷哪一個帳戶用來存取來源目錄。

### <a name="limitations"></a>限制

如果您指定的值`ReadOnly`for`Attributes`屬性一起`DestinationPath`，`Ensure = "Present"`會建立指定的路徑時`Contents`會設定檔案的內容。  `Absent`狀態的作業會忽略`Attributes`屬性，請完全移除位於指定路徑的任何檔案。

## <a name="example"></a>範例

下列範例會複製目錄和子目錄從提取伺服器到目標節點使用檔案資源。 如果作業成功，則記錄檔資源會將確認訊息寫入事件記錄檔。

來源目錄是 UNC 路徑 (`\\PullServer\DemoSource`) 從提取伺服器共用。 `Recurse`屬性，可確保一併複製所有的子目錄。

> [!IMPORTANT]
> 根據預設，本機系統帳戶內容中執行目標節點上的 LCM。 若要授與存取權**SourcePath**，授與目標節點的電腦帳戶適當的權限。 **認證**並**PSDSCRunAsCredential** (v5) 兩者都變更用來存取的內容 LCM **SourcePath**。 您仍然需要授與存取權的帳戶將用來存取**SourcePath**。

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

如需在使用**認證**在 DSC，請參閱[使用者的身分執行](../../../configurations/runAsUser.md)或[組態資料認證](../../../configurations/configDataCredentials.md)。
