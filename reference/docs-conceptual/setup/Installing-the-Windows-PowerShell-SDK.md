---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 安裝 Windows PowerShell SDK
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 830b054c2cf2b49d935d3d96b79effa7131f6db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="03a5e-103">安裝 Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="03a5e-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="03a5e-104">下列主題說明如何在不同版本的 Windows 上安裝 PowerShell SDK。</span><span class="sxs-lookup"><span data-stu-id="03a5e-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="03a5e-105">安裝適用於 Windows 8 及 Windows Server 2012 的 Windows PowerShell 3.0 SDK</span><span class="sxs-lookup"><span data-stu-id="03a5e-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="03a5e-106">Windows 8 及 Windows Server 2012 會自動安裝 Windows PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="03a5e-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="03a5e-107">您也可以下載並安裝 Windows PowerShell 3.0 的參考組件，當做 Windows 8 SDK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="03a5e-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="03a5e-108">這些組件可讓您撰寫 Windows PowerShell 3.0 的 Cmdlet、提供者和主機程式。</span><span class="sxs-lookup"><span data-stu-id="03a5e-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="03a5e-109">當您安裝 Windows SDK for Windows 8 時，Windows PowerShell 組件會自動安裝在參考組件資料夾中：\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0。</span><span class="sxs-lookup"><span data-stu-id="03a5e-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span></span>
<span data-ttu-id="03a5e-110">如需詳細資訊，請參閱 [Windows 8 SDK 下載網站](http://msdn.microsoft.com/windows/hardware/hh852363.aspx)。</span><span class="sxs-lookup"><span data-stu-id="03a5e-110">For more information, see the [Windows 8 SDK download site](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span></span>
<span data-ttu-id="03a5e-111">開發中心也會提供 Windows PowerShell 程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="03a5e-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="03a5e-112">如需詳細資訊，請參閱[開發人員中心網站](http://code.msdn.microsoft.com/windowsdesktop/)的桌面程式碼範例頁面。</span><span class="sxs-lookup"><span data-stu-id="03a5e-112">For more information, see the Desktop code sample page on the [Dev center site](http://code.msdn.microsoft.com/windowsdesktop/).</span></span>

<span data-ttu-id="03a5e-113">此外，包含多個程式碼範例的 Windows PowerShell 3.0 與 Windows PowerShell 2.0 SDK 相容。</span><span class="sxs-lookup"><span data-stu-id="03a5e-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="03a5e-114">如需如何下載 Windows PowerShell 2.0 SDK 的詳細資訊，請參閱以下內容。</span><span class="sxs-lookup"><span data-stu-id="03a5e-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="03a5e-115">(請注意，雖然 2.0 程式碼範例與 Windows 8 和 Windows PowerShell 3.0 相容，但 Windows 8 平台無法安裝 Windows PowerShell 2.0。)</span><span class="sxs-lookup"><span data-stu-id="03a5e-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="03a5e-116">安裝適用於 Windows 7 及 Windows Server 2008 R2 的 Windows PowerShell 3.0 SDK</span><span class="sxs-lookup"><span data-stu-id="03a5e-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="03a5e-117">Windows 7 及 Windows Server 2008 R2 會自動安裝 PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="03a5e-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="03a5e-118">您也可以在這些系統上安裝 PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="03a5e-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="03a5e-119">(如需詳細資訊，請參閱[安裝 Windows PowerShell](Installing-Windows-PowerShell.md)。)</span><span class="sxs-lookup"><span data-stu-id="03a5e-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="03a5e-120">如上所述，您也可以在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows 8 SDK。</span><span class="sxs-lookup"><span data-stu-id="03a5e-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="03a5e-121">安裝適用於 Windows 7、Vista、XP、Server 2003 及 Server 2008 的 Windows PowerShell 2.0 SDK</span><span class="sxs-lookup"><span data-stu-id="03a5e-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="03a5e-122">Windows PowerShell 2.0 SDK 提供撰寫 Cmdlet、提供者和主控應用程式所需的參考組件，並提供作為開始撰寫程式碼的起點 C# 範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="03a5e-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="03a5e-123">若要安裝此 SDK，請參閱 [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611)。</span><span class="sxs-lookup"><span data-stu-id="03a5e-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="03a5e-124">參考組件</span><span class="sxs-lookup"><span data-stu-id="03a5e-124">Reference assemblies</span></span>

<span data-ttu-id="03a5e-125">參考組件預設會安裝在下列位置︰`c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`。</span><span class="sxs-lookup"><span data-stu-id="03a5e-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> <span data-ttu-id="03a5e-126">**注意**：針對 Windows PowerShell 2.0 組件編譯的程式碼無法載入 Windows PowerShell 1.0 安裝。</span><span class="sxs-lookup"><span data-stu-id="03a5e-126">**Note**: Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
><span data-ttu-id="03a5e-127">不過，針對 Windows PowerShell 1.0 組件編譯的程式碼可以載入至 Windows PowerShell 2.0 安裝。</span><span class="sxs-lookup"><span data-stu-id="03a5e-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="03a5e-128">範例</span><span class="sxs-lookup"><span data-stu-id="03a5e-128">Samples</span></span>

<span data-ttu-id="03a5e-129">程式碼範例預設會安裝在下列位置︰`C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`。</span><span class="sxs-lookup"><span data-stu-id="03a5e-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="03a5e-130">以下各節提供每個範例之用途的簡要說明。</span><span class="sxs-lookup"><span data-stu-id="03a5e-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="03a5e-131">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="03a5e-131">Cmdlet samples</span></span>
<span data-ttu-id="03a5e-132">**GetProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="03a5e-132">**GetProcessSample01**</span></span>

<span data-ttu-id="03a5e-133">示範如何撰寫簡易的 Cmdlet，進而取得本機電腦上的所有處理序。</span><span class="sxs-lookup"><span data-stu-id="03a5e-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

<span data-ttu-id="03a5e-134">**GetProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="03a5e-134">**GetProcessSample02**</span></span>

<span data-ttu-id="03a5e-135">示範如何將參數新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="03a5e-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="03a5e-136">此 Cmdlet 會採用一或多個處理序名稱，並傳回相符的處理序。</span><span class="sxs-lookup"><span data-stu-id="03a5e-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

<span data-ttu-id="03a5e-137">**GetProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="03a5e-137">**GetProcessSample03**</span></span>

<span data-ttu-id="03a5e-138">示範如何新增可自管線接受輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="03a5e-138">Shows how to add parameters that accept input from the pipeline.</span></span>

<span data-ttu-id="03a5e-139">**GetProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="03a5e-139">**GetProcessSample04**</span></span>

<span data-ttu-id="03a5e-140">示範如何處理非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="03a5e-140">Shows how to handle nonterminating errors.</span></span>

<span data-ttu-id="03a5e-141">**GetProcessSample05**</span><span class="sxs-lookup"><span data-stu-id="03a5e-141">**GetProcessSample05**</span></span>

<span data-ttu-id="03a5e-142">示範如何顯示指定的處理序清單。</span><span class="sxs-lookup"><span data-stu-id="03a5e-142">Shows how to display a list of specified processes.</span></span>

<span data-ttu-id="03a5e-143">**SelectObject**</span><span class="sxs-lookup"><span data-stu-id="03a5e-143">**SelectObject**</span></span>

<span data-ttu-id="03a5e-144">示範如何撰寫篩選，進而僅選取特定的物件。</span><span class="sxs-lookup"><span data-stu-id="03a5e-144">Shows how to write a filter to select only certain objects.</span></span>

<span data-ttu-id="03a5e-145">**SelectString**</span><span class="sxs-lookup"><span data-stu-id="03a5e-145">**SelectString**</span></span>

<span data-ttu-id="03a5e-146">示範如何搜尋指定模式的檔案。</span><span class="sxs-lookup"><span data-stu-id="03a5e-146">Shows how to search files for specified patterns.</span></span>

<span data-ttu-id="03a5e-147">**StopProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="03a5e-147">**StopProcessSample01**</span></span>

<span data-ttu-id="03a5e-148">示範如何實作 *PassThru* 參數，以及如何透過呼叫 [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) 及 [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) 方法來要求使用者意見回應。</span><span class="sxs-lookup"><span data-stu-id="03a5e-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) and [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) methods.</span></span>
<span data-ttu-id="03a5e-149">使用者會在想要強制 Cmdlet 傳回物件時指定 *PassThru* 參數。</span><span class="sxs-lookup"><span data-stu-id="03a5e-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

<span data-ttu-id="03a5e-150">**StopProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="03a5e-150">**StopProcessSample02**</span></span>

<span data-ttu-id="03a5e-151">示範如何停止特定處理序。</span><span class="sxs-lookup"><span data-stu-id="03a5e-151">Shows how to stop a specific process.</span></span>

<span data-ttu-id="03a5e-152">**StopProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="03a5e-152">**StopProcessSample03**</span></span>

<span data-ttu-id="03a5e-153">示範如何宣告參數的別名，以及如何支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="03a5e-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

<span data-ttu-id="03a5e-154">**StopProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="03a5e-154">**StopProcessSample04**</span></span>

<span data-ttu-id="03a5e-155">示範如何宣告參數集 (Cmdlet 用作輸入的物件)，以及如何指定要使用的預設參數集。</span><span class="sxs-lookup"><span data-stu-id="03a5e-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="03a5e-156">遠端範例</span><span class="sxs-lookup"><span data-stu-id="03a5e-156">Remoting samples</span></span>

<span data-ttu-id="03a5e-157">**RemoteRunspace01**</span><span class="sxs-lookup"><span data-stu-id="03a5e-157">**RemoteRunspace01**</span></span>

<span data-ttu-id="03a5e-158">示範如何建立用來建立遠端連線的遠端 Runspace。</span><span class="sxs-lookup"><span data-stu-id="03a5e-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

<span data-ttu-id="03a5e-159">**RemoteRunspacePool01**</span><span class="sxs-lookup"><span data-stu-id="03a5e-159">**RemoteRunspacePool01**</span></span>

<span data-ttu-id="03a5e-160">示範如何建構遠端 Runspace 集區，以及如何使用此集區同時執行多個命令。</span><span class="sxs-lookup"><span data-stu-id="03a5e-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

<span data-ttu-id="03a5e-161">**Serialization01**</span><span class="sxs-lookup"><span data-stu-id="03a5e-161">**Serialization01**</span></span>

<span data-ttu-id="03a5e-162">示範如何查看現有的 .NET 類別，並確定此類別所選公用屬性的資訊會保留於序列化/還原序列化。</span><span class="sxs-lookup"><span data-stu-id="03a5e-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

<span data-ttu-id="03a5e-163">**Serialization02**</span><span class="sxs-lookup"><span data-stu-id="03a5e-163">**Serialization02**</span></span>

<span data-ttu-id="03a5e-164">示範如何查看現有的 .NET 類別，並確定此類別的執行個體資訊會在無法於類別的公用屬性中使用時，保留於序列化/還原序列化。</span><span class="sxs-lookup"><span data-stu-id="03a5e-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

<span data-ttu-id="03a5e-165">**Serialization03**</span><span class="sxs-lookup"><span data-stu-id="03a5e-165">**Serialization03**</span></span>

<span data-ttu-id="03a5e-166">示範如何查看現有的 .NET 類別，並確定此類別和衍生類別的執行個體都會還原序列化 (解除凍結) 成實際 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="03a5e-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="03a5e-167">事件範例</span><span class="sxs-lookup"><span data-stu-id="03a5e-167">Event samples</span></span>

<span data-ttu-id="03a5e-168">**Event01**</span><span class="sxs-lookup"><span data-stu-id="03a5e-168">**Event01**</span></span>

<span data-ttu-id="03a5e-169">示範如何透過衍生自 ObjectEventRegistrationBase 來建立事件註冊的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="03a5e-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

<span data-ttu-id="03a5e-170">**Event02**</span><span class="sxs-lookup"><span data-stu-id="03a5e-170">**Event02**</span></span>

<span data-ttu-id="03a5e-171">示範如何接收遠端電腦上所產生的 Windows PowerShell 事件的通知。</span><span class="sxs-lookup"><span data-stu-id="03a5e-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="03a5e-172">其會使用透過 [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) 類別公開的 PSEventReceived 事件。</span><span class="sxs-lookup"><span data-stu-id="03a5e-172">It uses the PSEventReceived event exposed through the [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="03a5e-173">主控應用程式範例</span><span class="sxs-lookup"><span data-stu-id="03a5e-173">Hosting application samples</span></span>

<span data-ttu-id="03a5e-174">**Runspace01**</span><span class="sxs-lookup"><span data-stu-id="03a5e-174">**Runspace01**</span></span>

<span data-ttu-id="03a5e-175">示範如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 類別以同步執行 [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="03a5e-175">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet synchronously.</span></span>
<span data-ttu-id="03a5e-176">[Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) Cmdlet 會為本機電腦上所執行的每個處理序傳回 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 物件。</span><span class="sxs-lookup"><span data-stu-id="03a5e-176">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

<span data-ttu-id="03a5e-177">**Runspace02**</span><span class="sxs-lookup"><span data-stu-id="03a5e-177">**Runspace02**</span></span>

<span data-ttu-id="03a5e-178">示範如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 類別以同步執行 [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) 及 [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="03a5e-178">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) and [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlets synchronously.</span></span>
<span data-ttu-id="03a5e-179">[Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) Cmdlet 會為本機電腦上所執行的每個處理序傳回 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 物件，而 Sort-Object 會依據物件的 [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) 屬性排序物件。</span><span class="sxs-lookup"><span data-stu-id="03a5e-179">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the Sort-Object sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="03a5e-180">這些命令的結果會透過使用 [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) 控制項來顯示。</span><span class="sxs-lookup"><span data-stu-id="03a5e-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

<span data-ttu-id="03a5e-181">**Runspace03**</span><span class="sxs-lookup"><span data-stu-id="03a5e-181">**Runspace03**</span></span>

<span data-ttu-id="03a5e-182">示範如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 類別以同步執行指令碼，以及如何處理非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="03a5e-182">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="03a5e-183">指令碼會接收處理序名稱的清單，然後擷取這些處理序。</span><span class="sxs-lookup"><span data-stu-id="03a5e-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="03a5e-184">指令碼的結果會顯示在主控台視窗中，包括執行指令碼時所產生的任何非終止錯誤在內。</span><span class="sxs-lookup"><span data-stu-id="03a5e-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

<span data-ttu-id="03a5e-185">**Runspace04**</span><span class="sxs-lookup"><span data-stu-id="03a5e-185">**Runspace04**</span></span>

<span data-ttu-id="03a5e-186">示範如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 類別來執行命令，以及如何捕捉執行命令時所擲回的終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="03a5e-186">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="03a5e-187">執行了兩個命令，而最後一個命令傳遞了無效的參數引數。</span><span class="sxs-lookup"><span data-stu-id="03a5e-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="03a5e-188">如此便不會傳回任何物件，且會擲回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="03a5e-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

<span data-ttu-id="03a5e-189">**Runspace05**</span><span class="sxs-lookup"><span data-stu-id="03a5e-189">**Runspace05**</span></span>

<span data-ttu-id="03a5e-190">示範如何將嵌入式管理單元新增至 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) 物件，讓嵌入式管理單元的 Cmdlet 可在 Runspace 開啟時使用。</span><span class="sxs-lookup"><span data-stu-id="03a5e-190">Shows how to add a snap-in to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="03a5e-191">嵌入式管理單元提供 Get-Proc Cmdlet (由 [GetProcessSample01 範例](https://technet.microsoft.com/library/ff602028.aspx) 定義)，其透過使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 物件同步執行。</span><span class="sxs-lookup"><span data-stu-id="03a5e-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="03a5e-192">**Runspace06**</span><span class="sxs-lookup"><span data-stu-id="03a5e-192">**Runspace06**</span></span>

<span data-ttu-id="03a5e-193">示範如何將模組新增至 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) 物件，使模組在 Runspace 開啟時載入。</span><span class="sxs-lookup"><span data-stu-id="03a5e-193">Shows how to add a module to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="03a5e-194">模組提供 Get-Proc Cmdlet (由 [GetProcessSample02 範例](https://technet.microsoft.com/library/ff602027.aspx) 定義)，其透過使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 物件同步執行。</span><span class="sxs-lookup"><span data-stu-id="03a5e-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="03a5e-195">**Runspace07**</span><span class="sxs-lookup"><span data-stu-id="03a5e-195">**Runspace07**</span></span>

<span data-ttu-id="03a5e-196">示範如何建立 Runspace，並使用該 Runspace 透過 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 物件以同步執行兩個 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="03a5e-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="03a5e-197">**Runspace08**</span><span class="sxs-lookup"><span data-stu-id="03a5e-197">**Runspace08**</span></span>

<span data-ttu-id="03a5e-198">示範如何將命令和引數新增至 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 物件的管線，以及如何同步執行命令。</span><span class="sxs-lookup"><span data-stu-id="03a5e-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the commands synchronously.</span></span>

<span data-ttu-id="03a5e-199">**Runspace09**</span><span class="sxs-lookup"><span data-stu-id="03a5e-199">**Runspace09**</span></span>

<span data-ttu-id="03a5e-200">示範如何將指令碼新增至 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 物件的管線，以及如何非同步地執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="03a5e-200">Shows how to add a script to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="03a5e-201">事件為用來處理指令碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="03a5e-201">Events are used to handle the output of the script.</span></span>

<span data-ttu-id="03a5e-202">**Runspace10**</span><span class="sxs-lookup"><span data-stu-id="03a5e-202">**Runspace10**</span></span>

<span data-ttu-id="03a5e-203">示範如何建立預設初始工作階段狀態、如何將 Cmdlet 新增至 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx)、如何建立使用初始工作階段狀態的 Runspace，以及如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 物件執行此命令。</span><span class="sxs-lookup"><span data-stu-id="03a5e-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="03a5e-204">**Runspace11**</span><span class="sxs-lookup"><span data-stu-id="03a5e-204">**Runspace11**</span></span>

<span data-ttu-id="03a5e-205">示範如何使用 [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) 類別來建立 Proxy 命令，該命令會呼叫現有的 Cmdlet，但會限制可用的參數集。</span><span class="sxs-lookup"><span data-stu-id="03a5e-205">Shows how to use the [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="03a5e-206">Proxy 命令接著會加入用來建立受限 Runspace 的初始工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="03a5e-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="03a5e-207">這表示使用者只能透過 Proxy 命令使用此 Cmdlet 的功能。</span><span class="sxs-lookup"><span data-stu-id="03a5e-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

<span data-ttu-id="03a5e-208">**PowerShell01**</span><span class="sxs-lookup"><span data-stu-id="03a5e-208">**PowerShell01**</span></span>

<span data-ttu-id="03a5e-209">示範如何使用 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) 物件建立受限的 Runspace 。</span><span class="sxs-lookup"><span data-stu-id="03a5e-209">Shows how to create a constrained runspace using an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object.</span></span>

<span data-ttu-id="03a5e-210">**PowerShell02**</span><span class="sxs-lookup"><span data-stu-id="03a5e-210">**PowerShell02**</span></span>

<span data-ttu-id="03a5e-211">示範如何使用 Runspace 集區同時執行多個命令。</span><span class="sxs-lookup"><span data-stu-id="03a5e-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="03a5e-212">主機範例</span><span class="sxs-lookup"><span data-stu-id="03a5e-212">Host samples</span></span>

<span data-ttu-id="03a5e-213">**Host01**</span><span class="sxs-lookup"><span data-stu-id="03a5e-213">**Host01**</span></span>

<span data-ttu-id="03a5e-214">示範如何實作使用自訂主機的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="03a5e-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="03a5e-215">在這個範例中，建立了使用自訂主機的 Runspace，然後使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API 執行呼叫 "exit" 的指令碼。</span><span class="sxs-lookup"><span data-stu-id="03a5e-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="03a5e-216">主應用程式會查看指令碼的輸出，並列印結果。</span><span class="sxs-lookup"><span data-stu-id="03a5e-216">The host application then looks at the output of the script and prints out the results.</span></span>

<span data-ttu-id="03a5e-217">**Host02**</span><span class="sxs-lookup"><span data-stu-id="03a5e-217">**Host02**</span></span>

<span data-ttu-id="03a5e-218">示範如何撰寫使用 Windows PowerShell 執行階段及自訂主機實作的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="03a5e-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="03a5e-219">主應用程式會將主機的文化特性設定為德文、執行 [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) Cmdlet，並顯示您使用 pwrsh.exe 時會看到的結果，然後以德文列印目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="03a5e-219">The host application sets the host culture to German, runs the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

<span data-ttu-id="03a5e-220">**Host03**</span><span class="sxs-lookup"><span data-stu-id="03a5e-220">**Host03**</span></span>

<span data-ttu-id="03a5e-221">示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。</span><span class="sxs-lookup"><span data-stu-id="03a5e-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

<span data-ttu-id="03a5e-222">**Host04**</span><span class="sxs-lookup"><span data-stu-id="03a5e-222">**Host04**</span></span>

<span data-ttu-id="03a5e-223">示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。</span><span class="sxs-lookup"><span data-stu-id="03a5e-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="03a5e-224">這個主應用程式也支援顯示允許使用者指定多個選項的提示。</span><span class="sxs-lookup"><span data-stu-id="03a5e-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

<span data-ttu-id="03a5e-225">**Host05**</span><span class="sxs-lookup"><span data-stu-id="03a5e-225">**Host05**</span></span>

<span data-ttu-id="03a5e-226">示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。</span><span class="sxs-lookup"><span data-stu-id="03a5e-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="03a5e-227">這個主應用程式也支援使用 [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) 和 [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) Cmdlet 呼叫遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="03a5e-227">This host application also supports calls to remote computers by using the [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) and [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlets.</span></span>

<span data-ttu-id="03a5e-228">**Host06**</span><span class="sxs-lookup"><span data-stu-id="03a5e-228">**Host06**</span></span>

<span data-ttu-id="03a5e-229">示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。</span><span class="sxs-lookup"><span data-stu-id="03a5e-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="03a5e-230">此外，這個範例會使用權杖化工具 API 指定使用者所輸入的文字色彩。</span><span class="sxs-lookup"><span data-stu-id="03a5e-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="03a5e-231">提供者範例</span><span class="sxs-lookup"><span data-stu-id="03a5e-231">Provider samples</span></span>

<span data-ttu-id="03a5e-232">**AccessDBProviderSample01**</span><span class="sxs-lookup"><span data-stu-id="03a5e-232">**AccessDBProviderSample01**</span></span>

<span data-ttu-id="03a5e-233">示範如何宣告直接衍生自 [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) 類別的提供者類別。</span><span class="sxs-lookup"><span data-stu-id="03a5e-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) class.</span></span>
<span data-ttu-id="03a5e-234">包含在此僅為完整性用途。</span><span class="sxs-lookup"><span data-stu-id="03a5e-234">It is included here only for completeness.</span></span>

<span data-ttu-id="03a5e-235">**AccessDBProviderSample02**</span><span class="sxs-lookup"><span data-stu-id="03a5e-235">**AccessDBProviderSample02**</span></span>

<span data-ttu-id="03a5e-236">示範如何覆寫 [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) 和 [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) 方法來支援呼叫 New-PSDrive 和 Remove-PSDrive Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="03a5e-236">Shows how to overwrite the [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) and [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) methods to support calls to the New-PSDrive and Remove-PSDrive cmdlets.</span></span>
<span data-ttu-id="03a5e-237">此範例中的提供者類別衍生自 [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) 類別。</span><span class="sxs-lookup"><span data-stu-id="03a5e-237">The provider class in this sample derives from the [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) class.</span></span>

<span data-ttu-id="03a5e-238">**AccessDBProviderSample03**</span><span class="sxs-lookup"><span data-stu-id="03a5e-238">**AccessDBProviderSample03**</span></span>

<span data-ttu-id="03a5e-239">示範如何覆寫 [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) 和 [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) 方法來支援呼叫 Get-Item 和 Set-Item Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="03a5e-239">Shows how to overwrite the [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) and [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) methods to support calls to the Get-Item and Set-Item cmdlets.</span></span>
<span data-ttu-id="03a5e-240">此範例中的提供者類別衍生自 [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) 類別。</span><span class="sxs-lookup"><span data-stu-id="03a5e-240">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="03a5e-241">**AccessDBProviderSample04**</span><span class="sxs-lookup"><span data-stu-id="03a5e-241">**AccessDBProviderSample04**</span></span>

<span data-ttu-id="03a5e-242">示範如何覆寫容器方法來支援呼叫 Copy-Item、Get-ChildItem、New-Item 和 Remove-Item Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="03a5e-242">Shows how to overwrite container methods to support calls to the Copy-Item, Get-ChildItem, New-Item, and Remove-Item cmdlets.</span></span>
<span data-ttu-id="03a5e-243">當資料存放區包含容器項目時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="03a5e-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="03a5e-244">容器是常見父項目底下的一組子項目。</span><span class="sxs-lookup"><span data-stu-id="03a5e-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="03a5e-245">此範例中的提供者類別衍生自 [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) 類別。</span><span class="sxs-lookup"><span data-stu-id="03a5e-245">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="03a5e-246">**AccessDBProviderSample05**</span><span class="sxs-lookup"><span data-stu-id="03a5e-246">**AccessDBProviderSample05**</span></span>

<span data-ttu-id="03a5e-247">示範如何覆寫容器方法來支援呼叫 Move-Item 及 Join-Path Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="03a5e-247">Shows how to overwrite container methods to support calls to the Move-Item and Join-Path cmdlets.</span></span>
<span data-ttu-id="03a5e-248">當使用者需要移動容器內的項目，而且資料存放區包含巢狀容器時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="03a5e-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="03a5e-249">此範例中的提供者類別衍生自 [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) 類別。</span><span class="sxs-lookup"><span data-stu-id="03a5e-249">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="03a5e-250">**AccessDBProviderSample06**</span><span class="sxs-lookup"><span data-stu-id="03a5e-250">**AccessDBProviderSample06**</span></span>

<span data-ttu-id="03a5e-251">示範如何覆寫內容方法來支援呼叫 Clear-Content、Get-Content 及 Set-Content Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="03a5e-251">Shows how to overwrite content methods to support calls to the Clear-Content, Get-Content, and Set-Content cmdlets.</span></span>
<span data-ttu-id="03a5e-252">當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="03a5e-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="03a5e-253">此範例中的提供者類別衍生自 [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) 類別，且其會實作 [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) 介面。</span><span class="sxs-lookup"><span data-stu-id="03a5e-253">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class, and it implements the [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interface.</span></span>