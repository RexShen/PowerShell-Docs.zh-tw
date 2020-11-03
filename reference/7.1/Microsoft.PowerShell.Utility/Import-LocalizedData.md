---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-localizeddata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-LocalizedData
ms.openlocfilehash: d19279133a42e3aea17f02348e44aec161ba5a23
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239989"
---
# <span data-ttu-id="1787c-103">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="1787c-103">Import-LocalizedData</span></span>

## <span data-ttu-id="1787c-104">概要</span><span class="sxs-lookup"><span data-stu-id="1787c-104">SYNOPSIS</span></span>
<span data-ttu-id="1787c-105">根據為作業系統選取的 UI 文化特性，將語言特定資料匯入指令碼和函式。</span><span class="sxs-lookup"><span data-stu-id="1787c-105">Imports language-specific data into scripts and functions based on the UI culture that is selected for the operating system.</span></span>

## <span data-ttu-id="1787c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1787c-106">SYNTAX</span></span>

```
Import-LocalizedData [[-BindingVariable] <String>] [[-UICulture] <String>] [-BaseDirectory <String>]
 [-FileName <String>] [-SupportedCommand <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="1787c-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1787c-107">DESCRIPTION</span></span>

<span data-ttu-id="1787c-108">此 `Import-LocalizedData` Cmdlet 會從名稱符合為作業系統目前使用者設定之 UI 語言的子目錄，動態抓取字串。</span><span class="sxs-lookup"><span data-stu-id="1787c-108">The `Import-LocalizedData` cmdlet dynamically retrieves strings from a subdirectory whose name matches the UI language set for the current user of the operating system.</span></span> <span data-ttu-id="1787c-109">它是專為讓指令碼以目前使用者選取的 UI 語言顯示使用者訊息而設計。</span><span class="sxs-lookup"><span data-stu-id="1787c-109">It is designed to enable scripts to display user messages in the UI language selected by the current user.</span></span>

<span data-ttu-id="1787c-110">`Import-LocalizedData` 從 `.psd1` 腳本目錄之語言特定子目錄中的檔案匯入資料，並將其儲存在命令中指定的本機變數中。</span><span class="sxs-lookup"><span data-stu-id="1787c-110">`Import-LocalizedData` imports data from `.psd1` files in language-specific subdirectories of the script directory and saves them in a local variable that is specified in the command.</span></span> <span data-ttu-id="1787c-111">此 Cmdlet 會根據自動變數的值來選取子目錄和檔案 `$PSUICulture` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-111">The cmdlet selects the subdirectory and file based on the value of the `$PSUICulture` automatic variable.</span></span> <span data-ttu-id="1787c-112">在指令碼中使用區域變數來顯示使用者訊息時，訊息會以使用者的 UI 語言顯示。</span><span class="sxs-lookup"><span data-stu-id="1787c-112">When you use the local variable in the script to display a user message, the message appears in the user's UI language.</span></span>

<span data-ttu-id="1787c-113">您可以使用的參數 `Import-LocalizedData` 來指定替代的 UI 文化特性、路徑及檔案名、新增支援的命令，以及抑制找不到檔案時所出現的錯誤訊息 `.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-113">You can use the parameters of `Import-LocalizedData` to specify an alternate UI culture, path, and filename, to add supported commands, and to suppress the error message that appears if the `.psd1` files are not found.</span></span>

<span data-ttu-id="1787c-114">此 `Import-LocalizedData` Cmdlet 支援 Windows PowerShell 2.0 中引進的腳本國際化計畫。</span><span class="sxs-lookup"><span data-stu-id="1787c-114">The `Import-LocalizedData` cmdlet supports the script internationalization initiative that was introduced in Windows PowerShell 2.0.</span></span> <span data-ttu-id="1787c-115">這個計畫的目標是要藉由讓指令碼能輕鬆以目前使用者的 UI 語言顯示使用者訊息，為世界各地的使用者提供更好的服務。</span><span class="sxs-lookup"><span data-stu-id="1787c-115">This initiative aims to better serve users worldwide by making it easy for scripts to display user messages in the UI language of the current user.</span></span> <span data-ttu-id="1787c-116">如需有關這項資訊以及檔案格式的詳細資訊 `.psd1` ，請參閱 [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)。</span><span class="sxs-lookup"><span data-stu-id="1787c-116">For more information about this and about the format of the `.psd1` files, see [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span></span>

## <span data-ttu-id="1787c-117">範例</span><span class="sxs-lookup"><span data-stu-id="1787c-117">EXAMPLES</span></span>

### <span data-ttu-id="1787c-118">範例 1︰匯入文字字串</span><span class="sxs-lookup"><span data-stu-id="1787c-118">Example 1: Import text strings</span></span>

<span data-ttu-id="1787c-119">此範例會將文字字串匯入到 `$Messages` 變數中。</span><span class="sxs-lookup"><span data-stu-id="1787c-119">This example imports text strings into the `$Messages` variable.</span></span> <span data-ttu-id="1787c-120">它會使用所有其他 Cmdlet 參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="1787c-120">It uses the default values of all other cmdlet parameters.</span></span>

```powershell
Import-LocalizedData -BindingVariable "Messages"
```

<span data-ttu-id="1787c-121">如果命令包含在目錄中的 Archives.ps1 腳本中 `C:\Test` ，且 `$PsUICulture` 自動變數的值為 ZH-CN，則會將目錄中的檔案匯 `Import-LocalizedData` 入 `Archives.psd1` `C:\test\zh-CN` 到變數中 `$Messages` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-121">If the command is included in the Archives.ps1 script in the `C:\Test` directory, and the value of the `$PsUICulture` automatic variable is zh-CN, `Import-LocalizedData` imports the `Archives.psd1` file in the `C:\test\zh-CN` directory into the `$Messages` variable.</span></span>

### <span data-ttu-id="1787c-122">範例 2︰匯入當地語系化資料字串</span><span class="sxs-lookup"><span data-stu-id="1787c-122">Example 2: Import localized data strings</span></span>

<span data-ttu-id="1787c-123">此範例會在命令列中執行，而不是在腳本中執行。</span><span class="sxs-lookup"><span data-stu-id="1787c-123">This example is run at the command line not in a script.</span></span> <span data-ttu-id="1787c-124">它會從 Test.psd1 檔案取得當地語系化資料字串，並在命令列中顯示這些字串。</span><span class="sxs-lookup"><span data-stu-id="1787c-124">It gets localized data strings from the Test.psd1 file and displays them at the command line.</span></span> <span data-ttu-id="1787c-125">由於此命令不是用於指令碼中，因此必須使用 **FileName** 參數。</span><span class="sxs-lookup"><span data-stu-id="1787c-125">Because the command is not used in a script, the **FileName** parameter is required.</span></span> <span data-ttu-id="1787c-126">此命令使用 **UICulture** 參數來指定 en-US 文化特性。</span><span class="sxs-lookup"><span data-stu-id="1787c-126">The command uses the **UICulture** parameter to specify the en-US culture.</span></span>

```powershell
Import-LocalizedData -FileName "Test.psd1" -UICulture "en-US"
```

```Output
Name                           Value
----                           -----
Msg3                           "Use $_ to represent the object that is being processed."
Msg2                           "This command requires the credentials of a member of the Administrators group on the...
Msg1                           "The Name parameter is missing from the command."
```

<span data-ttu-id="1787c-127">`Import-LocalizedData` 傳回包含當地語系化資料字串的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="1787c-127">`Import-LocalizedData` returns a hash table that contains the localized data strings.</span></span>

### <span data-ttu-id="1787c-128">範例 3︰匯入 UI 文化特性字串</span><span class="sxs-lookup"><span data-stu-id="1787c-128">Example 3: Import UI culture strings</span></span>

```powershell
Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

<span data-ttu-id="1787c-129">此命令會將文字字串匯入到 `$MsgTbl` 腳本的變數中。</span><span class="sxs-lookup"><span data-stu-id="1787c-129">This command imports text strings into the `$MsgTbl` variable of a script.</span></span>

<span data-ttu-id="1787c-130">它會使用 **UICulture** 參數指示 Cmdlet 從的子目錄中的檔案匯入資料 `Simple.psd1` `ar-SA` `C:\Data\Localized` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-130">It uses the **UICulture** parameter to direct the cmdlet to import data from the `Simple.psd1` file in the `ar-SA` subdirectory of `C:\Data\Localized`.</span></span>

### <span data-ttu-id="1787c-131">範例 4︰將當地語系化資料匯入指令碼</span><span class="sxs-lookup"><span data-stu-id="1787c-131">Example 4: Import localized data into a script</span></span>

<span data-ttu-id="1787c-132">這個範例示範如何在簡單的指令碼中使用當地語系化資料。</span><span class="sxs-lookup"><span data-stu-id="1787c-132">This example shows how to use localized data in a simple script.</span></span>

```powershell
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

# In Windows PowerShell

PS C:\> .\Test.ps1

This command requires the credentials of a member of the Administrators group on the computer.
```

<span data-ttu-id="1787c-133">此範例的第一個部分會顯示檔案的內容 `Test.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-133">The first part of the example shows the contents of the `Test.psd1` file.</span></span> <span data-ttu-id="1787c-134">它包含的 `ConvertFrom-StringData` 命令會將一系列的已命名文字字串轉換成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="1787c-134">It contains a `ConvertFrom-StringData` command that converts a series of named text strings into a hash table.</span></span> <span data-ttu-id="1787c-135">檔案 `Test.psd1` 位於包含腳本之目錄的 en-us 子目錄中 `C:\Test` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-135">The `Test.psd1` file is located in the en-US subdirectory of the `C:\Test` directory that contains the script.</span></span>

<span data-ttu-id="1787c-136">此範例的第二個部分會顯示腳本的內容 `Test.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-136">The second part of the example shows the contents of the `Test.ps1` script.</span></span> <span data-ttu-id="1787c-137">它包含 `Import-LocalizedData` 的命令會將相符檔案中的資料匯入 `.psd1` `$Messages` 變數，以及將 `Write-Host` 變數中的其中一個訊息寫入 `$Messages` 至主機程式的命令。</span><span class="sxs-lookup"><span data-stu-id="1787c-137">It contains an `Import-LocalizedData` command that imports the data from the matching `.psd1` file into the `$Messages` variable and a `Write-Host` command that writes one of the messages in the `$Messages` variable to the host program.</span></span>

<span data-ttu-id="1787c-138">此範例的最後一個部分會執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="1787c-138">The last part of the example runs the script.</span></span> <span data-ttu-id="1787c-139">此輸出顯示它使用了為作業系統目前使用者設定的 UI 語言顯示正確的使用者訊息。</span><span class="sxs-lookup"><span data-stu-id="1787c-139">The output shows that it displays the correct user message in the UI language set for the current user of the operating system.</span></span>

### <span data-ttu-id="1787c-140">範例 5︰取代指令碼中的預設文字字串</span><span class="sxs-lookup"><span data-stu-id="1787c-140">Example 5: Replace default text strings in a script</span></span>

<span data-ttu-id="1787c-141">這個範例示範如何使用 `Import-LocalizedData` 取代腳本的 DATA 區段中定義的預設文字字串。</span><span class="sxs-lookup"><span data-stu-id="1787c-141">This example shows how to use `Import-LocalizedData` to replace default text strings defined in the DATA section of a script.</span></span>

```powershell
PS C:\> # In TestScript.ps1
$UserMessages = DATA

{    ConvertFrom-StringData @'

    # English strings

        Msg1 = "Enter a name."
        Msg2 = "Enter your employee ID."
        Msg3 = "Enter your building number."
'@
}

Import-LocalizedData -BindingVariable "UserMessages"
$UserMessages.Msg1...
```

<span data-ttu-id="1787c-142">在此範例中，TestScript.ps1 腳本的 DATA 區段包含一個 `ConvertFrom-StringData` 命令，此命令會將 DATA 區段的內容轉換成雜湊表，並儲存在變數的值中 `$UserMessages` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-142">In this example, the DATA section of the TestScript.ps1 script contains a `ConvertFrom-StringData` command that converts the contents of the DATA section to a hash table and stores in the value of the `$UserMessages` variable.</span></span>

<span data-ttu-id="1787c-143">此腳本也包含一個 `Import-LocalizedData` 命令，此命令會從變數值所指定之子目錄中的 TestScript.psd1 檔案匯入已翻譯文字字串的雜湊表 `$PsUICulture` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-143">The script also includes an `Import-LocalizedData` command, which imports a hash table of translated text strings from the TestScript.psd1 file in the subdirectory specified by the value of the `$PsUICulture` variable.</span></span> <span data-ttu-id="1787c-144">如果命令找到檔案 `.psd1` ，則會將檔案中的已翻譯字串儲存在相同變數的值中 `$UserMessages` ，並覆寫資料區段邏輯所儲存的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="1787c-144">If the command finds the `.psd1` file, it saves the translated strings from the file in the value of the same `$UserMessages` variable, overwriting the hash table saved by the DATA section logic.</span></span>

<span data-ttu-id="1787c-145">第三個命令會顯示變數中的第一則訊息 `$UserMessages` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-145">The third command displays the first message in the `$UserMessages` variable.</span></span>

<span data-ttu-id="1787c-146">如果 `Import-LocalizedData` 命令找到語言的檔案 `.psd1` ，則 `$PsUICulture` 變數的值會包含已 `$UserMessages` 翻譯的文字字串。</span><span class="sxs-lookup"><span data-stu-id="1787c-146">If the `Import-LocalizedData` command finds a `.psd1` file for the `$PsUICulture` language, the value of the `$UserMessages` variable contains the translated text strings.</span></span> <span data-ttu-id="1787c-147">如果命令因任何原因而失敗，此命令便會顯示指令碼之 DATA 區段中定義的預設文字字串。</span><span class="sxs-lookup"><span data-stu-id="1787c-147">If the command fails for any reason, the command displays the default text strings defined in the DATA section of the script.</span></span>

### <span data-ttu-id="1787c-148">範例 6︰如果找不到 UI 文化特性就抑制錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="1787c-148">Example 6: Suppress error messages if the UI culture is not found</span></span>

<span data-ttu-id="1787c-149">這個範例示範如何抑制當找 `Import-LocalizedData` 不到符合使用者 UI 文化特性的目錄，或 `.psd1` 在這些目錄中找不到腳本的檔案時，所出現的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="1787c-149">This example shows how to suppress the error messages that appear when `Import-LocalizedData` cannot find the directories that match the user's UI culture or cannot find a `.psd1` file for the script in those directories.</span></span>

```powershell
PS C:\> # In Day1.ps1

Import-LocalizedData -BindingVariable "Day"

# In Day2.ps1

Import-LocalizedData -BindingVariable "Day" -ErrorAction:SilentlyContinue

PS C:\> .\Day1.ps1
Import-LocalizedData : Cannot find PowerShell data file 'Day1.psd1' in directory 'C:\ps-test\fr-BE\' or any parent culture directories.
At C:\ps-test\Day1.ps1:17 char:21+ Import-LocalizedData <<<<  Day
Today is Tuesday

PS C:\> .\Day2.ps1
Today is Tuesday
```

<span data-ttu-id="1787c-150">您可以使用 **ErrorAction** 一般參數搭配 SilentlyContinue 值來抑制錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="1787c-150">You can use the **ErrorAction** common parameter with a value of SilentlyContinue to suppress the error message.</span></span> <span data-ttu-id="1787c-151">當您已用預設語言或遞補語言提供使用者訊息，而不需要任何錯誤訊息時，這會特別有用。</span><span class="sxs-lookup"><span data-stu-id="1787c-151">This is especially useful when you have provided user messages in a default or fallback language, and no error message is needed.</span></span>

<span data-ttu-id="1787c-152">此範例會比較兩個腳本， `Day1.ps1` 以及包含命令的 Day2.ps1 `Import-LocalizedData` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-152">This example compares two scripts, `Day1.ps1` and Day2.ps1, that include an `Import-LocalizedData` command.</span></span> <span data-ttu-id="1787c-153">腳本完全相同，不同之處在于 Day2.ps1 會使用 **ErrorAction** 一般參數與值 `SilentlyContinue` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-153">The scripts are identical, except that Day2 uses the **ErrorAction** common parameter with a value of `SilentlyContinue`.</span></span>

<span data-ttu-id="1787c-154">範例輸出會顯示當 UI 文化特性設定為 `fr-BE` ，且該 ui 文化特性沒有相符檔案或目錄時，執行這兩個腳本的結果。</span><span class="sxs-lookup"><span data-stu-id="1787c-154">The sample output shows the results of running both scripts when the UI culture is set to `fr-BE` and there are no matching files or directories for that UI culture.</span></span> <span data-ttu-id="1787c-155">`Day1.ps1` 顯示錯誤訊息和英文輸出。</span><span class="sxs-lookup"><span data-stu-id="1787c-155">`Day1.ps1` displays an error message and English output.</span></span> <span data-ttu-id="1787c-156">`Day2.ps1` 只會顯示英文輸出。</span><span class="sxs-lookup"><span data-stu-id="1787c-156">`Day2.ps1` just displays the English output.</span></span>

## <span data-ttu-id="1787c-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1787c-157">PARAMETERS</span></span>

### <span data-ttu-id="1787c-158">-BaseDirectory</span><span class="sxs-lookup"><span data-stu-id="1787c-158">-BaseDirectory</span></span>

<span data-ttu-id="1787c-159">指定檔案所在的基底目錄 `.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-159">Specifies the base directory where the `.psd1` files are located.</span></span> <span data-ttu-id="1787c-160">預設值是指令碼所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="1787c-160">The default is the directory where the script is located.</span></span> <span data-ttu-id="1787c-161">`Import-LocalizedData``.psd1`在基底目錄的特定語言子目錄中搜尋腳本的檔案。</span><span class="sxs-lookup"><span data-stu-id="1787c-161">`Import-LocalizedData` searches for the `.psd1` file for the script in a language-specific subdirectory of the base directory.</span></span>

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

### <span data-ttu-id="1787c-162">-BindingVariable</span><span class="sxs-lookup"><span data-stu-id="1787c-162">-BindingVariable</span></span>

<span data-ttu-id="1787c-163">指定做為文字字串匯入位置的變數。</span><span class="sxs-lookup"><span data-stu-id="1787c-163">Specifies the variable into which the text strings are imported.</span></span> <span data-ttu-id="1787c-164">輸入不含貨幣正負號 () 的變數名稱 `$` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-164">Enter a variable name without a dollar sign (`$`).</span></span>

<span data-ttu-id="1787c-165">在 Windows PowerShell 2.0 中，這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="1787c-165">In Windows PowerShell 2.0, this parameter is required.</span></span> <span data-ttu-id="1787c-166">在 Windows PowerShell 3.0 中，這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="1787c-166">In Windows PowerShell 3.0, this parameter is optional.</span></span> <span data-ttu-id="1787c-167">如果您省略此參數，則會傳回 `Import-LocalizedData` 文字字串的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="1787c-167">If you omit this parameter, `Import-LocalizedData` returns a hash table of the text strings.</span></span> <span data-ttu-id="1787c-168">雜湊表會沿著管線向下傳遞或在命令列中顯示。</span><span class="sxs-lookup"><span data-stu-id="1787c-168">The hash table is passed down the pipeline or displayed at the command line.</span></span>

<span data-ttu-id="1787c-169">當使用 `Import-LocalizedData` 取代腳本的 data 區段中指定的預設文字字串時，請將 data 區段指派給變數，並在 **BindingVariable** 參數的值中輸入 data 區段變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="1787c-169">When using `Import-LocalizedData` to replace default text strings specified in the DATA section of a script, assign the DATA section to a variable and enter the name of the DATA section variable in the value of the **BindingVariable** parameter.</span></span> <span data-ttu-id="1787c-170">然後，當將匯 `Import-LocalizedData` 入的內容儲存在 **BindingVariable** 中時，匯入的資料就會取代預設文字字串。</span><span class="sxs-lookup"><span data-stu-id="1787c-170">Then, when `Import-LocalizedData` saves the imported content in the **BindingVariable** , the imported data will replace the default text strings.</span></span> <span data-ttu-id="1787c-171">如果您未指定預設的文字字串，則可選取任何變數名稱。</span><span class="sxs-lookup"><span data-stu-id="1787c-171">If you are not specifying default text strings, you can select any variable name.</span></span>

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

### <span data-ttu-id="1787c-172">-FileName</span><span class="sxs-lookup"><span data-stu-id="1787c-172">-FileName</span></span>

<span data-ttu-id="1787c-173">指定要匯入 (資料檔案的名稱 `.psd1)` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-173">Specifies the name of the data file (`.psd1)` to be imported.</span></span> <span data-ttu-id="1787c-174">請輸入檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="1787c-174">Enter a file name.</span></span> <span data-ttu-id="1787c-175">您可以指定不含副檔名的檔案名 `.psd1` ，也可以指定檔案名（包括 `.psd1` 副檔名）。</span><span class="sxs-lookup"><span data-stu-id="1787c-175">You can specify a file name that does not include its `.psd1` file name extension, or you can specify the file name including the `.psd1` file name extension.</span></span> <span data-ttu-id="1787c-176">資料檔案應該儲存為 Unicode 或 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="1787c-176">Data files should be saved as Unicode or UTF-8.</span></span>

<span data-ttu-id="1787c-177">當 **FileName** 未 `Import-LocalizedData` 在腳本中使用時，需要 FileName 參數。</span><span class="sxs-lookup"><span data-stu-id="1787c-177">The **FileName** parameter is required when `Import-LocalizedData` is not used in a script.</span></span>
<span data-ttu-id="1787c-178">否則，這個參數為選用參數，而預設值為指令碼的主檔名。</span><span class="sxs-lookup"><span data-stu-id="1787c-178">Otherwise, the parameter is optional and the default value is the base name of the script.</span></span> <span data-ttu-id="1787c-179">您可以使用這個參數來指示 `Import-LocalizedData` 搜尋不同的檔案 `.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-179">You can use this parameter to direct `Import-LocalizedData` to search for a different `.psd1` file.</span></span>

<span data-ttu-id="1787c-180">例如，如果省略 **檔案名** 且腳本名稱為 FindFiles.ps1，則會 `Import-LocalizedData` 搜尋 FindFiles.psd1 資料檔案。</span><span class="sxs-lookup"><span data-stu-id="1787c-180">For example, if the **FileName** is omitted and the script name is FindFiles.ps1, `Import-LocalizedData` searches for the FindFiles.psd1 data file.</span></span>

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

### <span data-ttu-id="1787c-181">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="1787c-181">-SupportedCommand</span></span>

<span data-ttu-id="1787c-182">指定只產生資料的 Cmdlet 和函式。</span><span class="sxs-lookup"><span data-stu-id="1787c-182">Specifies cmdlets and functions that generate only data.</span></span>

<span data-ttu-id="1787c-183">請使用這個參數來包含您已經撰寫或測試的 Cmdlet 和函式。</span><span class="sxs-lookup"><span data-stu-id="1787c-183">Use this parameter to include cmdlets and functions that you have written or tested.</span></span> <span data-ttu-id="1787c-184">如需詳細資訊，請參閱 [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)。</span><span class="sxs-lookup"><span data-stu-id="1787c-184">For more information, see [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span></span>

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

### <span data-ttu-id="1787c-185">-UICulture</span><span class="sxs-lookup"><span data-stu-id="1787c-185">-UICulture</span></span>

<span data-ttu-id="1787c-186">指定替代的 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="1787c-186">Specifies an alternate UI culture.</span></span>
<span data-ttu-id="1787c-187">預設值是自動變數的值 `$PsUICulture` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-187">The default is the value of the `$PsUICulture` automatic variable.</span></span>
<span data-ttu-id="1787c-188">以格式輸入 UI 文化特性 `<language>-<region>` ，例如 `en-US` 、 `de-DE` 或 `ar-SA` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-188">Enter a UI culture in `<language>-<region>` format, such as `en-US`, `de-DE`, or `ar-SA`.</span></span>

<span data-ttu-id="1787c-189">**UICulture** 參數的值會決定基底目錄中 (特定語言的子目錄，) 從中 `Import-LocalizedData` 取得腳本的檔案 `.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-189">The value of the **UICulture** parameter determines the language-specific subdirectory (within the base directory) from which `Import-LocalizedData` gets the `.psd1` file for the script.</span></span>

<span data-ttu-id="1787c-190">此 Cmdlet 會搜尋與 **UICulture** 參數的值或 `$PsUICulture` 自動變數（例如或）相同名稱的子目錄 `de-DE` `ar-SA` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-190">The cmdlet searches for a subdirectory with the same name as the value of the **UICulture** parameter or the `$PsUICulture` automatic variable, such as `de-DE` or `ar-SA`.</span></span> <span data-ttu-id="1787c-191">如果找不到目錄，或目錄未包含腳本的檔案， `.psd1` 則會使用語言代碼名稱（例如 de 或 ar）來搜尋子目錄。</span><span class="sxs-lookup"><span data-stu-id="1787c-191">If it cannot find the directory, or the directory does not contain a `.psd1` file for the script, it searches for a subdirectory with the name of the language code, such as de or ar.</span></span> <span data-ttu-id="1787c-192">如果找不到子目錄或檔案 `.psd1` ，則命令會失敗，而且資料會以腳本中指定的預設語言顯示。</span><span class="sxs-lookup"><span data-stu-id="1787c-192">If it cannot find the subdirectory or `.psd1` file, the command fails and the data is displayed in the default language specified in the script.</span></span>

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

### <span data-ttu-id="1787c-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1787c-193">CommonParameters</span></span>

<span data-ttu-id="1787c-194">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1787c-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1787c-195">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1787c-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1787c-196">輸入</span><span class="sxs-lookup"><span data-stu-id="1787c-196">INPUTS</span></span>

### <span data-ttu-id="1787c-197">無</span><span class="sxs-lookup"><span data-stu-id="1787c-197">None</span></span>

<span data-ttu-id="1787c-198">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1787c-198">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="1787c-199">輸出</span><span class="sxs-lookup"><span data-stu-id="1787c-199">OUTPUTS</span></span>

### <span data-ttu-id="1787c-200">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="1787c-200">System.Collections.Hashtable</span></span>

<span data-ttu-id="1787c-201">`Import-LocalizedData` 將雜湊表儲存在 **BindingVariable** 參數值所指定的變數中。</span><span class="sxs-lookup"><span data-stu-id="1787c-201">`Import-LocalizedData` saves the hash table in the variable that is specified by the value of the **BindingVariable** parameter.</span></span>

## <span data-ttu-id="1787c-202">注意</span><span class="sxs-lookup"><span data-stu-id="1787c-202">NOTES</span></span>

- <span data-ttu-id="1787c-203">在使用之前 `Import-LocalizedData` ，請將您的使用者訊息當地語系化。</span><span class="sxs-lookup"><span data-stu-id="1787c-203">Before using `Import-LocalizedData`, localize your user messages.</span></span> <span data-ttu-id="1787c-204">在索引鍵/值組的雜湊表中，將每個地區設定 (UI 文化特性) 的訊息格式化，並將雜湊表儲存在與腳本同名的檔案中，並將其命名為 `.psd1` 副檔名。</span><span class="sxs-lookup"><span data-stu-id="1787c-204">Format the messages for each locale (UI culture) in a hash table of key-value pairs, and save the hash table in a file with the same name as the script and a `.psd1` file name extension.</span></span> <span data-ttu-id="1787c-205">在腳本目錄下為每個支援的 UI 文化特性建立一個目錄，然後將 `.psd1` 每個 ui 文化特性的檔案儲存在具有 ui 文化特性名稱的目錄中。</span><span class="sxs-lookup"><span data-stu-id="1787c-205">Create a directory under the script directory for each supported UI culture, and then save the `.psd1` file for each UI culture in the directory with the UI culture name.</span></span>

  <span data-ttu-id="1787c-206">例如，將您的使用者訊息針對 de-DE 地區設定翻譯成當地語言，然後在雜湊表中格式化。</span><span class="sxs-lookup"><span data-stu-id="1787c-206">For example, localize your user messages for the de-DE locale and format them in a hash table.</span></span>
  <span data-ttu-id="1787c-207">將雜湊表儲存在檔案中 `<ScriptName>.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-207">Save the hash table in a `<ScriptName>.psd1` file.</span></span> <span data-ttu-id="1787c-208">然後在 `de-DE` 腳本目錄下建立子目錄，然後將德文檔案儲存 `<ScriptName\>.psd1` 在子目錄中 `de-DE` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-208">Then create a `de-DE` subdirectory under the script directory, and save the German `<ScriptName\>.psd1` file in the `de-DE` subdirectory.</span></span>
  <span data-ttu-id="1787c-209">針對您支援的每個地區設定重複使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="1787c-209">Repeat this method for each locale that you support.</span></span>

- <span data-ttu-id="1787c-210">`Import-LocalizedData` 針對腳本執行當地語系化使用者訊息的結構化搜尋。</span><span class="sxs-lookup"><span data-stu-id="1787c-210">`Import-LocalizedData` performs a structured search for the localized user messages for a script.</span></span>

  <span data-ttu-id="1787c-211">`Import-LocalizedData` 在腳本檔案所在的目錄中開始搜尋 (或 **BaseDirectory** 參數的值) 。</span><span class="sxs-lookup"><span data-stu-id="1787c-211">`Import-LocalizedData` begins the search in the directory where the script file is located (or the value of the **BaseDirectory** parameter).</span></span> <span data-ttu-id="1787c-212">然後，它會在基底目錄中搜尋名稱與 `$PsUICulture` 變數值 (或 **UICulture** 參數值) 的子目錄，例如 `de-DE` 或 `ar-SA` 。</span><span class="sxs-lookup"><span data-stu-id="1787c-212">It then searches within the base directory for a subdirectory with the same name as the value of the `$PsUICulture` variable (or the value of the **UICulture** parameter), such as `de-DE` or `ar-SA`.</span></span> <span data-ttu-id="1787c-213">然後，它會在該子目錄中搜尋 `.psd1` 與腳本 (相同名稱的檔案，或) **FileName** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="1787c-213">Then, it searches in that subdirectory for a `.psd1` file with the same name as the script (or the value of the **FileName** parameter).</span></span>

  <span data-ttu-id="1787c-214">如果找 `Import-LocalizedData` 不到具有 UI 文化特性名稱的子目錄，或子目錄未包含腳本的檔案 `.psd1` ，則會 `.psd1` 在具有語言代碼名稱（例如 de 或 ar）的子目錄中搜尋腳本的檔案。</span><span class="sxs-lookup"><span data-stu-id="1787c-214">If `Import-LocalizedData` cannot find a subdirectory with the name of the UI culture, or the subdirectory does not contain a `.psd1` file for the script, it searches for a `.psd1` file for the script in a subdirectory with the name of the language code, such as de or ar.</span></span> <span data-ttu-id="1787c-215">如果找不到子目錄或檔案 `.psd1` ，則命令會失敗，資料會以腳本中的預設語言顯示，並且會顯示錯誤訊息，說明無法匯入資料。</span><span class="sxs-lookup"><span data-stu-id="1787c-215">If it cannot find the subdirectory or `.psd1` file, the command fails, the data is displayed in the default language in the script, and an error message is displayed explaining that the data could not be imported.</span></span> <span data-ttu-id="1787c-216">若要抑制訊息並執行正常失敗程序，請使用 **ErrorAction** 一般參數搭配 SilentlyContinue 值。</span><span class="sxs-lookup"><span data-stu-id="1787c-216">To suppress the message and fail gracefully, use the **ErrorAction** common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="1787c-217">如果 `Import-LocalizedData` 找到子目錄和檔案 `.psd1` ，它就會將使用者訊息的雜湊表匯入到命令中 **BindingVariable** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="1787c-217">If `Import-LocalizedData` finds the subdirectory and the `.psd1` file, it imports the hash table of user messages into the value of the **BindingVariable** parameter in the command.</span></span> <span data-ttu-id="1787c-218">然後，當您從變數中的雜湊表顯示訊息時，就會顯示已翻譯成當地語言的訊息。</span><span class="sxs-lookup"><span data-stu-id="1787c-218">Then, when you display a message from the hash table in the variable, the localized message is displayed.</span></span>

  <span data-ttu-id="1787c-219">如需詳細資訊，請參閱 [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md)。</span><span class="sxs-lookup"><span data-stu-id="1787c-219">For more information, see [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md).</span></span>

## <span data-ttu-id="1787c-220">相關連結</span><span class="sxs-lookup"><span data-stu-id="1787c-220">RELATED LINKS</span></span>

[<span data-ttu-id="1787c-221">Write-Host</span><span class="sxs-lookup"><span data-stu-id="1787c-221">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="1787c-222">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="1787c-222">Import-PowerShellDataFile</span></span>](Import-PowerShellDataFile.md)

