---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 安裝 Windows PowerShell SDK
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893533"
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="7f716-103">安裝 Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7f716-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="7f716-104">下列主題說明如何在不同版本的 Windows 上安裝 PowerShell SDK。</span><span class="sxs-lookup"><span data-stu-id="7f716-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="7f716-105">安裝適用於 Windows 8 及 Windows Server 2012 的 Windows PowerShell 3.0 SDK</span><span class="sxs-lookup"><span data-stu-id="7f716-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="7f716-106">Windows 8 及 Windows Server 2012 會自動安裝 Windows PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="7f716-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="7f716-107">您也可以下載並安裝 Windows PowerShell 3.0 的參考組件，當做 Windows 8 SDK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="7f716-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="7f716-108">這些組件可讓您撰寫 Windows PowerShell 3.0 的 Cmdlet、提供者和主機程式。</span><span class="sxs-lookup"><span data-stu-id="7f716-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="7f716-109">當您安裝適用於 Windows 8 的 Windows SDK 時，Windows PowerShell 組件會自動安裝在參考組件資料夾中 (位於 `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0` 中)。</span><span class="sxs-lookup"><span data-stu-id="7f716-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span></span>
<span data-ttu-id="7f716-110">如需詳細資訊，請參閱 [Windows 8 SDK 下載網站](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive)。</span><span class="sxs-lookup"><span data-stu-id="7f716-110">For more information, see the [Windows 8 SDK download site](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span></span>
<span data-ttu-id="7f716-111">開發中心也會提供 Windows PowerShell 程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="7f716-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="7f716-112">如需詳細資訊，請參閱[開發人員中心網站](https://code.msdn.microsoft.com:443/windowsdesktop/)的桌面程式碼範例頁面。</span><span class="sxs-lookup"><span data-stu-id="7f716-112">For more information, see the Desktop code sample page on the [Dev center site](https://code.msdn.microsoft.com:443/windowsdesktop/).</span></span>

<span data-ttu-id="7f716-113">此外，包含多個程式碼範例的 Windows PowerShell 3.0 與 Windows PowerShell 2.0 SDK 相容。</span><span class="sxs-lookup"><span data-stu-id="7f716-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="7f716-114">如需如何下載 Windows PowerShell 2.0 SDK 的詳細資訊，請參閱以下內容。</span><span class="sxs-lookup"><span data-stu-id="7f716-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="7f716-115">(請注意，雖然 2.0 程式碼範例與 Windows 8 和 Windows PowerShell 3.0 相容，但 Windows 8 平台無法安裝 Windows PowerShell 2.0。)</span><span class="sxs-lookup"><span data-stu-id="7f716-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="7f716-116">安裝適用於 Windows 7 及 Windows Server 2008 R2 的 Windows PowerShell 3.0 SDK</span><span class="sxs-lookup"><span data-stu-id="7f716-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="7f716-117">Windows 7 及 Windows Server 2008 R2 會自動安裝 PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="7f716-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="7f716-118">您也可以在這些系統上安裝 PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="7f716-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="7f716-119">(如需詳細資訊，請參閱[安裝 Windows PowerShell](Installing-Windows-PowerShell.md)。)</span><span class="sxs-lookup"><span data-stu-id="7f716-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="7f716-120">如上所述，您也可以在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows 8 SDK。</span><span class="sxs-lookup"><span data-stu-id="7f716-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="7f716-121">安裝適用於 Windows 7、Vista、XP、Server 2003 及 Server 2008 的 Windows PowerShell 2.0 SDK</span><span class="sxs-lookup"><span data-stu-id="7f716-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="7f716-122">Windows PowerShell 2.0 SDK 提供撰寫 Cmdlet、提供者和主控應用程式所需的參考組件，並提供作為開始撰寫程式碼的起點 C# 範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="7f716-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="7f716-123">若要安裝此 SDK，請參閱 [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560)。</span><span class="sxs-lookup"><span data-stu-id="7f716-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="7f716-124">參考組件</span><span class="sxs-lookup"><span data-stu-id="7f716-124">Reference assemblies</span></span>

<span data-ttu-id="7f716-125">參考組件預設會安裝在下列位置︰`c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`。</span><span class="sxs-lookup"><span data-stu-id="7f716-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> [!NOTE] 
> <span data-ttu-id="7f716-126">針對 Windows PowerShell 2.0 組件編譯的程式碼無法載入到 Windows PowerShell 1.0 安裝中。</span><span class="sxs-lookup"><span data-stu-id="7f716-126">Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
> <span data-ttu-id="7f716-127">不過，針對 Windows PowerShell 1.0 組件編譯的程式碼可以載入至 Windows PowerShell 2.0 安裝。</span><span class="sxs-lookup"><span data-stu-id="7f716-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="7f716-128">範例</span><span class="sxs-lookup"><span data-stu-id="7f716-128">Samples</span></span>

<span data-ttu-id="7f716-129">程式碼範例預設會安裝在下列位置︰`C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`。</span><span class="sxs-lookup"><span data-stu-id="7f716-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="7f716-130">以下各節提供每個範例之用途的簡要說明。</span><span class="sxs-lookup"><span data-stu-id="7f716-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="7f716-131">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="7f716-131">Cmdlet samples</span></span>

### <a name="getprocesssample01"></a><span data-ttu-id="7f716-132">GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="7f716-132">GetProcessSample01</span></span>

<span data-ttu-id="7f716-133">示範如何撰寫簡易的 Cmdlet，進而取得本機電腦上的所有處理序。</span><span class="sxs-lookup"><span data-stu-id="7f716-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

### <a name="getprocesssample02"></a><span data-ttu-id="7f716-134">GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="7f716-134">GetProcessSample02</span></span>

<span data-ttu-id="7f716-135">示範如何將參數新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7f716-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="7f716-136">此 Cmdlet 會採用一或多個處理序名稱，並傳回相符的處理序。</span><span class="sxs-lookup"><span data-stu-id="7f716-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

### <a name="getprocesssample03"></a><span data-ttu-id="7f716-137">GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="7f716-137">GetProcessSample03</span></span>

<span data-ttu-id="7f716-138">示範如何新增可自管線接受輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="7f716-138">Shows how to add parameters that accept input from the pipeline.</span></span>

### <a name="getprocesssample04"></a><span data-ttu-id="7f716-139">GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="7f716-139">GetProcessSample04</span></span>

<span data-ttu-id="7f716-140">示範如何處理非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="7f716-140">Shows how to handle nonterminating errors.</span></span>

### <a name="getprocesssample05"></a><span data-ttu-id="7f716-141">GetProcessSample05</span><span class="sxs-lookup"><span data-stu-id="7f716-141">GetProcessSample05</span></span>

<span data-ttu-id="7f716-142">示範如何顯示指定的處理序清單。</span><span class="sxs-lookup"><span data-stu-id="7f716-142">Shows how to display a list of specified processes.</span></span>

### <a name="selectobject"></a><span data-ttu-id="7f716-143">SelectObject</span><span class="sxs-lookup"><span data-stu-id="7f716-143">SelectObject</span></span>

<span data-ttu-id="7f716-144">示範如何撰寫篩選，進而僅選取特定的物件。</span><span class="sxs-lookup"><span data-stu-id="7f716-144">Shows how to write a filter to select only certain objects.</span></span>

### <a name="selectstring"></a><span data-ttu-id="7f716-145">SelectString</span><span class="sxs-lookup"><span data-stu-id="7f716-145">SelectString</span></span>

<span data-ttu-id="7f716-146">示範如何搜尋指定模式的檔案。</span><span class="sxs-lookup"><span data-stu-id="7f716-146">Shows how to search files for specified patterns.</span></span>

### <a name="stopprocesssample01"></a><span data-ttu-id="7f716-147">StopProcessSample01</span><span class="sxs-lookup"><span data-stu-id="7f716-147">StopProcessSample01</span></span>

<span data-ttu-id="7f716-148">示範如何實作 *PassThru* 參數，以及如何透過呼叫 [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) 及 [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) 方法來要求使用者意見回應。</span><span class="sxs-lookup"><span data-stu-id="7f716-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) and [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) methods.</span></span>
<span data-ttu-id="7f716-149">使用者會在想要強制 Cmdlet 傳回物件時指定 *PassThru* 參數。</span><span class="sxs-lookup"><span data-stu-id="7f716-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

### <a name="stopprocesssample02"></a><span data-ttu-id="7f716-150">StopProcessSample02</span><span class="sxs-lookup"><span data-stu-id="7f716-150">StopProcessSample02</span></span>

<span data-ttu-id="7f716-151">示範如何停止特定處理序。</span><span class="sxs-lookup"><span data-stu-id="7f716-151">Shows how to stop a specific process.</span></span>

### <a name="stopprocesssample03"></a><span data-ttu-id="7f716-152">StopProcessSample03</span><span class="sxs-lookup"><span data-stu-id="7f716-152">StopProcessSample03</span></span>

<span data-ttu-id="7f716-153">示範如何宣告參數的別名，以及如何支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="7f716-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

### <a name="stopprocesssample04"></a><span data-ttu-id="7f716-154">StopProcessSample04</span><span class="sxs-lookup"><span data-stu-id="7f716-154">StopProcessSample04</span></span>

<span data-ttu-id="7f716-155">示範如何宣告參數集 (Cmdlet 用作輸入的物件)，以及如何指定要使用的預設參數集。</span><span class="sxs-lookup"><span data-stu-id="7f716-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="7f716-156">遠端範例</span><span class="sxs-lookup"><span data-stu-id="7f716-156">Remoting samples</span></span>

### <a name="remoterunspace01"></a><span data-ttu-id="7f716-157">RemoteRunspace01</span><span class="sxs-lookup"><span data-stu-id="7f716-157">RemoteRunspace01</span></span>

<span data-ttu-id="7f716-158">示範如何建立用來建立遠端連線的遠端 Runspace。</span><span class="sxs-lookup"><span data-stu-id="7f716-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

### <a name="remoterunspacepool01"></a><span data-ttu-id="7f716-159">RemoteRunspacePool01</span><span class="sxs-lookup"><span data-stu-id="7f716-159">RemoteRunspacePool01</span></span>

<span data-ttu-id="7f716-160">示範如何建構遠端 Runspace 集區，以及如何使用此集區同時執行多個命令。</span><span class="sxs-lookup"><span data-stu-id="7f716-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

### <a name="serialization01"></a><span data-ttu-id="7f716-161">Serialization01</span><span class="sxs-lookup"><span data-stu-id="7f716-161">Serialization01</span></span>

<span data-ttu-id="7f716-162">示範如何查看現有的 .NET 類別，並確定此類別所選公用屬性的資訊會保留於序列化/還原序列化。</span><span class="sxs-lookup"><span data-stu-id="7f716-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

### <a name="serialization02"></a><span data-ttu-id="7f716-163">Serialization02</span><span class="sxs-lookup"><span data-stu-id="7f716-163">Serialization02</span></span>

<span data-ttu-id="7f716-164">示範如何查看現有的 .NET 類別，並確定此類別的執行個體資訊會在無法於類別的公用屬性中使用時，保留於序列化/還原序列化。</span><span class="sxs-lookup"><span data-stu-id="7f716-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

### <a name="serialization03"></a><span data-ttu-id="7f716-165">Serialization03</span><span class="sxs-lookup"><span data-stu-id="7f716-165">Serialization03</span></span>

<span data-ttu-id="7f716-166">示範如何查看現有的 .NET 類別，並確定此類別和衍生類別的執行個體都會還原序列化 (解除凍結) 成實際 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="7f716-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="7f716-167">事件範例</span><span class="sxs-lookup"><span data-stu-id="7f716-167">Event samples</span></span>

### <a name="event01"></a><span data-ttu-id="7f716-168">Event01</span><span class="sxs-lookup"><span data-stu-id="7f716-168">Event01</span></span>

<span data-ttu-id="7f716-169">示範如何透過衍生自 ObjectEventRegistrationBase 來建立事件註冊的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7f716-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

### <a name="event02"></a><span data-ttu-id="7f716-170">Event02</span><span class="sxs-lookup"><span data-stu-id="7f716-170">Event02</span></span>

<span data-ttu-id="7f716-171">示範如何接收遠端電腦上所產生的 Windows PowerShell 事件的通知。</span><span class="sxs-lookup"><span data-stu-id="7f716-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="7f716-172">其會使用透過 [Runspace](/dotnet/api/system.management.automation.runspaces.runspace) 類別公開的 PSEventReceived 事件。</span><span class="sxs-lookup"><span data-stu-id="7f716-172">It uses the PSEventReceived event exposed through the [Runspace](/dotnet/api/system.management.automation.runspaces.runspace) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="7f716-173">主控應用程式範例</span><span class="sxs-lookup"><span data-stu-id="7f716-173">Hosting application samples</span></span>

### <a name="runspace01"></a><span data-ttu-id="7f716-174">Runspace01</span><span class="sxs-lookup"><span data-stu-id="7f716-174">Runspace01</span></span>

<span data-ttu-id="7f716-175">示範如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 類別以同步執行 [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7f716-175">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span>
<span data-ttu-id="7f716-176">[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet 會為本機電腦上所執行的每個處理序傳回 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 物件。</span><span class="sxs-lookup"><span data-stu-id="7f716-176">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

### <a name="runspace02"></a><span data-ttu-id="7f716-177">Runspace02</span><span class="sxs-lookup"><span data-stu-id="7f716-177">Runspace02</span></span>

<span data-ttu-id="7f716-178">示範如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 類別以同步執行 [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 及 [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7f716-178">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span>
<span data-ttu-id="7f716-179">[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet 會為本機電腦上所執行的每個處理序傳回 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 物件，而 `Sort-Object` 會依據物件的 [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) 屬性排序物件。</span><span class="sxs-lookup"><span data-stu-id="7f716-179">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="7f716-180">這些命令的結果會透過使用 [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) 控制項來顯示。</span><span class="sxs-lookup"><span data-stu-id="7f716-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

### <a name="runspace03"></a><span data-ttu-id="7f716-181">Runspace03</span><span class="sxs-lookup"><span data-stu-id="7f716-181">Runspace03</span></span>

<span data-ttu-id="7f716-182">示範如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 類別以同步執行指令碼，以及如何處理非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="7f716-182">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="7f716-183">指令碼會接收處理序名稱的清單，然後擷取這些處理序。</span><span class="sxs-lookup"><span data-stu-id="7f716-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="7f716-184">指令碼的結果會顯示在主控台視窗中，包括執行指令碼時所產生的任何非終止錯誤在內。</span><span class="sxs-lookup"><span data-stu-id="7f716-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

### <a name="runspace04"></a><span data-ttu-id="7f716-185">Runspace04</span><span class="sxs-lookup"><span data-stu-id="7f716-185">Runspace04</span></span>

<span data-ttu-id="7f716-186">示範如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 類別來執行命令，以及如何捕捉執行命令時所擲回的終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="7f716-186">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="7f716-187">執行了兩個命令，而最後一個命令傳遞了無效的參數引數。</span><span class="sxs-lookup"><span data-stu-id="7f716-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="7f716-188">如此便不會傳回任何物件，且會擲回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="7f716-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

### <a name="runspace05"></a><span data-ttu-id="7f716-189">Runspace05</span><span class="sxs-lookup"><span data-stu-id="7f716-189">Runspace05</span></span>

<span data-ttu-id="7f716-190">示範如何將嵌入式管理單元新增至 [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) 物件，讓嵌入式管理單元的 Cmdlet 可在 Runspace 開啟時使用。</span><span class="sxs-lookup"><span data-stu-id="7f716-190">Shows how to add a snap-in to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="7f716-191">嵌入式管理單元提供 Get-Proc Cmdlet (由 [GetProcessSample01 範例](https://technet.microsoft.com/library/ff602028.aspx) 定義)，其透過使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 物件同步執行。</span><span class="sxs-lookup"><span data-stu-id="7f716-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace06"></a><span data-ttu-id="7f716-192">Runspace06</span><span class="sxs-lookup"><span data-stu-id="7f716-192">Runspace06</span></span>

<span data-ttu-id="7f716-193">示範如何將模組新增至 [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) 物件，使模組在 Runspace 開啟時載入。</span><span class="sxs-lookup"><span data-stu-id="7f716-193">Shows how to add a module to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="7f716-194">模組提供 Get-Proc Cmdlet (由 [GetProcessSample02 範例](https://technet.microsoft.com/library/ff602027.aspx) 定義)，其透過使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 物件同步執行。</span><span class="sxs-lookup"><span data-stu-id="7f716-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace07"></a><span data-ttu-id="7f716-195">Runspace07</span><span class="sxs-lookup"><span data-stu-id="7f716-195">Runspace07</span></span>

<span data-ttu-id="7f716-196">示範如何建立 Runspace，並使用該 Runspace 透過 [PowerShell](/dotnet/api/system.management.automation.powershell) 物件以同步執行兩個 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7f716-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace08"></a><span data-ttu-id="7f716-197">Runspace08</span><span class="sxs-lookup"><span data-stu-id="7f716-197">Runspace08</span></span>

<span data-ttu-id="7f716-198">示範如何將命令和引數新增至 [PowerShell](/dotnet/api/system.management.automation.powershell) 物件的管線，以及如何同步執行命令。</span><span class="sxs-lookup"><span data-stu-id="7f716-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the commands synchronously.</span></span>

### <a name="runspace09"></a><span data-ttu-id="7f716-199">Runspace09</span><span class="sxs-lookup"><span data-stu-id="7f716-199">Runspace09</span></span>

<span data-ttu-id="7f716-200">示範如何將指令碼新增至 [PowerShell](/dotnet/api/system.management.automation.powershell) 物件的管線，以及如何非同步地執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="7f716-200">Shows how to add a script to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="7f716-201">事件為用來處理指令碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="7f716-201">Events are used to handle the output of the script.</span></span>

### <a name="runspace10"></a><span data-ttu-id="7f716-202">Runspace10</span><span class="sxs-lookup"><span data-stu-id="7f716-202">Runspace10</span></span>

<span data-ttu-id="7f716-203">示範如何建立預設初始工作階段狀態、如何將 Cmdlet 新增至 [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate)、如何建立使用初始工作階段狀態的 Runspace，以及如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 物件執行此命令。</span><span class="sxs-lookup"><span data-stu-id="7f716-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace11"></a><span data-ttu-id="7f716-204">Runspace11</span><span class="sxs-lookup"><span data-stu-id="7f716-204">Runspace11</span></span>

<span data-ttu-id="7f716-205">示範如何使用 [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) 類別來建立 Proxy 命令，該命令會呼叫現有的 Cmdlet，但會限制可用的參數集。</span><span class="sxs-lookup"><span data-stu-id="7f716-205">Shows how to use the [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="7f716-206">Proxy 命令接著會加入用來建立受限 Runspace 的初始工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="7f716-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="7f716-207">這表示使用者只能透過 Proxy 命令使用此 Cmdlet 的功能。</span><span class="sxs-lookup"><span data-stu-id="7f716-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

### <a name="powershell01"></a><span data-ttu-id="7f716-208">PowerShell01</span><span class="sxs-lookup"><span data-stu-id="7f716-208">PowerShell01</span></span>

<span data-ttu-id="7f716-209">示範如何使用 [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) 物件建立受限的 Runspace 。</span><span class="sxs-lookup"><span data-stu-id="7f716-209">Shows how to create a constrained runspace using an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object.</span></span>

### <a name="powershell02"></a><span data-ttu-id="7f716-210">PowerShell02</span><span class="sxs-lookup"><span data-stu-id="7f716-210">PowerShell02</span></span>

<span data-ttu-id="7f716-211">示範如何使用 Runspace 集區同時執行多個命令。</span><span class="sxs-lookup"><span data-stu-id="7f716-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="7f716-212">主機範例</span><span class="sxs-lookup"><span data-stu-id="7f716-212">Host samples</span></span>

### <a name="host01"></a><span data-ttu-id="7f716-213">Host01</span><span class="sxs-lookup"><span data-stu-id="7f716-213">Host01</span></span>

<span data-ttu-id="7f716-214">示範如何實作使用自訂主機的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="7f716-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="7f716-215">在這個範例中，建立了使用自訂主機的 Runspace，然後使用 [PowerShell](/dotnet/api/system.management.automation.powershell) API 執行呼叫 "exit" 的指令碼。</span><span class="sxs-lookup"><span data-stu-id="7f716-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](/dotnet/api/system.management.automation.powershell) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="7f716-216">主應用程式會查看指令碼的輸出，並列印結果。</span><span class="sxs-lookup"><span data-stu-id="7f716-216">The host application then looks at the output of the script and prints out the results.</span></span>

### <a name="host02"></a><span data-ttu-id="7f716-217">Host02</span><span class="sxs-lookup"><span data-stu-id="7f716-217">Host02</span></span>

<span data-ttu-id="7f716-218">示範如何撰寫使用 Windows PowerShell 執行階段及自訂主機實作的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="7f716-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="7f716-219">主應用程式會將主機的文化特性設定為德文、執行 [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet，並顯示您使用 pwrsh.exe 時會看到的結果，然後以德文列印目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="7f716-219">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

### <a name="host03"></a><span data-ttu-id="7f716-220">Host03</span><span class="sxs-lookup"><span data-stu-id="7f716-220">Host03</span></span>

<span data-ttu-id="7f716-221">示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。</span><span class="sxs-lookup"><span data-stu-id="7f716-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

### <a name="host04"></a><span data-ttu-id="7f716-222">Host04</span><span class="sxs-lookup"><span data-stu-id="7f716-222">Host04</span></span>

<span data-ttu-id="7f716-223">示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。</span><span class="sxs-lookup"><span data-stu-id="7f716-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="7f716-224">這個主應用程式也支援顯示允許使用者指定多個選項的提示。</span><span class="sxs-lookup"><span data-stu-id="7f716-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

### <a name="host05"></a><span data-ttu-id="7f716-225">Host05</span><span class="sxs-lookup"><span data-stu-id="7f716-225">Host05</span></span>

<span data-ttu-id="7f716-226">示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。</span><span class="sxs-lookup"><span data-stu-id="7f716-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="7f716-227">這個主應用程式也支援使用 [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) 和 [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) Cmdlet 呼叫遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="7f716-227">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets.</span></span>

### <a name="host06"></a><span data-ttu-id="7f716-228">Host06</span><span class="sxs-lookup"><span data-stu-id="7f716-228">Host06</span></span>

<span data-ttu-id="7f716-229">示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。</span><span class="sxs-lookup"><span data-stu-id="7f716-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="7f716-230">此外，這個範例會使用權杖化工具 API 指定使用者所輸入的文字色彩。</span><span class="sxs-lookup"><span data-stu-id="7f716-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="7f716-231">提供者範例</span><span class="sxs-lookup"><span data-stu-id="7f716-231">Provider samples</span></span>

### <a name="accessdbprovidersample01"></a><span data-ttu-id="7f716-232">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="7f716-232">AccessDBProviderSample01</span></span>

<span data-ttu-id="7f716-233">示範如何宣告直接衍生自 [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) 類別的提供者類別。</span><span class="sxs-lookup"><span data-stu-id="7f716-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) class.</span></span>
<span data-ttu-id="7f716-234">包含在此僅為完整性用途。</span><span class="sxs-lookup"><span data-stu-id="7f716-234">It is included here only for completeness.</span></span>

### <a name="accessdbprovidersample02"></a><span data-ttu-id="7f716-235">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="7f716-235">AccessDBProviderSample02</span></span>

<span data-ttu-id="7f716-236">示範如何覆寫 [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) 和 [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) 方法來支援對 `New-PSDrive` 和 `Remove-PSDrive` Cmdlet 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7f716-236">Shows how to overwrite the [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) and [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span>
<span data-ttu-id="7f716-237">此範例中的提供者類別衍生自 [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) 類別。</span><span class="sxs-lookup"><span data-stu-id="7f716-237">The provider class in this sample derives from the [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) class.</span></span>

### <a name="accessdbprovidersample03"></a><span data-ttu-id="7f716-238">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="7f716-238">AccessDBProviderSample03</span></span>

<span data-ttu-id="7f716-239">示範如何覆寫 [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) 和 [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) 方法來支援對 `Get-Item` 和 `Set-Item` Cmdlet 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7f716-239">Shows how to overwrite the [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) and [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span>
<span data-ttu-id="7f716-240">此範例中的提供者類別衍生自 [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) 類別。</span><span class="sxs-lookup"><span data-stu-id="7f716-240">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample04"></a><span data-ttu-id="7f716-241">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="7f716-241">AccessDBProviderSample04</span></span>

<span data-ttu-id="7f716-242">示範如何覆寫容器方法來支援對 `Copy-Item`、`Get-ChildItem`、`New-Item` 和 `Remove-Item` Cmdlet 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7f716-242">Shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span>
<span data-ttu-id="7f716-243">當資料存放區包含容器項目時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="7f716-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="7f716-244">容器是常見父項目底下的一組子項目。</span><span class="sxs-lookup"><span data-stu-id="7f716-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="7f716-245">此範例中的提供者類別衍生自 [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) 類別。</span><span class="sxs-lookup"><span data-stu-id="7f716-245">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample05"></a><span data-ttu-id="7f716-246">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="7f716-246">AccessDBProviderSample05</span></span>

<span data-ttu-id="7f716-247">示範如何覆寫容器方法來支援對 `Move-Item` 和 `Join-Path` Cmdlet 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7f716-247">Shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span>
<span data-ttu-id="7f716-248">當使用者需要移動容器內的項目，而且資料存放區包含巢狀容器時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="7f716-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="7f716-249">此範例中的提供者類別衍生自 [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) 類別。</span><span class="sxs-lookup"><span data-stu-id="7f716-249">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample06"></a><span data-ttu-id="7f716-250">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="7f716-250">AccessDBProviderSample06</span></span>

<span data-ttu-id="7f716-251">示範如何覆寫內容方法來支援對 `Clear-Content`、`Get-Content` 和 `Set-Content` Cmdlet 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7f716-251">Shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span>
<span data-ttu-id="7f716-252">當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="7f716-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="7f716-253">此範例中的提供者類別衍生自 [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) 類別，且其會實作 [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) 介面。</span><span class="sxs-lookup"><span data-stu-id="7f716-253">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class, and it implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>