---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/save-help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Help
ms.openlocfilehash: 3264bdc41d43fdec55ee80514bc988b33772a792
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388513"
---
# <span data-ttu-id="79072-103">Save-Help</span><span class="sxs-lookup"><span data-stu-id="79072-103">Save-Help</span></span>

## <span data-ttu-id="79072-104">概要</span><span class="sxs-lookup"><span data-stu-id="79072-104">SYNOPSIS</span></span>
<span data-ttu-id="79072-105">下載最新的說明檔並儲存至檔案系統目錄。</span><span class="sxs-lookup"><span data-stu-id="79072-105">Downloads and saves the newest help files to a file system directory.</span></span>

## <span data-ttu-id="79072-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="79072-106">SYNTAX</span></span>

### <span data-ttu-id="79072-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="79072-107">Path (Default)</span></span>

```
Save-Help [-DestinationPath] <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="79072-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="79072-108">LiteralPath</span></span>

```
Save-Help -LiteralPath <String[]> [[-Module] <PSModuleInfo[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force]
 [<CommonParameters>]
```

## <span data-ttu-id="79072-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="79072-109">DESCRIPTION</span></span>

<span data-ttu-id="79072-110">`Save-Help`Cmdlet 會下載適用于 PowerShell 模組的最新說明檔案，並將它們儲存至您指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="79072-110">The `Save-Help` cmdlet downloads the newest help files for PowerShell modules and saves them to a directory that you specify.</span></span> <span data-ttu-id="79072-111">此功能可讓您在無法存取網際網路的電腦上更新說明檔案，並輕鬆地在多部電腦上更新說明檔案。</span><span class="sxs-lookup"><span data-stu-id="79072-111">This feature lets you update the help files on computers that do not have access to the Internet, and makes it easier to update the help files on multiple computers.</span></span>

<span data-ttu-id="79072-112">在 Windows PowerShell 3.0 中， `Save-Help` 只會針對安裝在本機電腦上的模組進行處理。</span><span class="sxs-lookup"><span data-stu-id="79072-112">In Windows PowerShell 3.0, `Save-Help` worked only for modules that are installed on the local computer.</span></span> <span data-ttu-id="79072-113">雖然可以從遠端電腦匯入模組，或使用 PowerShell 遠端處理從遠端電腦取得 **PSModuleInfo** 物件的參考，但 **HelpInfoUri** 屬性不會保留，且 `Save-Help` 不適用於遠端模組說明。</span><span class="sxs-lookup"><span data-stu-id="79072-113">Although it was possible to import a module from a remote computer, or obtain a reference to a **PSModuleInfo** object from a remote computer by using PowerShell remoting, the **HelpInfoUri** property was not preserved, and `Save-Help` would not work for remote module Help.</span></span>

<span data-ttu-id="79072-114">在 Windows PowerShell 4.0 中， **HelpInfoUri** 屬性會透過 PowerShell 遠端處理保留，而這可讓您 `Save-Help` 在遠端電腦上安裝的模組運作。</span><span class="sxs-lookup"><span data-stu-id="79072-114">In Windows PowerShell 4.0, the **HelpInfoUri** property is preserved over PowerShell remoting, which enables `Save-Help` to work for modules that are installed on remote computers.</span></span> <span data-ttu-id="79072-115">您也可以在無法存取網際網路的電腦上執行，將 **PSModuleInfo** 物件儲存至磁片或卸載式媒體 `Export-Clixml` ，在可存取網際網路的電腦上匯入物件，然後 `Save-Help` 在 **PSModuleInfo** 物件上執行。</span><span class="sxs-lookup"><span data-stu-id="79072-115">It is also possible to save a **PSModuleInfo** object to disk or removable media by running `Export-Clixml` on a computer that does not have Internet access, import the object on a computer that does have Internet access, and then run `Save-Help` on the **PSModuleInfo** object.</span></span> <span data-ttu-id="79072-116">已儲存的說明可以使用卸除式存放裝置媒體（例如 USB 磁片磁碟機）傳輸到遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="79072-116">The saved help can be transported to the remote computer by using removable storage media, such as a USB drive.</span></span> <span data-ttu-id="79072-117">您可以藉由執行，在遠端電腦上安裝說明 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="79072-117">The help can be installed on the remote computer by running `Update-Help`.</span></span> <span data-ttu-id="79072-118">此程序可用來在沒有任何存取網路方式的電腦上安裝說明。</span><span class="sxs-lookup"><span data-stu-id="79072-118">This process can be used to install help on computers that do not have any kind of network access.</span></span>

<span data-ttu-id="79072-119">若要安裝已儲存的說明檔，請執行 `Update-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79072-119">To install saved help files, run the `Update-Help` cmdlet.</span></span> <span data-ttu-id="79072-120">新增其 **SourcePath** 參數，以指定您儲存說明檔的資料夾。</span><span class="sxs-lookup"><span data-stu-id="79072-120">Add its **SourcePath** parameter to specify the folder in which you saved the Help files.</span></span>

<span data-ttu-id="79072-121">如果沒有參數，命令就會針對會話中的 `Save-Help` 所有模組以及安裝在電腦上的模組，下載 **PSModulePath** 環境變數所列位置中的所有模組的最新說明。</span><span class="sxs-lookup"><span data-stu-id="79072-121">Without parameters, a `Save-Help` command downloads the newest help for all modules in the session and for modules that are installed on the computer in a location listed in the **PSModulePath** environment variable.</span></span> <span data-ttu-id="79072-122">此動作會略過不支援「可更新的說明」的模組，而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="79072-122">This action skips modules that do not support Updatable Help without warning.</span></span>

<span data-ttu-id="79072-123">`Save-Help`Cmdlet 會檢查目的地資料夾中任何說明檔的版本。</span><span class="sxs-lookup"><span data-stu-id="79072-123">The `Save-Help` cmdlet checks the version of any help files in the destination folder.</span></span> <span data-ttu-id="79072-124">如果有較新的說明檔，此 Cmdlet 會從網際網路下載最新的說明檔，然後將它們儲存在資料夾中。</span><span class="sxs-lookup"><span data-stu-id="79072-124">If newer help files are available, this cmdlet downloads the newest help files from the Internet, and then saves them in the folder.</span></span> <span data-ttu-id="79072-125">此 `Save-Help` Cmdlet 的運作方式與 `Update-Help` Cmdlet 相同，不同之處在于它會將下載的封包 ( .cab) 檔案中，而不是從封包檔解壓縮說明檔，並將它們安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="79072-125">The `Save-Help` cmdlet works just like the `Update-Help` cmdlet, except that it saves the downloaded cabinet (.cab) files, instead of extracting the help files from the cabinet files and installing them on the computer.</span></span>

<span data-ttu-id="79072-126">每個模組的已儲存說明都包含說明資訊 (HelpInfo XML) 檔案和包含每個 UI 文化特性說明檔案的封包 (.cab) 檔。</span><span class="sxs-lookup"><span data-stu-id="79072-126">The saved help for each module consists of one help information (HelpInfo XML) file and one cabinet (.cab) file for the help files each UI culture.</span></span> <span data-ttu-id="79072-127">您不需要從封包檔解壓縮說明檔案。</span><span class="sxs-lookup"><span data-stu-id="79072-127">You do not have to extract the help files from the cabinet file.</span></span> <span data-ttu-id="79072-128">此 `Update-Help` Cmdlet 會解壓縮說明檔案、驗證 XML 是否安全，然後將說明檔和說明資訊檔安裝在模組資料夾的特定語言子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="79072-128">The `Update-Help` cmdlet extracts the help files, validates the XML for safety, and then installs the help files and the help information file in a language-specific subfolder of the module folder.</span></span>

<span data-ttu-id="79072-129">若要儲存 PowerShell 安裝資料夾 () 中模組的說明檔 `$pshome\Modules` ，請使用 [以系統管理員身分執行] 選項啟動 powershell。</span><span class="sxs-lookup"><span data-stu-id="79072-129">To save the help files for modules in the PowerShell installation folder (`$pshome\Modules`), start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="79072-130">您必須為電腦上 Administrators 群組的成員才能下載這些模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="79072-130">You must be a member of the Administrators group on the computer to download the help files for these modules.</span></span>

<span data-ttu-id="79072-131">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="79072-131">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="79072-132">範例</span><span class="sxs-lookup"><span data-stu-id="79072-132">EXAMPLES</span></span>

### <span data-ttu-id="79072-133">範例1：儲存 DhcpServer 模組的說明</span><span class="sxs-lookup"><span data-stu-id="79072-133">Example 1: Save the help for the DhcpServer module</span></span>

```powershell
# Option 1: Run Invoke-Command to get the PSModuleInfo object for the remote DHCP Server module,
# save the PSModuleInfo object in the variable $m, and then run Save-Help.

$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock { Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 2: Open a PSSession--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$s = New-PSSession -ComputerName "RemoteServer"
$m = Get-Module -PSSession $s -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 3: Open a CIM session--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$c = New-CimSession -ComputerName "RemoteServer"
$m = Get-Module -CimSession $c -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"
```

<span data-ttu-id="79072-134">此範例顯示三種不同的方式 `Save-Help` ，可用來從連線到網際網路的用戶端電腦儲存 **DhcpServer** 模組的說明，而不需要在本機電腦上安裝 **DhcpServer** 模組或 DHCP 伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="79072-134">This example shows three different ways to use `Save-Help` to save the help for the **DhcpServer** module from an Internet-connected client computer, without installing the **DhcpServer** module or the DHCP Server role on the local computer.</span></span>

### <span data-ttu-id="79072-135">範例2：安裝 DhcpServer 模組的說明</span><span class="sxs-lookup"><span data-stu-id="79072-135">Example 2: Install help for the DhcpServer module</span></span>

```powershell
# First, run Export-CliXml to export the PSModuleInfo object to a shared folder or to removable media.

$m = Get-Module -Name "DhcpServer" -ListAvailable
Export-CliXml -Path "E:\UsbFlashDrive\DhcpModule.xml" -InputObject $m

# Next, transport the removable media to a computer that has Internet access, and then import the
# PSModuleInfo object with Import-CliXml. Run Save-Help to save the Help for the imported DhcpServer
# module PSModuleInfo object.

$deserialized_m = Import-CliXml "E:\UsbFlashDrive\DhcpModule.xml"
Save-Help -Module $deserialized_m -DestinationPath "E:\UsbFlashDrive\SavedHelp"

# Finally, transport the removable media back to the computer that does not have network access, and
# then install the help by running Update-Help.

Update-Help -Module DhcpServer -SourcePath "E:\UsbFlashDrive\SavedHelp"
```

<span data-ttu-id="79072-136">此範例示範如何在無法存取網際網路的電腦上，安裝您在範例1中為 **DhcpServer** 模組儲存的說明。</span><span class="sxs-lookup"><span data-stu-id="79072-136">This example shows how to install help that you saved in Example 1 for the **DhcpServer** module on a computer that does not have Internet access.</span></span>

### <span data-ttu-id="79072-137">範例3：儲存所有模組的說明</span><span class="sxs-lookup"><span data-stu-id="79072-137">Example 3: Save help for all modules</span></span>

```powershell
Save-Help -DestinationPath "\\Server01\FileShare01"
```

<span data-ttu-id="79072-138">此命令會根據為本機電腦上 Windows 設定的 UI 文化特性下載所有模組的最新說明檔案。</span><span class="sxs-lookup"><span data-stu-id="79072-138">This command downloads the newest help files for all modules in the UI culture set for Windows on the local computer.</span></span> <span data-ttu-id="79072-139">它會將說明檔案儲存在 `\\Server01\Fileshare01` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="79072-139">It saves the help files in the `\\Server01\Fileshare01` folder.</span></span>

### <span data-ttu-id="79072-140">範例4：儲存電腦上模組的說明</span><span class="sxs-lookup"><span data-stu-id="79072-140">Example 4: Save help for a module on the computer</span></span>

```powershell
Save-Help -Module ServerManager -DestinationPath "\\Server01\FileShare01" -Credential Domain01/Admin01
```

<span data-ttu-id="79072-141">此命令會下載 **ServerManager** 模組的最新說明檔，然後將它們儲存在 `\\Server01\Fileshare01` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="79072-141">This command downloads the newest help files for the **ServerManager** module, and then saves them in the `\\Server01\Fileshare01` folder.</span></span>

<span data-ttu-id="79072-142">當在電腦上安裝某個模組時，即使該模組不會匯入到目前的工作階段中，您也可以輸入模組名稱當做 **Module** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="79072-142">When a module is installed on the computer, you can type the module name as the value of the **Module** parameter, even if the module is not imported into the current session.</span></span>

<span data-ttu-id="79072-143">命令使用 **Credential** 參數提供具權限在檔案共用進行寫入之使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="79072-143">The command uses the **Credential** parameter to supply the credentials of a user who has permission to write to the file share.</span></span>

### <span data-ttu-id="79072-144">範例5：儲存不同電腦上模組的說明</span><span class="sxs-lookup"><span data-stu-id="79072-144">Example 5: Save help for a module on a different computer</span></span>

```powershell
Invoke-Command -ComputerName Server02 {Get-Module -Name CustomSQL -ListAvailable} | Save-Help -DestinationPath \\Server01\FileShare01 -Credential Domain01\Admin01
```

<span data-ttu-id="79072-145">這些命令會下載 **CustomSQL** 模組的最新說明檔案，並將它們儲存在 `\\Server01\Fileshare01` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="79072-145">These commands download the newest help files for the **CustomSQL** module and save them in the `\\Server01\Fileshare01` folder.</span></span>

<span data-ttu-id="79072-146">由於電腦上未安裝 **CustomSQL** 模組，因此序列包含一個 `Invoke-Command` 命令，可從 Server02 電腦取得 CustomSQL 模組的模組物件，然後使用管線將模組物件傳送至 `Save-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79072-146">Because the **CustomSQL** module is not installed on the computer, the sequence includes an `Invoke-Command` command that gets the module object for the CustomSQL module from the Server02 computer and then pipes the module object to the `Save-Help` cmdlet.</span></span>

<span data-ttu-id="79072-147">當電腦上未安裝模組時， `Save-Help` 需要模組物件，其中包含最新說明檔案位置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="79072-147">When a module is not installed on the computer, `Save-Help` needs the module object, which includes information about the location of the newest help files.</span></span>

### <span data-ttu-id="79072-148">範例6：儲存多種語言的模組說明</span><span class="sxs-lookup"><span data-stu-id="79072-148">Example 6: Save help for a module in multiple languages</span></span>

```powershell
Save-Help -Module Microsoft.PowerShell* -UICulture de-DE, en-US, fr-FR, ja-JP -DestinationPath "D:\Help"
```

<span data-ttu-id="79072-149">此命令會以四種不同的 UI 文化特性來儲存 PowerShell Core 模組的說明。</span><span class="sxs-lookup"><span data-stu-id="79072-149">This command saves help for the PowerShell Core modules in four different UI cultures.</span></span> <span data-ttu-id="79072-150">這些地區設定的語言套件不需要安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="79072-150">The language packs for these locales do not have to be installed on the computer.</span></span>

<span data-ttu-id="79072-151">`Save-Help` 只有當模組擁有者在網際網路上提供翻譯的檔案時，才能在不同的 UI 文化特性中下載模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="79072-151">`Save-Help` can download help files for modules in different UI cultures only when the module owner makes the translated files available on the Internet.</span></span>

### <span data-ttu-id="79072-152">範例7：每天儲存說明一次以上</span><span class="sxs-lookup"><span data-stu-id="79072-152">Example 7: Save help more than one time each day</span></span>

```powershell
Save-Help -Force -DestinationPath "\\Server3\AdminShare\Help"
```

<span data-ttu-id="79072-153">此命令會為安裝在電腦上所有的模組儲存說明。</span><span class="sxs-lookup"><span data-stu-id="79072-153">This command saves help for all modules that are installed on the computer.</span></span> <span data-ttu-id="79072-154">此命令會指定 **Force** 參數來覆寫規則，以防止 `Save-Help` Cmdlet 在每24小時期間下載說明超過一次。</span><span class="sxs-lookup"><span data-stu-id="79072-154">The command specifies the **Force** parameter to override the rule that prevents the `Save-Help` cmdlet from downloading help more than once in each 24-hour period.</span></span>

<span data-ttu-id="79072-155">**Force** 參數也會覆寫 1 GB 的限制和規避版本檢查。</span><span class="sxs-lookup"><span data-stu-id="79072-155">The **Force** parameter also overrides the 1 GB restriction and circumvents version checking.</span></span>
<span data-ttu-id="79072-156">因此，即使版本不晚于目的資料夾中的版本，您也可以下載檔案。</span><span class="sxs-lookup"><span data-stu-id="79072-156">Therefore, you can download files even if the version is not later than the version in the destination folder.</span></span>

<span data-ttu-id="79072-157">此命令會使用 `Save-Help` Cmdlet 來下載說明檔，並將其儲存至指定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="79072-157">The command uses the `Save-Help` cmdlet to download and save the help files to the specified folder.</span></span>
<span data-ttu-id="79072-158">當您每天必須執行一次以上的命令時，必須要有 **Force** 參數 `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="79072-158">The **Force** parameter is required when you have to run a `Save-Help` command more than one time each day.</span></span>

## <span data-ttu-id="79072-159">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="79072-159">PARAMETERS</span></span>

### <span data-ttu-id="79072-160">-Credential</span><span class="sxs-lookup"><span data-stu-id="79072-160">-Credential</span></span>

<span data-ttu-id="79072-161">指定使用者認證。</span><span class="sxs-lookup"><span data-stu-id="79072-161">Specifies a user credential.</span></span> <span data-ttu-id="79072-162">此 Cmdlet 會使用具有存取 **DestinationPath** 參數所指定之檔案系統位置之許可權的使用者認證來執行命令。</span><span class="sxs-lookup"><span data-stu-id="79072-162">This cmdlet runs the command by using credentials of a user who has permission to access the file system location specified by the **DestinationPath** parameter.</span></span> <span data-ttu-id="79072-163">只有當命令中使用 **DestinationPath** 或 **LiteralPath** 參數時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="79072-163">This parameter is valid only when the **DestinationPath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="79072-164">此參數可讓您 `Save-Help` 在遠端電腦上執行使用 **DestinationPath** 參數的命令。</span><span class="sxs-lookup"><span data-stu-id="79072-164">This parameter enables you to run `Save-Help` commands that use the **DestinationPath** parameter on remote computers.</span></span> <span data-ttu-id="79072-165">藉由提供明確的認證，您可以在遠端電腦上執行命令，並存取第三部電腦上的檔案共用，而不會遇到拒絕存取錯誤，或使用 CredSSP 驗證來委派認證。</span><span class="sxs-lookup"><span data-stu-id="79072-165">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="79072-166">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="79072-166">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="79072-167">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="79072-167">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="79072-168">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="79072-168">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="79072-169">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="79072-169">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79072-170">-DestinationPath</span><span class="sxs-lookup"><span data-stu-id="79072-170">-DestinationPath</span></span>

<span data-ttu-id="79072-171">指定用來儲存說明檔的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="79072-171">Specifies the path of the folder in which the help files are saved.</span></span> <span data-ttu-id="79072-172">不要指定檔案名稱或副檔名。</span><span class="sxs-lookup"><span data-stu-id="79072-172">Do not specify a file name or file name extension.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79072-173">-Force</span><span class="sxs-lookup"><span data-stu-id="79072-173">-Force</span></span>

<span data-ttu-id="79072-174">指出此 Cmdlet 不會遵循每天一次的限制、略過版本檢查，以及下載超過 1 GB 限制的檔案。</span><span class="sxs-lookup"><span data-stu-id="79072-174">Indicates that this cmdlet does not follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="79072-175">如果沒有這個參數，每 `Save-Help` 個24小時期間內只允許每個模組一個命令，每個模組的下載限制為 1 GB 的未壓縮內容，而且只有當模組的說明檔案比電腦上的檔案更新時才會安裝。</span><span class="sxs-lookup"><span data-stu-id="79072-175">Without this parameter, only one `Save-Help` command for each module is permitted in each 24-hour period, downloads are limited to 1 GB of uncompressed content per module, and help files for a module are installed only when they are newer than the files on the computer.</span></span>

<span data-ttu-id="79072-176">每日一次的限制可保護裝載說明檔的伺服器，並讓您可以將 `Save-Help` 命令新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="79072-176">The once-per-day limit protects the servers that host the help files, and makes it practical for you to add a `Save-Help` command to your PowerShell profile.</span></span>

<span data-ttu-id="79072-177">若要不使用 **Force** 參數來儲存多重 UI 文化特性中的模組說明，請在同一個命令中包含所有 UI 文化特性，例如：`Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`</span><span class="sxs-lookup"><span data-stu-id="79072-177">To save help for a module in multiple UI cultures without the **Force** parameter, include all UI cultures in the same command, such as: `Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79072-178">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="79072-178">-FullyQualifiedModule</span></span>

<span data-ttu-id="79072-179">指定以 **ModuleSpecification** 物件形式指定之名稱的模組。</span><span class="sxs-lookup"><span data-stu-id="79072-179">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span> <span data-ttu-id="79072-180">請參閱 [ModuleSpecification (雜湊表) ](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)的「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="79072-180">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="79072-181">例如， **FullyQualifiedModule** 參數會接受以下列其中一種格式指定的模組名稱：</span><span class="sxs-lookup"><span data-stu-id="79072-181">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="79072-182">**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="79072-182">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="79072-183">您無法在與 **模組** 參數相同的命令中指定 **FullyQualifiedModule** 參數。</span><span class="sxs-lookup"><span data-stu-id="79072-183">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="79072-184">這兩個參數是互斥的。</span><span class="sxs-lookup"><span data-stu-id="79072-184">the two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="79072-185">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="79072-185">-LiteralPath</span></span>

<span data-ttu-id="79072-186">指定目的資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="79072-186">Specifies a path of the destination folder.</span></span> <span data-ttu-id="79072-187">與 **DestinationPath** 參數的值不同， **LiteralPath** 參數的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="79072-187">Unlike the value of the **DestinationPath** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="79072-188">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="79072-188">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="79072-189">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="79072-189">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="79072-190">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="79072-190">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79072-191">-Module</span><span class="sxs-lookup"><span data-stu-id="79072-191">-Module</span></span>

<span data-ttu-id="79072-192">指定此 Cmdlet 下載說明的模組。</span><span class="sxs-lookup"><span data-stu-id="79072-192">Specifies modules for which this cmdlet downloads help.</span></span> <span data-ttu-id="79072-193">在以逗號分隔的清單中輸入一或多個模組名稱或名稱模式，或是在每一行有一個模組名稱的檔案中輸入一或多個模組名稱或名稱。</span><span class="sxs-lookup"><span data-stu-id="79072-193">Enter one or more module names or name patters in a comma-separated list or in a file that has one module name on each line.</span></span> <span data-ttu-id="79072-194">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="79072-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="79072-195">您也可以透過管線將模組物件從 `Get-Module` Cmdlet 傳送至 `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="79072-195">You can also pipe module objects from the `Get-Module` cmdlet to `Save-Help`.</span></span>

<span data-ttu-id="79072-196">根據預設， `Save-Help` 會為所有支援「可更新的說明」的模組下載說明，並將其安裝在本機電腦的 **PSModulePath** 環境變數所列的位置。</span><span class="sxs-lookup"><span data-stu-id="79072-196">By default, `Save-Help` downloads help for all modules that support Updatable Help and are installed on the local computer in a location listed in the **PSModulePath** environment variable.</span></span>

<span data-ttu-id="79072-197">若要為未安裝在電腦上的模組儲存說明，請 `Get-Module` 在遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="79072-197">To save help for modules that are not installed on the computer, run a `Get-Module` command on a remote computer.</span></span> <span data-ttu-id="79072-198">然後以管線將產生的模組物件傳送至 `Save-Help` Cmdlet，或將模組物件提交為 **模組** 或 **InputObject** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="79072-198">Then pipe the resulting module objects to the `Save-Help` cmdlet or submit the module objects as the value of the **Module** or **InputObject** parameters.</span></span>

<span data-ttu-id="79072-199">如果您指定的模組已安裝在電腦上，您可以輸入模組名稱或模組物件。</span><span class="sxs-lookup"><span data-stu-id="79072-199">If the module that you specify is installed on the computer, you can enter the module name or a module object.</span></span> <span data-ttu-id="79072-200">如果該模組未安裝在電腦上，您必須輸入模組物件，例如 Cmdlet 所傳回的物件 `Get-Module` 。</span><span class="sxs-lookup"><span data-stu-id="79072-200">If the module is not installed on the computer, you must enter a module object, such as one returned by the `Get-Module` cmdlet.</span></span>

<span data-ttu-id="79072-201">Cmdlet 的 **module** 參數不 `Save-Help` 接受模組檔案或模組資訊清單檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="79072-201">The **Module** parameter of the `Save-Help` cmdlet does not accept the full path of a module file or module manifest file.</span></span> <span data-ttu-id="79072-202">若要儲存不在 **PSModulePath** 位置之模組的說明，請在執行命令之前將模組匯入到目前的會話 `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="79072-202">To save help for a module that is not in a **PSModulePath** location, import the module into the current session before you run the `Save-Help` command.</span></span>

<span data-ttu-id="79072-203">"\*" 的值 (所有) 嘗試更新電腦上所安裝之所有模組的說明。</span><span class="sxs-lookup"><span data-stu-id="79072-203">A value of "\*" (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="79072-204">這包括不支援「可更新的說明」的模組。</span><span class="sxs-lookup"><span data-stu-id="79072-204">This includes modules that do not support Updatable Help.</span></span> <span data-ttu-id="79072-205">當命令遇到不支援「可更新的說明」的模組時，這個值可能會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="79072-205">This value might generate errors when the command encounters modules that do not support Updatable Help.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="79072-206">-UICulture</span><span class="sxs-lookup"><span data-stu-id="79072-206">-UICulture</span></span>

<span data-ttu-id="79072-207">指定此 Cmdlet 取得已更新說明檔的 UI 文化特性值。</span><span class="sxs-lookup"><span data-stu-id="79072-207">Specifies UI culture values for which this cmdlet gets updated help files.</span></span> <span data-ttu-id="79072-208">輸入一或多個語言代碼，例如 `es-ES` ，包含文化特性物件的變數，或可取得文化特性物件的命令，例如 `Get-Culture` 或 `Get-UICulture` 命令。</span><span class="sxs-lookup"><span data-stu-id="79072-208">Enter one or more language codes, such as `es-ES`, a variable that contains culture objects, or a command that gets culture objects, such as a `Get-Culture` or `Get-UICulture` command.</span></span>

<span data-ttu-id="79072-209">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="79072-209">Wildcard characters are not permitted.</span></span> <span data-ttu-id="79072-210">請勿指定部分語言代碼，例如 "de"。</span><span class="sxs-lookup"><span data-stu-id="79072-210">Do not specify a partial language code, such as "de".</span></span>

<span data-ttu-id="79072-211">根據預設，會 `Save-Help` 取得針對 Windows 設定的 UI 文化特性或其回溯文化特性的說明檔。</span><span class="sxs-lookup"><span data-stu-id="79072-211">By default, `Save-Help` gets help files in the UI culture set for Windows or its fallback culture.</span></span>
<span data-ttu-id="79072-212">如果您指定 **UICulture** 參數， `Save-Help` 只會尋找所指定 UI 文化特性的說明，而不會尋找任何 fallback 文化特性中的說明。</span><span class="sxs-lookup"><span data-stu-id="79072-212">If you specify the **UICulture** parameter, `Save-Help` looks for help only for the specified UI culture, not in any fallback culture.</span></span>

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: Current UI culture
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79072-213">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="79072-213">-UseDefaultCredentials</span></span>

<span data-ttu-id="79072-214">指出此 Cmdlet 會使用目前使用者的認證來執行命令，包括 web 下載。</span><span class="sxs-lookup"><span data-stu-id="79072-214">Indicates that this cmdlet runs the command, including the web download, with the credentials of the current user.</span></span> <span data-ttu-id="79072-215">根據預設，該命令執行時不會使用明確宣告的認證。</span><span class="sxs-lookup"><span data-stu-id="79072-215">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="79072-216">此參數只在網路下載是使用 NTLM、交涉或 Kerberos 驗證時有效。</span><span class="sxs-lookup"><span data-stu-id="79072-216">This parameter is effective only when the web download uses NTLM, negotiate, or Kerberos-based authentication.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79072-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="79072-217">CommonParameters</span></span>

<span data-ttu-id="79072-218">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="79072-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="79072-219">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="79072-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="79072-220">輸入</span><span class="sxs-lookup"><span data-stu-id="79072-220">INPUTS</span></span>

### <span data-ttu-id="79072-221">System.Management.Automation.PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="79072-221">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="79072-222">您可以使用管線將模組物件從 `Get-Module` Cmdlet 傳送至的 **模組** 參數 `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="79072-222">You can pipe a module object from the `Get-Module` cmdlet to the **Module** parameter of `Save-Help`.</span></span>

## <span data-ttu-id="79072-223">輸出</span><span class="sxs-lookup"><span data-stu-id="79072-223">OUTPUTS</span></span>

### <span data-ttu-id="79072-224">無</span><span class="sxs-lookup"><span data-stu-id="79072-224">None</span></span>

<span data-ttu-id="79072-225">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="79072-225">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="79072-226">注意</span><span class="sxs-lookup"><span data-stu-id="79072-226">NOTES</span></span>

- <span data-ttu-id="79072-227">若要為 $pshome \Modules 資料夾中的模組儲存說明，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="79072-227">To save help for modules in the $pshome\Modules folder, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="79072-228">只有電腦上 Administrators 群組的成員可以為 $pshome \Modules 資料夾中的模組下載說明。</span><span class="sxs-lookup"><span data-stu-id="79072-228">Only members of the Administrators group on the computer can download help for modules in the $pshome\Modules folder.</span></span>
- <span data-ttu-id="79072-229">每個模組的已儲存說明都包含說明資訊 (HelpInfo XML) 檔案和包含每個 UI 文化特性說明檔案的封包 (.cab) 檔。</span><span class="sxs-lookup"><span data-stu-id="79072-229">The saved help for each module consists of one help information (HelpInfo XML) file and one cabinet (.cab) file for the help files each UI culture.</span></span> <span data-ttu-id="79072-230">您不需要從封包檔解壓縮說明檔案。</span><span class="sxs-lookup"><span data-stu-id="79072-230">You do not have to extract the help files from the cabinet file.</span></span> <span data-ttu-id="79072-231">此 `Update-Help` Cmdlet 會解壓縮說明檔案、驗證 XML，然後在模組資料夾的特定語言子資料夾中安裝說明檔和說明資訊檔案。</span><span class="sxs-lookup"><span data-stu-id="79072-231">The `Update-Help` cmdlet extracts the help files, validates the XML, and then installs the help files and the help information file in a language-specific subfolder of the module folder.</span></span>
- <span data-ttu-id="79072-232">`Save-Help`Cmdlet 可以儲存未安裝在電腦上之模組的說明。</span><span class="sxs-lookup"><span data-stu-id="79072-232">The `Save-Help` cmdlet can save help for modules that are not installed on the computer.</span></span> <span data-ttu-id="79072-233">不過，因為說明檔是安裝在模組資料夾中，所以 `Update-Help` Cmdlet 只能針對安裝在電腦上的模組安裝已更新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="79072-233">However, because help files are installed in the module folder, the `Update-Help` cmdlet can install updated help file only for modules that are installed on the computer.</span></span>
- <span data-ttu-id="79072-234">如果找 `Save-Help` 不到模組的已更新說明檔，或找不到指定語言的已更新說明檔，它會繼續以無訊息模式繼續，而不會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="79072-234">If `Save-Help` cannot find updated help files for a module, or cannot find updated help files in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="79072-235">若要查看命令已儲存哪些檔案，請指定 **Verbose** 參數。</span><span class="sxs-lookup"><span data-stu-id="79072-235">To see which files were saved by the command, specify the **Verbose** parameter.</span></span>
- <span data-ttu-id="79072-236">模組是可更新的說明之最小單位。</span><span class="sxs-lookup"><span data-stu-id="79072-236">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="79072-237">您無法儲存特定 Cmdlet 的說明，僅適用于模組中的所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79072-237">You cannot save help for a particular cmdlet, only for all cmdlets in module.</span></span> <span data-ttu-id="79072-238">若要尋找包含特定 Cmdlet 的模組，請搭配使用 **ModuleName** 屬性與 `Get-Command` Cmdlet，例如 `(Get-Command \<cmdlet-name\>).ModuleName`</span><span class="sxs-lookup"><span data-stu-id="79072-238">To find the module that contains a particular cmdlet, use the **ModuleName** property together with the `Get-Command` cmdlet, for example, `(Get-Command \<cmdlet-name\>).ModuleName`</span></span>
- <span data-ttu-id="79072-239">`Save-Help` 支援所有模組和 PowerShell Core 嵌入式管理單元。它不支援任何其他嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="79072-239">`Save-Help` supports all modules and the PowerShell Core snap-ins. It does not support any other snap-ins.</span></span>
- <span data-ttu-id="79072-240">`Update-Help`和 `Save-Help` Cmdlet 使用下列埠下載說明檔：適用于 HTTP 的埠80和 HTTPS 的埠443。</span><span class="sxs-lookup"><span data-stu-id="79072-240">The `Update-Help` and `Save-Help` cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>
- <span data-ttu-id="79072-241">`Update-Help` `Save-Help` Windows 預先安裝環境 (Windows PE) 不支援和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79072-241">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="79072-242">相關連結</span><span class="sxs-lookup"><span data-stu-id="79072-242">RELATED LINKS</span></span>

[<span data-ttu-id="79072-243">Get-Help</span><span class="sxs-lookup"><span data-stu-id="79072-243">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="79072-244">Get-Module</span><span class="sxs-lookup"><span data-stu-id="79072-244">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="79072-245">Update-Help</span><span class="sxs-lookup"><span data-stu-id="79072-245">Update-Help</span></span>](Update-Help.md)
