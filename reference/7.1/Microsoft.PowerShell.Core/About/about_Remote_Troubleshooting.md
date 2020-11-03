---
description: 說明如何針對 PowerShell 中的遠端作業進行疑難排解。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Troubleshooting
ms.openlocfilehash: f19cb90a8671cbe0885af817b0cd8849adc79338
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2020
ms.locfileid: "93208935"
---
# <a name="about-remote-troubleshooting"></a><span data-ttu-id="76224-104">關於遠端疑難排解</span><span class="sxs-lookup"><span data-stu-id="76224-104">About Remote Troubleshooting</span></span>

## <a name="short-description"></a><span data-ttu-id="76224-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="76224-105">Short description</span></span>
<span data-ttu-id="76224-106">說明如何針對 PowerShell 中的遠端作業進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="76224-106">Describes how to troubleshoot remote operations in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="76224-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="76224-107">Long description</span></span>

<span data-ttu-id="76224-108">本節說明當您使用以 WS-Management 技術為基礎的 PowerShell 遠端功能時，可能會遇到的一些問題，並建議這些問題的解決方案。</span><span class="sxs-lookup"><span data-stu-id="76224-108">This section describes some of the problems that you might encounter when using the remoting features of PowerShell that are based on WS-Management technology and it suggests solutions to these problems.</span></span>

<span data-ttu-id="76224-109">使用 PowerShell 遠端處理之前，請參閱 [about_Remote](about_remote.md) 和 [about_Remote_Requirements](about_Remote_Requirements.md) ，以取得設定和基本用途的指引。</span><span class="sxs-lookup"><span data-stu-id="76224-109">Before using PowerShell remoting, see [about_Remote](about_remote.md) and [about_Remote_Requirements](about_Remote_Requirements.md) for guidance on configuration and basic use.</span></span> <span data-ttu-id="76224-110">此外，每個遠端 Cmdlet 的說明主題（特別是參數描述）都有實用的資訊，其設計目的是要協助您避免問題。</span><span class="sxs-lookup"><span data-stu-id="76224-110">Also, the Help topics for each of the remoting cmdlets, particularly the parameter descriptions, have useful information that is designed to help you avoid problems.</span></span>

> [!NOTE]
> <span data-ttu-id="76224-111">若要在 WSMan：磁片磁碟機中查看或變更本機電腦的設定，包括會話設定、受信任的主機、埠或接聽程式的變更，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="76224-111">To view or change settings for the local computer in the WSMan: drive, including changes to the session configurations, trusted hosts, ports, or listeners, start PowerShell with the **Run as administrator** option.</span></span>

## <a name="troubleshooting-permission-and-authentication-issues"></a><span data-ttu-id="76224-112">針對許可權和驗證問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="76224-112">Troubleshooting permission and authentication issues</span></span>

<span data-ttu-id="76224-113">本節討論與使用者和電腦許可權和遠端處理需求相關的遠端處理問題。</span><span class="sxs-lookup"><span data-stu-id="76224-113">This section discusses remoting problems that are related to user and computer permissions and remoting requirements.</span></span>

### <a name="how-to-run-as-administrator"></a><span data-ttu-id="76224-114">如何以系統管理員身分執行</span><span class="sxs-lookup"><span data-stu-id="76224-114">How to run as administrator</span></span>

```
ERROR: Access is denied. You need to run this cmdlet from an elevated
process.
```

<span data-ttu-id="76224-115">若要在本機電腦上啟動遠端會話，或在 WSMan：磁片磁碟機中查看或變更本機電腦的設定，包括會話設定、受信任的主機、埠或接聽程式的變更，請使用 [以 **系統管理員身分執行** ] 選項開始 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="76224-115">To start a remote session on the local computer, or to view or change settings for the local computer in the WSMan: drive, including changes to the session configurations, trusted hosts, ports, or listeners, start Windows PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="76224-116">若要使用 [以 **系統管理員身分執行** ] 選項開始 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="76224-116">To start Windows PowerShell with the **Run as administrator** option:</span></span>

- <span data-ttu-id="76224-117">以滑鼠右鍵按一下 Windows PowerShell (或 Windows PowerShell ISE) 圖示，然後按一下 [以 **系統管理員身分執行** ]。</span><span class="sxs-lookup"><span data-stu-id="76224-117">Right-click a Windows PowerShell (or Windows PowerShell ISE) icon and then click **Run as administrator**.</span></span>

  <span data-ttu-id="76224-118">使用 Windows 7 和 Windows Server 2008 R2 中的 [以 **系統管理員身分執行** ] 選項開始 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="76224-118">To start Windows PowerShell with the **Run as administrator** option in Windows 7 and Windows Server 2008 R2.</span></span>

- <span data-ttu-id="76224-119">在 Windows 工作列中，以滑鼠右鍵按一下 Windows PowerShell 圖示，然後按一下 [以 **系統管理員身分執行** ]。</span><span class="sxs-lookup"><span data-stu-id="76224-119">In the Windows taskbar, right-click the Windows PowerShell icon, and then click **Run as administrator**.</span></span>

  <span data-ttu-id="76224-120">在 Windows Server 2008 R2 中，預設會將 Windows PowerShell 圖示釘選到工作列。</span><span class="sxs-lookup"><span data-stu-id="76224-120">In Windows Server 2008 R2, the Windows PowerShell icon is pinned to the taskbar by default.</span></span>

### <a name="how-to-enable-remoting"></a><span data-ttu-id="76224-121">如何啟用遠端處理</span><span class="sxs-lookup"><span data-stu-id="76224-121">How to enable remoting</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to
listen for requests on the correct port and HTTP URL.
```

<span data-ttu-id="76224-122">不需要進行任何設定，就能讓電腦傳送遠端命令。</span><span class="sxs-lookup"><span data-stu-id="76224-122">No configuration is required to enable a computer to send remote commands.</span></span>
<span data-ttu-id="76224-123">不過，若要接收遠端命令，電腦上必須啟用 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="76224-123">However, to receive remote commands, PowerShell remoting must be enabled on the computer.</span></span> <span data-ttu-id="76224-124">啟用包括啟動 WinRM 服務、將 WinRM 服務的啟動類型設定為 [自動]、建立 HTTP 和 HTTPS 連接的接聽程式，以及建立預設的會話設定。</span><span class="sxs-lookup"><span data-stu-id="76224-124">Enabling includes starting the WinRM service, setting the startup type for the WinRM service to Automatic, creating listeners for HTTP and HTTPS connections, and creating default session configurations.</span></span>

<span data-ttu-id="76224-125">預設會在 Windows Server 2012 和更新版本的 Windows Server 上啟用 Windows PowerShell 遠端處理。</span><span class="sxs-lookup"><span data-stu-id="76224-125">Windows PowerShell remoting is enabled on Windows Server 2012 and newer releases of Windows Server by default.</span></span> <span data-ttu-id="76224-126">在所有其他系統上，執行 `Enable-PSRemoting` Cmdlet 以啟用遠端功能。</span><span class="sxs-lookup"><span data-stu-id="76224-126">On all other systems, run the `Enable-PSRemoting` cmdlet to enable remoting.</span></span> <span data-ttu-id="76224-127">`Enable-PSRemoting`如果停用遠端功能，您也可以執行 Cmdlet，在 Windows server 2012 和更新版本的 Windows server 上重新啟用遠端功能。</span><span class="sxs-lookup"><span data-stu-id="76224-127">You can also run the `Enable-PSRemoting` cmdlet to re-enable remoting on Windows Server 2012 and newer releases of Windows Server if remoting is disabled.</span></span>

<span data-ttu-id="76224-128">若要設定電腦接收遠端命令，請使用 `Enable-PSRemoting` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="76224-128">To configure a computer to receive remote commands, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="76224-129">下列命令會啟用所有必要的遠端設定、啟用會話設定，然後重新開機 WinRM 服務，讓變更生效。</span><span class="sxs-lookup"><span data-stu-id="76224-129">The following command enables all required remote settings, enables the session configurations, and restarts the WinRM service to make the changes effective.</span></span>

`Enable-PSRemoting`

<span data-ttu-id="76224-130">若要隱藏所有使用者提示，請輸入：</span><span class="sxs-lookup"><span data-stu-id="76224-130">To suppress all user prompts, type:</span></span>

`Enable-PSRemoting -Force`

<span data-ttu-id="76224-131">如需詳細資訊，請參閱 [啟用->enable-psremoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting)。</span><span class="sxs-lookup"><span data-stu-id="76224-131">For more information, see [Enable-PSRemoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting).</span></span>

### <a name="how-to-enable-remoting-in-an-enterprise"></a><span data-ttu-id="76224-132">如何在企業中啟用遠端功能</span><span class="sxs-lookup"><span data-stu-id="76224-132">How to enable remoting in an enterprise</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="76224-133">若要讓單一電腦接收遠端 PowerShell 命令並接受連接，請使用 `Enable-PSRemoting` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="76224-133">To enable a single computer to receive remote PowerShell commands and accept connections, use the `Enable-PSRemoting` cmdlet.</span></span>

<span data-ttu-id="76224-134">若要啟用企業中多部電腦的遠端功能，您可以使用下列調整的選項。</span><span class="sxs-lookup"><span data-stu-id="76224-134">To enable remoting for multiple computers in an enterprise, you can use the following scaled options.</span></span>

- <span data-ttu-id="76224-135">若要設定遠端接聽程式，請啟用 [ **允許自動** 設定接聽程式] 群組原則。</span><span class="sxs-lookup"><span data-stu-id="76224-135">To configure listeners for remoting, enable the **Allow automatic configuration of listeners** group policy.</span></span>

- <span data-ttu-id="76224-136">若要在多部電腦上將 Windows 遠端管理 (WinRM) 的啟動類型設定為 [自動]，請使用 `Set-Service` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="76224-136">To set the startup type of the Windows Remote Management (WinRM) to Automatic on multiple computers, use the `Set-Service` cmdlet.</span></span>

- <span data-ttu-id="76224-137">若要啟用防火牆例外，請使用 [ **Windows 防火牆：允許本機埠例外** ] 群組原則。</span><span class="sxs-lookup"><span data-stu-id="76224-137">To enable a firewall exception, use the **Windows Firewall: Allow Local Port Exceptions** group policy.</span></span>

### <a name="how-to-enable-listeners-by-using-a-group-policy"></a><span data-ttu-id="76224-138">如何使用群組原則啟用接聽程式</span><span class="sxs-lookup"><span data-stu-id="76224-138">How to enable listeners by using a group policy</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="76224-139">若要為網域中的所有電腦設定接聽程式，請在下列群組原則路徑中啟用 [ **允許自動** 設定接聽程式] 原則：</span><span class="sxs-lookup"><span data-stu-id="76224-139">To configure the listeners for all computers in a domain, enable the **Allow automatic configuration of listeners** policy in the following Group Policy path:</span></span>

```
Computer Configuration\Administrative Templates\Windows Components
    \Windows Remote Management (WinRM)\WinRM service
```

<span data-ttu-id="76224-140">啟用原則，並指定 IPv4 和 IPv6 篩選器。</span><span class="sxs-lookup"><span data-stu-id="76224-140">Enable the policy and specify the IPv4 and IPv6 filters.</span></span> <span data-ttu-id="76224-141">允許 (`*`) 的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="76224-141">Wildcards (`*`) are permitted.</span></span>

### <a name="how-to-enable-remoting-on-public-networks"></a><span data-ttu-id="76224-142">如何在公用網路上啟用遠端功能</span><span class="sxs-lookup"><span data-stu-id="76224-142">How to enable remoting on public networks</span></span>

```
ERROR:  Unable to check the status of the firewall
```

<span data-ttu-id="76224-143">`Enable-PSRemoting`當局域網路是公用的，而且命令中未使用 **SkipNetworkProfileCheck** 參數時，此 Cmdlet 會傳回這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="76224-143">The `Enable-PSRemoting` cmdlet returns this error when the local network is public and the **SkipNetworkProfileCheck** parameter is not used in the command.</span></span>

<span data-ttu-id="76224-144">在伺服器版本的 Windows 上， `Enable-PSRemoting` 所有網路位置類型都會成功。</span><span class="sxs-lookup"><span data-stu-id="76224-144">On server versions of Windows, `Enable-PSRemoting` succeeds on all network location types.</span></span> <span data-ttu-id="76224-145">它會建立防火牆規則，以允許遠端存取私用和網域 ( "Home" 和 "Work" ) 網路。</span><span class="sxs-lookup"><span data-stu-id="76224-145">It creates firewall rules that allow remote access to private and domain ("Home" and "Work") networks.</span></span> <span data-ttu-id="76224-146">針對公用網路，它會建立防火牆規則，以允許從相同的本機子網進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="76224-146">For public networks, it creates firewall rules that allows remote access from the same local subnet.</span></span>

<span data-ttu-id="76224-147">在用戶端版本的 Windows 上， `Enable-PSRemoting` 在私用和網域網路上會成功。</span><span class="sxs-lookup"><span data-stu-id="76224-147">On client versions of Windows, `Enable-PSRemoting` succeeds on private and domain networks.</span></span> <span data-ttu-id="76224-148">依預設，它會在公用網路上失敗，但如果您使用 **SkipNetworkProfileCheck** 參數，則會 `Enable-PSRemoting` 成功，並建立允許來自相同本機子網之流量的防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="76224-148">By default, it fails on public networks, but if you use the **SkipNetworkProfileCheck** parameter, `Enable-PSRemoting` succeeds and creates a firewall rule that allows traffic from the same local subnet.</span></span>

<span data-ttu-id="76224-149">若要移除公用網路上的本機子網限制，並允許從任何位置進行遠端存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="76224-149">To remove the local subnet restriction on public networks and allow remote access from any location, run the following command:</span></span>

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

<span data-ttu-id="76224-150">此 `Set-NetFirewallRule` Cmdlet 是由 NetSecurity 模組匯出。</span><span class="sxs-lookup"><span data-stu-id="76224-150">The `Set-NetFirewallRule` cmdlet is exported by the NetSecurity module.</span></span>

> [!NOTE]
> <span data-ttu-id="76224-151">在 Windows PowerShell 2.0 中，在執行 Windows server 版本的電腦上， `Enable-PSRemoting` 會建立防火牆規則，允許在私人、網域及公用網路上進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="76224-151">In Windows PowerShell 2.0, on computers running server versions of Windows, `Enable-PSRemoting` creates firewall rules that allow remote access on private, domain and public networks.</span></span> <span data-ttu-id="76224-152">在執行 Windows 用戶端版本的電腦上， `Enable-PSRemoting` 會建立只允許在私用和網域網路上進行遠端存取的防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="76224-152">On computers running client versions of Windows, `Enable-PSRemoting` creates firewall rules that allow remote access only on private and domain networks.</span></span>

### <a name="how-to-enable-a-firewall-exception-by-using-a-group-policy"></a><span data-ttu-id="76224-153">如何使用群組原則啟用防火牆例外</span><span class="sxs-lookup"><span data-stu-id="76224-153">How to enable a firewall exception by using a group policy</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="76224-154">若要在網域中的所有電腦上啟用防火牆例外，請啟用下列群組原則路徑中的 [ **Windows 防火牆：允許本機埠例外** ] 原則：</span><span class="sxs-lookup"><span data-stu-id="76224-154">To enable a firewall exception for in all computers in a domain, enable the **Windows Firewall: Allow local port exceptions** policy in the following Group Policy path:</span></span>

```
Computer Configuration\Administrative Templates\Network
    \Network Connections\Windows Firewall\Domain Profile
```

<span data-ttu-id="76224-155">這項原則可讓電腦上的 Administrators 群組成員使用 **主控台** 中的 **Windows 防火牆** ，以建立 Windows 遠端管理服務的防火牆例外。</span><span class="sxs-lookup"><span data-stu-id="76224-155">This policy allows members of the Administrators group on the computer to use **Windows Firewall** in **Control Panel** to create a firewall exception for the Windows Remote Management service.</span></span>

<span data-ttu-id="76224-156">如果原則設定不正確，您可能會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="76224-156">If the policy configuration is incorrect you may receive the following error:</span></span>

```
The client cannot connect to the destination specified in the request. Verify
that the service on the destination is running and is accepting requests.
```

<span data-ttu-id="76224-157">原則中的設定錯誤會導致 **ListeningOn** 屬性的值為空值。</span><span class="sxs-lookup"><span data-stu-id="76224-157">A configuration error in the policy results in an empty value for the **ListeningOn** property.</span></span> <span data-ttu-id="76224-158">使用下列命令來檢查值。</span><span class="sxs-lookup"><span data-stu-id="76224-158">Use the following command to check the value.</span></span>

```powershell
PS> Get-WSManInstance winrm/config/listener -Enumerate

cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
Source                : GPO
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 5985
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {}
```

### <a name="how-to-set-the-startup-type-of-the-winrm-service"></a><span data-ttu-id="76224-159">如何設定 WinRM 服務的啟動類型</span><span class="sxs-lookup"><span data-stu-id="76224-159">How to set the startup type of the WinRM service</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="76224-160">PowerShell 遠端處理取決於 Windows 遠端管理 (WinRM) 服務。</span><span class="sxs-lookup"><span data-stu-id="76224-160">PowerShell remoting depends upon the Windows Remote Management (WinRM) service.</span></span>
<span data-ttu-id="76224-161">服務必須正在執行，才能支援遠端命令。</span><span class="sxs-lookup"><span data-stu-id="76224-161">The service must be running to support remote commands.</span></span>

<span data-ttu-id="76224-162">在伺服器版本的 Windows 上，Windows 遠端管理 (WinRM) 服務的啟動類型為自動。</span><span class="sxs-lookup"><span data-stu-id="76224-162">On server versions of Windows, the startup type of the Windows Remote Management (WinRM) service is Automatic.</span></span>

<span data-ttu-id="76224-163">不過，在用戶端版本的 Windows 上，預設會停用 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="76224-163">However, on client versions of Windows, the WinRM service is disabled by default.</span></span>

<span data-ttu-id="76224-164">若要在遠端電腦上設定服務的啟動類型，請使用 `Set-Service` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="76224-164">To set the startup type of a service on a remote computer, use the `Set-Service` cmdlet.</span></span>

<span data-ttu-id="76224-165">若要在多部電腦上執行命令，您可以建立電腦名稱稱的文字檔或 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="76224-165">To run the command on multiple computers, you can create a text file or CSV file of the computer names.</span></span>

<span data-ttu-id="76224-166">例如，下列命令會取得檔案中的電腦名稱稱清單 `Servers.txt` ，然後將所有電腦上的 WinRM 服務啟動類型設定為 [ **自動** ]。</span><span class="sxs-lookup"><span data-stu-id="76224-166">For example, the following commands get a list of computer names from the `Servers.txt` file and then sets the startup type of the WinRM service on all of the computers to **Automatic**.</span></span>

```powershell
$servers = Get-Content servers.txt
Set-Service WinRM -ComputerName $servers -startuptype Automatic
```

<span data-ttu-id="76224-167">若要查看結果，請使用 `Get-WMIObject` Cmdlet 搭配 **Win32_Service** 物件。</span><span class="sxs-lookup"><span data-stu-id="76224-167">To see the results use the `Get-WMIObject` cmdlet with the **Win32_Service** object.</span></span> <span data-ttu-id="76224-168">如需詳細資訊，請參閱 [設定服務](xref:Microsoft.PowerShell.Management.Set-Service)。</span><span class="sxs-lookup"><span data-stu-id="76224-168">For more information, see [Set-Service](xref:Microsoft.PowerShell.Management.Set-Service).</span></span>

### <a name="how-to-recreate-the-default-session-configurations"></a><span data-ttu-id="76224-169">如何重新建立預設會話設定</span><span class="sxs-lookup"><span data-stu-id="76224-169">How to recreate the default session configurations</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="76224-170">若要連接到本機電腦並從遠端執行命令，本機電腦必須包含遠端命令的會話設定。</span><span class="sxs-lookup"><span data-stu-id="76224-170">To connect to the local computer and run commands remotely, the local computer must include session configurations for remote commands.</span></span>

<span data-ttu-id="76224-171">當您使用時 `Enable-PSRemoting` ，它會在本機電腦上建立預設的會話設定。</span><span class="sxs-lookup"><span data-stu-id="76224-171">When you use `Enable-PSRemoting`, it creates default session configurations on the local computer.</span></span> <span data-ttu-id="76224-172">遠端使用者只要遠端命令未包含 **ConfigurationName** 參數，就會使用這些會話設定。</span><span class="sxs-lookup"><span data-stu-id="76224-172">Remote users use these session configurations whenever a remote command does not include the **ConfigurationName** parameter.</span></span>

<span data-ttu-id="76224-173">如果電腦上的預設設定為取消註冊或刪除，請使用 `Enable-PSRemoting` Cmdlet 重新建立它們。</span><span class="sxs-lookup"><span data-stu-id="76224-173">If the default configurations on a computer are unregistered or deleted, use the `Enable-PSRemoting` cmdlet to recreate them.</span></span> <span data-ttu-id="76224-174">您可以重複使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="76224-174">You can use this cmdlet repeatedly.</span></span> <span data-ttu-id="76224-175">如果已設定功能，則不會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="76224-175">It does not generate errors if a feature is already configured.</span></span>

<span data-ttu-id="76224-176">如果您變更預設會話設定，並想要還原原始的預設會話設定，請使用 `Unregister-PSSessionConfiguration` Cmdlet 來刪除已變更的會話設定，然後使用指令程式 `Enable-PSRemoting` 來還原它們。</span><span class="sxs-lookup"><span data-stu-id="76224-176">If you change the default session configurations and want to restore the original default session configurations, use the `Unregister-PSSessionConfiguration` cmdlet to delete the changed session configurations and then use the `Enable-PSRemoting` cmdlet to restore them.</span></span>
<span data-ttu-id="76224-177">`Enable-PSRemoting` 不會變更現有的會話設定。</span><span class="sxs-lookup"><span data-stu-id="76224-177">`Enable-PSRemoting` does not change existing session configurations.</span></span>

> [!NOTE]
> <span data-ttu-id="76224-178">`Enable-PSRemoting`還原預設會話設定時，不會為設定建立明確的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="76224-178">When `Enable-PSRemoting` restores the default session configuration, it does not create explicit security descriptors for the configurations.</span></span> <span data-ttu-id="76224-179">相反地，設定會繼承 RootSDDL 的安全描述項（預設為安全）。</span><span class="sxs-lookup"><span data-stu-id="76224-179">Instead, the configurations inherit the security descriptor of the RootSDDL, which is secure by default.</span></span>

<span data-ttu-id="76224-180">若要查看 RootSDDL 安全描述項，請輸入：</span><span class="sxs-lookup"><span data-stu-id="76224-180">To see the RootSDDL security descriptor, type:</span></span>

```powershell
Get-Item wsman:\localhost\Service\RootSDDL
```

<span data-ttu-id="76224-181">若要變更 RootSDDL，請使用 `Set-Item` WSMan：磁片磁碟機中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="76224-181">To change the RootSDDL, use the `Set-Item` cmdlet in the WSMan: drive.</span></span> <span data-ttu-id="76224-182">若要變更會話設定的安全描述項，請使用 `Set-PSSessionConfiguration` Cmdlet 搭配 **SecurityDescriptorSDDL** 或 **ShowSecurityDescriptorUI** 參數。</span><span class="sxs-lookup"><span data-stu-id="76224-182">To change the security descriptor of a session configuration, use the `Set-PSSessionConfiguration` cmdlet with the **SecurityDescriptorSDDL** or **ShowSecurityDescriptorUI** parameters.</span></span>

<span data-ttu-id="76224-183">如需 WSMan：磁片磁碟機的詳細資訊，請參閱 WSMan 提供者的說明主題 ( "Get-help WSMan" ) 。</span><span class="sxs-lookup"><span data-stu-id="76224-183">For more information about the WSMan: drive, see the Help topic for the WSMan provider ("Get-Help wsman").</span></span>

### <a name="how-to-provide-administrator-credentials"></a><span data-ttu-id="76224-184">如何提供系統管理員認證</span><span class="sxs-lookup"><span data-stu-id="76224-184">How to provide administrator credentials</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="76224-185">若要在遠端電腦上建立 PSSession 或執行命令，則目前的使用者必須是遠端電腦上 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="76224-185">To create a PSSession or run commands on a remote computer, by default, the current user must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="76224-186">即使目前的使用者登入屬於 Administrators 群組成員的帳戶，有時還是需要認證。</span><span class="sxs-lookup"><span data-stu-id="76224-186">Credentials are sometimes required even when the current user is logged on to an account that is a member of the Administrators group.</span></span>

<span data-ttu-id="76224-187">如果目前的使用者是遠端電腦上 Administrators 群組的成員，或者可以提供 Administrators 群組成員的認證，請使用的 **Credential** 參數 `New-PSSession` `Enter-PSSession` 或 `Invoke-Command` Cmdlet 從遠端連線。</span><span class="sxs-lookup"><span data-stu-id="76224-187">If the current user is a member of the Administrators group on the remote computer, or can provide the credentials of a member of the Administrators group, use the **Credential** parameter of the `New-PSSession`, `Enter-PSSession` or `Invoke-Command` cmdlets to connect remotely.</span></span>

<span data-ttu-id="76224-188">例如，下列命令會提供系統管理員的認證。</span><span class="sxs-lookup"><span data-stu-id="76224-188">For example, the following command provides the credentials of an Administrator.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\Admin01
```

<span data-ttu-id="76224-189">如需 **Credential** 參數的詳細資訊，請參閱 [新的-pssession](xref:Microsoft.PowerShell.Core.New-PSSession)、 [輸入-pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession) 或 [Invoke 命令](xref:Microsoft.PowerShell.Core.Invoke-Command)。</span><span class="sxs-lookup"><span data-stu-id="76224-189">For more information about the **Credential** parameter, see [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) or [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command).</span></span>

### <a name="how-to-enable-remoting-for-non-administrative-users"></a><span data-ttu-id="76224-190">如何啟用非系統管理使用者的遠端處理</span><span class="sxs-lookup"><span data-stu-id="76224-190">How to enable remoting for non-administrative users</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="76224-191">若要在遠端電腦上建立 PSSession 或執行命令，使用者必須有許可權可以使用遠端電腦上的會話設定。</span><span class="sxs-lookup"><span data-stu-id="76224-191">To establish a PSSession or run a command on a remote computer, the user must have permission to use the session configurations on the remote computer.</span></span>

<span data-ttu-id="76224-192">依預設，只有電腦上 Administrators 群組的成員才有使用預設會話設定的許可權。</span><span class="sxs-lookup"><span data-stu-id="76224-192">By default, only members of the Administrators group on a computer have permission to use the default session configurations.</span></span> <span data-ttu-id="76224-193">因此，只有 Administrators 群組的成員可以從遠端連線到電腦。</span><span class="sxs-lookup"><span data-stu-id="76224-193">Therefore, only members of the Administrators group can connect to the computer remotely.</span></span>

<span data-ttu-id="76224-194">若要允許其他使用者連接到本機電腦，請將本機電腦上預設會話設定的 [執行] 許可權授與使用者。</span><span class="sxs-lookup"><span data-stu-id="76224-194">To allow other users to connect to the local computer, give the user Execute permissions to the default session configurations on the local computer.</span></span>

<span data-ttu-id="76224-195">下列命令會開啟屬性工作表，讓您在本機電腦上變更預設的 Microsoft PowerShell 會話設定的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="76224-195">The following command opens a property sheet that lets you change the security descriptor of the default Microsoft.PowerShell session configuration on the local computer.</span></span>

```powershell
Set-PSSessionConfiguration Microsoft.PowerShell -ShowSecurityDescriptorUI
```

<span data-ttu-id="76224-196">如需詳細資訊，請參閱 [about_Session_Configurations](about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="76224-196">For more information, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

### <a name="how-to-enable-remoting-for-administrators-in-other-domains"></a><span data-ttu-id="76224-197">如何為其他網域中的系統管理員啟用遠端處理</span><span class="sxs-lookup"><span data-stu-id="76224-197">How to enable remoting for administrators in other domains</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="76224-198">當另一個網域中的使用者是本機電腦上 Administrators 群組的成員時，該使用者就無法使用系統管理員許可權從遠端連線到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="76224-198">When a user in another domain is a member of the Administrators group on the local computer, the user cannot connect to the local computer remotely with Administrator privileges.</span></span> <span data-ttu-id="76224-199">根據預設，來自其他網域的遠端連線只會以標準使用者權限權杖執行。</span><span class="sxs-lookup"><span data-stu-id="76224-199">By default, remote connections from other domains run with only standard user privilege tokens.</span></span>

<span data-ttu-id="76224-200">不過，您可以使用 **LocalAccountTokenFilterPolicy** 登錄專案來變更預設行為，並允許身為 Administrators 群組成員的遠端使用者以系統管理員許可權執行。</span><span class="sxs-lookup"><span data-stu-id="76224-200">However, you can use the **LocalAccountTokenFilterPolicy** registry entry to change the default behavior and allow remote users who are members of the Administrators group to run with Administrator privileges.</span></span>

> [!CAUTION]
> <span data-ttu-id="76224-201">**LocalAccountTokenFilterPolicy** 專案會針對所有受影響電腦的所有使用者，停用 (UAC) 遠端限制的使用者帳戶控制。</span><span class="sxs-lookup"><span data-stu-id="76224-201">The **LocalAccountTokenFilterPolicy** entry disables user account control (UAC) remote restrictions for all users of all affected computers.</span></span> <span data-ttu-id="76224-202">變更原則之前，請先仔細考慮這項設定的含意。</span><span class="sxs-lookup"><span data-stu-id="76224-202">Consider the implications of this setting carefully before changing the policy.</span></span>

<span data-ttu-id="76224-203">若要變更原則，請使用下列命令將 **LocalAccountTokenFilterPolicy** 登錄專案的值設定為1。</span><span class="sxs-lookup"><span data-stu-id="76224-203">To change the policy, use the following command to set the value of the **LocalAccountTokenFilterPolicy** registry entry to 1.</span></span>

```powershell
New-ItemProperty -Name LocalAccountTokenFilterPolicy `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System `
  -PropertyType DWord -Value 1
```

### <a name="how-to-use-an-ip-address-in-a-remote-command"></a><span data-ttu-id="76224-204">如何在遠端命令中使用 ip 位址</span><span class="sxs-lookup"><span data-stu-id="76224-204">How to use an ip address in a remote command</span></span>

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

<span data-ttu-id="76224-205">的 **ComputerName** 參數 `New-PSSession` `Enter-PSSession` 和 `Invoke-Command` Cmdlet 會接受 IP 位址做為有效的值。</span><span class="sxs-lookup"><span data-stu-id="76224-205">The **ComputerName** parameter of the `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets accepts an IP address as a valid value.</span></span> <span data-ttu-id="76224-206">不過，因為 Kerberos 驗證不支援 IP 位址，所以每當您指定 IP 位址時，預設都會使用 NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="76224-206">However, because Kerberos authentication does not support IP addresses, NTLM authentication is used by default whenever you specify an IP address.</span></span>

<span data-ttu-id="76224-207">使用 NTLM 驗證時，需要下列程式進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="76224-207">When using NTLM authentication, the following procedure is required for remoting.</span></span>

1. <span data-ttu-id="76224-208">設定電腦的 HTTPS 傳輸，或將遠端電腦的 IP 位址新增至本機電腦上的 TrustedHosts 清單。</span><span class="sxs-lookup"><span data-stu-id="76224-208">Configure the computer for HTTPS transport or add the IP addresses of the remote computers to the TrustedHosts list on the local computer.</span></span>

1. <span data-ttu-id="76224-209">在所有遠端命令中使用 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="76224-209">Use the **Credential** parameter in all remote commands.</span></span>

   <span data-ttu-id="76224-210">即使您要提交目前使用者的認證，也需要此項。</span><span class="sxs-lookup"><span data-stu-id="76224-210">This is required even when you are submitting the credentials of the current user.</span></span>

### <a name="how-to-connect-remotely-from-a-workgroup-based-computer"></a><span data-ttu-id="76224-211">如何從工作組型電腦遠端連線</span><span class="sxs-lookup"><span data-stu-id="76224-211">How to connect remotely from a workgroup-based computer</span></span>

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

<span data-ttu-id="76224-212">當本機電腦不在網域中時，需要下列程式進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="76224-212">When the local computer is not in a domain, the following procedure is required for remoting.</span></span>

1. <span data-ttu-id="76224-213">設定電腦的 HTTPS 傳輸，或將遠端電腦的名稱新增至本機電腦上的 TrustedHosts 清單。</span><span class="sxs-lookup"><span data-stu-id="76224-213">Configure the computer for HTTPS transport or add the names of the remote computers to the TrustedHosts list on the local computer.</span></span>

1. <span data-ttu-id="76224-214">確認工作組型電腦上已設定密碼。</span><span class="sxs-lookup"><span data-stu-id="76224-214">Verify that a password is set on the workgroup-based computer.</span></span> <span data-ttu-id="76224-215">如果未設定密碼或密碼值是空的，您就無法執行遠端命令。</span><span class="sxs-lookup"><span data-stu-id="76224-215">If a password is not set or the password value is empty, you cannot run remote commands.</span></span>

   <span data-ttu-id="76224-216">若要設定使用者帳戶的密碼，請使用主控台中的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="76224-216">To set password for your user account, use User Accounts in Control Panel.</span></span>

1. <span data-ttu-id="76224-217">在所有遠端命令中使用 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="76224-217">Use the **Credential** parameter in all remote commands.</span></span>

   <span data-ttu-id="76224-218">即使您要提交目前使用者的認證，也需要此項。</span><span class="sxs-lookup"><span data-stu-id="76224-218">This is required even when you are submitting the credentials of the current user.</span></span>

### <a name="how-to-add-a-computer-to-the-trusted-hosts-list"></a><span data-ttu-id="76224-219">如何將電腦新增到信任的主機清單</span><span class="sxs-lookup"><span data-stu-id="76224-219">How to add a computer to the trusted hosts list</span></span>

<span data-ttu-id="76224-220">TrustedHosts 專案可以包含以逗號分隔的電腦名稱稱、IP 位址和完整功能變數名稱清單。</span><span class="sxs-lookup"><span data-stu-id="76224-220">The TrustedHosts item can contain a comma-separated list of computer names, IP addresses, and fully-qualified domain names.</span></span> <span data-ttu-id="76224-221">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="76224-221">Wildcards are permitted.</span></span>

<span data-ttu-id="76224-222">若要查看或變更信任的主機清單，請使用 WSMan：磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="76224-222">To view or change the trusted host list, use the WSMan: drive.</span></span> <span data-ttu-id="76224-223">TrustedHost 專案位於 `WSMan:\localhost\Client` 節點中。</span><span class="sxs-lookup"><span data-stu-id="76224-223">The TrustedHost item is in the `WSMan:\localhost\Client` node.</span></span>

<span data-ttu-id="76224-224">只有電腦上 Administrators 群組的成員有權變更電腦上受信任的主機清單。</span><span class="sxs-lookup"><span data-stu-id="76224-224">Only members of the Administrators group on the computer have permission to change the list of trusted hosts on the computer.</span></span>

<span data-ttu-id="76224-225">注意：您為 TrustedHosts 專案設定的值會影響電腦的所有使用者。</span><span class="sxs-lookup"><span data-stu-id="76224-225">Caution: The value that you set for the TrustedHosts item affects all users of the computer.</span></span>

<span data-ttu-id="76224-226">若要查看信任的主機清單，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="76224-226">To view the list of trusted hosts, use the following command:</span></span>

```powershell
Get-Item wsman:\localhost\Client\TrustedHosts
```

<span data-ttu-id="76224-227">您也可以使用 `Set-Location` Cmdlet (alias = cd) ，以從 WSMan：磁片磁碟機流覽至該位置。</span><span class="sxs-lookup"><span data-stu-id="76224-227">You can also use the `Set-Location` cmdlet (alias = cd) to navigate though the WSMan: drive to the location.</span></span> <span data-ttu-id="76224-228">例如：</span><span class="sxs-lookup"><span data-stu-id="76224-228">For example:</span></span>

```powershell
cd WSMan:\localhost\Client; dir
```

<span data-ttu-id="76224-229">若要將所有電腦新增到信任的主機清單，請使用下列命令，其值為 \* (ComputerName 中的所有) </span><span class="sxs-lookup"><span data-stu-id="76224-229">To add all computers to the list of trusted hosts, use the following command, which places a value of \* (all) in the ComputerName</span></span>

```powershell
Set-Item wsman:localhost\client\trustedhosts -Value *
```

<span data-ttu-id="76224-230">您也可以使用萬用字元 () 將 `*` 特定網域中的所有電腦新增到信任的主機清單。</span><span class="sxs-lookup"><span data-stu-id="76224-230">You can also use a wildcard character (`*`) to add all computers in a particular domain to the list of trusted hosts.</span></span> <span data-ttu-id="76224-231">例如，下列命令會將 Fabrikam 網域中的所有電腦新增到信任的主機清單中。</span><span class="sxs-lookup"><span data-stu-id="76224-231">For example, the following command adds all of the computers in the Fabrikam domain to the list of trusted hosts.</span></span>

```powershell
Set-Item wsman:localhost\client\trustedhosts *.fabrikam.com
```

<span data-ttu-id="76224-232">若要將特定電腦的名稱新增至信任主機清單，請使用下列命令格式：</span><span class="sxs-lookup"><span data-stu-id="76224-232">To add the names of particular computers to the list of trusted hosts, use the following command format:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <ComputerName>
```

<span data-ttu-id="76224-233">其中每個值都 `<ComputerName>` 必須具有下列格式：</span><span class="sxs-lookup"><span data-stu-id="76224-233">where each value `<ComputerName>` must have the following format:</span></span>

```
<Computer>.<Domain>.<Company>.<top-level-domain>
```

<span data-ttu-id="76224-234">例如：</span><span class="sxs-lookup"><span data-stu-id="76224-234">For example:</span></span>

```powershell
$server = 'Server01.Domain01.Fabrikam.com'
Set-Item wsman:\localhost\Client\TrustedHosts -Value $server
```

<span data-ttu-id="76224-235">若要將電腦名稱稱新增至現有的受信任主機清單，請先將目前的值儲存在變數中，然後將值設定為包含目前值和新值的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="76224-235">To add a computer name to an existing list of trusted hosts, first save the current value in a variable, and then set the value to a comma-separated list that includes the current and new values.</span></span>

<span data-ttu-id="76224-236">例如，若要將 Server01 電腦新增至現有的受信任主機清單，請使用下列命令</span><span class="sxs-lookup"><span data-stu-id="76224-236">For example, to add the Server01 computer to an existing list of trusted hosts, use the following command</span></span>

```powershell
$curValue = (Get-Item wsman:\localhost\Client\TrustedHosts).value

Set-Item wsman:\localhost\Client\TrustedHosts -Value `
  "$curValue, Server01.Domain01.Fabrikam.com"
```

<span data-ttu-id="76224-237">若要將特定電腦的 IP 位址新增至信任主機清單，請使用下列命令格式：</span><span class="sxs-lookup"><span data-stu-id="76224-237">To add the IP addresses of particular computers to the list of trusted hosts, use the following command format:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <IP Address>
```

<span data-ttu-id="76224-238">例如：</span><span class="sxs-lookup"><span data-stu-id="76224-238">For example:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value 172.16.0.0
```

<span data-ttu-id="76224-239">若要將電腦新增至遠端電腦的 TrustedHosts 清單，請使用 `Connect-WSMan` Cmdlet 將遠端電腦的節點新增到本機電腦上的 WSMan：磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="76224-239">To add a computer to the TrustedHosts list of a remote computer, use the `Connect-WSMan` cmdlet to add a node for the remote computer to the WSMan: drive on the local computer.</span></span> <span data-ttu-id="76224-240">然後使用 `Set-Item` 命令來新增電腦。</span><span class="sxs-lookup"><span data-stu-id="76224-240">Then use a `Set-Item` command to add the computer.</span></span>

<span data-ttu-id="76224-241">如需有關 Cmdlet 的詳細資訊 `Connect-WSMan` ，請參閱 [連接-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)。</span><span class="sxs-lookup"><span data-stu-id="76224-241">For more information about the `Connect-WSMan` cmdlet, see [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span></span>

## <a name="troubleshooting-computer-configuration-issues"></a><span data-ttu-id="76224-242">針對電腦設定問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="76224-242">Troubleshooting computer configuration issues</span></span>

<span data-ttu-id="76224-243">本節討論與電腦、網域或企業特定設定相關的遠端處理問題。</span><span class="sxs-lookup"><span data-stu-id="76224-243">This section discusses remoting problems that are related to particular configurations of a computer, domain, or enterprise.</span></span>

### <a name="how-to-configure-remoting-on-alternate-ports"></a><span data-ttu-id="76224-244">如何設定替代埠上的遠端處理</span><span class="sxs-lookup"><span data-stu-id="76224-244">How to configure remoting on alternate ports</span></span>

```
ERROR: The connection to the specified remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="76224-245">PowerShell 遠端預設會針對 HTTP 傳輸使用埠80。</span><span class="sxs-lookup"><span data-stu-id="76224-245">PowerShell remoting uses port 80 for HTTP transport by default.</span></span> <span data-ttu-id="76224-246">每當使用者未在遠端命令中指定 **ConnectionURI** 或 **埠** 參數時，就會使用預設通訊埠。</span><span class="sxs-lookup"><span data-stu-id="76224-246">The default port is used whenever the user does not specify the **ConnectionURI** or **Port** parameters in a remote command.</span></span>

<span data-ttu-id="76224-247">若要變更 PowerShell 使用的預設通訊埠，請使用 `Set-Item` WSMan：磁片磁碟機中的 Cmdlet 來變更接聽程式分節點中的埠值。</span><span class="sxs-lookup"><span data-stu-id="76224-247">To change the default port that PowerShell uses, use `Set-Item` cmdlet in the WSMan: drive to change the Port value in the listener leaf node.</span></span>

<span data-ttu-id="76224-248">例如，下列命令會將預設埠變更為8080。</span><span class="sxs-lookup"><span data-stu-id="76224-248">For example, the following command changes the default port to 8080.</span></span>

```powershell
Set-Item wsman:\localhost\listener\listener*\port -Value 8080
```

### <a name="how-to-configure-remoting-with-a-proxy-server"></a><span data-ttu-id="76224-249">如何設定 proxy 伺服器的遠端處理</span><span class="sxs-lookup"><span data-stu-id="76224-249">How to configure remoting with a proxy server</span></span>

```
ERROR: The client cannot connect to the destination specified in the request.
Verify that the service on the destination is running and is accepting
requests.
```

<span data-ttu-id="76224-250">因為 PowerShell 遠端使用 HTTP 通訊協定，所以會受到 HTTP proxy 設定的影響。</span><span class="sxs-lookup"><span data-stu-id="76224-250">Because PowerShell remoting uses the HTTP protocol, it is affected by HTTP proxy settings.</span></span> <span data-ttu-id="76224-251">在具有 proxy 伺服器的企業中，使用者無法直接存取 PowerShell 遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="76224-251">In enterprises that have proxy servers, users cannot access a PowerShell remote computer directly.</span></span>

<span data-ttu-id="76224-252">若要解決此問題，請在遠端命令中使用 proxy 設定選項。</span><span class="sxs-lookup"><span data-stu-id="76224-252">To resolve this problem, use proxy setting options in your remote command.</span></span> <span data-ttu-id="76224-253">可用的設定如下：</span><span class="sxs-lookup"><span data-stu-id="76224-253">The following settings are available:</span></span>

- <span data-ttu-id="76224-254">System.management.automation.remoting.proxyaccesstype</span><span class="sxs-lookup"><span data-stu-id="76224-254">ProxyAccessType</span></span>
- <span data-ttu-id="76224-255">ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="76224-255">ProxyAuthentication</span></span>
- <span data-ttu-id="76224-256">ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="76224-256">ProxyCredential</span></span>

<span data-ttu-id="76224-257">若要為特定命令設定這些選項，請使用下列程式：</span><span class="sxs-lookup"><span data-stu-id="76224-257">To set these options for a particular command, use the following procedure:</span></span>

1. <span data-ttu-id="76224-258">使用 Cmdlet 的 **system.management.automation.remoting.proxyaccesstype** 、 **ProxyAuthentication** 和 **ProxyCredential** 參數， `New-PSSessionOption` 建立具有您企業之 proxy 設定的會話選項物件。</span><span class="sxs-lookup"><span data-stu-id="76224-258">Use the **ProxyAccessType** , **ProxyAuthentication** , and **ProxyCredential** parameters of the `New-PSSessionOption` cmdlet to create a session option object with the proxy settings for your enterprise.</span></span> <span data-ttu-id="76224-259">將選項物件儲存為變數。</span><span class="sxs-lookup"><span data-stu-id="76224-259">Save the option object is a variable.</span></span>

1. <span data-ttu-id="76224-260">使用包含 option 物件的變數做為 **SessionOption** `New-PSSession` 、 `Enter-PSSession` 或命令的 SessionOption 參數值 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="76224-260">Use the variable that contains the option object as the value of the **SessionOption** parameter of a `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` command.</span></span>

<span data-ttu-id="76224-261">例如，下列命令會建立具有 proxy 會話選項的會話選項物件，然後使用該物件來建立遠端會話。</span><span class="sxs-lookup"><span data-stu-id="76224-261">For example, the following command creates a session option object with proxy session options and then uses the object to create a remote session.</span></span>

```powershell
$SessionOption = New-PSSessionOption -ProxyAccessType IEConfig `
-ProxyAuthentication Negotiate -ProxyCredential Domain01\User01

New-PSSession -ConnectionURI https://www.fabrikam.com
```

<span data-ttu-id="76224-262">如需有關 Cmdlet 的詳細資訊 `New-PSSessionOption` ，請參閱 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。</span><span class="sxs-lookup"><span data-stu-id="76224-262">For more information about the `New-PSSessionOption` cmdlet, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

<span data-ttu-id="76224-263">若要為目前會話中的所有遠端命令設定這些選項，請使用在 `New-PSSessionOption` 喜好設定變數值中建立的選項物件 `$PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="76224-263">To set these options for all remote commands in the current session, use the option object that `New-PSSessionOption` creates in the value of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="76224-264">如需詳細資訊，請參閱 [about_Preference_Variables](about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="76224-264">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="76224-265">若要為所有遠端命令設定本機電腦上所有 PowerShell 會話的這些選項，請將 `$PSSessionOption` 喜好設定變數新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="76224-265">To set these options for all remote commands all PowerShell sessions on the local computer, add the `$PSSessionOption` preference variable to your PowerShell profile.</span></span> <span data-ttu-id="76224-266">如需 PowerShell 設定檔的詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="76224-266">For more information about PowerShell profiles, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="how-to-detect-a-32-bit-session-on-a-64-bit-computer"></a><span data-ttu-id="76224-267">如何在64位電腦上偵測32位的會話</span><span class="sxs-lookup"><span data-stu-id="76224-267">How to detect a 32-bit session on a 64-bit computer</span></span>

```
ERROR: The term "<tool-Name>" is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="76224-268">如果遠端電腦執行的是64位版本的 Windows，而遠端命令使用32位會話設定（例如 Microsoft.powershell32），則 Windows 遠端管理 (WinRM) 會載入 WOW64 進程，而 Windows 會自動將目錄的所有參考重新導向 `$env:Windir\System32` 至 `$env:Windir\SysWOW64` 目錄。</span><span class="sxs-lookup"><span data-stu-id="76224-268">If the remote computer is running a 64-bit version of Windows, and the remote command is using a 32-bit session configuration, such as Microsoft.PowerShell32, Windows Remote Management (WinRM) loads a WOW64 process and Windows automatically redirects all references to the `$env:Windir\System32` directory to the `$env:Windir\SysWOW64` directory.</span></span>

<span data-ttu-id="76224-269">如此一來，如果您嘗試使用 System32 目錄中的工具，而這些工具在 SysWow64 目錄中沒有對應專案（例如），則在 `Defrag.exe` 目錄中找不到工具。</span><span class="sxs-lookup"><span data-stu-id="76224-269">As a result, if you try to use tools in the System32 directory that do not have counterparts in the SysWow64 directory, such as `Defrag.exe`, the tools cannot be found in the directory.</span></span>

<span data-ttu-id="76224-270">若要尋找會話中使用的處理器架構，請使用 **PROCESSOR_ARCHITECTURE** 環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="76224-270">To find the processor architecture that is being used in the session, use the value of the **PROCESSOR_ARCHITECTURE** environment variable.</span></span> <span data-ttu-id="76224-271">下列命令會在變數中尋找會話的處理器架構 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="76224-271">The following command finds the processor architecture of the session in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -ConfigurationName CustomShell
Invoke-Command -Session $s {$env:PROCESSOR_ARCHITECTURE}
```

```Output
x86
```

<span data-ttu-id="76224-272">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="76224-272">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

## <a name="troubleshooting-policy-and-preference-issues"></a><span data-ttu-id="76224-273">針對原則和喜好設定問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="76224-273">Troubleshooting policy and preference issues</span></span>

<span data-ttu-id="76224-274">本節討論與本機電腦和遠端電腦上設定的原則和喜好設定相關的遠端處理問題。</span><span class="sxs-lookup"><span data-stu-id="76224-274">This section discusses remoting problems that are related to policies and preferences set on the local and remote computers.</span></span>

### <a name="how-to-change-the-execution-policy-for-import-pssession-and-import-module"></a><span data-ttu-id="76224-275">如何變更 Import-PSSession 和 Import-Module 的執行原則</span><span class="sxs-lookup"><span data-stu-id="76224-275">How to change the execution policy for Import-PSSession and Import-Module</span></span>

```
ERROR: Import-Module: File <filename> cannot be loaded because the
execution of scripts is disabled on this system.
```

<span data-ttu-id="76224-276">`Import-PSSession`和 `Export-PSSession` Cmdlet 會建立包含未簽署腳本檔案和格式化檔案的模組。</span><span class="sxs-lookup"><span data-stu-id="76224-276">The `Import-PSSession` and `Export-PSSession` cmdlets create modules that contains unsigned script files and formatting files.</span></span>

<span data-ttu-id="76224-277">若要使用或來匯入這些 Cmdlet 所建立的模組， `Import-PSSession` 則 `Import-Module` 無法限制或 AllSigned 目前會話中的執行原則。</span><span class="sxs-lookup"><span data-stu-id="76224-277">To import the modules that are created by these cmdlets, either by using `Import-PSSession` or `Import-Module`, the execution policy in the current session cannot be Restricted or AllSigned.</span></span> <span data-ttu-id="76224-278">如需 PowerShell 執行原則的詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="76224-278">For information about PowerShell execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="76224-279">若要匯入模組而不變更登錄中設定之本機電腦的執行原則，請使用的 **範圍** 參數，為 `Set-ExecutionPolicy` 單一進程設定較不嚴格的執行原則。</span><span class="sxs-lookup"><span data-stu-id="76224-279">To import the modules without changing the execution policy for the local computer that is set in the registry, use the **Scope** parameter of `Set-ExecutionPolicy` to set a less restrictive execution policy for a single process.</span></span>

<span data-ttu-id="76224-280">例如，下列命令會啟動具有執行原則的進程 `RemoteSigned` 。</span><span class="sxs-lookup"><span data-stu-id="76224-280">For example, the following command starts a process with the `RemoteSigned` execution policy.</span></span> <span data-ttu-id="76224-281">執行原則變更只會影響目前的進程，而不會變更 PowerShell **ExecutionPolicy** 登錄設定。</span><span class="sxs-lookup"><span data-stu-id="76224-281">The execution policy change affects only the current process and does not change the PowerShell **ExecutionPolicy** registry setting.</span></span>

```powershell
Set-ExecutionPolicy -Scope process -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="76224-282">您也可以使用的 **ExecutionPolicy** 參數 `PowerShell.exe` ，以較不嚴格的執行原則來啟動單一會話。</span><span class="sxs-lookup"><span data-stu-id="76224-282">You can also use the **ExecutionPolicy** parameter of `PowerShell.exe` to start a single session with a less restrictive execution policy.</span></span>

```powershell
PowerShell.exe -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="76224-283">如需執行原則的詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="76224-283">For more information about execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span> <span data-ttu-id="76224-284">如需詳細資訊，請鍵入 `PowerShell.exe -?`。</span><span class="sxs-lookup"><span data-stu-id="76224-284">For more information, type `PowerShell.exe -?`.</span></span>

### <a name="how-to-set-and-change-quotas"></a><span data-ttu-id="76224-285">如何設定和變更配額</span><span class="sxs-lookup"><span data-stu-id="76224-285">How to set and change quotas</span></span>

```
ERROR: The total data received from the remote client exceeded allowed
maximum.
```

<span data-ttu-id="76224-286">您可以使用配額來防止本機電腦和遠端電腦過度使用資源，而不會發生意外和惡意。</span><span class="sxs-lookup"><span data-stu-id="76224-286">You can use quotas to protect the local computer and the remote computer from excessive resource use, both accidental and malicious.</span></span>

<span data-ttu-id="76224-287">基本設定中提供下列配額。</span><span class="sxs-lookup"><span data-stu-id="76224-287">The following quotas are available in the basic configuration.</span></span>

- <span data-ttu-id="76224-288">WSMan 提供者 (WSMan： ) 提供數個配額設定，例如節點中的 **MaxEnvelopeSizeKB** 和 **MaxProviderRequests** 設定， `WSMan:<ComputerName>` 以及節點中的 **MaxConcurrentOperations** 、 **MaxConcurrentOperationsPerUser** 和 **MaxConnections** 設定 `WSMan:<ComputerName>\Service` 。</span><span class="sxs-lookup"><span data-stu-id="76224-288">The WSMan provider (WSMan:) provides several quota settings, such as the **MaxEnvelopeSizeKB** and **MaxProviderRequests** settings in the `WSMan:<ComputerName>` node and the **MaxConcurrentOperations** , **MaxConcurrentOperationsPerUser** , and **MaxConnections** settings in the `WSMan:<ComputerName>\Service` node.</span></span>

- <span data-ttu-id="76224-289">您可以使用 Cmdlet 的 **MaximumReceivedDataSizePerCommand** 和 **MaximumReceivedObjectSize** 參數和喜好設定變數來保護本機電腦 `New-PSSessionOption` `$PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="76224-289">You can protect the local computer by using the **MaximumReceivedDataSizePerCommand** and **MaximumReceivedObjectSize** parameters of the `New-PSSessionOption` cmdlet and the `$PSSessionOption` preference variable.</span></span>

- <span data-ttu-id="76224-290">您可以藉由新增會話設定的限制（例如，使用 Cmdlet 的 **MaximumReceivedDataSizePerCommandMB** 和 **MaximumReceivedObjectSizeMB** 參數）來保護遠端電腦 `Register-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="76224-290">You can protect the remote computer by adding restrictions to the session configurations, such as by using the **MaximumReceivedDataSizePerCommandMB** and **MaximumReceivedObjectSizeMB** parameters of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="76224-291">當配額與命令衝突時，PowerShell 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="76224-291">When quotas conflict with a command, PowerShell generates an error.</span></span>

<span data-ttu-id="76224-292">若要解決此錯誤，請將遠端命令變更為符合配額。</span><span class="sxs-lookup"><span data-stu-id="76224-292">To resolve the error, change the remote command to comply with the quota.</span></span> <span data-ttu-id="76224-293">或者，判斷配額的來源，然後增加配額以允許命令完成。</span><span class="sxs-lookup"><span data-stu-id="76224-293">Or, determine the source of the quota, and then increase the quota to allow the command to complete.</span></span>

<span data-ttu-id="76224-294">例如，下列命令會將遠端電腦上的 Microsoft PowerShell 會話設定中的物件大小配額增加為 10 MB (預設值) 為 11 MB。</span><span class="sxs-lookup"><span data-stu-id="76224-294">For example, the following command increases the object size quota in the Microsoft.PowerShell session configuration on the remote computer from 10 MB (the default value) to 11 MB.</span></span>

```powershell
Set-PSSessionConfiguration -Name microsoft.PowerShell `
  -MaximumReceivedObjectSizeMB 11 -Force
```

<span data-ttu-id="76224-295">如需此 Cmdlet 的詳細資訊 `New-PSSessionOption` ，請參閱 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="76224-295">For more information about the `New-PSSessionOption` cmdlet, see `New-PSSessionOption`.</span></span>

<span data-ttu-id="76224-296">如需 WS-Management 配額的詳細資訊，請參閱 [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)。</span><span class="sxs-lookup"><span data-stu-id="76224-296">For more information about the WS-Management quotas, see [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md).</span></span>

### <a name="how-to-resolve-timeout-errors"></a><span data-ttu-id="76224-297">如何解決逾時錯誤</span><span class="sxs-lookup"><span data-stu-id="76224-297">How to resolve timeout errors</span></span>

```
ERROR: The WS-Management service cannot complete the operation within
the time specified in OperationTimeout.
```

<span data-ttu-id="76224-298">您可以使用超時來防止本機電腦和遠端電腦過度使用資源，而不會發生意外和惡意。</span><span class="sxs-lookup"><span data-stu-id="76224-298">You can use timeouts to protect the local computer and the remote computer from excessive resource use, both accidental and malicious.</span></span> <span data-ttu-id="76224-299">在本機和遠端電腦上設定 timeout 時，PowerShell 會使用最短的 timeout 設定。</span><span class="sxs-lookup"><span data-stu-id="76224-299">When timeouts are set on both the local and remote computer, PowerShell uses the shortest timeout settings.</span></span>

<span data-ttu-id="76224-300">基本設定中提供下列超時。</span><span class="sxs-lookup"><span data-stu-id="76224-300">The following timeouts are available in the basic configuration.</span></span>

- <span data-ttu-id="76224-301">WSMan 提供者 (WSMan： ) 提供數個用戶端和服務端的超時設定，例如節點中的 **MaxTimeoutms** 設定， `WSMan:<ComputerName>` 以及節點中的 **EnumerationTimeoutms** 和 **MaxPacketRetrievalTimeSeconds** 設定 `WSMan:<ComputerName>\Service` 。</span><span class="sxs-lookup"><span data-stu-id="76224-301">The WSMan provider (WSMan:) provides several client-side and service-side timeout settings, such as the **MaxTimeoutms** setting in the `WSMan:<ComputerName>` node and the **EnumerationTimeoutms** and **MaxPacketRetrievalTimeSeconds** settings in the `WSMan:<ComputerName>\Service` node.</span></span>

- <span data-ttu-id="76224-302">您可以使用 Cmdlet 的 **CancelTimeout** 、 **IdleTimeout** 、 **OpenTimeout** 和 **OperationTimeout** 參數和喜好設定變數來保護本機電腦 `New-PSSessionOption` `$PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="76224-302">You can protect the local computer by using the **CancelTimeout** , **IdleTimeout** , **OpenTimeout** , and **OperationTimeout** parameters of the `New-PSSessionOption` cmdlet and the `$PSSessionOption` preference variable.</span></span>

- <span data-ttu-id="76224-303">您也可以在會話的會話設定中，以程式設計的方式設定 timeout 值，以保護遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="76224-303">You can also protect the remote computer by setting timeout values programmatically in the session configuration for the session.</span></span>

<span data-ttu-id="76224-304">當超時值不允許作業完成時，PowerShell 會終止作業並產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="76224-304">When a timeout value does not permit a operation to complete, PowerShell terminates the operation and generates an error.</span></span>

<span data-ttu-id="76224-305">若要解決此錯誤，請將命令變更為在逾時間隔內完成，或判斷超時限制的來源，並增加逾時間隔，以允許命令完成。</span><span class="sxs-lookup"><span data-stu-id="76224-305">To resolve the error, change the command to complete within the timeout interval or determine the source of the timeout limit and increase the timeout interval to allow the command to complete.</span></span>

<span data-ttu-id="76224-306">例如，下列命令會使用指令 `New-PSSessionOption` 程式建立 **OperationTimeout** 值為4分鐘的會話選項物件 (在 MS) 中，然後使用會話選項物件來建立遠端會話。</span><span class="sxs-lookup"><span data-stu-id="76224-306">For example, the following commands use the `New-PSSessionOption` cmdlet to create a session option object with an **OperationTimeout** value of 4 minutes (in MS) and then use the session option object to create a remote session.</span></span>

```powershell
$pso = New-PSSessionoption -OperationTimeout 240000

New-PSSession -ComputerName Server01 -sessionOption $pso
```

<span data-ttu-id="76224-307">如需 WS-Management 超時的詳細資訊，請參閱 WSMan 提供者的說明主題 (類型 `Get-Help WSMan`) 。</span><span class="sxs-lookup"><span data-stu-id="76224-307">For more information about the WS-Management timeouts, see the Help topic for the WSMan provider (type `Get-Help WSMan`).</span></span>

<span data-ttu-id="76224-308">如需有關 Cmdlet 的詳細資訊 `New-PSSessionOption` ，請參閱 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。</span><span class="sxs-lookup"><span data-stu-id="76224-308">For more information about the `New-PSSessionOption` cmdlet, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

## <a name="troubleshooting-unresponsive-behavior"></a><span data-ttu-id="76224-309">針對沒有回應的行為進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="76224-309">Troubleshooting unresponsive behavior</span></span>

<span data-ttu-id="76224-310">本節討論防止命令完成和防止或延遲傳回 PowerShell 提示的遠端處理問題。</span><span class="sxs-lookup"><span data-stu-id="76224-310">This section discusses remoting problems that prevent a command from completing and prevent or delay the return of the PowerShell prompt.</span></span>

### <a name="how-to-interrupt-a-command"></a><span data-ttu-id="76224-311">如何中斷命令</span><span class="sxs-lookup"><span data-stu-id="76224-311">How to interrupt a command</span></span>

<span data-ttu-id="76224-312">某些原生的 Windows 程式，例如具有使用者介面的程式、會提示輸入的主控台應用程式，以及使用 Win32 主控台 API 的主控台應用程式，在 PowerShell 遠端主機中無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="76224-312">Some native Windows programs, such as programs with a user interface, console applications that prompt for input, and console applications that use the Win32 console API, do not work correctly in the PowerShell remote host.</span></span>

<span data-ttu-id="76224-313">當您使用這些程式時，可能會看到非預期的行為，例如沒有輸出、部分輸出或未完成的遠端命令。</span><span class="sxs-lookup"><span data-stu-id="76224-313">When you use these programs, you might see unexpected behavior, such as no output, partial output, or a remote command that does not complete.</span></span>

<span data-ttu-id="76224-314">若要結束沒有回應的程式，請輸入<kbd>CTRL</kbd> + <kbd>C</kbd>。</span><span class="sxs-lookup"><span data-stu-id="76224-314">To end an unresponsive program, type <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="76224-315">若要查看任何可能已回報的錯誤，請輸入 `$error` 本機主機和遠端會話。</span><span class="sxs-lookup"><span data-stu-id="76224-315">To view any errors that might have been reported, type `$error` in the local host and the remote session.</span></span>

## <a name="how-to-recover-from-an-operation-failure"></a><span data-ttu-id="76224-316">如何從操作失敗中復原</span><span class="sxs-lookup"><span data-stu-id="76224-316">How to recover from an operation failure</span></span>

```
ERROR: The I/O operation has been aborted because of either a thread exit
or an  application request.
```

<span data-ttu-id="76224-317">當作業結束時，會傳回此錯誤。</span><span class="sxs-lookup"><span data-stu-id="76224-317">This error is returned when an operation is terminated before it completes.</span></span>
<span data-ttu-id="76224-318">一般來說，當 WinRM 服務在其他 WinRM 作業正在進行時停止或重新開機時，就會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="76224-318">Typically, it occurs when the WinRM service stops or restarts while other WinRM operations are in progress.</span></span>

<span data-ttu-id="76224-319">若要解決此問題，請確認 WinRM 服務正在執行，然後再次嘗試命令。</span><span class="sxs-lookup"><span data-stu-id="76224-319">To resolve this issue, verify that the WinRM service is running and try the command again.</span></span>

1. <span data-ttu-id="76224-320">使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="76224-320">Start PowerShell with the **Run as administrator** option.</span></span>
1. <span data-ttu-id="76224-321">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="76224-321">Run the following command:</span></span>

   `Start-Service WinRM`

1. <span data-ttu-id="76224-322">重新執行產生錯誤的命令。</span><span class="sxs-lookup"><span data-stu-id="76224-322">Re-run the command that generated the error.</span></span>

## <a name="linux-and-macos-limitations"></a><span data-ttu-id="76224-323">Linux 和 macOS 限制</span><span class="sxs-lookup"><span data-stu-id="76224-323">Linux and macOS limitations</span></span>

### <a name="authentication"></a><span data-ttu-id="76224-324">驗證</span><span class="sxs-lookup"><span data-stu-id="76224-324">Authentication</span></span>

<span data-ttu-id="76224-325">只有基本驗證適用于 macOS，而且嘗試使用其他驗證配置可能會導致進程損毀。</span><span class="sxs-lookup"><span data-stu-id="76224-325">Only basic authentication works on macOS and attempting to use other authentication schemes may result in the process crashing.</span></span>

<span data-ttu-id="76224-326">請參閱 [OMI authentication](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) 指示。</span><span class="sxs-lookup"><span data-stu-id="76224-326">Please see the [OMI authentication](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) instructions.</span></span>

## <a name="see-also"></a><span data-ttu-id="76224-327">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76224-327">SEE ALSO</span></span>

[<span data-ttu-id="76224-328">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="76224-328">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)

[<span data-ttu-id="76224-329">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="76224-329">Export-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Export-PSSession)

[<span data-ttu-id="76224-330">Import-Module</span><span class="sxs-lookup"><span data-stu-id="76224-330">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

[<span data-ttu-id="76224-331">about_Remote</span><span class="sxs-lookup"><span data-stu-id="76224-331">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="76224-332">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="76224-332">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="76224-333">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="76224-333">about_Remote_Variables</span></span>](about_Remote_Variables.md)
