---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: Just Enough Administration 概觀
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "70017699"
---
# <a name="just-enough-administration"></a><span data-ttu-id="951ed-103">Just Enough Administration</span><span class="sxs-lookup"><span data-stu-id="951ed-103">Just Enough Administration</span></span>

<span data-ttu-id="951ed-104">Just Enough Administration (JEA) 是安全性技術，允許委派管理 PowerShell 管理的任何項目。</span><span class="sxs-lookup"><span data-stu-id="951ed-104">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything managed by PowerShell.</span></span> <span data-ttu-id="951ed-105">使用 JEA，您可以︰</span><span class="sxs-lookup"><span data-stu-id="951ed-105">With JEA, you can:</span></span>

- <span data-ttu-id="951ed-106">使用虛擬帳戶或群組受控服務帳戶來代表一般使用者執行特殊權限動作，以**減少電腦上的系統管理員數目**。</span><span class="sxs-lookup"><span data-stu-id="951ed-106">**Reduce the number of administrators on your machines** using virtual accounts or group-managed service accounts to perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="951ed-107">指定使用者可以執行的 Cmdlet、函式和外部命令，以**限制使用者可以執行的工作**。</span><span class="sxs-lookup"><span data-stu-id="951ed-107">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="951ed-108">透過文字記錄和記錄檔，顯示使用者在工作階段期間執行的確切命令，以**深入了解使用者正在執行的工作**。</span><span class="sxs-lookup"><span data-stu-id="951ed-108">**Better understand what your users are doing** with transcripts and logs that show you exactly which commands a user executed during their session.</span></span>

<span data-ttu-id="951ed-109">**JEA 為何如此重要？**</span><span class="sxs-lookup"><span data-stu-id="951ed-109">**Why is JEA important?**</span></span>

<span data-ttu-id="951ed-110">用來管理伺服器且具有高度權限的帳戶會造成嚴重的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="951ed-110">Highly privileged accounts used to administer your servers pose a serious security risk.</span></span> <span data-ttu-id="951ed-111">萬一攻擊者入侵其中一個帳戶，他們便可以對整個組織啟動[橫向攻擊](https://aka.ms/pth)。</span><span class="sxs-lookup"><span data-stu-id="951ed-111">Should an attacker compromise one of these accounts, they could launch [lateral attacks](https://aka.ms/pth) across your organization.</span></span> <span data-ttu-id="951ed-112">每個遭入侵的帳戶都能讓攻擊者存取更多帳戶和資源，讓他們進一步竊取公司祕密、啟動拒絕服務的攻擊等。</span><span class="sxs-lookup"><span data-stu-id="951ed-112">Each compromised account gives an attacker access to even more accounts and resources, and puts them one step closer to stealing company secrets, launching a denial-of-service attack, and more.</span></span>

<span data-ttu-id="951ed-113">移除系統管理員權限從來不是一件容易的事。</span><span class="sxs-lookup"><span data-stu-id="951ed-113">It's not always easy to remove administrative privileges, either.</span></span> <span data-ttu-id="951ed-114">請考慮常見的案例：DNS 角色安裝在與 Active Directory 網域控制站相同的電腦上。</span><span class="sxs-lookup"><span data-stu-id="951ed-114">Consider the common scenario where the DNS role is installed on the same machine as your Active Directory Domain Controller.</span></span> <span data-ttu-id="951ed-115">您的 DNS 系統管理員需要本機系統管理員權限，才能修正 DNS 伺服器的問題。</span><span class="sxs-lookup"><span data-stu-id="951ed-115">Your DNS administrators require local administrator privileges to fix issues with the DNS server.</span></span> <span data-ttu-id="951ed-116">但若要這樣做，您必須讓他們成為具高度權限的 **Domain Admins** 安全性群組成員。</span><span class="sxs-lookup"><span data-stu-id="951ed-116">But to do so, you must make them members of the highly privileged **Domain Admins** security group.</span></span> <span data-ttu-id="951ed-117">這個方法能有效地讓 DNS 系統管理員控制您的整個網域，並存取該電腦上的所有資源。</span><span class="sxs-lookup"><span data-stu-id="951ed-117">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="951ed-118">JEA 透過**最低權限**原則解決此問題。</span><span class="sxs-lookup"><span data-stu-id="951ed-118">JEA addresses this problem through the principle of **Least Privilege**.</span></span> <span data-ttu-id="951ed-119">有了 JEA，您就可以設定 DNS 系統管理員的管理端點，並讓他們只存取完成其工作所需的 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="951ed-119">With JEA, you can configure a management endpoint for DNS administrators that gives them access only to the PowerShell commands they need to get their job done.</span></span> <span data-ttu-id="951ed-120">這表示您可以提供適當的存取權以修復受害的 DNS 快取或重新啟動 DNS 伺服器，卻不會無意中給予他們使用 Active Directory、瀏覽檔案或執行有潛在危險指令碼的權限。</span><span class="sxs-lookup"><span data-stu-id="951ed-120">This means you can provide the appropriate access to repair a poisoned DNS cache or restart the DNS server without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span> <span data-ttu-id="951ed-121">更棒的是，當 JEA 工作階段設定為使用暫時性特殊權限虛擬帳戶時，您的 DNS 系統管理員仍可以在使用**非管理員**認證連線到伺服器的情況下，執行通常需要系統管理權限的命令。</span><span class="sxs-lookup"><span data-stu-id="951ed-121">Better yet, when the JEA session is configured to use temporary privileged virtual accounts, your DNS administrators can connect to the server using **non-admin** credentials and still run commands that typically require admin privileges.</span></span> <span data-ttu-id="951ed-122">這項功能可讓您從廣泛權限的本機/網域系統管理員角色移除使用者，且小心控制他們能夠在每部電腦上執行的事項。</span><span class="sxs-lookup"><span data-stu-id="951ed-122">JEA enables you to remove users from widely privileged local/domain administrator roles and carefully control what they can do on each machine.</span></span>

## <a name="next-steps"></a><span data-ttu-id="951ed-123">後續步驟</span><span class="sxs-lookup"><span data-stu-id="951ed-123">Next steps</span></span>

<span data-ttu-id="951ed-124">若要深入了解使用 JEA 的需求，請參閱[必要條件](prerequisites.md)一文。</span><span class="sxs-lookup"><span data-stu-id="951ed-124">To learn more about the requirements to use JEA, see the [Prerequisites](prerequisites.md) article.</span></span>

## <a name="samples-and-dsc-resource"></a><span data-ttu-id="951ed-125">範例和 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="951ed-125">Samples and DSC resource</span></span>

<span data-ttu-id="951ed-126">您可以在 [JEA GitHub 存放庫 (英文)](https://github.com/PowerShell/JEA) 中找到範例 JEA 設定和 JEA DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="951ed-126">Sample JEA configurations and the JEA DSC resource can be found in the [JEA GitHub repository](https://github.com/PowerShell/JEA).</span></span>
