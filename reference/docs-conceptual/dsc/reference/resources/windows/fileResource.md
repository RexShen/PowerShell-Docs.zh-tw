---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC 檔案資源
ms.openlocfilehash: 28e9ea3a590a0972e505912efae4a934bc39ba1d
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88799599"
---
# <a name="dsc-file-resource"></a>DSC 檔案資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 的**檔案**資源會提供機制，以在目標節點管理檔案和資料夾。 **DestinationPath** 和 **SourcePath** 都必須可供目標節點存取。

## <a name="syntax"></a>語法

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|DestinationPath |您想要確保目標節點上的位置是 **Present** 或 **Absent** 與 **Ensure**。 |
|屬性 |目標檔案或目錄屬性的預期狀態。 有效值為 _Archive_、_Hidden_、_ReadOnly_ 及 _System_。 |
|總和檢查碼 |判斷兩個檔案是否相同時所使用的總和檢查碼類型。 有效值包括：**SHA-1**、**SHA-256**、**SHA-512**、**createdDate**、**modifiedDate**。 |
|內容 |只有在搭配**類型** **檔案**類型使用時才有效。 表示在目標檔案中要確認的內容為 **Present** 或 **Absent** 與 **Ensure**。 |
|認證 |存取資源所需的認證，例如來源檔案。 |
|Force |覆寫會導致錯誤的存取作業 (例如覆寫檔案，或刪除不是空的目錄)。 預設值為 `$false`。 |
|Recurse |只有在搭配**類型** **目錄**使用時才有效。 以遞迴方式對所有目錄內容、子目錄和子目錄內容執行狀態作業。 預設值為 `$false`。 |
|SourcePath |要從中複製檔案或資料夾資源的路徑。 |
|類型 |要設定的資源類型。 有效值為 **Directory** 和 **File**。 預設值為 **File**。 |
|MatchSource |判斷資源是否應該監視在初始複本之後新增至來源目錄的新檔案。 若值為 `$true`，即表示在初始複本之後，任何新的原始程式檔都應該複製到目的地。 若設為 `$false`，資源就會快取來源目錄的內容，並忽略任何初始複本之後新增的檔案。 預設值為 `$false`。 |

> [!WARNING]
> 如果您未指定 **Credential** 或 **PSRunAsCredential** 的值，資源將使用目標節點的電腦帳戶來存取 **SourcePath**。 當 **SourcePath** 為 UNC 共用時，這可能導致「拒絕存取」錯誤。 請確定已相應地設定您的權限，或使用 **Credential** 或 **PSRunAsCredential** 屬性來指定應使用的帳戶。

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |判斷位於 **Destination** 的檔案和 **Contents** 是否應存在。 將此屬性設定為 **Present** 以確保檔案存在。 設為 **Absent** 以確保它們不存在。 預設值為 **Present**。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

### <a name="additional-information"></a>其他資訊

- 當您只指定 **DestinationPath** 時，資源可確保路徑存在 (若為 **Present**) 或不存在 (若為 **Absent**)。
- 當您以 **Directory** 的 **Type** 值指定 **SourcePath** 和 **DestinationPath** 時，資源會將來源目錄複寫到目的地路徑。 屬性 **Recurse**、**Force** 和 **MatchSource** 會變更所執行的複製作業類型，而 **Credential** 會判斷要使用哪一個帳戶來存取來源目錄。
- 如果未在複製目錄時將 **Recurse** 屬性設定為 `$true`，即不會複製現有目錄的任何內容。 只會複製指定的目錄。
- 如果您為 **Attributes** 屬性和 **DestinationPath** 指定了 **ReadOnly** 值，則 **Ensure** **Present** 會建立指定的路徑，而 **Contents** 會設定檔案的內容。 **Ensure** **Absent** 設定會完全忽略 **Attributes** 屬性，並移除指定路徑上的任何檔案。

## <a name="example"></a>範例

下列範例會使用檔案資源，將某個目錄及其子目錄從提取伺服器複製到目標節點。 如果此作業成功，記錄資源就會將確認訊息寫入至事件記錄檔。

來源目錄是從提取伺服器共用的 UNC 路徑 (`\\PullServer\DemoSource`)。 **Recurse** 屬性確保會一併複製所有子目錄。

> [!IMPORTANT]
> 根據預設，目標節點上的 LCM 會在本機系統帳戶的內容中執行。 若要授與存取 **SourcePath**，請為目標節點的電腦帳戶提供適當的權限。 **Credential** 和 **PSDSCRunAsCredential** 都會變更 LCM 用來存取 **SourcePath** 的內容。 您仍然需要授與存取將用來存取 **SourcePath** 的帳戶。

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
