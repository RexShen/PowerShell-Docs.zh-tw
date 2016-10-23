---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "powershell,cmdlet,組件庫"
ms.date: 2016-10-14
contributor: manikb
title: scriptwithpseditionsupport
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 46efb494303c4cb691d5b58791a156dcc5bc99b9

---

# 具有相容 PowerShell 版本的指令碼
從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。

- **Desktop Edition︰**建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行之 PowerShell 版本的指令碼和模組相容。
- **Core Edition︰**建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行之 PowerShell 版本的指令碼和模組相容。

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

除非在 #requires 陳述式上使用 PSEdition 參數的相容 PowerShell 版本上執行指令碼，否則指令碼作者可能會防止執行指令碼。
```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell Core edition. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

PowerShell Gallery 使用者可以尋找特定 PowerShell 版本上所支援的指令碼清單。
沒有 PSEdition_Desktop 和 PSEditon_Core 的指令碼可以在 PowerShell Desktop 版本上運作良好。

```powershell

# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEditon_Desktop

# Find scripts supported on PowerShell Core editions
Find-Script -Tag PSEditon_Core

```

## 更多詳細資料
### [PSEditions 的模組](../module/modulewithpseditionsupport.md)
### [PowerShellGallery 的 PSEditions 支援](../../psgallery/psgallery_pseditions.md)




<!--HONumber=Oct16_HO2-->


