---
ms.date: 04/19/2019
keywords: wmf,powershell,設定
title: Windows Management Framework (WMF)
description: WMF 是 Windows PowerShell 的一個必要條件。 此文章說明 WMF 版本的歷程，並提供如何尋找及安裝 WMF 的相關資訊。
ms.openlocfilehash: 339b140325befea0b28aa470d4249170937f2c37
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654046"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) 提供 Windows 的一致管理介面。 WMF 提供一種順暢的方式，來管理各種 Windows 用戶端和 Windows Server 版本。 WMF 安裝程式套件包含管理功能的更新，而且可用於舊版 Windows。

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

- [WMF 5.1](whats-new/release-notes.md#wmf-51-changes)
- [WMF 5.0](whats-new/release-notes.md#wmf-50-changes)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>各 Windows 作業系統的 WMF 可用性

|        作業系統版本         | [WMF 5.1][]  | WMF 5.0<br>*支援終止* | [WMF 4.0][]  | [WMF 3.0][]  | [WMF 2.0][]  |
| --------------------------------------- | ------------ | --------------------------- | ------------ | ------------ | ------------ |
| Windows Server 2019                     | 隨產品附贈 |                             |              |              |              |
| Windows Server 2016                     | 隨產品附贈 |                             |              |              |              |
| Windows 10                              | 隨產品附贈 | 隨產品附贈                |              |              |              |
| Windows Server 2012 R2                  | 是          | 是                         | 隨產品附贈 |              |              |
| Windows 8.1                             | 是          | 是                         | 隨產品附贈 |              |              |
| Windows Server 2012                     | 是          | 是                         | 是          | 隨產品附贈 |              |
| Windows 8<br>*支援終止*           |              |                             |              | 隨產品附贈 |              |
| Windows Server 2008 R2 SP1              | 是          | 是                         | 是          | 是          | 隨產品附贈 |
| Windows 7 SP1                           | 是          | 是                         | 是          | 是          | 隨產品附贈 |
| Windows Server 2008 SP2                 |              |                             |              | 是          | 是          |
| Windows Vista<br>*支援終止*       |              |                             |              |              | 是          |
| Windows Server 2003<br>*支援終止* |              |                             |              |              | 是          |
| Windows XP<br>*支援終止*          |              |                             |              | 是          | 是          |

- **隨產品出貨** ：所指定 WMF 版本的功能已與指出版本的 Windows 用戶端或 Windows Server 一起出貨。
- **支援終止** ：Microsoft 不再支援這些產品。 您必須升級至支援的新版本。 如需詳細資訊，請參閱 [Microsoft 週期原則][]頁面。

> [!NOTE]
> WMF 5.0 安裝程式已不再提供或支援。 它已被 WMF 5.1 取代。

[Microsoft 週期原則]: https://support.microsoft.com/lifecycle
[WMF 5.1]: https://aka.ms/wmf51download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
