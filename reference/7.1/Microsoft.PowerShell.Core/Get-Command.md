---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 60b6d2e380685650a86f74056a992afb4051ddc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205151"
---
# <span data-ttu-id="c27ef-103">Get-Command</span><span class="sxs-lookup"><span data-stu-id="c27ef-103">Get-Command</span></span>

## <span data-ttu-id="c27ef-104">概要</span><span class="sxs-lookup"><span data-stu-id="c27ef-104">SYNOPSIS</span></span>
<span data-ttu-id="c27ef-105">取得所有命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-105">Gets all commands.</span></span>

## <span data-ttu-id="c27ef-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c27ef-106">SYNTAX</span></span>

### <span data-ttu-id="c27ef-107">CmdletSet (預設) </span><span class="sxs-lookup"><span data-stu-id="c27ef-107">CmdletSet (Default)</span></span>

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### <span data-ttu-id="c27ef-108">AllCommandSet</span><span class="sxs-lookup"><span data-stu-id="c27ef-108">AllCommandSet</span></span>

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [-UseAbbreviationExpansion] [<CommonParameters>]
```

## <span data-ttu-id="c27ef-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c27ef-109">DESCRIPTION</span></span>

<span data-ttu-id="c27ef-110">此 `Get-Command` Cmdlet 會取得電腦上安裝的所有命令，包括 Cmdlet、別名、函式、篩選器、腳本和應用程式。</span><span class="sxs-lookup"><span data-stu-id="c27ef-110">The `Get-Command` cmdlet gets all commands that are installed on the computer, including cmdlets, aliases, functions, filters, scripts, and applications.</span></span> <span data-ttu-id="c27ef-111">`Get-Command` 從 PowerShell 模組和從其他會話匯入的命令取得命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-111">`Get-Command` gets the commands from PowerShell modules and commands that were imported from other sessions.</span></span> <span data-ttu-id="c27ef-112">若只要取得已經匯入目前工作階段的命令，請使用 **ListImported** 參數。</span><span class="sxs-lookup"><span data-stu-id="c27ef-112">To get only commands that have been imported into the current session, use the **ListImported** parameter.</span></span>

<span data-ttu-id="c27ef-113">如果沒有參數，則會 `Get-Command` 取得電腦上安裝的所有 Cmdlet、函式和別名。</span><span class="sxs-lookup"><span data-stu-id="c27ef-113">Without parameters, `Get-Command` gets all of the cmdlets, functions, and aliases installed on the computer.</span></span> <span data-ttu-id="c27ef-114">`Get-Command *` 取得所有類型的命令，包括 Path 環境變數中的所有非 PowerShell 檔案 (`$env:Path`) ，它會在應用程式命令類型中列出。</span><span class="sxs-lookup"><span data-stu-id="c27ef-114">`Get-Command *` gets all types of commands, including all of the non-PowerShell files in the Path environment variable (`$env:Path`), which it lists in the Application command type.</span></span>

<span data-ttu-id="c27ef-115">`Get-Command` 使用命令的完整名稱（不含萬用字元），會自動匯入包含命令的模組，讓您可以立即使用命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-115">`Get-Command` that uses the exact name of the command, without wildcard characters, automatically imports the module that contains the command so that you can use the command immediately.</span></span> <span data-ttu-id="c27ef-116">若要啟用、停用及設定自動匯入模組，請使用 `$PSModuleAutoLoadingPreference` 喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="c27ef-116">To enable, disable, and configure automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="c27ef-117">如需詳細資訊，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c27ef-117">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="c27ef-118">`Get-Command` 從命令代碼直接取得其資料，不同于從 `Get-Help` 說明主題取得其資訊。</span><span class="sxs-lookup"><span data-stu-id="c27ef-118">`Get-Command` gets its data directly from the command code, unlike `Get-Help`, which gets its information from help topics.</span></span>

<span data-ttu-id="c27ef-119">從 Windows PowerShell 5.0 開始，Cmdlet 的結果 `Get-Command` 預設會顯示 **版本** 資料行。</span><span class="sxs-lookup"><span data-stu-id="c27ef-119">Starting in Windows PowerShell 5.0, results of the `Get-Command` cmdlet display a **Version** column by default.</span></span> <span data-ttu-id="c27ef-120">已將新的 **版本** 屬性加入至 **CommandInfo** 類別。</span><span class="sxs-lookup"><span data-stu-id="c27ef-120">A new **Version** property has been added to the **CommandInfo** class.</span></span>

## <span data-ttu-id="c27ef-121">範例</span><span class="sxs-lookup"><span data-stu-id="c27ef-121">EXAMPLES</span></span>

### <span data-ttu-id="c27ef-122">範例1：取得 Cmdlet、函式和別名</span><span class="sxs-lookup"><span data-stu-id="c27ef-122">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="c27ef-123">此命令會取得電腦上安裝的 PowerShell Cmdlet、函式和別名。</span><span class="sxs-lookup"><span data-stu-id="c27ef-123">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <span data-ttu-id="c27ef-124">範例2：取得目前會話中的命令</span><span class="sxs-lookup"><span data-stu-id="c27ef-124">Example 2: Get commands in the current session</span></span>

<span data-ttu-id="c27ef-125">此命令使用 **ListImported** 參數，只取得目前工作階段中的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-125">This command uses the **ListImported** parameter to get only the commands in the current session.</span></span>

```powershell
Get-Command -ListImported
```

### <span data-ttu-id="c27ef-126">範例3：取得 Cmdlet 並依序顯示</span><span class="sxs-lookup"><span data-stu-id="c27ef-126">Example 3: Get cmdlets and display them in order</span></span>

<span data-ttu-id="c27ef-127">此命令會取得所有的 Cmdlet，接著依照 Cmdlet 名稱中之名詞的字母順序排序，然後將它們顯示於依名詞分類的群組中。</span><span class="sxs-lookup"><span data-stu-id="c27ef-127">This command gets all of the cmdlets, sorts them alphabetically by the noun in the cmdlet name, and then displays them in noun-based groups.</span></span> <span data-ttu-id="c27ef-128">此顯示方式可協助您尋找某個工作的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c27ef-128">This display can help you find the cmdlets for a task.</span></span>

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### <span data-ttu-id="c27ef-129">範例4：取得模組中的命令</span><span class="sxs-lookup"><span data-stu-id="c27ef-129">Example 4: Get commands in a module</span></span>

<span data-ttu-id="c27ef-130">此命令會使用 **Module** 參數來取得 Microsoft. 安全性和 microsoft.. a. powershell 模組中的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-130">This command uses the **Module** parameter to get the commands in the Microsoft.PowerShell.Security and Microsoft.PowerShell.Utility modules.</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### <span data-ttu-id="c27ef-131">範例5：取得 Cmdlet 的相關資訊</span><span class="sxs-lookup"><span data-stu-id="c27ef-131">Example 5: Get information about a cmdlet</span></span>

<span data-ttu-id="c27ef-132">此命令會取得 Cmdlet 的相關資訊 `Get-AppLockerPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="c27ef-132">This command gets information about the `Get-AppLockerPolicy` cmdlet.</span></span> <span data-ttu-id="c27ef-133">它也會匯入 **AppLocker** 模組，這會將 **AppLocker** 模組中的所有命令新增至目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="c27ef-133">It also imports the **AppLocker** module, which adds all of the commands in the **AppLocker** module to the current session.</span></span>

```powershell
Get-Command Get-AppLockerPolicy
```

<span data-ttu-id="c27ef-134">自動匯入模組時，效果會與使用 Import-Module Cmdlet 相同。</span><span class="sxs-lookup"><span data-stu-id="c27ef-134">When a module is imported automatically, the effect is the same as using the Import-Module cmdlet.</span></span>
<span data-ttu-id="c27ef-135">模組可以新增命令、類型及格式化檔案，並在工作階段中執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="c27ef-135">The module can add commands, types and formatting files, and run scripts in the session.</span></span> <span data-ttu-id="c27ef-136">若要啟用、停用及設定自動匯入模組，請使用 `$PSModuleAutoLoadingPreference` 喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="c27ef-136">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="c27ef-137">如需詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c27ef-137">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="c27ef-138">範例6：取得 Cmdlet 的語法</span><span class="sxs-lookup"><span data-stu-id="c27ef-138">Example 6: Get the syntax of a cmdlet</span></span>

<span data-ttu-id="c27ef-139">此命令會使用 **ArgumentList** 和 **語法** 參數來取得 `Get-ChildItem` Cmdlet 在 Cert：磁片磁碟機中使用時的語法。</span><span class="sxs-lookup"><span data-stu-id="c27ef-139">This command uses the **ArgumentList** and **Syntax** parameters to get the syntax of the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span> <span data-ttu-id="c27ef-140">Cert：磁片磁碟機是憑證提供者新增至會話的 PowerShell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="c27ef-140">The Cert: drive is a PowerShell drive that the Certificate Provider adds to the session.</span></span>

```powershell
Get-Command  -Name Get-Childitem -Args Cert: -Syntax
```

<span data-ttu-id="c27ef-141">當您比較輸出中所顯示的語法與省略 **Args** ( **ArgumentList** ) 參數時所顯示的語法時，您會看到 **憑證提供者** 將動態參數 **CodeSigningCert** 新增至 `Get-ChildItem` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c27ef-141">When you compare the syntax displayed in the output with the syntax that is displayed when you omit the **Args** ( **ArgumentList** ) parameter, you'll see that the **Certificate provider** adds a dynamic parameter, **CodeSigningCert** , to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="c27ef-142">如需有關憑證提供者的詳細資訊，請參閱 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)。</span><span class="sxs-lookup"><span data-stu-id="c27ef-142">For more information about the Certificate provider, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="c27ef-143">範例7：取得動態參數</span><span class="sxs-lookup"><span data-stu-id="c27ef-143">Example 7: Get dynamic parameters</span></span>

<span data-ttu-id="c27ef-144">此範例中的命令會使用函式 `Get-DynamicParameters` 來取得憑證提供者在 `Get-ChildItem` Cert：磁片磁碟機中使用時，新增至 Cmdlet 的動態參數。</span><span class="sxs-lookup"><span data-stu-id="c27ef-144">The command in the example uses the `Get-DynamicParameters` function to get the dynamic parameters that the Certificate provider adds to the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span>

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command -Name $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

<span data-ttu-id="c27ef-145">此範例中的函式會 `Get-DynamicParameters` 取得 Cmdlet 的動態參數。</span><span class="sxs-lookup"><span data-stu-id="c27ef-145">The `Get-DynamicParameters` function in this example gets the dynamic parameters of a cmdlet.</span></span> <span data-ttu-id="c27ef-146">這是上一個範例中所使用之方法的替代方法。</span><span class="sxs-lookup"><span data-stu-id="c27ef-146">This is an alternative to the method used in the previous example.</span></span> <span data-ttu-id="c27ef-147">動態參數可透過其他 Cmdlet 或提供者新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c27ef-147">Dynamic parameter can be added to a cmdlet by another cmdlet or a provider.</span></span>

### <span data-ttu-id="c27ef-148">範例8：取得所有類型的所有命令</span><span class="sxs-lookup"><span data-stu-id="c27ef-148">Example 8: Get all commands of all types</span></span>

<span data-ttu-id="c27ef-149">此命令會取得本機電腦上所有類型的所有命令，包括 **Path** 環境變數路徑中的可執行檔 (`$env:path`) 。</span><span class="sxs-lookup"><span data-stu-id="c27ef-149">This command gets all commands of all types on the local computer, including executable files in the paths of the **Path** environment variable (`$env:path`).</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="c27ef-150">它會傳回每個檔案的 **ApplicationInfo** 物件 (System.Management.Automation.ApplicationInfo)，而不是傳回 **FileInfo** 物件 (System.IO.FileInfo)。</span><span class="sxs-lookup"><span data-stu-id="c27ef-150">It returns an **ApplicationInfo** object (System.Management.Automation.ApplicationInfo) for each file, not a **FileInfo** object (System.IO.FileInfo).</span></span>

### <span data-ttu-id="c27ef-151">範例9：使用參數名稱和類型取得 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c27ef-151">Example 9: Get cmdlets by using a parameter name and type</span></span>

<span data-ttu-id="c27ef-152">此命令會取得具有參數的 Cmdlet，其名稱包含 Auth，而其型別為 **AuthenticationMechanism** 。</span><span class="sxs-lookup"><span data-stu-id="c27ef-152">This command gets cmdlets that have a parameter whose name includes Auth and whose type is **AuthenticationMechanism** .</span></span>

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

<span data-ttu-id="c27ef-153">您可以使用類似的命令，來尋找可讓您指定用來驗證使用者之方法的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c27ef-153">You can use a command like this one to find cmdlets that let you specify the method that is used to authenticate the user.</span></span>

<span data-ttu-id="c27ef-154">**ParameterType** 參數會區分接受 **AuthenticationMechanism** 值的參數與接受 **AuthenticationLevel** 參數的參數，即使它們有類似的名稱。</span><span class="sxs-lookup"><span data-stu-id="c27ef-154">The **ParameterType** parameter distinguishes parameters that take an **AuthenticationMechanism** value from those that take an **AuthenticationLevel** parameter, even when they have similar names.</span></span>

### <span data-ttu-id="c27ef-155">範例10：取得別名</span><span class="sxs-lookup"><span data-stu-id="c27ef-155">Example 10: Get an alias</span></span>

<span data-ttu-id="c27ef-156">此範例示範如何搭配使用 `Get-Command` Cmdlet 與別名。</span><span class="sxs-lookup"><span data-stu-id="c27ef-156">This example shows how to use the `Get-Command` cmdlet with an alias.</span></span>

```powershell
Get-Command Name dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

<span data-ttu-id="c27ef-157">雖然它通常用於 Cmdlet 和函式，但 `Get-Command` 也會取得腳本、函式、別名和可執行檔。</span><span class="sxs-lookup"><span data-stu-id="c27ef-157">Although it is typically used on cmdlets and functions, `Get-Command` also gets scripts, functions, aliases, and executable files.</span></span>

<span data-ttu-id="c27ef-158">命令的輸出顯示別名之 **Name** 屬性值的特別檢視。</span><span class="sxs-lookup"><span data-stu-id="c27ef-158">The output of the command shows the special view of the **Name** property value for aliases.</span></span> <span data-ttu-id="c27ef-159">該檢視顯示別名和完整命令名稱。</span><span class="sxs-lookup"><span data-stu-id="c27ef-159">The view shows the alias and the full command name.</span></span>

### <span data-ttu-id="c27ef-160">範例11：從別名取得語法</span><span class="sxs-lookup"><span data-stu-id="c27ef-160">Example 11: Get Syntax from an alias</span></span>

<span data-ttu-id="c27ef-161">此範例示範如何取得語法，以及別名的標準名稱。</span><span class="sxs-lookup"><span data-stu-id="c27ef-161">This example shows how to get the syntax along with the standard name of an alias.</span></span>

<span data-ttu-id="c27ef-162">命令的輸出會以標準名稱顯示標示的別名，後面接著語法。</span><span class="sxs-lookup"><span data-stu-id="c27ef-162">The output of the command shows the labeled alias with the standard name, followed by the syntax.</span></span>

```powershell
Get-Command -Name dir -Syntax
```

```Output
dir (alias) -> Get-ChildItem

dir [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]

dir [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### <span data-ttu-id="c27ef-163">範例12：取得記事本命令的所有實例</span><span class="sxs-lookup"><span data-stu-id="c27ef-163">Example 12: Get all instances of the Notepad command</span></span>

<span data-ttu-id="c27ef-164">此範例會使用 Cmdlet 的 **all** 參數 `Get-Command` ，在 `Notepad` 本機電腦上顯示命令的所有實例。</span><span class="sxs-lookup"><span data-stu-id="c27ef-164">This example uses the **All** parameter of the `Get-Command` cmdlet to show all instances of the `Notepad` command on the local computer.</span></span>

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

<span data-ttu-id="c27ef-165">當工作階段中有多個相同名稱的命令時， **All** 參數會非常有用。</span><span class="sxs-lookup"><span data-stu-id="c27ef-165">The **All** parameter is useful when there is more than one command with the same name in the session.</span></span>

<span data-ttu-id="c27ef-166">從 Windows PowerShell 3.0 開始，當會話中包含多個具有相同名稱的命令時， `Get-Command` 只會取得您輸入命令名稱時執行的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-166">Beginning in Windows PowerShell 3.0, by default, when the session includes multiple commands with the same name, `Get-Command` gets only the command that runs when you type the command name.</span></span> <span data-ttu-id="c27ef-167">使用 **all** 參數， `Get-Command` 取得具有指定名稱的所有命令，並依執行優先順序傳回它們。</span><span class="sxs-lookup"><span data-stu-id="c27ef-167">With the **All** parameter, `Get-Command` gets all commands with the specified name and returns them in execution precedence order.</span></span> <span data-ttu-id="c27ef-168">若要執行清單中第一個命令以外的某個命令，請輸入該命令的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c27ef-168">To run a command other than the first one in the list, type the fully qualified path to the command.</span></span>

<span data-ttu-id="c27ef-169">如需命令優先順序的詳細資訊，請參閱 [about_Command_Precedence](About/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="c27ef-169">For more information about command precedence, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="c27ef-170">範例13：取得包含 Cmdlet 的模組名稱</span><span class="sxs-lookup"><span data-stu-id="c27ef-170">Example 13: Get the name of a module that contains a cmdlet</span></span>

<span data-ttu-id="c27ef-171">此命令會取得 Cmdlet 來源的模組名稱 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="c27ef-171">This command gets the name of the module in which the `Get-Date` cmdlet originated.</span></span>
<span data-ttu-id="c27ef-172">此命令會使用所有命令的 **ModuleName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="c27ef-172">The command uses the **ModuleName** property of all commands.</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

<span data-ttu-id="c27ef-173">此命令格式適用于 PowerShell 模組中的命令，即使它們未匯入會話中也一樣。</span><span class="sxs-lookup"><span data-stu-id="c27ef-173">This command format works on commands in PowerShell modules, even if they are not imported into the session.</span></span>

### <span data-ttu-id="c27ef-174">範例14：取得有輸出類型的 Cmdlet 和函式</span><span class="sxs-lookup"><span data-stu-id="c27ef-174">Example 14: Get cmdlets and functions that have an output type</span></span>

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

<span data-ttu-id="c27ef-175">此命令會取得具有有輸出類型的 Cmdlet 和函式，以及它們傳回之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="c27ef-175">This command gets the cmdlets and functions that have an output type and the type of objects that they return.</span></span>

<span data-ttu-id="c27ef-176">命令的第一個部份會取得所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c27ef-176">The first part of the command gets all cmdlets.</span></span> <span data-ttu-id="c27ef-177">管線運算子 (`|`) 將指令程式傳送至 `Where-Object` Cmdlet，此 Cmdlet 只會選取已填入 **OutputType** 屬性的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c27ef-177">A pipeline operator (`|`) sends the cmdlets to the `Where-Object` cmdlet, which selects only the ones in which the **OutputType** property is populated.</span></span> <span data-ttu-id="c27ef-178">另一個管線運算子會將選取的 Cmdlet 物件傳送至 `Format-List` Cmdlet，此 Cmdlet 會顯示清單中每個 Cmdlet 的名稱和輸出類型。</span><span class="sxs-lookup"><span data-stu-id="c27ef-178">Another pipeline operator sends the selected cmdlet objects to the `Format-List` cmdlet, which displays the name and output type of each cmdlet in a list.</span></span>

<span data-ttu-id="c27ef-179">**CommandInfo** 物件的 **OutputType** 屬性只有在 Cmdlet 程式碼定義了 Cmdlet 的 **OutputType** 屬性時才會具有非 Null 的值。</span><span class="sxs-lookup"><span data-stu-id="c27ef-179">The **OutputType** property of a **CommandInfo** object has a non-null value only when the cmdlet code defines the **OutputType** attribute for the cmdlet.</span></span>

### <span data-ttu-id="c27ef-180">範例15：取得可採用特定物件類型做為輸入的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c27ef-180">Example 15: Get cmdlets that take a specific object type as input</span></span>

```powershell
Get-Command -ParameterType (((Get-NetAdapter)[0]).PSTypeNames)
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Disable-NetAdapter                                 NetAdapter
Function        Enable-NetAdapter                                  NetAdapter
Function        Rename-NetAdapter                                  NetAdapter
Function        Restart-NetAdapter                                 NetAdapter
Function        Set-NetAdapter                                     NetAdapter
```

<span data-ttu-id="c27ef-181">此命令會尋找使用網路介面卡物件做為輸入項目的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c27ef-181">This command finds cmdlets that take net adapter objects as input.</span></span> <span data-ttu-id="c27ef-182">您可以使用此命令格式來尋找接受任一命令傳回之物件類型的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c27ef-182">You can use this command format to find the cmdlets that accept the type of objects that any command returns.</span></span>

<span data-ttu-id="c27ef-183">此命令會使用所有物件的 **PSTypeNames** 內建屬性，它會取得描述物件的類型。</span><span class="sxs-lookup"><span data-stu-id="c27ef-183">The command uses the **PSTypeNames** intrinsic property of all objects, which gets the types that describe the object.</span></span> <span data-ttu-id="c27ef-184">為取得網路介面卡的 **PSTypeNames** 屬性，而不是網路介面卡集合的 **PSTypeNames** 屬性，該命令會使用陣列標記法來取得 Cmdlet 傳回的第一個網路介面卡。</span><span class="sxs-lookup"><span data-stu-id="c27ef-184">To get the **PSTypeNames** property of a net adapter, and not the **PSTypeNames** property of a collection of net adapters, the command uses array notation to get the first net adapter that the cmdlet returns.</span></span>

### <span data-ttu-id="c27ef-185">範例16：使用模糊相符來取得命令</span><span class="sxs-lookup"><span data-stu-id="c27ef-185">Example 16: Get commands using a fuzzy match</span></span>

<span data-ttu-id="c27ef-186">在此範例中，命令的名稱刻意以 ' commnd ' 的形式出現。</span><span class="sxs-lookup"><span data-stu-id="c27ef-186">In this example, the name of the command deliberately has a typo as 'get-commnd'.</span></span>
<span data-ttu-id="c27ef-187">使用 `-UseFuzzyMatching` 參數時，Cmdlet 判斷出最符合的 `Get-Command` 系統上的其他原生命令之後，會有相同的相符項。</span><span class="sxs-lookup"><span data-stu-id="c27ef-187">Using the `-UseFuzzyMatching` switch, the cmdlet determined that the best match was `Get-Command` followed by other native commands on the system that were a similar match.</span></span>

```powershell
Get-Command get-commnd -UseFuzzyMatching
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Command                                        6.2.0.0    Microsoft.PowerShell.Core
Application     getconf                                            0.0.0.0    /usr/bin/getconf
Application     command                                            0.0.0.0    /usr/bin/command
```

## <span data-ttu-id="c27ef-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c27ef-188">PARAMETERS</span></span>

### <span data-ttu-id="c27ef-189">-All</span><span class="sxs-lookup"><span data-stu-id="c27ef-189">-All</span></span>

<span data-ttu-id="c27ef-190">指出此 Cmdlet 會取得所有命令，包括具有相同名稱之相同類型的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-190">Indicates that this cmdlet gets all commands, including commands of the same type that have the same name.</span></span> <span data-ttu-id="c27ef-191">根據預設， `Get-Command` 只會取得您輸入命令名稱時所執行的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-191">By default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="c27ef-192">如需 PowerShell 在多個命令名稱相同時用來選取要執行之命令的方法的詳細資訊，請參閱 [about_Command_Precedence](About/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="c27ef-192">For more information about the method that PowerShell uses to select the command to run when multiple commands have the same name, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>
<span data-ttu-id="c27ef-193">如需模組合格命令名稱和執行命令的相關資訊（因為名稱衝突而不會預設執行），請參閱 [about_Modules](About/about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="c27ef-193">For information about module-qualified command names and running commands that do not run by default because of a name conflict, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="c27ef-194">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="c27ef-194">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="c27ef-195">在 Windows PowerShell 2.0 中， `Get-Command` 預設會取得所有命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-195">In Windows PowerShell 2.0, `Get-Command` gets all commands by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c27ef-196">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="c27ef-196">-ArgumentList</span></span>

<span data-ttu-id="c27ef-197">指定引數的陣列。</span><span class="sxs-lookup"><span data-stu-id="c27ef-197">Specifies an array of arguments.</span></span> <span data-ttu-id="c27ef-198">當 Cmdlet 或函式搭配指定的參數使用時，此 Cmdlet 會取得 Cmdlet 或函式的相關資訊 ( 「引數」 ) 。</span><span class="sxs-lookup"><span data-stu-id="c27ef-198">This cmdlet gets information about a cmdlet or function when it is used with the specified parameters ("arguments").</span></span> <span data-ttu-id="c27ef-199">**ArgumentList** 的別名是 **Args** 。</span><span class="sxs-lookup"><span data-stu-id="c27ef-199">The alias for **ArgumentList** is **Args** .</span></span>

<span data-ttu-id="c27ef-200">若要偵測只有在使用特定的其他參數時才能使用的動態參數，請將 **ArgumentList** 的值設為觸發動態參數的參數。</span><span class="sxs-lookup"><span data-stu-id="c27ef-200">To detect dynamic parameters that are available only when certain other parameters are used, set the value of **ArgumentList** to the parameters that trigger the dynamic parameters.</span></span>

<span data-ttu-id="c27ef-201">若要偵測提供者新增至 Cmdlet 的動態參數，請將 **ArgumentList** 參數的值設定為提供者磁片磁碟機中的路徑，例如 WSMan：、HKLM：或 Cert：。</span><span class="sxs-lookup"><span data-stu-id="c27ef-201">To detect the dynamic parameters that a provider adds to a cmdlet, set the value of the **ArgumentList** parameter to a path in the provider drive, such as WSMan:, HKLM:, or Cert:.</span></span> <span data-ttu-id="c27ef-202">當命令為 PowerShell 提供者 Cmdlet 時，請在每個命令中只輸入一個路徑。</span><span class="sxs-lookup"><span data-stu-id="c27ef-202">When the command is a PowerShell provider cmdlet, enter only one path in each command.</span></span> <span data-ttu-id="c27ef-203">提供者 Cmdlet 只會傳回 **ArgumentList** 值的第一個路徑的動態參數。</span><span class="sxs-lookup"><span data-stu-id="c27ef-203">The provider cmdlets return only the dynamic parameters for the first path the value of **ArgumentList** .</span></span> <span data-ttu-id="c27ef-204">如需提供者 Cmdlet 的詳細資訊，請參閱 [about_Providers](About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="c27ef-204">For information about the provider cmdlets, see [about_Providers](About/about_Providers.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c27ef-205">-CommandType</span><span class="sxs-lookup"><span data-stu-id="c27ef-205">-CommandType</span></span>

<span data-ttu-id="c27ef-206">指定此 Cmdlet 取得的命令類型。</span><span class="sxs-lookup"><span data-stu-id="c27ef-206">Specifies the types of commands that this cmdlet gets.</span></span> <span data-ttu-id="c27ef-207">輸入一或多個命令類型。</span><span class="sxs-lookup"><span data-stu-id="c27ef-207">Enter one or more command types.</span></span> <span data-ttu-id="c27ef-208">使用 **CommandType** 或它的別名 **Type** 。</span><span class="sxs-lookup"><span data-stu-id="c27ef-208">Use **CommandType** or its alias, **Type** .</span></span> <span data-ttu-id="c27ef-209">依預設，會 `Get-Command` 取得所有 Cmdlet、函式和別名。</span><span class="sxs-lookup"><span data-stu-id="c27ef-209">By default, `Get-Command` gets all cmdlets, functions, and aliases.</span></span>

<span data-ttu-id="c27ef-210">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="c27ef-210">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c27ef-211">別名。</span><span class="sxs-lookup"><span data-stu-id="c27ef-211">Alias.</span></span> <span data-ttu-id="c27ef-212">取得所有 PowerShell 命令的別名。</span><span class="sxs-lookup"><span data-stu-id="c27ef-212">Gets the aliases of all PowerShell commands.</span></span> <span data-ttu-id="c27ef-213">如需詳細資訊，請參閱 [about_Aliases](About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="c27ef-213">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>
- <span data-ttu-id="c27ef-214">全部。</span><span class="sxs-lookup"><span data-stu-id="c27ef-214">All.</span></span> <span data-ttu-id="c27ef-215">取得所有命令類型。</span><span class="sxs-lookup"><span data-stu-id="c27ef-215">Gets all command types.</span></span> <span data-ttu-id="c27ef-216">這個參數值相當於 `Get-Command *` 。</span><span class="sxs-lookup"><span data-stu-id="c27ef-216">This parameter value is the equivalent of `Get-Command *`.</span></span>
- <span data-ttu-id="c27ef-217">應用程式。</span><span class="sxs-lookup"><span data-stu-id="c27ef-217">Application.</span></span> <span data-ttu-id="c27ef-218">取得 **Path** 環境變數所列路徑中的非 PowerShell 檔案 ($env:p 路徑 a) ) ，包括 .txt、.exe 和 .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="c27ef-218">Gets non-PowerShell files in paths listed in the **Path** environment variable ($env:path), including .txt, .exe, and .dll files.</span></span> <span data-ttu-id="c27ef-219">如需 **Path** 環境變數的詳細資訊，請參閱 about_Environment_Variables。</span><span class="sxs-lookup"><span data-stu-id="c27ef-219">For more information about the **Path** environment variable, see about_Environment_Variables.</span></span>
- <span data-ttu-id="c27ef-220">Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c27ef-220">Cmdlet.</span></span> <span data-ttu-id="c27ef-221">取得所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c27ef-221">Gets all cmdlets.</span></span>
- <span data-ttu-id="c27ef-222">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="c27ef-222">ExternalScript.</span></span> <span data-ttu-id="c27ef-223">取得 **Path** 環境變數 ($env:path) 所列出之路徑中的所有 .ps1 檔案。</span><span class="sxs-lookup"><span data-stu-id="c27ef-223">Gets all .ps1 files in the paths listed in the **Path** environment variable ($env:path).</span></span>
- <span data-ttu-id="c27ef-224">篩選和函數。</span><span class="sxs-lookup"><span data-stu-id="c27ef-224">Filter and Function.</span></span> <span data-ttu-id="c27ef-225">取得所有 PowerShell advanced 和 simple 函數和篩選器。</span><span class="sxs-lookup"><span data-stu-id="c27ef-225">Gets all PowerShell advanced and simple functions and filters.</span></span>
- <span data-ttu-id="c27ef-226">指令碼：</span><span class="sxs-lookup"><span data-stu-id="c27ef-226">Script.</span></span> <span data-ttu-id="c27ef-227">取得所有指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="c27ef-227">Gets all script blocks.</span></span> <span data-ttu-id="c27ef-228">若要)  ( ps1 檔案取得 PowerShell 腳本，請使用 ExternalScript 值。</span><span class="sxs-lookup"><span data-stu-id="c27ef-228">To get PowerShell scripts (.ps1 files), use the ExternalScript value.</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: AllCommandSet
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c27ef-229">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="c27ef-229">-FullyQualifiedModule</span></span>

<span data-ttu-id="c27ef-230">以 **ModuleSpecification** 物件的形式指定具有指定名稱的模組，請參閱 [ModuleSpecification (雜湊) 表](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)的「 **備註** 」一節中所述。</span><span class="sxs-lookup"><span data-stu-id="c27ef-230">Specifies modules with names that are specified in the form of **ModuleSpecification** objects, described in the **Remarks** section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="c27ef-231">例如， **FullyQualifiedModule** 參數會接受以下列其中一種格式指定的模組名稱：</span><span class="sxs-lookup"><span data-stu-id="c27ef-231">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in one of the following formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="c27ef-232">**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="c27ef-232">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="c27ef-233">您無法在與 **模組** 參數相同的命令中指定 **FullyQualifiedModule** 參數。</span><span class="sxs-lookup"><span data-stu-id="c27ef-233">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="c27ef-234">這兩個參數是互斥的。</span><span class="sxs-lookup"><span data-stu-id="c27ef-234">The two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="c27ef-235">-ListImported</span><span class="sxs-lookup"><span data-stu-id="c27ef-235">-ListImported</span></span>

<span data-ttu-id="c27ef-236">指出此 Cmdlet 只會取得目前會話中的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-236">Indicates that this cmdlet gets only commands in the current session.</span></span>

<span data-ttu-id="c27ef-237">從 PowerShell 3.0 開始，根據預設， `Get-Command` 會取得所有已安裝的命令，包括（但不限於）目前會話中的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-237">Starting in PowerShell 3.0, by default, `Get-Command` gets all installed commands, including, but not limited to, the commands in the current session.</span></span> <span data-ttu-id="c27ef-238">在 PowerShell 2.0 中，它只會取得目前會話中的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-238">In PowerShell 2.0, it gets only commands in the current session.</span></span>

<span data-ttu-id="c27ef-239">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="c27ef-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c27ef-240">-Module</span><span class="sxs-lookup"><span data-stu-id="c27ef-240">-Module</span></span>

<span data-ttu-id="c27ef-241">指定模組的陣列。</span><span class="sxs-lookup"><span data-stu-id="c27ef-241">Specifies an array of modules.</span></span> <span data-ttu-id="c27ef-242">此 Cmdlet 會取得來自指定模組的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-242">This cmdlet gets the commands that came from the specified modules.</span></span>
<span data-ttu-id="c27ef-243">輸入模組或模組物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="c27ef-243">Enter the names of modules or module objects.</span></span>

<span data-ttu-id="c27ef-244">此參數接受字串值，但此參數的值也可以是 **PSModuleInfo** 物件，例如和 Cmdlet 所傳回的物件 `Get-Module` `Import-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="c27ef-244">This parameter takes string values, but the value of this parameter can also be a **PSModuleInfo** object, such as the objects that the `Get-Module` and `Import-PSSession` cmdlets return.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="c27ef-245">-Name</span><span class="sxs-lookup"><span data-stu-id="c27ef-245">-Name</span></span>

<span data-ttu-id="c27ef-246">指定名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="c27ef-246">Specifies an array of names.</span></span> <span data-ttu-id="c27ef-247">此 Cmdlet 只會取得具有指定之名稱的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-247">This cmdlet gets only commands that have the specified name.</span></span> <span data-ttu-id="c27ef-248">輸入名稱或名稱模式。</span><span class="sxs-lookup"><span data-stu-id="c27ef-248">Enter a name or name pattern.</span></span> <span data-ttu-id="c27ef-249">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c27ef-249">Wildcard characters are permitted.</span></span>

<span data-ttu-id="c27ef-250">若要取得名稱相同的命令，請使用 **All** 參數。</span><span class="sxs-lookup"><span data-stu-id="c27ef-250">To get commands that have the same name, use the **All** parameter.</span></span> <span data-ttu-id="c27ef-251">當兩個命令的名稱相同時，根據預設，會 `Get-Command` 取得當您輸入命令名稱時所執行的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-251">When two commands have the same name, by default, `Get-Command` gets the command that runs when you type the command name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="c27ef-252">-名詞</span><span class="sxs-lookup"><span data-stu-id="c27ef-252">-Noun</span></span>

<span data-ttu-id="c27ef-253">指定命令名詞的陣列。</span><span class="sxs-lookup"><span data-stu-id="c27ef-253">Specifies an array of command nouns.</span></span> <span data-ttu-id="c27ef-254">此 Cmdlet 會取得包含 Cmdlet、函式和別名的命令，這些命令的名稱包含指定的名詞。</span><span class="sxs-lookup"><span data-stu-id="c27ef-254">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified noun.</span></span> <span data-ttu-id="c27ef-255">輸入一或多個名詞或名詞模式。</span><span class="sxs-lookup"><span data-stu-id="c27ef-255">Enter one or more nouns or noun patterns.</span></span> <span data-ttu-id="c27ef-256">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c27ef-256">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="c27ef-257">-ParameterName</span><span class="sxs-lookup"><span data-stu-id="c27ef-257">-ParameterName</span></span>

<span data-ttu-id="c27ef-258">指定參數名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="c27ef-258">Specifies an array of parameter names.</span></span> <span data-ttu-id="c27ef-259">此 Cmdlet 會取得會話中具有指定參數的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-259">This cmdlet gets commands in the session that have the specified parameters.</span></span> <span data-ttu-id="c27ef-260">輸入參數名稱或參數別名。</span><span class="sxs-lookup"><span data-stu-id="c27ef-260">Enter parameter names or parameter aliases.</span></span> <span data-ttu-id="c27ef-261">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c27ef-261">Wildcard characters are supported.</span></span>

<span data-ttu-id="c27ef-262">**ParameterName** 和 **ParameterType** 參數只會搜尋目前工作階段中的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-262">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="c27ef-263">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="c27ef-263">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c27ef-264">-ParameterType</span><span class="sxs-lookup"><span data-stu-id="c27ef-264">-ParameterType</span></span>

<span data-ttu-id="c27ef-265">指定參數名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="c27ef-265">Specifies an array of parameter names.</span></span> <span data-ttu-id="c27ef-266">此 Cmdlet 會取得會話中具有指定類型參數的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-266">This cmdlet gets commands in the session that have parameters of the specified type.</span></span> <span data-ttu-id="c27ef-267">輸入參數類型的完整名稱或部分名稱。</span><span class="sxs-lookup"><span data-stu-id="c27ef-267">Enter the full name or partial name of a parameter type.</span></span> <span data-ttu-id="c27ef-268">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c27ef-268">Wildcard characters are supported.</span></span>

<span data-ttu-id="c27ef-269">**ParameterName** 和 **ParameterType** 參數只會搜尋目前工作階段中的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-269">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="c27ef-270">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="c27ef-270">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSTypeName[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c27ef-271">-ShowCommandInfo</span><span class="sxs-lookup"><span data-stu-id="c27ef-271">-ShowCommandInfo</span></span>

<span data-ttu-id="c27ef-272">指出此 Cmdlet 會顯示命令資訊。</span><span class="sxs-lookup"><span data-stu-id="c27ef-272">Indicates that this cmdlet displays command information.</span></span>

<span data-ttu-id="c27ef-273">此參數是在 Windows PowerShell 5.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c27ef-273">This parameter was introduced in Windows PowerShell 5.0.</span></span>

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

### <span data-ttu-id="c27ef-274">-語法</span><span class="sxs-lookup"><span data-stu-id="c27ef-274">-Syntax</span></span>

<span data-ttu-id="c27ef-275">指出此 Cmdlet 只會取得下列關於命令的指定資料：</span><span class="sxs-lookup"><span data-stu-id="c27ef-275">Indicates that this cmdlet gets only the following specified data about the command:</span></span>

- <span data-ttu-id="c27ef-276">別名。</span><span class="sxs-lookup"><span data-stu-id="c27ef-276">Aliases.</span></span> <span data-ttu-id="c27ef-277">取得標準名稱和語法。</span><span class="sxs-lookup"><span data-stu-id="c27ef-277">Gets the standard name and syntax.</span></span>
- <span data-ttu-id="c27ef-278">Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c27ef-278">Cmdlets.</span></span> <span data-ttu-id="c27ef-279">取得語法。</span><span class="sxs-lookup"><span data-stu-id="c27ef-279">Gets the syntax.</span></span>
- <span data-ttu-id="c27ef-280">函數和篩選準則。</span><span class="sxs-lookup"><span data-stu-id="c27ef-280">Functions and filters.</span></span> <span data-ttu-id="c27ef-281">取得函式定義。</span><span class="sxs-lookup"><span data-stu-id="c27ef-281">Gets the function definition.</span></span>
- <span data-ttu-id="c27ef-282">腳本和應用程式或檔案。</span><span class="sxs-lookup"><span data-stu-id="c27ef-282">Scripts and applications or files.</span></span> <span data-ttu-id="c27ef-283">取得路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="c27ef-283">Gets the path and filename.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c27ef-284">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="c27ef-284">-TotalCount</span></span>

<span data-ttu-id="c27ef-285">指定要取得的命令數目。</span><span class="sxs-lookup"><span data-stu-id="c27ef-285">Specifies the number of commands to get.</span></span> <span data-ttu-id="c27ef-286">您可以使用此參數來限制命令的輸出。</span><span class="sxs-lookup"><span data-stu-id="c27ef-286">You can use this parameter to limit the output of a command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c27ef-287">-UseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="c27ef-287">-UseAbbreviationExpansion</span></span>

<span data-ttu-id="c27ef-288">表示在命令中使用相符的字元來尋找大寫字元。</span><span class="sxs-lookup"><span data-stu-id="c27ef-288">Indicates using matching of the characters in the command to find with uppercase characters in a command.</span></span> <span data-ttu-id="c27ef-289">例如， `i-psdf` 會比 `Import-PowerShellDataFile` 對每個要尋找的字元符合結果中的大寫字元。</span><span class="sxs-lookup"><span data-stu-id="c27ef-289">For example, `i-psdf` would match `Import-PowerShellDataFile` as each of the characters to find matches an uppercase character in the result.</span></span> <span data-ttu-id="c27ef-290">使用這種類型的比對時，任何萬用字元都不會產生相符專案。</span><span class="sxs-lookup"><span data-stu-id="c27ef-290">When using this type of match, any wildcards will result in no matches.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c27ef-291">-UseFuzzyMatching</span><span class="sxs-lookup"><span data-stu-id="c27ef-291">-UseFuzzyMatching</span></span>

<span data-ttu-id="c27ef-292">表示在尋找命令時使用模糊比對演算法。</span><span class="sxs-lookup"><span data-stu-id="c27ef-292">Indicates using a fuzzy matching algorithm when finding commands.</span></span> <span data-ttu-id="c27ef-293">輸出的順序是從最接近的相符到最不相符的結果。</span><span class="sxs-lookup"><span data-stu-id="c27ef-293">The order of the output is from closest match to least likely match.</span></span> <span data-ttu-id="c27ef-294">萬用字元不應與模糊比對搭配使用，因為它會嘗試比對可能包含這些萬用字元的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-294">Wildcards should not be used with fuzzy matching as it will attempt to match commands that may contain those wildcard characters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c27ef-295">-Verb</span><span class="sxs-lookup"><span data-stu-id="c27ef-295">-Verb</span></span>

<span data-ttu-id="c27ef-296">指定命令動詞命令陣列。</span><span class="sxs-lookup"><span data-stu-id="c27ef-296">Specifies an array of command verbs.</span></span> <span data-ttu-id="c27ef-297">此 Cmdlet 會取得包含 Cmdlet、函式和別名的命令，這些命令的名稱包含指定的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-297">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified verb.</span></span> <span data-ttu-id="c27ef-298">輸入一或多個動詞或動詞模式。</span><span class="sxs-lookup"><span data-stu-id="c27ef-298">Enter one or more verbs or verb patterns.</span></span> <span data-ttu-id="c27ef-299">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c27ef-299">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="c27ef-300">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c27ef-300">CommonParameters</span></span>

<span data-ttu-id="c27ef-301">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c27ef-301">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c27ef-302">如需詳細資訊，請參閱 [about_CommonParameters](About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="c27ef-302">For more information, see [about_CommonParameters](About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c27ef-303">輸入</span><span class="sxs-lookup"><span data-stu-id="c27ef-303">INPUTS</span></span>

### <span data-ttu-id="c27ef-304">System.String</span><span class="sxs-lookup"><span data-stu-id="c27ef-304">System.String</span></span>

<span data-ttu-id="c27ef-305">您可以透過管道將命令名稱傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c27ef-305">You can pipe command names to this cmdlet.</span></span>

## <span data-ttu-id="c27ef-306">輸出</span><span class="sxs-lookup"><span data-stu-id="c27ef-306">OUTPUTS</span></span>

### <span data-ttu-id="c27ef-307">CommandInfo。</span><span class="sxs-lookup"><span data-stu-id="c27ef-307">System.Management.Automation.CommandInfo</span></span>

<span data-ttu-id="c27ef-308">此 Cmdlet 會傳回衍生自 **CommandInfo** 類別的物件。</span><span class="sxs-lookup"><span data-stu-id="c27ef-308">This cmdlet returns objects derived from the **CommandInfo** class.</span></span> <span data-ttu-id="c27ef-309">傳回的物件類型取決於取得的命令類型 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="c27ef-309">The type of object that is returned depends on the type of command that `Get-Command` gets.</span></span>

### <span data-ttu-id="c27ef-310">System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="c27ef-310">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="c27ef-311">代表別名。</span><span class="sxs-lookup"><span data-stu-id="c27ef-311">Represents aliases.</span></span>

### <span data-ttu-id="c27ef-312">ApplicationInfo。</span><span class="sxs-lookup"><span data-stu-id="c27ef-312">System.Management.Automation.ApplicationInfo</span></span>

<span data-ttu-id="c27ef-313">代表應用程式和檔案。</span><span class="sxs-lookup"><span data-stu-id="c27ef-313">Represents applications and files.</span></span>

### <span data-ttu-id="c27ef-314">CmdletInfo。</span><span class="sxs-lookup"><span data-stu-id="c27ef-314">System.Management.Automation.CmdletInfo</span></span>

<span data-ttu-id="c27ef-315">代表 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c27ef-315">Represents cmdlets.</span></span>

### <span data-ttu-id="c27ef-316">System.Management.Automation.FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="c27ef-316">System.Management.Automation.FunctionInfo</span></span>

<span data-ttu-id="c27ef-317">表示函數和篩選準則。</span><span class="sxs-lookup"><span data-stu-id="c27ef-317">Represents functions and filters.</span></span>

## <span data-ttu-id="c27ef-318">注意</span><span class="sxs-lookup"><span data-stu-id="c27ef-318">NOTES</span></span>

* <span data-ttu-id="c27ef-319">當會話可以使用一個以上具有相同名稱的命令時，會傳回 `Get-Command` 當您輸入命令名稱時所執行的命令。</span><span class="sxs-lookup"><span data-stu-id="c27ef-319">When more than one command that has the same name is available to the session, `Get-Command` returns the command that runs when you type the command name.</span></span> <span data-ttu-id="c27ef-320">若要取得具有相同名稱的命令（依照執行順序列出），請使用 **All** 參數。</span><span class="sxs-lookup"><span data-stu-id="c27ef-320">To get commands that have the same name, listed in run order, use the **All** parameter.</span></span> <span data-ttu-id="c27ef-321">如需詳細資訊，請參閱 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="c27ef-321">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>
* <span data-ttu-id="c27ef-322">自動匯入模組時，效果與使用 `Import-Module` Cmdlet 相同。</span><span class="sxs-lookup"><span data-stu-id="c27ef-322">When a module is imported automatically, the effect is the same as using the `Import-Module` cmdlet.</span></span> <span data-ttu-id="c27ef-323">模組可以新增命令、類型及格式化檔案，並在工作階段中執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="c27ef-323">The module can add commands, types and formatting files, and run scripts in the session.</span></span>
  <span data-ttu-id="c27ef-324">若要啟用、停用及設定自動匯入模組，請使用 `$PSModuleAutoLoadingPreference` 喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="c27ef-324">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="c27ef-325">如需詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c27ef-325">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="c27ef-326">相關連結</span><span class="sxs-lookup"><span data-stu-id="c27ef-326">RELATED LINKS</span></span>

[<span data-ttu-id="c27ef-327">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="c27ef-327">Export-PSSession</span></span>](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[<span data-ttu-id="c27ef-328">Get-Help</span><span class="sxs-lookup"><span data-stu-id="c27ef-328">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="c27ef-329">Get-Member</span><span class="sxs-lookup"><span data-stu-id="c27ef-329">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="c27ef-330">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="c27ef-330">Get-PSDrive</span></span>](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[<span data-ttu-id="c27ef-331">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="c27ef-331">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="c27ef-332">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="c27ef-332">about_Command_Precedence</span></span>](About/about_Command_Precedence.md)

