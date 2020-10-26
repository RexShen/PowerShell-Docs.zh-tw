---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 工作階段設定
description: 工作階段設定定義誰可以使用 JEA 端點，以及他們可以存取哪些角色。
ms.openlocfilehash: b616d5bf260bbdfe89b6422fd4a8b4866f7fdc67
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501553"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="753f0-104">JEA 工作階段設定</span><span class="sxs-lookup"><span data-stu-id="753f0-104">JEA Session Configurations</span></span>

<span data-ttu-id="753f0-105">JEA 端點透過建立和登錄 PowerShell 工作階段設定檔在系統上登錄。</span><span class="sxs-lookup"><span data-stu-id="753f0-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="753f0-106">工作階段設定定義誰可以使用 JEA 端點，以及他們可以存取哪些角色。</span><span class="sxs-lookup"><span data-stu-id="753f0-106">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="753f0-107">它們也會定義適用於 JEA 工作階段所有使用者的全域設定。</span><span class="sxs-lookup"><span data-stu-id="753f0-107">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="753f0-108">建立工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="753f0-108">Create a session configuration file</span></span>

<span data-ttu-id="753f0-109">若要登錄 JEA 端點，您必須指定該端點的設定方式。</span><span class="sxs-lookup"><span data-stu-id="753f0-109">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="753f0-110">有許多選項要考慮。</span><span class="sxs-lookup"><span data-stu-id="753f0-110">There are many options to consider.</span></span> <span data-ttu-id="753f0-111">最重要的選項如下：</span><span class="sxs-lookup"><span data-stu-id="753f0-111">The most important options are:</span></span>

- <span data-ttu-id="753f0-112">誰可以存取 JEA 端點</span><span class="sxs-lookup"><span data-stu-id="753f0-112">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="753f0-113">他們獲指派哪些角色</span><span class="sxs-lookup"><span data-stu-id="753f0-113">Which roles they be assigned</span></span>
- <span data-ttu-id="753f0-114">JEA 實際使用哪些身分識別</span><span class="sxs-lookup"><span data-stu-id="753f0-114">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="753f0-115">JEA 端點的名稱</span><span class="sxs-lookup"><span data-stu-id="753f0-115">The name of the JEA endpoint</span></span>

<span data-ttu-id="753f0-116">這些選項全都定義在副檔名為 `.pssc` 的 PowerShell 資料檔中，稱為 PowerShell 工作階段設定檔。</span><span class="sxs-lookup"><span data-stu-id="753f0-116">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="753f0-117">工作階段設定檔可使用任何文字編輯器編輯。</span><span class="sxs-lookup"><span data-stu-id="753f0-117">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="753f0-118">執行下列命令以建立空白的範本設定檔。</span><span class="sxs-lookup"><span data-stu-id="753f0-118">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="753f0-119">根據預設，範本檔只包含最常見的設定選項。</span><span class="sxs-lookup"><span data-stu-id="753f0-119">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="753f0-120">使用 `-Full` 參數可將所有適用的設定加入產生的 PSSC。</span><span class="sxs-lookup"><span data-stu-id="753f0-120">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="753f0-121">`-SessionType RestrictedRemoteServer` 欄位指出 JEA 使用工作階段設定進行安全管理。</span><span class="sxs-lookup"><span data-stu-id="753f0-121">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="753f0-122">這種類型的工作階段會以 **NoLanguage** 模式運作，且只能存取下列預設命令 (和別名)︰</span><span class="sxs-lookup"><span data-stu-id="753f0-122">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="753f0-123">Clear-Host (cls, clear)</span><span class="sxs-lookup"><span data-stu-id="753f0-123">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="753f0-124">Exit-PSSession (exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="753f0-124">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="753f0-125">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="753f0-125">Get-Command (gcm)</span></span>
- <span data-ttu-id="753f0-126">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="753f0-126">Get-FormatData</span></span>
- <span data-ttu-id="753f0-127">Get-Help</span><span class="sxs-lookup"><span data-stu-id="753f0-127">Get-Help</span></span>
- <span data-ttu-id="753f0-128">Measure-Object (measure)</span><span class="sxs-lookup"><span data-stu-id="753f0-128">Measure-Object (measure)</span></span>
- <span data-ttu-id="753f0-129">Out-Default</span><span class="sxs-lookup"><span data-stu-id="753f0-129">Out-Default</span></span>
- <span data-ttu-id="753f0-130">Select-Object (select)</span><span class="sxs-lookup"><span data-stu-id="753f0-130">Select-Object (select)</span></span>

<span data-ttu-id="753f0-131">沒有可用的 PowerShell 提供者或任何外部程式 (可執行檔或指令碼) 。</span><span class="sxs-lookup"><span data-stu-id="753f0-131">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="753f0-132">如需語言模式的詳細資訊，請參閱[about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes)。</span><span class="sxs-lookup"><span data-stu-id="753f0-132">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="753f0-133">選擇 JEA 身分識別</span><span class="sxs-lookup"><span data-stu-id="753f0-133">Choose the JEA identity</span></span>

<span data-ttu-id="753f0-134">在幕後，JEA 執行連線使用者的命令時，需要一個可使用的身分識別 (帳戶) 。</span><span class="sxs-lookup"><span data-stu-id="753f0-134">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="753f0-135">您定義 JEA 在工作階段設定檔中使用的身分識別。</span><span class="sxs-lookup"><span data-stu-id="753f0-135">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="753f0-136">本機虛擬帳戶</span><span class="sxs-lookup"><span data-stu-id="753f0-136">Local Virtual Account</span></span>

<span data-ttu-id="753f0-137">本機虛擬帳戶適用於當針對 JEA 端點定義的角色全都用來管理本機電腦，且本機系統管理員帳戶就足以順利執行命令的情況。</span><span class="sxs-lookup"><span data-stu-id="753f0-137">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="753f0-138">虛擬帳戶是特定使用者獨有的暫時帳戶，並且持續時間僅限於他們的 PowerShell 工作階段期間。</span><span class="sxs-lookup"><span data-stu-id="753f0-138">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="753f0-139">在成員伺服器或工作站上，虛擬帳戶屬於本機電腦的 **Administrators** 群組。</span><span class="sxs-lookup"><span data-stu-id="753f0-139">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="753f0-140">在 Active Directory 網域控制站上，虛擬帳戶預設屬於網域的 **Domain Admins** 群組。</span><span class="sxs-lookup"><span data-stu-id="753f0-140">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="753f0-141">如果工作階段設定定義的角色不需要完整系統管理權限，您就可以指定虛擬帳戶所屬的安全性群組。</span><span class="sxs-lookup"><span data-stu-id="753f0-141">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="753f0-142">在成員伺服器或工作站上，指定的安全性群組必須是本機群組，而非來自網域的群組。</span><span class="sxs-lookup"><span data-stu-id="753f0-142">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="753f0-143">指定一或多個安全性群組時，虛擬帳戶不會指派給本機或網域的 Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="753f0-143">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="753f0-144">虛擬帳戶會暫時獲得授與在本機伺服器安全性原則中以服務方式登入的權限。</span><span class="sxs-lookup"><span data-stu-id="753f0-144">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="753f0-145">若其中一個指定的 VirtualAccountGroups 已在原則中獲得授與此權限，則將無法再新增個別的虛擬帳戶並會從原則中移除。</span><span class="sxs-lookup"><span data-stu-id="753f0-145">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="753f0-146">這在例如對網域控制站所進行的修訂會經過仔細稽核的網域控制站案例中很有用。</span><span class="sxs-lookup"><span data-stu-id="753f0-146">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="753f0-147">此項目僅適用於包含 2018 年 11 月或更新彙總的 Windows Server 2016，以及包含 2019 年 1 月或更新彙總的 Windows Server 2019。</span><span class="sxs-lookup"><span data-stu-id="753f0-147">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="753f0-148">群組受控服務帳戶</span><span class="sxs-lookup"><span data-stu-id="753f0-148">Group-managed service account</span></span>

<span data-ttu-id="753f0-149">當 JEA 使用者需要存取網路資源，例如檔案共用和 Web 服務時，群組受控服務帳戶 (gMSA) 是適用的身分識別。</span><span class="sxs-lookup"><span data-stu-id="753f0-149">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="753f0-150">GMSA 提供的網域身分識別，可用來驗證網域中任何電腦上的資源。</span><span class="sxs-lookup"><span data-stu-id="753f0-150">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="753f0-151">您指派的資源決定 GMSA 提供的權限。</span><span class="sxs-lookup"><span data-stu-id="753f0-151">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="753f0-152">除非電腦或服務系統管理員已明確授與這些 GMSA 權限，否則您不會有任何電腦或服務的管理權限。</span><span class="sxs-lookup"><span data-stu-id="753f0-152">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="753f0-153">應在有必要時才使用 GMSA：</span><span class="sxs-lookup"><span data-stu-id="753f0-153">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="753f0-154">使用 GMSA 時很難從動作回溯到使用者。</span><span class="sxs-lookup"><span data-stu-id="753f0-154">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="753f0-155">每個使用者都會共用相同的執行身分識別。</span><span class="sxs-lookup"><span data-stu-id="753f0-155">Every user shares the same run-as identity.</span></span> <span data-ttu-id="753f0-156">您必須檢閱 PowerShell 工作階段文字記錄和記錄檔，讓個別的使用者與其動作相互關聯。</span><span class="sxs-lookup"><span data-stu-id="753f0-156">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="753f0-157">GMSA 可以存取許多連線使用者不需要存取的網路資源。</span><span class="sxs-lookup"><span data-stu-id="753f0-157">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="753f0-158">請務必嘗試限制在 JEA 工作階段中有效的權限，以遵循最低權限的原則。</span><span class="sxs-lookup"><span data-stu-id="753f0-158">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="753f0-159">群組受控服務帳戶僅適用於已加入網域，使用 PowerShell 5.1 或更新版本的電腦。</span><span class="sxs-lookup"><span data-stu-id="753f0-159">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="753f0-160">如需保護 JEA 工作階段的詳細資訊，請參閱[安全性考量](security-considerations.md)一文。</span><span class="sxs-lookup"><span data-stu-id="753f0-160">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="753f0-161">工作階段文字記錄</span><span class="sxs-lookup"><span data-stu-id="753f0-161">Session transcripts</span></span>

<span data-ttu-id="753f0-162">建議您將 JEA端點設定為自動記錄使用者工作階段的文字記錄。</span><span class="sxs-lookup"><span data-stu-id="753f0-162">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="753f0-163">PowerShell 工作階段文字記錄包含連線使用者、指派給他們的執行身分識別，以及使用者所執行的命令等相關資訊。</span><span class="sxs-lookup"><span data-stu-id="753f0-163">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="753f0-164">對於必須了解誰對系統執行特定變更的稽核小組而言，它們可能很實用。</span><span class="sxs-lookup"><span data-stu-id="753f0-164">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="753f0-165">若要在工作階段設定檔中設定自動文字記錄，請提供要儲存文字記錄的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="753f0-165">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="753f0-166">**本機系統** 帳戶會將文字記錄寫入資料夾，這需要該目錄的讀取和寫入權限。</span><span class="sxs-lookup"><span data-stu-id="753f0-166">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="753f0-167">標準使用者應該無法存取此資料夾。</span><span class="sxs-lookup"><span data-stu-id="753f0-167">Standard users should have no access to the folder.</span></span> <span data-ttu-id="753f0-168">限制有權稽核文字記錄的安全性系統管理員數目。</span><span class="sxs-lookup"><span data-stu-id="753f0-168">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="753f0-169">使用者磁碟機</span><span class="sxs-lookup"><span data-stu-id="753f0-169">User drive</span></span>

<span data-ttu-id="753f0-170">如果您的連線使用者需要在 JEA 端點來回複製檔案，您可在工作階段設定檔中啟用使用者磁碟機。</span><span class="sxs-lookup"><span data-stu-id="753f0-170">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="753f0-171">使用者磁碟機是 **PSDrive** ，且對應至每個連線使用者的唯一資料夾。</span><span class="sxs-lookup"><span data-stu-id="753f0-171">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="753f0-172">這個資料夾允許使用者在系統中來回複製檔案，但不讓他們存取完整的檔案系統，也不公開 FileSystem 提供者。</span><span class="sxs-lookup"><span data-stu-id="753f0-172">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="753f0-173">使用者磁碟機內容會在工作階段之間持續存在，以應付網路連線可能中斷的情況。</span><span class="sxs-lookup"><span data-stu-id="753f0-173">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="753f0-174">根據預設，使用者磁碟機可讓您儲存每個使用者最多 50 MB 的資料。</span><span class="sxs-lookup"><span data-stu-id="753f0-174">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="753f0-175">您可以使用 *UserDriveMaximumSize* 欄位限制使用者可以取用的資料量。</span><span class="sxs-lookup"><span data-stu-id="753f0-175">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="753f0-176">若不想讓使用者磁碟機中的資料持續存在，您可以設定系統的排程工作，每晚自動清理資料夾。</span><span class="sxs-lookup"><span data-stu-id="753f0-176">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="753f0-177">使用者磁碟機僅適用於 PowerShell 5.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="753f0-177">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="753f0-178">如需 PSDrive 的詳細資訊，請參閱[管理 PowerShell 磁碟機](/powershell/scripting/samples/managing-windows-powershell-drives)。</span><span class="sxs-lookup"><span data-stu-id="753f0-178">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="753f0-179">角色定義</span><span class="sxs-lookup"><span data-stu-id="753f0-179">Role definitions</span></span>

<span data-ttu-id="753f0-180">工作階段設定檔中的角色定義會定義「使用者」  對「角色」  的對應。</span><span class="sxs-lookup"><span data-stu-id="753f0-180">Role definitions in a session configuration file define the mapping of **users** to **roles** .</span></span> <span data-ttu-id="753f0-181">此欄位包含的每個使用者或群組會在登錄 JEA 端點後，自動獲得 JEA 端點的權限。</span><span class="sxs-lookup"><span data-stu-id="753f0-181">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="753f0-182">每個使用者或群組只能作為索引鍵包含在雜湊表中一次，但可以指派多個角色給它。</span><span class="sxs-lookup"><span data-stu-id="753f0-182">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="753f0-183">角色功能的名稱應該是角色功能檔案的名稱，不含 `.psrc` 副檔名。</span><span class="sxs-lookup"><span data-stu-id="753f0-183">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="753f0-184">如果使用者屬於角色定義中的多個群組，他們可以存取每個群組的角色。</span><span class="sxs-lookup"><span data-stu-id="753f0-184">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="753f0-185">當兩個角色授與同一 Cmdlet 存取權時，使用者將獲得最寬鬆的參數集。</span><span class="sxs-lookup"><span data-stu-id="753f0-185">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="753f0-186">在角色定義欄位中指定本機使用者或群組時，請務必使用電腦名稱，不要使用 **localhost** 或萬用字元。</span><span class="sxs-lookup"><span data-stu-id="753f0-186">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="753f0-187">您可以藉由檢查 `$env:COMPUTERNAME` 變數來檢查電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="753f0-187">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="753f0-188">角色功能搜尋順序</span><span class="sxs-lookup"><span data-stu-id="753f0-188">Role capability search order</span></span>

<span data-ttu-id="753f0-189">如上述範例所示，會以角色功能檔案的基底名稱來參考角色功能。</span><span class="sxs-lookup"><span data-stu-id="753f0-189">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="753f0-190">檔案的基底名稱是不含副檔名的檔名。</span><span class="sxs-lookup"><span data-stu-id="753f0-190">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="753f0-191">如果系統上有多個同名的角色功能，PowerShell 會使用其隱含搜尋順序，來選取有效的角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="753f0-191">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="753f0-192">JEA **不會** 提供存取權給同名的所有角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="753f0-192">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="753f0-193">JEA 使用 `$env:PSModulePath` 環境變數來判斷要掃描哪些路徑以取得角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="753f0-193">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="753f0-194">在每個路徑中，JEA 會尋找包含 "RoleCapabilities" 子資料夾的有效 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="753f0-194">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="753f0-195">如同匯入模組一般，相較於具有相同名稱的自訂角色功能，JEA 較偏好 Windows 隨附的角色功能。</span><span class="sxs-lookup"><span data-stu-id="753f0-195">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="753f0-196">針對所有其他的命名衝突，則由 Windows 在目錄中列舉檔案的順序來決定先後順序。</span><span class="sxs-lookup"><span data-stu-id="753f0-196">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="753f0-197">順序不一定依字母順序排列。</span><span class="sxs-lookup"><span data-stu-id="753f0-197">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="753f0-198">第一個符合指定名稱的角色功能檔案會用於連線使用者。</span><span class="sxs-lookup"><span data-stu-id="753f0-198">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="753f0-199">因為角色功能搜尋順序不具決定性，所以 **強烈建議** 角色功能使用唯一的檔名。</span><span class="sxs-lookup"><span data-stu-id="753f0-199">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="753f0-200">條件式存取原則</span><span class="sxs-lookup"><span data-stu-id="753f0-200">Conditional access rules</span></span>

<span data-ttu-id="753f0-201">包含在 **RoleDefinitions** 欄位的所有使用者和群組會自動獲得 JEA 端點的存取權。</span><span class="sxs-lookup"><span data-stu-id="753f0-201">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="753f0-202">條件式存取規則可讓您精簡此存取權，並要求使用者屬於不會影響他們獲派角色的其他安全性群組。</span><span class="sxs-lookup"><span data-stu-id="753f0-202">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="753f0-203">這適用於您想要使用 JEA 整合 Just-in-Time 特殊權限存取管理解決方案、智慧卡驗證或其他多因素驗證解決方案的情況。</span><span class="sxs-lookup"><span data-stu-id="753f0-203">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="753f0-204">工作階段設定檔中的 RequiredGroups 欄位定義了條件式存取規則。</span><span class="sxs-lookup"><span data-stu-id="753f0-204">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="753f0-205">在那裡，您可以包含雜湊表 (選擇性地為巢狀)，該雜湊表會使用 'And' 及 'Or' 索引鍵來建構您的規則。</span><span class="sxs-lookup"><span data-stu-id="753f0-205">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="753f0-206">以下是如何使用此欄位的一些範例：</span><span class="sxs-lookup"><span data-stu-id="753f0-206">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> <span data-ttu-id="753f0-207">條件式存取規則僅適用於 PowerShell 5.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="753f0-207">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="753f0-208">其他屬性</span><span class="sxs-lookup"><span data-stu-id="753f0-208">Other properties</span></span>

<span data-ttu-id="753f0-209">工作階段設定檔也可以執行工作角色功能檔案的一切操作，但無法提供連線使用者對不同命令的存取權。</span><span class="sxs-lookup"><span data-stu-id="753f0-209">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="753f0-210">如果您想要允許所有使用者存取特定 Cmdlet、函式或提供者，則您可以直接在工作階段設定檔中完成。</span><span class="sxs-lookup"><span data-stu-id="753f0-210">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="753f0-211">如需工作階段設定檔中支援屬性的完整清單，請執行 `Get-Help New-PSSessionConfigurationFile -Full`。</span><span class="sxs-lookup"><span data-stu-id="753f0-211">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="753f0-212">測試工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="753f0-212">Testing a session configuration file</span></span>

<span data-ttu-id="753f0-213">您可以使用 [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) Cmdlet 測試工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="753f0-213">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="753f0-214">如已使用手動方式編輯 `.pssc` 檔案，建議您測試工作階段設定檔。</span><span class="sxs-lookup"><span data-stu-id="753f0-214">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="753f0-215">測試可確保語法正確。</span><span class="sxs-lookup"><span data-stu-id="753f0-215">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="753f0-216">如果工作階段設定檔未通過此測試，即無法在系統上登錄。</span><span class="sxs-lookup"><span data-stu-id="753f0-216">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="753f0-217">範例工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="753f0-217">Sample session configuration file</span></span>

<span data-ttu-id="753f0-218">下例示範如何建立及驗證 JEA 的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="753f0-218">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="753f0-219">為了便利性和可讀性起見，角色定義會建立並儲存在 `$roles` 變數中。</span><span class="sxs-lookup"><span data-stu-id="753f0-219">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="753f0-220">這不是必要操作。</span><span class="sxs-lookup"><span data-stu-id="753f0-220">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="753f0-221">更新工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="753f0-221">Updating session configuration files</span></span>

<span data-ttu-id="753f0-222">若要變更 JEA 工作階段設定的屬性，包括將使用者對應至角色，您必須[取消登錄](register-jea.md#unregistering-jea-configurations)。</span><span class="sxs-lookup"><span data-stu-id="753f0-222">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="753f0-223">然後，使用更新的工作階段設定檔，[重新登錄](register-jea.md) JEA 工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="753f0-223">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="753f0-224">下一步</span><span class="sxs-lookup"><span data-stu-id="753f0-224">Next steps</span></span>

- [<span data-ttu-id="753f0-225">登錄 JEA 設定</span><span class="sxs-lookup"><span data-stu-id="753f0-225">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="753f0-226">編寫 JEA 角色</span><span class="sxs-lookup"><span data-stu-id="753f0-226">Author JEA roles</span></span>](role-capabilities.md)
