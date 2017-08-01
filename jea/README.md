---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "讀我檔案"
ms.technology: powershell
ms.openlocfilehash: b0ef4ff685b82e1a4e9ab83a45736720df7b39a2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-TW
---
# <a name="just-enough-administration"></a><span data-ttu-id="de52a-103">Just Enough Administration</span><span class="sxs-lookup"><span data-stu-id="de52a-103">Just Enough Administration</span></span>
<span data-ttu-id="de52a-104">Just Enough Administration (JEA) 是安全性技術，允許將可透過 PowerShell 管理的任何項目委派管理。</span><span class="sxs-lookup"><span data-stu-id="de52a-104">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything that can be managed with PowerShell.</span></span>
<span data-ttu-id="de52a-105">使用 JEA，您可以︰</span><span class="sxs-lookup"><span data-stu-id="de52a-105">With JEA, you can:</span></span>
- <span data-ttu-id="de52a-106">利用虛擬帳戶，代表一般使用者執行特殊權限動作，以**減少電腦上的系統管理員數目**。</span><span class="sxs-lookup"><span data-stu-id="de52a-106">**Reduce the number of administrators on your machines** by leveraging virtual accounts that perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="de52a-107">指定使用者可以執行的 Cmdlet、函式和外部命令，以**限制使用者可以執行的工作**。</span><span class="sxs-lookup"><span data-stu-id="de52a-107">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="de52a-108">透過 "Over The Shoulder" 文字記錄，顯示使用者在工作階段期間實際執行的命令，以**深入了解使用者正在執行的工作**。</span><span class="sxs-lookup"><span data-stu-id="de52a-108">**Better understand what your users are doing** with "over the shoulder" transcriptions that show you exactly what commands a user executed during a session.</span></span>

<span data-ttu-id="de52a-109">**為何重要？**</span><span class="sxs-lookup"><span data-stu-id="de52a-109">**Why is this important?**</span></span>  
<span data-ttu-id="de52a-110">假設在一般情況下，您的 DNS 伺服器會與 Active Directory 網域控制站共置。</span><span class="sxs-lookup"><span data-stu-id="de52a-110">Consider the common scenario where your DNS servers are co-located with your Active Directory Domain Controllers.</span></span>
<span data-ttu-id="de52a-111">您的 DNS 系統管理員必須具有本機系統管理員權限，才能修正 DNS 伺服器的問題，但若要這樣做，您必須將其設為具有高度權限之 "Domain Admins" 安全性群組的成員。</span><span class="sxs-lookup"><span data-stu-id="de52a-111">Your DNS administrators need to have local administrator privileges to fix issues with the DNS server, but in order to do so you have to make them members of the highly privileged "Domain Admins" security group.</span></span>
<span data-ttu-id="de52a-112">這個方法能有效地讓 DNS 系統管理員控制您的整個網域，並存取該電腦上的所有資源。</span><span class="sxs-lookup"><span data-stu-id="de52a-112">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="de52a-113">有了 JEA，您就可以設定 DNS 系統管理員的角色，並讓他們只存取完成其工作所需的所有命令。</span><span class="sxs-lookup"><span data-stu-id="de52a-113">With JEA in place, you can configure a role for your DNS administrators that gives them access to all the commands they need to get their job done, but nothing more.</span></span>
<span data-ttu-id="de52a-114">這表示您可以提供適當的存取權以修復有害的 DNS 快取，卻不會無意中給予他們使用 Active Directory、瀏覽檔案、或執行有潛在危險指令碼的權限。</span><span class="sxs-lookup"><span data-stu-id="de52a-114">This means you can provide the appropriate access to repair a poisoned DNS cache without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span>
<span data-ttu-id="de52a-115">更棒的是，當 JEA 工作階段設定為使用一次性特殊權限虛擬帳戶時，您的 DNS 系統管理員就可以在使用*非特殊權限*認證連接到伺服器的情況下，仍然能夠執行特殊權限命令。</span><span class="sxs-lookup"><span data-stu-id="de52a-115">Better yet, when the JEA session is configured to use one-time privileged virtual accounts, your DNS administrators can connect to the server using *unprivileged* credentials and still be able to run privileged commands.</span></span>

## <a name="availability"></a><span data-ttu-id="de52a-116">可用性</span><span class="sxs-lookup"><span data-stu-id="de52a-116">Availability</span></span>
<span data-ttu-id="de52a-117">JEA 是與 Windows Server 2016 同期開發的功能，舊版 Windows 可透過 Windows Management Framework 更新來使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="de52a-117">JEA is being developed in parallel to Windows Server 2016, and is available on older versions of Windows through Windows Management Framework updates.</span></span>
<span data-ttu-id="de52a-118">目前的 JEA 版本適用於下列平台︰</span><span class="sxs-lookup"><span data-stu-id="de52a-118">The current release of JEA is available on the following platforms:</span></span>

<span data-ttu-id="de52a-119">**Windows Server**</span><span class="sxs-lookup"><span data-stu-id="de52a-119">**Windows Server**</span></span>
- <span data-ttu-id="de52a-120">Windows Server 2016 Technical Preview 4 及更新版本</span><span class="sxs-lookup"><span data-stu-id="de52a-120">Windows Server 2016 Technical Preview 4 and higher</span></span>
- <span data-ttu-id="de52a-121">安裝 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 的 Windows Server 2012 R2、2012 和 2008 R2\*</span><span class="sxs-lookup"><span data-stu-id="de52a-121">Windows Server 2012 R2, 2012, and 2008 R2\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="de52a-122">**Windows 用戶端**</span><span class="sxs-lookup"><span data-stu-id="de52a-122">**Windows Client**</span></span>
- <span data-ttu-id="de52a-123">安裝的 11 月更新 (1511) 的 Windows 10</span><span class="sxs-lookup"><span data-stu-id="de52a-123">Windows 10 with the November Update (1511) installed</span></span>
- <span data-ttu-id="de52a-124">安裝 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 的 Windows 8.1、8 和 7\*</span><span class="sxs-lookup"><span data-stu-id="de52a-124">Windows 8.1, 8, and 7\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="de52a-125">\* Windows Server 2008 R2 或 Windows 7 目前不提供 JEA 工作階段中的虛擬帳戶支援。</span><span class="sxs-lookup"><span data-stu-id="de52a-125">\* Support for virtual accounts in JEA sessions is currently not available on Windows Server 2008 R2 or Windows 7.</span></span>


## <a name="explore-the-experience-guide"></a><span data-ttu-id="de52a-126">探索體驗指南</span><span class="sxs-lookup"><span data-stu-id="de52a-126">Explore the experience guide</span></span>
<span data-ttu-id="de52a-127">準備好了解如何撰寫、部署及使用您專屬的 JEA 端點了嗎？</span><span class="sxs-lookup"><span data-stu-id="de52a-127">Ready to learn how to author, deploy, and use your own JEA endpoint?</span></span>

<span data-ttu-id="de52a-128">本指南可讓您快速開始使用預先建置的 JEA 端點，以了解使用者體驗，然後逐步引導您從頭開始重新建立端點，以利示範工作階段設定和角色功能等概念。</span><span class="sxs-lookup"><span data-stu-id="de52a-128">This guide gets you started quickly with a pre-built JEA endpoint to get an idea of what the end-user experience is like, then walks you through recreating an endpoint from scratch to help demonstrate concepts like session configurations and Role Capabilities.</span></span>

1.  <span data-ttu-id="de52a-129">[簡介](introduction.md) </span><span class="sxs-lookup"><span data-stu-id="de52a-129">[Introduction](introduction.md) </span></span>  
<span data-ttu-id="de52a-130">簡短回顧您應該重視 JEA 的原因</span><span class="sxs-lookup"><span data-stu-id="de52a-130">Briefly review why you should care about JEA</span></span>

2.  [<span data-ttu-id="de52a-131">必要條件</span><span class="sxs-lookup"><span data-stu-id="de52a-131">Prerequisites</span></span>](prerequisites.md)  
<span data-ttu-id="de52a-132">說明如何設定環境</span><span class="sxs-lookup"><span data-stu-id="de52a-132">Explains how to set up your environment</span></span>

3.  [<span data-ttu-id="de52a-133">使用 JEA</span><span class="sxs-lookup"><span data-stu-id="de52a-133">Using JEA</span></span>](using-jea.md)  
<span data-ttu-id="de52a-134">協助您從了解使用 JEA 的操作員體驗開始</span><span class="sxs-lookup"><span data-stu-id="de52a-134">Helps you start by understanding the operator experience of using JEA</span></span>

4.  [<span data-ttu-id="de52a-135">重現示範</span><span class="sxs-lookup"><span data-stu-id="de52a-135">Remake the Demo</span></span>](remake-the-demo-endpoint.md)  
<span data-ttu-id="de52a-136">從頭開始建立 JEA 工作階段設定</span><span class="sxs-lookup"><span data-stu-id="de52a-136">Create a JEA Session Configuration from scratch</span></span>

5.  [<span data-ttu-id="de52a-137">角色功能</span><span class="sxs-lookup"><span data-stu-id="de52a-137">Role Capabilities</span></span>](role-capabilities.md)  
<span data-ttu-id="de52a-138">了解如何使用角色功能檔案來自訂 JEA 功能</span><span class="sxs-lookup"><span data-stu-id="de52a-138">Learn about how to customize JEA capabilities with Role Capability Files</span></span>

6.  [<span data-ttu-id="de52a-139">端對端 - Active Directory</span><span class="sxs-lookup"><span data-stu-id="de52a-139">End to End - Active Directory</span></span>](end-to-end---active-directory.md)  
<span data-ttu-id="de52a-140">建立全新的端點以管理 Active Directory</span><span class="sxs-lookup"><span data-stu-id="de52a-140">Make a whole new endpoint for managing Active Directory</span></span>

7.  [<span data-ttu-id="de52a-141">多電腦部署和維護</span><span class="sxs-lookup"><span data-stu-id="de52a-141">Multi-machine Deployment and Maintenance</span></span>](multi-machine-deployment-and-maintenance.md)  
<span data-ttu-id="de52a-142">探索部署和編寫如何隨著規模調整而變更</span><span class="sxs-lookup"><span data-stu-id="de52a-142">Discover how deployment and authoring changes with scale</span></span>

8.  [<span data-ttu-id="de52a-143">JEA 上的報告</span><span class="sxs-lookup"><span data-stu-id="de52a-143">Reporting on JEA</span></span>](reporting-on-jea.md)  
<span data-ttu-id="de52a-144">探索如何對所有 JEA 動作和基礎結構進行稽核與報告</span><span class="sxs-lookup"><span data-stu-id="de52a-144">Discover how to audit and report on all JEA actions and infrastructure</span></span>

9.  <span data-ttu-id="de52a-145">附錄</span><span class="sxs-lookup"><span data-stu-id="de52a-145">Appendixes</span></span>
  - [<span data-ttu-id="de52a-146">本指南所使用的重要概念</span><span class="sxs-lookup"><span data-stu-id="de52a-146">Key Concepts Used Throughout This Guide</span></span>](key-concepts-used-throughout-this-guide.md)  
  -  [<span data-ttu-id="de52a-147">建立網域控制站</span><span class="sxs-lookup"><span data-stu-id="de52a-147">Creating a Domain Controller</span></span>](creating-a-domain-controller.md)  
  -  [<span data-ttu-id="de52a-148">列入封鎖清單</span><span class="sxs-lookup"><span data-stu-id="de52a-148">On Blacklisting</span></span>](on-blacklisting.md)  
  -  [<span data-ttu-id="de52a-149">限制命令時的考量</span><span class="sxs-lookup"><span data-stu-id="de52a-149">Considerations When Limiting Commands</span></span>](considerations-when-limiting-commands.md)  
  -  [<span data-ttu-id="de52a-150">常見的角色功能問題</span><span class="sxs-lookup"><span data-stu-id="de52a-150">Common Role Capability Pitfalls</span></span>](common-role-capability-pitfalls.md)

## <a name="start-authoring-your-own-jea-endpoints"></a><span data-ttu-id="de52a-151">開始撰寫您自己的 JEA 端點</span><span class="sxs-lookup"><span data-stu-id="de52a-151">Start authoring your own JEA endpoints</span></span>
<span data-ttu-id="de52a-152">撰寫 JEA 端點很容易，您只需要啟用 JEA 的系統和文字編輯器 (例如 PowerShell ISE)。</span><span class="sxs-lookup"><span data-stu-id="de52a-152">It's easy to author a JEA endpoint -- all you need is a JEA-enabled system and a text editor (like PowerShell ISE).</span></span>
<span data-ttu-id="de52a-153">其中一項實用的入門秘訣是使用 [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) 和 [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx)但不提供任何其他引數來建立基本架構檔案。</span><span class="sxs-lookup"><span data-stu-id="de52a-153">One helpful tip to get started is to create skeleton files using [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) and [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx) without any other arguments.</span></span>
<span data-ttu-id="de52a-154">這些基本架構檔案包含所有適用的設定欄位，以及說明每個欄位可能用途的實用註解。</span><span class="sxs-lookup"><span data-stu-id="de52a-154">These skeleton files contain all of the applicable configuration fields along with helpful comments to explain what each field can be used for.</span></span>

<span data-ttu-id="de52a-155">若要更輕鬆地撰寫 JEA 端點，請參閱 [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx)，其提供可用來撰寫工作階段設定檔和角色功能檔案的 GUI。</span><span class="sxs-lookup"><span data-stu-id="de52a-155">To make authoring JEA endpoints even easier, check out the [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) which provides a GUI with which you can author Session Configuration and Role Capability files.</span></span>
<span data-ttu-id="de52a-156">甚至支援根據 PowerShell 記錄檔產生角色功能，讓您一開始就有使用者為完成工作所經常執行的命令。</span><span class="sxs-lookup"><span data-stu-id="de52a-156">It even supports generating Role Capabilities based on PowerShell logs to start you off with the commands your users regularly run to get their jobs done.</span></span>

