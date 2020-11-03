---
description: 描述腳本國際化功能，可讓腳本輕鬆地在使用者介面中顯示使用者介面的訊息和指示 (UI) 語言。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_internationalization?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Internationalization
ms.openlocfilehash: 51772eeb7517b5c61d9bc7a4333642684de6c37e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207555"
---
# <a name="about-script-internationalization"></a><span data-ttu-id="cf1c3-104">關於腳本國際化</span><span class="sxs-lookup"><span data-stu-id="cf1c3-104">About Script Internationalization</span></span>

## <a name="short-description"></a><span data-ttu-id="cf1c3-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="cf1c3-105">Short Description</span></span>
<span data-ttu-id="cf1c3-106">描述腳本國際化功能，可讓腳本輕鬆地在使用者介面中顯示使用者介面的訊息和指示 (UI) 語言。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-106">Describes the script internationalization features that make it easy for scripts to display messages and instructions to users in their user interface (UI) language.</span></span>

## <a name="long-description"></a><span data-ttu-id="cf1c3-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="cf1c3-107">Long Description</span></span>

<span data-ttu-id="cf1c3-108">PowerShell script 國際化功能可讓您以使用者的語言顯示說明和使用者訊息，更有效地提供全球各地的使用者。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-108">The PowerShell script internationalization features allow you to better serve users throughout the world by displaying help and user messages in the user's language.</span></span>

<span data-ttu-id="cf1c3-109">腳本國際化功能可在執行期間查詢作業系統的 UI 文化特性，匯入適當的已翻譯文字字串，並將其顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-109">The script internationalization features query the UI culture of the operating system during execution, import the appropriate translated text strings, and display them to the user.</span></span> <span data-ttu-id="cf1c3-110">Data 區段可讓您將文字字串與程式碼分開儲存，以便輕鬆地識別和解壓縮文字字串。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-110">The Data section lets you store text strings separate from code so they are easily identified and extracted.</span></span> <span data-ttu-id="cf1c3-111">新的 Cmdlet 會 `ConvertFrom-StringData` 將文字字串轉換成類似字典的雜湊表，以加速轉譯。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-111">A new cmdlet, `ConvertFrom-StringData`, converts text strings into dictionary-like hash tables to facilitate translation.</span></span>

<span data-ttu-id="cf1c3-112">為了支援國際化的解說文字，PowerShell 包含下列功能：</span><span class="sxs-lookup"><span data-stu-id="cf1c3-112">To support international Help text, PowerShell includes the following features:</span></span>

- <span data-ttu-id="cf1c3-113">分隔文字字串與程式碼指令的資料區段。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-113">A Data section that separates text strings from code instructions.</span></span> <span data-ttu-id="cf1c3-114">如需有關 [資料] 區段的詳細資訊，請參閱 [about_Data_Sections](about_Data_Sections.md)。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-114">For more information about the Data section, see [about_Data_Sections](about_Data_Sections.md).</span></span>

- <span data-ttu-id="cf1c3-115">新的自動變數 `$PSCulture` 和 `$PSUICulture` 。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-115">New automatic variables, `$PSCulture` and `$PSUICulture`.</span></span> <span data-ttu-id="cf1c3-116">`$PSCulture` 儲存用於系統上的 UI 語言名稱，以用於專案，例如日期、時間和貨幣。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-116">`$PSCulture` stores the name of the UI language used on the system for elements such as the date, time, and currency.</span></span> <span data-ttu-id="cf1c3-117">`$PSUICulture`變數會儲存系統上用於使用者介面元素（例如功能表和文字字串）之 UI 語言的名稱。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-117">The `$PSUICulture` variable stores the name of the UI language used on the system for user interface elements such as menus and text strings.</span></span>

- <span data-ttu-id="cf1c3-118">Cmdlet， `ConvertFrom-StringData` 它會將文字字串轉換成類似字典的雜湊表，以促進轉譯。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-118">A cmdlet, `ConvertFrom-StringData`, that converts text strings into dictionary-like hash tables to facilitate translation.</span></span> <span data-ttu-id="cf1c3-119">如需詳細資訊，請參閱 [convertfrom-string-至 convertfrom-stringdata](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-119">For more information, see [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData).</span></span>

- <span data-ttu-id="cf1c3-120">新的檔案類型， `.psd1` 儲存已翻譯的文字字串。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-120">A new file type, `.psd1`, that stores translated text strings.</span></span> <span data-ttu-id="cf1c3-121">這些檔案 `.psd1` 會儲存在腳本目錄的特定語言子目錄中。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-121">The `.psd1` files are stored in language-specific subdirectories of the script directory.</span></span>

- <span data-ttu-id="cf1c3-122">Cmdlet， `Import-LocalizedData` 它會在執行時間將指定語言的已翻譯文字字串匯入腳本中。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-122">A cmdlet, `Import-LocalizedData`, that imports translated text strings for a specified language into a script at runtime.</span></span> <span data-ttu-id="cf1c3-123">此 Cmdlet 會以任何支援 Windows 的語言辨識和匯入字串。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-123">This cmdlet recognizes and imports strings in any Windows-supported language.</span></span> <span data-ttu-id="cf1c3-124">如需詳細資訊，請參閱 [>import-localizeddata](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-124">For more information see [Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData).</span></span>

### <a name="the-data-section-storing-default-strings"></a><span data-ttu-id="cf1c3-125">Data 區段：儲存預設字串</span><span class="sxs-lookup"><span data-stu-id="cf1c3-125">The Data Section: Storing Default Strings</span></span>

<span data-ttu-id="cf1c3-126">使用腳本中的資料區段，以預設語言儲存文字字串。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-126">Use a Data section in the script to store the text strings in the default language.</span></span> <span data-ttu-id="cf1c3-127">將字串中的索引鍵/值組中的字串排列。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-127">Arrange the strings in key/value pairs in a here-string.</span></span> <span data-ttu-id="cf1c3-128">每個索引鍵/值組都必須位於不同的行。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-128">Each key/value pair must be on a separate line.</span></span> <span data-ttu-id="cf1c3-129">如果您包含批註，批註必須位於不同的行。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-129">If you include comments, the comments must be on separate lines.</span></span>

<span data-ttu-id="cf1c3-130">此 `ConvertFrom-StringData` Cmdlet 會將此字串中的索引鍵/值組轉換成類似字典的雜湊表，並儲存在 Data 區段變數的值中。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-130">The `ConvertFrom-StringData` cmdlet converts the key/value pairs in the here-string into a dictionary-like hash table that is stored in the value of the Data section variable.</span></span>

<span data-ttu-id="cf1c3-131">在下列範例中，腳本的 Data 區段 `World.ps1` 包含 English-United 狀態 (en-us) 腳本的提示訊息集。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-131">In the following example, the Data section of the `World.ps1` script includes the English-United States (en-US) set of prompt messages for a script.</span></span> <span data-ttu-id="cf1c3-132">`ConvertFrom-StringData`Cmdlet 會將字串轉換成雜湊表，並將它們儲存在 `$msgtable` 變數中。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-132">The `ConvertFrom-StringData` cmdlet converts the strings into a hash table and stores them in the `$msgtable` variable.</span></span>

```powershell
$msgTable = Data {
    #culture="en-US"
    ConvertFrom-StringData @'
    helloWorld = Hello, World.
    errorMsg1 = You cannot leave the user name field blank.
    promptMsg = Please enter your user name.
'@
}
```

<span data-ttu-id="cf1c3-133">如需有關此字串的詳細資訊，請參閱 [about_Quoting_Rules](about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-133">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

### <a name="psd1-files-storing-translated-strings"></a><span data-ttu-id="cf1c3-134">.PSD1 檔案：儲存轉譯的字串</span><span class="sxs-lookup"><span data-stu-id="cf1c3-134">PSD1 Files: Storing Translated Strings</span></span>

<span data-ttu-id="cf1c3-135">將每個 UI 語言的腳本訊息儲存在與腳本同名的不同文字檔中，並將其命名為 `.psd1` 副檔名。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-135">Save the script messages for each UI language in separate text files with the same name as the script and the `.psd1` file name extension.</span></span> <span data-ttu-id="cf1c3-136">以下列格式，將檔案儲存在腳本目錄中具有文化特性名稱的子目錄：</span><span class="sxs-lookup"><span data-stu-id="cf1c3-136">Store the files in subdirectories of the script directory with names of cultures in the following format:</span></span>

`<language>-<region>`

<span data-ttu-id="cf1c3-137">範例： de/DE、ar-SA 和 zh-Hans</span><span class="sxs-lookup"><span data-stu-id="cf1c3-137">Examples: de-DE, ar-SA, and zh-Hans</span></span>

<span data-ttu-id="cf1c3-138">例如，如果 `World.ps1` 腳本儲存在 `C:\Scripts` 目錄中，您會建立如下的檔案目錄結構：</span><span class="sxs-lookup"><span data-stu-id="cf1c3-138">For example, if the `World.ps1` script is stored in the `C:\Scripts` directory, you would create a file directory structure that resembles the following:</span></span>

```
C:\Scripts
C:\Scripts\World.ps1
C:\Scripts\de-DE\World.psd1
C:\Scripts\ar-SA\World.psd1
C:\Scripts\zh-CN\World.psd1
...
```

<span data-ttu-id="cf1c3-139">`World.psd1`腳本目錄的解除刪除子目錄中的檔案可能包含下列語句：</span><span class="sxs-lookup"><span data-stu-id="cf1c3-139">The `World.psd1` file in the de-DE subdirectory of the script directory might include the following statement:</span></span>

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = Hallo, Welt.
errorMsg1 = Das Feld Benutzername darf nicht leer sein.
promptMsg = Geben Sie Ihren Benutzernamen ein.
'@
```

<span data-ttu-id="cf1c3-140">同樣地， `World.psd1` 腳本目錄的 ar-SA 子目錄中的檔案可能包含下列語句：</span><span class="sxs-lookup"><span data-stu-id="cf1c3-140">Similarly, the `World.psd1` file in the ar-SA subdirectory of the script directory might includes the following statement:</span></span>

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = مرحبًا أيها العالَم
errorMsg1 = لا يمكنك ترك حقل اسم المستخدم فارغًا
promptMsg = يرجى إدخال اسم المستخدم الخاص بك
'@
```

### <a name="import-localizeddata-dynamic-retrieval-of-translated-strings"></a><span data-ttu-id="cf1c3-141">>import-localizeddata：動態抓取翻譯的字串</span><span class="sxs-lookup"><span data-stu-id="cf1c3-141">Import-LocalizedData: Dynamic Retrieval of Translated Strings</span></span>

<span data-ttu-id="cf1c3-142">若要以目前使用者的 UI 語言取出字串，請使用 `Import-LocalizedData` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-142">To retrieve the strings in the UI language of the current user, use the `Import-LocalizedData` cmdlet.</span></span>

<span data-ttu-id="cf1c3-143">`Import-LocalizedData` 尋找自動變數的值 `$PSUICulture` ，並匯入 `<script-name>.psd1` 符合值之子目錄中的檔案內容 `$PSUICulture` 。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-143">`Import-LocalizedData` finds the value of the `$PSUICulture` automatic variable and imports the content of the `<script-name>.psd1` files in the subdirectory that matches the `$PSUICulture` value.</span></span> <span data-ttu-id="cf1c3-144">然後，它會將匯入的內容儲存在 **BindingVariable** 參數值所指定的變數中。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-144">Then, it saves the imported content in the variable specified by the value of the **BindingVariable** parameter.</span></span>

```powershell
Import-LocalizedData -BindingVariable msgTable
```

<span data-ttu-id="cf1c3-145">例如，如果 `Import-LocalizedData` 命令出現在腳本中， `C:\Scripts\World.ps1` 且值 `$PSUICulture` 為 "ar-SA"，則會 `Import-LocalizedData` 尋找下列檔案：</span><span class="sxs-lookup"><span data-stu-id="cf1c3-145">For example, if the `Import-LocalizedData` command appears in the `C:\Scripts\World.ps1` script and the value of `$PSUICulture` is "ar-SA", `Import-LocalizedData` finds the following file:</span></span>

`C:\Scripts\ar-SA\World.psd1`

<span data-ttu-id="cf1c3-146">然後，它會將檔案中的阿拉伯文文字字串匯入到 `$msgTable` 變數中，取代任何可能在腳本的 Data 區段中定義的預設字串 `World.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-146">Then, it imports the Arabic text strings from the file into the `$msgTable` variable, replacing any default strings that might be defined in the Data section of the `World.ps1` script.</span></span>

<span data-ttu-id="cf1c3-147">因此，當腳本使用 `$msgTable` 變數來顯示使用者訊息時，訊息會以阿拉伯文顯示。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-147">As a result, when the script uses the `$msgTable` variable to display user messages, the messages are displayed in Arabic.</span></span>

<span data-ttu-id="cf1c3-148">例如，下列腳本會以阿拉伯文顯示「請輸入您的使用者名稱」訊息：</span><span class="sxs-lookup"><span data-stu-id="cf1c3-148">For example, the following script displays the "Please enter your user name" message in Arabic:</span></span>

```powershell
if (!($username)) { $msgTable.promptMsg }
```

<span data-ttu-id="cf1c3-149">如果找 `Import-LocalizedData` 不到 `.psd1` 符合值的檔案，則 `$PSUIculture` `$msgTable` 不會取代的值，而且會呼叫來顯示回復 `$msgTable.promptMsg` 的 en-us 字串。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-149">If `Import-LocalizedData` cannot find a `.psd1` file that matches the value of `$PSUIculture`, the value of `$msgTable` is not replaced, and the call to `$msgTable.promptMsg` displays the fallback en-US strings.</span></span>

## <a name="examples"></a><span data-ttu-id="cf1c3-150">範例</span><span class="sxs-lookup"><span data-stu-id="cf1c3-150">Examples</span></span>

<span data-ttu-id="cf1c3-151">這個範例示範如何在腳本中使用腳本國際化功能，以電腦上所設定的語言顯示一周的某一天。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-151">This example shows how the script internationalization features are used in a script to display a day of the week to users in the language that is set on the computer.</span></span>

<span data-ttu-id="cf1c3-152">以下是 Sample1.ps1 腳本檔案的完整清單。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-152">The following is a complete listing of the Sample1.ps1 script file.</span></span>

<span data-ttu-id="cf1c3-153">腳本一開始會有一個名為 Day ($Day) 包含命令的資料區段 `ConvertFrom-StringData` 。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-153">The script begins with a Data section named Day ($Day) that contains a `ConvertFrom-StringData` command.</span></span> <span data-ttu-id="cf1c3-154">提交至的運算式 `ConvertFrom-StringData` 是在此字串中，其中包含預設 UI 文化特性中的日名稱（en-us），其成對的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-154">The expression submitted to `ConvertFrom-StringData` is a here-string that contains the day names in the default UI culture, en-US, in key/value pairs.</span></span> <span data-ttu-id="cf1c3-155">`ConvertFrom-StringData`Cmdlet 會將此字串中的索引鍵/值組轉換成雜湊表，然後將它儲存在變數的值中 `$Day` 。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-155">The `ConvertFrom-StringData` cmdlet converts the key/value pairs in the here-string into a hash table and then saves it in the value of the `$Day` variable.</span></span>

<span data-ttu-id="cf1c3-156">此命令會將檔案的 `Import-LocalizedData` 內容匯入 `.psd1` 到符合自動變數值的目錄中， `$PSUICulture` 然後將它儲存在變數中 `$Day` ，以取代 `$Day` Data 區段中所定義的值。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-156">The `Import-LocalizedData` command imports the contents of the `.psd1` file in the directory that matches the value of the `$PSUICulture` automatic variable and then saves it in the `$Day` variable, replacing the values of `$Day` that are defined in the Data section.</span></span>

<span data-ttu-id="cf1c3-157">其餘的命令會將字串載入至陣列，並加以顯示。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-157">The remaining commands load the strings into an array and display them.</span></span>

```powershell
$Day = Data {
#culture="en-US"
ConvertFrom-StringData -StringData @'
    messageDate = Today is
    d0 = Sunday
    d1 = Monday
    d2 = Tuesday
    d3 = Wednesday
    d4 = Thursday
    d5 = Friday
    d6 = Saturday
'@
}

Import-LocalizedData -BindingVariable Day

#Build an array of weekdays.
$a = $Day.d0, $Day.d1, $Day.d2, $Day.d3, $Day.d4, $Day.d5, $Day.d6

# Get the day of the week as a number (Monday = 1).
# Index into $a to get the name of the day.
# Use string formatting to build a sentence.

"{0} {1}" -f $Day.messageDate, $a[(Get-Date -UFormat %u)] | Out-Host
```

<span data-ttu-id="cf1c3-158">`.psd1`支援腳本的檔案會儲存在腳本目錄的子目錄中，且名稱與 `$PSUICulture` 值相符。</span><span class="sxs-lookup"><span data-stu-id="cf1c3-158">The `.psd1` files that support the script are saved in subdirectories of the script directory with names that match the `$PSUICulture` values.</span></span>

<span data-ttu-id="cf1c3-159">以下是完整的清單 `.\de-DE\sample1.psd1` ：</span><span class="sxs-lookup"><span data-stu-id="cf1c3-159">The following is a complete listing of `.\de-DE\sample1.psd1`:</span></span>

```powershell
# culture="de-DE"
ConvertFrom-StringData @'
    messageDate = Heute ist
    d0 = Sonntag
    d1 = Montag
    d2 = Dienstag
    d3 = Mittwoch
    d4 = Donnerstag
    d5 = Freitag
    d6 = Samstag
'@
```

<span data-ttu-id="cf1c3-160">如此一來，當您在的系統上執行 Sample.ps1 取消刪除時 `$PSUICulture` ，腳本的輸出為：</span><span class="sxs-lookup"><span data-stu-id="cf1c3-160">As a result, when you run Sample.ps1 on a system on which the value of `$PSUICulture` is de-DE, the output of the script is:</span></span>

```Output
Heute ist Freitag
```

## <a name="see-also"></a><span data-ttu-id="cf1c3-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf1c3-161">See also</span></span>

- [<span data-ttu-id="cf1c3-162">about_Data_Sections</span><span class="sxs-lookup"><span data-stu-id="cf1c3-162">about_Data_Sections</span></span>](about_Data_Sections.md)
- [<span data-ttu-id="cf1c3-163">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="cf1c3-163">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="cf1c3-164">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="cf1c3-164">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="cf1c3-165">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="cf1c3-165">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="cf1c3-166">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="cf1c3-166">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
- [<span data-ttu-id="cf1c3-167">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="cf1c3-167">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)
