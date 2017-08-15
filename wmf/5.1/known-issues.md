---
ms.date: 2017-06-12T00:00:00.000Z
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
title: "WMF 5.1 的已知問題"
ms.openlocfilehash: bb8967a55ec32f0ce21812e065725985010bfc8e
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2017
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
 ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```  

## <a name="jea-virtual-accounts"></a>JEA 虛擬帳戶
WMF 5.0 中設定為使用虛擬帳戶的 JEA 端點與工作階段設定，在升級為 WMF 5.1 之後將不會設定為使用虛擬帳戶。
這表示在 JEA 工作階段中執行的命令將會以連線使用者的身分執行，而不是使用暫時的系統管理員帳戶，這將能避免使用者執行需要提高權限的命令。
若要還原虛擬帳戶，您需要取消註冊，然後重新註冊使用虛擬帳戶的所有工作階段設定。

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```

