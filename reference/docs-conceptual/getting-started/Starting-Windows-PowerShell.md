---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 啟動 Windows PowerShell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 9184e8b0e508610e7f4775f1032f3a69c93bb8c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058347"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="40b17-103">啟動 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="40b17-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="40b17-104">PowerShell 是指令碼引擎 dll，且會內嵌到多部主機中。</span><span class="sxs-lookup"><span data-stu-id="40b17-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="40b17-105">互動式命令列 PowerShell.exe 和互動式指令碼環境 PowerShell_ISE.exe 是您將啟動的最常見主機。</span><span class="sxs-lookup"><span data-stu-id="40b17-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="40b17-106">若要在 Windows Server® 2012 R2、Windows® 8.1、Windows Server 2012 及 Windows 8 上啟動 Windows PowerShell®，請參閱[常見管理工作及瀏覽方式](https://technet.microsoft.com/library/hh831491.aspx)。</span><span class="sxs-lookup"><span data-stu-id="40b17-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](https://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="40b17-107">如何在舊版 Windows 上啟動 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="40b17-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="40b17-108">本節說明如何在 Windows® 7、Windows Server® 2008 R2 和 Windows Server® 2008 中啟動 Windows PowerShell 和 Windows PowerShell 整合式指令碼環境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="40b17-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="40b17-109">它也會說明如何在 Windows Server® 2008 R2 和 Windows Server® 2008 上的 Windows PowerShell 2.0 中啟用 Windows PowerShell ISE 的選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="40b17-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="40b17-110">使用下列任何方法來啟動已安裝的 Windows PowerShell 3.0 或 Windows PowerShell 4.0 版本 (適用時)。</span><span class="sxs-lookup"><span data-stu-id="40b17-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="40b17-111">從 [開始] 功能表</span><span class="sxs-lookup"><span data-stu-id="40b17-111">From the Start Menu</span></span>

- <span data-ttu-id="40b17-112">按一下 **[開始]**，並輸入 **PowerShell**，然後按一下 **[Windows PowerShell]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="40b17-113">從 **[開始]** 功能表中，依序按一下 **[開始]**、**[所有程式]**、**[附屬應用程式]**、**[Windows PowerShell]** 資料夾和 **[Windows PowerShell]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="40b17-114">在命令提示字元中</span><span class="sxs-lookup"><span data-stu-id="40b17-114">At the Command Prompt</span></span>

<span data-ttu-id="40b17-115">在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要啟動 Windows PowerShell，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="40b17-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="40b17-116">您也可以使用 PowerShell.exe 程式的參數來自訂工作階段。</span><span class="sxs-lookup"><span data-stu-id="40b17-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="40b17-117">如需詳細資訊，請參閱 [PowerShell.exe 命令列說明](../core-powershell/console/PowerShell.exe-Command-Line-Help.md)。</span><span class="sxs-lookup"><span data-stu-id="40b17-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="40b17-118">使用系統管理權限 ([以系統管理員身分執行])</span><span class="sxs-lookup"><span data-stu-id="40b17-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="40b17-119">按一下 [開始]、輸入 **PowerShell**、以滑鼠右鍵按一下 [Windows PowerShell]，然後按一下 [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="40b17-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="40b17-120">如何在舊版 Windows 上啟動 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="40b17-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="40b17-121">使用下列任何方法來啟動 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="40b17-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="40b17-122">從 [開始] 功能表</span><span class="sxs-lookup"><span data-stu-id="40b17-122">From the Start Menu</span></span>

- <span data-ttu-id="40b17-123">按一下 **[開始]**，並輸入 **ISE**，然後按一下 **[Windows PowerShell ISE]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="40b17-124">從 **[開始]** 功能表中，依序按一下 **[開始]**、**[所有程式]**、**[附屬應用程式]**、**[Windows PowerShell]** 資料夾和 **[Windows PowerShell ISE]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="40b17-125">在命令提示字元中</span><span class="sxs-lookup"><span data-stu-id="40b17-125">At the Command Prompt</span></span>

<span data-ttu-id="40b17-126">在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要啟動 Windows PowerShell，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="40b17-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="40b17-127">或</span><span class="sxs-lookup"><span data-stu-id="40b17-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="40b17-128">使用系統管理權限 ([以系統管理員身分執行])</span><span class="sxs-lookup"><span data-stu-id="40b17-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="40b17-129">按一下 [開始]、輸入 **ISE**、以滑鼠右鍵按一下 [Windows PowerShell ISE]，然後按一下 [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="40b17-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="40b17-130">如何在舊版 Windows 上啟用 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="40b17-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="40b17-131">在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中，預設會在所有 Windows 版本上啟用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="40b17-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="40b17-132">如果尚未啟用，則 Windows Management Framework 4.0 或 Windows Management Framework 3.0 會啟用它。</span><span class="sxs-lookup"><span data-stu-id="40b17-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="40b17-133">在 Windows PowerShell 2.0 中，預設會在 Windows 7 上啟用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="40b17-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="40b17-134">不過，在 Windows Server 2008 R2 和 Windows Server 2008 中，這是選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="40b17-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="40b17-135">若要在 Windows Server 2008 R2 或 Windows Server 2008 上的 Windows PowerShell 2.0 中啟用 Windows PowerShell ISE，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="40b17-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="40b17-136">啟用 Windows PowerShell 整合式指令碼環境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="40b17-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="40b17-137">啟動 [伺服器管理員]。</span><span class="sxs-lookup"><span data-stu-id="40b17-137">Start Server Manager.</span></span>
2. <span data-ttu-id="40b17-138">按一下 **[功能]**，然後按一下 **[新增功能]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="40b17-139">在 [選取功能] 中，按一下 [Windows PowerShell 整合式指令碼環境 (ISE)]。</span><span class="sxs-lookup"><span data-stu-id="40b17-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="40b17-140">啟動 32 位元版本的 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="40b17-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="40b17-141">當您在 64 位元電腦上安裝 Windows PowerShell 時，除了 64 位元的版本，還會安裝 32 位元版本的 Windows PowerShell (**Windows PowerShell (x86)**)。</span><span class="sxs-lookup"><span data-stu-id="40b17-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="40b17-142">執行 Windows PowerShell 時，預設會執行 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="40b17-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="40b17-143">不過，您可能偶而需要執行 **Windows PowerShell (x86)**，例如，使用需要 32 位元版本的模組時，或遠端連線至 32 位元電腦時。</span><span class="sxs-lookup"><span data-stu-id="40b17-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="40b17-144">若要啟動 32 位元版本的 Windows PowerShell，請使用下列任何程序。</span><span class="sxs-lookup"><span data-stu-id="40b17-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="40b17-145">在 Windows Server® 2012 R2 中</span><span class="sxs-lookup"><span data-stu-id="40b17-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="40b17-146">在 **[開始]** 畫面上，輸入 **Windows PowerShell (x86)**。</span><span class="sxs-lookup"><span data-stu-id="40b17-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="40b17-147">按一下 **[Windows PowerShell x86]** 並排顯示。</span><span class="sxs-lookup"><span data-stu-id="40b17-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="40b17-148">在 **[伺服器管理員]** 中，從 **[工具]** 功能表中選取 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="40b17-149">在桌面上，將游標移到右上角、按一下 **[搜尋]**、輸入 **PowerShell x86**，然後按一下 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="40b17-150">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="40b17-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="40b17-151">在 Windows Server® 2012 中</span><span class="sxs-lookup"><span data-stu-id="40b17-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="40b17-152">在 **[開始]** 畫面上，輸入 **PowerShell**，然後按一下 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="40b17-153">在 **[伺服器管理員]** 中，從 **[工具]** 功能表中選取 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="40b17-154">在桌面上，將游標移到右上角、按一下 **[搜尋]**、輸入 **PowerShell**，然後按一下 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="40b17-155">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="40b17-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="40b17-156">在 Windows® 8.1 中</span><span class="sxs-lookup"><span data-stu-id="40b17-156">In Windows® 8.1</span></span>

- <span data-ttu-id="40b17-157">在 **[開始]** 畫面上，輸入 **Windows PowerShell (x86)**。</span><span class="sxs-lookup"><span data-stu-id="40b17-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="40b17-158">按一下 **[Windows PowerShell x86]** 並排顯示。</span><span class="sxs-lookup"><span data-stu-id="40b17-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="40b17-159">如果您正在執行 Windows 8.1 的[遠端伺服器管理工具](https://go.microsoft.com/fwlink/?LinkID=304145)，則也可以從 [伺服器管理員工具] 功能表中開啟 Windows PowerShell x86。</span><span class="sxs-lookup"><span data-stu-id="40b17-159">If you are running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="40b17-160">選取 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="40b17-161">在桌面上，將游標移到右上角、按一下 **[搜尋]**、輸入 **PowerShell x86**，然後按一下 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="40b17-162">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="40b17-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="40b17-163">在 Windows® 8 中</span><span class="sxs-lookup"><span data-stu-id="40b17-163">In Windows® 8</span></span>

- <span data-ttu-id="40b17-164">在 **[開始]** 畫面上，將游標移到右上角，並依序按一下 **[設定]** 和 **[並排顯示]**，然後將 **[顯示系統管理工具]** 移到 [是]。</span><span class="sxs-lookup"><span data-stu-id="40b17-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="40b17-165">然後輸入 **PowerShell**，並按一下 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="40b17-166">如果您正在執行 Windows 8 的 [遠端伺服器管理工具](https://www.microsoft.com/download/details.aspx?id=28972)，則也可以從 [伺服器管理員工具] 功能表中開啟 Windows PowerShell x86。</span><span class="sxs-lookup"><span data-stu-id="40b17-166">If you are running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="40b17-167">選取 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="40b17-168">在 **[開始]** 畫面或桌面上，輸入 **PowerShell (x86)**，然後按一下 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="40b17-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="40b17-169">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="40b17-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>