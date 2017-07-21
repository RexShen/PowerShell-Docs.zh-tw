---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "在舊版 Windows 上啟動 Windows PowerShell"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: cb56fded1e67a4f4219d210dd95078314e855b1a
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="1af1f-103">在舊版 Windows 上啟動 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1af1f-103">Starting Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="1af1f-104">本節說明如何在 Windows® 7、Windows Server® 2008 R2 和 Windows Server® 2008 中啟動 Windows PowerShell 和 Windows PowerShell 整合式指令碼環境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="1af1f-104">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="1af1f-105">它也會說明如何在 Windows Server® 2008 R2 和 Windows Server® 2008 上的 Windows PowerShell 2.0 中啟用 Windows PowerShell ISE 的選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="1af1f-105">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="1af1f-106">若要在支援的系統上安裝 Windows PowerShell 4.0，請下載並安裝 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881)。</span><span class="sxs-lookup"><span data-stu-id="1af1f-106">To install Windows PowerShell 4.0 on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span></span> <span data-ttu-id="1af1f-107">如需詳細資訊，請參閱[安裝 Windows PowerShell](Installing-Windows-PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="1af1f-107">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="1af1f-108">若要在支援的系統上安裝 Windows PowerShell 3.0，請下載並安裝 [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290)。</span><span class="sxs-lookup"><span data-stu-id="1af1f-108">To install Windows PowerShell 3.0 on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span> <span data-ttu-id="1af1f-109">如需詳細資訊，請參閱[安裝 Windows PowerShell](Installing-Windows-PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="1af1f-109">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="1af1f-110">如何在舊版 Windows 上啟動 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1af1f-110">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="1af1f-111">使用下列任何方法來啟動已安裝的 Windows PowerShell 3.0 或 Windows PowerShell 4.0 版本 (適用時)。</span><span class="sxs-lookup"><span data-stu-id="1af1f-111">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="1af1f-112">從 [開始] 功能表</span><span class="sxs-lookup"><span data-stu-id="1af1f-112">From the Start Menu</span></span>

-   <span data-ttu-id="1af1f-113">按一下 **[開始]**，並輸入 **PowerShell**，然後按一下 **[Windows PowerShell]**。</span><span class="sxs-lookup"><span data-stu-id="1af1f-113">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>

-   <span data-ttu-id="1af1f-114">從 **[開始]** 功能表中，依序按一下 **[開始]**、**[所有程式]**、**[附屬應用程式]**、**[Windows PowerShell]** 資料夾和 **[Windows PowerShell]**。</span><span class="sxs-lookup"><span data-stu-id="1af1f-114">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="1af1f-115">在命令提示字元中</span><span class="sxs-lookup"><span data-stu-id="1af1f-115">At the Command Prompt</span></span>

-   <span data-ttu-id="1af1f-116">在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要啟動 Windows PowerShell，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="1af1f-116">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell
    ```

    <span data-ttu-id="1af1f-117">您也可以使用 PowerShell.exe 程式的參數來自訂工作階段。</span><span class="sxs-lookup"><span data-stu-id="1af1f-117">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="1af1f-118">如需詳細資訊，請參閱 [PowerShell.exe 命令列說明](../core-powershell/console/PowerShell.exe-Command-Line-Help.md)。</span><span class="sxs-lookup"><span data-stu-id="1af1f-118">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="1af1f-119">使用系統管理權限 ([以系統管理員身分執行])</span><span class="sxs-lookup"><span data-stu-id="1af1f-119">With Administrative privileges ("Run as administrator")</span></span>

1.  <span data-ttu-id="1af1f-120">按一下 [開始]、輸入 **PowerShell**、以滑鼠右鍵按一下 [Windows PowerShell]，然後按一下 [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="1af1f-120">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="1af1f-121">如何在舊版 Windows 上啟動 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="1af1f-121">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="1af1f-122">使用下列任何方法來啟動 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="1af1f-122">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="1af1f-123">從 [開始] 功能表</span><span class="sxs-lookup"><span data-stu-id="1af1f-123">From the Start Menu</span></span>

-   <span data-ttu-id="1af1f-124">按一下 **[開始]**，並輸入 **ISE**，然後按一下 **[Windows PowerShell ISE]**。</span><span class="sxs-lookup"><span data-stu-id="1af1f-124">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>

-   <span data-ttu-id="1af1f-125">從 **[開始]** 功能表中，依序按一下 **[開始]**、**[所有程式]**、**[附屬應用程式]**、**[Windows PowerShell]** 資料夾和 **[Windows PowerShell ISE]**。</span><span class="sxs-lookup"><span data-stu-id="1af1f-125">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="1af1f-126">在命令提示字元中</span><span class="sxs-lookup"><span data-stu-id="1af1f-126">At the Command Prompt</span></span>

-   <span data-ttu-id="1af1f-127">在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要啟動 Windows PowerShell，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="1af1f-127">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell_ISE
    ```

    <span data-ttu-id="1af1f-128">或</span><span class="sxs-lookup"><span data-stu-id="1af1f-128">or</span></span>

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="1af1f-129">使用系統管理權限 ([以系統管理員身分執行])</span><span class="sxs-lookup"><span data-stu-id="1af1f-129">With Administrative privileges ("Run as administrator")</span></span>

1.  <span data-ttu-id="1af1f-130">按一下 [開始]、輸入 **ISE**、以滑鼠右鍵按一下 [Windows PowerShell ISE]，然後按一下 [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="1af1f-130">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="1af1f-131">如何在舊版 Windows 上啟用 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="1af1f-131">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="1af1f-132">在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中，預設會在所有 Windows 版本上啟用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="1af1f-132">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="1af1f-133">如果尚未啟用，則 Windows Management Framework 4.0 或 Windows Management Framework 3.0 會啟用它。</span><span class="sxs-lookup"><span data-stu-id="1af1f-133">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="1af1f-134">在 Windows PowerShell 2.0 中，預設會在 Windows 7 上啟用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="1af1f-134">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="1af1f-135">不過，在 Windows Server 2008 R2 和 Windows Server 2008 中，這是選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="1af1f-135">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="1af1f-136">若要在 Windows Server 2008 R2 或 Windows Server 2008 上的 Windows PowerShell 2.0 中啟用 Windows PowerShell ISE，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="1af1f-136">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="1af1f-137">啟用 Windows PowerShell 整合式指令碼環境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="1af1f-137">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1.  <span data-ttu-id="1af1f-138">啟動 [伺服器管理員]。</span><span class="sxs-lookup"><span data-stu-id="1af1f-138">Start Server Manager.</span></span>

2.  <span data-ttu-id="1af1f-139">按一下 **[功能]**，然後按一下 **[新增功能]**。</span><span class="sxs-lookup"><span data-stu-id="1af1f-139">Click **Features** and then click **Add Features**.</span></span>

3.  <span data-ttu-id="1af1f-140">在 [選取功能] 中，按一下 [Windows PowerShell 整合式指令碼環境 (ISE)]。</span><span class="sxs-lookup"><span data-stu-id="1af1f-140">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

