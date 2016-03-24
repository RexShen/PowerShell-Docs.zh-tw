# 指定跨節點相依性

使用內建 WaitFor\* 資源 (WaitForAll、WaitForAny 和 WaitForSome)，您現在可以於設定執行期間在電腦之間指定相依性，而不需要外部協調流程期間。 此行為或每個 WaitFor\* 資源為︰

* **WaitForAll** 等候在 NodeName 屬性中定義的*所有*目標節點轉變為所需的狀態。
* **WaitForAny** 等候在 NodeName 屬性中定義的*任何*目標節點轉變為所需的狀態。
* **WaitForSome** 在 NodeName 屬性中定義的特定數目 (該數目由屬性 NodeCount 所定義) 目標節點上，等候指定的資源轉變為所需的狀態。

這些資源會透過使用 WS-Man 通訊協定的 CIM 連線提供節點對節點同步處理。 藉由使用這些資源，設定可以等候另一部電腦特定的資源狀態變更，再繼續執行它自己的設定。 

例如，在下列設定中，目標節點正在等候 **xADDomain** 資源在 **MyDC** 節點上完成幾次重試，之後目標節點才能加入網域。

```PowerShell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement

    WaitForAll DC
    {
        ResourceName      = '[xADDomain]NewDomain'
        NodeName          = 'MyDC'
        RetryIntervalSec  = 15
        RetryCount        = 30
    }

    xComputer JoinDomain
    {
        Name             = 'MyPC'
        DomainName       = 'Contoso.com'
        Credential       = (get-credential)
        DependsOn        ='[WaitForAll]DC'
    }
}
```
**提示︰** WaitFor\* 資源預設為嘗試一次後失敗，所以雖然並非必要，但您通常會想要指定重試間隔和計數。
<!--HONumber=Mar16_HO2-->
