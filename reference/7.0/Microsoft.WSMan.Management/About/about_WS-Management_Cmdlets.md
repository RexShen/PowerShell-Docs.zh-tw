---
description: 提供 Web 服務管理的總覽 (WS-MANAGEMENT) 作為在 Windows PowerShell 中使用 WS-Management Cmdlet 的背景。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WS Management_Cmdlets
ms.openlocfilehash: 9e1042247b54bb7bde2451adb5344003bbf26ca0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208147"
---
# <a name="about-ws-management-cmdlets"></a>關於 WS-Management Cmdlet

## <a name="short-description"></a>簡短描述

提供 Web 服務管理的總覽 (WS-MANAGEMENT) 作為在 Windows PowerShell 中使用 WS-Management Cmdlet 的背景。

## <a name="long-description"></a>詳細描述

本主題將概述 (WS-MANAGEMENT) 作為背景，以在 Windows PowerShell 中使用 WS-Management Cmdlet 的「Web 服務管理」。 本主題也提供 WS-MANAGEMENT 的詳細資訊連結。 Microsoft 的 WS-Management 執行也稱為 Windows 遠端管理 (WinRM) 。

## <a name="about-ws-management"></a>關於 WS-Management

Windows 遠端管理是 Microsoft 的 WS-Management 通訊協定，這是標準的 SOAP 型、可感知防火牆的通訊協定，可讓不同廠商的硬體與作業系統交互操作。 WS-Management 通訊協定規格提供了一種常見的方式，可讓系統跨資訊技術存取及交換管理資訊， () 基礎結構。 WS-Management 和智慧型平臺管理介面 (IPMI) 以及事件收集器，都是 Windows 硬體管理功能的元件。

WS-Management 的通訊協定是以下列標準 Web 服務規格為基礎： HTTPS、SOAP over HTTP (WS-I 設定檔) 、SOAP 1.2、WS-ADDRESSING、WS-Transfer、WS-Enumeration 和 WS-事件。

## <a name="ws-management-and-wmi"></a>WS-Management 和 WMI

WS-Management 可以用來取得 Windows Management Instrumentation (WMI) 所公開的資料。 您可以透過使用 WS-Management 腳本 API 或透過 WinRM 命令列工具的腳本或應用程式取得 WMI 資料。 WS-Management 支援大部分常見的 WMI 類別和作業，包括內嵌的物件。 WS-Management 可以利用 WMI 收集資源的相關資料，或管理 Windows 電腦上的資源。 這表示您可以透過現有的 WMI 類別集，取得有關您企業中之物件（例如磁片、網路介面卡、服務或進程）的資料。 您也可以存取標準 WMI IPMI 提供者所提供的硬體資料。

## <a name="ws-management-windows-powershell-provider-wsman"></a>WS-Management Windows PowerShell 提供者 (WSMan) 

WSMan 提供者提供可用 WS-Management 設定的階層式查看。 此提供者可讓您探索及設定各種 WS-Management 設定選項。

## <a name="ws-management-configuration"></a>WS-Management 設定

如果未安裝和設定 WS-Management，Windows PowerShell 遠端處理無法使用、WS-Management Cmdlet 不會執行、WS-Management 腳本不會執行，且 WSMan 提供者無法執行資料作業。 WS-Management 命令列工具、WinRM 和事件轉送也取決於 WS-Management 設定。

## <a name="ws-management-cmdlets"></a>WS-Management Cmdlet

WS-Management 的功能是透過包含一組 Cmdlet 和 WSMan 提供者的模組，在 Windows PowerShell 中執行。 您可以使用這些 Cmdlet 來完成在本機和遠端電腦上管理 WS-Management 設定所需的端對端工作。

以下是可用的 WS-Management Cmdlet。

## <a name="connection-cmdlets"></a>連接 Cmdlet

- Connect-WSMan：將本機電腦連接至遠端電腦上的 WS-Management (WinRM) 服務。

- 中斷連線-WSMan：中斷本機電腦與遠端電腦上的 WS-Management (WinRM) 服務的連線。

## <a name="management-data-cmdlets"></a>Management-Data Cmdlet

- Set-wsmaninstance：顯示資源 URI 所指定之資源實例的管理資訊。

- Invoke-wsmanaction：在由資源 URI 和選取器所指定的目標物件上叫用動作。

- Set-wsmaninstance：建立新的管理資源實例。

- Set-wsmaninstance：刪除管理資源實例。

- Set-wsmaninstance：修改與資源相關的管理資訊。

## <a name="setup-and-configuration-cmdlets"></a>設定和設定 Cmdlet

- >set-wsmanquickconfig：設定本機電腦以進行遠端系統管理。
  您可以使用 Set-WSManQuickConfig Cmdlet 來設定 WS-Management，以允許 WS-Management (WinRM) 服務的遠端連線。 Set-WSManQuickConfig Cmdlet 會執行下列作業：
  - 它會判斷 WS-Management (WinRM) 服務是否正在執行。 如果 WinRM 服務未執行，Set-WSManQuickConfig Cmdlet 會啟動服務。
  - 它會將 WS-Management (WinRM) 服務啟動類型設定為 [自動]。
  - 它會建立接聽程式，以接受來自任何 IP 位址的要求。 預設的傳輸通訊協定為 HTTP。
  - 它會針對 WS-Management 流量啟用防火牆例外。

  注意：若要在 Windows Vista、Windows Server 2008 和更新版本的 Windows 中執行此 Cmdlet，您必須使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。

- 測試-WSMan：確認已安裝並設定 WS-Management。 Test-WSMan Cmdlet 會測試 WS-Management (WinRM) 服務是否正在本機或遠端電腦上執行和設定。

- WSManCredSSP：停用用戶端電腦上的 CredSSP 驗證。

- WSManCredSSP：在用戶端電腦上啟用 CredSSP 驗證。

- WSManCredSSP：取得用戶端電腦的 CredSSP 相關設定。

## <a name="ws-management-specific-cmdlets"></a>WS-MANAGEMENT 專用的 Cmdlet

- New-wsmansessionoption：建立 New-wsmansessionoption 物件，用來做為 WS-Management Cmdlet 的一或多個參數的輸入。

## <a name="additional-ws-management-information"></a>其他 WS-Management 資訊

如需 WS-MANAGEMENT 的詳細資訊，請參閱 MSDN (Microsoft 開發人員網路) 程式庫中的下列主題。

[Windows 遠端管理](/windows/win32/winrm/portal)

[關於 Windows 遠端管理](/windows/win32/winrm/about-windows-remote-management)

[Windows 遠端管理的安裝和設定](/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

[Windows 遠端管理架構](/windows/win32/winrm/windows-remote-management-architecture)

[WS-Management 通訊協定](/windows/win32/winrm/ws-management-protocol)

[Windows 遠端管理和 WMI](/windows/win32/winrm/windows-remote-management-and-wmi)

[資源 URI](/windows/win32/winrm/resource-uris)

[遠端硬體管理](/windows/win32/winrm/remote-hardware-management)

[事件](/windows/win32/winrm/events)

## <a name="see-also"></a>另請參閱

[Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)

[Disable-WSManCredSSP](xref:Microsoft.WSMan.Management.Disable-WSManCredSSP)

[Disconnect-WSMan](xref:Microsoft.WSMan.Management.Disconnect-WSMan)

[Enable-WSManCredSSP](xref:Microsoft.WSMan.Management.Enable-WSManCredSSP)

[Get-WSManCredSSP](xref:Microsoft.WSMan.Management.Get-WSManCredSSP)

[Get-WSManInstance](xref:Microsoft.WSMan.Management.Get-WSManInstance)

[Invoke-WSManAction](xref:Microsoft.WSMan.Management.Invoke-WSManAction)

[New-WSManInstance](xref:Microsoft.WSMan.Management.New-WSManInstance)

[Remove-WSManInstance](xref:Microsoft.WSMan.Management.Remove-WSManInstance)

[Set-WSManInstance](xref:Microsoft.WSMan.Management.Set-WSManInstance)

[Set-WSManQuickConfig](xref:Microsoft.WSMan.Management.Set-WSManQuickConfig)

[Test-WSMan](xref:Microsoft.WSMan.Management.Test-WSMan)
