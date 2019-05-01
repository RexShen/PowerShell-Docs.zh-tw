---
ms.date: 12/12/2018
keywords: dsc, powershell, 資源, 資源庫, 設定
title: 將參數新增至設定
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080249"
---
# <a name="add-parameters-to-a-configuration"></a>將參數新增至設定

就像函式一樣，您可以將[設定](configurations.md)參數化，根據使用者輸入來進行更動態的設定。 步驟類似於[使用參數的函式](/powershell/module/microsoft.powershell.core/about/about_functions)中所描述。

此範例從基本的 Configuration 開始，其將 "Spooler" 服務設定為 "Running"。

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

## <a name="built-in-configuration-parameters"></a>內建 Configuration 參數

與函式不同，[CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) 屬性不會新增任何功能。 除了[一般參數](/powershell/module/microsoft.powershell.core/about/about_commonparameters)之外，Configuration 也能夠使用下列內建參數，您不需要定義它們。

|參數  |描述  |
|---------|---------|
|`-InstanceName`|用於定義[複合設定](compositeconfigs.md)|
|`-DependsOn`|用於定義[複合設定](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|用於定義[複合設定](compositeconfigs.md)|
|`-ConfigurationData`|用於傳遞在 Configuration 中使用的結構化[設定資料](configData.md)。|
|`-OutputPath`|用於指定將要編譯的 "\<computername\>.mof" 檔案位置|

## <a name="adding-your-own-parameters-to-configurations"></a>將自己的參數加入 Configuration

除了內建參數之外，您還可以將自己的參數加入到 Configuration。 參數區塊直接位於 Configuration 宣告內，就和 Function 一樣。 Configuration 的參數區塊應該在任何的 **Node** 宣告之外，並且位於任何 *import* 陳述式上方。 您可藉由加入參數讓自己的 Configuration 更穩定且具動態性。

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>加入 ComputerName 參數

您可以加入的第一個參數是 `-Computername` 參數，如此您就能夠以動態方式針對任何傳遞到設定中的 `-Computername` 編譯 ".mof" 檔案。 和函式一樣，您也可以定義預設值，以防使用者並未傳入 `-ComputerName` 的值

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

在您的設定中，您之後可以在定義 Node 區塊時指定自己的 `-ComputerName` 參數。

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>使用參數呼叫 Configuration

在將參數加入到 Configuration 之後，您就可以像使用 Cmdlet般使用它們。

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>編譯多個.mof 檔案

Node 區塊也可接受以逗號分隔的電腦名稱清單，並且會為每個電腦名稱產生 ".mof" 檔案。 您可以執行下列範例，來為傳遞至 `-ComputerName` 參數的所有電腦產生 ".mof" 檔案。

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

## <a name="advanced-parameters-in-configurations"></a>Configuration 中的進階參數

除了 `-ComputerName` 參數以外，我們還可以加入服務名稱和狀態的參數。 下列範例區塊會加入具有 `-ServiceName` 參數的參數區塊，並使用它以動態方式定義 **Service** 資源區塊。 還會加入 `-State` 參數以動態方式定義 **Service** 資源區塊中的 **State**。

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
> 在更進一步的範例中，將您的動態資料移至結構化的[設定資料中](configData.md)可能較為合理。

範例 Configuration 現在會採用動態的 `$ServiceName`，但若它並未被指定，編譯結果會產生錯誤。 您可以如這個範例般加入預設值。

```powershell
[String]
$ServiceName="Spooler"
```

在本範例中，直接強制使用者指定 `$ServiceName` 參數的值比較合理。 `parameter` 屬性可讓您將更增進一步的驗證和管線支援加入到 Configuration 的參數。

在以上任何的參數宣告中加入 `parameter` 屬性區塊，如下列範例所示。

```powershell
[parameter()]
[String]
$ServiceName
```

您可以將引數指定到每個 `parameter` 屬性，來控制所定義之參數的各層面。 下列範例會使 `$ServiceName` 成為**強制**參數。

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

對於 `$State` 參數，我們想防止使用者指定預先定義值組 (例如 Running、Stopped) 以外的值，而 `ValidationSet*` 屬性將可防止使用者指定預先定義值組 (例如 Running、Stopped) 以外的值。 下列範例會將 `ValidationSet` 屬性加入 `$State` 參數。 由於我們不想讓 `$State` 參數成為**強制**參數，我們必須為它加入預設值。

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> 當使用 `validation` 屬性時，您不需要指定 `parameter` 屬性。

您可以在 [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md) 中深入了解 `parameter` 和 validation 屬性。

## <a name="fully-parameterized-configuration"></a>完全參數化的 Configuration

我們現在有參數化的 Configuration，可強制使用者指定 `-InstanceName`、`-ServiceName`，並驗證 `-State` 參數。

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
- [動態設定](flow-control-in-configurations.md)
- [在設定中使用設定資料](configData.md)
- [分離設定與環境資料](separatingEnvData.md)
