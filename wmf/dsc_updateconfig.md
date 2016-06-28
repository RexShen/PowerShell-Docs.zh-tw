# DSC 設定的依需求 PULL

新的 Update-DscConfiguration Cmdlet 觸發在中繼設定中定義的提取伺服器提取。 此行為通常稱為「現在提取」。 


一旦觸發，提取行為會和在一般的頻率期間觸發時完全相同︰

1. 目前設定的總和檢查碼會和在提取伺服器上設定的總和檢查碼比較。 
2. 如果兩者相同，它不套用設定就能順利完成。 
3. 如果兩者不同，就會從提取伺服器提取設定，並將其套用。

**注意︰** 如果中繼設定 RefreshMode = 'Push' 時，此 Cmdlet 會傳回錯誤，因此目標節點處在 'Push' 模式時此 Cmdlet 一律不會執行任何動作。

```PowerShell
Update-DscConfiguration     [[-ComputerName] <string[]>] 
                            [-Wait]
                            [-Force] 
                            [-JobName <string>] 
                            [-Credential<pscredential>] 
                            [-ThrottleLimit <int>] 
                            [-WhatIf] 
                            [-Confirm] 
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]> 
                            [-Wait] 
                            [-Force] 
                            [-JobName <string>] 
                            [-ThrottleLimit <int>]
                            [-WhatIf] 
                            [-Confirm] 
                            [<CommonParameters>]
```

<!--HONumber=Jun16_HO4-->


