---
title: "WMF 5.1 的已知問題"
ms.date: 2016-07-13
keywords: "PowerShell、DSC、WMF"
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: b341f57592feb183eb0e7228cdc08460e370369f
ms.sourcegitcommit: f06ef671c0a646bdd277634da89cc11bc2a78a41
translationtype: HT
---
# <a name="known-issues-in-wmf-51"></a>WMF 5.1 的已知問題 #

> 注意：本資訊有可能變更。

## <a name="starting-powershell-shortcut-as-administrator"></a>以系統管理員身分啟動 PowerShell 捷徑
安裝 WMF 時，如果您嘗試以系統管理員身分從捷徑啟動 PowerShell，可能會收到「未指定的錯誤」訊息。
您現在可以系統管理員以外的身分重新開啟捷徑，捷徑將會以系統管理員身分運作。

## <a name="pester"></a>Pester
在此版本中，當您在 Nano 伺服器使用 Pester 時有兩個問題應該要注意︰

* 因為完整 CLR 和核心 CLR 之間的差異，針對 Pester 本身執行測試時會導致某些失敗。 尤其 XmlDocument 不提供類型驗證方法。 已知有六個嘗試驗證 NUnit 輸出記錄檔結構描述的測試會失敗。 
* 有一個程式碼涵蓋範圍測試失敗起因於 Nano 伺服器沒有 *WindowsFeature* DSC 資源。 不過，這些失敗通常是無害的，可以放心地忽略。

## <a name="operation-validation"></a>作業驗證 

* 因為不具有效的說明 URI，導致 Microsoft.PowerShell.Operation.Validation 模組的 Update-Help 失敗

## <a name="dsc-after-uninstall-wmf"></a>解除安裝 WMF 之後的 DSC 
* 解除安裝 WMF 不會從組態資料夾中刪除 DSC MOF 文件。 若 MOF 文件包含更新且無法在舊版系統上使用的內容，DSC 便無法正常運作。 在此情況下，請從提高權限的 PowerShell 主控台中執行下列指令碼，以清除 DSC 狀態。
 ```PowerShell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```  
