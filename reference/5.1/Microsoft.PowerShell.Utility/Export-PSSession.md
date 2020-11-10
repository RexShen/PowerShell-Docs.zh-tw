---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-PSSession
ms.openlocfilehash: 11533a9b127dc6d088258392c0e142bfbe5c070c
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388020"
---
# <span data-ttu-id="7bfa9-103">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="7bfa9-103">Export-PSSession</span></span>

## <span data-ttu-id="7bfa9-104">概要</span><span class="sxs-lookup"><span data-stu-id="7bfa9-104">SYNOPSIS</span></span>

<span data-ttu-id="7bfa9-105">從另一個會話匯出命令，並將其儲存在 PowerShell 模組中。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-105">Exports commands from another session and saves them in a PowerShell module.</span></span>

## <span data-ttu-id="7bfa9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7bfa9-106">SYNTAX</span></span>

```
Export-PSSession [-Session] <PSSession> [-OutputModule] <string> [[-CommandName] <string[]>]
 [[-FormatTypeName] <string[]>] [-Force] [-Encoding <string>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <string[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-Certificate <X509Certificate2>]
 [<CommonParameters>]
```

## <span data-ttu-id="7bfa9-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7bfa9-107">DESCRIPTION</span></span>

<span data-ttu-id="7bfa9-108">`Export-PSSession`Cmdlet 會從另一個 powershell 會話取得 Cmdlet、函式、別名和其他命令類型 (PSSession) 在本機或遠端電腦上，並將它們儲存在 PowerShell 模組中。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-108">The `Export-PSSession` cmdlet gets cmdlets, functions, aliases, and other command types from another PowerShell session (PSSession) on a local or remote computer and saves them in a PowerShell module.</span></span> <span data-ttu-id="7bfa9-109">若要將模組中的命令新增至目前的會話，請使用 `Import-Module` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-109">To add the commands from the module to the current session, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="7bfa9-110">不同于 `Import-PSSession` 從另一個 PSSession 將命令匯入目前會話的，會 `Export-PSSession` 將命令儲存在模組中。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-110">Unlike `Import-PSSession`, which imports commands from another PSSession into the current session, `Export-PSSession` saves the commands in a module.</span></span> <span data-ttu-id="7bfa9-111">這些命令不會匯入目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-111">The commands are not imported into the current session.</span></span>

<span data-ttu-id="7bfa9-112">若要匯出命令，請使用指令 `New-PSSession` 程式來建立具有您想要匯出之命令的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-112">To export commands, use the `New-PSSession` cmdlet to create a PSSession that has the commands that you want to export.</span></span> <span data-ttu-id="7bfa9-113">然後使用 `Export-PSSession` Cmdlet 來匯出命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-113">Then use the `Export-PSSession` cmdlet to export the commands.</span></span>

<span data-ttu-id="7bfa9-114">為了防止命令名稱衝突，的預設值 `Export-PSSession` 是匯出所有命令，但目前會話中有命令除外。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-114">To prevent command name conflicts, the default for `Export-PSSession` is to export all commands, except for commands that exist in the current session.</span></span> <span data-ttu-id="7bfa9-115">您可以使用 **CommandName** 參數來指定要匯出的命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-115">You can use the **CommandName** parameter to specify the commands to export.</span></span>

<span data-ttu-id="7bfa9-116">此 `Export-PSSession` Cmdlet 會使用 PowerShell 的隱含遠端功能。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-116">The `Export-PSSession` cmdlet uses the implicit remoting feature of PowerShell.</span></span> <span data-ttu-id="7bfa9-117">當您將命令匯入目前的會話時，它們會以隱含方式在原始會話中或在來源電腦上類似的會話中執行。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-117">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

## <span data-ttu-id="7bfa9-118">範例</span><span class="sxs-lookup"><span data-stu-id="7bfa9-118">EXAMPLES</span></span>

### <span data-ttu-id="7bfa9-119">範例1：從 PSSession 匯出命令</span><span class="sxs-lookup"><span data-stu-id="7bfa9-119">Example 1: Export commands from a PSSession</span></span>

<span data-ttu-id="7bfa9-120">此範例會從本機電腦建立新的 PSSession 至 Server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-120">This example creates a new PSSession from the local computer to the Server01 computer.</span></span> <span data-ttu-id="7bfa9-121">除了存在於目前會話中的所有命令，都會匯出至本機電腦上名為 Server01 的模組。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-121">All of the commands, except those that exist in the current session, are exported to the module named Server01 on the local computer.</span></span> <span data-ttu-id="7bfa9-122">匯出包含命令的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-122">The export includes the formatting data for the commands.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Export-PSSession -Session $S -OutputModule Server01
```

<span data-ttu-id="7bfa9-123">此 `New-PSSession` 命令會在 Server01 電腦上建立 PSSession。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-123">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span> <span data-ttu-id="7bfa9-124">PSSession 會儲存在變數中 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-124">The PSSession is stored in the `$S` variable.</span></span> <span data-ttu-id="7bfa9-125">此 `Export-PSSession` 命令會匯出 `$S` 變數的命令，並將資料格式化為 Server01 模組。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-125">The `Export-PSSession` command exports the `$S` variable's commands and formatting data into the Server01 module.</span></span>

### <span data-ttu-id="7bfa9-126">範例2：匯出 Get 和 Set 命令</span><span class="sxs-lookup"><span data-stu-id="7bfa9-126">Example 2: Export the Get and Set commands</span></span>

<span data-ttu-id="7bfa9-127">此範例會 `Get` 從伺服器匯出所有和 `Set` 命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-127">This example exports all of the `Get` and `Set` commands from a server.</span></span>

```powershell
$S = New-PSSession -ConnectionUri https://exchange.microsoft.com/mailbox -Credential exchangeadmin01@hotmail.com -Authentication Negotiate
Export-PSSession -Session $S -Module exch* -CommandName Get-*, Set-* -FormatTypeName * -OutputModule $PSHOME\Modules\Exchange -Encoding ASCII
```

<span data-ttu-id="7bfa9-128">這些命令會將 `Get` 和 `Set` 命令從遠端電腦上的 Microsoft exchange Server 嵌入式管理單元，匯出到本機電腦上目錄中的 Exchange 模組 `$PSHOME\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-128">These commands export the `Get` and `Set` commands from a Microsoft Exchange Server snap-in on a remote computer to an Exchange module in the `$PSHOME\Modules` directory on the local computer.</span></span>
<span data-ttu-id="7bfa9-129">將模組放在目錄中，可供 `$PSHOME\Modules` 電腦的所有使用者存取。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-129">Placing the module in the `$PSHOME\Modules` directory makes it accessible to all users of the computer.</span></span>

### <span data-ttu-id="7bfa9-130">範例3：從遠端電腦匯出命令</span><span class="sxs-lookup"><span data-stu-id="7bfa9-130">Example 3: Export commands from a remote computer</span></span>

<span data-ttu-id="7bfa9-131">此範例會從遠端電腦上的 PSSession 匯出 Cmdlet，並將它們儲存在本機電腦上的模組中。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-131">This example exports cmdlets from a PSSession on a remote computer and saves them in a module on the local computer.</span></span> <span data-ttu-id="7bfa9-132">模組中的 Cmdlet 會新增至目前的會話，讓您可以使用它們。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-132">The cmdlets from the module are added to the current session so that they can be used.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01 -Credential Server01\User01
Export-PSSession -Session $S -OutputModule TestCmdlets -Type Cmdlet -CommandName *test* -FormatTypeName *
Remove-PSSession $S
Import-Module TestCmdlets
Get-Help Test*
Test-Files
```

<span data-ttu-id="7bfa9-133">此 `New-PSSession` 命令會在 Server01 電腦上建立 PSSession，並將它儲存在 `$S` 變數中。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-133">The `New-PSSession` command creates a PSSession on the Server01 computer and saves it in the `$S` variable.</span></span> <span data-ttu-id="7bfa9-134">此 `Export-PSSession` 命令會將名稱開頭為 Test 的 Cmdlet，從的 PSSession 匯出 `$S` 到本機電腦上的 TestCmdlets 模組。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-134">The `Export-PSSession` command exports the cmdlets whose names begin with Test from the PSSession in `$S` to the TestCmdlets module on the local computer.</span></span>

<span data-ttu-id="7bfa9-135">`Remove-PSSession`Cmdlet 會刪除目前會話中的 PSSession `$S` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-135">The `Remove-PSSession` cmdlet deletes the PSSession in `$S` from the current session.</span></span> <span data-ttu-id="7bfa9-136">此命令顯示 PSSession 不需要使用中，即可使用從會話匯入的命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-136">This command shows that the PSSession need not be active to use the commands that were imported from the session.</span></span> <span data-ttu-id="7bfa9-137">`Import-Module`Cmdlet 會將 TestCmdlets 模組中的 Cmdlet 新增到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-137">The `Import-Module` cmdlet adds the cmdlets in the TestCmdlets module to the current session.</span></span> <span data-ttu-id="7bfa9-138">您可以隨時在任何會話中執行此命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-138">The command can be run in any session at any time.</span></span>

<span data-ttu-id="7bfa9-139">`Get-Help`Cmdlet 會取得名稱開頭為 Test 之 Cmdlet 的說明。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-139">The `Get-Help` cmdlet gets help for cmdlets whose names begin with Test.</span></span> <span data-ttu-id="7bfa9-140">將模組中的命令新增至目前的會話之後，您可以使用 `Get-Help` 和 `Get-Command` Cmdlet 來瞭解匯入的命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-140">After the commands in a module are added to the current session, you can use the `Get-Help` and `Get-Command` cmdlets to learn about the imported commands.</span></span> <span data-ttu-id="7bfa9-141">`Test-Files`Cmdlet 是從 Server01 電腦匯出，並新增至會話。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-141">The `Test-Files` cmdlet was exported from the Server01 computer and added to the session.</span></span> <span data-ttu-id="7bfa9-142">此 `Test-Files` Cmdlet 會在匯入命令的電腦上的遠端會話中執行。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-142">The `Test-Files` cmdlet runs in a remote session on the computer from which the command was imported.</span></span> <span data-ttu-id="7bfa9-143">PowerShell 會從儲存在 TestCmdlets 模組中的資訊建立會話。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-143">PowerShell creates a session from information that is stored in the TestCmdlets module.</span></span>

### <span data-ttu-id="7bfa9-144">範例4：在目前的會話中匯出和 clobber 命令</span><span class="sxs-lookup"><span data-stu-id="7bfa9-144">Example 4: Export and clobber commands in the current session</span></span>

<span data-ttu-id="7bfa9-145">此範例會將儲存在變數中的命令匯出到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-145">This example exports commands that are stored in a variable into the current session.</span></span>

```powershell
Export-PSSession -Session $S -AllowClobber -OutputModule AllCommands
```

<span data-ttu-id="7bfa9-146">此 `Export-PSSession` 命令會將所有命令和所有格式設定資料從變數中的 PSSession 匯出 `$S` 到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-146">This `Export-PSSession` command exports all commands and all formatting data from the PSSession in the `$S` variable into the current session.</span></span> <span data-ttu-id="7bfa9-147">**AllowClobber** 參數包含與目前會話中的命令具有相同名稱的命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-147">The **AllowClobber** parameter includes commands with the same names as commands in the current session.</span></span>

### <span data-ttu-id="7bfa9-148">範例5：從封閉式 PSSession 匯出命令</span><span class="sxs-lookup"><span data-stu-id="7bfa9-148">Example 5: Export commands from a closed PSSession</span></span>

<span data-ttu-id="7bfa9-149">此範例示範如何在建立匯出命令的 PSSession 關閉時，以特殊選項執行匯出的命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-149">This example shows how to run the exported commands with special options when the PSSession that created the exported commands is closed.</span></span>

<span data-ttu-id="7bfa9-150">當匯入模組時，如果原始遠端會話已關閉，此模組將會使用任何連接到原始電腦的開啟遠端會話。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-150">If the original remote session is closed when a module is imported, the module will use any open remote session that connects to the originating computer.</span></span> <span data-ttu-id="7bfa9-151">如果來源電腦沒有目前的會話，模組將會重新建立會話。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-151">If there is no current session to the originating computer, the module will reestablish a session.</span></span>

<span data-ttu-id="7bfa9-152">若要在遠端會話中使用特殊選項來執行匯出的命令，您必須先建立具有這些選項的遠端會話，然後再匯入模組。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-152">To run exported commands with special options in a remote session, you must create a remote session with those options before you import the module.</span></span> <span data-ttu-id="7bfa9-153">使用 `New-PSSession` Cmdlet 搭配 **SessionOption** 參數</span><span class="sxs-lookup"><span data-stu-id="7bfa9-153">Use the `New-PSSession` cmdlet with the **SessionOption** parameter</span></span>

```powershell
$Options = New-PSSessionOption -NoMachineProfile
$S = New-PSSession -ComputerName Server01 -SessionOption $Options
Export-PSSession -Session $S -OutputModule Server01
Remove-PSSession $S
New-PSSession -ComputerName Server01 -SessionOption $Options
Import-Module Server01
```

<span data-ttu-id="7bfa9-154">此 `New-PSSessionOption` Cmdlet 會建立 **PSSessionOption** 物件，並將物件儲存在變數中 `$Options` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-154">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object, and it saves the object in the `$Options` variable.</span></span> <span data-ttu-id="7bfa9-155">此 `New-PSSession` 命令會在 Server01 電腦上建立 PSSession。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-155">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span>
<span data-ttu-id="7bfa9-156">**SessionOption** 參數會使用中儲存的物件 `$Options` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-156">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="7bfa9-157">會話會儲存在變數中 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-157">The session is stored in the `$S` variable.</span></span>

<span data-ttu-id="7bfa9-158">此 `Export-PSSession` Cmdlet 會將來自 PSSession 的命令匯出 `$S` 至 Server01 模組。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-158">The `Export-PSSession` cmdlet exports commands from the PSSession in `$S` to the Server01 module.</span></span>
<span data-ttu-id="7bfa9-159">此 `Remove-PSSession` Cmdlet 會刪除變數中的 PSSession `$S` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-159">The `Remove-PSSession` cmdlet deletes the PSSession in the `$S` variable.</span></span>

<span data-ttu-id="7bfa9-160">此 `New-PSSession` Cmdlet 會建立連接到 Server01 電腦的新 PSSession。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-160">The `New-PSSession` cmdlet creates a new PSSession that connects to the Server01 computer.</span></span> <span data-ttu-id="7bfa9-161">**SessionOption** 參數會使用中儲存的物件 `$Options` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-161">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="7bfa9-162">`Import-Module`Cmdlet 會從 Server01 模組匯入命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-162">The `Import-Module` cmdlet imports the commands from the Server01 module.</span></span> <span data-ttu-id="7bfa9-163">模組中的命令會在 Server01 電腦上的 PSSession 中執行。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-163">The commands in the module are run in the PSSession on the Server01 computer.</span></span>

## <span data-ttu-id="7bfa9-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7bfa9-164">PARAMETERS</span></span>

### <span data-ttu-id="7bfa9-165">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="7bfa9-165">-AllowClobber</span></span>

<span data-ttu-id="7bfa9-166">匯出指定的命令，即使它們的名稱與目前工作階段中的命令相同。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-166">Exports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="7bfa9-167">如果您匯出的命令與目前會話中的命令名稱相同，則匯出的命令會隱藏或取代原始命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-167">If you export a command with the same name as a command in the current session, the exported command hides or replaces the original commands.</span></span> <span data-ttu-id="7bfa9-168">如需詳細資訊，請參閱 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-168">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>

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

### <span data-ttu-id="7bfa9-169">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="7bfa9-169">-ArgumentList</span></span>

<span data-ttu-id="7bfa9-170">匯出因使用指定的引數 (參數值) 而產生之命令的變體。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-170">Exports the variant of the command that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="7bfa9-171">例如，若要匯出憑證中的命令變異數 `Get-Item` (Cert： ) 磁片磁碟機中的 PSSession `$S` ，請輸入 `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-171">For example, to export the variant of the `Get-Item` command in the certificate (Cert:) drive in the PSSession in `$S`, type `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bfa9-172">-Certificate</span><span class="sxs-lookup"><span data-stu-id="7bfa9-172">-Certificate</span></span>

<span data-ttu-id="7bfa9-173">指定用來簽署格式檔案 ( \* .Format.ps1xml) 或腳本模組檔案的用戶端憑證 (. .psm1) 在建立的模組中。 `Export-PSSession`</span><span class="sxs-lookup"><span data-stu-id="7bfa9-173">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the module that `Export-PSSession` creates.</span></span> <span data-ttu-id="7bfa9-174">輸入包含憑證的變數，或可取得憑證的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-174">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="7bfa9-175">若要尋找憑證，請使用 `Get-PfxCertificate` Cmdlet 或使用 `Get-ChildItem` 憑證 (Cert： ) 磁片磁碟機中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-175">To find a certificate, use the `Get-PfxCertificate` cmdlet or use the `Get-ChildItem` cmdlet in the Certificate (Cert:) drive.</span></span> <span data-ttu-id="7bfa9-176">若憑證無效或權限不足，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-176">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bfa9-177">-CommandName</span><span class="sxs-lookup"><span data-stu-id="7bfa9-177">-CommandName</span></span>

<span data-ttu-id="7bfa9-178">只匯出具有指定的名稱或名稱模式的命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-178">Exports only the commands with the specified names or name patterns.</span></span> <span data-ttu-id="7bfa9-179">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-179">Wildcards are permitted.</span></span> <span data-ttu-id="7bfa9-180">使用 **CommandName** 或其別名 **Name** 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-180">Use **CommandName** or its alias, **Name**.</span></span>

<span data-ttu-id="7bfa9-181">根據預設， `Export-PSSession` 會從 PSSession 匯出所有命令，但與目前會話中的命令具有相同名稱的命令除外。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-181">By default, `Export-PSSession` exports all commands from the PSSession except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="7bfa9-182">這可防止在目前會話中隱藏或取代命令的命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-182">This prevents commands from being hidden or replaced by commands in the current session.</span></span> <span data-ttu-id="7bfa9-183">若要匯出所有命令，甚至是隱藏或取代其他命令的命令，請使用 **AllowClobber** 參數。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-183">To export all commands, even those that hide or replace other commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="7bfa9-184">如果您使用 **CommandName** 參數，除非您使用 **FormatTypeName** 參數，否則不會匯出命令的格式設定檔案。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-184">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span> <span data-ttu-id="7bfa9-185">同樣地，如果您使用 **FormatTypeName** 參數，除非您使用 **CommandName** 參數，否則不會匯出任何命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-185">Similarly, if you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7bfa9-186">-CommandType</span><span class="sxs-lookup"><span data-stu-id="7bfa9-186">-CommandType</span></span>

<span data-ttu-id="7bfa9-187">只匯出指定類型的命令物件。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-187">Exports only the specified types of command objects.</span></span> <span data-ttu-id="7bfa9-188">使用 **CommandType** 或它的別名 **Type** 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-188">Use **CommandType** or its alias, **Type**.</span></span>

<span data-ttu-id="7bfa9-189">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="7bfa9-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="7bfa9-190">別名。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-190">Alias.</span></span> <span data-ttu-id="7bfa9-191">目前會話中的所有 PowerShell 別名。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-191">All PowerShell aliases in the current session.</span></span>
- <span data-ttu-id="7bfa9-192">全部。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-192">All.</span></span> <span data-ttu-id="7bfa9-193">所有命令類型。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-193">All command types.</span></span> <span data-ttu-id="7bfa9-194">這相當於 `Get-Command -Name *` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-194">It is the equivalent of `Get-Command -Name *`.</span></span>
- <span data-ttu-id="7bfa9-195">應用程式。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-195">Application.</span></span> <span data-ttu-id="7bfa9-196">Path 環境變數所列路徑中的 PowerShell 檔案以外的所有檔案 (`$env:path`) ，包括 .txt、.exe 和 .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-196">All files other than PowerShell files in paths listed in the Path environment variable (`$env:path`), including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="7bfa9-197">Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-197">Cmdlet.</span></span> <span data-ttu-id="7bfa9-198">目前工作階段中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-198">The cmdlets in the current session.</span></span> <span data-ttu-id="7bfa9-199">Cmdlet 是預設值。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-199">Cmdlet is the default.</span></span>
- <span data-ttu-id="7bfa9-200">設定。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-200">Configuration.</span></span> <span data-ttu-id="7bfa9-201">PowerShell 設定。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-201">A PowerShell configuration.</span></span> <span data-ttu-id="7bfa9-202">如需詳細資訊，請參閱 [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-202">For more information, see [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span></span>
- <span data-ttu-id="7bfa9-203">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="7bfa9-203">ExternalScript.</span></span> <span data-ttu-id="7bfa9-204">Path 環境變數所列路徑中的所有 ps1 檔案都 (`$env:path`) 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-204">All .ps1 files in the paths listed in the Path environment variable (`$env:path`).</span></span>
- <span data-ttu-id="7bfa9-205">篩選和函數。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-205">Filter and Function.</span></span> <span data-ttu-id="7bfa9-206">所有 PowerShell 函數。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-206">All PowerShell functions.</span></span>
- <span data-ttu-id="7bfa9-207">指令碼：</span><span class="sxs-lookup"><span data-stu-id="7bfa9-207">Script.</span></span> <span data-ttu-id="7bfa9-208">目前工作階段中的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-208">Script blocks in the current session.</span></span>
- <span data-ttu-id="7bfa9-209">流程。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-209">Workflow.</span></span> <span data-ttu-id="7bfa9-210">PowerShell 工作流程。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-210">A PowerShell workflow.</span></span> <span data-ttu-id="7bfa9-211">如需詳細資訊，請參閱 [about_Workflows](../PSWorkflow/About/about_Workflows.md)。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-211">For more information, see [about_Workflows](../PSWorkflow/About/about_Workflows.md).</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, All, Application, Cmdlet, Configuration, ExternalScript, Filter, Function, Script, Workflow

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bfa9-212">-Encoding</span><span class="sxs-lookup"><span data-stu-id="7bfa9-212">-Encoding</span></span>

<span data-ttu-id="7bfa9-213">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-213">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="7bfa9-214">預設值是 `UTF8`。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-214">The default value is `UTF8`.</span></span>

<span data-ttu-id="7bfa9-215">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="7bfa9-215">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="7bfa9-216">`ASCII` 使用 ASCII (7 位) 字元集。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-216">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="7bfa9-217">`BigEndianUnicode` 以位元組由大到小的順序使用 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-217">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="7bfa9-218">`Default` 使用對應至系統使用中字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-218">`Default` Uses the encoding that corresponds to the system's active code page.</span></span>
- <span data-ttu-id="7bfa9-219">`OEM` 使用對應至系統目前 OEM 字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-219">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="7bfa9-220">`Unicode` 使用 UTF-16 和位元組由小到小的位元組順序。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-220">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="7bfa9-221">`UTF7` 使用 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-221">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="7bfa9-222">`UTF8` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-222">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="7bfa9-223">`UTF32` 以位元組由小到大的位元組順序使用 UTF-32。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-223">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: UTF8
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bfa9-224">-Force</span><span class="sxs-lookup"><span data-stu-id="7bfa9-224">-Force</span></span>

<span data-ttu-id="7bfa9-225">即使一或多個現有的輸出檔案具有唯讀屬性，仍覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-225">Overwrites one or more existing output files, even if the file has the read-only attribute.</span></span>

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

### <span data-ttu-id="7bfa9-226">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="7bfa9-226">-FormatTypeName</span></span>

<span data-ttu-id="7bfa9-227">只匯出指定之 Microsoft .NET Framework 類型的格式設定指示。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-227">Exports formatting instructions only for the specified Microsoft .NET Framework types.</span></span> <span data-ttu-id="7bfa9-228">輸入類型名稱。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-228">Enter the type names.</span></span> <span data-ttu-id="7bfa9-229">根據預設， `Export-PSSession` 會針對不在 **System. Management. Automation** 命名空間中的所有 .NET Framework 類型，匯出格式設定指示。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-229">By default, `Export-PSSession` exports formatting instructions for all .NET Framework types that are not in the **System.Management.Automation** namespace.</span></span>

<span data-ttu-id="7bfa9-230">此參數的值必須是要從中匯 `Get-FormatData` 入命令之來源會話中的命令所傳回之類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-230">The value of this parameter must be the name of a type that is returned by a `Get-FormatData` command in the session from which the commands are being imported.</span></span> <span data-ttu-id="7bfa9-231">若要取得遠端會話中的所有格式設定資料，請輸入 `*` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-231">To get all of the formatting data in the remote session, type `*`.</span></span>

<span data-ttu-id="7bfa9-232">如果您使用 **FormatTypeName** 參數，除非您使用 **CommandName** 參數，否則不會匯出任何命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-232">If you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

<span data-ttu-id="7bfa9-233">如果您使用 **CommandName** 參數，除非您使用 **FormatTypeName** 參數，否則不會匯出命令的格式設定檔案。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-233">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bfa9-234">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="7bfa9-234">-FullyQualifiedModule</span></span>

<span data-ttu-id="7bfa9-235">指定以 **ModuleSpecification** 物件形式指定之名稱的模組。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-235">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span> <span data-ttu-id="7bfa9-236">請參閱 [ModuleSpecification (雜湊表) ](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)的「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-236">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="7bfa9-237">例如， **FullyQualifiedModule** 參數會接受以下列其中一種格式指定的模組名稱：</span><span class="sxs-lookup"><span data-stu-id="7bfa9-237">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="7bfa9-238">**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-238">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="7bfa9-239">您無法在與 **模組** 參數相同的命令中指定 **FullyQualifiedModule** 參數。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-239">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="7bfa9-240">這兩個參數是互斥的。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-240">the two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bfa9-241">-Module</span><span class="sxs-lookup"><span data-stu-id="7bfa9-241">-Module</span></span>

<span data-ttu-id="7bfa9-242">只匯出指定 PowerShell 嵌入式管理單元和模組中的命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-242">Exports only the commands in the specified PowerShell snap-ins and modules.</span></span> <span data-ttu-id="7bfa9-243">請輸入嵌入式管理單元和模組名稱。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-243">Enter the snap-in and module names.</span></span> <span data-ttu-id="7bfa9-244">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-244">Wildcards are not permitted.</span></span>

<span data-ttu-id="7bfa9-245">如需詳細資訊，請參閱 `Import-Module` 和 [about_PSSnapins](../Microsoft.PowerShell.Core/About/about_PSSnapins.md)。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-245">For more information, see `Import-Module` and [about_PSSnapins](../Microsoft.PowerShell.Core/About/about_PSSnapins.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bfa9-246">-OutputModule</span><span class="sxs-lookup"><span data-stu-id="7bfa9-246">-OutputModule</span></span>

<span data-ttu-id="7bfa9-247">為所建立的模組指定選擇性的路徑和名稱 `Export-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-247">Specifies an optional path and name for the module created by `Export-PSSession`.</span></span> <span data-ttu-id="7bfa9-248">預設路徑為 `$home\Documents\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-248">The default path is `$home\Documents\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="7bfa9-249">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-249">This parameter is required.</span></span>

<span data-ttu-id="7bfa9-250">如果模組子目錄或所建立的任何檔案 `Export-PSSession` 已經存在，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-250">If the module subdirectory or any of the files that `Export-PSSession` creates already exist, the command fails.</span></span> <span data-ttu-id="7bfa9-251">若要覆寫現有的檔案，請使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-251">To overwrite existing files, use the **Force** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, ModuleName

Required: True
Position: 1
Default value: $home\Documents\WindowsPowerShell\Modules
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bfa9-252">-Session</span><span class="sxs-lookup"><span data-stu-id="7bfa9-252">-Session</span></span>

<span data-ttu-id="7bfa9-253">指定要從中匯出命令的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-253">Specifies the PSSession from which the commands are exported.</span></span> <span data-ttu-id="7bfa9-254">輸入包含會話物件的變數，或輸入可取得會話物件的命令，例如 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-254">Enter a variable that contains a session object or a command that gets a session object, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="7bfa9-255">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-255">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bfa9-256">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7bfa9-256">CommonParameters</span></span>

<span data-ttu-id="7bfa9-257">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-257">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7bfa9-258">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-258">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7bfa9-259">輸入</span><span class="sxs-lookup"><span data-stu-id="7bfa9-259">INPUTS</span></span>

### <span data-ttu-id="7bfa9-260">無</span><span class="sxs-lookup"><span data-stu-id="7bfa9-260">None</span></span>

<span data-ttu-id="7bfa9-261">您無法透過管道傳送物件至 `Export-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-261">You cannot pipe objects to `Export-PSSession`.</span></span>

## <span data-ttu-id="7bfa9-262">輸出</span><span class="sxs-lookup"><span data-stu-id="7bfa9-262">OUTPUTS</span></span>

### <span data-ttu-id="7bfa9-263">System.IO.FileInfo</span><span class="sxs-lookup"><span data-stu-id="7bfa9-263">System.IO.FileInfo</span></span>

<span data-ttu-id="7bfa9-264">`Export-PSSession` 傳回包含它所建立之模組的檔案清單。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-264">`Export-PSSession` returns a list of files that comprise the module that it created.</span></span>

## <span data-ttu-id="7bfa9-265">注意</span><span class="sxs-lookup"><span data-stu-id="7bfa9-265">NOTES</span></span>

<span data-ttu-id="7bfa9-266">`Export-PSSession` 依賴 PowerShell 遠端基礎結構。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-266">`Export-PSSession` relies on the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="7bfa9-267">若要使用此 Cmdlet，電腦必須針對遠端功能做設定。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-267">To use this cmdlet, the computer must be configured for remoting.</span></span> <span data-ttu-id="7bfa9-268">如需詳細資訊，請參閱[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-268">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="7bfa9-269">您無法使用 `Export-PSSession` 匯出 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-269">You cannot use `Export-PSSession` to export a PowerShell provider.</span></span>

<span data-ttu-id="7bfa9-270">匯出的命令會在從中匯出它們的來源 PSSession 中以隱含的方式執行。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-270">Exported commands run implicitly in the PSSession from which they were exported.</span></span> <span data-ttu-id="7bfa9-271">從遠端執行命令的詳細資料會由 PowerShell 完全處理。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-271">The details of running the commands remotely are handled entirely by PowerShell.</span></span> <span data-ttu-id="7bfa9-272">執行匯出之命令的方式與執行本機命令的方式一樣。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-272">You can run the exported commands just as you would run local commands.</span></span>

<span data-ttu-id="7bfa9-273">`Export-ModuleMember` 在所匯出的模組中，捕捉和儲存 PSSession 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-273">`Export-ModuleMember` captures and saves information about the PSSession in the module that it exports.</span></span> <span data-ttu-id="7bfa9-274">當您匯入模組時，如果已匯出命令的 PSSession 已關閉，且沒有使用中的 Pssession 到同一部電腦，則模組中的命令會嘗試重新建立 PSSession。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-274">If the PSSession from which the commands were exported is closed when you import the module, and there are no active PSSessions to the same computer, the commands in the module attempt to recreate the PSSession.</span></span> <span data-ttu-id="7bfa9-275">如果嘗試重新建立 PSSession 失敗，匯出的命令將不會執行。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-275">If attempts to recreate the PSSession fail, the exported commands will not run.</span></span>

<span data-ttu-id="7bfa9-276">在模組中捕捉和儲存的會話資訊不 `Export-ModuleMember` 包含會話選項，例如您在喜好設定變數中指定的會話， `$PSSessionOption` 或使用 **SessionOption** `New-PSSession` 、或 Cmdlet 的 SessionOption 參數 `Enter-PSSession` `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-276">The session information that `Export-ModuleMember` captures and saves in the module does not include session options, such as those that you specify in the `$PSSessionOption` preference variable or by using the **SessionOption** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlets.</span></span> <span data-ttu-id="7bfa9-277">在您匯入模組時，如果原始 PSSession 已關閉，模組將會使用另一個連到同一部電腦的 PSSession (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-277">If the original PSSession is closed when you import the module, the module will use another PSSession to the same computer, if one is available.</span></span> <span data-ttu-id="7bfa9-278">若要讓匯入的命令在正確設定的工作階段中執行，請在匯入模組之前，先使用您想要的選項來建立 PSSession。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-278">To enable the imported commands to run in a correctly configured session, create a PSSession with the options that you want before you import the module.</span></span>

<span data-ttu-id="7bfa9-279">若要尋找要匯出的命令，請 `Export-PSSession` 使用 `Invoke-Command` Cmdlet `Get-Command` 在 PSSession 中執行命令。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-279">To find the commands to export, `Export-PSSession` uses the `Invoke-Command` cmdlet to run a `Get-Command` command in the PSSession.</span></span> <span data-ttu-id="7bfa9-280">為了取得並儲存命令的格式設定資料，它會使用 `Get-FormatData` 和 `Export-FormatData` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-280">To get and save formatting data for the commands, it uses the `Get-FormatData` and `Export-FormatData` cmdlets.</span></span> <span data-ttu-id="7bfa9-281">`Invoke-Command` `Get-Command` `Get-FormatData` `Export-FormatData` 當您執行命令時，您可能會在、、和中看到錯誤訊息 `Export-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-281">You might see error messages from `Invoke-Command`, `Get-Command`, `Get-FormatData`, and `Export-FormatData` when you run an `Export-PSSession` command.</span></span> <span data-ttu-id="7bfa9-282">此外， `Export-PSSession` 無法從不包含 `Get-Command` 、 `Get-FormatData` 、 `Select-Object` 和 Cmdlet 的會話匯出命令 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-282">Also, `Export-PSSession` cannot export commands from a session that does not include the `Get-Command`, `Get-FormatData`, `Select-Object`, and `Get-Help` cmdlets.</span></span>

<span data-ttu-id="7bfa9-283">`Export-PSSession` 使用 `Write-Progress` Cmdlet 來顯示命令的進度。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-283">`Export-PSSession` uses the `Write-Progress` cmdlet to display the progress of the command.</span></span> <span data-ttu-id="7bfa9-284">當命令執行時，您可以看到進度列。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-284">You might see the progress bar while the command is running.</span></span>

<span data-ttu-id="7bfa9-285">匯出的命令與其他遠端命令具有相同的限制，包括無法以使用者介面啟動程式，例如「記事本」。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-285">Exported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>

<span data-ttu-id="7bfa9-286">因為 PowerShell 設定檔不是在 Pssession 中執行，所以無法使用設定檔新增至會話的命令 `Export-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-286">Because PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to `Export-PSSession`.</span></span> <span data-ttu-id="7bfa9-287">若要從設定檔匯出命令，請在 `Invoke-Command` 匯出命令之前，先使用命令手動在 PSSession 中執行設定檔。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-287">To export commands from a profile, use an `Invoke-Command` command to run the profile in the PSSession manually before exporting commands.</span></span>

<span data-ttu-id="7bfa9-288">所建立的模組 `Export-PSSession` 可能包含格式化檔案，即使命令沒有匯入格式化資料。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-288">The module that `Export-PSSession` creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="7bfa9-289">如果命令不會匯入格式設定資料，所建立的任何格式檔案都將不會包含格式設定資料。</span><span class="sxs-lookup"><span data-stu-id="7bfa9-289">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>

## <span data-ttu-id="7bfa9-290">相關連結</span><span class="sxs-lookup"><span data-stu-id="7bfa9-290">RELATED LINKS</span></span>

[<span data-ttu-id="7bfa9-291">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="7bfa9-291">about_Command_Precedence</span></span>](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)

[<span data-ttu-id="7bfa9-292">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="7bfa9-292">about_PSSessions</span></span>](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[<span data-ttu-id="7bfa9-293">about_PSSnapins</span><span class="sxs-lookup"><span data-stu-id="7bfa9-293">about_PSSnapins</span></span>](../Microsoft.PowerShell.Core/About/about_PSSnapins.md)

[<span data-ttu-id="7bfa9-294">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="7bfa9-294">about_Remote_Requirements</span></span>](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)

[<span data-ttu-id="7bfa9-295">Import-Module</span><span class="sxs-lookup"><span data-stu-id="7bfa9-295">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="7bfa9-296">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="7bfa9-296">Import-PSSession</span></span>](Import-PSSession.md)

[<span data-ttu-id="7bfa9-297">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="7bfa9-297">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="7bfa9-298">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="7bfa9-298">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="7bfa9-299">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="7bfa9-299">New-PSSessionOption</span></span>](../Microsoft.PowerShell.Core/New-PSSessionOption.md)

[<span data-ttu-id="7bfa9-300">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="7bfa9-300">Remove-PSSession</span></span>](../Microsoft.PowerShell.Core/Remove-PSSession.md)
