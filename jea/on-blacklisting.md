---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "列入黑名單"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 8892e5e08a763fbc66d782bbc9252d1f3a7dcfcf

---

### 列入黑名單
試用 JEA 之後，您可能想知道它是否可以將命令列入黑名單。
這是合理的要求，但目前不在 JEA 的規劃中，原因如下︰

1.  我們已將 JEA 設計為限制操作員只執行他們所需的動作。
黑名單則相反。

2.  PowerShell 命令作者在設計 PowerShell 命令時並未考慮到 JEA。
在 Windows Server 2016 的全新安裝上，可立即使用的命令約有 1520 個。
這些命令的威脅模式並未納入使用者以提升權限的帳戶身分執行命令的可能性。
例如，特定命令可依設計插入程式碼 (例如核心 PowerShell 模組中的 Add-Type 和 Invoke-Command)。
當您公開我們已知的特定命令時，JEA 可能會警告您，但我們尚未根據新的威脅模式重新評估 Windows 中的所有其他命令。
您必須了解透過 JEA 公開之命令的功能。  

3.  此外，即使 JEA 封鎖了具有程式碼插入弱點的所有命令，也無法保證惡意使用者不會使用其他相關命令來執行列入黑名單的動作。
除非您了解要公開的所有命令，否則您無法保證不會發生特定動作。
不論使用白名單或黑名單，您都有責任了解要公開哪些命令。
您無法管理黑名單會公開的命令數目，因此 JEA 會改用白名單實作。




<!--HONumber=Jul16_HO1-->


