---
ms.date: 09/09/2019
keywords: powershell,cmdlet
title: 附錄 1 相容性別名
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "70848175"
---
# <a name="appendix-1---compatibility-aliases"></a>附錄 1 - 相容性別名

PowerShell 有數個別名，可讓 **UNIX** 和 **cmd.exe** 使用者使用熟悉的命令。
下表顯示命令及其相關的 PowerShell Cmdlet 和 PowerShell 別名：

|cmd.exe 命令|UNIX 命令|PowerShell Cmdlet|PowerShell 別名|
|---------------|----------------|--------------|------------|
|**cls**|**清除**|`Clear-Host` (函式)|`cls`|
|**copy**|**cp**|`Copy-Item`|`cpi`|
|**dir**|**ls**|`Get-ChildItem`|`gci`|
|**type**|**cat**|`Get-Content`|`gc`|
|**move**|**mv**|`Move-Item`|`mi`|
|**md**|**mkdir**|`New-Item`|`ni`|
|**pushd**|**pushd**|`Push-Location`|`pushd`|
|**popd**|**popd**|`Pop-Location`|`popd`|
|**del**、**erase**、**rd**、**rmdir**|**rm**|`Remove-Item`|`ri`|
|**ren**|**mv**|`Rename-Item`|`rni`|
|**cd**、**chdir**|**cd**|`Set-Location`|`sl`|

若要尋找 PowerShell 別名，請使用 [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) Cmdlet。 若要顯示 Cmdlet 的別名，請使用 **Definition** 參數並指定 Cmdlet 名稱。
或者，若要尋找別名的 Cmdlet 名稱，請使用 **Name** 參數並指定別名。

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
