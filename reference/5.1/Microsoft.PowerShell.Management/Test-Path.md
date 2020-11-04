---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Path
ms.openlocfilehash: ced5a5db05674c15fefada73ab55969d724117e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203452"
---
# <span data-ttu-id="b7134-103">Test-Path</span><span class="sxs-lookup"><span data-stu-id="b7134-103">Test-Path</span></span>

## <span data-ttu-id="b7134-104">概要</span><span class="sxs-lookup"><span data-stu-id="b7134-104">SYNOPSIS</span></span>
<span data-ttu-id="b7134-105">判斷路徑的所有元素是否都存在。</span><span class="sxs-lookup"><span data-stu-id="b7134-105">Determines whether all elements of a path exist.</span></span>

## <span data-ttu-id="b7134-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b7134-106">SYNTAX</span></span>

### <span data-ttu-id="b7134-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="b7134-107">Path (Default)</span></span>

```
Test-Path [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>] [-UseTransaction]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="b7134-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b7134-108">LiteralPath</span></span>

```
Test-Path -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>] [-UseTransaction]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

## <span data-ttu-id="b7134-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b7134-109">DESCRIPTION</span></span>

<span data-ttu-id="b7134-110">`Test-Path`Cmdlet 會判斷路徑的所有元素是否都存在。</span><span class="sxs-lookup"><span data-stu-id="b7134-110">The `Test-Path` cmdlet determines whether all elements of the path exist.</span></span> <span data-ttu-id="b7134-111">`$True`如果所有專案都存在且遺失任何專案，則會傳回 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="b7134-111">It returns `$True` if all elements exist and `$False` if any are missing.</span></span> <span data-ttu-id="b7134-112">它也可以分辨路徑語法是否有效，以及路徑是否會導向至容器或終端機或分葉元素。</span><span class="sxs-lookup"><span data-stu-id="b7134-112">It can also tell whether the path syntax is valid and whether the path leads to a container or a terminal or leaf element.</span></span> <span data-ttu-id="b7134-113">如果 `Path` 是空白字元，則 `$False` 會傳回。</span><span class="sxs-lookup"><span data-stu-id="b7134-113">If the `Path` is whitespace, then `$False` is returned.</span></span> <span data-ttu-id="b7134-114">如果 `Path` 是空字串、 `$null` 、陣列 `$null` 或空白陣列，則會傳回非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7134-114">If the `Path` is an empty string, `$null`, array of `$null` or empty array, a non-terminating error is returned.</span></span>

## <span data-ttu-id="b7134-115">範例</span><span class="sxs-lookup"><span data-stu-id="b7134-115">EXAMPLES</span></span>

### <span data-ttu-id="b7134-116">範例1：測試路徑</span><span class="sxs-lookup"><span data-stu-id="b7134-116">Example 1: Test a path</span></span>

```powershell
Test-Path -Path "C:\Documents and Settings\DavidC"
```

```Output
True
```

<span data-ttu-id="b7134-117">此命令會檢查路徑中的所有元素是否都存在，亦即 C：目錄、Documents and Settings 目錄，以及 DavidC 目錄。</span><span class="sxs-lookup"><span data-stu-id="b7134-117">This command checks whether all elements in the path exist, that is, the C: directory, the Documents and Settings directory, and the DavidC directory.</span></span> <span data-ttu-id="b7134-118">如果有任何遺漏，則 Cmdlet 會傳回 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="b7134-118">If any are missing, the cmdlet returns `$False`.</span></span>
<span data-ttu-id="b7134-119">否則，它會傳回 `$True`。</span><span class="sxs-lookup"><span data-stu-id="b7134-119">Otherwise, it returns `$True`.</span></span>

### <span data-ttu-id="b7134-120">範例2：測試組態檔的路徑</span><span class="sxs-lookup"><span data-stu-id="b7134-120">Example 2: Test the path of a profile</span></span>

```powershell
Test-Path -Path $profile
```

```Output
False
```

```powershell
Test-Path -Path $profile -IsValid
```

```Output
True
```

<span data-ttu-id="b7134-121">這些命令會測試 PowerShell 設定檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="b7134-121">These commands test the path of the PowerShell profile.</span></span>

<span data-ttu-id="b7134-122">第一個命令會判斷路徑中的所有元素是否都存在。</span><span class="sxs-lookup"><span data-stu-id="b7134-122">The first command determines whether all elements in the path exist.</span></span> <span data-ttu-id="b7134-123">第二個命令會判斷路徑的語法是否正確。</span><span class="sxs-lookup"><span data-stu-id="b7134-123">The second command determines whether the syntax of the path is correct.</span></span> <span data-ttu-id="b7134-124">在此情況下，路徑為 `$False` ，但語法正確 `$True` 。</span><span class="sxs-lookup"><span data-stu-id="b7134-124">In this case, the path is `$False`, but the syntax is correct `$True`.</span></span> <span data-ttu-id="b7134-125">這些命令 `$profile` 會使用指向設定檔位置的自動變數（即使設定檔不存在）。</span><span class="sxs-lookup"><span data-stu-id="b7134-125">These commands use `$profile`, the automatic variable that points to the location for the profile, even if the profile does not exist.</span></span>

<span data-ttu-id="b7134-126">如需自動變數的相關詳細資訊，請參閱 about_Automatic_Variables。</span><span class="sxs-lookup"><span data-stu-id="b7134-126">For more information about automatic variables, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="b7134-127">範例3：檢查指定類型以外是否有任何檔案</span><span class="sxs-lookup"><span data-stu-id="b7134-127">Example 3: Check whether there are any files besides a specified type</span></span>

```powershell
Test-Path -Path "C:\CAD\Commercial Buildings\*" -Exclude *.dwg
```

```Output
False
```

<span data-ttu-id="b7134-128">此命令會檢查商業大樓目錄中是否有任何檔案，而非 dwg 檔。</span><span class="sxs-lookup"><span data-stu-id="b7134-128">This command checks whether there are any files in the Commercial Buildings directory other than .dwg files.</span></span>

<span data-ttu-id="b7134-129">此命令會使用 **path** 參數來指定路徑。</span><span class="sxs-lookup"><span data-stu-id="b7134-129">The command uses the **Path** parameter to specify the path.</span></span> <span data-ttu-id="b7134-130">由於路徑包含空格，因此路徑會以引號括住。</span><span class="sxs-lookup"><span data-stu-id="b7134-130">Because the path includes a space, the path is enclosed in quotation marks.</span></span> <span data-ttu-id="b7134-131">路徑尾端的星號會指示 Commercial Building 目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="b7134-131">The asterisk at the end of the path indicates the contents of the Commercial Building directory.</span></span> <span data-ttu-id="b7134-132">使用較長的路徑（例如，），輸入路徑的前幾個字母，然後使用 TAB 鍵來完成路徑。</span><span class="sxs-lookup"><span data-stu-id="b7134-132">With long paths, such as this one, type the first few letters of the path, and then use the TAB key to complete the path.</span></span>

<span data-ttu-id="b7134-133">此命令會指定 **Exclude** 參數，以指定將在評估時省略的檔案。</span><span class="sxs-lookup"><span data-stu-id="b7134-133">The command specifies the **Exclude** parameter to specify files that will be omitted from the evaluation.</span></span>

<span data-ttu-id="b7134-134">在此情況下，因為目錄僅包含 dwg 檔案，所以結果為 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="b7134-134">In this case, because the directory contains only .dwg files, the result is `$False`.</span></span>

### <span data-ttu-id="b7134-135">範例4：檢查檔案</span><span class="sxs-lookup"><span data-stu-id="b7134-135">Example 4: Check for a file</span></span>

```powershell
Test-Path -Path $profile -PathType leaf
```

```Output
True
```

<span data-ttu-id="b7134-136">此命令會檢查儲存在變數中的路徑是否會 `$profile` 導致檔案。</span><span class="sxs-lookup"><span data-stu-id="b7134-136">This command checks whether the path stored in the `$profile` variable leads to a file.</span></span> <span data-ttu-id="b7134-137">在此情況下，由於 PowerShell 設定檔是檔案，因此 Cmdlet 會傳回 `.ps1` `$True` 。</span><span class="sxs-lookup"><span data-stu-id="b7134-137">In this case, because the PowerShell profile is a `.ps1` file, the cmdlet returns `$True`.</span></span>

### <span data-ttu-id="b7134-138">範例5：檢查登錄中的路徑</span><span class="sxs-lookup"><span data-stu-id="b7134-138">Example 5: Check paths in the Registry</span></span>

<span data-ttu-id="b7134-139">這些命令會搭配 `Test-Path` PowerShell 登錄提供者使用。</span><span class="sxs-lookup"><span data-stu-id="b7134-139">These commands use `Test-Path` with the PowerShell registry provider.</span></span>

<span data-ttu-id="b7134-140">第一個命令會測試系統上的 **Microsoft PowerShell** 登錄機碼登錄路徑是否正確。</span><span class="sxs-lookup"><span data-stu-id="b7134-140">The first command tests whether the registry path of the **Microsoft.PowerShell** registry key is correct on the system.</span></span> <span data-ttu-id="b7134-141">如果 PowerShell 已正確安裝，則 Cmdlet 會傳回 `$True` 。</span><span class="sxs-lookup"><span data-stu-id="b7134-141">If PowerShell is installed correctly, the cmdlet returns `$True`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7134-142">`Test-Path` 無法與所有 PowerShell 提供者正常搭配運作。</span><span class="sxs-lookup"><span data-stu-id="b7134-142">`Test-Path` does not work correctly with all PowerShell providers.</span></span> <span data-ttu-id="b7134-143">例如，您可以使用 `Test-Path` 來測試登錄機碼的路徑，但是如果您使用它來測試登錄專案的路徑，它一律會傳回 `$False` ，即使登錄專案存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="b7134-143">For example, you can use `Test-Path` to test the path of a registry key, but if you use it to test the path of a registry entry, it always returns `$False`, even if the registry entry is present.</span></span>

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell"
```

```Output
True
```

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell\ExecutionPolicy"
```

```Output
False
```

### <span data-ttu-id="b7134-144">範例6：測試檔案是否比指定的日期更新</span><span class="sxs-lookup"><span data-stu-id="b7134-144">Example 6: Test if a file is newer than a specified date</span></span>

<span data-ttu-id="b7134-145">此命令會使用 **NewerThan** 動態參數，來判斷電腦上的 "PowerShell.exe" 檔案是否比「2009年7月13日」更新。</span><span class="sxs-lookup"><span data-stu-id="b7134-145">This command uses the **NewerThan** dynamic parameter to determine whether the "PowerShell.exe" file on the computer is newer than "July 13, 2009".</span></span>

<span data-ttu-id="b7134-146">NewerThan 參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="b7134-146">The NewerThan parameter works only in file system drives.</span></span>

```powershell
Test-Path $pshome\PowerShell.exe -NewerThan "July 13, 2009"
```

```Output
True
```

### <span data-ttu-id="b7134-147">範例7：使用 null 做為值來測試路徑</span><span class="sxs-lookup"><span data-stu-id="b7134-147">Example 7: Test a path with null as the value</span></span>

<span data-ttu-id="b7134-148">傳回的錯誤 `null` 、 `null` 或空白陣列的陣列為非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7134-148">The error returned for `null`, array of `null` or empty array is a non-terminating error.</span></span> <span data-ttu-id="b7134-149">您可以使用來隱藏它 `-ErrorAction SilentlyContinue` 。</span><span class="sxs-lookup"><span data-stu-id="b7134-149">It can be suppress by using `-ErrorAction SilentlyContinue`.</span></span> <span data-ttu-id="b7134-150">下列範例會顯示傳回錯誤的所有案例 `NullPathNotPermitted` 。</span><span class="sxs-lookup"><span data-stu-id="b7134-150">The following example shows all cases which return the `NullPathNotPermitted` error.</span></span>

```powershell
Test-Path $null
Test-Path $null, $null
Test-Path @()
```

```Output
Test-Path : Cannot bind argument to parameter 'Path' because it is null.
At line:1 char:11
+ Test-Path $null
+           ~~~~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorNullNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

### <span data-ttu-id="b7134-151">範例8：測試具有空白字元的路徑作為值</span><span class="sxs-lookup"><span data-stu-id="b7134-151">Example 8: Test a path with whitespace as the value</span></span>

<span data-ttu-id="b7134-152">為參數提供空白字元字串時 `-Path` ，會傳回 **True** 。</span><span class="sxs-lookup"><span data-stu-id="b7134-152">When a whitespace string is provided for the the `-Path` parameter, it returns **True** .</span></span> <span data-ttu-id="b7134-153">提供空字串時，會傳回 `Test-Path` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7134-153">When an empty string is provided, `Test-Path` returns an error.</span></span> <span data-ttu-id="b7134-154">下列範例會顯示空白字元和空字串。</span><span class="sxs-lookup"><span data-stu-id="b7134-154">The following example shows whitespace and empty string.</span></span>

```powershell
Test-Path ' '
Test-Path ''
```

```Output
True
Test-Path : Cannot bind argument to parameter 'Path' because it is an empty string.
At line:1 char:11
+ Test-Path ''
+           ~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorEmptyStringNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

## <span data-ttu-id="b7134-155">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b7134-155">PARAMETERS</span></span>

### <span data-ttu-id="b7134-156">-Credential</span><span class="sxs-lookup"><span data-stu-id="b7134-156">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="b7134-157">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="b7134-157">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="b7134-158">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="b7134-158">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7134-159">-Exclude</span><span class="sxs-lookup"><span data-stu-id="b7134-159">-Exclude</span></span>

<span data-ttu-id="b7134-160">指定此 Cmdlet 省略的項目。</span><span class="sxs-lookup"><span data-stu-id="b7134-160">Specifies items that this cmdlet omits.</span></span> <span data-ttu-id="b7134-161">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="b7134-161">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b7134-162">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="b7134-162">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="b7134-163">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b7134-163">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b7134-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="b7134-164">-Filter</span></span>

<span data-ttu-id="b7134-165">以提供者的格式或語言指定篩選。</span><span class="sxs-lookup"><span data-stu-id="b7134-165">Specifies a filter in the format or language of the provider.</span></span> <span data-ttu-id="b7134-166">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="b7134-166">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b7134-167">篩選的語法 (包括是否使用萬用字元) 取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="b7134-167">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span> <span data-ttu-id="b7134-168">篩選比其他參數更有效率，因為提供者會在抓取物件時套用，而不是在抓取物件之後篩選物件。</span><span class="sxs-lookup"><span data-stu-id="b7134-168">Filters are more efficient than other parameters, because the provider applies them when it retrieves the objects instead of having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b7134-169">-Include</span><span class="sxs-lookup"><span data-stu-id="b7134-169">-Include</span></span>

<span data-ttu-id="b7134-170">指定此 Cmdlet 測試的路徑。</span><span class="sxs-lookup"><span data-stu-id="b7134-170">Specifies paths that this cmdlet tests.</span></span> <span data-ttu-id="b7134-171">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="b7134-171">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b7134-172">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="b7134-172">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="b7134-173">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b7134-173">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b7134-174">-IsValid</span><span class="sxs-lookup"><span data-stu-id="b7134-174">-IsValid</span></span>

<span data-ttu-id="b7134-175">指出此 Cmdlet 會測試路徑的語法，無論路徑的元素是否存在。</span><span class="sxs-lookup"><span data-stu-id="b7134-175">Indicates that this cmdlet tests the syntax of the path, regardless of whether the elements of the path exist.</span></span> <span data-ttu-id="b7134-176">`$True`如果路徑語法有效，則這個 Cmdlet 會傳回，否則會傳回 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="b7134-176">This cmdlet returns `$True` if the path syntax is valid and `$False` if it is not.</span></span>

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

### <span data-ttu-id="b7134-177">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b7134-177">-LiteralPath</span></span>

<span data-ttu-id="b7134-178">指定要測試的路徑。</span><span class="sxs-lookup"><span data-stu-id="b7134-178">Specifies a path to be tested.</span></span> <span data-ttu-id="b7134-179">與 **Path** 不同， **LiteralPath** 參數值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="b7134-179">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="b7134-180">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b7134-180">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="b7134-181">如果路徑包含可由 PowerShell 解釋為 escape 序列的字元，您必須將路徑括在單引號中，使其不會被解讀。</span><span class="sxs-lookup"><span data-stu-id="b7134-181">If the path includes characters that could be interpreted by PowerShell as escape sequences, you must enclose the path in single quote so that they won't be interpreted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7134-182">-NewerThan</span><span class="sxs-lookup"><span data-stu-id="b7134-182">-NewerThan</span></span>

<span data-ttu-id="b7134-183">將時間指定為 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="b7134-183">Specify a time as a **DateTime** object.</span></span>

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7134-184">-OlderThan</span><span class="sxs-lookup"><span data-stu-id="b7134-184">-OlderThan</span></span>

<span data-ttu-id="b7134-185">將時間指定為 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="b7134-185">Specify a time as a **DateTime** object.</span></span>

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7134-186">-Path</span><span class="sxs-lookup"><span data-stu-id="b7134-186">-Path</span></span>

<span data-ttu-id="b7134-187">指定要測試的路徑。</span><span class="sxs-lookup"><span data-stu-id="b7134-187">Specifies a path to be tested.</span></span> <span data-ttu-id="b7134-188">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b7134-188">Wildcard characters are permitted.</span></span> <span data-ttu-id="b7134-189">如果路徑包含空格，請將它括在引號中。</span><span class="sxs-lookup"><span data-stu-id="b7134-189">If the path includes spaces, enclose it in quotation marks.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="b7134-190">-PathType</span><span class="sxs-lookup"><span data-stu-id="b7134-190">-PathType</span></span>

<span data-ttu-id="b7134-191">指定路徑中最後一個元素的類型。</span><span class="sxs-lookup"><span data-stu-id="b7134-191">Specifies the type of the final element in the path.</span></span> <span data-ttu-id="b7134-192">`$True`如果元素是指定的類型，則這個 Cmdlet 會傳回，否則會傳回 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="b7134-192">This cmdlet returns `$True` if the element is of the specified type and `$False` if it is not.</span></span> <span data-ttu-id="b7134-193">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="b7134-193">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b7134-194">容器。</span><span class="sxs-lookup"><span data-stu-id="b7134-194">Container.</span></span>
  <span data-ttu-id="b7134-195">包含其他元素的元素，例如目錄或登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="b7134-195">An element that contains other elements, such as a directory or registry key.</span></span>
- <span data-ttu-id="b7134-196">葉。</span><span class="sxs-lookup"><span data-stu-id="b7134-196">Leaf.</span></span>
  <span data-ttu-id="b7134-197">未包含其他元素 (例如檔案) 的元素。</span><span class="sxs-lookup"><span data-stu-id="b7134-197">An element that does not contain other elements, such as a file.</span></span>
- <span data-ttu-id="b7134-198">任何。</span><span class="sxs-lookup"><span data-stu-id="b7134-198">Any.</span></span>
  <span data-ttu-id="b7134-199">容器或分葉。</span><span class="sxs-lookup"><span data-stu-id="b7134-199">Either a container or a leaf.</span></span>

<span data-ttu-id="b7134-200">告知路徑中的最終元素是否為特定類型。</span><span class="sxs-lookup"><span data-stu-id="b7134-200">Tells whether the final element in the path is of a particular type.</span></span>

> [!CAUTION]
>
> <span data-ttu-id="b7134-201">最多 PowerShell 版本6.1.2，同時指定 **IsValid** 和 **PathType** 參數時，此 Cmdlet 會 `Test-Path` 忽略 **PathType** 參數，並只驗證語法路徑，而不會驗證路徑類型。</span><span class="sxs-lookup"><span data-stu-id="b7134-201">Up to PowerShell version 6.1.2, when the **IsValid** and **PathType** switches are specified together, the `Test-Path` cmdlet ignores the **PathType** switch and only validates the syntactic path without validating the path type.</span></span>
>
> <span data-ttu-id="b7134-202">根據 [問題 #8607](https://github.com/PowerShell/PowerShell/issues/8607)，修正此行為可能是未來版本中的重大變更，其中 **IsValid** 和 **PathType** 參數屬於不同的參數集，因此無法一起使用以避免混淆。</span><span class="sxs-lookup"><span data-stu-id="b7134-202">According to [issue #8607](https://github.com/PowerShell/PowerShell/issues/8607), fixing this behavior may be a breaking change in a future version, where the **IsValid** and **PathType** switches belong to separate parameter sets, and thus, cannot be used together avoiding this confusion.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.TestPathType
Parameter Sets: (All)
Aliases: Type
Accepted values: Any, Container, Leaf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7134-203">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="b7134-203">-UseTransaction</span></span>

<span data-ttu-id="b7134-204">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="b7134-204">Includes the command in the active transaction.</span></span> <span data-ttu-id="b7134-205">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="b7134-205">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="b7134-206">如需詳細資訊，請參閱 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)</span><span class="sxs-lookup"><span data-stu-id="b7134-206">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7134-207">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7134-207">CommonParameters</span></span>

<span data-ttu-id="b7134-208">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="b7134-208">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="b7134-209">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b7134-209">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b7134-210">輸入</span><span class="sxs-lookup"><span data-stu-id="b7134-210">INPUTS</span></span>

### <span data-ttu-id="b7134-211">System.String</span><span class="sxs-lookup"><span data-stu-id="b7134-211">System.String</span></span>

<span data-ttu-id="b7134-212">您可以使用管線將包含路徑 (但不是常值路徑) 的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b7134-212">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="b7134-213">輸出</span><span class="sxs-lookup"><span data-stu-id="b7134-213">OUTPUTS</span></span>

### <span data-ttu-id="b7134-214">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="b7134-214">System.Boolean</span></span>

<span data-ttu-id="b7134-215">Cmdlet 會傳回 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="b7134-215">The cmdlet returns a **Boolean** value.</span></span>

## <span data-ttu-id="b7134-216">注意</span><span class="sxs-lookup"><span data-stu-id="b7134-216">NOTES</span></span>

<span data-ttu-id="b7134-217">包含路徑名詞 (Path **Cmdlet 的 Cmdlet** 會 **Path** ) 使用路徑名稱，並傳回所有 PowerShell 提供者都可解讀的精簡格式名稱。</span><span class="sxs-lookup"><span data-stu-id="b7134-217">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="b7134-218">它們是設計用於程式與指令碼，您可以在其中以特定格式顯示所有或部分路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="b7134-218">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span>
<span data-ttu-id="b7134-219">您可以使用 **Dirname** 、 **Normpath** 、 **Realpath** 、 **Join** 或其他路徑操作工具。</span><span class="sxs-lookup"><span data-stu-id="b7134-219">Use them as you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

<span data-ttu-id="b7134-220">`Test-Path`是設計來處理任何提供者所公開的資料。</span><span class="sxs-lookup"><span data-stu-id="b7134-220">The `Test-Path` is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="b7134-221">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="b7134-221">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="b7134-222">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="b7134-222">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="b7134-223">相關連結</span><span class="sxs-lookup"><span data-stu-id="b7134-223">RELATED LINKS</span></span>

[<span data-ttu-id="b7134-224">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="b7134-224">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="b7134-225">Join-Path</span><span class="sxs-lookup"><span data-stu-id="b7134-225">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="b7134-226">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="b7134-226">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="b7134-227">Split-Path</span><span class="sxs-lookup"><span data-stu-id="b7134-227">Split-Path</span></span>](Split-Path.md)