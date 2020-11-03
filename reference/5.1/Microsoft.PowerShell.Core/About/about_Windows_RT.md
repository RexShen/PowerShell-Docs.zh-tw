---
description: 說明 Windows RT 8.1 上 Windows PowerShell 4.0 的限制。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_rt?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_RT
ms.openlocfilehash: 323f06a7a0d8253417510503c1011ac02c20179f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207504"
---
# <a name="about-windows-rt"></a><span data-ttu-id="af712-104">關於 Windows RT</span><span class="sxs-lookup"><span data-stu-id="af712-104">About Windows RT</span></span>

## <a name="short-description"></a><span data-ttu-id="af712-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="af712-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="af712-106">說明 Windows RT 8.1 上 Windows PowerShell 4.0 的限制。</span><span class="sxs-lookup"><span data-stu-id="af712-106">Explains limitations of  Windows PowerShell 4.0 on Windows RT 8.1.</span></span>

## <a name="long-description"></a><span data-ttu-id="af712-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="af712-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="af712-108">Windows RT 8.1 作業系統安裝在 (的電腦和裝置上，例如 Microsoft Surface 2，它是隨附于電腦) 的作業系統，其使用 Advanced RISC 機器 (ARM) 處理器。</span><span class="sxs-lookup"><span data-stu-id="af712-108">The Windows RT 8.1 operating system is installed on computers and devices (such as Microsoft Surface 2, on which it is the operating system that ships with the computer) that use Advanced RISC Machine (ARM) processors.</span></span>

<span data-ttu-id="af712-109">Windows RT 8.1 中包含 Windows PowerShell 4.0。</span><span class="sxs-lookup"><span data-stu-id="af712-109">Windows PowerShell 4.0 is included in Windows RT 8.1.</span></span> <span data-ttu-id="af712-110">所有的 Cmdlet、提供者和模組，以及針對 Windows PowerShell 2.0 和更新版本所設計的大部分腳本，都是在 Windows RT 8.1 上執行而不需要變更。</span><span class="sxs-lookup"><span data-stu-id="af712-110">All cmdlets, providers, and modules, and most scripts designed for Windows PowerShell 2.0 and later releases run on Windows RT 8.1 without changes.</span></span>

<span data-ttu-id="af712-111">因為 Windows RT 8.1 不包含所有 Windows 功能，某些 Windows PowerShell 功能的運作方式不同，或無法在 Windows RT 型裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="af712-111">Because Windows RT 8.1 does not include all Windows features, some Windows PowerShell features work differently or do not work on Windows RT-based devices.</span></span> <span data-ttu-id="af712-112">下列清單說明差異。</span><span class="sxs-lookup"><span data-stu-id="af712-112">The following list explains the differences.</span></span>

- <span data-ttu-id="af712-113">Windows PowerShell ISE 不包含在中，而且無法在 Windows RT 8.1 上執行。</span><span class="sxs-lookup"><span data-stu-id="af712-113">Windows PowerShell ISE is not included in and cannot run on Windows RT 8.1.</span></span>
  <span data-ttu-id="af712-114">Windows PowerShell ISE 需要 Windows Presentation Foundation，但 Windows RT 8.1 不包含此功能。</span><span class="sxs-lookup"><span data-stu-id="af712-114">Windows PowerShell ISE requires Windows Presentation Foundation, which is not included in Windows RT 8.1.</span></span>

- <span data-ttu-id="af712-115">Windows PowerShell 的遠端處理和 WinRM 服務預設為停用。</span><span class="sxs-lookup"><span data-stu-id="af712-115">Windows PowerShell remoting and the WinRM service are disabled by default.</span></span>
  <span data-ttu-id="af712-116">若要啟用遠端功能，請執行 Enable-PSRemoting Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="af712-116">To enable remoting, run the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="af712-117">此外，也請執行 Set-Service Cmdlet，將 WinRM 服務的啟動類型設定為 [自動]，或 [自動 (延遲啟動) ]。</span><span class="sxs-lookup"><span data-stu-id="af712-117">Also, run the Set-Service cmdlet to set the startup type of the WinRM service to Automatic, or Automatic (Delayed Start).</span></span>

  <span data-ttu-id="af712-118">遠端停用時，您可以使用 Windows PowerShell 遠端處理在其他電腦上執行命令，但其他電腦無法在 Windows RT 裝置上執行命令。</span><span class="sxs-lookup"><span data-stu-id="af712-118">While remoting is disabled, you can use Windows PowerShell remoting to run commands on other computers, but other computers cannot run commands on the Windows RT device.</span></span> <span data-ttu-id="af712-119">此外，隱含遠端處理-也就是內建至 Cmdlet 或腳本的遠端處理，並不會使用新增的參數明確要求</span><span class="sxs-lookup"><span data-stu-id="af712-119">Also, implicit remoting - that is, remoting that is built in to a cmdlet or script, and not explicitly requested with added parameters</span></span>
  - <span data-ttu-id="af712-120">在 Windows RT 8.1 上執行的 Windows PowerShell 中無法運作。</span><span class="sxs-lookup"><span data-stu-id="af712-120">does not work in Windows PowerShell running on Windows RT 8.1.</span></span>

- <span data-ttu-id="af712-121">Windows RT 8.1 不支援已加入網域的計算和 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="af712-121">Domain-joined computing and Kerberos authentication are not supported on Windows RT 8.1.</span></span> <span data-ttu-id="af712-122">您無法使用 Windows PowerShell 來新增或管理這些功能。</span><span class="sxs-lookup"><span data-stu-id="af712-122">You cannot use Windows PowerShell to add or manage these features.</span></span>

- <span data-ttu-id="af712-123">Windows RT 8.1 上的 Windows PowerShell 也不支援 Windows RT 8.1 上不支援的 Microsoft .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="af712-123">Microsoft .NET Framework classes that are not supported on Windows RT 8.1 are also not supported by Windows PowerShell on Windows RT 8.1.</span></span>

- <span data-ttu-id="af712-124">未在 Windows RT 8.1 上啟用交易。</span><span class="sxs-lookup"><span data-stu-id="af712-124">Transactions are not enabled on Windows RT 8.1.</span></span> <span data-ttu-id="af712-125">交易 Cmdlet （例如，UseTransaction）無法正常運作，例如啟動交易和交易參數。</span><span class="sxs-lookup"><span data-stu-id="af712-125">Transaction cmdlets, such as Start-Transaction, and transaction parameters, such as UseTransaction, do not work properly.</span></span>

- <span data-ttu-id="af712-126">Windows RT 8.1 裝置上的所有 Windows PowerShell 會話都會使用 ConstrainedLanguage 語言模式。</span><span class="sxs-lookup"><span data-stu-id="af712-126">All Windows PowerShell sessions on Windows RT 8.1 devices use the ConstrainedLanguage language mode.</span></span> <span data-ttu-id="af712-127">ConstrainedLanguage 語言模式是使用者模式的程式碼完整性 (UMCI) 。</span><span class="sxs-lookup"><span data-stu-id="af712-127">ConstrainedLanguage language mode is a companion to User Mode Code Integrity (UMCI).</span></span> <span data-ttu-id="af712-128">它允許所有的 Windows Cmdlet 和 Windows PowerShell 的語言專案，但會限制類型，以確保使用者無法使用 Windows PowerShell 來規避或違反 UMCI 防護。</span><span class="sxs-lookup"><span data-stu-id="af712-128">It permits all Windows cmdlets and Windows PowerShell language elements, but restricts types to ensure that users cannot use Windows PowerShell to circumvent or violate the UMCI protections.</span></span>

<span data-ttu-id="af712-129">如需 ConstrainedLanguage 語言模式的詳細資訊，請參閱 [about_Language_Modes](about_Language_Modes.md)。</span><span class="sxs-lookup"><span data-stu-id="af712-129">For more information about ConstrainedLanguage language mode, see [about_Language_Modes](about_Language_Modes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="af712-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af712-130">SEE ALSO</span></span>

[<span data-ttu-id="af712-131">about_Language_Modes</span><span class="sxs-lookup"><span data-stu-id="af712-131">about_Language_Modes</span></span>](about_Language_Modes.md)

[<span data-ttu-id="af712-132">about_Remote</span><span class="sxs-lookup"><span data-stu-id="af712-132">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="af712-133">about_Windows_PowerShell_ISE</span><span class="sxs-lookup"><span data-stu-id="af712-133">about_Windows_PowerShell_ISE</span></span>](about_Windows_PowerShell_ISE.md)
