---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
title: Just Enough Administration (JEA) 的改善功能
ms.openlocfilehash: 847ae92a6225023bcd0ee3dfe7c7058bdc356836
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147598"
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="2dbeb-103">Just Enough Administration (JEA) 的改善功能</span><span class="sxs-lookup"><span data-stu-id="2dbeb-103">Improvements to Just Enough Administration (JEA)</span></span>

<span data-ttu-id="2dbeb-104">Just Enough Administration 是 WMF 5.0 中的新功能，可透過 PowerShell 遠端處理，啟用以角色為基礎的管理。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-104">Just Enough Administration is a new feature in WMF 5.0 that enables role-based administration through PowerShell remoting.</span></span> <span data-ttu-id="2dbeb-105">它藉由允許非系統管理員以系統管理員身分執行特定的命令、指令碼和可執行檔，來擴充現有受條件約束的端點基礎結構。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-105">It extends the existing constrained endpoint infrastructure by allowing non-administrators to run specific commands, scripts, and executables as an administrator.</span></span> <span data-ttu-id="2dbeb-106">這可讓您減少環境中系統高權限管理員的數目並提高安全性。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-106">This enables you to reduce the number of full administrators in your environment and improve security.</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="2dbeb-107">限制 JEA 端點間的檔案複製</span><span class="sxs-lookup"><span data-stu-id="2dbeb-107">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="2dbeb-108">您現在可以將檔案從遠端複製到 JEA 端點及從中複製檔案，並確保連線的使用者無法只複製系統上的「任意」  檔案。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-108">You can now remotely copy files to/from a JEA endpoint and be assured that the connecting user can't copy just *any* file on your system.</span></span> <span data-ttu-id="2dbeb-109">方法是將 PSSC 檔案設定為掛接連接使用者的使用者磁碟機。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-109">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span> <span data-ttu-id="2dbeb-110">使用者磁碟機是新的 PSDrive，對每個連接的使用者而言皆為唯一，並在工作階段之間保存。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-110">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span> <span data-ttu-id="2dbeb-111">使用 `Copy-Item` 將檔案複製到 JEA 工作階段或從中複製檔案時，其會受限為僅允許存取使用者磁碟機。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-111">When `Copy-Item` is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span> <span data-ttu-id="2dbeb-112">嘗試將檔案複製到任何其他 PSDrive 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-112">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="2dbeb-113">若要在您的 JEA 工作階段設定檔中設定使用者磁碟機，請使用下列新欄位︰</span><span class="sxs-lookup"><span data-stu-id="2dbeb-113">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="2dbeb-114">支援使用者磁碟機的資料夾將會建立於 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="2dbeb-114">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="2dbeb-115">若要利用使用者磁碟機，並將檔案複製到設為公開使用者磁碟機的 JEA 端點及從中複製檔案，請使用 `Copy-Item` 上的 `-ToSession` 和 `-FromSession` 參數。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-115">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on `Copy-Item`.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="2dbeb-116">接著您便可以撰寫自訂的函數來處理使用者磁碟機中儲存的資料，並讓角色功能檔案中的使用者可加以使用。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-116">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="2dbeb-117">群組受管理服務帳戶的支援</span><span class="sxs-lookup"><span data-stu-id="2dbeb-117">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="2dbeb-118">在某些情況下，使用者需要在 JEA 工作階段中執行的工作可能需要存取本機電腦以外的資源。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-118">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span> <span data-ttu-id="2dbeb-119">JEA 工作階段設定為使用虛擬帳戶時，任何嘗試連接到此類資源的行為將會顯示為來自本機電腦的身分識別，而非來自虛擬帳戶或連接的使用者。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-119">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span> <span data-ttu-id="2dbeb-120">在 TP5 中，我們已支援在[群組受控服務帳戶](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\))內容下執行 JEA，可讓您更容易使用網域身分識別來存取網路資源。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-120">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="2dbeb-121">若要將 JEA 工作階段設為在 gMSA 帳戶下執行，請使用您 PSSC 檔案中的下列新金鑰︰</span><span class="sxs-lookup"><span data-stu-id="2dbeb-121">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> <span data-ttu-id="2dbeb-122">群組受管理的服務帳戶無法承受隔離或受限的虛擬帳戶範圍。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-122">Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="2dbeb-123">每個連接的使用者會共用相同 gMSA 身分識別，其可能具備整個企業的權限。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-123">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span> <span data-ttu-id="2dbeb-124">若選取使用 gMSA，請務必特別小心，並一律盡可能優先選擇僅限於本機電腦的虛擬帳戶。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-124">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="2dbeb-125">條件式存取原則</span><span class="sxs-lookup"><span data-stu-id="2dbeb-125">Conditional access policies</span></span>

<span data-ttu-id="2dbeb-126">JEA 對於限制連接至系統且要管理系統的人員可做事項而言很實用，但若您同時想限制人員*何時*可使用 JEA 呢？</span><span class="sxs-lookup"><span data-stu-id="2dbeb-126">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span> <span data-ttu-id="2dbeb-127">我們已在工作階段設定檔 (.pssc) 中加入設定選項，以讓您指定使用者必須屬於哪個安全性群組才能建立 JEA 工作階段。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-127">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span> <span data-ttu-id="2dbeb-128">若您的環境中具有 Just In Time (JIT) 系統，且想要讓使用者先提高他們的權限，然後再存取高權限的 JEA 端點，則此作業相當實用。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-128">This is especially helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="2dbeb-129">PSSC 檔案中新的 *RequiredGroups* 欄位可讓您指定邏輯，以判斷使用者是否可連接到 JEA。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-129">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span> <span data-ttu-id="2dbeb-130">其包含指定雜湊表 (選擇性地為巢狀)，該雜湊表會使用 'And' 及 'Or' 索引鍵來建構您的規則。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-130">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="2dbeb-131">以下是如何使用此欄位的一些範例：</span><span class="sxs-lookup"><span data-stu-id="2dbeb-131">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="2dbeb-132">已修正：Windows Server 2008 R2 現在支援虛擬帳戶</span><span class="sxs-lookup"><span data-stu-id="2dbeb-132">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>

<span data-ttu-id="2dbeb-133">在 WMF 5.1 中，您現在可於 Windows Server 2008 R2 使用虛擬帳戶，讓 Windows Server 2008 R2 - 2016 上的設定和功能同位一致。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-133">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span> <span data-ttu-id="2dbeb-134">在 Windows 7 上使用 JEA 時，仍不支援虛擬帳戶。</span><span class="sxs-lookup"><span data-stu-id="2dbeb-134">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>