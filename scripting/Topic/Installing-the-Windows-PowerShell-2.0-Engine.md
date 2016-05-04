---
title: 安裝 Windows PowerShell 2.0 引擎
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
---
# 安裝 Windows PowerShell 2.0 引擎
本主題說明如何安裝 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎。

[!INCLUDE[psversion3](../Token/psversion3_md.md)] 設計成與 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 舊版相容。 在 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 中，針對 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 所撰寫的 Cmdlet、提供者、嵌入式管理單元、模組和指令碼會以現狀執行。 不過，因為 Microsoft .NET Framework 4 中執行階段啟用原則的變更，所以在較新版的 [!INCLUDE[psversion2](../Token/psversion2_md.md)] (使用 CLR 4.0 所編譯) 中，必須修改才能執行針對 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 所撰寫以及使用 Common Language Runtime (CLR) 2.0 所編譯的 Windows PowerShell 主機程式。

為了維持與受到這些變更影響之主機程式的回溯相容性，[!INCLUDE[psversion2](../Token/psversion2_md.md)]、[!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 引擎已設計成並存執行。 此外，[!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎隨附於 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)]、[!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)]、[!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)]、[!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 和 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]。 只有在現有指令碼或主機程式無法執行時才會使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎，因為它與 [!INCLUDE[psversion3](../Token/psversion3_md.md)]、[!INCLUDE[psversion4](../Token/psversion4_md.md)] 或 Microsoft .NET Framework 4 不相容。 這種情況應該很少見。

[!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎是 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)]、[!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)]、[!INCLUDE[win8_client_1](../Token/win8_client_1_md.md)] 和 [!INCLUDE[win8_server_1](../Token/win8_server_1_md.md)] 的選用功能。 在舊版 Windows 上，當您安裝 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 時，[!INCLUDE[psversion3](../Token/psversion3_md.md)] 安裝會完全取代 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 安裝目錄中的 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 安裝， 但會保留 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎。

如需啟動 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的資訊，請參閱[啟動 Windows PowerShell 2.0 引擎](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)。

## 在 [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] 和 [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] 上
在 [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] 和 [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] 上，預設會開啟 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎功能。 不過若要使用，則必須開啟所需的 Microsoft .NET Framework 3.5 選項。 本節也說明如何開啟及關閉 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎功能。

#### 開啟 .NET Framework 3.5

1.  在 **[開始]** 畫面上，輸入 **Windows 功能**。

2.  在 **[應用程式]** 列中按一下 **[設定]**，然後按一下 **[開啟或關閉 Windows 功能]**。

3.  在 **[Windows 功能]** 方塊中，按一下 **[.NET Framework 3.5 (包括 .NET 2.0 和 3.0)]** 加以選取。

    當您選取 **[.NET Framework 3.5 (包括 .NET 2.0 和 3.0)]** 時，會填入方塊中以指出僅選取部分功能。 不過，這對 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎便已足夠。

#### 開啟及關閉 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎

1.  在 **[開始]** 畫面上，輸入 **Windows 功能**。

2.  在 **[應用程式]** 列中按一下 **[設定]**，然後按一下 **[開啟或關閉 Windows 功能]**。

3.  在 **[Windows 功能]** 方塊中，展開 **[[!INCLUDE[psversion2](../Token/psversion2_md.md)]]** 節點，然後按一下 **[[!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎]** 方塊加以選取或清除。

## 在 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] 和 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 上
使用下列程序新增 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎和 Microsoft .NET Framework 3.5 功能。 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎至少需要 Microsoft .NET Framework 2.0.50727。 Microsoft .NET Framework 3.5 可完成這項需求。

#### 新增 .NET Framework 3.5 功能

1.  在 **[伺服器管理員]** 中，從 **[管理]** 功能表選取 **[新增角色及功能]**。

    在 **[伺服器管理員]** 中，按一下 **[所有伺服器]**，以滑鼠右鍵按一下伺服器名稱，然後選取 **[新增角色及功能]**。

2.  在 **[安裝類型]** 頁面上，選取 **[角色型或功能型安裝]**。

3.  在 **[功能]** 頁面上，展開 **[.NET 3.5 Framework 功能]** 節點，然後選取 **[.NET Framework 3.5 (包括 .NET 2.0 和 3.0)]**。

    [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎不需要該節點下的其他選項。

#### 新增 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎功能

-   在 **[伺服器管理員]** 中，從 **[管理]** 功能表選取 **[新增角色及功能]**。

    或者，在 **[伺服器管理員]** 中，按一下 **[所有伺服器]**，以滑鼠右鍵按一下伺服器名稱，然後選取 **[新增角色及功能]**。

-   在 **[安裝類型]** 頁面上，選取 **[角色型或功能型安裝]**。

-   在 **[功能]** 頁面上，展開 **[[!INCLUDE[mshshort](../Token/mshshort_md.md)] (已安裝)]** 節點，然後選取 **[[!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎]**。

如需啟動 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的資訊，請參閱[啟動 Windows PowerShell 2.0 引擎](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)。

## 在舊版系統上
在 [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)]、[!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 和 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 上安裝 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 的 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) 套件包含 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎。 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎可視需要啟用並開始使用，而不需要額外的安裝、設定或組態。

在 [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)]、[!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 和 [!INCLUDE[lserver](../Token/lserver_md.md)] 上安裝 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 的 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 套件包含 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎。 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎可視需要啟用並開始使用，而不需要額外的安裝、設定或組態。

## 另請參閱
[Windows PowerShell 系統需求](../Topic/Windows-PowerShell-System-Requirements.md)
[安裝 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[啟動 Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
[啟動 Windows PowerShell 2.0 引擎](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)



<!--HONumber=Apr16_HO2-->


