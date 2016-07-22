---
title: "WMF 5.1 (Preview) 的 PowerShell 引擎改善"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 0e876b291075458a089c8a550bcee84b6e06b393

---

#PowerShell 引擎改善

WMF 5.1 已實作核心 PowerShell 引擎的下列改善︰


## 效能 ##

某些重要區域的效能已改善︰

- 啟動
- 管線到 ForEach-Object 和 Where-Object 等 Cmdlet 大約快了 50% 

一些改善範例 (結果隨硬體而有不同)： 

| 案例 | 5.0 的時間 (毫秒) | 5.1 的時間 (毫秒) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| PowerShell 首次執行︰ `powershell -command "Unknown-Command"` | 30000 | 13000 |
| 命令分析快取組建︰ `powershell -command "Unknown-Command"` | 7000 | 520 |
| `1..1000000 | % { }` | 1400 | 750 |
  
> [!NOTE]  
> 與啟動相關的一項變更，可能影響到某些不受支援的案例。 PowerShell 不再讀取 `$pshome\*.ps1xml` 檔案，這些檔案已轉換成 C#，以避免處理 XML 檔案的一些檔案和 CPU 負荷。 這些檔案對 V2 的支援仍然不變，因此，若變更檔案內容，對 V5 沒有任何效果，只對 V2 有效果。 請注意，變更這些檔案內容向來是不受支援的案例。

另一個明顯的變更，是 PowerShell 如何快取匯出的命令和安裝在系統上的模組其他資訊。 以往，此快取儲存於 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` 目錄。 在 WMF 5.1，快取是單一的 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 檔案。
如需詳細資訊，請參閱 [analysis_cache.md]()。


<!--HONumber=Jul16_HO3-->


