---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用設定資料
ms.openlocfilehash: f2d25b9ced805fb4c91378ebfe840104eb6ce52a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400684"
---
# <a name="using-configuration-data-in-dsc"></a>使用 DSC 中的設定資料

> 適用於：Windows PowerShell 4.0 中，Windows PowerShell 5.0

您可以使用內建的 DSC **ConfigurationData** 參數，定義可用於設定中的資料。
這可讓您建立可用於多個節點或不同環境的單一設定。
例如，如果您要開發應用程式，您可以針對開發和生產環境使用一個設定，並使用設定資料來指定每個環境的資料。

本主題將說明 **ConfigurationData** 雜湊表的結構。
如需如何使用設定資料的範例，請參閱[分離設定和環境資料](separatingEnvData.md)。

## <a name="the-configurationdata-common-parameter"></a>ConfigurationData 一般參數

DSC 設定採用 **ConfigurationData** 一般參數，這是編譯設定時所指定的參數。
如需編譯設定的資訊，請參閱 [DSC 設定](configurations.md)。

**ConfigurationData** 參數是至少必須有一個名為 **AllNodes** 之索引鍵的雜湊表。
它也可以包含一或多個其他索引鍵。

> [!NOTE]
> 本主題中的範例使用名為 `NonNodeData` 的單一額外索引鍵 (而不是具名 **AllNodes** 索引鍵)，但是您可以包含任意數目的額外索引鍵，並將它們任意命名。

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

**AllNodes** 索引鍵的值是陣列。 此陣列的每個元素也是至少必須有一個名為 **NodeName** 之索引鍵的雜湊表：

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

您也可以將其他索引鍵新增至每個雜湊表：

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

若要將屬性套用至所有節點，您可以建立 **AllNodes** 陣列的成員，其 **NodeName** 為 `*`。
例如，您可以如下為每個節點提供 `LogPath` 屬性：

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

這相當於將名稱為 `LogPath` 且值為 `"C:\Logs"` 的屬性新增至每個其他區塊 (`VM-1`、`VM-2` 和 `VM-3`)。

## <a name="defining-the-configurationdata-hashtable"></a>定義 ConfigurationData 雜湊表

您可以將 **ConfigurationData** 定義為與設定位於相同指令碼檔內的變數 (如上述範例)，或個別 `.psd1` 檔案中的變數。
若要在 `.psd1` 檔案中定義 **ConfigurationData**，請建立只包含代表設定資料之雜湊表的檔案。

例如，您可以建立具有下列內容的檔案，並命名為 `MyData.psd1`：

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a>編譯具有設定資料的設定

若要編譯您已為其定義設定資料的設定，請將設定資料當作 **ConfigurationData** 參數的值來傳遞。

這會為 **AllNodes** 陣列中的每個項目建立一個 MOF 檔案。
每個 MOF 檔案都會以對應之陣列項目的 `NodeName` 屬性來命名。

例如，如果您依上述 `MyData.psd1` 檔案中的方式定義設定資料，則編譯設定將會同時建立 `VM-1.mof` 和 `VM-2.mof` 檔案。

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>使用變數來編譯具有設定資料的設定

若要使用定義為與設定位於相同 `.ps1` 檔案中之變數的設定資料，請在編譯設定時，將該變數名稱當作 **ConfigurationData** 參數的值來傳遞：

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>使用資料檔來編譯具有設定資料的設定

若要使用在 .psd1 檔案中定義的設定資料，您可以在編譯設定時，傳遞該檔案的路徑和名稱作為 **ConfigurationData** 參數值：

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>在設定中使用 ConfigurationData 變數

DSC 提供下列特殊變數，可用於設定指令碼：

- **$AllNodes** 代表 **ConfigurationData** 中所定義的整個節點集合。 您可以使用 **.Where()** 和 **.ForEach()** 篩選 **AllNodes** 集合。
- **ConfigurationData** 代表編譯設定時，當做參數傳遞的整個雜湊表。
- **MyTypeName**包含[組態](configurations.md)中使用變數的名稱。 例如，在組態`MyDscConfiguration`，則`$MyTypeName`的值`MyDscConfiguration`。
- **Node** 代表 **AllNodes** 集合使用 **.Where()** 或 **.ForEach()** 篩選後所包含的特定項目。
  - 您可以在 [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md) 中深入閱讀這些方法

## <a name="using-non-node-data"></a>使用非節點資料

如我們在先前的範例中所見，**ConfigurationData** 雜湊表除了必要的 **AllNodes** 索引鍵之外，還可以有一或多個索引鍵。
在本主題的範例中，我們只使用了單一額外節點，並將它命名為 `NonNodeData`。
不過，您可以定義任何數目的額外索引鍵，並將它們任意命名。

如需有關使用非節點資料的範例，請參閱[分離設定和環境資料](separatingEnvData.md)。

## <a name="see-also"></a>另請參閱

- [設定資料的認證選項](configDataCredentials.md)
- [DSC 設定](configurations.md)