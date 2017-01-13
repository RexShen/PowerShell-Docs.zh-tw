---
title: "WMF 5.1 版本資訊"
ms.date: 2016-07-27
keywords: "PowerShell、DSC、WMF"
description: 
ms.topic: article
author: jkeithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 0a499bbfd2517c1f44e41f1096cda0c23b1c3df8
ms.sourcegitcommit: f06ef671c0a646bdd277634da89cc11bc2a78a41
translationtype: HT
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Windows Management Framework (WMF) 5.1 版本資訊 #

WMF 5.1 包含已搭配 Windows Server 2016 發行的 PowerShell、WMI、WinRM，以及軟體清查和授權 (SIL) 元件。 WMF 5.1 可以在 Windows 7、Windows 8.1、Windows Server 2008 R2、2012 及 2012 R2 上安裝，並提供許多對 WMF 5.0 RTM 的改善，包括︰

- 新的 Cmdlet︰本機使用者和群組；Get-ComputerInfo
- PowerShellGet 改善功能包括強制執行已簽署的模組，以及安裝 JEA 模組
- PackageManagement 新增對容器、CBS 安裝、以執行檔為基礎的安裝、封包封裝的支援
- DSC 和 PowerShell 類別的偵錯改善
- 安全性增強功能包括強制執行來自提取伺服器的目錄簽署模組，以及在使用 PowerShellGet Cmdlet 時加以強制執行
- 回應數個使用者要求和問題

**重要事項：**

- **WMF 5.1 需要 .NET Framework 4.6**。 安裝會成功，但若未安裝 .NET 4.6，主要功能將會失敗。 您可在[安裝和設定 WMF 5.1](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) 主題中取得指示。 
- 安裝 WMF 5.1 RTM 之前，必須先解除安裝 WMF 5.1 Preview。
- WMF 5.1 可直接透過 WMF 5.0 或 WMF 4.0 安裝。
- 在 Windows 7 和 Windows Server 2008 R2 上安裝 WMF 5.1 之前，__不需要__先安裝 WMF 4.0。 WMF 5.1 Preview 版本有問題，並且已解決。  


