---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxScript 資源
ms.openlocfilehash: a7f2114aba47bb581cdd19168e784b79dfc5b6ad
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953185"
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC for Linux nxScript 資源

PowerShell 預期狀態設定 (DSC) 的 **nxScript** 資源會提供一個機制，在 Linux 節點上執行 Linux 指令碼。

## <a name="syntax"></a>語法

```Syntax
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|GetScript |提供指令碼以傳回機器目前狀態。 當您叫用 [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) \(英文\) 指令碼時，此指令碼會執行。 指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 `#!/bin/bash`。 |
|SetScript |提供讓機器處於正確狀態的指令碼。 當您叫用 [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) \(英文\) 指令碼時，**TestScript** 會先執行。 如果 **TestScript** 區塊傳回的結束代碼不是 0，則 **SetScript** 區塊將會執行。 如果 **TestScript** 傳回的結束代碼是 0，則 **SetScript** 區塊將不會執行。 指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 `#!/bin/bash`。 |
|TestScript |提供評估節點目前是否處於正確狀態的指令碼。 當您叫用 [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) \(英文\) 指令碼時，此指令碼會執行。 如果傳回的結束代碼不是 0，則 **SetScript** 將會執行。 如果傳回的結束代碼是 0，則 **SetScript** 將不會執行。 當您叫用 [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) \(英文\) 指令碼時，**TestScript** 也會執行。 不過，在此情況下，無論從 **TestScript** 傳回何種結束碼，**SetScript** 都不會執行。 如果實際設定符合目前的預期狀態設定，則 **TestScript** 必須包含內容且傳回的結束代碼必須為 0，如果不符合，則結束碼不是 0。 目前的預期狀態設定，是上次使用 DSC 之節點上施行的設定。 指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 `#!/bin/bash`。 |
|User |要執行指令碼的使用者。 |
|群組 |要執行指令碼的群組。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |

## <a name="example"></a>範例

下列範例示範如何使用 **nxScript** 資源來執行其他設定管理。

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxScript KeepDirEmpty {

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
