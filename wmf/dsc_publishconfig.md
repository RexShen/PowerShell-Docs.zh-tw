# 傳遞設定文件，但不套用它

**Publish-DscConfiguration** Cmdlet 將設定 MOF 檔案複製到目標節點，但不會套用此設定。 此設定會在下個一致性階段中套用，或當您執行 `Update-DscConfiguration` Cmdlet 時套用。

```powershell
Publish-DscConfiguration [-Path] <string> [[-ComputerName] <string[]>] [-Force] [-Credential <pscredential>] [-ThrottleLimit <int>] [-WhatIf] [-Confirm] [<CommonParameters>]

Publish-DscConfiguration [-Path] <string> -CimSession <CimSession[]> [-Force] [-ThrottleLimit <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<!--HONumber=Mar16_HO2-->
