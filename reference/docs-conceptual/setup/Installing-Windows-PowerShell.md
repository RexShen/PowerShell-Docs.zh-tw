---
ms.date: 2017-08-09
keywords: "powershell,cmdlet,下載,安裝,安裝程式,windows 10, windows 8.1, windows 8.0,windows 7"
title: "安裝 Windows PowerShell"
ms.openlocfilehash: 781bf50b6ac649e72bcdbb708555275fb7422d94
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2017
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="3af15-103">安裝 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3af15-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="3af15-104">從 Windows 7 SP1 和 Windows Server 2008 R2 SP1 開始，根據預設，每個 Windows 中都已預先安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3af15-104">PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="3af15-105">想要在機器中安裝 **PowerShell 6** (beta) 的 Linux、macOS 和 Windows 使用者，必須：</span><span class="sxs-lookup"><span data-stu-id="3af15-105">Linux, macOS, and Windows users that would like to install **PowerShell 6** (beta), in their machines, need to:</span></span>

1. <span data-ttu-id="3af15-106">從 [GitHub](https://github.com/powershell/powershell#get-powershell) 取得特定 OS 和版本適用的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3af15-106">Get PowerShell for the specific OS and version, from [GitHub](https://github.com/powershell/powershell#get-powershell)</span></span>
1. <span data-ttu-id="3af15-107">依照安裝指示操作</span><span class="sxs-lookup"><span data-stu-id="3af15-107">Follow the installation instructions</span></span>
  - [<span data-ttu-id="3af15-108">Linux</span><span class="sxs-lookup"><span data-stu-id="3af15-108">Linux</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
  - [<span data-ttu-id="3af15-109">macOS</span><span class="sxs-lookup"><span data-stu-id="3af15-109">macOS</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)
  - [<span data-ttu-id="3af15-110">Windows</span><span class="sxs-lookup"><span data-stu-id="3af15-110">Windows</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi)

<span data-ttu-id="3af15-111">Docker 也可以使用 PowerShell 6；請參閱 [Docker 安裝](https://github.com/PowerShell/PowerShell/tree/master/docker)指示。</span><span class="sxs-lookup"><span data-stu-id="3af15-111">PowerShell 6 is also available for Docker; see [Docker installation](https://github.com/PowerShell/PowerShell/tree/master/docker) instructions.</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="3af15-112">在 Windows 10、8.1、8.0 和 7 中尋找 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3af15-112">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="3af15-113">由於 PowerShell 主控台或 ISE (整合式指令碼環境) 的位置會從某個 Windows 版本移到另一版，因此要在 Windows 中找到並不容易。</span><span class="sxs-lookup"><span data-stu-id="3af15-113">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as it's location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="3af15-114">下表有助於在您的 Windows 版本中找到 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3af15-114">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="3af15-115">此處列出的所有版本都是發行之後未經更新的原始版本。</span><span class="sxs-lookup"><span data-stu-id="3af15-115">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="3af15-116">主控台</span><span class="sxs-lookup"><span data-stu-id="3af15-116">For Console</span></span>

<span data-ttu-id="3af15-117">版本</span><span class="sxs-lookup"><span data-stu-id="3af15-117">Version</span></span> | <span data-ttu-id="3af15-118">位置</span><span class="sxs-lookup"><span data-stu-id="3af15-118">Location</span></span>
-- | --
<span data-ttu-id="3af15-119">Windows 10</span><span class="sxs-lookup"><span data-stu-id="3af15-119">Windows 10</span></span> | <span data-ttu-id="3af15-120">按一下左下角 Windows 圖示，開始鍵入 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3af15-120">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="3af15-121">Windows 8.1、8.0</span><span class="sxs-lookup"><span data-stu-id="3af15-121">Windows 8.1, 8.0</span></span> | <span data-ttu-id="3af15-122">在開始畫面中，開始鍵入 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3af15-122">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="3af15-123">如果在桌面上，則按一下左下角 Windows 圖示，開始鍵入 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3af15-123">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="3af15-124">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="3af15-124">Windows 7 SP1</span></span> | <span data-ttu-id="3af15-125">按一下左下角 Windows 圖示，在搜尋方塊開始鍵入 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3af15-125">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="3af15-126">ISE</span><span class="sxs-lookup"><span data-stu-id="3af15-126">For ISE</span></span>

<span data-ttu-id="3af15-127">版本</span><span class="sxs-lookup"><span data-stu-id="3af15-127">Version</span></span> | <span data-ttu-id="3af15-128">位置</span><span class="sxs-lookup"><span data-stu-id="3af15-128">Location</span></span>
-- | --
<span data-ttu-id="3af15-129">Windows 10</span><span class="sxs-lookup"><span data-stu-id="3af15-129">Windows 10</span></span> | <span data-ttu-id="3af15-130">按一下左下角 Windows 圖示，開始鍵入 ISE</span><span class="sxs-lookup"><span data-stu-id="3af15-130">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="3af15-131">Windows 8.1、8.0</span><span class="sxs-lookup"><span data-stu-id="3af15-131">Windows 8.1, 8.0</span></span> | <span data-ttu-id="3af15-132">在開始畫面上，鍵入 **PowerShell ISE**。</span><span class="sxs-lookup"><span data-stu-id="3af15-132">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="3af15-133">如果在桌面上，則按一下左下角 Windows 圖示，鍵入 **PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="3af15-133">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="3af15-134">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="3af15-134">Windows 7 SP1</span></span> | <span data-ttu-id="3af15-135">按一下左下角 Windows 圖示，在搜尋方塊開始鍵入 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3af15-135">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="3af15-136">在 Windows Server 版本中尋找 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3af15-136">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="3af15-137">從 Windows Server 2008 R2 開始，可以不使用圖形化使用者介面 (GUI) 安裝 Windows 作業系統。</span><span class="sxs-lookup"><span data-stu-id="3af15-137">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="3af15-138">不含 GUI 的 Windows Server 版本會命名為 **Core** 版本，而含 GUI 的版本會命名為 **Desktop**。</span><span class="sxs-lookup"><span data-stu-id="3af15-138">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="3af15-139">Windows Server Core 版本</span><span class="sxs-lookup"><span data-stu-id="3af15-139">Windows Server Core editions</span></span>

<span data-ttu-id="3af15-140">在所有 Core 版本中，當您登入伺服器時，會看到 Windows 命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="3af15-140">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="3af15-141">鍵入 `powershell` 並按 **ENTER**，以在命令提示字元工作階段內啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3af15-141">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span> <span data-ttu-id="3af15-142">鍵入 `exit` 以終止 PowerShell 工作階段，並返回命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="3af15-142">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="3af15-143">Windows Server Desktop 版本</span><span class="sxs-lookup"><span data-stu-id="3af15-143">Windows Server Desktop editions</span></span>

<span data-ttu-id="3af15-144">在所有 Desktop 版本中，按一下左下角 Windows 圖示，開始鍵入 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3af15-144">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="3af15-145">您會同時取得主控台和 ISE 選項。</span><span class="sxs-lookup"><span data-stu-id="3af15-145">You get both console and ISE options.</span></span>

<span data-ttu-id="3af15-146">上述規則中唯一例外的是 Windows Server 2008 R2 SP1 的 ISE。在此情況下，按一下左下角 Windows 圖示，鍵入 PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="3af15-146">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="3af15-147">如何檢查 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="3af15-147">How to check the version of PowerShell</span></span>

<span data-ttu-id="3af15-148">若要知道您安裝的 PowerShell 是哪個版本，請開啟 PowerShell 主控台 (或 ISE)，鍵入 `$PSVersionTable` 並按 **ENTER**。</span><span class="sxs-lookup"><span data-stu-id="3af15-148">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="3af15-149">升級現有的 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3af15-149">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="3af15-150">PowerShell 的安裝套件隨附於 WMF 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="3af15-150">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="3af15-151">WMF 安裝程式的版本會與 PowerShell 版本相符；Windows PowerShell 沒有獨立安裝程式。</span><span class="sxs-lookup"><span data-stu-id="3af15-151">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="3af15-152">如果您需要在 Windows 中更新現有的 PowerShell 版本，請使用下表找出您想要更新的目標 PowerShell 版本安裝程式。</span><span class="sxs-lookup"><span data-stu-id="3af15-152">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="3af15-153">Windows</span><span class="sxs-lookup"><span data-stu-id="3af15-153">Windows</span></span> | <span data-ttu-id="3af15-154">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="3af15-154">PS 3.0</span></span> | <span data-ttu-id="3af15-155">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="3af15-155">PS 4.0</span></span> | <span data-ttu-id="3af15-156">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="3af15-156">PS 5.0</span></span> | <span data-ttu-id="3af15-157">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="3af15-157">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="3af15-158">Windows 10 (請參閱備註 1)</span><span class="sxs-lookup"><span data-stu-id="3af15-158">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="3af15-159">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="3af15-159">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="3af15-160">已安裝</span><span class="sxs-lookup"><span data-stu-id="3af15-160">installed</span></span>
<span data-ttu-id="3af15-161">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="3af15-161">Windows 8.1</span></span><br/><span data-ttu-id="3af15-162">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3af15-162">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="3af15-163">已安裝</span><span class="sxs-lookup"><span data-stu-id="3af15-163">installed</span></span> | [<span data-ttu-id="3af15-164">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="3af15-164">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="3af15-165">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="3af15-165">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="3af15-166">Windows 8</span><span class="sxs-lookup"><span data-stu-id="3af15-166">Windows 8</span></span><br/><span data-ttu-id="3af15-167">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3af15-167">Windows Server 2012</span></span> | <span data-ttu-id="3af15-168">已安裝</span><span class="sxs-lookup"><span data-stu-id="3af15-168">installed</span></span> | [<span data-ttu-id="3af15-169">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="3af15-169">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="3af15-170">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="3af15-170">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="3af15-171">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="3af15-171">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="3af15-172">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="3af15-172">Windows 7 SP1</span></span><br/><span data-ttu-id="3af15-173">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="3af15-173">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="3af15-174">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="3af15-174">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="3af15-175">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="3af15-175">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="3af15-176">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="3af15-176">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="3af15-177">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="3af15-177">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> <span data-ttu-id="3af15-178">**備註 1**：</span><span class="sxs-lookup"><span data-stu-id="3af15-178">**Note 1**:</span></span>
  >>
  >> <span data-ttu-id="3af15-179">在已啟用自動更新的 Windows 10 初始版本上，PowerShell 會從 5.0 版更新為 5.1 版。</span><span class="sxs-lookup"><span data-stu-id="3af15-179">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
  >>
  >> <span data-ttu-id="3af15-180">若 Windows 10 的原始版本未透過 Windows Updtaes 更新，PowerShell 的版本會是 5.0。</span><span class="sxs-lookup"><span data-stu-id="3af15-180">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="3af15-181">Microsoft Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="3af15-181">Need Azure PowerShell</span></span>

<span data-ttu-id="3af15-182">如果您要尋找 **Azure PowerShell**，可以從 [Azure PowerShell 概觀](https://docs.microsoft.com/en-us/powershell/azure)著手。</span><span class="sxs-lookup"><span data-stu-id="3af15-182">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).</span></span>

<span data-ttu-id="3af15-183">否則，您可能需要[安裝與設定 Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span><span class="sxs-lookup"><span data-stu-id="3af15-183">Otherwise, what you might need is [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="3af15-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3af15-184">See Also</span></span>

- [<span data-ttu-id="3af15-185">Windows PowerShell 系統需求</span><span class="sxs-lookup"><span data-stu-id="3af15-185">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="3af15-186">啟動 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3af15-186">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)
