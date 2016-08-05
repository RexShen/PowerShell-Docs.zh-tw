---
title: "WMF 5.1 版本資訊 (預覽)"
ms.date: 2016-07-27
keywords: "PowerShell、DSC、WMF"
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 5eb9eae6257cdb57f4f778b5dddf5aa7ef9d10bb
ms.openlocfilehash: 12f2c084ab92134b733ee037c3d9fbd512af2e4c

---

# Windows Management Framework (WMF) 5.1 Preview 版本資訊 #

WMF 5.1 Preview 包含已搭配 Windows Server 2016 發行的 PowerShell、WMI、WinRM，以及軟體清查和授權 (SIL) 元件。 WMF 5.1 可以在 Windows 7、Windows 8.1、Windows Server 2008 R2、2012 及 2012 R2 上安裝，並提供許多對 WMF 5.0 RTM 的改善，包括︰

- 新的 Cmdlet︰本機使用者和群組；Get-ComputerInfo
- PowerShellGet 改善功能包括強制執行已簽署的模組，以及安裝 JEA 模組
- PackageManagement 新增對容器、CBS 安裝、以執行檔為基礎的安裝、封包封裝的支援
- DSC 和 PowerShell 類別的偵錯改善
- 安全性增強功能包括強制執行來自提取伺服器的目錄簽署模組，以及在使用 PowerShellGet Cmdlet 時加以強制執行
- 回應數個使用者要求和問題

**重要事項：**

- **WMF 5.1 Preview 需要 Windows Management Framework 4.6**。 安裝會成功，但若未安裝 .Net 4.6，主要功能將會失敗。 您可在[安裝和設定 WMF 5.1 (Preview)](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) 主題中取得指示。 
- 此次**不支援將 WMF 5.1 Preview 用於生產環境**部署。 其旨在提供版本相關功能的早期資訊，並讓您得以將意見反應提供給 PowerShell 小組。
- WMF 5.1 Preview 可直接透過 WMF 5.0 安裝。
- 目前在 Windows 7 及 Windows Server 2008 上安裝 WMF 5.1 Preview 時需要 WMF 4.0 為已知問題。 預計在最終發行版本前移除這項需求。
- 安裝包括 RTM 版本在內的 WMF 5.1 未來版本時，即需要將 WMF 5.1 Preview 解除安裝。



<!--HONumber=Jul16_HO5-->


