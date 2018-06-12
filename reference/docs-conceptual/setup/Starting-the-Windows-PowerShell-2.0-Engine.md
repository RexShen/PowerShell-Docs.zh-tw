---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 啟動 Windows PowerShell 2.0 引擎
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
ms.openlocfilehash: 618745ff4865dd046acf46487e87c3ca0e324f95
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482959"
---
# <a name="starting-the-windows-powershell-20-engine"></a><span data-ttu-id="de538-103">啟動 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="de538-103">Starting the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="de538-104">本節說明如何在 Windows 8.1、Windows Server 2012 R2、Windows 8 及 Windows Server 2012 (其中包括 Windows PowerShell 2.0 引擎) 上啟動 Windows PowerShell 2.0 引擎，以及在安裝 Windows PowerShell 2.0、Windows PowerShell 3.0 及 Windows PowerShell 4.0 的其他系統上啟動此引擎。</span><span class="sxs-lookup"><span data-stu-id="de538-104">This section explains how to start the Windows PowerShell 2.0 Engine on Windows 8.1, Windows Server 2012 R2, Windows 8, and Windows Server 2012, which include the Windows PowerShell 2.0 Engine, and on other systems on which Windows PowerShell 2.0, Windows PowerShell 3.0, and Windows PowerShell 4.0 are installed.</span></span>

<span data-ttu-id="de538-105">Windows PowerShell 4.0 和 Windows PowerShell 3.0 已設計為可回溯相容至 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="de538-105">Windows PowerShell 4.0 and Windows PowerShell 3.0 are designed to be backwards compatible with Windows PowerShell 2.0.</span></span> <span data-ttu-id="de538-106">針對 Windows PowerShell 2.0 撰寫的 Cmdlet、提供者、嵌入式管理單元、模組及指令碼，在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中仍以同樣方式執行。</span><span class="sxs-lookup"><span data-stu-id="de538-106">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 run unchanged in Windows PowerShell 4.0 and Windows PowerShell 3.0.</span></span> <span data-ttu-id="de538-107">不過，因為 Microsoft .NET Framework 4 中執行階段啟用原則的變更，所以在 Windows PowerShell 3.0 或 Windows PowerShell 4.0 (使用 CLR 4.0 編譯) 中，必須修改才能執行針對 Windows PowerShell 2.0 所撰寫並使用通用語言執行平台 (CLR) 2.0 編譯的 Windows PowerShell 主機程式。</span><span class="sxs-lookup"><span data-stu-id="de538-107">However, due to a change in the runtime activation policy in Microsoft .NET Framework 4, Windows PowerShell host programs that were written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in Windows PowerShell 3.0 or Windows PowerShell 4.0, which are compiled with CLR 4.0.</span></span> <span data-ttu-id="de538-108">只有在現有指令碼或主機程式無法執行時才會使用 Windows PowerShell 2.0 引擎，因為它與 Windows PowerShell 4.0、Windows PowerShell 3.0 或 Microsoft .NET Framework 4 不相容。</span><span class="sxs-lookup"><span data-stu-id="de538-108">The Windows PowerShell 2.0 Engine is intended to be used only when an existing script or host program cannot run because it is incompatible with Windows PowerShell 4.0, Windows PowerShell 3.0, or Microsoft .NET Framework 4.</span></span> <span data-ttu-id="de538-109">這種情況應該很少見。</span><span class="sxs-lookup"><span data-stu-id="de538-109">Such cases are expected to be rare.</span></span>

<span data-ttu-id="de538-110">許多需要 Windows PowerShell 2.0 引擎的程式都會自動啟動它。</span><span class="sxs-lookup"><span data-stu-id="de538-110">Many programs that require the Windows PowerShell 2.0 Engine start it automatically.</span></span> <span data-ttu-id="de538-111">這些指示是針對需要手動啟動引擎的罕見情況。</span><span class="sxs-lookup"><span data-stu-id="de538-111">These instructions are included for the rare situations in which you need to start the engine manually.</span></span>

## <a name="installing-and-enabling-required-programs"></a><span data-ttu-id="de538-112">安裝和啟用必要的程式</span><span class="sxs-lookup"><span data-stu-id="de538-112">Installing and Enabling Required Programs</span></span>

<span data-ttu-id="de538-113">啟動 Windows PowerShell 2.0 引擎之前，請啟用 Windows PowerShell 2.0 引擎和 Microsoft .NET Framework 3.5 (含 Service Pack 1)。</span><span class="sxs-lookup"><span data-stu-id="de538-113">Before starting the Windows PowerShell 2.0 Engine, enable the Windows PowerShell 2.0 Engine and Microsoft .NET Framework 3.5 with Service Pack 1.</span></span> <span data-ttu-id="de538-114">如需相關指示，請參閱[安裝 Windows PowerShell](Installing-Windows-PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="de538-114">For instructions, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="de538-115">已安裝 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) 或 Windows Management Framework 3.0 的系統都具有所有必要元件。</span><span class="sxs-lookup"><span data-stu-id="de538-115">Systems on which [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) or Windows Management Framework 3.0 are installed have all of the required components.</span></span> <span data-ttu-id="de538-116">不需要進一步設定。</span><span class="sxs-lookup"><span data-stu-id="de538-116">No further configuration is necessary.</span></span> <span data-ttu-id="de538-117">如需安裝 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) 或 Windows Management Framework 3.0 的相關資訊，請參閱[安裝 Windows PowerShell](Installing-Windows-PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="de538-117">For information about installing [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) or Windows Management Framework 3.0, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-the-windows-powershell-20-engine"></a><span data-ttu-id="de538-118">如何啟動 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="de538-118">How to start the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="de538-119">當您啟動 Windows PowerShell 時，預設會啟動最新版本。</span><span class="sxs-lookup"><span data-stu-id="de538-119">When you start Windows PowerShell the newest version starts by default.</span></span> <span data-ttu-id="de538-120">若要啟動含 Windows PowerShell 2.0 引擎的 Windows PowerShell，請使用 PowerShell.exe 的 Version 參數。</span><span class="sxs-lookup"><span data-stu-id="de538-120">To start Windows PowerShell with the Windows PowerShell 2.0 Engine, use the Version parameter of PowerShell.exe.</span></span> <span data-ttu-id="de538-121">您可以在任何命令提示字元 (包括 Windows PowerShell 和 Cmd.exe) 執行命令。</span><span class="sxs-lookup"><span data-stu-id="de538-121">You can run the command at any command prompt, including Windows PowerShell and Cmd.exe.</span></span>

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a><span data-ttu-id="de538-122">如何啟動含 Windows PowerShell 2.0 引擎的遠端工作階段</span><span class="sxs-lookup"><span data-stu-id="de538-122">How to start a remote session with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="de538-123">若要在遠端工作階段中執行 Windows PowerShell 2.0 引擎，請在載入 Windows PowerShell 2.0 引擎的遠端電腦上建立工作階段設定 (也稱為「端點」)。</span><span class="sxs-lookup"><span data-stu-id="de538-123">To run the Windows PowerShell 2.0 Engine in a remote session, create a session configuration (also known as an "endpoint") on the remote computer that loads the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="de538-124">工作階段組態會儲存於遠端電腦上，而且任何授權使用者皆可用來建立使用 Windows PowerShell 2.0 引擎的工作階段。</span><span class="sxs-lookup"><span data-stu-id="de538-124">The session configuration is saved on the remote computer and can be used by any authorized user to create sessions that use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="de538-125">這是通常由系統管理員所執行的進階工作。</span><span class="sxs-lookup"><span data-stu-id="de538-125">This is an advanced task that is typically performed by a system administrator.</span></span>

<span data-ttu-id="de538-126">下列程序使用 [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) Cmdlet 的 **PSVersion** 參數，來建立使用 Windows PowerShell 2.0 引擎的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="de538-126">The following procedure uses the **PSVersion** parameter of the [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet to create a session configuration that uses the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="de538-127">您也可以使用 [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) Cmdlet 的 **PowerShellVersion** 參數來建立可載入 Windows PowerShell 2.0 引擎之工作階段的工作階段設定檔，以及使用 [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) 參數的 **PSVersion** 參數來將工作階段設定變更為使用 Windows PowerShell 2.0 引擎。</span><span class="sxs-lookup"><span data-stu-id="de538-127">You can also use the **PowerShellVersion** parameter of the [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet to create a session configuration file for a session that loads the Windows PowerShell 2.0 Engine and you can use the **PSVersion** parameter of the [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) parameter to change a session configuration to use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="de538-128">如需工作階段組態檔的詳細資訊，請參閱 [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8)。如需工作階段組態 (包括設定和安全性) 的資訊，請參閱 [about_Session_Configurations [v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab)。</span><span class="sxs-lookup"><span data-stu-id="de538-128">For more information about session configuration files, see [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8).For information about session configurations, including setup and security, see [about_Session_Configurations[v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab).</span></span>

#### <a name="to-start-a-remote-windows-powershell-20-session"></a><span data-ttu-id="de538-129">啟動遠端 Windows PowerShell 2.0 工作階段</span><span class="sxs-lookup"><span data-stu-id="de538-129">To start a remote Windows PowerShell 2.0 session</span></span>

1. <span data-ttu-id="de538-130">若要建立需要 Windows PowerShell 2.0 引擎的工作階段設定，請使用 [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) Cmdlet 的 **PSVersion** 參數 (值為 "2.0")。</span><span class="sxs-lookup"><span data-stu-id="de538-130">To create a session configuration that requires the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet with a value of "2.0".</span></span> <span data-ttu-id="de538-131">在「伺服器端」或連線接收端的電腦上，執行此命令。</span><span class="sxs-lookup"><span data-stu-id="de538-131">Run this command on the computer at the "server side" or receiving end of the connection.</span></span>

   <span data-ttu-id="de538-132">下列範例命令會在 Server01 電腦上建立 PS2 工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="de538-132">The following sample command creates the PS2 session configuration on the Server01 computer.</span></span> <span data-ttu-id="de538-133">若要執行此命令，使用 [以系統管理員身分執行] 選項來啟動 Windows PowerShell 4.0 或 Windows PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="de538-133">To run this command, start Windows PowerShell 4.0 or Windows PowerShell 3.0 with the **Run as administrator** option.</span></span>

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. <span data-ttu-id="de538-134">若要在 Server01 電腦上建立使用 PS2 工作階段設定的工作階段，請使用建立遠端工作階段之 Cmdlet 的 **ConfigurationName** 參數 (例如 [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) Cmdlet)。</span><span class="sxs-lookup"><span data-stu-id="de538-134">To create a session on the Server01 computer that uses the PS2 session configuration, use the **ConfigurationName** parameter of cmdlets that create a remote session, such as the [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) cmdlet.</span></span>

   <span data-ttu-id="de538-135">當使用工作階段設定的工作階段啟動時，會將 Windows PowerShell 2.0 引擎自動載入工作階段。</span><span class="sxs-lookup"><span data-stu-id="de538-135">When a session that uses the session configuration starts, the Windows PowerShell 2.0 Engine is automatically loaded into the session.</span></span>

   <span data-ttu-id="de538-136">下列命令會在 Server01 電腦上啟動使用 PS2 工作階段設定的工作階段。</span><span class="sxs-lookup"><span data-stu-id="de538-136">The following command starts a session on the Server01 computer that uses the PS2 session configuration.</span></span> <span data-ttu-id="de538-137">命令會將工作階段儲存於 $s 變數中。</span><span class="sxs-lookup"><span data-stu-id="de538-137">The command saves the session in the $s variable.</span></span>

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a><span data-ttu-id="de538-138">如何使用 Windows PowerShell 2.0 引擎啟動背景工作</span><span class="sxs-lookup"><span data-stu-id="de538-138">How to start a background job with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="de538-139">若要使用 Windows PowerShell 2.0 引擎啟動背景工作，請使用 [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) Cmdlet 的 **PSVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="de538-139">To start a background job with the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) cmdlet.</span></span>

<span data-ttu-id="de538-140">下列命令會使用 Windows PowerShell 2.0 引擎啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="de538-140">The following command starts a background job with the Windows PowerShell 2.0 Engine</span></span>

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

<span data-ttu-id="de538-141">如需背景工作的詳細資訊，請參閱 [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)。</span><span class="sxs-lookup"><span data-stu-id="de538-141">For more information about background jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>