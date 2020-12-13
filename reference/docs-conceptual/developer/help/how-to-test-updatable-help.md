---
ms.date: 09/12/2016
ms.topic: reference
title: 如何測試可更新的說明
description: 如何測試可更新的說明
ms.openlocfilehash: 47873089bfa1b918ea9970915e829a22aa7254c5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667618"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="b989f-103">如何測試可更新的說明</span><span class="sxs-lookup"><span data-stu-id="b989f-103">How to Test Updatable Help</span></span>

<span data-ttu-id="b989f-104">本主題說明針對模組測試可更新說明的方法。</span><span class="sxs-lookup"><span data-stu-id="b989f-104">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="b989f-105">使用詳細資訊來偵測錯誤</span><span class="sxs-lookup"><span data-stu-id="b989f-105">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="b989f-106">上傳模組的 HelpInfo XML 檔案和 CAB 檔之後，請執行 [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 命令並搭配 **Verbose** 參數來測試檔案。</span><span class="sxs-lookup"><span data-stu-id="b989f-106">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="b989f-107">**Verbose** 參數會指示 `Update-Help` 報告其動作中的重要步驟，從讀取模組資訊清單中的 **HelpInfoUri** 索引鍵到驗證解壓縮的 CAB 檔案中的檔案類型，並將檔案放在特定語言的模組目錄中。</span><span class="sxs-lookup"><span data-stu-id="b989f-107">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="b989f-108">解決所有詳細資訊訊息時，請 `Update-Help` 使用 **Debug** 參數執行命令。</span><span class="sxs-lookup"><span data-stu-id="b989f-108">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span>
<span data-ttu-id="b989f-109">此參數應會偵測可更新說明檔的任何剩餘問題。</span><span class="sxs-lookup"><span data-stu-id="b989f-109">This parameter should detect any remaining problems with the Updatable Help files.</span></span>
