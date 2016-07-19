---
title: "DSC for Linux nxScript 資源"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 4c575bbf0e0553e19e56bcc6edd605e36586cb94

---

# DSC for Linux nxScript 資源

PowerShell 預期狀態設定 (DSC) 的 **nxScript** 資源會提供一個機制，在 Linux 節點上執行 Linux 指令碼。

## 語法

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    { Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## [內容]

|  屬性 |  描述 | 
|---|---|
| GetScript| 提供當您叫用 [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) Cmdlet 時所執行的指令碼。 指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 #!/bin/bash。| 
| SetScript| 提供指令碼。 當您叫用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 時，**TestScript** 會先執行。 如果 **TestScript** 區塊傳回的結束代碼不是 0，則 **SetScript** 區塊將會執行。 如果 **TestScript** 傳回的結束代碼是 0，則 **SetScript** 區塊將不會執行。 指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 `#!/bin/bash`。| 
| TestScript| 提供指令碼。 當您叫用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 時，這個指令碼會先執行。 如果傳回的結束代碼不是 0，則 SetScript 將會執行。 如果傳回的結束代碼是 0，則 **SetScript** 將不會執行。 **TestScript** 也會在叫用 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) Cmdlet 時執行。 不過，在此情況下，無論從 **TestScript** 傳回何種結束碼，**SetScript** 都不會執行。 如果實際的設定符合目前的預期狀態設定，則 **TestScript** 傳回的結束代碼必須為 0，如果不符合，則結束碼不是 0。 (目前的預期狀態設定是上次使用 DSC 的節點上制定的設定)。 指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 1#!/bin/bash.1。| 
| 使用者| 要執行指令碼的使用者。| 
| 群組| 要執行指令碼的群組。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的**識別碼**是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 

## 範例

下列範例示範如何使用 **nxScript** 資源來執行其他設定管理。

```
Import-DSCResource -Module nx 

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
} 
}
```




<!--HONumber=Jun16_HO4-->


