---
title: Windows Management Framework (WMF)
ms.date: 2016-05-16
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: eacd33d2a0a92977a3990132e23eef9871a7f0dc
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-TW
---
# <a name="windows-management-framework"></a><span data-ttu-id="42577-103">Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="42577-103">Windows Management Framework</span></span>

<span data-ttu-id="42577-104">Windows Management Framework (WMF) 是一種傳遞機制，可在各式各樣的 Windows 和 Windows Server 中提供一致的管理介面。</span><span class="sxs-lookup"><span data-stu-id="42577-104">Windows Management Framework (WMF) is the delivery mechanism that provides a consistent management interface across the various flavors of Windows and Windows Server.</span></span>
<span data-ttu-id="42577-105">安裝 WMF 後，客戶即可順暢自如地在其混合了各種作業系統的環境中操作。</span><span class="sxs-lookup"><span data-stu-id="42577-105">With the installation of WMF, customers get a seamless way to interoperate between mixes of OSes in their environment.</span></span>
<span data-ttu-id="42577-106">WMF 會更新指定 Windows 和 Windows Server 版本的管理功能，於安裝較低版本的 Windows 和 Windows Server (一般是低 2 個版本) 時提供。</span><span class="sxs-lookup"><span data-stu-id="42577-106">WMF makes the updates to management functionality, in a given release of Windows and Windows Server, available for installation on lower versions (typically, 2 lower versions) of Windows and Windows Server.</span></span>

<span data-ttu-id="42577-107">WMF 安裝新增及 (或) 更新下列功能︰</span><span class="sxs-lookup"><span data-stu-id="42577-107">WMF installation adds and/or updates the following features:</span></span>

- <span data-ttu-id="42577-108">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="42577-108">Windows PowerShell</span></span>
- <span data-ttu-id="42577-109">Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="42577-109">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="42577-110">Windows PowerShell 整合式指令碼環境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="42577-110">Windows PowerShell Integrated Script Environment (ISE)</span></span>
- <span data-ttu-id="42577-111">Windows 遠端管理 (WinRM)</span><span class="sxs-lookup"><span data-stu-id="42577-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="42577-112">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="42577-112">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="42577-113">Windows PowerShell Web 服務 (Management OData IIS 擴充功能)</span><span class="sxs-lookup"><span data-stu-id="42577-113">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="42577-114">軟體清查記錄 (SIL)</span><span class="sxs-lookup"><span data-stu-id="42577-114">Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="42577-115">伺服器管理員 CIM 提供者</span><span class="sxs-lookup"><span data-stu-id="42577-115">Server Manager CIM Provider</span></span>

## <a name="wmf-release-notes"></a><span data-ttu-id="42577-116">WMF 版本資訊</span><span class="sxs-lookup"><span data-stu-id="42577-116">WMF Release Notes</span></span>
<span data-ttu-id="42577-117">如需深入了解 PowerShell 的各種增強功能以及指定 WMF 的其他元件，請參閱下列版本資訊連結︰</span><span class="sxs-lookup"><span data-stu-id="42577-117">To learn about various enhancements in PowerShell and other components of a given WMF, please refer to the links below to review the release notes:</span></span>


- [<span data-ttu-id="42577-118">WMF 5.1 (預覽)</span><span class="sxs-lookup"><span data-stu-id="42577-118">WMF 5.1 (Preview)</span></span>](5.1/release-notes.md)
- [<span data-ttu-id="42577-119">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="42577-119">WMF 5.0</span></span>](5.0/releasenotes.md)


## <a name="wmf-availability-across-windows-operating-systems"></a><span data-ttu-id="42577-120">各 Windows 作業系統的 WMF 可用性</span><span class="sxs-lookup"><span data-stu-id="42577-120">WMF Availability Across Windows Operating Systems</span></span>

><span data-ttu-id="42577-121">TODO︰將連結新增至欄標題的特定 WMF DLC</span><span class="sxs-lookup"><span data-stu-id="42577-121">TODO: Add links to specific WMF DLC on the column header</span></span>

| <span data-ttu-id="42577-122">作業系統版本</span><span class="sxs-lookup"><span data-stu-id="42577-122">Operating System Version</span></span> | [<span data-ttu-id="42577-123">WMF 5.1 預覽*</span><span class="sxs-lookup"><span data-stu-id="42577-123">WMF 5.1 Preview*</span></span>]() | [<span data-ttu-id="42577-124">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="42577-124">WMF 5.0</span></span>]() | [<span data-ttu-id="42577-125">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="42577-125">WMF 4.0</span></span>]() |  [<span data-ttu-id="42577-126">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="42577-126">WMF 3.0</span></span>]() | [<span data-ttu-id="42577-127">WMF (2.0)</span><span class="sxs-lookup"><span data-stu-id="42577-127">WMF (2.0)</span></span>]() |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| <span data-ttu-id="42577-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="42577-128">Windows Server 2016</span></span> | <span data-ttu-id="42577-129">隨產品附贈*</span><span class="sxs-lookup"><span data-stu-id="42577-129">Ships in-box*</span></span> | <span data-ttu-id="42577-130">隨產品附贈*</span><span class="sxs-lookup"><span data-stu-id="42577-130">Ships in-box*</span></span> |  |  |  |
| <span data-ttu-id="42577-131">Windows 10</span><span class="sxs-lookup"><span data-stu-id="42577-131">Windows 10</span></span> | <span data-ttu-id="42577-132">隨產品附贈*</span><span class="sxs-lookup"><span data-stu-id="42577-132">Ships in-box*</span></span> | <span data-ttu-id="42577-133">隨產品附贈*</span><span class="sxs-lookup"><span data-stu-id="42577-133">Ships in-box*</span></span>  | | | |  
| <span data-ttu-id="42577-134">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="42577-134">Windows Server 2012 R2</span></span>| <span data-ttu-id="42577-135">??</span><span class="sxs-lookup"><span data-stu-id="42577-135">??</span></span> | <span data-ttu-id="42577-136">是</span><span class="sxs-lookup"><span data-stu-id="42577-136">Yes</span></span> | <span data-ttu-id="42577-137">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="42577-137">Ships in-box</span></span> |  |  |
| <span data-ttu-id="42577-138">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="42577-138">Windows 8.1</span></span> | <span data-ttu-id="42577-139">??</span><span class="sxs-lookup"><span data-stu-id="42577-139">??</span></span> | <span data-ttu-id="42577-140">是</span><span class="sxs-lookup"><span data-stu-id="42577-140">Yes</span></span> |  <span data-ttu-id="42577-141">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="42577-141">Ships in-box</span></span> |  |  |
| <span data-ttu-id="42577-142">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="42577-142">Windows Server 2012</span></span> | <span data-ttu-id="42577-143">??</span><span class="sxs-lookup"><span data-stu-id="42577-143">??</span></span> | <span data-ttu-id="42577-144">是</span><span class="sxs-lookup"><span data-stu-id="42577-144">Yes</span></span> | <span data-ttu-id="42577-145">是</span><span class="sxs-lookup"><span data-stu-id="42577-145">Yes</span></span> |  <span data-ttu-id="42577-146">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="42577-146">Ships in-box</span></span> | |
| <span data-ttu-id="42577-147">Windows 8</span><span class="sxs-lookup"><span data-stu-id="42577-147">Windows 8</span></span> |  |  |  | <span data-ttu-id="42577-148">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="42577-148">Ships in-box</span></span> | |
| <span data-ttu-id="42577-149">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="42577-149">Windows Server 2008 R2 SP1</span></span> | <span data-ttu-id="42577-150">??</span><span class="sxs-lookup"><span data-stu-id="42577-150">??</span></span> | <span data-ttu-id="42577-151">是</span><span class="sxs-lookup"><span data-stu-id="42577-151">Yes</span></span> | <span data-ttu-id="42577-152">是</span><span class="sxs-lookup"><span data-stu-id="42577-152">Yes</span></span> |  <span data-ttu-id="42577-153">是</span><span class="sxs-lookup"><span data-stu-id="42577-153">Yes</span></span>| <span data-ttu-id="42577-154">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="42577-154">Ships in-box</span></span> |
| <span data-ttu-id="42577-155">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="42577-155">Windows 7 SP1</span></span>  | <span data-ttu-id="42577-156">??</span><span class="sxs-lookup"><span data-stu-id="42577-156">??</span></span> | <span data-ttu-id="42577-157">是</span><span class="sxs-lookup"><span data-stu-id="42577-157">Yes</span></span> | <span data-ttu-id="42577-158">是</span><span class="sxs-lookup"><span data-stu-id="42577-158">Yes</span></span> | <span data-ttu-id="42577-159">是</span><span class="sxs-lookup"><span data-stu-id="42577-159">Yes</span></span> | <span data-ttu-id="42577-160">隨產品附贈</span><span class="sxs-lookup"><span data-stu-id="42577-160">Ships in-box</span></span> |
| <span data-ttu-id="42577-161">Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="42577-161">Windows Server 2008 SP2</span></span> | | | | <span data-ttu-id="42577-162">是</span><span class="sxs-lookup"><span data-stu-id="42577-162">Yes</span></span> | <span data-ttu-id="42577-163">是</span><span class="sxs-lookup"><span data-stu-id="42577-163">Yes</span></span> |
| <span data-ttu-id="42577-164">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="42577-164">Windows Vista</span></span> | | | | | <span data-ttu-id="42577-165">是</span><span class="sxs-lookup"><span data-stu-id="42577-165">Yes</span></span> |
| <span data-ttu-id="42577-166">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="42577-166">Windows Server 2003</span></span>| | | |  | <span data-ttu-id="42577-167">是</span><span class="sxs-lookup"><span data-stu-id="42577-167">Yes</span></span> |
| <span data-ttu-id="42577-168">Windows XP</span><span class="sxs-lookup"><span data-stu-id="42577-168">Windows XP</span></span> | | | |  | <span data-ttu-id="42577-169">是</span><span class="sxs-lookup"><span data-stu-id="42577-169">Yes</span></span> |

><span data-ttu-id="42577-170">TODO︰說明上表中的 *</span><span class="sxs-lookup"><span data-stu-id="42577-170">TODO: Explain * in the above table</span></span>
