---
title: 安裝 Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
---
# 安裝 Windows PowerShell
[!INCLUDE[win8_client_1](../Token/win8_client_1_md.md)] 和 [!INCLUDE[win8_server_1](../Token/win8_server_1_md.md)] 包含 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 及其所有先決條件。 此系統也包含 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎，以與無法使用 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 的舊版主機程式相容。

本主題說明如何在舊版系統上安裝 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 並安裝及啟用必要的功能。

這個主題包括下列各節：

-   [在 Windows 8 和 Windows Server 2012 上安裝 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [在 Windows Server 2008 上安裝 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [在 Server Core 上安裝 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [部署 Windows PowerShell Web 存取](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [安裝 Windows PowerShell 2.0 引擎](../Topic/Installing-the-Windows-PowerShell-2.0-Engine.md)

## <a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>在 Windows 8 和 Windows Server 2012 上安裝 Windows PowerShell
[!INCLUDE[psversion3](../Token/psversion3_md.md)] 預設已安裝、設定且可供使用。 [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)] 也已安裝並啟用。 如需啟動 [!INCLUDE[mshshort](../Token/mshshort_md.md)] 的資訊，請參閱 [Starting Windows PowerShell on Windows 8 (在 Windows 8 上啟動 Windows PowerShell)](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) 和 [Starting Windows PowerShell on Windows Server 2012 (在 Windows Server 2012 上啟動 Windows PowerShell)](https://technet.microsoft.com/en-us/library/4fc0110a-cc0c-42a4-bbb5-3cc89a0fc968)。

## <a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows PowerShell
下列指示說明如何在執行 [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)] Service Pack 1 和 [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] Service Pack 1 的電腦上安裝 [!INCLUDE[psversion3](../Token/psversion3_md.md)]。 針對以 [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 的 Server Core 安裝選項執行的電腦，將在下方提供個別安裝指示。

#### 準備安裝

-   安裝 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 之前，請先解除安裝任何舊版的 Windows Management Framework 3.0。

#### 安裝 [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547) 安裝 Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) 的完整安裝。

    或者，從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919) 安裝 Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe)。

2.  從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 安裝 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]。

如需啟動 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 的資訊，請參閱 [Starting Windows PowerShell on Earlier Versions of Windows (在舊版 Windows 上啟動 Windows PowerShell)](../Topic/Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md)。

## <a name="BKMK_InstallingOnServerCore"></a>在 Server Core 上安裝 Windows PowerShell
下列指示說明如何在執行 [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] Service Pack 1 之 Server Core 安裝選項的電腦上安裝 [!INCLUDE[psversion3](../Token/psversion3_md.md)]。

此程序的第一個步驟是使用部署映像服務與管理 (DISM) 命令，安裝適用於 Server Core 的 Microsoft [!INCLUDE[dnprdnlong](../Token/dnprdnlong_md.md)] 和 [!INCLUDE[psversion2](../Token/psversion2_md.md)]。 這些程式是後續步驟所要安裝之 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 的先決條件。

#### 準備安裝

-   安裝 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 之前，請先解除安裝任何舊版的 Windows Management Framework 3.0。

#### 安裝 [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  啟動 Cmd.exe

2.  執行下列 DISM 命令。 這些命令會安裝 [!INCLUDE[dnprdnlong](../Token/dnprdnlong_md.md)] 和 [!INCLUDE[psversion2](../Token/psversion2_md.md)]。

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450) 安裝適用於 Server Core 的 Microsoft [!INCLUDE[netfx40_short](../Token/netfx40_short_md.md)] 完整安裝。

4.  從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 安裝 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]。

## <a name="BKMK_InstallingOnWindowsServer2008LH"></a>在 Windows Server 2008 上安裝 Windows PowerShell
下列指示說明如何在執行 [!INCLUDE[lserver](../Token/lserver_md.md)] Service Pack 2 的電腦上安裝 [!INCLUDE[psversion3](../Token/psversion3_md.md)]。

在 [!INCLUDE[lserver](../Token/lserver_md.md)] 系統上，Windows Management Framework ([!INCLUDE[psversion2](../Token/psversion2_md.md)]，KB 968930) 是 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 的先決條件。 [驗證擴充保護] 功能可防止電腦遭受驗證轉寄攻擊，並可讓您在建立遠端工作階段時使用 **UseSSL** 參數。 若要安裝 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎，請使用下列程序。

#### 準備安裝

-   安裝 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 之前，請先解除安裝任何舊版的 Windows Management Framework 3.0。

#### 安裝 [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910) 安裝 Microsoft .NET Framework 3.5 Service Pack 1。

2.  從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035) 安裝 Windows Management Framework ([!INCLUDE[psversion2](../Token/psversion2_md.md)]KB 968930)。

3.  從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547) 安裝 Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) 的完整安裝。

    或者，從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919) 安裝 Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe)。

4.  從 [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398) 安裝「驗證延伸保護」(KB 968389)。

5.  從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 安裝 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]。

## 另請參閱
[Windows PowerShell 系統需求](../Topic/Windows-PowerShell-System-Requirements.md)
[啟動 Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO2-->


