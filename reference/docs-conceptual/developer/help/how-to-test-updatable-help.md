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
# <a name="how-to-test-updatable-help"></a>如何測試可更新的說明

本主題說明針對模組測試可更新說明的方法。

## <a name="using-verbose-to-detect-errors"></a>使用詳細資訊來偵測錯誤

上傳模組的 HelpInfo XML 檔案和 CAB 檔之後，請執行 [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 命令並搭配 **Verbose** 參數來測試檔案。 **Verbose** 參數會指示 `Update-Help` 報告其動作中的重要步驟，從讀取模組資訊清單中的 **HelpInfoUri** 索引鍵到驗證解壓縮的 CAB 檔案中的檔案類型，並將檔案放在特定語言的模組目錄中。

解決所有詳細資訊訊息時，請 `Update-Help` 使用 **Debug** 參數執行命令。
此參數應會偵測可更新說明檔的任何剩餘問題。
