---
title: "安裝及設定 WMF 5.1 (預覽)"
ms.date: 2016-05-16
keywords: "PowerShell、DSC、WMF"
description: 
ms.topic: article
contributor: kriscv
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 0a53817d6af625822d9183d2a0d5bc7bf4d2b264
ms.openlocfilehash: 058d18deeb3d4926970ea25a157f92ad14836e4b

---

# 安裝及設定 WMF 5.1 (預覽) #

## 安裝 .Net 4.6
您必須先安裝 .Net Framework 4.6 才能使用 WMF 5.1。 需要此項才能啟用新的類別目錄簽署功能，其會影響模組的多個區域及 WMF 5.1 中的指令碼載入。 

[.Net Framework 4.6 可於 KB 3045560 取得](https://support.microsoft.com/en-us/kb/3045560)。 下載位置上有安裝指示。

> **注意︰**WMF 5.1 Preview 安裝程式未偵測到 .NET 4.6 需求為已知問題，所以您可以在安裝 .Net 4.6 之前安裝 WMF 5.1 Preview。 我們的測試顯示，您在安裝 WMF 5.1 Preview 後可以安裝 .Net 4.6。 WMF 5.1 的最終版本將會正確地在安裝前檢查此必要條件需求。 

## 下載並安裝 WMF 5.1 Preview

為適用於其安裝所在的作業系統和架構下載 WMF 5.1 封裝︰

| 作業系統       | 必要條件 | 封裝連結             |
|------------------------|---------------|---------------------------|
| Windows Server 2012 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586)|
| Windows Server 2012    | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823587)|
| Windows Server 2008 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> [SHA-2 程式碼簽署](https://technet.microsoft.com/en-us/library/security/3033929)的安全性更新 | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) |
| Windows 8.1            | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | **x64:** [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586) </br> **x86:** [Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823589) |
| Windows 7 SP1          | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> [SHA-2 程式碼簽署](https://technet.microsoft.com/en-us/library/security/3033929)的安全性更新 | **x64:** [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) </br> **x86:** [Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823590) |


## 從 Windows 檔案總管 (或 Windows Server 2012 R2 或 Windows 8.1 檔案總管) 安裝 WMF 5.1

1. 瀏覽至您用來下載 MSU 檔案的資料夾。

2. 按兩下 MSU 以執行。

## 從 [命令提示字元] 安裝 WMF 5.1##

1. 下載您電腦架構的正確封裝之後，以提高的使用者權限 (以系統管理員身分執行) 開啟 [命令提示字元] 視窗。 在 Windows Server 2012 R2 或 Windows Server 2012 或 Windows Server 2008 R2 SP1 的 Server Core 安裝選項上，預設會以提高的使用者權限開啟 [命令提示字元]。

2. 將目錄變更為您已下載或複製 WMF 5.1 安裝封裝的資料夾。

3. 執行下列其中一個命令：
    - 在執行 Windows Server 2012 R2 或 Windows 8.1 x64 的電腦上執行 `Win8.1AndW2K12R2-KB3156422-x64.msu /quiet`。
    - 在執行 Windows Server 2012 的電腦上執行 `W2K12-KB3156423-x64.msu /quiet`。
    - 在執行 Windows Server 2008 R2 SP1 或 Windows 7 SP1 x64 的電腦上執行 `Win7AndW2K8R2-KB3156424-x64.msu /quiet`。
    - 在執行 Windows 8.1 x86 的電腦上執行 `Win8.1-KB3156422-x86.msu /quiet`。
    - 在執行 Windows 7 SP1 x86 的電腦上執行 `Win7-KB3156424-x86.msu /quiet`。

## Windows Server 2008 SP1 和 Windows 7 SP1 的其他安裝注意事項︰##
在 Windows Server 2008 SP1 或 Windows 7 SP1 上安裝 WMF 5.1，需要安裝︰
- 最新的 Service Pack。
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855)
- WMF 5.1 需要 [Microsoft .NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560)。 您可以遵循下載位置的指示來安裝 Microsoft.NET Framework 4.6。
- [SHA-2 程式碼簽署](https://technet.microsoft.com/en-us/library/security/3033929)的安全性更新。 需要此項才能將新的 PowerShell Cmdlet 用於 Windows 類別目錄檔案。 

> **WinRM Dependency：**Windows PowerShell 預期狀態設定 (DSC) 取決於 WinRM。 在 Windows Server 2008 R2 和 Windows 7 上預設不啟用 WinRM。 若要啟用 WinRM，請在 Windows PowerShell 提高權限的工作階段中，執行 `Set-WSManQuickConfig`。




<!--HONumber=Jul16_HO5-->


