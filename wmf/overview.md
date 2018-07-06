---
ms.date: 06/12/2018
keywords: wmf,powershell,設定
title: Windows Management Framework (WMF)
ms.openlocfilehash: 17011f88c364cb56a0c87f092873ccd99db450bc
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36943602"
---
# <a name="windows-management-framework"></a><span data-ttu-id="962a5-103">Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="962a5-103">Windows Management Framework</span></span>

<span data-ttu-id="962a5-104">Windows Management Framework (WMF) 提供 Windows 的一致管理介面。</span><span class="sxs-lookup"><span data-stu-id="962a5-104">Windows Management Framework (WMF) provides a consistent management interface for Windows.</span></span> <span data-ttu-id="962a5-105">WMF 提供一種順暢的方式，來管理各種 Windows 用戶端和 Windows Server 版本。</span><span class="sxs-lookup"><span data-stu-id="962a5-105">WMF provides a seamless way to manage various versions of Windows client and Windows Server.</span></span> <span data-ttu-id="962a5-106">WMF 安裝程式套件包含管理功能的更新，而且可用於舊版 Windows。</span><span class="sxs-lookup"><span data-stu-id="962a5-106">WMF installer packages contain updates to management functionality and are available for older versions of Windows.</span></span>

<span data-ttu-id="962a5-107">WMF 安裝新增及 (或) 更新下列功能︰</span><span class="sxs-lookup"><span data-stu-id="962a5-107">WMF installation adds and/or updates the following features:</span></span>

- <span data-ttu-id="962a5-108">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="962a5-108">Windows PowerShell</span></span>
- <span data-ttu-id="962a5-109">Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="962a5-109">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="962a5-110">Windows PowerShell 整合式指令碼環境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="962a5-110">Windows PowerShell Integrated Script Environment (ISE)</span></span>
- <span data-ttu-id="962a5-111">Windows 遠端管理 (WinRM)</span><span class="sxs-lookup"><span data-stu-id="962a5-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="962a5-112">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="962a5-112">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="962a5-113">Windows PowerShell Web 服務 (Management OData IIS 擴充功能)</span><span class="sxs-lookup"><span data-stu-id="962a5-113">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="962a5-114">軟體清查記錄 (SIL)</span><span class="sxs-lookup"><span data-stu-id="962a5-114">Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="962a5-115">伺服器管理員 CIM 提供者</span><span class="sxs-lookup"><span data-stu-id="962a5-115">Server Manager CIM Provider</span></span>

## <a name="wmf-release-notes"></a><span data-ttu-id="962a5-116">WMF 版本資訊</span><span class="sxs-lookup"><span data-stu-id="962a5-116">WMF Release Notes</span></span>

<span data-ttu-id="962a5-117">如需深入了解 PowerShell 的各種增強功能以及指定 WMF 的其他元件，請參閱下列版本資訊連結︰</span><span class="sxs-lookup"><span data-stu-id="962a5-117">To learn about various enhancements in PowerShell and other components of a given WMF, please refer to the links below to review the release notes:</span></span>

- [<span data-ttu-id="962a5-118">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="962a5-118">WMF 5.1</span></span>](5.1/release-notes.md)
- [<span data-ttu-id="962a5-119">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="962a5-119">WMF 5.0</span></span>](5.0/releasenotes.md)
- [<span data-ttu-id="962a5-120">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="962a5-120">WMF 4.0</span></span>](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [<span data-ttu-id="962a5-121">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="962a5-121">WMF 3.0</span></span>](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a><span data-ttu-id="962a5-122">各 Windows 作業系統的 WMF 可用性</span><span class="sxs-lookup"><span data-stu-id="962a5-122">WMF Availability Across Windows Operating Systems</span></span>

|<span data-ttu-id="962a5-123">作業系統版本</span><span class="sxs-lookup"><span data-stu-id="962a5-123">Operating System Version</span></span>  |<span data-ttu-id="962a5-124">[WMF 5.1][]</span><span class="sxs-lookup"><span data-stu-id="962a5-124">[WMF 5.1][]</span></span> |<span data-ttu-id="962a5-125">[WMF 5.0][]</span><span class="sxs-lookup"><span data-stu-id="962a5-125">[WMF 5.0][]</span></span> |<span data-ttu-id="962a5-126">[WMF 4.0][]</span><span class="sxs-lookup"><span data-stu-id="962a5-126">[WMF 4.0][]</span></span> |<span data-ttu-id="962a5-127">[WMF 3.0][]</span><span class="sxs-lookup"><span data-stu-id="962a5-127">[WMF 3.0][]</span></span>  |<span data-ttu-id="962a5-128">[WMF 2.0][]</span><span class="sxs-lookup"><span data-stu-id="962a5-128">[WMF 2.0][]</span></span> |
|--------------------------|------------|------------|------------|-------------|------------|
|<span data-ttu-id="962a5-129">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="962a5-129">Windows Server 2016</span></span>       |<span data-ttu-id="962a5-130">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="962a5-130">Ships in-box</span></span>|            |            |             |            |
|<span data-ttu-id="962a5-131">Windows 10</span><span class="sxs-lookup"><span data-stu-id="962a5-131">Windows 10</span></span>                |<span data-ttu-id="962a5-132">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="962a5-132">Ships in-box</span></span>|<span data-ttu-id="962a5-133">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="962a5-133">Ships in-box</span></span>|            |             |            |
|<span data-ttu-id="962a5-134">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="962a5-134">Windows Server 2012 R2</span></span>    |<span data-ttu-id="962a5-135">是</span><span class="sxs-lookup"><span data-stu-id="962a5-135">Yes</span></span>         |<span data-ttu-id="962a5-136">是</span><span class="sxs-lookup"><span data-stu-id="962a5-136">Yes</span></span>         |<span data-ttu-id="962a5-137">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="962a5-137">Ships in-box</span></span>|             |            |
|<span data-ttu-id="962a5-138">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="962a5-138">Windows 8.1</span></span>               |<span data-ttu-id="962a5-139">是</span><span class="sxs-lookup"><span data-stu-id="962a5-139">Yes</span></span>         |<span data-ttu-id="962a5-140">是</span><span class="sxs-lookup"><span data-stu-id="962a5-140">Yes</span></span>         |<span data-ttu-id="962a5-141">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="962a5-141">Ships in-box</span></span>|             |            |
|<span data-ttu-id="962a5-142">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="962a5-142">Windows Server 2012</span></span>       |<span data-ttu-id="962a5-143">是</span><span class="sxs-lookup"><span data-stu-id="962a5-143">Yes</span></span>         |<span data-ttu-id="962a5-144">是</span><span class="sxs-lookup"><span data-stu-id="962a5-144">Yes</span></span>         |<span data-ttu-id="962a5-145">是</span><span class="sxs-lookup"><span data-stu-id="962a5-145">Yes</span></span>         |<span data-ttu-id="962a5-146">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="962a5-146">Ships in-box</span></span> |            |
|<span data-ttu-id="962a5-147">Windows 8</span><span class="sxs-lookup"><span data-stu-id="962a5-147">Windows 8</span></span>                 |            |            |            |<span data-ttu-id="962a5-148">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="962a5-148">Ships in-box</span></span> |            |
|<span data-ttu-id="962a5-149">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="962a5-149">Windows Server 2008 R2 SP1</span></span>|<span data-ttu-id="962a5-150">是</span><span class="sxs-lookup"><span data-stu-id="962a5-150">Yes</span></span>         |<span data-ttu-id="962a5-151">是</span><span class="sxs-lookup"><span data-stu-id="962a5-151">Yes</span></span>         |<span data-ttu-id="962a5-152">是</span><span class="sxs-lookup"><span data-stu-id="962a5-152">Yes</span></span>         |<span data-ttu-id="962a5-153">是</span><span class="sxs-lookup"><span data-stu-id="962a5-153">Yes</span></span>          |<span data-ttu-id="962a5-154">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="962a5-154">Ships in-box</span></span>|
|<span data-ttu-id="962a5-155">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="962a5-155">Windows 7 SP1</span></span>             |<span data-ttu-id="962a5-156">是</span><span class="sxs-lookup"><span data-stu-id="962a5-156">Yes</span></span>         |<span data-ttu-id="962a5-157">是</span><span class="sxs-lookup"><span data-stu-id="962a5-157">Yes</span></span>         |<span data-ttu-id="962a5-158">是</span><span class="sxs-lookup"><span data-stu-id="962a5-158">Yes</span></span>         |<span data-ttu-id="962a5-159">是</span><span class="sxs-lookup"><span data-stu-id="962a5-159">Yes</span></span>          |<span data-ttu-id="962a5-160">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="962a5-160">Ships in-box</span></span>|
|<span data-ttu-id="962a5-161">Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="962a5-161">Windows Server 2008 SP2</span></span>   |            |            |            |<span data-ttu-id="962a5-162">是</span><span class="sxs-lookup"><span data-stu-id="962a5-162">Yes</span></span>          |<span data-ttu-id="962a5-163">是</span><span class="sxs-lookup"><span data-stu-id="962a5-163">Yes</span></span>         |
|<span data-ttu-id="962a5-164">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="962a5-164">Windows Vista</span></span>             |            |            |            |             |<span data-ttu-id="962a5-165">是</span><span class="sxs-lookup"><span data-stu-id="962a5-165">Yes</span></span>         |
|<span data-ttu-id="962a5-166">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="962a5-166">Windows Server 2003</span></span>       |            |            |            |             |<span data-ttu-id="962a5-167">是</span><span class="sxs-lookup"><span data-stu-id="962a5-167">Yes</span></span>         |
|<span data-ttu-id="962a5-168">Windows XP</span><span class="sxs-lookup"><span data-stu-id="962a5-168">Windows XP</span></span>                |            |            |            |<span data-ttu-id="962a5-169">是</span><span class="sxs-lookup"><span data-stu-id="962a5-169">Yes</span></span>          |            |

<span data-ttu-id="962a5-170">**隨產品出貨**：所指定 WMF 版本的功能已與指出版本的 Windows 用戶端或 Windows Server 一起出貨。</span><span class="sxs-lookup"><span data-stu-id="962a5-170">**Ships in-box**: The features of the specified version of WMF were shipped in the indicated version of Windows client or Windows Server.</span></span>

[WMF 5.1]: https://aka.ms/wmf51download
[WMF 5.0]: https://aka.ms/wmf5download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
