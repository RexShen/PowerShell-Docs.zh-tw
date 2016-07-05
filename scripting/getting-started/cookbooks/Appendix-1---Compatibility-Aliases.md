---
title: "附錄 1   相容性別名"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 38a6cb1b0402825b307652e6747ea65baafd1d8b

---

# 附錄 1 - 相容性別名
Windows PowerShell 有幾個轉換別名可讓 UNIX 和 Cmd 使用者在 Windows PowerShell 中使用熟悉的命令名稱。 下表列出最常見的別名、別名對應的 Windows PowerShell 命令以及標準的 Windows PowerShell 別名 (如果有的話)。

您可以在 Windows PowerShell 中使用 Get\-Alias Cmdlet，以找到任何別名對應的 Windows PowerShell 命令。 例如，您可以輸入 **get\-alias cls**。

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|CMD 命令|UNIX 命令|PS 命令|PS 別名|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get\-ChildItem**|**gci**|
|**cls**|**clear**|**Clear\-Host** (函數)|N\/A|
|**del, erase, rmdir**|**rm**|**Remove\-Item**|**ri**|
|**copy**|**cp**|**Copy\-Item**|**ci**|
|**move**|**mv**|**Move\-Item**|**mi**|
|**rename**|**mv**|**Rename\-Item**|**rni**|
|**型別**|**cat**|**Get\-Content**|**gc**|
|**cd**|**cd**|**Set\-Location**|**sl**|
|**md**|**mkdir**|**New\-Item**|**ni**|
|N\/A|**pushd**|**Push\-Location**|N\/A|
|N\/A|**popd**|**Pop\-Location**|N\/A|




<!--HONumber=Jun16_HO4-->


