---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "變更電腦狀態"
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: 636690c72b16bf19826b0a7e54ce00114ce30fb6
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="changing-computer-state"></a><span data-ttu-id="b12b2-103">變更電腦狀態</span><span class="sxs-lookup"><span data-stu-id="b12b2-103">Changing Computer State</span></span>
<span data-ttu-id="b12b2-104">若要在 Windows PowerShell 中重設電腦，請使用標準命令列工具或 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="b12b2-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="b12b2-105">雖然您使用 Windows PowerShell 只是為了執行工具，但是了解如何在 Windows PowerShell 中變更電腦的電源狀態，描述了有關在 Windows PowerShell 中使用外部工具的一些重要詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b12b2-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

### <a name="locking-a-computer"></a><span data-ttu-id="b12b2-106">鎖定電腦</span><span class="sxs-lookup"><span data-stu-id="b12b2-106">Locking a Computer</span></span>
<span data-ttu-id="b12b2-107">透過可用的標準工具直接鎖定電腦的唯一方式，是呼叫 **user32.dll** 中的 **LockWorkstation()** 函式：</span><span class="sxs-lookup"><span data-stu-id="b12b2-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="b12b2-108">此命令會立即鎖定工作站。</span><span class="sxs-lookup"><span data-stu-id="b12b2-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="b12b2-109">它使用執行 Windows DLL (並儲存其程式庫以供重複使用) 的 *rundll32.exe*，來執行 Windows 管理函式程式庫 user32.dll。</span><span class="sxs-lookup"><span data-stu-id="b12b2-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="b12b2-110">如果您在啟用 [快速切換使用者] 時鎖定工作站 (例如在 Windows XP 上)，電腦會顯示在使用者登入畫面，而不是啟動目前使用者的螢幕保護裝置。</span><span class="sxs-lookup"><span data-stu-id="b12b2-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="b12b2-111">若要關閉終端機伺服器上的特定工作階段，請使用 **tsshutdn.exe** 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="b12b2-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

### <a name="logging-off-the-current-session"></a><span data-ttu-id="b12b2-112">登出目前的工作階段</span><span class="sxs-lookup"><span data-stu-id="b12b2-112">Logging Off the Current Session</span></span>
<span data-ttu-id="b12b2-113">您可以使用幾項不同的技術，來登出本機系統上的工作階段。</span><span class="sxs-lookup"><span data-stu-id="b12b2-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="b12b2-114">最簡單的方式是使用遠端桌面/終端機服務命令列工具 **logoff.exe** (如需詳細資訊，請在 Windows PowerShell 命令提示字元中，輸入 **logoff /?**)。</span><span class="sxs-lookup"><span data-stu-id="b12b2-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="b12b2-115">若要登出目前使用中的工作階段，請輸入 **logoff** 且不加引數。</span><span class="sxs-lookup"><span data-stu-id="b12b2-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="b12b2-116">您也可以使用 **shutdown.exe** 工具搭配其登出選項︰</span><span class="sxs-lookup"><span data-stu-id="b12b2-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="b12b2-117">第三個選項是使用 WMI。</span><span class="sxs-lookup"><span data-stu-id="b12b2-117">A third option is to use WMI.</span></span> <span data-ttu-id="b12b2-118">Win32_OperatingSystem 類別具有 Win32Shutdown 方法。</span><span class="sxs-lookup"><span data-stu-id="b12b2-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="b12b2-119">叫用方法加上 0 旗標會起始登出︰</span><span class="sxs-lookup"><span data-stu-id="b12b2-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="b12b2-120">如需詳細資訊，以及尋找 Win32Shutdown 方法的其他函式，請參閱 MSDN 中的＜Win32Shutdown Method of the Win32_OperatingSystem Class＞(Win32_OperatingSystem 類別的 Win32Shutdown 方法)。</span><span class="sxs-lookup"><span data-stu-id="b12b2-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

### <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="b12b2-121">關閉或重新啟動電腦</span><span class="sxs-lookup"><span data-stu-id="b12b2-121">Shutting Down or Restarting a Computer</span></span>
<span data-ttu-id="b12b2-122">關閉並重新啟動電腦通常是相同類型的工作。</span><span class="sxs-lookup"><span data-stu-id="b12b2-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="b12b2-123">用來關閉電腦的工具通常也會用來重新啟動電腦，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="b12b2-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="b12b2-124">從 Windows PowerShell 重新啟動電腦有兩個直接的作法。</span><span class="sxs-lookup"><span data-stu-id="b12b2-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="b12b2-125">使用 Tsshutdn.exe 或 Shutdown.exe 加上適當的引數。</span><span class="sxs-lookup"><span data-stu-id="b12b2-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="b12b2-126">您可以從 **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="b12b2-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="b12b2-127">或 **shutdown.exe /?** 取得詳細的使用資訊。</span><span class="sxs-lookup"><span data-stu-id="b12b2-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="b12b2-128">您也可以直接從 Windows PowerShell 使用 **Win32_OperatingSystem**，來執行關閉和重新啟動作業。</span><span class="sxs-lookup"><span data-stu-id="b12b2-128">You can also perform shutdown and restart operations by using **Win32_OperatingSystem** directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="b12b2-129">若要關閉電腦，請使用 Win32Shutdown 方法加上 **1** 旗標。</span><span class="sxs-lookup"><span data-stu-id="b12b2-129">To shut down the computer, use the Win32Shutdown method with the **1** flag.</span></span>

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(1)
```

<span data-ttu-id="b12b2-130">若要重新啟動電腦，請使用 Win32Shutdown 方法加上 **2** 旗標。</span><span class="sxs-lookup"><span data-stu-id="b12b2-130">To restart the operating system, use the Win32Shutdown method with the **2** flag.</span></span>

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(2)
```

