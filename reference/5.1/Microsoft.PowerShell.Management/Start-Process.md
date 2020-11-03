---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: b6147b35a8818cf448b1e23f5458550d1c6e5c50
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "93205815"
---
# <span data-ttu-id="4487f-103">Start-Process</span><span class="sxs-lookup"><span data-stu-id="4487f-103">Start-Process</span></span>

## <span data-ttu-id="4487f-104">概要</span><span class="sxs-lookup"><span data-stu-id="4487f-104">SYNOPSIS</span></span>
<span data-ttu-id="4487f-105">啟動本機電腦上的一或多個處理程序。</span><span class="sxs-lookup"><span data-stu-id="4487f-105">Starts one or more processes on the local computer.</span></span>

## <span data-ttu-id="4487f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4487f-106">SYNTAX</span></span>

### <span data-ttu-id="4487f-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="4487f-107">Default (Default)</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [<CommonParameters>]
```

### <span data-ttu-id="4487f-108">UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="4487f-108">UseShellExecute</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [<CommonParameters>]
```

## <span data-ttu-id="4487f-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4487f-109">DESCRIPTION</span></span>

<span data-ttu-id="4487f-110">`Start-Process`Cmdlet 會在本機電腦上啟動一或多個處理常式。</span><span class="sxs-lookup"><span data-stu-id="4487f-110">The `Start-Process` cmdlet starts one or more processes on the local computer.</span></span> <span data-ttu-id="4487f-111">依預設， `Start-Process` 會建立新的進程，以繼承目前進程中定義的所有環境變數。</span><span class="sxs-lookup"><span data-stu-id="4487f-111">By default, `Start-Process` creates a new process that inherits all the environment variables that are defined in the current process.</span></span>

<span data-ttu-id="4487f-112">如果要指定在處理程序中執行的程式，請輸入可執行檔或指令碼檔案，或可使用電腦上的程式開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="4487f-112">To specify the program that runs in the process, enter an executable file or script file, or a file that can be opened by using a program on the computer.</span></span> <span data-ttu-id="4487f-113">如果您指定無法執行的檔案，則 `Start-Process` 會啟動與檔案相關聯的程式，類似于 `Invoke-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4487f-113">If you specify a non-executable file, `Start-Process` starts the program that is associated with the file, similar to the `Invoke-Item` cmdlet.</span></span>

<span data-ttu-id="4487f-114">您可以使用的參數 `Start-Process` 來指定選項，例如載入使用者設定檔、在新視窗中啟動進程，或使用替代認證。</span><span class="sxs-lookup"><span data-stu-id="4487f-114">You can use the parameters of `Start-Process` to specify options, such as loading a user profile, starting the process in a new window, or using alternate credentials.</span></span>

## <span data-ttu-id="4487f-115">範例</span><span class="sxs-lookup"><span data-stu-id="4487f-115">EXAMPLES</span></span>

### <span data-ttu-id="4487f-116">範例1：啟動使用預設值的處理常式</span><span class="sxs-lookup"><span data-stu-id="4487f-116">Example 1: Start a process that uses default values</span></span>

<span data-ttu-id="4487f-117">此範例會啟動使用目前資料夾中之檔案的處理常式 `Sort.exe` 。</span><span class="sxs-lookup"><span data-stu-id="4487f-117">This example starts a process that uses the `Sort.exe` file in the current folder.</span></span> <span data-ttu-id="4487f-118">此命令會使用所有預設值，包括預設視窗樣式、工作資料夾和認證。</span><span class="sxs-lookup"><span data-stu-id="4487f-118">The command uses all of the default values, including the default window style, working folder, and credentials.</span></span>

```powershell
Start-Process -FilePath "sort.exe"
```

### <span data-ttu-id="4487f-119">範例2：列印文字檔</span><span class="sxs-lookup"><span data-stu-id="4487f-119">Example 2: Print a text file</span></span>

<span data-ttu-id="4487f-120">此範例會啟動列印檔案的處理常式 `C:\PS-Test\MyFile.txt` 。</span><span class="sxs-lookup"><span data-stu-id="4487f-120">This example starts a process that prints the `C:\PS-Test\MyFile.txt` file.</span></span>

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### <span data-ttu-id="4487f-121">範例3：啟動將專案排序至新檔案的進程</span><span class="sxs-lookup"><span data-stu-id="4487f-121">Example 3: Start a process to sort items to a new file</span></span>

<span data-ttu-id="4487f-122">此範例會啟動一個進程，以排序檔案中 `Testsort.txt` 的專案，並傳回檔案中已排序的專案 `Sorted.txt` 。</span><span class="sxs-lookup"><span data-stu-id="4487f-122">This example starts a process that sorts items in the `Testsort.txt` file and returns the sorted items in the `Sorted.txt` files.</span></span> <span data-ttu-id="4487f-123">任何錯誤都會寫入至檔案 `SortError.txt` 。</span><span class="sxs-lookup"><span data-stu-id="4487f-123">Any errors are written to the `SortError.txt` file.</span></span>

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

<span data-ttu-id="4487f-124">**UseNewEnvironment** 參數會指定進程會以自己的環境變數執行。</span><span class="sxs-lookup"><span data-stu-id="4487f-124">The **UseNewEnvironment** parameter specifies that the process runs with its own environment variables.</span></span>

### <span data-ttu-id="4487f-125">範例4：在最大化的視窗中啟動進程</span><span class="sxs-lookup"><span data-stu-id="4487f-125">Example 4: Start a process in a maximized window</span></span>

<span data-ttu-id="4487f-126">此範例會啟動 `Notepad.exe` 進程。</span><span class="sxs-lookup"><span data-stu-id="4487f-126">This example starts the `Notepad.exe` process.</span></span> <span data-ttu-id="4487f-127">在處理程序完成前，它會最大化視窗並保留視窗。</span><span class="sxs-lookup"><span data-stu-id="4487f-127">It maximizes the window and retains the window until the process completes.</span></span>

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### <span data-ttu-id="4487f-128">範例5：以系統管理員身分啟動 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4487f-128">Example 5: Start PowerShell as an administrator</span></span>

<span data-ttu-id="4487f-129">此範例會使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4487f-129">This example starts PowerShell by using the **Run as administrator** option.</span></span>

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### <span data-ttu-id="4487f-130">範例6：使用不同的動詞來啟動處理常式</span><span class="sxs-lookup"><span data-stu-id="4487f-130">Example 6: Using different verbs to start a process</span></span>

<span data-ttu-id="4487f-131">此範例顯示如何尋找啟動處理常式時可使用的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="4487f-131">This example shows how to find the verbs that can be used when starting a process.</span></span> <span data-ttu-id="4487f-132">可用的動詞取決於處理常式中執行之檔案的檔案名副檔名。</span><span class="sxs-lookup"><span data-stu-id="4487f-132">The available verbs are determined by the filename extension of the file that runs in the process.</span></span>

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

<span data-ttu-id="4487f-133">此範例會使用 `New-Object` 來建立 **PowerShell.exe** 的 **ProcessStartInfo** 物件，這是在 PowerShell 處理常式中執行的檔案。</span><span class="sxs-lookup"><span data-stu-id="4487f-133">The example uses `New-Object` to create a **System.Diagnostics.ProcessStartInfo** object for **PowerShell.exe** , the file that runs in the PowerShell process.</span></span> <span data-ttu-id="4487f-134">**ProcessStartInfo** 物件的 **動詞** 屬性顯示您可以使用 **Open** 和 **RunAs** 動詞搭配或執行檔案的 `PowerShell.exe` 任何進程 `.exe` 。</span><span class="sxs-lookup"><span data-stu-id="4487f-134">The **Verbs** property of the **ProcessStartInfo** object shows that you can use the **Open** and **RunAs** verbs with `PowerShell.exe`, or with any process that runs a `.exe` file.</span></span>

### <span data-ttu-id="4487f-135">範例7：指定進程的引數</span><span class="sxs-lookup"><span data-stu-id="4487f-135">Example 7: Specifying arguments to the process</span></span>

<span data-ttu-id="4487f-136">這兩個命令都會啟動 Windows 命令直譯器，並 `dir` 在資料夾上發出命令 `Program Files` 。</span><span class="sxs-lookup"><span data-stu-id="4487f-136">Both commands start the Windows command interpreter, issuing a `dir` command on the `Program Files` folder.</span></span> <span data-ttu-id="4487f-137">因為此資料夾包含空格，所以值需要以引號括住。</span><span class="sxs-lookup"><span data-stu-id="4487f-137">Because this foldername contains a space, the value needs surrounded with escaped quotes.</span></span>
<span data-ttu-id="4487f-138">請注意，第一個命令會將字串指定為 **ArgumentList** 。</span><span class="sxs-lookup"><span data-stu-id="4487f-138">Note that the first command specifies a string as **ArgumentList** .</span></span> <span data-ttu-id="4487f-139">第二個命令是字串陣列。</span><span class="sxs-lookup"><span data-stu-id="4487f-139">The second command is a string array.</span></span>

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

## <span data-ttu-id="4487f-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4487f-140">PARAMETERS</span></span>

### <span data-ttu-id="4487f-141">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="4487f-141">-ArgumentList</span></span>

<span data-ttu-id="4487f-142">指定此 Cmdlet 啟動進程時要使用的參數或參數值。</span><span class="sxs-lookup"><span data-stu-id="4487f-142">Specifies parameters or parameter values to use when this cmdlet starts the process.</span></span> <span data-ttu-id="4487f-143">引數可以接受為具有以空格分隔之引數的單一字串，或是以逗號分隔的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="4487f-143">Arguments can be accepted as a single string with the arguments separated by spaces, or as an array of strings separated by commas.</span></span>

<span data-ttu-id="4487f-144">如果參數或參數值包含空格，則必須以換用雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="4487f-144">If parameters or parameter values contain a space, they need to be surrounded with escaped double quotes.</span></span> <span data-ttu-id="4487f-145">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="4487f-145">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="4487f-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="4487f-146">-Credential</span></span>

<span data-ttu-id="4487f-147">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4487f-147">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="4487f-148">根據預設，Cmdlet 會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="4487f-148">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="4487f-149">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="4487f-149">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="4487f-150">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="4487f-150">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="4487f-151">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="4487f-151">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="4487f-152">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="4487f-152">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="4487f-153">-FilePath</span><span class="sxs-lookup"><span data-stu-id="4487f-153">-FilePath</span></span>

<span data-ttu-id="4487f-154">指定在處理常式中執行之程式的選擇性路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="4487f-154">Specifies the optional path and filename of the program that runs in the process.</span></span> <span data-ttu-id="4487f-155">輸入 `.txt` `.doc` 與電腦上程式相關聯之可執行檔或檔（例如或檔案）的名稱。</span><span class="sxs-lookup"><span data-stu-id="4487f-155">Enter the name of an executable file or of a document, such as a `.txt` or `.doc` file, that is associated with a program on the computer.</span></span> <span data-ttu-id="4487f-156">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="4487f-156">This parameter is required.</span></span>

<span data-ttu-id="4487f-157">如果您只指定檔案名，請使用 **WorkingDirectory** 參數來指定路徑。</span><span class="sxs-lookup"><span data-stu-id="4487f-157">If you specify only a filename, use the **WorkingDirectory** parameter to specify the path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4487f-158">-LoadUserProfile</span><span class="sxs-lookup"><span data-stu-id="4487f-158">-LoadUserProfile</span></span>

<span data-ttu-id="4487f-159">指出此 Cmdlet 會載入儲存在目前使用者的登錄機碼中的 Windows 使用者設定檔 `HKEY_USERS` 。</span><span class="sxs-lookup"><span data-stu-id="4487f-159">Indicates that this cmdlet loads the Windows user profile stored in the `HKEY_USERS` registry key for the current user.</span></span>

<span data-ttu-id="4487f-160">此參數不會影響 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="4487f-160">This parameter does not affect the PowerShell profiles.</span></span> <span data-ttu-id="4487f-161">如需詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="4487f-161">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

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

### <span data-ttu-id="4487f-162">-NoNewWindow</span><span class="sxs-lookup"><span data-stu-id="4487f-162">-NoNewWindow</span></span>

<span data-ttu-id="4487f-163">在目前的主控台視窗中啟動新的處理程序。</span><span class="sxs-lookup"><span data-stu-id="4487f-163">Start the new process in the current console window.</span></span> <span data-ttu-id="4487f-164">PowerShell 預設會開啟新的視窗。</span><span class="sxs-lookup"><span data-stu-id="4487f-164">By default PowerShell opens a new window.</span></span>

<span data-ttu-id="4487f-165">您不能在同一個命令中同時使用 **NoNewWindow** 和 **WindowStyle** 參數。</span><span class="sxs-lookup"><span data-stu-id="4487f-165">You cannot use the **NoNewWindow** and **WindowStyle** parameters in the same command.</span></span>

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

### <span data-ttu-id="4487f-166">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4487f-166">-PassThru</span></span>

<span data-ttu-id="4487f-167">傳回此 Cmdlet 啟動之每個處理程序的處理程序物件。</span><span class="sxs-lookup"><span data-stu-id="4487f-167">Returns a process object for each process that the cmdlet started.</span></span> <span data-ttu-id="4487f-168">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="4487f-168">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="4487f-169">-RedirectStandardError</span><span class="sxs-lookup"><span data-stu-id="4487f-169">-RedirectStandardError</span></span>

<span data-ttu-id="4487f-170">指定檔案。</span><span class="sxs-lookup"><span data-stu-id="4487f-170">Specifies a file.</span></span> <span data-ttu-id="4487f-171">此 Cmdlet 會將進程產生的任何錯誤傳送至您指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="4487f-171">This cmdlet sends any errors generated by the process to a file that you specify.</span></span>
<span data-ttu-id="4487f-172">輸入路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="4487f-172">Enter the path and filename.</span></span> <span data-ttu-id="4487f-173">根據預設，錯誤會顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="4487f-173">By default, the errors are displayed in the console.</span></span>

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

### <span data-ttu-id="4487f-174">-RedirectStandardInput</span><span class="sxs-lookup"><span data-stu-id="4487f-174">-RedirectStandardInput</span></span>

<span data-ttu-id="4487f-175">指定檔案。</span><span class="sxs-lookup"><span data-stu-id="4487f-175">Specifies a file.</span></span> <span data-ttu-id="4487f-176">此 Cmdlet 會從指定的檔案讀取輸入。</span><span class="sxs-lookup"><span data-stu-id="4487f-176">This cmdlet reads input from the specified file.</span></span> <span data-ttu-id="4487f-177">輸入輸入檔的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="4487f-177">Enter the path and filename of the input file.</span></span> <span data-ttu-id="4487f-178">根據預設，處理程序會從鍵盤取得其輸入。</span><span class="sxs-lookup"><span data-stu-id="4487f-178">By default, the process gets its input from the keyboard.</span></span>

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

### <span data-ttu-id="4487f-179">-RedirectStandardOutput</span><span class="sxs-lookup"><span data-stu-id="4487f-179">-RedirectStandardOutput</span></span>

<span data-ttu-id="4487f-180">指定檔案。</span><span class="sxs-lookup"><span data-stu-id="4487f-180">Specifies a file.</span></span> <span data-ttu-id="4487f-181">此 Cmdlet 會將進程產生的輸出傳送至您指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="4487f-181">This cmdlet sends the output generated by the process to a file that you specify.</span></span>
<span data-ttu-id="4487f-182">輸入路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="4487f-182">Enter the path and filename.</span></span> <span data-ttu-id="4487f-183">根據預設，輸出會顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="4487f-183">By default, the output is displayed in the console.</span></span>

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

### <span data-ttu-id="4487f-184">-UseNewEnvironment</span><span class="sxs-lookup"><span data-stu-id="4487f-184">-UseNewEnvironment</span></span>

<span data-ttu-id="4487f-185">指出此 Cmdlet 會使用為處理常式指定的新環境變數。</span><span class="sxs-lookup"><span data-stu-id="4487f-185">Indicates that this cmdlet uses new environment variables specified for the process.</span></span> <span data-ttu-id="4487f-186">根據預設，啟動的進程會以繼承自父進程的環境變數執行。</span><span class="sxs-lookup"><span data-stu-id="4487f-186">By default, the started process runs with the environment variables inherited from the parent process.</span></span>

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

### <span data-ttu-id="4487f-187">-Verb</span><span class="sxs-lookup"><span data-stu-id="4487f-187">-Verb</span></span>

<span data-ttu-id="4487f-188">指定此 Cmdlet 啟動進程時要使用的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="4487f-188">Specifies a verb to use when this cmdlet starts the process.</span></span> <span data-ttu-id="4487f-189">可用的動詞取決於處理常式中執行之檔案的檔案名副檔名。</span><span class="sxs-lookup"><span data-stu-id="4487f-189">The verbs that are available are determined by the filename extension of the file that runs in the process.</span></span>

<span data-ttu-id="4487f-190">下表顯示一些常見之處理程序檔案類型的動詞。</span><span class="sxs-lookup"><span data-stu-id="4487f-190">The following table shows the verbs for some common process file types.</span></span>

| <span data-ttu-id="4487f-191">檔案類型</span><span class="sxs-lookup"><span data-stu-id="4487f-191">File type</span></span> |                <span data-ttu-id="4487f-192">動詞</span><span class="sxs-lookup"><span data-stu-id="4487f-192">Verbs</span></span>                |
| --------- | ----------------------------------- |
| <span data-ttu-id="4487f-193">.cmd</span><span class="sxs-lookup"><span data-stu-id="4487f-193">.cmd</span></span>      | <span data-ttu-id="4487f-194">編輯、開啟、列印、RunAs、RunAsUser</span><span class="sxs-lookup"><span data-stu-id="4487f-194">Edit, Open, Print, RunAs, RunAsUser</span></span> |
| <span data-ttu-id="4487f-195">.exe</span><span class="sxs-lookup"><span data-stu-id="4487f-195">.exe</span></span>      | <span data-ttu-id="4487f-196">Open、RunAs、RunAsUser</span><span class="sxs-lookup"><span data-stu-id="4487f-196">Open, RunAs, RunAsUser</span></span>              |
| <span data-ttu-id="4487f-197">.txt</span><span class="sxs-lookup"><span data-stu-id="4487f-197">.txt</span></span>      | <span data-ttu-id="4487f-198">Open、Print、PrintTo</span><span class="sxs-lookup"><span data-stu-id="4487f-198">Open, Print, PrintTo</span></span>                |
| <span data-ttu-id="4487f-199">.wav</span><span class="sxs-lookup"><span data-stu-id="4487f-199">.wav</span></span>      | <span data-ttu-id="4487f-200">開啟、播放</span><span class="sxs-lookup"><span data-stu-id="4487f-200">Open, Play</span></span>                          |

<span data-ttu-id="4487f-201">若要尋找可搭配在處理常式中執行之檔案使用的動詞，請使用 `New-Object` Cmdlet 來建立檔案的 **ProcessStartInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="4487f-201">To find the verbs that can be used with the file that runs in a process, use the `New-Object` cmdlet to create a **System.Diagnostics.ProcessStartInfo** object for the file.</span></span> <span data-ttu-id="4487f-202">可用的動詞位於 **ProcessStartInfo** 物件的 **動詞** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="4487f-202">The available verbs are in the **Verbs** property of the **ProcessStartInfo** object.</span></span> <span data-ttu-id="4487f-203">如需詳細資訊，請參閱範例。</span><span class="sxs-lookup"><span data-stu-id="4487f-203">For details, see the examples.</span></span>

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

### <span data-ttu-id="4487f-204">-Wait</span><span class="sxs-lookup"><span data-stu-id="4487f-204">-Wait</span></span>

<span data-ttu-id="4487f-205">指出此 Cmdlet 會等待指定的進程及其下階完成，再接受更多輸入。</span><span class="sxs-lookup"><span data-stu-id="4487f-205">Indicates that this cmdlet waits for the specified process and its descendants to complete before accepting more input.</span></span> <span data-ttu-id="4487f-206">此參數會抑制命令提示字元或保留視窗，直到處理程式完成為止。</span><span class="sxs-lookup"><span data-stu-id="4487f-206">This parameter suppresses the command prompt or retains the window until the processes finish.</span></span>

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

### <span data-ttu-id="4487f-207">-WindowStyle</span><span class="sxs-lookup"><span data-stu-id="4487f-207">-WindowStyle</span></span>

<span data-ttu-id="4487f-208">指定用於新處理程序之視窗的狀態。</span><span class="sxs-lookup"><span data-stu-id="4487f-208">Specifies the state of the window that is used for the new process.</span></span> <span data-ttu-id="4487f-209">此參數可接受的值包括： **Normal** 、 **Hidden** 、 **最小化** 和 **最大化** 。</span><span class="sxs-lookup"><span data-stu-id="4487f-209">The acceptable values for this parameter are: **Normal** , **Hidden** , **Minimized** , and **Maximized** .</span></span> <span data-ttu-id="4487f-210">預設值為 **Normal** 。</span><span class="sxs-lookup"><span data-stu-id="4487f-210">The default value is **Normal** .</span></span>

<span data-ttu-id="4487f-211">您不能在同一個命令中同時使用 **WindowStyle** 和 **NoNewWindow** 參數。</span><span class="sxs-lookup"><span data-stu-id="4487f-211">You cannot use the **WindowStyle** and **NoNewWindow** parameters in the same command.</span></span>

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

### <span data-ttu-id="4487f-212">-WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="4487f-212">-WorkingDirectory</span></span>

<span data-ttu-id="4487f-213">指定新進程的開始位置。</span><span class="sxs-lookup"><span data-stu-id="4487f-213">Specifies the location that the new process should start in.</span></span> <span data-ttu-id="4487f-214">預設值是要啟動的可執行檔或檔的位置。</span><span class="sxs-lookup"><span data-stu-id="4487f-214">The default is the location of the executable file or document being started.</span></span> <span data-ttu-id="4487f-215">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4487f-215">Wildcards are not supported.</span></span> <span data-ttu-id="4487f-216">路徑名稱不能包含會被視為萬用字元的字元。</span><span class="sxs-lookup"><span data-stu-id="4487f-216">The path name must not contain characters that would be interpreted as wildcards.</span></span>

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

### <span data-ttu-id="4487f-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4487f-217">CommonParameters</span></span>

<span data-ttu-id="4487f-218">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4487f-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4487f-219">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4487f-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4487f-220">輸入</span><span class="sxs-lookup"><span data-stu-id="4487f-220">INPUTS</span></span>

### <span data-ttu-id="4487f-221">無</span><span class="sxs-lookup"><span data-stu-id="4487f-221">None</span></span>

<span data-ttu-id="4487f-222">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4487f-222">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="4487f-223">輸出</span><span class="sxs-lookup"><span data-stu-id="4487f-223">OUTPUTS</span></span>

### <span data-ttu-id="4487f-224">無，系統診斷。進程</span><span class="sxs-lookup"><span data-stu-id="4487f-224">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="4487f-225">如果您指定 **PassThru** 參數，此 Cmdlet 會產生 **system.object** 物件。</span><span class="sxs-lookup"><span data-stu-id="4487f-225">This cmdlet generates a **System.Diagnostics.Process** object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="4487f-226">否則，此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="4487f-226">Otherwise, this cmdlet does not return any output.</span></span>

## <span data-ttu-id="4487f-227">注意</span><span class="sxs-lookup"><span data-stu-id="4487f-227">NOTES</span></span>

- <span data-ttu-id="4487f-228">這個 Cmdlet 是使用 system.string 類別的 **Start** 方法來執行 **。**</span><span class="sxs-lookup"><span data-stu-id="4487f-228">This cmdlet is implemented by using the **Start** method of the **System.Diagnostics.Process** class.</span></span> <span data-ttu-id="4487f-229">如需此方法的詳細資訊，請參閱 [Process. Start 方法](/dotnet/api/system.diagnostics.process.start#overloads)。</span><span class="sxs-lookup"><span data-stu-id="4487f-229">For more information about this method, see [Process.Start Method](/dotnet/api/system.diagnostics.process.start#overloads).</span></span>

- <span data-ttu-id="4487f-230">在 Windows 上，當您使用 **UseNewEnvironment** 時，新的進程只會啟動針對 **電腦** 範圍定義的預設環境變數。</span><span class="sxs-lookup"><span data-stu-id="4487f-230">On Windows, when you use **UseNewEnvironment** , the new process starts only containing the default environment variables defined for the **Machine** scope.</span></span> <span data-ttu-id="4487f-231">這會影響 `$env:USERNAME` 設為 **SYSTEM** 的端。</span><span class="sxs-lookup"><span data-stu-id="4487f-231">This has the side affect that the `$env:USERNAME` is set to **SYSTEM** .</span></span> <span data-ttu-id="4487f-232">不包含 **使用者** 範圍中的任何變數。</span><span class="sxs-lookup"><span data-stu-id="4487f-232">None of the variables from the **User** scope are included.</span></span>

## <span data-ttu-id="4487f-233">相關連結</span><span class="sxs-lookup"><span data-stu-id="4487f-233">RELATED LINKS</span></span>

[<span data-ttu-id="4487f-234">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="4487f-234">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="4487f-235">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="4487f-235">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="4487f-236">Get-Process</span><span class="sxs-lookup"><span data-stu-id="4487f-236">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="4487f-237">Start-Service</span><span class="sxs-lookup"><span data-stu-id="4487f-237">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="4487f-238">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="4487f-238">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="4487f-239">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="4487f-239">Wait-Process</span></span>](Wait-Process.md)
