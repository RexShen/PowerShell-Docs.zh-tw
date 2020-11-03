---
description: 描述 PowerShell 中收集的遙測資料，以及如何退出。
keywords: powershell
Locale: en-US
ms.date: 08/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_telemetry?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Telemetry
ms.openlocfilehash: 4aeab828d66d1f015946051419facd81ce2b78c1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206552"
---
# <a name="about-telemetry"></a>關於遙測

## <a name="short-description"></a>簡短描述

描述 PowerShell 中收集的遙測資料，以及如何退出。

## <a name="long-description"></a>詳細描述

PowerShell 會將基本遙測資料傳送給 Microsoft。
這項資料可讓我們更加了解使用 PowerShell 的環境，並讓我們排列新功能和修正的優先順序。
記錄的遙測資料點如下：

- PowerShell 的計數會以類型 (API 與主控台) 
- 唯一 PowerShell 使用量的計數
- 下列執行類型的計數：
  - 應用程式 (原生命令) 
  - ExternalScript
  - 指令碼
  - 函式
  - Cmdlet
- PowerShell 隨附的已啟用 Microsoft 擁有實驗性功能或實驗性功能計數
- 託管會話的計數
- 已載入的 Microsoft 擁有模組計數

此資料包含 OS 名稱、作業系統版本、PowerShell 版本和散發通道。

若要退出此遙測，請將環境變數 POWERSHELL_TELEMETRY_OPTOUT 設定為 [true]、[是] 或1。
