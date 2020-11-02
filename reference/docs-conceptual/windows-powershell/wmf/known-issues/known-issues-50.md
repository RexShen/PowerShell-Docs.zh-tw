---
ms.date: 06/12/2017
title: WMF 5.0 中的已知問題
description: WMF 5.0 中的已知問題
ms.openlocfilehash: 3f8dcf0f7aab27ff9d3c3a17377959988844a430
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663361"
---
# <a name="known-issues-in-wmf-50"></a>WMF 5.0 中的已知問題

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>第一次使用時，會無法使用 PowerShell 快速鍵

**解決方案：** 執行下列動作之一：

1. 以滑鼠右鍵按一下 [PowerShell] 捷徑。 選取 [Windows PowerShell] 以在未提高權限的模式中啟動。
2. 以滑鼠右鍵按一下 [PowerShell] 捷徑。 以滑鼠右鍵按一下 [Windows PowerShell]，然後選取 [以系統管理員身分執行] 以在提高權限的模式中啟動。

一旦您已經執行上述動作，PowerShell 快速鍵將可以使用。 這些動作只需要執行一次。

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>在 Windows 7 上 ExecutionPolicy 相關的 PowerShell 模組和 DSC 資源報告錯誤

在 Windows 7 上，使用 PowerShell 模組和 DSC 資源可能導致報告有關 ExecutionPolicy 的錯誤。

**解決方案：** 在提高權限的 PowerShell 工作階段 (以系統管理員身分執行) 中執行下列命令，藉以將 ExecutionPolicy 設定為 **RemoteSigned** ：

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>連接到舊的遠端 Exchange 端點造成當機

舊的 Exchange 端點會重新導向至新的端點。 重新導向邏輯中的 Bug 會導致當機。

**解決方案：** 直接連線到新的端點。

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>在 Windows Server 2012 R2 上安裝 WMF 5.0 之後，錯誤地停止軟體清查記錄功能

在已執行 SIL 的 Windows Server 2012 R2 上安裝 WMF 5.0 時，軟體清查記錄功能在安裝後錯誤地停止。

**解決方案：** 安裝 WMF 之後立即執行 `Start-SilLogging` Cmdlet，因為安裝程序將會不當停止軟體清查記錄功能。

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>如果同時使用 -LiteralPath 和 -Recurse，`Get-ChildItem` 就無法運作

如果目錄名稱包含無效的萬用字元，則在同時使用 -LiteralPath 和 -Recurse 時，`Get-ChildItem` 將不會產生預期的結果。

**解決方案：** 不理想，但目前的因應措施是在指令碼中實作遞迴，不是依賴此 Cmdlet。

## <a name="sysprep-fails-after-wmf-50-installation"></a>Sysprep 在安裝 WMF 5.0 之後失敗

根據您目前執行的 Windows Server 版本而定，有兩種因應措施可解決此問題。

**解決方案：**

- 針對執行 **Windows Server 2008 R2** 的系統
  1. 以系統管理員身分開啟 PowerShell
  2. 執行下列命令

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. 執行命令並忽略錯誤 (因為它們如預期般發生)。

     ```powershell
     Publish-SilData
     ```

  4. 刪除 \Windows\System32\Logfiles\SIL\ 目錄中的檔案

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. 安裝所有可用的重要 Windows 更新，然後就能正常開始進行 Sysyprep 操作。

- 針對執行 **Windows Server 2012** 的系統
  1. 在伺服器上安裝 WMF 5.0，並使其成為 Sysprep 之後，以系統管理員身分登入。
  2. 將 Generize.xml 從目錄 `\Windows\System32\Sysprep\ActionFiles\` 複製到 Windows 目錄之外的位置，例如 `C:\`。
  3. 使用「記事本」開啟 Generalize.xml 複本。
  4. 找出並移除下列文字，每一個都有一個執行個體需要刪除 (它們將位於文件結尾附近)。

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. 儲存編輯過的 Generalize.xml 複本並關閉檔案。
  6. 以系統管理員身分開啟命令提示字元
  7. 執行下列命令，以取得 system32 資料夾中 Generalize.xml 檔案的擁有權︰

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. 執行下列命令，在檔案中設定適當的權限︰

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - 在提示字元中回答 [是]，以進行確認。
     - 請注意，您只能使用電腦上系統管理員的使用者名稱來取代 `<AdministratorUserName>`。 例如，"Administrator"。

  9. 使用下列命令，複製您編輯過的檔案，並儲存到 Sysprep 目錄︰

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - 回答 [是] 以進行覆寫 (注意，如果沒有提示要進行覆寫，請再次檢查所輸入的路徑)。
     - 假設已將您編輯過的 Generalize.xml 複本複製到 C:\。

  10. 現在已使用因應措施來更新 Generalize.xml。 請搭配已啟用的一般化選項來執行 Sysprep。
