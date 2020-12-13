---
ms.date: 03/22/2012
ms.topic: reference
title: 可更新的說明系統
description: 可更新的說明系統
ms.openlocfilehash: b8008b7c28d94ebaac135934606042e6a6053591
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649562"
---
# <a name="updatable-help-overview"></a>可更新的說明系統

本檔提供 PowerShell 可更新說明功能的設計和操作的基本簡介。 它是專為模組作者以及提供 Windows PowerShell 說明主題給使用者的其他人員所設計。

## <a name="introduction"></a>簡介

PowerShell 說明主題是 PowerShell 體驗不可或缺的一部分。 如同 PowerShell 模組，「說明」主題會依作者和 PowerShell 使用者的貢獻而不斷更新和改進。

在 Windows PowerShell 3.0 中引進的 *可更新* 的說明功能，可確保使用者在命令提示字元中擁有最新版本的說明主題，即使是內建的 PowerShell 命令，也不需要下載新的模組或執行 Windows Update。 「可更新的說明」會提供 Cmdlet，從網際網路下載最新版本的說明主題，並將它們安裝在使用者本機電腦上的正確子目錄中，讓更新變得簡單。 即使是位於防火牆後方的使用者，也可以使用新的 Cmdlet 從內部檔案共用取得已更新的說明。

Windows 8 和 Windows Server 2012 中的所有 Windows PowerShell 模組完全支援可更新的說明，而且所有 Windows PowerShell 的模組作者都可以使用其功能。 可更新的說明只支援以 XML 為基礎的說明檔。 它不支援以批註為基礎的說明。

可更新的說明包含下列功能。

- [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet，它會判斷使用者是否有模組的最新說明檔，如果不是，則會從網際網路下載最新的說明檔、解壓縮這些檔案，並將它們安裝在使用者電腦上正確的模組子目錄中。 使用者可以使用 [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 來立即查看新安裝的說明主題。 它們不需要重新開機 PowerShell。

- [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 會從網際網路下載最新的說明檔，並將它們儲存在檔案系統目錄中。 使用者可以使用指令程式 `Update-Help` 從檔案系統目錄取得說明檔，並將其解壓縮並安裝在使用者電腦上的模組子目錄中。 此 `Save-Help` Cmdlet 是專為擁有受限或無法存取網際網路的使用者，以及希望限制網際網路存取的企業所設計。

- **模組的** 說明。 模組的說明檔是以一個單位來管理和傳遞，讓使用者可以取得所使用模組的所有說明檔。 只有模組支援可更新的說明，不適用於 Windows PowerShell 嵌入式管理單元。

- **版本支援**。 可更新的說明使用標準的四個位置 (N1。N2.N3.N4) 版本號碼。
  當使用者電腦上的說明檔案版本號碼 (或在) 目錄中時，可更新的說明會下載說明檔，其版本號碼低於網際網路位置上說明檔的 `Save-Help` 版本號碼。

- **多語言支援**。 可更新的說明支援多個 UI 文化特性中的模組說明檔。
  可更新的說明文件名包含標準語言代碼（例如 "en-us" 和 "ja-jp"），而 `Update-Help` 和 Cmdlet 會將說明檔案 `Save-Help` 放入模組目錄的特定語言子目錄中。

- **自動產生的** 說明。 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 會顯示沒有說明檔之命令的基本說明。 自動產生的說明包括命令語法和別名，以及使用「線上說明」和「可更新的說明」的指示。

- **增強的線上說明**。 輕鬆存取線上說明不再需要說明檔。 如果在說明檔 `Get-Help` 中找不到線上說明 URL，則 Cmdlet 的 online 參數現在會從任何命令的 **HelpUri** 屬性值取得線上說明主題的 URL。 您可以藉由將 **HelpUri** 屬性新增至 Cmdlet、函式和 CIM 命令的程式碼，或使用來填入 **HelpUri** 屬性 **。** 在工作流程和腳本中連結以批註為基礎的說明指示詞。

  為了讓我們的說明檔可更新，Windows 8 和 Windows Server vNext 中的 Windows PowerShell 模組不會隨附說明檔。 使用者可以使用「可更新的說明」來安裝說明檔並加以更新。 其他模組的作者可以在模組中包含說明檔，或省略這些檔案。 可更新說明的支援是選擇性的，但建議使用。
