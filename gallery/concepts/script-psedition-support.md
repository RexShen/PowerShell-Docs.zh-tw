---
ms.date: 06/12/2017
contributor: manikb
keywords: 資源庫,powershell,cmdlet,psget
title: 具備相容 PowerShell 版本的指令碼
ms.openlocfilehash: e364879f611429a8583e550fb7704431e456fbb1
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655271"
---
# <a name="script-with-compatible-powershell-editions"></a>具備相容 PowerShell 版本的指令碼

從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。

- Desktop Edition在.NET Framework 上建置，並提供與指令碼和模組在完整使用量的 Server Core 等的 Windows 和 Windows 桌面版本上執行的 PowerShell 版本的相容性。

- **Core Edition:** 建置在.NET Core，並提供與指令碼和模組的縮減版 Nano Server 等的 Windows 和 Windows IoT 上執行的 PowerShell 版本相容性。

$PSVersionTable PSEdition 屬性會顯示正在執行的 PowerShell 版本。

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

指令碼作者可在 `#requires` 陳述式上使用 PSEdition 參數，只允許指令碼在相容的 PowerShell 版本上執行。

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

PowerShell Gallery 使用者可以尋找特定 PowerShell 版本上所支援的指令碼清單。
沒有 PSEdition_Desktop 與 PSEdition_Core 標記的指令碼會被視為可在 PowerShell Desktop 版本上正常運作。

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a>更多詳細資料

- [PSEditions 的模組](module-psedition-support.md)
- [PowerShellGallery 的 PSEditions 支援](../how-to/finding-packages/searching-by-compatibility.md)
