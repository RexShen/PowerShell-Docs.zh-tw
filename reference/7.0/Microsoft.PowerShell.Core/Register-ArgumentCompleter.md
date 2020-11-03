---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-argumentcompleter?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ArgumentCompleter
ms.openlocfilehash: 0e0b5fcd99372d699bd6250383adc85b3a5f8847
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201567"
---
# <span data-ttu-id="df486-103">Register-ArgumentCompleter</span><span class="sxs-lookup"><span data-stu-id="df486-103">Register-ArgumentCompleter</span></span>

## <span data-ttu-id="df486-104">概要</span><span class="sxs-lookup"><span data-stu-id="df486-104">SYNOPSIS</span></span>

<span data-ttu-id="df486-105">註冊自訂引數完成器。</span><span class="sxs-lookup"><span data-stu-id="df486-105">Registers a custom argument completer.</span></span>

## <span data-ttu-id="df486-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="df486-106">SYNTAX</span></span>

### <span data-ttu-id="df486-107">NativeSet</span><span class="sxs-lookup"><span data-stu-id="df486-107">NativeSet</span></span>

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### <span data-ttu-id="df486-108">PowerShellSet</span><span class="sxs-lookup"><span data-stu-id="df486-108">PowerShellSet</span></span>

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="df486-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="df486-109">DESCRIPTION</span></span>

<span data-ttu-id="df486-110">此 `Register-ArgumentCompleter` Cmdlet 會註冊自訂引數完成器。</span><span class="sxs-lookup"><span data-stu-id="df486-110">The `Register-ArgumentCompleter` cmdlet registers a custom argument completer.</span></span> <span data-ttu-id="df486-111">引數完成器可讓您在執行時間為您指定的任何命令提供動態 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="df486-111">An argument completer allows you to provide dynamic tab completion, at run time for any command that you specify.</span></span>

## <span data-ttu-id="df486-112">範例</span><span class="sxs-lookup"><span data-stu-id="df486-112">EXAMPLES</span></span>

### <span data-ttu-id="df486-113">範例1：註冊自訂引數完成器</span><span class="sxs-lookup"><span data-stu-id="df486-113">Example 1: Register a custom argument completer</span></span>

<span data-ttu-id="df486-114">下列範例會針對 Cmdlet 的 **Id** 參數註冊引數完成器 `Set-TimeZone` 。</span><span class="sxs-lookup"><span data-stu-id="df486-114">The following example registers an argument completer for the **Id** parameter of the `Set-TimeZone` cmdlet.</span></span>

```powershell
$scriptBlock = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)

    (Get-TimeZone -ListAvailable).Id | Where-Object {
        $_ -like "$wordToComplete*"
    } | ForEach-Object {
          "'$_'"
    }
}
Register-ArgumentCompleter -CommandName Set-TimeZone -ParameterName Id -ScriptBlock $scriptBlock
```

<span data-ttu-id="df486-115">第一個命令會建立腳本區塊，該區塊會採用使用者按下 <kbd>Tab 鍵</kbd>時所傳入的必要參數。如需詳細資訊，請參閱 **ScriptBlock** 參數描述。</span><span class="sxs-lookup"><span data-stu-id="df486-115">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="df486-116">在腳本區塊中，會使用 Cmdlet 抓取 **識別碼** 的可用值 `Get-TimeZone` 。</span><span class="sxs-lookup"><span data-stu-id="df486-116">Within the script block, the available values for **Id** are retrieved using the `Get-TimeZone` cmdlet.</span></span> <span data-ttu-id="df486-117">每個時區的 **識別碼** 屬性都會輸送至 `Where-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="df486-117">The **Id** property for each Time Zone is piped to the `Where-Object` cmdlet.</span></span> <span data-ttu-id="df486-118">指令 `Where-Object` 程式會篩選出不是以提供的值開頭的任何識別碼 `$wordToComplete` ，代表使用者在按下 <kbd>Tab 鍵</kbd>之前所輸入的文字。篩選的識別碼會以管線傳送至 `For-EachObject` Cmdlet，此 Cmdlet 會將每個值括在引號中（如果值包含空格）。</span><span class="sxs-lookup"><span data-stu-id="df486-118">The `Where-Object` cmdlet filters out any ids that do not start with the value provided by `$wordToComplete`, which represents the text the user typed before they pressed <kbd>Tab</kbd>. The filtered ids are piped to the `For-EachObject` cmdlet which encloses each value in quotes, should the value contain spaces.</span></span>

<span data-ttu-id="df486-119">第二個命令會藉由傳遞 scriptblock、 **ParameterName** **識別碼** 和 **CommandName** 來註冊引數完成器 `Set-TimeZone` 。</span><span class="sxs-lookup"><span data-stu-id="df486-119">The second command registers the argument completer by passing the scriptblock, the **ParameterName** **Id** and the **CommandName** `Set-TimeZone`.</span></span>

### <span data-ttu-id="df486-120">範例2：將詳細資料新增至您的 tab 鍵自動完成值</span><span class="sxs-lookup"><span data-stu-id="df486-120">Example 2: Add details to your tab completion values</span></span>

<span data-ttu-id="df486-121">下列範例會覆寫 Cmdlet **Name** 參數的 tab 鍵自動完成 `Stop-Service` ，而且只會傳回執行中的服務。</span><span class="sxs-lookup"><span data-stu-id="df486-121">The following example overwrites tab completion for the **Name** parameter of the `Stop-Service` cmdlet and only returns running services.</span></span>

```powershell
$s = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)
    $services = Get-Service | Where-Object {$_.Status -eq "Running" -and $_.Name -like "$wordToComplete*"}
    $services | ForEach-Object {
        New-Object -Type System.Management.Automation.CompletionResult -ArgumentList $_.Name,
            $_.Name,
            "ParameterValue",
            $_.Name
    }
}
Register-ArgumentCompleter -CommandName Stop-Service -ParameterName Name -ScriptBlock $s
```

<span data-ttu-id="df486-122">第一個命令會建立腳本區塊，該區塊會採用使用者按下 <kbd>Tab 鍵</kbd>時所傳入的必要參數。如需詳細資訊，請參閱 **ScriptBlock** 參數描述。</span><span class="sxs-lookup"><span data-stu-id="df486-122">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="df486-123">在腳本區塊中，第一個命令會使用 Cmdlet 來抓取所有正在執行的服務 `Where-Object` 。</span><span class="sxs-lookup"><span data-stu-id="df486-123">Within the script block, the first command retrieves all running services using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="df486-124">這些服務會透過管道傳送至 `ForEach-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="df486-124">The services are piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="df486-125">此 `ForEach-Object` Cmdlet 會建立新的 [CompletionResult](/dotnet/api/system.management.automation.completionresult) 物件，並以管線變數) 所表示的目前服務 (名稱填入該物件 `$_.Name` 。</span><span class="sxs-lookup"><span data-stu-id="df486-125">The `ForEach-Object` cmdlet creates a new [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) object and populates it with the name of the current service (represented by the pipeline variable `$_.Name`).</span></span>

<span data-ttu-id="df486-126">**CompletionResult** 物件可讓您針對每個傳回的值提供其他詳細資料：</span><span class="sxs-lookup"><span data-stu-id="df486-126">The **CompletionResult** object allows you to provide additional details to each returned value:</span></span>

- <span data-ttu-id="df486-127">**completionText** (字串) -要當做自動完成結果使用的文字。</span><span class="sxs-lookup"><span data-stu-id="df486-127">**completionText** (String) - The text to be used as the auto completion result.</span></span> <span data-ttu-id="df486-128">這是傳送至命令的值。</span><span class="sxs-lookup"><span data-stu-id="df486-128">This is the value sent to the command.</span></span>
- <span data-ttu-id="df486-129">**listItemText** (字串) -要在清單中顯示的文字，例如使用者按下 <kbd>Ctrl</kbd> + <kbd>空格鍵</kbd>時。</span><span class="sxs-lookup"><span data-stu-id="df486-129">**listItemText** (String) - The text to be displayed in a list, such as when the user presses <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span> <span data-ttu-id="df486-130">這僅供顯示，且在選取時不會傳遞至命令。</span><span class="sxs-lookup"><span data-stu-id="df486-130">This is used for display only and is not passed to the command when selected.</span></span>
- <span data-ttu-id="df486-131">**resultType** ( [CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) -完成結果的類型。</span><span class="sxs-lookup"><span data-stu-id="df486-131">**resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) - The type of completion result.</span></span>
- <span data-ttu-id="df486-132">**工具提示** (字串) -工具提示的文字，其中包含有關物件的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="df486-132">**toolTip** (String) - The text for the tooltip with details to be displayed about the object.</span></span>
  <span data-ttu-id="df486-133">當使用者在按下<kbd>Ctrl</kbd>空格鍵之後選取專案時，就會看到這種情況 + <kbd> </kbd>。</span><span class="sxs-lookup"><span data-stu-id="df486-133">This is visible when the user selects an item after pressing <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span>

<span data-ttu-id="df486-134">最後一個命令會示範已停止的服務仍然可以手動傳遞給 `Stop-Service` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="df486-134">The last command demonstrates that stopped services can still be passed in manually to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="df486-135">Tab 鍵自動完成是唯一受影響的層面。</span><span class="sxs-lookup"><span data-stu-id="df486-135">The tab completion is the only aspect affected.</span></span>

### <span data-ttu-id="df486-136">範例3：註冊自訂原生引數完成器</span><span class="sxs-lookup"><span data-stu-id="df486-136">Example 3: Register a custom Native argument completer</span></span>

<span data-ttu-id="df486-137">您可以使用 **原生** 參數來提供原生命令的 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="df486-137">You can use the **Native** parameter to provide tab-completion for a native command.</span></span> <span data-ttu-id="df486-138">下列範例會將命令列介面的 tab 鍵自動完成新增 `dotnet` (CLI) 。</span><span class="sxs-lookup"><span data-stu-id="df486-138">The following example adds tab-completion for the `dotnet` Command Line Interface (CLI).</span></span>

> [!NOTE]
> <span data-ttu-id="df486-139">此 `dotnet complete` 命令僅適用于2.0 版和更高版本的 dotnet cli。</span><span class="sxs-lookup"><span data-stu-id="df486-139">The `dotnet complete` command is only available in version 2.0 and greater of the dotnet cli.</span></span>

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

<span data-ttu-id="df486-140">第一個命令會建立腳本區塊，該區塊會採用使用者按下 <kbd>Tab 鍵</kbd>時所傳入的必要參數。如需詳細資訊，請參閱 **ScriptBlock** 參數描述。</span><span class="sxs-lookup"><span data-stu-id="df486-140">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="df486-141">在腳本區塊中， `dotnet complete` 命令是用來執行 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="df486-141">Within the script block, the `dotnet complete` command is used to perform the tab completion.</span></span>
<span data-ttu-id="df486-142">結果會輸送到 Cmdlet，以 `ForEach-Object` 使用 [CompletionResult](/dotnet/api/system.management.automation.completionresult)類別的 **新** 靜態方法來為每個值建立新的 **CompletionResult** 物件。</span><span class="sxs-lookup"><span data-stu-id="df486-142">The results are piped to the `ForEach-Object` cmdlet which use the **new** static method of the [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) class to create a new **CompletionResult** object for each value.</span></span>

## <span data-ttu-id="df486-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="df486-143">PARAMETERS</span></span>

### <span data-ttu-id="df486-144">-CommandName</span><span class="sxs-lookup"><span data-stu-id="df486-144">-CommandName</span></span>

<span data-ttu-id="df486-145">以陣列的形式指定命令的名稱。</span><span class="sxs-lookup"><span data-stu-id="df486-145">Specifies the name of the commands as an array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NativeSet, PowerShellSet
Aliases:

Required: True (NativeSet), False (PowerShellSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="df486-146">-原生</span><span class="sxs-lookup"><span data-stu-id="df486-146">-Native</span></span>

<span data-ttu-id="df486-147">表示引數完成器適用于 PowerShell 無法完成參數名稱的原生命令。</span><span class="sxs-lookup"><span data-stu-id="df486-147">Indicates that the argument completer is for a native command where PowerShell cannot complete parameter names.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NativeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="df486-148">-ParameterName</span><span class="sxs-lookup"><span data-stu-id="df486-148">-ParameterName</span></span>

<span data-ttu-id="df486-149">指定要完成其引數的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="df486-149">Specifies the name of the parameter whose argument is being completed.</span></span> <span data-ttu-id="df486-150">指定的參數名稱不可以是列舉值，例如 Cmdlet 的 **ForegroundColor** 參數 `Write-Host` 。</span><span class="sxs-lookup"><span data-stu-id="df486-150">The parameter name specified cannot be an enumerated value, such as the **ForegroundColor** parameter of the `Write-Host` cmdlet.</span></span>

<span data-ttu-id="df486-151">如需列舉的詳細資訊，請參閱 [about_Enum](./About/about_Enum.md)。</span><span class="sxs-lookup"><span data-stu-id="df486-151">For more information on enums, see [about_Enum](./About/about_Enum.md).</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="df486-152">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="df486-152">-ScriptBlock</span></span>

<span data-ttu-id="df486-153">指定要執行的命令以執行 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="df486-153">Specifies the commands to run to perform tab completion.</span></span> <span data-ttu-id="df486-154">您提供的腳本區塊應該會傳回完成輸入的值。</span><span class="sxs-lookup"><span data-stu-id="df486-154">The script block you provide should return the values that complete the input.</span></span> <span data-ttu-id="df486-155">腳本區塊必須使用管線 (`ForEach-Object` 、等等 `Where-Object` ) 或另一個適當的方法來展開值。</span><span class="sxs-lookup"><span data-stu-id="df486-155">The script block must unroll the values using the pipeline (`ForEach-Object`, `Where-Object`, etc.), or another suitable method.</span></span> <span data-ttu-id="df486-156">傳回值陣列會導致 PowerShell 將整個陣列視為 **一個** tab 鍵自動完成值。</span><span class="sxs-lookup"><span data-stu-id="df486-156">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="df486-157">腳本區塊必須以下列指定的順序接受下列參數。</span><span class="sxs-lookup"><span data-stu-id="df486-157">The script block must accept the following parameters in the order specified below.</span></span> <span data-ttu-id="df486-158">參數的名稱並不重要，因為 PowerShell 會依位置傳遞值。</span><span class="sxs-lookup"><span data-stu-id="df486-158">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="df486-159">`$commandName` (位置 0) -此參數會設定為腳本區塊提供 tab 鍵自動完成之命令的名稱。</span><span class="sxs-lookup"><span data-stu-id="df486-159">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="df486-160">`$parameterName` (位置 1) -此參數會設定為其值需要 tab 鍵自動完成的參數。</span><span class="sxs-lookup"><span data-stu-id="df486-160">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="df486-161">`$wordToComplete` (位置 2) -此參數會設定為使用者在按下 <kbd>Tab 鍵</kbd>之前所提供的值。您的腳本區塊應該使用此值來判斷 tab 鍵自動完成值。</span><span class="sxs-lookup"><span data-stu-id="df486-161">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="df486-162">`$commandAst` (位置 3) -這個參數會設定為目前輸入行 (AST) 的抽象語法樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="df486-162">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="df486-163">如需詳細資訊，請參閱 [Ast 類別](/dotnet/api/system.management.automation.language.ast)。</span><span class="sxs-lookup"><span data-stu-id="df486-163">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="df486-164">`$fakeBoundParameters` (位置 4) - `$PSBoundParameters` 在使用者按下索引標籤之前，此參數會設定為包含 Cmdlet 之<kbd>Tab</kbd>的雜湊表。如需詳細資訊，請參閱[about_Automatic_Variables](./About/about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="df486-164">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](./About/about_Automatic_Variables.md).</span></span>

<span data-ttu-id="df486-165">當您指定 **原生** 參數時，腳本區塊必須以指定的順序採用下列參數。</span><span class="sxs-lookup"><span data-stu-id="df486-165">When you specify the **Native** parameter, the script block must take the following parameters in the specified order.</span></span> <span data-ttu-id="df486-166">參數的名稱並不重要，因為 PowerShell 會依位置傳遞值。</span><span class="sxs-lookup"><span data-stu-id="df486-166">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="df486-167">`$wordToComplete` (位置 0) -此參數會設定為使用者在按下 <kbd>Tab 鍵</kbd>之前所提供的值。您的腳本區塊應該使用此值來判斷 tab 鍵自動完成值。</span><span class="sxs-lookup"><span data-stu-id="df486-167">`$wordToComplete` (Position 0) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="df486-168">`$commandAst` (位置 1) -這個參數會設定為目前輸入行 (AST) 的抽象語法樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="df486-168">`$commandAst` (Position 1) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="df486-169">如需詳細資訊，請參閱 [Ast 類別](/dotnet/api/system.management.automation.language.ast)。</span><span class="sxs-lookup"><span data-stu-id="df486-169">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="df486-170">`$cursorPosition` (位置 2) -當使用者 <kbd>按下索引</kbd>標籤時，此參數會設定為游標的位置。</span><span class="sxs-lookup"><span data-stu-id="df486-170">`$cursorPosition` (Position 2) - This parameter is set to the position of the cursor when the user pressed <kbd>Tab</kbd>.</span></span>

<span data-ttu-id="df486-171">您也可以將 **ArgumentCompleter** 提供為參數屬性。</span><span class="sxs-lookup"><span data-stu-id="df486-171">You can also provide an **ArgumentCompleter** as a parameter attribute.</span></span> <span data-ttu-id="df486-172">如需詳細資訊，請參閱 [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="df486-172">For more information, see [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="df486-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="df486-173">CommonParameters</span></span>

<span data-ttu-id="df486-174">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="df486-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="df486-175">如需詳細資訊，請參閱 [about_CommonParameters](./About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="df486-175">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="df486-176">輸入</span><span class="sxs-lookup"><span data-stu-id="df486-176">INPUTS</span></span>

### <span data-ttu-id="df486-177">無</span><span class="sxs-lookup"><span data-stu-id="df486-177">None</span></span>

<span data-ttu-id="df486-178">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="df486-178">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="df486-179">輸出</span><span class="sxs-lookup"><span data-stu-id="df486-179">OUTPUTS</span></span>

### <span data-ttu-id="df486-180">無</span><span class="sxs-lookup"><span data-stu-id="df486-180">None</span></span>

<span data-ttu-id="df486-181">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="df486-181">This cmdlet returns no output.</span></span>

## <span data-ttu-id="df486-182">注意</span><span class="sxs-lookup"><span data-stu-id="df486-182">NOTES</span></span>

## <span data-ttu-id="df486-183">相關連結</span><span class="sxs-lookup"><span data-stu-id="df486-183">RELATED LINKS</span></span>
