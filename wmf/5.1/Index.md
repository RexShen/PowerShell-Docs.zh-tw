---
ms.date: 2017-08-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
title: "WMF 5.1 版本資訊"
ms.openlocfilehash: 3a6b7fb84d679d9bbe7a89e30c8c769e26f7381a
ms.sourcegitcommit: 3f49bd2e0b786e69c71393c00ad85d05a8466753
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2017
---
# <a name="windows-management-framework-wmf-51"></a><span data-ttu-id="09859-103">Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="09859-103">Windows Management Framework (WMF) 5.1</span></span> #

<span data-ttu-id="09859-104">WMF 讓使用者能夠將現有的 Windows 系統更新為搭配 Windows Server 2016 發行的 PowerShell、WMI、WinRM 及軟體清查記錄 (SIL) 元件版本。</span><span class="sxs-lookup"><span data-stu-id="09859-104">WMF provides users with the ability to update existing Windows systems to the versions of PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> 

<span data-ttu-id="09859-105">WMF 5.1 可以在 Windows 7、Windows 8.1、Windows Server 2008 R2、2012 及 2012 R2 上安裝，並提供許多對 WMF 5.0 RTM 的改善，包括︰</span><span class="sxs-lookup"><span data-stu-id="09859-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="09859-106">新的 Cmdlet︰本機使用者和群組；Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="09859-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="09859-107">PowerShellGet 改善功能包括強制執行已簽署的模組，以及安裝 JEA 模組</span><span class="sxs-lookup"><span data-stu-id="09859-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="09859-108">PackageManagement 新增對容器、CBS 安裝、以執行檔為基礎的安裝、封包封裝的支援</span><span class="sxs-lookup"><span data-stu-id="09859-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="09859-109">DSC 和 PowerShell 類別的偵錯改善</span><span class="sxs-lookup"><span data-stu-id="09859-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="09859-110">安全性增強功能包括強制執行來自提取伺服器的目錄簽署模組，以及在使用 PowerShellGet Cmdlet 時加以強制執行</span><span class="sxs-lookup"><span data-stu-id="09859-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="09859-111">回應數個使用者要求和問題</span><span class="sxs-lookup"><span data-stu-id="09859-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="09859-112">若要了解此版本中的最新消息，請瀏覽[新的案例與功能](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features)下列出的主題。</span><span class="sxs-lookup"><span data-stu-id="09859-112">To learn about what is new in this release, browse the topics listed under [New Scenarios and Features](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features).</span></span> 

<span data-ttu-id="09859-113">[安裝與設定](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure)主題列出了需求，且提供 WMF 的安裝指示。</span><span class="sxs-lookup"><span data-stu-id="09859-113">The [Install and Configure](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic lists the requirements and provides installation instructions for WMF.</span></span> 

<span data-ttu-id="09859-114">[相容性](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility)主題列出了各 Windows 版本可安裝的 WMF 版本。</span><span class="sxs-lookup"><span data-stu-id="09859-114">The [Compatibility](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) topic lists which versions of WMF may be installed on which Windows releases.</span></span> 

<span data-ttu-id="09859-115">[產品相容性](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat)列出了目前尚未核准使用 WMF 5.1 的 Microsoft 應用程式。</span><span class="sxs-lookup"><span data-stu-id="09859-115">[Product Compatibility](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) lists the Microsoft applications that have not approved WMF 5.1 for use at this time.</span></span> 

<span data-ttu-id="09859-116">MSDN 文件中提供了 WMF 元件的詳細資料：</span><span class="sxs-lookup"><span data-stu-id="09859-116">Details for the components of WMF will be found in MSDN documentation:</span></span>

- [<span data-ttu-id="09859-117">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="09859-117">PowerShell 5.1</span></span>](https://docs.microsoft.com/en-us/powershell/) 
- [<span data-ttu-id="09859-118">WMI</span><span class="sxs-lookup"><span data-stu-id="09859-118">WMI</span></span>](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)
- [<span data-ttu-id="09859-119">WinRM</span><span class="sxs-lookup"><span data-stu-id="09859-119">WinRM</span></span>](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)
- [<span data-ttu-id="09859-120">軟體清查記錄</span><span class="sxs-lookup"><span data-stu-id="09859-120">Software Inventory Logging</span></span>](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)

