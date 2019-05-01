---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 07ebcfd37cc3e1f38a9434ffa8d86f479b89ee0f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085213"
---
# <a name="windows-management-framework-wmf-50-rtm-release-notes-overview"></a><span data-ttu-id="f0b4d-102">Windows Management Framework (WMF) 5.0 RTM 版本資訊概觀</span><span class="sxs-lookup"><span data-stu-id="f0b4d-102">Windows Management Framework (WMF) 5.0 RTM Release Notes Overview</span></span>

<span data-ttu-id="f0b4d-103">**WMF 5.1 已取代 WMF 5.0。使用 WMF 5.0 的使用者必須升級至 WMF 5.1 才能獲得支援。請遵循 [WMF 5.1 的安裝指示](../5.1/install-configure.md)**</span><span class="sxs-lookup"><span data-stu-id="f0b4d-103">**WMF 5.0 is superseded by WMF 5.1. Users with WMF 5.0 must upgrade to WMF 5.1 to receive support. Please follow the [installation intructions of WMF 5.1](../5.1/install-configure.md)**</span></span>

<span data-ttu-id="f0b4d-104">Windows Management Framework (WMF) 5.0 RTM 延續 WMF 4.0 已更新的功能。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-104">Windows Management Framework (WMF) 5.0 RTM brings functionality that has been updated from WMF 4.0.</span></span> <span data-ttu-id="f0b4d-105">WMF 5.0 RTM 只能安裝在 **Windows Server 2012 R2**、**Windows Server 2012**、**Windows Server 2008 R2**、**Windows 8.1** 和 **Windows 7 SP1**，包含下列功能的更新版本或簡介：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-105">WMF 5.0 RTM is available for installation only on **Windows Server 2012 R2**, **Windows Server 2012**, **Windows Server 2008 R2**, **Windows 8.1**, and **Windows 7 SP1** and contains updated versions or introduction of the following features:</span></span>

- <span data-ttu-id="f0b4d-106">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f0b4d-106">Windows PowerShell</span></span>
- <span data-ttu-id="f0b4d-107">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="f0b4d-107">Just Enough Administration (JEA)</span></span>
- <span data-ttu-id="f0b4d-108">Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="f0b4d-108">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="f0b4d-109">Windows PowerShell 整合式指令碼環境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="f0b4d-109">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>
- <span data-ttu-id="f0b4d-110">Windows PowerShell Web 服務 (Management OData IIS 擴充功能)</span><span class="sxs-lookup"><span data-stu-id="f0b4d-110">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="f0b4d-111">Windows 遠端管理 (WinRM)</span><span class="sxs-lookup"><span data-stu-id="f0b4d-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="f0b4d-112">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="f0b4d-112">Windows Management Instrumentation (WMI)</span></span>

<span data-ttu-id="f0b4d-113">WMF 5.0 RTM 取代了 [WMF 5.0 Production Preview](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-113">WMF 5.0 RTM replaces the [WMF 5.0 Production Preview](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx).</span></span> <span data-ttu-id="f0b4d-114">您可以安裝 WMF 5.0 RTM 卻不用解除安裝 WMF 5.0 Production Preview，但必須先解除安裝所有其他舊版的 WMF 5.0 RTM Preview 再安裝 WMF 5.0 RTM。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-114">You can install WMF 5.0 RTM without uninstalling WMF 5.0 Production Preview, but you must uninstall all other older releases of WMF 5.0 previews before installing the WMF 5.0 RTM.</span></span>

<span data-ttu-id="f0b4d-115">*注意：* 如果執行的是 Windows 10，只要更新至 Windows 10 的 11 月更新 (版本 1511)，即可取得和 WMF 5.0 RTM 同樣的功能集。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-115">*Note:* If you are running Windows 10, you can get the same set of functionality available in WMF 5.0 RTM by updating to the November update of Windows 10 (Version 1511).</span></span> <span data-ttu-id="f0b4d-116">如尚未更新 Windows 10 系統，請選取 [開始] 按鈕，然後選取 [設定] > [更新與安全性] > [Windows Update] > 檢查更新。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-116">If you have not already updated your Windows 10 system, select the Start button, then select Settings > Update & security > Windows Update > Check for updates.</span></span>
