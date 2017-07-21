---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "安裝 Windows PowerShell"
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
ms.openlocfilehash: 2b4cdec52dfc98649a81ab2265a204fcdb0bd8d7
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="e7691-103">安裝 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7691-103">Installing Windows PowerShell</span></span>
<span data-ttu-id="e7691-104">Windows® 8 和 Windows Server® 2012 包括 Windows PowerShell 3.0 及其所有必要條件。</span><span class="sxs-lookup"><span data-stu-id="e7691-104">Windows® 8 and Windows Server® 2012 include Windows PowerShell 3.0 and all of its prerequisites.</span></span> <span data-ttu-id="e7691-105">此系統也會包含 Windows PowerShell 2.0 引擎，以針對無法使用 Windows PowerShell 3.0 的舊版主機程式提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="e7691-105">The system also includes the Windows PowerShell 2.0 engine for backward compatibility with host programs that cannot use Windows PowerShell 3.0.</span></span>

<span data-ttu-id="e7691-106">本主題說明如何在舊版系統上安裝 Windows PowerShell 3.0，以及安裝和啟用必要的功能。</span><span class="sxs-lookup"><span data-stu-id="e7691-106">This topic explains how to install Windows PowerShell 3.0 on earlier systems and install and enable the required features.</span></span>

<span data-ttu-id="e7691-107">這個主題包括下列各節：</span><span class="sxs-lookup"><span data-stu-id="e7691-107">This topic includes the following sections:</span></span>

-   [<span data-ttu-id="e7691-108">在 Windows 8 和 Windows Server 2012 上安裝 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7691-108">Installing Windows PowerShell on Windows 8 and Windows Server 2012</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [<span data-ttu-id="e7691-109">在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7691-109">Installing Windows PowerShell on Windows 7 and Windows Server 2008 R2</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [<span data-ttu-id="e7691-110">在 Windows Server 2008 上安裝 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7691-110">Installing Windows PowerShell on Windows Server 2008</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [<span data-ttu-id="e7691-111">在 Server Core 上安裝 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7691-111">Installing Windows PowerShell on Server Core</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [<span data-ttu-id="e7691-112">部署 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="e7691-112">Deploying Windows PowerShell Web Access</span></span>](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [<span data-ttu-id="e7691-113">安裝 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="e7691-113">Installing the Windows PowerShell 2.0 Engine</span></span>](Installing-the-Windows-PowerShell-2.0-Engine.md)

## <span data-ttu-id="e7691-114"><a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>在 Windows 8 和 Windows Server 2012 上安裝 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7691-114"><a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Installing Windows PowerShell on Windows 8 and Windows Server 2012</span></span>
<span data-ttu-id="e7691-115">Windows PowerShell 3.0 預設已安裝、設定且可供使用。</span><span class="sxs-lookup"><span data-stu-id="e7691-115">Windows PowerShell 3.0 arrives installed, configured, and ready to use.</span></span> <span data-ttu-id="e7691-116">Windows PowerShell 整合指令碼環境 (ISE) 已安裝並啟用。</span><span class="sxs-lookup"><span data-stu-id="e7691-116">Windows PowerShell Integrated Scripting Environment (ISE) is installed and enabled.</span></span> <span data-ttu-id="e7691-117">如需啟動 Windows PowerShell 的相關資訊，請參閱 [在 Windows 8 上啟動 Windows PowerShell](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) 以及[在 Windows Server 2012 上啟動 Windows PowerShell](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell)。</span><span class="sxs-lookup"><span data-stu-id="e7691-117">For information about starting Windows PowerShell, see [Starting Windows PowerShell on Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) and [Starting Windows PowerShell on Windows Server 2012](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell).</span></span>

## <span data-ttu-id="e7691-118"><a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7691-118"><a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Installing Windows PowerShell on Windows 7 and Windows Server 2008 R2</span></span>
<span data-ttu-id="e7691-119">下列指示說明如何在執行 Windows 7 Service Pack 1 和 Windows Server 2008 R2 Service Pack 1 的電腦上安裝 Windows PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="e7691-119">These instructions explain how to install Windows PowerShell 3.0 on computers running Windows 7 with Service Pack 1 and Windows Server 2008 R2 with Service Pack 1.</span></span> <span data-ttu-id="e7691-120">針對以 Windows Server 2008 R2 的 Server Core 安裝選項執行的電腦，將在下方提供個別安裝指示。</span><span class="sxs-lookup"><span data-stu-id="e7691-120">There are separate installation instructions below for computers running with the Server Core installation option of Windows Server 2008 R2.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="e7691-121">準備安裝</span><span class="sxs-lookup"><span data-stu-id="e7691-121">Getting ready to install</span></span>

-   <span data-ttu-id="e7691-122">安裝 Windows Management Framework 3.0 之前，請先解除安裝任何舊版的 Windows Management Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="e7691-122">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="e7691-123">安裝 Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="e7691-123">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="e7691-124">從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547) 安裝 Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) 的完整安裝。</span><span class="sxs-lookup"><span data-stu-id="e7691-124">Install the full installation of Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span></span>

    <span data-ttu-id="e7691-125">或者，從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919) 安裝 Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe)。</span><span class="sxs-lookup"><span data-stu-id="e7691-125">Or, install Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span></span>

2.  <span data-ttu-id="e7691-126">前往 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 從 Microsoft 下載中心安裝 Windows Management Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="e7691-126">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

<span data-ttu-id="e7691-127">如需啟動 Windows PowerShell 3.0 的相關資訊，請參閱[在舊版 Windows 上啟動 Windows PowerShell](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md)。</span><span class="sxs-lookup"><span data-stu-id="e7691-127">For information about starting Windows PowerShell 3.0, see [Starting Windows PowerShell on Earlier Versions of Windows](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md).</span></span>

## <span data-ttu-id="e7691-128"><a name="BKMK_InstallingOnServerCore"></a>在 Server Core 上安裝 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7691-128"><a name="BKMK_InstallingOnServerCore"></a>Installing Windows PowerShell on Server Core</span></span>
<span data-ttu-id="e7691-129">下列指示說明如何在執行 Windows Server 2008 R2 Service Pack 1 之 Server Core 安裝選項的電腦上安裝 Windows PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="e7691-129">These instructions explain how to install Windows PowerShell 3.0 on computers running the Server Core installation option of Windows Server 2008 R2 with Service Pack 1.</span></span>

<span data-ttu-id="e7691-130">此程序的第一個步驟是使用部署映像服務與管理 (DISM) 命令，安裝適用於 Server Core 的 Microsoft .NET Framework 2.0 和 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="e7691-130">The first steps in the procedure use Deployment Image Servicing and Management (DISM) commands to install Microsoft .NET Framework 2.0 for Server Core and Windows PowerShell 2.0.</span></span> <span data-ttu-id="e7691-131">這些程式是要在後續步驟中安裝之 Windows Management Framework 3.0 的先決條件。</span><span class="sxs-lookup"><span data-stu-id="e7691-131">These programs are prerequisites for Windows Management Framework 3.0, which is installed in a subsequent step.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="e7691-132">準備安裝</span><span class="sxs-lookup"><span data-stu-id="e7691-132">Getting ready to install</span></span>

-   <span data-ttu-id="e7691-133">安裝 Windows Management Framework 3.0 之前，請先解除安裝任何舊版的 Windows Management Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="e7691-133">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="e7691-134">安裝 Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="e7691-134">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="e7691-135">啟動 Cmd.exe</span><span class="sxs-lookup"><span data-stu-id="e7691-135">Start Cmd.exe</span></span>

2.  <span data-ttu-id="e7691-136">執行下列 DISM 命令。</span><span class="sxs-lookup"><span data-stu-id="e7691-136">Run the following DISM commands.</span></span> <span data-ttu-id="e7691-137">這些命令會安裝 .NET Framework 2.0 與 Windows PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="e7691-137">These commands install .NET Framework 2.0 and Windows PowerShell 2.0.</span></span>

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  <span data-ttu-id="e7691-138">前往 [https://www.microsoft.com/zh-tw/download/details.aspx?displaylang=en&id=22833](http://go.microsoft.com/fwlink/?LinkID=248450) 從 Microsoft 下載中心安裝適用於 Server Core 的 Microsoft .NET Framework 4.0 完整安裝。</span><span class="sxs-lookup"><span data-stu-id="e7691-138">Install Microsoft .NET Framework 4.0 full installation for Server Core from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).</span></span>

4.  <span data-ttu-id="e7691-139">前往 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 從 Microsoft 下載中心安裝 Windows Management Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="e7691-139">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

## <span data-ttu-id="e7691-140"><a name="BKMK_InstallingOnWindowsServer2008LH"></a>在 Windows Server 2008 上安裝 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7691-140"><a name="BKMK_InstallingOnWindowsServer2008LH"></a>Installing Windows PowerShell on Windows Server 2008</span></span>
<span data-ttu-id="e7691-141">下列指示說明如何在執行 Windows Server 2008 Service Pack 2 的電腦上安裝 Windows PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="e7691-141">These instructions explain how to install Windows PowerShell 3.0 on computers running Windows Server 2008 with Service Pack 2.</span></span>

<span data-ttu-id="e7691-142">在 Windows Server 2008 系統上，Windows Management Framework (Windows PowerShell 2.0，KB 968930) 是 Windows Management Framework 3.0 的先決條件。</span><span class="sxs-lookup"><span data-stu-id="e7691-142">On Windows Server 2008 systems, Windows Management Framework (Windows PowerShell 2.0, KB 968930) is a prerequisite for Windows Management Framework 3.0.</span></span> <span data-ttu-id="e7691-143">[驗證擴充保護] 功能可防止電腦遭受驗證轉寄攻擊，並可讓您在建立遠端工作階段時使用 **UseSSL** 參數。</span><span class="sxs-lookup"><span data-stu-id="e7691-143">The "Extended Protection for Authentication" feature protects the computer from authentication forwarding attacks and allows you to use the **UseSSL** parameter when creating remote sessions.</span></span> <span data-ttu-id="e7691-144">若要安裝 Windows PowerShell 3.0 和 Windows PowerShell 2.0 引擎，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="e7691-144">To install Windows PowerShell 3.0 and the Windows PowerShell 2.0 Engine, use the following procedure.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="e7691-145">準備安裝</span><span class="sxs-lookup"><span data-stu-id="e7691-145">Getting ready to install</span></span>

-   <span data-ttu-id="e7691-146">安裝 Windows Management Framework 3.0 之前，請先解除安裝任何舊版的 Windows Management Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="e7691-146">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="e7691-147">安裝 Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="e7691-147">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="e7691-148">從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910) 安裝 Microsoft .NET Framework 3.5 Service Pack 1。</span><span class="sxs-lookup"><span data-stu-id="e7691-148">Install Microsoft .NET Framework 3.5 with Service Pack 1 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).</span></span>

2.  <span data-ttu-id="e7691-149">前往 [https://support.microsoft.com/zh-tw/kb/968930](http://go.microsoft.com/fwlink/?LinkId=243035) 從 Microsoft 下載中心安裝 Windows Management Framework (Windows PowerShell 2.0，KB 968930)。</span><span class="sxs-lookup"><span data-stu-id="e7691-149">Install Windows Management Framework (Windows PowerShell 2.0, KB 968930) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).</span></span>

3.  <span data-ttu-id="e7691-150">從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547) 安裝 Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) 的完整安裝。</span><span class="sxs-lookup"><span data-stu-id="e7691-150">Install the full installation of Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span></span>

    <span data-ttu-id="e7691-151">或者，從 Microsoft 下載中心的 [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919) 安裝 Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe)。</span><span class="sxs-lookup"><span data-stu-id="e7691-151">Or, install Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span></span>

4.  <span data-ttu-id="e7691-152">從 [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398) 安裝「驗證延伸保護」(KB 968389)。</span><span class="sxs-lookup"><span data-stu-id="e7691-152">Install "Extended Protection for Authentication" (KB 968389) from [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).</span></span>

5.  <span data-ttu-id="e7691-153">前往 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 從 Microsoft 下載中心安裝 Windows Management Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="e7691-153">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

## <a name="see-also"></a><span data-ttu-id="e7691-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7691-154">See Also</span></span>
- [<span data-ttu-id="e7691-155">Windows PowerShell 系統需求</span><span class="sxs-lookup"><span data-stu-id="e7691-155">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="e7691-156">啟動 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7691-156">Starting Windows PowerShell</span></span>](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)

