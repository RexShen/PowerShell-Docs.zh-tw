---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: 啟動 Windows PowerShell
description: 此文章說明啟動各種 PowerShell 版本的方式。
ms.openlocfilehash: 47da7d85c9f7e6966a7f7e809c77979cd24cf129
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664028"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="50623-104">啟動 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="50623-104">Starting Windows PowerShell</span></span>

<span data-ttu-id="50623-105">Windows PowerShell 是指令碼引擎 `.DLL`，其會內嵌到多部主機中。</span><span class="sxs-lookup"><span data-stu-id="50623-105">Windows PowerShell is a scripting engine `.DLL` that's embedded into multiple hosts.</span></span> <span data-ttu-id="50623-106">您將啟動的最常見主機為互動式命令列 `powershell.exe` 與互動式指令碼環境 `powershell_ise.exe`。</span><span class="sxs-lookup"><span data-stu-id="50623-106">The most common hosts you'll start are the interactive command-line `powershell.exe` and the Interactive Scripting Environment `powershell_ise.exe`.</span></span>

<span data-ttu-id="50623-107">若要在 Windows Server&reg; 2012 R2、Windows&reg; 8.1、Windows Server 2012 與 Windows 8 上啟動 Windows PowerShell&reg;，請參閱 [Windows 中的常見管理工作與瀏覽](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11))。</span><span class="sxs-lookup"><span data-stu-id="50623-107">To start Windows PowerShell&reg; on Windows Server&reg; 2012 R2, Windows&reg; 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span></span>

## <a name="powershell-core-has-renamed-binary"></a><span data-ttu-id="50623-108">PowerShell Core 已重新命名二進位</span><span class="sxs-lookup"><span data-stu-id="50623-108">PowerShell Core has renamed binary</span></span>

<span data-ttu-id="50623-109">PowerShell Core (稱為 PowerShell) 是開放原始碼的第 6 版和更高版本，且使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="50623-109">PowerShell Core, referred to as PowerShell, is version 6 and higher that's open source and uses .NET Core.</span></span> <span data-ttu-id="50623-110">支援的版本適用於 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="50623-110">Supported versions are available on Windows, macOS, and Linux.</span></span>

<span data-ttu-id="50623-111">從 PowerShell 6 開始，PowerShell 二進位已針對 Windows 重新命名為 `pwsh.exe`，並針對 macOS 與 Linux 重新命名為 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="50623-111">Beginning in PowerShell 6, the PowerShell binary was renamed `pwsh.exe` for Windows and `pwsh` for macOS and Linux.</span></span> <span data-ttu-id="50623-112">您可以使用 `pwsh-preview` 來啟動 PowerShell 預覽版本。</span><span class="sxs-lookup"><span data-stu-id="50623-112">You can start PowerShell preview versions using `pwsh-preview`.</span></span> <span data-ttu-id="50623-113">如需詳細資訊，請參閱 [PowerShell Core 6.0 的新功能](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe)和[關於 pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh)。</span><span class="sxs-lookup"><span data-stu-id="50623-113">For more information, see [What's New in PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) and [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh).</span></span>

<span data-ttu-id="50623-114">若要尋找 PowerShell 7 的 Cmdlet 參考和安裝文件，請使用下列連結：</span><span class="sxs-lookup"><span data-stu-id="50623-114">To find cmdlet reference and installation documentation for PowerShell 7, use the following links:</span></span>

| <span data-ttu-id="50623-115">文件</span><span class="sxs-lookup"><span data-stu-id="50623-115">Document</span></span> | <span data-ttu-id="50623-116">連結</span><span class="sxs-lookup"><span data-stu-id="50623-116">Link</span></span> |
| ----- | ----- |
| <span data-ttu-id="50623-117">Cmdlet 參考</span><span class="sxs-lookup"><span data-stu-id="50623-117">Cmdlet reference</span></span> | [<span data-ttu-id="50623-118">PowerShell 模組瀏覽器</span><span class="sxs-lookup"><span data-stu-id="50623-118">PowerShell Module Browser</span></span>](/powershell/module/) |
| <span data-ttu-id="50623-119">Windows 安裝</span><span class="sxs-lookup"><span data-stu-id="50623-119">Windows installation</span></span> | [<span data-ttu-id="50623-120">在 Windows 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="50623-120">Installing PowerShell Core on Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows) |
| <span data-ttu-id="50623-121">macOS 安裝</span><span class="sxs-lookup"><span data-stu-id="50623-121">macOS installation</span></span> | [<span data-ttu-id="50623-122">在 macOS 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="50623-122">Installing PowerShell Core on macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos) |
| <span data-ttu-id="50623-123">Linux 安裝</span><span class="sxs-lookup"><span data-stu-id="50623-123">Linux installation</span></span> | [<span data-ttu-id="50623-124">在 Linux 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="50623-124">Installing PowerShell Core on Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux) |

<span data-ttu-id="50623-125">若要查看其他 PowerShell 版本的內容，請參閱[如何使用 PowerShell 文件](../how-to-use-docs.md)。</span><span class="sxs-lookup"><span data-stu-id="50623-125">To view content for other PowerShell versions, see [How to use the PowerShell documentation](../how-to-use-docs.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="50623-126">如何在舊版 Windows 上啟動 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="50623-126">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="50623-127">此節說明如何在 Windows&reg; 7、Windows Server&reg; 2008 R2 與 Windows Server&reg; 2008 中，啟動 Windows PowerShell 與 Windows PowerShell 整合式指令碼環境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="50623-127">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows&reg; 7, Windows Server&reg; 2008 R2, and Windows Server&reg; 2008.</span></span> <span data-ttu-id="50623-128">同時也會說明如何在 Windows Server&reg; 2008 R2 與 Windows Server&reg; 2008 上的 Windows PowerShell 2.0 中，啟用 Windows PowerShell ISE 的選用功能。</span><span class="sxs-lookup"><span data-stu-id="50623-128">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server&reg; 2008 R2 and Windows Server&reg; 2008.</span></span>

<span data-ttu-id="50623-129">使用下列任何方法來啟動已安裝的 Windows PowerShell 3.0 或 Windows PowerShell 4.0 版本 (適用時)。</span><span class="sxs-lookup"><span data-stu-id="50623-129">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="50623-130">從 [開始] 功能表</span><span class="sxs-lookup"><span data-stu-id="50623-130">From the Start Menu</span></span>

- <span data-ttu-id="50623-131">按一下 **[開始]** ，並輸入 **PowerShell** ，然後按一下 **[Windows PowerShell]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-131">Click **Start** , type **PowerShell** , and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="50623-132">從 **[開始]** 功能表中，依序按一下 **[開始]** 、 **[所有程式]** 、 **[附屬應用程式]** 、 **[Windows PowerShell]** 資料夾和 **[Windows PowerShell]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-132">From the **Start** menu, click **Start** , click **All Programs** , click **Accessories** , click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="50623-133">在命令提示字元中</span><span class="sxs-lookup"><span data-stu-id="50623-133">At the Command Prompt</span></span>

<span data-ttu-id="50623-134">在 **cmd.exe** 、Windows PowerShell 或 Windows PowerShell ISE 中，若要啟動 Windows PowerShell，請鍵入︰</span><span class="sxs-lookup"><span data-stu-id="50623-134">In **cmd.exe** , Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="50623-135">您也可以使用 `powershell.exe` 程式的參數來自訂工作階段。</span><span class="sxs-lookup"><span data-stu-id="50623-135">You can also use the parameters of the `powershell.exe` program to customize the session.</span></span> <span data-ttu-id="50623-136">如需詳細資訊，請參閱 [PowerShell.exe 命令列說明](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe)。</span><span class="sxs-lookup"><span data-stu-id="50623-136">For more information, see [PowerShell.exe Command-Line Help](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="50623-137">使用系統管理權限 (以系統管理員身分執行)</span><span class="sxs-lookup"><span data-stu-id="50623-137">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="50623-138">按一下 [開始]、輸入 **PowerShell** 、以滑鼠右鍵按一下 [Windows PowerShell]，然後按一下 [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="50623-138">Click **Start** , type **PowerShell** , right-click **Windows PowerShell** , and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="50623-139">如何在舊版 Windows 上啟動 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="50623-139">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="50623-140">使用下列任何方法來啟動 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="50623-140">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="50623-141">從 [開始] 功能表</span><span class="sxs-lookup"><span data-stu-id="50623-141">From the Start Menu</span></span>

- <span data-ttu-id="50623-142">按一下 **[開始]** ，並輸入 **ISE** ，然後按一下 **[Windows PowerShell ISE]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-142">Click **Start** , type **ISE** , and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="50623-143">從 **[開始]** 功能表中，依序按一下 **[開始]** 、 **[所有程式]** 、 **[附屬應用程式]** 、 **[Windows PowerShell]** 資料夾和 **[Windows PowerShell ISE]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-143">From the **Start** menu, click **Start** , click **All Programs** , click **Accessories** , click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="50623-144">在命令提示字元中</span><span class="sxs-lookup"><span data-stu-id="50623-144">At the Command Prompt</span></span>

<span data-ttu-id="50623-145">在 `cmd.exe`、Windows PowerShell 或 Windows PowerShell ISE 中，若要啟動 Windows PowerShell，請輸入：</span><span class="sxs-lookup"><span data-stu-id="50623-145">In `cmd.exe`, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="50623-146">或</span><span class="sxs-lookup"><span data-stu-id="50623-146">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="50623-147">使用系統管理權限 (以系統管理員身分執行)</span><span class="sxs-lookup"><span data-stu-id="50623-147">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="50623-148">按一下 [開始]、輸入 **ISE** 、以滑鼠右鍵按一下 [Windows PowerShell ISE]，然後按一下 [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="50623-148">Click **Start** , type **ISE** , right-click **Windows PowerShell ISE** , and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="50623-149">如何在舊版 Windows 上啟用 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="50623-149">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="50623-150">在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中，預設會在所有 Windows 版本上啟用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="50623-150">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="50623-151">如果尚未啟用，則 Windows Management Framework 4.0 或 Windows Management Framework 3.0 會將其啟用。</span><span class="sxs-lookup"><span data-stu-id="50623-151">If it isn't already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="50623-152">在 Windows PowerShell 2.0 中，預設會在 Windows 7 上啟用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="50623-152">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="50623-153">不過，在 Windows Server 2008 R2 和 Windows Server 2008 中，這是選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="50623-153">However, on Windows Server 2008 R2 and Windows Server 2008, it's an optional feature.</span></span>

<span data-ttu-id="50623-154">若要在 Windows Server 2008 R2 或 Windows Server 2008 上的 Windows PowerShell 2.0 中啟用 Windows PowerShell ISE，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="50623-154">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="50623-155">啟用 Windows PowerShell 整合式指令碼環境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="50623-155">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="50623-156">啟動伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="50623-156">Start Server Manager.</span></span>
2. <span data-ttu-id="50623-157">按一下 **[功能]** ，然後按一下 **[新增功能]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-157">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="50623-158">在 [選取功能] 中，按一下 [Windows PowerShell 整合式指令碼環境 (ISE)]。</span><span class="sxs-lookup"><span data-stu-id="50623-158">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="50623-159">啟動 32 位元版本的 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="50623-159">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="50623-160">當您在 64 位元電腦上安裝 Windows PowerShell 時，除了 64 位元的版本，還會安裝 32 位元版本的 Windows PowerShell ( **Windows PowerShell (x86)** )。</span><span class="sxs-lookup"><span data-stu-id="50623-160">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)** , a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="50623-161">執行 Windows PowerShell 時，預設會執行 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="50623-161">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="50623-162">不過，您可能偶爾需要執行 **Windows PowerShell (x86)** 例如，使用需要 32 位元版本的模組時，或遠端連線至 32 位元電腦時。</span><span class="sxs-lookup"><span data-stu-id="50623-162">However, you might occasionally need to run **Windows PowerShell (x86)** , such as when you're using a module that requires the 32-bit version or when you're connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="50623-163">若要啟動 32 位元版本的 Windows PowerShell，請使用下列任何程序。</span><span class="sxs-lookup"><span data-stu-id="50623-163">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-serverreg-2012-r2"></a><span data-ttu-id="50623-164">在 Windows Server&reg; 2012 R2 中</span><span class="sxs-lookup"><span data-stu-id="50623-164">In Windows Server&reg; 2012 R2</span></span>

- <span data-ttu-id="50623-165">在 **[開始]** 畫面上，輸入 **Windows PowerShell (x86)** 。</span><span class="sxs-lookup"><span data-stu-id="50623-165">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="50623-166">按一下 **[Windows PowerShell x86]** 並排顯示。</span><span class="sxs-lookup"><span data-stu-id="50623-166">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="50623-167">在 **[伺服器管理員]** 中，從 **[工具]** 功能表中選取 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-167">In **Server Manager** , from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="50623-168">在桌面上，將游標移到右上角、按一下 **[搜尋]** 、輸入 **PowerShell x86** ，然後按一下 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-168">On the desktop, move the cursor to the upper right corner, click **Search** , type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="50623-169">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="50623-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-serverreg-2012"></a><span data-ttu-id="50623-170">在 Windows Server&reg; 2012 中</span><span class="sxs-lookup"><span data-stu-id="50623-170">In Windows Server&reg; 2012</span></span>

- <span data-ttu-id="50623-171">在 **[開始]** 畫面上，輸入 **PowerShell** ，然後按一下 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-171">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="50623-172">在 **[伺服器管理員]** 中，從 **[工具]** 功能表中選取 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-172">In **Server Manager** , from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="50623-173">在桌面上，將游標移到右上角、按一下 **[搜尋]** 、輸入 **PowerShell** ，然後按一下 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-173">On the desktop, move the cursor to the upper right corner, click **Search** , type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="50623-174">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="50623-174">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windowsreg-81"></a><span data-ttu-id="50623-175">在 Windows&reg; 8.1 中</span><span class="sxs-lookup"><span data-stu-id="50623-175">In Windows&reg; 8.1</span></span>

- <span data-ttu-id="50623-176">在 **[開始]** 畫面上，輸入 **Windows PowerShell (x86)** 。</span><span class="sxs-lookup"><span data-stu-id="50623-176">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="50623-177">按一下 **[Windows PowerShell x86]** 並排顯示。</span><span class="sxs-lookup"><span data-stu-id="50623-177">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="50623-178">如果您正在執行 Windows 8.1 的[遠端伺服器管理工具](https://go.microsoft.com/fwlink/?LinkID=304145)，則也可以從 [伺服器管理員工具] 功能表中開啟 Windows PowerShell x86。</span><span class="sxs-lookup"><span data-stu-id="50623-178">If you're running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="50623-179">選取 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-179">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="50623-180">在桌面上，將游標移到右上角、按一下 **[搜尋]** 、輸入 **PowerShell x86** ，然後按一下 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-180">On the desktop, move the cursor to the upper right corner, click **Search** , type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="50623-181">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="50623-181">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windowsreg-8"></a><span data-ttu-id="50623-182">在 Windows&reg; 8 中</span><span class="sxs-lookup"><span data-stu-id="50623-182">In Windows&reg; 8</span></span>

- <span data-ttu-id="50623-183">在 [開始] 畫面上，將游標移到右上角，並依序按一下 [設定] 和 [並排顯示]，然後將 [顯示系統管理工具] 移到 [是]。</span><span class="sxs-lookup"><span data-stu-id="50623-183">On the **Start** screen, move the cursor to the upper right corner, click **Settings** , click **Tiles** , and then move the **Show Administrative Tools** slider to **Yes**.</span></span> <span data-ttu-id="50623-184">然後輸入 **PowerShell** ，並按一下 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-184">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="50623-185">如果您正在執行 Windows 8 的 [遠端伺服器管理工具](https://www.microsoft.com/download/details.aspx?id=28972)，則也可以從 [伺服器管理員工具] 功能表中開啟 Windows PowerShell x86。</span><span class="sxs-lookup"><span data-stu-id="50623-185">If you're running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="50623-186">選取 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-186">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="50623-187">在 **[開始]** 畫面或桌面上，輸入 **PowerShell (x86)** ，然後按一下 **[Windows PowerShell (x86)]** 。</span><span class="sxs-lookup"><span data-stu-id="50623-187">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="50623-188">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="50623-188">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>
