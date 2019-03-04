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
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854734"
---
# <a name="how-to-test-updatable-help"></a>如何測試可更新的說明

本主題描述若要測試之模組的 可更新說明的方法。

## <a name="using-verbose-to-detect-errors"></a>使用詳細資訊，以偵測錯誤

上傳後 HelpInfo XML 檔案和封包檔的模組，來測試檔案執行[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)命令搭配**Verbose**參數。 **Verbose**參數會指示`Update-Help`回報其動作，讀取的重要步驟**HelpInfoUri**驗證解除封裝的封包檔中的檔案類型的模組資訊清單中的索引鍵並將這些檔案放在特定語言的模組目錄中。
上傳後 HelpInfo XML 檔案和封包檔的模組，來測試檔案執行[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)命令搭配**Verbose**參數。 **Verbose**參數會指示`Update-Help`回報其動作，讀取的重要步驟**HelpInfoUri**驗證解除封裝的封包檔中的檔案類型的模組資訊清單中的索引鍵並將這些檔案放在特定語言的模組目錄中。

解析所有的詳細資訊訊息時，執行`Update-Help`命令搭配**偵錯**參數。 這個參數應該會偵測任何剩餘的問題，可更新的說明檔案。