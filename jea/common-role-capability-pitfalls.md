---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "常見的角色功能問題"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 0e221c840f083ce0b8ecbcbb34c184bcdbc0c73e

---

### 常見的角色功能問題
當您自行執行此處理程序時，可能會遇到一些常見的問題。
下列快速指南說明如何在修改及建立新端點時，找出並修正這些問題︰

#### 函式與Cmdlet
以 PowerShell 撰寫的 PowerShell 命令是 PowerShell 函式。
撰寫為特定 .NET 類別的 PowerShell 命令是 PowerShell Cmdlet。
您可以執行 `Get-Command` 來查看命令類型。

#### VisibleProviders
您必須公開命令所需的任何提供者。
最常見的是檔案系統提供者，但您可能也需要公開其他提供者，像是登錄提供者。
如需提供者簡介，請參閱這篇 [Hey, Scripting Guy 部落格文章](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx)。
公開提供者時請小心，通常最好是定義自己的函式來搭配基礎提供者使用，而不是直接公開 JEA 工作階段中的提供者。
如此一來，您仍然可以允許使用者使用檔案、登錄機碼等，但會保留使用者可以使用自訂驗證邏輯處理**哪些**檔案和登錄機碼的控制權。




<!--HONumber=Jun16_HO4-->


