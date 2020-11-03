---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: ade80115f85cb241fdf0dc4e829daa5b381644ef
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "93205831"
---
# <span data-ttu-id="dbcfd-103">Start-Process</span><span class="sxs-lookup"><span data-stu-id="dbcfd-103">Start-Process</span></span>

## <span data-ttu-id="dbcfd-104">概要</span><span class="sxs-lookup"><span data-stu-id="dbcfd-104">SYNOPSIS</span></span>
<span data-ttu-id="dbcfd-105">啟動本機電腦上的一或多個處理程序。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-105">Starts one or more processes on the local computer.</span></span>

## <span data-ttu-id="dbcfd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dbcfd-106">SYNTAX</span></span>

### <span data-ttu-id="dbcfd-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="dbcfd-107">Default (Default)</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dbcfd-108">UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="dbcfd-108">UseShellExecute</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="dbcfd-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dbcfd-109">DESCRIPTION</span></span>

<span data-ttu-id="dbcfd-110">`Start-Process`Cmdlet 會在本機電腦上啟動一或多個處理常式。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-110">The `Start-Process` cmdlet starts one or more processes on the local computer.</span></span> <span data-ttu-id="dbcfd-111">依預設， `Start-Process` 會建立新的進程，以繼承目前進程中定義的所有環境變數。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-111">By default, `Start-Process` creates a new process that inherits all the environment variables that are defined in the current process.</span></span>

<span data-ttu-id="dbcfd-112">如果要指定在處理程序中執行的程式，請輸入可執行檔或指令碼檔案，或可使用電腦上的程式開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-112">To specify the program that runs in the process, enter an executable file or script file, or a file that can be opened by using a program on the computer.</span></span> <span data-ttu-id="dbcfd-113">如果您指定無法執行的檔案，則 `Start-Process` 會啟動與檔案相關聯的程式，類似于 `Invoke-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-113">If you specify a non-executable file, `Start-Process` starts the program that is associated with the file, similar to the `Invoke-Item` cmdlet.</span></span>

<span data-ttu-id="dbcfd-114">您可以使用的參數 `Start-Process` 來指定選項，例如載入使用者設定檔、在新視窗中啟動進程，或使用替代認證。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-114">You can use the parameters of `Start-Process` to specify options, such as loading a user profile, starting the process in a new window, or using alternate credentials.</span></span>

## <span data-ttu-id="dbcfd-115">範例</span><span class="sxs-lookup"><span data-stu-id="dbcfd-115">EXAMPLES</span></span>

### <span data-ttu-id="dbcfd-116">範例1：啟動使用預設值的處理常式</span><span class="sxs-lookup"><span data-stu-id="dbcfd-116">Example 1: Start a process that uses default values</span></span>

<span data-ttu-id="dbcfd-117">此範例會啟動使用目前資料夾中之檔案的處理常式 `Sort.exe` 。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-117">This example starts a process that uses the `Sort.exe` file in the current folder.</span></span> <span data-ttu-id="dbcfd-118">此命令會使用所有預設值，包括預設視窗樣式、工作資料夾和認證。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-118">The command uses all of the default values, including the default window style, working folder, and credentials.</span></span>

```powershell
Start-Process -FilePath "sort.exe"
```

### <span data-ttu-id="dbcfd-119">範例2：列印文字檔</span><span class="sxs-lookup"><span data-stu-id="dbcfd-119">Example 2: Print a text file</span></span>

<span data-ttu-id="dbcfd-120">此範例會啟動列印檔案的處理常式 `C:\PS-Test\MyFile.txt` 。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-120">This example starts a process that prints the `C:\PS-Test\MyFile.txt` file.</span></span>

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### <span data-ttu-id="dbcfd-121">範例3：啟動將專案排序至新檔案的進程</span><span class="sxs-lookup"><span data-stu-id="dbcfd-121">Example 3: Start a process to sort items to a new file</span></span>

<span data-ttu-id="dbcfd-122">此範例會啟動一個進程，以排序檔案中 `Testsort.txt` 的專案，並傳回檔案中已排序的專案 `Sorted.txt` 。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-122">This example starts a process that sorts items in the `Testsort.txt` file and returns the sorted items in the `Sorted.txt` files.</span></span> <span data-ttu-id="dbcfd-123">任何錯誤都會寫入至檔案 `SortError.txt` 。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-123">Any errors are written to the `SortError.txt` file.</span></span>

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

<span data-ttu-id="dbcfd-124">**UseNewEnvironment** 參數會指定進程會以自己的環境變數執行。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-124">The **UseNewEnvironment** parameter specifies that the process runs with its own environment variables.</span></span>

### <span data-ttu-id="dbcfd-125">範例4：在最大化的視窗中啟動進程</span><span class="sxs-lookup"><span data-stu-id="dbcfd-125">Example 4: Start a process in a maximized window</span></span>

<span data-ttu-id="dbcfd-126">此範例會啟動 `Notepad.exe` 進程。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-126">This example starts the `Notepad.exe` process.</span></span> <span data-ttu-id="dbcfd-127">在處理程序完成前，它會最大化視窗並保留視窗。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-127">It maximizes the window and retains the window until the process completes.</span></span>

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### <span data-ttu-id="dbcfd-128">範例5：以系統管理員身分啟動 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dbcfd-128">Example 5: Start PowerShell as an administrator</span></span>

<span data-ttu-id="dbcfd-129">此範例會使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-129">This example starts PowerShell by using the **Run as administrator** option.</span></span>

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### <span data-ttu-id="dbcfd-130">範例6：使用不同的動詞來啟動處理常式</span><span class="sxs-lookup"><span data-stu-id="dbcfd-130">Example 6: Using different verbs to start a process</span></span>

<span data-ttu-id="dbcfd-131">此範例顯示如何尋找啟動處理常式時可使用的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-131">This example shows how to find the verbs that can be used when starting a process.</span></span> <span data-ttu-id="dbcfd-132">可用的動詞取決於處理常式中執行之檔案的檔案名副檔名。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-132">The available verbs are determined by the filename extension of the file that runs in the process.</span></span>

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

<span data-ttu-id="dbcfd-133">此範例會使用 `New-Object` 來建立 **PowerShell.exe** 的 **ProcessStartInfo** 物件，這是在 PowerShell 處理常式中執行的檔案。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-133">The example uses `New-Object` to create a **System.Diagnostics.ProcessStartInfo** object for **PowerShell.exe** , the file that runs in the PowerShell process.</span></span> <span data-ttu-id="dbcfd-134">**ProcessStartInfo** 物件的 **動詞** 屬性顯示您可以使用 **Open** 和 **RunAs** 動詞搭配或執行檔案的 `PowerShell.exe` 任何進程 `.exe` 。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-134">The **Verbs** property of the **ProcessStartInfo** object shows that you can use the **Open** and **RunAs** verbs with `PowerShell.exe`, or with any process that runs a `.exe` file.</span></span>

### <span data-ttu-id="dbcfd-135">範例7：指定進程的引數</span><span class="sxs-lookup"><span data-stu-id="dbcfd-135">Example 7: Specifying arguments to the process</span></span>

<span data-ttu-id="dbcfd-136">這兩個命令都會啟動 Windows 命令直譯器，並 `dir` 在資料夾上發出命令 `Program Files` 。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-136">Both commands start the Windows command interpreter, issuing a `dir` command on the `Program Files` folder.</span></span> <span data-ttu-id="dbcfd-137">因為此資料夾包含空格，所以值需要以引號括住。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-137">Because this foldername contains a space, the value needs surrounded with escaped quotes.</span></span>
<span data-ttu-id="dbcfd-138">請注意，第一個命令會將字串指定為 **ArgumentList** 。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-138">Note that the first command specifies a string as **ArgumentList** .</span></span> <span data-ttu-id="dbcfd-139">第二個命令是字串陣列。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-139">The second command is a string array.</span></span>

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

## <span data-ttu-id="dbcfd-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dbcfd-140">PARAMETERS</span></span>

### <span data-ttu-id="dbcfd-141">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="dbcfd-141">-ArgumentList</span></span>

<span data-ttu-id="dbcfd-142">指定此 Cmdlet 啟動進程時要使用的參數或參數值。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-142">Specifies parameters or parameter values to use when this cmdlet starts the process.</span></span> <span data-ttu-id="dbcfd-143">引數可以接受為具有以空格分隔之引數的單一字串，或是以逗號分隔的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-143">Arguments can be accepted as a single string with the arguments separated by spaces, or as an array of strings separated by commas.</span></span>

<span data-ttu-id="dbcfd-144">如果參數或參數值包含空格，則必須以換用雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-144">If parameters or parameter values contain a space, they need to be surrounded with escaped double quotes.</span></span> <span data-ttu-id="dbcfd-145">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-145">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="dbcfd-146">-Credential</span></span>

<span data-ttu-id="dbcfd-147">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-147">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="dbcfd-148">根據預設，Cmdlet 會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-148">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="dbcfd-149">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-149">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="dbcfd-150">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-150">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="dbcfd-151">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-151">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="dbcfd-152">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-152">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Default
Aliases: RunAs

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-153">-FilePath</span><span class="sxs-lookup"><span data-stu-id="dbcfd-153">-FilePath</span></span>

<span data-ttu-id="dbcfd-154">指定在處理常式中執行之程式的選擇性路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-154">Specifies the optional path and filename of the program that runs in the process.</span></span> <span data-ttu-id="dbcfd-155">輸入 `.txt` `.doc` 與電腦上程式相關聯之可執行檔或檔（例如或檔案）的名稱。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-155">Enter the name of an executable file or of a document, such as a `.txt` or `.doc` file, that is associated with a program on the computer.</span></span> <span data-ttu-id="dbcfd-156">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-156">This parameter is required.</span></span>

<span data-ttu-id="dbcfd-157">如果您只指定檔案名，請使用 **WorkingDirectory** 參數來指定路徑。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-157">If you specify only a filename, use the **WorkingDirectory** parameter to specify the path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-158">-LoadUserProfile</span><span class="sxs-lookup"><span data-stu-id="dbcfd-158">-LoadUserProfile</span></span>

<span data-ttu-id="dbcfd-159">指出此 Cmdlet 會載入儲存在目前使用者的登錄機碼中的 Windows 使用者設定檔 `HKEY_USERS` 。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-159">Indicates that this cmdlet loads the Windows user profile stored in the `HKEY_USERS` registry key for the current user.</span></span> <span data-ttu-id="dbcfd-160">參數不適用於非 Windows 系統。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-160">The parameter does not apply for non-Windows systems.</span></span>

<span data-ttu-id="dbcfd-161">此參數不會影響 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-161">This parameter does not affect the PowerShell profiles.</span></span> <span data-ttu-id="dbcfd-162">如需詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-162">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: Lup

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-163">-NoNewWindow</span><span class="sxs-lookup"><span data-stu-id="dbcfd-163">-NoNewWindow</span></span>

<span data-ttu-id="dbcfd-164">在目前的主控台視窗中啟動新的處理程序。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-164">Start the new process in the current console window.</span></span> <span data-ttu-id="dbcfd-165">根據預設，在 Windows 上，PowerShell 會開啟新的視窗。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-165">By default on Windows, PowerShell opens a new window.</span></span> <span data-ttu-id="dbcfd-166">在非 Windows 系統上，您永遠不會收到新的終端機視窗。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-166">On non-Windows systems, you never get a new terminal window.</span></span>

<span data-ttu-id="dbcfd-167">您不能在同一個命令中同時使用 **NoNewWindow** 和 **WindowStyle** 參數。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-167">You cannot use the **NoNewWindow** and **WindowStyle** parameters in the same command.</span></span>

<span data-ttu-id="dbcfd-168">參數不適用於非 Windows 系統。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-168">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: nnw

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-169">-PassThru</span><span class="sxs-lookup"><span data-stu-id="dbcfd-169">-PassThru</span></span>

<span data-ttu-id="dbcfd-170">傳回此 Cmdlet 啟動之每個處理程序的處理程序物件。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-170">Returns a process object for each process that the cmdlet started.</span></span> <span data-ttu-id="dbcfd-171">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-171">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="dbcfd-172">-RedirectStandardError</span><span class="sxs-lookup"><span data-stu-id="dbcfd-172">-RedirectStandardError</span></span>

<span data-ttu-id="dbcfd-173">指定檔案。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-173">Specifies a file.</span></span> <span data-ttu-id="dbcfd-174">此 Cmdlet 會將進程產生的任何錯誤傳送至您指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-174">This cmdlet sends any errors generated by the process to a file that you specify.</span></span>
<span data-ttu-id="dbcfd-175">輸入路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-175">Enter the path and filename.</span></span> <span data-ttu-id="dbcfd-176">根據預設，錯誤會顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-176">By default, the errors are displayed in the console.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-177">-RedirectStandardInput</span><span class="sxs-lookup"><span data-stu-id="dbcfd-177">-RedirectStandardInput</span></span>

<span data-ttu-id="dbcfd-178">指定檔案。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-178">Specifies a file.</span></span> <span data-ttu-id="dbcfd-179">此 Cmdlet 會從指定的檔案讀取輸入。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-179">This cmdlet reads input from the specified file.</span></span> <span data-ttu-id="dbcfd-180">輸入輸入檔的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-180">Enter the path and filename of the input file.</span></span> <span data-ttu-id="dbcfd-181">根據預設，處理程序會從鍵盤取得其輸入。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-181">By default, the process gets its input from the keyboard.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-182">-RedirectStandardOutput</span><span class="sxs-lookup"><span data-stu-id="dbcfd-182">-RedirectStandardOutput</span></span>

<span data-ttu-id="dbcfd-183">指定檔案。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-183">Specifies a file.</span></span> <span data-ttu-id="dbcfd-184">此 Cmdlet 會將進程產生的輸出傳送至您指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-184">This cmdlet sends the output generated by the process to a file that you specify.</span></span>
<span data-ttu-id="dbcfd-185">輸入路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-185">Enter the path and filename.</span></span> <span data-ttu-id="dbcfd-186">根據預設，輸出會顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-186">By default, the output is displayed in the console.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-187">-UseNewEnvironment</span><span class="sxs-lookup"><span data-stu-id="dbcfd-187">-UseNewEnvironment</span></span>

<span data-ttu-id="dbcfd-188">指出此 Cmdlet 會使用為處理常式指定的新環境變數。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-188">Indicates that this cmdlet uses new environment variables specified for the process.</span></span> <span data-ttu-id="dbcfd-189">根據預設，啟動的進程會以繼承自父進程的環境變數執行。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-189">By default, the started process runs with the environment variables inherited from the parent process.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-190">-Verb</span><span class="sxs-lookup"><span data-stu-id="dbcfd-190">-Verb</span></span>

<span data-ttu-id="dbcfd-191">指定此 Cmdlet 啟動進程時要使用的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-191">Specifies a verb to use when this cmdlet starts the process.</span></span> <span data-ttu-id="dbcfd-192">可用的動詞取決於處理常式中執行之檔案的檔案名副檔名。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-192">The verbs that are available are determined by the filename extension of the file that runs in the process.</span></span>

<span data-ttu-id="dbcfd-193">下表顯示一些常見之處理程序檔案類型的動詞。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-193">The following table shows the verbs for some common process file types.</span></span>

| <span data-ttu-id="dbcfd-194">檔案類型</span><span class="sxs-lookup"><span data-stu-id="dbcfd-194">File type</span></span> |                <span data-ttu-id="dbcfd-195">動詞</span><span class="sxs-lookup"><span data-stu-id="dbcfd-195">Verbs</span></span>                |
| --------- | ----------------------------------- |
| <span data-ttu-id="dbcfd-196">.cmd</span><span class="sxs-lookup"><span data-stu-id="dbcfd-196">.cmd</span></span>      | <span data-ttu-id="dbcfd-197">編輯、開啟、列印、RunAs、RunAsUser</span><span class="sxs-lookup"><span data-stu-id="dbcfd-197">Edit, Open, Print, RunAs, RunAsUser</span></span> |
| <span data-ttu-id="dbcfd-198">.exe</span><span class="sxs-lookup"><span data-stu-id="dbcfd-198">.exe</span></span>      | <span data-ttu-id="dbcfd-199">Open、RunAs、RunAsUser</span><span class="sxs-lookup"><span data-stu-id="dbcfd-199">Open, RunAs, RunAsUser</span></span>              |
| <span data-ttu-id="dbcfd-200">.txt</span><span class="sxs-lookup"><span data-stu-id="dbcfd-200">.txt</span></span>      | <span data-ttu-id="dbcfd-201">Open、Print、PrintTo</span><span class="sxs-lookup"><span data-stu-id="dbcfd-201">Open, Print, PrintTo</span></span>                |
| <span data-ttu-id="dbcfd-202">.wav</span><span class="sxs-lookup"><span data-stu-id="dbcfd-202">.wav</span></span>      | <span data-ttu-id="dbcfd-203">開啟、播放</span><span class="sxs-lookup"><span data-stu-id="dbcfd-203">Open, Play</span></span>                          |

<span data-ttu-id="dbcfd-204">若要尋找可搭配在處理常式中執行之檔案使用的動詞，請使用 `New-Object` Cmdlet 來建立檔案的 **ProcessStartInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-204">To find the verbs that can be used with the file that runs in a process, use the `New-Object` cmdlet to create a **System.Diagnostics.ProcessStartInfo** object for the file.</span></span> <span data-ttu-id="dbcfd-205">可用的動詞位於 **ProcessStartInfo** 物件的 **動詞** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-205">The available verbs are in the **Verbs** property of the **ProcessStartInfo** object.</span></span> <span data-ttu-id="dbcfd-206">如需詳細資訊，請參閱範例。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-206">For details, see the examples.</span></span>

<span data-ttu-id="dbcfd-207">參數不適用於非 Windows 系統。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-207">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.String
Parameter Sets: UseShellExecute
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-208">-Wait</span><span class="sxs-lookup"><span data-stu-id="dbcfd-208">-Wait</span></span>

<span data-ttu-id="dbcfd-209">指出此 Cmdlet 會等待指定的進程及其下階完成，再接受更多輸入。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-209">Indicates that this cmdlet waits for the specified process and its descendants to complete before accepting more input.</span></span> <span data-ttu-id="dbcfd-210">此參數會抑制命令提示字元或保留視窗，直到處理程式完成為止。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-210">This parameter suppresses the command prompt or retains the window until the processes finish.</span></span>

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

### <span data-ttu-id="dbcfd-211">-WindowStyle</span><span class="sxs-lookup"><span data-stu-id="dbcfd-211">-WindowStyle</span></span>

<span data-ttu-id="dbcfd-212">指定用於新處理程序之視窗的狀態。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-212">Specifies the state of the window that is used for the new process.</span></span> <span data-ttu-id="dbcfd-213">此參數可接受的值包括： **Normal** 、 **Hidden** 、 **最小化** 和 **最大化** 。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-213">The acceptable values for this parameter are: **Normal** , **Hidden** , **Minimized** , and **Maximized** .</span></span> <span data-ttu-id="dbcfd-214">預設值為 **Normal** 。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-214">The default value is **Normal** .</span></span>

<span data-ttu-id="dbcfd-215">您不能在同一個命令中同時使用 **WindowStyle** 和 **NoNewWindow** 參數。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-215">You cannot use the **WindowStyle** and **NoNewWindow** parameters in the same command.</span></span>

<span data-ttu-id="dbcfd-216">參數不適用於非 Windows 系統。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-216">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.Diagnostics.ProcessWindowStyle
Parameter Sets: (All)
Aliases:
Accepted values: Normal, Hidden, Minimized, Maximized

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-217">-WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="dbcfd-217">-WorkingDirectory</span></span>

<span data-ttu-id="dbcfd-218">指定新進程的開始位置。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-218">Specifies the location that the new process should start in.</span></span> <span data-ttu-id="dbcfd-219">預設值是要啟動的可執行檔或檔的位置。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-219">The default is the location of the executable file or document being started.</span></span> <span data-ttu-id="dbcfd-220">提供的路徑會被視為常值路徑。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-220">The path provided is treated as a literal path.</span></span> <span data-ttu-id="dbcfd-221">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-221">Wildcards are not supported.</span></span> <span data-ttu-id="dbcfd-222">您必須將路徑括在單引號中 (`'`) 如果路徑名稱包含的字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-222">You must enclose the path in single quotes (`'`) if the path name contains characters that would be interpreted as wildcards.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-223">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dbcfd-223">-Confirm</span></span>

<span data-ttu-id="dbcfd-224">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-224">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-225">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dbcfd-225">-WhatIf</span></span>

<span data-ttu-id="dbcfd-226">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-226">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="dbcfd-227">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-227">The cmdlet is not run.</span></span>

<span data-ttu-id="dbcfd-228">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-228">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dbcfd-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dbcfd-229">CommonParameters</span></span>

<span data-ttu-id="dbcfd-230">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dbcfd-231">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-231">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dbcfd-232">輸入</span><span class="sxs-lookup"><span data-stu-id="dbcfd-232">INPUTS</span></span>

### <span data-ttu-id="dbcfd-233">無</span><span class="sxs-lookup"><span data-stu-id="dbcfd-233">None</span></span>

<span data-ttu-id="dbcfd-234">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-234">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="dbcfd-235">輸出</span><span class="sxs-lookup"><span data-stu-id="dbcfd-235">OUTPUTS</span></span>

### <span data-ttu-id="dbcfd-236">無，系統診斷。進程</span><span class="sxs-lookup"><span data-stu-id="dbcfd-236">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="dbcfd-237">如果您指定 **PassThru** 參數，此 Cmdlet 會產生 **system.object** 物件。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-237">This cmdlet generates a **System.Diagnostics.Process** object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="dbcfd-238">否則，此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-238">Otherwise, this cmdlet does not return any output.</span></span>

## <span data-ttu-id="dbcfd-239">注意</span><span class="sxs-lookup"><span data-stu-id="dbcfd-239">NOTES</span></span>

- <span data-ttu-id="dbcfd-240">這個 Cmdlet 是使用 system.string 類別的 **Start** 方法來執行 **。**</span><span class="sxs-lookup"><span data-stu-id="dbcfd-240">This cmdlet is implemented by using the **Start** method of the **System.Diagnostics.Process** class.</span></span> <span data-ttu-id="dbcfd-241">如需此方法的詳細資訊，請參閱 [Process. Start 方法](/dotnet/api/system.diagnostics.process.start#overloads)。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-241">For more information about this method, see [Process.Start Method](/dotnet/api/system.diagnostics.process.start#overloads).</span></span>

- <span data-ttu-id="dbcfd-242">在 Windows 上，當您使用 **UseNewEnvironment** 時，新的進程只會啟動針對 **電腦** 範圍定義的預設環境變數。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-242">On Windows, when you use **UseNewEnvironment** , the new process starts only containing the default environment variables defined for the **Machine** scope.</span></span> <span data-ttu-id="dbcfd-243">這會影響 `$env:USERNAME` 設為 **SYSTEM** 的端。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-243">This has the side affect that the `$env:USERNAME` is set to **SYSTEM** .</span></span> <span data-ttu-id="dbcfd-244">不包含 **使用者** 範圍中的任何變數。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-244">None of the variables from the **User** scope are included.</span></span>

- <span data-ttu-id="dbcfd-245">在 Windows 上，最常見的使用案例 `Start-Process` 是使用 **Wait** 參數來封鎖進度，直到新的進程結束為止。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-245">On Windows, the most common use case for `Start-Process` is to use the **Wait** parameter to block progress until the new process exits.</span></span> <span data-ttu-id="dbcfd-246">在非 Windows 系統上，很少需要這樣做，因為命令列應用程式的預設行為相當於 `Start-Process -Wait` 。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-246">On non-Windows system, this is rarely needed since the default behavior for command-line applications is equivalent to `Start-Process -Wait`.</span></span>

- <span data-ttu-id="dbcfd-247">`Start-Process`在非 Windows 系統上使用時，您永遠不會收到新的終端機視窗。</span><span class="sxs-lookup"><span data-stu-id="dbcfd-247">When using `Start-Process` on non-Windows systems, you never get a new terminal window.</span></span>

## <span data-ttu-id="dbcfd-248">相關連結</span><span class="sxs-lookup"><span data-stu-id="dbcfd-248">RELATED LINKS</span></span>

[<span data-ttu-id="dbcfd-249">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="dbcfd-249">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="dbcfd-250">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="dbcfd-250">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="dbcfd-251">Get-Process</span><span class="sxs-lookup"><span data-stu-id="dbcfd-251">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="dbcfd-252">Start-Service</span><span class="sxs-lookup"><span data-stu-id="dbcfd-252">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="dbcfd-253">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="dbcfd-253">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="dbcfd-254">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="dbcfd-254">Wait-Process</span></span>](Wait-Process.md)
