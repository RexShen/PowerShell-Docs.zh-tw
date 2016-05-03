---
title: Windows PowerShell 系統需求
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
---
# Windows PowerShell 系統需求
本主題列出 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 的系統需求，以及特殊功能 (例如 [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]、CIM 命令和工作流程) 的系統需求。

[!INCLUDE[winblue_client_1](../Token/winblue_client_1_md.md)] 和 [!INCLUDE[winblue_server_1](../Token/winblue_server_1_md.md)] 包括所有必要的程式。 本主題是針對舊版 Windows 使用者所設計。

## 作業系統需求
[!INCLUDE[psversion4](../Token/psversion4_md.md)] 是在下列版本的 Windows 上執行。

-   [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] (預設會安裝)

-   [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] (預設會安裝)

-   [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)] (含 Service Pack 1)，安裝 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) 來執行 [!INCLUDE[psversion4](../Token/psversion4_md.md)]

-   [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] (含 Service Pack 1)，安裝 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) 來執行 [!INCLUDE[psversion4](../Token/psversion4_md.md)]

[!INCLUDE[psversion3](../Token/psversion3_md.md)] 是在下列版本的 Windows 上執行。

-   [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] (預設會安裝)

-   [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] (預設會安裝)

-   [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)] (含 Service Pack 1)，安裝 [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) 來執行 [!INCLUDE[psversion3](../Token/psversion3_md.md)]

-   [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] (含 Service Pack 1)，安裝 [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) 來執行 [!INCLUDE[psversion3](../Token/psversion3_md.md)]

-   [!INCLUDE[lserver](../Token/lserver_md.md)] (含 Service Pack 2)，安裝 [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) 來執行 [!INCLUDE[psversion3](../Token/psversion3_md.md)]

## Microsoft .NET Framework 需求
[!INCLUDE[psversion4](../Token/psversion4_md.md)] 需要完整安裝 Microsoft .NET Framework 4.5。 [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] 和 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] 預設會包括 Microsoft .NET Framework 4.5。

[!INCLUDE[psversion3](../Token/psversion3_md.md)] 需要完整安裝 Microsoft .NET Framework 4。 [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] 和 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 預設會包括 Microsoft .NET Framework 4.5 (這滿足此需求)。

若要安裝 Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe)，請參閱 Microsoft 下載中心上的 [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919)。

若要安裝 Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) 的完整安裝，請參閱 Microsoft 下載中心上的 [Microsoft .NET Framework 4 (Web 安裝程式)](http://go.microsoft.com/fwlink/?LinkID=212931)。

## WS-Management 3.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 需要可支援 WinRM 服務和 WSMan 通訊協定的 WS-Management 3.0。 此程式包括在 [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)]、[!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)]、[!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)]、[!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)]、Windows Management Framework 4.0 和 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 中。

## Windows Management Instrumentation 3.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 需要 Windows Management Instrumentation 3.0 (WMI)。 此程式包括在 [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)]、[!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)]、[!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)]、[!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)]、Windows Management Framework 4.0 和 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 中。 如果電腦上未安裝此程式，則不會執行需要 WMI 的功能 (例如 CIM 命令)。

## Common Language Runtime 4.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 是針對 Common Language Runtime (CLR) 4.0 所編譯。

## 圖形化使用者介面需求
[!INCLUDE[wps_2](../Token/wps_2_md.md)] 是不需要圖形化使用者介面的主控台應用程式。 同樣地，它也適用於沒有螢幕或監視器的電腦或者使用者介面 (例如 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] 或 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 的 Server Core 安裝選項)。

不過，某些項目 (例如下列項目) 需要圖形化使用者介面。 如需詳細資料，請參閱每個項目的說明主題。

-   [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]

-   Cmdlet

    1.  [Out-GridView](https://technet.microsoft.com/en-us/library/70915a86-d753-464e-8349-cba02316154c)

    2.  [Show-Command](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41)

    3.  [Show-ControlPanelItem](https://technet.microsoft.com/en-us/library/0685d42c-37cc-498f-acf6-0ecfeb0cb162)

    4.  [Show-EventLog](https://technet.microsoft.com/en-us/library/a3b0f5ad-0438-42c7-915b-d1b4793a431c)

-   參數

    1.  [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) Cmdlet 的 **ShowWindow** 參數。

    2.  [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) 和 [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) Cmdlet 的 **ShowSecurityDescriptorUi** 參數。

## Windows PowerShell 引擎需求
[!INCLUDE[psversion4](../Token/psversion4_md.md)] 設計成與 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 舊版相容。 在 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 中，針對 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 和 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 所撰寫的 Cmdlet、提供者、嵌入式管理單元、模組和指令碼會以現狀執行。

不過，因為 Microsoft .NET Framework 4 中執行階段啟用原則的變更，所以在 [!INCLUDE[psversion3](../Token/psversion3_md.md)] (使用 CLR 4.0 所編譯) 中，必須修改才能執行針對 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 所撰寫以及使用 Common Language Runtime (CLR) 2.0 所編譯的 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 主程式。

[!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎至少需要 Microsoft .NET Framework 2.0.50727。 Microsoft .NET Framework 3.5 Service Pack 1 可滿足這項需求。 Microsoft .NET Framework 4 和更新版本的 Microsoft .NET Framework 不滿足這項需求。

如需新增或安裝 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎以及新增或安裝所需 Microsoft .NET Framework 版本的資訊，請參閱[安裝 Windows PowerShell 2.0 引擎](../Topic/Installing-the-Windows-PowerShell-2.0-Engine.md)。 如需啟動 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的資訊，請參閱[啟動 Windows PowerShell 2.0 引擎](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)。

## Windows 預先安裝環境
[!INCLUDE[psversion2](../Token/psversion2_md.md)]、[!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 是在 Windows 預先安裝環境 (Windows PE) 中執行。 不過，不支援下列 Cmdlet。

-   [背景智慧型傳送服務 (BITS) Cmdlet](http://go.microsoft.com/fwlink/?LinkId=257514)

-   [Get-EventLog](https://technet.microsoft.com/en-us/library/b4985b11-82bf-487d-928d-becd96fc0419)

-   [Get-WinEvent[PSITPro5_Diagnostic]](https://technet.microsoft.com/en-us/library/5fe94870-ed6b-4ce2-9500-93846cc65c95)

-   [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa)

-   [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545)

此外，Windows PE 上沒有 **WinRm** 服務。

## 另請參閱
[開始使用 Windows PowerShell](../Topic/Getting-Started-with-Windows-PowerShell.md)
[安裝 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[啟動 Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO2-->


