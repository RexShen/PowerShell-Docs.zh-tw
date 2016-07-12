---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "JEA 上的報告"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: d867a6462e9fa8b6e16c8c2103899c72b380116c

---

# JEA 上的報告
因為 JEA 允許非特殊權限使用者在特殊權限內容中執行，所以記錄和稽核格外重要。
在本節中，我們將執行您可以用來協助記錄和報告的所有工具。

## 報告 JEA 動作
### 潛在文字記錄
摘要說明 PowerShell 工作階段狀況的其中一個最快速方法是回顧人員輸入的內容。
您會看到其命令及這些命令的輸出安然無恙。
即使發生問題，至少您知道。
PowerShell 文字記錄的設計是為了讓您有與事實類似的檢視。

使用工作階段設定中的 "TranscriptDirectory" 欄位時，PowerShell 會自動記錄在指定工作階段中執行之所有動作的文字記錄。
您可以在下列位置，找到本文工作階段的文字記錄："$env:ProgramData\JEAConfiguration\Transcripts"

如您所見，文字記錄會記錄「已連線」的使用者、「執行身分」使用者、在工作階段中執行之命令等相關資訊。
如需 PowerShell 文字記錄的詳細資訊，請參閱這篇[部落格文章](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)。

### PowerShell 事件記錄檔
當您開啟模組記錄時，所有 PowerShell 動作也會記錄在一般 Windows 事件記錄檔中。
這比處理文字記錄稍微複雜，但提供給您的詳細程度會很實用。

在 "PowerShell" 作業記錄中，如果您已啟用模組記錄，事件識別碼 4104 會記錄所叫用的每個命令。

### 其他事件記錄檔
不同於 PowerShell 記錄檔和文字記錄，其他記錄機制不會擷取「已連線的使用者」。
您必須在其他記錄檔與 PowerShell 記錄檔之間進行一些相互關聯，以對應到所執行的動作。

在「Windows 遠端管理」作業記錄中，事件識別碼 193 會記錄連線使用者的 SID 和名稱，以及 RunAs 虛擬帳戶的 SID，以便協助此相互關聯。
您可能也注意到 RunAs 虛擬帳戶的名稱結尾包含連線使用者的網域和使用者名稱。

## 報告 JEA 設定
### Get-PSSessionConfiguration
為了精確地報告環境的狀態，請務必了解您在電腦上設定的 JEA 端點數目。
`Get-PSSessionConfiguration` 便能執行此作業。

### Get-PSSessionCapability
透過 JEA 端點手動報告任何指定使用者的功能可能相當複雜。
您可能必須檢查幾個角色功能。
所幸 "Get-PSSessionCapability" Cmdlet 可執行此作業。

若要對此進行測試，請從系統管理員的 PowerShell 命令提示字元執行下列命令：
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```




<!--HONumber=Jul16_HO1-->


