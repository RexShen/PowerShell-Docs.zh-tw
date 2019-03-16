---
title: 可更新的說明概觀 |Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: f2dfb9642ba2dde38124142b659b425bbbb00f37
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057598"
---
# <a name="updatable-help-overview"></a>可更新的說明系統

本文件提供的設計和操作 Windows PowerShell 可更新的說明 」 功能的基本介紹。 它被針對模組作者和其他人都將傳遞給使用者的 Windows PowerShell 說明主題。

## <a name="introduction"></a>簡介

Windows PowerShell 說明主題是 Windows PowerShell 體驗中不可或缺的一部分。 類似 Windows PowerShell 模組，[說明] 主題會持續更新，並改善作者和 Windows PowerShell 使用者社群的貢獻。

*Updatable Help* Windows PowerShell 3.0 中引進的功能可確保使用者擁有最新版本說明主題在命令提示字元，甚至是內建的 Windows PowerShell 命令，而不需要下載新的模組或執行 Windows Update。 可更新的說明簡化了更新提供 cmdlet，從網際網路下載最新版本說明主題，以及使用者的本機電腦上正確的子目錄中安裝它們。 即使位於防火牆後方的使用者可以使用新的 cmdlet，從內部檔案共用取得已更新的說明。

Windows® 8 和 Windows Server® 2012年中的所有 Windows PowerShell 模組的完整都支援可更新的說明和其功能都適用於所有 Windows PowerShell 模組的作者。 可更新的說明只支援以 XML 為基礎的說明檔案。 它不支援註解型說明。

可更新的說明包括下列功能。

- [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)指令程式，以判斷使用者是否具有的最新說明檔案的模組，如果沒有，請從網際網路下載最新說明檔案，解壓縮，並在正確的模組子目錄中安裝在使用者的電腦。
  使用者可以使用[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet，以立即檢視新安裝的 [說明] 主題。
  它們不需要重新啟動 PowerShell。

- [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help)指令程式，以下載最新的說明檔從網際網路，並將它們儲存在檔案系統目錄。 使用者可以使用`Update-Help`cmdlet 來取得說明檔從檔案系統目錄中，並解壓縮並安裝在使用者的電腦上的模組子目錄。 `Save-Help` Cmdlet 的設計目的，使用者有限或沒有網際網路存取權，並對於想要限制網際網路存取的企業。

- **模組的說明**。 管理和傳遞做為一個單位，因此使用者可以取得它們所使用的模組的說明檔案的所有模組的說明檔。 只能針對模組，不適用於 Windows PowerShell 嵌入式管理單元支援可更新的說明。

- **版本支援**。 可更新的說明使用的標準四個位置 (N1。N2。N3。N4) 版本號碼。 可更新的說明會在使用者電腦上的版本號碼的說明檔案時，會下載說明檔 (或`Save-Help`目錄) 低於網際網路位置的說明檔案的版本號碼。

- **多語言支援**。 可更新的說明支援多重 UI 文化特性中的模組的說明檔。 可更新的說明檔案名稱中包含標準的語言代碼，例如"EN-US"和"JA-JP"，而`Update-Help`和`Save-Help`指令程式會放在模組目錄的語言特定子目錄中的說明檔。

- **自動產生的說明**。 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet 會顯示基本的說明，並沒有說明檔的命令。 自動產生的說明包含命令語法和別名，並使用線上說明和可更新說明的指示。

- **增強的線上說明**。 輕鬆存取線上說明不再需要的說明檔。 **線上**的參數`Get-Help`cmdlet 現在可取得線上說明主題的 URL 的值**HelpUri**任何命令，如果說明檔中找不到線上說明 URL 的屬性。 您可以填入**HelpUri**屬性，加上**HelpUri**屬性設定為 cmdlet、 函數及 CIM 命令，或使用的程式碼 **。連結**註解型說明工作流程和指令碼中的指示詞。

  若要讓我們說明檔的可更新，Windows 8 和 Windows Server vNext 中的 Windows PowerShell 模組不是隨附說明檔。 使用者可以使用可更新的說明來安裝說明檔並加以更新。 其他模組的作者可以在模組中包含說明檔，或省略它們。 選擇性的但建議使用支援可更新的說明。
