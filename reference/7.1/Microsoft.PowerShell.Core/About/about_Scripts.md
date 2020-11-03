---
description: 說明如何在 PowerShell 中執行和寫入腳本。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scripts
ms.openlocfilehash: c877627f8caeab8309326826caa4ec13d65d5d9d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206708"
---
# <a name="about-scripts"></a><span data-ttu-id="4e134-104">關於腳本</span><span class="sxs-lookup"><span data-stu-id="4e134-104">About Scripts</span></span>

## <a name="short-description"></a><span data-ttu-id="4e134-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="4e134-105">Short description</span></span>
<span data-ttu-id="4e134-106">說明如何在 PowerShell 中執行和寫入腳本。</span><span class="sxs-lookup"><span data-stu-id="4e134-106">Describes how to run and write scripts in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="4e134-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="4e134-107">Long description</span></span>

<span data-ttu-id="4e134-108">腳本是純文字檔案，其中包含一或多個 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="4e134-108">A script is a plain text file that contains one or more PowerShell commands.</span></span>
<span data-ttu-id="4e134-109">PowerShell 腳本有 `.ps1` 副檔名。</span><span class="sxs-lookup"><span data-stu-id="4e134-109">PowerShell scripts have a `.ps1` file extension.</span></span>

<span data-ttu-id="4e134-110">執行腳本很像是執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4e134-110">Running a script is a lot like running a cmdlet.</span></span> <span data-ttu-id="4e134-111">您可以輸入腳本的路徑和檔案名，並使用參數來提交資料和設定選項。</span><span class="sxs-lookup"><span data-stu-id="4e134-111">You type the path and file name of the script and use parameters to submit data and set options.</span></span> <span data-ttu-id="4e134-112">您可以在電腦或不同電腦上的遠端會話中執行腳本。</span><span class="sxs-lookup"><span data-stu-id="4e134-112">You can run scripts on your computer or in a remote session on a different computer.</span></span>

<span data-ttu-id="4e134-113">撰寫腳本會儲存命令以供稍後使用，並可讓您輕鬆地與其他人共用。</span><span class="sxs-lookup"><span data-stu-id="4e134-113">Writing a script saves a command for later use and makes it easy to share with others.</span></span> <span data-ttu-id="4e134-114">最重要的是，它可讓您直接輸入腳本路徑和檔案名來執行命令。</span><span class="sxs-lookup"><span data-stu-id="4e134-114">Most importantly, it lets you run the commands simply by typing the script path and the filename.</span></span> <span data-ttu-id="4e134-115">腳本可以像是檔案中的單一命令一樣簡單，也可以像複雜程式一樣廣泛。</span><span class="sxs-lookup"><span data-stu-id="4e134-115">Scripts can be as simple as a single command in a file or as extensive as a complex program.</span></span>

<span data-ttu-id="4e134-116">腳本具有其他功能，例如 `#Requires` 特殊批註、使用參數、支援資料區段，以及用於安全性的數位簽章。</span><span class="sxs-lookup"><span data-stu-id="4e134-116">Scripts have additional features, such as the `#Requires` special comment, the use of parameters, support for data sections, and digital signing for security.</span></span>
<span data-ttu-id="4e134-117">您也可以撰寫腳本的說明主題，以及腳本中的任何函數。</span><span class="sxs-lookup"><span data-stu-id="4e134-117">You can also write Help topics for scripts and for any functions in the script.</span></span>

## <a name="how-to-run-a-script"></a><span data-ttu-id="4e134-118">如何執行腳本</span><span class="sxs-lookup"><span data-stu-id="4e134-118">How to run a script</span></span>

<span data-ttu-id="4e134-119">您必須先變更預設的 PowerShell 執行原則，才能在 Windows 上執行腳本。</span><span class="sxs-lookup"><span data-stu-id="4e134-119">Before you can run a script on Windows, you need to change the default PowerShell execution policy.</span></span> <span data-ttu-id="4e134-120">執行原則並不適用于在非 Windows 平臺上執行的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4e134-120">Execution policy does not apply to PowerShell running on non-Windows platforms.</span></span>

<span data-ttu-id="4e134-121">預設的執行原則 `Restricted` 會防止所有腳本執行，包括您在本機電腦上撰寫的腳本。</span><span class="sxs-lookup"><span data-stu-id="4e134-121">The default execution policy, `Restricted`, prevents all scripts from running, including scripts that you write on the local computer.</span></span> <span data-ttu-id="4e134-122">如需詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="4e134-122">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="4e134-123">執行原則會儲存在登錄中，因此您只需要在每部電腦上變更一次。</span><span class="sxs-lookup"><span data-stu-id="4e134-123">The execution policy is saved in the registry, so you need to change it only once on each computer.</span></span>

<span data-ttu-id="4e134-124">若要變更執行原則，請使用下列程式。</span><span class="sxs-lookup"><span data-stu-id="4e134-124">To change the execution policy, use the following procedure.</span></span>

<span data-ttu-id="4e134-125">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="4e134-125">At the command prompt, type:</span></span>

```powershell
Set-ExecutionPolicy AllSigned
```

<span data-ttu-id="4e134-126">或</span><span class="sxs-lookup"><span data-stu-id="4e134-126">or</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="4e134-127">變更會立即生效。</span><span class="sxs-lookup"><span data-stu-id="4e134-127">The change is effective immediately.</span></span>

<span data-ttu-id="4e134-128">若要執行腳本，請輸入腳本檔案的完整名稱和完整路徑。</span><span class="sxs-lookup"><span data-stu-id="4e134-128">To run a script, type the full name and the full path to the script file.</span></span>

<span data-ttu-id="4e134-129">例如，若要在 C：\Scripts 目錄中執行 Get-ServiceLog.ps1 腳本，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4e134-129">For example, to run the Get-ServiceLog.ps1 script in the C:\Scripts directory, type:</span></span>

```powershell
C:\Scripts\Get-ServiceLog.ps1
```

<span data-ttu-id="4e134-130">若要在目前的目錄中執行腳本，請輸入目前的目錄的路徑，或使用點來代表目前的目錄，後面接著路徑反斜線 (`.\`) 。</span><span class="sxs-lookup"><span data-stu-id="4e134-130">To run a script in the current directory, type the path to the current directory, or use a dot to represent the current directory, followed by a path backslash (`.\`).</span></span>

<span data-ttu-id="4e134-131">例如，若要在本機目錄中執行 ServicesLog.ps1 腳本，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4e134-131">For example, to run the ServicesLog.ps1 script in the local directory, type:</span></span>

```powershell
.\Get-ServiceLog.ps1
```

<span data-ttu-id="4e134-132">如果腳本有參數，請在指令檔名之後輸入參數和參數值。</span><span class="sxs-lookup"><span data-stu-id="4e134-132">If the script has parameters, type the parameters and parameter values after the script filename.</span></span>

<span data-ttu-id="4e134-133">例如，下列命令會使用 Get-ServiceLog 腳本的 ServiceName 參數來要求 WinRM 服務活動的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4e134-133">For example, the following command uses the ServiceName parameter of the Get-ServiceLog script to request a log of WinRM service activity.</span></span>

```powershell
.\Get-ServiceLog.ps1 -ServiceName WinRM
```

<span data-ttu-id="4e134-134">做為安全性功能，當您按兩下檔案總管中的腳本圖示時，或是當您輸入腳本名稱但沒有完整路徑時（即使腳本是在目前的目錄中），PowerShell 並不會執行腳本。</span><span class="sxs-lookup"><span data-stu-id="4e134-134">As a security feature, PowerShell does not run scripts when you double-click the script icon in File Explorer or when you type the script name without a full path, even when the script is in the current directory.</span></span> <span data-ttu-id="4e134-135">如需在 PowerShell 中執行命令和腳本的詳細資訊，請參閱 [about_Command_Precedence](about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="4e134-135">For more information about running commands and scripts in PowerShell, see [about_Command_Precedence](about_Command_Precedence.md).</span></span>

### <a name="run-with-powershell"></a><span data-ttu-id="4e134-136">使用 PowerShell 執行</span><span class="sxs-lookup"><span data-stu-id="4e134-136">Run with PowerShell</span></span>

<span data-ttu-id="4e134-137">從 PowerShell 3.0 開始，您可以從檔案總管執行腳本。</span><span class="sxs-lookup"><span data-stu-id="4e134-137">Beginning in PowerShell 3.0, you can run scripts from File Explorer.</span></span>

<span data-ttu-id="4e134-138">若要使用「使用 PowerShell 執行」功能：</span><span class="sxs-lookup"><span data-stu-id="4e134-138">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="4e134-139">執行檔案總管，以滑鼠右鍵按一下指令檔名，然後選取 [使用 PowerShell 執行]。</span><span class="sxs-lookup"><span data-stu-id="4e134-139">Run File Explorer, right-click the script filename and then select "Run with PowerShell".</span></span>

<span data-ttu-id="4e134-140">「使用 PowerShell 執行」功能的設計目的是要執行沒有必要參數的腳本，而不會將輸出傳回命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="4e134-140">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="4e134-141">如需詳細資訊，請參閱 [about_Run_With_PowerShell](about_Run_With_PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="4e134-141">For more information, see [about_Run_With_PowerShell](about_Run_With_PowerShell.md).</span></span>

### <a name="running-scripts-on-other-computers"></a><span data-ttu-id="4e134-142">在其他電腦上執行腳本</span><span class="sxs-lookup"><span data-stu-id="4e134-142">Running scripts on other computers</span></span>

<span data-ttu-id="4e134-143">若要在一或多部遠端電腦上執行腳本，請使用 Cmdlet 的 **FilePath** 參數 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="4e134-143">To run a script on one or more remote computers, use the **FilePath** parameter of the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="4e134-144">輸入腳本的路徑和檔案名作為 **FilePath** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="4e134-144">Enter the path and filename of the script as the value of the **FilePath** parameter.</span></span> <span data-ttu-id="4e134-145">指令碼必須位於本機電腦上，或在本機電腦可以存取的目錄中。</span><span class="sxs-lookup"><span data-stu-id="4e134-145">The script must reside on the local computer or in a directory that the local computer can access.</span></span>

<span data-ttu-id="4e134-146">下列命令會 `Get-ServiceLog.ps1` 在名為 Server01 和 Server02 的遠端電腦上執行腳本。</span><span class="sxs-lookup"><span data-stu-id="4e134-146">The following command runs the `Get-ServiceLog.ps1` script on the remote computers named Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01,Server02 -FilePath `
  C:\Scripts\Get-ServiceLog.ps1
```

## <a name="get-help-for-scripts"></a><span data-ttu-id="4e134-147">取得腳本的說明</span><span class="sxs-lookup"><span data-stu-id="4e134-147">Get help for scripts</span></span>

<span data-ttu-id="4e134-148">Get-Help Cmdlet 會取得腳本的說明主題，以及 Cmdlet 和其他命令類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="4e134-148">The Get-Help cmdlet gets the help topics for scripts as well as for cmdlets and other types of commands.</span></span> <span data-ttu-id="4e134-149">若要取得腳本的說明主題，請輸入，然後輸入 `Get-Help` 腳本的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="4e134-149">To get the help topic for a script, type `Get-Help` followed by the path and filename of the script.</span></span> <span data-ttu-id="4e134-150">如果腳本路徑是在您的 `Path` 環境變數中，則您可以省略路徑。</span><span class="sxs-lookup"><span data-stu-id="4e134-150">If the script path is in your `Path` environment variable, you can omit the path.</span></span>

<span data-ttu-id="4e134-151">例如，若要取得 ServicesLog.ps1 腳本的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4e134-151">For example, to get help for the ServicesLog.ps1 script, type:</span></span>

```powershell
get-help C:\admin\scripts\ServicesLog.ps1
```

## <a name="how-to-write-a-script"></a><span data-ttu-id="4e134-152">如何撰寫腳本</span><span class="sxs-lookup"><span data-stu-id="4e134-152">How to write a script</span></span>

<span data-ttu-id="4e134-153">腳本可以包含任何有效的 PowerShell 命令，包括單一命令、使用管線的命令、函數，以及 If 語句和 For 迴圈等控制結構。</span><span class="sxs-lookup"><span data-stu-id="4e134-153">A script can contain any valid PowerShell commands, including single commands, commands that use the pipeline, functions, and control structures such as If statements and For loops.</span></span>

<span data-ttu-id="4e134-154">若要撰寫腳本，請在文字編輯器中開啟新檔案、輸入命令，然後將它們儲存在副檔名為有效的檔案名的檔案中 `.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="4e134-154">To write a script, open a new file in a text editor, type the commands, and save them in a file with a valid filename with the `.ps1` file extension.</span></span>

<span data-ttu-id="4e134-155">下列範例是一個簡單的腳本，可取得目前系統上執行的服務，並將它們儲存至記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4e134-155">The following example is a simple script that gets the services that are running on the current system and saves them to a log file.</span></span> <span data-ttu-id="4e134-156">記錄檔檔案名會從目前的日期建立。</span><span class="sxs-lookup"><span data-stu-id="4e134-156">The log filename is created from the current date.</span></span>

```powershell
$date = (get-date).dayofyear
get-service | out-file "$date.log"
```

<span data-ttu-id="4e134-157">若要建立此腳本，請開啟文字編輯器或腳本編輯器、輸入這些命令，然後將它們儲存在名為的檔案中 `ServiceLog.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="4e134-157">To create this script, open a text editor or a script editor, type these commands, and then save them in a file named `ServiceLog.ps1`.</span></span>

### <a name="parameters-in-scripts"></a><span data-ttu-id="4e134-158">腳本中的參數</span><span class="sxs-lookup"><span data-stu-id="4e134-158">Parameters in scripts</span></span>

<span data-ttu-id="4e134-159">若要在腳本中定義參數，請使用 Param 語句。</span><span class="sxs-lookup"><span data-stu-id="4e134-159">To define parameters in a script, use a Param statement.</span></span> <span data-ttu-id="4e134-160">`Param`語句必須是腳本中的第一個語句，除了批註和任何語句之外 `#Require` 。</span><span class="sxs-lookup"><span data-stu-id="4e134-160">The `Param` statement must be the first statement in a script, except for comments and any `#Require` statements.</span></span>

<span data-ttu-id="4e134-161">腳本參數的運作方式類似于函式參數。</span><span class="sxs-lookup"><span data-stu-id="4e134-161">Script parameters work like function parameters.</span></span> <span data-ttu-id="4e134-162">參數值可供腳本中的所有命令使用。</span><span class="sxs-lookup"><span data-stu-id="4e134-162">The parameter values are available to all of the commands in the script.</span></span> <span data-ttu-id="4e134-163">函數參數的所有功能（包括參數屬性和其具名引數）在腳本中也有效。</span><span class="sxs-lookup"><span data-stu-id="4e134-163">All of the features of function parameters, including the Parameter attribute and its named arguments, are also valid in scripts.</span></span>

<span data-ttu-id="4e134-164">執行腳本時，腳本使用者在腳本名稱之後輸入參數。</span><span class="sxs-lookup"><span data-stu-id="4e134-164">When running the script, script users type the parameters after the script name.</span></span>

<span data-ttu-id="4e134-165">下列範例顯示 `Test-Remote.ps1` 具有 **ComputerName** 參數的腳本。</span><span class="sxs-lookup"><span data-stu-id="4e134-165">The following example shows a `Test-Remote.ps1` script that has a **ComputerName** parameter.</span></span> <span data-ttu-id="4e134-166">這兩個腳本函數都可以存取 **ComputerName** 參數值。</span><span class="sxs-lookup"><span data-stu-id="4e134-166">Both of the script functions can access the **ComputerName** parameter value.</span></span>

```powershell
param ($ComputerName = $(throw "ComputerName parameter is required."))

function CanPing {
   $error.clear()
   $tmp = test-connection $computername -erroraction SilentlyContinue

   if (!$?)
       {write-host "Ping failed: $ComputerName."; return $false}
   else
       {write-host "Ping succeeded: $ComputerName"; return $true}
}

function CanRemote {
    $s = new-pssession $computername -erroraction SilentlyContinue

    if ($s -is [System.Management.Automation.Runspaces.PSSession])
        {write-host "Remote test succeeded: $ComputerName."}
    else
        {write-host "Remote test failed: $ComputerName."}
}

if (CanPing $computername) {CanRemote $computername}
```

<span data-ttu-id="4e134-167">若要執行此腳本，請在腳本名稱後面輸入參數名稱。</span><span class="sxs-lookup"><span data-stu-id="4e134-167">To run this script, type the parameter name after the script name.</span></span> <span data-ttu-id="4e134-168">例如：</span><span class="sxs-lookup"><span data-stu-id="4e134-168">For example:</span></span>

```powershell
C:\PS> .\test-remote.ps1 -computername Server01

Ping succeeded: Server01
Remote test failed: Server01
```

<span data-ttu-id="4e134-169">如需 Param 語句和函數參數的詳細資訊，請參閱 [about_Functions](about_Functions.md) 和 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="4e134-169">For more information about the Param statement and the function parameters, see [about_Functions](about_Functions.md) and [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="writing-help-for-scripts"></a><span data-ttu-id="4e134-170">撰寫腳本的說明</span><span class="sxs-lookup"><span data-stu-id="4e134-170">Writing help for scripts</span></span>

<span data-ttu-id="4e134-171">您可以使用下列兩種方法之一來撰寫腳本的說明主題：</span><span class="sxs-lookup"><span data-stu-id="4e134-171">You can write a help topic for a script by using either of the two following methods:</span></span>

- <span data-ttu-id="4e134-172">腳本的 Comment-Based 說明</span><span class="sxs-lookup"><span data-stu-id="4e134-172">Comment-Based Help for Scripts</span></span>

  <span data-ttu-id="4e134-173">使用批註中的特殊關鍵字來建立說明主題。</span><span class="sxs-lookup"><span data-stu-id="4e134-173">Create a Help topic by using special keywords in the comments.</span></span> <span data-ttu-id="4e134-174">若要為腳本建立以批註為基礎的說明，必須將批註放在腳本檔案的開頭或結尾。</span><span class="sxs-lookup"><span data-stu-id="4e134-174">To create comment-based Help for a script, the comments must be placed at the beginning or end of the script file.</span></span> <span data-ttu-id="4e134-175">如需以批註為基礎的說明的詳細資訊，請參閱 [about_Comment_Based_Help](about_Comment_Based_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="4e134-175">For more information about comment-based Help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="4e134-176">腳本的 XML-Based 說明</span><span class="sxs-lookup"><span data-stu-id="4e134-176">XML-Based Help  for Scripts</span></span>

  <span data-ttu-id="4e134-177">建立以 XML 為基礎的說明主題，例如通常為 Cmdlet 建立的類型。</span><span class="sxs-lookup"><span data-stu-id="4e134-177">Create an XML-based Help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="4e134-178">如果您要將說明主題翻譯成多種語言，則需要以 XML 為基礎的說明。</span><span class="sxs-lookup"><span data-stu-id="4e134-178">XML-based Help is required if you are translating Help topics into multiple languages.</span></span>

<span data-ttu-id="4e134-179">若要將腳本與以 XML 為基礎的說明主題產生關聯，請使用。.Externalhelp Help comment 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4e134-179">To associate the script with the XML-based Help topic, use the .ExternalHelp Help comment keyword.</span></span> <span data-ttu-id="4e134-180">如需 .Externalhelp 關鍵字的詳細資訊，請參閱 [about_Comment_Based_Help](about_Comment_Based_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="4e134-180">For more information about the ExternalHelp keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="4e134-181">如需以 XML 為基礎之說明的詳細資訊，請參閱 [如何撰寫 Cmdlet 說明](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)。</span><span class="sxs-lookup"><span data-stu-id="4e134-181">For more information about XML-based help, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

### <a name="returning-an-exit-value"></a><span data-ttu-id="4e134-182">傳回結束值</span><span class="sxs-lookup"><span data-stu-id="4e134-182">Returning an exit value</span></span>

<span data-ttu-id="4e134-183">根據預設，腳本結束時，腳本不會傳回結束狀態。</span><span class="sxs-lookup"><span data-stu-id="4e134-183">By default, scripts do not return an exit status when the script ends.</span></span> <span data-ttu-id="4e134-184">您必須使用 `exit` 語句來傳回腳本的結束代碼。</span><span class="sxs-lookup"><span data-stu-id="4e134-184">You must use the `exit` statement to return an exit code from a script.</span></span> <span data-ttu-id="4e134-185">根據預設， `exit` 語句會傳回 `0` 。</span><span class="sxs-lookup"><span data-stu-id="4e134-185">By default, the `exit` statement returns `0`.</span></span> <span data-ttu-id="4e134-186">您可以提供數值來傳回不同的結束狀態。</span><span class="sxs-lookup"><span data-stu-id="4e134-186">You can provide a numeric value to return a different exit status.</span></span> <span data-ttu-id="4e134-187">非零的結束代碼通常會發出錯誤信號。</span><span class="sxs-lookup"><span data-stu-id="4e134-187">A nonzero exit code typically signals a failure.</span></span>

<span data-ttu-id="4e134-188">在 Windows 上，允許和之間的任何數位 `[int]::MinValue` `[int]::MaxValue` 。</span><span class="sxs-lookup"><span data-stu-id="4e134-188">On Windows, any number between `[int]::MinValue` and `[int]::MaxValue` is allowed.</span></span>

<span data-ttu-id="4e134-189">在 Unix 上，只 `[byte]::MinValue` 允許 (0) 和 `[byte]::MaxValue` (255) 之間的正數。</span><span class="sxs-lookup"><span data-stu-id="4e134-189">On Unix, only positive numbers between `[byte]::MinValue` (0) and `[byte]::MaxValue` (255) are allowed.</span></span> <span data-ttu-id="4e134-190">範圍中的負數會 `-1` `-255` 自動轉譯為正數，方法是新增</span><span class="sxs-lookup"><span data-stu-id="4e134-190">A negative number in the range of `-1` through `-255` is automatically translated into a positive number by adding</span></span>
256. <span data-ttu-id="4e134-191">例如， `-2` 會轉換成 `254` 。</span><span class="sxs-lookup"><span data-stu-id="4e134-191">For example, `-2` is transformed to `254`.</span></span>

<span data-ttu-id="4e134-192">在 PowerShell 中， `exit` 語句會設定變數的值 `$LASTEXITCODE` 。</span><span class="sxs-lookup"><span data-stu-id="4e134-192">In PowerShell, the `exit` statement sets the value of the `$LASTEXITCODE` variable.</span></span> <span data-ttu-id="4e134-193">在 Windows 命令 Shell ( # A0) 中，exit 語句會設定環境變數的值 `%ERRORLEVEL%` 。</span><span class="sxs-lookup"><span data-stu-id="4e134-193">In the Windows Command Shell (cmd.exe), the exit statement sets the value of the `%ERRORLEVEL%` environment variable.</span></span>

<span data-ttu-id="4e134-194">任何非數位或外部平臺特定範圍的引數，都會轉譯為的值 `0` 。</span><span class="sxs-lookup"><span data-stu-id="4e134-194">Any argument that is non-numeric or outside the platform-specific range is translated to the value of `0`.</span></span>

## <a name="script-scope-and-dot-sourcing"></a><span data-ttu-id="4e134-195">腳本範圍和點的來源</span><span class="sxs-lookup"><span data-stu-id="4e134-195">Script scope and dot sourcing</span></span>

<span data-ttu-id="4e134-196">每個腳本都是在它自己的範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="4e134-196">Each script runs in its own scope.</span></span> <span data-ttu-id="4e134-197">在腳本中建立的函式、變數、別名和磁片磁碟機只存在於腳本範圍中。</span><span class="sxs-lookup"><span data-stu-id="4e134-197">The functions, variables, aliases, and drives that are created in the script exist only in the script scope.</span></span> <span data-ttu-id="4e134-198">您無法在腳本執行的範圍中存取這些專案或其值。</span><span class="sxs-lookup"><span data-stu-id="4e134-198">You cannot access these items or their values in the scope in which the script runs.</span></span>

<span data-ttu-id="4e134-199">若要在不同範圍中執行腳本，您可以指定範圍（例如 Global 或 Local），或在腳本中使用點（source）。</span><span class="sxs-lookup"><span data-stu-id="4e134-199">To run a script in a different scope, you can specify a scope, such as Global or Local, or you can dot source the script.</span></span>

<span data-ttu-id="4e134-200">「點為來源」功能可讓您在目前的範圍中執行腳本，而不是在腳本範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="4e134-200">The dot sourcing feature lets you run a script in the current scope instead of in the script scope.</span></span> <span data-ttu-id="4e134-201">當您執行以點為來源的腳本時，腳本中的命令會以您在命令提示字元中輸入它們的方式執行。</span><span class="sxs-lookup"><span data-stu-id="4e134-201">When you run a script that is dot sourced, the commands in the script run as though you had typed them at the command prompt.</span></span> <span data-ttu-id="4e134-202">腳本所建立的函式、變數、別名和磁片磁碟機會在您工作的範圍內建立。</span><span class="sxs-lookup"><span data-stu-id="4e134-202">The functions, variables, aliases, and drives that the script creates are created in the scope in which you are working.</span></span> <span data-ttu-id="4e134-203">腳本執行之後，您可以使用所建立的專案，並存取其在會話中的值。</span><span class="sxs-lookup"><span data-stu-id="4e134-203">After the script runs, you can use the created items and access their values in your session.</span></span>

<span data-ttu-id="4e134-204">若為點來源 a 腳本，請在腳本路徑前面輸入一個點 (. ) 和一個空格。</span><span class="sxs-lookup"><span data-stu-id="4e134-204">To dot source a script, type a dot (.) and a space before the script path.</span></span>

<span data-ttu-id="4e134-205">例如：</span><span class="sxs-lookup"><span data-stu-id="4e134-205">For example:</span></span>

```powershell
. C:\scripts\UtilityFunctions.ps1
```

<span data-ttu-id="4e134-206">或</span><span class="sxs-lookup"><span data-stu-id="4e134-206">or</span></span>

```powershell
. .\UtilityFunctions.ps1
```

<span data-ttu-id="4e134-207">`UtilityFunctions.ps1`腳本執行之後，腳本所建立的函式和變數就會新增至目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="4e134-207">After the `UtilityFunctions.ps1` script runs, the functions and variables that the script creates are added to the current scope.</span></span>

<span data-ttu-id="4e134-208">例如，腳本會 `UtilityFunctions.ps1` 建立 `New-Profile` 函數和 `$ProfileName` 變數。</span><span class="sxs-lookup"><span data-stu-id="4e134-208">For example, the `UtilityFunctions.ps1` script creates the `New-Profile` function and the `$ProfileName` variable.</span></span>

```powershell
#In UtilityFunctions.ps1

function New-Profile
{
  Write-Host "Running New-Profile function"
  $profileName = split-path $profile -leaf

  if (test-path $profile)
    {write-error "Profile $profileName already exists on this computer."}
  else
    {new-item -type file -path $profile -force }
}
```

<span data-ttu-id="4e134-209">如果您 `UtilityFunctions.ps1` 在自己的腳本範圍中執行腳本，則 `New-Profile` 只有在腳本執行時，函式和 `$ProfileName` 變數才會存在。</span><span class="sxs-lookup"><span data-stu-id="4e134-209">If you run the `UtilityFunctions.ps1` script in its own script scope, the `New-Profile` function and the `$ProfileName` variable exist only while the script is running.</span></span> <span data-ttu-id="4e134-210">當腳本結束時，會移除函式和變數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4e134-210">When the script exits, the function and variable are removed, as shown in the following example.</span></span>

```powershell
C:\PS> .\UtilityFunctions.ps1

C:\PS> New-Profile
The term 'new-profile' is not recognized as a cmdlet, function, operable
program, or script file. Verify the term and try again.
At line:1 char:12
+ new-profile <<<<
   + CategoryInfo          : ObjectNotFound: (new-profile:String) [],
   + FullyQualifiedErrorId : CommandNotFoundException

C:\PS> $profileName
C:\PS>
```

<span data-ttu-id="4e134-211">當您的點來源為腳本並執行時，腳本會在您的範圍內的會話中建立函式 `New-Profile` 和 `$ProfileName` 變數。</span><span class="sxs-lookup"><span data-stu-id="4e134-211">When you dot source the script and run it, the script creates the `New-Profile` function and the `$ProfileName` variable in your session in your scope.</span></span> <span data-ttu-id="4e134-212">腳本執行之後，您可以 `New-Profile` 在會話中使用函數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4e134-212">After the script runs, you can use the `New-Profile` function in your session, as shown in the following example.</span></span>

```powershell
C:\PS> . .\UtilityFunctions.ps1

C:\PS> New-Profile

    Directory: C:\Users\juneb\Documents\WindowsPowerShell

    Mode    LastWriteTime     Length Name
    ----    -------------     ------ ----
    -a---   1/14/2009 3:08 PM      0 Microsoft.PowerShellISE_profile.ps1

C:\PS> $profileName
Microsoft.PowerShellISE_profile.ps1
```

<span data-ttu-id="4e134-213">如需範圍的詳細資訊，請參閱 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="4e134-213">For more information about scope, see about_Scopes.</span></span>

## <a name="scripts-in-modules"></a><span data-ttu-id="4e134-214">模組中的腳本</span><span class="sxs-lookup"><span data-stu-id="4e134-214">Scripts in modules</span></span>

<span data-ttu-id="4e134-215">模組是一組相關的 PowerShell 資源，可作為一個單位來散發。</span><span class="sxs-lookup"><span data-stu-id="4e134-215">A module is a set of related PowerShell resources that can be distributed as a unit.</span></span> <span data-ttu-id="4e134-216">您可以使用模組來組織您的腳本、函數和其他資源。</span><span class="sxs-lookup"><span data-stu-id="4e134-216">You can use modules to organize your scripts, functions, and other resources.</span></span> <span data-ttu-id="4e134-217">您也可以使用模組，將程式碼散發給其他人，並取得來自信任來源的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4e134-217">You can also use modules to distribute your code to others, and to get code from trusted sources.</span></span>

<span data-ttu-id="4e134-218">您可以將腳本包含在模組中，也可以建立腳本模組，這是完全或主要由腳本和支援資源所組成的模組。</span><span class="sxs-lookup"><span data-stu-id="4e134-218">You can include scripts in your modules, or you can create a script module, which is a module that consists entirely or primarily of a script and supporting resources.</span></span> <span data-ttu-id="4e134-219">腳本模組只是副檔名為 .psm1 的腳本。</span><span class="sxs-lookup"><span data-stu-id="4e134-219">A script module is just a script with a .psm1 file extension.</span></span>

<span data-ttu-id="4e134-220">如需模組的詳細資訊，請參閱 [about_Modules](about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="4e134-220">For more information about modules, see [about_Modules](about_Modules.md).</span></span>

## <a name="other-script-features"></a><span data-ttu-id="4e134-221">其他腳本功能</span><span class="sxs-lookup"><span data-stu-id="4e134-221">Other script features</span></span>

<span data-ttu-id="4e134-222">PowerShell 有許多有用的功能，可供您在腳本中使用。</span><span class="sxs-lookup"><span data-stu-id="4e134-222">PowerShell has many useful features that you can use in scripts.</span></span>

- <span data-ttu-id="4e134-223">`#Requires` -您可以使用 `#Requires` 語句來防止腳本在沒有指定的模組或嵌入式管理單元和指定的 PowerShell 版本的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="4e134-223">`#Requires` - You can use a `#Requires` statement to prevent a script from running without specified modules or snap-ins and a specified version of PowerShell.</span></span> <span data-ttu-id="4e134-224">如需詳細資訊，請參閱 about_Requires。</span><span class="sxs-lookup"><span data-stu-id="4e134-224">For more information, see about_Requires.</span></span>

- <span data-ttu-id="4e134-225">`$PSCommandPath` -包含正在執行之腳本的完整路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="4e134-225">`$PSCommandPath` - Contains the full path and name of the script that is being run.</span></span> <span data-ttu-id="4e134-226">此參數在所有腳本中都是有效的。</span><span class="sxs-lookup"><span data-stu-id="4e134-226">This parameter is valid in all scripts.</span></span> <span data-ttu-id="4e134-227">此自動變數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="4e134-227">This automatic variable is introduced in PowerShell 3.0.</span></span>

- <span data-ttu-id="4e134-228">`$PSScriptRoot` -包含執行腳本的目錄。</span><span class="sxs-lookup"><span data-stu-id="4e134-228">`$PSScriptRoot` - Contains the directory from which a script is being run.</span></span> <span data-ttu-id="4e134-229">在 PowerShell 2.0 中，此變數僅適用于腳本模組 (`.psm1`) 。</span><span class="sxs-lookup"><span data-stu-id="4e134-229">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
  <span data-ttu-id="4e134-230">從 PowerShell 3.0 開始，它在所有腳本中都是有效的。</span><span class="sxs-lookup"><span data-stu-id="4e134-230">Beginning in PowerShell 3.0, it is valid in all scripts.</span></span>

- <span data-ttu-id="4e134-231">`$MyInvocation` - `$MyInvocation` 自動變數包含目前腳本的相關資訊，包括其啟動或「叫用」的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4e134-231">`$MyInvocation` - The `$MyInvocation` automatic variable contains information about the current script, including information about how it was started or "invoked."</span></span> <span data-ttu-id="4e134-232">當腳本正在執行時，您可以使用此變數及其屬性來取得腳本的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4e134-232">You can use this variable and its properties to get information about the script while it is running.</span></span> <span data-ttu-id="4e134-233">例如， `$MyInvocation` 。MyCommand： Path 變數包含腳本的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="4e134-233">For example, the `$MyInvocation`.MyCommand.Path variable contains the path and filename of the script.</span></span> <span data-ttu-id="4e134-234">`$MyInvocation`.行包含啟動腳本的命令，包括所有參數和值。</span><span class="sxs-lookup"><span data-stu-id="4e134-234">`$MyInvocation`.Line contains the command that started the script, including all parameters and values.</span></span>

  <span data-ttu-id="4e134-235">從 PowerShell 3.0 開始， `$MyInvocation` 有兩個新的屬性，提供呼叫或叫用目前腳本之腳本的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4e134-235">Beginning in PowerShell 3.0, `$MyInvocation` has two new properties that provide information about the script that called or invoked the current script.</span></span> <span data-ttu-id="4e134-236">只有當啟動程式或呼叫端為腳本時，才會填入這些屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4e134-236">The values of these properties are populated only when the invoker or caller is a script.</span></span>

  - <span data-ttu-id="4e134-237">**PSCommandPath** 包含呼叫或叫用目前腳本之腳本的完整路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="4e134-237">**PSCommandPath** contains the full path and name of the script that called or invoked the current script.</span></span>

  - <span data-ttu-id="4e134-238">**PSScriptRoot** 包含呼叫或叫用目前腳本之腳本的目錄。</span><span class="sxs-lookup"><span data-stu-id="4e134-238">**PSScriptRoot** contains the directory of the script that called or invoked the current script.</span></span>

  <span data-ttu-id="4e134-239">不同于 `$PSCommandPath` 和 `$PSScriptRoot` 自動變數（包含目前腳本的相關資訊），變數的 **PSCommandPath** 和 **PSScriptRoot** 屬性 `$MyInvocation` 會包含呼叫目前腳本之腳本的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4e134-239">Unlike the `$PSCommandPath` and `$PSScriptRoot` automatic variables, which contain information about the current script, the **PSCommandPath** and **PSScriptRoot** properties of the `$MyInvocation` variable contain information about the script that called the current script.</span></span>

- <span data-ttu-id="4e134-240">資料區段-您可以使用 `Data` 關鍵字來分隔腳本中的邏輯資料。</span><span class="sxs-lookup"><span data-stu-id="4e134-240">Data sections - You can use the `Data` keyword to separate data from logic in scripts.</span></span> <span data-ttu-id="4e134-241">資料區段也可以簡化當地語系化作業。</span><span class="sxs-lookup"><span data-stu-id="4e134-241">Data sections can also make localization easier.</span></span> <span data-ttu-id="4e134-242">如需詳細資訊，請參閱 [about_Data_Sections](about_Data_Sections.md) 和 [about_Script_Internationalization](about_Script_Internationalization.md)。</span><span class="sxs-lookup"><span data-stu-id="4e134-242">For more information, see [about_Data_Sections](about_Data_Sections.md) and [about_Script_Internationalization](about_Script_Internationalization.md).</span></span>

- <span data-ttu-id="4e134-243">腳本簽署-您可以將數位簽章新增至腳本。</span><span class="sxs-lookup"><span data-stu-id="4e134-243">Script Signing - You can add a digital signature to a script.</span></span> <span data-ttu-id="4e134-244">視執行原則而定，您可以使用數位簽章來限制可能包含 unsafe 命令的腳本執行。</span><span class="sxs-lookup"><span data-stu-id="4e134-244">Depending on the execution policy, you can use digital signatures to restrict the running of scripts that could include unsafe commands.</span></span> <span data-ttu-id="4e134-245">如需詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md) 和 [about_Signing](about_Signing.md)。</span><span class="sxs-lookup"><span data-stu-id="4e134-245">For more information, see [about_Execution_Policies](about_Execution_Policies.md) and [about_Signing](about_Signing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e134-246">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e134-246">See also</span></span>

[<span data-ttu-id="4e134-247">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="4e134-247">about_Command_Precedence</span></span>](about_Command_Precedence.md)

[<span data-ttu-id="4e134-248">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="4e134-248">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="4e134-249">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="4e134-249">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="4e134-250">about_Functions</span><span class="sxs-lookup"><span data-stu-id="4e134-250">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="4e134-251">about_Modules</span><span class="sxs-lookup"><span data-stu-id="4e134-251">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="4e134-252">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="4e134-252">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="4e134-253">about_Requires</span><span class="sxs-lookup"><span data-stu-id="4e134-253">about_Requires</span></span>](about_Requires.md)

[<span data-ttu-id="4e134-254">about_Run_With_PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e134-254">about_Run_With_PowerShell</span></span>](about_Run_With_PowerShell.md)

[<span data-ttu-id="4e134-255">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="4e134-255">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="4e134-256">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="4e134-256">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="4e134-257">about_Signing</span><span class="sxs-lookup"><span data-stu-id="4e134-257">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="4e134-258">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="4e134-258">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
