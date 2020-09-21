---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC Script 資源
ms.openlocfilehash: 9b89981c17e87b3681c6416c7dee44a75c432ea1
ms.sourcegitcommit: eb6a7c01e6385809656ac828b9211683e0b1a6fe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "89041124"
---
# <a name="dsc-script-resource"></a>DSC Script 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的 `Script` 資源提供了在目標節點執行 Windows PowerShell 指令碼區塊的機制。 `Script` 資源會使用 `GetScript`
`SetScript` 和 `TestScript` 屬性，其包含定義來執行對應 DSC 狀態作業的指令碼區塊。

## <a name="syntax"></a>語法

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> `GetScript`、`TestScript` 和 `SetScript` 區塊會儲存為字串。

## <a name="properties"></a>屬性

|  屬性  |                                          描述                                          |
| ---------- | --------------------------------------------------------------------------------------------- |
| GetScript  | 指令碼區塊，會傳回節點的目前狀態。                                    |
| SetScript  | 指令碼區塊，DSC 會在節點未處於預期狀態時，用來強制執行合規性。 |
| TestScript | 指令碼區塊，可判斷節點是否處於預期狀態。                           |
| 認證 | 如果需要認證，表示執行這個指令碼所要使用的認證。        |

## <a name="common-properties"></a>通用屬性

|       屬性       |                                            描述                                            |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| DependsOn            | 表示必須先執行另一個資源的設定，再設定這個資源。 |
| PsDscRunAsCredential | 設定用於執行整個資源的認證。                                           |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

### <a name="additional-information"></a>其他資訊

#### <a name="getscript"></a>GetScript

DSC 不會使用 `GetScript` 的輸出。[Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) Cmdlet 會執行 `GetScript` 以擷取節點目前的狀態。 不需要來自 `GetScript` 的傳回值。如果指定傳回值，則必須是 **Result** 機碼的雜湊表，其中所包含的值為字串。

#### <a name="testscript"></a>TestScript

`TestScript` 會透過 DSC 執行，以判斷是否應該執行 `SetScript`。 如果 `TestScript` 傳回 `$false`，DSC 就會執行 `SetScript`，以讓節點回到預期狀態。 它必須傳回布林值。 `$true` 的結果指出節點符合規範，而且 `SetScript` 應該不會執行。

[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) Cmdlet 會執行 `TestScript` 以利用 `Script` 資源來擷取節點合規性。 不過，在此情況下，無論 `TestScript` 區塊傳回什麼，`SetScript` 都不會執行。

> [!NOTE]
> 來自您 `TestScript` 的所有輸出都是其傳回值的一部分。 PowerShell 會將非隱藏的輸出解譯為非零值，這表示不論節點的狀態為何，您的 `TestScript` 都將傳回 `$true`。 這會產生無法預期的結果、誤判，並導致疑難排解期間出現問題。

#### <a name="setscript"></a>SetScript

`SetScript` 會修改節點以強制進入預期狀態。 如果 `TestScript` 指令碼區塊傳回 `$false`，則會由 DSC 加以呼叫。 `SetScript` 應該不會傳回值。

## <a name="examples"></a>範例

### <a name="example-1-write-sample-text-using-a-script-resource"></a>範例 1：使用指令碼資源撰寫範例文字

此範例會在每個節點上測試 `C:\TempFolder\TestFile.txt` 是否存在。 如果不存在，就會使用 `SetScript` 建立它。 `GetScript` 會傳回檔案的內容，而且不會使用它的傳回值。

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a>範例 2：使用指令碼資源比較版本資訊

此範例會從撰寫電腦上的文字檔擷取「符合規範」的版本資訊，並將它儲存在 `$version` 變數中。 產生節點的 MOF 檔案時，DSC 會使用 `$version` 變數的值，來取代每個指令碼區塊中的 `$using:version` 變數。
執行期間，「符合規範」的版本會儲存在每個節點的文字檔中，並與後續執行進行比較及更新。

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state.Result -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state.Result,$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```

### <a name="example-3-utilizing-parameters-in-a-script-resource"></a>範例 3：利用指令碼資源中的參數

此範例使用 `using` 範圍，存取指令碼資源中的參數。
請注意，您可以使用類似方式存取 **ConfigurationData**。 一如範例 2，版本會儲存在目標節點的本機檔案中。 然而，因為本機檔案路徑與版本均可設定，所以會將程式碼與設定資料分離。

```powershell
Configuration ScriptTest
{
    param
    (
        [Version]
        $Version,

        [string]
        $FilePath
    )

    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content -Path $using:FilePath
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:Version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }

                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                Set-Content -Path $using:FilePath -Value $using:Version
            }
        }
    }
}
```

產生的 MOF 檔案包含透過 `using` 範圍存取的變數及其值。
這些檔案會插入每個使用變數的 ScriptBlock。 因簡要考量，已移除 Test 與 Set 指令碼：

```Output
instance of MSFT_ScriptResource as $MSFT_ScriptResource1ref
{
 GetScript = "$FilePath ='C:\\Config.ini'\n\n $currentVersion = Get-Content -Path $FilePath\n return @{ 'Result' = \"$currentVersion\" }\n";
 TestScript = ...;
 SetScript = ...;
};
```

### <a name="known-limitations"></a>已知限制

- 使用提取或推送伺服器模型時，在指令碼資源內傳遞的認證不一定可靠。 這種情況下，建議使用完整資源，不要使用指令碼資源。
