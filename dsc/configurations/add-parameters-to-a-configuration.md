---
ms.date: 12/12/2018
keywords: dsc，powershell、 資源、 資源庫、 安裝程式
title: 將參數新增至設定
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400715"
---
# <a name="add-parameters-to-a-configuration"></a>將參數新增至設定

函數，類似[組態](configurations.md)一種可以參數化，以允許更多動態組態，根據使用者輸入。 中所描述的步驟大致[具有參數的函式](/powershell/module/microsoft.powershell.core/about/about_functions)。

此範例會啟動基本的設定會設定為 「 執行 」 的 「 多工緩衝處理器 」 服務。

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a>內建的組態參數

不同於函式， [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)屬性新增任何功能。 除了[一般參數](/powershell/module/microsoft.powershell.core/about/about_commonparameters)，組態也可以使用下列內建參數，而不需要您定義它們。

|參數  |描述  |
|---------|---------|
|`-InstanceName`|用於定義[複合設定](compositeconfigs.md)|
|`-DependsOn`|用於定義[複合設定](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|用於定義[複合設定](compositeconfigs.md)|
|`-ConfigurationData`|用來將傳遞的結構化[組態資料](configData.md)組態中使用。|
|`-OutputPath`|用來指定的位置，您 「\<computername\>.mof"檔案將會編譯|

## <a name="adding-your-own-parameters-to-configurations"></a>將您自己的參數新增至組態

除了內建的參數，您也可以新增您自己的參數到您的設定。 在參數區塊會直接在設定宣告，就像函式。 設定參數區塊應該是任何外部**節點**宣告，及任何上面*匯入*陳述式。 新增參數，您可以在更穩定且動態進行您的設定。

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>將 ComputerName 參數

您可以新增第一個參數是`-Computername`參數，讓您以動態方式可以編譯 「.mof 」 檔案的任何`-Computername`您傳遞給您的設定。 例如函式中，您也可以定義預設值，如果使用者未通過的值 `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

在您的設定，然後您可以指定您`-ComputerName`參數定義您的節點區塊時。

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>呼叫您的組態參數

您已將參數加入到您的組態之後，您可以使用它們，就像您使用 cmdlet。

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>編譯多個.mof 檔案

節點區塊也可接受電腦名稱的逗號分隔的清單，並會針對每個產生 「.mof 」 檔案。 您可以執行下列範例產生的所有電腦傳遞至 「.mof"檔案`-ComputerName`參數。

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a>在組態中的進階的參數

除了`-ComputerName`參數，我們可以新增的服務名稱和狀態的參數。 下列範例會將參數區塊`-ServiceName`參數並使用它來動態定義**服務**資源區塊。 它也會新增`-State`參數來動態定義**狀態**中**服務**資源區塊。

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> 在多個 advacned 案例中，它可能會讓您動態的資料移至結構化比較合理[組態資料](configData.md)。

範例組態現在會採用動態`$ServiceName`，但如果未指定其中一個項目，則編譯會產生錯誤。 您可以新增如下列範例的預設值。

```powershell
[String]
$ServiceName="Spooler"
```

在本例中，它比較理想的只會強制使用者指定的值`$ServiceName`參數。 `parameter`屬性可讓您將進一步的驗證和管線支援新增至您的組態參數。

以上任何參數宣告中，新增`parameter`屬性區塊，如下列範例所示。

```powershell
[parameter()]
[String]
$ServiceName
```

您可以指定每個引數`parameter`屬性，以控制定義參數的各個層面。 下列範例會使`$ServiceName`**強制**參數。

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

針對`$State`參數，我們想要防止使用者指定一組預先定義以外的值 （例如執行中、 已停止）`ValidationSet*`屬性會防止使用者指定一組預先定義 （例如執行中、 以外的值已停止）。 下列範例會將`ValidationSet`屬性設定為`$State`參數。 因為我們不想要`$State`參數**強制**，我們需要加入它的預設值。

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> 您不需要指定`parameter`屬性使用時`validation`屬性。

您可以深入了解`parameter`和驗證屬性中的[about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md)。

## <a name="fully-parameterized-configuration"></a>完全參數化的設定

我們現在有會強制使用者在指定的參數化的組態`-InstanceName`， `-ServiceName`，並驗證`-State`參數。

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a>另請參閱

- [撰寫 DSC 設定的說明](configHelp.md)
- [動態組態](flow-control-in-configurations.md)
- [使用您的組態中的組態資料](configData.md)
- [個別的設定和環境資料](separatingEnvData.md)
