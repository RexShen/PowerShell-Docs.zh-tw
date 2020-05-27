---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: 啟動 Windows PowerShell
ms.openlocfilehash: 32ed85510899ea239c9dc332a023554ce9b53e47
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809014"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="a45bd-103">啟動 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a45bd-103">Starting Windows PowerShell</span></span>

<span data-ttu-id="a45bd-104">Windows PowerShell 是指令碼引擎 `.DLL`，其會內嵌到多部主機中。</span><span class="sxs-lookup"><span data-stu-id="a45bd-104">Windows PowerShell is a scripting engine `.DLL` that's embedded into multiple hosts.</span></span> <span data-ttu-id="a45bd-105">互動式命令列 **powershell.exe** 與互動式指令碼環境 **powershell_ise.exe** 是您將啟動的最常見主機。</span><span class="sxs-lookup"><span data-stu-id="a45bd-105">The most common hosts you'll start are the interactive command-line **powershell.exe** and the Interactive Scripting Environment **powershell_ise.exe**.</span></span>

<span data-ttu-id="a45bd-106">若要在 Windows Server® 2012 R2、Windows® 8.1、Windows Server 2012 及 Windows 8 上啟動 Windows PowerShell®，請參閱 [Windows 中的常見管理工作與瀏覽](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11))。</span><span class="sxs-lookup"><span data-stu-id="a45bd-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span></span>

## <a name="powershell-core-has-renamed-binary"></a><span data-ttu-id="a45bd-107">PowerShell Core 已重新命名二進位</span><span class="sxs-lookup"><span data-stu-id="a45bd-107">PowerShell Core has renamed binary</span></span>

<span data-ttu-id="a45bd-108">PowerShell Core (稱為 PowerShell) 是開放原始碼的第 6 版和更高版本，且使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="a45bd-108">PowerShell Core, referred to as PowerShell, is version 6 and higher that's open source and uses .NET Core.</span></span> <span data-ttu-id="a45bd-109">支援的版本適用於 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="a45bd-109">Supported versions are available on Windows, macOS, and Linux.</span></span>

<span data-ttu-id="a45bd-110">從 PowerShell 6 開始，PowerShell 二進位已針對 Windows 重新命名為 **pwsh.exe**，並針對 macOS 和 Linux 重新命名為 **pwsh**。</span><span class="sxs-lookup"><span data-stu-id="a45bd-110">Beginning in PowerShell 6, the PowerShell binary was renamed **pwsh.exe** for Windows and **pwsh** for macOS and Linux.</span></span> <span data-ttu-id="a45bd-111">您可以使用 **pwsh-preview** 以啟動 PowerShell 預覽版本。</span><span class="sxs-lookup"><span data-stu-id="a45bd-111">You can start PowerShell preview versions using **pwsh-preview**.</span></span> <span data-ttu-id="a45bd-112">如需詳細資訊，請參閱 [PowerShell Core 6.0 的新功能](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe)和[關於 pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="a45bd-112">For more information, see [What's New in PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) and [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span></span>

<span data-ttu-id="a45bd-113">若要尋找 PowerShell 7 的 Cmdlet 參考和安裝文件，請使用下列連結：</span><span class="sxs-lookup"><span data-stu-id="a45bd-113">To find cmdlet reference and installation documentation for PowerShell 7, use the following links:</span></span>

| <span data-ttu-id="a45bd-114">Document</span><span class="sxs-lookup"><span data-stu-id="a45bd-114">Document</span></span> | <span data-ttu-id="a45bd-115">連結</span><span class="sxs-lookup"><span data-stu-id="a45bd-115">Link</span></span> |
| ----- | ----- |
| <span data-ttu-id="a45bd-116">Cmdlet 參考</span><span class="sxs-lookup"><span data-stu-id="a45bd-116">Cmdlet reference</span></span> | [<span data-ttu-id="a45bd-117">PowerShell 模組瀏覽器</span><span class="sxs-lookup"><span data-stu-id="a45bd-117">PowerShell Module Browser</span></span>](/powershell/module/?view=powershell-7) |
| <span data-ttu-id="a45bd-118">Windows 安裝</span><span class="sxs-lookup"><span data-stu-id="a45bd-118">Windows installation</span></span> | [<span data-ttu-id="a45bd-119">在 Windows 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="a45bd-119">Installing PowerShell Core on Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7) |
| <span data-ttu-id="a45bd-120">macOS 安裝</span><span class="sxs-lookup"><span data-stu-id="a45bd-120">macOS installation</span></span> | [<span data-ttu-id="a45bd-121">在 macOS 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="a45bd-121">Installing PowerShell Core on macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) |
| <span data-ttu-id="a45bd-122">Linux 安裝</span><span class="sxs-lookup"><span data-stu-id="a45bd-122">Linux installation</span></span> | [<span data-ttu-id="a45bd-123">在 Linux 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="a45bd-123">Installing PowerShell Core on Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) |

<span data-ttu-id="a45bd-124">若要查看其他 PowerShell 版本的內容，請參閱[如何使用 PowerShell 文件](../how-to-use-docs.md)。</span><span class="sxs-lookup"><span data-stu-id="a45bd-124">To view content for other PowerShell versions, see [How to use the PowerShell documentation](../how-to-use-docs.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="a45bd-125">如何在舊版 Windows 上啟動 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a45bd-125">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="a45bd-126">本節說明如何在 Windows® 7、Windows Server® 2008 R2 和 Windows Server® 2008 中啟動 Windows PowerShell 和 Windows PowerShell 整合式指令碼環境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="a45bd-126">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="a45bd-127">它也會說明如何在 Windows Server® 2008 R2 和 Windows Server® 2008 上的 Windows PowerShell 2.0 中啟用 Windows PowerShell ISE 的選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="a45bd-127">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="a45bd-128">使用下列任何方法來啟動已安裝的 Windows PowerShell 3.0 或 Windows PowerShell 4.0 版本 (適用時)。</span><span class="sxs-lookup"><span data-stu-id="a45bd-128">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="a45bd-129">從 [開始] 功能表</span><span class="sxs-lookup"><span data-stu-id="a45bd-129">From the Start Menu</span></span>

- <span data-ttu-id="a45bd-130">按一下 **[開始]** ，並輸入 **PowerShell**，然後按一下 **[Windows PowerShell]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-130">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="a45bd-131">從 **[開始]** 功能表中，依序按一下 **[開始]** 、 **[所有程式]** 、 **[附屬應用程式]** 、 **[Windows PowerShell]** 資料夾和 **[Windows PowerShell]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-131">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="a45bd-132">在命令提示字元中</span><span class="sxs-lookup"><span data-stu-id="a45bd-132">At the Command Prompt</span></span>

<span data-ttu-id="a45bd-133">在 **cmd.exe**、Windows PowerShell 或 Windows PowerShell ISE 中，若要啟動 Windows PowerShell，請鍵入︰</span><span class="sxs-lookup"><span data-stu-id="a45bd-133">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="a45bd-134">您也可以使用 **powershell.exe** 程式的參數來自訂工作階段。</span><span class="sxs-lookup"><span data-stu-id="a45bd-134">You can also use the parameters of the **powershell.exe** program to customize the session.</span></span> <span data-ttu-id="a45bd-135">如需詳細資訊，請參閱 [PowerShell.exe 命令列說明](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe)。</span><span class="sxs-lookup"><span data-stu-id="a45bd-135">For more information, see [PowerShell.exe Command-Line Help](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="a45bd-136">使用系統管理權限 (以系統管理員身分執行)</span><span class="sxs-lookup"><span data-stu-id="a45bd-136">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="a45bd-137">按一下 [開始]  、輸入 **PowerShell**、以滑鼠右鍵按一下 [Windows PowerShell]  ，然後按一下 [以系統管理員身分執行]  。</span><span class="sxs-lookup"><span data-stu-id="a45bd-137">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="a45bd-138">如何在舊版 Windows 上啟動 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a45bd-138">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="a45bd-139">使用下列任何方法來啟動 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="a45bd-139">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="a45bd-140">從 [開始] 功能表</span><span class="sxs-lookup"><span data-stu-id="a45bd-140">From the Start Menu</span></span>

- <span data-ttu-id="a45bd-141">按一下 **[開始]** ，並輸入 **ISE**，然後按一下 **[Windows PowerShell ISE]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-141">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="a45bd-142">從 **[開始]** 功能表中，依序按一下 **[開始]** 、 **[所有程式]** 、 **[附屬應用程式]** 、 **[Windows PowerShell]** 資料夾和 **[Windows PowerShell ISE]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-142">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="a45bd-143">在命令提示字元中</span><span class="sxs-lookup"><span data-stu-id="a45bd-143">At the Command Prompt</span></span>

<span data-ttu-id="a45bd-144">在 **cmd.exe**、Windows PowerShell 或 Windows PowerShell ISE 中，若要啟動 Windows PowerShell，請鍵入︰</span><span class="sxs-lookup"><span data-stu-id="a45bd-144">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="a45bd-145">或</span><span class="sxs-lookup"><span data-stu-id="a45bd-145">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="a45bd-146">使用系統管理權限 (以系統管理員身分執行)</span><span class="sxs-lookup"><span data-stu-id="a45bd-146">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="a45bd-147">按一下 [開始]  、輸入 **ISE**、以滑鼠右鍵按一下 [Windows PowerShell ISE]  ，然後按一下 [以系統管理員身分執行]  。</span><span class="sxs-lookup"><span data-stu-id="a45bd-147">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="a45bd-148">如何在舊版 Windows 上啟用 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a45bd-148">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="a45bd-149">在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中，預設會在所有 Windows 版本上啟用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="a45bd-149">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="a45bd-150">如果尚未啟用，則 Windows Management Framework 4.0 或 Windows Management Framework 3.0 會將其啟用。</span><span class="sxs-lookup"><span data-stu-id="a45bd-150">If it isn't already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="a45bd-151">在 Windows PowerShell 2.0 中，預設會在 Windows 7 上啟用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="a45bd-151">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="a45bd-152">不過，在 Windows Server 2008 R2 和 Windows Server 2008 中，這是選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="a45bd-152">However, on Windows Server 2008 R2 and Windows Server 2008, it's an optional feature.</span></span>

<span data-ttu-id="a45bd-153">若要在 Windows Server 2008 R2 或 Windows Server 2008 上的 Windows PowerShell 2.0 中啟用 Windows PowerShell ISE，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="a45bd-153">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="a45bd-154">啟用 Windows PowerShell 整合式指令碼環境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="a45bd-154">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="a45bd-155">啟動伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="a45bd-155">Start Server Manager.</span></span>
2. <span data-ttu-id="a45bd-156">按一下 **[功能]** ，然後按一下 **[新增功能]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-156">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="a45bd-157">在 [選取功能] 中，按一下 [Windows PowerShell 整合式指令碼環境 (ISE)]。</span><span class="sxs-lookup"><span data-stu-id="a45bd-157">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="a45bd-158">啟動 32 位元版本的 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a45bd-158">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="a45bd-159">當您在 64 位元電腦上安裝 Windows PowerShell 時，除了 64 位元的版本，還會安裝 32 位元版本的 Windows PowerShell (**Windows PowerShell (x86)** )。</span><span class="sxs-lookup"><span data-stu-id="a45bd-159">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="a45bd-160">執行 Windows PowerShell 時，預設會執行 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="a45bd-160">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="a45bd-161">不過，您可能偶爾需要執行 **Windows PowerShell (x86)** 例如，使用需要 32 位元版本的模組時，或遠端連線至 32 位元電腦時。</span><span class="sxs-lookup"><span data-stu-id="a45bd-161">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you're using a module that requires the 32-bit version or when you're connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="a45bd-162">若要啟動 32 位元版本的 Windows PowerShell，請使用下列任何程序。</span><span class="sxs-lookup"><span data-stu-id="a45bd-162">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="a45bd-163">在 Windows Server® 2012 R2 中</span><span class="sxs-lookup"><span data-stu-id="a45bd-163">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="a45bd-164">在 **[開始]** 畫面上，輸入 **Windows PowerShell (x86)** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-164">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="a45bd-165">按一下 **[Windows PowerShell x86]** 並排顯示。</span><span class="sxs-lookup"><span data-stu-id="a45bd-165">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="a45bd-166">在 **[伺服器管理員]** 中，從 **[工具]** 功能表中選取 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-166">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a45bd-167">在桌面上，將游標移到右上角、按一下 **[搜尋]** 、輸入 **PowerShell x86**，然後按一下 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-167">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a45bd-168">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="a45bd-168">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="a45bd-169">在 Windows Server® 2012 中</span><span class="sxs-lookup"><span data-stu-id="a45bd-169">In Windows Server® 2012</span></span>

- <span data-ttu-id="a45bd-170">在 **[開始]** 畫面上，輸入 **PowerShell**，然後按一下 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-170">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a45bd-171">在 **[伺服器管理員]** 中，從 **[工具]** 功能表中選取 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-171">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a45bd-172">在桌面上，將游標移到右上角、按一下 **[搜尋]** 、輸入 **PowerShell**，然後按一下 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-172">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a45bd-173">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="a45bd-173">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="a45bd-174">在 Windows® 8.1 中</span><span class="sxs-lookup"><span data-stu-id="a45bd-174">In Windows® 8.1</span></span>

- <span data-ttu-id="a45bd-175">在 **[開始]** 畫面上，輸入 **Windows PowerShell (x86)** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-175">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="a45bd-176">按一下 **[Windows PowerShell x86]** 並排顯示。</span><span class="sxs-lookup"><span data-stu-id="a45bd-176">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="a45bd-177">如果您正在執行 Windows 8.1 的[遠端伺服器管理工具](https://go.microsoft.com/fwlink/?LinkID=304145)，則也可以從 [伺服器管理員工具]  功能表中開啟 Windows PowerShell x86。</span><span class="sxs-lookup"><span data-stu-id="a45bd-177">If you're running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="a45bd-178">選取 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-178">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a45bd-179">在桌面上，將游標移到右上角、按一下 **[搜尋]** 、輸入 **PowerShell x86**，然後按一下 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-179">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a45bd-180">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="a45bd-180">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="a45bd-181">在 Windows® 8 中</span><span class="sxs-lookup"><span data-stu-id="a45bd-181">In Windows® 8</span></span>

- <span data-ttu-id="a45bd-182">在 [開始]  畫面上，將游標移到右上角，並依序按一下 [設定]  和 [並排顯示]  ，然後將 [顯示系統管理工具]  移到 [是]  。</span><span class="sxs-lookup"><span data-stu-id="a45bd-182">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to **Yes**.</span></span> <span data-ttu-id="a45bd-183">然後輸入 **PowerShell**，並按一下 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-183">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a45bd-184">如果您正在執行 Windows 8 的 [遠端伺服器管理工具](https://www.microsoft.com/download/details.aspx?id=28972)，則也可以從 [伺服器管理員工具]  功能表中開啟 Windows PowerShell x86。</span><span class="sxs-lookup"><span data-stu-id="a45bd-184">If you're running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="a45bd-185">選取 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-185">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a45bd-186">在 **[開始]** 畫面或桌面上，輸入 **PowerShell (x86)** ，然後按一下 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="a45bd-186">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a45bd-187">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="a45bd-187">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>
