---
description: 描述在 PowerShell 中執行遠端命令的系統需求與設定需求。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Requirements
ms.openlocfilehash: bcaed40082c694aa7271177e6c8040a06d02772b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207724"
---
# <a name="about-remote-requirements"></a><span data-ttu-id="77122-104">關於遠端需求</span><span class="sxs-lookup"><span data-stu-id="77122-104">About Remote Requirements</span></span>

## <a name="short-description"></a><span data-ttu-id="77122-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="77122-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="77122-106">描述在 PowerShell 中執行遠端命令的系統需求與設定需求。</span><span class="sxs-lookup"><span data-stu-id="77122-106">Describes the system requirements and configuration requirements for running remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="77122-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="77122-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="77122-108">本主題說明在 PowerShell 中建立遠端連線和執行遠端命令的系統需求、使用者需求和資源需求。</span><span class="sxs-lookup"><span data-stu-id="77122-108">This topic describes the system requirements, user requirements, and resource requirements for establishing remote connections and running remote commands in PowerShell.</span></span> <span data-ttu-id="77122-109">它也提供設定遠端作業的指示。</span><span class="sxs-lookup"><span data-stu-id="77122-109">It also provides instructions for configuring remote operations.</span></span>

<span data-ttu-id="77122-110">注意：許多 Cmdlet (包括 Get-help、>get-wmiobject、get-help、Get-EventLog 和 Get-WinEvent Cmdlet) 從遠端電腦取得物件，方法是使用 Microsoft .NET Framework 方法來取出物件。</span><span class="sxs-lookup"><span data-stu-id="77122-110">Note: Many cmdlets (including the Get-Service, Get-Process, Get-WMIObject, Get-EventLog, and Get-WinEvent cmdlets) get objects from remote computers by using Microsoft .NET Framework methods to retrieve the objects.</span></span> <span data-ttu-id="77122-111">它們不會使用 PowerShell 遠端基礎結構。</span><span class="sxs-lookup"><span data-stu-id="77122-111">They do not use the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="77122-112">本檔中的需求不適用於這些 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77122-112">The requirements in this document do not apply to these cmdlets.</span></span>

<span data-ttu-id="77122-113">若要尋找具有 ComputerName 參數但未使用 PowerShell 遠端的 Cmdlet，請閱讀 Cmdlet 的 ComputerName 參數描述。</span><span class="sxs-lookup"><span data-stu-id="77122-113">To find the cmdlets that have a ComputerName parameter but do not use PowerShell remoting, read the description of the ComputerName parameter of the cmdlets.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="77122-114">系統需求</span><span class="sxs-lookup"><span data-stu-id="77122-114">SYSTEM REQUIREMENTS</span></span>

<span data-ttu-id="77122-115">若要在 Windows PowerShell 3.0 上執行遠端會話，本機和遠端電腦必須具有下列各項：</span><span class="sxs-lookup"><span data-stu-id="77122-115">To run remote sessions on Windows PowerShell 3.0, the local and remote computers must have the following:</span></span>

- <span data-ttu-id="77122-116">Windows PowerShell 3.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="77122-116">Windows PowerShell 3.0 or later</span></span>
- <span data-ttu-id="77122-117">Microsoft .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="77122-117">The Microsoft .NET Framework 4 or later</span></span>
- <span data-ttu-id="77122-118">Windows 遠端管理3。0</span><span class="sxs-lookup"><span data-stu-id="77122-118">Windows Remote Management 3.0</span></span>

<span data-ttu-id="77122-119">若要在 Windows PowerShell 2.0 上執行遠端會話，本機和遠端電腦必須具有下列各項：</span><span class="sxs-lookup"><span data-stu-id="77122-119">To run remote sessions on Windows PowerShell 2.0, the local and remote computers must have the following:</span></span>

- <span data-ttu-id="77122-120">Windows PowerShell 2.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="77122-120">Windows PowerShell 2.0 or later</span></span>
- <span data-ttu-id="77122-121">Microsoft .NET Framework 2.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="77122-121">The Microsoft .NET Framework 2.0 or later</span></span>
- <span data-ttu-id="77122-122">Windows 遠端管理2。0</span><span class="sxs-lookup"><span data-stu-id="77122-122">Windows Remote Management 2.0</span></span>

<span data-ttu-id="77122-123">您可以在執行 Windows PowerShell 2.0 和 Windows PowerShell 3.0 的電腦之間建立遠端會話。</span><span class="sxs-lookup"><span data-stu-id="77122-123">You can create remote sessions between computers running Windows PowerShell 2.0 and Windows PowerShell 3.0.</span></span> <span data-ttu-id="77122-124">不過，只有當兩部電腦都在執行 Windows PowerShell 3.0 時，才可使用在 Windows PowerShell 3.0 上執行的功能，例如中斷連線和重新連線至會話的能力。</span><span class="sxs-lookup"><span data-stu-id="77122-124">However, features that run only on Windows PowerShell 3.0, such as the ability to disconnect and reconnect to sessions, are available only when both computers are running Windows PowerShell 3.0.</span></span>

<span data-ttu-id="77122-125">若要尋找已安裝之 PowerShell 版本的版本號碼，請使用 $PSVersionTable 自動變數。</span><span class="sxs-lookup"><span data-stu-id="77122-125">To find the version number of an installed version of PowerShell, use the $PSVersionTable automatic variable.</span></span>

<span data-ttu-id="77122-126">Windows 8、Windows Server 2012 和更新版本的 Windows 作業系統包含 Windows 遠端管理 (WinRM) 3.0 和 Microsoft .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="77122-126">Windows Remote Management (WinRM) 3.0 and Microsoft .NET Framework 4 are included in Windows 8, Windows Server 2012, and newer releases of the Windows operating system.</span></span> <span data-ttu-id="77122-127">舊版作業系統的 Windows Management Framework 3.0 包含 WinRM 3.0。</span><span class="sxs-lookup"><span data-stu-id="77122-127">WinRM 3.0 is included in Windows Management Framework 3.0 for older operating systems.</span></span> <span data-ttu-id="77122-128">如果電腦沒有必要的 WinRM 版本或 Microsoft .NET Framework，則安裝會失敗。</span><span class="sxs-lookup"><span data-stu-id="77122-128">If the computer does not have the required version of WinRM or the Microsoft .NET Framework, the installation fails.</span></span>

## <a name="user-permissions"></a><span data-ttu-id="77122-129">使用者權限</span><span class="sxs-lookup"><span data-stu-id="77122-129">USER PERMISSIONS</span></span>

<span data-ttu-id="77122-130">若要建立遠端會話並執行遠端命令，預設的使用者必須是遠端電腦上 Administrators 群組的成員，或是提供系統管理員的認證。</span><span class="sxs-lookup"><span data-stu-id="77122-130">To create remote sessions and run remote commands, by default, the current user must be a member of the Administrators group on the remote computer or provide the credentials of an administrator.</span></span> <span data-ttu-id="77122-131">否則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="77122-131">Otherwise, the command fails.</span></span>

<span data-ttu-id="77122-132">在遠端電腦上建立會話和執行命令所需的許可權 (或本機電腦上的遠端會話) 是由會話設定 (也稱為「端點」 ) 在會話連線的遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="77122-132">The permissions required to create sessions and run commands on a remote computer (or in a remote session on the local computer) are established by the session configuration (also known as an "endpoint") on the remote computer to which the session connects.</span></span> <span data-ttu-id="77122-133">具體而言，會話設定上的安全描述項會決定誰可以存取會話設定，以及誰可以使用它來連接。</span><span class="sxs-lookup"><span data-stu-id="77122-133">Specifically, the security descriptor on the session configuration determines who has access to the session configuration and who can use it to connect.</span></span>

<span data-ttu-id="77122-134">預設會話設定的安全描述項、Microsoft.powershell32 和 Microsoft. 工作流程，只允許存取 Administrators 群組成員的許可權。</span><span class="sxs-lookup"><span data-stu-id="77122-134">The security descriptors on the default session configurations, Microsoft.PowerShell, Microsoft.PowerShell32, and Microsoft.PowerShell.Workflow, allow access only to members of the Administrators group.</span></span>

<span data-ttu-id="77122-135">如果目前的使用者沒有使用會話設定的許可權，則執行命令的命令 (（使用暫時性會話) 或在遠端電腦上建立持續性會話）將會失敗。</span><span class="sxs-lookup"><span data-stu-id="77122-135">If the current user doesn't have permission to use the session configuration, the command to run a command (which uses a temporary session) or create a persistent session on the remote computer fails.</span></span> <span data-ttu-id="77122-136">使用者可以使用 Cmdlet 的 ConfigurationName 參數來建立會話，以選取不同的會話設定（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="77122-136">The user can use the ConfigurationName parameter of cmdlets that create sessions to select a different session configuration, if one is available.</span></span>

<span data-ttu-id="77122-137">電腦上 Administrators 群組的成員可以藉由變更預設會話設定的安全描述項，以及建立具有不同安全描述項的新會話設定，來判斷誰有權從遠端連線到電腦。</span><span class="sxs-lookup"><span data-stu-id="77122-137">Members of the Administrators group on a computer can determine who has permission to connect to the computer remotely by changing the security descriptors on the default session configurations and by creating new session configurations with different security descriptors.</span></span>

<span data-ttu-id="77122-138">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="77122-138">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

## <a name="windows-network-locations"></a><span data-ttu-id="77122-139">WINDOWS 網路位置</span><span class="sxs-lookup"><span data-stu-id="77122-139">WINDOWS NETWORK LOCATIONS</span></span>

<span data-ttu-id="77122-140">從 Windows PowerShell 3.0 開始，Enable-PSRemoting Cmdlet 可以在私人、網域及公用網路上的用戶端和伺服器版本的 Windows 上啟用遠端功能。</span><span class="sxs-lookup"><span data-stu-id="77122-140">Beginning in Windows PowerShell 3.0, the Enable-PSRemoting cmdlet can enable remoting on client and server versions of Windows on private, domain, and public networks.</span></span>

<span data-ttu-id="77122-141">在具有私人和網域網路的 Windows server 版本上，Enable-PSRemoting Cmdlet 會建立允許不受限制的遠端存取的防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="77122-141">On server versions of Windows with private and domain networks, the Enable-PSRemoting cmdlet creates firewall rules that allow unrestricted remote access.</span></span> <span data-ttu-id="77122-142">它也會針對公用網路建立防火牆規則，以允許從相同本機子網的電腦進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="77122-142">It also creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span> <span data-ttu-id="77122-143">此本機子網防火牆規則預設會在公用網路上的 Windows server 版本上啟用，但 Enable-PSRemoting 會在變更或刪除時重新套用規則。</span><span class="sxs-lookup"><span data-stu-id="77122-143">This local subnet firewall rule is enabled by default on server versions of Windows on public networks, but Enable-PSRemoting reapplies the rule in case it was changed or deleted.</span></span>

<span data-ttu-id="77122-144">在具有私人和網域網路的 Windows 用戶端版本上，根據預設，Enable-PSRemoting Cmdlet 會建立允許不受限制的遠端存取的防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="77122-144">On client versions of Windows with private and domain networks, by default, the Enable-PSRemoting cmdlet creates firewall rules that allow unrestricted remote access.</span></span>

<span data-ttu-id="77122-145">若要在用戶端版本的 Windows 上啟用具有公用網路的遠端功能，請使用 Enable-PSRemoting Cmdlet 的 SkipNetworkProfileCheck 參數。</span><span class="sxs-lookup"><span data-stu-id="77122-145">To enable remoting on client versions of Windows with public networks, use the SkipNetworkProfileCheck parameter of the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="77122-146">它會建立防火牆規則，只允許來自相同本機子網的電腦進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="77122-146">It creates a firewall rule that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="77122-147">若要移除公用網路上的本機子網限制，並允許從用戶端和伺服器版本的 Windows 上的所有位置進行遠端存取，請使用 NetSecurity 模組中的 Set-NetFirewallRule Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77122-147">To remove the local subnet restriction on public networks and allow remote access from all locations on client and server versions of Windows, use the Set-NetFirewallRule cmdlet in the NetSecurity module.</span></span> <span data-ttu-id="77122-148">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="77122-148">Run the following command:</span></span>

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

<span data-ttu-id="77122-149">在 Windows PowerShell 2.0 中，在伺服器版本的 Windows 上，Enable-PSRemoting 會建立允許在所有網路上進行遠端存取的防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="77122-149">In Windows PowerShell 2.0, on server versions of Windows, Enable-PSRemoting creates firewall rules that permit remote access on all networks.</span></span>

<span data-ttu-id="77122-150">在 Windows PowerShell 2.0 中，在用戶端版本的 Windows 上，Enable-PSRemoting 只會在私人和網域網路上建立防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="77122-150">In Windows PowerShell 2.0, on client versions of Windows, Enable-PSRemoting creates firewall rules only on private and domain networks.</span></span> <span data-ttu-id="77122-151">如果網路位置是公用的，Enable-PSRemoting 會失敗。</span><span class="sxs-lookup"><span data-stu-id="77122-151">If the network location is public, Enable-PSRemoting fails.</span></span>

## <a name="run-as-administrator"></a><span data-ttu-id="77122-152">以系統管理員身分執行</span><span class="sxs-lookup"><span data-stu-id="77122-152">RUN AS ADMINISTRATOR</span></span>

<span data-ttu-id="77122-153">下列遠端操作需要系統管理員許可權：</span><span class="sxs-lookup"><span data-stu-id="77122-153">Administrator privileges are required for the following remoting operations:</span></span>

- <span data-ttu-id="77122-154">建立本機電腦的遠端連線。</span><span class="sxs-lookup"><span data-stu-id="77122-154">Establishing a remote connection to the local computer.</span></span> <span data-ttu-id="77122-155">這通常稱為「回送」案例。</span><span class="sxs-lookup"><span data-stu-id="77122-155">This is commonly known as a "loopback" scenario.</span></span>

- <span data-ttu-id="77122-156">管理本機電腦上的會話設定。</span><span class="sxs-lookup"><span data-stu-id="77122-156">Managing session configurations on the local computer.</span></span>

- <span data-ttu-id="77122-157">在本機電腦上進行 WS-Management 設定的查看與變更。</span><span class="sxs-lookup"><span data-stu-id="77122-157">Viewing and changing WS-Management settings on the local computer.</span></span> <span data-ttu-id="77122-158">這些是 WSMAN：磁片磁碟機的 LocalHost 節點中的設定。</span><span class="sxs-lookup"><span data-stu-id="77122-158">These are the settings in the LocalHost node of the WSMAN: drive.</span></span>

<span data-ttu-id="77122-159">若要執行這些工作，您必須使用 [以系統管理員身分執行] 選項啟動 PowerShell，即使您是本機電腦上 Administrators 群組的成員也一樣。</span><span class="sxs-lookup"><span data-stu-id="77122-159">To perform these tasks, you must start PowerShell with the "Run as administrator" option even if you are a member of the Administrators group on the local computer.</span></span>

<span data-ttu-id="77122-160">在 Windows 7 和 Windows Server 2008 R2 中，使用 [以系統管理員身分執行] 選項開始 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="77122-160">In Windows 7 and in Windows Server 2008 R2, to start Windows PowerShell with the "Run as administrator" option:</span></span>

1. <span data-ttu-id="77122-161">依序按一下 [開始]、[所有程式]、[附屬應用程式]，然後按一下 Windows PowerShell 資料夾。</span><span class="sxs-lookup"><span data-stu-id="77122-161">Click Start, click All Programs, click Accessories, and then click the Windows PowerShell folder.</span></span>
2. <span data-ttu-id="77122-162">在 [Windows PowerShell] 上按一下滑鼠右鍵，然後按一下 [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="77122-162">Right-click Windows PowerShell, and then click "Run as administrator".</span></span>

<span data-ttu-id="77122-163">若要使用 [以系統管理員身分執行] 選項開始 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="77122-163">To start Windows PowerShell with the "Run as administrator" option:</span></span>

1. <span data-ttu-id="77122-164">按一下 [開始]，按一下 [所有程式]，然後按一下 Windows PowerShell 資料夾。</span><span class="sxs-lookup"><span data-stu-id="77122-164">Click Start, click All Programs, and then click the Windows PowerShell folder.</span></span>
2. <span data-ttu-id="77122-165">在 [Windows PowerShell] 上按一下滑鼠右鍵，然後按一下 [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="77122-165">Right-click Windows PowerShell, and then click "Run as administrator".</span></span>

<span data-ttu-id="77122-166">[以系統管理員身分執行] 選項也適用于 Windows PowerShell 的其他 Windows 檔案總管專案，包括快捷方式。</span><span class="sxs-lookup"><span data-stu-id="77122-166">The "Run as administrator" option is also available in other Windows Explorer entries for Windows PowerShell, including shortcuts.</span></span> <span data-ttu-id="77122-167">只要以滑鼠右鍵按一下專案，然後按一下 [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="77122-167">Just right-click the item, and then click "Run as administrator".</span></span>

<span data-ttu-id="77122-168">當您從另一個程式（例如 Cmd.exe）開始 Windows PowerShell 時，請使用 [以系統管理員身分執行] 選項來啟動程式。</span><span class="sxs-lookup"><span data-stu-id="77122-168">When you start Windows PowerShell from another program such as Cmd.exe, use the "Run as administrator" option to start the program.</span></span>

## <a name="how-to-configure-your-computer-for-remoting"></a><span data-ttu-id="77122-169">如何設定您的電腦以進行遠端處理</span><span class="sxs-lookup"><span data-stu-id="77122-169">HOW TO CONFIGURE YOUR COMPUTER FOR REMOTING</span></span>

<span data-ttu-id="77122-170">執行所有支援的 Windows 版本的電腦可以在 PowerShell 中建立遠端連線並執行遠端命令，而不需要進行任何設定。</span><span class="sxs-lookup"><span data-stu-id="77122-170">Computers running all supported versions of Windows can establish remote connections to and run remote commands in PowerShell without any configuration.</span></span> <span data-ttu-id="77122-171">不過，若要接收連線，並允許使用者建立本機和遠端使用者管理的 PowerShell 會話 ( "Pssession" ) 並在本機電腦上執行命令，您必須在電腦上啟用 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="77122-171">However, to receive connections, and allow users to create local and remote user-managed PowerShell sessions ("PSSessions") and run commands on the local computer, you must enable PowerShell remoting on the computer.</span></span>

<span data-ttu-id="77122-172">Windows server 2012 和更新版本的 Windows Server 預設會啟用 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="77122-172">Windows Server 2012 and newer releases of Windows Server are enabled for PowerShell remoting by default.</span></span> <span data-ttu-id="77122-173">如果設定已變更，您可以執行 Enable-PSRemoting Cmdlet 來還原預設設定。</span><span class="sxs-lookup"><span data-stu-id="77122-173">If the settings are changed, you can restore the default settings by running the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="77122-174">在所有其他支援的 Windows 版本上，您必須執行 Enable-PSRemoting Cmdlet 以啟用 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="77122-174">On all other supported versions of Windows, you need to run the Enable-PSRemoting cmdlet to enable PowerShell remoting.</span></span>

<span data-ttu-id="77122-175">WinRM 服務支援 PowerShell 的遠端功能，也就是 Microsoft 管理 Web Services for Management (WS-MANAGEMENT) 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="77122-175">The remoting features of PowerShell are supported by the WinRM service, which is the Microsoft implementation of the Web Services for Management (WS-Management) protocol.</span></span> <span data-ttu-id="77122-176">當您啟用 PowerShell 遠端功能時，您會變更 WS-Management 的預設設定，並新增可讓使用者連線至 WS-MANAGEMENT 的系統組態。</span><span class="sxs-lookup"><span data-stu-id="77122-176">When you enable PowerShell remoting, you change the default configuration of WS-Management and add system configuration that allow users to connect to WS-Management.</span></span>

<span data-ttu-id="77122-177">若要將 PowerShell 設定為接收遠端命令：</span><span class="sxs-lookup"><span data-stu-id="77122-177">To configure PowerShell to receive remote commands:</span></span>

1. <span data-ttu-id="77122-178">使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="77122-178">Start PowerShell with the "Run as administrator" option.</span></span>
2. <span data-ttu-id="77122-179">在命令提示字元中，輸入：`Enable-PSRemoting`</span><span class="sxs-lookup"><span data-stu-id="77122-179">At the command prompt, type: `Enable-PSRemoting`</span></span>

<span data-ttu-id="77122-180">若要確認是否已正確設定遠端，請執行如下命令的測試命令，這會在本機電腦上建立遠端會話。</span><span class="sxs-lookup"><span data-stu-id="77122-180">To verify that remoting is configured correctly, run a test command such as the following command, which creates a remote session on the local computer.</span></span>

```powershell
New-PSSession
```

<span data-ttu-id="77122-181">如果已正確設定遠端，此命令會在本機電腦上建立會話，並傳回代表會話的物件。</span><span class="sxs-lookup"><span data-stu-id="77122-181">If remoting is configured correctly, the command will create a session on the local computer and return an object that represents the session.</span></span> <span data-ttu-id="77122-182">輸出應類似下列範例輸出：</span><span class="sxs-lookup"><span data-stu-id="77122-182">The output should resemble the following sample output:</span></span>

```output
Id Name        ComputerName    State    ConfigurationName
-- ----        ------------    -----    -----
1  Session1    localhost       Opened   Microsoft.PowerShell
```

<span data-ttu-id="77122-183">如果命令失敗，如需協助，請參閱 [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="77122-183">If the command fails, for assistance, see [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md).</span></span>

## <a name="understand-policies"></a><span data-ttu-id="77122-184">瞭解原則</span><span class="sxs-lookup"><span data-stu-id="77122-184">UNDERSTAND POLICIES</span></span>

<span data-ttu-id="77122-185">當您從遠端工作時，您會使用兩個 PowerShell 實例，一個在本機電腦上，另一個位於遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="77122-185">When you work remotely, you use two instances of PowerShell, one on the local computer and one on the remote computer.</span></span> <span data-ttu-id="77122-186">因此，您的工作會受到 Windows 原則和本機電腦和遠端電腦上的 PowerShell 原則影響。</span><span class="sxs-lookup"><span data-stu-id="77122-186">As a result, your work is affected by the Windows policies and the PowerShell policies on the local and remote computers.</span></span>

<span data-ttu-id="77122-187">一般情況下，在您連接之前，以及在建立連線之前，本機電腦上的原則都會生效。</span><span class="sxs-lookup"><span data-stu-id="77122-187">In general, before you connect and as you are establishing the connection, the policies on the local computer are in effect.</span></span> <span data-ttu-id="77122-188">當您使用此連接時，遠端電腦上的原則會生效。</span><span class="sxs-lookup"><span data-stu-id="77122-188">When you are using the connection, the policies on the remote computer are in effect.</span></span>

## <a name="basic-authentication-limitations-on-linux-and-macos"></a><span data-ttu-id="77122-189">Linux 和 macOS 上的基本驗證限制</span><span class="sxs-lookup"><span data-stu-id="77122-189">Basic Authentication Limitations on Linux and macOS</span></span>

<span data-ttu-id="77122-190">從 Linux 或 macOS 系統連接到 Windows 時，不支援透過 HTTP 進行基本驗證。</span><span class="sxs-lookup"><span data-stu-id="77122-190">When connecting from a Linux or macOS system to Windows, Basic Authentication over HTTP is not supported.</span></span> <span data-ttu-id="77122-191">您可以在目標伺服器上安裝憑證，透過 HTTPS 使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="77122-191">Basic Authentication can be used over HTTPS by installing a certificate on the target server.</span></span> <span data-ttu-id="77122-192">憑證的 CN 名稱必須符合主機名稱、未過期或已撤銷。</span><span class="sxs-lookup"><span data-stu-id="77122-192">The certificate must have a CN name that matches the hostname, is not expired or revoked.</span></span> <span data-ttu-id="77122-193">自我簽署憑證可用於測試用途。</span><span class="sxs-lookup"><span data-stu-id="77122-193">A self-signed certificate may be used for testing purposes.</span></span>

<span data-ttu-id="77122-194">如需其他詳細資料，請參閱 [如何：設定 WINRM FOR HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) 。</span><span class="sxs-lookup"><span data-stu-id="77122-194">See [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) for additional details.</span></span>

<span data-ttu-id="77122-195">下列命令會從提高許可權的命令提示字元中執行，並使用已安裝的憑證，在 Windows 上設定 HTTPS 接聽程式。</span><span class="sxs-lookup"><span data-stu-id="77122-195">The following command, run from an elevated command prompt, will configure the HTTPS listener on Windows with the installed certificate.</span></span>

```powershell
$hostinfo = '@{Hostname="<DNS_NAME>"; CertificateThumbprint="<THUMBPRINT>"}'
winrm create winrm/config/Listener?Address=*+Transport=HTTPS $hostinfo
```

<span data-ttu-id="77122-196">在 Linux 或 macOS 端上，選取 [基本] 以進行驗證和-UseSSl。</span><span class="sxs-lookup"><span data-stu-id="77122-196">On the Linux or macOS side, select Basic for authentication and -UseSSl.</span></span>

> <span data-ttu-id="77122-197">注意：基本驗證無法與網域帳戶搭配使用。需要本機帳戶，而且該帳戶必須在 Administrators 群組中。</span><span class="sxs-lookup"><span data-stu-id="77122-197">NOTE: Basic authentication cannot be used with domain accounts; a local account is required and the account must be in the Administrators group.</span></span>

```powershell
# The specified local user must have administrator rights on the target machine.
# Specify the unqualified username.
$cred = Get-Credential username
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Basic -UseSSL
```

<span data-ttu-id="77122-198">透過 HTTPS 進行基本驗證的替代方案是 Negotiate。</span><span class="sxs-lookup"><span data-stu-id="77122-198">An alternative to Basic Authentication over HTTPS is Negotiate.</span></span> <span data-ttu-id="77122-199">這會導致用戶端和伺服器之間的 NTLM 驗證，以及透過 HTTP 加密的承載。</span><span class="sxs-lookup"><span data-stu-id="77122-199">This results in NTLM authentication between the client and server and payload is encrypted over HTTP.</span></span>

<span data-ttu-id="77122-200">以下說明如何搭配使用 Negotiate 與新的-PSSession：</span><span class="sxs-lookup"><span data-stu-id="77122-200">The following illustrates using Negotiate with New-PSSession:</span></span>

```powershell
# The specified user must have administrator rights on the target machine.
$cred = Get-Credential username@hostname
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Negotiate
```

> [!NOTE]
> <span data-ttu-id="77122-201">Windows Server 需要額外的登錄設定，才能讓系統管理員（而非內建的系統管理員）使用 NTLM 進行連接。</span><span class="sxs-lookup"><span data-stu-id="77122-201">Windows Server requires an additional registry setting to enable administrators, other than the built in administrator, to connect using NTLM.</span></span>
> <span data-ttu-id="77122-202">[針對遠端](/windows/win32/winrm/authentication-for-remote-connections)連線，請參閱 [驗證中的協商驗證] 底下的 LocalAccountTokenFilterPolicy 登錄設定</span><span class="sxs-lookup"><span data-stu-id="77122-202">Refer to the LocalAccountTokenFilterPolicy registry setting under Negotiate Authentication in [Authentication for Remote Connections](/windows/win32/winrm/authentication-for-remote-connections)</span></span>

## <a name="see-also"></a><span data-ttu-id="77122-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77122-203">SEE ALSO</span></span>

[<span data-ttu-id="77122-204">about_Remote</span><span class="sxs-lookup"><span data-stu-id="77122-204">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="77122-205">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="77122-205">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="77122-206">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="77122-206">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="77122-207">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="77122-207">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="77122-208">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="77122-208">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="77122-209">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="77122-209">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

