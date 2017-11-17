---
title: Windows Management Framework (WMF)
ms.date: 2017-02-14
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 749dd8b19592cb5f40a5aed32d28edeb5cb2dfc9
ms.sourcegitcommit: bb2c52577a519c0599a0b3c961f749fe0df70a45
ms.translationtype: HT
ms.contentlocale: zh-TW
---
# <a name="windows-management-framework"></a><span data-ttu-id="30664-103">Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="30664-103">Windows Management Framework</span></span>

<span data-ttu-id="30664-104">Windows Management Framework (WMF) 是一種傳遞機制，可在各式各樣的 Windows 和 Windows Server 中提供一致的管理介面。</span><span class="sxs-lookup"><span data-stu-id="30664-104">Windows Management Framework (WMF) is the delivery mechanism that provides a consistent management interface across the various flavors of Windows and Windows Server.</span></span>
<span data-ttu-id="30664-105">安裝 WMF 後，客戶即可順暢自如地在其混合了各種作業系統的環境中操作。</span><span class="sxs-lookup"><span data-stu-id="30664-105">With the installation of WMF, customers get a seamless way to interoperate between mixes of OSes in their environment.</span></span>
<span data-ttu-id="30664-106">WMF 會更新指定 Windows 和 Windows Server 版本的管理功能，於安裝較低版本的 Windows 和 Windows Server (一般是低 2 個版本) 時提供。</span><span class="sxs-lookup"><span data-stu-id="30664-106">WMF makes the updates to management functionality, in a given release of Windows and Windows Server, available for installation on lower versions (typically, 2 lower versions) of Windows and Windows Server.</span></span>

<span data-ttu-id="30664-107">WMF 安裝新增及 (或) 更新下列功能︰</span><span class="sxs-lookup"><span data-stu-id="30664-107">WMF installation adds and/or updates the following features:</span></span>

- <span data-ttu-id="30664-108">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="30664-108">Windows PowerShell</span></span>
- <span data-ttu-id="30664-109">Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="30664-109">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="30664-110">Windows PowerShell 整合式指令碼環境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="30664-110">Windows PowerShell Integrated Script Environment (ISE)</span></span>
- <span data-ttu-id="30664-111">Windows 遠端管理 (WinRM)</span><span class="sxs-lookup"><span data-stu-id="30664-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="30664-112">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="30664-112">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="30664-113">Windows PowerShell Web 服務 (Management OData IIS 擴充功能)</span><span class="sxs-lookup"><span data-stu-id="30664-113">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="30664-114">軟體清查記錄 (SIL)</span><span class="sxs-lookup"><span data-stu-id="30664-114">Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="30664-115">伺服器管理員 CIM 提供者</span><span class="sxs-lookup"><span data-stu-id="30664-115">Server Manager CIM Provider</span></span>

## <a name="wmf-release-notes"></a><span data-ttu-id="30664-116">WMF 版本資訊</span><span class="sxs-lookup"><span data-stu-id="30664-116">WMF Release Notes</span></span>

<span data-ttu-id="30664-117">如需深入了解 PowerShell 的各種增強功能以及指定 WMF 的其他元件，請參閱下列版本資訊連結︰</span><span class="sxs-lookup"><span data-stu-id="30664-117">To learn about various enhancements in PowerShell and other components of a given WMF, please refer to the links below to review the release notes:</span></span>

- [<span data-ttu-id="30664-118">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="30664-118">WMF 5.1</span></span>](5.1/release-notes.md)
- [<span data-ttu-id="30664-119">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="30664-119">WMF 5.0</span></span>](5.0/releasenotes.md)
- [<span data-ttu-id="30664-120">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="30664-120">WMF 4.0</span></span>](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [<span data-ttu-id="30664-121">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="30664-121">WMF 3.0</span></span>](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a><span data-ttu-id="30664-122">各 Windows 作業系統的 WMF 可用性</span><span class="sxs-lookup"><span data-stu-id="30664-122">WMF Availability Across Windows Operating Systems</span></span>

| <span data-ttu-id="30664-123">作業系統版本</span><span class="sxs-lookup"><span data-stu-id="30664-123">Operating System Version</span></span> | [<span data-ttu-id="30664-124">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="30664-124">WMF 5.1</span></span>](https://aka.ms/wmf51download) | [<span data-ttu-id="30664-125">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="30664-125">WMF 5.0</span></span>](https://aka.ms/wmf5download) | [<span data-ttu-id="30664-126">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="30664-126">WMF 4.0</span></span>](https://aka.ms/wmf4download) |  [<span data-ttu-id="30664-127">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="30664-127">WMF 3.0</span></span>](https://aka.ms/wmf3download) | [<span data-ttu-id="30664-128">WMF 2.0</span><span class="sxs-lookup"><span data-stu-id="30664-128">WMF 2.0</span></span>](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| <span data-ttu-id="30664-129">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="30664-129">Windows Server 2016</span></span> | <span data-ttu-id="30664-130">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="30664-130">Ships in-box</span></span> |  |  |  |  |
| <span data-ttu-id="30664-131">Windows 10</span><span class="sxs-lookup"><span data-stu-id="30664-131">Windows 10</span></span> | <span data-ttu-id="30664-132">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="30664-132">Ships in-box</span></span> | <span data-ttu-id="30664-133">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="30664-133">Ships in-box</span></span>  | | | |  
| <span data-ttu-id="30664-134">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="30664-134">Windows Server 2012 R2</span></span>| <span data-ttu-id="30664-135">是</span><span class="sxs-lookup"><span data-stu-id="30664-135">Yes</span></span> | <span data-ttu-id="30664-136">是</span><span class="sxs-lookup"><span data-stu-id="30664-136">Yes</span></span> | <span data-ttu-id="30664-137">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="30664-137">Ships in-box</span></span> |  |  |
| <span data-ttu-id="30664-138">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="30664-138">Windows 8.1</span></span> | <span data-ttu-id="30664-139">是</span><span class="sxs-lookup"><span data-stu-id="30664-139">Yes</span></span> | <span data-ttu-id="30664-140">是</span><span class="sxs-lookup"><span data-stu-id="30664-140">Yes</span></span> |  <span data-ttu-id="30664-141">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="30664-141">Ships in-box</span></span> |  |  |
| <span data-ttu-id="30664-142">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="30664-142">Windows Server 2012</span></span> | <span data-ttu-id="30664-143">是</span><span class="sxs-lookup"><span data-stu-id="30664-143">Yes</span></span> | <span data-ttu-id="30664-144">是</span><span class="sxs-lookup"><span data-stu-id="30664-144">Yes</span></span> | <span data-ttu-id="30664-145">是</span><span class="sxs-lookup"><span data-stu-id="30664-145">Yes</span></span> |  <span data-ttu-id="30664-146">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="30664-146">Ships in-box</span></span> | |
| <span data-ttu-id="30664-147">Windows 8</span><span class="sxs-lookup"><span data-stu-id="30664-147">Windows 8</span></span> |  |  |  | <span data-ttu-id="30664-148">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="30664-148">Ships in-box</span></span> | |
| <span data-ttu-id="30664-149">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="30664-149">Windows Server 2008 R2 SP1</span></span> | <span data-ttu-id="30664-150">是</span><span class="sxs-lookup"><span data-stu-id="30664-150">Yes</span></span> | <span data-ttu-id="30664-151">是</span><span class="sxs-lookup"><span data-stu-id="30664-151">Yes</span></span> | <span data-ttu-id="30664-152">是</span><span class="sxs-lookup"><span data-stu-id="30664-152">Yes</span></span> |  <span data-ttu-id="30664-153">是</span><span class="sxs-lookup"><span data-stu-id="30664-153">Yes</span></span>| <span data-ttu-id="30664-154">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="30664-154">Ships in-box</span></span> |
| <span data-ttu-id="30664-155">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="30664-155">Windows 7 SP1</span></span>  | <span data-ttu-id="30664-156">是</span><span class="sxs-lookup"><span data-stu-id="30664-156">Yes</span></span> | <span data-ttu-id="30664-157">是</span><span class="sxs-lookup"><span data-stu-id="30664-157">Yes</span></span> | <span data-ttu-id="30664-158">是</span><span class="sxs-lookup"><span data-stu-id="30664-158">Yes</span></span> | <span data-ttu-id="30664-159">是</span><span class="sxs-lookup"><span data-stu-id="30664-159">Yes</span></span> | <span data-ttu-id="30664-160">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="30664-160">Ships in-box</span></span> |
| <span data-ttu-id="30664-161">Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="30664-161">Windows Server 2008 SP2</span></span> | | | | <span data-ttu-id="30664-162">是</span><span class="sxs-lookup"><span data-stu-id="30664-162">Yes</span></span> | <span data-ttu-id="30664-163">是</span><span class="sxs-lookup"><span data-stu-id="30664-163">Yes</span></span> |
| <span data-ttu-id="30664-164">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="30664-164">Windows Vista</span></span> | | | | | <span data-ttu-id="30664-165">是</span><span class="sxs-lookup"><span data-stu-id="30664-165">Yes</span></span> |
| <span data-ttu-id="30664-166">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="30664-166">Windows Server 2003</span></span>| | | |  | <span data-ttu-id="30664-167">是</span><span class="sxs-lookup"><span data-stu-id="30664-167">Yes</span></span> |
| <span data-ttu-id="30664-168">Windows XP</span><span class="sxs-lookup"><span data-stu-id="30664-168">Windows XP</span></span> | | | |  | <span data-ttu-id="30664-169">是</span><span class="sxs-lookup"><span data-stu-id="30664-169">Yes</span></span> |

<span data-ttu-id="30664-170">**隨產品附贈**：`specified WMF` 的功能已和指定版本的 Windows 和 Windows Server 一起出貨。</span><span class="sxs-lookup"><span data-stu-id="30664-170">**"Ships in-box"**: The features of the `specified WMF` were shipped in the indicated version of  Windows and Windows Server.</span></span>
<span data-ttu-id="30664-171">因此，`specified WMF` 不需要安裝在指定的作業系統版本上。</span><span class="sxs-lookup"><span data-stu-id="30664-171">Hence, the `specified WMF` doesn't need to be installed on the indicated operating system versions.</span></span>
