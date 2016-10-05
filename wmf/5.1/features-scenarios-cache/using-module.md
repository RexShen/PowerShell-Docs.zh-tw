---
title: "'using module' 的 FullyQuilifiedModuleName"
author: jaimeo
contributor: vors
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: e09cfe0994ac523fd10658955731a93b6c176c88

---

'using module' 的 FullyQuilifiedModuleName
=========================

`using module` 與 PowerShell 中其他模組相關的語法結構表現一致。

WMF 5.0 問題
----------

* 使用者無法在 `using module` 中指定模組版本。
* 系統上如果有多個模組版本，使用者會收到錯誤。

WMF 5.1
----------

* 使用者可以使用 `ModuleSpecification` [雜湊表](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx)。 此雜湊表的格式同於 `Get-Module -FullyQualifiedName`

**範例：** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* 如果有多個模組版本，PowerShell 會使用與 `Import-Module` **相同的解析邏輯**，不會結束。

* 這會讓 `using module` 支持 `Import-Module` 和 `Import-DscResource`。



<!--HONumber=Aug16_HO3-->


