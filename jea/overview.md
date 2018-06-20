---
ms.date: 06/12/2017
keywords: jea,powershell,安全性
title: Just Enough Administration 概觀
ms.openlocfilehash: 3dae8b31d4d13ff9033803035c870c02fc7c38ca
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222083"
---
# <a name="just-enough-administration"></a><span data-ttu-id="5bc20-103">Just Enough Administration</span><span class="sxs-lookup"><span data-stu-id="5bc20-103">Just Enough Administration</span></span>

<span data-ttu-id="5bc20-104">Just Enough Administration (JEA) 是安全性技術，允許將可透過 PowerShell 管理的任何項目委派管理。</span><span class="sxs-lookup"><span data-stu-id="5bc20-104">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything that can be managed with PowerShell.</span></span>
<span data-ttu-id="5bc20-105">使用 JEA，您可以︰</span><span class="sxs-lookup"><span data-stu-id="5bc20-105">With JEA, you can:</span></span>

- <span data-ttu-id="5bc20-106">利用虛擬帳戶或群組受管理服務帳戶，代表一般使用者執行特殊權限動作，以「減少電腦上的系統管理員數目」。</span><span class="sxs-lookup"><span data-stu-id="5bc20-106">**Reduce the number of administrators on your machines** by leveraging virtual accounts or group managed service accounts that perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="5bc20-107">指定使用者可以執行的 Cmdlet、函式和外部命令，以**限制使用者可以執行的工作**。</span><span class="sxs-lookup"><span data-stu-id="5bc20-107">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="5bc20-108">透過文字記錄和記錄檔，顯示使用者在工作階段期間執行的確切命令，以**深入了解使用者正在執行的工作**。</span><span class="sxs-lookup"><span data-stu-id="5bc20-108">**Better understand what your users are doing** with transcripts and logs that show you exactly which commands a user executed during their session.</span></span>

<span data-ttu-id="5bc20-109">**為何重要？**</span><span class="sxs-lookup"><span data-stu-id="5bc20-109">**Why is this important?**</span></span>

<span data-ttu-id="5bc20-110">用來管理伺服器且具有高度權限的帳戶會造成嚴重的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="5bc20-110">Highly privileged accounts used to administer your servers pose a serious security risk.</span></span>
<span data-ttu-id="5bc20-111">萬一攻擊者入侵其中一個帳戶，他們便可以對整個組織啟動[橫向攻擊](http://aka.ms/pth)。</span><span class="sxs-lookup"><span data-stu-id="5bc20-111">Should an attacker compromise one of these accounts, they could launch [lateral attacks](http://aka.ms/pth) across your organization.</span></span>
<span data-ttu-id="5bc20-112">他們入侵的每個帳戶都能讓他們存取更多帳戶和資源，讓他們更進一步竊取公司機密、啟動阻絕服務攻擊等等。</span><span class="sxs-lookup"><span data-stu-id="5bc20-112">Each account they compromise can give them access to even more accounts and resources, putting them one step closer to stealing company secrets, launching a denial-of-service attack, and more.</span></span>

<span data-ttu-id="5bc20-113">移除系統管理員的權限並不一定容易。</span><span class="sxs-lookup"><span data-stu-id="5bc20-113">It is not always easy to remove administrative privileges, either.</span></span>
<span data-ttu-id="5bc20-114">請考慮常見的案例：DNS 角色安裝在與 Active Directory 網域控制站相同的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5bc20-114">Consider the common scenario where the DNS role is installed on the same machine as your Active Directory Domain Controller.</span></span>
<span data-ttu-id="5bc20-115">您的 DNS 系統管理員必須具有本機系統管理員權限，才能修正 DNS 伺服器的問題，但若要這樣做，您必須將其設為具有高度權限之 "Domain Admins" 安全性群組的成員。</span><span class="sxs-lookup"><span data-stu-id="5bc20-115">Your DNS administrators require local administrator privileges to fix issues with the DNS server, but in order to do so you have to make them members of the highly privileged "Domain Admins" security group.</span></span>
<span data-ttu-id="5bc20-116">這個方法能有效地讓 DNS 系統管理員控制您的整個網域，並存取該電腦上的所有資源。</span><span class="sxs-lookup"><span data-stu-id="5bc20-116">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="5bc20-117">JEA 有助於解決這個問題，因為它可以協助您採用*最低權限*的原則。</span><span class="sxs-lookup"><span data-stu-id="5bc20-117">JEA helps address this problem by helping you adopt the principle of *Least Privilege*.</span></span>
<span data-ttu-id="5bc20-118">有了 JEA，您就可以設定 DNS 系統管理員的管理端點，並讓他們只存取完成其工作所需的所有 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="5bc20-118">With JEA, you can configure a management endpoint for DNS administrators that gives them access to all the PowerShell commands they need to get their job done, but nothing more.</span></span>
<span data-ttu-id="5bc20-119">這表示您可以提供適當的存取權以修復受害的 DNS 快取或重新啟動 DNS 伺服器，卻不會無意中給予他們使用 Active Directory、瀏覽檔案或執行有潛在危險指令碼的權限。</span><span class="sxs-lookup"><span data-stu-id="5bc20-119">This means you can provide the appropriate access to repair a poisoned DNS cache or restart the DNS server without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span>
<span data-ttu-id="5bc20-120">更棒的是，當 JEA 工作階段設定為使用暫時性特殊權限虛擬帳戶時，您的 DNS 系統管理員就可以在使用「非系統管理員」認證連接到伺服器的情況下，仍然能夠執行通常需要系統管理權限的命令。</span><span class="sxs-lookup"><span data-stu-id="5bc20-120">Better yet, when the JEA session is configured to use temporary privileged virtual accounts, your DNS administrators can connect to the server using *non-admin* credentials and still be able to run commands which typically require admin privileges.</span></span>
<span data-ttu-id="5bc20-121">這項功能可讓您從廣泛權限的本機/網域系統管理員角色移除使用者，並改為小心控制他們能夠在每部電腦上執行的事項。</span><span class="sxs-lookup"><span data-stu-id="5bc20-121">This capability enables you to remove users from widely-privileged local/domain administrator roles and instead carefully control what they are able to do on each machine.</span></span>

## <a name="get-started-with-jea"></a><span data-ttu-id="5bc20-122">開始使用 JEA</span><span class="sxs-lookup"><span data-stu-id="5bc20-122">Get Started with JEA</span></span>

<span data-ttu-id="5bc20-123">您可以在執行 Windows Server 2016 或 Windows 10 的任何電腦上立即開始使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="5bc20-123">You can start using JEA today on any machine running Windows Server 2016 or Windows 10.</span></span>
<span data-ttu-id="5bc20-124">您也可以在具有 Windows Management Framework 更新的舊版作業系統上執行 JEA。</span><span class="sxs-lookup"><span data-stu-id="5bc20-124">You can also run JEA on older operating systems with a Windows Management Framework update.</span></span>
<span data-ttu-id="5bc20-125">若要深入了解使用 JEA 的需求，並了解如何建立、使用和稽核 JEA 端點，請參閱下列主題︰</span><span class="sxs-lookup"><span data-stu-id="5bc20-125">To learn more about the requirements to use JEA and to learn how to create, use, and audit a JEA endpoint, check out the following topics:</span></span>

- <span data-ttu-id="5bc20-126">[必要條件](prerequisites.md) - 說明如何設定環境以使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="5bc20-126">[Prerequisites](prerequisites.md) - explains how to set up your environment to use JEA.</span></span>
- <span data-ttu-id="5bc20-127">[角色功能](role-capabilities.md) - 說明如何建立角色，來判斷使用者允許在 JEA 工作階段中執行的動作。</span><span class="sxs-lookup"><span data-stu-id="5bc20-127">[Role Capabilities](role-capabilities.md) - explains how to create roles which determine what a user is allowed to do in a JEA session.</span></span>
- <span data-ttu-id="5bc20-128">[工作階段設定](session-configurations.md) - 說明如何設定 JEA 端點，將使用者對應至角色，並且設定 JEA 識別</span><span class="sxs-lookup"><span data-stu-id="5bc20-128">[Session Configurations](session-configurations.md) - explains how to configure JEA endpoints that map users to roles and set the JEA identity</span></span>
- <span data-ttu-id="5bc20-129">[註冊 JEA](register-jea.md) - 建立 JEA 端點，並使其可供使用者連接。</span><span class="sxs-lookup"><span data-stu-id="5bc20-129">[Registering JEA](register-jea.md) - create a JEA endpoint and make it available for users to connect to.</span></span>
- <span data-ttu-id="5bc20-130">[使用 JEA](using-jea.md) - 了解您可以使用 JEA 的各種方式。</span><span class="sxs-lookup"><span data-stu-id="5bc20-130">[Using JEA](using-jea.md) - learn the various ways you can use JEA.</span></span>
- <span data-ttu-id="5bc20-131">[安全性考量](security-considerations.md) - 檢閱安全性最佳做法和 JEA 設定選項的影響。</span><span class="sxs-lookup"><span data-stu-id="5bc20-131">[Security Considerations](security-considerations.md) - review security best practices and implications of JEA configuration options.</span></span>
- <span data-ttu-id="5bc20-132">[JEA 上的稽核和報告](audit-and-report.md) - 了解如何在 JEA 端點進行稽核和報告。</span><span class="sxs-lookup"><span data-stu-id="5bc20-132">[Audit and Report on JEA](audit-and-report.md) - learn how to audit and report on JEA endpoints.</span></span>

## <a name="samples-and-dsc-resource"></a><span data-ttu-id="5bc20-133">範例和 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="5bc20-133">Samples and DSC resource</span></span>

<span data-ttu-id="5bc20-134">您可以在 [JEA GitHub 存放庫 (英文)](https://github.com/PowerShell/JEA) 中找到範例 JEA 設定和 JEA DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="5bc20-134">Sample JEA configurations and the JEA DSC resource can be found in the [JEA GitHub repository](https://github.com/PowerShell/JEA).</span></span>