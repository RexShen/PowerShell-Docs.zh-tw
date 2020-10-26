---
ms.date: 08/03/2020
keywords: powershell,cmdlet
title: 附錄 1 相容性別名
description: PowerShell 有數個別名，可讓 UNIX 和 cmd.exe 使用者使用熟悉的命令。
ms.openlocfilehash: 8cbbd5a358de9018fcb5c840e711cd76f7a9a353
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500737"
---
# <a name="appendix-1---compatibility-aliases"></a>附錄 1 - 相容性別名

PowerShell 有數個別名，可讓 **UNIX** 和 **cmd.exe** 使用者使用熟悉的命令。
下表顯示命令及其相關的 PowerShell Cmdlet 和 PowerShell 別名：

|            cmd.exe 命令            | UNIX 命令 | PowerShell Cmdlet | PowerShell 別名 |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| **cd** 、 **chdir**                     | **cd**       | `Set-Location`    | `sl`             |
| **cls**                               | **清除**    | `Clear-Host`      | `cls`            |
| **copy**                              | **cp**       | `Copy-Item`       | `cpi`            |
| **del** 、 **erase** 、 **rd** 、 **rmdir** | **rm**       | `Remove-Item`     | `ri`             |
| **dir**                               | **ls**       | `Get-ChildItem`   | `gci`            |
| **echo**                              | **echo**     | `Write-Output`    | `write`          |
| **md**                                | **mkdir**    | `New-Item`        | `ni`             |
| **move**                              | **mv**       | `Move-Item`       | `mi`             |
| **popd**                              | **popd**     | `Pop-Location`    | `popd`           |
| **pushd**                             | **pushd**    | `Push-Location`   | `pushd`          |
| **ren**                               | **mv**       | `Rename-Item`     | `rni`            |
| **type**                              | **cat**      | `Get-Content`     | `gc`             |

若要尋找 PowerShell 別名，請使用 [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) Cmdlet。 若要顯示 Cmdlet 的別名，請使用 **Definition** 參數並指定 Cmdlet 名稱。
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
