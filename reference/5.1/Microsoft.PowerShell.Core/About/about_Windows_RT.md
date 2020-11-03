---
description: 說明 Windows RT 8.1 上 Windows PowerShell 4.0 的限制。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_rt?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_RT
ms.openlocfilehash: 323f06a7a0d8253417510503c1011ac02c20179f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207504"
---
# <a name="about-windows-rt"></a>關於 Windows RT

## <a name="short-description"></a>簡短描述

說明 Windows RT 8.1 上 Windows PowerShell 4.0 的限制。

## <a name="long-description"></a>詳細描述

Windows RT 8.1 作業系統安裝在 (的電腦和裝置上，例如 Microsoft Surface 2，它是隨附于電腦) 的作業系統，其使用 Advanced RISC 機器 (ARM) 處理器。

Windows RT 8.1 中包含 Windows PowerShell 4.0。 所有的 Cmdlet、提供者和模組，以及針對 Windows PowerShell 2.0 和更新版本所設計的大部分腳本，都是在 Windows RT 8.1 上執行而不需要變更。

因為 Windows RT 8.1 不包含所有 Windows 功能，某些 Windows PowerShell 功能的運作方式不同，或無法在 Windows RT 型裝置上運作。 下列清單說明差異。

- Windows PowerShell ISE 不包含在中，而且無法在 Windows RT 8.1 上執行。
  Windows PowerShell ISE 需要 Windows Presentation Foundation，但 Windows RT 8.1 不包含此功能。

- Windows PowerShell 的遠端處理和 WinRM 服務預設為停用。
  若要啟用遠端功能，請執行 Enable-PSRemoting Cmdlet。 此外，也請執行 Set-Service Cmdlet，將 WinRM 服務的啟動類型設定為 [自動]，或 [自動 (延遲啟動) ]。

  遠端停用時，您可以使用 Windows PowerShell 遠端處理在其他電腦上執行命令，但其他電腦無法在 Windows RT 裝置上執行命令。 此外，隱含遠端處理-也就是內建至 Cmdlet 或腳本的遠端處理，並不會使用新增的參數明確要求
  - 在 Windows RT 8.1 上執行的 Windows PowerShell 中無法運作。

- Windows RT 8.1 不支援已加入網域的計算和 Kerberos 驗證。 您無法使用 Windows PowerShell 來新增或管理這些功能。

- Windows RT 8.1 上的 Windows PowerShell 也不支援 Windows RT 8.1 上不支援的 Microsoft .NET Framework 類別。

- 未在 Windows RT 8.1 上啟用交易。 交易 Cmdlet （例如，UseTransaction）無法正常運作，例如啟動交易和交易參數。

- Windows RT 8.1 裝置上的所有 Windows PowerShell 會話都會使用 ConstrainedLanguage 語言模式。 ConstrainedLanguage 語言模式是使用者模式的程式碼完整性 (UMCI) 。 它允許所有的 Windows Cmdlet 和 Windows PowerShell 的語言專案，但會限制類型，以確保使用者無法使用 Windows PowerShell 來規避或違反 UMCI 防護。

如需 ConstrainedLanguage 語言模式的詳細資訊，請參閱 [about_Language_Modes](about_Language_Modes.md)。

## <a name="see-also"></a>另請參閱

[about_Language_Modes](about_Language_Modes.md)

[about_Remote](about_Remote.md)

[about_Windows_PowerShell_ISE](about_Windows_PowerShell_ISE.md)
