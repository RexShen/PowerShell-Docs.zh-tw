---
description: 提供 Web 服務管理的總覽 (WS-MANAGEMENT) 作為在 Windows PowerShell 中使用 WS-Management Cmdlet 的背景。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WS Management_Cmdlets
ms.openlocfilehash: 242e9aef9015e3acef11a191a9f2fa83615a12db
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208719"
---
# <a name="about-ws-management-cmdlets"></a><span data-ttu-id="e479e-104">關於 WS-Management Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e479e-104">About WS-Management Cmdlets</span></span>

## <a name="short-description"></a><span data-ttu-id="e479e-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="e479e-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="e479e-106">提供 Web 服務管理的總覽 (WS-MANAGEMENT) 作為在 Windows PowerShell 中使用 WS-Management Cmdlet 的背景。</span><span class="sxs-lookup"><span data-stu-id="e479e-106">Provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="e479e-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="e479e-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e479e-108">本主題將概述 (WS-MANAGEMENT) 作為背景，以在 Windows PowerShell 中使用 WS-Management Cmdlet 的「Web 服務管理」。</span><span class="sxs-lookup"><span data-stu-id="e479e-108">This topic provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span> <span data-ttu-id="e479e-109">本主題也提供 WS-MANAGEMENT 的詳細資訊連結。</span><span class="sxs-lookup"><span data-stu-id="e479e-109">This topic also provides links to more information about WS-Management.</span></span> <span data-ttu-id="e479e-110">Microsoft 的 WS-Management 執行也稱為 Windows 遠端管理 (WinRM) 。</span><span class="sxs-lookup"><span data-stu-id="e479e-110">The Microsoft implementation of WS-Management is also known as Windows Remote Management (WinRM).</span></span>

## <a name="about-ws-management"></a><span data-ttu-id="e479e-111">關於 WS-Management</span><span class="sxs-lookup"><span data-stu-id="e479e-111">About WS-Management</span></span>

<span data-ttu-id="e479e-112">Windows 遠端管理是 Microsoft 的 WS-Management 通訊協定，這是標準的 SOAP 型、可感知防火牆的通訊協定，可讓不同廠商的硬體與作業系統交互操作。</span><span class="sxs-lookup"><span data-stu-id="e479e-112">Windows Remote Management is the Microsoft implementation of the WS-Management protocol, a standard SOAP-based, firewall-friendly protocol that allows hardware and operating systems from different vendors to interoperate.</span></span> <span data-ttu-id="e479e-113">WS-Management 通訊協定規格提供了一種常見的方式，可讓系統跨資訊技術存取及交換管理資訊， () 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="e479e-113">The WS-Management protocol specification provides a common way for systems to access and exchange management information across an information technology (IT) infrastructure.</span></span> <span data-ttu-id="e479e-114">WS-Management 和智慧型平臺管理介面 (IPMI) 以及事件收集器，都是 Windows 硬體管理功能的元件。</span><span class="sxs-lookup"><span data-stu-id="e479e-114">WS-Management and Intelligent Platform Management Interface (IPMI), along with the Event Collector, are components of the Windows Hardware Management features.</span></span>

<span data-ttu-id="e479e-115">WS-Management 的通訊協定是以下列標準 Web 服務規格為基礎： HTTPS、SOAP over HTTP (WS-I 設定檔) 、SOAP 1.2、WS-ADDRESSING、WS-Transfer、WS-Enumeration 和 WS-事件。</span><span class="sxs-lookup"><span data-stu-id="e479e-115">The WS-Management protocol is based on the following standard Web service specifications: HTTPS, SOAP over HTTP (WS-I profile), SOAP 1.2, WS-Addressing, WS-Transfer, WS-Enumeration, and WS-Eventing.</span></span>

## <a name="ws-management-and-wmi"></a><span data-ttu-id="e479e-116">WS-Management 和 WMI</span><span class="sxs-lookup"><span data-stu-id="e479e-116">WS-Management and WMI</span></span>

<span data-ttu-id="e479e-117">WS-Management 可以用來取得 Windows Management Instrumentation (WMI) 所公開的資料。</span><span class="sxs-lookup"><span data-stu-id="e479e-117">WS-Management can be used to retrieve data exposed by Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="e479e-118">您可以透過使用 WS-Management 腳本 API 或透過 WinRM 命令列工具的腳本或應用程式取得 WMI 資料。</span><span class="sxs-lookup"><span data-stu-id="e479e-118">You can obtain WMI data with scripts or applications that use the WS-Management Scripting API or through the WinRM command-line tool.</span></span> <span data-ttu-id="e479e-119">WS-Management 支援大部分常見的 WMI 類別和作業，包括內嵌的物件。</span><span class="sxs-lookup"><span data-stu-id="e479e-119">WS-Management supports most of the familiar WMI classes and operations, including embedded objects.</span></span> <span data-ttu-id="e479e-120">WS-Management 可以利用 WMI 收集資源的相關資料，或管理 Windows 電腦上的資源。</span><span class="sxs-lookup"><span data-stu-id="e479e-120">WS-Management can leverage WMI to collect data about resources or to manage resources on a Windows-based computers.</span></span> <span data-ttu-id="e479e-121">這表示您可以透過現有的 WMI 類別集，取得有關您企業中之物件（例如磁片、網路介面卡、服務或進程）的資料。</span><span class="sxs-lookup"><span data-stu-id="e479e-121">That means that you can obtain data about objects such as disks, network adapters, services, or processes in your enterprise through the existing set of WMI classes.</span></span> <span data-ttu-id="e479e-122">您也可以存取標準 WMI IPMI 提供者所提供的硬體資料。</span><span class="sxs-lookup"><span data-stu-id="e479e-122">You can also access the hardware data that is available from the standard WMI IPMI provider.</span></span>

## <a name="ws-management-windows-powershell-provider-wsman"></a><span data-ttu-id="e479e-123">WS-Management Windows PowerShell 提供者 (WSMan) </span><span class="sxs-lookup"><span data-stu-id="e479e-123">WS-Management Windows PowerShell Provider (WSMan)</span></span>

<span data-ttu-id="e479e-124">WSMan 提供者提供可用 WS-Management 設定的階層式查看。</span><span class="sxs-lookup"><span data-stu-id="e479e-124">The WSMan provider provides a hierarchical view into the available WS-Management configuration settings.</span></span> <span data-ttu-id="e479e-125">此提供者可讓您探索及設定各種 WS-Management 設定選項。</span><span class="sxs-lookup"><span data-stu-id="e479e-125">The provider allows you to explore and set the various WS-Management configuration options.</span></span>

## <a name="ws-management-configuration"></a><span data-ttu-id="e479e-126">WS-Management 設定</span><span class="sxs-lookup"><span data-stu-id="e479e-126">WS-Management Configuration</span></span>

<span data-ttu-id="e479e-127">如果未安裝和設定 WS-Management，Windows PowerShell 遠端處理無法使用、WS-Management Cmdlet 不會執行、WS-Management 腳本不會執行，且 WSMan 提供者無法執行資料作業。</span><span class="sxs-lookup"><span data-stu-id="e479e-127">If WS-Management is not installed and configured, Windows PowerShell remoting is not available, the WS-Management cmdlets do not run, WS-Management scripts do not run, and the WSMan provider cannot perform data operations.</span></span> <span data-ttu-id="e479e-128">WS-Management 命令列工具、WinRM 和事件轉送也取決於 WS-Management 設定。</span><span class="sxs-lookup"><span data-stu-id="e479e-128">The WS-Management command-line tool, WinRM, and event forwarding also depend on the WS-Management configuration.</span></span>

## <a name="ws-management-cmdlets"></a><span data-ttu-id="e479e-129">WS-Management Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e479e-129">WS-Management Cmdlets</span></span>

<span data-ttu-id="e479e-130">WS-Management 的功能是透過包含一組 Cmdlet 和 WSMan 提供者的模組，在 Windows PowerShell 中執行。</span><span class="sxs-lookup"><span data-stu-id="e479e-130">WS-Management functionality is implemented in Windows PowerShell through a module that contains a set of cmdlets and the WSMan provider.</span></span> <span data-ttu-id="e479e-131">您可以使用這些 Cmdlet 來完成在本機和遠端電腦上管理 WS-Management 設定所需的端對端工作。</span><span class="sxs-lookup"><span data-stu-id="e479e-131">You can use these cmdlets to complete the end-to-end tasks necessary to manage WS-Management settings on local and remote computers.</span></span>

<span data-ttu-id="e479e-132">以下是可用的 WS-Management Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e479e-132">The following WS-Management cmdlets are available.</span></span>

## <a name="connection-cmdlets"></a><span data-ttu-id="e479e-133">連接 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e479e-133">Connection Cmdlets</span></span>

- <span data-ttu-id="e479e-134">Connect-WSMan：將本機電腦連接至遠端電腦上的 WS-Management (WinRM) 服務。</span><span class="sxs-lookup"><span data-stu-id="e479e-134">Connect-WSMan: Connects the local computer to the WS-Management (WinRM) service on a remote computer.</span></span>

- <span data-ttu-id="e479e-135">中斷連線-WSMan：中斷本機電腦與遠端電腦上的 WS-Management (WinRM) 服務的連線。</span><span class="sxs-lookup"><span data-stu-id="e479e-135">Disconnect-WSMan: Disconnects the local computer from the WS-Management (WinRM) service on a remote computer.</span></span>

## <a name="management-data-cmdlets"></a><span data-ttu-id="e479e-136">Management-Data Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e479e-136">Management-Data Cmdlets</span></span>

- <span data-ttu-id="e479e-137">Set-wsmaninstance：顯示資源 URI 所指定之資源實例的管理資訊。</span><span class="sxs-lookup"><span data-stu-id="e479e-137">Get-WSManInstance: Displays management information for a resource instance that is specified by a resource URI.</span></span>

- <span data-ttu-id="e479e-138">Invoke-wsmanaction：在由資源 URI 和選取器所指定的目標物件上叫用動作。</span><span class="sxs-lookup"><span data-stu-id="e479e-138">Invoke-WSManAction: Invokes an action on the target object that is specified by the resource URI and by the selectors.</span></span>

- <span data-ttu-id="e479e-139">Set-wsmaninstance：建立新的管理資源實例。</span><span class="sxs-lookup"><span data-stu-id="e479e-139">New-WSManInstance: Creates a new management resource instance.</span></span>

- <span data-ttu-id="e479e-140">Set-wsmaninstance：刪除管理資源實例。</span><span class="sxs-lookup"><span data-stu-id="e479e-140">Remove-WSManInstance: Deletes a management resource instance.</span></span>

- <span data-ttu-id="e479e-141">Set-wsmaninstance：修改與資源相關的管理資訊。</span><span class="sxs-lookup"><span data-stu-id="e479e-141">Set-WSManInstance: Modifies the management information that is related to a resource.</span></span>

## <a name="setup-and-configuration-cmdlets"></a><span data-ttu-id="e479e-142">設定和設定 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e479e-142">Setup and Configuration Cmdlets</span></span>

- <span data-ttu-id="e479e-143">>set-wsmanquickconfig：設定本機電腦以進行遠端系統管理。</span><span class="sxs-lookup"><span data-stu-id="e479e-143">Set-WSManQuickConfig: Configures the local computer for remote management.</span></span>
  <span data-ttu-id="e479e-144">您可以使用 Set-WSManQuickConfig Cmdlet 來設定 WS-Management，以允許 WS-Management (WinRM) 服務的遠端連線。</span><span class="sxs-lookup"><span data-stu-id="e479e-144">You can use the Set-WSManQuickConfig cmdlet to configure WS-Management to allow remote connections to the WS-Management (WinRM) service.</span></span> <span data-ttu-id="e479e-145">Set-WSManQuickConfig Cmdlet 會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e479e-145">The Set-WSManQuickConfig cmdlet performs the following operations:</span></span>
  - <span data-ttu-id="e479e-146">它會判斷 WS-Management (WinRM) 服務是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="e479e-146">It determines whether the WS-Management (WinRM) service is running.</span></span> <span data-ttu-id="e479e-147">如果 WinRM 服務未執行，Set-WSManQuickConfig Cmdlet 會啟動服務。</span><span class="sxs-lookup"><span data-stu-id="e479e-147">If the WinRM service is not running, the Set-WSManQuickConfig cmdlet starts the service.</span></span>
  - <span data-ttu-id="e479e-148">它會將 WS-Management (WinRM) 服務啟動類型設定為 [自動]。</span><span class="sxs-lookup"><span data-stu-id="e479e-148">It sets the WS-Management (WinRM) service startup type to automatic.</span></span>
  - <span data-ttu-id="e479e-149">它會建立接聽程式，以接受來自任何 IP 位址的要求。</span><span class="sxs-lookup"><span data-stu-id="e479e-149">It creates a listener that accepts requests from any IP address.</span></span> <span data-ttu-id="e479e-150">預設的傳輸通訊協定為 HTTP。</span><span class="sxs-lookup"><span data-stu-id="e479e-150">The default transport protocol is HTTP.</span></span>
  - <span data-ttu-id="e479e-151">它會針對 WS-Management 流量啟用防火牆例外。</span><span class="sxs-lookup"><span data-stu-id="e479e-151">It enables a firewall exception for WS-Management traffic.</span></span>

  <span data-ttu-id="e479e-152">注意：若要在 Windows Vista、Windows Server 2008 和更新版本的 Windows 中執行此 Cmdlet，您必須使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e479e-152">Note: To run this cmdlet in Windows Vista, Windows Server 2008, and later versions of Windows, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

- <span data-ttu-id="e479e-153">測試-WSMan：確認已安裝並設定 WS-Management。</span><span class="sxs-lookup"><span data-stu-id="e479e-153">Test-WSMan: Verifies that WS-Management is installed and configured.</span></span> <span data-ttu-id="e479e-154">Test-WSMan Cmdlet 會測試 WS-Management (WinRM) 服務是否正在本機或遠端電腦上執行和設定。</span><span class="sxs-lookup"><span data-stu-id="e479e-154">The Test-WSMan cmdlet tests whether the WS-Management (WinRM) service is running and configured on a local or remote computer.</span></span>

- <span data-ttu-id="e479e-155">WSManCredSSP：停用用戶端電腦上的 CredSSP 驗證。</span><span class="sxs-lookup"><span data-stu-id="e479e-155">Disable-WSManCredSSP: Disables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="e479e-156">WSManCredSSP：在用戶端電腦上啟用 CredSSP 驗證。</span><span class="sxs-lookup"><span data-stu-id="e479e-156">Enable-WSManCredSSP: Enables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="e479e-157">WSManCredSSP：取得用戶端電腦的 CredSSP 相關設定。</span><span class="sxs-lookup"><span data-stu-id="e479e-157">Get-WSManCredSSP: Gets the CredSSP-related configuration for a client computer.</span></span>

## <a name="ws-management-specific-cmdlets"></a><span data-ttu-id="e479e-158">WS-MANAGEMENT 專用的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e479e-158">WS-Management-Specific Cmdlets</span></span>

- <span data-ttu-id="e479e-159">New-wsmansessionoption：建立 New-wsmansessionoption 物件，用來做為 WS-Management Cmdlet 的一或多個參數的輸入。</span><span class="sxs-lookup"><span data-stu-id="e479e-159">New-WSManSessionOption: Creates a WSManSessionOption object to use as input to one or more parameters of a WS-Management cmdlet.</span></span>

## <a name="additional-ws-management-information"></a><span data-ttu-id="e479e-160">其他 WS-Management 資訊</span><span class="sxs-lookup"><span data-stu-id="e479e-160">Additional WS-Management Information</span></span>

<span data-ttu-id="e479e-161">如需 WS-MANAGEMENT 的詳細資訊，請參閱 MSDN (Microsoft 開發人員網路) 程式庫中的下列主題。</span><span class="sxs-lookup"><span data-stu-id="e479e-161">For more information about WS-Management, see the following topics in the MSDN (Microsoft Developer Network) library.</span></span>

[<span data-ttu-id="e479e-162">Windows 遠端管理</span><span class="sxs-lookup"><span data-stu-id="e479e-162">Windows Remote Management</span></span>](/windows/win32/winrm/portal)

[<span data-ttu-id="e479e-163">關於 Windows 遠端管理</span><span class="sxs-lookup"><span data-stu-id="e479e-163">About Windows Remote Management</span></span>](/windows/win32/winrm/about-windows-remote-management)

[<span data-ttu-id="e479e-164">Windows 遠端管理的安裝和設定</span><span class="sxs-lookup"><span data-stu-id="e479e-164">Installation and Configuration for Windows Remote Management</span></span>](/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

[<span data-ttu-id="e479e-165">Windows 遠端管理架構</span><span class="sxs-lookup"><span data-stu-id="e479e-165">Windows Remote Management Architecture</span></span>](/windows/win32/winrm/windows-remote-management-architecture)

[<span data-ttu-id="e479e-166">WS-Management 通訊協定</span><span class="sxs-lookup"><span data-stu-id="e479e-166">WS-Management Protocol</span></span>](/windows/win32/winrm/ws-management-protocol)

[<span data-ttu-id="e479e-167">Windows 遠端管理和 WMI</span><span class="sxs-lookup"><span data-stu-id="e479e-167">Windows Remote Management and WMI</span></span>](/windows/win32/winrm/windows-remote-management-and-wmi)

[<span data-ttu-id="e479e-168">資源 URI</span><span class="sxs-lookup"><span data-stu-id="e479e-168">Resource URIs</span></span>](/windows/win32/winrm/resource-uris)

[<span data-ttu-id="e479e-169">遠端硬體管理</span><span class="sxs-lookup"><span data-stu-id="e479e-169">Remote Hardware Management</span></span>](/windows/win32/winrm/remote-hardware-management)

[<span data-ttu-id="e479e-170">事件</span><span class="sxs-lookup"><span data-stu-id="e479e-170">Events</span></span>](/windows/win32/winrm/events)

## <a name="see-also"></a><span data-ttu-id="e479e-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e479e-171">SEE ALSO</span></span>

[<span data-ttu-id="e479e-172">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="e479e-172">Connect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Connect-WSMan)

[<span data-ttu-id="e479e-173">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e479e-173">Disable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Disable-WSManCredSSP)

[<span data-ttu-id="e479e-174">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="e479e-174">Disconnect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Disconnect-WSMan)

[<span data-ttu-id="e479e-175">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e479e-175">Enable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Enable-WSManCredSSP)

[<span data-ttu-id="e479e-176">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e479e-176">Get-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Get-WSManCredSSP)

[<span data-ttu-id="e479e-177">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e479e-177">Get-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Get-WSManInstance)

[<span data-ttu-id="e479e-178">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="e479e-178">Invoke-WSManAction</span></span>](xref:Microsoft.WSMan.Management.Invoke-WSManAction)

[<span data-ttu-id="e479e-179">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e479e-179">New-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.New-WSManInstance)

[<span data-ttu-id="e479e-180">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e479e-180">Remove-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Remove-WSManInstance)

[<span data-ttu-id="e479e-181">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e479e-181">Set-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Set-WSManInstance)

[<span data-ttu-id="e479e-182">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="e479e-182">Set-WSManQuickConfig</span></span>](xref:Microsoft.WSMan.Management.Set-WSManQuickConfig)

[<span data-ttu-id="e479e-183">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="e479e-183">Test-WSMan</span></span>](xref:Microsoft.WSMan.Management.Test-WSMan)
