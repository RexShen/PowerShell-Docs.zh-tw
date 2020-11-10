---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-PSSnapin
ms.openlocfilehash: a21c2974fd66a9b02929752ae487c8995579b8a7
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388819"
---
# <span data-ttu-id="565ec-103">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="565ec-103">Add-PSSnapin</span></span>

## <span data-ttu-id="565ec-104">概要</span><span class="sxs-lookup"><span data-stu-id="565ec-104">SYNOPSIS</span></span>
<span data-ttu-id="565ec-105">新增一或多個 Windows PowerShell 嵌入式管理單元至目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="565ec-105">Adds one or more Windows PowerShell snap-ins to the current session.</span></span>

## <span data-ttu-id="565ec-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="565ec-106">SYNTAX</span></span>

```
Add-PSSnapin [-Name] <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="565ec-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="565ec-107">DESCRIPTION</span></span>

<span data-ttu-id="565ec-108">`Add-PSSnapin`Cmdlet 會將已註冊 Windows PowerShell 嵌入式管理單元新增至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="565ec-108">The `Add-PSSnapin` cmdlet adds registered Windows PowerShell snap-ins to the current session.</span></span> <span data-ttu-id="565ec-109">新增嵌入式管理單元之後，您就可以在目前的工作階段中使用嵌入式管理單元支援的 Cmdlet 與提供者。</span><span class="sxs-lookup"><span data-stu-id="565ec-109">After the snap-ins are added, you can use the cmdlets and providers that the snap-ins support in the current session.</span></span>

<span data-ttu-id="565ec-110">若要將嵌入式管理單元新增至所有未來的 Windows PowerShell 會話，請將 `Add-PSSnapin` 命令新增至您的 Windows PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="565ec-110">To add the snap-in to all future Windows PowerShell sessions, add an `Add-PSSnapin` command to your Windows PowerShell profile.</span></span> <span data-ttu-id="565ec-111">如需詳細資訊，請參閱 [about_Profiles](about/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="565ec-111">For more information, see [about_Profiles](about/about_Profiles.md).</span></span>

<span data-ttu-id="565ec-112">從 Windows PowerShell 3.0 開始，Windows PowerShell 中包含的核心命令已經封裝成模組。</span><span class="sxs-lookup"><span data-stu-id="565ec-112">Beginning in Windows PowerShell 3.0, the core commands that are included in Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="565ec-113">**Microsoft.PowerShell.Core** 是一個例外，它是一個嵌入式管理單元 (PSSnapin)。</span><span class="sxs-lookup"><span data-stu-id="565ec-113">The exception is **Microsoft.PowerShell.Core** , which is a snap-in (PSSnapin).</span></span>
<span data-ttu-id="565ec-114">依照預設，只會新增 **Microsoft.PowerShell.Core** 嵌入式管理單元至工作階段。</span><span class="sxs-lookup"><span data-stu-id="565ec-114">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span> <span data-ttu-id="565ec-115">模組會在第一次使用時自動匯入，而您可以使用 Import-Module Cmdlet 來匯入它們。</span><span class="sxs-lookup"><span data-stu-id="565ec-115">Modules are imported automatically on first use and you can use the Import-Module cmdlet to import them.</span></span>

## <span data-ttu-id="565ec-116">範例</span><span class="sxs-lookup"><span data-stu-id="565ec-116">EXAMPLES</span></span>

### <span data-ttu-id="565ec-117">範例1：新增嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="565ec-117">Example 1: Add snap-ins</span></span>

```powershell
PS C:\> Add-PSSnapIn -Name Microsoft.Exchange, Microsoft.Windows.AD
```

<span data-ttu-id="565ec-118">此命令會將 Microsoft Exchange 與 Active Directory 嵌入式管理單元新增至目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="565ec-118">This command adds the Microsoft Exchange and Active Directory snap-ins to the current session.</span></span>

### <span data-ttu-id="565ec-119">範例2：新增所有已註冊的嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="565ec-119">Example 2: Add all the registered snap-ins</span></span>

```powershell
PS C:\> Get-PSSnapin -Registered | Add-PSSnapin -Passthru
```

<span data-ttu-id="565ec-120">此命令會將所有已註冊的 Windows PowerShell 嵌入式管理單元新增至工作階段。</span><span class="sxs-lookup"><span data-stu-id="565ec-120">This command adds all of the registered Windows PowerShell snap-ins to the session.</span></span> <span data-ttu-id="565ec-121">它會使用 Get-PSSnapin Cmdlet 搭配 **已註冊** 的參數，以取得代表每個已註冊嵌入式管理單元的物件。管線運算子 (|) 將結果傳遞給 `Add-PSSnapin` ，以將其新增至會話。</span><span class="sxs-lookup"><span data-stu-id="565ec-121">It uses the Get-PSSnapin cmdlet with the **Registered** parameter to get objects representing each of the registered snap-ins. The pipeline operator (|) passes the result to `Add-PSSnapin`, which adds them to the session.</span></span> <span data-ttu-id="565ec-122">**PassThru** 參數會傳回代表每個新增之嵌入式管理單元的物件。</span><span class="sxs-lookup"><span data-stu-id="565ec-122">The **PassThru** parameter returns objects that represent each of the added snap-ins.</span></span>

### <span data-ttu-id="565ec-123">範例3：註冊嵌入式管理單元並加以新增</span><span class="sxs-lookup"><span data-stu-id="565ec-123">Example 3: Register a snap-in and add it</span></span>

<span data-ttu-id="565ec-124">第一個命令會取得已新增至目前會話的嵌入式管理單元，其中包含隨 Windows PowerShell 安裝的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="565ec-124">The first command gets snap-ins that have been added to the current session that include the snap-ins that are installed with Windows PowerShell.</span></span> <span data-ttu-id="565ec-125">在這個範例中，並沒有傳回 ManagementFeatures。</span><span class="sxs-lookup"><span data-stu-id="565ec-125">In this example, ManagementFeatures is not returned.</span></span> <span data-ttu-id="565ec-126">這表示它尚未新增至工作階段。</span><span class="sxs-lookup"><span data-stu-id="565ec-126">This indicates that it has not been added to the session.</span></span>

<span data-ttu-id="565ec-127">第二個命令會取得已在系統上註冊的嵌入式管理單元，其中包括已新增至會話的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="565ec-127">The second command gets snap-ins that have been registered on your system, which includes those that have already been added to the session.</span></span> <span data-ttu-id="565ec-128">它不包含隨 Windows PowerShell 安裝的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="565ec-128">It does not include the snap-ins that are installed with Windows PowerShell.</span></span> <span data-ttu-id="565ec-129">在此情況下，此命令不會傳回任何嵌入式管理單元。這表示 ManagementFeatures 嵌入式管理單元未在系統上註冊。</span><span class="sxs-lookup"><span data-stu-id="565ec-129">In this case, the command does not return any snap-ins. This indicates that the ManagementFeatures snapin has not been registered on the system.</span></span>

<span data-ttu-id="565ec-130">第三個命令會在 .NET Framework 中建立 Installutil.exe 工具路徑的別名 installutil.exe。</span><span class="sxs-lookup"><span data-stu-id="565ec-130">The third command creates an alias, installutil, for the path of the InstallUtil tool in .NET Framework.</span></span>

<span data-ttu-id="565ec-131">第四個命令會使用 Installutil.exe 工具來註冊嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="565ec-131">The fourth command uses the InstallUtil tool to register the snap-in.</span></span> <span data-ttu-id="565ec-132">此命令會指定 ManagementCmdlets.dll 的路徑，也就是嵌入式管理單元的檔案名或模組名稱。</span><span class="sxs-lookup"><span data-stu-id="565ec-132">The command specifies the path of ManagementCmdlets.dll, the filename or module name of the snap-in.</span></span>

<span data-ttu-id="565ec-133">第五個命令與第二個命令相同。</span><span class="sxs-lookup"><span data-stu-id="565ec-133">The fifth command is the same as the second command.</span></span> <span data-ttu-id="565ec-134">這一次您是使用此命令來確認 ManagementCmdlets 嵌入式管理單元已經註冊。</span><span class="sxs-lookup"><span data-stu-id="565ec-134">This time, you use it to verify that the ManagementCmdlets snap-in is registered.</span></span>

<span data-ttu-id="565ec-135">第六個命令會使用 `Add-PSSnapin` Cmdlet 將 ManagementFeatures 嵌入式管理單元新增至會話。</span><span class="sxs-lookup"><span data-stu-id="565ec-135">The sixth command uses the `Add-PSSnapin` cmdlet to add the ManagementFeatures snap-in to the session.</span></span> <span data-ttu-id="565ec-136">它會指定 ManagementFeatures 嵌入式管理單元的名稱，而不是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="565ec-136">It specifies the name of the snap-in, ManagementFeatures, not the file name.</span></span>

<span data-ttu-id="565ec-137">為了確認此嵌入式管理單元是否已新增至會話，第七個命令使用 Get-Command Cmdlet 的 **Module** 參數。</span><span class="sxs-lookup"><span data-stu-id="565ec-137">To verify that the snap-in is added to the session, the seventh command uses the **Module** parameter of the Get-Command cmdlet.</span></span> <span data-ttu-id="565ec-138">它會顯示由嵌入式管理單元或模組新增至工作階段的項目。</span><span class="sxs-lookup"><span data-stu-id="565ec-138">It displays the items that were added to the session by a snap-in or module.</span></span>

<span data-ttu-id="565ec-139">您也可以使用 Cmdlet 所傳回之物件的 **PSSnapin** 屬性， `Get-Command` 來尋找 Cmdlet 所產生的嵌入式管理單元或模組。</span><span class="sxs-lookup"><span data-stu-id="565ec-139">You can also use the **PSSnapin** property of the object that the `Get-Command` cmdlet returns to find the snap-in or module in which a cmdlet originated.</span></span> <span data-ttu-id="565ec-140">第八個命令會使用點標記法來尋找 Set-Alias Cmdlet 的 PSSnapin 屬性值。</span><span class="sxs-lookup"><span data-stu-id="565ec-140">The eighth command uses dot notation to find the value of the PSSnapin property of the Set-Alias cmdlet.</span></span>

```powershell
PS C:\> Get-PSSnapin
PS C:\> Get-PSSnapin -Registered
PS C:\> Set-Alias installutil $env:windir\Microsoft.NET\Framework\v2.0.50727\installutil.exe
PS C:\> installutil C:\Dev\Management\ManagementCmdlets.dll
PS C:\> Get-PSSnapin -Registered
PS C:\> add-pssnapin ManagementFeatures
PS C:\> Get-Command -Module ManagementFeatures
PS C:\> (Get-Command Set-Alias).pssnapin
```

<span data-ttu-id="565ec-141">此範例示範在您的系統上註冊嵌入式管理單元，然後將它們新增至您的工作階段的處理程序。</span><span class="sxs-lookup"><span data-stu-id="565ec-141">This example demonstrates the process of registering a snap-in on your system and then adding it to your session.</span></span> <span data-ttu-id="565ec-142">它會使用 ManagementFeatures，這是在名為 ManagementCmdlets.dll 的檔案中執行的虛構嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="565ec-142">It uses ManagementFeatures, a fictitious snap-in implemented in a file that is named ManagementCmdlets.dll.</span></span>

## <span data-ttu-id="565ec-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="565ec-143">PARAMETERS</span></span>

### <span data-ttu-id="565ec-144">-Name</span><span class="sxs-lookup"><span data-stu-id="565ec-144">-Name</span></span>

<span data-ttu-id="565ec-145">指定嵌入式管理單元的名稱。</span><span class="sxs-lookup"><span data-stu-id="565ec-145">Specifies the name of the snap-in.</span></span> <span data-ttu-id="565ec-146">這是名稱，而不是 AssemblyName 或 ModuleName。</span><span class="sxs-lookup"><span data-stu-id="565ec-146">This is the Name, not the AssemblyName or ModuleName.</span></span> <span data-ttu-id="565ec-147">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="565ec-147">Wildcards are permitted.</span></span>

<span data-ttu-id="565ec-148">若要尋找您系統上已註冊之嵌入式管理單元的名稱，請輸入 `Get-PSSnapin -Registered` 。</span><span class="sxs-lookup"><span data-stu-id="565ec-148">To find the names of the registered snap-ins on your system, type `Get-PSSnapin -Registered`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="565ec-149">-PassThru</span><span class="sxs-lookup"><span data-stu-id="565ec-149">-PassThru</span></span>

<span data-ttu-id="565ec-150">指出此 Cmdlet 會傳回代表每個新增之嵌入式管理單元的物件。</span><span class="sxs-lookup"><span data-stu-id="565ec-150">Indicates that this cmdlet returns an object that represents each added snap-in.</span></span> <span data-ttu-id="565ec-151">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="565ec-151">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="565ec-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="565ec-152">CommonParameters</span></span>

<span data-ttu-id="565ec-153">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="565ec-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="565ec-154">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="565ec-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="565ec-155">輸入</span><span class="sxs-lookup"><span data-stu-id="565ec-155">INPUTS</span></span>

### <span data-ttu-id="565ec-156">無</span><span class="sxs-lookup"><span data-stu-id="565ec-156">None</span></span>
<span data-ttu-id="565ec-157">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="565ec-157">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="565ec-158">輸出</span><span class="sxs-lookup"><span data-stu-id="565ec-158">OUTPUTS</span></span>

### <span data-ttu-id="565ec-159">無或 System.Management.Automation.PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="565ec-159">None or System.Management.Automation.PSSnapInInfo</span></span>

<span data-ttu-id="565ec-160">如果您指定 **PassThru** 參數，此 Cmdlet 會傳回代表嵌入式管理單元的 PSSnapInInfo 物件。</span><span class="sxs-lookup"><span data-stu-id="565ec-160">This cmdlet returns a PSSnapInInfo object that represents the snap-in if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="565ec-161">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="565ec-161">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="565ec-162">注意</span><span class="sxs-lookup"><span data-stu-id="565ec-162">NOTES</span></span>

- <span data-ttu-id="565ec-163">從 Windows PowerShell 3.0 開始，與 Windows PowerShell 一起安裝的核心命令已經封裝成模組。</span><span class="sxs-lookup"><span data-stu-id="565ec-163">Beginning in Windows PowerShell 3.0, the core commands that are installed with Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="565ec-164">在 Windows PowerShell 2.0，以及在較新版本的 Windows PowerShell 中建立舊版會話的主機程式中，核心命令會封裝在嵌入式管理單元 (PSSnapins) 中。</span><span class="sxs-lookup"><span data-stu-id="565ec-164">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of Windows PowerShell, the core commands are packaged in snap-ins (PSSnapins).</span></span> <span data-ttu-id="565ec-165">**Microsoft.PowerShell.Core** 是一個例外，它一律是一個嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="565ec-165">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="565ec-166">此外，遠端工作階段 (例如由 New-PSSession cmdlet 所啟動的遠端工作階段) 都是包含核心嵌入式管理單元的舊式工作階段。</span><span class="sxs-lookup"><span data-stu-id="565ec-166">Also, remote sessions, such as those started by the New-PSSession cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="565ec-167">如需使用核心模組建立較新樣式會話之 **CreateDefault2** 方法的詳細資訊，請參閱 [CreateDefault2 方法](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2)。</span><span class="sxs-lookup"><span data-stu-id="565ec-167">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2).</span></span>

- <span data-ttu-id="565ec-168">如需嵌入式管理單元的詳細資訊，請參閱 [about_PSSnapins](About/about_PSSnapins.md) 以及 [如何建立 Windows PowerShell 嵌入式管理](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in)單元。</span><span class="sxs-lookup"><span data-stu-id="565ec-168">For more information about snap-ins, see [about_PSSnapins](About/about_PSSnapins.md) and [How to Create a Windows PowerShell Snap-in](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in).</span></span>
- <span data-ttu-id="565ec-169">`Add-PSSnapin` 僅將嵌入式管理單元新增至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="565ec-169">`Add-PSSnapin` adds the snap-in only to the current session.</span></span> <span data-ttu-id="565ec-170">若要將嵌入式管理單元新增至所有 Windows PowerShell 工作階段，請將它新增至您的 Windows PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="565ec-170">To add the snap-in to all Windows PowerShell sessions, add it to your Windows PowerShell profile.</span></span> <span data-ttu-id="565ec-171">如需詳細資訊，請參閱 about_Profiles。</span><span class="sxs-lookup"><span data-stu-id="565ec-171">For more information, see about_Profiles.</span></span>
- <span data-ttu-id="565ec-172">您可以新增任何已使用 Microsoft .NET Framework 安裝公用程式註冊的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="565ec-172">You can add any snap-in that has been registered using the Microsoft .NET Framework install utility.</span></span> <span data-ttu-id="565ec-173">如需詳細資訊，請參閱 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="565ec-173">For more information, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>
- <span data-ttu-id="565ec-174">若要取得已在電腦上註冊的嵌入式管理單元清單，請輸入 `Get-PSSnapin -Registered` 。</span><span class="sxs-lookup"><span data-stu-id="565ec-174">To get a list of snap-ins that are registered on your computer, type `Get-PSSnapin -Registered`.</span></span>
- <span data-ttu-id="565ec-175">在新增嵌入式管理單元之前，請先檢查嵌入式管理單元的 `Add-PSSnapin` 版本，以確認它是否與 Windows PowerShell 的目前版本相容。</span><span class="sxs-lookup"><span data-stu-id="565ec-175">Before adding a snap-in, `Add-PSSnapin` checks the version of the snap-in to verify that it is compatible with the current version of Windows PowerShell.</span></span> <span data-ttu-id="565ec-176">如果嵌入式管理單元版本檢查失敗，Windows PowerShell 會回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="565ec-176">If the snap-in fails the version check, Windows PowerShell reports an error.</span></span>

## <span data-ttu-id="565ec-177">相關連結</span><span class="sxs-lookup"><span data-stu-id="565ec-177">RELATED LINKS</span></span>

[<span data-ttu-id="565ec-178">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="565ec-178">Get-PSSnapin</span></span>](Get-PSSnapin.md)

[<span data-ttu-id="565ec-179">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="565ec-179">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
