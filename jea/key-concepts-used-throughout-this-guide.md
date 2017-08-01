---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "本指南所使用的重要概念"
ms.technology: powershell
ms.openlocfilehash: 873ab19fdf43ec4ac41cc546aa94b64fbc607984
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-TW
---
# <a name="key-concepts-used-throughout-this-guide"></a><span data-ttu-id="13dc1-103">本指南所使用的重要概念</span><span class="sxs-lookup"><span data-stu-id="13dc1-103">Key Concepts Used Throughout This Guide</span></span>
<span data-ttu-id="13dc1-104">**JEA 到底是什麼？**</span><span class="sxs-lookup"><span data-stu-id="13dc1-104">**What exactly is JEA?**</span></span>

<span data-ttu-id="13dc1-105">JEA 是 PowerShell [限制端點](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx)的延伸模組，其新增了角色定義、虛擬帳戶及其他幾項增強功能，讓您更輕鬆地鎖定管理端點。</span><span class="sxs-lookup"><span data-stu-id="13dc1-105">JEA is an extension of PowerShell [constrained endpoints](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) that adds in role definitions, virtual accounts, and several other improvements to make it even easier to lock down your management endpoints.</span></span>
<span data-ttu-id="13dc1-106">JEA 端點是由 PowerShell 工作階段設定檔以及一或多個角色功能檔案所組成。</span><span class="sxs-lookup"><span data-stu-id="13dc1-106">A JEA endpoint consists of a PowerShell Session Configuration file and one or more Role Capability files.</span></span>

<span data-ttu-id="13dc1-107">**什麼是工作階段設定檔和角色功能檔案？**</span><span class="sxs-lookup"><span data-stu-id="13dc1-107">**What are Session Configuration and Role Capability files?**</span></span>

<span data-ttu-id="13dc1-108">PowerShell 工作階段設定檔 (.pssc) 定義*誰*可以連線到 PowerShell 端點，以及*如何*進行設定。</span><span class="sxs-lookup"><span data-stu-id="13dc1-108">PowerShell Session Configuration files (.pssc) define *who* can connect to a PowerShell endpoint and *how* it is configured.</span></span>
<span data-ttu-id="13dc1-109">您可以在此將使用者和安全性群組對應到特定管理角色，並設定虛擬帳戶和文字記錄原則等全域設定。</span><span class="sxs-lookup"><span data-stu-id="13dc1-109">This is where you would map users and security groups to specific management roles and configure global settings like virtual accounts and transcription policies.</span></span>
<span data-ttu-id="13dc1-110">工作階段設定檔是每部電腦專屬的檔案，可讓您視需要控制每部電腦的存取權。</span><span class="sxs-lookup"><span data-stu-id="13dc1-110">Session configuration files are specific to each machine, which allows you to control access on a per-machine basis if desired.</span></span>

<span data-ttu-id="13dc1-111">PowerShell 角色功能檔案 (.psrc) 定義屬於某個角色的使用者能夠在系統上執行*什麼*工作。</span><span class="sxs-lookup"><span data-stu-id="13dc1-111">PowerShell Role Capability files (.psrc) define *what* users belonging to a role are able to do on the system.</span></span>
<span data-ttu-id="13dc1-112">您可以在此限制使用者可在其 JEA 工作階段中使用的 Cmdlet、函式、提供者和外部程式。</span><span class="sxs-lookup"><span data-stu-id="13dc1-112">Here, you can restrict which cmdlets, functions, providers, and external programs a user may use in their JEA session.</span></span>
<span data-ttu-id="13dc1-113">角色功能檔案通常沒有特定的服務角色 (DNS 管理、初級技術支援、唯讀清查稽核等)，並屬於 PowerShell 模組，因此可讓您輕鬆地在環境中與其他人共用。</span><span class="sxs-lookup"><span data-stu-id="13dc1-113">Role Capability files are often generic for the role being served (DNS admin, level 1 helpdesk, read-only inventory auditing, etc.) and belong to PowerShell modules, making it easy to share them across your environment and with others.</span></span>

<span data-ttu-id="13dc1-114">**JEA 如何利用虛擬帳戶？**</span><span class="sxs-lookup"><span data-stu-id="13dc1-114">**How does JEA leverage virtual accounts?**</span></span>

<span data-ttu-id="13dc1-115">在 PowerShell 工作階段設定檔中，您可以將 JEA 工作階段設定為使用虛擬「執行身分」帳戶。</span><span class="sxs-lookup"><span data-stu-id="13dc1-115">In the PowerShell Session Configuration file, you can configure JEA sessions to use virtual "run as" accounts.</span></span>
<span data-ttu-id="13dc1-116">虛擬帳戶是專為特定工作階段中的特定連線使用者所設計的一次性特殊權限帳戶，使用者的命令會在該內容中執行。</span><span class="sxs-lookup"><span data-stu-id="13dc1-116">Virtual accounts are one-time privileged accounts spun up for the specific connecting user in that specific session under which context the user's commands are executed.</span></span>
<span data-ttu-id="13dc1-117">虛擬帳戶預設屬於本機 "Administrators" 安全性群組，但可以選擇性地設定為只屬於您指定的安全性群組。</span><span class="sxs-lookup"><span data-stu-id="13dc1-117">Virtual accounts belong to the local "Administrators" security group by default, but can optionally be configured to only belong to security groups you specify.</span></span>

<span data-ttu-id="13dc1-118">**PowerShell 遠端**：PowerShell 遠端可讓您對遠端電腦執行 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="13dc1-118">**PowerShell Remoting**: PowerShell remoting allows you to run PowerShell commands against remote machines.</span></span>
<span data-ttu-id="13dc1-119">您可以對一或多部電腦執行，並使用暫時或持續連線。</span><span class="sxs-lookup"><span data-stu-id="13dc1-119">You can operate against one or many computers, and use either temporary or persistent connections.</span></span>
<span data-ttu-id="13dc1-120">在此示範中，您會使用互動式工作階段從遠端登入本機電腦。</span><span class="sxs-lookup"><span data-stu-id="13dc1-120">In this demo, you remoted into your local machine with an interactive session.</span></span>
<span data-ttu-id="13dc1-121">JEA 會限制可透過 PowerShell 遠端使用的功能。</span><span class="sxs-lookup"><span data-stu-id="13dc1-121">JEA restricts the functionality available through PowerShell remoting.</span></span>
<span data-ttu-id="13dc1-122">如需 PowerShell 遠端的詳細資訊，請執行 `Get-Help about_Remote`。</span><span class="sxs-lookup"><span data-stu-id="13dc1-122">For more information about PowerShell remoting, run `Get-Help about_Remote`.</span></span>

<span data-ttu-id="13dc1-123">**"RunAs" 使用者**︰使用 JEA 時，非系統管理員會以特殊權限「虛擬帳戶」身分執行。</span><span class="sxs-lookup"><span data-stu-id="13dc1-123">**"RunAs" User**: When using JEA, a non-administrator "runs as" a privileged "Virtual Account."</span></span>
<span data-ttu-id="13dc1-124">虛擬帳戶只會持續到遠端工作階段期間結束為止。</span><span class="sxs-lookup"><span data-stu-id="13dc1-124">The Virtual Account only lasts the duration of the remote session.</span></span>
<span data-ttu-id="13dc1-125">也就是說，它會在使用者連線到端點時建立，並在使用者結束工作階段時摧毀。</span><span class="sxs-lookup"><span data-stu-id="13dc1-125">That is to say, it is created when a user connects to the endpoint, and destroyed when the user ends the session.</span></span>
<span data-ttu-id="13dc1-126">根據預設，虛擬帳戶是本機 Administrator 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="13dc1-126">By default, the Virtual Account is a member of the local Administrators group.</span></span>
<span data-ttu-id="13dc1-127">在網域控制站上，它是 Domain Admins 的成員。</span><span class="sxs-lookup"><span data-stu-id="13dc1-127">On a domain controller, it is a member of Domain Admins.</span></span>
<span data-ttu-id="13dc1-128">虛擬帳戶是帳戶建立所在電腦上的本機帳戶，沒有該電腦以外的權限。</span><span class="sxs-lookup"><span data-stu-id="13dc1-128">Virtual Accounts are local to the machine on which they are created, and do not have permissions outside of that machine.</span></span>
<span data-ttu-id="13dc1-129">這表示它們未登錄在 Active Directory 中 (未指派 RID)。</span><span class="sxs-lookup"><span data-stu-id="13dc1-129">This means that they are not registered in Active Directory (no RID is assigned).</span></span>
<span data-ttu-id="13dc1-130">此外，如果允許的命令/指令碼嘗試存取本機電腦以外的資源，它會使用電腦身分識別 (而不是虛擬帳戶身分識別) 來存取這些資源。</span><span class="sxs-lookup"><span data-stu-id="13dc1-130">Additionally, if an allowed command/script tries to access resources outside of the local machine, it will be accessing those resources under the machine's identity, not the Virtual Account identity.</span></span>

<span data-ttu-id="13dc1-131">**「已連線」的使用者**︰連線到 JEA 端點且已指派角色的非系統管理員使用者。</span><span class="sxs-lookup"><span data-stu-id="13dc1-131">**"Connected" User**: The non-administrator user who connects to the JEA endpoint and to whom roles are assigned.</span></span>
<span data-ttu-id="13dc1-132">這位使用者執行的任何命令，都會在 RunAs 使用者或虛擬帳戶的內容下執行。</span><span class="sxs-lookup"><span data-stu-id="13dc1-132">Any commands this user runs are run under the context of the RunAs User or virtual account.</span></span>

