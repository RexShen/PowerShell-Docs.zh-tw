---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 安裝 Windows PowerShell 2.0 引擎
description: Windows PowerShell 2.0 引擎是 Windows 的選用功能。 此文章說明如何安裝此功能及必要的需求。
ms.openlocfilehash: c82725c34f5c5864eba0c88eb33ecac9e43f86d3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663969"
---
# <a name="installing-the-windows-powershell-20-engine"></a><span data-ttu-id="f5184-105">安裝 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="f5184-105">Installing the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="f5184-106">本主題說明如何安裝 Windows PowerShell 2.0 引擎。</span><span class="sxs-lookup"><span data-stu-id="f5184-106">This topic explains how to install the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="f5184-107">Windows PowerShell 3.0 已設計為可回溯相容至 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="f5184-107">Windows PowerShell 3.0 is designed to be backwards compatible with Windows PowerShell 2.0.</span></span> <span data-ttu-id="f5184-108">針對 Windows PowerShell 2.0 撰寫的 Cmdlet、提供者、嵌入式管理單元、模組及指令碼，在 Windows PowerShell 3.0 和 Windows PowerShell 4.0 中仍以同樣方式執行。</span><span class="sxs-lookup"><span data-stu-id="f5184-108">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 run unchanged in Windows PowerShell 3.0 and Windows PowerShell 4.0.</span></span> <span data-ttu-id="f5184-109">不過，因為 Microsoft .NET Framework 4 中執行階段啟用原則的變更，所以在較新版的 Windows PowerShell (使用 CLR 4.0 編譯) 中，必須修改才能執行針對 Windows PowerShell 2.0 所撰寫並使用通用語言執行平台 (CLR) 2.0 編譯的 Windows PowerShell 主機程式。</span><span class="sxs-lookup"><span data-stu-id="f5184-109">However, due to a change in the runtime activation policy in Microsoft .NET Framework 4, Windows PowerShell host programs that were written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in later releases of Windows PowerShell, which is compiled with CLR 4.0.</span></span>

<span data-ttu-id="f5184-110">為了維持與受到這些變更影響之主機程式的回溯相容性，已將 Windows PowerShell 2.0、Windows PowerShell 3.0 及 Windows PowerShell 4.0 引擎設計為並存執行。</span><span class="sxs-lookup"><span data-stu-id="f5184-110">To maintain backward compatibility with commands and host programs that are affected by these changes, the Windows PowerShell 2.0, Windows PowerShell 3.0, and Windows PowerShell 4.0 engines are designed to run side-by-side.</span></span> <span data-ttu-id="f5184-111">此外，Windows PowerShell 2.0 引擎隨附於 Windows Server 2012 R2、Windows 8.1、Windows 8、Windows Server 2012 及 Windows Management Framework 3.0 中。</span><span class="sxs-lookup"><span data-stu-id="f5184-111">Also, the Windows PowerShell 2.0 Engine is included in Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012, and Windows Management Framework 3.0.</span></span> <span data-ttu-id="f5184-112">只有在現有指令碼或主機程式無法執行時才會使用 Windows PowerShell 2.0 引擎，因為它與 Windows PowerShell 3.0、Windows PowerShell 4.0 或 Microsoft .NET Framework 4 不相容。</span><span class="sxs-lookup"><span data-stu-id="f5184-112">The Windows PowerShell 2.0 Engine is intended to be used only when an existing script or host program cannot run because it is incompatible with Windows PowerShell 3.0, Windows PowerShell 4.0, or Microsoft .NET Framework 4.</span></span> <span data-ttu-id="f5184-113">這種情況應該很少見。</span><span class="sxs-lookup"><span data-stu-id="f5184-113">Such cases are expected to be rare.</span></span>

<span data-ttu-id="f5184-114">Windows PowerShell 2.0 引擎是 Windows Server 2012 R2、Windows 8.1、Windows&reg; 8 與 Windows Server&reg; 2012 的選用功能。</span><span class="sxs-lookup"><span data-stu-id="f5184-114">The Windows PowerShell 2.0 Engine is an optional feature of Windows Server 2012 R2, Windows 8.1, Windows&reg; 8 and Windows Server&reg; 2012.</span></span> <span data-ttu-id="f5184-115">在舊版 Windows 中，當您安裝 Windows Management Framework 3.0 時，Windows PowerShell 3.0 安裝會完全取代 Windows PowerShell 安裝目錄中的 Windows PowerShell 2.0 安裝。</span><span class="sxs-lookup"><span data-stu-id="f5184-115">On earlier versions of Windows, when you install Windows Management Framework 3.0, the Windows PowerShell 3.0 installation completely replaces the Windows PowerShell 2.0 installation in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="f5184-116">不過，會保留 Windows PowerShell 2.0 引擎。</span><span class="sxs-lookup"><span data-stu-id="f5184-116">However, the Windows PowerShell 2.0 Engine is retained.</span></span>

<span data-ttu-id="f5184-117">如需啟動 Windows PowerShell 2.0 引擎的相關資訊，請參閱[啟動 Windows PowerShell 2.0 引擎](../Starting-the-Windows-PowerShell-2.0-Engine.md)。</span><span class="sxs-lookup"><span data-stu-id="f5184-117">For information about starting the Windows PowerShell 2.0 Engine, see [Starting the Windows PowerShell 2.0 Engine](../Starting-the-Windows-PowerShell-2.0-Engine.md).</span></span>

## <a name="on-windows-81-and-windows-8"></a><span data-ttu-id="f5184-118">在 Windows 8.1 和 Windows 8 上</span><span class="sxs-lookup"><span data-stu-id="f5184-118">On Windows 8.1 and Windows 8</span></span>

<span data-ttu-id="f5184-119">在 Windows 8.1 和 Windows 8 上，預設會開啟 Windows PowerShell 2.0 引擎功能。</span><span class="sxs-lookup"><span data-stu-id="f5184-119">On Windows 8.1 and Windows 8, the Windows PowerShell 2.0 Engine feature is turned on by default.</span></span>
<span data-ttu-id="f5184-120">不過若要使用，則必須開啟所需的 Microsoft .NET Framework 3.5 選項。</span><span class="sxs-lookup"><span data-stu-id="f5184-120">However, to use it, you need to turn on the option for Microsoft .NET Framework 3.5, which it requires.</span></span> <span data-ttu-id="f5184-121">本節也會說明如何開啟及關閉 Windows PowerShell 2.0 引擎功能。</span><span class="sxs-lookup"><span data-stu-id="f5184-121">This section also explains how to turn the Windows PowerShell 2.0 Engine feature on and off.</span></span>

#### <a name="to-turn-on-net-framework-35"></a><span data-ttu-id="f5184-122">開啟 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="f5184-122">To turn on .NET Framework 3.5</span></span>

1. <span data-ttu-id="f5184-123">在 **[開始]** 畫面上，輸入 **Windows 功能** 。</span><span class="sxs-lookup"><span data-stu-id="f5184-123">On the **Start** screen, type **Windows Features**.</span></span>
2. <span data-ttu-id="f5184-124">在 **[應用程式]** 列中按一下 **[設定]** ，然後按一下 **[開啟或關閉 Windows 功能]** 。</span><span class="sxs-lookup"><span data-stu-id="f5184-124">On the **Apps** bar, click **Settings** , and then click **Turn Windows features on or off**.</span></span>
3. <span data-ttu-id="f5184-125">在 **[Windows 功能]** 方塊中，按一下 **[.NET Framework 3.5 (包括 .NET 2.0 和 3.0)]** 加以選取。</span><span class="sxs-lookup"><span data-stu-id="f5184-125">In the **Windows Features** box, click **.NET Framework 3.5 (includes .NET 2.0 and 3.0** to select it.</span></span>

   <span data-ttu-id="f5184-126">當您選取 **[.NET Framework 3.5 (包括 .NET 2.0 和 3.0)]** 時，會填入方塊中以指出僅選取部分功能。</span><span class="sxs-lookup"><span data-stu-id="f5184-126">When you select **.NET Framework 3.5 (includes .NET 2.0 and 3.0** , the box fills to indicate that only part of the feature is selected.</span></span> <span data-ttu-id="f5184-127">不過，這樣已足以應付 Windows PowerShell 2.0 引擎。</span><span class="sxs-lookup"><span data-stu-id="f5184-127">However, this is sufficient for the Windows PowerShell 2.0 Engine.</span></span>

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a><span data-ttu-id="f5184-128">啟動和關閉 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="f5184-128">To turn the Windows PowerShell 2.0 Engine on and off</span></span>

1. <span data-ttu-id="f5184-129">在 **[開始]** 畫面上，輸入 **Windows 功能** 。</span><span class="sxs-lookup"><span data-stu-id="f5184-129">On the **Start** screen, type **Windows Features**.</span></span>

2. <span data-ttu-id="f5184-130">在 **[應用程式]** 列中按一下 **[設定]** ，然後按一下 **[開啟或關閉 Windows 功能]** 。</span><span class="sxs-lookup"><span data-stu-id="f5184-130">On the **Apps** bar, click **Settings** , and then click **Turn Windows features on or off**.</span></span>

3. <span data-ttu-id="f5184-131">在 [Windows 功能] 方塊中，展開 [Windows PowerShell 2.0] 節點，然後按一下 [Windows PowerShell 2.0 引擎] 方塊加以選取或清除。</span><span class="sxs-lookup"><span data-stu-id="f5184-131">In the **Windows Features** box, expand the **Windows PowerShell 2.0** node, and click the **Windows PowerShell 2.0 Engine** box to select or clear it.</span></span>

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a><span data-ttu-id="f5184-132">在 Windows Server 2012 R2 和 Windows Server 2012 上</span><span class="sxs-lookup"><span data-stu-id="f5184-132">On Windows Server 2012 R2 and Windows Server 2012</span></span>

<span data-ttu-id="f5184-133">使用下列程序來新增 Windows PowerShell 2.0 引擎和 Microsoft .NET Framework 3.5 功能。</span><span class="sxs-lookup"><span data-stu-id="f5184-133">Use the following procedures to add the Windows PowerShell 2.0 Engine and Microsoft .NET Framework 3.5 features.</span></span> <span data-ttu-id="f5184-134">Windows PowerShell 2.0 引擎至少需要 Microsoft .NET Framework 2.0.50727。</span><span class="sxs-lookup"><span data-stu-id="f5184-134">The Windows PowerShell 2.0 Engine requires Microsoft .NET Framework 2.0.50727 at a minimum.</span></span> <span data-ttu-id="f5184-135">Microsoft .NET Framework 3.5 可完成這項需求。</span><span class="sxs-lookup"><span data-stu-id="f5184-135">This requirement is fulfilled by Microsoft .NET Framework 3.5.</span></span>

#### <a name="to-add-the-net-framework-35-feature"></a><span data-ttu-id="f5184-136">新增 .NET Framework 3.5 功能</span><span class="sxs-lookup"><span data-stu-id="f5184-136">To add the .NET Framework 3.5 feature</span></span>

1. <span data-ttu-id="f5184-137">在 **[伺服器管理員]** 中，從 **[管理]** 功能表選取 **[新增角色及功能]** 。</span><span class="sxs-lookup"><span data-stu-id="f5184-137">In **Server Manager** , from the **Manage** menu, select **Add Roles and Features**.</span></span>

    <span data-ttu-id="f5184-138">或者，在 [伺服器管理員] 中，按一下 [所有伺服器]，以滑鼠右鍵按一下伺服器名稱，然後選取 [新增角色及功能]。</span><span class="sxs-lookup"><span data-stu-id="f5184-138">Or in **Server Manager** , click **All Servers** , right-click a server name, and then select  **Add Roles and Features**.</span></span>

2. <span data-ttu-id="f5184-139">在 [安裝類型] 頁面上，選取 [角色型或功能型安裝]。</span><span class="sxs-lookup"><span data-stu-id="f5184-139">On the **Installation Type** page, select **Role-based or feature-based installation**.</span></span>

3. <span data-ttu-id="f5184-140">在 **[功能]** 頁面上，展開 **[.NET 3.5 Framework 功能]** 節點，然後選取 **[.NET Framework 3.5 (包括 .NET 2.0 和 3.0)]** 。</span><span class="sxs-lookup"><span data-stu-id="f5184-140">On the **Features** page, expand the **.NET 3.5 Framework Features** node and select **.NET Framework 3.5 (includes .NET 2.0 and 3.0)**.</span></span>

   <span data-ttu-id="f5184-141">Windows PowerShell 2.0 引擎不需要該節點下方的其他選項。</span><span class="sxs-lookup"><span data-stu-id="f5184-141">The other options under that node are not required for the Windows PowerShell 2.0 Engine.</span></span>

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a><span data-ttu-id="f5184-142">新增 Windows PowerShell 2.0 引擎功能</span><span class="sxs-lookup"><span data-stu-id="f5184-142">To add the Windows PowerShell 2.0 Engine feature</span></span>

- <span data-ttu-id="f5184-143">在 **[伺服器管理員]** 中，從 **[管理]** 功能表選取 **[新增角色及功能]** 。</span><span class="sxs-lookup"><span data-stu-id="f5184-143">In **Server Manager** , from the **Manage** menu, select **Add Roles and Features**.</span></span>

  <span data-ttu-id="f5184-144">或者，在 [伺服器管理員] 中，按一下 [所有伺服器]，以滑鼠右鍵按一下伺服器名稱，然後選取 [新增角色及功能]。</span><span class="sxs-lookup"><span data-stu-id="f5184-144">Or **Server Manager** , click **All Servers** , right-click a server name, and then select **Add Roles and Features**.</span></span>

- <span data-ttu-id="f5184-145">在 [安裝類型] 頁面上，選取 [角色型或功能型安裝]。</span><span class="sxs-lookup"><span data-stu-id="f5184-145">On the **Installation Type** page, select **Role-based or feature-based installation**.</span></span>

- <span data-ttu-id="f5184-146">在 **[功能]** 頁面上，展開 **[Windows PowerShell (Installed) (Windows PowerShell (已安裝))]** 節點，然後選取 **[Windows PowerShell 2.0 引擎]** 。</span><span class="sxs-lookup"><span data-stu-id="f5184-146">On the **Features** page, expand the **Windows PowerShell (Installed)** node and select **Windows PowerShell 2.0 Engine**.</span></span>

<span data-ttu-id="f5184-147">如需啟動 Windows PowerShell 2.0 引擎的相關資訊，請參閱[啟動 Windows PowerShell 2.0 引擎](../Starting-the-Windows-PowerShell-2.0-Engine.md)。</span><span class="sxs-lookup"><span data-stu-id="f5184-147">For information about starting the Windows PowerShell 2.0 Engine, see [Starting the Windows PowerShell 2.0 Engine](../Starting-the-Windows-PowerShell-2.0-Engine.md).</span></span>

## <a name="on-earlier-systems"></a><span data-ttu-id="f5184-148">在舊版系統上</span><span class="sxs-lookup"><span data-stu-id="f5184-148">On Earlier Systems</span></span>

<span data-ttu-id="f5184-149">在 Windows 7、Windows Server 2008 R2 和 Windows Server 2012 上安裝 Windows PowerShell 4.0 的 [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) 套件會包含 Windows PowerShell 2.0 引擎。</span><span class="sxs-lookup"><span data-stu-id="f5184-149">The [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) package that installs Windows PowerShell 4.0 on Windows 7, Windows Server 2008 R2, and Windows Server 2012, includes the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="f5184-150">Windows PowerShell 2.0 引擎可視需要啟用並開始使用，而不需要額外的安裝、設定或組態。</span><span class="sxs-lookup"><span data-stu-id="f5184-150">The Windows PowerShell 2.0 Engine is enabled and ready to use, if necessary, without additional installation, setup, or configuration.</span></span>

<span data-ttu-id="f5184-151">在 Windows 7、Windows Server 2008 R2 和 Windows Server 2008 上安裝 Windows PowerShell 3.0 的 Windows Management Framework 3.0 套件會包含 Windows PowerShell 2.0 引擎。</span><span class="sxs-lookup"><span data-stu-id="f5184-151">The Windows Management Framework 3.0 package that installs Windows PowerShell 3.0 on Windows 7, Windows Server 2008 R2, and Windows Server 2008, includes the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="f5184-152">Windows PowerShell 2.0 引擎可視需要啟用並開始使用，而不需要額外的安裝、設定或組態。</span><span class="sxs-lookup"><span data-stu-id="f5184-152">The Windows PowerShell 2.0 Engine is enabled and ready to use, if necessary, without additional installation, setup, or configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5184-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5184-153">See Also</span></span>

- [<span data-ttu-id="f5184-154">Windows PowerShell 系統需求</span><span class="sxs-lookup"><span data-stu-id="f5184-154">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="f5184-155">安裝 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5184-155">Installing Windows PowerShell</span></span>](Installing-Windows-PowerShell.md)
- <span data-ttu-id="f5184-156">[啟動 Windows PowerShell](/previous-versions/ms714415(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f5184-156">[Starting Windows PowerShell](/previous-versions/ms714415(v=vs.85))</span></span>
- [<span data-ttu-id="f5184-157">啟動 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="f5184-157">Starting the Windows PowerShell 2.0 Engine</span></span>](../Starting-the-Windows-PowerShell-2.0-Engine.md)
