---
description: 描述工作階段設定，這會決定可以從遠端連線到電腦的使用者，以及他們可以執行的命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 0956e2e96cb67d1c4b8c3ef245c6fa084b781351
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206871"
---
# <a name="about-session-configurations"></a><span data-ttu-id="45c1c-104">關於會話設定</span><span class="sxs-lookup"><span data-stu-id="45c1c-104">About Session Configurations</span></span>

## <a name="short-description"></a><span data-ttu-id="45c1c-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="45c1c-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="45c1c-106">描述工作階段設定，這會決定可以從遠端連線到電腦的使用者，以及他們可以執行的命令。</span><span class="sxs-lookup"><span data-stu-id="45c1c-106">Describes session configurations, which determine the users who can connect to the computer remotely and the commands they can run.</span></span>

## <a name="long-description"></a><span data-ttu-id="45c1c-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="45c1c-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="45c1c-108">會話設定（也稱為「端點」）是本機電腦上的一組設定，可定義當遠端或本機使用者連接到本機電腦上的 PowerShell 時所建立的 PowerShell 會話環境。</span><span class="sxs-lookup"><span data-stu-id="45c1c-108">A session configuration, also known as an "endpoint" is a group of settings on the local computer that define the environment for the PowerShell sessions that are created when remote or local users connect to PowerShell on the local computer.</span></span>

<span data-ttu-id="45c1c-109">電腦的系統管理員可以使用會話設定來保護電腦，以及為連接到電腦的使用者定義自訂環境。</span><span class="sxs-lookup"><span data-stu-id="45c1c-109">Administrators of the computer can use session configurations to protect the computer and to define custom environments for users who connect to the computer.</span></span>

<span data-ttu-id="45c1c-110">系統管理員也可以使用會話設定，判斷從遠端連線到電腦所需的許可權。</span><span class="sxs-lookup"><span data-stu-id="45c1c-110">Administrators can also use session configurations to determine the permissions that are required to connect to the computer remotely.</span></span> <span data-ttu-id="45c1c-111">依預設，只有 Administrators 群組的成員才有許可權可以使用會話設定從遠端連線，但您可以變更預設設定以允許所有使用者或選取的使用者從遠端連線到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="45c1c-111">By default, only members of the Administrators group have permission to use the session configuration to connect remotely, but you can change the default settings to allow all users, or selected users, to connect remotely to your computer.</span></span>

<span data-ttu-id="45c1c-112">從 PowerShell 3.0 開始，您可以使用會話設定檔來定義會話設定的元素。</span><span class="sxs-lookup"><span data-stu-id="45c1c-112">Beginning in PowerShell 3.0, you can use a session configuration file to define the elements of a session configuration.</span></span> <span data-ttu-id="45c1c-113">這項功能可讓您輕鬆自訂會話，而不需要撰寫程式碼及探索會話設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="45c1c-113">This feature makes it easy to customize sessions without writing code and to discover the properties of a session configuration.</span></span> <span data-ttu-id="45c1c-114">若要建立會話設定檔，請使用 New-PSSessionConfiguration Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45c1c-114">To create a session configuration file, use the New-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="45c1c-115">如需有關工作階段設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files](about_Session_Configuration_Files.md)。</span><span class="sxs-lookup"><span data-stu-id="45c1c-115">For more information about session configuration files, see [about_Session_Configuration_Files](about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="45c1c-116">會話設定是 Web 服務的管理功能 (WS-MANAGEMENT) 架構的 PowerShell 遠端處理。</span><span class="sxs-lookup"><span data-stu-id="45c1c-116">Session configurations are a feature of Web Services for Management (WS-Management) based PowerShell remoting.</span></span> <span data-ttu-id="45c1c-117">只有當您使用新的-PSSession、Invoke 命令或 Enter-PSSession Cmdlet 來連接到遠端電腦時，才會使用它們。</span><span class="sxs-lookup"><span data-stu-id="45c1c-117">They are used only when you use the New-PSSession, Invoke-Command, or Enter-PSSession cmdlets to connect to a remote computer.</span></span>

<span data-ttu-id="45c1c-118">注意：若要管理會話設定，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="45c1c-118">Note: To manage the session configurations, start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="45c1c-119">關於會話設定</span><span class="sxs-lookup"><span data-stu-id="45c1c-119">About Session Configurations</span></span>

<span data-ttu-id="45c1c-120">每個 PowerShell 會話都會使用會話設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-120">Every PowerShell session uses a session configuration.</span></span> <span data-ttu-id="45c1c-121">這包括您使用 New-PSSession 或 Enter-PSSession Cmdlet 建立的持續性會話，以及當您使用使用以 WS-MANAGEMENT 為基礎的遠端處理技術（例如 Invoke 命令）之 Cmdlet 的 ComputerName 參數時，PowerShell 所建立的暫時會話。</span><span class="sxs-lookup"><span data-stu-id="45c1c-121">This includes persistent sessions that you create by using the New-PSSession or Enter-PSSession cmdlets, and the temporary sessions that PowerShell creates when you use the ComputerName parameter of a cmdlet that uses WS-Management-based remoting technology, such as Invoke-Command.</span></span>

<span data-ttu-id="45c1c-122">系統管理員可以使用會話設定來保護電腦的資源，以及為連接到電腦的使用者建立自訂環境。</span><span class="sxs-lookup"><span data-stu-id="45c1c-122">Administrators can use session configurations to protect the resources of the computer and to create custom environments for users who connect to the computer.</span></span> <span data-ttu-id="45c1c-123">例如，您可以使用會話設定來限制電腦在會話中收到的物件大小、定義會話的語言模式，以及指定可在會話中使用的 Cmdlet、提供者和功能。</span><span class="sxs-lookup"><span data-stu-id="45c1c-123">For example, you can use a session configuration to limit the size of objects that the computer receives in the session, to define the language mode of the session, and to specify the cmdlets, providers, and functions that are available in the session.</span></span>

<span data-ttu-id="45c1c-124">您可以藉由設定會話設定的安全描述項，判斷誰可以使用會話設定連接到電腦。</span><span class="sxs-lookup"><span data-stu-id="45c1c-124">By configuring the security descriptor of a session configuration, you determine who can use the session configuration to connect to the computer.</span></span>
<span data-ttu-id="45c1c-125">使用者必須擁有會話設定的 Execute 許可權，才能在會話中使用它。</span><span class="sxs-lookup"><span data-stu-id="45c1c-125">Users must have Execute permission to a session configuration to use it in a session.</span></span> <span data-ttu-id="45c1c-126">如果使用者沒有在電腦上使用任何會話設定的必要許可權，則使用者將無法從遠端連線到電腦。</span><span class="sxs-lookup"><span data-stu-id="45c1c-126">If a user does not have the required permissions to use any of the session configurations on a computer, the user cannot connect to the computer remotely.</span></span>

<span data-ttu-id="45c1c-127">依預設，只有電腦的系統管理員具有使用預設會話設定的許可權。</span><span class="sxs-lookup"><span data-stu-id="45c1c-127">By default, only Administrators of the computer have permission to use the default session configurations.</span></span> <span data-ttu-id="45c1c-128">但是，您可以變更安全描述項，讓所有人、沒有人或只有選取的使用者使用您電腦上的會話設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-128">But, you can change the security descriptors to allow everyone, no one, or only selected users to use the session configurations on your computer.</span></span>

<span data-ttu-id="45c1c-129">內建會話設定</span><span class="sxs-lookup"><span data-stu-id="45c1c-129">Built-in Session Configurations</span></span>

<span data-ttu-id="45c1c-130">PowerShell 3.0 包含內建的會話設定，名稱為 Microsoft PowerShell 和 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="45c1c-130">PowerShell 3.0 includes built-in session configurations named Microsoft.PowerShell and Microsoft.PowerShell.Workflow.</span></span> <span data-ttu-id="45c1c-131">在執行 Windows 64 位版本的電腦上，PowerShell 也會提供 Microsoft.powershell32，也就是32位的會話設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-131">On computers running 64-bit versions of Windows, PowerShell also provides Microsoft.PowerShell32, a 32-bit session configuration.</span></span>

<span data-ttu-id="45c1c-132">依預設，會話會使用 Microsoft PowerShell 會話設定，也就是建立會話的命令不包含新的-PSSession、輸入-PSSession 或 Invoke-Command Cmdlet 的 ConfigurationName 參數。</span><span class="sxs-lookup"><span data-stu-id="45c1c-132">The Microsoft.PowerShell session configuration is used for sessions by default, that is, when a command to create a session does not include the ConfigurationName parameter of the New-PSSession, Enter-PSSession, or Invoke-Command cmdlet.</span></span>

<span data-ttu-id="45c1c-133">預設會話設定的安全描述項只允許本機電腦上的 Administrators 群組成員使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-133">The security descriptors for the default session configurations allow only members of the Administrators group on the local computer to use them.</span></span> <span data-ttu-id="45c1c-134">因此，除非您變更預設設定，否則只有 Administrators 群組的成員可以從遠端連線到電腦。</span><span class="sxs-lookup"><span data-stu-id="45c1c-134">As such, only members of the Administrators group can connect to the computer remotely unless you change the default settings.</span></span>

<span data-ttu-id="45c1c-135">您可以使用 $PSSessionConfigurationName 喜好設定變數來變更預設的會話設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-135">You can change the default session configurations by using the $PSSessionConfigurationName preference variable.</span></span> <span data-ttu-id="45c1c-136">如需詳細資訊，請參閱 about_Preference_Variables。</span><span class="sxs-lookup"><span data-stu-id="45c1c-136">For more information, see about_Preference_Variables.</span></span>

<span data-ttu-id="45c1c-137">在本機電腦上查看會話設定</span><span class="sxs-lookup"><span data-stu-id="45c1c-137">Viewing Session Configurations on the Local Computer</span></span>

<span data-ttu-id="45c1c-138">若要取得本機電腦上的會話設定，請使用 Get-PSSessionConfiguration Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45c1c-138">To get the session configurations on your local computer, use the Get-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="45c1c-139">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="45c1c-139">For example, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

<span data-ttu-id="45c1c-140">會話設定物件會在 PowerShell 3.0 中展開，以顯示使用會話設定檔所設定的會話設定屬性。</span><span class="sxs-lookup"><span data-stu-id="45c1c-140">The session configuration object is expanded in PowerShell 3.0 to display the properties of the session configuration that are configured by using a session configuration file.</span></span>

<span data-ttu-id="45c1c-141">例如，若要查看會話設定物件的所有屬性，請輸入：</span><span class="sxs-lookup"><span data-stu-id="45c1c-141">For example, to see all of the properties of a session configuration object, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

<span data-ttu-id="45c1c-142">您也可以使用 PowerShell 中的 WSMan 提供者來查看會話設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-142">You can also use the WSMan provider in PowerShell to view session configurations.</span></span> <span data-ttu-id="45c1c-143">WSMan 提供者會在您的會話中建立 WSMAN：磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="45c1c-143">The WSMan provider creates a WSMAN: drive in your session.</span></span>

<span data-ttu-id="45c1c-144">在 WSMAN：磁片磁碟機中，會話設定位於外掛程式節點中。</span><span class="sxs-lookup"><span data-stu-id="45c1c-144">In the WSMAN: drive, session configurations are in the Plugin node.</span></span> <span data-ttu-id="45c1c-145"> (所有會話設定都位於外掛程式節點中，但外掛程式節點中有不是會話設定的專案。 ) </span><span class="sxs-lookup"><span data-stu-id="45c1c-145">(All session configurations are in the Plugin node, but there are items in the Plugin node that are not session configurations.)</span></span>

<span data-ttu-id="45c1c-146">例如，若要查看本機電腦上的會話設定，請輸入：</span><span class="sxs-lookup"><span data-stu-id="45c1c-146">For example, to view the session configurations on the local computer, type:</span></span>

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="45c1c-147">在遠端電腦上查看會話設定</span><span class="sxs-lookup"><span data-stu-id="45c1c-147">Viewing Session Configurations on a Remote Computer</span></span>

<span data-ttu-id="45c1c-148">若要查看遠端電腦上的會話設定，請使用 Connect-WSMan Cmdlet 將遠端電腦的附注新增至本機電腦上的 WSMAN：磁片磁碟機，然後使用 WSMAN：磁片磁碟機來查看會話設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-148">To view the session configurations on a remote computer, use the Connect-WSMan cmdlet to add a note for the remote computer to the WSMAN: drive on your local computer, and then use the WSMAN: drive to view the session configurations.</span></span>

<span data-ttu-id="45c1c-149">例如，下列命令會將 Server01 遠端電腦的節點新增到本機電腦上的 WSMAN：磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="45c1c-149">For example, the following command adds a node for the Server01 remote computer to the WSMAN: drive on the local computer.</span></span>

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

<span data-ttu-id="45c1c-150">當命令完成時，您可以流覽至 Server01 電腦的節點，以查看會話設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-150">When the command is complete, you can navigate to the node for the Server01 computer to view the session configurations.</span></span>

<span data-ttu-id="45c1c-151">例如：</span><span class="sxs-lookup"><span data-stu-id="45c1c-151">For example:</span></span>

```powershell
PS C:> cd wsman:

PS WSMan:> dir

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01.corp.fabrikam.com                    Container

PS WSMan:> dir server01\plugin\

WSManConfig: Microsoft.WSMan.Management\WSMan::server01.corp.fabrikam.com\Pl
ugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="45c1c-152">變更會話設定的安全描述項</span><span class="sxs-lookup"><span data-stu-id="45c1c-152">Changing the Security Descriptor of a Session Configuration</span></span>

<span data-ttu-id="45c1c-153">在 Windows Server 2012 和更新版本的 Windows Server 中，預設會為遠端使用者啟用內建的會話設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-153">In Windows Server 2012 and newer releases of Windows Server, the built-in session configurations are enabled for remote users by default.</span></span> <span data-ttu-id="45c1c-154">在其他支援的 Windows 版本中，您必須變更會話設定的安全描述項，以允許遠端存取。</span><span class="sxs-lookup"><span data-stu-id="45c1c-154">In other supported versions of Windows, you must change the security descriptors of the session configurations to allow remote access.</span></span>

<span data-ttu-id="45c1c-155">若要啟用電腦上會話設定的遠端存取，請使用 Enable-PSRemoting Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45c1c-155">To enable remote access to the session configurations on the computer, use the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="45c1c-156">此 Cmdlet 會建立兩個會話設定：</span><span class="sxs-lookup"><span data-stu-id="45c1c-156">This cmdlet creates two session configurations:</span></span>

- <span data-ttu-id="45c1c-157">將名稱定義為： "PowerShell"。</span><span class="sxs-lookup"><span data-stu-id="45c1c-157">with the name defined as: "PowerShell."</span></span> <span data-ttu-id="45c1c-158">+ "目前的 PowerShell 版本"</span><span class="sxs-lookup"><span data-stu-id="45c1c-158">+ "current PowerShell version"</span></span>
- <span data-ttu-id="45c1c-159">使用名稱 "PowerShell. 6"，untied 至任何特定的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="45c1c-159">with name "PowerShell.6", untied to any specific PowerShell version.</span></span>

<span data-ttu-id="45c1c-160">此外，根據預設，只有電腦上 Administrators 群組的成員具有預設會話設定的 [執行] 許可權，但您可以變更預設會話設定的安全描述項，以及您所建立之任何會話設定的安全性描述項。</span><span class="sxs-lookup"><span data-stu-id="45c1c-160">Also, by default, only members of the Administrators group on the computer have Execute permission to the default session configurations, but you can change the security descriptors on the default session configurations and on any session configurations that you create.</span></span>

<span data-ttu-id="45c1c-161">若要授與其他使用者從遠端連線到電腦的許可權，請使用 Set-PSSessionConfiguration Cmdlet 將這些使用者的「執行」許可權新增至 Microsoft.powershell32 會話設定的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="45c1c-161">To give other users permission to connect to the computer remotely, use the Set-PSSessionConfiguration cmdlet to add "Execute" permissions for those users to the security descriptors of the Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span>

<span data-ttu-id="45c1c-162">例如，下列命令會開啟屬性頁，讓您變更 Microsoft PowerShell 預設會話設定的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="45c1c-162">For example, the following command opens a property page that lets you change the security descriptor for the Microsoft.PowerShell default session configuration.</span></span>

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="45c1c-163">若要拒絕所有使用者對電腦上所有會話設定的許可權，請使用 Disable-PSSessionConfiguration Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45c1c-163">To deny everyone permission to all the session configurations on the computer, use the Disable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="45c1c-164">例如，下列命令會停用電腦上的預設會話設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-164">For example, the following command disables the default session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

<span data-ttu-id="45c1c-165">若要防止遠端使用者連線到電腦，但允許本機使用者連接，請使用 Disable-PSRemoting Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45c1c-165">To prevent remote users from connecting to the computer, but allow local users to connect, use the Disable-PSRemoting cmdlet.</span></span> <span data-ttu-id="45c1c-166">Disable-PSRemoting 將 "Network_Deny_All" 專案新增到電腦上的所有會話設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-166">Disable-PSRemoting adds a "Network_Deny_All" entry to all session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSRemoting
```

<span data-ttu-id="45c1c-167">若要允許遠端使用者使用電腦上的所有會話設定，請使用 Enable-PSRemoting 或 Enable-PSSessionConfiguration Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45c1c-167">To allow remote users to use all session configurations on the computer, use the Enable-PSRemoting or Enable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="45c1c-168">例如，下列命令會啟用內建會話設定的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="45c1c-168">For example, the following command enables remote access to the built-in session configurations.</span></span>

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

<span data-ttu-id="45c1c-169">若要對會話設定的安全描述項進行其他變更，請使用 Set-PSSessionConfiguration Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45c1c-169">To make other changes to the security descriptor of a session configuration, use the Set-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="45c1c-170">使用 SecurityDescriptorSDDL 參數來提交 SDDL 字串值。</span><span class="sxs-lookup"><span data-stu-id="45c1c-170">Use the SecurityDescriptorSDDL parameter to submit an SDDL string value.</span></span> <span data-ttu-id="45c1c-171">使用 ShowSecurityDescriptorUI 參數來顯示使用者介面屬性工作表，以協助您建立新的 SDDL。</span><span class="sxs-lookup"><span data-stu-id="45c1c-171">Use the ShowSecurityDescriptorUI parameter to display a user interface property sheet that helps you to create a new SDDL.</span></span>

<span data-ttu-id="45c1c-172">例如：</span><span class="sxs-lookup"><span data-stu-id="45c1c-172">For example:</span></span>

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="45c1c-173">建立新的會話設定</span><span class="sxs-lookup"><span data-stu-id="45c1c-173">Creating a New Session Configuration</span></span>

<span data-ttu-id="45c1c-174">若要在本機電腦上建立新的會話設定，請使用 Register-PSSessionConfiguration Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45c1c-174">To create a new session configuration on the local computer, use the Register-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="45c1c-175">若要定義新的會話設定，您可以使用 c # 元件、PowerShell 腳本，以及 Register-PSSessionConfiguration Cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="45c1c-175">To define the new session configuration, you can use a C# assembly, a PowerShell script, and the parameters of the Register-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="45c1c-176">例如，下列命令會建立與 Microsoft PowerShell 會話設定相同的會話設定，不同之處在于它會將從遠端命令接收的資料限制為 20 mb 的 (MB) 。</span><span class="sxs-lookup"><span data-stu-id="45c1c-176">For example, the following command creates a session configuration that is identical the Microsoft.PowerShell session configuration, except that it limits the data received from a remote command to 20 megabytes (MB).</span></span> <span data-ttu-id="45c1c-177"> (預設值為 50 MB) 。</span><span class="sxs-lookup"><span data-stu-id="45c1c-177">(The default is 50 MB).</span></span>

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

<span data-ttu-id="45c1c-178">當您建立會話設定時，您可以使用其他會話設定 Cmdlet 來管理它，它會出現在 WSMAN：磁片磁碟機中。</span><span class="sxs-lookup"><span data-stu-id="45c1c-178">When you create a session configuration, you can manage it by using the other session configuration cmdlets, and it appears in the WSMAN: drive.</span></span>

<span data-ttu-id="45c1c-179">如需詳細資訊，請參閱 PSSessionConfiguration。</span><span class="sxs-lookup"><span data-stu-id="45c1c-179">For more information, see Register-PSSessionConfiguration.</span></span>

<span data-ttu-id="45c1c-180">移除會話設定</span><span class="sxs-lookup"><span data-stu-id="45c1c-180">Removing a Session Configuration</span></span>

<span data-ttu-id="45c1c-181">若要從本機電腦移除會話設定，請使用 Unregister-PSSessionConfiguration Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45c1c-181">To remove a session configuration from the local computer, use the Unregister-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="45c1c-182">例如，下列命令會從電腦移除 >newconfig.json 會話設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-182">For example, the following command removes the NewConfig session configuration from the computer.</span></span>

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

<span data-ttu-id="45c1c-183">如需詳細資訊，請參閱取消登錄-PSSessionConfiguration。</span><span class="sxs-lookup"><span data-stu-id="45c1c-183">For more information, see Unregister-PSSessionConfiguration.</span></span>

<span data-ttu-id="45c1c-184">還原會話設定</span><span class="sxs-lookup"><span data-stu-id="45c1c-184">Restoring a Session Configuration</span></span>

<span data-ttu-id="45c1c-185">若要還原已刪除的預設會話設定 (未) 意外註冊，請使用 Enable-PSRemoting Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45c1c-185">To restore a default session configuration that was deleted (unregistered) accidentally, use the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="45c1c-186">Enable-PSRemoting Cmdlet 會重新建立所有不存在於電腦上的預設會話設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-186">The Enable-PSRemoting cmdlet recreates all default sessions configurations that do not exist on the computer.</span></span> <span data-ttu-id="45c1c-187">它不會覆寫或變更現有會話設定的屬性值。</span><span class="sxs-lookup"><span data-stu-id="45c1c-187">It does not overwrite or change the property values of existing session configurations.</span></span>

<span data-ttu-id="45c1c-188">若要還原預設會話設定的原始屬性值，請使用 Unregister-PSSessionConfiguration 刪除會話設定，然後使用 Enable-PSRemoting Cmdlet 來重新建立它。</span><span class="sxs-lookup"><span data-stu-id="45c1c-188">To restore the original property values of a default session configuration, use the Unregister-PSSessionConfiguration to delete the session configuration and then use the Enable-PSRemoting cmdlet to recreate it.</span></span>

<span data-ttu-id="45c1c-189">選取會話設定</span><span class="sxs-lookup"><span data-stu-id="45c1c-189">Selecting a Session Configuration</span></span>

<span data-ttu-id="45c1c-190">若要選取會話的特定會話設定，請使用新的-PSSession、輸入-PSSession 或 Invoke 命令的 ConfigurationName 參數。</span><span class="sxs-lookup"><span data-stu-id="45c1c-190">To select a particular session configuration for a session, use the ConfigurationName parameter of New-PSSession, Enter-PSSession, or Invoke-Command.</span></span>

<span data-ttu-id="45c1c-191">例如，此命令會使用 New-PSSession Cmdlet 來啟動 Server01 電腦上的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="45c1c-191">For example, this command uses the New-PSSession cmdlet to start a PSSession on the Server01 computer.</span></span> <span data-ttu-id="45c1c-192">此命令會使用 ConfigurationName 參數來選取 Server01 電腦上的 WithProfile 設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-192">The command uses the ConfigurationName parameter to select the WithProfile configuration on the Server01 computer.</span></span>

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

<span data-ttu-id="45c1c-193">只有當目前的使用者具有使用 WithProfile 會話設定的許可權，或可提供擁有必要許可權之使用者的認證時，此命令才會成功。</span><span class="sxs-lookup"><span data-stu-id="45c1c-193">This command will succeed only if the current user has permission to use the WithProfile session configuration or can supply the credentials of a user who has the required permissions.</span></span>

<span data-ttu-id="45c1c-194">您也可以使用 $PSSessionConfigurationName 喜好設定變數來變更電腦上的預設會話設定。</span><span class="sxs-lookup"><span data-stu-id="45c1c-194">You can also use the $PSSessionConfigurationName preference variable to change the default session configuration on the computer.</span></span> <span data-ttu-id="45c1c-195">如需 $PSSessionConfigurationName 喜好設定變數的詳細資訊，請參閱 about_Preference_Variables。</span><span class="sxs-lookup"><span data-stu-id="45c1c-195">For more information about the $PSSessionConfigurationName preference variable, see about_Preference_Variables.</span></span>

## <a name="keywords"></a><span data-ttu-id="45c1c-196">關鍵 字</span><span class="sxs-lookup"><span data-stu-id="45c1c-196">KEYWORDS</span></span>

<span data-ttu-id="45c1c-197">about_Endpoints about_SessionConfigurations</span><span class="sxs-lookup"><span data-stu-id="45c1c-197">about_Endpoints about_SessionConfigurations</span></span>

## <a name="see-also"></a><span data-ttu-id="45c1c-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45c1c-198">SEE ALSO</span></span>

[<span data-ttu-id="45c1c-199">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="45c1c-199">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="45c1c-200">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="45c1c-200">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="45c1c-201">about_Remote</span><span class="sxs-lookup"><span data-stu-id="45c1c-201">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="45c1c-202">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="45c1c-202">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)

[<span data-ttu-id="45c1c-203">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="45c1c-203">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="45c1c-204">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="45c1c-204">Disable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[<span data-ttu-id="45c1c-205">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="45c1c-205">Enable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[<span data-ttu-id="45c1c-206">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="45c1c-206">Get-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[<span data-ttu-id="45c1c-207">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="45c1c-207">New-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[<span data-ttu-id="45c1c-208">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="45c1c-208">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[<span data-ttu-id="45c1c-209">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="45c1c-209">Set-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[<span data-ttu-id="45c1c-210">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="45c1c-210">Test-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[<span data-ttu-id="45c1c-211">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="45c1c-211">Unregister-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)
