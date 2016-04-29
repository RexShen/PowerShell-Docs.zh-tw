# 指定跨節點相依性

使用內建 WaitFor\* 資源 (WaitForAll、WaitForAny 和 WaitForSome)，您現在可以於設定執行期間在電腦之間指定相依性，而不需要外部協調流程期間。 此行為或每個 WaitFor\* 資源為︰

* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAll</ctype="x-NOTFOUND"> 在 NodeName 屬性中定義的<ctype="x-NOTFOUND" mdpre="*" mdpost="*">所有</ctype="x-NOTFOUND">目標節點上，等候指定的資源轉變為預期狀態。
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAny</ctype="x-NOTFOUND"> 在 NodeName 屬性中定義的<ctype="x-NOTFOUND" mdpre="*" mdpost="*">任何</ctype="x-NOTFOUND">目標節點上，等候指定的資源轉變為預期狀態。
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForSome</ctype="x-NOTFOUND"> 在 NodeName 屬性中定義的特定數目 (該數目由屬性 NodeCount 所定義) 目標節點上，等候指定的資源轉變為預期狀態。

這些資源會透過使用 WS-Man 通訊協定的 CIM 連線提供節點對節點同步處理。 藉由使用這些資源，設定可以等候另一部電腦特定的資源狀態變更，再繼續執行它自己的設定。 

例如，在下列設定中，目標節點正在等候 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">xADDomain</ctype="x-NOTFOUND"> 資源在 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">MyDC</ctype="x-NOTFOUND"> 節點上完成幾次重試，之後目標節點才能加入網域。

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
<ctype="x-NOTFOUND" mdpre="**" mdpost="**">提示︰</ctype="x-NOTFOUND">WaitFor\* 資源預設為嘗試一次後失敗，所以雖然並非必要，但您通常會想要指定重試間隔和計數。


<!--HONumber=Mar16_HO3-->


