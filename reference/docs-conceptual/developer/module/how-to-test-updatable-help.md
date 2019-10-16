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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367147"
---
# <a name="how-to-test-updatable-help"></a>如何測試可更新的說明

本主題說明如何測試模組的可更新說明。

## <a name="using-verbose-to-detect-errors"></a>使用 Verbose 來偵測錯誤

上傳模組的 HelpInfo XML 檔案和 CAB 檔案之後，請使用**Verbose**參數執行[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)命令來測試檔案。 **Verbose**參數會指示 `Update-Help` 來報告其動作中的重要步驟，從讀取模組資訊清單中的**HelpInfoUri**索引鍵，到驗證解壓縮封包檔中的檔案類型，並將檔案放在特定語言的模組目錄。

解決所有詳細資訊訊息時，請使用**Debug**參數執行 `Update-Help` 命令。 這個參數應該會偵測到可更新的說明檔中的任何剩餘問題。