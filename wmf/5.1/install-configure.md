---
title: "安裝及設定 WMF 5.1 (預覽)"
ms.date: 2016-05-16
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
contributor: kriscv
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 26da6c80568327faadc6746099ac9869f2018fcf
ms.openlocfilehash: 8a10903c421f62311a28c9f32e352bba75f21052

---

# 安裝及設定 WMF 5.1 (預覽) #

***請注意︰*** 
*此內容是預留位置。下列連結指向 WMF 5.0 版，會在發行二進位碼檔案時更新。*

為適用於其安裝所在的作業系統和架構下載 WMF 5.1 封裝︰

| 作業系統       | 架構 | 封裝名稱              |
|------------------------|--------------|---------------------------|
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows Server 2012    | x64      | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


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

> **WinRM Dependency：**Windows PowerShell 預期狀態設定 (DSC) 取決於 WinRM。 在 Windows Server 2008 R2 和 Windows 7 上預設不啟用 WinRM。 若要啟用 WinRM，請在 Windows PowerShell 提高權限的工作階段中，執行 `Set-WSManQuickConfig`。




<!--HONumber=Jul16_HO2-->


