---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 2d629d98b59c455011f4a5d955ef666218ae2f3f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="test-dscconfiguration-cmdlet-supports-reference-configurations" class="xliff"></a>
# Test-DscConfiguration Cmdlet 支援參考設定

Test-DscConfiguration Cmdlet 已更新，允許進行一個或多個目標節點所需設定狀態的測試 (藉由比較指定的參考設定文件來完成測試)。

下列的新參數集，只在指定的路徑中將 DSC 設定用於測試，並永遠不會將個別設定套用在指定的目標節點上。 就像 Start-DscConfiguration 與其他 DSC Cmdlets 一樣，每個 MOF 的名稱將用於判斷在哪個目標節點上測試設定。 

```PowerShell
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

```PowerShell
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

