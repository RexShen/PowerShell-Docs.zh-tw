---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-localizeddata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-LocalizedData
ms.openlocfilehash: 552e37f8bef096ec7d072d41186f8919bc58f630
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203775"
---
# <span data-ttu-id="cf9dd-103">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="cf9dd-103">Import-LocalizedData</span></span>

## <span data-ttu-id="cf9dd-104">概要</span><span class="sxs-lookup"><span data-stu-id="cf9dd-104">SYNOPSIS</span></span>
<span data-ttu-id="cf9dd-105">根據為作業系統選取的 UI 文化特性，將語言特定資料匯入指令碼和函式。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-105">Imports language-specific data into scripts and functions based on the UI culture that is selected for the operating system.</span></span>

## <span data-ttu-id="cf9dd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cf9dd-106">SYNTAX</span></span>

```
Import-LocalizedData [[-BindingVariable] <String>] [[-UICulture] <String>] [-BaseDirectory <String>]
 [-FileName <String>] [-SupportedCommand <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="cf9dd-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cf9dd-107">DESCRIPTION</span></span>

<span data-ttu-id="cf9dd-108">**Import-LocalizedData** Cmdlet 會從名稱與為作業系統目前使用者設定之 UI 語言相符的子目錄動態抓取字串。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-108">The **Import-LocalizedData** cmdlet dynamically retrieves strings from a subdirectory whose name matches the UI language set for the current user of the operating system.</span></span>
<span data-ttu-id="cf9dd-109">它是專為讓指令碼以目前使用者選取的 UI 語言顯示使用者訊息而設計。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-109">It is designed to enable scripts to display user messages in the UI language selected by the current user.</span></span>

<span data-ttu-id="cf9dd-110">**Import-LocalizedData** 會從指令碼目錄之語言特定子目錄中的 .psd1 檔案匯入資料，並將其儲存在命令中指定的區域變數中。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-110">**Import-LocalizedData** imports data from .psd1 files in language-specific subdirectories of the script directory and saves them in a local variable that is specified in the command.</span></span>
<span data-ttu-id="cf9dd-111">這個 Cmdlet 會根據 $PSUICulture 自動變數的值來選取子目錄和檔案。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-111">The cmdlet selects the subdirectory and file based on the value of the $PSUICulture automatic variable.</span></span>
<span data-ttu-id="cf9dd-112">在指令碼中使用區域變數來顯示使用者訊息時，訊息會以使用者的 UI 語言顯示。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-112">When you use the local variable in the script to display a user message, the message appears in the user's UI language.</span></span>

<span data-ttu-id="cf9dd-113">您可以使用 **Import-LocalizedData** 的參數來指定替代的 UI 文化特性、路徑及檔案名稱、新增支援的命令，以及抑制找不到 .psd1 檔案時所顯示的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-113">You can use the parameters of **Import-LocalizedData** to specify an alternate UI culture, path, and file name, to add supported commands, and to suppress the error message that appears if the .psd1 files are not found.</span></span>

<span data-ttu-id="cf9dd-114">**Import-LocalizedData** Cmdlet 支援 Windows PowerShell 2.0 中所導入的指令碼國際化計畫。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-114">The **Import-LocalizedData** cmdlet supports the script internationalization initiative that was introduced in Windows PowerShell 2.0.</span></span>
<span data-ttu-id="cf9dd-115">這個計畫的目標是要藉由讓指令碼能輕鬆以目前使用者的 UI 語言顯示使用者訊息，為世界各地的使用者提供更好的服務。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-115">This initiative aims to better serve users worldwide by making it easy for scripts to display user messages in the UI language of the current user.</span></span>
<span data-ttu-id="cf9dd-116">如需有關此計畫及 .psd1 檔案格式的詳細資訊，請參閱 about_Script_Internationalization。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-116">For more information about this and about the format of the .psd1 files, see about_Script_Internationalization.</span></span>

## <span data-ttu-id="cf9dd-117">範例</span><span class="sxs-lookup"><span data-stu-id="cf9dd-117">EXAMPLES</span></span>

### <span data-ttu-id="cf9dd-118">範例 1︰匯入文字字串</span><span class="sxs-lookup"><span data-stu-id="cf9dd-118">Example 1: Import text strings</span></span>

```
PS C:\> Import-LocalizedData -BindingVariable "Messages"
```

<span data-ttu-id="cf9dd-119">這個命令會將文字字串匯入到 $Messages 變數中。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-119">This command imports text strings into the $Messages variable.</span></span>
<span data-ttu-id="cf9dd-120">它會使用所有其他 Cmdlet 參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-120">It uses the default values of all other cmdlet parameters.</span></span>

<span data-ttu-id="cf9dd-121">如果此命令包含在 C:\Test 目錄下的 Archives.ps1 指令碼中，並且 $PsUICulture 自動變數的值是 zh-CN， **Import-LocalizedData** 就會將 C:\test\zh-CN 目錄下的 Archives.psd1 檔案匯入到 $Messages 變數中。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-121">If the command is included in the Archives.ps1 script in the C:\Test directory, and the value of the $PsUICulture automatic variable is zh-CN, **Import-LocalizedData** imports the Archives.psd1 file in the C:\test\zh-CN directory into the $Messages variable.</span></span>

### <span data-ttu-id="cf9dd-122">範例 2︰匯入當地語系化資料字串</span><span class="sxs-lookup"><span data-stu-id="cf9dd-122">Example 2: Import localized data strings</span></span>

```
PS C:\> Import-LocalizedData -FileName "Test.psd1" -UICulture "en-US"

Name                           Value
----                           -----
Msg3                           "Use $_ to represent the object that is being processed."
Msg2                           "This command requires the credentials of a member of the Administrators group on the...
Msg1                           "The Name parameter is missing from the command."
```

<span data-ttu-id="cf9dd-123">這個命令是在命令列中執行；不是在指令碼中執行。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-123">This command is run at the command line; not in a script.</span></span>
<span data-ttu-id="cf9dd-124">它會從 Test.psd1 檔案取得當地語系化資料字串，並在命令列中顯示這些字串。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-124">It gets localized data strings from the Test.psd1 file and displays them at the command line.</span></span>
<span data-ttu-id="cf9dd-125">由於此命令不是用於指令碼中，因此必須使用 *FileName* 參數。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-125">Because the command is not used in a script, the *FileName* parameter is required.</span></span>
<span data-ttu-id="cf9dd-126">此命令使用 *UICulture* 參數來指定 en-US 文化特性。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-126">The command uses the *UICulture* parameter to specify the en-US culture.</span></span>

<span data-ttu-id="cf9dd-127">**Import-LocalizedData** 會傳回一個包含當地語系化資料字串的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-127">**Import-LocalizedData** returns a hash table that contains the localized data strings.</span></span>

### <span data-ttu-id="cf9dd-128">範例 3︰匯入 UI 文化特性字串</span><span class="sxs-lookup"><span data-stu-id="cf9dd-128">Example 3: Import UI culture strings</span></span>

```
PS C:\> Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

<span data-ttu-id="cf9dd-129">此命令會將文字字串匯入指令碼的 $MsgTbl 變數中。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-129">This command imports text strings into the $MsgTbl variable of a script.</span></span>

<span data-ttu-id="cf9dd-130">它使用 *UICulture* 參數來指示 Cmdlet 從 C:\Data\Localized 之 ar-SA 子目錄中的 Simple.psd1 檔案匯入資料。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-130">It uses the *UICulture* parameter to direct the cmdlet to import data from the Simple.psd1 file in the ar-SA subdirectory of C:\Data\Localized.</span></span>

### <span data-ttu-id="cf9dd-131">範例 4︰將當地語系化資料匯入指令碼</span><span class="sxs-lookup"><span data-stu-id="cf9dd-131">Example 4: Import localized data into a script</span></span>

```
PS C:\> # In C:\Test\en-US\Test.psd1:

ConvertFrom-StringData @'

# English strings

Msg1 = "The Name parameter is missing from the command."
Msg2 = "This command requires the credentials of a member of the Administrators group on the computer."
Msg3 = "Use $_ to represent the object that is being processed."
'@

# In C:\Test\Test.ps1

Import-LocalizedData -BindingVariable "Messages"
Write-Host $Messages.Msg2

# In PowerShell

PS C:\> .\Test.ps1

This command requires the credentials of a member of the Administrators group on the computer.
```

<span data-ttu-id="cf9dd-132">這個範例示範如何在簡單的指令碼中使用當地語系化資料。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-132">This example shows how to use localized data in a simple script.</span></span>

<span data-ttu-id="cf9dd-133">此範例的第一個部分示範 Test.psd1 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-133">The first part of the example shows the contents of the Test.psd1 file.</span></span>
<span data-ttu-id="cf9dd-134">它包含一個 ConvertFrom-StringData 命令，此命令會將一系列具名的文字字串轉換成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-134">It contains a ConvertFrom-StringData command that converts a series of named text strings into a hash table.</span></span>
<span data-ttu-id="cf9dd-135">Test.psd1 檔案位於包含指令碼之 C:\Test 目錄的 en-US 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-135">The Test.psd1 file is located in the en-US subdirectory of the C:\Test directory that contains the script.</span></span>

<span data-ttu-id="cf9dd-136">此範例的第二個部分示範 Test.ps1 指令碼的內容。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-136">The second part of the example shows the contents of the Test.ps1 script.</span></span>
<span data-ttu-id="cf9dd-137">它包含一個 **Import-LocalizedData** 命令，此命令會將 matching .psd1 檔案中的資料匯入 $Messages 變數中，以及包含一個 Write-Host 命令，此命令會將 $Messages 變數中的其中一個訊息寫入主機程式中。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-137">It contains an **Import-LocalizedData** command that imports the data from the matching .psd1 file into the $Messages variable and a Write-Host command that writes one of the messages in the $Messages variable to the host program.</span></span>

<span data-ttu-id="cf9dd-138">此範例的最後一個部分會執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-138">The last part of the example runs the script.</span></span>
<span data-ttu-id="cf9dd-139">此輸出顯示它使用了為作業系統目前使用者設定的 UI 語言顯示正確的使用者訊息。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-139">The output shows that it displays the correct user message in the UI language set for the current user of the operating system.</span></span>

### <span data-ttu-id="cf9dd-140">範例 5︰取代指令碼中的預設文字字串</span><span class="sxs-lookup"><span data-stu-id="cf9dd-140">Example 5: Replace default text strings in a script</span></span>

```
PS C:\> # In TestScript.ps1
$UserMessages = DATA

{    ConvertFrom-StringData @'

    # English strings

        Msg1 = "Enter a name."
        Msg2 = "Enter your employee ID."
        Msg3 = "Enter your building number."
'@ }
Import-LocalizedData -BindingVariable "UserMessages"
$UserMessages.Msg1...
```

<span data-ttu-id="cf9dd-141">這個範例示範如何使用 **Import-LocalizedData** 來取代指令碼的 DATA 區段中定義的預設文字字串。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-141">This example shows how to use **Import-LocalizedData** to replace default text strings defined in the DATA section of a script.</span></span>

<span data-ttu-id="cf9dd-142">在這個範例中，TestScript.ps1 指令碼的 DATA 區段包含 ConvertFrom-StringData 命令，此命令會將 DATA 區段的內容轉換成雜湊表，並儲存在 $UserMessages 變數的值中。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-142">In this example, the DATA section of the TestScript.ps1 script contains a ConvertFrom-StringData command that converts the contents of the DATA section to a hash table and stores in the value of the $UserMessages variable.</span></span>

<span data-ttu-id="cf9dd-143">此指令碼也包含 **Import-LocalizedData** 命令，此命令會從 $PsUICulture 變數的值所指定之子目錄中的 TestScript.psd1 檔案匯入已翻譯之文字字串的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-143">The script also includes an **Import-LocalizedData** command, which imports a hash table of translated text strings from the TestScript.psd1 file in the subdirectory specified by the value of the $PsUICulture variable.</span></span>
<span data-ttu-id="cf9dd-144">如果此命令找到 .psd1 檔案，它就會將來自檔案的已翻譯字串儲存在相同 $UserMessages 變數的值中，覆寫 DATA 區段邏輯所儲存的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-144">If the command finds the .psd1 file, it saves the translated strings from the file in the value of the same $UserMessages variable, overwriting the hash table saved by the DATA section logic.</span></span>

<span data-ttu-id="cf9dd-145">第三個命令會顯示 $UserMessages 變數中的第一個訊息。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-145">The third command displays the first message in the $UserMessages variable.</span></span>

<span data-ttu-id="cf9dd-146">如果 **Import-LocalizedData** 命令找到 $PsUICulture 語言的 .psd1 檔案，$UserMessages 變數的值便會包含已翻譯的文字字串。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-146">If the **Import-LocalizedData** command finds a .psd1 file for the $PsUICulture language, the value of the $UserMessages variable contains the translated text strings.</span></span>
<span data-ttu-id="cf9dd-147">如果命令因任何原因而失敗，此命令便會顯示指令碼之 DATA 區段中定義的預設文字字串。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-147">If the command fails for any reason, the command displays the default text strings defined in the DATA section of the script.</span></span>

### <span data-ttu-id="cf9dd-148">範例 6︰如果找不到 UI 文化特性就抑制錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="cf9dd-148">Example 6: Suppress error messages if the UI culture is not found</span></span>

```
PS C:\> # In Day1.ps1

Import-LocalizedData -BindingVariable "Day"

# In Day2.ps1

Import-LocalizedData -BindingVariable "Day" -ErrorAction:SilentlyContinue

PS C:\> .\Day1.ps1
Import-LocalizedData : Cannot find PowerShell data file 'Day1.psd1' in directory 'C:\ps-test\fr-BE\' or any parent culture directories.
At C:\ps-test\Day1.ps1:17 char:21+ Import-LocalizedData <<<<  Day
Today is Tuesday PS C:\> .\Day2.ps1
Today is Tuesday
```

<span data-ttu-id="cf9dd-149">這個範例示範如何抑制當 **Import-LocalizedData** 找不到與使用者之 UI 文化特性相符的目錄時所顯示的錯誤訊息，或在這些目錄中找不到指令碼的 .psd1 檔案時所顯示的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-149">This example shows how to suppress the error messages that appear when **Import-LocalizedData** cannot find the directories that match the user's UI culture or cannot find a .psd1 file for the script in those directories.</span></span>

<span data-ttu-id="cf9dd-150">您可以使用 *ErrorAction* 一般參數搭配 SilentlyContinue 值來抑制錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-150">You can use the *ErrorAction* common parameter with a value of SilentlyContinue to suppress the error message.</span></span>
<span data-ttu-id="cf9dd-151">當您已用預設語言或遞補語言提供使用者訊息，而不需要任何錯誤訊息時，這會特別有用。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-151">This is especially useful when you have provided user messages in a default or fallback language, and no error message is needed.</span></span>

<span data-ttu-id="cf9dd-152">這個範例會比較兩個包含 **Import-LocalizedData** 命令的指令碼：Day1.ps1 和 Day2.ps1。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-152">This example compares two scripts, Day1.ps1 and Day2.ps1, that include an **Import-LocalizedData** command.</span></span>
<span data-ttu-id="cf9dd-153">除了 Day2 使用了 *ErrorAction* 一般參數搭配 SilentlyContinue 值之外，這些指令碼完全相同。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-153">The scripts are identical, except that Day2 uses the *ErrorAction* common parameter with a value of SilentlyContinue.</span></span>

<span data-ttu-id="cf9dd-154">此範例輸出顯示當 UI 文化特性設定為 fr-BE 而沒有與此 UI 文化特性相符的檔案或目錄時，這兩個指令碼的執行結果。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-154">The sample output shows the results of running both scripts when the UI culture is set to fr-BE and there are no matching files or directories for that UI culture.</span></span>
<span data-ttu-id="cf9dd-155">Day1.ps1 會顯示錯誤訊息和英文輸出。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-155">Day1.ps1 displays an error message and English output.</span></span>
<span data-ttu-id="cf9dd-156">Day2.ps1 只會顯示英文輸出。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-156">Day2.ps1 just displays the English output.</span></span>

## <span data-ttu-id="cf9dd-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cf9dd-157">PARAMETERS</span></span>

### <span data-ttu-id="cf9dd-158">-BaseDirectory</span><span class="sxs-lookup"><span data-stu-id="cf9dd-158">-BaseDirectory</span></span>

<span data-ttu-id="cf9dd-159">指定 .psd1 檔案所在位置的基礎目錄。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-159">Specifies the base directory where the .psd1 files are located.</span></span>
<span data-ttu-id="cf9dd-160">預設值是指令碼所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-160">The default is the directory where the script is located.</span></span>
<span data-ttu-id="cf9dd-161">**Import-LocalizedData** 會在基礎目錄之語言特定子目錄中搜尋指令碼的 .psd1 檔案。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-161">**Import-LocalizedData** searches for the .psd1 file for the script in a language-specific subdirectory of the base directory.</span></span>

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

### <span data-ttu-id="cf9dd-162">-BindingVariable</span><span class="sxs-lookup"><span data-stu-id="cf9dd-162">-BindingVariable</span></span>

<span data-ttu-id="cf9dd-163">指定做為文字字串匯入位置的變數。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-163">Specifies the variable into which the text strings are imported.</span></span>
<span data-ttu-id="cf9dd-164">請輸入沒有貨幣符號 ($) 的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-164">Enter a variable name without a dollar sign ($).</span></span>

<span data-ttu-id="cf9dd-165">在 Windows PowerShell 2.0 中，這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-165">In Windows PowerShell 2.0, this parameter is required.</span></span>
<span data-ttu-id="cf9dd-166">在 Windows PowerShell 3.0 中，這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-166">In Windows PowerShell 3.0, this parameter is optional.</span></span>
<span data-ttu-id="cf9dd-167">如果省略這個參數， **Import-LocalizedData** 就會傳回文字字串的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-167">If you omit this parameter, **Import-LocalizedData** returns a hash table of the text strings.</span></span>
<span data-ttu-id="cf9dd-168">雜湊表會沿著管線向下傳遞或在命令列中顯示。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-168">The hash table is passed down the pipeline or displayed at the command line.</span></span>

<span data-ttu-id="cf9dd-169">使用 **Import-LocalizedData** 來取代指令碼的 DATA 區段中指定的預設文字字串時，請將 DATA 區段指派給變數，並在 *BindingVariable* 參數的值中輸入 DATA 區段變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-169">When using **Import-LocalizedData** to replace default text strings specified in the DATA section of a script, assign the DATA section to a variable and enter the name of the DATA section variable in the value of the *BindingVariable* parameter.</span></span>
<span data-ttu-id="cf9dd-170">然後，當 **Import-LocalizedData** 將匯入的內容儲存在 *BindingVariable* 中時，匯入的資料就會取代預設文字字串。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-170">Then, when **Import-LocalizedData** saves the imported content in the *BindingVariable* , the imported data will replace the default text strings.</span></span>
<span data-ttu-id="cf9dd-171">如果您未指定預設的文字字串，則可選取任何變數名稱。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-171">If you are not specifying default text strings, you can select any variable name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Variable

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cf9dd-172">-FileName</span><span class="sxs-lookup"><span data-stu-id="cf9dd-172">-FileName</span></span>

<span data-ttu-id="cf9dd-173">指定要匯入之資料檔 (.psd1) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-173">Specifies the name of the data file (.psd1) to be imported.</span></span>
<span data-ttu-id="cf9dd-174">請輸入檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-174">Enter a file name.</span></span>
<span data-ttu-id="cf9dd-175">您可以指定不包含 .psd1 副檔名的檔案名稱，也可以指定包含 .psd1 副檔名的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-175">You can specify a file name that does not include its .psd1 file name extension, or you can specify the file name including the .psd1 file name extension.</span></span>

<span data-ttu-id="cf9dd-176">指令碼中未使用 *Import-LocalizedData* 時，必須使用 **FileName** 參數。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-176">The *FileName* parameter is required when **Import-LocalizedData** is not used in a script.</span></span>
<span data-ttu-id="cf9dd-177">否則，這個參數為選用參數，而預設值為指令碼的主檔名。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-177">Otherwise, the parameter is optional and the default value is the base name of the script.</span></span>
<span data-ttu-id="cf9dd-178">您可以使用這個參數來指示 **Import-LocalizedData** 搜尋不同的 .psd1 檔案。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-178">You can use this parameter to direct **Import-LocalizedData** to search for a different .psd1 file.</span></span>

<span data-ttu-id="cf9dd-179">例如，如果省略 *FileName* ，而指令碼名稱為 FindFiles.ps1， **Import-LocalizedData** 便會搜尋 FindFiles.psd1 資料檔。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-179">For example, if the *FileName* is omitted and the script name is FindFiles.ps1, **Import-LocalizedData** searches for the FindFiles.psd1 data file.</span></span>

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

### <span data-ttu-id="cf9dd-180">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="cf9dd-180">-SupportedCommand</span></span>

<span data-ttu-id="cf9dd-181">指定只產生資料的 Cmdlet 和函式。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-181">Specifies cmdlets and functions that generate only data.</span></span>

<span data-ttu-id="cf9dd-182">請使用這個參數來包含您已經撰寫或測試的 Cmdlet 和函式。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-182">Use this parameter to include cmdlets and functions that you have written or tested.</span></span>
<span data-ttu-id="cf9dd-183">如需詳細資訊，請參閱 about_Script_Internationalization。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-183">For more information, see about_Script_Internationalization.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cf9dd-184">-UICulture</span><span class="sxs-lookup"><span data-stu-id="cf9dd-184">-UICulture</span></span>

<span data-ttu-id="cf9dd-185">指定替代的 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-185">Specifies an alternate UI culture.</span></span>
<span data-ttu-id="cf9dd-186">預設為 $PsUICulture 自動變數的值。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-186">The default is the value of the $PsUICulture automatic variable.</span></span>
<span data-ttu-id="cf9dd-187">輸入格式的 UI 文化特性 \<language\> - \<region\> ，例如 en-us、de 或 ar-SA。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-187">Enter a UI culture in \<language\>-\<region\> format, such as en-US, de-DE, or ar-SA.</span></span>

<span data-ttu-id="cf9dd-188">*UICulture* 參數的值會決定供 **Import-LocalizedData** 取得指令碼之 .psd1 檔案的語言特定子目錄 (在基底目錄內)。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-188">The value of the *UICulture* parameter determines the language-specific subdirectory (within the base directory) from which **Import-LocalizedData** gets the .psd1 file for the script.</span></span>

<span data-ttu-id="cf9dd-189">這個 Cmdlet 會搜尋名稱與 *UICulture* 參數或 $PsUICulture 自動變數的值 (例如 de-DE 或 ar-SA) 相同的子目錄。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-189">The cmdlet searches for a subdirectory with the same name as the value of the *UICulture* parameter or the $PsUICulture automatic variable, such as de-DE or ar-SA.</span></span>
<span data-ttu-id="cf9dd-190">如果找不到目錄，或目錄未包含指令碼的 .psd1 檔案，它就會搜尋具有語言代碼之名稱 (例如 de 或 ar) 的子目錄。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-190">If it cannot find the directory, or the directory does not contain a .psd1 file for the script, it searches for a subdirectory with the name of the language code, such as de or ar.</span></span>
<span data-ttu-id="cf9dd-191">如果找不到子目錄或 .psd1 檔案，則命令會失敗，資料會以指令碼中指定的預設語言顯示。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-191">If it cannot find the subdirectory or .psd1 file, the command fails and the data is displayed in the default language specified in the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cf9dd-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cf9dd-192">CommonParameters</span></span>

<span data-ttu-id="cf9dd-193">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cf9dd-194">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cf9dd-195">輸入</span><span class="sxs-lookup"><span data-stu-id="cf9dd-195">INPUTS</span></span>

### <span data-ttu-id="cf9dd-196">無</span><span class="sxs-lookup"><span data-stu-id="cf9dd-196">None</span></span>

<span data-ttu-id="cf9dd-197">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-197">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="cf9dd-198">輸出</span><span class="sxs-lookup"><span data-stu-id="cf9dd-198">OUTPUTS</span></span>

### <span data-ttu-id="cf9dd-199">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="cf9dd-199">System.Collections.Hashtable</span></span>

<span data-ttu-id="cf9dd-200">**Import-LocalizedData** 會將雜湊表儲存在 **BindingVariable** 參數的值所指定的變數中。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-200">**Import-LocalizedData** saves the hash table in the variable that is specified by the value of the **BindingVariable** parameter.</span></span>

## <span data-ttu-id="cf9dd-201">注意</span><span class="sxs-lookup"><span data-stu-id="cf9dd-201">NOTES</span></span>

* <span data-ttu-id="cf9dd-202">使用 **Import-LocalizedData** 之前，請先將您的使用者訊息翻譯成當地語言。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-202">Before using **Import-LocalizedData** , localize your user messages.</span></span> <span data-ttu-id="cf9dd-203">在機碼/值組的雜湊表中，將每個地區設定 (UI 文化特性) 的訊息格式化，並將此雜湊表儲存在與指令碼同名且副檔名為 .psd1 的檔案中。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-203">Format the messages for each locale (UI culture) in a hash table of key/value pairs, and save the hash table in a file with the same name as the script and a .psd1 file name extension.</span></span> <span data-ttu-id="cf9dd-204">在指令碼目錄下為每個支援的 UI 文化特性建立一個目錄，然後將每個 UI 文化特性的.psd1 檔案以 UI 文化特性名稱儲存在目錄中。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-204">Create a directory under the script directory for each supported UI culture, and then save the .psd1 file for each UI culture in the directory with the UI culture name.</span></span>

  <span data-ttu-id="cf9dd-205">例如，將您的使用者訊息針對 de-DE 地區設定翻譯成當地語言，然後在雜湊表中格式化。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-205">For example, localize your user messages for the de-DE locale and format them in a hash table.</span></span>
<span data-ttu-id="cf9dd-206">將雜湊表儲存在 \<ScriptName\>.psd1 檔案中。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-206">Save the hash table in a \<ScriptName\>.psd1 file.</span></span>
<span data-ttu-id="cf9dd-207">接著，在指令碼目錄下建立 de-DE 子目錄，然後將 de-DE \<ScriptName\>.psd1 檔案儲存在 de-DE 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-207">Then create a de-DE subdirectory under the script directory, and save the de-DE \<ScriptName\>.psd1 file in the de-DE subdirectory.</span></span>
<span data-ttu-id="cf9dd-208">針對您支援的每個地區設定重複使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-208">Repeat this method for each locale that you support.</span></span>

* <span data-ttu-id="cf9dd-209">**Import-LocalizedData** 會執行指令碼之當地語系化使用者訊息的結構化搜尋。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-209">**Import-LocalizedData** performs a structured search for the localized user messages for a script.</span></span>

  <span data-ttu-id="cf9dd-210">**Import-LocalizedData** 會在指令檔所在的目錄 (或 *BaseDirectory* 參數的值) 中開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-210">**Import-LocalizedData** begins the search in the directory where the script file is located (or the value of the *BaseDirectory* parameter).</span></span>
<span data-ttu-id="cf9dd-211">然後，它會在基礎目錄內搜尋名稱與 $PsUICulture 變數的值 (或 *UICulture* 參數的值) (例如 de-DE 或 ar-SA) 相同的子目錄。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-211">It then searches within the base directory for a subdirectory with the same name as the value of the $PsUICulture variable (or the value of the *UICulture* parameter), such as de-DE or ar-SA.</span></span>
<span data-ttu-id="cf9dd-212">接著，它會在該子目錄中搜尋名稱與指令碼 (或 *FileName* 參數的值) 相同的 .psd1 檔案。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-212">Then, it searches in that subdirectory for a .psd1 file with the same name as the script (or the value of the *FileName* parameter).</span></span>

  <span data-ttu-id="cf9dd-213">如果 **Import-LocalizedData** 找不到具有 UI 文化特性名稱的子目錄，或子目錄未包含指令碼的 .psd1 檔案，它就會在具有語言代碼名稱 (例如 de 或 ar) 的子目錄中搜尋指令碼的 .psd1 檔案。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-213">If **Import-LocalizedData** cannot find a subdirectory with the name of the UI culture, or the subdirectory does not contain a .psd1 file for the script, it searches for a .psd1 file for the script in a subdirectory with the name of the language code, such as de or ar.</span></span>
<span data-ttu-id="cf9dd-214">如果找不到子目錄或 .psd1 檔案，則命令會失敗，資料會以指令碼中的預設語言顯示，並且會顯示一則錯誤訊息，說明無法匯入資料。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-214">If it cannot find the subdirectory or .psd1 file, the command fails, the data is displayed in the default language in the script, and an error message is displayed explaining that the data could not be imported.</span></span>
<span data-ttu-id="cf9dd-215">若要抑制訊息並執行正常失敗程序，請使用 *ErrorAction* 一般參數搭配 SilentlyContinue 值。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-215">To suppress the message and fail gracefully, use the *ErrorAction* common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="cf9dd-216">如果 **Import-LocalizedData** 找到子目錄和 .psd1 檔案，它就會將使用者訊息的雜湊表匯入到命令中 *BindingVariable* 參數的值中。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-216">If **Import-LocalizedData** finds the subdirectory and the .psd1 file, it imports the hash table of user messages into the value of the *BindingVariable* parameter in the command.</span></span>
<span data-ttu-id="cf9dd-217">然後，當您從變數中的雜湊表顯示訊息時，就會顯示已翻譯成當地語言的訊息。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-217">Then, when you display a message from the hash table in the variable, the localized message is displayed.</span></span>

  <span data-ttu-id="cf9dd-218">如需詳細資訊，請參閱 [about_Script_Internationalization](../Microsoft.PowerShell.Core/about/about_Script_Internationalization.md)。</span><span class="sxs-lookup"><span data-stu-id="cf9dd-218">For more information, see [about_Script_Internationalization](../Microsoft.PowerShell.Core/about/about_Script_Internationalization.md).</span></span>

## <span data-ttu-id="cf9dd-219">相關連結</span><span class="sxs-lookup"><span data-stu-id="cf9dd-219">RELATED LINKS</span></span>

[<span data-ttu-id="cf9dd-220">Write-Host</span><span class="sxs-lookup"><span data-stu-id="cf9dd-220">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="cf9dd-221">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="cf9dd-221">Import-PowerShellDataFile</span></span>](Import-PowerShellDataFile.md)
