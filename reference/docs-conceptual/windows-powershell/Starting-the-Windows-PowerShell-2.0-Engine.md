---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用 Windows PowerShell 2.0 引擎
description: 只有在現有指令碼或主機程式無法執行時才會使用 Windows PowerShell 2.0 引擎，因為針對 Windows PowerShell 2.0 撰寫且使用 CLR 2.0 編譯的主機程式無法在未經修改的情況下執行。
ms.openlocfilehash: 214b87b7314f31974801bb07f98ddea3b68008f0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664010"
---
# <a name="using-the-windows-powershell-20-engine"></a><span data-ttu-id="da81d-104">使用 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="da81d-104">Using the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="da81d-105">Windows PowerShell 已設計為可回溯相容先前的版本。</span><span class="sxs-lookup"><span data-stu-id="da81d-105">Windows PowerShell is designed to be backward compatible with previous versions.</span></span> <span data-ttu-id="da81d-106">針對 Windows PowerShell 2.0 撰寫的 Cmdlet、提供者、嵌入式管理單元、模組及指令碼，在新版 Windows PowerShell 中仍以同樣方式執行。</span><span class="sxs-lookup"><span data-stu-id="da81d-106">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 run unchanged in newer versions Windows PowerShell.</span></span> <span data-ttu-id="da81d-107">不過，Microsoft .NET Framework 4 變更了執行時間啟用原則。</span><span class="sxs-lookup"><span data-stu-id="da81d-107">However, Microsoft .NET Framework 4 changed the runtime activation policy.</span></span>
<span data-ttu-id="da81d-108">針對 Windows PowerShell 2.0 撰寫並使用 Common Language Runtime (CLR) 2.0 編譯的 Windows PowerShell 主機程式，需要在使用 CLR 4.0 (或更高版本) 編譯的新版 Windows PowerShell 中修改才能執行。</span><span class="sxs-lookup"><span data-stu-id="da81d-108">Windows PowerShell host programs written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in new versions Windows PowerShell that are compiled with CLR 4.0 (or higher).</span></span>

<span data-ttu-id="da81d-109">Windows PowerShell 2.0 引擎只有在現有指令碼或主機程式無法執行時才會使用 ，因為其與 Windows PowerShell 5.1 不相容。</span><span class="sxs-lookup"><span data-stu-id="da81d-109">The Windows PowerShell 2.0 Engine is intended to be used only when an existing script or host program cannot run because it is incompatible with Windows PowerShell 5.1.</span></span> <span data-ttu-id="da81d-110">這種情況的範例包括舊版的 Exchange 或 SQL Server 模組。</span><span class="sxs-lookup"><span data-stu-id="da81d-110">Examples of this include older versions of Exchange or SQL Server modules.</span></span> <span data-ttu-id="da81d-111">這種情況應該很少見。</span><span class="sxs-lookup"><span data-stu-id="da81d-111">Such cases are expected to be rare.</span></span>

<span data-ttu-id="da81d-112">許多需要 Windows PowerShell 2.0 引擎的程式都會自動啟動它。</span><span class="sxs-lookup"><span data-stu-id="da81d-112">Many programs that require the Windows PowerShell 2.0 Engine start it automatically.</span></span> <span data-ttu-id="da81d-113">這些指示是針對需要手動啟動引擎的罕見情況。</span><span class="sxs-lookup"><span data-stu-id="da81d-113">These instructions are included for the rare situations in which you need to start the engine manually.</span></span>

## <a name="deprecation-and-security-concerns"></a><span data-ttu-id="da81d-114">淘汰和安全性考量</span><span class="sxs-lookup"><span data-stu-id="da81d-114">Deprecation and security concerns</span></span>

<span data-ttu-id="da81d-115">Windows PowerShell 2.0 已於 2017 年 8 月淘汰。</span><span class="sxs-lookup"><span data-stu-id="da81d-115">Windows PowerShell 2.0 was deprecated in August, 2017.</span></span> <span data-ttu-id="da81d-116">如需詳細資訊，請參閱 PowerShell 部落格上的[公告][]。</span><span class="sxs-lookup"><span data-stu-id="da81d-116">For more information, see the [announcement][] on the PowerShell blog.</span></span>

<span data-ttu-id="da81d-117">Windows PowerShell 2.0 缺少第 3、4 和 5 版中新增的大量強化與安全性功能。</span><span class="sxs-lookup"><span data-stu-id="da81d-117">Windows PowerShell 2.0 is missing a significant amount of the hardening and security features added in versions 3, 4, and 5.</span></span> <span data-ttu-id="da81d-118">強烈建議，如果可以的話，請使用者避免使用。</span><span class="sxs-lookup"><span data-stu-id="da81d-118">We highly, highly recommend that users not use it if they can help it.</span></span> <span data-ttu-id="da81d-119">如需詳細資訊，請參閱 [Shell 與指令碼語言安全性的比較][]和 [PowerShell ♥ Blue Team][blueteam]。</span><span class="sxs-lookup"><span data-stu-id="da81d-119">For more information, see [A Comparison of Shell and Scripting Language Security][] and [PowerShell ♥ the Blue Team][blueteam].</span></span>

## <a name="installing-and-enabling-required-programs"></a><span data-ttu-id="da81d-120">安裝和啟用必要的程式</span><span class="sxs-lookup"><span data-stu-id="da81d-120">Installing and Enabling Required Programs</span></span>

<span data-ttu-id="da81d-121">啟動 Windows PowerShell 2.0 引擎之前，請啟用 Windows PowerShell 2.0 引擎和 Microsoft .NET Framework 3.5 (含 Service Pack 1)。</span><span class="sxs-lookup"><span data-stu-id="da81d-121">Before starting the Windows PowerShell 2.0 Engine, enable the Windows PowerShell 2.0 Engine and Microsoft .NET Framework 3.5 with Service Pack 1.</span></span> <span data-ttu-id="da81d-122">如需相關指示，請參閱[安裝 Windows PowerShell][]。</span><span class="sxs-lookup"><span data-stu-id="da81d-122">For instructions, see [Installing Windows PowerShell][].</span></span>

<span data-ttu-id="da81d-123">已安裝 Windows Management Framework 3.0 或更高版本的系統都具有所有必要元件。</span><span class="sxs-lookup"><span data-stu-id="da81d-123">Systems on which Windows Management Framework 3.0 or higher is installed have all of the required components.</span></span> <span data-ttu-id="da81d-124">不需要進一步設定。</span><span class="sxs-lookup"><span data-stu-id="da81d-124">No further configuration is necessary.</span></span> <span data-ttu-id="da81d-125">如需安裝 Windows Management Framework 的相關資訊，請參閱[安裝與設定 WMF][]。</span><span class="sxs-lookup"><span data-stu-id="da81d-125">For information about installing Windows Management Framework, see [Install and configure WMF][].</span></span>

## <a name="how-to-start-the-windows-powershell-20-engine"></a><span data-ttu-id="da81d-126">如何啟動 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="da81d-126">How to start the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="da81d-127">當您啟動 Windows PowerShell 時，預設會啟動最新版本。</span><span class="sxs-lookup"><span data-stu-id="da81d-127">When you start Windows PowerShell the newest version starts by default.</span></span> <span data-ttu-id="da81d-128">若要啟動含 Windows PowerShell 2.0 引擎的 Windows PowerShell，請使用 `PowerShell.exe` 的 Version 參數。</span><span class="sxs-lookup"><span data-stu-id="da81d-128">To start Windows PowerShell with the Windows PowerShell 2.0 Engine, use the Version parameter of `PowerShell.exe`.</span></span> <span data-ttu-id="da81d-129">您可以在任何命令提示字元 (包括 Windows PowerShell 和 Cmd.exe) 執行命令。</span><span class="sxs-lookup"><span data-stu-id="da81d-129">You can run the command at any command prompt, including Windows PowerShell and Cmd.exe.</span></span>

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a><span data-ttu-id="da81d-130">如何啟動含 Windows PowerShell 2.0 引擎的遠端工作階段</span><span class="sxs-lookup"><span data-stu-id="da81d-130">How to start a remote session with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="da81d-131">若要在遠端工作階段中執行 Windows PowerShell 2.0 引擎，請在載入 Windows PowerShell 2.0 引擎的遠端電腦上建立工作階段設定 (又稱 _端點_ )。</span><span class="sxs-lookup"><span data-stu-id="da81d-131">To run the Windows PowerShell 2.0 Engine in a remote session, create a session configuration (also known as an _endpoint_ ) on the remote computer that loads the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="da81d-132">工作階段組態會儲存於遠端電腦上，而且任何授權使用者皆可用來建立使用 Windows PowerShell 2.0 引擎的工作階段。</span><span class="sxs-lookup"><span data-stu-id="da81d-132">The session configuration is saved on the remote computer and can be used by any authorized user to create sessions that use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="da81d-133">這是通常由系統管理員所執行的進階工作。</span><span class="sxs-lookup"><span data-stu-id="da81d-133">This is an advanced task that is typically performed by a system administrator.</span></span>

<span data-ttu-id="da81d-134">下列程序使用 [Register-PSSessionConfiguration][] Cmdlet 的 **PSVersion** 參數，來建立使用 Windows PowerShell 2.0 引擎的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="da81d-134">The following procedure uses the **PSVersion** parameter of the [Register-PSSessionConfiguration][] cmdlet to create a session configuration that uses the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="da81d-135">您也可以使用 [New-PSSessionConfigurationFile][] Cmdlet 的 **PowerShellVersion** 參數來建立可載入 Windows PowerShell 2.0 引擎之工作階段的工作階段設定檔，以及使用 [Set-PSSessionConfiguration][] 參數的 **PSVersion** 參數來將工作階段設定變更為使用 Windows PowerShell 2.0 引擎。</span><span class="sxs-lookup"><span data-stu-id="da81d-135">You can also use the **PowerShellVersion** parameter of the [New-PSSessionConfigurationFile][] cmdlet to create a session configuration file for a session that loads the Windows PowerShell 2.0 Engine and you can use the **PSVersion** parameter of the [Set-PSSessionConfiguration][] parameter to change a session configuration to use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="da81d-136">如需有關工作階段設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files][]。</span><span class="sxs-lookup"><span data-stu-id="da81d-136">For more information about session configuration files, see [about_Session_Configuration_Files][].</span></span>
<span data-ttu-id="da81d-137">如需有關設定和安全性等工作階段設定的詳細資訊，請參閱 [about_Session_Configurations][]。</span><span class="sxs-lookup"><span data-stu-id="da81d-137">For information about session configurations, including setup and security, see [about_Session_Configurations][].</span></span>

### <a name="to-start-a-remote-windows-powershell-20-session"></a><span data-ttu-id="da81d-138">啟動遠端 Windows PowerShell 2.0 工作階段</span><span class="sxs-lookup"><span data-stu-id="da81d-138">To start a remote Windows PowerShell 2.0 session</span></span>

1. <span data-ttu-id="da81d-139">若要建立需要 Windows PowerShell 2.0 引擎的工作階段設定，請使用 `Register-PSSessionConfiguration` cmdlet 的 **PSVersion** 參數 (值為 `2.0`)。</span><span class="sxs-lookup"><span data-stu-id="da81d-139">To create a session configuration that requires the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the `Register-PSSessionConfiguration` cmdlet with a value of `2.0`.</span></span>
   <span data-ttu-id="da81d-140">在「伺服器端」或連線接收端的電腦上，執行此命令。</span><span class="sxs-lookup"><span data-stu-id="da81d-140">Run this command on the computer at the "server side" or receiving end of the connection.</span></span>

   <span data-ttu-id="da81d-141">下列範例命令會在 Server01 電腦上建立 PS2 工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="da81d-141">The following sample command creates the PS2 session configuration on the Server01 computer.</span></span> <span data-ttu-id="da81d-142">若要執行此命令，請使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="da81d-142">To run this command, start Windows PowerShell with the **Run as administrator** option.</span></span>

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

1. <span data-ttu-id="da81d-143">若要在使用 PS2 工作階段設定的 Server01 電腦上建立工作階段，請使用建立遠端工作階段之 Cmdlet (例如 \`New-PSSession cmdlet) 的 **ConfigurationName** 參數。</span><span class="sxs-lookup"><span data-stu-id="da81d-143">To create a session on the Server01 computer that uses the PS2 session configuration, use the **ConfigurationName** parameter of cmdlets that create a remote session, such as the \`New-PSSession cmdlet.</span></span>

   <span data-ttu-id="da81d-144">當使用工作階段設定的工作階段啟動時，會將 Windows PowerShell 2.0 引擎自動載入工作階段。</span><span class="sxs-lookup"><span data-stu-id="da81d-144">When a session that uses the session configuration starts, the Windows PowerShell 2.0 Engine is automatically loaded into the session.</span></span>

   <span data-ttu-id="da81d-145">下列命令會在 Server01 電腦上啟動使用 PS2 工作階段設定的工作階段。</span><span class="sxs-lookup"><span data-stu-id="da81d-145">The following command starts a session on the Server01 computer that uses the PS2 session configuration.</span></span> <span data-ttu-id="da81d-146">命令會將工作階段儲存於 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="da81d-146">The command saves the session in the `$s` variable.</span></span>

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a><span data-ttu-id="da81d-147">如何使用 Windows PowerShell 2.0 引擎啟動背景工作</span><span class="sxs-lookup"><span data-stu-id="da81d-147">How to start a background job with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="da81d-148">若要使用 Windows PowerShell 2.0 引擎啟動背景工作，請使用 [Start-Job][] Cmdlet 的 **PSVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="da81d-148">To start a background job with the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the [Start-Job][] cmdlet.</span></span>

<span data-ttu-id="da81d-149">下列命令會使用 Windows PowerShell 2.0 引擎啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="da81d-149">The following command starts a background job with the Windows PowerShell 2.0 Engine</span></span>

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

<span data-ttu-id="da81d-150">如需背景工作的詳細資訊，請參閱 [about_Jobs][]。</span><span class="sxs-lookup"><span data-stu-id="da81d-150">For more information about background jobs, see [about_Jobs][].</span></span>

<!-- link references -->
[公告]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[announcement]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[Shell 與指令碼語言安全性的比較]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[A Comparison of Shell and Scripting Language Security]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[blueteam]: https://devblogs.microsoft.com/powershell/powershell-the-blue-team/
[安裝 Windows PowerShell]: install/Installing-Windows-PowerShell.md
[Installing Windows PowerShell]: install/Installing-Windows-PowerShell.md
[安裝與設定 WMF]: wmf/setup/install-configure.md
[Install and configure WMF]: wmf/setup/install-configure.md
[Register-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration
[New-PSSessionConfigurationFile]: /powershell/module/Microsoft.PowerShell.Core/New-PSSessionConfigurationFile
[Set-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration
[about_Session_Configuration_Files]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configuration_Files
[about_Session_Configurations]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configurations
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[about_Jobs]: /powershell/module/microsoft.powershell.core/about/about_jobs
