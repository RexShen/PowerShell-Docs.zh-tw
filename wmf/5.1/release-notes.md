---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
title: "WMF 5.1 版本資訊"
ms.openlocfilehash: fa3d9a3563ecf1bfc76d82b027641d19c9a4ff4e
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="a0213-103">Windows Management Framework (WMF) 5.1 版本資訊</span><span class="sxs-lookup"><span data-stu-id="a0213-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span> #

<span data-ttu-id="a0213-104">WMF 5.1 包含已搭配 Windows Server 2016 發行的 PowerShell、WMI、WinRM，以及軟體清查記錄 (SIL) 元件。</span><span class="sxs-lookup"><span data-stu-id="a0213-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="a0213-105">WMF 5.1 可以在 Windows 7、Windows 8.1、Windows Server 2008 R2、2012 及 2012 R2 上安裝，並提供許多對 WMF 5.0 RTM 的改善，包括︰</span><span class="sxs-lookup"><span data-stu-id="a0213-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="a0213-106">新的 Cmdlet︰本機使用者和群組；Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="a0213-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="a0213-107">PowerShellGet 改善功能包括強制執行已簽署的模組，以及安裝 JEA 模組</span><span class="sxs-lookup"><span data-stu-id="a0213-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="a0213-108">PackageManagement 新增對容器、CBS 安裝、以執行檔為基礎的安裝、封包封裝的支援</span><span class="sxs-lookup"><span data-stu-id="a0213-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="a0213-109">DSC 和 PowerShell 類別的偵錯改善</span><span class="sxs-lookup"><span data-stu-id="a0213-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="a0213-110">安全性增強功能包括強制執行來自提取伺服器的目錄簽署模組，以及在使用 PowerShellGet Cmdlet 時加以強制執行</span><span class="sxs-lookup"><span data-stu-id="a0213-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="a0213-111">回應數個使用者要求和問題</span><span class="sxs-lookup"><span data-stu-id="a0213-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="a0213-112">**重要事項：**</span><span class="sxs-lookup"><span data-stu-id="a0213-112">**Important notes:**</span></span>

- <span data-ttu-id="a0213-113">**WMF 5.1 需要 .NET Framework 4.5.2** (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="a0213-113">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="a0213-114">雖然安裝會成功，但若未安裝 .NET 4.5.2 (或更新版本)，主要功能將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a0213-114">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span> <span data-ttu-id="a0213-115">您可在[安裝和設定 WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) 主題中取得指示。</span><span class="sxs-lookup"><span data-stu-id="a0213-115">Instructions are available in the [Install and Configure WMF 5.1 ](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="a0213-116">安裝 WMF 5.1 RTM 之前，必須先解除安裝 WMF 5.1 Preview。</span><span class="sxs-lookup"><span data-stu-id="a0213-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="a0213-117">WMF 5.1 可直接透過 WMF 5.0 或 WMF 4.0 安裝。</span><span class="sxs-lookup"><span data-stu-id="a0213-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="a0213-118">在 Windows 7 和 Windows Server 2008 R2 上安裝 WMF 5.1 之前，__不需要__先安裝 WMF 4.0。</span><span class="sxs-lookup"><span data-stu-id="a0213-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="a0213-119">WMF 5.1 Preview 版本有問題，並且已解決。</span><span class="sxs-lookup"><span data-stu-id="a0213-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>  


