---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 4008a7f91af41150f26c4147135b30aa8835281c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058738"
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>Test-DscConfiguration Cmdlet 支援參考設定

Test-DscConfiguration Cmdlet 已更新，允許進行一個或多個目標節點所需設定狀態的測試 (藉由比較指定的參考設定文件來完成測試)。

下列的新參數集，只在指定的路徑中將 DSC 設定用於測試，並永遠不會將個別設定套用在指定的目標節點上。 就像 Start-DscConfiguration 與其他 DSC Cmdlets 一樣，每個 MOF 的名稱將用於判斷在哪個目標節點上測試設定。

```powershell
Test-DscConfiguration   [-Path] <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```

下列新的參數集只將單一 DSC 設定用於測試，且永遠不會將設定套用在指定的目標節點上。

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```
