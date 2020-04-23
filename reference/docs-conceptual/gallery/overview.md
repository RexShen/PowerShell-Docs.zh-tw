---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 資源庫,powershell,cmdlet,psgallery,psget
title: PowerShell 資源庫
ms.openlocfilehash: e489d2dd4db087b53eb07d2a8793c8f586c9b210
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500571"
---
# <a name="the-powershell-gallery"></a>PowerShell 資源庫

PowerShell 資源庫是 PowerShell 內容的集中存放庫。 您可以在其中找到包含 PowerShell 命令或預期狀態設定 (DSC) 資源的有用 PowerShell 模組。
您也可以尋找 PowerShell 指令碼，其中有些可能會包含 PowerShell 工作流程，有些則概述一組工作並提供這些工作的序列。 這些套件有一部分是由 Microsoft 所撰寫，其他則是由 PowerShell 社群所撰寫。

## <a name="powershellget-overview"></a>PowerShellGet 概觀

PowerShellGet 模組包含適用於探索、安裝、更新及發行 PowerShell 套件的 Cmdlet，其包含來自 [PowerShell 資源庫](https://www.PowerShellGallery.com) \(英文\) 及其他私用存放庫的成品，例如模組、DSC 資源、角色功能與指令碼。

## <a name="getting-started-with-the-gallery"></a>開始使用資源庫

從資源庫安裝套件需要最新版本的 PowerShellGet 模組。 請參閱[安裝 PowerShellGet](installing-psget.md) 以取得完整的指示。

如需如何在資源庫使用 PowerShellGet 命令的詳細資訊，請查看[開始使用](getting-started.md)頁面。 您也可以執行 *Update-Help -Module PowerShellGet* 以安裝這些命令的本機說明。

## <a name="supported-operating-systems"></a>支援的作業系統

**PowerShellGet** 模組需要 **PowerShell 3.0 或更新版本**。

**PowerShellGet** 需要 .NET Framework 4.5 或更新版本。 您可以從[這裡](https://msdn.microsoft.com/library/5a4x27ek.aspx)安裝 .NET Framework 4.5 或更新版本。

由於 **PowerShell Core** 的跨平台特性，使它能在 Windows、Linux 和 MacOS 上運作，這也代表 **PowerShellGet** 可在那些系統上使用。 如需 **PowerShell Core** 所支援之系統的完整清單，請參閱[安裝 PowerShell](/powershell/scripting/install/installing-powershell)。

資源庫中裝載的眾多模組將會支援不同的 OS 並具有額外的需求。
如需詳細資訊，請參考模組的文件。

## <a name="got-a-question-have-feedback"></a>有任何問題嗎？ 想提供任何意見？

如需 PowerShell 資源庫與 PowerShellGet 的詳細資料，請前往[開始使用](getting-started.md)頁面。 請使用 [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell) 提供意見反應及回報問題。
