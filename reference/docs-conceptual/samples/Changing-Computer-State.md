---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 變更電腦狀態
description: 此範例會示範如何使用 PowerShell 中的外部命令來管理電腦組態。
ms.openlocfilehash: 341f29f24d7e4bd341ccc0954b16d4b75880678b
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500669"
---
# <a name="changing-computer-state"></a><span data-ttu-id="a0724-104">變更電腦狀態</span><span class="sxs-lookup"><span data-stu-id="a0724-104">Changing Computer State</span></span>

<span data-ttu-id="a0724-105">若要在 PowerShell 中重設電腦，請使用標準命令列工具、WMI 或 CIM 類別。</span><span class="sxs-lookup"><span data-stu-id="a0724-105">To reset a computer in PowerShell, use either a standard command-line tool, WMI, or a CIM class.</span></span>
<span data-ttu-id="a0724-106">雖然您使用 PowerShell 只是為了執行工具，但是了解如何在 PowerShell 中變更電腦的電源狀態，描述了有關在 PowerShell 中使用外部工具的一些重要詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a0724-106">Although you are using PowerShell only to run the tool, learning how to change a computer's power state in PowerShell illustrates some of the important details about working with external tools in PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="a0724-107">鎖定電腦</span><span class="sxs-lookup"><span data-stu-id="a0724-107">Locking a Computer</span></span>

<span data-ttu-id="a0724-108">透過可用的標準工具直接鎖定電腦的唯一方式，是呼叫 **user32.dll** 中的 **LockWorkstation()** 函式：</span><span class="sxs-lookup"><span data-stu-id="a0724-108">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll** :</span></span>

```powershell
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="a0724-109">此命令會立即鎖定工作站。</span><span class="sxs-lookup"><span data-stu-id="a0724-109">This command immediately locks the workstation.</span></span> <span data-ttu-id="a0724-110">它使用執行 Windows DLL (並儲存其程式庫以供重複使用) 的 **rundll32.exe** ，來執行 Windows 管理函式程式庫 `user32.dll`。</span><span class="sxs-lookup"><span data-stu-id="a0724-110">It uses **rundll32.exe** , which runs Windows DLLs (and saves their libraries for repeated use) to run `user32.dll`, a library of Windows management functions.</span></span>

<span data-ttu-id="a0724-111">如果您在啟用 [快速切換使用者] 時鎖定工作站 (例如在 Windows XP 上)，電腦會顯示在使用者登入畫面，而不是啟動目前使用者的螢幕保護裝置。</span><span class="sxs-lookup"><span data-stu-id="a0724-111">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="a0724-112">若要關閉終端機伺服器上的特定工作階段，請使用 **tsshutdn.exe** 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="a0724-112">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="a0724-113">登出目前的工作階段</span><span class="sxs-lookup"><span data-stu-id="a0724-113">Logging Off the Current Session</span></span>

<span data-ttu-id="a0724-114">您可以使用幾項不同的技術，來登出本機系統上的工作階段。</span><span class="sxs-lookup"><span data-stu-id="a0724-114">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="a0724-115">最簡單的方式是使用遠端桌面/終端機服務命令列工具 **logoff.exe** (如需詳細資訊，請在 PowerShell 命令提示字元中，輸入 `logoff /?`)。</span><span class="sxs-lookup"><span data-stu-id="a0724-115">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the PowerShell prompt, type `logoff /?`).</span></span> <span data-ttu-id="a0724-116">若要登出目前使用中的工作階段，請輸入 `logoff` 且不搭配引數。</span><span class="sxs-lookup"><span data-stu-id="a0724-116">To log off the current active session, type `logoff` with no arguments.</span></span>

<span data-ttu-id="a0724-117">您也可以使用 **shutdown.exe** 工具搭配其登出選項︰</span><span class="sxs-lookup"><span data-stu-id="a0724-117">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```powershell
shutdown.exe -l
```

<span data-ttu-id="a0724-118">另一個選項是使用 WMI。</span><span class="sxs-lookup"><span data-stu-id="a0724-118">Another option is to use WMI.</span></span> <span data-ttu-id="a0724-119">**Win32_OperatingSystem** 類別具有 **Shutdown** 方法。</span><span class="sxs-lookup"><span data-stu-id="a0724-119">The **Win32_OperatingSystem** class has a **Shutdown** method.</span></span>
<span data-ttu-id="a0724-120">叫用方法加上 0 旗標會起始登出︰</span><span class="sxs-lookup"><span data-stu-id="a0724-120">Invoking the method with the 0 flag initiates logoff:</span></span>

<span data-ttu-id="a0724-121">如需有關 **Shutdown** 方法的詳細資訊，請參閱 [Win32_OperatingSystem 類別的 Shutdown 方法](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span><span class="sxs-lookup"><span data-stu-id="a0724-121">For more information about the **Shutdown** method, see [Shutdown method of the Win32_OperatingSystem class](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span></span>

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="a0724-122">關閉或重新啟動電腦</span><span class="sxs-lookup"><span data-stu-id="a0724-122">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="a0724-123">關閉並重新啟動電腦通常是相同類型的工作。</span><span class="sxs-lookup"><span data-stu-id="a0724-123">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="a0724-124">用來關閉電腦的工具通常也會用來重新啟動電腦，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="a0724-124">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="a0724-125">有兩個從 PowerShell 重新啟動電腦的簡單選項。</span><span class="sxs-lookup"><span data-stu-id="a0724-125">There are two straightforward options for restarting a computer from PowerShell.</span></span> <span data-ttu-id="a0724-126">使用 **tsshutdn.exe** 或 **shutdown.exe** 搭配適當的引數。</span><span class="sxs-lookup"><span data-stu-id="a0724-126">Use either **tsshutdn.exe** or **shutdown.exe** with appropriate arguments.</span></span> <span data-ttu-id="a0724-127">您可以從 `tsshutdn.exe /?` 或 `shutdown.exe /?` 取得詳細的使用方式資訊。</span><span class="sxs-lookup"><span data-stu-id="a0724-127">You can get detailed usage information from `tsshutdn.exe /?` or `shutdown.exe /?`.</span></span>

<span data-ttu-id="a0724-128">您也可以直接從 PowerShell 執行關閉和重新啟動作業。</span><span class="sxs-lookup"><span data-stu-id="a0724-128">You can also perform shutdown and restart operations directly from PowerShell as well.</span></span>

<span data-ttu-id="a0724-129">若要關閉電腦，請使用 Stop-Computer 命令</span><span class="sxs-lookup"><span data-stu-id="a0724-129">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="a0724-130">若要重新啟動作業系統，請使用 Restart-Computer 命令</span><span class="sxs-lookup"><span data-stu-id="a0724-130">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="a0724-131">若要強制立即重新啟動電腦，請使用 -Force 參數。</span><span class="sxs-lookup"><span data-stu-id="a0724-131">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
