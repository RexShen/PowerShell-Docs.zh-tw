---
title: 可更新的說明總覽 |Microsoft Docs
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
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811477"
---
# <a name="updatable-help-overview"></a>可更新的說明系統

本檔提供 Windows PowerShell 可更新說明功能的設計和操作的基本簡介。 它是專為向使用者提供 Windows PowerShell 說明主題的模組作者和其他人所設計。

## <a name="introduction"></a>簡介

Windows PowerShell 說明主題是 Windows PowerShell 經驗不可或缺的一部分。 就像 Windows PowerShell 模組一樣，作者和 Windows PowerShell 使用者的貢獻也會持續更新及改善說明主題。

Windows PowerShell 3.0 引進的「*可更新*的說明」功能，可確保使用者在命令提示字元中擁有最新版本的說明主題，即使是內建的 Windows PowerShell 命令，也不需要下載新模組或執行 Windows Update。 可更新的說明藉由提供可從網際網路下載最新版本說明主題的 Cmdlet，並將它們安裝在使用者本機電腦上正確的子目錄，讓更新變得簡單。 即使是位於防火牆後方的使用者，也可以使用新的 Cmdlet 從內部檔案共用取得已更新的說明。

Windows®8和 Windows Server®2012中的所有 Windows PowerShell 模組完全支援「可更新的說明」，而且所有 Windows PowerShell 模組作者都可以使用其功能。 可更新的說明僅支援以 XML 為基礎的說明檔。 它不支援以批註為基礎的說明。

可更新的說明包含下列功能。

- [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet 會判斷使用者是否具有模組的最新說明檔案，如果不是，則會從網際網路下載最新的說明檔案、解壓縮它們，然後將它們安裝在使用者電腦上正確的模組子目錄中。
  使用者可以使用[get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 立即查看新安裝的說明主題。
  它們不需要重新開機 PowerShell。

- [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 會從網際網路下載最新的說明檔案，並將它們儲存在檔案系統目錄中。 使用者可以使用指令程式 `Update-Help` 從檔案系統目錄取得說明檔，並將它們解壓縮並安裝在使用者電腦上的模組子目錄中。 此 `Save-Help` Cmdlet 是專為受限或無法存取網際網路的使用者，以及偏好限制網際網路存取的企業所設計。

- **模組的**說明。 模組的說明檔會以一個單位來管理及傳遞，讓使用者可以取得其所使用之模組的所有說明檔。 只有模組支援「可更新的說明」，不適用於 Windows PowerShell 嵌入式管理單元。

- **版本支援**。 可更新的說明使用標準的四位置（N1。N2.N3.N4）版本號碼。 「可更新的說明」會在使用者電腦（或目錄）的說明檔案版本號碼低於網際網路位置的說明檔案版本號碼時，下載說明檔 `Save-Help` 。

- **多種語言支援**。 可更新的說明支援多個 UI 文化特性中的模組說明檔。 可更新的說明文件名包含標準語言代碼，例如 "en-us" 和 "ja-jp"，而 `Update-Help` 和 Cmdlet 會將說明檔 `Save-Help` 放入模組目錄的特定語言子目錄中。

- **自動產生的**說明。 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 會針對沒有說明檔的命令顯示基本說明。 自動產生的說明包括命令語法和別名，以及使用 [線上說明] 和 [可更新的協助] 的指示。

- **增強的線上說明**。 輕鬆存取線上說明不再需要說明檔案。 Cmdlet 的**online**參數 `Get-Help` 現在會從任何命令的**HelpUri**屬性值取得線上說明主題的 URL （如果找不到說明檔中的線上說明 URL）。 您可以填入**HelpUri**屬性，方法是將**HelpUri**屬性新增至 Cmdlet、函式和 CIM 命令的程式碼，或使用 **。** 在工作流程和腳本中連結以批註為基礎的說明指示詞。

  為了讓我們的說明檔案可更新，Windows 8 和 Windows Server vNext 中的 Windows PowerShell 模組不會隨附說明檔。 使用者可以使用「可更新的說明」來安裝說明檔並加以更新。 其他模組的作者可以將說明檔包含在模組中，或予以省略。 「可更新的說明」的支援是選擇性的，但建議使用。
