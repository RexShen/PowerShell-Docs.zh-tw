---
title: 如何測試可更新的說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367147"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="d9bb9-102">如何測試可更新的說明</span><span class="sxs-lookup"><span data-stu-id="d9bb9-102">How to Test Updatable Help</span></span>

<span data-ttu-id="d9bb9-103">本主題說明如何測試模組的可更新說明。</span><span class="sxs-lookup"><span data-stu-id="d9bb9-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="d9bb9-104">使用 Verbose 來偵測錯誤</span><span class="sxs-lookup"><span data-stu-id="d9bb9-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="d9bb9-105">上傳模組的 HelpInfo XML 檔案和 CAB 檔案之後，請使用**Verbose**參數執行[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)命令來測試檔案。</span><span class="sxs-lookup"><span data-stu-id="d9bb9-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="d9bb9-106">**Verbose**參數會指示 `Update-Help` 回報其動作中的重要步驟，從讀取模組資訊清單中的**HelpInfoUri**索引鍵，到驗證已解壓縮封包檔中的檔案類型，然後將檔案放在特定語言的模組目錄中。</span><span class="sxs-lookup"><span data-stu-id="d9bb9-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="d9bb9-107">解決所有詳細資訊訊息時，請使用**Debug**參數執行 `Update-Help` 命令。</span><span class="sxs-lookup"><span data-stu-id="d9bb9-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="d9bb9-108">這個參數應該會偵測到可更新的說明檔中的任何剩餘問題。</span><span class="sxs-lookup"><span data-stu-id="d9bb9-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>