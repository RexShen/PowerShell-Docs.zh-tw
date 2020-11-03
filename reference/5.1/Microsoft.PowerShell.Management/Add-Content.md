---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 903c4eb784c1bb86b66766c7dfb563f586545dc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204092"
---
# <span data-ttu-id="cf747-103">Add-Content</span><span class="sxs-lookup"><span data-stu-id="cf747-103">Add-Content</span></span>

## <span data-ttu-id="cf747-104">概要</span><span class="sxs-lookup"><span data-stu-id="cf747-104">SYNOPSIS</span></span>
<span data-ttu-id="cf747-105">新增內容至指定的項目，例如將文字新增到檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-105">Adds content to the specified items, such as adding words to a file.</span></span>

## <span data-ttu-id="cf747-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cf747-106">SYNTAX</span></span>

### <span data-ttu-id="cf747-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="cf747-107">Path (Default)</span></span>

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

### <span data-ttu-id="cf747-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="cf747-108">LiteralPath</span></span>

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

## <span data-ttu-id="cf747-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cf747-109">DESCRIPTION</span></span>

<span data-ttu-id="cf747-110">Cmdlet 會將 `Add-Content` 內容附加至指定的專案或檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-110">The `Add-Content` cmdlet appends content to a specified item or file.</span></span> <span data-ttu-id="cf747-111">您可以在命令中輸入內容或透過指定包含內容的物件指定內容。</span><span class="sxs-lookup"><span data-stu-id="cf747-111">You can specify the content by typing the content in the command or by specifying an object that contains the content.</span></span>

<span data-ttu-id="cf747-112">如果您需要建立下列範例的檔案或目錄，請參閱 [新專案](New-Item.md)。</span><span class="sxs-lookup"><span data-stu-id="cf747-112">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="cf747-113">範例</span><span class="sxs-lookup"><span data-stu-id="cf747-113">EXAMPLES</span></span>

### <span data-ttu-id="cf747-114">範例1：將字串新增至所有文字檔，但有例外狀況</span><span class="sxs-lookup"><span data-stu-id="cf747-114">Example 1: Add a string to all text files with an exception</span></span>

<span data-ttu-id="cf747-115">此範例會將值附加至目前的目錄中的文字檔，但會根據檔案的檔案名來排除這些檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-115">This example appends a value to text files in the current directory but excludes files based on their file name.</span></span>

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

<span data-ttu-id="cf747-116">此 `Add-Content` Cmdlet 會使用 **Path** 參數來指定目前目錄中的所有 .txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-116">The `Add-Content` cmdlet uses the **Path** parameter to specify all .txt files in the current directory.</span></span> <span data-ttu-id="cf747-117">**Exclude** 參數會忽略符合指定模式的檔案名。</span><span class="sxs-lookup"><span data-stu-id="cf747-117">The **Exclude** parameter ignores file names that match the specified pattern.</span></span> <span data-ttu-id="cf747-118">**Value** 參數會指定寫入檔案的文字字串。</span><span class="sxs-lookup"><span data-stu-id="cf747-118">The **Value** parameter specifies the text string that is written to the files.</span></span>

<span data-ttu-id="cf747-119">使用 [ [取得內容](Get-Content.md) ] 來顯示這些檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="cf747-119">Use [Get-Content](Get-Content.md) to display the contents of these files.</span></span>

### <span data-ttu-id="cf747-120">範例2：在指定檔案的結尾加上日期</span><span class="sxs-lookup"><span data-stu-id="cf747-120">Example 2: Add a date to the end of the specified files</span></span>

<span data-ttu-id="cf747-121">此範例會將日期附加至目前目錄中的檔案，並在 PowerShell 主控台中顯示日期。</span><span class="sxs-lookup"><span data-stu-id="cf747-121">This example appends the date to files in the current directory and displays the date in the PowerShell console.</span></span>

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

<span data-ttu-id="cf747-122">此 `Add-Content` Cmdlet 會使用 **Path** 和 **Value** 參數，在目前的目錄中建立兩個新檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-122">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create two new files in the current directory.</span></span> <span data-ttu-id="cf747-123">**Value** 參數指定 `Get-Date` 取得日期並將日期傳遞給的 Cmdlet `Add-Content` 。</span><span class="sxs-lookup"><span data-stu-id="cf747-123">The **Value** parameter specifies the `Get-Date` cmdlet to get the date and passes the date to `Add-Content`.</span></span> <span data-ttu-id="cf747-124">Cmdlet 會將 `Add-Content` 日期寫入每個檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-124">The `Add-Content` cmdlet writes the date to each file.</span></span> <span data-ttu-id="cf747-125">**PassThru** 參數會傳遞代表 date 物件的物件。</span><span class="sxs-lookup"><span data-stu-id="cf747-125">The **PassThru** parameter passes an object that represents the date object.</span></span> <span data-ttu-id="cf747-126">因為沒有任何其他 Cmdlet 接收傳遞的物件，所以它會顯示在 PowerShell 主控台中。</span><span class="sxs-lookup"><span data-stu-id="cf747-126">Because there is no other cmdlet to receive the passed object, it is displayed in the PowerShell console.</span></span> <span data-ttu-id="cf747-127">此 `Get-Content` Cmdlet 會顯示已更新的檔案 DateTimeFile1。</span><span class="sxs-lookup"><span data-stu-id="cf747-127">The `Get-Content` cmdlet displays the updated file, DateTimeFile1.log.</span></span>

### <span data-ttu-id="cf747-128">範例3：將指定檔案的內容加入至另一個檔案</span><span class="sxs-lookup"><span data-stu-id="cf747-128">Example 3: Add the contents of a specified file to another file</span></span>

<span data-ttu-id="cf747-129">此範例會從檔案取得內容，並將該內容附加至另一個檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-129">This example gets the content from a file and appends that content into another file.</span></span>

```powershell
Add-Content -Path .\CopyToFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="cf747-130">此 `Add-Content` Cmdlet 會使用 **Path** 參數來指定目前目錄中的新檔案，CopyToFile.txt。</span><span class="sxs-lookup"><span data-stu-id="cf747-130">The `Add-Content` cmdlet uses the **Path** parameter to specify the new file in the current directory, CopyToFile.txt.</span></span> <span data-ttu-id="cf747-131">**Value** 參數會使用 `Get-Content` Cmdlet 取得檔案的內容，CopyFromFile.txt。</span><span class="sxs-lookup"><span data-stu-id="cf747-131">The **Value** parameter uses the `Get-Content` cmdlet to get the contents of the file, CopyFromFile.txt.</span></span> <span data-ttu-id="cf747-132">Cmdlet 周圍的括弧 `Get-Content` 可確保命令會在 `Add-Content` 命令開始之前完成。</span><span class="sxs-lookup"><span data-stu-id="cf747-132">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span> <span data-ttu-id="cf747-133">**值** 參數會傳遞至 `Add-Content` 。</span><span class="sxs-lookup"><span data-stu-id="cf747-133">The **Value** parameter is passed to `Add-Content`.</span></span> <span data-ttu-id="cf747-134">Cmdlet 會將 `Add-Content` 資料附加至 CopyToFile.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-134">The `Add-Content` cmdlet appends the data to the CopyToFile.txt file.</span></span> <span data-ttu-id="cf747-135">此 `Get-Content` Cmdlet 會顯示已更新的檔案 CopyToFile.txt。</span><span class="sxs-lookup"><span data-stu-id="cf747-135">The `Get-Content` cmdlet displays the updated file, CopyToFile.txt.</span></span>

### <span data-ttu-id="cf747-136">範例4：使用變數將指定檔案的內容加入至另一個檔案</span><span class="sxs-lookup"><span data-stu-id="cf747-136">Example 4: Use a variable to add the contents of a specified file to another file</span></span>

<span data-ttu-id="cf747-137">此範例會從檔案取得內容，並將內容儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="cf747-137">This example gets the content from a file and stores the content in a variable.</span></span> <span data-ttu-id="cf747-138">變數是用來將內容附加至另一個檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-138">The variable is used to append the content into another file.</span></span>

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="cf747-139">`Get-Content`Cmdlet 會取得 CopyFromFile.txt 的內容，並將內容儲存在 `$From` 變數中。</span><span class="sxs-lookup"><span data-stu-id="cf747-139">The `Get-Content` cmdlet gets the contents of CopyFromFile.txt and stores the contents in the `$From` variable.</span></span> <span data-ttu-id="cf747-140">此 `Add-Content` Cmdlet 會使用 **Path** 參數來指定目前目錄中的 CopyToFile.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-140">The `Add-Content` cmdlet uses the **Path** parameter to specify the CopyToFile.txt file in the current directory.</span></span> <span data-ttu-id="cf747-141">**Value** 參數會使用 `$From` 變數，並將內容傳遞給 `Add-Content` 。</span><span class="sxs-lookup"><span data-stu-id="cf747-141">The **Value** parameter uses the `$From` variable and passes the content to `Add-Content`.</span></span> <span data-ttu-id="cf747-142">`Add-Content`Cmdlet 會更新 CopyToFile.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-142">The `Add-Content` cmdlet updates the CopyToFile.txt file.</span></span> <span data-ttu-id="cf747-143">`Get-Content`Cmdlet 會顯示 CopyToFile.txt。</span><span class="sxs-lookup"><span data-stu-id="cf747-143">The `Get-Content` cmdlet displays CopyToFile.txt.</span></span>

### <span data-ttu-id="cf747-144">範例5：建立新的檔案並複製內容</span><span class="sxs-lookup"><span data-stu-id="cf747-144">Example 5: Create a new file and copy content</span></span>

<span data-ttu-id="cf747-145">這個範例會建立新的檔案，並將現有檔案的內容複寫到新檔案中。</span><span class="sxs-lookup"><span data-stu-id="cf747-145">This example creates a new file and copies an existing file's content into the new file.</span></span>

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

<span data-ttu-id="cf747-146">此 `Add-Content` Cmdlet 會使用 **Path** 和 **Value** 參數在目前的目錄中建立新檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-146">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create a new file in the current directory.</span></span> <span data-ttu-id="cf747-147">**Value** 參數會使用 `Get-Content` Cmdlet 來取得現有檔案的內容，CopyFromFile.txt。</span><span class="sxs-lookup"><span data-stu-id="cf747-147">The **Value** parameter uses the `Get-Content` cmdlet to get the contents of an existing file, CopyFromFile.txt.</span></span> <span data-ttu-id="cf747-148">Cmdlet 周圍的括弧 `Get-Content` 可確保命令會在 `Add-Content` 命令開始之前完成。</span><span class="sxs-lookup"><span data-stu-id="cf747-148">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span> <span data-ttu-id="cf747-149">**Value** 參數會傳遞更新 NewFile.txt 檔案的內容 `Add-Content` 。</span><span class="sxs-lookup"><span data-stu-id="cf747-149">The **Value** parameter passes the content to `Add-Content` which updates the NewFile.txt file.</span></span> <span data-ttu-id="cf747-150">`Get-Content`Cmdlet 會顯示新檔案的內容 NewFile.txt。</span><span class="sxs-lookup"><span data-stu-id="cf747-150">The `Get-Content` cmdlet displays the contents of the new file, NewFile.txt.</span></span>

### <span data-ttu-id="cf747-151">範例6：將內容新增至唯讀檔案</span><span class="sxs-lookup"><span data-stu-id="cf747-151">Example 6: Add content to a read-only file</span></span>

<span data-ttu-id="cf747-152">此命令會將值新增至檔案，即使 **IsReadOnly** 檔案屬性設定為 True 也是如此。</span><span class="sxs-lookup"><span data-stu-id="cf747-152">This command adds the value to the file even if the **IsReadOnly** file attribute is set to True.</span></span>
<span data-ttu-id="cf747-153">範例中包含建立唯讀檔案的步驟。</span><span class="sxs-lookup"><span data-stu-id="cf747-153">The steps to create a read-only file are included in the example.</span></span>

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar---        1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

<span data-ttu-id="cf747-154">此 `New-Item` Cmdlet 會使用 **Path** 和 **ItemType** 參數，在目前的目錄中建立檔案 IsReadOnlyTextFile.txt。</span><span class="sxs-lookup"><span data-stu-id="cf747-154">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the file IsReadOnlyTextFile.txt in the current directory.</span></span> <span data-ttu-id="cf747-155">此 `Set-ItemProperty` Cmdlet 會使用 **Name** 和 **Value** 參數將檔案的 **IsReadOnly** 屬性變更為 True。</span><span class="sxs-lookup"><span data-stu-id="cf747-155">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to True.</span></span> <span data-ttu-id="cf747-156">此 `Get-ChildItem` Cmdlet 會顯示 (0) 的檔案是空的，且 () 的唯讀屬性 `r` 。</span><span class="sxs-lookup"><span data-stu-id="cf747-156">The `Get-ChildItem` cmdlet shows the file is empty (0) and has the read-only attribute (`r`).</span></span> <span data-ttu-id="cf747-157">此 `Add-Content` Cmdlet 會使用 **Path** 參數來指定檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-157">The `Add-Content` cmdlet uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="cf747-158">**Value** 參數包含要附加至檔案的文字字串。</span><span class="sxs-lookup"><span data-stu-id="cf747-158">The **Value** parameter includes the text string to append to the file.</span></span> <span data-ttu-id="cf747-159">**Force** 參數會將文字寫入至唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-159">The **Force** parameter writes the text to the read-only file.</span></span> <span data-ttu-id="cf747-160">此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="cf747-160">The `Get-Content` cmdlet uses the **Path** parameter to display the file's contents.</span></span>

<span data-ttu-id="cf747-161">若要移除唯讀屬性，請使用命令， `Set-ItemProperty` 並將 **Value** 參數設定為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="cf747-161">To remove the read-only attribute, use the `Set-ItemProperty` command with the **Value** parameter set to `False`.</span></span>

## <span data-ttu-id="cf747-162">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cf747-162">PARAMETERS</span></span>

### <span data-ttu-id="cf747-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cf747-163">-Confirm</span></span>

<span data-ttu-id="cf747-164">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="cf747-164">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cf747-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="cf747-165">-Credential</span></span>

<span data-ttu-id="cf747-166">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cf747-166">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="cf747-167">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="cf747-167">The default is the current user.</span></span>

<span data-ttu-id="cf747-168">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="cf747-168">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="cf747-169">若您輸入使用者名稱，將會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="cf747-169">If you type a user name, you will be prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="cf747-170">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="cf747-170">This parameter is not supported by any providers installed with PowerShell.</span></span>

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

### <span data-ttu-id="cf747-171">-Encoding</span><span class="sxs-lookup"><span data-stu-id="cf747-171">-Encoding</span></span>

<span data-ttu-id="cf747-172">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="cf747-172">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="cf747-173">預設值是 `Default`。</span><span class="sxs-lookup"><span data-stu-id="cf747-173">The default value is `Default`.</span></span>

<span data-ttu-id="cf747-174">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="cf747-174">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="cf747-175">`Ascii` 使用 ASCII (7 位) 字元集。</span><span class="sxs-lookup"><span data-stu-id="cf747-175">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="cf747-176">`BigEndianUnicode` 以位元組由大到小的順序使用 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="cf747-176">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="cf747-177">`BigEndianUTF32` 使用具有位元組由大到小的 32 UTF-8 順序。</span><span class="sxs-lookup"><span data-stu-id="cf747-177">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="cf747-178">`Byte` 將一組字元編碼成位元組序列。</span><span class="sxs-lookup"><span data-stu-id="cf747-178">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="cf747-179">`Default` 使用與系統的作用中字碼頁對應的編碼， (通常是 ANSI) 。</span><span class="sxs-lookup"><span data-stu-id="cf747-179">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="cf747-180">`Oem` 使用對應至系統目前 OEM 字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="cf747-180">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="cf747-181">`String` 與 **Unicode** 相同。</span><span class="sxs-lookup"><span data-stu-id="cf747-181">`String` Same as **Unicode** .</span></span>
- <span data-ttu-id="cf747-182">`Unicode` 使用 UTF-16 和位元組由小到小的位元組順序。</span><span class="sxs-lookup"><span data-stu-id="cf747-182">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="cf747-183">`Unknown` 與 **Unicode** 相同。</span><span class="sxs-lookup"><span data-stu-id="cf747-183">`Unknown` Same as **Unicode** .</span></span>
- <span data-ttu-id="cf747-184">`UTF7` 使用 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="cf747-184">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="cf747-185">`UTF8` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="cf747-185">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="cf747-186">`UTF32` 以位元組由小到大的位元組順序使用 UTF-32。</span><span class="sxs-lookup"><span data-stu-id="cf747-186">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="cf747-187">Encoding 是動態參數，FileSystem 提供者會將它新增至 `Add-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cf747-187">Encoding is a dynamic parameter that the FileSystem provider adds to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="cf747-188">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="cf747-188">This parameter works only in file system drives.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, Byte, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cf747-189">-Exclude</span><span class="sxs-lookup"><span data-stu-id="cf747-189">-Exclude</span></span>

<span data-ttu-id="cf747-190">省略指定的項目。</span><span class="sxs-lookup"><span data-stu-id="cf747-190">Omits the specified items.</span></span> <span data-ttu-id="cf747-191">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="cf747-191">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="cf747-192">輸入路徑元素或模式，例如 **\* .txt** 。</span><span class="sxs-lookup"><span data-stu-id="cf747-192">Enter a path element or pattern, such as **\*.txt** .</span></span> <span data-ttu-id="cf747-193">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cf747-193">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="cf747-194">-Filter</span><span class="sxs-lookup"><span data-stu-id="cf747-194">-Filter</span></span>

<span data-ttu-id="cf747-195">以提供者的格式或語言指定篩選。</span><span class="sxs-lookup"><span data-stu-id="cf747-195">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="cf747-196">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="cf747-196">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="cf747-197">篩選的語法 (包括是否使用萬用字元) 取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="cf747-197">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="cf747-198">**篩選** 比其他參數更有效率，因為提供者會在抓取物件時套用篩選。</span><span class="sxs-lookup"><span data-stu-id="cf747-198">**Filters** are more efficient than other parameters because the provider applies filters when objects are retrieved.</span></span> <span data-ttu-id="cf747-199">否則，PowerShell 會在抓取物件之後處理篩選。</span><span class="sxs-lookup"><span data-stu-id="cf747-199">Otherwise, PowerShell processes filters after the objects are retrieved.</span></span>

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

### <span data-ttu-id="cf747-200">-Force</span><span class="sxs-lookup"><span data-stu-id="cf747-200">-Force</span></span>

<span data-ttu-id="cf747-201">覆寫唯讀屬性，可讓您新增內容至唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="cf747-201">Overrides the read-only attribute, allowing you to add content to a read-only file.</span></span> <span data-ttu-id="cf747-202">例如， **Force** 會覆寫唯讀屬性或建立目錄來完成檔案路徑，但不會嘗試變更檔案權限。</span><span class="sxs-lookup"><span data-stu-id="cf747-202">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="cf747-203">-Include</span><span class="sxs-lookup"><span data-stu-id="cf747-203">-Include</span></span>

<span data-ttu-id="cf747-204">只新增指定的項目。</span><span class="sxs-lookup"><span data-stu-id="cf747-204">Adds only the specified items.</span></span> <span data-ttu-id="cf747-205">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="cf747-205">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="cf747-206">輸入路徑元素或模式，例如 **\* .txt** 。</span><span class="sxs-lookup"><span data-stu-id="cf747-206">Enter a path element or pattern, such as **\*.txt** .</span></span> <span data-ttu-id="cf747-207">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cf747-207">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="cf747-208">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="cf747-208">-LiteralPath</span></span>

<span data-ttu-id="cf747-209">指定要接收其他內容的項目路徑。</span><span class="sxs-lookup"><span data-stu-id="cf747-209">Specifies the path to the items that receive the additional content.</span></span> <span data-ttu-id="cf747-210">與 **Path** 不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="cf747-210">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="cf747-211">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cf747-211">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="cf747-212">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="cf747-212">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="cf747-213">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="cf747-213">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="cf747-214">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="cf747-214">-NoNewline</span></span>

<span data-ttu-id="cf747-215">指出此 Cmdlet 不會將新的一行或換行內容新增至內容。</span><span class="sxs-lookup"><span data-stu-id="cf747-215">Indicates that this cmdlet does not add a new line or carriage return to the content.</span></span>

<span data-ttu-id="cf747-216">輸入物件的字串表示會串連以形成輸出。</span><span class="sxs-lookup"><span data-stu-id="cf747-216">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="cf747-217">輸出字串之間不會插入空格或分行符號。</span><span class="sxs-lookup"><span data-stu-id="cf747-217">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="cf747-218">最後一個輸出字串之後不會加入任何新行。</span><span class="sxs-lookup"><span data-stu-id="cf747-218">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="cf747-219">-PassThru</span><span class="sxs-lookup"><span data-stu-id="cf747-219">-PassThru</span></span>

<span data-ttu-id="cf747-220">傳回代表新增內容的物件。</span><span class="sxs-lookup"><span data-stu-id="cf747-220">Returns an object representing the added content.</span></span> <span data-ttu-id="cf747-221">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="cf747-221">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="cf747-222">-Path</span><span class="sxs-lookup"><span data-stu-id="cf747-222">-Path</span></span>

<span data-ttu-id="cf747-223">指定要接收其他內容的項目路徑。</span><span class="sxs-lookup"><span data-stu-id="cf747-223">Specifies the path to the items that receive the additional content.</span></span> <span data-ttu-id="cf747-224">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cf747-224">Wildcards are permitted.</span></span> <span data-ttu-id="cf747-225">如果您指定多個路徑，請使用逗號來分隔路徑。</span><span class="sxs-lookup"><span data-stu-id="cf747-225">If you specify multiple paths, use commas to separate the paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="cf747-226">-Stream</span><span class="sxs-lookup"><span data-stu-id="cf747-226">-Stream</span></span>

<span data-ttu-id="cf747-227">指定內容的替代資料流程。</span><span class="sxs-lookup"><span data-stu-id="cf747-227">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="cf747-228">如果資料流程不存在，此 Cmdlet 會建立該資料流程。</span><span class="sxs-lookup"><span data-stu-id="cf747-228">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="cf747-229">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cf747-229">Wildcard characters are not supported.</span></span>

<span data-ttu-id="cf747-230">**Stream** 是動態參數，FileSystem 提供者會將其加入至 `Add-Content` 。</span><span class="sxs-lookup"><span data-stu-id="cf747-230">**Stream** is a dynamic parameter that the FileSystem provider adds to `Add-Content`.</span></span> <span data-ttu-id="cf747-231">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="cf747-231">This parameter works only in file system drives.</span></span>

<span data-ttu-id="cf747-232">您可以使用 `Add-Content` Cmdlet 來變更區域的內容 **。識別碼** 替代資料流程。</span><span class="sxs-lookup"><span data-stu-id="cf747-232">You can use the `Add-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="cf747-233">不過，我們不建議您這樣做，以排除封鎖從網際網路下載之檔案的安全性檢查。</span><span class="sxs-lookup"><span data-stu-id="cf747-233">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="cf747-234">如果您確認下載的檔案是安全的，請使用 `Unblock-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cf747-234">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="cf747-235">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="cf747-235">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="cf747-236">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="cf747-236">-UseTransaction</span></span>

<span data-ttu-id="cf747-237">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="cf747-237">Includes the command in the active transaction.</span></span> <span data-ttu-id="cf747-238">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="cf747-238">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="cf747-239">如需詳細資訊，請參閱 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="cf747-239">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="cf747-240">-Value</span><span class="sxs-lookup"><span data-stu-id="cf747-240">-Value</span></span>

<span data-ttu-id="cf747-241">指定要新增的內容。</span><span class="sxs-lookup"><span data-stu-id="cf747-241">Specifies the content to be added.</span></span> <span data-ttu-id="cf747-242">輸入加上引號的字串，例如 **此資料僅供內部使用** ，或指定包含內容的物件，例如產生的 **DateTime** 物件 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="cf747-242">Type a quoted string, such as **This data is for internal use only** , or specify an object that contains content, such as the **DateTime** object that `Get-Date` generates.</span></span>

<span data-ttu-id="cf747-243">您無法藉由輸入檔案的路徑來指定檔案的內容，因為路徑只是一個字串。</span><span class="sxs-lookup"><span data-stu-id="cf747-243">You cannot specify the contents of a file by typing its path, because the path is just a string.</span></span>
<span data-ttu-id="cf747-244">您可以使用 `Get-Content` 命令取得內容，並將其傳遞至 **Value** 參數。</span><span class="sxs-lookup"><span data-stu-id="cf747-244">You can use a `Get-Content` command to get the content and pass it to the **Value** parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cf747-245">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cf747-245">-WhatIf</span></span>

<span data-ttu-id="cf747-246">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="cf747-246">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="cf747-247">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="cf747-247">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cf747-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cf747-248">CommonParameters</span></span>

<span data-ttu-id="cf747-249">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="cf747-249">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="cf747-250">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cf747-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cf747-251">輸入</span><span class="sxs-lookup"><span data-stu-id="cf747-251">INPUTS</span></span>

### <span data-ttu-id="cf747-252">System.string、System.object、system.string</span><span class="sxs-lookup"><span data-stu-id="cf747-252">System.Object, System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="cf747-253">您可以透過管道將值、路徑或認證傳送至 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="cf747-253">You can pipe values, paths, or credentials to `Set-Content`.</span></span>

## <span data-ttu-id="cf747-254">輸出</span><span class="sxs-lookup"><span data-stu-id="cf747-254">OUTPUTS</span></span>

### <span data-ttu-id="cf747-255">無或 System.String</span><span class="sxs-lookup"><span data-stu-id="cf747-255">None or System.String</span></span>

<span data-ttu-id="cf747-256">當您使用 **PassThru** 參數時，會 `Add-Content` 產生代表內容的 **system.string** 物件。</span><span class="sxs-lookup"><span data-stu-id="cf747-256">When you use the **PassThru** parameter, `Add-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="cf747-257">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="cf747-257">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="cf747-258">注意</span><span class="sxs-lookup"><span data-stu-id="cf747-258">NOTES</span></span>

<span data-ttu-id="cf747-259">當您使用管線將物件傳送至時 `Add-Content` ，會先將物件轉換成字串，然後再將它加入至專案。</span><span class="sxs-lookup"><span data-stu-id="cf747-259">When you pipe an object to `Add-Content`, the object is converted to a string before it is added to the item.</span></span> <span data-ttu-id="cf747-260">物件類型決定字串格式，但是格式可能會不同於物件的預設顯示。</span><span class="sxs-lookup"><span data-stu-id="cf747-260">The object type determines the string format, but the format might be different than the default display of the object.</span></span> <span data-ttu-id="cf747-261">若要控制字串格式，請使用傳送 Cmdlet 的格式化參數。</span><span class="sxs-lookup"><span data-stu-id="cf747-261">To control the string format, use the formatting parameters of the sending cmdlet.</span></span>

<span data-ttu-id="cf747-262">您也可以 `Add-Content` 使用內建的別名來參考 `ac` 。</span><span class="sxs-lookup"><span data-stu-id="cf747-262">You can also refer to `Add-Content` by its built-in alias, `ac`.</span></span> <span data-ttu-id="cf747-263">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="cf747-263">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="cf747-264">此 `Add-Content` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="cf747-264">The `Add-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="cf747-265">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="cf747-265">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="cf747-266">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="cf747-266">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="cf747-267">相關連結</span><span class="sxs-lookup"><span data-stu-id="cf747-267">RELATED LINKS</span></span>

[<span data-ttu-id="cf747-268">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="cf747-268">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="cf747-269">about_Providers</span><span class="sxs-lookup"><span data-stu-id="cf747-269">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="cf747-270">about_Transactions</span><span class="sxs-lookup"><span data-stu-id="cf747-270">about_Transactions</span></span>](../Microsoft.PowerShell.Core/About/about_Transactions.md)

[<span data-ttu-id="cf747-271">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="cf747-271">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="cf747-272">Get-Content</span><span class="sxs-lookup"><span data-stu-id="cf747-272">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="cf747-273">Get-Item</span><span class="sxs-lookup"><span data-stu-id="cf747-273">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="cf747-274">New-Item</span><span class="sxs-lookup"><span data-stu-id="cf747-274">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="cf747-275">Set-Content</span><span class="sxs-lookup"><span data-stu-id="cf747-275">Set-Content</span></span>](Set-Content.md)
