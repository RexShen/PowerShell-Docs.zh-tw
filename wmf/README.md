---
title: Windows Management Framework (WMF)
ms.date: 2016-05-16
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: eacd33d2a0a92977a3990132e23eef9871a7f0dc
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) 是一種傳遞機制，可在各式各樣的 Windows 和 Windows Server 中提供一致的管理介面。
安裝 WMF 後，客戶即可順暢自如地在其混合了各種作業系統的環境中操作。
WMF 會更新指定 Windows 和 Windows Server 版本的管理功能，於安裝較低版本的 Windows 和 Windows Server (一般是低 2 個版本) 時提供。

WMF 安裝新增及 (或) 更新下列功能︰

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
- Windows PowerShell 整合式指令碼環境 (ISE)
- Windows 遠端管理 (WinRM)
- Windows Management Instrumentation (WMI)
- Windows PowerShell Web 服務 (Management OData IIS 擴充功能)
- 軟體清查記錄 (SIL)
- 伺服器管理員 CIM 提供者

## <a name="wmf-release-notes"></a>WMF 版本資訊
如需深入了解 PowerShell 的各種增強功能以及指定 WMF 的其他元件，請參閱下列版本資訊連結︰


- [WMF 5.1 (預覽)](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)


## <a name="wmf-availability-across-windows-operating-systems"></a>各 Windows 作業系統的 WMF 可用性

>TODO︰將連結新增至欄標題的特定 WMF DLC

| 作業系統版本 | [WMF 5.1 預覽*]() | [WMF 5.0]() | [WMF 4.0]() |  [WMF 3.0]() | [WMF (2.0)]() |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | 隨產品附贈* | 隨產品附贈* |  |  |  |
| Windows 10 | 隨產品附贈* | 隨產品附贈*  | | | |  
| Windows Server 2012 R2| ?? | 是 | 隨產品附贈 |  |  |
| Windows 8.1 | ?? | 是 |  隨產品附贈 |  |  |
| Windows Server 2012 | ?? | 是 | 是 |  隨產品附贈 | |
| Windows 8 |  |  |  | 隨產品附贈 | |
| Windows Server 2008 R2 SP1 | ?? | 是 | 是 |  是| 隨產品附贈 |
| Windows 7 SP1  | ?? | 是 | 是 | 是 | 隨產品附贈 |
| Windows Server 2008 SP2 | | | | 是 | 是 |
| Windows Vista | | | | | 是 |
| Windows Server 2003| | | |  | 是 |
| Windows XP | | | |  | 是 |

>TODO︰說明上表中的 *
