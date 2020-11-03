---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/14/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 5e76a15e8f2dcacc7f973cbc46d057bb92c3ad41
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204904"
---
# <span data-ttu-id="5448b-103">Get-Command</span><span class="sxs-lookup"><span data-stu-id="5448b-103">Get-Command</span></span>

## <span data-ttu-id="5448b-104">概要</span><span class="sxs-lookup"><span data-stu-id="5448b-104">SYNOPSIS</span></span>
<span data-ttu-id="5448b-105">取得所有命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-105">Gets all commands.</span></span>

## <span data-ttu-id="5448b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5448b-106">SYNTAX</span></span>

### <span data-ttu-id="5448b-107">CmdletSet (預設) </span><span class="sxs-lookup"><span data-stu-id="5448b-107">CmdletSet (Default)</span></span>

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### <span data-ttu-id="5448b-108">AllCommandSet</span><span class="sxs-lookup"><span data-stu-id="5448b-108">AllCommandSet</span></span>

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [<CommonParameters>]
```

## <span data-ttu-id="5448b-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5448b-109">DESCRIPTION</span></span>

<span data-ttu-id="5448b-110">此 `Get-Command` Cmdlet 會取得電腦上安裝的所有命令，包括 Cmdlet、別名、函式、篩選器、腳本和應用程式。</span><span class="sxs-lookup"><span data-stu-id="5448b-110">The `Get-Command` cmdlet gets all commands that are installed on the computer, including cmdlets, aliases, functions, filters, scripts, and applications.</span></span> <span data-ttu-id="5448b-111">`Get-Command` 從 PowerShell 模組和從其他會話匯入的命令取得命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-111">`Get-Command` gets the commands from PowerShell modules and commands that were imported from other sessions.</span></span> <span data-ttu-id="5448b-112">若只要取得已經匯入目前工作階段的命令，請使用 **ListImported** 參數。</span><span class="sxs-lookup"><span data-stu-id="5448b-112">To get only commands that have been imported into the current session, use the **ListImported** parameter.</span></span>

<span data-ttu-id="5448b-113">如果沒有參數，則會 `Get-Command` 取得電腦上安裝的所有 Cmdlet、函式和別名。</span><span class="sxs-lookup"><span data-stu-id="5448b-113">Without parameters, `Get-Command` gets all of the cmdlets, functions, and aliases installed on the computer.</span></span> <span data-ttu-id="5448b-114">`Get-Command *` 取得所有類型的命令，包括 Path 環境變數中的所有非 PowerShell 檔案 (`$env:Path`) ，它會在應用程式命令類型中列出。</span><span class="sxs-lookup"><span data-stu-id="5448b-114">`Get-Command *` gets all types of commands, including all of the non-PowerShell files in the Path environment variable (`$env:Path`), which it lists in the Application command type.</span></span>

<span data-ttu-id="5448b-115">`Get-Command` 使用命令的完整名稱（不含萬用字元），會自動匯入包含命令的模組，讓您可以立即使用命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-115">`Get-Command` that uses the exact name of the command, without wildcard characters, automatically imports the module that contains the command so that you can use the command immediately.</span></span> <span data-ttu-id="5448b-116">若要啟用、停用及設定自動匯入模組，請使用 `$PSModuleAutoLoadingPreference` 喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="5448b-116">To enable, disable, and configure automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="5448b-117">如需詳細資訊，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="5448b-117">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="5448b-118">`Get-Command` 從命令代碼直接取得其資料，不同于從 `Get-Help` 說明主題取得其資訊。</span><span class="sxs-lookup"><span data-stu-id="5448b-118">`Get-Command` gets its data directly from the command code, unlike `Get-Help`, which gets its information from help topics.</span></span>

<span data-ttu-id="5448b-119">從 Windows PowerShell 5.0 開始，Cmdlet 的結果 `Get-Command` 預設會顯示 **版本** 資料行。</span><span class="sxs-lookup"><span data-stu-id="5448b-119">Starting in Windows PowerShell 5.0, results of the `Get-Command` cmdlet display a **Version** column by default.</span></span> <span data-ttu-id="5448b-120">已將新的 **版本** 屬性加入至 **CommandInfo** 類別。</span><span class="sxs-lookup"><span data-stu-id="5448b-120">A new **Version** property has been added to the **CommandInfo** class.</span></span>

## <span data-ttu-id="5448b-121">範例</span><span class="sxs-lookup"><span data-stu-id="5448b-121">EXAMPLES</span></span>

### <span data-ttu-id="5448b-122">範例1：取得 Cmdlet、函式和別名</span><span class="sxs-lookup"><span data-stu-id="5448b-122">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="5448b-123">此命令會取得電腦上安裝的 PowerShell Cmdlet、函式和別名。</span><span class="sxs-lookup"><span data-stu-id="5448b-123">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <span data-ttu-id="5448b-124">範例2：取得目前會話中的命令</span><span class="sxs-lookup"><span data-stu-id="5448b-124">Example 2: Get commands in the current session</span></span>

<span data-ttu-id="5448b-125">此命令使用 **ListImported** 參數，只取得目前工作階段中的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-125">This command uses the **ListImported** parameter to get only the commands in the current session.</span></span>

```powershell
Get-Command -ListImported
```

### <span data-ttu-id="5448b-126">範例3：取得 Cmdlet 並依序顯示</span><span class="sxs-lookup"><span data-stu-id="5448b-126">Example 3: Get cmdlets and display them in order</span></span>

<span data-ttu-id="5448b-127">此命令會取得所有的 Cmdlet，接著依照 Cmdlet 名稱中之名詞的字母順序排序，然後將它們顯示於依名詞分類的群組中。</span><span class="sxs-lookup"><span data-stu-id="5448b-127">This command gets all of the cmdlets, sorts them alphabetically by the noun in the cmdlet name, and then displays them in noun-based groups.</span></span> <span data-ttu-id="5448b-128">此顯示方式可協助您尋找某個工作的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5448b-128">This display can help you find the cmdlets for a task.</span></span>

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### <span data-ttu-id="5448b-129">範例4：取得模組中的命令</span><span class="sxs-lookup"><span data-stu-id="5448b-129">Example 4: Get commands in a module</span></span>

<span data-ttu-id="5448b-130">此命令會使用 **Module** 參數來取得 Microsoft. 安全性和 microsoft.. a. powershell 模組中的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-130">This command uses the **Module** parameter to get the commands in the Microsoft.PowerShell.Security and Microsoft.PowerShell.Utility modules.</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### <span data-ttu-id="5448b-131">範例5：取得 Cmdlet 的相關資訊</span><span class="sxs-lookup"><span data-stu-id="5448b-131">Example 5: Get information about a cmdlet</span></span>

<span data-ttu-id="5448b-132">此命令會取得 Cmdlet 的相關資訊 `Get-AppLockerPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="5448b-132">This command gets information about the `Get-AppLockerPolicy` cmdlet.</span></span> <span data-ttu-id="5448b-133">它也會匯入 **AppLocker** 模組，這會將 **AppLocker** 模組中的所有命令新增至目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="5448b-133">It also imports the **AppLocker** module, which adds all of the commands in the **AppLocker** module to the current session.</span></span>

```powershell
Get-Command Get-AppLockerPolicy
```

<span data-ttu-id="5448b-134">自動匯入模組時，效果會與使用 Import-Module Cmdlet 相同。</span><span class="sxs-lookup"><span data-stu-id="5448b-134">When a module is imported automatically, the effect is the same as using the Import-Module cmdlet.</span></span>
<span data-ttu-id="5448b-135">模組可以新增命令、類型及格式化檔案，並在工作階段中執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="5448b-135">The module can add commands, types and formatting files, and run scripts in the session.</span></span> <span data-ttu-id="5448b-136">若要啟用、停用及設定自動匯入模組，請使用 `$PSModuleAutoLoadingPreference` 喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="5448b-136">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="5448b-137">如需詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="5448b-137">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="5448b-138">範例6：取得 Cmdlet 的語法</span><span class="sxs-lookup"><span data-stu-id="5448b-138">Example 6: Get the syntax of a cmdlet</span></span>

<span data-ttu-id="5448b-139">此命令會使用 **ArgumentList** 和 **語法** 參數來取得 `Get-ChildItem` Cmdlet 在 Cert：磁片磁碟機中使用時的語法。</span><span class="sxs-lookup"><span data-stu-id="5448b-139">This command uses the **ArgumentList** and **Syntax** parameters to get the syntax of the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span> <span data-ttu-id="5448b-140">Cert：磁片磁碟機是憑證提供者新增至會話的 PowerShell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="5448b-140">The Cert: drive is a PowerShell drive that the Certificate Provider adds to the session.</span></span>

```powershell
Get-Command Get-Childitem -Args Cert: -Syntax
```

<span data-ttu-id="5448b-141">當您比較輸出中所顯示的語法與省略 **Args** ( **ArgumentList** ) 參數時所顯示的語法時，您會看到 **憑證提供者** 將動態參數 **CodeSigningCert** 新增至 `Get-ChildItem` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5448b-141">When you compare the syntax displayed in the output with the syntax that is displayed when you omit the **Args** ( **ArgumentList** ) parameter, you'll see that the **Certificate provider** adds a dynamic parameter, **CodeSigningCert** , to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="5448b-142">如需有關憑證提供者的詳細資訊，請參閱 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)。</span><span class="sxs-lookup"><span data-stu-id="5448b-142">For more information about the Certificate provider, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="5448b-143">範例7：取得動態參數</span><span class="sxs-lookup"><span data-stu-id="5448b-143">Example 7: Get dynamic parameters</span></span>

<span data-ttu-id="5448b-144">此範例中的命令會使用函式 `Get-DynamicParameters` 來取得憑證提供者在 `Get-ChildItem` Cert：磁片磁碟機中使用時，新增至 Cmdlet 的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5448b-144">The command in the example uses the `Get-DynamicParameters` function to get the dynamic parameters that the Certificate provider adds to the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span>

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

<span data-ttu-id="5448b-145">此範例中的函式會 `Get-DynamicParameters` 取得 Cmdlet 的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5448b-145">The `Get-DynamicParameters` function in this example gets the dynamic parameters of a cmdlet.</span></span> <span data-ttu-id="5448b-146">這是上一個範例中所使用之方法的替代方法。</span><span class="sxs-lookup"><span data-stu-id="5448b-146">This is an alternative to the method used in the previous example.</span></span> <span data-ttu-id="5448b-147">動態參數可透過其他 Cmdlet 或提供者新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5448b-147">Dynamic parameter can be added to a cmdlet by another cmdlet or a provider.</span></span>

### <span data-ttu-id="5448b-148">範例8：取得所有類型的所有命令</span><span class="sxs-lookup"><span data-stu-id="5448b-148">Example 8: Get all commands of all types</span></span>

<span data-ttu-id="5448b-149">此命令會取得本機電腦上所有類型的所有命令，包括 **Path** 環境變數路徑中的可執行檔 (`$env:path`) 。</span><span class="sxs-lookup"><span data-stu-id="5448b-149">This command gets all commands of all types on the local computer, including executable files in the paths of the **Path** environment variable (`$env:path`).</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="5448b-150">它會傳回每個檔案的 **ApplicationInfo** 物件 (System.Management.Automation.ApplicationInfo)，而不是傳回 **FileInfo** 物件 (System.IO.FileInfo)。</span><span class="sxs-lookup"><span data-stu-id="5448b-150">It returns an **ApplicationInfo** object (System.Management.Automation.ApplicationInfo) for each file, not a **FileInfo** object (System.IO.FileInfo).</span></span>

### <span data-ttu-id="5448b-151">範例9：使用參數名稱和類型取得 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5448b-151">Example 9: Get cmdlets by using a parameter name and type</span></span>

<span data-ttu-id="5448b-152">此命令會取得具有參數的 Cmdlet，其名稱包含 Auth，而其型別為 **AuthenticationMechanism** 。</span><span class="sxs-lookup"><span data-stu-id="5448b-152">This command gets cmdlets that have a parameter whose name includes Auth and whose type is **AuthenticationMechanism** .</span></span>

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

<span data-ttu-id="5448b-153">您可以使用類似的命令，來尋找可讓您指定用來驗證使用者之方法的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5448b-153">You can use a command like this one to find cmdlets that let you specify the method that is used to authenticate the user.</span></span>

<span data-ttu-id="5448b-154">**ParameterType** 參數會區分接受 **AuthenticationMechanism** 值的參數與接受 **AuthenticationLevel** 參數的參數，即使它們有類似的名稱。</span><span class="sxs-lookup"><span data-stu-id="5448b-154">The **ParameterType** parameter distinguishes parameters that take an **AuthenticationMechanism** value from those that take an **AuthenticationLevel** parameter, even when they have similar names.</span></span>

### <span data-ttu-id="5448b-155">範例10：取得別名</span><span class="sxs-lookup"><span data-stu-id="5448b-155">Example 10: Get an alias</span></span>

<span data-ttu-id="5448b-156">此範例示範如何搭配使用 `Get-Command` Cmdlet 與別名。</span><span class="sxs-lookup"><span data-stu-id="5448b-156">This example shows how to use the `Get-Command` cmdlet with an alias.</span></span>

```powershell
Get-Command dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

<span data-ttu-id="5448b-157">雖然它通常用於 Cmdlet 和函式，但 `Get-Command` 也會取得腳本、函式、別名和可執行檔。</span><span class="sxs-lookup"><span data-stu-id="5448b-157">Although it is typically used on cmdlets and functions, `Get-Command` also gets scripts, functions, aliases, and executable files.</span></span>

<span data-ttu-id="5448b-158">命令的輸出顯示別名之 **Name** 屬性值的特別檢視。</span><span class="sxs-lookup"><span data-stu-id="5448b-158">The output of the command shows the special view of the **Name** property value for aliases.</span></span> <span data-ttu-id="5448b-159">該檢視顯示別名和完整命令名稱。</span><span class="sxs-lookup"><span data-stu-id="5448b-159">The view shows the alias and the full command name.</span></span>

### <span data-ttu-id="5448b-160">範例11：取得記事本命令的所有實例</span><span class="sxs-lookup"><span data-stu-id="5448b-160">Example 11: Get all instances of the Notepad command</span></span>

<span data-ttu-id="5448b-161">此範例會使用 Cmdlet 的 **all** 參數 `Get-Command` 顯示本機電腦上 "Notepad" 命令的所有實例。</span><span class="sxs-lookup"><span data-stu-id="5448b-161">This example uses the **All** parameter of the `Get-Command` cmdlet to show all instances of the "Notepad" command on the local computer.</span></span>

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

<span data-ttu-id="5448b-162">當工作階段中有多個相同名稱的命令時， **All** 參數會非常有用。</span><span class="sxs-lookup"><span data-stu-id="5448b-162">The **All** parameter is useful when there is more than one command with the same name in the session.</span></span>

<span data-ttu-id="5448b-163">從 Windows PowerShell 3.0 開始，當會話中包含多個具有相同名稱的命令時， `Get-Command` 只會取得您輸入命令名稱時執行的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-163">Beginning in Windows PowerShell 3.0, by default, when the session includes multiple commands with the same name, `Get-Command` gets only the command that runs when you type the command name.</span></span> <span data-ttu-id="5448b-164">使用 **all** 參數， `Get-Command` 取得具有指定名稱的所有命令，並依執行優先順序傳回它們。</span><span class="sxs-lookup"><span data-stu-id="5448b-164">With the **All** parameter, `Get-Command` gets all commands with the specified name and returns them in execution precedence order.</span></span> <span data-ttu-id="5448b-165">若要執行清單中第一個命令以外的某個命令，請輸入該命令的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="5448b-165">To run a command other than the first one in the list, type the fully qualified path to the command.</span></span>

<span data-ttu-id="5448b-166">如需命令優先順序的詳細資訊，請參閱 [about_Command_Precedence](About/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="5448b-166">For more information about command precedence, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="5448b-167">範例12：取得包含 Cmdlet 的模組名稱</span><span class="sxs-lookup"><span data-stu-id="5448b-167">Example 12: Get the name of a module that contains a cmdlet</span></span>

<span data-ttu-id="5448b-168">此命令會取得 Cmdlet 來源的模組名稱 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="5448b-168">This command gets the name of the module in which the `Get-Date` cmdlet originated.</span></span>
<span data-ttu-id="5448b-169">此命令會使用所有命令的 **ModuleName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="5448b-169">The command uses the **ModuleName** property of all commands.</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

<span data-ttu-id="5448b-170">此命令格式適用于 PowerShell 模組中的命令，即使它們未匯入會話中也一樣。</span><span class="sxs-lookup"><span data-stu-id="5448b-170">This command format works on commands in PowerShell modules, even if they are not imported into the session.</span></span>

### <span data-ttu-id="5448b-171">範例13：取得有輸出類型的 Cmdlet 和函式</span><span class="sxs-lookup"><span data-stu-id="5448b-171">Example 13: Get cmdlets and functions that have an output type</span></span>

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

<span data-ttu-id="5448b-172">此命令會取得具有有輸出類型的 Cmdlet 和函式，以及它們傳回之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="5448b-172">This command gets the cmdlets and functions that have an output type and the type of objects that they return.</span></span>

<span data-ttu-id="5448b-173">命令的第一個部份會取得所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5448b-173">The first part of the command gets all cmdlets.</span></span>
<span data-ttu-id="5448b-174">管線運算子 (|) 將指令程式傳送至 `Where-Object` Cmdlet，此 Cmdlet 只會選取已填入 **OutputType** 屬性的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5448b-174">A pipeline operator (|) sends the cmdlets to the `Where-Object` cmdlet, which selects only the ones in which the **OutputType** property is populated.</span></span>
<span data-ttu-id="5448b-175">另一個管線運算子會將選取的 Cmdlet 物件傳送至 `Format-List` Cmdlet，此 Cmdlet 會顯示清單中每個 Cmdlet 的名稱和輸出類型。</span><span class="sxs-lookup"><span data-stu-id="5448b-175">Another pipeline operator sends the selected cmdlet objects to the `Format-List` cmdlet, which displays the name and output type of each cmdlet in a list.</span></span>

<span data-ttu-id="5448b-176">**CommandInfo** 物件的 **OutputType** 屬性只有在 Cmdlet 程式碼定義了 Cmdlet 的 **OutputType** 屬性時才會具有非 Null 的值。</span><span class="sxs-lookup"><span data-stu-id="5448b-176">The **OutputType** property of a **CommandInfo** object has a non-null value only when the cmdlet code defines the **OutputType** attribute for the cmdlet.</span></span>

### <span data-ttu-id="5448b-177">範例14：取得可採用特定物件類型做為輸入的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5448b-177">Example 14: Get cmdlets that take a specific object type as input</span></span>

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

<span data-ttu-id="5448b-178">此命令會尋找使用網路介面卡物件做為輸入項目的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5448b-178">This command finds cmdlets that take net adapter objects as input.</span></span> <span data-ttu-id="5448b-179">您可以使用此命令格式來尋找接受任一命令傳回之物件類型的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5448b-179">You can use this command format to find the cmdlets that accept the type of objects that any command returns.</span></span>

<span data-ttu-id="5448b-180">此命令會使用所有物件的 **PSTypeNames** 內建屬性，它會取得描述物件的類型。</span><span class="sxs-lookup"><span data-stu-id="5448b-180">The command uses the **PSTypeNames** intrinsic property of all objects, which gets the types that describe the object.</span></span> <span data-ttu-id="5448b-181">為取得網路介面卡的 **PSTypeNames** 屬性，而不是網路介面卡集合的 **PSTypeNames** 屬性，該命令會使用陣列標記法來取得 Cmdlet 傳回的第一個網路介面卡。</span><span class="sxs-lookup"><span data-stu-id="5448b-181">To get the **PSTypeNames** property of a net adapter, and not the **PSTypeNames** property of a collection of net adapters, the command uses array notation to get the first net adapter that the cmdlet returns.</span></span>

### <span data-ttu-id="5448b-182">範例15：使用模糊相符取得命令</span><span class="sxs-lookup"><span data-stu-id="5448b-182">Example 15: Get commands using a fuzzy match</span></span>

<span data-ttu-id="5448b-183">在此範例中，命令的名稱刻意以 ' commnd ' 的形式出現。</span><span class="sxs-lookup"><span data-stu-id="5448b-183">In this example, the name of the command deliberately has a typo as 'get-commnd'.</span></span>
<span data-ttu-id="5448b-184">使用 `-UseFuzzyMatching` 參數時，Cmdlet 判斷出最符合的 `Get-Command` 系統上的其他原生命令之後，會有相同的相符項。</span><span class="sxs-lookup"><span data-stu-id="5448b-184">Using the `-UseFuzzyMatching` switch, the cmdlet determined that the best match was `Get-Command` followed by other native commands on the system that were a similar match.</span></span>

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

## <span data-ttu-id="5448b-185">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5448b-185">PARAMETERS</span></span>

### <span data-ttu-id="5448b-186">-All</span><span class="sxs-lookup"><span data-stu-id="5448b-186">-All</span></span>

<span data-ttu-id="5448b-187">指出此 Cmdlet 會取得所有命令，包括具有相同名稱之相同類型的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-187">Indicates that this cmdlet gets all commands, including commands of the same type that have the same name.</span></span> <span data-ttu-id="5448b-188">根據預設， `Get-Command` 只會取得您輸入命令名稱時所執行的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-188">By default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="5448b-189">如需 PowerShell 在多個命令名稱相同時用來選取要執行之命令的方法的詳細資訊，請參閱 [about_Command_Precedence](About/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="5448b-189">For more information about the method that PowerShell uses to select the command to run when multiple commands have the same name, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>
<span data-ttu-id="5448b-190">如需模組合格命令名稱和執行命令的相關資訊（因為名稱衝突而不會預設執行），請參閱 [about_Modules](About/about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="5448b-190">For information about module-qualified command names and running commands that do not run by default because of a name conflict, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="5448b-191">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="5448b-191">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="5448b-192">在 Windows PowerShell 2.0 中， `Get-Command` 預設會取得所有命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-192">In Windows PowerShell 2.0, `Get-Command` gets all commands by default.</span></span>

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

### <span data-ttu-id="5448b-193">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="5448b-193">-ArgumentList</span></span>

<span data-ttu-id="5448b-194">指定引數的陣列。</span><span class="sxs-lookup"><span data-stu-id="5448b-194">Specifies an array of arguments.</span></span> <span data-ttu-id="5448b-195">當 Cmdlet 或函式搭配指定的參數使用時，此 Cmdlet 會取得 Cmdlet 或函式的相關資訊 ( 「引數」 ) 。</span><span class="sxs-lookup"><span data-stu-id="5448b-195">This cmdlet gets information about a cmdlet or function when it is used with the specified parameters ("arguments").</span></span> <span data-ttu-id="5448b-196">**ArgumentList** 的別名是 **Args** 。</span><span class="sxs-lookup"><span data-stu-id="5448b-196">The alias for **ArgumentList** is **Args** .</span></span>

<span data-ttu-id="5448b-197">若要偵測只有在使用特定的其他參數時才能使用的動態參數，請將 **ArgumentList** 的值設為觸發動態參數的參數。</span><span class="sxs-lookup"><span data-stu-id="5448b-197">To detect dynamic parameters that are available only when certain other parameters are used, set the value of **ArgumentList** to the parameters that trigger the dynamic parameters.</span></span>

<span data-ttu-id="5448b-198">若要偵測提供者新增至 Cmdlet 的動態參數，請將 **ArgumentList** 參數的值設定為提供者磁片磁碟機中的路徑，例如 WSMan：、HKLM：或 Cert：。</span><span class="sxs-lookup"><span data-stu-id="5448b-198">To detect the dynamic parameters that a provider adds to a cmdlet, set the value of the **ArgumentList** parameter to a path in the provider drive, such as WSMan:, HKLM:, or Cert:.</span></span> <span data-ttu-id="5448b-199">當命令為 PowerShell 提供者 Cmdlet 時，請在每個命令中只輸入一個路徑。</span><span class="sxs-lookup"><span data-stu-id="5448b-199">When the command is a PowerShell provider cmdlet, enter only one path in each command.</span></span> <span data-ttu-id="5448b-200">提供者 Cmdlet 只會傳回 **ArgumentList** 值的第一個路徑的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5448b-200">The provider cmdlets return only the dynamic parameters for the first path the value of **ArgumentList** .</span></span> <span data-ttu-id="5448b-201">如需提供者 Cmdlet 的詳細資訊，請參閱 [about_Providers](About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="5448b-201">For information about the provider cmdlets, see [about_Providers](About/about_Providers.md).</span></span>

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

### <span data-ttu-id="5448b-202">-CommandType</span><span class="sxs-lookup"><span data-stu-id="5448b-202">-CommandType</span></span>

<span data-ttu-id="5448b-203">指定此 Cmdlet 取得的命令類型。</span><span class="sxs-lookup"><span data-stu-id="5448b-203">Specifies the types of commands that this cmdlet gets.</span></span> <span data-ttu-id="5448b-204">輸入一或多個命令類型。</span><span class="sxs-lookup"><span data-stu-id="5448b-204">Enter one or more command types.</span></span> <span data-ttu-id="5448b-205">使用 **CommandType** 或它的別名 **Type** 。</span><span class="sxs-lookup"><span data-stu-id="5448b-205">Use **CommandType** or its alias, **Type** .</span></span> <span data-ttu-id="5448b-206">依預設，會 `Get-Command` 取得所有 Cmdlet、函式和別名。</span><span class="sxs-lookup"><span data-stu-id="5448b-206">By default, `Get-Command` gets all cmdlets, functions, and aliases.</span></span>

<span data-ttu-id="5448b-207">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="5448b-207">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5448b-208">別名。</span><span class="sxs-lookup"><span data-stu-id="5448b-208">Alias.</span></span> <span data-ttu-id="5448b-209">取得所有 PowerShell 命令的別名。</span><span class="sxs-lookup"><span data-stu-id="5448b-209">Gets the aliases of all PowerShell commands.</span></span> <span data-ttu-id="5448b-210">如需詳細資訊，請參閱 [about_Aliases](About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="5448b-210">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>
- <span data-ttu-id="5448b-211">全部。</span><span class="sxs-lookup"><span data-stu-id="5448b-211">All.</span></span> <span data-ttu-id="5448b-212">取得所有命令類型。</span><span class="sxs-lookup"><span data-stu-id="5448b-212">Gets all command types.</span></span> <span data-ttu-id="5448b-213">這個參數值相當於 `Get-Command *` 。</span><span class="sxs-lookup"><span data-stu-id="5448b-213">This parameter value is the equivalent of `Get-Command *`.</span></span>
- <span data-ttu-id="5448b-214">應用程式。</span><span class="sxs-lookup"><span data-stu-id="5448b-214">Application.</span></span> <span data-ttu-id="5448b-215">取得 **Path** 環境變數所列路徑中的非 PowerShell 檔案 ($env:p 路徑 a) ) ，包括 .txt、.exe 和 .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="5448b-215">Gets non-PowerShell files in paths listed in the **Path** environment variable ($env:path), including .txt, .exe, and .dll files.</span></span> <span data-ttu-id="5448b-216">如需 **Path** 環境變數的詳細資訊，請參閱 about_Environment_Variables。</span><span class="sxs-lookup"><span data-stu-id="5448b-216">For more information about the **Path** environment variable, see about_Environment_Variables.</span></span>
- <span data-ttu-id="5448b-217">Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5448b-217">Cmdlet.</span></span> <span data-ttu-id="5448b-218">取得所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5448b-218">Gets all cmdlets.</span></span>
- <span data-ttu-id="5448b-219">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="5448b-219">ExternalScript.</span></span> <span data-ttu-id="5448b-220">取得 **Path** 環境變數 ($env:path) 所列出之路徑中的所有 .ps1 檔案。</span><span class="sxs-lookup"><span data-stu-id="5448b-220">Gets all .ps1 files in the paths listed in the **Path** environment variable ($env:path).</span></span>
- <span data-ttu-id="5448b-221">篩選和函數。</span><span class="sxs-lookup"><span data-stu-id="5448b-221">Filter and Function.</span></span> <span data-ttu-id="5448b-222">取得所有 PowerShell advanced 和 simple 函數和篩選器。</span><span class="sxs-lookup"><span data-stu-id="5448b-222">Gets all PowerShell advanced and simple functions and filters.</span></span>
- <span data-ttu-id="5448b-223">指令碼：</span><span class="sxs-lookup"><span data-stu-id="5448b-223">Script.</span></span> <span data-ttu-id="5448b-224">取得所有指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="5448b-224">Gets all script blocks.</span></span> <span data-ttu-id="5448b-225">若要)  ( ps1 檔案取得 PowerShell 腳本，請使用 ExternalScript 值。</span><span class="sxs-lookup"><span data-stu-id="5448b-225">To get PowerShell scripts (.ps1 files), use the ExternalScript value.</span></span>

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

### <span data-ttu-id="5448b-226">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="5448b-226">-FullyQualifiedModule</span></span>

<span data-ttu-id="5448b-227">以 **ModuleSpecification** 物件的形式指定具有指定名稱的模組，請參閱 [ModuleSpecification (雜湊) 表](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)的「 **備註** 」一節中所述。</span><span class="sxs-lookup"><span data-stu-id="5448b-227">Specifies modules with names that are specified in the form of **ModuleSpecification** objects, described in the **Remarks** section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="5448b-228">例如， **FullyQualifiedModule** 參數會接受以下列其中一種格式指定的模組名稱：</span><span class="sxs-lookup"><span data-stu-id="5448b-228">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in one of the following formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="5448b-229">**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="5448b-229">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="5448b-230">您無法在與 **模組** 參數相同的命令中指定 **FullyQualifiedModule** 參數。</span><span class="sxs-lookup"><span data-stu-id="5448b-230">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="5448b-231">這兩個參數是互斥的。</span><span class="sxs-lookup"><span data-stu-id="5448b-231">The two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="5448b-232">-ListImported</span><span class="sxs-lookup"><span data-stu-id="5448b-232">-ListImported</span></span>

<span data-ttu-id="5448b-233">指出此 Cmdlet 只會取得目前會話中的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-233">Indicates that this cmdlet gets only commands in the current session.</span></span>

<span data-ttu-id="5448b-234">從 PowerShell 3.0 開始，根據預設， `Get-Command` 會取得所有已安裝的命令，包括（但不限於）目前會話中的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-234">Starting in PowerShell 3.0, by default, `Get-Command` gets all installed commands, including, but not limited to, the commands in the current session.</span></span> <span data-ttu-id="5448b-235">在 PowerShell 2.0 中，它只會取得目前會話中的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-235">In PowerShell 2.0, it gets only commands in the current session.</span></span>

<span data-ttu-id="5448b-236">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="5448b-236">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5448b-237">-Module</span><span class="sxs-lookup"><span data-stu-id="5448b-237">-Module</span></span>

<span data-ttu-id="5448b-238">指定模組的陣列。</span><span class="sxs-lookup"><span data-stu-id="5448b-238">Specifies an array of modules.</span></span> <span data-ttu-id="5448b-239">此 Cmdlet 會取得來自指定模組的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-239">This cmdlet gets the commands that came from the specified modules.</span></span>
<span data-ttu-id="5448b-240">輸入模組或模組物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="5448b-240">Enter the names of modules or module objects.</span></span>

<span data-ttu-id="5448b-241">此參數接受字串值，但此參數的值也可以是 **PSModuleInfo** 物件，例如和 Cmdlet 所傳回的物件 `Get-Module` `Import-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="5448b-241">This parameter takes string values, but the value of this parameter can also be a **PSModuleInfo** object, such as the objects that the `Get-Module` and `Import-PSSession` cmdlets return.</span></span>

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

### <span data-ttu-id="5448b-242">-Name</span><span class="sxs-lookup"><span data-stu-id="5448b-242">-Name</span></span>

<span data-ttu-id="5448b-243">指定名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="5448b-243">Specifies an array of names.</span></span> <span data-ttu-id="5448b-244">此 Cmdlet 只會取得具有指定之名稱的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-244">This cmdlet gets only commands that have the specified name.</span></span> <span data-ttu-id="5448b-245">輸入名稱或名稱模式。</span><span class="sxs-lookup"><span data-stu-id="5448b-245">Enter a name or name pattern.</span></span> <span data-ttu-id="5448b-246">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5448b-246">Wildcard characters are permitted.</span></span>

<span data-ttu-id="5448b-247">若要取得名稱相同的命令，請使用 **All** 參數。</span><span class="sxs-lookup"><span data-stu-id="5448b-247">To get commands that have the same name, use the **All** parameter.</span></span> <span data-ttu-id="5448b-248">當兩個命令的名稱相同時，根據預設，會 `Get-Command` 取得當您輸入命令名稱時所執行的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-248">When two commands have the same name, by default, `Get-Command` gets the command that runs when you type the command name.</span></span>

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

### <span data-ttu-id="5448b-249">-名詞</span><span class="sxs-lookup"><span data-stu-id="5448b-249">-Noun</span></span>

<span data-ttu-id="5448b-250">指定命令名詞的陣列。</span><span class="sxs-lookup"><span data-stu-id="5448b-250">Specifies an array of command nouns.</span></span> <span data-ttu-id="5448b-251">此 Cmdlet 會取得包含 Cmdlet、函式和別名的命令，這些命令的名稱包含指定的名詞。</span><span class="sxs-lookup"><span data-stu-id="5448b-251">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified noun.</span></span> <span data-ttu-id="5448b-252">輸入一或多個名詞或名詞模式。</span><span class="sxs-lookup"><span data-stu-id="5448b-252">Enter one or more nouns or noun patterns.</span></span> <span data-ttu-id="5448b-253">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5448b-253">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="5448b-254">-ParameterName</span><span class="sxs-lookup"><span data-stu-id="5448b-254">-ParameterName</span></span>

<span data-ttu-id="5448b-255">指定參數名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="5448b-255">Specifies an array of parameter names.</span></span> <span data-ttu-id="5448b-256">此 Cmdlet 會取得會話中具有指定參數的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-256">This cmdlet gets commands in the session that have the specified parameters.</span></span> <span data-ttu-id="5448b-257">輸入參數名稱或參數別名。</span><span class="sxs-lookup"><span data-stu-id="5448b-257">Enter parameter names or parameter aliases.</span></span> <span data-ttu-id="5448b-258">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5448b-258">Wildcard characters are supported.</span></span>

<span data-ttu-id="5448b-259">**ParameterName** 和 **ParameterType** 參數只會搜尋目前工作階段中的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-259">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="5448b-260">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="5448b-260">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5448b-261">-ParameterType</span><span class="sxs-lookup"><span data-stu-id="5448b-261">-ParameterType</span></span>

<span data-ttu-id="5448b-262">指定參數名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="5448b-262">Specifies an array of parameter names.</span></span> <span data-ttu-id="5448b-263">此 Cmdlet 會取得會話中具有指定類型參數的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-263">This cmdlet gets commands in the session that have parameters of the specified type.</span></span> <span data-ttu-id="5448b-264">輸入參數類型的完整名稱或部分名稱。</span><span class="sxs-lookup"><span data-stu-id="5448b-264">Enter the full name or partial name of a parameter type.</span></span> <span data-ttu-id="5448b-265">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5448b-265">Wildcard characters are supported.</span></span>

<span data-ttu-id="5448b-266">**ParameterName** 和 **ParameterType** 參數只會搜尋目前工作階段中的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-266">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="5448b-267">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="5448b-267">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5448b-268">-ShowCommandInfo</span><span class="sxs-lookup"><span data-stu-id="5448b-268">-ShowCommandInfo</span></span>

<span data-ttu-id="5448b-269">指出此 Cmdlet 會顯示命令資訊。</span><span class="sxs-lookup"><span data-stu-id="5448b-269">Indicates that this cmdlet displays command information.</span></span>

<span data-ttu-id="5448b-270">此參數是在 Windows PowerShell 5.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="5448b-270">This parameter was introduced in Windows PowerShell 5.0.</span></span>

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

### <span data-ttu-id="5448b-271">-語法</span><span class="sxs-lookup"><span data-stu-id="5448b-271">-Syntax</span></span>

<span data-ttu-id="5448b-272">指出此 Cmdlet 只會取得下列關於命令的指定資料：</span><span class="sxs-lookup"><span data-stu-id="5448b-272">Indicates that this cmdlet gets only the following specified data about the command:</span></span>

- <span data-ttu-id="5448b-273">別名。</span><span class="sxs-lookup"><span data-stu-id="5448b-273">Aliases.</span></span> <span data-ttu-id="5448b-274">取得標準名稱。</span><span class="sxs-lookup"><span data-stu-id="5448b-274">Gets the standard name.</span></span>
- <span data-ttu-id="5448b-275">Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5448b-275">Cmdlets.</span></span> <span data-ttu-id="5448b-276">取得語法。</span><span class="sxs-lookup"><span data-stu-id="5448b-276">Gets the syntax.</span></span>
- <span data-ttu-id="5448b-277">函數和篩選準則。</span><span class="sxs-lookup"><span data-stu-id="5448b-277">Functions and filters.</span></span> <span data-ttu-id="5448b-278">取得函式定義。</span><span class="sxs-lookup"><span data-stu-id="5448b-278">Gets the function definition.</span></span>
- <span data-ttu-id="5448b-279">腳本和應用程式或檔案。</span><span class="sxs-lookup"><span data-stu-id="5448b-279">Scripts and applications or files.</span></span> <span data-ttu-id="5448b-280">取得路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="5448b-280">Gets the path and filename.</span></span>

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

### <span data-ttu-id="5448b-281">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="5448b-281">-TotalCount</span></span>

<span data-ttu-id="5448b-282">指定要取得的命令數目。</span><span class="sxs-lookup"><span data-stu-id="5448b-282">Specifies the number of commands to get.</span></span> <span data-ttu-id="5448b-283">您可以使用此參數來限制命令的輸出。</span><span class="sxs-lookup"><span data-stu-id="5448b-283">You can use this parameter to limit the output of a command.</span></span>

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

### <span data-ttu-id="5448b-284">-UseFuzzyMatching</span><span class="sxs-lookup"><span data-stu-id="5448b-284">-UseFuzzyMatching</span></span>

<span data-ttu-id="5448b-285">表示在尋找命令時使用模糊比對演算法。</span><span class="sxs-lookup"><span data-stu-id="5448b-285">Indicates using a fuzzy matching algorithm when finding commands.</span></span> <span data-ttu-id="5448b-286">輸出的順序是從最接近的相符到最不相符的結果。</span><span class="sxs-lookup"><span data-stu-id="5448b-286">The order of the output is from closest match to least likely match.</span></span> <span data-ttu-id="5448b-287">萬用字元不應與模糊比對搭配使用，因為它會嘗試比對可能包含這些萬用字元的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-287">Wildcards should not be used with fuzzy matching as it will attempt to match commands that may contain those wildcard characters.</span></span>

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

### <span data-ttu-id="5448b-288">-Verb</span><span class="sxs-lookup"><span data-stu-id="5448b-288">-Verb</span></span>

<span data-ttu-id="5448b-289">指定命令動詞命令陣列。</span><span class="sxs-lookup"><span data-stu-id="5448b-289">Specifies an array of command verbs.</span></span> <span data-ttu-id="5448b-290">此 Cmdlet 會取得包含 Cmdlet、函式和別名的命令，這些命令的名稱包含指定的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-290">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified verb.</span></span> <span data-ttu-id="5448b-291">輸入一或多個動詞或動詞模式。</span><span class="sxs-lookup"><span data-stu-id="5448b-291">Enter one or more verbs or verb patterns.</span></span> <span data-ttu-id="5448b-292">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5448b-292">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="5448b-293">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5448b-293">CommonParameters</span></span>

<span data-ttu-id="5448b-294">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5448b-294">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5448b-295">如需詳細資訊，請參閱 [about_CommonParameters](About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="5448b-295">For more information, see [about_CommonParameters](About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5448b-296">輸入</span><span class="sxs-lookup"><span data-stu-id="5448b-296">INPUTS</span></span>

### <span data-ttu-id="5448b-297">System.String</span><span class="sxs-lookup"><span data-stu-id="5448b-297">System.String</span></span>

<span data-ttu-id="5448b-298">您可以透過管道將命令名稱傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5448b-298">You can pipe command names to this cmdlet.</span></span>

## <span data-ttu-id="5448b-299">輸出</span><span class="sxs-lookup"><span data-stu-id="5448b-299">OUTPUTS</span></span>

### <span data-ttu-id="5448b-300">CommandInfo。</span><span class="sxs-lookup"><span data-stu-id="5448b-300">System.Management.Automation.CommandInfo</span></span>

<span data-ttu-id="5448b-301">此 Cmdlet 會傳回衍生自 **CommandInfo** 類別的物件。</span><span class="sxs-lookup"><span data-stu-id="5448b-301">This cmdlet returns objects derived from the **CommandInfo** class.</span></span> <span data-ttu-id="5448b-302">傳回的物件類型取決於取得的命令類型 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="5448b-302">The type of object that is returned depends on the type of command that `Get-Command` gets.</span></span>

### <span data-ttu-id="5448b-303">System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="5448b-303">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="5448b-304">代表別名。</span><span class="sxs-lookup"><span data-stu-id="5448b-304">Represents aliases.</span></span>

### <span data-ttu-id="5448b-305">ApplicationInfo。</span><span class="sxs-lookup"><span data-stu-id="5448b-305">System.Management.Automation.ApplicationInfo</span></span>

<span data-ttu-id="5448b-306">代表應用程式和檔案。</span><span class="sxs-lookup"><span data-stu-id="5448b-306">Represents applications and files.</span></span>

### <span data-ttu-id="5448b-307">CmdletInfo。</span><span class="sxs-lookup"><span data-stu-id="5448b-307">System.Management.Automation.CmdletInfo</span></span>

<span data-ttu-id="5448b-308">代表 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5448b-308">Represents cmdlets.</span></span>

### <span data-ttu-id="5448b-309">System.Management.Automation.FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="5448b-309">System.Management.Automation.FunctionInfo</span></span>

<span data-ttu-id="5448b-310">表示函數和篩選準則。</span><span class="sxs-lookup"><span data-stu-id="5448b-310">Represents functions and filters.</span></span>

## <span data-ttu-id="5448b-311">注意</span><span class="sxs-lookup"><span data-stu-id="5448b-311">NOTES</span></span>

* <span data-ttu-id="5448b-312">當會話可以使用一個以上具有相同名稱的命令時，會傳回 `Get-Command` 當您輸入命令名稱時所執行的命令。</span><span class="sxs-lookup"><span data-stu-id="5448b-312">When more than one command that has the same name is available to the session, `Get-Command` returns the command that runs when you type the command name.</span></span> <span data-ttu-id="5448b-313">若要取得具有相同名稱的命令（依照執行順序列出），請使用 **All** 參數。</span><span class="sxs-lookup"><span data-stu-id="5448b-313">To get commands that have the same name, listed in run order, use the **All** parameter.</span></span> <span data-ttu-id="5448b-314">如需詳細資訊，請參閱 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="5448b-314">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>
* <span data-ttu-id="5448b-315">自動匯入模組時，效果與使用 `Import-Module` Cmdlet 相同。</span><span class="sxs-lookup"><span data-stu-id="5448b-315">When a module is imported automatically, the effect is the same as using the `Import-Module` cmdlet.</span></span> <span data-ttu-id="5448b-316">模組可以新增命令、類型及格式化檔案，並在工作階段中執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="5448b-316">The module can add commands, types and formatting files, and run scripts in the session.</span></span>
  <span data-ttu-id="5448b-317">若要啟用、停用及設定自動匯入模組，請使用 `$PSModuleAutoLoadingPreference` 喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="5448b-317">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="5448b-318">如需詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="5448b-318">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="5448b-319">相關連結</span><span class="sxs-lookup"><span data-stu-id="5448b-319">RELATED LINKS</span></span>

[<span data-ttu-id="5448b-320">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="5448b-320">Export-PSSession</span></span>](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[<span data-ttu-id="5448b-321">Get-Help</span><span class="sxs-lookup"><span data-stu-id="5448b-321">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="5448b-322">Get-Member</span><span class="sxs-lookup"><span data-stu-id="5448b-322">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="5448b-323">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="5448b-323">Get-PSDrive</span></span>](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[<span data-ttu-id="5448b-324">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="5448b-324">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="5448b-325">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="5448b-325">about_Command_Precedence</span></span>](About/about_Command_Precedence.md)
