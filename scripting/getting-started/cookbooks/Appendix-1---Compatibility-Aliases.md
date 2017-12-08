---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "附錄 1 相容性別名"
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: d789139ef80d4208b56e0b2930f04f824a00537d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="appendix-1---compatibility-aliases"></a>附錄 1 - 相容性別名
Windows PowerShell 有幾個轉換別名可讓 UNIX 和 Cmd 使用者在 Windows PowerShell 中使用熟悉的命令名稱。 下表列出最常見的別名、別名對應的 Windows PowerShell 命令以及標準的 Windows PowerShell 別名 (如果有的話)。

您可以在 Windows PowerShell 中使用 Get-Alias Cmdlet，以找到任何別名對應的 Windows PowerShell 命令。 例如，您可以輸入 **get-alias cls**。

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|CMD 命令|UNIX 命令|PS 命令|PS 別名|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**clear**|**Clear-Host** (函式)|**cls**|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Push-Location**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|

