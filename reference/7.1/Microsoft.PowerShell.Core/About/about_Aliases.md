---
description: 說明如何在 PowerShell 中使用 Cmdlet 和命令的替代名稱。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_aliases?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Aliases
ms.openlocfilehash: e0a1fa357e591dd17986a8dd685a1818751ab355
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208328"
---
# <a name="about-aliases"></a><span data-ttu-id="e14a5-104">關於別名</span><span class="sxs-lookup"><span data-stu-id="e14a5-104">About Aliases</span></span>

## <a name="short-description"></a><span data-ttu-id="e14a5-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="e14a5-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="e14a5-106">說明如何在 PowerShell 中使用 Cmdlet 和命令的替代名稱。</span><span class="sxs-lookup"><span data-stu-id="e14a5-106">Describes how to use alternate names for cmdlets and commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="e14a5-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="e14a5-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e14a5-108">別名是 Cmdlet 或命令元素的替代名稱或昵稱，例如函數、腳本、檔案或可執行檔。</span><span class="sxs-lookup"><span data-stu-id="e14a5-108">An alias is an alternate name or nickname for a cmdlet or for a command element, such as a function, script, file, or executable file.</span></span> <span data-ttu-id="e14a5-109">您可以使用別名來取代任何 PowerShell 命令中的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="e14a5-109">You can use the alias instead of the command name in any PowerShell commands.</span></span>

<span data-ttu-id="e14a5-110">若要建立別名，請使用 New-Alias Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e14a5-110">To create an alias, use the New-Alias cmdlet.</span></span> <span data-ttu-id="e14a5-111">例如，下列命令會建立 Cmdlet 的「天然氣」別名 `Get-AuthenticodeSignature` ：</span><span class="sxs-lookup"><span data-stu-id="e14a5-111">For example, the following command creates the "gas" alias for the `Get-AuthenticodeSignature` cmdlet:</span></span>

```powershell
New-Alias -Name gas -Value Get-AuthenticodeSignature
```

<span data-ttu-id="e14a5-112">建立 Cmdlet 名稱的別名之後，您可以使用別名，而不是 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="e14a5-112">After you create the alias for the cmdlet name, you can use the alias instead of the cmdlet name.</span></span> <span data-ttu-id="e14a5-113">例如，若要取得 SqlScript.ps1 檔案的 Authenticode 簽章，請輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-113">For example, to get the Authenticode signature for the SqlScript.ps1 file, type:</span></span>

```powershell
Get-AuthenticodeSignature SqlScript.ps1
```

<span data-ttu-id="e14a5-114">或者，輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-114">Or, type:</span></span>

```powershell
gas SqlScript.ps1
```

<span data-ttu-id="e14a5-115">如果您建立 "word" 做為 Microsoft Office Word 的別名，您可以輸入 "word" 而非下列內容：</span><span class="sxs-lookup"><span data-stu-id="e14a5-115">If you create "word" as the alias for Microsoft Office Word, you can type "word" instead of the following:</span></span>

```powershell
"C:\Program Files\Microsoft Office\Office11\Winword.exe"
```

## <a name="built-in-aliases"></a><span data-ttu-id="e14a5-116">內建別名</span><span class="sxs-lookup"><span data-stu-id="e14a5-116">BUILT-IN ALIASES</span></span>

<span data-ttu-id="e14a5-117">PowerShell 包含一組內建的別名，包括 Set-Location Cmdlet 的 "cd" 和 "chdir"，以及 Get-ChildItem Cmdlet 的 "ls" 和 "dir"。</span><span class="sxs-lookup"><span data-stu-id="e14a5-117">PowerShell includes a set of built-in aliases, including "cd" and "chdir" for the Set-Location cmdlet, and "ls" and "dir" for the Get-ChildItem cmdlet.</span></span>

<span data-ttu-id="e14a5-118">若要取得電腦上的所有別名（包括內建的別名），請輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-118">To get all the aliases on the computer, including the built-in aliases, type:</span></span>

```powershell
Get-Alias
```

## <a name="alias-cmdlets"></a><span data-ttu-id="e14a5-119">別名 CMDLET</span><span class="sxs-lookup"><span data-stu-id="e14a5-119">ALIAS CMDLETS</span></span>

<span data-ttu-id="e14a5-120">PowerShell 包含下列適用于使用別名的 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="e14a5-120">PowerShell includes the following cmdlets, which are designed for working with aliases:</span></span>

- <span data-ttu-id="e14a5-121">`Get-Alias` -取得目前會話中的所有別名。</span><span class="sxs-lookup"><span data-stu-id="e14a5-121">`Get-Alias` - Gets all the aliases in the current session.</span></span>
- <span data-ttu-id="e14a5-122">`New-Alias` -建立新的別名。</span><span class="sxs-lookup"><span data-stu-id="e14a5-122">`New-Alias` - Creates a new alias.</span></span>
- <span data-ttu-id="e14a5-123">`Set-Alias` -建立或變更別名。</span><span class="sxs-lookup"><span data-stu-id="e14a5-123">`Set-Alias` - Creates or changes an alias.</span></span>
- <span data-ttu-id="e14a5-124">`Export-Alias` -將一或多個別名匯出到檔案。</span><span class="sxs-lookup"><span data-stu-id="e14a5-124">`Export-Alias` - Exports one or more aliases to a file.</span></span>
- <span data-ttu-id="e14a5-125">`Import-Alias` -將別名檔案匯入 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e14a5-125">`Import-Alias` - Imports an alias file into PowerShell.</span></span>

<span data-ttu-id="e14a5-126">如需 Cmdlet 的詳細資訊，請輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-126">For detailed information about the cmdlets, type:</span></span>

```powershell
Get-Help <cmdlet-Name> -Detailed
```

<span data-ttu-id="e14a5-127">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-127">For example, type:</span></span>

```powershell
Get-Help Export-Alias -Detailed
```

## <a name="creating-an-alias"></a><span data-ttu-id="e14a5-128">建立別名</span><span class="sxs-lookup"><span data-stu-id="e14a5-128">CREATING AN ALIAS</span></span>

<span data-ttu-id="e14a5-129">若要建立新的別名，請使用 New-Alias Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e14a5-129">To create a new alias, use the New-Alias cmdlet.</span></span> <span data-ttu-id="e14a5-130">例如，若要建立 Get-help 的 "gh" 別名，請輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-130">For example, to create the "gh" alias for Get-Help, type:</span></span>

```powershell
New-Alias -Name gh -Value Get-Help
```

<span data-ttu-id="e14a5-131">您可以使用命令中的別名，就像使用完整 Cmdlet 名稱一樣，您也可以使用別名搭配參數。</span><span class="sxs-lookup"><span data-stu-id="e14a5-131">You can use the alias in commands, just as you would use the full cmdlet name, and you can use the alias with parameters.</span></span>

<span data-ttu-id="e14a5-132">例如，若要取得 Get-WmiObject Cmdlet 的詳細說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-132">For example, to get detailed Help for the Get-WmiObject cmdlet, type:</span></span>

```powershell
Get-Help Get-WmiObject -Detailed
```

<span data-ttu-id="e14a5-133">或者，輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-133">Or, type:</span></span>

```powershell
gh Get-WmiObject -Detailed
```

## <a name="saving-aliases"></a><span data-ttu-id="e14a5-134">正在儲存別名</span><span class="sxs-lookup"><span data-stu-id="e14a5-134">SAVING ALIASES</span></span>

<span data-ttu-id="e14a5-135">您建立的別名只會儲存在目前的會話中。</span><span class="sxs-lookup"><span data-stu-id="e14a5-135">The aliases that you create are saved only in the current session.</span></span> <span data-ttu-id="e14a5-136">若要在不同的會話中使用別名，請將別名新增至 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="e14a5-136">To use the aliases in a different session, add the alias to your PowerShell profile.</span></span> <span data-ttu-id="e14a5-137">或者，使用 Export-Alias Cmdlet 將別名儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="e14a5-137">Or, use the Export-Alias cmdlet to save the aliases to a file.</span></span>

<span data-ttu-id="e14a5-138">如需詳細資訊，請鍵入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-138">For more information, type:</span></span>

```powershell
Get-Help about_Profiles
```

## <a name="getting-aliases"></a><span data-ttu-id="e14a5-139">取得別名</span><span class="sxs-lookup"><span data-stu-id="e14a5-139">GETTING ALIASES</span></span>

<span data-ttu-id="e14a5-140">若要取得目前會話中的所有別名，包括內建的別名、您 PowerShell 設定檔中的別名，以及您在目前會話中建立的別名，請輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-140">To get all the aliases in the current session, including the built-in aliases, the aliases in your PowerShell profiles, and the aliases that you have created in the current session, type:</span></span>

```powershell
Get-Alias
```

<span data-ttu-id="e14a5-141">若要取得特定別名，請使用 Get-Alias Cmdlet 的 Name 參數。</span><span class="sxs-lookup"><span data-stu-id="e14a5-141">To get particular aliases, use the Name parameter of the Get-Alias cmdlet.</span></span> <span data-ttu-id="e14a5-142">例如，若要取得以 "p" 開頭的別名，請輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-142">For example, to get aliases that begin with "p", type:</span></span>

```powershell
Get-Alias -Name p*
```

<span data-ttu-id="e14a5-143">若要取得特定專案的別名，請使用定義參數。</span><span class="sxs-lookup"><span data-stu-id="e14a5-143">To get the aliases for a particular item, use the Definition parameter.</span></span> <span data-ttu-id="e14a5-144">例如，若要取得 Get-ChildItem Cmdlet 類型的別名：</span><span class="sxs-lookup"><span data-stu-id="e14a5-144">For example, to get the aliases for the Get-ChildItem cmdlet type:</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

### <a name="get-alias-output"></a><span data-ttu-id="e14a5-145">取得別名輸出</span><span class="sxs-lookup"><span data-stu-id="e14a5-145">GET-ALIAS OUTPUT</span></span>

<span data-ttu-id="e14a5-146">Get-Alias 只會傳回一種類型的物件，也就是 System.management.automation.aliasinfo 物件 (System.management.automation.aliasinfo) 。</span><span class="sxs-lookup"><span data-stu-id="e14a5-146">Get-Alias returns only one type of object, an AliasInfo object (System.Management.Automation.AliasInfo).</span></span> <span data-ttu-id="e14a5-147">不含連字號的別名名稱（例如 "cd"）會以下列格式顯示：</span><span class="sxs-lookup"><span data-stu-id="e14a5-147">The name of aliases that don't include a hyphen, such as "cd" are displayed in the following format:</span></span>

```powershell
Get-Alias ac
```

```Output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Alias           ac -> Add-Content
```

<span data-ttu-id="e14a5-148">這可讓您快速且輕鬆地取得所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="e14a5-148">This makes it very quick and easy to get the information that you need.</span></span>

<span data-ttu-id="e14a5-149">箭號型別名名稱格式不會用於含連字號的別名。</span><span class="sxs-lookup"><span data-stu-id="e14a5-149">The arrow-based alias name format is not used for aliases that include a hyphen.</span></span> <span data-ttu-id="e14a5-150">這些可能是 Cmdlet 和函式的慣用替代名稱，而不是一般的縮寫或昵稱，而且作者可能不會想要它們都能顯而易見。</span><span class="sxs-lookup"><span data-stu-id="e14a5-150">These are likely to be preferred substitute names for cmdlets and functions, instead of typical abbreviations or nicknames, and the author might not want them to be as evident.</span></span>

## <a name="alternate-names-for-commands-with-parameters"></a><span data-ttu-id="e14a5-151">具有參數之命令的替代名稱</span><span class="sxs-lookup"><span data-stu-id="e14a5-151">ALTERNATE NAMES FOR COMMANDS WITH PARAMETERS</span></span>

<span data-ttu-id="e14a5-152">您可以將別名指派給 Cmdlet、腳本、函式或可執行檔。</span><span class="sxs-lookup"><span data-stu-id="e14a5-152">You can assign an alias to a cmdlet, script, function, or executable file.</span></span> <span data-ttu-id="e14a5-153">您無法將別名指派給命令及其參數。</span><span class="sxs-lookup"><span data-stu-id="e14a5-153">You cannot assign an alias to a command and its parameters.</span></span> <span data-ttu-id="e14a5-154">例如，您可以將別名指派給 `Get-Eventlog` Cmdlet，但是不能將別名指派給 `Get-Eventlog -LogName System` 命令。</span><span class="sxs-lookup"><span data-stu-id="e14a5-154">For example, you can assign an alias to the `Get-Eventlog` cmdlet, but you cannot assign an alias to the `Get-Eventlog -LogName System` command.</span></span>

<span data-ttu-id="e14a5-155">您可以建立包含命令的函式。</span><span class="sxs-lookup"><span data-stu-id="e14a5-155">You can create a function that includes the command.</span></span> <span data-ttu-id="e14a5-156">若要建立函式，請輸入 "function" 這個字，後面接著函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="e14a5-156">To create a function, type the word "function" followed by a name for the function.</span></span> <span data-ttu-id="e14a5-157">輸入命令，並將它括在大括弧 ({}) 中。</span><span class="sxs-lookup"><span data-stu-id="e14a5-157">Type the command, and enclose it in braces ({}).</span></span>

<span data-ttu-id="e14a5-158">例如，下列命令會建立 syslog 函數。</span><span class="sxs-lookup"><span data-stu-id="e14a5-158">For example, the following command creates the syslog function.</span></span> <span data-ttu-id="e14a5-159">此函數代表 `Get-Eventlog -LogName System` 命令：</span><span class="sxs-lookup"><span data-stu-id="e14a5-159">This function represents the `Get-Eventlog -LogName System` command:</span></span>

```powershell
function Get-SystemEventlog {Get-Eventlog -LogName System}
Set-Alias -Name syslog -Value Get-SystemEventlog
```

<span data-ttu-id="e14a5-160">您現在可以輸入 "syslog"，而不是命令。</span><span class="sxs-lookup"><span data-stu-id="e14a5-160">You can now type "syslog" instead of the command.</span></span> <span data-ttu-id="e14a5-161">而且，您可以為新的函式建立別名。</span><span class="sxs-lookup"><span data-stu-id="e14a5-161">And, you can create aliases for the new function.</span></span>

<span data-ttu-id="e14a5-162">如需函數的詳細資訊，請輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-162">For more information about functions, type:</span></span>

```powershell
Get-Help about_Functions
```

## <a name="alias-objects"></a><span data-ttu-id="e14a5-163">別名物件</span><span class="sxs-lookup"><span data-stu-id="e14a5-163">ALIAS OBJECTS</span></span>

<span data-ttu-id="e14a5-164">PowerShell 別名會以 System.management.automation.aliasinfo 類別實例的物件來表示。</span><span class="sxs-lookup"><span data-stu-id="e14a5-164">PowerShell aliases are represented by objects that are instances of the System.Management.Automation.AliasInfo class.</span></span> <span data-ttu-id="e14a5-165">如需此類型之物件的詳細資訊，請參閱 Microsoft 開發人員 Network (MSDN) library 中的 [System.management.automation.aliasinfo 類別][aliasinfo] 。</span><span class="sxs-lookup"><span data-stu-id="e14a5-165">For more information about this type of object, see [AliasInfo Class][aliasinfo] in the Microsoft Developer Network (MSDN) library.</span></span>

<span data-ttu-id="e14a5-166">若要查看別名物件的屬性和方法，請取得別名。</span><span class="sxs-lookup"><span data-stu-id="e14a5-166">To view the properties and methods of the alias objects, get the aliases.</span></span>
<span data-ttu-id="e14a5-167">然後，將它們輸送至 Get-Member Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e14a5-167">Then, pipe them to the Get-Member cmdlet.</span></span> <span data-ttu-id="e14a5-168">例如：</span><span class="sxs-lookup"><span data-stu-id="e14a5-168">For example:</span></span>

```powershell
Get-Alias | Get-Member
```

<span data-ttu-id="e14a5-169">若要查看特定別名（例如別名）的屬性值， `dir` 請取得別名。</span><span class="sxs-lookup"><span data-stu-id="e14a5-169">To view the values of the properties of a specific alias, such as the `dir` alias, get the alias.</span></span> <span data-ttu-id="e14a5-170">然後，將它輸送至 Format-List Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e14a5-170">Then, pipe it to the Format-List cmdlet.</span></span> <span data-ttu-id="e14a5-171">例如，下列命令會取得 "dir" 別名。</span><span class="sxs-lookup"><span data-stu-id="e14a5-171">For example, the following command gets the "dir" alias.</span></span> <span data-ttu-id="e14a5-172">接著，命令會以管道將別名傳送至 Format-List Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e14a5-172">Next, the command pipes the alias to the Format-List cmdlet.</span></span> <span data-ttu-id="e14a5-173">然後，此命令會使用 Format-List 的 Property 參數搭配萬用字元字元 (\*) 來顯示別名的所有屬性 `dir` 。</span><span class="sxs-lookup"><span data-stu-id="e14a5-173">Then, the command uses the Property parameter of Format-List with a wildcard character (\*) to display all the properties of the `dir` alias.</span></span> <span data-ttu-id="e14a5-174">下列命令會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="e14a5-174">The following command performs these tasks:</span></span>

```powershell
Get-Alias -Name dir | Format-List -Property *
```

## <a name="powershell-alias-provider"></a><span data-ttu-id="e14a5-175">PowerShell 別名提供者</span><span class="sxs-lookup"><span data-stu-id="e14a5-175">PowerShell ALIAS PROVIDER</span></span>

<span data-ttu-id="e14a5-176">PowerShell 包含別名提供者。</span><span class="sxs-lookup"><span data-stu-id="e14a5-176">PowerShell includes the Alias provider.</span></span> <span data-ttu-id="e14a5-177">別名提供者可讓您在 PowerShell 中查看別名，就好像它們是在檔案系統磁片磁碟機上一樣。</span><span class="sxs-lookup"><span data-stu-id="e14a5-177">The Alias provider lets you view the aliases in PowerShell as though they were on a file system drive.</span></span>

<span data-ttu-id="e14a5-178">別名提供者會公開 Alias：磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="e14a5-178">The Alias provider exposes the Alias: drive.</span></span> <span data-ttu-id="e14a5-179">若要進入 Alias：磁片磁碟機，請輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-179">To go into the Alias: drive, type:</span></span>

```powershell
Set-Location Alias:
```

<span data-ttu-id="e14a5-180">若要查看磁片磁碟機的內容，請輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-180">To view the contents of the drive, type:</span></span>

```powershell
Get-ChildItem
```

<span data-ttu-id="e14a5-181">若要從另一個 PowerShell 磁片磁碟機查看磁片磁碟機的內容，請使用磁片磁碟機名稱來開始路徑。</span><span class="sxs-lookup"><span data-stu-id="e14a5-181">To view the contents of the drive from another PowerShell drive, begin the path with the drive name.</span></span> <span data-ttu-id="e14a5-182">包含冒號 (： ) 。</span><span class="sxs-lookup"><span data-stu-id="e14a5-182">Include the colon (:).</span></span> <span data-ttu-id="e14a5-183">例如：</span><span class="sxs-lookup"><span data-stu-id="e14a5-183">For example:</span></span>

```powershell
Get-ChildItem -Path Alias:
```

<span data-ttu-id="e14a5-184">若要取得特定別名的相關資訊，請輸入磁片磁碟機名稱和別名名稱。</span><span class="sxs-lookup"><span data-stu-id="e14a5-184">To get information about a particular alias, type the drive name and the alias name.</span></span> <span data-ttu-id="e14a5-185">或者，輸入名稱模式。</span><span class="sxs-lookup"><span data-stu-id="e14a5-185">Or, type a name pattern.</span></span> <span data-ttu-id="e14a5-186">例如，若要取得以 "p" 開頭的所有別名，請輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-186">For example, to get all the aliases that begin with "p", type:</span></span>

```powershell
Get-ChildItem -Path Alias:p*
```

<span data-ttu-id="e14a5-187">如需 PowerShell 別名提供者的詳細資訊，請輸入：</span><span class="sxs-lookup"><span data-stu-id="e14a5-187">For more information about the PowerShell Alias provider, type:</span></span>

```powershell
Get-Help Alias
```

## <a name="see-also"></a><span data-ttu-id="e14a5-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e14a5-188">SEE ALSO</span></span>

- [<span data-ttu-id="e14a5-189">New-Alias</span><span class="sxs-lookup"><span data-stu-id="e14a5-189">New-Alias</span></span>](xref:Microsoft.PowerShell.Utility.New-Alias)
- [<span data-ttu-id="e14a5-190">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="e14a5-190">Get-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [<span data-ttu-id="e14a5-191">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="e14a5-191">Set-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Set-Alias)
- [<span data-ttu-id="e14a5-192">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="e14a5-192">Export-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [<span data-ttu-id="e14a5-193">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="e14a5-193">Import-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [<span data-ttu-id="e14a5-194">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="e14a5-194">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)
- [<span data-ttu-id="e14a5-195">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="e14a5-195">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="e14a5-196">about_functions</span><span class="sxs-lookup"><span data-stu-id="e14a5-196">about_functions</span></span>](about_functions.md)
- [<span data-ttu-id="e14a5-197">about_profiles</span><span class="sxs-lookup"><span data-stu-id="e14a5-197">about_profiles</span></span>](about_profiles.md)
- [<span data-ttu-id="e14a5-198">about_providers</span><span class="sxs-lookup"><span data-stu-id="e14a5-198">about_providers</span></span>](about_providers.md)

<!-- External links -->
[aliasinfo]: /dotnet/api/system.management.automation.aliasinfo

