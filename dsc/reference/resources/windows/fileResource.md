---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 檔案資源
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077325"
---
# <a name="dsc-file-resource"></a>DSC 檔案資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的檔案資源會提供一個機制，在目標節點管理檔案和資料夾。 **DestinationPath** 和 **SourcePath** 都必須可供目標節點存取。

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
|DestinationPath|您想要確保目標節點上的位置是 `Present` 或 `Absent`。|是|否|
|屬性     |目標檔案或目錄屬性的預期狀態。 有效值為 **Archive**、**Hidden**、**ReadOnly** 及 **System**。|否|無|
|總和檢查碼      |判斷兩個檔案是否相同時所使用的總和檢查碼類型。 有效值包括：SHA-1、SHA-256、SHA-512、createdDate、modifiedDate。|否|只會比較檔案或目錄名稱。|
|內容       |只有在搭配 `File` 類型使用時才有效。 表示在目標檔案中要確認的內容為 `Present` 或 `Absent`。 |否|無|
|認證     |存取資源所需的認證，例如來源檔案。|否|目標節點的電腦帳戶。 (*請參閱備註*)|
|Ensure         |目標檔案或目錄的預期狀態。 |否|**目前**|
|Force          |覆寫會導致錯誤的存取作業 (例如覆寫檔案，或刪除不是空的目錄)。|否|`$false`|
|Recurse        |只有在搭配 `Directory` 類型使用時才有效。 以遞迴方式在所有子目錄中執行狀態作業。|否|`$false`|
|DependsOn      |在指定的資源上設定相依性。 唯有成功執行任何相依資源之後，此資源才能執行。 您可以使用 `"[ResourceType]ResourceName"` 語法來指定相依資源。 請參閱 [about_DependsOn](../../../configurations/resource-depends-on.md)|否|無|
|SourcePath     |要從中複製檔案或資料夾資源的路徑。|否|無|
|類型           |要設定的資源類型。 有效值為 `Directory` 和 `File`。|否|`File`|
|MatchSource    |判斷資源是否應該監視在初始複本之後新增至來源目錄的新檔案。 若值為 `$true`，即表示在初始複本之後，任何新的原始程式檔都應該複製到目的地。 若設為 `$False`，資源就會快取來源目錄的內容，並忽略任何初始複本之後新增的檔案。|否|`$false`|

> [!WARNING]
> 如果您未指定 `Credential` 或 `PSRunAsCredential` (PS V.5) 的值，資源將使用目標節點的電腦帳戶來存取 `SourcePath`。  當 `SourcePath` 為 UNC 共用時，這可能導致「拒絕存取」錯誤。 請確定會據以設定您的權限，或是使用 `Credential` 或 `PSRunAsCredential` 屬性來指定應使用的帳戶。

## <a name="present-vs-absent"></a>Present 與Absent

每個 DSC 資源都會根據您針對 `Ensure` 屬性指定的值來執行不同的作業。 您針對上述屬性指定的值會決定要執行的狀態作業。

### <a name="existence"></a>存在

當您只指定 `DestinationPath` 時，資源可確保路徑存在 (`Present`) 或不存在 (`Absent`)。

### <a name="copy-operations"></a>複製作業

當您指定 `SourcePath` 和 `DestinationPath` 且 `Type` 的值為 **Directory** 時，資源會將來源目錄複製到目的地路徑。 屬性 `Recurse`、`Force` 及 `MatchSource` 會變更所執行的複製作業類型，而 `Credential` 會判斷要使用哪一個帳戶來存取來源目錄。

### <a name="limitations"></a>限制

如果您與 `DestinationPath` 一起為 `Attributes` 屬性指定了 `ReadOnly` 的值，則 `Ensure = "Present"` 會建立指定的路徑，而 `Contents` 會設定檔案的內容。  `Absent` 狀態作業會完全忽略 `Attributes` 屬性，並移除指定路徑上的任何檔案。

## <a name="example"></a>範例

下列範例會使用檔案資源，將某個目錄及其子目錄從提取伺服器複製到目標節點。 如果此作業成功，記錄資源就會將確認訊息寫入至事件記錄檔。

來源目錄是從提取伺服器共用的 UNC 路徑 (`\\PullServer\DemoSource`)。 `Recurse` 屬性確保會一併複製所有子目錄。

> [!IMPORTANT]
> 根據預設，目標節點上的 LCM 會在本機系統帳戶的內容中執行。 若要授與存取 **SourcePath**，請為目標節點的電腦帳戶提供適當的權限。 **Credential** 和 **PSDSCRunAsCredential** (v5) 都會變更 LCM 用來存取 **SourcePath** 的內容。 您仍然需要授與存取將用來存取 **SourcePath** 的帳戶。

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

如需在 DSC 中使用**認證**的詳細資訊，請參閱[以使用者身分執行](../../../configurations/runAsUser.md)或[設定資料認證](../../../configurations/configDataCredentials.md)。
