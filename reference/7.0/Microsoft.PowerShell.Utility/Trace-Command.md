---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/trace-command?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Trace-Command
ms.openlocfilehash: f3f9e47ac6d969dc08518bf97bb87699fb04ade8
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201540"
---
# <span data-ttu-id="af8e3-103">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="af8e3-103">Trace-Command</span></span>

## <span data-ttu-id="af8e3-104">概要</span><span class="sxs-lookup"><span data-stu-id="af8e3-104">SYNOPSIS</span></span>
<span data-ttu-id="af8e3-105">設定並啟動指定運算式或命令的追蹤。</span><span class="sxs-lookup"><span data-stu-id="af8e3-105">Configures and starts a trace of the specified expression or command.</span></span>

## <span data-ttu-id="af8e3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="af8e3-106">SYNTAX</span></span>

### <span data-ttu-id="af8e3-107">expressionSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="af8e3-107">expressionSet (Default)</span></span>

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Expression] <ScriptBlock> [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force] [-Debugger]
 [-PSHost] [<CommonParameters>]
```

### <span data-ttu-id="af8e3-108">commandSet</span><span class="sxs-lookup"><span data-stu-id="af8e3-108">commandSet</span></span>

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Command] <String> [-ArgumentList <Object[]>] [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force]
 [-Debugger] [-PSHost] [<CommonParameters>]
```

## <span data-ttu-id="af8e3-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="af8e3-109">DESCRIPTION</span></span>
<span data-ttu-id="af8e3-110">指令程式會設定 `Trace-Command` 並啟動指定運算式或命令的追蹤。</span><span class="sxs-lookup"><span data-stu-id="af8e3-110">The `Trace-Command` cmdlet configures and starts a trace of the specified expression or command.</span></span>
<span data-ttu-id="af8e3-111">它的運作方式類似 Set-TraceSource，但只適用於指定的命令。</span><span class="sxs-lookup"><span data-stu-id="af8e3-111">It works like Set-TraceSource, except that it applies only to the specified command.</span></span>

## <span data-ttu-id="af8e3-112">範例</span><span class="sxs-lookup"><span data-stu-id="af8e3-112">EXAMPLES</span></span>

### <span data-ttu-id="af8e3-113">範例1：追蹤元資料處理、參數系結和運算式</span><span class="sxs-lookup"><span data-stu-id="af8e3-113">Example 1: Trace metadata processing, parameter binding, and an expression</span></span>

<span data-ttu-id="af8e3-114">此範例會開始追蹤元資料處理、參數系結，以及建立和終結運算式的 Cmdlet `Get-Process Notepad` 。</span><span class="sxs-lookup"><span data-stu-id="af8e3-114">This example starts a trace of metadata processing, parameter binding, and cmdlet creation and destruction of the `Get-Process Notepad` expression.</span></span>

```powershell
Trace-Command -Name metadata,parameterbinding,cmdlet -Expression {Get-Process Notepad} -PSHost
```

<span data-ttu-id="af8e3-115">它會使用 **Name** 參數來指定追蹤來源，使用 **Expression** 參數指定命令，並使用 **PSHost** 參數將輸出傳送至主控台。</span><span class="sxs-lookup"><span data-stu-id="af8e3-115">It uses the **Name** parameter to specify the trace sources, the **Expression** parameter to specify the command, and the **PSHost** parameter to send the output to the console.</span></span> <span data-ttu-id="af8e3-116">因為它並未指定任何追蹤選項或接聽程式選項，所以此命令會使用預設值：</span><span class="sxs-lookup"><span data-stu-id="af8e3-116">Because it does not specify any tracing options or listener options, the command uses the defaults:</span></span>

- <span data-ttu-id="af8e3-117">所有追蹤選項</span><span class="sxs-lookup"><span data-stu-id="af8e3-117">All for the tracing options</span></span>
- <span data-ttu-id="af8e3-118">無接聽程式選項</span><span class="sxs-lookup"><span data-stu-id="af8e3-118">None for the listener options</span></span>

### <span data-ttu-id="af8e3-119">範例2：追蹤 ParameterBinding 作業的動作</span><span class="sxs-lookup"><span data-stu-id="af8e3-119">Example 2: Trace the actions of ParameterBinding operations</span></span>

<span data-ttu-id="af8e3-120">此範例會追蹤 PowerShell 的 **ParameterBinding** 作業動作，同時處理 `Get-Alias` 接受管線輸入的運算式。</span><span class="sxs-lookup"><span data-stu-id="af8e3-120">This example traces the actions of the **ParameterBinding** operations of PowerShell while it processes a `Get-Alias` expression that takes input from the pipeline.</span></span>

```powershell
$A = "i*"
Trace-Command ParameterBinding {Get-Alias $Input} -PSHost -InputObject $A
```

<span data-ttu-id="af8e3-121">在中 `Trace-Command` ， **InputObject** 參數會將物件傳遞至追蹤期間正在處理的運算式。</span><span class="sxs-lookup"><span data-stu-id="af8e3-121">In `Trace-Command`, the **InputObject** parameter passes an object to the expression that is being processed during the trace.</span></span>

<span data-ttu-id="af8e3-122">第一個命令會將字串儲存 `i*` 在 `$A` 變數中。</span><span class="sxs-lookup"><span data-stu-id="af8e3-122">The first command stores the string `i*` in the `$A` variable.</span></span> <span data-ttu-id="af8e3-123">第二個命令會使用 `Trace-Command` Cmdlet 搭配 ParameterBinding 追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="af8e3-123">The second command uses the `Trace-Command` cmdlet with the ParameterBinding trace source.</span></span> <span data-ttu-id="af8e3-124">**PSHost** 參數會將輸出傳送至主控台。</span><span class="sxs-lookup"><span data-stu-id="af8e3-124">The **PSHost** parameter sends the output to the console.</span></span>

<span data-ttu-id="af8e3-125">正在處理的運算式是 `Get-Alias $Input` `$Input` 與 **InputObject** 參數相關聯的變數。</span><span class="sxs-lookup"><span data-stu-id="af8e3-125">The expression being processed is `Get-Alias $Input`, where the `$Input` variable is associated with the **InputObject** parameter.</span></span> <span data-ttu-id="af8e3-126">**InputObject** 參數會將變數傳遞 `$A` 給運算式。</span><span class="sxs-lookup"><span data-stu-id="af8e3-126">The **InputObject** parameter passes the variable `$A` to the expression.</span></span> <span data-ttu-id="af8e3-127">實際上，追蹤期間處理的命令為 `Get-Alias -InputObject $A" or "$A | Get-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="af8e3-127">In effect, the command being processed during the trace is `Get-Alias -InputObject $A" or "$A | Get-Alias`.</span></span>

## <span data-ttu-id="af8e3-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="af8e3-128">PARAMETERS</span></span>

### <span data-ttu-id="af8e3-129">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="af8e3-129">-ArgumentList</span></span>

<span data-ttu-id="af8e3-130">指定要追蹤之命令的參數和參數值。</span><span class="sxs-lookup"><span data-stu-id="af8e3-130">Specifies the parameters and parameter values for the command being traced.</span></span> <span data-ttu-id="af8e3-131">**ArgumentList** 的別名是 **Args** 。</span><span class="sxs-lookup"><span data-stu-id="af8e3-131">The alias for **ArgumentList** is **Args** .</span></span> <span data-ttu-id="af8e3-132">此功能特別適用於動態參數偵錯。</span><span class="sxs-lookup"><span data-stu-id="af8e3-132">This feature is especially useful for debugging dynamic parameters.</span></span>

<span data-ttu-id="af8e3-133">如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="af8e3-133">For more information about the behavior of **ArgumentList** , see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: commandSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af8e3-134">-Command</span><span class="sxs-lookup"><span data-stu-id="af8e3-134">-Command</span></span>

<span data-ttu-id="af8e3-135">指定追蹤期間處理的命令。</span><span class="sxs-lookup"><span data-stu-id="af8e3-135">Specifies a command that is being processed during the trace.</span></span>

```yaml
Type: System.String
Parameter Sets: commandSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af8e3-136">-Debugger</span><span class="sxs-lookup"><span data-stu-id="af8e3-136">-Debugger</span></span>

<span data-ttu-id="af8e3-137">指出此 Cmdlet 會將追蹤輸出傳送至偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="af8e3-137">Indicates that the cmdlet sends the trace output to the debugger.</span></span> <span data-ttu-id="af8e3-138">您可以在任何使用者模式或核心模式的偵錯工具或 Visual Studio 中檢視輸出。</span><span class="sxs-lookup"><span data-stu-id="af8e3-138">You can view the output in any user-mode or kernel mode debugger or in Visual Studio.</span></span> <span data-ttu-id="af8e3-139">這個參數也會選取預設的追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="af8e3-139">This parameter also selects the default trace listener.</span></span>

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

### <span data-ttu-id="af8e3-140">-Expression</span><span class="sxs-lookup"><span data-stu-id="af8e3-140">-Expression</span></span>

<span data-ttu-id="af8e3-141">指定追蹤期間處理的運算式。</span><span class="sxs-lookup"><span data-stu-id="af8e3-141">Specifies the expression that is being processed during the trace.</span></span> <span data-ttu-id="af8e3-142">以大括弧括住運算式 (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="af8e3-142">Enclose the expression in braces (`{}`).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: expressionSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af8e3-143">-FilePath</span><span class="sxs-lookup"><span data-stu-id="af8e3-143">-FilePath</span></span>

<span data-ttu-id="af8e3-144">指定 Cmdlet 將追蹤輸出傳送至其中的檔案。</span><span class="sxs-lookup"><span data-stu-id="af8e3-144">Specifies a file that the cmdlet sends the trace output to.</span></span> <span data-ttu-id="af8e3-145">這個參數也會選取檔案追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="af8e3-145">This parameter also selects the file trace listener.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af8e3-146">-Force</span><span class="sxs-lookup"><span data-stu-id="af8e3-146">-Force</span></span>

<span data-ttu-id="af8e3-147">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="af8e3-147">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="af8e3-148">搭配 **FilePath** 參數使用。</span><span class="sxs-lookup"><span data-stu-id="af8e3-148">Used with the **FilePath** parameter.</span></span> <span data-ttu-id="af8e3-149">即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="af8e3-149">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="af8e3-150">-InputObject</span><span class="sxs-lookup"><span data-stu-id="af8e3-150">-InputObject</span></span>

<span data-ttu-id="af8e3-151">指定在追蹤期間處理的運算式的輸入。</span><span class="sxs-lookup"><span data-stu-id="af8e3-151">Specifies input to the expression that is being processed during the trace.</span></span> <span data-ttu-id="af8e3-152">您可以輸入代表運算式接受之輸入的變數，或透過管線傳送物件。</span><span class="sxs-lookup"><span data-stu-id="af8e3-152">You can enter a variable that represents the input that the expression accepts, or pass an object through the pipeline.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="af8e3-153">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="af8e3-153">-ListenerOption</span></span>

<span data-ttu-id="af8e3-154">在輸出中，將選擇性資料指定為每個追蹤訊息的前置詞。</span><span class="sxs-lookup"><span data-stu-id="af8e3-154">Specifies optional data to the prefix of each trace message in the output.</span></span> <span data-ttu-id="af8e3-155">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="af8e3-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="af8e3-156">無</span><span class="sxs-lookup"><span data-stu-id="af8e3-156">None</span></span>
- <span data-ttu-id="af8e3-157">LogicalOperationStack</span><span class="sxs-lookup"><span data-stu-id="af8e3-157">LogicalOperationStack</span></span>
- <span data-ttu-id="af8e3-158">Datetime</span><span class="sxs-lookup"><span data-stu-id="af8e3-158">DateTime</span></span>
- <span data-ttu-id="af8e3-159">時間戳記</span><span class="sxs-lookup"><span data-stu-id="af8e3-159">Timestamp</span></span>
- <span data-ttu-id="af8e3-160">ProcessId</span><span class="sxs-lookup"><span data-stu-id="af8e3-160">ProcessId</span></span>
- <span data-ttu-id="af8e3-161">ThreadId</span><span class="sxs-lookup"><span data-stu-id="af8e3-161">ThreadId</span></span>
- <span data-ttu-id="af8e3-162">呼叫堆疊</span><span class="sxs-lookup"><span data-stu-id="af8e3-162">Callstack</span></span>

<span data-ttu-id="af8e3-163">預設值為 **None** 。</span><span class="sxs-lookup"><span data-stu-id="af8e3-163">**None** is the default.</span></span>

<span data-ttu-id="af8e3-164">如果要指定多個選項，請以逗點加以區隔，但不含空格，並將其括在引號中，例如 "ProcessID,ThreadID"。</span><span class="sxs-lookup"><span data-stu-id="af8e3-164">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "ProcessID,ThreadID".</span></span>

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af8e3-165">-Name</span><span class="sxs-lookup"><span data-stu-id="af8e3-165">-Name</span></span>

<span data-ttu-id="af8e3-166">指定要追蹤的 PowerShell 元件陣列。</span><span class="sxs-lookup"><span data-stu-id="af8e3-166">Specifies an array of PowerShell components that are traced.</span></span> <span data-ttu-id="af8e3-167">輸入每個元件的追蹤來源名稱。</span><span class="sxs-lookup"><span data-stu-id="af8e3-167">Enter the name of the trace source of each component.</span></span> <span data-ttu-id="af8e3-168">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="af8e3-168">Wildcards are permitted.</span></span> <span data-ttu-id="af8e3-169">若要尋找電腦上的追蹤來源，請輸入 `Get-TraceSource` 。</span><span class="sxs-lookup"><span data-stu-id="af8e3-169">To find the trace sources on your computer, type `Get-TraceSource`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af8e3-170">-Option</span><span class="sxs-lookup"><span data-stu-id="af8e3-170">-Option</span></span>

<span data-ttu-id="af8e3-171">決定追蹤的事件類型。</span><span class="sxs-lookup"><span data-stu-id="af8e3-171">Determines the type of events that are traced.</span></span> <span data-ttu-id="af8e3-172">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="af8e3-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="af8e3-173">無</span><span class="sxs-lookup"><span data-stu-id="af8e3-173">None</span></span>
- <span data-ttu-id="af8e3-174">建構函式</span><span class="sxs-lookup"><span data-stu-id="af8e3-174">Constructor</span></span>
- <span data-ttu-id="af8e3-175">處置</span><span class="sxs-lookup"><span data-stu-id="af8e3-175">Dispose</span></span>
- <span data-ttu-id="af8e3-176">完成項</span><span class="sxs-lookup"><span data-stu-id="af8e3-176">Finalizer</span></span>
- <span data-ttu-id="af8e3-177">方法</span><span class="sxs-lookup"><span data-stu-id="af8e3-177">Method</span></span>
- <span data-ttu-id="af8e3-178">屬性</span><span class="sxs-lookup"><span data-stu-id="af8e3-178">Property</span></span>
- <span data-ttu-id="af8e3-179">委派</span><span class="sxs-lookup"><span data-stu-id="af8e3-179">Delegates</span></span>
- <span data-ttu-id="af8e3-180">事件</span><span class="sxs-lookup"><span data-stu-id="af8e3-180">Events</span></span>
- <span data-ttu-id="af8e3-181">例外狀況</span><span class="sxs-lookup"><span data-stu-id="af8e3-181">Exception</span></span>
- <span data-ttu-id="af8e3-182">鎖定</span><span class="sxs-lookup"><span data-stu-id="af8e3-182">Lock</span></span>
- <span data-ttu-id="af8e3-183">錯誤</span><span class="sxs-lookup"><span data-stu-id="af8e3-183">Error</span></span>
- <span data-ttu-id="af8e3-184">Errors</span><span class="sxs-lookup"><span data-stu-id="af8e3-184">Errors</span></span>
- <span data-ttu-id="af8e3-185">警告</span><span class="sxs-lookup"><span data-stu-id="af8e3-185">Warning</span></span>
- <span data-ttu-id="af8e3-186">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="af8e3-186">Verbose</span></span>
- <span data-ttu-id="af8e3-187">WriteLine</span><span class="sxs-lookup"><span data-stu-id="af8e3-187">WriteLine</span></span>
- <span data-ttu-id="af8e3-188">資料</span><span class="sxs-lookup"><span data-stu-id="af8e3-188">Data</span></span>
- <span data-ttu-id="af8e3-189">範圍</span><span class="sxs-lookup"><span data-stu-id="af8e3-189">Scope</span></span>
- <span data-ttu-id="af8e3-190">ExecutionFlow</span><span class="sxs-lookup"><span data-stu-id="af8e3-190">ExecutionFlow</span></span>
- <span data-ttu-id="af8e3-191">Assert</span><span class="sxs-lookup"><span data-stu-id="af8e3-191">Assert</span></span>
- <span data-ttu-id="af8e3-192">全部</span><span class="sxs-lookup"><span data-stu-id="af8e3-192">All</span></span>

<span data-ttu-id="af8e3-193">All 為預設值。</span><span class="sxs-lookup"><span data-stu-id="af8e3-193">All is the default.</span></span>

<span data-ttu-id="af8e3-194">下列的值為其他值的組合：</span><span class="sxs-lookup"><span data-stu-id="af8e3-194">The following values are combinations of other values:</span></span>

- <span data-ttu-id="af8e3-195">ExecutionFlow：(Constructor、Dispose、Finalizer、Method、Delegates、Events 及 Scope)</span><span class="sxs-lookup"><span data-stu-id="af8e3-195">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, Delegates, Events, and Scope)</span></span>
- <span data-ttu-id="af8e3-196">Data：(Constructor、Dispose、Finalizer、Property、Verbose 及 WriteLine)</span><span class="sxs-lookup"><span data-stu-id="af8e3-196">Data: (Constructor, Dispose, Finalizer, Property, Verbose, and WriteLine)</span></span>
- <span data-ttu-id="af8e3-197">Errors：(Error 和 Exception)。</span><span class="sxs-lookup"><span data-stu-id="af8e3-197">Errors: (Error and Exception).</span></span>

<span data-ttu-id="af8e3-198">如果要指定多個選項，請以逗點加以區隔，但不含空格，並將其括在引號中，例如 "Constructor,Dispose"。</span><span class="sxs-lookup"><span data-stu-id="af8e3-198">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "Constructor,Dispose".</span></span>

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af8e3-199">-PSHost</span><span class="sxs-lookup"><span data-stu-id="af8e3-199">-PSHost</span></span>

<span data-ttu-id="af8e3-200">指出此 Cmdlet 會將追蹤輸出傳送至 PowerShell 主機。</span><span class="sxs-lookup"><span data-stu-id="af8e3-200">Indicates that the cmdlet sends the trace output to the PowerShell host.</span></span> <span data-ttu-id="af8e3-201">這個參數也會選取 PSHost 追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="af8e3-201">This parameter also selects the PSHost trace listener.</span></span>

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

### <span data-ttu-id="af8e3-202">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="af8e3-202">CommonParameters</span></span>

<span data-ttu-id="af8e3-203">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="af8e3-203">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="af8e3-204">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="af8e3-204">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="af8e3-205">輸入</span><span class="sxs-lookup"><span data-stu-id="af8e3-205">INPUTS</span></span>

### <span data-ttu-id="af8e3-206">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="af8e3-206">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="af8e3-207">您可以透過管線將表示輸入的物件傳送至運算式 `Trace-Command` 。</span><span class="sxs-lookup"><span data-stu-id="af8e3-207">You can pipe objects that represent input to the expression to `Trace-Command`.</span></span>

## <span data-ttu-id="af8e3-208">輸出</span><span class="sxs-lookup"><span data-stu-id="af8e3-208">OUTPUTS</span></span>

### <span data-ttu-id="af8e3-209">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="af8e3-209">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="af8e3-210">在偵錯資料流中傳回命令追蹤。</span><span class="sxs-lookup"><span data-stu-id="af8e3-210">Returns the command trace in the debug stream.</span></span>

## <span data-ttu-id="af8e3-211">注意</span><span class="sxs-lookup"><span data-stu-id="af8e3-211">NOTES</span></span>

- <span data-ttu-id="af8e3-212">追蹤是開發人員用來偵錯及改善程式的方法。</span><span class="sxs-lookup"><span data-stu-id="af8e3-212">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="af8e3-213">當進行追蹤時，程式會產生有關內部處理中每個步驟的詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="af8e3-213">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

- <span data-ttu-id="af8e3-214">PowerShell 追蹤 Cmdlet 是設計來協助 PowerShell 開發人員，但它們可供所有使用者使用。</span><span class="sxs-lookup"><span data-stu-id="af8e3-214">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span> <span data-ttu-id="af8e3-215">它們可讓您監視殼層功能的幾乎各個層面。</span><span class="sxs-lookup"><span data-stu-id="af8e3-215">They let you monitor nearly every aspect of the functionality of the shell.</span></span>

- <span data-ttu-id="af8e3-216">若要尋找已啟用追蹤的 PowerShell 元件，請輸入 `Get-Help Get-TraceSource` 。</span><span class="sxs-lookup"><span data-stu-id="af8e3-216">To find the PowerShell components that are enabled for tracing, type `Get-Help Get-TraceSource`.</span></span>

  <span data-ttu-id="af8e3-217">追蹤來源是每個 PowerShell 元件的一部分，可管理追蹤並產生元件的追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="af8e3-217">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span> <span data-ttu-id="af8e3-218">如果要追蹤元件，您必須識別其追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="af8e3-218">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="af8e3-219">追蹤接聽程式會接收追蹤的輸出，並將其顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="af8e3-219">A trace listener receives the output of the trace and displays it to the user.</span></span> <span data-ttu-id="af8e3-220">您可以選擇將追蹤資料傳送至使用者模式或核心模式的偵錯工具、主機或主控台、檔案，或是從 **TraceListener** 類別衍生的自訂接聽程式。</span><span class="sxs-lookup"><span data-stu-id="af8e3-220">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the host or console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

- <span data-ttu-id="af8e3-221">當您使用 commandSet 參數集時，PowerShell 會處理命令，就像在管線中處理一樣。</span><span class="sxs-lookup"><span data-stu-id="af8e3-221">When you use the commandSet parameter set, PowerShell processes the command just as it would be processed in a pipeline.</span></span> <span data-ttu-id="af8e3-222">例如，命令探索不會針對每個連入物件重複。</span><span class="sxs-lookup"><span data-stu-id="af8e3-222">For example, command discovery is not repeated for each incoming object.</span></span>

- <span data-ttu-id="af8e3-223">**Name** 、 **Expression** 、 **Option** 及 **Command** 參數的名稱是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="af8e3-223">The names of the **Name** , **Expression** , **Option** , and **Command** parameters are optional.</span></span> <span data-ttu-id="af8e3-224">如果您省略參數名稱，未命名的參數值必須以下列順序顯示： **Name** 、 **Expression** 、 **Option** 或 **Name** 、 **Command\*\*\*\*選項** 。</span><span class="sxs-lookup"><span data-stu-id="af8e3-224">If you omit the parameter names, the unnamed parameter values must appear in this order: **Name** , **Expression** , **Option** or **Name** , **Command** , **Option** .</span></span> <span data-ttu-id="af8e3-225">如果包含參數名稱，參數可以任何順序顯示。</span><span class="sxs-lookup"><span data-stu-id="af8e3-225">If you include the parameter names, the parameters can appear in any order.</span></span>

## <span data-ttu-id="af8e3-226">相關連結</span><span class="sxs-lookup"><span data-stu-id="af8e3-226">RELATED LINKS</span></span>

[<span data-ttu-id="af8e3-227">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="af8e3-227">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="af8e3-228">Measure-Command</span><span class="sxs-lookup"><span data-stu-id="af8e3-228">Measure-Command</span></span>](Measure-Command.md)

[<span data-ttu-id="af8e3-229">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="af8e3-229">Set-TraceSource</span></span>](Set-TraceSource.md)
