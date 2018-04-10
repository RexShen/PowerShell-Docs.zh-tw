---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,安全性
title: JEA 工作階段設定
ms.openlocfilehash: 317a549ed20b5800d5bafdabd266e93ba7cd321c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="jea-session-configurations"></a><span data-ttu-id="3f45e-103">JEA 工作階段設定</span><span class="sxs-lookup"><span data-stu-id="3f45e-103">JEA Session Configurations</span></span>

> <span data-ttu-id="3f45e-104">適用對象：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3f45e-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="3f45e-105">JEA 端點透過以特定方式建立和登錄 PowerShell 工作階段設定檔以在系統上登錄。</span><span class="sxs-lookup"><span data-stu-id="3f45e-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="3f45e-106">工作階段設定決定「誰」可以使用 JEA 端點，以及他們可以存取哪些角色。</span><span class="sxs-lookup"><span data-stu-id="3f45e-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="3f45e-107">工作階段設定也會定義適用於 JEA 工作階段中任何角色之使用者的全域設定。</span><span class="sxs-lookup"><span data-stu-id="3f45e-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="3f45e-108">本主題描述如何建立 PowerShell 工作階段設定檔，並登錄 JEA 端點。</span><span class="sxs-lookup"><span data-stu-id="3f45e-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="3f45e-109">建立工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="3f45e-109">Create a session configuration file</span></span>

<span data-ttu-id="3f45e-110">為了登錄 JEA 端點，您必須指定該端點應該如何設定。</span><span class="sxs-lookup"><span data-stu-id="3f45e-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="3f45e-111">在這裡有許多選項要考慮，最重要的一項是誰應該可以存取 JEA 端點、將指派什麼角色給他們、JEA 將在幕後使用哪一個身分識別，以及 JEA 端點的名稱為何。</span><span class="sxs-lookup"><span data-stu-id="3f45e-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="3f45e-112">這些全都定義在 PowerShell 工作階段設定檔中，這個檔案是結尾副檔名為 .pssc 的 PowerShell 資料檔。</span><span class="sxs-lookup"><span data-stu-id="3f45e-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="3f45e-113">若要建立 JEA 端點的基本架構工作階段設定檔，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="3f45e-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="3f45e-114">此基本架構檔案預設只會包含最常見的設定選項。</span><span class="sxs-lookup"><span data-stu-id="3f45e-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="3f45e-115">使用 `-Full` 參數可將所有適用的設定加入產生的 PSSC。</span><span class="sxs-lookup"><span data-stu-id="3f45e-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="3f45e-116">您可以在任何文字編輯器中開啟工作階段設定檔。</span><span class="sxs-lookup"><span data-stu-id="3f45e-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="3f45e-117">`-SessionType RestrictedRemoteServer` 欄位指出 JEA 將使用工作階段設定以進行安全管理。</span><span class="sxs-lookup"><span data-stu-id="3f45e-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="3f45e-118">以這種方式設定的工作階段會以 [NoLanguage 模式 (英文)](https://technet.microsoft.com/library/dn433292.aspx) 運作，且只能使用下列 8 種預設命令 (和別名)︰</span><span class="sxs-lookup"><span data-stu-id="3f45e-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="3f45e-119">Clear-Host (cls, clear)</span><span class="sxs-lookup"><span data-stu-id="3f45e-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="3f45e-120">Exit-PSSession (exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="3f45e-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="3f45e-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="3f45e-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="3f45e-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="3f45e-122">Get-FormatData</span></span>
- <span data-ttu-id="3f45e-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="3f45e-123">Get-Help</span></span>
- <span data-ttu-id="3f45e-124">Measure-Object (measure)</span><span class="sxs-lookup"><span data-stu-id="3f45e-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="3f45e-125">Out-Default</span><span class="sxs-lookup"><span data-stu-id="3f45e-125">Out-Default</span></span>
- <span data-ttu-id="3f45e-126">Select-Object (select)</span><span class="sxs-lookup"><span data-stu-id="3f45e-126">Select-Object (select)</span></span>

<span data-ttu-id="3f45e-127">沒有 PowerShell 提供者或任何外部程式 (可執行檔、指令碼等等) 可用。</span><span class="sxs-lookup"><span data-stu-id="3f45e-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="3f45e-128">您有想要為 JEA 工作階段設定的數個其他欄位。</span><span class="sxs-lookup"><span data-stu-id="3f45e-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="3f45e-129">下列各節會介紹它們。</span><span class="sxs-lookup"><span data-stu-id="3f45e-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="3f45e-130">選擇 JEA 身分識別</span><span class="sxs-lookup"><span data-stu-id="3f45e-130">Choose the JEA identity</span></span>

<span data-ttu-id="3f45e-131">在幕後，JEA 執行連線使用者的命令時，需要一個可使用的身分識別 (帳戶) 。</span><span class="sxs-lookup"><span data-stu-id="3f45e-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="3f45e-132">您決定 JEA 將在工作階段設定檔中使用哪一個身分識別。</span><span class="sxs-lookup"><span data-stu-id="3f45e-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="3f45e-133">本機虛擬帳戶</span><span class="sxs-lookup"><span data-stu-id="3f45e-133">Local Virtual Account</span></span>

<span data-ttu-id="3f45e-134">如果此 JEA 端點支援的角色全都用來管理本機電腦，且本機系統管理員帳戶就足以順利執行命令，則您應該將 JEA 設定為使用本機虛擬帳戶。</span><span class="sxs-lookup"><span data-stu-id="3f45e-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands succesfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="3f45e-135">虛擬帳戶是特定使用者獨有的暫時帳戶，並且持續時間僅限於他們的 PowerShell 工作階段期間。</span><span class="sxs-lookup"><span data-stu-id="3f45e-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="3f45e-136">在成員伺服器或工作站上，虛擬帳戶屬於本機電腦的 **Administrators** 群組，並且可以存取大部分的系統資源。</span><span class="sxs-lookup"><span data-stu-id="3f45e-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="3f45e-137">在 Active Directory 網域控制站上，虛擬帳戶預設屬於網域的 **Domain Admins** 群組。</span><span class="sxs-lookup"><span data-stu-id="3f45e-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="3f45e-138">如果工作階段設定所支援的角色不需要這類廣泛的權限，則您可以選擇是否指定虛擬帳戶所屬的安全性群組。</span><span class="sxs-lookup"><span data-stu-id="3f45e-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="3f45e-139">在成員伺服器或工作站上，指定的安全性群組必須是本機群組，而非來自網域的群組。</span><span class="sxs-lookup"><span data-stu-id="3f45e-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="3f45e-140">指定一或多個安全性群組時，虛擬帳戶將不再屬於本機或網域系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="3f45e-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a><span data-ttu-id="3f45e-141">群組受管理的服務帳戶</span><span class="sxs-lookup"><span data-stu-id="3f45e-141">Group Managed Service Account</span></span>


<span data-ttu-id="3f45e-142">針對需要 JEA 使用者以存取網路資源，例如其他電腦或 Web 服務的情況，群組受管理的服務帳戶 (gMSA) 是更適合使用的身分識別。</span><span class="sxs-lookup"><span data-stu-id="3f45e-142">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="3f45e-143">gMSA 帳戶為您提供可以用來對網域中任何電腦上的資源進行驗證的網域身分識別。</span><span class="sxs-lookup"><span data-stu-id="3f45e-143">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="3f45e-144">gMSA 帳戶提供給您的權限由您正在存取的資源決定。</span><span class="sxs-lookup"><span data-stu-id="3f45e-144">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="3f45e-145">您不會在任何電腦或服務上自動擁有系統管理權限，除非電腦/服務系統管理員已明確授與 gMSA 帳戶系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="3f45e-145">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="3f45e-146">gMSA 帳戶應該只用於因為一些原因而需要存取網路資源時︰</span><span class="sxs-lookup"><span data-stu-id="3f45e-146">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="3f45e-147">使用 gMSA 帳戶時從動作回溯到使用者比較困難，因為每個使用者都共用相同的執行身分識別。</span><span class="sxs-lookup"><span data-stu-id="3f45e-147">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="3f45e-148">您必須參閱 PowerShell 工作階段文字記錄以及記錄檔，以讓使用者與他們的動作相互關聯。</span><span class="sxs-lookup"><span data-stu-id="3f45e-148">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="3f45e-149">gMSA 帳戶可能可以存取許多連線使用者不需要存取的網路資源。</span><span class="sxs-lookup"><span data-stu-id="3f45e-149">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="3f45e-150">請務必嘗試限制在 JEA 工作階段中有效的權限，以遵循最低權限的原則。</span><span class="sxs-lookup"><span data-stu-id="3f45e-150">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="3f45e-151">群組受管理的服務帳戶僅適用於 Windows PowerShell 5.1 或更新版本，以及在已加入網域的電腦上。</span><span class="sxs-lookup"><span data-stu-id="3f45e-151">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>


#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="3f45e-152">執行身分使用者的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="3f45e-152">More information about run as users</span></span>

<span data-ttu-id="3f45e-153">如需執行身分識別的詳細資訊，以及它們如何納入 JEA 工作階段的安全性，請參閱[安全性考量](security-considerations.md)文章。</span><span class="sxs-lookup"><span data-stu-id="3f45e-153">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="3f45e-154">工作階段文字記錄</span><span class="sxs-lookup"><span data-stu-id="3f45e-154">Session transcripts</span></span>

<span data-ttu-id="3f45e-155">建議您將 JEA 工作階段設定檔設定為自動記錄使用者工作階段的文字記錄。</span><span class="sxs-lookup"><span data-stu-id="3f45e-155">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="3f45e-156">PowerShell 工作階段文字記錄包含連線使用者、指派給他們的執行身分識別，以及使用者所執行的命令等相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3f45e-156">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="3f45e-157">對於必須了解誰對系統執行了特定變更的稽核小組而言，它們可能很實用。</span><span class="sxs-lookup"><span data-stu-id="3f45e-157">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="3f45e-158">若要在工作階段設定檔中設定自動文字記錄，請提供要儲存文字記錄的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="3f45e-158">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="3f45e-159">指定的資料夾應該設定為防止使用者修改或刪除其中的任何資料。</span><span class="sxs-lookup"><span data-stu-id="3f45e-159">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="3f45e-160">本機系統帳戶會將文字記錄寫入資料夾，這需要該目錄的讀取和寫入權限。</span><span class="sxs-lookup"><span data-stu-id="3f45e-160">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="3f45e-161">標準使用者應該無法存取該資料夾，並且只有有限的一組安全性系統管理員有權可稽核文字記錄。</span><span class="sxs-lookup"><span data-stu-id="3f45e-161">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="3f45e-162">使用者磁碟機</span><span class="sxs-lookup"><span data-stu-id="3f45e-162">User drive</span></span>

<span data-ttu-id="3f45e-163">如果您的連線使用者將需要從 JEA 端點複製檔案或將檔案複製到 JEA 端點才能執行命令，則您可以啟用工作階段設定檔中的使用者磁碟機。</span><span class="sxs-lookup"><span data-stu-id="3f45e-163">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="3f45e-164">使用者磁碟機是 [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives)，且對應至每個連線使用者的唯一資料夾。</span><span class="sxs-lookup"><span data-stu-id="3f45e-164">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="3f45e-165">這個資料夾可作為他們在系統中複製檔案的空間，而不讓他們存取完整的檔案系統或公開檔案系統提供者。</span><span class="sxs-lookup"><span data-stu-id="3f45e-165">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="3f45e-166">使用者磁碟機內容會在工作階段之間持續存在，以應付網路連線可能中斷的情況。</span><span class="sxs-lookup"><span data-stu-id="3f45e-166">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="3f45e-167">根據預設，使用者磁碟機可讓您儲存每個使用者最多 50 MB 的資料。</span><span class="sxs-lookup"><span data-stu-id="3f45e-167">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="3f45e-168">您可以使用 *UserDriveMaximumSize* 欄位限制使用者可以取用的資料量。</span><span class="sxs-lookup"><span data-stu-id="3f45e-168">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="3f45e-169">若不想讓使用者磁碟機中的資料持續存在，您可以在系統上設定排定的工作，每晚自動清理資料夾。</span><span class="sxs-lookup"><span data-stu-id="3f45e-169">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="3f45e-170">使用者磁碟機僅適用於 Windows PowerShell 5.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="3f45e-170">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="3f45e-171">角色定義</span><span class="sxs-lookup"><span data-stu-id="3f45e-171">Role definitions</span></span>

<span data-ttu-id="3f45e-172">工作階段設定檔中的角色定義會定義「使用者」對「角色」的對應。</span><span class="sxs-lookup"><span data-stu-id="3f45e-172">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="3f45e-173">此欄位包含的每個使用者或群組會在登錄 JEA 端點時自動獲得 JEA 端點的權限。</span><span class="sxs-lookup"><span data-stu-id="3f45e-173">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="3f45e-174">每個使用者或群組只能作為索引鍵包含在雜湊表中一次，但可以指派多個角色給它。</span><span class="sxs-lookup"><span data-stu-id="3f45e-174">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="3f45e-175">角色功能的名稱應該是角色功能檔案的名稱，不含 .psrc 副檔名。</span><span class="sxs-lookup"><span data-stu-id="3f45e-175">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="3f45e-176">如果使用者屬於角色定義中的多個群組，他們將可以存取每個群組的角色。</span><span class="sxs-lookup"><span data-stu-id="3f45e-176">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="3f45e-177">如果兩個角色授與對相同 Cmdlet 的存取權，使用者將獲得最寬鬆的參數集。</span><span class="sxs-lookup"><span data-stu-id="3f45e-177">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="3f45e-178">在角色定義欄位中指定本機使用者或群組時，務必在反斜線前使用電腦名稱 (而非 *localhost* 或 *.*)。</span><span class="sxs-lookup"><span data-stu-id="3f45e-178">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="3f45e-179">您可以藉由檢查 `$env:computername` 變數來檢查電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="3f45e-179">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="3f45e-180">角色功能搜尋順序</span><span class="sxs-lookup"><span data-stu-id="3f45e-180">Role capability search order</span></span>
<span data-ttu-id="3f45e-181">如上述範例所示，會以角色功能檔案的一般名稱 (不含副檔名的檔名) 來參考角色功能。</span><span class="sxs-lookup"><span data-stu-id="3f45e-181">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="3f45e-182">如果系統上有多個相同一般名稱的角色功能，PowerShell 將使用其隱含搜尋順序，來選取有效的角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="3f45e-182">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="3f45e-183">它將**不會**提供存取權給同名的所有角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="3f45e-183">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="3f45e-184">JEA 使用 `$env:PSModulePath` 環境變數來判斷要掃描哪些路徑以取得角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="3f45e-184">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="3f45e-185">在每個路徑中，JEA 會尋找包含 "RoleCapabilities" 子資料夾的有效 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="3f45e-185">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="3f45e-186">如同匯入模組一般，相較於具有相同名稱的自訂角色功能，JEA 較偏好 Windows 隨附的角色功能。</span><span class="sxs-lookup"><span data-stu-id="3f45e-186">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="3f45e-187">針對所有其他的命名衝突，會由 Windows 列舉目錄中檔案的順序來決定順序 (不保證依字母順序)。</span><span class="sxs-lookup"><span data-stu-id="3f45e-187">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="3f45e-188">第一個符合需求名稱的角色功能檔案將會用於連線使用者。</span><span class="sxs-lookup"><span data-stu-id="3f45e-188">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="3f45e-189">由於在兩個 (或更多) 角色功能共用相同名稱時，角色功能搜尋順序具有不確定性，「強烈建議」您確保電腦上的角色功能都使用唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="3f45e-189">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="3f45e-190">條件式存取原則</span><span class="sxs-lookup"><span data-stu-id="3f45e-190">Conditional access rules</span></span>

<span data-ttu-id="3f45e-191">包含在 RoleDefinitions 欄位的所有使用者和群組會自動獲得 JEA 端點的存取權。</span><span class="sxs-lookup"><span data-stu-id="3f45e-191">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="3f45e-192">條件式存取規則可讓您精簡此存取權，並要求使用者屬於不會影響指派給他們之角色的其他安全性群組。</span><span class="sxs-lookup"><span data-stu-id="3f45e-192">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="3f45e-193">這適用於您想要整合「即時」(Just-in-Time) 特殊權限存取管理解決方案、智慧卡驗證或其他多因素驗證解決方案與 JEA。</span><span class="sxs-lookup"><span data-stu-id="3f45e-193">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="3f45e-194">工作階段設定檔中的 RequiredGroups 欄位定義了條件式存取規則。</span><span class="sxs-lookup"><span data-stu-id="3f45e-194">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="3f45e-195">在那裡，您可以包含雜湊表 (選擇性地為巢狀)，該雜湊表會使用 'And' 及 'Or' 索引鍵來建構您的規則。</span><span class="sxs-lookup"><span data-stu-id="3f45e-195">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="3f45e-196">以下是如何運用此欄位的一些範例︰</span><span class="sxs-lookup"><span data-stu-id="3f45e-196">Here are some examples of how to leverage this field:</span></span>

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
> <span data-ttu-id="3f45e-197">條件式存取原則僅適用於 Windows PowerShell 5.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="3f45e-197">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="3f45e-198">其他屬性</span><span class="sxs-lookup"><span data-stu-id="3f45e-198">Other properties</span></span>
<span data-ttu-id="3f45e-199">工作階段設定檔也可以執行工作角色功能檔案的一切操作，但無法提供連線使用者對不同命令的存取權。</span><span class="sxs-lookup"><span data-stu-id="3f45e-199">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="3f45e-200">如果您想要允許所有使用者存取特定 Cmdlet、函式或提供者，則您可以直接在工作階段設定檔中完成。</span><span class="sxs-lookup"><span data-stu-id="3f45e-200">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="3f45e-201">如需工作階段設定檔中支援屬性的完整清單，請執行 `Get-Help New-PSSessionConfigurationFile -Full`。</span><span class="sxs-lookup"><span data-stu-id="3f45e-201">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="3f45e-202">測試工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="3f45e-202">Testing a session configuration file</span></span>

<span data-ttu-id="3f45e-203">您可以使用 [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) Cmdlet 測試工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="3f45e-203">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="3f45e-204">如果您已使用文字編輯器手動編輯 pssc 檔案，強烈建議您測試您的工作階段設定檔，以確定語法正確。</span><span class="sxs-lookup"><span data-stu-id="3f45e-204">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="3f45e-205">如果工作階段設定檔未通過此測試，它將無法順利在系統上登錄。</span><span class="sxs-lookup"><span data-stu-id="3f45e-205">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="3f45e-206">範例工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="3f45e-206">Sample session configuration file</span></span>

<span data-ttu-id="3f45e-207">以下是完整的範例，示範如何建立及驗證 JEA 的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="3f45e-207">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="3f45e-208">請注意，為了便利性和可讀性起見，角色定義會建立並儲存在 `$roles` 變數。</span><span class="sxs-lookup"><span data-stu-id="3f45e-208">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="3f45e-209">並不要求須執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="3f45e-209">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="3f45e-210">更新工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="3f45e-210">Updating session configuration files</span></span>

<span data-ttu-id="3f45e-211">如果您需要變更 JEA 工作階段設定的屬性，包括將使用者對應至角色，您必須[取消登錄](register-jea.md#unregistering-jea-configurations)並[重新登錄](register-jea.md) JEA 工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="3f45e-211">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="3f45e-212">當您重新登錄 JEA 工作階段設定時，請使用包含您想要之變更的已更新 PowerShell 工作階段設定檔。</span><span class="sxs-lookup"><span data-stu-id="3f45e-212">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3f45e-213">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="3f45e-213">Next steps</span></span>

- [<span data-ttu-id="3f45e-214">登錄 JEA 設定</span><span class="sxs-lookup"><span data-stu-id="3f45e-214">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="3f45e-215">編寫 JEA 角色</span><span class="sxs-lookup"><span data-stu-id="3f45e-215">Author JEA roles</span></span>](role-capabilities.md)