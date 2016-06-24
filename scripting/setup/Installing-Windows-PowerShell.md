---
title:  安裝 Windows PowerShell
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
---

# 安裝 Windows PowerShell
Windows® 8 和 Windows Server® 2012 包括 Windows PowerShell 3.0 及其所有必要條件。 此系統也會包含 Windows PowerShell 2.0 引擎，以針對無法使用 Windows PowerShell 3.0 的舊版主機程式提供回溯相容性。

本主題說明如何在舊版系統上安裝 Windows PowerShell 3.0，以及安裝和啟用必要的功能。

這個主題包括下列各節：

-   [在 Windows 8 和 Windows Server 2012 上安裝 Windows PowerShell](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows PowerShell](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [在 Windows Server 2008 上安裝 Windows PowerShell](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [在 Server Core 上安裝 Windows PowerShell](Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [部署 Windows PowerShell Web 存取](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [安裝 Windows PowerShell 2.0 引擎](Installing-the-Windows-PowerShell-2.0-Engine.md)

## <a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>在 Windows 8 和 Windows Server 2012 上安裝 Windows PowerShell
Windows PowerShell 3.0 預設已安裝、設定且可供使用。 Windows PowerShell 整合指令碼環境 (ISE) 已安裝並啟用。 如需啟動 Windows PowerShell 的相關資訊，請參閱 [在 Windows 8 上啟動 Windows PowerShell](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) 以及[在 Windows Server 2012 上啟動 Windows PowerShell](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell)。

## <a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows PowerShell
下列指示說明如何在執行 Windows 7 Service Pack 1 和 Windows Server 2008 R2 Service Pack 1 的電腦上安裝 Windows PowerShell 3.0。 針對以 Windows Server 2008 R2 的 Server Core 安裝選項執行的電腦，將在下方提供個別安裝指示。

#### 準備安裝

-   安裝 Windows Management Framework 3.0 之前，請先解除安裝任何舊版的 Windows Management Framework 3.0。

#### 安裝 Windows PowerShell 3.0

1.  前往 [https://www.microsoft.com/zh-tw/download/details.aspx?id=17851](http://go.microsoft.com/fwlink/?LinkID=212547) 從 Microsoft 下載中心安裝 Microsoft .NET Framework 4 (dotNetFx40\_Full\_setup.exe) 的完整安裝。

    或者，前往 [https://www.microsoft.com/zh-tw/download/details.aspx?id=30653](http://go.microsoft.com/fwlink/?LinkID=242919) 從 Microsoft 下載中心安裝 Microsoft .NET Framework 4.5 (dotNetFx45\_Full\_setup.exe)。

2.  前往 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 從 Microsoft 下載中心安裝 Windows Management Framework 3.0。

如需啟動 Windows PowerShell 3.0 的相關資訊，請參閱[在舊版 Windows 上啟動 Windows PowerShell](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md)。

## <a name="BKMK_InstallingOnServerCore"></a>在 Server Core 上安裝 Windows PowerShell
下列指示說明如何在執行 Windows Server 2008 R2 Service Pack 1 之 Server Core 安裝選項的電腦上安裝 Windows PowerShell 3.0。

此程序的第一個步驟是使用部署映像服務與管理 (DISM) 命令，安裝適用於 Server Core 的 Microsoft .NET Framework 2.0 和 Windows PowerShell 2.0。 這些程式是要在後續步驟中安裝之 Windows Management Framework 3.0 的先決條件。

#### 準備安裝

-   安裝 Windows Management Framework 3.0 之前，請先解除安裝任何舊版的 Windows Management Framework 3.0。

#### 安裝 Windows PowerShell 3.0

1.  啟動 Cmd.exe

2.  執行下列 DISM 命令。 這些命令會安裝 .NET Framework 2.0 與 Windows PowerShell 2.0

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  前往 [https://www.microsoft.com/zh-tw/download/details.aspx?displaylang=en&id=22833](http://go.microsoft.com/fwlink/?LinkID=248450) 從 Microsoft 下載中心安裝適用於 Server Core 的 Microsoft .NET Framework 4.0 完整安裝。

4.  前往 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 從 Microsoft 下載中心安裝 Windows Management Framework 3.0。

## <a name="BKMK_InstallingOnWindowsServer2008LH"></a>在 Windows Server 2008 上安裝 Windows PowerShell
下列指示說明如何在執行 Windows Server 2008 Service Pack 2 的電腦上安裝 Windows PowerShell 3.0。

在 Windows Server 2008 系統上，Windows Management Framework (Windows PowerShell 2.0，KB 968930) 是 Windows Management Framework 3.0 的先決條件。 [驗證擴充保護] 功能可防止電腦遭受驗證轉寄攻擊，並可讓您在建立遠端工作階段時使用 **UseSSL** 參數。 若要安裝 Windows PowerShell 3.0 和 Windows PowerShell 2.0 引擎，請使用下列程序。

#### 準備安裝

-   安裝 Windows Management Framework 3.0 之前，請先解除安裝任何舊版的 Windows Management Framework 3.0。

#### 安裝 Windows PowerShell 3.0

1.  從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910) 安裝 Microsoft .NET Framework 3.5 Service Pack 1。

2.  前往 [https://support.microsoft.com/zh-tw/kb/968930](http://go.microsoft.com/fwlink/?LinkId=243035) 從 Microsoft 下載中心安裝 Windows Management Framework (Windows PowerShell 2.0，KB 968930)。

3.  前往 [https://www.microsoft.com/zh-tw/download/details.aspx?id=17851](http://go.microsoft.com/fwlink/?LinkID=212547) 從 Microsoft 下載中心安裝 Microsoft .NET Framework 4 (dotNetFx40\_Full\_setup.exe) 的完整安裝。

    或者，前往 [https://www.microsoft.com/zh-tw/download/details.aspx?id=30653](http://go.microsoft.com/fwlink/?LinkID=242919) 從 Microsoft 下載中心安裝 Microsoft .NET Framework 4.5 (dotNetFx45\_Full\_setup.exe)。

4.  從 [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398) 安裝「驗證延伸保護」(KB 968389)。

5.  前往 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 從 Microsoft 下載中心安裝 Windows Management Framework 3.0。

## 另請參閱
[Windows PowerShell 系統需求](Windows-PowerShell-System-Requirements.md)
[啟動 Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)


<!--HONumber=Jun16_HO3-->


