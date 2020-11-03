---
description: 描述 Windows PowerShell 的嵌入式管理單元，並示範如何使用和管理它們。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSnapins
ms.openlocfilehash: cc22f8de0b9d8a55dcfa12f3b47f3852d891e67b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207619"
---
# <a name="about-pssnapins"></a><span data-ttu-id="c80f2-104">關於 PSSnapins</span><span class="sxs-lookup"><span data-stu-id="c80f2-104">About PSSnapins</span></span>

## <a name="short-description"></a><span data-ttu-id="c80f2-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="c80f2-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="c80f2-106">描述 Windows PowerShell 的嵌入式管理單元，並示範如何使用和管理它們。</span><span class="sxs-lookup"><span data-stu-id="c80f2-106">Describes  Windows PowerShell snap-ins and shows how to use and manage them.</span></span>

## <a name="long-description"></a><span data-ttu-id="c80f2-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="c80f2-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="c80f2-108">Windows PowerShell 嵌入式管理單元是包含 Windows PowerShell 提供者和或 Cmdlet 的 Microsoft .NET Framework 元件 \/ 。</span><span class="sxs-lookup"><span data-stu-id="c80f2-108">A Windows PowerShell snap-in is a Microsoft .NET Framework assembly that contains Windows PowerShell providers and\/or cmdlets.</span></span> <span data-ttu-id="c80f2-109">Windows PowerShell 包含一組基本的嵌入式管理單元，但您可以藉由新增包含您所建立之提供者和 Cmdlet 的嵌入式管理單元，來擴充 Windows PowerShell 的威力和價值。</span><span class="sxs-lookup"><span data-stu-id="c80f2-109">Windows PowerShell includes a set of basic snap-ins, but you can extend the power and value of Windows PowerShell by adding snap-ins that contain providers and cmdlets that you create or get from others.</span></span>

<span data-ttu-id="c80f2-110">當您新增嵌入式管理單元時，它所包含的 Cmdlet 和提供者可以立即在目前的會話中使用，但這項變更只會影響目前的會話。</span><span class="sxs-lookup"><span data-stu-id="c80f2-110">When you add a snap-in, the cmdlets and providers that it contains are immediately available for use in the current session, but the change affects only the current session.</span></span>

<span data-ttu-id="c80f2-111">若要將嵌入式管理單元新增至所有未來的會話，請將它儲存在您的 Windows PowerShell 設定檔中。</span><span class="sxs-lookup"><span data-stu-id="c80f2-111">To add the snap-in to all future sessions, save it in your Windows PowerShell profile.</span></span> <span data-ttu-id="c80f2-112">您也可以使用 Export-Console Cmdlet，將嵌入式管理單元名稱儲存到主控台檔案，然後在未來的會話中使用。</span><span class="sxs-lookup"><span data-stu-id="c80f2-112">You can also use the Export-Console cmdlet to save the snap-in names to a console file and then use it in future sessions.</span></span> <span data-ttu-id="c80f2-113">您甚至可以儲存多個主控台檔案，每個檔案都有一組不同的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="c80f2-113">You can even save multiple console files, each with a different set of snap-ins.</span></span>

<span data-ttu-id="c80f2-114">注意： Windows PowerShell 嵌入式管理單元 (PSSnapins) 可在 Windows PowerShell 3.0 和 Windows PowerShell 2.0 中使用。</span><span class="sxs-lookup"><span data-stu-id="c80f2-114">NOTE: Windows PowerShell snap-ins (PSSnapins) are available for use in Windows PowerShell 3.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="c80f2-115">它們可能會在後續版本中變更或無法使用。</span><span class="sxs-lookup"><span data-stu-id="c80f2-115">They might be altered or unavailable in subsequent versions.</span></span> <span data-ttu-id="c80f2-116">若要封裝 Windows PowerShell Cmdlet 和提供者，請使用模組。</span><span class="sxs-lookup"><span data-stu-id="c80f2-116">To package Windows PowerShell cmdlets and providers, use modules.</span></span> <span data-ttu-id="c80f2-117">如需建立模組並將嵌入式管理單元轉換成模組的相關資訊，請參閱 [撰寫 Windows PowerShell 模組](/powershell/scripting/developer/module/writing-a-windows-powershell-module)。</span><span class="sxs-lookup"><span data-stu-id="c80f2-117">For information about creating modules and converting snap-ins to modules, see [Writing a Windows PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

### <a name="finding-snap-ins"></a><span data-ttu-id="c80f2-118">尋找嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="c80f2-118">FINDING SNAP-INS</span></span>

<span data-ttu-id="c80f2-119">若要取得電腦上 Windows PowerShell 的嵌入式管理單元清單，請輸入：</span><span class="sxs-lookup"><span data-stu-id="c80f2-119">To get a list of the  Windows PowerShell snap-ins on your computer, type:</span></span>

```powershell
Get-PSSnapin
```

<span data-ttu-id="c80f2-120">若要取得每個 Windows PowerShell 提供者的嵌入式管理單元，請輸入：</span><span class="sxs-lookup"><span data-stu-id="c80f2-120">To get the snap-in for each  Windows PowerShell provider, type:</span></span>

```powershell
Get-PSProvider | Format-List name, pssnapin
```

<span data-ttu-id="c80f2-121">若要取得 Windows PowerShell 嵌入式管理單元中的 Cmdlet 清單，請輸入：</span><span class="sxs-lookup"><span data-stu-id="c80f2-121">To get a list of the cmdlets in a  Windows PowerShell snap-in, type:</span></span>

```powershell
Get-Command -Module <snap-in_name>
```

### <a name="installing-a-snap-in"></a><span data-ttu-id="c80f2-122">安裝嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="c80f2-122">INSTALLING A SNAP-IN</span></span>

<span data-ttu-id="c80f2-123">內建的嵌入式管理單元會在系統中註冊，並在您開始 Windows PowerShell 時新增到預設會話中。</span><span class="sxs-lookup"><span data-stu-id="c80f2-123">The built-in snap-ins are registered in the system and added to the default session when you start Windows PowerShell.</span></span> <span data-ttu-id="c80f2-124">不過，您必須註冊您建立或從其他人取得的嵌入式管理單元，然後將嵌入式管理單元新增至您的會話。</span><span class="sxs-lookup"><span data-stu-id="c80f2-124">However, you have to register snap-ins that you create or obtain from others and then add the snap-ins to your session.</span></span>

### <a name="registering-a-snap-in"></a><span data-ttu-id="c80f2-125">註冊嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="c80f2-125">REGISTERING A SNAP-IN</span></span>

<span data-ttu-id="c80f2-126">Windows PowerShell 嵌入式管理單元是以編譯成 .dll 檔案的 .NET Framework 語言撰寫的程式。</span><span class="sxs-lookup"><span data-stu-id="c80f2-126">A Windows PowerShell snap-in is a program written in a .NET Framework language that is compiled into a .dll file.</span></span> <span data-ttu-id="c80f2-127">若要在嵌入式管理單元中使用提供者和 Cmdlet，您必須先註冊嵌入式管理單元， (將它新增至登錄) 。</span><span class="sxs-lookup"><span data-stu-id="c80f2-127">To use the providers and cmdlets in a snap-in, you must first register the snap-in (add it to the registry).</span></span>

<span data-ttu-id="c80f2-128">大部分的嵌入式管理單元都包含一個安裝程式， (.exe 或 .msi 檔案) 為您註冊 .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="c80f2-128">Most snap-ins include an installation program (an .exe or .msi file) that registers the .dll file for you.</span></span> <span data-ttu-id="c80f2-129">但是，如果您以 .dll 檔案的形式接收嵌入式管理單元，您可以在系統上註冊。</span><span class="sxs-lookup"><span data-stu-id="c80f2-129">However, if you receive a snap-in as a .dll file, you can register it on your system.</span></span> <span data-ttu-id="c80f2-130">如需詳細資訊，請參閱 MSDN library 中的 [如何註冊 Cmdlet、提供者和主機應用程式](https://go.microsoft.com/fwlink/?LinkID=143619) 。</span><span class="sxs-lookup"><span data-stu-id="c80f2-130">For more information, see [How to Register Cmdlets, Providers, and Host Applications](https://go.microsoft.com/fwlink/?LinkID=143619) in the MSDN library.</span></span>

<span data-ttu-id="c80f2-131">若要取得系統上所有已註冊的嵌入式管理單元，或確認已註冊嵌入式管理單元，請輸入：</span><span class="sxs-lookup"><span data-stu-id="c80f2-131">To get all the registered snap-ins on your system or to verify that a snap-in is registered, type:</span></span>

```powershell
Get-PSSnapin -registered
```

### <a name="adding-the-snap-in-to-the-current-session"></a><span data-ttu-id="c80f2-132">將嵌入式管理單元新增至目前的會話</span><span class="sxs-lookup"><span data-stu-id="c80f2-132">ADDING THE SNAP-IN TO THE CURRENT SESSION</span></span>

<span data-ttu-id="c80f2-133">若要將已註冊的嵌入式管理單元新增至目前的會話，請使用 Add-PsSnapin Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c80f2-133">To add a registered snap-in to the current session, use the Add-PsSnapin cmdlet.</span></span> <span data-ttu-id="c80f2-134">例如，若要將 Microsoft SQL Server 嵌入式管理單元新增至會話，請輸入：</span><span class="sxs-lookup"><span data-stu-id="c80f2-134">For example, to add the Microsoft SQL Server snap-in to the session, type:</span></span>

```powershell
Add-PSSnapin sql
```

<span data-ttu-id="c80f2-135">命令完成之後，就可以在會話中使用嵌入式管理單元中的提供者和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c80f2-135">After the command is completed, the providers and cmdlets in the snap-in are available in the session.</span></span> <span data-ttu-id="c80f2-136">不過，只有在目前的會話中才能使用它們，除非您儲存它們。</span><span class="sxs-lookup"><span data-stu-id="c80f2-136">However, they are available only in the current session unless you save them.</span></span>

### <a name="saving-the-snap-ins"></a><span data-ttu-id="c80f2-137">儲存嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="c80f2-137">SAVING THE SNAP-INS</span></span>

<span data-ttu-id="c80f2-138">若要在未來的 Windows PowerShell 會話中使用嵌入式管理單元，請在 Windows PowerShell 設定檔中新增 Add-PsSnapin 命令。</span><span class="sxs-lookup"><span data-stu-id="c80f2-138">To use a snap-in in future Windows PowerShell sessions, add the Add-PsSnapin command to your Windows PowerShell profile.</span></span> <span data-ttu-id="c80f2-139">或者，將嵌入式管理單元名稱匯出到主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="c80f2-139">Or, export the snap-in names to a console file.</span></span>

<span data-ttu-id="c80f2-140">如果您將 Add-PSSnapin 命令新增至您的設定檔，它在所有未來的 Windows PowerShell 會話中都可以使用。</span><span class="sxs-lookup"><span data-stu-id="c80f2-140">If you add the Add-PSSnapin command to your profile, it is available in all future Windows PowerShell sessions.</span></span> <span data-ttu-id="c80f2-141">如果您在會話中匯出嵌入式管理單元的名稱，只有在需要嵌入式管理單元時，才能使用匯出檔案。</span><span class="sxs-lookup"><span data-stu-id="c80f2-141">If you export the names of the snap-ins in your session, you can use the export file only when you need the snap-ins.</span></span>

<span data-ttu-id="c80f2-142">若要將 Add-PsSnapin 命令新增至您的 Windows PowerShell 設定檔，請開啟您的設定檔、貼上或輸入命令，然後儲存設定檔。</span><span class="sxs-lookup"><span data-stu-id="c80f2-142">To add the Add-PsSnapin command to your Windows PowerShell profile, open your profile, paste or type the command, and then save the profile.</span></span> <span data-ttu-id="c80f2-143">如需詳細資訊，請參閱 about_Profiles。</span><span class="sxs-lookup"><span data-stu-id="c80f2-143">For more information, see about_Profiles.</span></span>

<span data-ttu-id="c80f2-144">若要將嵌入式管理單元從主控台檔案中的會話儲存 ( console01.psc1) ，請使用 Export-Console Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c80f2-144">To save the snap-ins from a session in console file (.psc1), use the Export-Console cmdlet.</span></span> <span data-ttu-id="c80f2-145">例如，若要將目前會話設定中的嵌入式管理單元儲存到目前目錄中的 Newconsole.psc1. console01.psc1 檔案，請輸入：</span><span class="sxs-lookup"><span data-stu-id="c80f2-145">For example, to save the snap-ins in the current session configuration to the NewConsole.psc1 file in the current directory, type:</span></span>

```powershell
Export-Console NewConsole
```

<span data-ttu-id="c80f2-146">如需詳細資訊，請參閱匯出主控台。</span><span class="sxs-lookup"><span data-stu-id="c80f2-146">For more information, see Export-Console.</span></span>

### <a name="opening-windows-powershell-with-a-console-file"></a><span data-ttu-id="c80f2-147">使用主控台檔案開啟 WINDOWS POWERSHELL</span><span class="sxs-lookup"><span data-stu-id="c80f2-147">OPENING WINDOWS POWERSHELL WITH A CONSOLE FILE</span></span>

<span data-ttu-id="c80f2-148">若要使用包含嵌入式管理單元的主控台檔案，請從 Cmd.exe 或另一個 Windows PowerShell 會話中的命令提示字元開始 Windows PowerShell ( # A0) 。</span><span class="sxs-lookup"><span data-stu-id="c80f2-148">To use a console file that includes the snap-in, start Windows PowerShell (PowerShell.exe) from the command prompt in Cmd.exe or in another Windows PowerShell session.</span></span> <span data-ttu-id="c80f2-149">使用 PsConsoleFile 參數來指定包含嵌入式管理單元的主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="c80f2-149">Use the PsConsoleFile parameter to specify the console file that includes the snap-in.</span></span> <span data-ttu-id="c80f2-150">例如，下列命令會使用 Newconsole.psc1. console01.psc1 主控台檔案啟動 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="c80f2-150">For example, the following command starts Windows PowerShell with the NewConsole.psc1 console file:</span></span>

```powershell
PowerShell.exe -psconsolefile NewConsole.psc1
```

<span data-ttu-id="c80f2-151">嵌入式管理單元中的提供者和 Cmdlet 現在可在會話中使用。</span><span class="sxs-lookup"><span data-stu-id="c80f2-151">The providers and cmdlets in the snapin are now available for use in the session.</span></span>

### <a name="removing-a-snap-in"></a><span data-ttu-id="c80f2-152">移除嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="c80f2-152">REMOVING A SNAP-IN</span></span>

<span data-ttu-id="c80f2-153">若要從目前的會話移除 Windows PowerShell 嵌入式管理單元，請使用 Remove-PsSnapin Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c80f2-153">To remove a Windows PowerShell snap-in from the current session, use the Remove-PsSnapin cmdlet.</span></span> <span data-ttu-id="c80f2-154">例如，若要從目前的會話移除 SQL Server 嵌入式管理單元，請輸入：</span><span class="sxs-lookup"><span data-stu-id="c80f2-154">For example, to remove the SQL Server snap-in from the current session, type:</span></span>

```powershell
Remove-PSSnapin sql
```

<span data-ttu-id="c80f2-155">此 Cmdlet 會從會話中移除嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="c80f2-155">This cmdlet removes the snap-in from the session.</span></span> <span data-ttu-id="c80f2-156">仍會載入此嵌入式管理單元，但它支援的提供者和 Cmdlet 已無法再使用。</span><span class="sxs-lookup"><span data-stu-id="c80f2-156">The snap-in is still loaded, but the providers and cmdlets that it supports are no longer available.</span></span>

### <a name="built-in-commands"></a><span data-ttu-id="c80f2-157">內建命令</span><span class="sxs-lookup"><span data-stu-id="c80f2-157">BUILT-IN COMMANDS</span></span>

<span data-ttu-id="c80f2-158">在 Windows PowerShell 2.0 和 Windows PowerShell 3.0 和更新版本中舊版的主機程式中，隨 Windows PowerShell 安裝的內建命令會封裝在自動加入至每個 Windows PowerShell 會話的嵌入式管理單元中。</span><span class="sxs-lookup"><span data-stu-id="c80f2-158">In Windows PowerShell 2.0 and in older-style host programs in Windows PowerShell 3.0 and later, the built-in commands that are installed with Windows PowerShell are packaged in snap-ins that are added automatically to every Windows PowerShell session.</span></span>

<span data-ttu-id="c80f2-159">從 Windows PowerShell 3.0 開始，在較新樣式的主機程式中（使用 >initialsessionstate. CreateDefault2 方法啟動會話的程式）--內建命令會封裝在模組中。</span><span class="sxs-lookup"><span data-stu-id="c80f2-159">Beginning in Windows PowerShell 3.0, in newer-style host programs -- those that start sessions by using the InitialSessionState.CreateDefault2 method -- the built-in commands are packaged in modules.</span></span> <span data-ttu-id="c80f2-160">例外狀況是，一律會顯示為嵌入式管理單元的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c80f2-160">The exception is Microsoft.PowerShell.Core, which always appears as a snap-in.</span></span> <span data-ttu-id="c80f2-161">核心嵌入式管理單元預設會包含在每個會話中。</span><span class="sxs-lookup"><span data-stu-id="c80f2-161">The Core snap-in is included in every session by default.</span></span> <span data-ttu-id="c80f2-162">內建模組會在第一次使用時自動載入。</span><span class="sxs-lookup"><span data-stu-id="c80f2-162">The built-in modules are loaded automatically on first-use.</span></span>

<span data-ttu-id="c80f2-163">注意：遠端會話（包括使用 New-PSSession Cmdlet 啟動的會話）是舊版的會話，其中內建的命令會封裝在嵌入式管理單元中。</span><span class="sxs-lookup"><span data-stu-id="c80f2-163">NOTE: Remote sessions, including sessions that are started by using the New-PSSession cmdlet, are older-style sessions in which the built-in commands are packaged in snap-ins.</span></span>

<span data-ttu-id="c80f2-164">下列嵌入式管理單元 (或模組) 與 Windows PowerShell 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="c80f2-164">The following snap-ins (or modules) are installed with Windows PowerShell.</span></span>

- <span data-ttu-id="c80f2-165">Microsoft. Core-包含用來管理 Windows PowerShell 基本功能的提供者和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c80f2-165">Microsoft.PowerShell.Core - Contains providers and cmdlets used to manage the basic features of Windows PowerShell.</span></span> <span data-ttu-id="c80f2-166">它包含 FileSystem、登錄、別名、環境、函式和變數提供者，以及基本 Cmdlet，例如 Get-help、Get-Command 和 Get 歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="c80f2-166">It includes the FileSystem, Registry, Alias, Environment, Function, and Variable providers and basic cmdlets like Get-Help, Get-Command, and Get-History.</span></span>

- <span data-ttu-id="c80f2-167">Microsoft. Host-包含 Windows PowerShell 主機所使用的 Cmdlet，例如 Start-Transcript 和停止文字記錄。</span><span class="sxs-lookup"><span data-stu-id="c80f2-167">Microsoft.PowerShell.Host - Contains cmdlets used by the Windows PowerShell host, such as Start-Transcript and Stop-Transcript.</span></span>

- <span data-ttu-id="c80f2-168">Microsoft. 管理-包含用來管理 Windows 功能的 Cmdlet，例如 Get-Service 和 Get-ChildItem。</span><span class="sxs-lookup"><span data-stu-id="c80f2-168">Microsoft.PowerShell.Management - Contains cmdlets such as Get-Service and Get-ChildItem that are used to manage Windows-based features.</span></span>

- <span data-ttu-id="c80f2-169">Get-authenticodesignature：包含用來管理 Windows PowerShell 安全性的憑證提供者和 Cmdlet，例如和 ConvertTo-SecureString。</span><span class="sxs-lookup"><span data-stu-id="c80f2-169">Microsoft.PowerShell.Security - Contains the Certificate provider and cmdlets used to manage Windows PowerShell security, such as Get-Acl, Get-AuthenticodeSignature, and ConvertTo-SecureString.</span></span>

- <span data-ttu-id="c80f2-170">（公用程式）包含用來操作物件和資料的 Cmdlet，例如，取得成員、寫入主機和格式清單。</span><span class="sxs-lookup"><span data-stu-id="c80f2-170">Microsoft.PowerShell.Utility - Contains cmdlets used to manipulate objects and data, such as Get-Member, Write-Host, and Format-List.</span></span>

- <span data-ttu-id="c80f2-171">WSManCredSSP：包含用來管理 Windows 遠端管理服務的 WSMan 提供者和 Cmdlet，例如 Connect-WSMan 和。</span><span class="sxs-lookup"><span data-stu-id="c80f2-171">Microsoft.WSMan.Management - Contains the WSMan provider and cmdlets that manage the Windows Remote Management service, such as Connect-WSMan and Enable-WSManCredSSP.</span></span>

## <a name="logging-snap-in-events"></a><span data-ttu-id="c80f2-172">記錄嵌入式管理單元事件</span><span class="sxs-lookup"><span data-stu-id="c80f2-172">LOGGING SNAP-IN EVENTS</span></span>

<span data-ttu-id="c80f2-173">從 Windows PowerShell 3.0 開始，您可以將模組和嵌入式管理單元的 LogPipelineExecutionDetails 屬性設定為 TRUE，以記錄 Windows PowerShell 模組和嵌入式管理單元中 Cmdlet 的執行事件。</span><span class="sxs-lookup"><span data-stu-id="c80f2-173">Beginning in Windows PowerShell 3.0, you can record execution events for the cmdlets in Windows PowerShell modules and snap-ins by setting the LogPipelineExecutionDetails property of modules and snap-ins to TRUE.</span></span> <span data-ttu-id="c80f2-174">如需詳細資訊，請參閱 [about_EventLogs](about_EventLogs.md)。</span><span class="sxs-lookup"><span data-stu-id="c80f2-174">For more information, see [about_EventLogs](about_EventLogs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c80f2-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c80f2-175">SEE ALSO</span></span>

[<span data-ttu-id="c80f2-176">新增-PsSnapin</span><span class="sxs-lookup"><span data-stu-id="c80f2-176">Add-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Add-PSSnapin)

[<span data-ttu-id="c80f2-177">PsSnapin</span><span class="sxs-lookup"><span data-stu-id="c80f2-177">Get-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSnapin)

[<span data-ttu-id="c80f2-178">移除-PsSnapin</span><span class="sxs-lookup"><span data-stu-id="c80f2-178">Remove-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSnapin)

[<span data-ttu-id="c80f2-179">Export-Console</span><span class="sxs-lookup"><span data-stu-id="c80f2-179">Export-Console</span></span>](xref:Microsoft.PowerShell.Core.Export-Console)

[<span data-ttu-id="c80f2-180">Get-Command</span><span class="sxs-lookup"><span data-stu-id="c80f2-180">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)

[<span data-ttu-id="c80f2-181">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="c80f2-181">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="c80f2-182">about_Modules</span><span class="sxs-lookup"><span data-stu-id="c80f2-182">about_Modules</span></span>](about_Modules.md)

## <a name="keywords"></a><span data-ttu-id="c80f2-183">關鍵 字</span><span class="sxs-lookup"><span data-stu-id="c80f2-183">KEYWORDS</span></span>

<span data-ttu-id="c80f2-184">about_Snapins、about_Snap_ins、about_Snap 宏</span><span class="sxs-lookup"><span data-stu-id="c80f2-184">about_Snapins, about_Snap_ins, about_Snap-ins</span></span>
