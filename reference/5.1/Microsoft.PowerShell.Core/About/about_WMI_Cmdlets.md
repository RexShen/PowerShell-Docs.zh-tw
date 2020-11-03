---
description: 提供關於 Windows Management Instrumentation (WMI) 和 Windows PowerShell 的背景資訊。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI_Cmdlets
ms.openlocfilehash: c2099c005cedf64e9621d66d6757419320c9b43e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207883"
---
# <a name="about-wmi-cmdlets"></a><span data-ttu-id="95eb3-104">關於 WMI Cmdlet</span><span class="sxs-lookup"><span data-stu-id="95eb3-104">About WMI Cmdlets</span></span>

## <a name="short-description"></a><span data-ttu-id="95eb3-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="95eb3-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="95eb3-106">提供關於 Windows Management Instrumentation (WMI) 和 Windows PowerShell 的背景資訊。</span><span class="sxs-lookup"><span data-stu-id="95eb3-106">Provides background information about Windows Management Instrumentation (WMI) and Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="95eb3-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="95eb3-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="95eb3-108">本主題提供 WMI 技術、Windows PowerShell 的 WMI Cmdlet、wmi 型遠端、WMI 加速器和 WMI 疑難排解的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="95eb3-108">This topic provides information about WMI technology, the WMI cmdlets for Windows PowerShell, WMI-based remoting, WMI accelerators, and WMI troubleshooting.</span></span> <span data-ttu-id="95eb3-109">本主題也提供 WMI 的詳細資訊連結。</span><span class="sxs-lookup"><span data-stu-id="95eb3-109">This topic also provides links to more information about WMI.</span></span>

### <a name="about-wmi"></a><span data-ttu-id="95eb3-110">關於 WMI</span><span class="sxs-lookup"><span data-stu-id="95eb3-110">ABOUT WMI</span></span>

<span data-ttu-id="95eb3-111">Windows Management Instrumentation (WMI) 是 Microsoft 在 Web 架構企業管理 (WBEM) 方面的實作，這是一種開發標準技術的業界措施，用於存取企業環境中的管理資訊。</span><span class="sxs-lookup"><span data-stu-id="95eb3-111">Windows Management Instrumentation (WMI) is the Microsoft implementation of Web-Based Enterprise Management (WBEM), which is an industry initiative to develop a standard technology for accessing management information in an enterprise environment.</span></span> <span data-ttu-id="95eb3-112">WMI 使用通用訊息模型 (CIM) 業界標準來代表系統、應用程式、網路、裝置和其他受管理元件。</span><span class="sxs-lookup"><span data-stu-id="95eb3-112">WMI uses the Common Information Model (CIM) industry standard to represent systems, applications, networks, devices, and other managed components.</span></span> <span data-ttu-id="95eb3-113">CIM 由分散式管理任務推動小組 (DMTF) 開發與維護。</span><span class="sxs-lookup"><span data-stu-id="95eb3-113">CIM is developed and maintained by the Distributed Management Task Force (DMTF).</span></span> <span data-ttu-id="95eb3-114">您可以使用 WMI 來管理本機和遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="95eb3-114">You can use WMI to manage both local and remote computers.</span></span> <span data-ttu-id="95eb3-115">例如，您可以使用 WMI 來執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="95eb3-115">For example, you can use WMI to do the following:</span></span>

- <span data-ttu-id="95eb3-116">在遠端電腦上啟動處理常式。</span><span class="sxs-lookup"><span data-stu-id="95eb3-116">Start a process on a remote computer.</span></span>
- <span data-ttu-id="95eb3-117">從遠端重新開機電腦。</span><span class="sxs-lookup"><span data-stu-id="95eb3-117">Restart a computer remotely.</span></span>
- <span data-ttu-id="95eb3-118">取得安裝在本機或遠端電腦上的應用程式清單。</span><span class="sxs-lookup"><span data-stu-id="95eb3-118">Get a list of the applications that are installed on a local or remote computer.</span></span>
- <span data-ttu-id="95eb3-119">查詢本機或遠端電腦上的 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="95eb3-119">Query the Windows event logs on a local or remote computer.</span></span>

### <a name="the-wmi-cmdlets-for-windows-powershell"></a><span data-ttu-id="95eb3-120">適用于 WINDOWS POWERSHELL 的 WMI CMDLET</span><span class="sxs-lookup"><span data-stu-id="95eb3-120">THE WMI CMDLETS FOR WINDOWS POWERSHELL</span></span>

<span data-ttu-id="95eb3-121">Windows PowerShell 會透過一組可在 Windows PowerShell 中使用的 Cmdlet 來執行 WMI 功能。</span><span class="sxs-lookup"><span data-stu-id="95eb3-121">Windows PowerShell implements WMI functionality through a set of cmdlets that are available in Windows PowerShell by default.</span></span> <span data-ttu-id="95eb3-122">您可以使用這些 Cmdlet 來完成管理本機和遠端電腦所需的端對端工作。</span><span class="sxs-lookup"><span data-stu-id="95eb3-122">You can use these cmdlets to complete the end-to-end tasks necessary to manage local and remote computers.</span></span>

<span data-ttu-id="95eb3-123">包含下列 WMI Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="95eb3-123">The following WMI cmdlets are included.</span></span>

|<span data-ttu-id="95eb3-124">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="95eb3-124">Cmdlet</span></span>           |<span data-ttu-id="95eb3-125">描述</span><span class="sxs-lookup"><span data-stu-id="95eb3-125">Description</span></span>                                   |
|-----------------|----------------------------------------------|
|<span data-ttu-id="95eb3-126">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="95eb3-126">Get-WmiObject</span></span>    |<span data-ttu-id="95eb3-127">取得 WMI 類別或資訊的實例</span><span class="sxs-lookup"><span data-stu-id="95eb3-127">Gets instances of WMI classes or information</span></span>  |
|                 |<span data-ttu-id="95eb3-128">關於可用的類別。</span><span class="sxs-lookup"><span data-stu-id="95eb3-128">about the available classes.</span></span>                  |
|<span data-ttu-id="95eb3-129">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="95eb3-129">Invoke-WmiMethod</span></span> |<span data-ttu-id="95eb3-130">呼叫 WMI 方法。</span><span class="sxs-lookup"><span data-stu-id="95eb3-130">Calls WMI methods.</span></span>                            |
|<span data-ttu-id="95eb3-131">Register-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="95eb3-131">Register-WmiEvent</span></span>|<span data-ttu-id="95eb3-132">訂閱 WMI 事件。</span><span class="sxs-lookup"><span data-stu-id="95eb3-132">Subscribes to a WMI event.</span></span>                    |
|<span data-ttu-id="95eb3-133">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="95eb3-133">Remove-WmiObject</span></span> |<span data-ttu-id="95eb3-134">刪除 WMI 類別和執行個體。</span><span class="sxs-lookup"><span data-stu-id="95eb3-134">Deletes WMI classes and instances.</span></span>            |
|<span data-ttu-id="95eb3-135">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="95eb3-135">Set-WmiInstance</span></span>  |<span data-ttu-id="95eb3-136">建立或修改 WMI 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="95eb3-136">Creates or modifies instances of WMI classes.</span></span> |

### <a name="sample-commands"></a><span data-ttu-id="95eb3-137">範例命令</span><span class="sxs-lookup"><span data-stu-id="95eb3-137">SAMPLE COMMANDS</span></span>
<span data-ttu-id="95eb3-138">下列命令會顯示本機電腦的 BIOS 資訊。</span><span class="sxs-lookup"><span data-stu-id="95eb3-138">The following command displays the BIOS information for the local computer.</span></span>

```powershell
C:\PS> get-wmiobject win32_bios | format-list *
```

<span data-ttu-id="95eb3-139">下列命令會顯示三部遠端電腦的 WinRM 服務相關資訊。</span><span class="sxs-lookup"><span data-stu-id="95eb3-139">The following command displays information about the WinRM service for three remote computers.</span></span>

```powershell
$wql = "select * from win32_service where name='WinRM'"
get-wmiobject -query $wql -computername server01, server01, server03
```

<span data-ttu-id="95eb3-140">下列更複雜的命令會結束程式的所有實例。</span><span class="sxs-lookup"><span data-stu-id="95eb3-140">The following more complex command exits all instances of a program.</span></span>

```powershell
C:\PS> notepad.exe
C:\PS> $wql = "select * from win32_process where name='notepad.exe'"
C:\PS> $np = get-wmiobject -query $wql
C:\PS> $np | remove-wmiobject
```

### <a name="wmi-based-remoting"></a><span data-ttu-id="95eb3-141">以 WMI 為基礎的遠端</span><span class="sxs-lookup"><span data-stu-id="95eb3-141">WMI-BASED REMOTING</span></span>

<span data-ttu-id="95eb3-142">雖然透過 WMI 管理本機系統的能力很有説明，但它是讓 WMI 成為強大系統管理工具的遠端功能。</span><span class="sxs-lookup"><span data-stu-id="95eb3-142">While the ability to manage a local system through WMI is useful, it is the remoting capabilities that make WMI a powerful administrative tool.</span></span> <span data-ttu-id="95eb3-143">WMI 會使用 Microsoft 的分散式元件物件模型 (DCOM) 來連接和管理系統。</span><span class="sxs-lookup"><span data-stu-id="95eb3-143">WMI uses Microsoft's Distributed Component Object Model (DCOM) to connect to and manage systems.</span></span> <span data-ttu-id="95eb3-144">您可能必須設定某些系統以允許 DCOM 連線。</span><span class="sxs-lookup"><span data-stu-id="95eb3-144">You might have to configure some systems to allow DCOM connections.</span></span>
<span data-ttu-id="95eb3-145">防火牆設定和鎖定的 DCOM 許可權可以封鎖 WMI 從遠端管理系統的能力。</span><span class="sxs-lookup"><span data-stu-id="95eb3-145">Firewall settings and locked-down DCOM permissions can block WMI's ability to remotely manage systems.</span></span>

### <a name="wmi-type-accelerators"></a><span data-ttu-id="95eb3-146">WMI 類型加速器</span><span class="sxs-lookup"><span data-stu-id="95eb3-146">WMI TYPE ACCELERATORS</span></span>

<span data-ttu-id="95eb3-147">Windows PowerShell 包含 WMI 類型加速器。</span><span class="sxs-lookup"><span data-stu-id="95eb3-147">Windows PowerShell includes WMI type accelerators.</span></span> <span data-ttu-id="95eb3-148">這些 WMI 類型加速器 (快捷方式，) 可讓您更直接存取 WMI 物件，而非以非類型加速器的方法允許。</span><span class="sxs-lookup"><span data-stu-id="95eb3-148">These WMI type accelerators (shortcuts) allow more direct access to a WMI objects than a non-type accelerator approach would allow.</span></span>

<span data-ttu-id="95eb3-149">WMI 支援下列類型加速器：</span><span class="sxs-lookup"><span data-stu-id="95eb3-149">The following type accelerators are supported with WMI:</span></span>

<span data-ttu-id="95eb3-150">[WMISEARCHER]-用來搜尋 WMI 物件的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="95eb3-150">[WMISEARCHER] - A shortcut for searching for WMI objects.</span></span>

<span data-ttu-id="95eb3-151">[WMICLASS]-存取類別之靜態屬性和方法的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="95eb3-151">[WMICLASS] - A shortcut for accessing the static properties and methods of a class.</span></span>

<span data-ttu-id="95eb3-152">[WMI]-取得類別的單一實例的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="95eb3-152">[WMI] - A shortcut for getting a single instance of a class.</span></span>

<span data-ttu-id="95eb3-153">[WMISEARCHER] 是 ManagementObjectSearcher 的型別加速器。</span><span class="sxs-lookup"><span data-stu-id="95eb3-153">[WMISEARCHER] is a type accelerator for a ManagementObjectSearcher.</span></span> <span data-ttu-id="95eb3-154">它可以採用字串的函式來建立搜尋，讓您可以在上執行 GET ( # A1。</span><span class="sxs-lookup"><span data-stu-id="95eb3-154">It can take a string constructor to create a searcher that you can then do a GET() on.</span></span>

<span data-ttu-id="95eb3-155">例如：</span><span class="sxs-lookup"><span data-stu-id="95eb3-155">For example:</span></span>

```powershell
PS> $s = [WmiSearcher]'Select * from Win32_Process where Handlecount > 1000'
PS> $s.Get() |sort handlecount |ft handlecount,__path,name -auto

count  __PATH                                              name
-----  ------                                              ----
1105   \\SERVER01\root\cimv2:Win32_Process.Handle="3724"   PowerShell...
1132   \\SERVER01\root\cimv2:Win32_Process.Handle="1388"   winlogon.exe
1495   \\SERVER01\root\cimv2:Win32_Process.Handle="2852"   iexplore.exe
1699   \\SERVER01\root\cimv2:Win32_Process.Handle="1204"   OUTLOOK.EXE
1719   \\SERVER01\root\cimv2:Win32_Process.Handle="1912"   iexplore.exe
2579   \\SERVER01\root\cimv2:Win32_Process.Handle="1768"   svchost.exe
```

<span data-ttu-id="95eb3-156">[WMICLASS] 是 ManagementClass 的型別加速器。</span><span class="sxs-lookup"><span data-stu-id="95eb3-156">[WMICLASS] is a type accelerator for ManagementClass.</span></span> <span data-ttu-id="95eb3-157">這個字串的函式會接受 WMI 類別的本機或絕對 WMI 路徑，並傳回系結至該類別的物件。</span><span class="sxs-lookup"><span data-stu-id="95eb3-157">This has a string constructor that takes a local or absolute WMI path to a WMI class and returns an object that is bound to that class.</span></span>

<span data-ttu-id="95eb3-158">例如：</span><span class="sxs-lookup"><span data-stu-id="95eb3-158">For example:</span></span>

```powershell
PS> $c = [WMICLASS]"root\cimv2:WIn32_Process"
PS> $c |fl *
Name             : Win32_Process
__GENUS          : 1
__CLASS          : Win32_Process
__SUPERCLASS     : CIM_Process
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Process
__PROPERTY_COUNT : 45
__DERIVATION     : {CIM_Process, CIM_LogicalElement,
                   CIM_ManagedSystemElement}
__SERVER         : SERVER01
__NAMESPACE      : ROOT\cimv2
__PATH           : \\SERVER01\ROOT\cimv2:Win32_Process
```

<span data-ttu-id="95eb3-159">[WMI] 是 System.management.managementobject 的型別加速器。</span><span class="sxs-lookup"><span data-stu-id="95eb3-159">[WMI] is a type accelerator for ManagementObject.</span></span> <span data-ttu-id="95eb3-160">這個字串的函式會接受 WMI 實例的本機或絕對 WMI 路徑，並傳回系結至該實例的物件。</span><span class="sxs-lookup"><span data-stu-id="95eb3-160">This has a string constructor that takes a local or absolute WMI path to a WMI instance and returns an object that is bound to that instance.</span></span>

<span data-ttu-id="95eb3-161">例如：</span><span class="sxs-lookup"><span data-stu-id="95eb3-161">For example:</span></span>

```powershell
PS> $p = [WMI]'\\SERVER01\root\cimv2:Win32_Process.Handle="1204"'
PS> $p.Name
OUTLOOK.EXE
```

### <a name="wmi-troubleshooting"></a><span data-ttu-id="95eb3-162">WMI 疑難排解</span><span class="sxs-lookup"><span data-stu-id="95eb3-162">WMI TROUBLESHOOTING</span></span>

<span data-ttu-id="95eb3-163">下列問題是當您嘗試連接到遠端電腦時，可能發生的最常見問題。</span><span class="sxs-lookup"><span data-stu-id="95eb3-163">The following problems are the most common problems that might occur when you try to connect to a remote computer.</span></span>

<span data-ttu-id="95eb3-164">問題1：遠端電腦不在線上。</span><span class="sxs-lookup"><span data-stu-id="95eb3-164">Problem 1: The remote computer is not online.</span></span>

<span data-ttu-id="95eb3-165">如果電腦離線，您將無法使用 WMI 連接到電腦。</span><span class="sxs-lookup"><span data-stu-id="95eb3-165">If a computer is offline, you will not be able to connect to it by using WMI.</span></span>
<span data-ttu-id="95eb3-166">您可能會收到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="95eb3-166">You may receive the following error message:</span></span>

```
Remote server machine does not exist or is unavailable
```

<span data-ttu-id="95eb3-167">如果您收到此錯誤訊息，請確認電腦已上線。</span><span class="sxs-lookup"><span data-stu-id="95eb3-167">If you receive this error message, verify that the computer is online.</span></span> <span data-ttu-id="95eb3-168">嘗試 ping 遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="95eb3-168">Try to ping the remote computer.</span></span>

<span data-ttu-id="95eb3-169">問題2：您在遠端電腦上沒有本機系統管理員許可權。</span><span class="sxs-lookup"><span data-stu-id="95eb3-169">Problem 2: You do not have local administrator rights on the remote computer.</span></span>

<span data-ttu-id="95eb3-170">若要從遠端使用 WMI，您必須擁有遠端電腦的本機系統管理員許可權。</span><span class="sxs-lookup"><span data-stu-id="95eb3-170">To use WMI remotely, you must have local administrator rights on the remote computer.</span></span> <span data-ttu-id="95eb3-171">如果沒有這麼做，就會拒絕存取該電腦。</span><span class="sxs-lookup"><span data-stu-id="95eb3-171">If you do not, access to that computer will be denied.</span></span>

<span data-ttu-id="95eb3-172">若要驗證命名空間安全性：</span><span class="sxs-lookup"><span data-stu-id="95eb3-172">To verify namespace security:</span></span>

1. <span data-ttu-id="95eb3-173">按一下 [開始]，以滑鼠右鍵按一下我的電腦，然後按一下 [管理]。</span><span class="sxs-lookup"><span data-stu-id="95eb3-173">Click Start, right-click My Computer, and then click Manage.</span></span>
2. <span data-ttu-id="95eb3-174">在 [電腦管理] 中，展開 [服務和應用程式]，以滑鼠右鍵按一下 [WMI 控制]，然後按一下 [內容]</span><span class="sxs-lookup"><span data-stu-id="95eb3-174">In Computer Management, expand Services and Applications, right-click WMI Control, and then click Properties.</span></span>
3. <span data-ttu-id="95eb3-175">在 [WMI 控制項屬性] 對話方塊中，按一下 [[安全性] 索引標籤]。</span><span class="sxs-lookup"><span data-stu-id="95eb3-175">In the WMI Control Properties dialog box, click  the Security tab.</span></span>

<span data-ttu-id="95eb3-176">問題3：防火牆正在封鎖對遠端電腦的存取。</span><span class="sxs-lookup"><span data-stu-id="95eb3-176">Problem 3: A firewall is blocking access to the remote computer.</span></span>

<span data-ttu-id="95eb3-177">WMI 使用 DCOM (分散式 COM) 和 RPC (遠端程序呼叫) 通訊協定來跨越網路。</span><span class="sxs-lookup"><span data-stu-id="95eb3-177">WMI uses the DCOM (Distributed COM) and RPC (Remote Procedure Call) protocols to traverse the network.</span></span> <span data-ttu-id="95eb3-178">根據預設，許多防火牆會封鎖 DCOM 和 RPC 流量。</span><span class="sxs-lookup"><span data-stu-id="95eb3-178">By default, many firewalls block DCOM and RPC traffic.</span></span> <span data-ttu-id="95eb3-179">如果您的防火牆封鎖這些通訊協定，連接將會失敗。</span><span class="sxs-lookup"><span data-stu-id="95eb3-179">If your firewall is blocking these protocols, your connection will fail.</span></span> <span data-ttu-id="95eb3-180">例如，Microsoft Windows XP Service Pack 2 中的 Windows 防火牆是設定成自動封鎖所有未經要求的網路流量，包括 DCOM 和 WMI。</span><span class="sxs-lookup"><span data-stu-id="95eb3-180">For example, Windows Firewall in Microsoft Windows XP Service Pack 2 is configured to automatically block all unsolicited network traffic, including DCOM and WMI.</span></span> <span data-ttu-id="95eb3-181">在其預設設定中，Windows 防火牆會拒絕傳入的 WMI 要求，且您會收到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="95eb3-181">In its default configuration, Windows Firewall rejects an incoming WMI request, and you receive the following error message:</span></span>

```
Remote server machine does not exist or is unavailable
```

## <a name="see-also"></a><span data-ttu-id="95eb3-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95eb3-182">SEE ALSO</span></span>

[<span data-ttu-id="95eb3-183">關於 WMI</span><span class="sxs-lookup"><span data-stu-id="95eb3-183">About WMI</span></span>](/windows/win32/wmisdk/about-wmi)

<span data-ttu-id="95eb3-184">[WMI 疑難排解](/windows/win32/wmisdk/wmi-troubleshooting) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="95eb3-184">[WMI Troubleshooting](/windows/win32/wmisdk/wmi-troubleshooting)</span></span>

[<span data-ttu-id="95eb3-185">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="95eb3-185">Get-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[<span data-ttu-id="95eb3-186">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="95eb3-186">Invoke-WmiMethod</span></span>](xref:Microsoft.PowerShell.Management.Invoke-WmiMethod)

[<span data-ttu-id="95eb3-187">Register-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="95eb3-187">Register-WmiEvent</span></span>](xref:Microsoft.PowerShell.Management.Register-WmiEvent)

[<span data-ttu-id="95eb3-188">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="95eb3-188">Remove-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Remove-WmiObject)

[<span data-ttu-id="95eb3-189">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="95eb3-189">Set-WmiInstance</span></span>](xref:Microsoft.PowerShell.Management.Set-WmiInstance)
