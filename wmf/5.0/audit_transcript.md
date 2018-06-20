---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 5e17b0a78f6e860c6144d2e81c426bb26126a85f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222446"
---
# <a name="enhanced-transcription-options"></a><span data-ttu-id="e9c4f-102">增強的轉譯選項</span><span class="sxs-lookup"><span data-stu-id="e9c4f-102">Enhanced Transcription Options</span></span>

<span data-ttu-id="e9c4f-103">Windows PowerShell 轉譯已經過改良，可套用至所有的裝載應用程式 (例如 Windows PowerShell ISE)，而不只是主控台主機 (powershell.exe)。</span><span class="sxs-lookup"><span data-stu-id="e9c4f-103">Windows PowerShell transcription has been improved to apply to all hosting applications (such as Windows PowerShell ISE) rather than just the console host (powershell.exe).</span></span>

<span data-ttu-id="e9c4f-104">除了擴充轉譯，轉譯功能本身也已更新為支援任意巢狀轉譯、在產生的轉譯標頭中有其他中繼資料，以及設定轉譯輸出目錄 (以支援集中式記錄檔集合)。</span><span class="sxs-lookup"><span data-stu-id="e9c4f-104">In addition to extending for transcripting, the transcripting functionality itself has been updated to support arbitrary nesting of transcripts, additional metadata in the resulting transcript header, and setting a transcription output directory (to support centralized log collection).</span></span>

<span data-ttu-id="e9c4f-105">轉譯選項 (包括啟用全系統轉譯) 可以使用 **[打開 PowerShell 轉譯]** 群組原則設定 (在 [系統管理範本] -> [Windows 元件] -> [Windows PowerShell]) 來設定。</span><span class="sxs-lookup"><span data-stu-id="e9c4f-105">Transcription options (including enabling a system-wide transcript) can be configured with the **Turn on PowerShell Transcription** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>
